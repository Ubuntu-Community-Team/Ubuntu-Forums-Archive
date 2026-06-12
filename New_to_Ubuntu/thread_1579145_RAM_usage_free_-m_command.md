---
title: "RAM usage free -m command"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by arpit22x on 2010-09-21
Hi All,
 While I give a command (free -m) in console, it gives that RAM usage 1700 mb and it keeps on increasing from the time I login but the system monitor is showing only 400mb usage..... which is true??


Help please !!

---

### Post by zadehas on 2010-09-21
Here's my output of free -m:

```
             
             total       used       free     shared    buffers     cached
Mem:          2765       2626        139          0         98       1604
-/+ buffers/cache:        922       1842
Swap:         8103        120       7982

```

As you see, it reports 2626 MB used, although the system monitor reports 930 MB used. You need to add the "free", "buffers" and "cached" column to get the free memory on your system, or watch the third line below "used" and "free". On the "Mem:" line, this program counts cached memory as used.

---

### Post by bodhi.zazen on 2010-09-21
I suggest you read up on how Linux uses RAM

[http://distilledb.com/blog/archives/date/2009/02/22/swap-files-in-linux.page](http://distilledb.com/blog/archives/date/2009/02/22/swap-files-in-linux.page)

[http://www.cyberciti.biz/faq/linux-check-memory-usage/](http://www.cyberciti.biz/faq/linux-check-memory-usage/)

[http://www.linuxjournal.com/article/2770](http://www.linuxjournal.com/article/2770)

[http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html)

[http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage](http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage)

Otherwise you did not provide us with sufficient information to give a better answer.

How much RAM do you have and what are you doing ?

What is the exact output and what part do you not understand or what part do you have a question about ?

---

### Post by arpit22x on 2010-09-22
thanx bodhi.zazen for reply,

I just want to know whether it is harmful for my system if ubuntu uses 95 % of RAM. According to free -m, My used mem. increases upto 95-96 % after login.

---

### Post by 3rdalbum on 2010-09-22
> **arpit22x said:**
> thanx bodhi.zazen for reply,

I just want to know whether it is harmful for my system if ubuntu uses 95 % of RAM. According to free -m, My used mem. increases upto 95-96 % after login.

Not harmful. The amount used by cache can be reclaimed at any time when the system  needs to. And RAM is there to be used.

---

### Post by lloyd_b on 2010-09-22
> **arpit22x said:**
> thanx bodhi.zazen for reply,

I just want to know whether it is harmful for my system if ubuntu uses 95 % of RAM. According to free -m, My used mem. increases upto 95-96 % after login.

Not only not harmful, it's *desirable*.  Linux will use any and all free memory to cache data if it can do so, in order to improve performance.

With the "free -m" command, look at the line "-/+ buffers/cache".  This is telling you how much of your RAM is being used by *programs*, and is the most important value.  If/when a program needs more memory, Linux will release some from cache/buffer usage for it, so that first line of the "free" command doesn't give you an accurate picture of how much of your RAM is actually available for programs.

Lloyd B.

---

### Post by arpit22x on 2010-09-22
thanx all !!

---

### Post by bodhi.zazen on 2010-09-22
Unused RAM is wasted RAM.

Linux uses RAM very different then Windows.

---

### Post by philinux on 2010-09-22
> **arpit22x said:**
> Hi All,
 While I give a command (free -m) in console, it gives that RAM usage 1700 mb and it keeps on increasing from the time I login but the system monitor is showing only 400mb usage..... which is true??


Help please !!

[http://www.linuxatemyram.com/index.html](http://www.linuxatemyram.com/index.html)

---

### Post by arpit22x on 2010-09-24
hi,
My problem has not been solved yet, Now, when my RAM usage reached to 95 -96 %, running applications are automatically closed out. when I again turn them up, they will again crash. It seems like sufficient RAM is not available for them. Please help !!


gauranga@gauranga:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2987       2900         86          0         70       2267
-/+ buffers/cache:        562       2425
Swap:            0          0          0

---

### Post by plucky on 2010-09-24
> Swap: 0 0 0

Your swap file is not enabled.That is probably your problem.

What does ```
sudo swapon -a
``` show you?

---

### Post by arpit22x on 2010-09-24
I entered this 'sudo swapon -a'. It gives nothing. No result.

---

### Post by plucky on 2010-09-24
> **arpit22x said:**
> I entered this 'sudo swapon -a'. It gives nothing. No result.

Check if the swap partition is now on ```
free -m
```


If not post output of ```
sudo fdisk -l
cat /etc/fstab
sudo blkid
```

---

### Post by arpit22x on 2010-09-24
gauranga@gauranga:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2987       2829        158          0         21        675
-/+ buffers/cache:       2132        855
Swap:            0          0          0
gauranga@gauranga:~$ sudo fdisk -l
[sudo] password for gauranga: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2              11        3437    27527377+  83  Linux
/dev/sda3   *        3438       18412   120286687+   7  HPFS/NTFS
/dev/sda4           18413       38914   164675435    f  W95 Ext'd (LBA)
/dev/sda5           18413       26165    62275941    7  HPFS/NTFS
/dev/sda6           26166       38914   102398976    7  HPFS/NTFS
gauranga@gauranga:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=bc612f14-9043-433b-88bc-0c7d8540123a /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
gauranga@gauranga:~$ sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D9-050F" TYPE="vfat" 
/dev/sda2: UUID="bc612f14-9043-433b-88bc-0c7d8540123a" TYPE="ext4" 
/dev/sda3: LABEL="Main" UUID="7EB82599B82550C7" TYPE="ntfs" 
/dev/sda5: LABEL="Hari Bol II" UUID="01CAC2EC46F54530" TYPE="ntfs" 
/dev/sda6: LABEL="Hari Bol" UUID="2C30A9F330A9C464" TYPE="ntfs" 
gauranga@gauranga:~$

---

### Post by plucky on 2010-09-24
No swap partition was created when you installed.You already have 3 primary partitions and 1 extended partition.You should reduce one of your ntfs partitions within the extended partition and create a swap partition there.

See [Swapfaq](https://help.ubuntu.com/community/SwapFaq)

If you run windows 7 or Vista,use the windows disk management tool to resize the ntfs partition.

You have 3G memory installed,if you hibernate you will need the swap partition to be at least the size of ram.If not a 1G swap partition should be enough.

Good Luck

---

### Post by roemer2201 on 2011-04-21
> **arpit22x said:**
> Now, when my RAM usage reached to 95 -96 %, running applications are automatically closed out.

I'm having a similar problem, but i hope someone can answer my question to this topic:
My PC has 12GB RAM and no Swap. Sometimes my RAM is filled up to 95% and Ubuntu kills applications. I respect Ubuntu to preserve 5% of the memory for the system it, BUT ( ... let's calculate: 12GB * 1024 * 0,05 = ~ 600MB) ubuntu blocks me from using 600MB of my memory. 
So I would like to raise the 95% to 98% so that i can use about 400MB more than at the limit of 95% percent.

Is the a Way to configure this?

---

