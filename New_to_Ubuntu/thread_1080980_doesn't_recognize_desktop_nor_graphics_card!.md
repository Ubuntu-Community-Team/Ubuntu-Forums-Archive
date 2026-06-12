---
title: "doesn't recognize desktop nor graphics card!"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by anico on 2009-02-26
i was originally trying to solve my sleep hybernate problem using the instructions on this site..[http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/](http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/)
however.. now when i restart my computer.. ubuntu does some random checks and then displays an error that i'm on very low graphics card.. i know i must have screwed something up big time! i'm very new to ubuntu and this is just overwhelming! Please help me! I'm stuck with a very bad and tiny resolution!! thank you so much!!

---

### Post by overdrank on 2009-02-26
Hi and are you using Gutsy 7.10? If so you can try using the ctrl, alt, F1 keys to reach the command like and reconfigure your xorg ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by anico on 2009-02-26
no i'm running on hardy 8.04 , I tried to undo every code i modified in the link.. but it seems as though the code that i typed under section "Device" isn't there anymore.. i'm worried about this..

---

### Post by overdrank on 2009-02-26
> **anico said:**
> no i'm running on hardy 8.04 , I tried to undo every code i modified in the link.. but it seems as though the code that i typed under section "Device" isn't there anymore.. i'm worried about this..

Ok if you are using Hardy then you should be able to boot into recovery mode and use the xfix option to correct the graphics issues. Recovery mode is usually the second choice at the grub. Then you should be given 4 options and the last is the xfix.

---

### Post by anico on 2009-02-26
ok i'm on recovery mode and i tried xfix, i got an error which said :
error: possibly-costumised configuration file; back up found in /ect/x11/xorg.conf.20090226011704

Being on recovery mode the screen resolution seems to magically work though!.. should i try booting as normal and finding that back up? What is the procedure with a back up? thank you for your help i appreciate it!

---

### Post by overdrank on 2009-02-26
> **anico said:**
> ok i'm on recovery mode and i tried xfix, i got an error which said :
error: possibly-costumised configuration file; back up found in /ect/x11/xorg.conf.20090226011704

Being on recovery mode the screen resolution seems to magically work though!.. should i try booting as normal and finding that back up? What is the procedure with a back up? thank you for your help i appreciate it!

Yea after xfix is complete you should be given the 4 options again which one is to boot normally. If you did back up your xorg before modifying it then you should be able to replace it.

 How did you install the nvidia drivers and what is the model of the graphics card?

---

### Post by anico on 2009-02-26
to be honest, i never did a backup of the file.. so i don't know how that showed up there..Also i don't have Nvidia at all.. i have this: 

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

I found a file /ect/x11/xorg.conf1 and the line that i added "  Option “NvAGP” “1&#8243;" while following the instructions is there..do i just delete it?

---

### Post by overdrank on 2009-02-26
> **anico said:**
> 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

I found a file /ect/x11/xorg.conf1 and the line that i added "  Option “NvAGP” “1&#8243;" while following the instructions is there..do i just delete it?

Yes you should not have to delete it after using the xfix. You can not use that "how to" that you link as it is for nvidia graphics not intel graphics that you have.

---

