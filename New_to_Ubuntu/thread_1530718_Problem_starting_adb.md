---
title: "Problem starting adb"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by slughappy1 on 2010-07-14
I am currently trying to run adb, to root my android phone, in Linux Mint 64bit. When I was running Ubuntu 64bit I was able to get adb started with no problem. No matter what I do I can't get it started. It says there is no file or directory. I tried on their forums, but got no response all day and now it's down.

---

### Post by ptviperz on 2010-07-14
Can't you just

```
sudo ./adb start-server
```

That's how it works on my machine

---

### Post by slughappy1 on 2010-07-14
Nope
```
jason@jason-laptop ~ $ cd Desktop/MyTouch\ Slide/SimpleRoot-v1.3-Linux/
jason@jason-laptop ~/Desktop/MyTouch Slide/SimpleRoot-v1.3-Linux $ ls
adb  donate.htm  loop.sh  ota.zip  pause  README  rootme  rootme2  update.zip
jason@jason-laptop ~/Desktop/MyTouch Slide/SimpleRoot-v1.3-Linux $ sudo ./adb start-server
sudo: unable to execute ./adb: No such file or directory
jason@jason-laptop ~/Desktop/MyTouch Slide/SimpleRoot-v1.3-Linux $ cd /usr/local/bin/
jason@jason-laptop /usr/local/bin $ ls
adb  apt  highlight  mint-md5sum  search
jason@jason-laptop /usr/local/bin $ sudo ./adb start-server
sudo: unable to execute ./adb: No such file or directory
jason@jason-laptop /usr/local/bin $ 

```

---

