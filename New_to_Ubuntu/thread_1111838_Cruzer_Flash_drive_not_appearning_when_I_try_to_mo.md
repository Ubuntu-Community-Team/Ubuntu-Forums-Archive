---
title: "Cruzer Flash drive not appearning when I try to mount it"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by erunamo114 on 2009-03-31
I have just recently installed Ubuntu on my desktop PC. I put a good amount of back-up data on an 8GB Cruzer Flash Drive that has U3 on it also. I am having a lot of problems trying to figure out how to mount the flash drive. I have run several of the commands that were suggested to me. The output from the lsusb command was

Bus 002 Device 002: ID 0461:4d16 Primax Electronics, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 001 Device 005: ID 04a9:1712 Canon, Inc. MP530
Bus 001 Device 004: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 003: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The output from sudo fdisk -l was:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbc58b91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60051   482359626   83  Linux
/dev/sda2           60052       60801     6024375    5  Extended
/dev/sda5           60052       60801     6024343+  82  Linux swap / Solaris

I also ran sudo lshw -numeric. The relevant part of the output there was:

 *-scsi:0
          physical id: a
          bus info: usb@1:7
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
     *-scsi:1
          physical id: e
          bus info: usb@1:9
          logical name: scsi11
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Cruzer
             vendor: SanDisk
             physical id: 0.0.0
             bus info: scsi@11:0.0.0
             logical name: /dev/sdf
             version: 8.01
             serial: u
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdf
        *-cdrom
             description: SCSI CD-ROM
             product: Cruzer
             vendor: SanDisk
             physical id: 0.0.1
             bus info: scsi@11:0.0.1
             logical name: /dev/cdrom1
             logical name: /dev/cdrom2
             logical name: /dev/scd1
             logical name: /dev/sr1
             logical name: /mnt/USB
             version: 8.01
             serial: uSanDisk Cruzer          8.01
             capabilities: removable audio
             configuration: mount.fstype=iso9660 mount.options=ro state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom1
                logical name: /mnt/USB
                configuration: mount.fstype=iso9660 mount.options=ro state=mount

I'm wondering why it says that the the Cruzer is a cd-rom? Could that be part of the problem?

---

### Post by Russell Burrows on 2009-03-31
I had the same problem and what fixed it at last was finding the U3 removal tool from the manufacturer.

Now my usb drive is U3 free and works like a charm.

I hope this helps.

---

### Post by bumanie on 2009-03-31
U3 lasted about 2 days on my usb stick. Yeah, go to the manufacturers site and remove it - it then works like a regular usb stick. I found U3 to be the most annoying thing I have ever used, even when I used it on that other popular OS.

---

### Post by mikechant on 2009-03-31
I read some article about this a while ago, and if I remember correctly, the U3 partition is supposed to look like a CDROM to try to fool Windows into running some program off of it, in order to support the drive encryption. As per the other posts, I believe you have to get rid of the U3 partition.

---

### Post by erunamo114 on 2009-03-31
Thanks for the feedback guys. The only thing is that when I try to run the U3 removal tool through Wine (cuz it's a Windows only exe. application), it asks me to insert the USB drive. The problem is that Linux can't find the USB drive lol. So I'm not sure what to do. I had it plugged in and everything. It's just not mounted. Which was the whole problem to begin with. What do you think?

---

### Post by mikechant on 2009-03-31
Can gparted see it? Your lshw output implies it might appear as /dev/sdf. If so you might be able to delete the U3 partition.

---

### Post by erunamo114 on 2009-04-02
Could I delete the U3 partition in the terminal? What would the code be for that?

---

### Post by mikechant on 2009-04-10
I found some instructions for removing U3 partitions in Linux at
[http://noisetheatre.blogspot.com/2006/08/uninstall-u3-and-free-your-usb-drive.html](http://noisetheatre.blogspot.com/2006/08/uninstall-u3-and-free-your-usb-drive.html)

It looks from your lshw output that the U3 partition is mounting as a
CDROM:
```
*-cdrom
description: SCSI CD-ROM
product: Cruzer
vendor: SanDisk
physical id: 0.0.1
bus info: scsi@11:0.0.1
logical name: /dev/cdrom1
logical name: /dev/cdrom2
logical name: /dev/scd1
logical name: /dev/sr1
logical name: /mnt/USB
version: 8.01
serial: uSanDisk Cruzer 8.01
capabilities: removable audio
configuration: mount.fstype=iso9660 mount.options=ro state=mounted
status=ready
```

So, applying the instructions it looks like you need to do the following
in a terminal:
sudo cd /sys/class/block/sr1/device/
sudo echo "1" > delete


No idea if this will actually work though!

---

### Post by niteshifter on 2009-04-10
Hi,

As per above unU3 it, but with a SanDisk Cruzer you must use SanDisk's removal tool (a Windows machine or a VM is handy) - the generic tool from U3 won't work.

Don't know if it will work within Wine, but it does work via Windows Guest in Virtualbox. I used it to make my Heron-On-A-Stick (2GB Cruzer).

---

### Post by Martin Marshalek on 2009-04-10
I have never actually tried to get rid of U3 on my Linux install but I believe you can use the U3 removal tool on the internet. If not, I suggest finding a Windows machine (library, school, or a computer store that lets you test the computers) and remove U3 from there. The only downside to that is you're going to be there a while with an 8GB drive. The removal tool needs to completely format the drive and then restore any backed up data on the drive.

Also, you can't dust delete the fake-CD partition as the data partition still tells that to be read from.

---

