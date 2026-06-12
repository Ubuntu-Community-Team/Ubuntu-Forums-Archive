---
title: "Installing with Windows 7?"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by scottishbloke on 2009-12-27
Hi i just upgraded my pc this christmas,now running dual core,with 2gb ram and 160gb hdd,currently installed is windows 7,however i want to know if its possible i can still install karmic koala along side windows 7 on the ntfs file system as thats what my hdd currently is,ntfs?

---

### Post by taurus on 2009-12-27
You mean install Ubuntu with wubi?

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by scottishbloke on 2009-12-27
nope no wubi,want to install with the cd if possible?

---

### Post by taurus on 2009-12-27
Then you probably want to resize your harddrive, making some space (unallocated) at the end to install Ubuntu on it then.

---

### Post by scottishbloke on 2009-12-27
I see,i dont really know how to do that and i dont want to go muck my system up,perhaps i should just install inside windows 7 if this is ok?

---

### Post by Captain_tux on 2009-12-27
> **scottishbloke said:**
> I see,i dont really know how to do that and i dont want to go muck my system up,perhaps i should just install inside windows 7 if this is ok?

If you want Ubuntu inside Windows, then what you want is Wubi. If you want to dual boot, you'll have to make changes to your hard drive... not impossible or difficult, and there are lots of guides/tutorials you can Google for. Here's one to get you started: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If you have any problems, post the question and someone will help as best they could.

Good luck!

---

### Post by ssulaco on 2009-12-27
> **scottishbloke said:**
>  on the ntfs file system as thats what my hdd currently is,ntfs?
Linux does not use NTFS,like taurus said you will have to resize your disk free space to accomidate Ubuntu (dual boot)...read this,will give you info on dual booting:
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by sandyd on 2009-12-27
> **scottishbloke said:**
> I see,i dont really know how to do that and i dont want to go muck my system up,perhaps i should just install inside windows 7 if this is ok?
go to control panel -> Administrative Tools -> Computer Management -> Disk Management

shrink the windows partition, leave it as free space

when you get to the partitioining stage of installing ubuntu, select "use all free space" (or something like this).

---

### Post by thelethargarian on 2009-12-27
I have done this on many computers (two of them running Windows 7). Just follow these steps:
1. Put in the CD
2. Restart the computer.
3. Choose your language.
4. Choose either the live CD mode if you would like to try out the system before installing ("Try Ubuntu with out any change to your computer", or something like that), or install mode if you know you want to install (this mode is much faster since it is not running the whole operating system off the disk).
5. If you chose the live CD mode, double click the "Install" icon on the desktop and follow the simple instructions on screen. If you chose the install mode, follow the instructions on screen.
6. When you get to the partitioner, choose the manual option ("Define partitions manually", or something like that), choose the main partition (probably the largest. There may also be a recovery partition and a boot partition), and resize it to whatever size you would like to have left for Windows (It will tell you how much of this space is used, so resize it to at least a few gigabytes more than that). Click new space called "free space", and say "new partition". Make it about a gigabyte or so (many people disagree about this)and set the drop down menu to "use as swap" (swap space is used by the system as virtual RAM when all of your ram is used up). With the remaining free space, make a new partition and in the drop down menu, select "use as /" or "use as root". 
7. Continue the step by step instructions, and install.

This will give you a simple one partition Ubuntu system and will allow you to choose what operating system to boot at startup. I would reccomend to start here [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation), then, after you have the CD, use this nice tutorial with screenshots [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) or [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot).[URL="https://help.ubuntu.com/community/GraphicalInstall"]
[/URL]

---

### Post by kansasnoob on 2009-12-27
To dual-boot:

Step #1: Defrag Windows.
Step #2: Resize Windows with it's own tools:

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

Step #3: Install Ubuntu, this may be helpful:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

To perform a Wubi install:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by scottishbloke on 2009-12-27
Thanks for the info and advice everyone,looks like im going to be busy for a while doing all this,thanks,much appreciated

---

### Post by Captain_tux on 2009-12-27
Frankly, I'd defrag and run **chkdsk** at least a couple of times... can never be too safe with Windows.

---

### Post by ranch hand on 2009-12-27
If you have the LiveCD for Ubuntu I would boot to it and try it out an see how it gets along with your hardware.

