---
title: "problems with dormant mode"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by 2blue on 2009-02-02
Hi
I have xubuntu on an old laptop. For the moment every thing is working fine except for one thing; computer will not go into hibernation mood. In other words there is something that prevents the system from going into hibernation and it knows it (if that makes any sense). 

This is a very small laptop with 750 KB RAM (that is at least what the system monitor detects). I don't know how much RAM there really is because this computer came originally with two memory cards each 125 MB, and I replaced them with two new ones each 512 MB. I think max RAM was set as 512 MB by the producers, but I'm not shore. Processor is 700 MHz if I remember correctly.

Is is the very limited resources of this computer that prevents Xubuntu from hibernation or some kind of setting that can alter?

---

### Post by taurus on 2009-02-02
How much space did you create for swap partition?  Open a terminal and post the output of this command.

```
free -m
```

---

### Post by 2blue on 2009-02-02
Hi
I got this:

             total       used       free     shared    buffers     cached
Mem:           755        695         60          0        254        216
-/+ buffers/cache:        224        531
Swap:          298          0        298


I don't know what I did when I installed. I was aiming at xubuntu taking over the entire harddisk. I use xubuntu/ubuntu because it slided on to my machine rather effortlessly and everything worked right away. Can you make any sense of this chart?

---

### Post by taurus on 2009-02-02
To use hibernation option, your swap partition should be at least 1.5x more than your RAM and it looks like your swap partition is smaller than your RAM.

---

### Post by 2blue on 2009-02-02
These numbers might be easier to read. The diagram got all messed up after posting. 

total    755
used     700      
free      54     
shared     0
buffers  254
cached   217

-/+ buffers/cache: used:228  free:527

Swap: total:298 
Swap: used:   0 
Swap: free: 298

What is swap partition really? how do I change it?

---

### Post by taurus on 2009-02-02
> **2blue said:**
> These numbers might be easier to read. The diagram got all messed up after posting. 

**total    755**  <-- RAM
used     700      
free      54     
shared     0
buffers  254
cached   217

-/+ buffers/cache: used:228  free:527

**Swap: total:298**  <-- Swap
Swap: used:   0 
Swap: free: 298

What is swap partition really? how do I change it?

You have to shrink your root filesystem (/), making room.  Then, you have to expand your swap partition, taking up that new unallocated space.  And since you have the installer to create the partitions for you, your / is probably a primary while your swap is probably a logical partition.  Therefore, you need to expand the extended partition first before you can use that new space in the logical partition.

What's the layout of your harddrive then?

```
sudo fdisk -l
```

---

### Post by 2blue on 2009-02-02
I get this

Disk /dev/sda: 6007 MB, 6007357440 bytes
255 heads, 63 sectors/track, 730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3df93df8


/dev/sda1 Start:1    End:692 Blocks:5558458+ Id:83  System:Linux
/dev/sda2 Start:693  End:730 Blocks:305235   Id:5  System:Extended
/dev/sda5 Start:693  End:730 Blocks:305203+  Id:82  System Linux swap/Solaris

---

### Post by taurus on 2009-02-02
If you want to resize your harddrive, you have to use gparted from either Ubuntu LiveCD (can your machine even boot from it?) or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).  Then, you can shrink your /dev/sda1 and expand /dev/sda2 to take up that unallocated space.  Now, you can expand /dev/sda5 to use the whole extended space.  

While you are doing all that, the UUIDs for both /dev/sda1 & /dev/sda5 would change so you need to edit /etc/fstab & /boot/grub/menu.lst on /dev/sda1 (your harddrive) to reflect the new UUIDs.

---

### Post by 2blue on 2009-02-02
Yes my machine boots from CD and runs live from CD too. I need some kind of idiot proof parting system, a wizard or something. 

I use this machine as an extra work station and internet access. Compared to the new Vista computer my brother got just before Christmas this old thing runs fast. My brothers new laptop is a large and powerful thing, believe it or not. 

I hardly ever store anything on the harddisk. I use usb memory sticks and external harddrive which xubuntu recognises just fine. 

I feel this partition problem might be my fault as I really don't understand the difference between the options I can choose from when installing xubuntu. I probably have chosen the wrong thing.

---

### Post by taurus on 2009-02-02
Well, you can either resize your harddrive with gparted from the LiveCD or you can reinstall.  And if you reinstall, you can use gparted from the LiveCD to remove all the partitions.  Then, create two partitions, one for / and one for swap.  However, make swap partition twice as large as your RAM.  Then run the installer process.  When you get to the partitions screen, pick Manual option and mount the first partition to / (you must mount it / or it will complain about no root filesystem) and format it.  You don't have to do anything with the swap partition since the installer should know what to do with it.

But if you don't feel like reinstalling, then you have to do something like in my previous post.

---

### Post by 2blue on 2009-02-02
Thanks for your help :)

Is removing all partitions with gpartet preferable when istalling? ...even a must? I never thought of this as a possible problem, believing that the installer CD fixed everything. I see I have to do some thinking and trying here.

---

### Post by taurus on 2009-02-02
Since you need to repartition your harddrive again the way you want, creating a larger swap partition, it's best to remove everything and start from the beginning.

I am sure there are other ways but at least this is probably the simplest.

---

