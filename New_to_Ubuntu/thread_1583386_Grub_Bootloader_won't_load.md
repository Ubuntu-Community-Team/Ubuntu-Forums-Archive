---
title: "Grub Bootloader won't load"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by thebarisaxkid on 2010-09-27
I have a desktop pc with two hard drives (1 80g and 1 120g)  They are set in master/slave format.  The 80g hd has windows XP and I just installed Ubuntu 10.04 on the 120g hd.  The installation completes normally, but when I restart, I get a message saying:

error: no such device: da7d5b20-fc2e-479d-96e3-04dd5f38a43c.

Below that, it says grub rescue> _

Next to the grub rescue> is type-able. (you can type things)

Anyone know what to do or what is wrong?

---

### Post by jtarin on 2010-09-27
Can you boot into Windows from the Grub boot screen?

---

### Post by jtarin on 2010-09-27
[Here are some commands you can use.]("https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode") Command Line and Rescue Mode

---

### Post by thebarisaxkid on 2010-09-27
No, I cannot boot into anything.  I tried all the commands, and even tried reinstalling GRUB form LiveCD but still no luck.  Same message appears.

Starting to get pissed!

---

### Post by thebarisaxkid on 2010-09-27
Is there a possibility that the disk has corrupted data on it?  Should I try another CD?

---

### Post by jtarin on 2010-09-27
> **thebarisaxkid said:**
> No, I cannot boot into anything.  I tried all the commands, and even tried reinstalling GRUB form LiveCD but still no luck.  Same message appears.

Starting to get pissed!How did you try to reinstall Grub? What method did you use?

---

### Post by garyed on 2010-09-27
I've had the same problem & here's what I did to solve it.

1 - Boot from the live CD

2 - Get to a terminal & do :
```
sudo fdisk -l
```
This will tell you for sure the correct partition that has the Ubuntu files, the "id" should be 83 & "system" Linux.
3 - Lets say the partition comes out to be /dev/sdb1.
    Substitute whatever your /dev/sdx is
Do these commands one at a time:
```

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

```

Then reboot & hopefully you'll have a grub menu on the HD to get into Ubuntu. Get to a terminal & run:
```
 sudo update-grub
```
Hope it works,
Good luck

---

### Post by thebarisaxkid on 2010-10-01
Thanks for all the help guys, but i decided to just install Ubuntu and nothing else.  Anyway, my parents would probably get confused on how to use the grub menu... so yeah.

---

