---
title: "installing Jaunty while preserving files"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by RoflKarnage on 2009-05-10
Hey all first post here

So my seagate hdd containing my windows died today. So I decided to install ubuntu. However on my 2nd hdd (which has no operating system) I have a lot of existing files (music, movies etc) that I want to preserve for when I get a new harddrive and such. So I tried to install but on step 4 ubuntu only gives me the option to either use the entire harddrive or manual. When i go into manual, install can't detect that the hdd has used space in it and will only give me the option to completely format the entire drive. Am I just doing something dumb or is there a specific way to do this.

---

### Post by mafaldaspeaks on 2009-05-10
> **RoflKarnage said:**
> Hey all first post here

So my seagate hdd containing my windows died today. So I decided to install ubuntu. However on my 2nd hdd (which has no operating system) I have a lot of existing files (music, movies etc) that I want to preserve for when I get a new harddrive and such. So I tried to install but on step 4 ubuntu only gives me the option to either use the entire harddrive or manual. When i go into manual, install can't detect that the hdd has used space in it and will only give me the option to completely format the entire drive. Am I just doing something dumb or is there a specific way to do this.

Am not an expert myself but as far as I know, doing the install I think you're doing will really erase everything on your hdd. I think only existing OS/es are detected, not files. So better back up everything first before your start installing.

---

### Post by kansasnoob on 2009-05-10
OK, so you've been able to run the live CD?

If yes, then go to Terminal and post the output of:

```
sudo fdisk -l
```

BTW that's a lower case L!

---

### Post by kansasnoob on 2009-05-10
Well, I'm soon off to bed, but the basic thing is to identify which drive you want to install Ubuntu on, and the existing partitioning of the drive.

Like we must know how many primary partitions already exist on that drive. (There's a 4 primary limit!)

Have you removed the failed drive?

---

### Post by RoflKarnage on 2009-05-10
I used the USB creator to create a Live USB and using that at the moment.

The failed drive has been removed yes. 

ok the sudo fdisk command gives me this output

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x501cf028

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sda5               2       30401   244187968+   7  HPFS/NTFS

I really don't know what's going here ^^;; but it's definitely the harddrive I'm trying to install on.

in terms of partitions, right now it's just one that uses the entire drive.

---

### Post by servicetech on 2009-05-10
I'd pick up and extra drive for $30 - $40 and install your OS on it. Have a separate drive for your media. Works MUCH better if you ever need to reformat you OS drive.

---

### Post by RoflKarnage on 2009-05-10
well wouldn't I just format the OS partition if I needed to? and my replacement drive that's coming is way bigger than the capacity I need at the moment so it would become my media drive.

---

### Post by pauna on 2009-05-10
> **RoflKarnage said:**
> well wouldn't I just format the OS partition if I needed to? and my replacement drive that's coming is way bigger than the capacity I need at the moment so it would become my media drive.

I would suggest that you do the following:
[LIST=1]
[*]Install your new drive into the machine.
[*]Boot into a live Ubuntu session (from DVD or USB).
[*]Partition and format the new disk into a media drive as you like.
[*]Copy everything from the smaller disk into your new media disk.
[*]Start installing Ubuntu into your smaller disk, which at this point can be safely reformatted since the data has been copied.
[/LIST]

---

### Post by RoflKarnage on 2009-05-10
But isn't what I'm trying to do in the first place already possible? I would wait for the new drive but it says it'll most likely arrive on the 20th =\ kind of a long time to be sticking with a USB OS

---

### Post by RoflKarnage on 2009-05-11
bump

---

### Post by RoflKarnage on 2009-05-13
bump

come on I seriously doubt that it's impossible to do what I'm trying to accomplish here. Does anyone know what's going on?

---

### Post by bodhi.zazen on 2009-05-13
> **RoflKarnage said:**
> bump

come on I seriously doubt that it's impossible to do what I'm trying to accomplish here. Does anyone know what's going on?

You can do this, you just need to be careful you understand partitioning.

Start with :

1. Make a back up of your data. Installation usually goes smoothly, but there are occasional problems.

2. Next, make sure you understand partition terminology.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

3. You can do this automagically using the installer, using freespace on the existing partition. (AKA Guided - Resize).

See: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Step 8 in particular. This is a "bug" in the installer, at the first step it only appears to use the entire disk. 

4. Or you can do it manually . Boot the live CD and use gparted to resize your existing partitions.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Now you can also use the free space to install ubuntu.

---

### Post by RoflKarnage on 2009-05-14
thx for the reply bodhi

I tried to use the graphical install, but the problem is there is no guided resize option at all. Only manual or guided use entire disk

---

