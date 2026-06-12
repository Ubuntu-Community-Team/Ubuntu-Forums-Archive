---
title: "arguments"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by penguinee on 2008-12-21
How can I run wubi with the argument "--32bit"? (in win xp)

Also, will wubi install 32 bit if i have a 32bit iso nearby?

Last time, Wubi installed 64 bit, even though my computer is FOR SURE 32 bit. 

Thanks for the help!

---

### Post by anim on 2008-12-21
What is your processor?

[edit] sorry to answer your question, yes:
[https://wiki.ubuntu.com/WubiGuide#Can%20I%20force%20Wubi%20to%20download%20and%20install%20a%2032%20bit%20version%20of%20Ubuntu?](https://wiki.ubuntu.com/WubiGuide#Can%20I%20force%20Wubi%20to%20download%20and%20install%20a%2032%20bit%20version%20of%20Ubuntu?)

It's just a seemingly large number of people don't realize that core2 duo's are 64 bit.

---

### Post by penguinee on 2008-12-21
[http://en.wikipedia.org/wiki/Pentium_4](http://en.wikipedia.org/wiki/Pentium_4)

i.e 	x86 (i386), x86-64, MMX, SSE, SSE2, SSE3


edit: do i have i duo? sorry.. i cant tell (im nub)

---

### Post by Xiong Chiamiov on 2008-12-21
Doesn't Wubi require you to provide an iso?  Haven't used it, but if that's the case, then you should just have to feed it an x86 iso and you're good.

---

### Post by anim on 2008-12-21
You don't have a core2duo, but you do have a 64bit capable processor (assuming its one of the newer pent4's), which is why wubi downloaded the 64 bit version automatically. That is what the x86-64 instruction set is.
[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by penguinee on 2008-12-21
yep wubi dl's one.

---

### Post by anim on 2008-12-21
> **Xiong Chiamiov said:**
> Doesn't Wubi require you to provide an iso?  Haven't used it, but if that's the case, then you should just have to feed it an x86 iso and you're good.

Nope. If you provide one, wubi will use it by default, but if you don't it will auto-detect system capabilities and download the correct files.

---

### Post by penguinee on 2008-12-21
hey.. maybe my system is 64 bit. didnt know that. 

can i run 32 bit ubuntu on 64 bit win xp?

---

### Post by SunnyRabbiera on 2008-12-21
> **penguinee said:**
> hey.. maybe my system is 64 bit. didnt know that. 

can i run 32 bit ubuntu on 64 bit win xp?

you probably can, as many people run 32bit systems on 64bit processors.

---

### Post by penguinee on 2008-12-21
I'll check it out. Thanks for the replies.

---

### Post by igknighted on 2008-12-21
> **penguinee said:**
> hey.. maybe my system is 64 bit. didnt know that. 

can i run 32 bit ubuntu on 64 bit win xp?

Your winXP is almost certainly 32 bit.  And Ubuntu isn't running "in" winXP.  It boots separately.

Also, Cairo Dock works just as well in 64bit.  If anything it would work better, so I would just stick with 64 bit ubuntu.  Now that there is a 64 bit flash plugin, and a 64bit java plugin, there really isn't anything you are missing.

---

### Post by anim on 2008-12-21
Just because your processor SUPPORTS 64 bit, doesn't mean your operating system is or [should be 64 bit]("http://www.google.com/search?q=64+bit+vs+32+bit&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a"). It's a choice you have to make (I use all 32 bit because I don't need the memory). But yes, you can have a 64 bit version of one OS and a 32 bit version of the other. For a while, I was running 32bit xp and 64 bit ubuntu gutsy on a dual boot core2 machine before I decided to regress to 32bit when hardy came out.

---

### Post by penguinee on 2008-12-21
> **igknighted said:**
> Your winXP is almost certainly 32 bit.  And Ubuntu isn't running "in" winXP.  It boots separately.

Also, Cairo Dock works just as well in 64bit.  If anything it would work better, so I would just stick with 64 bit ubuntu.  Now that there is a 64 bit flash plugin, and a 64bit java plugin, there really isn't anything you are missing.

Please tell me how to install cairo dock in 64 bit!

does it have something to do with some commands? forcing?


edit: think i found it!
[http://www.cairo-dock.org/ww_page.php?p=For%2064%20bits%20processor&lang=en](http://www.cairo-dock.org/ww_page.php?p=For%2064%20bits%20processor&lang=en)
yay.


double edit: i think that winxp is 64 bit. dunno why. feels like it. Are there any limitations?


triple edit: nope. 32bit. confirmed.


Thanks for all your help!!

---

### Post by igknighted on 2008-12-21
> **penguinee said:**
> Please tell me how to install cairo dock in 64 bit!

does it have something to do with some commands? forcing?


edit: think i found it!
[http://www.cairo-dock.org/ww_page.php?p=For%2064%20bits%20processor&lang=en](http://www.cairo-dock.org/ww_page.php?p=For%2064%20bits%20processor&lang=en)
yay.


double edit: i think that winxp is 64 bit. dunno why. feels like it. Are there any limitations?


triple edit: nope. 32bit. confirmed.


Thanks for all your help!!

All you need to do is type in a terminal 'sudo apt-get install cairo-dock'.  And you need to be running compiz.

EDIT: don't force the 32bit packages.  There are 64bit ones available.

---

### Post by igknighted on 2008-12-22
I was just thinking... what version of ubuntu are you using?  Cairo Dock is in the repos for 8.10 but not 8.04.  You might be able to install the 8.10 version in 8.04, I'll look into it and edit the post if it looks like it will work.

---

