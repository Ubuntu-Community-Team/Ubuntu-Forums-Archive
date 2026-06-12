---
title: "[SOLVED] Unable to mount DIgital Camera"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by nicholas mccarthy on 2008-12-06
Hello,

When I try to mount my digital camera, this comes up:

Unable to mount Nikon Corp. Coolpix 4600 (ptp)
Error initializing camera: -1: Unspecified error

Anything you guys can do to help would be greatly appreciated.

---

### Post by newbee70 on 2008-12-06
> **nicholas mccarthy said:**
> Hello,

When I try to mount my digital camera, this comes up:

Unable to mount Nikon Corp. Coolpix 4600 (ptp)
Error initializing camera: -1: Unspecified error

Anything you guys can do to help would be greatly appreciated.

Nicholas, give us a run down on what distribution your using, and on your system. so everyone can try to help you out.

and give a description on how you attached the camera. 

my Nikon is found just like a removable disk.

---

### Post by malathion on 2008-12-06
Please post the output of this command:

```
sudo fdisk -l
```

---

### Post by linux_tech on 2008-12-06
First see if the computer at least recognizes that the camera is plugged into the usb port:

```
 lsusb
```

---

### Post by nicholas mccarthy on 2008-12-06
> **malathion said:**
> Please post the output of this command:

```
sudo fdisk -l
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005e987

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1cb31993

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7301    58645251    7  HPFS/NTFS


> **linux_tech said:**
> First see if the computer at least recognizes that the camera is plugged into the usb port:

```
 lsusb
```

Bus 004 Device 002: ID 4971:cb01  
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 04b0:0130 Nikon Corp. Coolpix 4600 (ptp)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


> **newbee70 said:**
> Nicholas, give us a run down on what distribution your using, and on your system. so everyone can try to help you out.

and give a description on how you attached the camera. 

my Nikon is found just like a removable disk.

I'm using 8.10. I plugged in the cord to the USB port and plugged in the camera. On my computer I had a while ago, still with Ubuntu on it, that's all I had to do to mount it.

---

### Post by scorp123 on 2008-12-06
> **nicholas mccarthy said:**
> Anything you guys can do to help would be greatly appreciated. Do you have a card reader? If yes: you could remove the card from the camera and insert it into your Ubuntu system as if it were a floppy disk. That should work.

Also: I am not familiar with your type and brand of camera ... but with the HP cameras that I have it is possible to go into their "Settings" menus and there one can then define how they should be seen by PC's ... either as "Camera" or as "USB Mass Storage". At least on one of my cameras the "Camera" mode doesn't work, so I set it to "USB Mass Storage". Now when I connect it to my Ubuntu system my camera is seen as "Disk Drive" ... the end result is the same: I get to copy my pictures off the camera.

Maybe you could check if your camera has a similar feature?

---

### Post by nicholas mccarthy on 2008-12-06
> **scorp123 said:**
> Do you have a card reader? If yes: you could remove the card from the camera and insert it into your Ubuntu system as if it were a floppy disk. That should work.

Also: I am not familiar with your type and brand of camera ... but with the HP cameras that I have it is possible to go into their "Settings" menus and there one can then define how they should be seen by PC's ... either as "Camera" or as "USB Mass Storage". At least on one of my cameras the "Camera" mode doesn't work, so I set it to "USB Mass Storage". Now when I connect it to my Ubuntu system my camera is seen as "Disk Drive" ... the end result is the same: I get to copy my pictures off the camera.

Maybe you could check if your camera has a similar feature?

No, I don't have a card reader.

And no, there's no setting on my camera like that, it's a few years old though, so I don't know. It's a Nikon Coolpix 4600 if that helps.

---

### Post by newbee70 on 2008-12-06
> 
Bus 004 Device 002: ID 4971:cb01  
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 04b0:0130 Nikon Corp. Coolpix 4600 (ptp)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




I'm using 8.10. I plugged in the cord to the USB port and plugged in the camera. On my computer I had a while ago, still with Ubuntu on it, that's all I had to do to mount it.


on your setup menu how do you have this set?

# Interface

    * USB (PTP, Mass Storage)
    * Video mode (NTSC, PAL)

Hopefully USB mass storage.

# Auto transfer (on/off) - whether photos are automatically transferred to your PC by default .

---

### Post by nicholas mccarthy on 2008-12-06
yeah, I have it as Mass Storage, I don't get why it is saying PTP then when I plug it in?

---

### Post by newbee70 on 2008-12-06
> **nicholas mccarthy said:**
> yeah, I have it as Mass Storage, I don't get why it is saying PTP then when I plug it in?

Have you tried setting the camera for PTP, to see if it will recognize it in that mode?

---

### Post by nicholas mccarthy on 2008-12-06
Oh, I didn't even think about doing that, it worked! Thanks!

---

### Post by Radio89 on 2012-04-11
Writing here as a reference for Google.

I had the same problem (Unable to mount camera. error unspecified -1) today, resolved not using the USB 3.0 port of my pc but falling back to the "normal" 2.0 ones.

Not sure if it is a bug or the intended behaviour (what about a future with only usb 3.0 ports?)

P.S. Reported @SF against libgphoto2 ref. #3517006

---

### Post by oldos2er on 2012-04-11
Closed, necromancy.

---

