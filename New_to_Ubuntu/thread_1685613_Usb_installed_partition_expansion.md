---
title: "Usb installed partition expansion"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by JonathanEp on 2011-02-11
Okay i have a 4gb usb flash drive i installed Ubuntu 10.10 on it yesterday and made a 1500mb reserve for changes to be saved. i am already out of memory with this partition and cannot open gparted to try to expand it. how can i expand this partition to use the 1.6gb of extra space on my flash drive?

---

### Post by Mark Phelps on 2011-02-11
I'm guessing, because you didn't make it clear, that you're trying to expand partitions on the same USB from which you're running Ubuntu. Right?

You basically can't do that.

You have to mount partitions to use them and you can't work on mounted partitions.

You will have to find a way to boot from a GParted LiveCD or an Ubuntu LiveCD and THEN work on your Linux partitions on the USB drive.

---

### Post by C.S.Cameron on 2011-02-11
> **JonathanEp said:**
> Okay i have a 4gb usb flash drive i installed Ubuntu 10.10 on it yesterday and made a 1500mb reserve for changes to be saved. i am already out of memory with this partition and cannot open gparted to try to expand it. how can i expand this partition to use the 1.6gb of extra space on my flash drive?

Hi, welcome to the Forums:

Did you actually make a casper-rw partition? usb-creator makes a persistent file named casper-rw, A casper-rw partition does work for persistence. 

If you did make a casper-rw partition, boot the Live CD, plug in the flash drive and then use gparted.

If you are wanting to enlarge the casper-rw file, you can mount casper-rw using

```
sudo mkdir /media/casper
sudo mount -o loop casper-rw /media/casper/
```

I think you can copy the files from the old casper-rw file to a larger one that is mounted similarly.
(I have not tried this yet).

If you google this topic you can find some really complex methods.

---

