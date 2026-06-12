---
title: "RE-installing in same partitions - to fix errors"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by den160593 on 2009-02-28
Hi,

I had some pretty bad errors with my Ubuntu which I can't fix. So I was wondering, how could I easily re-install it, to make it the default again.

The thing is that I have dual boot, and I have important things on my Windows XP second boot (I have a back-up, but I'd prefer not to have to use it), and I already have partitions set up for Ubuntu, which is where it currently is.

So how could I get it to install in that same partition?

I did: ```
sudo fdisk -l
``` and my results were:

Disk /dev/sda

Device Boot goes from /dev/sda1 - 3... then has a gap and continues from /dev/sda 6-9. Why's this?

Also, device /dev/sad2 has a weird ID of f and is called a W95 Ext'd. What does this mean? The other ones are all HPFS/NTFD and have an ID of 7

Lastly, /sda9 has an ID of 83 and is called Linux. Is this in some way special?

Thanks,
Den

---

### Post by albinootje on 2009-02-28
> **den160593 said:**
> 
Device Boot goes from /dev/sda1 - 3... then has a gap and continues from /dev/sda 6-9. Why's this?


Please post the complete output of "sudo fdisk -l" here, then it is much easier for us to help you with your question.

---

### Post by den160593 on 2009-02-28
[IMG]http://i12.photobucket.com/albums/a247/den160593/linuxpartitions.jpg[/IMG]

---

### Post by kansasnoob on 2009-02-28
That is not a common output of:

> lance@lance-desktop:~$ sudo fdisk -l
[sudo] password for lance: 

Disk /dev/sda: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002940f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1146     9205213+  83  Linux
/dev/sda2            2293        3736    11598930    5  Extended
/dev/sda3            1147        2292     9205245   83  Linux
/dev/sda5            3578        3736     1277136   82  Linux swap / Solaris
/dev/sda6            2293        3577    10321699+  83  Linux

Partition table entries are not in disk order


That's what we need!

---

### Post by den160593 on 2009-02-28
I can't copy it, do you need the start and end and block values? Cos i got everything else there.

Can i copy from root shell? Because I don't have access to Ubuntu graphically

---

### Post by albinootje on 2009-02-28
> **den160593 said:**
> I can't copy it, do you need the start and end and block values? Cos i got everything else there.

Can i copy from root shell? Because I don't have access to Ubuntu graphically

You can do this :
```

sudo fdisk -l > /home/output.txt

```
Is it a dual-boot ? You can access Linux-partitions from MS-Windows  on the same machine :
[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

---

### Post by albinootje on 2009-02-28
My current disk looks like this :
> 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          18      144553+  83  Linux
/dev/sda2              19        1234     9767520   83  Linux
/dev/sda3            1235        9729    68236087+   5  Extended
/dev/sda5            1235        2207     7815591   83  Linux
/dev/sda6            2208        3180     7815591   83  Linux
/dev/sda7            3181        4153     7815591   83  Linux
/dev/sda8            4154        4396     1951866   82  Linux swap / Solaris
/dev/sda9            4397        9729    42837291   83  Linux

As you can see the Extended partition has several logical partitions, and /dev/sda4 is not there.

---

### Post by den160593 on 2009-02-28
None of them work... They won't open the Linux partition

---

### Post by den160593 on 2009-02-28
[IMG]http://i12.photobucket.com/albums/a247/den160593/linux2.jpg[/IMG]

I wrote it up and put it like this. Pretty sure all data is correct. Hope this is ok.

---

### Post by albinootje on 2009-02-28
> **den160593 said:**
> 
I wrote it up and put it like this. Pretty sure all data is correct. Hope this is ok.
Looks like you can go ahead and reinstall Ubuntu on /dev/sda9.

---

### Post by den160593 on 2009-02-28
ok, so in installation i tell it to manually install there, and it won't affect windows?

and do i have to delete it somehow? or will install overwrite?

---

### Post by albinootje on 2009-02-28
> **den160593 said:**
> ok, so in installation i tell it to manually install there, and it won't affect windows?

and do i have to delete it somehow? or will install overwrite?

Choose "manual" during the partitioning step in the Ubuntu installation, then use / as mount point for /dev/sda9, and choose to format that /dev/sda9 partition, and nothing else.
Then that should be fine.

---

### Post by -kg- on 2009-03-01
As long as he defines a swap partition also, right?

---

### Post by den160593 on 2009-03-01
Worked, and my Windows XP is still alive :) Thanks heaps!

---

### Post by albinootje on 2009-03-02
> **-kg- said:**
> As long as he defines a swap partition also, right?

I saw that he didn't have a swap partition, and I decided not to mention it.
We can discuss for hours whether a swap partition (or swap file) is 
really needed or not, but I also assumed that the machine of the OP was not that ancient, and the computer usage that very heavy, that a swap partition was really needed.
If the OP runs into trouble a swap file is the quickest way, without repartitioning/resizing_partitions, to get more virtual memory.

And, to the OP, I'm glad to see the new installation went fine. :)

---

