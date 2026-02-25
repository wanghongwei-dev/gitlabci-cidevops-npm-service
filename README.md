# GitLab CI NPM 服务示例

这是一个基于Vue.js的前端Web应用示例，展示了如何在GitLab CI/CD环境中实现前端项目的持续集成和部署。

## 功能特性

- Vue.js单页面应用
- Webpack构建配置
- 响应式UI组件
- Vue Router路由管理
- Docker容器化支持
- Kubernetes部署配置

## 技术栈

- **框架**: Vue.js 2.5+
- **路由**: Vue Router 3.x
- **构建工具**: Webpack 3.x
- **包管理**: npm
- **容器化**: Docker
- **部署**: Kubernetes

## 项目结构

```
gitlabci-cidevops-npm-service/
├── build/                           # 构建配置
│   ├── build.js                     # 生产构建脚本
│   ├── check-versions.js            # 版本检查
│   └── utils.js                     # 构建工具函数
├── config/                          # 配置文件
│   ├── dev.env.js                   # 开发环境配置
│   ├── index.js                     # 主配置文件
│   └── prod.env.js                  # 生产环境配置
├── manifest_tpl/                    # Kubernetes部署模板
│   ├── deployment.yaml              # 基础部署配置
│   ├── deployment-stag.yaml         # 预发布环境配置
│   ├── deployment-uat.yaml          # UAT环境配置
│   └── deployment-prod.yaml         # 生产环境配置
├── src/                             # 源代码目录
│   ├── components/                  # Vue组件
│   │   └── HelloWorld.vue           # 示例组件
│   ├── router/                      # 路由配置
│   │   └── index.js                 # 路由入口
│   ├── App.vue                      # 根组件
│   └── main.js                      # 应用入口
├── Dockerfile                       # Docker镜像构建文件
├── index.html                       # HTML模板
├── package.json                     # npm配置文件
├── package-lock.json                # 依赖锁定文件
└── README.md                        # 项目说明文档
```

## 快速开始

### 本地开发

1. 克隆项目
```bash
git clone <repository-url>
cd gitlabci-cidevops-npm-service
```

2. 安装依赖
```bash
npm install
```

3. 启动开发服务器
```bash
npm run dev
```

访问 `http://localhost:8080` 查看应用。

### 生产构建

```bash
# 构建生产版本
npm run build

# 构建后的文件位于 dist/ 目录
```

### Docker运行

1. 构建镜像
```bash
docker build -t npm-service .
```

2. 运行容器
```bash
docker run -p 8080:80 npm-service
```

访问 `http://localhost:8080` 查看应用。

## npm脚本

```json
{
  "dev": "webpack-dev-server --inline --progress --config build/webpack.dev.conf.js",
  "start": "npm run dev",
  "build": "node build/build.js"
}
```

## CI/CD配置

项目包含完整的GitLab CI/CD配置，支持：
- Node.js环境设置
- npm依赖安装
- 前端构建
- Docker镜像构建
- 自动化部署

## 部署配置

### Kubernetes部署

使用提供的YAML模板进行Kubernetes部署：

```bash
# 部署到开发环境
kubectl apply -f manifest_tpl/deployment.yaml

# 部署到预发布环境
kubectl apply -f manifest_tpl/deployment-stag.yaml

# 部署到生产环境
kubectl apply -f manifest_tpl/deployment-prod.yaml
```

## 环境要求

- Node.js >= 6.0.0
- npm >= 3.0.0
- Docker (可选)
- Kubernetes集群 (可选)

## 开发说明

### 组件开发
- 组件位于 `src/components/` 目录
- 使用单文件组件(.vue)格式
- 支持ES6+语法

### 路由配置
- 路由配置位于 `src/router/index.js`
- 支持动态路由和嵌套路由

### 样式处理
- 支持CSS、SCSS预处理器
- 自动添加浏览器前缀
- 支持CSS模块化

## 浏览器支持

- Chrome >= 55
- Firefox >= 50
- Safari >= 10
- Edge >= 13
- IE >= 9

## 许可证

Apache License
