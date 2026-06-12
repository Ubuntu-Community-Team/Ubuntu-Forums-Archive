---
title: "Ubuntu won't load"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by kevindubrow on 2010-02-19
Hi, I'm using Ubuntu Netbook Remix. It had been running fine until now. During startup, it hangs on the splash screen for a while and some error message pops up. I attached an image of what it says.

I'm not sure what happened. I ran no updates nor did I install any programs last time the computer was running.

Could someone help me get my netbook running again? Thanks!

---

### Post by undecim on 2010-02-19
Looks like a problem with hard drive or SSD.

---

### Post by Gone fishing on 2010-02-19
Looks like a drive problem to me.

Start in recovery mode to get more information as to what device is the problem (when does it hang)

The I think you need to use fsck to fix the problem. I'm trying to find an easy fsck howto :D

---

### Post by kevindubrow on 2010-02-19
Awesome, thanks so much. I just don't know how I would get to the terminal from here.

---

### Post by Gone fishing on 2010-02-19
OK found this 

[http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html](http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html)

I don't suppose it will start in recovery mode (single user mode is init 1), but try it it will give you a better idea of when the system is hanging. So you might have to use a live CD or bootable flash drive and use fsck from the live CD.

Choose recovery mode from the grub menu

---

### Post by kevindubrow on 2010-02-19
Oddly enough, I do have a bootable USB on ne. So do I just run it live, go tithe terminal and run fdisk?

---

### Post by kevindubrow on 2010-02-19
Hey, one more  question: I am about to run fdisk, but the guide says I have do designate my file type. When I right click on the disk and hit properties, it says that it's ext3/ext4.

What command would I type in according to that guide?

Thanks so much for your help!

---

### Post by Gone fishing on 2010-02-19
fsck not fdisk

You need to run the command on the device that is failing - got to go do a screen shot of when the boot process stops in recovery mode

---

### Post by argos3016 on 2010-02-19
Do you want to make a new fs?
mkfs.ext4 OR
mkfs.ext3
mkfs.ext2


Choose your flavour!!

---

### Post by Gone fishing on 2010-02-19
If you run fdisk you will remove the date and add a new file system or partition. This is Ok if you want to re install. If you have a separate home partition this might be the easiest way to fix the system. Just reinstall and make sure you DON'T format the home partition.

fsck is tool for fixing ext partitions if they have errors.

Now I don't pretend to be an expert on fsck but the link I gave should give you an idea it going to be something like fsck /dev/sda1

---

### Post by kevindubrow on 2010-02-20
Hey, I'm sorry but I'm pretty sick and I may be missing something.

Whats going on right now is sda1 is failing to load. This SSD uses the ext3/ext4 file system. I don't want to reinstall, I just want to fix whats wrong. I have a lot of files I can't afford to lose on this computer.

Through running the live USB drive, I can go through the files, so I don't think something is wrong with the drive itself.

I got up to the point where I was about to run fsck, but according to that guide you sent me, I have to designate what file system the drive is or else it will default to ext2 and corrupt my files more.

So what do I type in so that fsck knows that the file system is ext3/ext4. Do I just type fsck.ext3 /dev/sda1? I just want to avoid messing up things more.

Thanks so much for your patience.

---

