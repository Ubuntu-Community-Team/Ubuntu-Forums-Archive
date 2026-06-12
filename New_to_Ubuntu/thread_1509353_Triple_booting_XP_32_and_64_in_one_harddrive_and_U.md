---
title: "Triple booting XP 32 and 64 in one harddrive and Ubuntu in another harddrive"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by PCZ on 2010-06-14
Hi, I have been trying to install Ubuntu to my existing XP 32 bit and XP 64 bit which are install in harddrive 0.
 
I am trying to install Ubuntu in harddrive 1 because I already made 3 partition in harddrive 0. As far as I know, you cannot have 4 partition in one drive so my original goal of having 3 OS in the same drive does not work. 
 
I installed Ubuntu several times in harddrive 1 and yet, when I load the system, I cannot see the Ubuntu OS. I can only see XP32 and XP 64.
 
I tried just doing this:
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
but it still does not work so I kind of gave up.
 
I do not know exactly what is going on.
 
Could it be my PC hardware? I heard that some motherboard boot IDE first then SATA or viceversa. 
 
I tried something called GRUB but I do not know how to use it and I have no access to it in XP. 
 
Also, in Computer Management, I can see harddrive 1 as "unknown partition".
 
Please advice. Thank you.

---

### Post by londonkeith on 2010-06-14
Try booting from hard drive 1 by changing the boot order in BIOS (prob F2 when you start up). At the moment your computer is just looking on hard drive 0 for an OS. Also I have had 3 OSs on one drive, XP SUSE and Ubuntu, so it could be done if you have enough free space.

---

### Post by Mark Phelps on 2010-06-14
IF, by default, you had both drives connected when you installed Ubuntu, my guess is that it would have installed GRUB to your first drive -- the one with XP on it.  SO, changing the order to boot from your second drive will not work in that scenario.

Your best approach would have been the following:
1) Disconnect the XP drive
2) Boot from the Ubuntu CD
3) Install to the only drive present
4) Reconnect the first drive -- but still boot from the second
5) Once into Ubuntu, open a terminal and enter "sudo update-grub".

This would have auto-generated a new GRUB2 menu such that, when you rebooted, you would have had access to all your OSs.

Unfortunately, now, you will probably need to reinstall GRUB2, this time, to your second drive. You would need to disconnect the first drive when you do this to ensure that GRUB2 gets installed to the proper drive.  Once you do that, you do the Ubuntu reboot, the update-grub command, and after reboot, you should be OK.

---

### Post by xiainx on 2010-06-14
Hi there,

There could be a few things wrong...

1) Did you set your ubuntu part with /boot on it (this could be the part mounted on /boot, or / if you don't have a /boot part) as bootable? Run sudo fdisk -l to find out.

2) You might have to switch the boot order of your drive in BIOS. You can do this by pressing f12 when your computer is booting, selecting boot sequence and swapping the two SATA drives.

Ubuntu *should* have installed GRUB and automatically loaded your two windows entries into the bootloader. This means when you boot from the second hd, it will show you a menu that says something like...

Ubuntu whatever whatever
Another Ubuntu ....
Memtest or something
Windows XP 32
Windows XP 64

And you will be able to choose which OS to boot.

Iain

---

### Post by PCZ on 2010-06-14
Testing all your suggestions now. Thank you.

---

### Post by Mark Phelps on 2010-06-15
As I already mentioned, changing boot order won't accomplish anything if GRUB is installed to the first drive ...

Also, I should have mentioned that AFTER you install GRUB to the second drive, you need to reconnect the first drive -- but still boot from the second drive.  THEN, when you do "update-grub", it will find the OSs on the first drive and autogenerate the correct menu entries for them.

---

### Post by PCZ on 2010-06-16
> **londonkeith said:**
> Try booting from hard drive 1 by changing the boot order in BIOS (prob F2 when you start up). At the moment your computer is just looking on hard drive 0 for an OS. Also I have had 3 OSs on one drive, XP SUSE and Ubuntu, so it could be done if you have enough free space.
 
I just tried this and I could not select the HD with Ubuntu on it to boot first. I guess because it is not the master drive. I could only select the HD that XP 32 and 64 are installed. Thank you anyway.
 
Trying the other methods.

---

### Post by PCZ on 2010-06-17
> **Mark Phelps said:**
> IF, by default, you had both drives connected when you installed Ubuntu, my guess is that it would have installed GRUB to your first drive -- the one with XP on it.  SO, changing the order to boot from your second drive will not work in that scenario.

Your best approach would have been the following:
1) Disconnect the XP drive
2) Boot from the Ubuntu CD
3) Install to the only drive present
4) Reconnect the first drive -- but still boot from the second
5) Once into Ubuntu, open a terminal and enter "sudo update-grub".

This would have auto-generated a new GRUB2 menu such that, when you rebooted, you would have had access to all your OSs.

Unfortunately, now, you will probably need to reinstall GRUB2, this time, to your second drive. You would need to disconnect the first drive when you do this to ensure that GRUB2 gets installed to the proper drive.  Once you do that, you do the Ubuntu reboot, the update-grub command, and after reboot, you should be OK.

I have 3 HD. 
HD1 IDE has 3 primary partition with XP 63 and 32 installed and it is the master drive.
HD2 IDE I use it entirely for Ubuntu because I do not know how to install inside a partition in HD2 so I basically chose the option to wipe the whole 120GB and install Ubuntu
HD3 SATA just data.

I followed your step
1) Disconnected HD1 and HD3.
2) Booth from Ubuntu CD and installed in HD2
3) Turned off PC
4) Connected back HD1

My results are
5) Restart PC and it loaded Ubuntu
6) Opened terminal and then update-grub
7) Restart computer 
8) It works very well. 

I can load 3 OS now. I installed Ubuntu 64. 

Thank you very much Mark.

Now how do I put [SOLVED] in the thread title.

---

