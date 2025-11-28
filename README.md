# 🎰 추첨 프로그램

## 📹 데모

<video width="1200" controls>
  <source src="https://github.com/sanggi-wjg/picker/blob/main/.data/demo.webm" type="video/webm">
  브라우저가 video 태그를 지원하지 않습니다.
</video>


## 🚀 사용 방법

### 1. CSV 파일 준비

다음 형식의 CSV 파일을 준비하세요:

```csv
id,name,mobileNumber
1001,홍길동,010-1234-5678
1002,김철수,010-2345-6789
1003,이영희,010-3456-7890
```

**필수 헤더**: `id`, `name`, `mobileNumber`

### 2. 파일 업로드

1. 브라우저에서 `picker.html` 파일을 엽니다
2. 화면 우상단에 `녹화대기` 버튼을 클릭합니다.
3. "데이터 파일 로드" 버튼을 클릭하여 CSV 파일을 업로드합니다
4. 데이터가 로드되면 SHA-256 해시값이 자동으로 생성됩니다

### 3. 추첨 진행

1. "추첨 시작" 버튼을 클릭합니다
2. 화면 녹화 권한을 허용합니다
3. 슬롯 머신 애니메이션이 시작되고 당첨자가 순차적으로 공개됩니다

### 4. 결과 다운로드

추첨이 완료되면:
- **결과 다운로드**: 당첨자 정보와 로그가 포함된 JSON 파일
- **녹화본 다운로드**: 추첨 과정이 담긴 WebM 영상 파일

## 📋 결과 파일 형식

다운로드되는 JSON 파일에는 다음 정보가 포함됩니다:

```json
{
  "title": "추첨 결과 보고서",
  "drawInfo": {
    "timestamp": "2025-11-27 19:00:00",
    "totalCandidates": 100,
    "drawCount": 2,
    "algorithm": "CSPRNG"
  },
  "dataIntegrity": {
    "hashAlgorithm": "SHA-256",
    "dataHash": "abc123..."
  },
  "winners": [
    {
      "position": "1번 당첨자",
      "id": "1001",
      "name": "홍길동",
      "mobileNumber": "010-1234-5678"
    }
  ],
  "logs": [...]
}
```

## 🔍 개인정보 마스킹 규칙

화면에 표시될 때:
- **이름**: `홍길동` → `홍*동`
- **ID**: `1001234` → `1001***`
- **전화번호**: `010-1234-5678` → `010-****-5678`
