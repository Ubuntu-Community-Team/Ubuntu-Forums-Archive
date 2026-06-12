---
title: "please help!!!desktop wont load after login"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by paristhadon on 2009-01-20
the last time i tried to install some software (did not work) it had me change the init level from 3 to 5... i think, but i tried for hours and gave up. i just recently wanted to give it another try and after i login...the screen just shows the mouse pointer and sits there. i went to recovery and back through my history to see what iwas doing and tried to reverse it but im stuck. please help. ubuntu 7.10 if that helps

---

### Post by blueridgedog on 2009-01-20
Well, I am not certain it will help, but it you changed the init level, you can press ctr+alt+F2, login and then

```
sudo telinit 2
```

You can get back to X with ctr+alt+F7

---

### Post by gettinoriginal on 2009-01-20
Try this:  :p

Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

---

### Post by paristhadon on 2009-01-21
Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter


when i enter recovery mode i dont get the Repair Broken Packages...please explain.

 i really appreciate the help

---

### Post by gettinoriginal on 2009-01-21
hmmmmmmm, don't know why you don't have that option, but sorry I don't know how to add it :(

---

### Post by sleepyjon on 2009-01-21
> **gettinoriginal said:**
> hmmmmmmm, don't know why you don't have that option, but sorry I don't know how to add it :(

I think the menu may have been added in 8.04. Recovery used to just drop you into a root terminal.

OP: Do you just get a terminal? 

If so, try:

```

dpkg --configure -a

```

---

### Post by paristhadon on 2009-01-22
thank you!!!!!!!!!! sleepyjon im back!!! you are the man thanks...but since im still learning, can you explain the command. it was perfect like nothing ever happened. it did create a new entry in my grub menu which i can correct..and it said "setting up" to all of the features and functions in my version of ubuntu (7.10). AGAIN THANK YOU...  oh  and if you have time can you tell me what i did...i know i was messing with the run levels to try and install some video drivers. :(

---

### Post by sleepyjon on 2009-01-22
Oh, sorry, I meant to put the explanation. 

dpkg --configure -a

That dpkg is the debian package manager, --configure tells it to configure packages that were downloaded but not fully installed, -a tells it to do all of the packages.

Here's some reading that explains it much better than I can:

[http://en.wikipedia.org/wiki/Dpkg](http://en.wikipedia.org/wiki/Dpkg)
[http://www.debian.org/doc/FAQ/ch-pkgtools.en.html](http://www.debian.org/doc/FAQ/ch-pkgtools.en.html)
[http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/dpkg.8.gz](http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/dpkg.8.gz)

Glad it's all fixed for you!

---

### Post by paristhadon on 2009-01-23
THANKS AGAIN AND THANKSFOR THE LINKS....it acually works better than it was working...cause all this started while was trying to install video driver my package manager was not working...now it is thanks!!

---

