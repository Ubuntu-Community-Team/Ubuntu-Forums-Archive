---
title: "how to load 9.10 through a separate legacy grub partition"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by rahul_bhise on 2010-02-25
I have a separate legacy grub partition which gives me choice of booting in several different ubuntu flavors and windows xp. I recently installed ubuntu 9.10. and while installing I specifically told the installer to install grub on the same partition and not on the mbr of the hard disk. the installation went fine but when i restarted the computer, none of the OS which were on the same HD of the installed 9.10 were loading. there grub was corrupted. i reinstalled grub of all OS with help of [herman's site]("http://members.iinet.net/~herman546/p15.html#Re-install_Grub_with_Live_CD"). but i cant reinstall grub2 on the partition of ubuntu 9.10. 


is there any another method to load ubuntu 9.10 through this separate legacy grub partition.

---

### Post by mikeyphi on 2010-02-25
> **rahul_bhise said:**
> I have a separate legacy grub partition which gives me choice of booting in several different ubuntu flavors and windows xp. I recently installed ubuntu 9.10. and while installing I specifically told the installer to install grub on the same partition and not on the mbr of the hard disk. the installation went fine but when i restarted the computer, none of the OS which were on the same HD of the installed 9.10 were loading. there grub was corrupted. i reinstalled grub of all OS with help of [herman's site]("http://members.iinet.net/~herman546/p15.html#Re-install_Grub_with_Live_CD"). but i cant reinstall grub2 on the partition of ubuntu 9.10. 


is there any another method to load ubuntu 9.10 through this separate legacy grub partition.

Not sure I understand what you're actually after!
I have 3 HDs with XP and 3 Ubuntu versions installed.
Grub lists all of those on my 'normal' setup
I did have a minor problem when Grub2 was first installed. The 'older' Grub didn't see the new OS, so I had to do a new Grub-install allowing Grub2 to replace grub, followed by update-grub to get the full list of OSs.

Don't think you can run legacy grub on the mbr and also grub2 on a partition.

---

### Post by rahul_bhise on 2010-02-25
OK, so i have to reinstall the old grub with the new grub2 and also install it on the mbr of the first HD which will then point to this grub2 partition which will then load the OS of our choice. 

but will then grub2 chainload the older ubuntu OS's which uses legacy grub

---

### Post by mikeyphi on 2010-02-25
> **rahul_bhise said:**
> 
but will then grub2 chainload the older ubuntu OS's which uses legacy grub

grub2 will find all your OSs and give you a boot list for you to choose! Just as legacy grub did.

---

