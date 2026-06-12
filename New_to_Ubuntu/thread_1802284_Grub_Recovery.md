---
title: "Grub Recovery"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by zephyrous7 on 2011-07-11
Hi, 
I deleted a partition with Ubuntu on it and it also removed grub. When I try to boot into Windows 7 it takes me to the grub recovery console. 

Right now I am using the Live through a usb and I have searched for hours looking for a solution as I dont want to format Windows 7. I dont have a Windows CD as I read that you can reload the windows boot manager. 

Also I was going to try to reinstall Ubuntu but it wont let me reduce the partition size windows is on to make room for an installation.

---

### Post by lmarmisa on 2011-07-11
Welcome to the forums.

I recommend to reinstall Ubuntu defining manually the partitions. If you are more interested in Windows 7 than in Ubuntu, we could define a Ubuntu installation using a minimal space on disk.

Please, boot into a Ubuntu Live CD / USB, open a terminal, type these commands and post the results in this thread:

```

sudo parted -l
sudo lshw -C memory
free

```

Best regards,

Luis

---

### Post by Gr72 on 2011-07-11
Hey I had the same problem the first time I put Ubuntu on my old laptop. Easiest way I found was to download this iso burn it to a cd and choose the option for MBR to just windows. It works like a charm. [http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml)

Download it, burn the image to a cd, just like you did to install Ubuntu. Boot to it. it'll boot to a yellow screen. Using the keyboard scroll down to "!WIN!" this'll cahnge the MBR to just windows.... then reboot and you're in windows.

---

### Post by jtarin on 2011-07-11
> **Gr72 said:**
> Hey I had the same problem the first time I put Ubuntu on my old laptop. Easiest way I found was to download this iso burn it to a cd and choose the option for MBR to just windows. It works like a charm. [http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml)

Download it, burn the image to a cd, just like you did to install Ubuntu. Boot to it. it'll boot to a yellow screen. Using the keyboard scroll down to "!WIN!" this'll cahnge the MBR to just windows.... then reboot and you're in windows.That link is based on Grub Legacy...thats OK if all you want is Windows back and you have an older version of Ubuntu, but if newer and using Grub2 you might as well get this one [SuperGrubDisk2]("http://www.supergrubdisk.org/").....but......."Super GRUB2 Disk does not write to the disk at all, and so cannot rewrite the MBR. Super GRUB2 Disk can only be used to boot a broken system, it cannot fix it directly".When you get into windows you can use EasyBCD (in my signature) to write a new MBR.

---

### Post by Gr72 on 2011-07-11
Yes, the Super Grub Disk is good because it changes the MBR to just windows..... I've used it many a times. and I believe that He just wants to boot to windows to change the partitions and shrink Windows (which you can only do safely from within windows)

---

### Post by zephyrous7 on 2011-07-12
Im not able to boot with supergrub and I have tried supergrub2 and supergrub. I just dragged and dropped into flash and boot from usb and it takes me to grub recovery. Its quite a predicament because my cd drive is broken so burning to CD wont work.

---

### Post by Gr72 on 2011-07-12
Umm, looks like you need another computer. unless you could make a live USB with universal USB creator if you can download and install it. If you can get that and make a USB... boot to it and fix the MBR then you would be good to go. If not then only other thing is to get on another computer get the iso, burn the cd and boot to it.

---

