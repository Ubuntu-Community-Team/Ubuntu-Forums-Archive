---
title: "Having issues after updates"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by er6ben on 2010-02-01
Hello all !
So I took the plunge last night and decided to dual boot my Toshiba satellite with XP and Ubuntu. Everything went really well and I was pretty excited ( I used the netbook remix )About and hour after surfing around I was notified that there was two hundred and seven updates. I downloaded them and installed them and followed the system recommendation to reboot. Once I was returned to the grub screen I had my original ubuntu install and its recovery and a newer version and its recovery along with my xp....... Now when ever I try to load either Ubuntu, I get a small logo for about 2 minutes followed by a black screen. I did let it sit at the black screen for about 4 hours ( cause I fell asleep ) Does anybody know what I did wrong ? or what I can do? Any help would be appreciated.:D

---

### Post by corncob on 2010-02-01
I Don't know about NBR but if you're connected to the internet while you're installing 9.10 it will automatically download and install the new version right off rather than the original.  Might save you some of these upgrades which apparently messed up somewhere.
Do you get a command prompt or is the entire screen black?  If so you might try typing in
```
startx
```
or pressing [CTRL][ALT][F7]

---

### Post by er6ben on 2010-02-01
> **corncob said:**
> I Don't know about NBR but if you're connected to the internet while you're installing 9.10 it will automatically download and install the new version right off rather than the original.  Might save you some of these upgrades which apparently messed up somewhere.
Do you get a command prompt or is the entire screen black?  If so you might try typing in
```
startx
```
or pressing [CTRL][ALT][F7]

Hey thank you for the advice. I ended up re-installing and I am once again faced with 207 updates but I am just going to put them off for now until I can figure out where I went wrong::)

---

### Post by SPazzo on 2010-02-01
Hmm...  Of course there is going to be quite a few updates after a new install.  I agree that you should wait a bit.  I'd say wait a day or two and then refresh the update list.  Maybe try again then.  But be prepared for it still not to work.

---

### Post by corncob on 2010-02-02
> **er6ben said:**
> Hey thank you for the advice. I ended up re-installing and I am once again faced with 207 updates but I am just going to put them off for now until I can figure out where I went wrong::)

Maybe you could just install a few updates at a time.  I know that's a lot of boxes to uncheck but you could pick out anything suspicious like startup or desktop items, also things you don't need or use.  Something similar happened to me on my eeepc when I tried changing the NBR desktop to the classic desktop in 9.04.  I never was able to fix it but 9.10 came out and I installed that.

---

### Post by Flimm on 2010-02-02
> **corncob said:**
> Maybe you could just install a few updates at a time.  I know that's a lot of boxes to uncheck[...]

Tip of the day: you can uncheck all the updates at once by right clicking on one and clicking "Uncheck all" (or "Untick all", in British English).

---

### Post by corncob on 2010-02-02
I had installed plain old Ubuntu 9.10 in my Gateway notebook about a month ago.  The Update Manager never did pop up so I started it.  Sure enough, I had 208 upgrades to install.  I was a little hesitant thinking of you but I went ahead and installed them with the one exception of keeping the currently installed version of GRUB.  I rebooted the pc and everything appears to be okay.

---

