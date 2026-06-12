---
title: "Beginner Help"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by Bardasian on 2009-03-25
Hey everyone. 
I'm new to Ubuntu but I have a good grasp on semi-advanced Windows tasks. :p

Anyways, I recently downloaded ubuntu off the website and installed it as "Mount in Windows" choice because I can't burn CD's/DVD's (broken disk drive). 

I'm really enjoying the layout of Ubuntu, however I do need help with some things...

1. I'm trying to transfer my files (mostly just music/pics) from Vista over to Ubuntu, but I'm a little confused on exactly how to do so. 

2. If I understand correctly, right now Ubuntu is being run by Vista? So that would mean that Ubuntu is not fully independent? Is there anyway to make it so without using a CD?

Thanks for your time everyone.

-Hunter

---

### Post by halitech on 2009-03-25
> **Bardasian said:**
> Hey everyone. 
I'm new to Ubuntu but I have a good grasp on semi-advanced Windows tasks. :p

Anyways, I recently downloaded ubuntu off the website and installed it as "Mount in Windows" choice because I can't burn CD's/DVD's (broken disk drive). 

I'm really enjoying the layout of Ubuntu, however I do need help with some things...

1. I'm trying to transfer my files (mostly just music/pics) from Vista over to Ubuntu, but I'm a little confused on exactly how to do so. 

2. If I understand correctly, right now Ubuntu is being run by Vista? So that would mean that Ubuntu is not fully independent? Is there anyway to make it so without using a CD?

Thanks for your time everyone.

-Hunter

for 1. Ubuntu should be able to mount the windows drives and then just copy them over.

2. If you used WUBI then it is actually running as a file inside windows so you would be correct. You can try Unetbootin to install ubuntu in an actual native partition.

---

### Post by llamabr on 2009-03-25
There are other options too, such as booting from a usb flash drive.

---

### Post by otakuj462 on 2009-03-26
Hi Hunter, and welcome to the Ubuntu community. 

It sounds like you're using Ubuntu via Wubi. Wubi basically works by installing Ubuntu inside of a single file (called a loopback file) on the windows file system, and modifying the Windows bootloader so that it allows you to boot from that file. In this way, you're able to avoid partitioning your hard drive, which can be difficult in Windows XP (but is actually remarkably easy in Vista, see here for details: [http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)).

Normally, if you have a Windows dual-boot setup, with Windows on one partition and Ubuntu on another, your Windows partition will show up in the Places menu as a disk. Clicking on it should mount it and launch Nautilus, the file manager, at that particular location. However, I seem to remember Wubi mounting the windows partition in a slightly unorthodox place... If it's not in Places, then check /WINDOWS (that's the directory called "WINDOWS" inside of your system root directory). I seem to remember it being there.

It's important to note that you shouldn't need to copy files over from Windows to Ubuntu in order for them to be accessible. Ubuntu has very good read/write support for both NTFS and FAT32, so once you have the drive mounted, working with files on a Windows partition should be seamless.

If you have any further questions, please don't hesitate to ask.

Jake

---

