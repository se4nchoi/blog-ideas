# 에러해결기 - Proxy

회사 iMac에서 작업하다가, 다른 동료분이 만든 새 repo 를 클론 받으려 했는데...

`github.com` 을 찾을 수가 없다고 한다.

구글링 해보니... [여기](https://stackoverflow.com/questions/20370294/git-could-not-resolve-host-github-com-error-while-cloning-remote-repository-in)에서 츄라이 해볼 솔루션 발견.

```console
git config --global --unset http.proxy
git config --global --unset https.proxy

git clone https://github.com/~/~
```

성공 !

하지만...

<br><br/>

클론 받고 나서 dev server를 띄우려 install 하니... 이번에는 `npm` 이 에러를 뱉어낸다.

```console
> npm i
npm ERR! code ENOTFOUND
npm ERR! syscall getaddrinfo
npm ERR! errno ENOTFOUND
npm ERR! network request to http://~~ failed, reason: getaddrinfo ENOTFOUND registry.~.~
npm ERR! network This is a problem related to network connectivity.
npm ERR! network In most cases you are behind a proxy or have bad network settings.
npm ERR! network
npm ERR! network If you are behind a proxy, please make sure that the
npm ERR! network 'proxy' config is set properly.  See: 'npm help config'

npm ERR! A complete log of this run can be found in:
npm ERR!     /Users/yehyun/.npm/_logs/2023-01-26T11_09_58_014Z-debug-0.log
```

하지만 이것 또한 구글링을 하니 단번에 솔루션 발견.

`stackoverflow` 는 사랑이다.

```console
> npm config delete proxy
```

proxy 관련해서 뭔가 일어난 것 같지만 따로 설정을 한적이 없고, 어제까지 잘 되었어서 의아하다 생각만 했다. 또 일어나면 그때는 찾아보는 걸로...

끝.
