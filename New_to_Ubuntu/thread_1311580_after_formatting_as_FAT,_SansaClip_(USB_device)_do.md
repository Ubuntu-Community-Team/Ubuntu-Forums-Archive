---
title: "after formatting as FAT, SansaClip (USB device) does not on Ubuntu when connected"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by hanzj on 2009-11-02
Hello,
I was preparing to use my SansaClip (2GB usb device) as my bootable Ubuntu 9.10 device. So the first step I did was format it as FAT. I disconnected it and reconnected, but now the SansaClip screen gives this message: 
> Not enough space for music DB. Please free 30MB

 If that wasn't enough of a problem, the device won't appear on my Desktop (as it usually does) nor appear in Places list.

Pls advise.

---

### Post by hanzj on 2009-11-02
I unsuccessfully followed the instructions on [https://help.ubuntu.com/community/Mount/USB#Manually Mounting]("https://help.ubuntu.com/community/Mount/USB#Manually Mounting").

I did
```
sudo fdisk -l
```
I see my MP3 Device in the last part:
> Disk /dev/sdc: 2044 MB, 2044198912 bytes
63 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x00015c34

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1022     1995935    c  W95 FAT32 (LBA)


I then created a mountpoint:

```
sudo mkdir /media/sansaclip
```


I then tried mounting the drive. When I do ```
 sudo mount -t vfat /dev/sdc1 /media/sansaclip -o uid=1000,gid=100,utf8,dmask=027,fmask=137
```, I get the error message 

> mount: wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail  or so


i see the MP3 USB device in ```
lsusb
```
 > Bus 001 Device 004: ID 0781:7433 SanDisk Corp. Sansa Clip (msc)

---

### Post by hanzj on 2009-11-02
by the way, here's the info from 
 ```
dmesg | tail
```> 
[ 2148.282869] sd 9:0:0:0: [sdc] Mode Sense: 04 00 00 00
[ 2148.282874] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[ 2148.307548] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[ 2148.307558]  sdc: sdc1
[ 2148.348557] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[ 2148.348568] sd 9:0:0:0: [sdc] Attached SCSI removable disk
[ 2337.549642] FAT: bogus number of reserved sectors
[ 2337.549651] VFS: Can't find a valid FAT filesystem on dev sdc1.
[ 2965.082523] FAT: bogus number of reserved sectors
[ 2965.082532] VFS: Can't find a valid FAT filesystem on dev sdc1.

---

### Post by sandyd on 2009-11-02
> **hanzj said:**
> Hello,
I was preparing to use my SansaClip (2GB usb device) as my bootable Ubuntu 9.10 device. **So the first step I did was format it as FAT.** I disconnected it and reconnected, but now the SansaClip screen gives this message: 


 If that wasn't enough of a problem, the device won't appear on my Desktop (as it usually does) nor appear in Places list.

Pls advise.
Heres the problem.
1. the sansa clip is not a usb mass storage device. its a mtp device.(by default)
2. The sansa clip requires its own special partition, hence the message on the screen.

---

### Post by hanzj on 2009-11-02
Carlee,
thanks for your reply.
1. You mentioned that it's not a "USB mass storage device. It's an MTP device." Ok. I guess I thought that since I can copy and paste some non-media files (files such as documents and spreadsheets) onto the sansa clip, that the Sansa Clip doubles as a USB storage device.


2. You mentioned that the Sansa Clip requires its own special partition. How can I give it its own special partition, if Ubuntu does not even recognize things?

---

### Post by hanzj on 2009-11-02
On System/Administration/Disk Utility (Palimpsest Disk Utility), I can see the SanDisk Sansa Clip 2GB.

---

### Post by peculiar penguin on 2009-11-02
You could check Sansa's support pages, they may have a recovery tool that reinstalls the firmware and properly sets up the partitions/file systems the way it needs them (but if they do it'll probably be for Windows only).

---

### Post by hanzj on 2009-11-02
Hello,
In Disk Utility (System/Administration/Disk Utility), I currently see the Type as > W95 FAT32 (LBA) (OxOc). There is a check in the box beside the word "Bootable". Should the Partition be changed to something else?

---

### Post by hanzj on 2009-11-02
**[COLOR="Red"]SOLUTION[/COLOR]**
I solved the problem by going to a Windows XP computer.

I opened up "My Computer". I saw the device. I formatted the drive with the default type (I think it was FAT). I then ran Sansa Firmware Updater to get the version from 1.01.30 to version 1.01.32. I tried adding an mp3 audio file onto the Clip. I couldn't find the device in "Safely Remove Hardware" but after I did remove the hardware, I saw the message "Disconnected" and then "Refreshing Media". I then saw the mp3 in the Clip and played it.


What I don't understand is why I don't see the device on System/Adminstration/Disk Utility. When the device was not working, I saw the Device. Maybe this is related to what carlee posted.

---

### Post by hanzj on 2009-11-04
I was finally able to get the Sansa Clip working by changing from MTP to MSC/UMS on the Sansa Clip's Settings/USB Mode

reference: [https://help.ubuntu.com/community/SansaClip](https://help.ubuntu.com/community/SansaClip)

---

