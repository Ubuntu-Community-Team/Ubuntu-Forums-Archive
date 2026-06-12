---
title: "speeding up usb?"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by minsf on 2009-01-26
my usb drive is transferring data at 1MB/s.
i know it is capable of more (back in the XP days, a couple of months ago, i remember it was able to copy 14GB in about 40 min= about 6MB/s).
is it possible for me to speed it up?

to be specific, i am running "cp" from the terminal; can i tell the kernel to allocate more resources to this process? will i get better results if i ran "cp" outside gnome (by ctrl+alt+f1 and "sudo /etc/init.d/gdm stop" before starting the "cp")? 
any other idea how to make the data transfer faster?

thanks, and let me know if you need more info about the system
(i am running 8.10)

---

### Post by roquefilipe on 2009-01-26
something similar happen to me weeks ago. Suddenly my external hard drive has slow. Finally I discovered that it was a USB hub that was slowing it down. 

Are you using any hubs, extensions, etc ?

---

### Post by blueridgedog on 2009-01-26
What file system is on the external drive? Fat32 or NTFS?

---

### Post by minsf on 2009-01-26
> **blueridgedog said:**
> what file system is on the external drive? Fat32 or ntfs?

fat

---

### Post by minsf on 2009-01-26
> **roquefilipe said:**
> something similar happen to me weeks ago. Suddenly my external hard drive has slow. Finally I discovered that it was a USB hub that was slowing it down. 

Are you using any hubs, extensions, etc ?
the external HD is connected straight to the usb.
no hubs or extensions

---

### Post by lisati on 2009-01-26
> **roquefilipe said:**
> something similar happen to me weeks ago. Suddenly my external hard drive has slow. Finally I discovered that it was a USB hub that was slowing it down. 

Are you using any hubs, extensions, etc ?
Alas the removal of the forum's "thank you" feature! :p This kinda confirms what I'd noticed on my Vista laptop.....a couple of devices I have hooked up via a USB hub show up in BIOS as 1.1, even though everything is supposedly 2.0 
> **minsf said:**
> fat

+1 Unless I'm mistaken, fat-based filesystems are often slower than some of the newer systems.

---

### Post by minsf on 2009-01-26
> **lisati said:**
> +1 Unless I'm mistaken, fat-based filesystems are often slower than some of the newer systems.
i can 90% confirm that it is not related to the filesystem: i formatted the external HD as EXT3, and i still have the poor 1MB/s rate of transfer.

the remaining 10%, you can see from the following output that the EXT3 sits in msdos partition (not fat or ntfs). i dont know how to get rid of this. i used gparted to format the entire unallocated space as ext3 (took 2 hours...). if you know how to get rid of the dos frame let me know.
```
        *-disk
             description: SCSI Disk
             product: FreeAgent
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 102D
             serial: 2GEV9G9P
             size: 465GiB (500GB)
             capabilities: partitioned [COLOR="Red"]partitioned:dos[/COLOR]
             configuration: ansiversion=4 signature=000d0245
           *-volume
                description: Linux filesystem partition
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                capacity: 465GiB
                capabilities: primary
```
nevertheless, i feel that the slow usb rate is not related to the file system. maybe to the usb driver or the kernel (i have the same slow rate when using "dd if=/dev/zero of=/dev/sdb bs=8M" which is very low level. i think only the kernel is underneath this...)
by the way, the reason why you cannot see ext3 inside the above output is that i already started covering it with this dd command.

---

### Post by minsf on 2009-01-26
i have also tried to boot the kernel with noapic and pci=routeirq and with each one of them seperately. same poor transfer rate.
i noticed that the transfer rate starts way above 4MB/s and drops to 2MB/s after about 10 sec, and to 1MB/s after about a minute.
the usb controller seems to be using the uhci_usb driver (according to lshw)
the (scsi) disk itself seems to be using the usb-storage driver
let me know if you need more precise info and i'll post it 
thanks

EDIT: typo... the driver is of course uhci_hcd :)

---

### Post by rok3 on 2009-01-27
Have you tried the HD on another computer and/or another drive on this computer?  Try to rule out any hardware issues before chasing software issues.

Also you might want to try a different usb cable.

---

