---
title: "Dual Boot Ubuntu 10.04 and 11.04 and Partitioning help please"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by mikodo on 2011-07-26
Hi,

I use 10.04 only on my computer. I have decided to start learning Unity. I would like to dual-boot with 10.04 and 11.04. See below the results of fdisk-l and a screenshot of gparted.

/dev/sda1 = boot and  (/) partition.
/dev/sda2 = Extended partition
/dev/sda5 = /home partition 
/dev/sda6 = swap partition

Can I use sda1 as boot and (/) for both 10.04 and 11.04, by doing a manual install, using the .iso cd of 11.04 to do it? I am actually using it now.

If so, if I un-install 11.04 in the future, will it mess up my ability to boot into 10.04? 

Could I use my /home partition (sda5) for /home with 10.04 and 11.04, without complicating things like config files?

If any of this is not possible or unwise to do; What would be recommended, for dual-booting my system?


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002efb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19530752   83  Linux
/dev/sda2            2432       38914   293038081    5  Extended
/dev/sda5            2432       38119   286658067+  83  Linux
/dev/sda6           38184       38914     5859328   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```Thanks.

---

### Post by Rex Bouwense on 2011-07-26
Since you are going to install 11.04, have you tried it out on a live CD or flash drive yet just to make sure that all your hardware and the new software will be playing nice together?  If you have done that, I would install side by side.  Alternatively you could probably install 11.04 in a virtual box if all that you want to do is learn unity.

---

### Post by mikodo on 2011-07-26
Yes, I could do either of these without risking screwing things up like I have in the Past.

Thanks.

---

### Post by mikodo on 2011-07-26
My wife just told me she needs me to help her, so I have to go.

Oh, 11.04 runs all my hardware from the CD.

Thanks.

---

### Post by Rex Bouwense on 2011-07-26
I am speaking of course from screwing up my stuff more than once and if there is a way to do something without a high probability of errors, I'm all for that.

---

### Post by mikodo on 2011-07-26
> **Rex Bouwense said:**
> I am speaking of course from screwing up my stuff more than once and if there is a way to do something without a high probability of errors, I'm all for that.


Ditto!

;)

---

