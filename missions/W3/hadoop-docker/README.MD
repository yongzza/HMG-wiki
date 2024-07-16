# Docker를 사용하여 단일 노드 Hadoop 클러스터 설정하기

## Dockerfile과 Hadoop 설정 파일 생성 후 Docker 이미지 빌드

```bash
docker build -t hadoop-single-node .  
```

## Docker 컨테이너 실행

```bash
docker run -it --platform linux/amd64 --name hadoop-container -p 9870:9870 -p 9864:9864 -p 8088:8088 -p 8042:8042 hadoop-single-node  

## 컨테이너 실행 상태 확인

```bash
http://localhost:9870 # NameNode
http://localhost:9864 # DataNode
http://localhost:8088 # ResourceManager
http://localhost:8042 # NodeManager 
```　

## HDFS에 저장

```bash 
docker exec -it hadoop-container bash # 새 터미널열고 Docker 컨테이너 내부에 접속

hdfs dfs -mkdir /user # HDFS에 디렉터리 생성 
hdfs dfs -mkdir /user/root
```　