### Post by minsf on 2009-01-27
> **rok3 said:**
> Have you tried the HD on another computer and/or another drive on this computer?  Try to rule out any hardware issues before chasing software issues.

Also you might want to try a different usb cable.
same usb cable and HD provide more than 6MB/s transfer rate with XP.
hence, not a hardware problem

---

### Post by rok3 on 2009-01-27
Hrm... I know that there have been a lot of issues with USB 2.0 transfer rates lately.  

What is your output from 

```
lsmod | grep -i usb
```

I've had to manually load/reload ehci_hcd with the device plugged in to get a USB 2.0 MP3 player to transfer at full speed in the past.

```
sudo modprobe -r ehci_hcd
sudo modprobe ehci_hcd
```

---

### Post by minsf on 2009-01-27
```
~$ lsmod|grep -i usb
usbcore               148848  2 uhci_hcd
```
I'll try ehci_hcd soon

---

### Post by mbzn on 2009-01-27
hi there

this seems like the same problem i'm having with all my usb drives.
i have 2 usb to sata drives that copies at a good speed in the begining, and seems to slow down to under 1mbps in seconds. this problem is not hardware related as i find the same thing happening on a 2gib flash-drive.
All of these hardware is formated ntfs.

Maybe this could help solve the problem

---

### Post by minsf on 2009-01-27
tried it on another external hard drive- still the same. so this excludes hardware issues outside the box (that is, it can still be internal hardware, though i dont think it is the usb port since it starts fine, maybe it's its driver).
i tried to reload the ehci_hcd and the uhci_hcd and the usb-storage drivers with "sudo modprobe -r XXX" and "sudo modprobe XXX". did not help.
i tried to run it from a live cd of 8.10 and a live cd of 8.04.2 but still get the same poor transfer rate.

---

### Post by velophil on 2009-01-27
i have had very similar problems over the past few weeks, since i switched to ubuntu. the peculiar thing is though: i have two fat32 formatted pen drives, one of them (sandisk cruzer) writes at 7 mbps and copies at 20 mbps, the other one, put into the same port, gives me 1 mbps and less.
external hard drives take a long time to initialize and they have a poor transfer rate. all components work wonderful on a friends XP machine. i would be the happiest person on earth if someone could address this issue, the other day it took me 6 hours to copy 23 gb to my drive :-(

cheers

velo

---

### Post by minsf on 2009-01-27
> **velophil said:**
> i have had very similar problems over the past few weeks, since i switched to ubuntu. 
did you switch from windows or f
om a different flavor of linux? i ask because my next step is checking usb transfer rates in other distributions, so please let me know if you have any experience with another flavor.

---

### Post by LowSky on 2009-01-27
Im having some really odd issue with USB too... slow transfer speeds, and thumb drives loose connections while transfering files... this isn't fun
here is the output of lsusb
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 001 Device 006: ID 0dc6:9801 Precision Squared Technology Corp. 
Bus 001 Device 005: ID 0dc6:3000 Precision Squared Technology Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I dont know where all these hubs are but there are 4 usb ports on the back, two up front and two on the keyboard (so that as a hub I understand)

im running windows XP and Windows 7, and no problem running USB flash drives on that

---

### Post by minsf on 2009-01-28
i found another thread about this:
[http://ubuntuforums.org/showthread.php?t=793688&page=8](http://ubuntuforums.org/showthread.php?t=793688&page=8)
so i think i will continue there

---

### Post by HermanAB on 2009-01-28
Replug the device, then check dmesg to see whether it is identified as a USB 2.0 high speed device.

Cheers,

Herman

---

### Post by Mexico Man on 2009-02-20
> **rok3 said:**
> Hrm... I know that there have been a lot of issues with USB 2.0 transfer rates lately.  

What is your output from 

```
lsmod | grep -i usb
```

I've had to manually load/reload ehci_hcd with the device plugged in to get a USB 2.0 MP3 player to transfer at full speed in the past.

```
sudo modprobe -r ehci_hcd
sudo modprobe ehci_hcd
```

I have the same problem on AMD x64
```
Linux administrator-desktop 2.6.24-22-generic #1 SMP Mon Nov 24 19:35:06 UTC 2008 x86_64 GNU/Linux

```
and have to use the same workaround :(

---

