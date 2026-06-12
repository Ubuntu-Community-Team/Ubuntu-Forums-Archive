---
title: "Sandisk Memory Stick PRO Duo NOT mounting on Ubuntu 9.04"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by soma1509 on 2009-10-22
Hello, Everyone,

I'm still quite new to Ubuntu, but I've been using it sporadically since version 7.10. However, since it's now my only OS on my Gateway m255-E laptop, Im going to use Ubuntu more often from now on. Everything is working good except I am having a problem with the SD card reader on my laptop. I have a 1GB Sandisk Memory Stick PRO Duo SD card along with a Memory Stick Duo Adaptor (the SD card itself will NOT fit on the reader without this adapter!). When I plug it in, nothing happens, no Disk icon shows up. Nothing shows up on my desktop nor a window opens up to show the memory stick itself. It's like it's having trouble mounting somehow.

For reference, I have a Sandisk CRUZER 2GB USB stick, and it works perfectly fine. It's detected on Ubuntu 9.04 and sets a Hard Drive icon on my desktop until I unplug it.

My Laptop Specs:

Gateway M255-E Laptop
Intel Dual-Core T2050 (freshly bought from eBay as a cheap upgrade :))
2GB of RAM
7-in-1 Card reader (I think from Texas Instruments)

Can someone help me out with this? I am a total newbie when it comes to Terminal/command-line stuff so please go easy on me with instructions on how to solve this.

Do I have to compile drivers for this memory card? If so, how do I do that in the most easiest way possible?

Thanks in advance!

~Soma

---

### Post by Hospadar on 2009-10-22
There's definitely no drivers involved.  There may be something strange with your card reader, but I doubt it.

Could you post the output of "sudo fdisk -l" (this will show all connected drives) as well as "df -h" (this will show all mounted drives).

---

### Post by sandyd on 2009-10-22
run this
```

sudo modprobe tifm_core
sudo modprobe tifm_7xx1
sudo modprobe tifm_sd
sudo modprobe tifm_ms

```

---

### Post by soma1509 on 2009-10-22
Alright, I ran the all commands suggested and this is what I got

```

sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007cc1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

``````

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   33G   35G  49% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M  212K 1002M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M  140K 1002M   1% /dev
tmpfs                1003M  260K 1002M   1% /dev/shm
lrm                  1003M  2.2M 1000M   1% /lib/modules/2.6.28-16-generic/volatile

``````

sudo modprobe tifm_core
sudo modprobe tifm_7xxl
FATAL: Module tifm_7xxl not found.
sudo modprobe tifm_sd
sudo modprobe tifm_ms
FATAL: Module tifm_ms not found.

```So from those last commands, two modules are missing, is this something I should be concerned about?

Thanks for the help so far!

PS: At the time of running those commands, nothing is connected to my laptop, be it USB sticks or other wise.

---

### Post by soma1509 on 2009-10-25
Well, after looking around, it seems that the problem is the CARD itself that's not being detected, the card reader is fine, as shown here:

```

lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
04:09.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
04:09.4 Communication controller: Texas Instruments PCIxx12 GemCore based SmartCard controller

```I found an old SD 512MB card lying around and it was automatically detected by Ubuntu, so I can safely say that the card reader is fine. But now how can I make Ubuntu recognize my Sandisk PRO Duo card? Do I have to compile something to make it get recognized by the OS? If so, how would I do that?

~Soma

---

### Post by LewRockwell on 2009-10-25
We will be starting a dedicated thread in the Absolute Beginner Talk area regarding flash media but thought you could start with this:

[http://wiki.laptop.org/go/How_to_Damage_a_FLASH_Storage_Device](http://wiki.laptop.org/go/How_to_Damage_a_FLASH_Storage_Device)

[http://elm-chan.org/docs/mmc/mmc_e.html](http://elm-chan.org/docs/mmc/mmc_e.html)

[http://en.wikipedia.org/wiki/Secure_Digital](http://en.wikipedia.org/wiki/Secure_Digital)



Not sure yet what title and tag combination will produce the most effective search results but we'll probably use a tag of mmcblk0 at least

Here's the new thread:

[http://ubuntuforums.org/showthread.php?t=1300716](http://ubuntuforums.org/showthread.php?t=1300716)

.

---

### Post by soma1509 on 2009-10-25
Thanks a lot!

In the meantime, After looking around the forums some more, I found a temporary solution at this thread here:
[http://ubuntuforums.org/showthread.php?t=797031&page=5](http://ubuntuforums.org/showthread.php?t=797031&page=5)

I say temporary because now whenever I use my PRO duo without unmounting it first, the hard disk icon remains on the desktop, thus becoming a "ghost drive", and if I click on it by accident, it locks up my entire desktop. So I know the proper way to do this would be unmounting the stick first then removing it, but I know for a fact that there will be times that I will forget to do this. My SD cards don't have this problem, I can just plug them in and they are detected immediately, and I can take it out without unmounting it and my desktop will work like usual. So this has something to do with the cards themselves.

Thanks a lot for making that thread. Hopefully it will help other people as well.

Since this small bug still exists, I don't know if whether to consider this thread SOLVED, even though my Sandisk PRO Duo works OK during those certain conditions.

~Soma

---

