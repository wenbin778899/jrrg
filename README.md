<<<<<<< HEAD
# jrrg
=======
# NJU金融软工项目

该项目是南京大学《金融软工》课程的项目，包含前后端完整代码。

## 项目结构

项目分为前端和后端两个部分：

- `jrrg_framework_backend`：后端项目，基于Python Flask框架开发
- `jrrg_framework_frontend`：前端项目，基于React和Ant Design开发

## 功能特性

- 用户注册与登录
- JWT认证机制
- 用户信息管理
- 响应式界面设计

## 运行项目前的必要准备

### 数据库配置

1. 确保已安装MySQL数据库

2. 创建数据库和用户表
   ```sql
   create database jrrg_framework_db;
   use jrrg_framework_db;
   create table user (
       id       int auto_increment primary key,
       username varchar(255) not null,
       password varchar(60)  not null,
       nickname varchar(255) null,
       email    varchar(255) null,
       phone    varchar(11)  null,
       constraint user_pk unique (username)
   );
   ```

3. 修改`jrrg_framework_backend/app.env`文件中的数据库连接信息
   ```
   SQLALCHEMY_DATABASE_URI=mysql+mysqlconnector://root:您的密码@localhost:3306/jrrg_framework_db
   JWT_SECRET_KEY=your-secret-key
   ```

### 后端环境准备

1. 确保使用Python 3.10
   ```
   python --version
   ```

2. 创建并激活虚拟环境（推荐）
   ```
   # 使用conda
   conda create -n jrrg python==3.10
   conda activate jrrg
   
   # 或使用venv
   python -m venv venv
   # Windows
   venv\Scripts\activate
   # Linux/Mac
   source venv/bin/activate
   ```

3. 安装依赖包
   ```
   pip install -r requirements.txt
   ```

### 前端环境准备

1. 确保已安装Node.js（推荐LTS版本）
   ```
   node --version
   npm --version
   ```

2. 安装前端依赖
   ```
   cd jrrg_framework_frontend
   npm install
   ```

3. 如果后端服务不是默认的`http://localhost:8080`，需要修改`jrrg_framework_frontend/src/setupProxy.js`文件中的后端地址

## 运行项目

### 启动后端服务

```
cd jrrg_framework_backend
python run.py
```
后端将在`http://localhost:8080`启动

### 启动前端服务

```
cd jrrg_framework_frontend
npm start
```
前端将在`http://localhost:3000`启动

浏览器会自动打开前端页面。如果没有自动打开，请手动访问`http://localhost:3000`

## 项目使用

1. 首次使用需要在注册页面创建账号
2. 使用已注册的账号登录系统
3. 登录后可以查看个人资料页面

## 注意事项

1. **app.env配置文件**：
   - 该文件包含敏感信息，生产环境不应上传到代码仓库
   - 必须正确配置数据库连接信息

2. **node_modules和Python虚拟环境**：
   - 这些目录不包含在代码仓库中
   - 需要按照上述步骤自行创建和安装依赖

3. **跨域问题**：
   - 前端通过setupProxy.js解决跨域问题
   - 如修改后端端口，必须同步修改前端代理配置

4. **可能遇到的问题**：
   - 如果MySQL连接失败，请检查用户名、密码、主机和端口配置
   - 如果依赖安装失败，可能需要配置代理或更换源

## API接口

后端提供以下主要API接口：

- `/user/login`: 用户登录
- `/user/logout`: 用户登出
- `/user/register`: 用户注册
- `/user/info`: 获取当前用户信息
- `/user/info/<user_id>`: 获取指定用户信息 
>>>>>>> c687e20 (first commit)
