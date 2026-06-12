---
title: "How do I go from Wubi to dual boot?"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by Trandre on 2011-01-16
How do I go from Wubi to dual boot? What is the easiest way, when I want to keep all my settings as is?

---

### Post by migs73 on 2011-01-16
I believe this is how it's done;

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Regards 

Mike

---

### Post by dostumai on 2011-01-16
Once you've partitioned and installed another OS onto your system, you'll get an option on startup to choose which partition you want to run.

---

### Post by migs73 on 2011-01-16
> **dostumai said:**
> Once you've partitioned and installed another OS onto your system, you'll get an option on startup to choose which partition you want to run.

Not with a WUBI install I'm afraid. It is not Grub that gives the boot choice in WUBI.

If you were to install Ubuntu it would have default settings and the Grub screen would give you the options of Ubuntu (newly installed full version) or windows, and if you selected windows you would then get the original boot screen offering Ubuntu (the WUBI one) and windows.

Follow the link I posted.

---

### Post by alzie on 2011-01-16
The link migs73 gave should guide you through the process.  I tried to do this some time ago (different instructions) and it failed miserable so I would urge you to **BACKUP** all your important files in both Windows and Ubuntu just in case it goes badly.

---

### Post by migs73 on 2011-01-16
> **alzie said:**
> The link migs73 gave should guide you through the process.  I tried to do this some time ago (different instructions) and it failed miserable so I would urge you to **BACKUP** all your important files in both Windows and Ubuntu just in case it goes badly.

+1 to that, never can be to careful!!

---

### Post by Trandre on 2011-01-16
Can I be sure that I will not wipe my Windows 7 install, running the manual installation as described in the link?

---

### Post by migs73 on 2011-01-16
>  Can I be sure that I will not wipe my Windows 7 install, running the manual installation as described in the link? 

You can't! Altering any partition under any OS can be catastrophic. Hence the advice to backup all your data.

EDIT you might want to have search around for the many good guides to dual booting and partitioning in the forums

---

### Post by migs73 on 2011-01-16
Whilst we are on the subject

Any changes you want to make to your windows partition, should be done from within windows (defrag and shrink) if you need to make space for an Ubuntu partition.

---

### Post by Trandre on 2011-01-16
Following this command 

Format new partition if not done so already - make sure it's empty, large enough and unmounted
WARNING -- the next command will wipe all existing data on /dev/sda5
Code:
mkfs.ext4 /dev/sda5

I got this output: 

famfem@ubuntu:~$ sudo -i
[sudo] password for famfem: 
root@ubuntu:~# grub-install --version
grub-install (GNU GRUB 1.98-1ubuntu9)
root@ubuntu:~# mkfs.ext4 /dev/sda5
mke2fs 1.41.11 (14-Mar-2010)
Could not stat /dev/sda5 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
root@ubuntu:~# 

What shall I Do further?

---

### Post by Trandre on 2011-01-16
I have 360gb space on the disk. No movies or space demanding stuff. How large should I make the partion?

---

### Post by migs73 on 2011-01-16
You maybe missed my edit further up, please, please check the forums about how to partition and dual boot.

The problem looks like you have not created a partition called sda5, the WUBI transfer instructions are about how to get the install onto your new partition (which doesn't seem to be there, and may not be called sda5 depending on your HDD partitioning set up).

I would advise a bit (a lot!!) more reading on the subject, as the possibility of corrupting/wiping your windows partition is quite real.

Although no permanent damage would be done (you did back up those files, right?? You would need to re-install windows/partition/install ubuntu.

---

### Post by Trandre on 2011-01-16
Thanx for the warning, I will read up a little before I go further. Yes I already have a fresh backup of my Windows files. The Win7 "cd" is a partition on the harddrive

---

### Post by Trandre on 2011-01-19
Back up the files I need in ubuntu and deinstalled the wubi. To make a safer approach to the partitioning. Well i thought anyway. Looking at youtubes on how to install the dual partition, it looked fairly simple. But when I tried to go through with a 10.10 cd a came almost straight to the partition tool. Here I downsized the win7 partition to 170 and had 130 something in free space.

My problem is that this was labelled unusable and the only option I had was revert.I tried to go for install now which was not possible. So I resized the win 7 partition to original size. Where did I go wrong?

---

### Post by Trandre on 2011-01-20
First i didnt get the option of installing side by side. So i tried to make a partition from windows as seen on print screen. But when i try to start the install now from the cd. It freezes after a while on the page displaying Ubuntu and the five dots. Any suggestions on how I can get past that freeze?
<img>http://ubuntuforums.org/attachment.php?attachmentid=181580&stc=1&d=1295553249</img>

---

### Post by Trandre on 2011-01-20
First i didnt get the option of installing side by side. So i tried to make a partition from windows as seen on print screen. But when i try to start the install now from the cd. It freezes after a while on the page displaying Ubuntu and the five dots. Any suggestions on how I can get past that freeze?
<img>http://ubuntuforums.org/attachment.php?attachmentid=181580&stc=1&d=1295553249</img>

---

