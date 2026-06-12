---
title: "Manually Mounting an External Hard Drive"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by Ranemills on 2009-08-01
So I've got an external hard drive, which I've just plugged into the USB port of my computer. I thought it was meant to automatically mount it, but maybe there's a problem somewhere. Could someone tell me how I would go about mounting it? I have tried searching the forums and the Internet but to no avail.

The hard drive is 320 GB.

Two piece of information which I've seen asked for were "sudo lshw -C disk" and "sudo fdisk -l" Not sure whether these are any use but the results for these were:

```
ryan@ryan-desktop:~$ sudo lshw -C disk
 *-disk:0            
       description: ATA Disk
       product: MAXTOR 6L060J3
       vendor: Maxtor
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: A93.
       serial: 663128714142
       size: 55GiB (60GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=1a4a9a6b
  *-disk:1
       description: ATA Disk
       product: Maxtor 32049H2
       vendor: Maxtor
       physical id: 1
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: YAH8
       serial: L21C5HHC
       size: 19GiB (20GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=26412640
  *-cdrom:0
       description: DVD reader
       product: DVDRW LDW-451S
       vendor: LITE-ON
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: GSB4
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: CD-R/CD-RW writer
       product: R/RW 8x4x32
       vendor: IDE-CD
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.1
       serial: 3IDE-CD  R/RW 8x4x32      1.10
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=nodisc
ryan@ryan-desktop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a4a9a6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7161    57520701   83  Linux
/dev/sda2            7162        7299     1108485    5  Extended
/dev/sda5            7162        7299     1108453+  82  Linux swap / Solaris

Disk /dev/sdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26412640

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2482    19936633+   7  HPFS/NTFS

```

---

### Post by Volt9000 on 2009-08-01
Thanks for pasting those outputs, they are indeed helpful.
Based on them, it looks like the disk is not being recognized. Are you sure you have it plugged in when you typed those commands?

Try this: plug the drive in, wait a few seconds, then in the terminal type

```

dmesg | tail -20

```

and post the output of that. This should reveal any errors Linux detects when trying to communicate with the device.

---

### Post by CREEPING DEATH on 2009-08-01
A lot of the external drives aren't recognized by Linux.

CD

---

### Post by Ranemills on 2009-08-01
Well, it seems to notice something.

```

[   65.534736] wlan0: associate with AP 00:1b:2f:6d:67:e4
[   65.537214] wlan0: RX AssocResp from 00:1b:2f:6d:67:e4 (capab=0x431 status=0 aid=3)
[   65.537227] wlan0: associated
[   65.539988] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   75.584052] wlan0: no IPv6 routers present
[  198.544060] usb 4-2: new full speed USB device using uhci_hcd and address 3
[  207.306734] usb 4-2: not running at top speed; connect to a high speed hub
[  207.362322] usb 4-2: configuration #1 chosen from 1 choice
[  235.504105] usb 4-2: USB disconnect, address 3
[  235.744055] usb 4-2: new full speed USB device using uhci_hcd and address 4
[  235.998238] usb 4-2: not running at top speed; connect to a high speed hub
[  236.020495] usb 4-2: configuration #1 chosen from 1 choice
[ 3615.016133] usb 4-2: USB disconnect, address 4
[ 3623.192088] usb 4-2: new full speed USB device using uhci_hcd and address 5
[ 3623.502653] usb 4-2: not running at top speed; connect to a high speed hub
[ 3623.530196] usb 4-2: configuration #1 chosen from 1 choice
[ 3651.720137] usb 4-2: USB disconnect, address 5
[ 3651.964120] usb 4-2: new full speed USB device using uhci_hcd and address 6
[ 3652.138178] usb 4-2: not running at top speed; connect to a high speed hub
[ 3652.191651] usb 4-2: configuration #1 chosen from 1 choice

```

---

