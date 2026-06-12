---
title: "Someone please help!"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by Rybandt on 2010-07-01
Okay, so, its been 3 days now, and I can't just get linux working right. First things first. I have a Toshiba Satellite A505-S6033 running a Nvidia GeForce 310M. Through trial and error, I was able to get an install of Ubuntu working. I updated drivers and did updates to my computer... This is where it gets bad. When I rebooted, I would either A) Get stuck on the Ubuntu Splash screen or B) Have a message flashing for about a quarter second in the upper left. Now I held shift and clicked recovery mode, and now I'm in low graphics mode and everything is working. When it doesn't work something says Ehcd_??? Unset after IRQ? I don't know if this is the problem! I'm brand new to linux, but I have installed it for friends on other computers and had it work fine. Whats the problem! I'm here all night, so please, if you can help me fully switch over to linux, that'd be awesome.  And no, I am not partitioned.

---

### Post by realzippy on 2010-07-01
Which ubuntu version do you use?
Tried to install nvidia drivers?If so which one?

BTW,;
HOWTO: Get Ubuntu 10.04 working properly on the Toshiba A505 laptop

[http://ubuntuforums.org/showthread.php?t=1503491](http://ubuntuforums.org/showthread.php?t=1503491)

---

### Post by Rybandt on 2010-07-01
I am using the 10.04 version of ubuntu. And I installed the recommended Nvidia Driver. from System<Admin<Hardware drivers. I have followed that guide and many others to no avail :\ I've done at least 40 installs and this is the furthest I have gotten. I guess that is some form of success. The reason I am persistent is because I know that when this is all fixed, there is such a reward in the end for me!

---

### Post by realzippy on 2010-07-01
Did you run a kernel update before things got wrong?

```
uname -r
```

---

### Post by Rybandt on 2010-07-01
Code:
2.6.32-22-generic


Thats what I got.

Edit: Also, this is not the guide I thought this was. This looks promising but time consuming. I'll keep everyone in the know.

---

### Post by realzippy on 2010-07-01
*The Easy Way - Installing kernel 2.6.35-rc1*
from the link should take a few minutes...

---

### Post by Rybandt on 2010-07-01
> **realzippy said:**
> *The Easy Way - Installing kernel 2.6.35-rc1*
from the link should take a few minutes...

What link!!!

---

### Post by realzippy on 2010-07-01
HOWTO: Get Ubuntu 10.04 working properly on the Toshiba A505 laptop

[http://ubuntuforums.org/showthread.php?t=1503491](http://ubuntuforums.org/showthread.php?t=1503491)

---

### Post by Rybandt on 2010-07-01
> **realzippy said:**
> HOWTO: Get Ubuntu 10.04 working properly on the Toshiba A505 laptop

[http://ubuntuforums.org/showthread.php?t=1503491](http://ubuntuforums.org/showthread.php?t=1503491)



Realzippy... You are a godsend my friend. Thank you so much for helping me!!! All I need to do now is figure out my wireless card and I am golden! YOU ARE AWESOME! :D:D:o:D:D:D:D

---

### Post by realzippy on 2010-07-02
Nah,I only ran google.
Thanks to *purelinuxuser* who wrote that guide.
Have you seen the link at the end of that guide?(wireless problem)

[http://ubuntuforums.org/showpost.php?p=9446203&postcount=35](http://ubuntuforums.org/showpost.php?p=9446203&postcount=35)

---

