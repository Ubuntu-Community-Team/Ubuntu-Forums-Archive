---
title: "need help updating proprietary ati driver"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by joshua84 on 2010-08-05
running ubuntu 10.04 x86 amd turionx2, ati 3xxxhd card---, i am unable to update my ati driver using the  terminal. i downloaded the latest driver but it is a ".run" file. i am unsure how to install update over the current proprietary driver installed.  i followed the steps from AMD.com yet no luck. 

reason for update: have starcraft 2-- loads fine graphics are pixels and horizontal lines-- when installing was told by the install setup/update graphics driver is out of date for running the game.

---

### Post by sylvainrb on 2010-08-05
Installed the driver for my HD4870 last night following this guide

[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide")

---

### Post by sylvainrb on 2010-08-05
Sorry didn't fully read your post. You have to completely uninstall the previous version before you install the new one. The guide tells you how to remove it as well.

---

### Post by clhsharky on 2010-08-05
joshua84

The easiest way to install binary drivers is to use the built in Hardware Drivers manager in Ubuntu.
System->Administration->Hardware Drivers

This is for Karmic but apply's to Lucid also.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Sharky

---

### Post by joshua84 on 2010-08-05
thanks 
[clhsharky]("http://ubuntuforums.org/member.php?u=543156"), sylvainrb, 
 problem solved,, starcraft 2 works flawlessly

---

