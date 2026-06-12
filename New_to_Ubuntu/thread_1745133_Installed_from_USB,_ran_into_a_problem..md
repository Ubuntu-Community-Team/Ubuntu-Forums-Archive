---
title: "Installed from USB, ran into a problem."
date: 2011-04-30
forum: New to Ubuntu
---

### Post by ShadeMK on 2011-04-30
I followed [this]("https://help.ubuntu.com/community/Installation/FromUSBStick#Creating a bootable Ubuntu USB flash drive") guide to create a bootable USB drive and install ubuntu.

So I go into my BIOS and make it boot from my thumb drive.

Once I get to the part where it asks me what I want to do (install ubuntu, run it from the USB drive, etc.) and I press install ubuntu.

Ubuntu loads and when I get to the point where it wants to really do the install (picture here: [http://i.imgur.com/EgraR.png](http://i.imgur.com/EgraR.png)) it says I don't have enough space. I assume it's trying to install into my thumb drive and I have no idea how to make it install to my hard drive.


This is the farthest I've ever gotten into an Ubuntu install and have no idea what to do.

My main operating system is Windows XP SP3 32bit.

---

### Post by oldfred on 2011-04-30
Have you used all four primary partitions? It cannot create an extended for the install if all four are used. 

Post screenshot of gparted or this from liveCD.

```
sudo fdisk -lu
```

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by ShadeMK on 2011-04-30
> **oldfred said:**
> Have you used all four primary partitions? It cannot create an extended for the install if all four are used. 

Post screenshot of gparted or this from liveCD.

```
sudo fdisk -lu
```

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)


Here is a screenshot of gparted: [http://i.imgur.com/n8MJ8.png](http://i.imgur.com/n8MJ8.png)

I don't believe I've willingly done anything with any partitions.

---

### Post by oldfred on 2011-04-30
It is saying sda is 3.73GB, is that your flash device? Some BIOS seem to promote a USB to sda and then your hard drive becomes sdb. It starts to get confusing, but grub/Ubuntu use UUIDs so it still works.

Can you choose sdb?

---

### Post by ShadeMK on 2011-04-30
> **oldfred said:**
> It is saying sda is 3.73GB, is that your flash device? Some BIOS seem to promote a USB to sda and then your hard drive becomes sdb. It starts to get confusing, but grub/Ubuntu use UUIDs so it still works.

Can you choose sdb?

Yes that is my flash device.

How would I go about choosing sbd?

Sorry, I'm quite new to this.

---

### Post by wilee-nilee on 2011-04-30
> **ShadeMK said:**
> Yes that is my flash device.

How would I go about choosing sbd?

Sorry, I'm quite new to this.

Upper right corner is a drop down.
[ATTACH]190581[/ATTACH]

---

### Post by ShadeMK on 2011-04-30
> **wilee-nilee said:**
> Upper right corner is a drop down.
[ATTACH]190581[/ATTACH]

Ah, thanks!

No other options are shown when I click that.

---

### Post by Quackers on 2011-04-30
What pc is this please? Are you using raid? Have you done any partitioning lately?
Are you on SATA3 ports?

---

### Post by ShadeMK on 2011-04-30
> **Quackers said:**
> What pc is this please? Are you using raid? Have you done any partitioning lately?
Are you on SATA3 ports?

Custom built from a few years ago.

Some of my specs: 

Motherboard: XFX nForce 750a SLI

CPU: 3.1GHZ AMD Athlon II X2 255

Graphics Card: EVGA GeForce 9500 GT 512MB 128-bit DDR2

I tried installing Ubuntu with Wubi first, but that didn't work very well. Wubi may have partitioned my disk, but I don't really know.

I don't believe I'm on SATA3 ports.

---

### Post by Quackers on 2011-04-30
If you boot from the usb and select "try ubuntu" and let the desktop load you can then open a terminal and run this command
```
sudo fdisk -lu
``` which is the one oldfred asked for earlier. Please quote its output in your next post, if any. Thanks.

---

