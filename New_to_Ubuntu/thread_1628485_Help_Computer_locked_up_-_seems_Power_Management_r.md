---
title: "Help: Computer locked up - seems Power Management related"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by bthomson100 on 2010-11-22
I have an Acer Aspire 3104 running Ubuntu 10.4 which has just locked me out.

It also has a French version of Windows Vista Basic but that has become so cluttered that it is almost useless since it takes forever to load.

The error message that I get is as follows:

Install problem!
The configuration defaults for 
GNOME Power Manager have not
been installed correctly.
Please contact your computer
administrator.

This happens when I try to load Ubuntu normally or with the menu item
Ubuntu, Linux 2.6.32-25-generic (recovery mode)

I have no idea how this happened as I haven't changed any power settings.

I thought I was the administrator but it won't allow me to log in as myself or as any other user, including "admin" or "administrator". I don't know if there are passwords for an administrator anyway and I've certainly never set one up.

I'm a complete Linux newbie so please be very simple with any tips and don't assume I know what any Linux commands are. I need step by step instructions.

---

### Post by yankysunny on 2010-11-22
go  to the recovery mode and login as root by "sudo su"
Then try to reinstall the gnome power manager by "apt-get remove gnome-power-manager*.deb" and then install it again

---

### Post by bthomson100 on 2010-11-22
How do I go to recovery mode?

---

### Post by Amente on 2010-11-22
> **bthomson100 said:**
> I have an Acer Aspire 3104 running Ubuntu 10.4 which has just locked me out.

It also has a French version of Windows Vista Basic but that has become  so cluttered that it is almost useless since it takes forever to load.

The error message that I get is as follows:

Install problem!
The configuration defaults for 
GNOME Power Manager have not
been installed correctly.
Please contact your computer
administrator.

This happens when I try to load Ubuntu normally or with the menu item
Ubuntu, Linux 2.6.32-25-generic (recovery mode)

I have no idea how this happened as I haven't changed any power settings.

I thought I was the administrator but it won't allow me to log in as  myself or as any other user, including "admin" or "administrator". I  don't know if there are passwords for an administrator anyway and I've  certainly never set one up.

I'm a complete Linux newbie so please be very simple with any tips and  don't assume I know what any Linux commands are. I need step by step  instructions.

I think this will help [http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/.]("http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/")

If you need additional help on following that,then post it and I will try to explain.Good Luck!

---

### Post by yankysunny on 2010-11-22
Ubuntu, Linux 2.6.32-25-generic (recovery mode)..if this recovery mode give u error before giving u any prompt, you can use ubuntu live cd to go into the system

---

### Post by bthomson100 on 2010-11-22
Thanks Amente. However, cleaning the cache and even deleting a largish file that I have saved elsewhere didn't change anything.

I tried the other suggestions but I keep getting messages saying I don't have permission to do them.

