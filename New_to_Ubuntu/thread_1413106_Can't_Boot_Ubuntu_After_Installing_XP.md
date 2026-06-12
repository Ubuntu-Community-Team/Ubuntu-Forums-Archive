---
title: "Can't Boot Ubuntu After Installing XP"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by t4nv1r on 2010-02-22
I had Windows Xp installed in Drive C and Ubuntu 9.04 installed in Drive F. Now my windows got infected by a virus so i decided to re-install it. So i deleted my C partition (jus like i always do if i install windows) and created a new C partition and installed Windows XP in it. As i', new in ubuntu u didnt know i had to back up MBR and those stuff. So now when my pc starts Windows Automatically boots. How to i Boot ubuntu now?

[my F drive was 89GB and i gave ubuntu 20GB so still now in windows it shows my F drive has 69GB so i think ubuntu is still there ,right? ]

---

### Post by Bradtek on 2010-02-22
Windows setup has deleted Grub info from the MBR
You will need to reinstall grub from the Ubuntu Live CD

[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

---

### Post by kansasnoob on 2010-02-22
> **Bradtek said:**
> Windows setup has deleted Grub info from the MBR
You will need to reinstall grub from the Ubuntu Live CD

[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

That link is for restoring grub2, if the OP is using 9.04 it's more likely legacy grub so he should look here;

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

