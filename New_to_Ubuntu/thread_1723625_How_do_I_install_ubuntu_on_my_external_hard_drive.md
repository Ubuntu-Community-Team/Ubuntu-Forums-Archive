---
title: "How do I install ubuntu on my external hard drive?"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by David87123 on 2011-04-07
I have searched around and can't really find an easy guide to follow. I have an external hard drive and want to parition 100GB to install ubunut on it so I can boot from USB. Does anyone know how to do this??

Thanks Dave.

---

### Post by nothingspecial on 2011-04-07
Boot from the live cd.

When you get to the partitioning bit, choose manual or advanced or whatever they call it at the moment.

Make sure you choose the right partition. Choose to format it and use it as an ext4 journaling file system.

Give it a mount point of /

Go have a beer (or soft drink if under age).

You may also create a swap partition or you could just make a swap file later.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by David87123 on 2011-04-07
I am booting ubuntu from usb to install does this matter?

---

### Post by nothingspecial on 2011-04-07
Nope

---

### Post by David87123 on 2011-04-07
How do I know which partition to chose and where to put the Grub boot loader?? It has varioua SDA's.

---

### Post by C.S.Cameron on 2011-04-07
> **David87123 said:**
> How do I know which partition to chose and where to put the Grub boot loader?? It has varioua SDA's.

Put the bootloader on the / partition, If / is sda2 put it on sda not sda2.
If you disable the computers internal drive first, you can just install the normal way.

---

### Post by dcsoldschool53 on 2011-04-07
[IMG]https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=install-step4a.png[/IMG]

[B]Do you see the line starting in the picture with SCS! (0,0,0) - 40.0 GB ATA WDC ,etc. The arrow at the end indicates a drop down box. If you click it, you will see the drive that you want to use. Now you can click on it to install Ubuntu on that drive. Sorry about the big picture.
[/B]

---

### Post by oldfred on 2011-04-08
Since it is an external drive you want to install the grub boot loader to the external drive as dcsoldschool53 posted. But to get that screen you do have to use the manual partitioning or advanced  nothingspecial mentioned.

I like to add a separate partition for /home and keep system partition small. If allocating 100GB then I would do this:

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Lots of detail and lots of pictures.
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

