

# 도커란?

컨테이너라는 독립된 환경에서의 애플리케이션 구동을 지원하는 플랫폼

* 컨테이너란? 애플리케이션을 환경에 구애받지 않고 실행하는 기술

# 도커를 써야하는 이유 !

## 1. 팀원 및 서버와 개발 환경을 쉽게 동기화할 수 있다.

### 팀워크에서의 이점

- 개발을 하다보면 팀원들과 OS나 언어, 프레임워크 버전이 달라 오류가 나는 경우 도커를 사용하면 해결할 수 있다.
- 도커 이미지에 언어나 프레임워크 버전을 미리 모두 정해놓을 수 있고 해당 이미지를 컨테이너화 시키면 그 컨테이너는 로컬 환경의 간섭 없이 독립적으로 구동하기 때문에 위와 같은 걱정을 할 필요가 싹 사라진다.
- Dockerfile을 사용하면 설치할 언어, 프레임워크, 패키지 등을 미리 코드 형태로 명시하고 어느 컴퓨터에서든 쉽게 자동으로 설치할 수 있다.

### 서버에서의 이점

- 서버 컴퓨터 또한 쉽게 내 개발 환경과 같은 환경으로 만들 수 있다.
- 서버를 옮기거나 늘릴 때 도커를 사용하면 이미지만을 가져와 새로운 서버에 컨테이너를 만들어 쉽게 동일한 환경을 구축할 수 있다.

</br>

## 2. 자원적, 성능적으로 뛰어나다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6d1b61bf-11e4-4bf5-aaac-af18e8b86e77/Untitled.png)

### 가상화 방식

- 각 가상 환경마다 독립된 커널 OS가 존재 → 매우 무겁고 느림.
- 각 환경마다 쓸 수 있는 자원이 고정  → 컴퓨터의 성능과 환경이 제한됨.

### 도커

- 새롭게 커널 OS를 생성하지 않고 기존의 커널 OS 자원을 계승하여 사용
- 각 환경마다 사용할 수 있는 자원이 고정으로 정해져 있지 않아 유동적

</br>

# 도커 아키텍처

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0b83f8ec-ec86-40a0-96ce-ed28bcac4b61/Untitled.png)

- `Docker`는 크게 `Client`와 `Server`로 나뉜다.
- `Client`에서는 'CLI (Command Line Interface)' 혹은 'Docker API'를 통해 '데몬'과 소통한다.
- '데몬'은 `Client`의 요청을 기다리며 또 다른 '데몬'들과 통신한다.
- '데몬'은 '컨테이너', '이미지', '볼륨', '네트워크'와 같은 `Docker`의 객체들을 전반적으로 관리하는 역할을 한다.
- `Docker`의 `Registry`는 '이미지'들을 저장하는 장소이며 기본적으로 `Docker Hub`이 'Public Registry'로 설정되어 있고 'Private Registry'를 따로 설정할 수도 있다.

## 도커 이미지

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/39bcc732-74de-4189-a06f-b624099c07ec/Untitled.png)

- 컨테이너 **실행에 필요한 파일과 설정값 등을 포함하고 있는것.**
- 이미지는 컨테이너를 실행하기 위한 모든 정보를 가지고 있기 때문에 더이상 의존성 파일을 컴파일 하고 서버환경을 맞추기 위해 이것저것 설치할 필요가 없다!
- 같은 이미지에서 여러개의 컨테이너를 생성할 수 있고 컨테이너의 상태가 바뀌거나 컨테이너가 삭제되더라도 이미지는 변하지 않음
- 새로운 서버가 추가되면 미리 만들어놓은 이미지를 다운받고 컨테이너를 생성만 하면 된다.
- 한 서버에 여러개의 컨테이너를 실행할 수 있고, 수천대의 서버도 문제없음!
- 도커 이미지는 는 Docker hub에 등록하거나 Docker Registry 저장소를 직접 만들어 관리할 수 있다.

## 도커 컨테이너

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/49d05db1-5da2-40ba-b0b8-322e9d6c9c53/Untitled.png)

- 애플리케이션을 환경에 구애받지 않고 실행하는 기술
- 애플리케이션 뿐만 아니라 애플리케이션을 실행하는데 필요한 모든 환경을 포함
- 백엔드 프로그램, 데이터베이스 서버, 메세지 큐 등 어떤 프로그램도 컨테이너로 추상화할 수 있음
- PC, AWS, Azure, Google cloud 등 어디서든 실행할 수 있음

→ 즉, 실행시키고 싶은 애플리케이션의 필요한 설정값들을 이미지로 만들어 관리한다. 그리고 컨테이너는 이러한 이미지를 실행시키는 가상화 공간이자 해당 이미지의 인스턴스인 것!



</br>

