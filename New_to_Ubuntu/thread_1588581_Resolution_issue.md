---
title: "Resolution issue"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by Intsmssss on 2010-10-05
Ive just installed ubuntu 10.04 and its the first time ive ever used it.

The first problem i ran into was during the installation, the monitor hooked up to my laptop didn't display anything. This is a big problem cause the backlight of my laptop monitor is broke. Luckily with a flashlight I could got through it.

I found the monitor preferences and put the refresh rate on 75hz which turned on my 2nd monitor. The only issue now is the resolution which ive currently put on 800 600. 1280 1024 would be ideal for the monitor but this isn't an option atm.

Do i need to install video drivers to solve this? And where can i get these?
Any other things i need to do after first install?

Any help would be appreciated

Im using:
Samsung Syncmaster 710n monitor 
Asus A6Ja laptop
Ati x1600 video card

---

### Post by xtremesupremacy3 on 2010-10-05
It looks like you need the ATI drivers.

If I am right you will find an icon near your clock at the top letting you know there are hardware drivers, if you click on it it will list the drivers, install this and restart and you should have a nice good resolution.

If you dont find it there, click on System > Administration and there should be an entry there too.

Hope that helps

---

### Post by Intsmssss on 2010-10-05
i dont see any button near clock of importance.
Under system, administration, hardware drivers it only finds one proprietary modem driver.

This is its description

"The SmartLink modem daemon is the application part of thedriver for recent modems produced by Smart Link Ltd.

This package replaces (along with hardware access drivers) the olddriver generation (2.7.x) which consisted of kernel modules only.

It needs a kernel driver to access the hardware. This can be eitherrecent ALSA (shipped with a newer kernel (>=2.6.4) with ALSA supportand snd-intel8x0m module) which is sufficient for basic operation anddata/Internet connection, or the SmartLink kernel driver which isprovided by separate packages which you can build using the source fromthe sl-modem-source package. "

could you please be more specific on where to download the driver? 

a big thanks in advance

---

### Post by xtremesupremacy3 on 2010-10-05
Personally I have Nvidia but I remember the problems I had with ATI.

There is a package in the repositories called jockey. From what I hear, this is an application to help install drivers for ATI and Nvidia.

I would recommend trying it out.

If you are using 10.04 and will be upgrading to 10.10 make sure you remove that package before upgrading. Not that you will lose files, but it will cause graphical issues after the upgrade. Just a forewarning.

Let me know how you get on

---

### Post by Intsmssss on 2010-10-05
[LEFT]Sorry for replying so late, kinda busy moving all m stuff to my new room. Those packages were already installed, i tried reinstalling to see if i could find out how to open the program. 

I havent been very successful at that so far. Could you please shed some light on where to open this jockey?

I appologize for my ubuntu noobness  but i guess thats no surprise considering the forum topic.

[xtremesupremacy3]("http://ubuntuforums.org/member.php?u=556350") bedankt voor de hulp zover :)

[/LEFT]

---

