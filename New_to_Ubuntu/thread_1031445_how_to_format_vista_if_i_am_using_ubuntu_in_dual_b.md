---
title: "how to format vista if i am using ubuntu in dual boot"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by sudhir yadav on 2009-01-05
Hi friends,

I am using ubuntu for the past 2 months.I really love ubuntu.This is my first post in forum and i am feeling very excited to be the part of ubuntu forum.I have almost stopped using window but i do have to use window for some applications. Since my window is getting slow i have to format it.I am using ubuntu along with vista.my window is in C drive and ubuntu is in D drive. If i format C drive to reinstall my window, will it affect my Master boot loader?? Do i have to use super grub disk to enlist window and ubuntu again or two operating systems will boot normally as before?? can someone give detailed explanation about it??

thanks

sudhir

---

### Post by jimmy the saint on 2009-01-05
You have all the right ideas, it sounds like you just need a little hand holding.  No worries!  There is a community documentation guide that addresses this process quite well:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
The relevant section is about half way down.  It is titled "installing windows after Ubuntu" and will help you get the bootloader repaired.

---

### Post by jerome1232 on 2009-01-05
--edit-- beaten to it, that how-to will work great as well.

Well when you reinstall windows it will take the mbr back but it's an easy fix from a live cd.

An easy way to get grub back from a live cd. Assuming you have /boot on your root partition. Is to mount your root partition and chroot it, then you run the command to install grub.

you will change the mount /dev/sda1 to where ever your root partition actually is. If you need help figureing that out post the contents of these commands.

```
sudo fdisk -l
mount
``` 

```
sudo -i
mount /dev/sda1 /mnt
chroot /mnt
grub-install /dev/sda
exit
reboot
```

---

### Post by sudhir yadav on 2009-01-08
thanks jerome and jimmy the saint.

:D

---

