# 智慧停车引导系统

基于 YOLOv8 的智能停车场管理系统，支持车位检测、车位预约、导航引导等核心功能。

## 项目概述

本项目是一个面向停车场场景的智能管理系统，融合了计算机视觉和深度学习技术，实现车位占用状态自动识别、车位预约、导航引导等核心功能。

## 技术栈

| 层级 | 技术 |
|------|------|
| 前端 | Vue.js 3 + Vite + Tailwind CSS + ECharts |
| 后端 | Flask (Python) + Express (Node.js) |
| 数据库 | MySQL |
| AI检测 | YOLOv8 目标检测模型 |
| 地图服务 | 高德地图 Web API |

## 项目结构

```
AI_text_2/
├── backend/
│   ├── flask/                 # Flask 后端 (主服务)
│   │   ├── receive_and_predict.py   # 核心API + YOLO推理
│   │   ├── init_db.py         # 数据库初始化
│   │   ├── create_sql.py      # 数据库模型创建
│   │   ├── conect_sql.py      # 数据库连接工具
│   │   ├── require_sql.py     # 数据查询接口
│   │   └── images_to_video.py # 视频处理工具
│   └── node/                  # Node.js 后端 (辅助服务)
│       ├── server.js          # API服务
│       └── mockData/          # 模拟数据
├── frontend/                  # Vue.js 前端
│   ├── src/
│   │   ├── view/              # 页面组件
│   │   │   ├── components/    # 公共组件
│   │   │   └── ParkingManagement.vue
│   │   ├── App.vue            # 根组件
│   │   └── main.js            # 入口文件
│   └── index.html
└── training/                  # YOLO 模型训练
    ├── train.py               # 训练脚本
    ├── val.py                 # 验证脚本
    └── data/                  # 训练数据
```

## 功能特性

- **实时车位检测** - 基于 YOLOv8 模型自动识别车位占用状态
- **车位预约** - 用户可提前预约停车位
- **智能导航** - 高德地图集成，一键导航至目标车位
- **AI 对话助手** - 智能问答，解答停车相关问题
- **可视化大屏** - 实时展示停车场运营数据
- **多停车场管理** - 支持多停车场接入与管理

## 快速开始

### 环境要求

- Python 3.8+
- Node.js 16+
- MySQL 5.7+
- CUDA 11.0+ (GPU 推理可选)


### 模型配置

1. 将训练好的 YOLOv8 模型权重文件 (`best.pt`) 放置到 `backend/flask/models/` 目录
2. 或修改 `receive_and_predict.py` 中的模型路径配置

## 环境变量

| 变量名 | 说明 | 默认值 |
|--------|------|--------|
| DB_USER | 数据库用户名 | YOUR_DB_USER |
| DB_PASS | 数据库密码 | YOUR_DB_PASS |
| DB_HOST | 数据库地址 | localhost |
| DB_NAME | 数据库名 | car_sql |

## API 接口

### Flask 后端

| 接口 | 方法 | 说明 |
|------|------|------|
| `/api/parking-lots` | GET | 获取停车场列表 |
| `/api/parking-spots` | GET | 获取车位列表 |
| `/api/detect` | POST | 车位检测 |
| `/api/chat` | POST | AI 对话 |

### Node.js 后端

| 接口 | 方法 | 说明 |
|------|------|------|
| `/api/parking-lots` | GET | 获取停车场数据 |
| `/api/parking-spots` | GET | 获取车位数据 |

## 许可证

本项目基于 Apache License 2.0 开源。

## 联系方式

- GitHub: wanna2023

## 致谢

- [YOLOv8](https://github.com/ultralytics/ultralytics) - Ultralytics YOLO 模型
- [Vue.js](https://vuejs.org/) - 渐进式 JavaScript 框架
- [高德地图](https://lbs.amap.com/) - 地图服务
