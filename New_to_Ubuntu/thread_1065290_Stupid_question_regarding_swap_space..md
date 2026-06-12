---
title: "Stupid question regarding swap space."
date: 2009-02-09
forum: New to Ubuntu
---

### Post by OneMixDJ on 2009-02-09
Greetings,

Another stupid question from a newbie if you don't mind.

Can I use a separate drive as swap space for my primary drive?

If yes, can someone tell me how this can be done?

Thanks!

Regards,

OneMixDJ

---

### Post by unplugged23 on 2009-02-09
I'm still pretty much a noob to partitioning to so someone please correct me if I'm wrong, but i don't think that would work unless you somehow managed to configure an lvm swap.

---

### Post by llamakc on 2009-02-09
The swap partition can be on a second, installed drive.

What's your current layout? Post the contents of the below:

```

sudo fdisk -l 

```

That is a lowercase L. The above command will return your current disk layout in the below fashion.

```

ken@llamakc 06:32:05:/etc/init.d$ sudo fdisk -l
[sudo] password for ken: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a9a1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         127     1020096   82  Linux swap / Solaris
/dev/sda2             128        6502    51207187+  83  Linux
/dev/sda3            6503       19457   104061037+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6180339b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3187    25599546   83  Linux
/dev/sdb2   *        3188        9729    52548615   83  Linux

```

Cut/paste your results here. 

Also, any changes you make to the second drive will be permanent and data on that drive will be lost. Be aware of that before proceeding.

---

### Post by egalvan on 2009-02-09
> **llamakc said:**
> The swap partition can be on a second, installed drive.

Or third, or fourth, or whatever number your motherboard and wallet can support... :)

A swap on a separate drive, which is on a separate channel, will make for faster access.
 Server-type and HPC-type machines do this routinely.


> any changes you make to the second drive will be permanent and **data on that drive will be lost.**
Be aware of that before proceeding.

That depends on HOW he makes the changes...

Using a good partition manager will reduce the chances of losing data.
Of course, back-ups of valuable data is ALWAYS recommended when mucking around with this stuff.

Gparted LiveCD is a good choice,
as is PartedMagic LiveCD, (even though the latter has changed to a Microsoft-clone interface).

Use Windows to defrag the drive, then use the partition manager to shrink the Windows partition, then make a swap out of the space you freed up.

---

### Post by llamakc on 2009-02-09
> **egalvan said:**
> Or third, or fourth, or whatever number your motherboard and wallet can support... :)

A swap on a separate drive, which is on a separate channel, will make for faster access.
 Server-type and HPC-type machines do this routinely.




That depends on HOW he makes the changes...

Using a good partition manager will reduce the chances of losing data.
Of course, back-ups of valuable data is ALWAYS recommended when mucking around with this stuff.

Gparted LiveCD is a good choice,
as is PartedMagic LiveCD, (even though the latter has changed to a Microsoft-clone interface).

Use Windows to defrag the drive, then use the partition manager to shrink the Windows partition, then make a swap out of the space you freed up.

Yes, those caveats apply. I'm not sure this is an "Absolute Beginner" discussion though.

Using GParted is no different than using fdisk if the additional drive has no data on it that is required.

---

### Post by egalvan on 2009-02-10
> **llamakc said:**
> Yes, those caveats apply.** I'm not sure this is an "Absolute Beginner" discussion though.**

Using GParted is no different than using fdisk if the additional drive has no data on it that is required.


Well, lots of beginners have been led by the hand down this road...
a very large majority come through OK.
This is done all the time for dual-boot installs.

I guess my problem with your post was the "no-nonsense, it WILL happen" tone;

*any **changes you make** to the second drive **will be permanent** and **data on that drive will be lost**.*

There was no "be careful, this can wipe the data off your drive, if you don't follow instructions";
We should not make beginners afraid, we should teach them caution.

It reminds me of the first time I applied labels to existing partitions;
 Gparted said that data would be lost, and lo and behold, the data was lost... :)
lucky for me, I was experimenting on a fresh install, so nothing lost. 
I DID learn to heed such "no-nonsense" warnings.. :)
Now I use a newer Gparted than what was on 8.04 LiveCD, and have not had that problem...

