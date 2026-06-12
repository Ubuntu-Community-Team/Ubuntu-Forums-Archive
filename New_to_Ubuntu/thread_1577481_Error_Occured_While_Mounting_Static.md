---
title: "Error Occured While Mounting Static"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by lkraemer on 2010-09-18
After trying to get my Floppy to mount on Ubuntu 10.04, I have started getting the following Error Message:
"An Error Occured While Mounting Static"
"Press S to skip mounting, or M for Manual Recovery."

I have one Physical 500 Gig Drive in my Laptop partitioned as follows:
/dev/sda1  /          19.53 Gig
/dev/sda2  /Home      437.92 Gig
/dev/sda4  Linux/Swap 8.30 Gig

My Laptop has 3 Gig RAM.

Why am I getting this Error Message and how do I fix the problem?
My Laptop boots properly when I SKIP the mounting.

Here is the Posting I followed while getting the Floppy to mount.
[http://ubuntuforums.org/showthread.php?t=1569234](http://ubuntuforums.org/showthread.php?t=1569234)


Thanks.

L Kraemer

---

### Post by jtarin on 2010-09-18
Is this a USB floppy drive?

---

### Post by Dustin2128 on 2010-09-19
> **jtarin said:**
> Is this a USB floppy drive?
If there's a 500GB hard drive and 3GB of RAM in said laptop, it definitely is- they haven't offered them internally for years before laptops got that much hardware.

---

### Post by jtarin on 2010-09-19
> **Dustin2128 said:**
> If there's a 500GB hard drive and 3GB of RAM in said laptop, it definitely is- they haven't offered them internally for years before laptops got that much hardware.
Shows my attention to laptops.:P

---

### Post by lkraemer on 2010-09-20
This error message may not have anything to do with trying to get my 
External USB Floppy to mount, but before trying to get the floppy to mount
it showed up as /dev/sdc with (0) bytes when it was plugged into my
computer.  I used Gparted to look at what hard drives were mounted and
accidentally saw a second one sdc when the USB Floppy was connected.

I removed the floppy from the USB port, and then I only have /dev/sda
as a Hard Drive which is correct.

Here is the posting I was following when I was trying to get the External
USB Floppy to mount.

[http://ubuntuforums.org/showthread.php?t=1569234](http://ubuntuforums.org/showthread.php?t=1569234)

There has to be some Guru out there that can assist getting to the problem
causing this error message on every boot.

Here is the output from the mount command:
larry@larry-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda2 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/larry/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=larry)
larry@larry-laptop:~$

My /etc/fstab contains:
/etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=eb736378-7ae5-4810-a6fb-1f6c43795c26 /               ext3    errors=remoun$
# /home was on /dev/sda2 during installation
UUID=25ac3cf2-e73b-4f92-951c-bf486ee7fd73 /home           ext3    defaults     $
# swap was on /dev/sda4 during installation
UUID=fdae0d31-62f4-4951-814e-91c3d4cf50ad none            swap    sw           $


My /proc/mount contains:
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /dev devtmpfs rw,relatime,size=1507404k,nr_inodes=212112,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
/dev/disk/by-uuid/eb736378-7ae5-4810-a6fb-1f6c43795c26 / ext3 rw,relatime,error$
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
/dev/sda2 /home ext3 rw,relatime,errors=continue,data=ordered 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatim$
gvfs-fuse-daemon /home/larry/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relati$

A google search only found one other similar posting at:
[http://ubuntuforums.org/showthread.php?t=1468486](http://ubuntuforums.org/showthread.php?t=1468486)

Any help would be appreciated.

Thanks.


lk

---

### Post by jtarin on 2010-09-20
After plugging in the external USB floppy, wait about 10 seconds, and then paste the output of this command:


```
dmesg | tail -n 30
```

---

### Post by lkraemer on 2010-09-20
jtarin,
Thanks for the response.  Here is the output of dmesg.....

larry@larry-laptop:/etc$ dmesg | tail -n 30
[   38.471878] wlan0: authenticated
[   38.471908] wlan0: associate with AP 00:14:a5:31:f9:3a (try 1)
[   38.473996] wlan0: RX AssocResp from 00:14:a5:31:f9:3a (capab=0x431 status=0 aid=1)
[   38.474002] wlan0: associated
[   38.474709] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   48.968022] wlan0: no IPv6 routers present
[   60.020024] usb 7-1: new low speed USB device using uhci_hcd and address 2
[   60.194980] usb 7-1: configuration #1 chosen from 1 choice
[   60.259544] usbcore: registered new interface driver hiddev
[   60.275167] input: Logitech USB Trackball as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input11
[   60.275298] generic-usb 0003:046D:C408.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:1d.1-1/input0
[   60.275331] usbcore: registered new interface driver usbhid
[   60.275334] usbhid: v2.6:USB HID core driver
[ 1599.240393] ath5k phy0: unsupported jumbo
[ 4024.804069] usb 8-1: new full speed USB device using uhci_hcd and address 2
[ 4024.996269] usb 8-1: configuration #1 chosen from 1 choice
[ 4024.999418] scsi7 : SCSI emulation for USB Mass Storage devices
[ 4024.999772] usb-storage: device found at 2
[ 4024.999777] usb-storage: waiting for device to settle before scanning
[ 4029.996125] usb-storage: device scan complete
[ 4030.050183] scsi 7:0:0:0: Direct-Access     MITSUMI  USB FDD     070M 3.01 PQ: 0 ANSI: 0 CCS
[ 4030.053275] sd 7:0:0:0: Attached scsi generic sg3 type 0
[ 4030.562124] sd 7:0:0:0: [sdc] 2880 512-byte logical blocks: (1.47 MB/1.40 MiB)
[ 4030.690134] sd 7:0:0:0: [sdc] Write Protect is off
[ 4030.690142] sd 7:0:0:0: [sdc] Mode Sense: 00 4c 94 00
[ 4030.690147] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 4031.330120] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 4031.330131]  sdc:
[ 4032.098125] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 4032.098136] sd 7:0:0:0: [sdc] Attached SCSI removable disk
larry@larry-laptop:/etc$ 

