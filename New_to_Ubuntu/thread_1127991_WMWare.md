---
title: "WMWare"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by serros88 on 2009-04-17
Hi,

Need to install XP on my PC in order to use a customer application and connect my laptop on their company LAN.

Difficult to do that? (or better to install XP native on HD multi-boot)

Pretty urgent for me.
Thanks a lot
Serros

---

### Post by Flag on 2009-04-17
Am using Virtual Box, no probs, easy to install through synaptic.

---

### Post by serros88 on 2009-04-17
well,

I dont see Virtual Box in Synaptics!?

Another name or I miss a container?
serros

---

### Post by kpkeerthi on 2009-04-17
I'd recommend VirtualBox. Easy to install and use.

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)
[www.psychocats.net/ubuntu/virtualbox](www.psychocats.net/ubuntu/virtualbox) 

Running a guest on a virtual machine can be quite taxing on the host sometimes and requires plenty of RAM. I have 2 GB of RAM and my Windows XP guest had 512 MB alloted to it. I often found my linux host starting to swap soon after my XP guest was started and the performance of both guest and host began to crawl. If RAM is deficit I suggest you do native installation. 

Note: Alloting more RAM to guest will only worsen the performance of the host further.

---

### Post by serros88 on 2009-04-17
ok,

to install XP native, need to do new partitioning on HD.
what can i use to do that?

Thanks
Serro

---

### Post by kpkeerthi on 2009-04-17
> **serros88 said:**
> ok,

to install XP native, need to do new partitioning on HD.
what can i use to do that?

Thanks
Serro

Just boot with Ubuntu Live CD. Press ALT + F2 and enter **gparted**. You can use it to shrink your existing partition and create a free space (a new partition).

Now install Windows XP to the partition you just created. XP will overwrite your GRUB with its own bootloader. But don't worry, ubuntu is still there. You just have to restore it back: [http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11](http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11). GRUB should now contain Ubuntu and XP listed.

**NOTE: Make sure you back up before you play with your partitions. You have been warned.**

---

### Post by serros88 on 2009-04-17
i am installing Virtual Box, using the help of
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

but they select an image of another version of Linux and myself I want to install XP!

how can I do that????

Serros

---

### Post by kpkeerthi on 2009-04-17
[Windows XP on VirtualBox]("http://www.google.com/search?q=ubuntu%2C+windows+xp+on+virtualbox")

---

### Post by serros88 on 2009-04-17
Hi,

I installed Virtual Box and it works very well, great.

Have a little ridiculous problem:

- I setup the display of Windows XP full screen and don't find how to get back with a small window.

Now when I launch XP, it takes the whole screen.
 
Any idea how to come back with previous setup? (I don't find in settings)

Txs
Serros

---

### Post by DGortze380 on 2009-04-17
> **serros88 said:**
> Hi,

I installed Virtual Box and it works very well, great.

Have a little ridiculous problem:

- I setup the display of Windows XP full screen and don't find how to get back with a small window.

Now when I launch XP, it takes the whole screen.
 
Any idea how to come back with previous setup? (I don't find in settings)

Txs
Serros

HostKey + F

On my mac it's Left Command, so I would guess it's Left Ctrl + F

---

### Post by serros88 on 2009-04-17
ya,

it's Right Control + F

Txs:D

***********************************************************
Now to share the same folder between Linux and XP???????????
I defined a share, but cannot find it from XP!!!!!

How does it work?

---

### Post by DGortze380 on 2009-04-17
> **serros88 said:**
> ya,

it's Right Control + F

Txs:D

***********************************************************
Now to share the same folder between Linux and XP???????????
I defined a share, but cannot find it from XP!!!!!

How does it work?

You have to install VirtualBox Guest Additions

---

