---
title: "2nd hard drive not recognized by install"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by jadeeyedgirl on 2010-03-15
First of all, hello everyone! I've hit a bit of a snag in my new Ubuntu install, and I'm hoping someone can give me a hand.

I've used Linux for about a year now, but I'm fairly new to Ubuntu. Or installing. To be honest, I've really only used our university's Linux lab and ssh'ed in from home. I figured it was time for an install of my own, and Ubuntu was a logical choice. So, I get the Linux basics and some terminal commands. Other than that, I'm fairly useless. Hence, why I'm here.

I recently got a new SATA hard drive that I wanted to install Ubuntu 9.1 on as a second hard drive. When I go to install, the hard drive doesn't show. Instead, it shows my main hard drive with Windows 7, which I do not want to install on.

I've gone through every post I can find on the topic and nothing has really worked. Sorry if this has already been answered recently and I missed it, but I've spent hours searching. Maybe I'm looking for the wrong thing, but most of the posts I saw didn't quite have the same circumstances or I already tried the advice.

The drive is recognized by BIOS, and it is also seen by GParted. I formatted it as both ext3 and ntfs using GParted. I set it as the initial boot disk and it is read by the Live CD as /dev/sda1. It's also read by Disk Utility, which says that it is healthy and it passes all the tests. It's also set as bootable (but I tried when that was not enabled as well, just for the sake of trying). But when installing, it just does not show up as an option. It's frustrating how long I've been tinkering with this thing.

From sudo fdisk -l:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24dd0f2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x67746774

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       38914   312466432    7  HPFS/NTFS

So... thoughts?

---

### Post by Fenris_rising on 2010-03-15
I had this when I had an IDE HDD and a SATA HDD on my system. The simple method, for me was to unplug the IDE HDD when the PC was off plug the sata in and it was then picked up by the install process. Obviously I had no grub so I had to use the [esc] key on my keyboard to get the boot device menu up to select which drive to boot once both were attached of course.

Other than that you may need to install dmraid? this is some sort of fakeraid which helps mount sata drives. I may be wrong but they may point you in the right direction I hope.

regards

Fenris

---

### Post by jadeeyedgirl on 2010-03-15
Ironically enough, when I had my IDE hard drive plugged in right before my new SATA, the install read both hard drives without an issue.

Now, I don't know if this is relevant to what you were saying but I am able to mount the drive when running on the live CD. I am having no other issues messing with it, other than not being able to install on it.

---

### Post by jadeeyedgirl on 2010-03-16
Oh, and I tried both Native IDE and AHCI mode for my hard drives too. I found that was a suggestion on another forum to try AHCI so I did, but it was unsuccessful.

---

### Post by egalvan on 2010-03-16
> **jadeeyedgirl said:**
> Ironically enough, **when I had my IDE hard drive plugged in right before my new SATA, **the install read both hard drives without an issue.

So what drives are plugged in now?

And what do you mean by
 *when I had my IDE hard drive **plugged in right before **my new SATA*

What does "right before" mean? 
Plugged in first, as in "physical order" (first is A, second is B)
OR
Plugged in first, as is "time-wise" (plug one in, then disconnect, then plug in the second)


> Now, I don't know if this is relevant to what you were saying but I am able to mount the drive when running on the live CD. I am having no other issues messing with it, other than not being able to install on it.

Curious, as the installer is using the same back-end (parted) as the LiveCD.

OK,
so when you mount the drive with the LiveCD,
 i take it you can "see" it with Gparted? (disk partitioner)

If so, then what happens if you immediately (without re-booting) try the "install" option on the desktop to install to the second drive?

---

### Post by jadeeyedgirl on 2010-03-28
> **egalvan said:**
> So what drives are plugged in now?

And what do you mean by
 *when I had my IDE hard drive **plugged in right before **my new SATA*

What does "right before" mean? 
Plugged in first, as in "physical order" (first is A, second is B)
OR
Plugged in first, as is "time-wise" (plug one in, then disconnect, then plug in the second)


Sorry for the confusion. I have two SATA hard drives in now (my main with Windows 7, and the 2nd one that I want to install Ubuntu on. My IDE hard drive was plugged in before my new SATA time-wise. I had used the IDE to run Ubuntu, but disconnected it before plugging in my new SATA.

> **egalvan said:**
> 
Curious, as the installer is using the same back-end (parted) as the LiveCD.

OK,
so when you mount the drive with the LiveCD,
 i take it you can "see" it with Gparted? (disk partitioner)

If so, then what happens if you immediately (without re-booting) try the "install" option on the desktop to install to the second drive?


When I use GParted, I can indeed see the 2nd drive. When I try and use that install option, it does the exact same thing... it only shows my main HD and not the 2nd one.

---

### Post by jadeeyedgirl on 2010-03-28
So, I just started spending more time with my good friend Google, and managed to fix the issue. I have spent hours searching for anything relevant, and found this link today after only a couple minutes:

[http://serverfault.com/questions/84132/ubuntu-9-10-installer-doesnt-recognize-the-hard-drive](http://serverfault.com/questions/84132/ubuntu-9-10-installer-doesnt-recognize-the-hard-drive)

Not sure how I searched differently or how I missed this before but removing dmraid in Synaptic allowed Ubuntu to see the 2nd hard drive. 

So thanks to everyone for your help, and hopefully some other confused newbie will see this in the future and have a much easier time with it than I did :D

---