And I can NOT mount the Floppy.....But it is shown as a Hard drive
in Gparted as the Floppy.png that I attached shows.....

When I remove the Floppy this false Hard Drive disappears....

I've also noticed three empty subdirectories under / and they
are:
selinux
srv
static

These were not there before.......

I've deleted all three, but static returns when I power up.

IDEAS??????

Thanks.

lk

---

### Post by jtarin on 2010-09-20
OK its showing up as /dev/sdc ....can you disable in the bios and then see what happens?

---

### Post by lkraemer on 2010-09-20
It is NOT enabled in my BIOS for Drive D.  But there is a Boot
device USB FLOPPY that is absolutely last in the boot up process.

lk

---

### Post by jtarin on 2010-09-20
/dev/sdc is the Linux designation for your USB drive......it has nothing to do with your bios. In the bios see if you can disable the USB floppy so it won't show in the boot process then boot up and see what happens.

---

### Post by lkraemer on 2010-09-21
jtarin,
There is nothing in my Compaq CQ50-139NR BIOS to disable or enable
anything for the USB Floppy.  Sorry.

Any other ideas?

Thanks.

lk

---

### Post by bodhi.zazen on 2010-09-22
I can not tell from what you have posted which partition you are having a problem with during boot.

If it is a removable device, try putting the option "noauto" in /etc/fstab

---

### Post by lkraemer on 2010-09-22
bodhi.zazen,
Thanks for the response.  As far as I know I am not having
a problem with a partition mounting, I just get an error message
each and every time I boot.  I press "S" to skip and it boots fine.
But, I'd like to prevent, or fix what is causing the error message.
The message started appearing after I tried to get my USB Floppy to
mount work with Ubuntu 10.04 LTS.

I don't know what the error message it is trying to tell me.
ERROR MOUNTING STATIC....PRESS "S" to SKIP or "M" for MANUAL.
I Press "S" and it boots.

lk

---

### Post by bodhi.zazen on 2010-09-22
The error message is telling you ubuntu is not finding the usb floppy when it tries to boot.

I am not sure which config file is looking for the floppy as I do not see an entry in fstab

---

### Post by lkraemer on 2010-09-22
bodhi.zazen,
If I plug in the USB Floppy, it shows up as /dec/sdc and shows up
as a hard drive, which Gparted sees, but has 0 storage.  And I can't
get any floppy disk to mount, or read a floppy in the drive.

When I REMOVE the USB Cable from the computer, /dec/sdc goes away.


