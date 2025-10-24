# Toursys

Toursys 是一个基于 Flask 的旅游景点推荐和评论系统，用户可以浏览景点、发表评论、上传头像，管理员可以管理用户和景点信息。
默认用户:user1/password123
	admin/admin123

## 功能特性

### 用户功能
- 用户注册和登录
- 浏览景点列表和详情
- 搜索景点（按名称、位置、描述）
- 发表景点评论和评分
- 个人中心：
  - 修改个人信息
  - 修改密码
  - 上传头像

### 管理员功能
- 管理员登录
- 用户管理：
  - 查看所有用户
  - 删除用户
- 景点管理：
  - 添加新景点
  - 编辑景点信息
  - 删除景点
  - 上传景点封面图片

### 技术特性
- 基于 Flask 框架
- 使用 SQLAlchemy 进行数据库操作
- 使用 Flask-Login 处理用户认证
- 使用 Flask-WTF 处理表单验证
- 使用 SQLite 作为默认数据库
- 响应式前端设计

## 项目结构

```
├── app.py
├── forms.py
├── gui_app.py
├── init_db.py
├── instance
│   └── toursys.db
├── models.py
├── __pycache__
│   ├── app.cpython-312.pyc
│   ├── app.cpython-38.pyc
│   ├── forms.cpython-312.pyc
│   ├── forms.cpython-38.pyc
│   ├── init_db.cpython-38.pyc
│   ├── min_app.cpython-38.pyc
│   ├── models.cpython-312.pyc
│   ├── models.cpython-38.pyc
│   ├── routes.cpython-312.pyc
│   └── routes.cpython-38.pyc
├── README.md
├── routes.py
├── run_app.py
├── setup.cfg
├── static
│   ├── css
│   │   └── style.css
│   ├── images
│   │   ├── attraction_1761181899_6660.jpg
│   │   ├── attraction_1761182703_3197.jpg
│   │   ├── default.jpg
│   │   ├── forbidden_city.jpg
│   │   ├── great_wall.jpg
│   │   ├── huangshan.jpg
│   │   ├── OIP.jpg
│   │   └── west_lake.jpg
│   ├── js
│   └── uploads
├── templates
│   ├── 404.html
│   ├── 500.html
│   ├── admin
│   │   ├── admin_attractions.html
│   │   ├── admin.html
│   │   ├── admin_users.html
│   │   └── login.html
│   ├── attraction_detail.html
│   ├── attractions_list.html
│   ├── base.html
│   ├── index.html
│   ├── login.html
│   ├── profile.html
│   ├── register.html
│   └── search.html
└── toursys_config.ini
```

## 安装和运行

### 环境要求
- Python 3.8+
- Flask
- Flask-SQLAlchemy
- Flask-Login
- Flask-WTF

### 安装步骤
0.安装依赖：
    ```
    pip install flask flask_sqlalchemy　flask_login flask_wtf.csrf tkinter pillow

    ```

1. 克隆项目到本地：
   ```
   git clone <repository-url>
   cd Toursys
   ```

2. 创建虚拟环境（推荐）：
   ```
   python -m venv venv
   source venv/bin/activate  # Linux/Mac
   # 或者在 Windows 上使用:
   # venv\Scripts\activate
   ```

3. 初始化数据库：
   ```
   python init_db.py
   ```

4. 运行应用：
   ```
   python app.py
   ```

5. 访问应用：
   在浏览器中打开 `http://127.0.0.1:5000`

6.图形化界面：
   ```
   python gui_app.py
   ```

### 配置

应用可以通过环境变量进行配置：

- `SECRET_KEY`: Flask 应用的密钥
- `DATABASE_URL`: 数据库连接 URL
- `PORT`: 应用运行端口（默认 5000）
- `DEBUG`: 是否启用调试模式（默认 True）

## 使用说明

### 用户操作流程
1. 访问首页浏览推荐景点
2. 点击景点查看详细信息和评论
3. 注册账户并登录
4. 在景点详情页发表评论和评分
5. 在个人中心修改个人信息、密码或上传头像

### 管理员操作流程
1. 访问 `/admin/login` 登录管理员账户
2. 在管理员面板中管理用户和景点
3. 可以添加、编辑、删除景点信息

## 数据库设计

### 用户表 (users)
- id: 用户ID
- username: 用户名
- email: 邮箱
- password_hash: 密码哈希值
- avatar: 头像文件名
- is_admin: 是否为管理员
- created_at: 创建时间

### 景点表 (attractions)
- id: 景点ID
- name: 景点名称
- description: 景点描述
- location: 景点位置
- image_url: 封面图片URL
- category: 景点类别
- price: 门票价格
- rating: 平均评分
- created_at: 创建时间

### 评论表 (comments)
- id: 评论ID
- user_id: 用户ID（外键）
- attraction_id: 景点ID（外键）
- content: 评论内容
- rating: 评分（1-5）
- created_at: 创建时间

## 贡献

欢迎提交 Issue 和 Pull Request 来改进本项目。

## 许可证

本项目采用 MIT 许可证。
