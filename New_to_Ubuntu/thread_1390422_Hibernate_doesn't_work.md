---
title: "Hibernate doesn't work"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by Yerushalmi on 2010-01-25
Hey folks,

I'm completely new to Ubuntu but learning it slowly slowly. Most questions I've been able to figure out myself but this one's giving me some trouble...

Every time I set the computer to hibernate, the CPU starts churning, the writing-to-disk light turns on, and the screen goes dark... and that's all that happens. The computer doesn't shut down. Indeed, as soon as I touch the mousepad or a key, the login screen pops up as if I had just come back out of hibernate.

Now, previous threads in the forum have said that if your swap file is less than your RAM you can't hibernate. And this is indeed the case here - my system monitor indicates I have 994.2 MiB of memory but only 227.4 MiB of swap. I don't know how to increase my swap file, though.

I have two drives on this computer - one the internal 3.5 GB drive that only has 540 MiB available (I honestly have no clue what's taking up all that space - since I only this week got this computer and erased everything on it, is it possible that all 2.9 used GiB are from the Ubuntu operating system?) and a 13.2 GiB disk that's almost entirely empty (another thing I don't understand, because it's labeled as 16 GiB). Obviously I'll want to put the swap file on the disk.

So... how do I do that?

Thanks in advance.

---

### Post by stoogiebuncho on 2010-01-25
The swap file is actually it's own partition that is formatted as swap when you install Ubuntu.  You have the option of saying how much space you want to give it when you install, but if you want to change the size later, my guess is that the easiest way to do so is to burn a GParted live CD ([http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")), boot it up, and start the partition editor.  It should be easy to see which partition is the swap partition, and you should be able to enlarge it fairly easily.

Backup all your data first, or course.

And for you other issue - whenever I don't know where all my hard drive space has gone, I start up Applications > Accessories > Disk Usage Analyzer and if gives you a nice graph showing what's taking up all the space.

Good luck.

---

### Post by audiomick on 2010-01-25
Getting a gparted CD is a good idea. You can also run it from the live CD, or install it and run it from your Ubuntu install. The thing is, if you want to operate on a partition, it has to be unmounted, so it is a bit simpler to do it from the live CD or the gparted CD.

A fresh Ubuntu install that I did recently had around 2.7 GB in the / partition. It had a separate /home partition. Your 2.9 sounds about right.

As a first step, do
```
fdisk -l
```
in a terminal, and post the output here, so we can see where you are at.

---

### Post by Yerushalmi on 2010-01-26
I'm at work now and I'll try out what you've both said when I get home tonight - but I wanted to post and say that I discovered just before bed last night where the missing section of the 16GB disk is. It turns out it's already got a 2-or-more-gig swap partition on it (that my brother, who gave me the computer, had placed). What I don't get is why the computer doesn't recognize and use it.

---

### Post by Yerushalmi on 2010-01-26
Responses:

-Typing "fdisk -l" into the console does nothing - it just gives me the same command line again.

- I've formatted, reformatted, rereformatted, and done everything I could think of in the Disk Utility window to the external 16GB drive, but no matter how many times or in how many different ways I create the swap partition (even if I allocate the entire drive to being a swap file), it still doesn't increase the mere 227 MB listed under System Monitor.

---

### Post by audiomick on 2010-01-26
sorry, needs root priveliges 
```
sudo fdisk -l
```
That just reads out a list of your partitions. It should show you that the swap partition is really there.

---

### Post by Yerushalmi on 2010-01-26
Thanks! It worked this time (how do I grant myself root privileges by default? It's very annoying to be asked for my password all the time when nobody else uses the computer!)


Here's the output (it would probably have been different every three minutes when I was rewiping the drive over and over and trying to pick a different partition scheme that might work):


Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00001f7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         461     3702951   83  Linux
/dev/sda2             462         490      232942+   5  Extended
/dev/sda5             462         490      232911   82  Linux swap / Solaris
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 16.3 GB, 16288579584 bytes
64 heads, 32 sectors/track, 15534 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x0009ad8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9537     9765872    c  W95 FAT32 (LBA)
/dev/sdb2            9538       15534     6140928    5  Extended

---

### Post by audiomick on 2010-01-26
Hi.
Firstly, you **do not** want to give yourself root priveliges by default. It is not only other users; the fact that you aren't root is also one of the things that makes Linux so resistant to viruses and such.

Also, the password request is a useful reminder that you are about to do something that might break your system if you do it wrong.

Quite apart  from that, I believe it to be against the code of conduct of this forum to tell someone how to do that. And I don't know how to anyway...


to your output:
Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00001f7e

```
Device Boot Start End Blocks Id System
/dev/sda1 * 1 461 3702951 83 Linux
/dev/sda2 462 490 232942+ 5 Extended
[COLOR="Red"]/dev/sda5 462 490 232911 82 Linux swap / Solaris
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)[/COLOR]

Disk /dev/sdb: 16.3 GB, 16288579584 bytes
64 heads, 32 sectors/track, 15534 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x0009ad8b

Device Boot Start End Blocks Id System
/dev/sdb1 1 9537 9765872 c W95 FAT32 (LBA)
[COLOR="SeaGreen"]/dev/sdb2 9538 15534 6140928 5 Extended[/COLOR]
```

In red, there is a swap partition on the smaller of the two drives. This will be the one that the system is using, I would say. Given that the drive is so small, it makes a certain amount of sense to remove it and give the space to the the partition sda1

In green there is an extended partition /dev/sdb2 which has no logical partitions in it. This extended partition is a good deal larger than your current swap, but I am afraid I don't know exactly how big. I don't know how to convert blocks to bytes.

Anyway, that is where to put your new swap partition. Use gparted to do this, and to remove the small swap partition /dev/sda5 and the extended partition it is in, /dev/sda2. It will also show you the sizes in GB.

**Take note:** messing around with this will mean that the boot process will not be able to find the old swap that you have removed, that it still thinks is there. I don't know if this will prevent you from booting or not. You have to correct the fstab file. You should wait for someone to come who can explain this to you; I don't know enough about it.
There is some info about it here
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://manpages.ubuntu.com/manpages/hardy/man5/fstab.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/fstab.5.html)

and about UUIDs here
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by Yerushalmi on 2010-01-26
I wasn't aware about the root privileges thing. I'm afraid I'm still very new to this!

The partition you labeled in green is what I attempted to create as a swap partition; I guess my last attempt left it as extended by accident. I'd used Disk Utility to make these attempts, and I'm frankly still rather confused as to why that isn't sufficient!

Anyway, what alternatives do I have to the gparted CD? I'm on a netbook without a cd drive. Can I run such a program from my bootable USBstick (which is what I used to install ubuntu in the first place)?

---

### Post by stoogiebuncho on 2010-01-26
> **Yerushalmi said:**
> Anyway, what alternatives do I have to the gparted CD? I'm on a netbook without a cd drive. Can I run such a program from my bootable USBstick (which is what I used to install ubuntu in the first place)?

Yes, you can use the USB.  I can't remember if Ubuntu has the program labeled GParted, or just something generic like Partition Editor, but it should be in one of your menus.

---

### Post by audiomick on 2010-01-26
Gparted is on the live CD, so if you have made a bootable USB out of that, it is there
system>  administration> gparted

An extended partition is not a mistake per se. You can only have 4 primary partitions on a drive, so having an extended is a good thing. Within an extended partition you can make lots of logical partitions, I think 64.

---

### Post by Yerushalmi on 2010-01-27
Okay, I booted from the USBstick and rewiped the 16GB drive. I created a 6GB swap partition and found within GParted on that drive an option called swapon, which I activated, and voila! My system monitor displays a 6GB swap file!


So I restart the computer, boot from my regular hard drive... and it's using the 200meg hard drive swap file. Anaargh!


Here's my new fdisk output.

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00001f7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         461     3702951   83  Linux
/dev/sda2             462         490      232942+   5  Extended
/dev/sda5             462         490      232911   82  Linux swap / Solaris

Disk /dev/sdb: 16.3 GB, 16288579584 bytes
64 heads, 32 sectors/track, 15534 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x0004d2ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9537     9765872   83  Linux
/dev/sdb2            9538       15534     6140928   82  Linux swap / Solaris

---

### Post by J V on 2010-01-27
try this:

```
sudo dd if=/dev/zero of=/swapfile bs=1024 count=1000
sudo mkswap /swapfile
sudo swapon /swapfile
echo "/swapfile swap swap defaults 0 0" | sudo tee -a /etc/fstab
```

---

### Post by Yerushalmi on 2010-01-27
Actually immediately after posting that I said to myself, is GParted is in the download center, i could try that. So I did, and it worked - I now have a 6-gig swap file. But hibernate still doesn't work. Could I have a completely different problem?

EDIT: Okay, I don't get this - the system upon reboot keeps reverting to the 200-MiB swap file and I have to choose the 6-gig one manually each time. Even upon erasing the 200-mb partition, which I thought would force it to look for a different swap file, merely meant that I had no swap file until I designate the 6-gig one manually, again each time. And hibernate still doesn't work :(

---

### Post by Yerushalmi on 2010-01-27
Okay, so now I've reinstate the old 200-MB swap file and, from what I can tell, restored everything to exactly the way it was before...


...and my computer now does not activate EITHER swap file upon bootup. And hibernate still doesn't work.

Here's my fdisk output:

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00001f7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         461     3702951   83  Linux
/dev/sda2             462         490      232942+   5  Extended
/dev/sda5             462         490      232911   82  Linux swap / Solaris

Disk /dev/sdb: 16.3 GB, 16288579584 bytes
255 heads, 63 sectors/track, 1980 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d2ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1275    10241406   83  Linux
/dev/sdb2            1276        1980     5662912+   5  Extended
/dev/sdb5            1276        1980     5662881   82  Linux swap / Solaris


----------

This particular incarnation of the problem has been solved. However, hibernate still doesn't work; I'll create a new thread to deal with it.

---

