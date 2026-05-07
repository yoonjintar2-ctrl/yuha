# 🍼 유하의 이유식 플랜 (Yuha's Iyusik Plan)

PC와 모바일에서 모두 잘 보이는, 가벼운 단일 HTML 기반의 이유식 캘린더입니다.
GitHub Pages에 그대로 올려서 배포할 수 있도록 구성되어 있어요.

---

## ✨ 주요 기능

- 4주(28일) 단위의 **가족 공유용 이유식 달력**
- 한 끼니마다 **미음 / 고기 / 채소 / 생선 / 과일 / 알레르기 / 메모** 입력
- 기본 카테고리에 없는 항목은 **+ 추가** 버튼으로 직접 등록 가능
- D+일수, 이유식 시작 D+, 메모장, 날씨/미세먼지, 월령별 팁
- **GitHub에 JSON으로 저장** → 다른 가족도 같은 페이지에서 동일한 데이터 확인
- 수정 모드 비밀번호 잠금 (기본값: `y0310402`, 코드 내 `PASSWORD` 상수에서 변경)
- 인쇄 보기 지원

---

## 🚀 GitHub Pages 배포 방법

### 1) 새 리포지토리 만들기
- GitHub에서 `yuha-plan` 같은 이름으로 **Public** 리포지토리 생성

### 2) 파일 업로드
이 폴더의 파일을 그대로 업로드합니다.
- `index.html`
- `README.md`
- `.nojekyll` (점으로 시작하는 파일이라 일부 환경에서 안 보일 수 있어요)

> 끌어서 놓기로 업로드할 때 `.nojekyll`이 누락되면, 리포지토리 페이지에서
> **Add file → Create new file**로 직접 만들어 주세요. (내용은 비워둬도 됩니다.)

### 3) Pages 활성화
- 리포지토리 → **Settings → Pages**
- Source: **Deploy from a branch**
- Branch: **main** / **(root)** 선택 후 저장
- 1~2분 후 `https://<username>.github.io/<repo>/` 주소가 활성화됩니다.

### 4) 데이터 동기화 (가족 공유)
1. GitHub → Settings → Developer settings → **Personal access tokens (classic)**
2. **Generate new token (classic)** → `repo` 권한만 체크 → 토큰 복사
3. 사이트 우측 상단 **⚙️ 설정** → GitHub 저장 설정 입력:
   - Personal Access Token: `ghp_xxxxxxxxxxxx`
   - 저장소: `username/yuha-plan`
   - 저장 파일 경로: `yuha-iyusik.json` (그대로 두면 됨)
4. **🔓 수정** 버튼으로 잠금 해제 → 입력 후 **💾 저장**
5. 다른 사람이 같은 URL을 열면 GitHub에 저장된 데이터가 자동으로 로드돼요.

> 토큰은 **본인이 사용하는 기기의 브라우저에만** 저장됩니다.
> 다른 가족은 토큰 없이 **읽기 전용**으로 데이터를 볼 수 있어요.

---

## 🔐 비밀번호 변경

`index.html` 상단 스크립트의 다음 줄을 원하는 값으로 변경:

```js
const PASSWORD = 'y0310402';
```

---

## 📁 폴더 구조

```
yuha-plan/
├── index.html       # 본체 (HTML/CSS/JS 한 파일)
├── README.md        # 이 문서
└── .nojekyll        # GitHub Pages가 Jekyll 처리하지 않게 하는 마커
```

---

## 📝 추가/제거된 카테고리 메모

- 🥩 고기, 🥕 채소, 🐟 생선, 🍎 과일 — 모두 동일한 패턴 (그리드 + 추가 버튼 + 총량 g)
- 기존 데이터 호환을 위해 옛 `meat:[{type, grams}]` 형식도 그대로 읽을 수 있어요.
