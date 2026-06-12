---
title: "Maxtor 80gig external hd"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by ProStockNut on 2009-07-11
I just installed Jaunty on my laptop and would like to get this external hd to work as well. It works fine with XP but i cannot get it to read with Ubuntu. Im not very literate with this type of stuff and not sure if it will even work. This is the last thing i want to install. 

I have searched and googled the best i could, but i feel as though im missing the point as to how this is done.

Thanks.

---

### Post by ajgreeny on 2009-07-11
If it is a usb drive just plugging it in should mount it automatically and make it available to ubuntu.  Normally a nautilus (file manager) window appears when it mounts as well, but if not open nautilus and look in /media to see if anything shows there.

Can you also plug it in and then in terminal run ```
sudo fdisk -l
```that's a lower case L not figure 1, and post the output back here.

---

### Post by davmac on 2009-07-11
Hmmm, when I plug my external hdd in it just automounts and appears on the desktop. How is the disk connected? Is it USB? If so, try starting up the terminal and typing "lsusb".

When I do this I get

```
davmac@dav001:~$ lsusb
Bus 002 Device 003: ID 0930:0b09 Toshiba Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

The first one is my Toshiba drive.

Can you copy and paste what you get?

Regards,

Dave Mac

---

### Post by ProStockNut on 2009-07-11
> **ajgreeny said:**
> If it is a usb drive just plugging it in should mount it automatically and make it available to ubuntu.  Normally a nautilus (file manager) window appears when it mounts as well, but if not open nautilus and look in /media to see if anything shows there.

Can you also plug it in and then in terminal run ```
sudo fdisk -l
```that's a lower case L not figure 1, and post the output back here.

Here is what i get.
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

---

### Post by ProStockNut on 2009-07-11
> **davmac said:**
> Hmmm, when I plug my external hdd in it just automounts and appears on the desktop. How is the disk connected? Is it USB? If so, try starting up the terminal and typing "lsusb".

When I do this I get

```
davmac@dav001:~$ lsusb
Bus 002 Device 003: ID 0930:0b09 Toshiba Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```The first one is my Toshiba drive.

Can you copy and paste what you get?

Regards,

Dave Mac
jeff@jeff-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

And this.

---

### Post by LewRockwell on 2009-07-11
is this external hard drive set-up something you bought that way or did you put a drive in an external enclosure

the reason I ask is because sometimes people leave the drive jumper in the wrong place and windoze might overlook it but perhaps *nix might not...

just a thought...hey, we're pullin' for ya!

.

---

### Post by ajgreeny on 2009-07-11
With the drive plugged in reboot and note whether or not the BIOS sees the disk by going into your BIOS (you will get a "Press Del/F2 to enter setup) and see if the BIOS has seen the disk.  It should be there somewhere, but where will depend on your make of motherboard and BIOS.

---

### Post by ProStockNut on 2009-07-11
> **LewRockwell said:**
> is this external hard drive set-up something you bought that way or did you put a drive in an external enclosure

the reason I ask is because sometimes people leave the drive jumper in the wrong place and windoze might overlook it but perhaps *nix might not...

just a thought...hey, we're pullin' for ya!

.

It's all orginal. No mods or hd swaps.

---

### Post by bigbb on 2009-07-11
> **ProStockNut said:**
> I just installed Jaunty on my laptop and would like to get this external hd to work as well. It works fine with XP but i cannot get it to read with Ubuntu. Im not very literate with this type of stuff and not sure if it will even work. This is the last thing i want to install. 
 
I have searched and googled the best i could, but i feel as though im missing the point as to how this is done.
 
Thanks.
 
[http://ms.minick.net/om5/t2n7z4n5/inst_oust60.mp3](http://ms.minick.net/om5/t2n7z4n5/inst_oust60.mp3)

---

### Post by LewRockwell on 2009-07-11
IIRC, there were BIOS set-ups that had selections for whether the BIOS itself was supposed to control certain hardware...or whether it was to be left for the operating system itself to initiate and control

Given that, I'd be inclined to carefully examine and familiarize myself with every possible BIOS setting

The BIOS area is usually entered at start-up by depressing "F2" or "delete"
(some machines give this information in the very beginning of the on-screen details at start-up)

keep us posted

.

---

### Post by ProStockNut on 2009-07-11
Went into the bios and had a look around and nothing was coming up. So, for giggles i decided to unplug the power and upon plugging it back in. It now finds the drive. But now the "working" light will not go off. It's spinning inside. I cannot even run gparted as it keeps scanning for devices.

---

### Post by LewRockwell on 2009-07-11
> **ProStockNut said:**
> Went into the bios and had a look around and nothing was coming up. So, for giggles i decided to unplug the power and upon plugging it back in. It now finds the drive. But now the "working" light will not go off. It's spinning inside. I cannot even run gparted as it keeps scanning for devices.

I wanted to clarify:

the "working" indicator light is on the external hard drive?

does "it's spinning inside" refer also to the external hard drive?

perhaps you could boot into the LiveCD and see what happens with all this then?

.

---

### Post by ProStockNut on 2009-07-11
> **LewRockwell said:**
> I wanted to clarify:

the "working" indicator light is on the external hard drive?

does "it's spinning inside" refer also to the external hard drive?

perhaps you could boot into the LiveCD and see what happens with all this then?

.

Yes to both of your questions. Running the live cd and it did not find the drive. So i reboot and it is not spinning anymore. Gparted has found the drive and i am attempting to format as i type this. Crossing my fingers.

Edit: Do i need to use fat32? or can i just give it EXT 2,3, or 4?

---

### Post by ajgreeny on 2009-07-12
> Edit: Do i need to use fat32? or can i just give it EXT 2,3, or 4? 	It will depend on whether or not the disk will be needed for windows as well as linux.  If windows will possibly be involved at some time either now or in the future, format to fat32 or NTFS, if only linux use is expected, use ext3.  Or you could of course make two partitions, one fat32 and the other ext3, and get the best of both situations.

---

