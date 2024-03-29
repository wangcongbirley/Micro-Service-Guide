# Micro-Service

各模块服务化，暴露接口，完成子模块互相调用。

## 目录
- [前言](#前言)
- [项目架构](#项目架构)
  - [技术栈选型](#技术栈选型)
- [网关层](#网关层)
- [注册中心](#注册中心)
  - [nacos](#nacos)  
  - [治理策略](#治理策略)
- [运维服务层](#运维服务层)
    - [系统监控](#系统监控)    
    - [部署](#部署)
      - [Docker](#Docker)
      - [tomcat集群](#tomcat集群)
    - [消息队列](#消息队列)
- [待办...](#待办)


### 前言
自顶向下设计微服务平台，以下是系统设计过程。

### 项目架构
系统分层，用户、接入层、网关层、业务服务层、基础服务层、运维服务层。分层目的是松耦合，增加拓展性。架构图如下
![](/images/1.png)

前端使用vue/element-ui构建可视界面，后端采用maven多模块/springboot构建API接口，业务层。项目通过华为his部署，灰度发布。
#### 技术栈选型

1. [微服务技术栈有哪些？](docs/micro-stack.md)

### 网关层
网关应用，提供网关路由转发、降级、熔断、请求处理等网关功能。
gateway-admin 提供路由应用管理，包括路由配置，设置灰度分流。
网关主要做了一件事：请求过滤。我们在网关处理一些非业务逻辑的事情，权限认证、缓存、请求路由等。
#### 常用开源网关组件
- Kong
- zuul

#### API网关


### 注册中心
- Zookeeper
- nacos
- euraka

#### nacos
使用nacos替代eureka为服务的注册中心。

1. [SpringCloud Euraka](docs/springcloud.md)


#### 治理策略

1. [治理策略](docs/micro-governance.md)


#### redis

1. [redis](docs/redis.md)


### 运维服务层

#### 系统监控

1. [Kibana](docs/kibana.md)

2. [druid](docs/druid.md)

#### 部署

部署发布使用华为鲲鹏计算云，RDS的MySQL集群，灰度发布。项目打成war包，使用tomcat集群。生产环境操作需提交变更号，经过专家评审，审批通过后部署。

1. [部署模式](docs/micro-deployment.md)
2. [tomcat集群](docs/deploy.md)

##### Docker
Docker是一个开源的容器引擎，它有助于更快地交付应用。方便快捷已经是 Docker的最大优势，过去需要用数天乃至数周的任务，在Docker容器的处理下，只需要数秒就能完成。

Docker-compose 是 docker 提供的一个命令行工具，用来定义和运行由多个容器组成的应用。使用 compose，我们可以通过 YAML 文件声明式的定义应用程序的各个服务，并由单个命令完成应用的创建和启动。

##### tomcat集群
-[tomcat集群](docs/deploy.md)
#### 消息队列

1. [消息队列选型](docs/mq.md)

### 待办
