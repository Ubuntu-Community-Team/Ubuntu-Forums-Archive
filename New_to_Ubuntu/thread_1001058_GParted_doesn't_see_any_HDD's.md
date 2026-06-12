---
title: "GParted doesn't see any HDD's"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by x0prah_Winfr3yx on 2008-12-03
Hello, this is my first post. I'm very new to Ubuntu, so you may have to exercise some patience with my lack of knowledge.

I have a 120gb hard drive with Ubuntu as the only OS on it. I'd like to add either Vista or OS X to my boot, but in order to do that i'll need to partition my HDD to accept a new OS.

I downloaded Gparted because I hear it's the only way to partition with a GUI. after it's install, i launched the app by using the command line:

```
sudo gparted hdb
```

The GUI loads, but it doesn't display any HDD, logically my system does have one. Can someone break down what i'm doing incorrectly, or simply link me to find what i'm looking for?

Thanks.

---

### Post by Het Irv on 2008-12-03
Try using GParted from the LiveCD, since you won't be able to change anything from your normal Ubuntu partition anyway (the drive is in use, so you can not make changes).


You also may want to look up how to Restore GRUB, you will need that.

---

### Post by grepnix on 2008-12-03
Try this guide:-

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=1)

---

### Post by Michael.Godawski on 2008-12-03
Try ```
sudo gparted
```
without the hdb.

I hope you have done a back-up, because playing around with partitions is slightly dangerous. ;)

I also would run gparted from the live cd which you can download here:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

And feel free to ask...

---

### Post by x0prah_Winfr3yx on 2008-12-03
> **Michael.Godawski said:**
> Try ```
sudo gparted
```
without the hdb.

I hope you have done a back-up, because playing around with partitions is slightly dangerous. ;)

I also would run gparted from the live cd which you can download here:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

And feel free to ask...

thanks for the heads up on backing up. i know all too well the dangers of partitions. until last week, i had vista home running, failed a dual boot with os x, many many times. i decided to give up on those two and switch to linux.

perhaps i always wanted to be as cool as you guys. perhaps...

i'm going to use the Live CD route for now, thanks for your responses.

---

### Post by Duck2006 on 2008-12-03
Some info on using gparted.

[http://wiki.partedmagic.com/index.php/Using_GParted](http://wiki.partedmagic.com/index.php/Using_GParted)

From the installion you can install gparted from your Synaptic Package Manager. To partition fron within ubuntu installion you have to make sure the partition your going to work with is unmounted, so the live cd of gparted or parted magic will be easyer.

---

### Post by Captain_tux on 2008-12-03
Here's the link to a somewhat similar problem I had:

[http://ubuntuforums.org/showthread.php?t=996303]("http://ubuntuforums.org/showthread.php?t=996303")

And also, a very good website at Psychocats:

[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

Hope this helps!

---

