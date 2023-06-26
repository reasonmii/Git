### Main code

- git으로 push 할 폴더에서 `git init`

```
git fetch
git switch branch-name

git add --all
git commit -m "commit message"
git remote add origin "원격저장소 https"
git push origin main
git push -f origin main
```

### Git, Github, Git Immersion
- github is where you can collaborate with others

<b>git commit message convention</b>
- 기본 구성 : type:subject, body, footer
- type
  - feat : 새로운 기능 추가
  - fix : 버그 수정
  - docs : 문서 수정
  - style : code formatting, semicolon 누락, 코드 변경이 없는 경우
  - refactor : refactoring production code
    - ※ refactoring : 결과의 변경 없이 코드 구조 재조정함 (가독성↑, 유지보수 굿)
  - test : adding/refactoring test code (no production code change)
  - chore : updating build tasks, package manager configs (no production code change)
- subject : 50자 내, 마침표X, 현재시제 사용, 명령어로 작성
- body (optional)
  - commit 부연설명
  - 72자 내, 제목과 구분하여 한 칸 띄어 작성
- footer (optional)
  - issue tracker id 작성할 때 사용

<b>git commit으로 issue 종료하기</b>
- commit message에 종료 keyword, issue no. 기입하면 push 할 때 해당 이슈 자동으로 종료 처리
- 종료 keyword : close, closes, closed, fix, fixes, fixed, resolve, resolves, resolved
- ex) `git commit -m "fixed XSS Vulnerability - #20"`
- 여러 개 이슈 모두 종료하기 : `git commit -m "fixed XSS Vulnerability - #20", #21, #23`
- 다른 repository의 이슈 종료하기 : `git commit -m "close issue #21 #22 and [other_repo_path]#10"`

<b>.gitignore</b>
- git push 하고 싶지 않은 파일명들 입력
- 작업 중인 파일을 전부 github에 업로드 하면 용량이 크니, 특정 파일들은 업로드 하지 않기 위함

<b>issue</b>
- issue : 추가/개선사항, 버그 등 모든 것
  - 모든 활동 내역에 대해 이슈 등록, 이를 기반으로 작업 진행
  - `@이름`을 통해 특정 인물 호출 가능
- issue template : 자주 사용하는 template은 등록하고 사용하는 것이 효율적
- issue 작업
  - Assignees : 해당 작업의 담당자
  - Labels: 해당 작업의 성격 ex) enhancement
  - Milestone: 해당 작업이 속한 파트
    - ex) 새로운 버전 (1.0.0) 출시 시 추가된 모든 이슈를 Version 1.0.0 Milestone에 추가하면 Version 1.0.0에 대한 전체적인 상황을 한눈에 볼 수 있음
- issue 기반 branch 생성
  - branch naming의 한계 : 작업 의도를 모두 담기 어려움 + 동료 개발자들의 업무를 유추하기 어려움
  - → 'issue number' 기반으로 branch 생성하면 명확해짐
    - 각 github issue는 unique한 issue number 갖고, 이를 기반으로 branch 이름 생성하여, branch가 명확한 작업 의도를 갖게 할 수 있음
- github pull request (pr)
  - reviewers 지정 (교수님, 다른 담당자 등)
  - description 작성
    - keyword: #issueNo.
    - [ ] blabla1
    - [x] blabla2
    - [ ] blabla3
  - keyword 예시
    - issue : 아직 issue인 상태
    - resolved : 해당 pull request가 master branch에 반영되면 자동으로 close
  - pull request가 생성되면 새로운 issue number 생성됨 = pull request도 issue의 일종
  - ★ 반드시 해당 pull request가 어떤 issue에 따른 요청인지 명시하는 것 권장
    - #2[pull request]가 연결되어 해당 issue가 어떤 code 때문에 진행됐는지 추적하기 좋음
  - code review : Approve (승인), Comment (간단한 피드백 제출), Request changes (코드 수정 요구)
  - approve 후 `merge pull request` 버튼을 통해 pull request 반영
    - 완료 후 해당 branch가 더 필요 없으면 delete branch (remote branch 삭제됨)

<b>Gists</b>
- Github Gists are a simple way to share code snippets and useful fragments with others
- Gists are much easier to create, but offer far fewer features than a typical Github repository
