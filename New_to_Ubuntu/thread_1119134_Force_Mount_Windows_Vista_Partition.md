---
title: "Force Mount Windows Vista Partition"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-04-07
Unfortunately after partitioning my hard drive with gparted vista fails to boot (I knew this would happen as it was a last resort...) although after trying to fix the problem with the vista install disc, there's still no signs of life... so what I want to do is force mount the partition in Ubuntu and copy over some video files:KS can anyone tell me what commands I need to do this? and also what is the name of the partition in Ubuntu as it appears to be "392.1 GB Media" but I was expecting something like a letter?

Thanks in advance!

---

### Post by WRDN on 2009-04-07
To find the device, type:

```
sudo fdisk -l
```

Now, type:
```
sudo mkdir /media/VistaDisk
```

Finally:

```
sudo mount -t ntfs-3g /dev/[device] /media/VistaDisk -o force
```

---

### Post by kamitsukai on 2009-04-07
Brilliant! Thanks very much\\:D/

I'm now off to banish the brownness of a default Ubuntu install:lolflag:

---

### Post by northern lights on 2009-04-07
> **kamitsukai said:**
> Unfortunately after partitioning my hard drive with gparted vista fails to boot (I knew this would happen as it was a last resort...) although after trying to fix the problem with the vista install disc, there's still no signs of life... so what I want to do is force mount the partition in Ubuntu and copy over some video files:KS can anyone tell me what commands I need to do this?
There's several ways to achieve what you want to do. Most likely, your Windows partition is the first partition on the first drive, i.e. *sda1*. First create a folder to mount to```
sudo mkdir /media/windows
```and then mount it using```
sudo mount -t ntfs /dev/sda1 /media/windows -o force
```. For permanent mounting, you could edit [fstab]("http://www.humbug.org.au/talks/fstab/fstab.html").
To verify that it's indeed sda1, run```
sudo fdisk -l
```

> **kamitsukai said:**
> what is the name of the partition in Ubuntu as it appears to be "392.1 GB Media" but I was expecting something like a letter?GNU/Linux devices are not named by single characters with A and B (still) reserved for floppys and harddrives starting at C. Instead they are identified by a combintion of three letters and a running number. Historically SCSI devices are called sdaX and IDE/others hdaX where X is the running number. In your system, all devices are sdaX. What you see under the *Places* menu is a label or further name given to the partition as displayed after the drive letter under Windows. Ubuntu called some further partition of yours "392.1 GB Media" because you haven specified any other name for it yet and it's further got thet much of usable space. You must have some partiton and/or harddrive with about that much space. Shouldn't content tell you what it is?

---

