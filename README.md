# Hello Serverless

## 1. Getting Started

첫 번째 프로젝트를 만들려면 아래 명령어를 실행하고 프롬프트에 따라 진행하세요.

```
serverless
```

위 명령어를 실행하면 Serverless Framework CLI가 실행됩니다. 이제, 다음과 같은 프롬프트가 나타납니다.

```
No project detected. Do you want to create a new one? Yes
```

여기서 `Yes`를 입력하면 새로운 프로젝트를 생성할 수 있습니다. 이제 프로젝트의 이름과 AWS 계정의 자격증명을 입력합니다.

```
Enter a name for your new project: my-first-serverless-project
Enter your AWS Access Key ID: [hidden]
Enter your AWS Secret Access Key: [hidden]
Enter your AWS region: us-west-2
```

위와 같이 프로젝트 이름, AWS Access Key ID, AWS Secret Access Key, AWS region을 입력하고 엔터 키를 누르면, Serverless Framework CLI가 새로운 프로젝트를 생성합니다.

새로운 프로젝트가 생성되면, `handler.js` 파일이 생성됩니다. 이 파일에 AWS Lambda 함수의 코드를 작성할 수 있습니다.

### Deploy

serverless 명령어 내에서 아직 수행하지 않았다면, 아래 명령어를 실행하여 프로젝트를 배포할 수 있습니다.

```
serverless deploy
```

위 명령어를 실행하면 Serverless Framework CLI가 현재 디렉토리의 Serverless 프로젝트를 패키징하고 AWS 계정에 배포합니다. 배포가 완료되면, 배포된 서버리스 애플리케이션의 엔드포인트 URL이 출력됩니다.

또한, 배포된 AWS Lambda 함수의 ARN(Amazon Resource Name)도 출력됩니다. 이 ARN은 다른 AWS 서비스와의 연동에 사용될 수 있습니다.

### Invoke function

API를 배포했다면, 해당 API의 URL에 쿼리를 보내면 관련된 AWS Lambda 함수가 트리거됩니다. 해당 URL은 serverless deploy 출력에서 찾거나, 나중에 serverless info를 통해 검색할 수 있습니다.

URL을 노출하지 않고 배포한 함수를 호출하려면 다음 명령어를 사용할 수 있습니다.

```
serverless invoke -f function-name
```

위 명령어에서 `function-name`은 호출하려는 함수의 이름으로 바꿔주어야 합니다. 예를 들어, `hello`라는 함수를 호출하려면 아래와 같이 입력합니다.

```
serverless invoke -f hello
```

위 명령어를 실행하면 `hello` 함수가 호출되고, 함수가 반환하는 결과를 출력합니다.

### Fetching function logs

함수 호출에 의해 생성된 모든 로그는 자동으로 AWS CloudWatch에 저장됩니다. CLI에서 이러한 로그를 검색하려면 다음 명령어를 사용할 수 있습니다.

```
serverless logs -f function-name
```

위 명령어에서 `function-name`은 로그를 가져올 함수의 이름으로 바꿔주어야 합니다. 예를 들어, `hello`라는 함수의 로그를 가져오려면 아래와 같이 입력합니다.

```
serverless logs -f hello
```

위 명령어를 실행하면 `hello` 함수에서 생성된 로그가 출력됩니다.

### Remove your service

서비스를 삭제하려면, `serverless remove` 명령어를 실행합니다. 이 명령어는 프로젝트에서 생성된 모든 AWS 리소스를 삭제하며 예상치 못한 요금이 발생하지 않도록 합니다. 또한, 이 명령어를 실행하면 Serverless 대시보드에서 해당 서비스가 삭제됩니다.