I tried powering down, and plugged in the USB Floppy Drive, then
powered up.  Same error message, as when I boot without the USB
Floppy plugged in.

I plugged in the Floppy and after a bit I did dmesg |Tail.
```

larry@larry-laptop:~$ dmesg | tail
[  259.223794] usb-storage: waiting for device to settle before scanning
[  264.220150] usb-storage: device scan complete
[  264.239156] scsi 8:0:0:0: Direct-Access     MITSUMI  USB FDD     070M 3.01 PQ: 0 ANSI: 0 CCS
[  264.240411] sd 8:0:0:0: Attached scsi generic sg3 type 0
[  264.751144] sd 8:0:0:0: [sdc] 2880 512-byte logical blocks: (1.47 MB/1.40 MiB)
[  264.879143] sd 8:0:0:0: [sdc] Write Protect is off
[  264.879152] sd 8:0:0:0: [sdc] Mode Sense: 00 4c 94 00
[  264.879157] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  265.519131] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  265.519142]  sdc:

```

Nothing is shown mounted in /media or /mnt


lk

---

### Post by jtarin on 2010-09-22
Try editing your /etc/fstab to read as such. I've higlighted the changes.```
# / was on /dev/sda1 during installation
UUID=eb736378-7ae5-4810-a6fb-1f6c43795c26 / ext3 [COLOR="Red"]errors=remount-ro  0  1[/COLOR]
# /home was on /dev/sda2 during installation
UUID=25ac3cf2-e73b-4f92-951c-bf486ee7fd73 /home ext3 [COLOR="Red"]defaults 0  2[/COLOR]
# swap was on /dev/sda4 during installation
UUID=fdae0d31-62f4-4951-814e-91c3d4cf50ad none swap [COLOR="Red"]sw 0  0[/COLOR]
```

---

### Post by lkraemer on 2010-09-22
jtarin,
I don't know how, but my file /etc/fstab is exactly what you have posted.
```

/etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=eb736378-7ae5-4810-a6fb-1f6c43795c26 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=25ac3cf2-e73b-4f92-951c-bf486ee7fd73 /home           ext3    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=fdae0d31-62f4-4951-814e-91c3d4cf50ad none            swap    sw              0       0

