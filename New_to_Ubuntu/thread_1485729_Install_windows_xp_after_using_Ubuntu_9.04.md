---
title: "Install windows xp after using Ubuntu 9.04"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by perryb2006 on 2010-05-17
Hi,
I am a new user of ubuntu and have practically no knowledge of how ubuntu works. A week ago i installed ubuntu on a pen drive (windows was corrupted) and since then i have been booting ubuntu via pen drive. Now, i want to switch back to windows, however i get an error message "Error loading operating system" after the initial boot while installing windows xp. 

Can someone please help me? I searched google and got a rough idea that it is related to boot loader. I would really appreciate if ubuntu community could help me with this matter.

BTW, i also formatted C drive (primary drive on which i wish to install windows xp) using Partition editor in live cd of ubuntu 9.04.

---

### Post by julio_cortez on 2010-05-17
> **perryb2006 said:**
> however i get an error message "Error loading operating system" after the initial boot while installing windows xp
It looks like you're trying to boot from the hard drive and no OS is found there (because you already wiped partitions with gparted).

Have you tried setting the BIOS to boot from the CD first of all? I'm quite confident it's the solution in this case.

---

### Post by zeroseven0183 on 2010-05-17
Hi [perryb2006]("http://ubuntuforums.org/member.php?u=1076761") and welcome to Ubuntu Forums.

You mentioned that you formatted drive C using the Ubuntu Live CD/Partition Editor. This erases the all data on that particular partition which in this case, your Windows system.

Now if you have with you the Windows CD and Ubuntu and you want to dual-boot, follow the instructions mentioned in [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot). You have an option to either install first Ubuntu then Windows or vice-versa.

A piece of advise before formatting any drive, back-up your data somewhere else.

Hope that helps.

---

### Post by perryb2006 on 2010-05-17
> **julio_cortez said:**
> It looks like you're trying to boot from the hard drive and no OS is found there (because you already wiped partitions with gparted).

Have you tried setting the BIOS to boot from the CD first of all? I'm quite confident it's the solution in this case.

My problem is after wiping the partition, when i tried to install windows xp in that partition, i got error message as stated above. So, i did try to install windows but for some reason windows was not able to load the initial boot files during startup and thats why the error message. And i believe formatting my c drive using ubuntu has something to do with this. Hope i am more clear this time.

> **zeroseven0183 said:**
> Hi [perryb2006]("http://ubuntuforums.org/member.php?u=1076761") and welcome to Ubuntu Forums.

You mentioned that you formatted drive C using the Ubuntu Live CD/Partition Editor. This erases the all data on that particular partition which in this case, your Windows system.

Now if you have with you the Windows CD and Ubuntu and you want to dual-boot, follow the instructions mentioned in [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot). You have an option to either install first Ubuntu then Windows or vice-versa.

A piece of advise before formatting any drive, back-up your data somewhere else.

Hope that helps.

---

### Post by sydbat on 2010-05-17
> **perryb2006 said:**
> My problem is after wiping the partition, when i tried to install windows xp in that partition, i got error message as stated above. So, i did try to install windows but for some reason windows was not able to load the initial boot files during startup and thats why the error message. And i believe formatting my c drive using ubuntu has something to do with this. Hope i am more clear this time.No. Formatting your hard drive with the Live CD only erased the data. Regardless of what file system the Live CD formatted to, your Windows CD will format to a Windows file system when Windows installs.

However, it sounds like you are trying to do a clean install of Windows with an upgrade disc, which requires a pre-existing installation of Windows to upgrade from. If you do have a full copy of Windows, are you positive it is legitimate (as in NOT downloaded and cracked from somewhere)?

---

### Post by zeekoman on 2010-05-17
> **julio_cortez said:**
> It looks like you're trying to boot from the hard drive and no OS is found there (because you already wiped partitions with gparted).

Have you tried setting the BIOS to boot from the CD first of all? I'm quite confident it's the solution in this case.

I agree.. I've had  the same problem (gives a "no operating systems found" error when the hard drive is wiped and it was trying to boot from the HD), make sure that your BIOS is set to boot from the CD.

---

### Post by gazj on 2010-05-17
try this as suggested in the second post

[http://ubuntuforums.org/showthread.php?t=631730](http://ubuntuforums.org/showthread.php?t=631730) [+]

---

### Post by perryb2006 on 2010-05-20
> **zeekoman said:**
> I agree.. I've had  the same problem (gives a "no operating systems found" error when the hard drive is wiped and it was trying to boot from the HD), make sure that your BIOS is set to boot from the CD.
BIOS is set to boot from cd. Anyways, my hdd was the culprit here. Found the problem.
Thanks for support ubuntu community!!! :)

---

