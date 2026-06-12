---
title: "Smoother boot sequence??"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by hdemarzo on 2010-11-24
Im looking to make the boot up sequence smoother showing only the ubuntu loading screen.  i am also having trouble with my microphone (ie its not working)

---

### Post by Naitsirhc Hsem on 2010-11-24
if you want to remove the grub timeout before loading ubuntu,

 sudo gedit /boot/grub/grub.cfg 

and change 

set timeout=10

to

set timeout=0


just play around with that setting

---

### Post by yankysunny on 2010-11-24
> **hdemarzo said:**
> Im looking to make the boot up sequence smoother showing only the ubuntu loading screen.**  i am also having trouble with my microphone (ie its not working)**

Can u tell us the details. which version of ubuntu. hardware. sound drivers. have u changed anything recently

---

### Post by amjjawad on 2010-11-25
> **hdemarzo said:**
> Im looking to make the boot up sequence smoother showing only the ubuntu loading screen. 

You need first to read these:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


> i am also having trouble with my microphone (ie its not working)

Check your settings (System > Preferences > Sound) or check that mic on another machine.

---

### Post by wilee-nilee on 2010-11-25
> **Naitsirhc Hsem said:**
> if you want to remove the grub timeout before loading ubuntu,

 sudo gedit /boot/grub/grub.cfg 

and change 

set timeout=10

to

**set timeout=0**



just play around with that setting

You can do that but be sure to check if holding down the proper key will actually show the grub menu if needed. Not having access to the recovery kernel through grub is bad practice, it breaks your possibly in trouble, unless you chmod on chroot from a live cd.

---

### Post by hdemarzo on 2010-11-26
I am using 10.04 64 bit.  no i havent really changed anything,  i installed prelinking, and did the swappable thing.  other than that no i havent done anything anything out of the ordinary.  Im also looking for a really special theme,  something like that of a scifi movie and hackers combined,  any suggestions

---