- **📚 도커의 기본 명령어들**

    ❗️ 명령 입력 시 **permission** 관련 오류가 뜨는 환경에서는 각 명령어 앞에 `sudo`를 붙여주세요.

    > ⭐️ 도커 버전 확인

    ```docker
    docker -v
    ```

    > 도커 이미지 다운만 받기

    ```docker
    docker pull {이미지명}:{태그} # 예: docker pull python:3
    ```

    - 태그는 필수가 아닙니다.

    > ⭐️ 컴퓨터 내 도커 이미지들 보기

    ```docker
    docker images
    ```

    > 이미지로 컨테이너 생성하기

    ```docker
    docker create {옵션} {이미지명}:{태그} # 예: docker create -it python
    ```

    > 만들어진 컨테이너 시작하기 (이미지에 CMD로 지정해놓은 작업 시키기)

    ```docker
    docker start {컨테이너 id 또는 이름}
    ```

    > 컨테이너로 들어가기 (컨테이너 내 CLI 이용하기)

    ```docker
    docker attach {컨테이너 id 또는 이름}
    ```

    > ⭐️ 이미지를 다운받아(없을 시에만) 바로 컨테이너 실행하여 진입하기

    ```docker
    docker run {이미지명}:{태그} # 예: docker -it run python:3
    ```

    - *pull*, *create*, *start*, *attach* 를 한꺼번에 실행하는 것과 같습니다.

    > 동작중인 컨테이너 재시작

    ```docker
    docker restart {컨테이너 id 또는 이름}
    ```

    > 도커 컨테이너의 내부 쉘에서 빠져나오기 (컨테이너를 종료)

    ```docker
    exit
    ```

    - 또는 **Ctrl + D**

    > 도커 컨테이너의 내부 쉘에서 빠져나오기 (컨테이너를 종료하지 않음)

    ```docker
    docker pull {이미지명}:{태그}# 예: docker pull python:3
    ```

    - **Ctrl + P, Q**

    > ⭐️ (동작중인) 컨테이너들 보기

    ```docker
    docker ps
    ```

    - 동작중이 아닌 것을 포함한 모든 컨테이너를 보려면 *a* 옵션을 뒤에 붙입니다.

    > 컨테이너 삭제

    ```docker
    docker rm {컨테이너 id 또는 이름} # ⭐️ 모든 컨테이너 삭제docker rm `docker ps -a -q`
    ```

    > 이미지 삭제

    ```docker
    docker rmi {옵션} {이미지 id}
    ```

    - 컨테이너가 있을 시 강제삭제: `f` 옵션 사용

    > ⭐️ 모든 컨테이너와 이미지 등 도커 요소 중지 및 삭제

    ```docker
    # 모든 컨테이너 중지docker stop $(docker ps -aq)
    # 사용되지 않는 모든 도커 요소(컨테이너, 이미지, 네트워크, 볼륨 등) 삭제
    docker system prune -a
    # 아래를 복붙하여 함께 실행하면 편리합니다.
    docker stop $(docker ps -aq)docker system prune -a
    ```

    - 확인 질문에 *y*로 답하고 마무리합니다.

    > ⭐️ 도커파일로 이미지 생성

    ```docker
    # Dockerfile 파일이 있는 디렉토리 기준.  마지막의 . 이 상대주소
    docker build -t {이미지명} .
    ```

    > ⭐️ 도커 컴포즈 실행

    ```docker
    # docker-compose 파일이 있는 디렉토리 기준docker-compose up
    ```

    - 백그라운드에서 데몬으로 돌도록 하려면 *d* 옵션을 붙입니다
    
    
</br>

## Node.js 에서의 도커라이징

### 0. 도커 설치 (생략)

![스크린샷 2021-09-25 오전 11.06.36.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f39262b1-cd71-4e77-9902-2c2a283d1087/스크린샷_2021-09-25_오전_11.06.36.png)

프로젝트 구조

### 1. Node.js 앱 생성

```json
{
  "name": "docker_web_app",
  "version": "1.0.0",
  "description": "Node.js on Docker",
  "author": "First Last <first.last@example.com>",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.16.1"
  }
}
```

```jsx
'use strict';

const express = require('express');

// 상수
const PORT = 8080;
const HOST = '0.0.0.0';

// 앱
const app = express();
app.get('/', (req, res) => {
  res.send('Hello World');
});

app.listen(PORT, HOST);
console.log(`Running on http://${HOST}:${PORT}`);

