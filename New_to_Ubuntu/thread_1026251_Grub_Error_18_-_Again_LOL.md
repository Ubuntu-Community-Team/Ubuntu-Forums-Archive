---
title: "Grub Error 18 - Again LOL"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by qaissi on 2008-12-30
Yup I have searched around and tried what I could figure out to try so I guess I had better get some hand holding.

Trying to install Ubuntu 8.10 on an older system with an Intel P4, 1 G of Ram using a new 500 Gig WD Hard Drive.  Checked and the BIOS does in fact recognize the hard drive and does recognize its size.

I have tried installing Windows in a Primary partition with Ubuntu in an Extended partition and Windows got error 18.  Fixed MBR and windows would boot fine but of course no sign of Grub.

Tried installing Ubuntu using the whole drive and still Error 18

Tried all sorts of combinations as to which partition to install Ubuntu to and still Error 18.

Tried the steps in the Ubuntu Documentation [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) after each install on the different partitions.

I have tried so many variations that they have all blurred together and I am lost as to what is going on anymore.  So yes I guess I could use some newbie help.

I am running off of a Live CD right now and will wait a bit to see if anybody is hanging around who can help and if not I will try reinstalling letting Ubuntu use the whole drive.

Thanks in advance

---

### Post by tad1073 on 2008-12-30
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by caljohnsmith on 2008-12-31
A Grub error 18 typically occurs when you have a BIOS that can't access anything on a HDD past either 8.4 GB or 137 GB, depending on how old the BIOS is. Usually you can fix the problem by creating a ~200 MB boot partition at the front of the drive, and hence all of the Grub and Ubuntu boot files are easily accessible to the BIOS. Then when you go through the Ubuntu installer, simply set the mount point on the new boot partition as "/boot", and that should solve the Grub error 18 problem if all goes well. Let me know how it goes.

---