```

I did change udisk to the previous version a few days back to get
the floppy disk functional and maybe that is when it was modified.

I still get the error message on power up or boot each and every time...

The floppy drive is fully functional by forcing and then locking udisk
to the previous version.

That error mounting static message is annoying....
 
lk

---

### Post by jtarin on 2010-09-22
In the Removable Drives and Media Preferences dialog (under
System/Preferences), you'll find an option to "Auto-run programs on new
drives and media". I believe the setting is Off by default.

---

### Post by lkraemer on 2010-09-22
Under SYSTEM -> PREFERENCES
I don't have "Removable Drives" or "Media Preferences"

I even went to EDIT MENU's to see if it could be added.

I just not finding it on 10.04 LTS.

lk

---

### Post by jtarin on 2010-09-22
> **lkraemer said:**
> Under SYSTEM -> PREFERENCES
I don't have "Removable Drives" or "Media Preferences"

I even went to EDIT MENU's to see if it could be added.

I just not finding it on 10.04 LTS.

lk

Places > Home > Edit > Preferences > Media and then navigate to the Media tab

---

### Post by jtarin on 2010-09-22
or run:
```
gconftool --set /apps/nautilus/preferences/media_automount_open --type bool "false"
```

There is also:
```
gconftool --set /apps/nautilus/preferences/media_automount --type bool "false"
```

Which I think skips auto-mount all together.

---

### Post by lkraemer on 2010-09-22
I've tried checking the box for:
"Never prompt or start programs on media insertion"
and un-checking the box for:
"Browse Media when inserted"
and then I powered off.  I still get the ERROR MOUNTING STATIC" Message
on bootup.


lk

---

### Post by jtarin on 2010-09-22
Look in your /dev folder...is there a device named static? It might be a hidden file so when in the directory using Nautilus do Ctrl+H to show .static. If youfind it try to change permissions.
(as root) :
chmod 755 /dev/static
or if hidden
chmod 755 /dev/.static

---

### Post by jtarin on 2010-09-22
OK...big update to this problem. I think what this error is indicating is that it cannot mount your "Static" entries /etc/fstab file due to the call being intercepted by something you have done previously during this mounting procedure of your floppy drive. If you installed some application to accomplish this...uninstall it. In otherwords undo everything you did before this problem appeared. This is my take on it. Could be totally wrong but I've run out of ideas as to how to solve this. There is an unknown factor in the mix that _should not normally_ be there,I feel.

---

### Post by lkraemer on 2010-09-22
jtarin,
Here is a listing of my commands in my history:
```

 1754  cd /
 1755  cd /media
 1756  ls
 1758  sudo mkdir floppy
 1759  mount /dev/fd0 /media/floppy
 1760  sudo mount /dev/fd0 /media/floppy
 1761  lsusb
 1762  ls
 1763  man mount
 1764  sudo mount /dev/fd0 /media/floppy
 1766  cd /
 1767  cd /media
 1768  cd floppy
 1769  ls
 1770  mount /dev/fd0
 1772  sudo mount /dev/fd0 /media/floppy
 1773  cd /
 1774  sudo nano /etc/fstab
 1783  sudo mount -t vfat /dev/fd0 /media/floppy
 1784  uname -r
 1786  udisks --mount /dev/fd
 1787  udisks --mount /dev/fd0
 1789  cd /
 1790  cd /media
 1791  ls
 1792  udisks --mount /dev/fd0 /media/floppy
 1793  udisks --mount /dev/sdb /media/floppy
 1794  ls
 1795  udisks --mount /dev/sdc /media/floppy
 1796  udisks --umount /dev/sdc 
 1800  cd /
 1801  cd /media
 1802  ls
 1803  cd floppy
 1804  ls
 1805  cd ..
 1806  rmdir floppy
 1807  sudo rmdir floppy
 1811  cd /
 1812  cd /media
 1813  sudo mkdir floppy0
 1814  sudo mount -t msdos /dev/fd0 /media/floppy0
 1815  lsusb
 1816  ls
 1817  sudo umount /media/floppy0
 1818  sudo umount /media/floppy0
 1819  ls
 1820  sudo rmdir floppy0
 1821  ls
 1822  cd /
 1823  cd /etc
 1824  sudo nano modules
 1825  sudo modprobe floppy

```
Would any of these commands have caused the problem?
If so, let me know how to reverse the command......

Maybe I need to remove the module floppy?


I didn't find anything for static in /dev even looking for hidden files.

There is a folder in / named static.  If I delete it, it is recreated the
next boot.

I have removed the module floppy with:
```

sudo modprobe -r floppy

```
so the next boot I will know for sure.  Don't know where I read to do this
but it is obviously not needed because my floppy still works.


Thanks.

lk

---

### Post by jtarin on 2010-09-22
Did you add Udisks? as extra package?

---

### Post by jtarin on 2010-09-22
I don't know where the config files is for this, but here is the manpage with options.I'm not on my Linux machine at home now.
[http://manpages.ubuntu.com/manpages/lucid/man7/udisks.7.html](http://manpages.ubuntu.com/manpages/lucid/man7/udisks.7.html)

---

### Post by jtarin on 2010-09-22
Maybe simply going in reverse order of your command list and unmounting all mounted devices with udisks preface command.

---

### Post by jtarin on 2010-09-23
Any resolution to this yet?

---

### Post by lkraemer on 2010-09-23
jtarin,
I used modprobe to remove the module floppy and on power up this
morning I have the same ERROR MESSAGE.

udisk is the default that is installed with Lucid.  I did FORCE it to
the previous version to make the floppy work as I posted in a previous thread.
NOTE: (With the previous version of udisk, the USB Floppy mounts properly, and the
ICON is a  Floppy Disk, and Gparted doesn't detect any extra hard disks added to my system.)

This morning, I unlocked udisk, and updated to the Lucid version, then ran:
```
sudo fdisk -l
```
The output is:
```

larry@larry-laptop:~$ sudo fdisk -l


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ba58e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+  83  Linux
/dev/sda2            2551       59717   459193927+  83  Linux
/dev/sda4           59718       60801     8707230   82  Linux swap / Solaris

