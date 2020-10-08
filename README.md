# SQL(Strucured Query Language)이란
SQL은 관계형 데이터베이스 관리 시스템(RDBMS)의 데이터를 관리하기 위해 설계된 특수 목적의 프로그래밍 언어이다.

관계형 데이터 베이스 관리 시스템에서 자료의 검색과 관리, 데이터베이스 스키마 생성과 수정, 데이터 베이스 객체 접근 조정 관리를 위해 고안되었다.

많은 수의 데이터베이스 관련 프로그램들이 SQL을 표준으로 채택하고 있다.

# 데이터 베이스 기본 구조
![Alt text](img1.jpg)
- 표 : 기본적인 데이터들을 기준에 따라 나열한 것.
- 데이터베이스 or 스키마 : 서로 연관된 데이터들을 그룹핑하여 만든 표들로 구성된 일종의 파일의 폴더개념 
- 데이터베이스 서버 : 데이터베이스들을 관리함.

# MySQL이란
표준 데이터베이스 질의 언어 SQL을 사용하는 오픈 소스의 관계형 데이터베이스 관리시스템(RDBMS).

매우 빠르고, 유연하며, 사용하기 쉬운 특징이 있다.

## MySQL 설치 과정
- https://www.mysql.com/products/community/ 에서 자신의 OS에 맞는 버젼으로 설치가능.
- https://bitnami.com/stack/wamp 에서 더 간편하게 설치 가능.
- 설치과정에서 비밀번호를 만들게 되는데 해당 비밀번호는 실행시에 사용하게됨

## MySQL 실행 과정
1) cmd창 열기
2) cd 명령어를 통해 C:\Bitnami\wampstack-7.4.10-0\mysql\bin로 이동 (설치한 버젼에 맞게)
3) mysql -uroot -p로 프로그램 실행. 후에 설치시 입력한 비밀번호 입력
> ### -u[username] -p
> - -u는 유저을 의미한다. username으로 접근한다. username이 root인 경우 root권한으로 접근
> - -p는 해당 username에 비밀번호가 설정되어있지 않은 경우에는 생략해도 된다. 그러나 비밀번호가 설정되어 있는데 생략하게되면 에러발생.
4) 완료
 
## MySQL 문법 정리
### 데이터베이스 관련
> #### CREATE DATABASE [databaseName];
> - databaseName으로 데이터베이스 생성
> #### DROP DATABASE [databaseName];
> - databaseName의 데이터베이스 삭제
> #### SHOW (DATABASES | SCHEMAS);
> - 데이터베이스 내용 출력
> #### USE [databaseName];
> - MySQL에게 내가 접근할 데이터베이스가 무엇인지 알려줌. 이를 통해 내가 업데이트하고자하는 데이터베이스에 접근가능
### 표 관련
> #### CREATE TABLE [tableName](
> [1번열 항목] [data_type] (length),

> ...

> )
> - 테이블 생성. dataType은 해당 데이터의 type에 맞게 사용. type의 종류는 검색해볼것. length는 노출시킬 데이터의 범위를 의미. 
> ##### ex) CREATE TABLE topic(
> -> id INT(11) NOT NULL AUTO_INCREMENT,

> -> title VARCHAR(100) NOT NULL,

> -> description TEXT NULL,

> -> created DATETIME NOT NULL,

> -> author VARCHAR(30) NULL,

> -> profile VARCHAR(100) NULL,

> -> PRIMARY KEY(id));   
>> NOT NULL은 데이터의 값이 없는것을 허용하지 않음. NULL은 반대. AUTO_INCREMENT는 숫자가 자동적으로 하나씩 늘어나게됨. 각 데이터타입은 찾아서 적절한 타입으로 생성할것. PRIMARY KEY는 고유키로써 해당 열의 데이터 값들은 중복없이 고유한 값을 가져야함을 의미.

> #### SHOW TABLES;
> - 생성된 테이블들을 보여줌

> #### DESC [tableName];
> - 해당 테이블의 field, type, NULL등의 정보가 출력됨

> #### INSERT INTO [tableName] ([fieldName,]) VALUES([value,]);
> - tableName의 table안에서 fieldName과 value를 매칭하여 데이터 생성. fieldName과 value의 순서 중요. 순서에 따라 매칭됨.

> ##### ex) INSERT INTO topic (title,description,created,author,profile) VALUES('MySQL','MySQL is ...',NOW(),'wonny','developer');
> - created에 매칭되는 곳에 NOW()를 사용하였는데 이는 현재시간을 말함

> #### SELECT [열의 항목들] FROM [tableName];
> - tableName에 있는 데이터를 원하는 [열의 항목들]만 읽어옴. [열의 항목들]을 *로 할 경우 전체를 받아옴.

> ##### ex) SELECT id,title,created,author FROM topic;
> ##### ex) SELECT id,title,created,author FROM topic WHERE author='wonny';
> ##### ex) SELECT id,title,created,author FROM topic WHERE author='wonny' ORDER BY id DESC;
> ##### ex) SELECT id,title,created,author FROM topic WHERE author='wonny' ORDER BY id DESC LIMIT 2;

> #### UPDATE [tableName] SET [바꿀항목=바꿀내용] WHERE [바꿀 위치];
> ##### ex) UPDATE topic SET description='ORACLE is .....', title='Oracle' WHERE id=2;
> - WHERE를 빼고 실행시키면 모든 행에 다 적용되므로 돌이킬수 없는 강을 건너버린다. 반드시 그런일이 일어나지 않도록 조심하고 또 조심하자.

> #### DELETE [tableName] WHERE [삭제할 위치];
> ##### ex) DELETE FROM topic WHERE id=5;
> - WHETE 빼고 쓰면 모두 삭제되므로 절대 주의!!



