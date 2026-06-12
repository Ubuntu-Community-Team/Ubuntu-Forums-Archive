---
title: "Wine installation failed  on maverick 64bit"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by cakerapujangga on 2010-10-15
I just fresh install ubuntu 10.10 Maverick Meerkat 64 bit. But when I'm going to install wine it failed. After I inserted ```
sudo apt-get install wine
```
and accept it by insert y,it comes the error:
```
After this operation, 263MB of additional disk space will be used.
Do you want to continue [Y/n]? y 
Err http://my.archive.ubuntu.com/ubuntu/ maverick/universe ia32-libs amd64 20090808ubuntu8
  404  Not Found
Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_20090808ubuntu8_amd64.deb  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```
Someone can help me?

---

### Post by sandyd on 2010-10-15
> **cakerapujangga said:**
> I just fresh install ubuntu 10.10 Maverick Meerkat 64 bit. But when I'm going to install wine it failed. After I inserted ```
sudo apt-get install wine
```and accept it by insert y,it comes the error:
```
After this operation, 263MB of additional disk space will be used.
Do you want to continue [Y/n]? y 
Err http://my.archive.ubuntu.com/ubuntu/ maverick/universe ia32-libs amd64 20090808ubuntu8
  404  Not Found
Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_20090808ubuntu8_amd64.deb  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```Someone can help me?
do what it says
```

sudo apt-get update
sudo apt-get install wine
```

you might also want to look into the WINE dev ppa. the developmental versions of WINE run much better than the current version in the repos. the only downside is that occasionally, the developmental versions will break something. ([https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa))

---

### Post by cakerapujangga on 2010-10-15
> **sandyd said:**
> do what it says
```

sudo apt-get update
sudo apt-get install wine
```

you might also want to look into the WINE dev ppa. the developmental versions of WINE run much better than the current version in the repos. the only downside is that occasionally, the developmental versions will break something. ([https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa))

I've done it several times and the same error happens. The same error also happen when I trying to install it in Software center and Ubuntu Tweak. I'll try the dev version now.

---

### Post by cakerapujangga on 2010-10-15
Unfortunately,after trying to install wine 1.3 ```
sudo apt-get install wine1.3
```
 same error happens.

---

### Post by sandyd on 2010-10-15
> **cakerapujangga said:**
> Unfortunately,after trying to install wine 1.3 ```
sudo apt-get install wine1.3
``` same error happens.

go to system -> administration -> software sources
change server to "main server"

the other servers sometimes get out of sync

---

### Post by cakerapujangga on 2010-10-15
> **sandyd said:**
> go to system -> administration -> software sources
change server to "main server"

the other servers sometimes get out of sync

Thank you! it works, but I change the server through synaptic package manager because I cannot find the Software Source in administration menu. Thanks a lot..

---

