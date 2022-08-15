cd 当前目录
  执行命令 docker-compose up -d cli 启动写好的docker-compose.yml
查看容器是否运行
  docker-compose ps
进入容器命令
  docker-compose exec cli /bin/sh
在 docker-compose.yml 文件里，再定义一个运行 Nest.js 应用的服务：  nest:
    image: node:${NODE_VERSION}
    working_dir: /home/node/app
    command: npm config set registry https://registry.npm.taobao.org
    command: npm run start:dev
    volumes:
      - ./app:/home/node/app
    ports:
      - ${APP_PORT}:3000
启动这个服务
     docker-compose up -d nest
定义数据库
     docker-compose up -d mysql