---
title: "Unable to mount external HD in 10.04"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by mathfreak123 on 2010-05-02
The title says it all. I have a SimpleTech Signature Mini 500 GB USB external hard drive that just won't mount ever since I upgraded to 10.04.

I have no clue what to do, and I don't think autofs is what 9.10 used before. :S

(In all seriousness, I kind of want to downgrade back to 9.10. This probably won't be easy, so the best way to do this is a clean install, right?)

---

### Post by mikewhatever on 2010-05-02
I think it's silly to reinstall just because a usb device wouldn't mount. At least try troubleshooting first. Does an entry appear in the left panel of the file browser? Do you get any errors? Plug the drive in, then run the following commands and post the outputs:

```
sudo fdisk -l
dmesg | tail
```

---

### Post by johnnoshay on 2010-05-02
i have the same problem after 10.04 update. ALL USB  and drives not recognised. Total beginner . take it easy . I have posted the terminal info .here .help.BeSorry, try again.
[sudo] password for squonk: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0b027a56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3585    28796481   83  Linux
/dev/sda2            3586        4864    10273567+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris
/dev/sda6            3586        4607     8209152   83  Linux
/dev/sda7            4608        4659      417658+  82  Linux swap / Solaris

Partition table entries are not in disk order
squonk@squonk-laptop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0b027a56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3585    28796481   83  Linux
/dev/sda2            3586        4864    10273567+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris
/dev/sda6            3586        4607     8209152   83  Linux
/dev/sda7            4608        4659      417658+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1031 MB, 1031798784 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         126     1007584+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 51)
squonk@squonk-laptop:~$ dmesg | tail
[ 1561.381824] scsi 2:0:0:0: Direct-Access     Generic  USB Flash Disk   0.00 PQ: 0 ANSI: 2
[ 1561.388673] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 1561.393029] sd 2:0:0:0: [sdb] 2015232 512-byte logical blocks: (1.03 GB/984 MiB)
[ 1561.404486] sd 2:0:0:0: [sdb] Write Protect is off
[ 1561.404498] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 1561.404507] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1561.408678] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1561.408691]  sdb: sdb1
[ 1561.555072] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1561.555087] sd 2:0:0:0: [sdb] Attached SCSI removable disk
squonk@squonk-laptop:~$ 
fore and after usb mount.

---

### Post by mikewhatever on 2010-05-02
What do you mean by 'not recognized'? Do you get 'NOT RECOGNIZED' icons on the desktop for every usb drive?
As you can see, there is a 1GB (/dev/sdb) usb flash drive which is definitely recognized. Are there more attached?

---

### Post by mathfreak123 on 2010-05-02
It's not just that I want to reinstall due to a hard drive not being recognized, but there seem to be more issues for me to deal with in 10.04. Oh well... gotta fix them one-by-one...

Output of sudo fdisk -l
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe4ae7bcf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       14679   116365851    7  HPFS/NTFS
/dev/sda3           14680       30401   126286965    5  Extended
/dev/sda5           14680       29757   121114003+  83  Linux
/dev/sda6           29758       30401     5172898+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdbf79d17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

```

Output of dmesg|tail (and a bit more):
```

[  158.664210] usb 1-2: new high speed USB device using ehci_hcd and address 2
[  158.812353] usb 1-2: configuration #1 chosen from 1 choice
[  158.885596] Initializing USB Mass Storage driver...
[  158.885817] scsi5 : SCSI emulation for USB Mass Storage devices
[  158.885982] usbcore: registered new interface driver usb-storage
[  158.885988] USB Mass Storage support registered.
[  158.888863] usb-storage: device found at 2
[  158.888866] usb-storage: waiting for device to settle before scanning
[  163.888559] usb-storage: device scan complete
[  164.908949] scsi 5:0:0:0: Direct-Access     Hitachi  HTS545050B9A300  PB4O PQ: 0 ANSI: 0
[  164.909745] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  164.910757] sd 5:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[  164.912868] sd 5:0:0:0: [sdb] Write Protect is off
[  164.912876] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  164.912881] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  164.914359] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  164.914368]  sdb: sdb1
[  164.933376] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  164.933385] sd 5:0:0:0: [sdb] Attached SCSI disk