Since I still (painfully) remember my "beginner" status with Ubuntu,
I can feel the beginner's pain in all this.

ErnestG

ErnestG

---

### Post by OneMixDJ on 2009-02-10
Greetings llamakc,

Sorry, I just noticed your reply while in class.

I'll be sure to post promptly when I get home.

Thanks!

---

### Post by Rolcol on 2009-02-10
You can also create a swap file but I don't think it can be used for hibernation.  Swap files are more manageable since you can resize the file anytime.  Just edit step 1 and 3 to make the file on the mounted drive.  Honestly, I think a partition would be better in this case.

> **Rolcol said:**
> A swap file should not cause a performance loss unless the file is vastly fragmented on the same individual drive.  The big benefit of a swap file (in my opinion) is that it's more manageable.  If, for example, you need more space, just increase the size of the file without having to shutdown to modify partitions.  I've read multiple times that the 2.6.* Linux kernels usually maintain the same performance between both methods.

Sample method of creating and using a swap file:

(The preceding hash (#) means that the command should be ran as root)

1) Create the file (2GB in this example):
```

# dd if=/dev/zero of=/swap bs=1024 count=2097152

```2) Make it usable as swap:
```

# mkswap /swap

```3) Edit fstab so it may be used on startup
```

# echo -e "/swap\tnone\tswap\tsw\t0 0" >> /etc/fstab

```4) Activate it for use immediately
```

# swapon -a

```

---

### Post by OneMixDJ on 2009-02-12
> **llamakc said:**
> The swap partition can be on a second, installed drive.

What's your current layout? Post the contents of the below:

Cut/paste your results here. 

Also, any changes you make to the second drive will be permanent and data on that drive will be lost. Be aware of that before proceeding.

Hi Everyone,

Sorry for the delay, here are stats below:

[IMG]http://www.geocities.com/onemixdj/screenshot.png[/IMG]

Right now, my primary drive is a 12GB drive which is half is for swap.

I want to add a 10GB and designate that drive as the swap for the 12GB instead of the 12GB doing both.

I also have a puny 3GB drive which in this description is /dev/sdb.

I only have this to work on setting up as a shared drive to my Windows XP machines via Samba. In the scenario described above, this would be the 3rd drive. 

Thanks again!

---

### Post by egalvan on 2009-02-13
> **Rolcol said:**
> You can also create a swap file but I don't think it can be used for hibernation.  Swap files are more manageable since you can resize the file anytime.  Just edit step 1 and 3 to make the file on the mounted drive.  Honestly, I think a partition would be better in this case.

Linux uses the swap for hibernation. Recommended size is thus larger than physical RAM.
Obviously, the swap cannot be shared with other OS's if hibernate is in use.

I don't use hibernate, and share swap with multiple *nix.

---

### Post by egalvan on 2009-02-13
> **OneMixDJ said:**
> 

primary drive is a 12GB drive, half is for swap.

You show two different swap partitions.
Unless you have special circumstances, you only need one.

> 
I want to add a 10GB and designate that drive as the swap for the 12GB instead of the 12GB doing both.

Using a separate hard drive can speed up swap access. Good Idea.
I do this in my home "server".

> 
I also have a puny 3GB drive which in this description is /dev/sdb.

I only have this to work on setting up as a shared drive to my Windows XP machines via Samba. In the scenario described above, this would be the 3rd drive. 
Thanks again!

3GB is small by today's standards, but if it fills a need, go for it.
You may not need or want anything more.

---

### Post by glotz on 2009-02-13
Check the wiki out [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by gjoellee on 2009-02-13
If you have a lot of RAM (like 2GB and more) and you don't use any specific RAM eating operations you won't need a lot of swap.

I use Arch Linux, I have 2GB RAM and 500mb SWAP which is a lot more then what I actually need, but it is all about the computers specs and what you usually do with it.

---

### Post by OneMixDJ on 2009-02-17
Hey Guys,

I want to thank you all for your time and advice.

I'm going to work on my machine first chance I get (hopefully this weekend).

THANKS!!!

---

