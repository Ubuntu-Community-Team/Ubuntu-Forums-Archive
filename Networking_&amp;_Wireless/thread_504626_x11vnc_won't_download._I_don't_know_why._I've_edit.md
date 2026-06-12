---
title: "x11vnc won't download. I don't know why. I've edited sources.list already..."
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by Genecks on 2007-07-19
For some odd reason, I can't download x11vnc. I've edited the sources list and whatnot.

ubuntu@ubuntu:~/Desktop/x11vnc-0.9.2$ sudo apt-get install x11vnc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package x11vnc

---

### Post by overdrank on 2007-07-19
> **Genecks said:**
> For some odd reason, I can't download x11vnc. I've edited the sources list and whatnot.

ubuntu@ubuntu:~/Desktop/x11vnc-0.9.2$ sudo apt-get install x11vnc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package x11vnc

Hi I have been searching and I just notice that it looks like you cd to a file in the command line 
```
ubuntu@ubuntu:~/Desktop/x11vnc-0.9.2$ 
```
Did you download the file or are you trying to retrieve it from the repo's? Also what version of ubuntu are you using? I downloaded the x11vnc from the repo's in feisty.

---