Disk /dev/sdc: 1 MB, 1474560 bytes
1 heads, 3 sectors/track, 960 cylinders
Units = cylinders of 3 * 512 = 1536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x64616572

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?   544679435   600897836    84327602   77  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(288, 101, 57) logical=(544679434, 0, 3)
Partition 1 has different physical/logical endings:
     phys=(366, 104, 37) logical=(600897835, 0, 3)
Partition 1 does not end on cylinder boundary.
/dev/sdc2       651153345  1240483617   883995408   69  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(68, 13, 10) logical=(651153344, 0, 3)
Partition 2 has different physical/logical endings:
     phys=(288, 115, 43) logical=(1240483616, 0, 2)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?   179658779   644530213   697307152    d  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(357, 117, 50) logical=(179658778, 0, 2)
Partition 3 has different physical/logical endings:
     phys=(73, 10, 0) logical=(644530212, 0, 3)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?   499539979   502062033     3783081+  44  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(339, 83, 13) logical=(499539978, 0, 3)
Partition 4 has different physical/logical endings:
     phys=(288, 79, 19) logical=(502062032, 0, 3)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

So, when I plug in the USB Floppy, Ubuntu finds:
Disk /dev/sdc:
Partitions:
   /dev/sdc1
   /dev/sdc2
   /dev/sdc3
   /dev/sdc4

And Gparted finds sdc with 0 bytes.

```

udisks --dump

```
shows:
```

========================================================================
Showing information for /org/freedesktop/UDisks/devices/sdc
  native-path:                 /sys/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/host7/target7:0:0/7:0:0:0/block/sdc
  device:                      8:32
  device-file:                 /dev/sdc
    presentation:              /dev/sdc
    by-id:                     /dev/disk/by-id/usb-MITSUMI_MITSUMI_USB_FDD
    by-path:                   /dev/disk/by-path/pci-0000:00:1d.2-usb-0:1:1.0-scsi-0:0:0:0
  detected at:                 Thu 23 Sep 2010 05:06:28 AM CDT
  system internal:             0
  removable:                   1
  has media:                   0
    detects change:            1
    detection by polling:      1
    detection inhibitable:     1
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        0
  block size:                  0
  job underway:                no
  usage:                       filesystem
  type:                        vfat
  version:                     FAT12
  uuid:                        
  label:                       
  drive:
    vendor:                    MITSUMI
    model:                     MITSUMI USB FDD
    revision:                  0100
    serial:                    
    WWN:                       
    detachable:                1
    can spindown:              0
    rotational media:          Yes, unknown rate
    write-cache:               unknown
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                  floppy
    interface:                 usb
    if speed:                  12000000 bits/s
    ATA SMART:                 not available

========================================================================

```

With the USB Floppy plugged in to my computer I can do:
```

udisks --mount /dev/sdc

```
and I can access the floppy via the PLACES -> COMPUTER as it is mounted in
/media/disk.......It's ICON does show as a HARD DRIVE instead of a FLOPPY DISK ICON.

I can un-mount it with:
```

udisks --unmount /dev/sdc

```

So, I basically tried to undo any mount command I had previously executed with udisks,
but I still get the error message on power up or reboot.

I just don't understand what is trying to Mount as "STATIC", or what caused it, or how
to fix the problem. Would/should this be reported as a "BUG"?  I certainly don't think
it was anything I did to cause it.
 

lk

---

### Post by jtarin on 2010-09-23
unmount and remove the floppy and then run sudo fdisk -l again and post the output.

---

### Post by lkraemer on 2010-09-23
jtarin,
Here it is:
```

larry@larry-laptop:/$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ba58e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+  83  Linux
/dev/sda2            2551       59717   459193927+  83  Linux
/dev/sda4           59718       60801     8707230   82  Linux swap / Solaris
larry@larry-laptop:/$ 

```

Looks fine to me!  I only have one Physical Hard Drive, Partitioned
just as it shows here with fdisk.

lk

---

### Post by jtarin on 2010-09-23
Yea! I agree looks fine without the USB attached. Something is throwing your partition table out of whack with it attached. I've never seen anything like that to affect a readout like that.

---

### Post by QLee on 2010-09-24
I wonder if this is a case for a udev rule, similar to the way a rule "changes" one of those "USB CD" broadband WiFi modems when it is plugged? Something that "creates" a proper device for the floppy from the ID rather than that false sdc. Just don't ask me to write it. I've only mucked about with those broadband modem rules and it was previous to the addition of the modern rule set.

