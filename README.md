## Docker Images Pusher

使用Github Action将国外的Docker镜像转存到阿里云私有仓库

- 支持国外任意仓库
- 支持最大40GB的大型镜像
- 使用阿里云的官方线路，速度快

## 


## 配置阿里云

- [阿里云容器镜像服务](https://cr.console.aliyun.com/)

![image-20250425001234684](http://pic.swireb.cn/images/image-20250425001234684.png)

![image-20250425001436935](http://pic.swireb.cn/images/image-20250425001436935.png)

- 配置Github Action环境变量

![image-20250425000457991](http://pic.swireb.cn/images/image-20250425000457991.png)

```
ALIYUN_NAME_SPACE             #命名空间
ALIYUN_REGISTRY               #仓库地址
ALIYUN_REGISTRY_PASSWORD      #密码
ALIYUN_REGISTRY_USER          #用户名
```



## Docker配置

- 配置文件修改

```shell
#修改配置文件
vim /etc/docker/daemon.json
{
  "registry-mirrors": ["https://crpi-5djp3l2ebt5lyhar.cn-hangzhou.personal.cr.aliyuncs.com"]
}

#重启服务
systemctl restart docker
```

- 拉取容器镜像只要在前面添加用户名即可

```shell
docker pull jackywn/nginx:latest
```

