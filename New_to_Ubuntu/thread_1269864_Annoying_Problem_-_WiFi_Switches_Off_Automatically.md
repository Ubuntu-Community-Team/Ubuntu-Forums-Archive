---
title: "Annoying Problem - WiFi Switches Off Automatically"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by gccradioscience on 2009-09-18
When I was surfing the web the security prompt came up and it told me to re-enter in my pass-phrase. But it would not let me connect. All of the sudden the WiFi got disabled.  I had this problem before with Ubuntu 9.04 desktop version, and that is when had to 
install the Remix version.   What I don't like about remix is that when I use Mixx a DJ program to listen to my favorite music the software starts locking up and messes up my soundcard.   Right now I just want to get my WiFi back up and running, but don't know 
how.  When the computer told me that I have updates ready to install, I thought that would fix the WiFi problem, but it didn't.    Can someone help me with this. I would gladly appreciate it and it would make me happy.   Right now I feel like putting Windows XP back 
on my netbook, I cannot ever get WiFi back after I get my recovery CD.  

Adam E.
Virginia Beach, VA

---

### Post by nhasian on 2009-09-18
to help we need to know the output of a few things:

```
lsb_release -a
```
```
uname -a
```
```
lshw -C network

```

correct me if i'm wrong, but did you say in your post that your wifi WAS working and then it STOPPED working after you did the updates?

also can you give us the make/model of your netbook?

---

