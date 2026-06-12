---
title: "xp wont boot first time back up"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by C. Pugwash on 2011-06-18
Hi,

really sorry if this is already posted. if so, please could you direct me to answer? i've had a look round and couldn't find any answers yet.

Problem:

recently installed ubuntu 11.04 on my laptop. its running fine. boots fine. (seems to) shut down fine.

its dual booting with win xp. xp is running fine, boots fine, shuts down fine.

BUT: after every ubuntu session, the first re-boot of XP stalls.  the only fix is to kill the power. then reboot xp. xp then displays the usual 'didn't shut down properly' message, then I choose to 'start xp as normal' and it works just fine.

i am guessing ubuntu is leaving something that xp doesn't like, but I don't know enough to get further than that.

this error doesn't happen with my other laptop running xp and ubuntu 10.10 dual boot.

any ideas for a fix please?

---

### Post by dhyonz on 2011-06-18
> **C. Pugwash said:**
> Hi,

really sorry if this is already posted. if so, please could you direct me to answer? i've had a look round and couldn't find any answers yet.

Problem:

recently installed ubuntu 11.04 on my laptop. its running fine. boots fine. (seems to) shut down fine.

its dual booting with win xp. xp is running fine, boots fine, shuts down fine.

BUT: after every ubuntu session, the first re-boot of XP stalls.  the only fix is to kill the power. then reboot xp. xp then displays the usual 'didn't shut down properly' message, then I choose to 'start xp as normal' and it works just fine.

i am guessing ubuntu is leaving something that xp doesn't like, but I don't know enough to get further than that.

this error doesn't happen with my other laptop running xp and ubuntu 10.10 dual boot.

any ideas for a fix please?

reinstall the grub if you want

:cheers

---

### Post by C. Pugwash on 2011-06-18
thanks for your help,

i think its not a grub problem. both OS's are booting fine. grub menu appears fine. it passes the instruction to to start the OS, and the OS starts. its DURING the XP boot process that the problem occurs. xp doesnt like something on the disk and stalls.

i think it's permissions on the drive or temp files, or something that xp isnt liking. 

any thoughts?

---

### Post by ruben_linux on 2011-06-18
then the fail is XP
:confused::confused:

---

### Post by C. Pugwash on 2011-06-18
> **ruben_linux said:**
> then the fail is XP
:confused::confused:

i'm not sure what you mean. where is the failure? I would like to understand, then fix the problem.

the xp installation was fine before ubuntu 11.04 install.

running a live linux distro is also fine, (it isnt touching the hard disk). 

10.10 appears fine, no probs with rebooting.

11.04 is showing this error.

how is xp at fault?

thanks

---

### Post by crispy_420 on 2011-06-18
Sounds like an XP issue to me. What does booting to safemode do for you? You may be able to see what locks it up.

---

### Post by C. Pugwash on 2011-06-18
> **crispy_420 said:**
> Sounds like an XP issue to me. What does booting to safemode do for you? You may be able to see what locks it up.


thanks, 

you think xp is to blame too? 

i'll try safe mode boot xp. do you know where I can read logs/ determine the fault in xp?

any idea why this is only happening with 11.04?

Thank you

---

### Post by Jerry N on 2011-06-18
I have a similar problem in my primary computer, which normally runs Win 7.  If I boot to Mint 9 (Ubuntu 10.04), which is on a separate drive, and subsequently reboot to Win 7, the mouse is frozen and the ethernet adapter is shut down.  The only solution I have found is to turn the power to the computer off completely and then back on.  This also happens if I run Puppy Linux although I haven't tried any other linux live CDs.  I don't believe that Win 7 is at fault but it doesn't make much difference because I don't normally run Linux on that machine anyway.  The computer has a Gigabyte MB with a Phenom II 955 quad core processor, 4 gb RAM, and a GT 9800 video board.

My secondary computer which currently has XP, Win 7, Mint 11, Mint Xubunt 11.04, and Ubuntu 11.04, does not exhibit this problem.  Also a Gigabyte MB, although several years older, with an Athlon 3800+ dual core, 2gb RAM, and a GT430 video board.

Jerry

---

