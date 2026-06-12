---
title: "problem with my labtop"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by mahmoud fayed on 2010-10-11
[CENTER][SIZE=3]hi, everybody
i try to install ubuntu with my new [COLOR=#000000]Laptop[/COLOR] Sony Vaio CW-21
but i can't
 he gives me a black screen after choice "try ubuntu" or "install"
and i try to install it from live cd and usb flash
and i used newest and previous versions of ubuntu

so how can i solve this problem ?





[/SIZE][LEFT][SIZE=3][SIZE=2]Thanks, Keep Smiling It's Sunnah and Free Too :)
Mahmoud Fayed[/SIZE]
[/SIZE][/LEFT]
[/CENTER]

---

### Post by Peter09 on 2010-10-11
Here is what appears to be the bug, and if you look carefully near the bottom of the thread, a fix.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/571383](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/571383)

---

### Post by mahmoud fayed on 2010-10-11
> **Peter09 said:**
> Here is what appears to be the bug, and if you look carefully near the bottom of the thread, a fix.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/571383](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/571383)


[CENTER]sorry peter but i can't find the solution, can u write it here :)

Thanks 
[/CENTER]

---

### Post by Peter09 on 2010-10-11
OK,
when you get to the grub command line type 'e' for edit. add 'nomodeset' to the boot line, see if that works.

---

### Post by sanderd17 on 2010-10-11
You don't get grub when you boot the live CD.

Press any key at boot, then you come in a choice screen, choose your lang and your keyboard. After that, press F6 and check the "nomodeset". 

If it works and when you installed it, it's possible you still have to do the grub thing.

---

### Post by anewguy on 2010-10-11
The advice is coming from the solution you were pointed to in the thread:

> fompi wrote on 2010-05-04:  #26  

Affected with vaio VPC-CW2X
Managed to install with alternate install; then:
* boot with the alternate
* mounted my new install, chrooted inside them
* copied /dev directory to /$mntpoint/dev, mount proc to /$mntpoint/proc
* edit /etc/default/grub, added "nomodeset" to GRUB_CMDLINE_LINUX_DEFAULT
* exec update-grub
Reboot and worked :)


If need be, you can download and burn the alternate installer CD and do the above as well.  The key is the "nomodeset".

Dave ;)

---

### Post by mahmoud fayed on 2010-10-11
> **Peter09 said:**
> OK,
when you get to the grub command line type 'e' for edit. add 'nomodeset' to the boot line, see if that works.

[CENTER][SIZE=4]oohhh :D thanks peter it's work [/SIZE]
[/CENTER]
 
> **sanderd17 said:**
> You don't get grub when you boot the live CD.

Press any key at boot, then you come in a choice screen, choose your lang and your keyboard. After that, press F6 and check the "nomodeset". 

If it works and when you installed it, it's possible you still have to do the grub thing.

> **anewguy said:**
> The advice is coming from the solution you were pointed to in the thread:



If need be, you can download and burn the alternate installer CD and do the above as well.  The key is the "nomodeset".

Dave ;)


[CENTER][SIZE=4]Thanks sanderd and anewguy For your help[/SIZE]
[/CENTER]

---

### Post by anewguy on 2010-10-12
Glad Peter09's info worked for you - it's always good to see another problem solved!

Best of luck to you!

Dave ;)

---

### Post by Peter09 on 2010-10-12
Hi,
glad to see your up and running with your machine, apologies for the slightly confused solution (it was the end of a long day yesterday) and thanks to those who came in and clarified what need to be done.

---

