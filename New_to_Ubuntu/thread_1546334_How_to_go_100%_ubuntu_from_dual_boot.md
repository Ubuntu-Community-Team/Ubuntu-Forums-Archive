---
title: "How to go 100% ubuntu from dual boot?"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-08-05
Hello:

How do I go from a dual boot (unbuntu & xp) to a 100% ubuntu PC?

I want to totally remove XP and have ONLY ubuntu.

Thanks,

Rob.

Lenovo x61 Laptop
ubuntu 10.04 LTS

---

### Post by lkraemer on 2010-08-05
Since you have dual boot working, why not just boot into Ubuntu, and let
M$ sit while you continue on for a few months.  You can always remove
the M$ partition and re-install grub.

lk

---

### Post by Robert.Thompson on 2010-08-05
So, there is no advantage to having a 100% ubuntu machine?

---

### Post by uRock on 2010-08-05
> **Robert.Thompson said:**
> So, there is no advantage to having a 100% ubuntu machine?
There is, it is faster and more secure. If you are ready to delete Windows XP, then all you have to do is,
1. Boot the LiveCD,
2, Go in the menus to System> Administration> Gparted then,
3. Delete the Windows partition, then,
4. Reinstall grub with these directions, [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Let us know if you have any questions.

Cheers,
uRock

---

### Post by dodo3773 on 2010-10-06
> **uRock said:**
> There is, it is faster and more secure. If you are ready to delete Windows XP, then all you have to do is,
1. Boot the LiveCD,
2, Go in the menus to System> Administration> Gparted then,
3. Delete the Windows partition, then,
4. Reinstall grub with these directions, [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Let us know if you have any questions.

Cheers,
uRock

Hey I have a question about this too. My system right now is set up to triple boot Windows 7, Ubuntu 10.04, and Backtrack 4 R1. What I would like to do is remove Windows 7 and Backtrack 4. I see Windows 7 as 2 ntfs partitions that is simple enough. My problem is knowing exactly which swap and boot stuff is for Backtrack and which is Ubuntu. Is there an easy way to find out? If instead of using a live cd I just did it from gparted in Ubuntu would that not allow me to delete any Ubuntu stuff because it is all mounted? Like I could just delete it all and the stuff that was mounted would be untouched? Also how do I extend the partition for Ubuntu (ext4). If I do will that mess anything up? I have heard that if you extend a partition that can mess with your boot. Something about partition ID numbers or something. I am ready to make this move as well just need a little direction. Thanks in advance.

---

