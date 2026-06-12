---
title: "Make error - /usr/bin/ld: cannot find -lglut"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by lol768 on 2010-11-13
**Edit: Fixed the issue (See below)**
Hi,

I'm trying to compile some code ([http://www.erinacom.de/download](http://www.erinacom.de/download), it is an alpha version of extreme tux racer) and I have installed about 5 dependencies but I am now getting this error:

```
/usr/bin/ld: cannot find -lglut
collect2: ld returned 1 exit status
make: *** [etr] Error 1
```I am unsure as to what this means. I have only compiled code a few times on ubuntu so please explain to me as simply as possible :).

Any help would be greatly appreciated.


[U][B]Solution:
[/B][/U][B]For those who are interested:
[/B]```
 sudo apt-get install freeglut3-dev
```[B]Type the above command in the terminal to install glut (free version)
[/B]

---

