---
title: "ubuntu disk copy"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by SumYunGy on 2009-02-22
Can I use ubuntu to copy a Windows XP System disk to a new drive that I will use to replace the original C: drive? I have tried several wintel free applications with no luck.

---

### Post by lykwydchykyn on 2009-02-22
Yes.  The most straightforward way is to use the dd command, like this:
```

sudo dd if=/dev/sda of=/dev/sdb

```
Where /dev/sda is the original disk and /dev/sdb is the new disk.  This is for whole disk copying; if you just want to move the partition around, things get trickier because of the way the windows bootloader works.

I've also made good use of the g4l boot CD, which you can get here:

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

---

### Post by SumYunGy on 2009-02-22
I will try it. Thanks for the information.

---

### Post by KuroYoma on 2009-02-22
Another good one is PING (Partimage is not Ghost)  It is a backup and restore utility that I use all the time.  I push my system a little and used to crash it 2 to 3 times a week and used this to restore a backup file.  I used it to migrate my system a few times to.  The ntfs shrink is option is still experimental so only use it after you have a normal backup already.

---

### Post by HermanAB on 2009-02-22
Most fancy looking disk copy programs use dd underneath.  You can even copy a disk over a network connection:
[http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

Cheers,

Herman

---

### Post by mringer on 2009-03-13
I copied my old disk successfully with dd as described above (thank you).
But the old disk was 12 G, the new one has a paper label that says 30G.
I tried to enlarge the (only) partition with parted, but parted thinks
the new disk is only 12G. I assume that this is because  dd  copied the 
recorded label as well as all the data. info parted says that you can
do mklabel but this destroys the partition.Please any advice? thankyou

---

