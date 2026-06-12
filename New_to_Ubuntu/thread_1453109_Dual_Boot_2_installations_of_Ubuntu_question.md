---
title: "Dual Boot 2 installations of Ubuntu question"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by mikodo on 2010-04-12
Hello everyone,

I would like to dual boot 2 different installs of Ubuntu to do some testing of an appication. The last time I had a dual boot situation between Ubuntu releases (Hardy and Karmic in in the same extended partition, the boot was slow). Then I tried to install Debian Lenny on some remaining space in the extended partition, and that didn't work. Long story short, I hosed my system and wound up re-installing Karmic as seen in fsdik below and the screen shot of gparted. The way things are set up now, everything is running like quick silver and I am hesitant to change anything!

My question is this:  If I do a new Live CD install of Ubuntu 9.04 or 10.04 (after the new release is out), to the remaining unallocated space, should I have any problems with my excellently running initial install of Ubuntu 9.04? I wouldn't be bringing forward my /home partition from Karmic, I would just let the installer install everything automatically to the largest unallocated space (I have one more primary partition left to use).  Sound doable? Anyone have any reservations about this plan?

 ```
mikodo@mikodo-desktop:~$ sudo fdisk -l
[sudo] password for mikodo: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        3040    14651280   83  Linux
/dev/sda3            3041       15684   101562930    5  Extended
/dev/sda5            3041        3526     3903763+  82  Linux swap / Solaris
/dev/sda6            3527       15684    97659103+  83  Linux
mikodo@mikodo-desktop:~$ 

```

Thank you.

---

### Post by WinterRain on 2010-04-12
I would do a manual partition and tell it where you want it to install. But that's just me, I don't trust auto anything.

---

### Post by mikodo on 2010-04-12
> **WinterRain said:**
> I would do a manual partition and tell it where you want it to install. But that's just me, I don't trust auto anything.
Yes, I was thinking that too. Can I in the manual install, tell it to use the remaining unallocated space, and then install as it wants to then, without any other partitioning done other than to make it all installed in the last pimary partition?

And.... would everything continue to run as well, as it is for me now, in my first install of Ubuntu 9.10? That's the real question.

---

### Post by WinterRain on 2010-04-12
When doing a manual install, just make the partition you want to use,- "/"

Pretty easy actually.

---

### Post by WinterRain on 2010-04-12
> **mikodo said:**
> 

And.... would everything continue to run as well as it for me now in my first install of Ubuntu 9.10? That's the real question.

Everything should be fine. But there are no guarantees with computers, as with anything else in life. Just backup any important data, which you should be doing anyway.

---

### Post by mellort on 2010-04-12
Hey mikodo,

I agree with WinterRain: you should set up the install manually to ensure everything is going to turn out as you want. The installer really is fairly straightforward. Make sure to select the same swap space that you already use for your current Ubuntu version; no need to have two swap spaces.

Cheers

---

### Post by mikodo on 2010-04-12
> **WinterRain said:**
> Everything should be fine. But there are no guarantees with computers, as with anything else in life. Just backup any important data, which you should be doing anyway.
Thanks for the reply, I do do backups. Your response is reassuring; I'll leave the thread open a bit before adding it as solved, to see if anyone else has any gems of info.

Thank you.

---

### Post by scrapmetal on 2010-04-12
Follow WinterRain's instructions and all should be fine.:)

---

### Post by WinterRain on 2010-04-12
> **mellort said:**
> Make sure to select the same swap space that you already use for your current Ubuntu version; no need to have two swap spaces.



Actually, there's no need to do anything for swap, as ubuntu will see that there is one there already.

---

### Post by Bucky Ball on 2010-04-12
Manual partition. I think 'unallocated space' means 'unpartitioned space' so you would probably get an error if you try auto. 

Go manual and point the install to the partition you want to use. From your output there is no telling which partition is the empty one and if it is in an extended partition, it will definitely NOT be read as 'unallocated space'.

Nothing about your original install will be effected as the two installs will be on totally separate partitions.

The swap file belongs to the 9.04 install and thus will also be on another partition, so you need to make a swap file on the same partition as your new install.

