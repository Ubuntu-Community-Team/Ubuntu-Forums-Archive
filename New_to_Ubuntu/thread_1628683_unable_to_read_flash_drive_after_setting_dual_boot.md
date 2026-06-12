---
title: "unable to read flash drive after setting dual boot(ubuntu 10.10 and windows xp)"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by vkimovich on 2010-11-23
I installed windows xp 3 after ubuntu 10.10 in dual boot mode. Things went fine after retrieving grub from ubuntu 10.10 but ubuntu cannot read flash drives after doing so (tried many flash drive brands). Any tips or similar experiences?  Any help would be appreciated. :) Thanks.

---

### Post by mikewhatever on 2010-11-23
That's odd, and seems unrelated to installing Windows. Do you get any error messages when trying to access a flash drive? If not, what happens exactly?

---

### Post by karlwbloedorn on 2010-11-23
Try typing "dmesg" and hit enter in a terminal.

Then plug in a usb drive

Then try "dmesg" again. What is at the very end of the output that wasn't there before you plugged it in?

---

### Post by vkimovich on 2010-11-23
> **mikewhatever said:**
> That's odd, and seems unrelated to installing Windows. Do you get any error messages when trying to access a flash drive? If not, what happens exactly?
No error message appears. Its just that the usb drive could not be recognized. I tried plugging in the flash drive then restart. Sometimes it works 2% of the time. Last known good configuration was before installing windows in the partition so im guessing it was from that process since i had to restore grub2 from the live disc. Im not sure though. Could it be that installing windows wipedout other things aside from grub2? Thanks.

---

### Post by mikewhatever on 2010-11-23
WEll, I hate to be a pita, but can you explain in details, how you know that the 'drive could not be recognized'.
Installing Windows to another partition doesn't really remove Grub or anything else from Ubuntu, it just overwrites the MBR of the hdd. Anyway, if that's all somewhat confusing, plug in a usb drive, then run the following from a terminal and post the outputs:

sudo fdisk -l

dmesg | tail

mount | grep /dev/sd

---

### Post by vkimovich on 2010-11-23
> **karlwbloedorn said:**
> Try typing "dmesg" and hit enter in a terminal.

Then plug in a usb drive

Then try "dmesg" again. What is at the very end of the output that wasn't there before you plugged it in?
This part of the message was not present when i plugged it in. Thanks.

[  197.739925] usb 1-4: USB disconnect, address 2
[  222.322314] wlan0: authenticate with 00:1e:e5:3b:fe:fb (try 1)
[  222.352910] wlan0: authenticated
[  222.352947] wlan0: associate with 00:1e:e5:3b:fe:fb (try 1)
[  222.552070] wlan0: associate with 00:1e:e5:3b:fe:fb (try 2)
[  222.558192] wlan0: RX AssocResp from 00:1e:e5:3b:fe:fb (capab=0x401 status=0 aid=5)
[  222.558200] wlan0: associated
[  222.558785] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  233.105072] wlan0: no IPv6 routers present

---

### Post by karlwbloedorn on 2010-11-23
One more command to run when the usb drive is plugged in "lsusb". What is the output of this command?

Also, if you haven't already tried using a couple different USB ports, do it and see if any of them work.

---

### Post by vkimovich on 2010-11-23
I meant that the device does not show up. Sorry. Anyway this is what shows up. Thanks. I really appreciate it. :)

:~$ sudo fdisk -l 
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x552d552d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7845    63014931    7  HPFS/NTFS
/dev/sda2            7846       19457    93272417+   5  Extended
/dev/sda3           18980       19457     3839503+  82  Linux swap / Solaris
/dev/sda5            7846       18979    89432064   83  Linux

Disk /dev/sdb: 4007 MB, 4007264256 bytes
74 heads, 10 sectors/track, 10576 cylinders
Units = cylinders of 740 * 512 = 378880 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              11       10577     3909312    c  W95 FAT32 (LBA)


:~$ dmesg | tail
[ 1973.653357] scsi 5:0:0:0: Direct-Access     Imation  Nano Pro         PMAP PQ: 0 ANSI: 0 CCS
[ 1973.654623] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 1973.987304] sd 5:0:0:0: [sdb] 7826688 512-byte logical blocks: (4.00 GB/3.73 GiB)
[ 1973.987918] sd 5:0:0:0: [sdb] Write Protect is off
[ 1973.987925] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1973.987930] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1973.991537] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1973.991550]  sdb: sdb1
[ 1974.007646] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1974.007657] sd 5:0:0:0: [sdb] Attached SCSI removable disk


:~$ mount | grep /dev/sd
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=600)

---

