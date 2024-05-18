# marker-deploy

## 简介
一个简易的pdf转markdown服务
- 前端项目地址：[marker-ui](https://github.com/zivenyang/marker-ui)
- 后端项目地址：[marker-api](https://github.com/zivenyang/marker-api.git)

## 特性
- 基于[marker](https://github.com/VikParuchuri/marker.git)的PDF转Markdown服务，支持OCR识别
- 基于[Vditor](https://b3log.org/vditor/)的markdown编辑器
- 基于docker部署

## 部署
在运行安装命令之前，请确保您的机器上安装了 [Docker](https://docs.docker.com/get-docker/) 和 [Docker Compose](https://docs.docker.com/compose/install/)

```bash
git clone https://github.com/zivenyang/marker-deploy.git --recursive
cd marker-deploy
docker-compose up -d --build
```

前端日志查看：`docker logs -f marker-ui`  
后端日志查看：`docker logs -f marker-api`

## 使用
访问[http://localhost:28000/](http://localhost:28000/)进行访问

点击第一个图标上传pdf文件进行识别，识别时长取决与本机算力，第一次使用会从huggingface上下载模型，本镜像默认使用的cpu计算，识别时间较长（约10分钟），如需使用gpu请修改docker-compose.yml中的api服务
![使用教程](./images/image.png)

## 效果
![识别xiaog](./images/image2.png)

## 不足
- 暂不支持图片预览，但接口有返回base64编码
- marker-api原生模型对中文的识别效果欠佳，后续可考虑对接国产识别模型
- 交互体验有待改进

## 依赖
- [marker](https://github.com/VikParuchuri/marker.git)
- [marker-api](https://github.com/adithya-s-k/marker-api)
- [Vditor](https://b3log.org/vditor/)