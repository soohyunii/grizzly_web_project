# grizzly_web_project
- 프로젝트에 contribute 하기위해서 project owner 가 contributor 로 추가해줘야한다.
- 추가하려는 email 은 개인 profile > setting 에서 email 을 공개해줘야한다.


## git config
1. 로컬에서 프로젝트를 다운받으려는 폴더로 이동
```
$ cd {path}
```
2. git init 설정
```
git init
```
3. git global 설정
```
$ git config --global user.name {username}
$ git config --global user.email {email}
```
4. 프로젝트 clone
```
$ git clone https://github.com/soohyunii/grizzly_web_project.git
```
5. 프로젝트의 push url 설정 
```
- 프로젝트 push 는 fork 된 프로젝트로 (ex) 개인 브랜치/grizzly_web_project
- merge request 는 본 프로젝트로 (ex) 로컬/grizzly_web_project
$ git remote set-url --push origin https://github.com/soohyunii/grizzly_web_project.git
```
5. remote 경로가 다음과 같으면 정상적으로 remote 가 설정된 것
```
- push url 은 fork 된 프로젝트
- fetch(pull) url 은 본 프로젝트

$ git remote -v
origin	git@github.com:개인브랜치/grizzly_web_project.git (fetch)
origin	git@github.com:로컬/grizzly_web_project.git (push)
```
6. 다운받은 프로젝트 폴더로 이동
```
$ cd grizzly_web_project
```

## project push 정책
1. 모든 contributor 는 로컬에서 개인 branch 를 따서 작업한다.
- Merge request 는 fork 한 repository 에 새로운 브랜치를 따서 등록한다.

$ git branch
$ git branch {작업브랜치명}


### =======================이하는 추후에==========================
***현재는 아직 웹사이트를 통합하지 않았기 때문에 각자의 개인 branch에서 계속 작업을 수행하는 것을 권장합니다. 
(웹사이트 경로 및 기능 통합을 한 후에 아래 작업을 하도록 권장합니다)***

2. push 하기 전에는 항상 로컬 master branch 로 이동해 최신분을 pull 받고, push 하려는 branch 를 최신 상태로 만들어준다.
```
$ git checkout master
$ git pull
$ git checkout {작업브랜치명} (자기 현재 작업중 브랜치)
$ git rebase master
```
3. remote 프로젝트로 push 한다. (remote 프로젝트의 master 브랜치가 아닌 다른 브랜치로 push)
** 여기서 로컬프로젝트로 push 하지 않도록 한다**
```
$ git add .
$ git commit -am "{작업내용}"
$ git push origin {작업브랜치명}
```
4. [soohyunii/grizzly_web_project](https://github.com/soohyunii/grizzly_web_project.git)에서 "pull Request" 를 생성한다.
- pull Request 의 commit message 를 통해 어떤 이슈에대한 내용을 해결했는지에 대한 태깅을 해준다. ex) resolve #{이슈번호} {커밋내용}
**여기서 #을 붙이면 자동으로 이슈번호가 매겨지므로 이슈번호는 할 필요없음

5. 프로젝트 owner(현재 soohyunii) 가 request 를 확인해 push 한 내용을 머지해준다.
6. Merge request 이후 머지된 브랜치는 가능한 삭제하고, 새로운 브랜치를 따서 새로운 작업을 진행할 수 있도록 한다.
```
$ git checkout master
$ git pull
$ git branch -D {작업브랜치명}
$ git checkout -b {새로운브랜치명}
```
- 브랜치를 제거한 경우 로컬에서 트래킹 중인 remote 브랜치 정보를 제거해 준다.
```
# 트래킹 중인 remote branch 가 있는 경우 서버에서 삭제되면 로컬에서도 리모트 브랜치 정보가 삭제됨.
$ git fetch -p
```



 



