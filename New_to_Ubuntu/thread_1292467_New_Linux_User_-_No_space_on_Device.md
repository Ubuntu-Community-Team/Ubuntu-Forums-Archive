---
title: "New Linux User - No space on Device"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by emilville on 2009-10-15
I've searched for help for the past 3 days. 
I've come up with little or no help. 
I know that the solution is here somewhere, 
it may have already been posted and solved. 
Or my puny brain is just to dumb for Linux. 

I'm about wipe my entire drive and go back to using M$Win...

My problem is I cannot download files, install files, because Ubuntu tells me that "No Space on Device" 

when i do a "df -h"

I see a 2GB disk 0% free, 100% used

I need to increase this disk and utilize my other 248GB

In window$ I can simply utilize the disk size or set quota on disk management. In ubuntu, i have no idea. Need your help, thanks.

---

### Post by Nesaskewatch on 2009-10-15
Just a hint; more details about your system would help a bit.  And threatening to go back to windoze won't get you anywhere but broke.

---

### Post by lrcaballero on 2009-10-15
Lets start by asking you, are you dual booting??? if yes you can do what is call "Partition" in windows, answer this first and we'll go from there. OK!!!  :KS

---

### Post by Merk42 on 2009-10-15
Since you're familiar with how to run commands, run:
```
sudo fdisk -l
```

---

### Post by 3rdalbum on 2009-10-16
Let me guess: When you installed Ubuntu as a dual-boot, you never moved the little slider to the left on the partitioning screen to tell Ubuntu to use more than the absolute minimum amount of space?

You might be able to boot up from the live CD and use the Partition Editor program to resize the Windows partition down and increase the size of the Ubuntu partition. If the Ubuntu partition is wrapped in a Logical/Extended partition, you might need to remove the Logical partition entirely before you can resize the Windows partition downward, and then reinstall Ubuntu into the free space.

---

### Post by emilville on 2009-10-16
> And threatening to go back to windoze won't get you anywhere but broke.

I am in no position to threat sir. 

> are you dual booting??

Nope. clean install of ubuntu

> sudo fdisk -l

I'll post the result when i get home. i'm currently at work

>  you never moved the little slider to the left on the partitioning screen to tell Ubuntu to use more than the absolute minimum amount of space?

aha, its a fresh install but you are correct i haven't moved any slider during installation. 

@ALL

Thanks a lot for your help. I'll post more information about my system. when i get home.

---

### Post by mapes12 on 2009-10-16
It may not be related to your problem but something else to check before you go back to the dark side...............

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by Harshana on 2009-10-16
You better try PARTITON MAGIC 8.0 in windows system.First install it and resize linux partition.You will be able to find PARTITION MAGIC 8.0 in an torrent zone.........

---

### Post by random turnip on 2009-10-16
Either re-instal or use the LiveCD to edit your partition so that you're using all your disk space, other wise Ubuntu only takes what it needs to install.

I did the same thing when i first installed Ubuntu a while back.

---

### Post by jrandolph on 2009-10-16
If its a clean install of Ubuntu on a 250gb drive - when you install you should jus be sure to use the entire disk space during the install process - but if you plan to dual boot i believe from what i have been told here its best to install your Microshit first and then install Ubuntu so it will automatically set it up for u

---

### Post by tarps87 on 2009-10-16
First before you try any resizing we need the output of this:

> **Merk42 said:**
> Since you're familiar with how to run commands, run:
```
sudo fdisk -l
```

It will show us what you hard drive looks like.

Also do you have a copy of the live cd? You probably installed it using this.
Also can you post the detailed output of df just in case it's behaving silly

---

### Post by emilville on 2009-10-16
/dev/sda1  *  1        1333 
/dev/sda2      1334  2333 

i couldn't copy the whole thing coz i'm posting this on another pc. 
since there is no disk space firefox is not letting me login

there are 4 other sda. 

my plan was to ....
mkdir /Documents/HD
sudo mount /dev/sda2 /Documents/HD

but i couldn't get past mkdir
it says "could not create directory no space available on drive"

---

### Post by Merk42 on 2009-10-16
> **emilville said:**
> /dev/sda1  *  1        1333 
/dev/sda2      1334  2333 

i couldn't copy the whole thing coz i'm posting this on another pc. 
since there is no disk space firefox is not letting me login

there are 4 other sda. 

my plan was to ....
mkdir /Documents/HD
sudo mount /dev/sda2 /Documents/HD

but i couldn't get past mkdir
it says "could not create directory no space available on drive"

Boot from the LiveCD then run sudo fdisk -l again

---

### Post by tarps87 on 2009-10-16
It sounds like you have 6 six partitions, the defaul install usally has two.

Could you post the output /etc/fstab, as you don't have a working connection I will tell you what I'd like to know.

Run the command **sudo blkid**

now **gedit /etc/fstab**

Now can you match up each line using the uuid and post the device number and mount point e.g.

/dev/sda1 /
/dev/sda2 /home
/dev/sda3 swap

It is possible you a partition for each drive, this will show us what has happened

---

### Post by emilville on 2009-10-16
The gedit showed multiple /dev/sda's 
unfortunately i cannot paste this since firefox in that pc does allow me to login to any website
this is clearly a mistake on my installation. 

You guys have been extremely helpful. I will just wipe the drive and reinstall ubuntu.

---

