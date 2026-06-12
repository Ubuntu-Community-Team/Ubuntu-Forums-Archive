---
title: "From openSUSE to Ubuntu?"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by blnl on 2009-01-22
Hello, I'm using openSUSE (GNOME) for 6 months already and I like it a lot. Still, I would also like to try Ubuntu, since I hear a lot of good things about this distro.

I plan to install Ubuntu on the following system:
```
MSI K7T266 Pro2-RU, AMD Athlon 1.4GHz, 768MB DDR SDRAM
SpeedTouch 120 USB Wireless
```
Assuming that Ubuntu has all necessary drivers for my hardware. If someone is aware of any possible issues, please let me know?

On this system I have a separate etx3 formatted */home* partition. Besides my files it also contains FireFox settings and bookmarks, Evolution settings and mailboxes, Keyring passwords...

How much of this will be picked up by Ubuntu?
I would like to avoid extra work configuring these applications if it is possible.

---

### Post by overdrank on 2009-01-22
Moved to  Absolute Beginner Talk

---

### Post by clive littlewood on 2009-01-22
Hi blnl

Welcome to the forums and Ubuntu.

Your best way to "prove" your system is to run Ubuntu from the live CD as a boot OS.

This will enable you to try all the apps and internet etc. before you fully install to your HD.

Make sure your BIOS is set to boot from CD

Hope this helps      :D


Clive

---

### Post by mister_pink on 2009-01-22
Ubuntu will pick up the firefox settings etc, but there is a chance things might get messed up. The issue is if one uses a different version to the other, or if ubuntu requires different settings to opensuse, then things may not work right and its possible they might get broken for opensuse too. I'd back thing's up before you try at least.

---

### Post by blnl on 2009-01-23
Thank you all for the advice!

> Your best way to "prove" your system is to run Ubuntu from the live CD as a boot OS.
I was searching for the Live CD, but without success. At the [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) I can only download one type of CD *ubuntu-8.10-desktop-i386.iso*.

Where can I find the latest Live CD?

---

### Post by TheLions on 2009-01-23
liveCD is also a install CD

8.10 is the lastest, 9.04 is in alpha stage

---

### Post by clive littlewood on 2009-01-23
Hi

Just download the iso file, ubuntu-8.10-desktop-i386.iso.

Burn this to a CD-R and then run as boot.

Job done.       :D

If everything is OK you can then use the install option on the CD.

Regards

Clive

---

### Post by rustutzman on 2009-01-23
If you create a user with the same username and password as your openSUSE user it will attempt to use the same /home directory. As stated with two different distros that may end up being more of a problem than you want. Better to create a different username in Ubuntu. After installation backup your /home/ubuntu_user then try copying the config from your openSUSE to the ubuntu user giving the appropriate permissions on the files and see what happens. If it goes bad just restore the backup profile and go from there.

You might get away with trying a few things at a time and see how it works instead of a wholesale profile copy.

Russ

---

### Post by blnl on 2009-02-22
I just tried installing Ubuntu 8.10, but it didn't work for me.

I have aborted installation at the partitioning setup because Ubuntu didn't recognize any of my existing partitions. Actually, there were only two options available:
 1. Guided - use entire disk
 2. Manual

If I correctly understood, Guided partitioning would remove all my existing partitions and create new ones. This is absolutely not what I need.
However, when I selected the Manual partitioning, it listed all my existing partitions correctly. I'm not really in the mood for setting all mounts and file systems (I have 11 partitions on 4 HDDs), so I aborted the installation.

This is unfortunate, but I'll try installing Ubuntu again when the next release gets out.

---

### Post by carml on 2009-02-22
You can also a software like Virtualbox to try all the OS you want to.;)

---

### Post by LowSky on 2009-02-22
> **blnl said:**
> I just tried installing Ubuntu 8.10, but it didn't work for me.

However, when I selected the Manual partitioning, it listed all my existing partitions correctly. I'm not really in the mood for setting all mounts and file systems (I have 11 partitions on 4 HDDs), so I aborted the installation.

This is unfortunate, but I'll try installing Ubuntu again when the next release gets out.

How did it not work? It did what it was supposed to but you didn't feel like partitioning, so who's fault is that?

---

### Post by blnl on 2009-02-27
Sorry LowSky, I really do not understand the Ubuntu partitioning philosophy.

Correct me if I'm wrong.
Ubuntu offers several different Guided partitioning options:
 o Guided - resize DISK(###), partition # and use free space
 o Guided - use entire disk
 o Guided - use the largest continuous free space

So, why were these options not available for me? :confused:
I was only offered the "Guided - use entire disk" option.

Another thing that I did not mention is that I already have the linux partitions ready (swap, /, /home). I expected from Ubuntu to recognize them and offer me the choice of partitioning.
That is in fact what openSUSE does. I never manually partition or mount my drives in openSUSE. Once the partitions are in place it offers me the choice with correctly mounted partitions.
Therefore, I expected from Ubuntu to do a similar thing. I'm sorry if I'm spoiled by openSUSE. ;)
Also, on the Official Ubuntu Documentation web-page I was reading about partitioning. Since it mentions a *fully automatic mode*, I expected it to do that as well.
>  partman

    Allows the user to partition disks attached to the system, create file systems on the selected partitions, and attach them to the mountpoints. Included are also interesting features like a fully automatic mode or LVM support. This is the preferred partitioning tool in Ubuntu.


The main reason that I aborted the installation is because I did not get all expected Guided options. Thus, I thought that something is wrong.

So if you say that the partitioning options I got are perfectly normal, I'm prepared to try again (although the partitioning is not fully automatic).

---

### Post by Ben Page on 2009-02-27
Use manual partitioning option, select the partition you like to install Ubuntu to and mount it as "root" and mark the checkbox to format it, and do the same thing with the Home partition (just select the desired partition and right click - edit). I always do the manual partitioning (because of dualboot with 7).

---

### Post by mister_pink on 2009-02-27
It's normal for it to not offer you all the guided or automatic partitioning options. The installer is quite conservative - if it doesn't fully know whats going on it won't offer options that might break things. If you have a really simple partitioning scheme that it understands then it will offer more options.

But seriously, manual partitioning takes about 30 seconds. I've never used anything else.

---

### Post by RyanVanDiemen on 2009-02-27
> **blnl said:**
> I expected from Ubuntu to recognize them and offer me the choice of partitioning.
That is in fact what openSUSE does. I never manually partition or mount my drives in openSUSE. Once the partitions are in place it offers me the choice with correctly mounted partitions.
Therefore, I expected from Ubuntu to do a similar thing. I'm sorry if I'm spoiled by openSUSE. ;)


Well, once you move from OpenSUSE to Ubuntu you will find many things that Ubuntu lacks compared to OpenSUSE. For one thing, there`s nothing as yast in Ubuntu... I`m not saying Ubuntu is not a good system (I`m using it myself; KDE4), but mentioning your issues with installer, you will find more things once you`re using the system. Anyway, considering your computer`s HW, Ubuntu (gnome) is the best option for you. It`s really good (and stable) system.

---

### Post by blnl on 2013-01-25
I just installed Ubuntu 12.04. It was a success!
Therefore, marking this thread as SOLVED.

---

