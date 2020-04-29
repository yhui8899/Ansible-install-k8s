# ansible部署K8S

#### 部署版本：v1.16.0

软件包下载：链接: https://pan.baidu.com/s/1PD9pE_AiZd2HiLUMMf4_BA 提取码: 6679

1、修改hosts文件

2、修改group_vars/all.yaml文件

执行命令：

```
单master：ansible-playbook -i hosts single-master-deploy.yml -uroot -k

多master：ansible-playbook -i hosts multi-master-deploy.yml -uroot -k
```

#### 增加node节点：

```
修改multi-master-deploy.yml文件中只需保留如下两个task：
- name: 2.部署Docker
- name: 6.部署K8S Node，hosts填写node的IP地址然后执行部署即可

例如：ansible-playbook -i hosts addnode.yaml -uroot -k

部署完之后执行：kubectl get csr  查看未授权的csr请求

通过csr请求：
kubectl certificate approve node-csr-qK9fxgBOTwd986YSZEKPCWzyi7oa4sCnKNAe3xaaJxA
```

#### 部署时生产的秘钥证书文件统一放在ansible-install-k8s-master目录下的ssl中

