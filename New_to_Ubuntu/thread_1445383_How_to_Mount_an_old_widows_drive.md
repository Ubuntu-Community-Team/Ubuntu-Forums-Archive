---
title: "How to Mount an old widows drive"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by jlmflys on 2010-04-02
How can I mount a widows hard drive I removed for an old computer.  I believe it had windows 95 or 97 on it.  I am using ubuntu 8.10 on a compaq CQ60 notebook PC.  It has a dual boot with window vista.  I have the hard drive removed from the old computer and plugged into a usb adapter.  

This is what I get when I use command: fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d900954

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16270   130680800    7  HPFS/NTFS
/dev/sda2           28982       30401    11405312    7  HPFS/NTFS
/dev/sda3           16271       28981   102101107+   5  Extended
/dev/sda5           16271       28459    97908111   83  Linux
/dev/sda6           28460       28981     4192933+  82  Linux swap / Solaris

The two NTFS drives listed are the partitions for the vista operating system and the restore for windows.  

The old drive is plugged into a usb port and I can't find it on the system.  I would appreciate any help I could get.

---

### Post by Mark Phelps on 2010-04-02
You're confusing drives with partitions.  The fdisk output shows only one drive -- but it has several partitions on it.

Is your other drive plugged into the USB port before you start your machine? If so, unplug it, start your machine, and don't plugin the drive until after your desktop has been open for a few minutes.

When you plug it in, you should see some folders pop open on your desktop.  You'll get a folder for each partition on that drive.

---

### Post by HermanAB on 2010-04-02
"old widows"

Uhmmm... well, if the widow is still younger than me...

---

### Post by jlmflys on 2010-04-02
I tried your suggestion, and it didn't work.  I can see the USB drive on the computer window, but nothing on the desk top.  If I click on the properties it indicates unknown type.  I have tried this before with other drives and the same thing happens.  One drive I re-formated and then ubuntu was able to mount the drive, but I want what is on this drive so I am trying to mount it without losing all the data.  If you have any ideas, let me know.  Thanks for your help.

---

### Post by jlmflys on 2010-04-02
Sorry about the type-0, but that is funny!

---

### Post by theozzlives on 2010-04-02
The only thing I can think of is either FAT or Drivespace. There is no such thing as `97. If it's been compressed with Drivespace, Only Windows 95 can open it. There is no FAT32 in Windows 95. I'd suggest you boot the drive as Master and access your data that way. Copy what you want to floppy. Or use a third party program to burn a CD.

---

### Post by jlmflys on 2010-04-02
Does this help?  Here is a copy of dmesg | tail

[  238.723001] sd 5:0:0:0: Attached scsi generic sg3 type 0
[ 1711.965965] FAT: bogus number of reserved sectors
[ 1711.965974] VFS: Can't find a valid FAT filesystem on dev sda1.
[ 2819.972411] usb 2-4: USB disconnect, address 2
[ 2911.860941] usb 2-4: new low speed USB device using ohci_hcd and address 3
[ 2912.077434] usb 2-4: configuration #1 chosen from 1 choice
[ 2912.096627] input: Microsoft Microsoft Notebook Receiver v2.0 as /devices/pci0000:00/0000:00:04.0/usb2/2-4/2-4:1.0/input/input10
[ 2912.691830] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Notebook Receiver v2.0] on usb-0000:00:04.0-4
[ 3000.714884] FAT: bogus number of reserved sectors
[ 3000.714892] VFS: Can't find a valid FAT filesystem on dev sda1.

Does any of this tell me what this drive is or file system type?

---

### Post by HermanAB on 2010-04-03
I suggest that you plug it back into a Windows machine and see whether you can copy the data to a memory stick. Since the drive is very old, it is likely also very small and all the data will likely fit on a modern memory stick.

---

### Post by Wiebelhaus on 2010-04-03
> **HermanAB said:**
> I suggest that you plug it back into a Windows machine and see whether you can copy the data to a memory stick. Since the drive is very old, it is likely also very small and all the data will likely fit on a modern memory stick.

Either that or the drive has or is failing , You can also reboot with the drive connected , if there's been some type IO anomaly that may allow it to reset.

---

### Post by Tom.Gee on 2010-04-03
> **jlmflys said:**
>   I believe it had windows 95 or 97 on it. USB to IDE adaptors depend on the hard drive reporting its specifics, just as a modern BIOS does.  Old drives of the era you describe were manually configured for drive geometry (heads, cylinders, etc. set in the BIOS, often by a single numeric Drive Type entry.) If this is such a drive, it is NOT compatible with the USB adapter you are using.  If this is the case, and I strongly suspect it is, your best bet for reading the drive lies in the motherboard it was attached to, if that still exists and functions.

---

### Post by lkraemer on 2010-04-04
Your Win 95/98 is an IDE type Drive,  It most likely has a Drive Select
Jumper set for Master/Slave/CableSelect.  Try using the Jumper MASTER
with your USB to IDE Adapter.  If that doesn't work try Slave or no Jumper.
One of the choices should work. (My Adapter uses MASTER Jumper)

Boot Ubuntu
Connect Drive to USB to IDE Adapter (Make sure it is CORRECT)
Connect Power Adapter (Wall Wart supplied with Adapter to IDE Drive with 4 Pin Molex connector)
Wait for it to Spin up  (Listen for it to it spin up)
Plug in USB cable to Laptop USB Port and wait a minute
Desktop should have added ICON for Drive  (If not you could try to manually mount the drive)

Access Files and copy as needed

UNMOUNT USB to IDE Drive
Unplug USB Cable
Power OFF USB to IDE Drive
Remove Drive Power Cables & Adapter

The only thing that might be a problem is if STACKER or some other Drive
Compression Utility was installed to compress your Data on the drive.
And you should know this if you used the drive....... But, the USB to IDE
Adapter should mount the drive in any case.  You just might not be able
to easily access the files you want.

lk

---

### Post by jlmflys on 2010-04-05
Thanks for your post, this helps to explain why I couldn't get into this  drive.

---

