# 수입검사 시트 생성기

FRA 캡처 + DEBREX 화면 사진으로 수입검사성적서(엑셀)를 만드는 정적 웹페이지입니다. 서버 없이 `index.html` 하나와 `ocr/` 폴더만 있으면 동작합니다.

- 양식 탭: 동일기연 (100) / 어쿠스틱웍스 (100) / 어쿠스틱웍스 (100M) (양식 엑셀은 index.html 안에 내장, 100M은 화면이 달라 읽는 방식도 따로)
- 사진 값 읽기: 브라우저 글자 인식(Tesseract) + 학습한 숫자 모양 검증
- 엑셀 다운로드: 브라우저 기본 다운로드

## GitHub Pages로 올리기

1. GitHub에서 새 저장소(repository)를 만든다.
2. 이 폴더 안의 파일 전부(`index.html`, `ocr/`, `.nojekyll`, `README.md`)를 저장소 맨 위(루트)에 올린다.
   - 웹에서는 "Add file → Upload files"로 `ocr` 폴더째 끌어놓으면 된다. 파일 하나가 4.8MB라 웹 업로드 한도(25MB 이하)는 문제없다.
3. 저장소 Settings → Pages → Source를 "Deploy from a branch", Branch를 `main` / `(root)`로 두고 Save.
4. 1~2분 뒤 `https://<계정>.github.io/<저장소이름>/` 주소로 열린다.

## 주의

- 무료 GitHub Pages는 저장소가 공개(public)여야 하며, 그러면 검사성적서 양식(로고 포함)과 학습 데이터가 누구에게나 보입니다. 사내 자료라면 회사 기준으로 먼저 확인하세요. 접근 제한이 필요하면 Cloudflare Pages(Access)나 사내 서버를 쓰세요.
- 처음 쓸 때 글자 인식 엔진(약 11MB)을 내려받느라 조금 걸릴 수 있습니다.
- 이 페이지는 jszip(cdnjs)와 Google Fonts를 인터넷에서 불러옵니다. 사내망이 이를 막으면 jszip.min.js를 같은 폴더에 두고 index.html의 주소를 바꿔야 합니다.
