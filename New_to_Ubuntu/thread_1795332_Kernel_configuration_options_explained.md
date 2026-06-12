---
title: "Kernel configuration options explained"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by kranthi.doss on 2011-07-02
Hi,
     Im new to ubuntu ( 25 days of Natty :guitar: ) and i use windows only to sync my ipod and nothing else. I looked around all the settings and is running well on a Dell inspiron 1520. I saw some tutorials over google to compile the kernel (2.6.38). I am a beginner and i want to know if there is some place where all the kernel configuration options are explained in detail. Some of the options i can get over google but some are confusing. I am using xconfig to customize kernel options and yes i saw the explanation for options in the xconfig window but i cant figure out what those parameter mean :confused:.
[LEFT]
Also there are packages installed like ATI card support (I have a intel G965). Is there a way to remove all those unused packages or is it about compiling the kernel?

I AM READING A LOT ABOUT KERNEL AND I APPRECIATE ALL THE HELP. THANKQ
[/LEFT]

---

### Post by sandyd on 2011-07-02
> **kranthi.doss said:**
> Hi,
     Im new to ubuntu ( 25 days of Natty :guitar: ) and i use windows only to sync my ipod and nothing else. I looked around all the settings and is running well on a Dell inspiron 1520. I saw some tutorials over google to compile the kernel (2.6.38). I am a beginner and i want to know if there is some place where all the kernel configuration options are explained in detail. Some of the options i can get over google but some are confusing. I am using xconfig to customize kernel options and yes i saw the explanation for options in the xconfig window but i cant figure out what those parameter mean :confused:.
[LEFT]
Also there are packages installed like ATI card support (I have a intel G965). Is there a way to remove all those unused packages or is it about compiling the kernel?

I AM READING A LOT ABOUT KERNEL AND I APPRECIATE ALL THE HELP. THANKQ
[/LEFT]

a) don't bother customizing the kernel if your a beginner. Even more advanced users don't bother, because setting the kernel options from scratch is a PITA.

I only customize the kernel because I use gentoo, and even that, it took a long time for me to select all the right options to get all the hardware working.

b) use menuconfig instead. When you highlight a option using your keyboard arrows, you can use the "/" key to read the description.

---

### Post by NightwishFan on 2011-07-02
If you ignore the bfs/ck patch parts this is a basic guide to compiling a kernel. Though I doubt it will prove very useful.
[http://ubuntuforums.org/showthread.php?t=1637004](http://ubuntuforums.org/showthread.php?t=1637004)

---

### Post by kranthi.doss on 2011-07-02
@SANDYD- Thank you, i didn't know eve pros need a lot a time to know the best working options. Today i read about creating kernel modules and im getting excited learning about the kernel. I wil try to use menuconfig and customize the kernel. 

I will keep looking for any info i might get.

@NIGHTWISHFAN- I will look into the guide.. Thank you.

---

### Post by wildmanne39 on 2011-07-02
Hi, it is a hard subject, I to configured a kernel for gentoo to run in virtualbox just for the experience, the whole process of compiling and setting up gentoo took about a week for me to do.

---

### Post by kranthi.doss on 2011-07-03
@WILDMANNE39.. wow.. a week?? Thanks for sharing..

I am de-selecting all the hardware that is not in my laptop. Removed all the AMD and ATI support (mine is a intel core 2 duo). Miscellaneous hardware like accelerometer, magnetometer etc are also removed. I hope this is the way it works.

---

### Post by JASONFUSARO on 2011-07-22
I just compiled 3.0.0 and deselected alot of stuff and selected core 2 and I am experiencing no problems

jason@UbuntuStudio64bit:~$ uname -a
Linux UbuntuStudio64bit 3.0.0 #1 SMP Fri Jul 22 03:05:50 EDT 2011 x86_64 x86_64 x86_64 GNU/Linux


this was the second version compile I have done and it went pretty smooth.

I used 


[http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html#CONFIGURATION-2-6](http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html#CONFIGURATION-2-6)

as a reference

as well as 

[http://linuxgazette.net/111/krishnakumar.html](http://linuxgazette.net/111/krishnakumar.html)


also looked at 

[http://book.opensourceproject.org.cn/kernel/kernelpri/opensource/0131181637/ch09lev1sec2.html](http://book.opensourceproject.org.cn/kernel/kernelpri/opensource/0131181637/ch09lev1sec2.html)

---

### Post by kranthi.doss on 2011-07-29
@JASONFUSARO - That were some really useful information. Thank U for sharing.

---