Use the first option on the menu and it will install onto the ram and not touch your HDD.

One of the things you should do is go to System>Administration>GParted (sometimes labeled Partition Editor) and click on that to pull it up.  This will let you see how your HDD is set up right now.

All of the space is taken by MS.  There should be 3 partitions.  I do not know what they are titled and I do not have any on any of my boxes so I can't check.  One is small an contains the MS boot stuff Leave it alone).  The other 2 are your OS and a "recovery" partition.  "Recovery" is the last partiton (the one on the right end of the graphic display).

Assuming that it works fine, do you have the install disc for Win JerryLewis Pro (or whatever MS you have)?

If you have the disc this is good as the "recovery" partition is useless without it.  You should be able to get one through the computer manufacturer.  It should come with the computer but usually does not.

If you go to (still on LiveCD) System>Administration>System Monitor and pull it up you can click on the "file systems" tab and see how much of each mounted partition is used.  This will also be listed on the text in Gparted.

I would be surprised if you could not shrink that partition by 45 to 55GB and still leave unused space in it.

For the MS OS partition you should, I have heard, use the MS partition tool.  For the "recovery" partition gparted will do fine.

The problem is that you can only have 4 "primary" partitions on any HDD.  You need at least 2 partitions for Ubuntu bringing you to 5.

The way around this is to shrink the "recovery" partition and then format the unused space as an "extended" partition.  An 'extended" partition is a type of primary partition but you can make as many "logical" partitions inside it as you want.  I would recommend a 1/2 to 1GB partition at the very end of it for "swap", a 10GB partition at the beginning as / (root) and the rest in between as your /home partition.

There are guides for partitioning and you should read some.  I can walk you through it too.

You could also just set up the "extended" partition and point the Ubuntu installer partitioner at it and let it set it up.  This is not as good an installation in case of problems.

Wubi will install Ubuntu inside MS.  A lot of folks do this.  I, personally, think it is silly for this reason; Ubuntu installed on its own is a very good resource for MS recovery and data recovery.  If one system goes down, why loose both, is my position.

---

### Post by sandyd on 2009-12-27
> **thelethargarian said:**
> I have done this on many computers (two of them running Windows 7). Just follow these steps:
1. Put in the CD
2. Restart the computer.
3. Choose your language.
4. Choose either the live CD mode if you would like to try out the system before installing ("Try Ubuntu with out any change to your computer", or something like that), or install mode if you know you want to install (this mode is much faster since it is not running the whole operating system off the disk).
5. If you chose the live CD mode, double click the "Install" icon on the desktop and follow the simple instructions on screen. If you chose the install mode, follow the instructions on screen.
**6. When you get to the partitioner, choose the manual option ("Define partitions manually", or something like that), choose the main partition (probably the largest. There may also be a recovery partition and a boot partition), and resize it to whatever size you would like to have left for Windows (It will tell you how much of this space is used, so resize it to at least a few gigabytes more than that). Click new space called "free space", and say "new partition". Make it about a gigabyte or so (many people disagree about this)and set the drop down menu to "use as swap" (swap space is used by the system as virtual RAM when all of your ram is used up). With the remaining free space, make a new partition and in the drop down menu, select "use as /" or "use as root". **
7. Continue the step by step instructions, and install.

This will give you a simple one partition Ubuntu system and will allow you to choose what operating system to boot at startup. I would reccomend to start here [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation), then, after you have the CD, use this nice tutorial with screenshots [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) or [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot).[URL="https://help.ubuntu.com/community/GraphicalInstall"]
[/URL]
NO
please dont do that unless youve got the windows install/recovery disk handy

---

### Post by ranch hand on 2009-12-27
+1

---

### Post by Zoot7 on 2009-12-27
> **kansasnoob said:**
> To dual-boot:

Step #1: Defrag Windows.
Step #2: Resize Windows with it's own tools:

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

Step #3: Install Ubuntu, this may be helpful:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

To perform a Wubi install:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
This is the best way to go about it. you could resize the ntfs partition with something like Gparted, but then you've to repair the bootloader of Windows 7 before it'll boot again (assuming 7 is the same as Vista).

---

