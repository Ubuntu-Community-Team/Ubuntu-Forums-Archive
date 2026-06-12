---
title: "Part of /usr on another partition"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by tkzv on 2010-12-14
I am using a subnotebook (Asus EEE 4G) with a small built-in drive (3G), but with relatively large external flash card (32G). Is it possible to install some programs to flash card, but keep the core system on the internal drive?

I need some programs (X.org, DE, console, browser, editor, mplayer...) to be always available with or without the card. Some large programs: Lazarus, OpenOffice — are needed less frequently, I want to put them to the card.

It is possible to install Ubuntu to the card, but the card is significantly slower than the internal drive.

It should be possible to recompile those programs to install to /opt or /usr/local and use mount --bind to mount directories on the card, but I switched from Gentoo to Ubuntu just for that reason — to avoid recompiling everything.

I am not sure if the internal drive can be replaced. Some people say it can't, some say it can, but the replacement drive is not available around here.

Is there any other way to offload some files from the internal drive to the card without breaking the system when the card is removed?

---

### Post by Joeb454 on 2010-12-14
You should be able to specify this when you install Ubuntu, during the partition manager section.

That said, I'm not 100% sure if this appears in the Netbook Edition installation, nor do I have any means of testing this.

---

### Post by tkzv on 2010-12-14
> **Joeb454 said:**
> You should be able to specify this when you install Ubuntu, during the partition manager section.

That said, I'm not 100% sure if this appears in the Netbook Edition installation, nor do I have any means of testing this.

If I remember correctly the installer of version 10.04, there was an option to use LVM, an it was also possible to create separate partitions for /boot, /home, /usr ...

LVM won't do. If there is no way to control in which sectors files end up after installation, the frequently used files may end up on the card. Fully or partially. And there would be the slowdown.

Separate partitions is a lot like using mount --bind. But it offers no way to split /usr between two partitions.

Or are there any other options in 10.10?

---

### Post by AngusH on 2010-12-14
I've no idea if this would work so wait for someone else to confirm, but you might be able to put the appropriate apps on the flash drive, mount the flash drive to somewhere like /programs then add /programs to your path.
Regards 
Angus

---

### Post by tkzv on 2010-12-14
> **AngusH said:**
> I've no idea if this would work so wait for someone else to confirm, but you might be able to put the appropriate apps on the flash drive, mount the flash drive to somewhere like /programs then add /programs to your path.
Regards 
Angus

I'll also have to add /programs/usr/lib to something like LD_PATH for some programs. 

Installing small packages manually this way is no problem. This is how I run Lugaru. There could be problems with something bigger — like OOo.  

Besides there are numerous warnings against using LD_PATH more than absolutely necessary :)

Then the question is: can apt/aptitude/whatever be tuned to install only some programs and their updates to a directory other than /usr ? For example to /opt

---

