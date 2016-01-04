# AWS

## Keypair생성
- 1. Tokyo Region을 선택
- 2. 스터디용KeyPair생성
- 3. 다운로든 된 Key Pair 및 경로 확인
- 4. 생성한KeyPair삭제
- 5. Key Pair 다시 생성

## Security Group 생성
- 1. 각 인스턴스에 IN/OUT 트레픽을 제어하는 방화벽
- 2. 보안을 위해 필요한 서비스 포트만 오픈
- 3. 복수개의 Rule 정의 가능
- 4. 설정 항목
   - 프로토콜 (TCP / UDP / ICMP)
   - Port
   - Source IP (IP 또는 Security Group ID)
   - Destination IP (IP 또는 Security Group ID)
- 5. Region별로 생성 관리
- 6. 인스턴스 기동 시 Security Group 할당

## EC2
- CLI접속
```
$> chmod 700 study.pem
$> ssh -i study.pem ec2-user@{ip}
```

## Linux (CentOS)
- [setting] yum설정
- vi  /etc/yum.repos.d/epel.repo 에서 baseurl을주석해제하고, mirrorlist를 주석
- yum -y install gcc-c++ curl curl-devel


## 계정
```
0. 계정 생성
# mkdir /app (애플리케이션 모든정보)
# groupadd -g 501 torres
# useradd -u 501 -g 501 -d /app/torres -s /bin/bash torres
(# useradd -d /app/torres torres)
# passwd torres
# cat /etc/passwd (확인)

0. 권한부여
# chown torres . (/app에서 파일의 소유권을 ids사용자에게)
# chgrp torres . (/app에서 파일의 소유권을 ids그룹에게)
!!!!! chown -R torres:torres /app/
```

# Mysql
- rpm -qa | grep mysql-server // 설치확인
- yum install mysql-server // 설치
- service mysqld start // 서비스 시작
- /usr/bin/mysqladmin -u root password '1111' // 패스워드변경
- mysql -uroot -p  // 접속

- http://kwonnam.pe.kr/wiki/database/mysql/basic

# MongoDB
- http://misoin.tistory.com/21
- 1. 다운로드 wget https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-amazon-3.2.0.tgz
- 2. vi mongodb.conf
```
dbpath=/app/mongodb-3.2.0/data   # mkdir -p /app/mongodb-3.2.0/data/
logpath=/app/mongodb-3.2.0/mongodb.log
logappend=true
verbose=true
#bind_ip=127.0.0.1
port=27017
fork=true
# rest 옵션은 브라우저에서 접속할건지 여부, 브라우저포트는 port로 잡은 거에 +1000 한 값 (28017)
rest=true
#auth=true
#noauth=true
```
- 3. MongoDB 서버 실행 : bin/mongod --config mongodb.conf  
- 4. MongoDB client 실행 : bin/mongo localhost:27017
- 5. MongoDB web 실행 : http://{ip}:28017/