### Post by Volt9000 on 2009-08-01
Ok, so now that you have that (and it doesn't look like there are any errors) paste the output of 

```

sudo fdisk -l

```

---

### Post by Ranemills on 2009-08-01
Looks the same as the first one.

```

Disk /dev/sda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a4a9a6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7161    57520701   83  Linux
/dev/sda2            7162        7299     1108485    5  Extended
/dev/sda5            7162        7299     1108453+  82  Linux swap / Solaris

Disk /dev/sdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26412640

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2482    19936633+   7  HPFS/NTFS

```

---

### Post by camper365 on 2009-08-01
Here's what you need to do:

```

sudo -i
mkdir /media/externalHDD
mount /dev/sdb1 -t ntfs-3g /media/externalHDD

```Explanation of each line:
the hash signs (#) after each line are a comment in bash-like syntax and are the explanation
```

sudo -i      # Enter a root shell. You don't have to do this, but if you don't then you have to type sudo before every command
mkdir /media/externalHDD      # Make a directory to mount the hard drive in
mount /dev/sdb1 -t ntfs-3g /media/externalHDD      # Mount the device on /media/externalHDD. The -t ntfs-3g tells mount that it is an NTFS filesystem.

```


If any error comes up, post their output here.

---

### Post by Volt9000 on 2009-08-01
Hmmm, very strange.

Unfortunately I have no idea how to proceed-- I'm anything but a Linux guru, sorry :(

Hopefully one of the many experts on these forums has some advice.

[edit]
@camper365:
I don't think /dev/sdb is his hard drive, as he said it's a 320GB and fdisk only reports it as a 20GB.

Although, I suppose it's possible the system didn't recognize the capacity properly.

@Ranemills
Can you post the output of

```

sudo fdisk -l

```

with the hard drive unplugged?

---

### Post by Ranemills on 2009-08-01
I just ran the commands that you gave me. They mounted my second internal hard drive, the 20 GB one.

---

### Post by SuperSonic4 on 2009-08-01
Hmm, it seems like it's not being recognised...

What happens if you open up gparted (either get it through the repos or use a live cd) and look for it there? Especially if it's not formatted

> I just ran the commands that you gave me. They mounted my second internal hard drive, the 20 GB one.

Yeah it would, that poster must have misread the original post

---

### Post by Ranemills on 2009-08-01
All I get is the two internal hard drives inside GParted.

---

### Post by wojox on 2009-08-01
```
lsusb
```

What's it seeing?

---

### Post by Ranemills on 2009-08-01
@ Volt9000

```

ryan@ryan-desktop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a4a9a6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7161    57520701   83  Linux
/dev/sda2            7162        7299     1108485    5  Extended
/dev/sda5            7162        7299     1108453+  82  Linux swap / Solaris

Disk /dev/sdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26412640

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2482    19936633+   7  HPFS/NTFS

```

@wojox

```

ryan@ryan-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 019: ID 04fc:0c05 Sunplus Technology Co., Ltd 
Bus 004 Device 002: ID 05fe:1010 Chic Technology Corp. Optical Wireless
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by Ranemills on 2009-08-01
After plugging it back in to do Wojox's command, it's automatically been recognised. Now it's working. Not sure what happened. Do you think it will happen like that from now on? Or is it just a one off?

---

### Post by Volt9000 on 2009-08-01
Try another

```

dmesg | tail -20

```

to see if you have a different output than before. It doesn't make sense that it's not working, then all of a sudden it starts working.

---

### Post by Ranemills on 2009-08-01
I increased the output to 30 to show what was before it working as well.

```

ryan@ryan-desktop:~$ dmesg | tail -30
[ 4462.331484] wlan0: RX ReassocResp from 00:1b:2f:6d:67:e4 (capab=0x431 status=0 aid=2)
[ 4462.331497] wlan0: associated
[ 5480.720133] usb 4-2: USB disconnect, address 18
[ 5867.840101] usb 4-2: new full speed USB device using uhci_hcd and address 19
[ 5868.022104] usb 4-2: not running at top speed; connect to a high speed hub
[ 5868.076013] usb 4-2: configuration #1 chosen from 1 choice
[ 5896.120124] usb 4-2: USB disconnect, address 19
[ 5896.384112] usb 4-2: new full speed USB device using uhci_hcd and address 20
[ 5896.682882] usb 4-2: not running at top speed; connect to a high speed hub
[ 5896.744115] usb 4-2: configuration #1 chosen from 1 choice
[ 5896.994360] Initializing USB Mass Storage driver...
[ 5897.000373] scsi2 : SCSI emulation for USB Mass Storage devices
[ 5897.001075] usbcore: registered new interface driver usb-storage
[ 5897.001086] USB Mass Storage support registered.
[ 5897.057691] usb-storage: device found at 20
[ 5897.057700] usb-storage: waiting for device to settle before scanning
[ 5902.058037] usb-storage: device scan complete
[ 5908.112109] usb 4-2: reset full speed USB device using uhci_hcd and address 20
[ 5908.268996] scsi 2:0:0:0: Direct-Access     WDC WD32 00AAJB-00WGA0         PQ: 0 ANSI: 2
[ 5908.285962] sd 2:0:0:0: [sdc] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[ 5908.291972] sd 2:0:0:0: [sdc] Write Protect is off
[ 5908.291987] sd 2:0:0:0: [sdc] Mode Sense: 38 00 00 00
[ 5908.291994] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 5908.345915] sd 2:0:0:0: [sdc] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[ 5908.350864] sd 2:0:0:0: [sdc] Write Protect is off
[ 5908.350873] sd 2:0:0:0: [sdc] Mode Sense: 38 00 00 00
[ 5908.350879] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 5908.350898]  sdc: sdc1
[ 5914.025523] sd 2:0:0:0: [sdc] Attached SCSI disk
[ 5914.025768] sd 2:0:0:0: Attached scsi generic sg4 type 0

```

---

### Post by Volt9000 on 2009-08-02
Interesting, the only difference seems to be that before, the dmesg output stopped at

```

usb 4-2: configuration #1 chosen from 1 choice

```

whereas now you have

```

Initializing USB Mass Storage driver...

```

Not sure what happened between these two instances, but, there ya go...

---

### Post by Ranemills on 2009-08-02
The only difference that I made was that I had switched the external drive on before plugging it in, as there is a switch on it. It's working fine still, so maybe I just needed to have it switched on before plugging it in.

---

### Post by lswb on 2009-08-02
Is your external drive powered through the usb port only? Sometimes there is just not enough current available to run a hd from the usb port. If it has an AC adapter use that as well, or (less preferable) one of those usb cables with a second plug that goes in another usb port on the computer.

---

### Post by Ranemills on 2009-08-02
Yeah, it's always plugged in to the socket. I think this is pretty much solved anyway. I'll come back if I have any more problems. Thanks to everyone who tried to help!

---

