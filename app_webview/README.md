# SafetyFam App WebView

자녀 안전 관리 서비스 **SafetyFam**의 모바일 WebView 기반 UI 프로젝트입니다.

## 개요

부모(보호자)와 자녀(아동)가 각각 다른 화면을 사용하는 하이브리드 모바일 앱의 웹뷰 UI입니다. 순수 HTML/CSS/JavaScript로 구성된 정적 웹 페이지이며, 네이티브 앱 내 WebView로 렌더링됩니다.

## 주요 기능

- **실시간 위치 추적** - 자녀의 현재 위치 및 이동 경로 확인, 안심존 이탈 알림
- **긴급 통화** - 부모가 자녀에게 긴급 전화 연결, 자녀가 SOS 긴급 알림 전송
- **채팅 가드** - 유해 메시지 탐지 및 키워드 필터링 (폭력, 음란물 등)
- **자녀 관리** - 초대 코드 기반 자녀 등록, 복수 자녀 계정 관리
- **알림 관리** - 알림 히스토리, 푸시/SMS 설정
- **고객 서비스** - 공지사항, FAQ, 이용 가이드
- **다국어 지원** - 한국어 / 영어

## 프로젝트 구조

```
app_webview/
├── index.html                    # 메인 진입점 (언어/역할 선택)
├── css/
│   ├── safetyfam_app.css        # 메인 스타일시트
│   ├── reset.css                 # CSS 초기화
│   ├── slick.css                 # 슬라이드 컴포넌트 스타일
│   ├── intlTelInput.css          # 국제 전화번호 입력 스타일
│   └── intlTelInput_custom.css   # 전화번호 입력 커스텀 스타일
├── js/
│   ├── utils.js                  # 전화번호 유효성 검사 (libphonenumber)
│   ├── temp.js                   # 샘플/임시 구현 스크립트
│   ├── slick.js / slick.min.js   # 캐러셀/슬라이더 라이브러리
│   └── intlTelInput.min.js       # 국제 전화번호 입력 UI
├── html/                         # 부모(보호자) 화면 (약 50개)
│   ├── 00_FRCM/                  # 알림/공지
│   ├── 01_FRIN/                  # 서비스 소개/온보딩
│   ├── 02_FRJO/                  # 회원가입 플로우
│   ├── 04_FRHO/                  # 홈 대시보드
│   ├── 06_FRMM/                  # 채팅 가드 (메시지 모니터링)
│   ├── 07_FRSE/                  # 설정
│   ├── 08_FRCS/                  # 고객센터
│   └── 99_sample/                # 샘플/테스트 페이지
├── html_child/                   # 자녀(아동) 화면 (약 15개)
│   ├── 00_FRCM/                  # 알림
│   ├── 01_FRIN/                  # 초대 코드 확인
│   └── 04_FRHO/                  # 홈 (SOS 기능 포함)
└── images/
    ├── common/                   # 공통 아이콘 (뒤로가기, 홈, 알림 등)
    ├── home/                     # 홈 화면 그래픽
    └── temp/                     # 임시/샘플 이미지
```

## 화면 코드 체계

각 HTML 파일은 `FR + 화면코드 + 순번` 형식으로 명명됩니다.

| 코드 | 설명 |
|------|------|
| FRCM | 알림/공지 (Notification/CM) |
| FRIN | 서비스 소개/온보딩 (Introduction) |
| FRJO | 회원가입 (Join) |
| FRHO | 홈 대시보드 (Home) |
| FRCL | 자녀 위치 관리 (Child Location) |
| FRMM | 채팅 가드 (Message Monitoring) |
| FRSE | 설정 (Settings) |
| FRCS | 고객센터 (Customer Service) |

## 기술 스택

| 분류 | 기술 |
|------|------|
| 마크업 | HTML5 |
| 스타일 | CSS3 (CSS Variables, Flexbox) |
| 스크립트 | Vanilla JavaScript (ES6) |
| 폰트 | Google Fonts - Noto Sans KR |
| 라이브러리 | Slick (캐러셀), libphonenumber, intlTelInput |
| 최적화 | 모바일 퍼스트, 최대 너비 720px |

## 사용자 역할

- **부모(보호자)**: `html/` 디렉토리 — 자녀 위치 확인, 채팅 가드, 설정 등 전체 기능
- **자녀(아동)**: `html_child/` 디렉토리 — SOS 버튼, 알림 수신 등 간소화된 화면

## 개발 환경

별도의 빌드 도구 없이 실행 가능한 정적 프로젝트입니다. 브라우저에서 직접 HTML 파일을 열거나 간단한 로컬 서버로 확인할 수 있습니다.

```bash
# Python으로 로컬 서버 실행
python3 -m http.server 8080
```

## 파일 현황

- HTML 파일: 약 65개 (부모 50 + 자녀 15)
- CSS 파일: 5개
- JavaScript 파일: 5개
- 이미지 파일: 70개 이상
