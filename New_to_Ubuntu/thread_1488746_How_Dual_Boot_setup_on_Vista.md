---
title: "How Dual Boot setup on Vista"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by mawil1013 on 2010-05-20
I started reading the sticky about dual boot install but it was written for xp. I'm running vista. I have the newest ubuntu already on cd. where are instructions for vista and dual booting please.
piedmont

---

### Post by edgy360 on 2010-05-20
When you run the installer it will ask you if you want to dual boot (create another space for Ubuntu on your hard disk) or if you want to clean install. You should see a slider during the setup which will ask you what amount of space you want to give to Ubuntu and what you want to leave to Vista.

After the install you should find GRUB bootloader (included in the setup) will ask you which OS you want to boot.

---

### Post by mawil1013 on 2010-05-20
> **edgy360 said:**
> When you run the installer it will ask you if you want to dual boot (create another space for Ubuntu on your hard disk) or if you want to clean install. You should see a slider during the setup which will ask you what amount of space you want to give to Ubuntu and what you want to leave to Vista.

After the install you should find GRUB bootloader (included in the setup) will ask you which OS you want to boot.

sounds easy peasy, thanks!

---

### Post by oldfred on 2010-05-20
Some links, the difference in versions of windows or Ubuntu is small. With Vista or 7 it is better to use the windows tools to shrink the windows partition and reboot several times to make sure it recognizes the new size before installing. With Ubuntu the new versions install grub2 not grub legacy which has different repair instructions:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

ASUS EeePC netbook PC 10.04 install
[http://members.iinet.net/~herman546/p28.html](http://members.iinet.net/~herman546/p28.html)

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
See info on windows resizing, but do not agree with grub2 complaints
[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes)

---

### Post by edgy360 on 2010-05-20
> **mawil1013 said:**
> sounds easy peasy, thanks!

You're welcome :)

---

