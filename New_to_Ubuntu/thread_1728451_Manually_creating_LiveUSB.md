---
title: "Manually creating LiveUSB"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by nightcracker on 2011-04-13
Hi!

I have the following:

[LIST]
[*] A 4GB USB stick (bootable, confirmed)
[*] The Ubuntu 10.10 ISO
[*] Access to a Ubuntu 10.10 installation and Windows
[/LIST]

And I'm trying to do the following:

[LIST]
[*] Create a Ubuntu 10.10 LiveUSB
[*] On the same partition of the LiveUSB I want another ~500MB of space for Windows files
[*] Use the rest of the space for a casper-rw persistance partition (preferably ext3 to prevent crashes on dirty shutdown)
[/LIST]

I can make the two partitions I want through fdisk (1250MB for LiveUSB + Windows files and the rest for casper-rw), and I can format them with mkfs, but I fail to correctly install the LiveUSB and making it use the casper-rw partition. Any help would awesome :)

---

### Post by bodhi.zazen on 2011-04-13
Not sure what you are trying to do exactly, but Windows will only recognize the first partition on your USB device.

Install Ubuntu into the second partition and config isolinux (the boot manager) accordingly.

alternately use an alternate boot manager (google search multiboot usb live).

---

### Post by nightcracker on 2011-04-13
> **bodhi.zazen said:**
> Not sure what you are trying to do exactly, but Windows will only recognize the first partition on your USB device.

Install Ubuntu into the second partition and config isolinux (the boot manager) accordingly.

alternately use an alternate boot manager (google search multiboot usb live).

Could you perhaps clarify? Do you suggest 3 partitions?

1 - 500MB - FAT16 - Windows files
2 - 750MB - FAT16 - Bootable - Ubuntu
3 - REST - EXT3 - casper-rw

---

### Post by bodhi.zazen on 2011-04-13
You can put the casper-rw file on the first (FAT) partition if you wish (I think that would be standard).

---

### Post by nightcracker on 2011-04-13
I read that giving the partition the label casper-rw should suffice. Putting it in the first partition "slot" would render my windows partition useless.

And I REALLY don't want casper-rw on a FAT partition, the unstability is insane.

I now have come to the point where I made the partitions and installed LiveUSB using the standard tool on the second, bootable, FAT partition. However when I boot I just get stuck at the syslinux boot message. Any idea what could cause this?

---

### Post by bodhi.zazen on 2011-04-13
> **nightcracker said:**
> I read that giving the partition the label casper-rw should suffice. Putting it in the first partition "slot" would render my windows partition useless.

And I REALLY don't want casper-rw on a FAT partition, the unstability is insane.

I now have come to the point where I made the partitions and installed LiveUSB using the standard tool on the second, bootable, FAT partition. However when I boot I just get stuck at the syslinux boot message. Any idea what could cause this?

Oh, I think you are correct re casper-rw.

You will probably need to configure syslinux to boot the second, rather then the first partition.

You may also need to mark the second partition as bootable.

---

### Post by nightcracker on 2011-04-13
> **bodhi.zazen said:**
> Oh, I think you are correct re casper-rw.

You will probably need to configure syslinux to boot the second, rather then the first partition.

You may also need to mark the second partition as bootable.

I'm sorry, I'm a bit of a noob. I have marked the second partition as bootable and executed syslinux /dev/sdf2. Yet I still get stuck on the "syslinux version bla bla bla" line. No command prompt, nothing.

---

### Post by bodhi.zazen on 2011-04-13
You probably need a syslinux.cfg

[http://syslinux.zytor.com/wiki/index.php/SYSLINUX](http://syslinux.zytor.com/wiki/index.php/SYSLINUX)

[http://syslinux.zytor.com/wiki/index.php/SYSLINUX#How_do_I_Configure_SYSLINUX.3F](http://syslinux.zytor.com/wiki/index.php/SYSLINUX#How_do_I_Configure_SYSLINUX.3F)

---

### Post by nightcracker on 2011-04-13
I'm getting so sick of this. I just can't do it lol.

Are there any clear guides for installing ubuntu manually on a USB? And I can't get syslinux to work on the 2nd partition.

---

### Post by bodhi.zazen on 2011-04-13
> **nightcracker said:**
> I'm getting so sick of this. I just can't do it lol.

Are there any clear guides for installing ubuntu manually on a USB? And I can't get syslinux to work on the 2nd partition.

The guides are spotty, it is for the most part trial and error.

---

### Post by nightcracker on 2011-04-13
> **bodhi.zazen said:**
> The guides are spotty, it is for the most part trial and error.

=S

I have found this: [http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2) which actually is still pretty decent.

I really have no idea on how to get SYSLINUX to work on the 2nd partition, how does it work anyway? What parameters should I set? Does it parse the .cfg files during the boot, or compile them into machine code or?

---

### Post by bodhi.zazen on 2011-04-14
See the link I gave you as well =)

syslinux.cfg is the boot menu, akin to say the grub menu.

Copy your kernel and initrd to the first partition. Put syslinux.cfg in the first partition.

Then use :

```
DEFAULT Ubuntu
LABEL Ubuntu
  SAY Now booting Ubuntu...
  KERNEL vmlinuz.img
  APPEND ro root=/dev/sda2 initrd=initrd.img
```

---

### Post by nightcracker on 2011-04-14
> **bodhi.zazen said:**
> See the link I gave you as well =)

syslinux.cfg is the boot menu, akin to say the grub menu.

Copy your kernel and initrd to the first partition. Put syslinux.cfg in the first partition.

Then use :

```
DEFAULT Ubuntu
LABEL Ubuntu
  SAY Now booting Ubuntu...
  KERNEL vmlinuz.img
  APPEND ro root=/dev/sda2 initrd=initrd.img
```

Ok, I'm going to try that and see how that works.

---

### Post by bodhi.zazen on 2011-04-14
> **nightcracker said:**
> Ok, I'm going to try that and see how that works.

Hope you get it working, and I agree it would be nice to see a well written set of documents for "how to live CD".

---