```

Also: an entry does not appear in the left panel of the file browser.

---

### Post by WiReIs on 2010-05-02
i am having this problem aswell.. 

my exHD is recognised and mounts fine, but my Fujifilm camera does not mount and is not recognised in the nautilus

---

### Post by mathfreak123 on 2010-05-02
I am currently using autofs and automount as temporary fixes to this problem. If anyone has a better solution, please post it on this thread to share.

---

### Post by mikewhatever on 2010-05-03
As you can see from the output, you have a 500GB ntfs hdd, /dev/sdb, which is recognized just fine. The problem seems to be that it doesn't show in Nautilus, nor does it automount. In case you dual boot with Windows, try running a file system check on that drive.

Edit:Also, make sure to always unplug the drive properly. If you just pull the cord, the ntfs partition gets marked as 'unclean' and wouldn't automount in Ubuntu.

---

### Post by egalvan on 2010-05-03
[QUOTE=mikewhatever;9225939In case you dual boot with Windows, try **running a file system check on that drive**.[/QUOTE]

+1

He shows a bootable NTFS, so it's probably dual-booting with Windows.

He should boot into Windows, do a complete "check disk for errors",
re-boot into Windows and check it again (Windows will sometimes miss errors, this step will help)
then shut down and boot into Ubuntu.

then run

```
mount
```

to show all mounted drives.

---

### Post by 23dornot23d on 2010-05-03
I just want to add a quick one liner here ....

Sometime the USB drives can be slow at picking up on initial boot ...... I sometimes have to re-start the machine twice from a cold start ...... for it to mount my USB drives ...

I have a Terra Drive and a 500gig plugged in most of the time but as I say from the first boot up in a morning ..... sometimes I have to re-start the computer after the drives have been powered up properly ...... 

Just a thought ..... hope this helps ..... 

(  If you do not boot up from your USB drive ..... 
see if it mounts - by plugging it in once you get the desktop loaded ... )

---

### Post by sb5551 on 2010-05-03
I don't know if this helps, but I am having the same kind of problem with my external harddrive; however, it is a network hardrive. I can get it mounted by using connect to server just like I did in 9.10, but nautilus can't show the folders. It just says error in the steam or something. Sorry I don't have the computer near me right now. 
 
I can get into the drive through my computer when booting into windows 7 and see all the folders. I can also get see all the folders through my gf's mac. I can also see the folders going through the internet of mounting it on my netbook using 9.04. It is just 10.04 that it doesn't work.

---

### Post by mikewhatever on 2010-05-03
> **sb5551 said:**
> I don't know if this helps, but I am having the same kind of problem with my external harddrive; however, it is a network hardrive. I can get it mounted by using connect to server just like I did in 9.10, but nautilus can't show the folders. It just says error in the steam or something. Sorry I don't have the computer near me right now. 
 ...

I think the problem you describe is quite a bit different. See, we've been discussing usb drives that are directly attached to the computer usb port. Yours seems to be a samba related issue, but since you can access the drive through 'Connect to server...', I don't see the problem.

---

### Post by sb5551 on 2010-05-03
Sorry, I thought it was the same because his computer was recognizing the drive, but he couldn't see the folders, just like I can't see my folders but nevermind. I will start my own thread, don't mean to hijack this one.

---

### Post by mathfreak123 on 2010-05-03
Went into windows and checked the disk. I booted back into Ubuntu, and the same result occurs: still can't mount. It says I'm not authorized to mount the drive. I can mount fine with sudo, but then everything is labeled as owned by root, which can be pretty annoying, since nearly doing anything with the files would require me to use sudo.

Using sudo chown is a second option, but that's just as annoying. I am still currently using autofs to mount my disk.

---

### Post by mikewhatever on 2010-05-03
mathfreak123, How exactly were you trying to mount it, when the authorization error appeared?

---

### Post by mathfreak123 on 2010-05-03
I just plug it in and wait for it to mount like in 9.10. Instead of mounting, I get the "unable to mount" message.

To get around that, I usually either use sudo mount (which makes all the files on the drive appear to be owned by root), or I let autofs take care of it for me. :S

EDIT: I'm still considering reinstalling Karmic, and it's not just because I'm having issues with mounting external HDs. I seem to be having some other problems as well.

---

### Post by mikewhatever on 2010-05-04
> **mathfreak123 said:**
> ...
EDIT: I'm still considering reinstalling Karmic, and it's not just because I'm having issues with mounting external HDs. I seem to be having some other problems as well.

To be honest, I still haven't switched to Lucid, as despite the bashing, and some initial sound problems, Karmic has been working very well for me. Ubuntu is known to be a little 'rough around the edges' at the release date.

---

### Post by mathfreak123 on 2010-05-04
Reinstalled Karmic. I was beginning to have issues just logging in on Lucid (in addition to other things). I think it'll be best for me to stick with Karmic for a while. I'm sorry for inconveniencing everyone who has tried to help.

---

