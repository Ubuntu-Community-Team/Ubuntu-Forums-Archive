---
title: "bluetooth-alsa package is missing"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by lavadisco on 2009-01-14
I'm trying to follow these instructions:

[http://www.board4all.cz/showthread.php?t=134759](http://www.board4all.cz/showthread.php?t=134759)

But when I attempt to install bluetooth-alsa as instructed in the first step, I get:

```
lavadisco@lavadisco:~$ sudo apt-get install bluetooth-alsa
[sudo] password for lavadisco: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bluetooth-alsa

```

I am nearly 100% positive that all my repositories are updated. Anybody know what I'm doing wrong?

---

### Post by utnubuuser on 2009-01-15
Is it "bluez-alsa" intead of "bluetooth-alsa"  -- It's audio support for bluetooth right?  "Try sudo apt-get intall bluez-alsa".

---

### Post by lavadisco on 2009-01-15
Hey, that was it, thanks!

---

