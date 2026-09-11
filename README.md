# My Web Page with CSS & Bootstrap

HTML 문서의 기본 구조 및 CSS 역할을 이해하고, 동일한 HTML에 서로 다른 CSS를 적용해보며, Bootstrap 프레임워크로 웹페이지를 제작한 프로젝트입니다. (학번: 22300330 / 이름: 박찬)

## 배포 URL

- Vercel 배포: https://2026-oss-assign02-eight.vercel.app/
- index.html: https://2026-oss-assign02-eight.vercel.app/
- nostyle.html: https://2026-oss-assign02-eight.vercel.app/nostyle.html
- style1.html: https://2026-oss-assign02-eight.vercel.app/style1.html
- style2.html: https://2026-oss-assign02-eight.vercel.app/style2.html
- bootstrap_ex.html: https://2026-oss-assign02-eight.vercel.app/bootstrap_ex.html

## 페이지 설명

| 파일 | 설명 |
|---|---|
| `index.html` | 전체 페이지로 이동할 수 있는 링크 모음 (홈 역할) |
| `nostyle.html` | W3Schools CSS Demo(No Style 버전)를 참고한, CSS 없이 HTML 구조만으로 작성한 기본 페이지 |
| `style1.html` | `nostyle.html`과 동일한 HTML에 W3Schools Stylesheet 1을 참고하여 Internal CSS를 적용한 페이지 |
| `style2.html` | `nostyle.html`과 동일한 HTML에 W3Schools Stylesheet 4(다크 테마)를 참고하여 Internal CSS를 적용한 페이지 |
| `bootstrap_ex.html` | Bootstrap 공식 예제(Album)를 참고하여 CDN으로 Bootstrap을 불러와 구현한 페이지 |

## Development Flow

VS Code에서 코드 작성 → Git commit → GitHub push → Vercel이 push를 감지해 자동 배포 → 배포된 URL 접속 확인

## Weekly Review – Week 2

### Key Learning
1. HTML은 페이지의 구조와 내용을, CSS는 그 위에 입히는 디자인을 담당하며, 동일한 HTML이라도 CSS만 바꾸면 완전히 다른 화면이 나온다는 것을 직접 확인했다.
2. `display: flex`를 이용한 레이아웃 구성법(`gap`, `flex: 1`, `flex-shrink: 0`, `margin: auto`로 요소를 특정 방향으로 밀어내는 방법 등)을 배웠다.
3. Bootstrap처럼 외부 CSS 프레임워크를 CDN으로 불러와 미리 정의된 class만으로 디자인을 적용하는 방법을 배웠다.

### HTML vs CSS
html은 브라우저로 보여줄 정보들의 구조를 일관성있게 보여주는 정보글이다.
css는 그 정보들을 브라우저에서 어떤식으로 보여줄지를 정하는 구조 방법이다.

### Bootstrap 사용법
Bootstrap은 이미 만들어진 CSS 클래스(`btn`, `card`, `navbar`, `container`, `row`/`col` 등)를 모아둔 라이브러리로, 직접 CSS를 작성하지 않고도 class 이름만 붙이면 정돈된 디자인을 빠르게 적용할 수 있어서 사용한다. 사용법은 `<head>`에 Bootstrap CSS CDN `<link>`를, `</body>` 직전에 Bootstrap JS CDN `<script>`를 추가한 뒤, 공식 예제 페이지의 class 구조를 참고해 필요한 부분만 가져와 내용을 수정하는 방식으로 활용했다.

### Problem & Solution
- **문제**: Bootstrap 공식 예제 페이지의 소스를 그대로 복사해서 붙여넣었는데, 스타일이 전혀 적용되지 않고 꾸밈없는 화면으로 나왔다.
- **원인**: 예제 페이지의 `<link>`, `<script>` 경로가 `/docs/5.3/dist/css/bootstrap.min.css`처럼 Bootstrap 공식 사이트 서버 기준의 상대경로로 되어 있어서, 내 컴퓨터의 파일에서는 해당 경로에 파일이 존재하지 않아 CSS/JS를 불러오지 못했기 때문이었다.
- **해결**: 상대경로 대신 어디서든 접근 가능한 jsDelivr CDN의 완전한 URL(`https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/...`)로 교체하여 해결했다.

### AI Usage
Claude를 활용해 HTML/CSS 개념(선택자, 박스 모델, flex 레이아웃) 설명을 듣고, 직접 작성한 CSS가 의도대로 적용되지 않을 때 원인을 진단받는 방식으로 사용했다. 코드를 대신 작성해달라고 요청하기보다는, 스크린샷을 보여주며 "왜 이렇게 렌더링되는지"를 질문하고 원인을 파악한 뒤 직접 코드를 수정했으며, 수정 후 다시 스크린샷으로 결과를 확인하는 과정을 반복했다. Bootstrap 예제를 가져오는 과정에서도 AI가 제안한 CDN 경로가 실제로 유효한 파일인지 브라우저 주소창에 직접 입력해 확인하는 방식으로 검증했다.

### Reflection
CSS의 `<style>` 태그가 `<head>`에 위치해야 하는 이유가 단순히 관례가 아니라, 브라우저가 HTML을 위에서 아래로 읽으며 렌더링하기 때문에 스타일 규칙을 콘텐츠보다 먼저 읽어야 화면이 깜빡이지 않는다는 실질적인 이유가 있다는 걸 알게 되었다. 또한 CSS의 class/id 선택자와 HTML의 class/id 속성이 완전히 다른 문법 규칙(`#`/`.`은 CSS에서만 붙임)이라는 점을 명확히 이해하게 되었다.
