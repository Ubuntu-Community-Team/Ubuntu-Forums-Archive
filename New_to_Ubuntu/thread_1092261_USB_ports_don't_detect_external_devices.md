---
title: "USB ports don't detect external devices"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by darramonde on 2009-03-10
The USB ports don't automatically mount Ipod, digital camera, mobile phone etc. However, headphones and mic mount in Skype, but unfortunately not with none of the Ubuntu music players. 

This is a problem unknown in the Windows partition of my Packard Bell Easynote R1960 laptop.

Please help me, I'm sick and tired of Windows...

---

### Post by skymera on 2009-03-10
ok plug in the devices and run

```
 sudo fdisk -l 
```

Post the output please, that will tell us if it's being detected.
If so we can manually mount it :)

I've never personally used an iPod or Camera with Ubuntu, so this is the wat I'd do it :)

---

### Post by philinux on 2009-03-10
With the device connected open a terminal. Appps>access>terminal.

Issue the command

```
lsusb
```

See if that kickstarts it.

---

### Post by blueridgedog on 2009-03-10
In addition to the commends mentioned above, you can also get a great deal of information about a reluctant USB device by plugging it in, then using the command

dmesg

It will show you how the system interpreted the device plugged in and any error that was generated (you will want to look at only the text at the end as that would be related to your most recent action).

---

### Post by Locke_99GS on 2009-03-10
Plug one of your problematic devices in to a USB port, those please post the output of:

```
lsusb
```

and the last few lines (let say the last 10, to be safe) of:

```
dmesg
```

for us to begin with.


Note: Most devices should just work with recent kernels. For emample, my MP3 player and cell phone function perfectly with Intrepid - no configuration required. One area of pain can be digital cameras, which don't rely on the kernel, but rather *gphoto2*. The *gphoto2* maintainers do a good job trying to keep up with new camera models, but sometimes they are a bit behind. Furthermore, the Ubuntu developers sometimes cut corners when pushing for a release, and a recent issue has happened with some cameras that are recognised by *gphoto2* not having proper permissions to do anything with. Call this a regression in Intrepid. Hopefully it is repaired or kludged in Jaunty, and backported.

edit: Apparently, I'm typing fairly slowly today.

---

### Post by darramonde on 2009-03-10
> **skymera said:**
> ok plug in the devices and run

```
 sudo fdisk -l 
```

Post the output please, that will tell us if it's being detected.
If so we can manually mount it :)

I've never personally used an iPod or Camera with Ubuntu, so this is the wat I'd do it :)

ok:

Disk /dev/sda: 160,0 GB, 160041885696 byte
255 huvuden, 63 sektorer/spår, 19457 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0xace22e9e

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       18532    97659135   83  Linux
/dev/sda3           18533       19457     7430062+   f  W95 Utökad (LBA)
/dev/sda5           18533       19457     7430031   82  Linux växling / Solaris

---

### Post by darramonde on 2009-03-10
> **philinux said:**
> With the device connected open a terminal. Appps>access>terminal.

Issue the command

```
lsusb
```

See if that kickstarts it.

Nope. Nada.

---

### Post by darramonde on 2009-03-10
lsub

Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ac:1260 Apple, Inc. iPod Nano 2.Gen
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


> **blueridgedog said:**
> In addition to the commends mentioned above, you can also get a great deal of information about a reluctant USB device by plugging it in, then using the command

dmesg

It will show you how the system interpreted the device plugged in and any error that was generated (you will want to look at only the text at the end as that would be related to your most recent action).

Ok, here's the result:

[ 6762.328745] Initializing USB Mass Storage driver...
[ 6762.331422] scsi2 : SCSI emulation for USB Mass Storage devices
[ 6762.332585] usbcore: registered new interface driver usb-storage
[ 6762.332877] USB Mass Storage support registered.
[ 6762.333272] usb-storage: device found at 2
[ 6762.333278] usb-storage: waiting for device to settle before scanning
[ 6767.346753] usb-storage: device scan complete
[ 6768.088241] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 6769.328117] sd 2:0:0:0: [sdb] 3964928 2048-byte hardware sectors (8120 MB)
[ 6770.072190] sd 2:0:0:0: [sdb] Write Protect is off
[ 6770.072204] sd 2:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 6770.072208] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 6772.304117] sd 2:0:0:0: [sdb] 3964928 2048-byte hardware sectors (8120 MB)
[ 6773.048123] sd 2:0:0:0: [sdb] Write Protect is off
[ 6773.048135] sd 2:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 6773.048139] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 6773.051414]  sdb: sdb1 sdb2
[ 6774.293009] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 6774.293731] sd 2:0:0:0: Attached scsi generic sg2 type 0

---

### Post by darramonde on 2009-03-10
Oh my goodness! It works! But why? Can someone please explain the magic behind the commands and when/how to use them?

---

### Post by philinux on 2009-03-10
Girlfriends pc, my old one will not activate the usb 4 port hub without lsusb to kickstart it. No idea why except it's an old pc from 1999 with a new usb 2, 4 port hub. My new pc has no problems at all.
dmesg just shows the messages from the system.

---

### Post by darramonde on 2009-03-10
> **philinux said:**
> Girlfriends pc, my old one will not activate the usb 4 port hub without lsusb to kickstart it. No idea why except it's an old pc from 1999 with a new usb 2, 4 port hub. My new pc has no problems at all.
dmesg just shows the messages from the system.

Is there any way of configuring as it automatically mounts everytime or am I stuck for life with lsub:) ?

---

### Post by philinux on 2009-03-10
On my old pc I created a launcher on the desktop, type = application in terminal, with the command lsusb. I told my girlfriend to double click this as soon as desktop working. She uses a usb stick for her stuff.

Maybe a script at startup might do the trick but the above workaround is just fine for us. Like I said on my new pc, bought last year, this is not a problem.

Next time I'm there I might try sticking lsusb in System>prefs>sessions, see if that does the trick.

---