This method is a new install on a new partition as if you were putting it on a new drive. The original 9.04 install has NOTHING to do with the new install if you are putting it on a SEPARATE partition.

---

### Post by WinterRain on 2010-04-12
> **Bucky Ball said:**
> 
The swap file belongs to the 9.04 install and thus will also be on another partition, so you need to make a swap file on the same partition as your new install.

With all due respect, swap "belongs" to nothing. A new install will "see" the swap partition and include it. Over the years, I've never had a problem sharing swap partitions.

---

### Post by mikodo on 2010-04-12
> **Bucky Ball said:**
> Manual partition. I think 'unallocated space' means 'unpartitioned space' so you would probably get an error if you try auto. 
```

Go manual and point the install to the partition you want to use. From your output there is no telling which partition is the empty one and if it is in an extended partition, it will definitely NOT be read as 'unallocated space'.

```
Nothing about your original install will be effected as the two installs will be on totally separate partitions.

The swap file belongs to the 9.04 install and thus will also be on another partition, so you need to make a swap file on the same partition as your new install.

This method is a new install on a new partition as if you were putting it on a new drive. The original 9.04 install has NOTHING to do with the new install if you are putting it on a SEPARATE partition.

So make one more Primary Partition, of the remaining unallocated space on the Hard drive, before a fresh live install and point to the new partition as the partition to install (/)?

Have I got it?

---

### Post by WinterRain on 2010-04-12
> **mikodo said:**
> So make one more Primary Partition, of the remaining unallocated space on the Hard drive, before a fresh live install and point to the new partition as the partition to install (/)?

Have I got it?

Yes.

---

### Post by mikodo on 2010-04-12
Thanks everyone,

Solved!

Mike

---

### Post by Bucky Ball on 2010-04-13
> **WinterRain said:**
> With all due respect, swap "belongs" to nothing. A new install will "see" the swap partition and include it. Over the years, I've never had a problem sharing swap partitions.

Yep, will see the swap and use it, will even see home and use it if you want, if you are re-installing on the SAME partition. This is going on another partition entirely and the original is staying on its original partition.

You can't make a primary partition in an extended partition and you can only have one primary per drive from memory. Ubuntu, unlike windows, is quite happy not to be on a primary partition, and will even happily exist on a partition inside an extended partition. Rethink.

---

### Post by mikodo on 2010-04-13
> **Bucky Ball said:**
> Yep, will see the swap and use it, will even see home and use it if you want, if you are re-installing on the SAME partition. This is going on another partition entirely and the original is staying on its original partition.

You can't make a primary partition in an extended partition and you can only have one primary per drive from memory. Ubuntu, unlike windows, is quite happy not to be on a primary partition, and will even happily exist on a partition inside an extended partition. Rethink.
Thanks for the clarification and pointers. As you pointed out, "*This is going on another partition entirely and the original is staying on its original partition.*".** That is what I wanted.** I wanted it completely separate of the initial install partition. So, to do that, I can make a 4th Primary partition of the unallocated space on my hard drive, and install the second OS on it, with everything new including (/), (/home) and Swap.

If I wanted to, I could make in the existing extended partition, another logical partition and install the new OS, sharing Swap, /home (if I wanted), and could, given the space, make more logical partitions in the extended partition, with more OS's installed in each.

All right; Now to decide what I might want to do, down the road, and what I will need to accomplish that. Maybe the use of logical partitions gives me the most flexibility.

**I'll rethink.** 

Mike

---

### Post by WinterRain on 2010-04-13
> **Bucky Ball said:**
> Rethink.

I don't need to rethink anything. I have done it many times and it works. Why are you telling me otherwise? You only need 1 swap partition on any 1 drive. You don't need to reinstall to the same partition to use swap. You can have 8 OS's all using the same swap partition. I have been a linux user for 7 years, and have my own computer repair business. Rethink.

---

### Post by atomizer on 2010-04-13
I second Winterrain. Done it a lot of times, and no problem.
The swap has its own partition and you can point every install to the same swap.

---