### Post by karlwbloedorn on 2010-11-23
From the looks of that output, I would wager that your flash drive is 4GB and is /dev/sdb. I would attempt to mount /dev/sdb1 to somewhere (maybe /mnt) as a FAT partition and see if it works.

Something like:
mount -t msdos /dev/sdb1 /mnt

---

### Post by mikewhatever on 2010-11-23
The device is clearly recognized according to the output, just not mounted. If you see it in the file browser, try mounting it by simply clicking with the mouse.

---

### Post by vkimovich on 2010-11-23
> **mikewhatever said:**
> The device is clearly recognized according to the output, just not mounted. If you see it in the file browser, try mounting it by simply clicking with the mouse.
Haha. Of course I would have done that if it was that simple. Anyway, I  could not see the device in the desktop or in the browser where it  usually shows up even though the output shows that the device is  recognized.

---

### Post by vkimovich on 2010-11-23
> **karlwbloedorn said:**
> From the looks of that output, I would wager that your flash drive is 4GB and is /dev/sdb. I would attempt to mount /dev/sdb1 to somewhere (maybe /mnt) as a FAT partition and see if it works.

Something like:
mount -t msdos /dev/sdb1 /mnt
This command gives me back a blank prompt. After entering it again, I get a message that says it is already mounted. However, I could still not see the drive in the desktop or in the browser where it usually shows up when I plug the Flash Drive.

---

### Post by mikewhatever on 2010-11-24
> **vkimovich said:**
> This command gives me back a blank prompt. After entering it again, I get a message that says it is already mounted. However, I could still not see the drive in the desktop or in the browser where it usually shows up when I plug the Flash Drive.

Partitions mounted under /mnt don't show on the desktop. Try manually navigating to /mnt in the file browser.

---

### Post by vkimovich on 2010-11-25
> **mikewhatever said:**
> Partitions mounted under /mnt don't show on the desktop. Try manually navigating to /mnt in the file browser.
Oh. Well checking mnt shows the contents of the flashdrive and i can copy it to my filesystem but not vice versa. I cannot copy anything into the flash drive. Any solutions? Thanks. 

And also, there was a suggestion from another thread that i should use
         sudo mkdir /media/usbdrive
         sudo mount /dev/sdb /media/usbdrive

These commands make me see the flash drive in nautilus but the same problem occurs where i can access the files from the flash drive but I cannot write anything into it.

Do you know a solution where I could restore my previous settings so that plugging the flash drive will automatically mount it and I can see it in the browser or desktop? Thanks

---

### Post by mikewhatever on 2010-11-25
You might need to run a file system check on the drive. If Ubuntu thinks the file system is inconsistent, it sometimes won't automount it or will only mount as read only. Just make sure to unmount it first.

```
sudo umount /dev/sdb

sudo fsck -vy /dev/sdb1
```

---

### Post by vkimovich on 2010-11-25
> **mikewhatever said:**
> You might need to run a file system check on the drive. If Ubuntu thinks the file system is inconsistent, it sometimes won't automount it or will only mount as read only. Just make sure to unmount it first.

```
sudo umount /dev/sdb

sudo fsck -vy /dev/sdb1
```
Thanks. I get this message but I really don't know what it means

:~$ sudo fsck -vy /deb/sdbl
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: No such file or directory while trying to open /deb/sdbl

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

Thanks.

---

### Post by mikewhatever on 2010-11-25
The partition in question is /dev/sdb1 (that's one at the end and not small L).

---

### Post by vkimovich on 2010-11-25
> **mikewhatever said:**
> The partition in question is /dev/sdb1 (that's one at the end and not small L).
Oh. Sorry. I found out that I could now delete and write files into the flash drive by using

sudo mkdir /media/drive1

sudo mount /dev/sdb1 /media/drive1

....Then use the terminal as a root to copy, move, and delete files. (I could not do this with nautilus)
Thanks for the help. 
Do you know of a  way that I can return to the old setting where the flash drive automatically mounts and shows itself in the desktop or in nautilus?

Something's really wrong with my system and I really don't know what's causing all of it. I lately tried to check if it still reads discs in the cdrom so I inserted the lxf130 dvd and I could hear it turning but nothing appears. This used to work before. I tried several cds and nothing works.

---

### Post by mikewhatever on 2010-11-27
I don't know. This could be a hardware issue.

---

### Post by vkimovich on 2010-11-29
> **mikewhatever said:**
> I don't know. This could be a hardware issue.
I found out that i need to manually mount the disc in the cd rom just like in the flash drive case by
sudo mkdir /media/drive1
sudo mount /dev/cdrom /media/drive1.
I still dont know why things started to fail automatically. I am using an asus f80l laptop.

Thanks for all the help. I really appreciate it. :)

---