Is there some way to find out if there is indeed a low disk space problem? e.g. a command to display disk space on the root drive. Is there a way to make the root disk larger as I have lots of space still on the physical drive? (I think because I have no way of knowing if the Ubuntu root drive is on my drive C: partition or the drive D: partition on the hard drive.

Bob

---

### Post by yankysunny on 2010-11-22
> **bthomson100 said:**
> Thanks Amente. However, cleaning the cache and even deleting a largish file that I have saved elsewhere didn't change anything.

I tried the other suggestions but I keep getting messages saying I don't have permission to do them.

**Is there some way to find out if there is indeed a low disk space problem?** e.g. a command to display disk space on the root drive. Is there a way to make the root disk larger as I have lots of space still on the physical drive? (I think because I have no way of knowing if the Ubuntu root drive is on my drive C: partition or the drive D: partition on the hard drive.

Bob
```
df -h
```

For the earlier problem
do ctrl+alt+f2
and then try to reinstall the gnome power manager

---

### Post by bthomson100 on 2010-11-22
If I try to remove the gnome-power-manager*.deb it says it couldn't find it.
And it couldn't find gnome-power-manager*.deb to install it.

---

### Post by Jetso on 2010-11-22
Hmmm, I don't know. Because when I originally installed Ubuntu and was doing the partitioning, then put Ubuntu on here, grub didn't call Windows Windows, it Called it Windows Recovery Enviroment, so I don't know if that partition has something to do with My Windows bootability. I wouldn't mess with it until I had another computer or something.

---

### Post by yankysunny on 2010-11-22
> **bthomson100 said:**
> If I try to remove the gnome-power-manager*.deb it says it couldn't find it.
And it couldn't find gnome-power-manager*.deb to install it.

Actually I put star at the end cuz I dont know the full name or attached version number with that. just try to push tab to auto-complete the name. and same for installing

---

### Post by bthomson100 on 2010-11-22
OK. I've backup up my C: partition files and I've been able to load another version of Linux (Knoppix) onto the laptop from a USB key I had with that on it from a while ago when I was exploring Linux. However I can't see the Ubuntu partition. I was hoping to be able to see it but I guess I'm going to have to put Ubuntu on a USB key and try again. I'll then back it up and reinstall Ubuntu 10.10 or 10.4.

Is there any way when installing Ubuntu to make that partition larger so it won't run out of disk space so soon?

Bob

---

### Post by yankysunny on 2010-11-22
If u want more disk space then install ubuntu on bigger partition.
Can you tell me what partitions u got on ur hard disk ?

---

### Post by bthomson100 on 2010-11-24
I'm back after a day still trying to recover use of my laptop. (reminder Acer Aspire running Ubuntu 10.4 and Windows Vista Basic).

I've tried the sudo apt-get clean, and using "df" I still get the listing of file system that says that my Ubuntu partition (/dev/loop0 I assume) has 0 available space, According to the AbsolutelyTech.com page that Amente so helpfully provided, this is likelythe problem, i.e. low disk space on the root drive.

I've been able to copy some important files from the root drive to a Windows partition (sda3) on the laptop, but this then means I have to reboot, go into Windows (which takes 5 minutes !!@#) and then copy them to an external drive and then from there to my netbook which thank goodness is still working with Ubuntu 10.10. I was also able to delete some files that were backed up elsewhere, but the drive still shows 0 space available which might mean the deleted files are still sitting in some invisible cache somewhere.

I appear to have lost some financial data files because the GnuCash file I recovered this way doesn't work and my backup is a week old. (I know I should back up more often but I have yet to find a linux backup programme that will automate this for me. I'm a newbie to the linux world, although I have some old DOS command knowledge.)

I'd like to be able to get Ubuntu working again on the laptop so I can properly back up everything before wiping out and reinstalling Ubuntu. I'm assuming if I can create some memory space it will come back but I haven't been able to do that.

It would also be nice to be able to use a USB memory stick to back up files using the copy command, but I can't get linux to recognize one when running in a terminal. (Which I can do now thanks to yankysunny's tip about ctrl+alt+f2). That way I could bypass having to go back into Windows to collect files copied to sda3 (Windows D:).

Any tips?

Bob

---

### Post by bthomson100 on 2010-11-25
I was finally able to back up my /home/user directory to a USB drive with help from another thread I created because I wasn't getting the help I needed from this thread. A friend of a friend also came over and helped me mount the USB drive so that I could make a backup.

The posting at lp [http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/](http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/)  which was sent by Amente was the most helpful. It was indeed a disk space problem and I needed to find out how to backup my root drive before I could delete files from it to create space. 

I did that, deleted some 16,000 thumbnail *.png files from a .thumbnails directory and then Ubuntu was able to run. I then was able to backup the files I couldn't copy from the root directory (for some reason they got corrupted in the copy process - don't ask me how) using the applications that created them.

So I'm back in business after wasting probably an entire day on all this. Thank goodness I'm retired. It reminds me of my first computer with Windows Vista where I wasted several days because Microsoft decided to store all users files in a place that was different from where Windows XP stored them, making it impossible to just load files backed up under XP because Vista couldn't find them. 

So while Linux is faster, cheaper and just as useful and generally has as easy a user interface as Windows, in the long run, like other computer operating systems, it is not intrinsically user friendly at all. The one saving grace I guess is that support forums like this are free and there are a lot of generous people willing to guess from kilometers away what might help solve any given problem.

Thanks for your comments and tips. I'm now somewhat further along the Linux learning curve.

Bob

---