```

### 2. Dockerfile 생성 (이미지 생성)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fd8a9455-9c71-4d77-9aa1-7302e658d4e2/Untitled.png)

- 어떤 이미지를 사용해서 빌드할 것인지 정의
- 애플리케이션의 작업 디렉터리 설정
- 앱의 소스코드를 넣기 위해 COPY 지시어를 사용
- 앱이 8080 포트에 바인딩 되어 있으므로 EXPOSE 지시어로 docker demon에 매핑
- 서버를 구동하도록 하는 명령어 정의

### 3. .dockerignore 생성

![스크린샷 2021-09-25 오전 11.05.11.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1191a12b-b1c5-4533-a616-5bfb356ae800/스크린샷_2021-09-25_오전_11.05.11.png)

- Docker 이미지에 로컬 모듈과 디버깅 로그를 복사하는 것을 막아서 이미지 내에서 설치한 모듈을 덮어쓰지 않게 함.

### 4. 이미지 빌드

```docker
docker build . -t <your username>/<image name>
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/43f4f53f-6138-48d3-8d77-68fe3d45df26/Untitled.png)

![스크린샷 2021-09-25 오전 11.01.56.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/deb35dbf-b5e3-4e41-811e-5982b2158935/스크린샷_2021-09-25_오전_11.01.56.png)

![스크린샷 2021-09-25 오전 11.02.36.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/76745790-d9d9-466e-9e3c-5acfc1ad378f/스크린샷_2021-09-25_오전_11.02.36.png)

도커 허브에 이미지가 올라간 것을 확인할 수 있음. 

### 5. 이미지 실행

```docker
docker run -p 49160:8080 -d <your username>/<image name>
```

![스크린샷 2021-09-25 오후 2.12.49.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0fe1e300-4d29-423c-9130-fa360aae8958/스크린샷_2021-09-25_오후_2.12.49.png)

### 6. 테스트

앱을 테스트하려면 Docker 매핑된 앱 포트를 확인합니다.

```docker
$ docker ps
```

![스크린샷 2021-09-25 오후 2.13.31.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ac2e800d-b397-4c73-a963-d55a29657a57/스크린샷_2021-09-25_오후_2.13.31.png)

Docker가 컨테이너 내의 `8080` 포트를 머신의 `49160` 포트로 매핑한 걸 확인.

![스크린샷 2021-09-25 오전 11.00.36.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4d326452-9924-4e27-a8e3-82160358d1fb/스크린샷_2021-09-25_오전_11.00.36.png)

![스크린샷 2021-09-25 오전 10.59.15.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/52a8cb5f-43dd-4859-a718-ff38e034cd82/스크린샷_2021-09-25_오전_10.59.15.png)

</br>
---

## 여러 이미지를 실행시킬 때는 ?

- Docker Compose.yaml 파일 구성하여 이미지들의 구동 순서, 구동환경을 설정할 수 있다.
- ex ) 만약 Front, Back, DB 구성된 프로그램을 이미지 생성 후 동시에 실행시킬 경우

```docker
version: '3'
services:
  database:
    # Dockerfile이 있는 위치
    build: ./database
    # 내부에서 개방할 포트 : 외부에서 접근할 포트
    ports:
      - "3306:3306"
  backend:
    build: ./backend
    # 연결할 외부 디렉토리 : 컨테이너 내 디렉토리
    volumes:
      - ./backend:/usr/src/app
    ports:
      - "5000:5000"
    # 환경변수 설정
    environment: 
      - DBHOST=database
  frontend:
    build: ./frontend
    # 연결할 외부 디렉토리 : 컨테이너 내 디렉토리
    volumes:
      - ./frontend:/home/node/app
    ports:
      - "8080:8080"
```
</br>

## 도커가 주목받는 이유

![스크린샷 2021-09-25 오전 11.31.50.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c0297c42-ee25-4960-a3ff-9ed0b29e330d/스크린샷_2021-09-25_오전_11.31.50.png)

### 마이크로 서비스 아키텍처

- 비즈니스 기능마다 서버를 분리
- 분리된 서비스마다 다른 기술 적용 가능
- 서비스가 분리되었기 때문에 개발속도 상승
- 서비스 별 통신 방법이 어렵다.
- 구축이 어렵다.

→ 마이크로 서비스 아키텍처의 **세분화된 서비스**와 **컨테이너의 확장성의 장점**이 맞물리면서 이런 컨테이너들을 쉽게 관리, 배포할 수 있는 Docker가 주목을 받기 시작

</br>
## 결론

도커를 사용하면 기존에 개발자들이 환경 설정으로부터 겪던 고충을 말끔히 해결시켜 준다! 

</br>

---

### 참고자료

[https://docs.docker.com/get-started/overview/](https://docs.docker.com/get-started/overview/)

[https://nodejs.org/ko/docs/guides/nodejs-docker-webapp/](https://nodejs.org/ko/docs/guides/nodejs-docker-webapp/)

[https://subicura.com/2017/01/19/docker-guide-for-beginners-2.html](https://subicura.com/2017/01/19/docker-guide-for-beginners-2.html)

[https://opennote46.tistory.com/207](https://opennote46.tistory.com/207)

[https://www.yalco.kr/36_docker/](https://www.yalco.kr/36_docker/)