---

### Post by lkraemer on 2010-09-24
QLee,
At this point I'm lost, but I'll accept any suggestions.  I think someone out there has a clue, I just wish they would stumble across this posting.

I'm about at my technical limit, and out of ideas.

lk

---

### Post by jtarin on 2010-09-24
> **QLee said:**
> I wonder if this is a case for a udev rule, similar to the way a rule "changes" one of those "USB CD" broadband WiFi modems when it is plugged? Something that "creates" a proper device for the floppy from the ID rather than that false sdc. Just don't ask me to write it. I've only mucked about with those broadband modem rules and it was previous to the addition of the modern rule set.
I have had that same feeling on this myself several times....so I will point you to [this]("http://ubuntu-tutorials.com/2006/12/06/how-to-always-mount-removable-drives-in-the-same-place-ubuntu-6061-610/") to see if it might help in your case. It's the best scenario I've come across.

---

### Post by lkraemer on 2010-09-26
jtarin,
I was ready to try your information on creating a rule, but there is
no man page in Terminal for udevinfo for 10.04 and the command won't
execute for me to find the information needed for step #2.

I found a posting that said to use udevadm instead.
```

udevadm info -q all -n /dev/sdc

```
```

larry@larry-laptop:~$ udevadm info -q all -n /dev/sdc
P: /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/host8/target8:0:0/8:0:0:0/block/sdc
N: sdc
W: 59
S: block/8:32
S: disk/by-id/usb-MITSUMI_MITSUMI_USB_FDD
S: disk/by-path/pci-0000:00:1d.2-usb-0:1:1.0-scsi-0:0:0:0
S: disk/by-uuid/4071-0EF0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/host8/target8:0:0/8:0:0:0/block/sdc
E: MAJOR=8
E: MINOR=32
E: DEVNAME=/dev/sdc
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: ID_VENDOR=MITSUMI
E: ID_VENDOR_ENC=MITSUMI\x20
E: ID_VENDOR_ID=03ee
E: ID_MODEL=MITSUMI_USB_FDD
E: ID_MODEL_ENC=MITSUMI\x20USB\x20FDD\x20
E: ID_MODEL_ID=6901
E: ID_REVISION=0100
E: ID_SERIAL=MITSUMI_MITSUMI_USB_FDD
E: ID_TYPE=floppy
E: ID_BUS=usb
E: ID_USB_INTERFACES=:080400:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=usb-storage
E: ID_PATH=pci-0000:00:1d.2-usb-0:1:1.0-scsi-0:0:0:0
E: ID_FS_SEC_TYPE=msdos
E: ID_FS_UUID=4071-0EF0
E: ID_FS_UUID_ENC=4071-0EF0
E: ID_FS_VERSION=FAT12
E: ID_FS_TYPE=vfat
E: ID_FS_USAGE=filesystem
E: UDISKS_PRESENTATION_NOPOLICY=0
E: ID_DRIVE_FLOPPY=1
E: DEVLINKS=/dev/block/8:32 /dev/disk/by-id/usb-MITSUMI_MITSUMI_USB_FDD /dev/disk/by-path/pci-0000:00:1d.2-usb-0:1:1.0-scsi-0:0:0:0 /dev/disk/by-uuid/4071-0EF0

larry@larry-laptop:~$

```


I tried to convert the command to the current.

udevadm info -q all -n $(udevadm info -q all -n /dev/sdc) | grep SYSFS{serial}
device node not found

But, I must have something incorrect.

Can you offer a suggestion?

I found this posting, but likewise it isn't current for udevadm.
[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

lk

---

### Post by lkraemer on 2010-10-01
[http://ubuntuforums.org/showthread.php?t=168221&page=6](http://ubuntuforums.org/showthread.php?t=168221&page=6)
Posting #57

Just following along with Ubuntu 9.04 when I noticed udevinfo was missing, or rather, renamed. I didn't check all the other posts to see if there was a solution, but this worked for me (as root):

```

ln -s /sbin/udevadm /usr/bin/udevinfo

```
To make a link from the new/renamed program to where it used to be, or just call the new program/version directly:

```

udevadm info -a -p $(udevadm info -q path -n /dev/XXX)

```
I also had to do this, instead of 'udevstart', as mentioned in the guide:

I hope that saves someone some time.

lk

---

