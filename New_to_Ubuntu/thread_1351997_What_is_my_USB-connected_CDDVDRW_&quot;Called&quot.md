---
title: "What is my USB-connected CD/DVDRW &quot;Called&quot;"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by ekswhyzee on 2009-12-11
Hi folks and thanks in advance for any help you may be able to give this noob who has decades of IT experience but with all the wrong OS's!

I'd like to use ddrescue to recover a CD.

The command I'm advised to use is something along the lines of:

```
$ sudo ddrescue -v **/dev/hdc** cdr-backup2.iso ddrescue.log
```

I would like a command-line noob way of finding of the "equivalent" to

**```
/dev/hdc
```**

for my USB-connected CD/DVDRW drive so I can use it as a parameter to **ddrescue**.

I can play the audio CD (with, say VLC), if I click on the "Audio Disc" entry (since there is a mounted audio CD in the drive) in Gnome's file browser, I get...

```
**[SIZE="5"]Could not display "cdda://sr1."[/SIZE]**

Error: DBus error org.freedesktop.DBus.Error.ServiceUnknown: The name :1.104 was not provided by any .service files
Please select another viewer and try again

```

If I right-click on the gnome desktop icon of the "Audio Disc", the Permissions tab states:

```
The permissions of "cdda" could not be determined.
```


If I unmount the audio disk then I seem to have no graphical way of accessing this drive.

I've looked at

```
mount
```

and

```
fdisk -l
```

In frustration I tried gparted but now I realise this was a bonkers thing to do.

I'm not SCARED of Terminal and the command line but simply don't know how to get the info I need.

It looks like it's "cdda" but what is the full path I need so I can use it in ddrescue?

Thanks folks.

XYZ

---

### Post by ukripper on 2009-12-11
post output of the following:
```
ls -al /dev/cd*
```

and ```
sudo mount
```

---

### Post by ekswhyzee on 2009-12-11
Thanks for the ultra-quick response!

> **ukripper said:**
> post output of the following:
```
ls -al /dev/cd*
```
```
lrwxrwxrwx 1 root root 3 2009-12-11 05:15 /dev/cdrom -> sr0
lrwxrwxrwx 1 root root 3 2009-12-11 05:15 /dev/cdrom2 -> sr1
lrwxrwxrwx 1 root root 3 2009-12-11 05:15 /dev/cdrw -> sr0
lrwxrwxrwx 1 root root 3 2009-12-11 05:15 /dev/cdrw2 -> sr1
```

and ```
sudo mount
```
```
/dev/mapper/main-root on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-17-generic/volatile type tmpfs (rw,mode=755)
/dev/sda3 on /boot type ext3 (rw,relatime)
/dev/mapper/main-home on /home type ext3 (rw)
/dev/mapper/main-usr on /usr type ext3 (rw)
/dev/mapper/main-var on /var type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/xyz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=xyz)
/dev/mmcblk0p1 on /media/Kingston type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdd1 on /media/PEA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/New Volume type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
```

XYZ

---

### Post by ukripper on 2009-12-11
put a cd you want to rescue in your cdrom and then run this:
```
sudo ddrescue -v /dev/cdrom2 cdbackup.iso ddrescue.log
```

I assume you have two cd drives connected. And cdrom2 is your second one usb based

---

### Post by ekswhyzee on 2009-12-11
OK Thanks I think I worked it out... linking the "sr1" in my earlier error message and the "sr1" to the output from

```
ls -al /dev/cd*
```

I'm "guessing" that for READING in my case it's

```
/dev/cdrom2
```

so

```
sudo ddrescue -v **/dev/cdrom2** cdr-backup2.iso ddrescue.log
```

If I'm wrong, please tell me.

XYZ

---

### Post by ukripper on 2009-12-11
> **ekswhyzee said:**
> OK Thanks I think I worked it out... linking the "sr1" in my earlier error message and the "sr1" to the output from

```
ls -al /dev/cd*
```

I'm "guessing" that for READING in my case it's

```
/dev/cdrom2
```

so

```
sudo ddrescue -v **/dev/cdrom2** cdr-backup2.iso ddrescue.log
```

If I'm wrong, please tell me.

XYZ

You are right as i explained in my previous post.

---

### Post by ekswhyzee on 2009-12-11
> **ukripper said:**
> You are right as i explained in my previous post.

The wonders of synchronicity. We overlapped. The forum should  develop a locking protocol :)

Thank you for your help but I'm not sure I know how I myself came to any conclusion other than there being a fortuitous error message in Gnome.

XYZ

---

### Post by 3rdalbum on 2009-12-11
You can find it out by using the hal-device command:

```
hal-device | less
```

Somewhere in that list you will see stuff relating to your optical drive (there's a big list of keys regarding whether your drive handles DVDs, CD-RWs, Blu-ray etc), and toward the end of that section is "block.device" which tells you what the device file name of that device is.

This is how my Blu-ray drive looks:

```
6: udi = '/org/freedesktop/Hal/devices/storage_model_BDDVDRW_GGC_H20L'
  storage.model = 'BDDVDRW GGC-H20L'  (string)
  storage.vendor = 'HL-DT-ST'  (string)
  info.capabilities = { 'storage', 'block', 'storage.cdrom' } (string list)
  storage.firmware_version = '1.03'  (string)
  storage.lun = 0  (0x0)  (int)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.removable.media_available = false  (bool)
  storage.removable = true  (bool)
  storage.size = 0  (0x0)  (uint64)
  storage.hotpluggable = false  (bool)
  storage.requires_eject = true  (bool)
  storage.removable.support_async_notification = false  (bool)
  info.vendor = 'HL-DT-ST'  (string)
  info.addons = { 'hald-addon-storage' } (string list)
  storage.partitioning_scheme = ''  (string)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_BDDVDRW_GGC_H20L'  (string)
  info.category = 'storage'  (string)
  storage.cdrom.cdr = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.dvdr = true  (bool)
  storage.cdrom.dvdrw = true  (bool)
  storage.cdrom.dvdrdl = true  (bool)
  storage.cdrom.dvdram = true  (bool)
  storage.cdrom.dvdplusr = true  (bool)
  storage.cdrom.dvdplusrw = true  (bool)
  storage.cdrom.dvdplusrwdl = false  (bool)
  storage.cdrom.dvdplusrdl = true  (bool)
  storage.cdrom.bd = true  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.hddvd = true  (bool)
  info.product = 'BDDVDRW GGC-H20L'  (string)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.mo = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.mrw_w = true  (bool)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.support_multisession = true  (bool)
  storage.cdrom.read_speed = 7056  (0x1b90)  (int)
  storage.cdrom.write_speed = 7056  (0x1b90)  (int)
  storage.cdrom.mrw = true  (bool)
  org.freedesktop.Hal.Device.Storage.method_signatures = { 'as', 'as' } (string list)
  org.freedesktop.Hal.Device.Storage.method_argnames = { 'extra_options', 'extra_options' } (string list)
  org.freedesktop.Hal.Device.Storage.method_execpaths = { 'hal-storage-eject', 'hal-storage-closetray' } (string list)
  storage.cdrom.write_speeds = { '7056', '5645', '4234', '2822', '1411', '706' } (string list)
  org.freedesktop.Hal.Device.Storage.method_names = { 'Eject', 'CloseTray' } (string list)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_BDDVDRW_GGC_H20L'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sr0'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2922_scsi_host_1_scsi_device_lun0'  (string)
  info.interfaces = { 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage.Removable' } (string list)
  block.device = '/dev/sr0'  (string)
  block.major = 11  (0xb)  (int)
  block.minor = 0  (0x0)  (int)
  block.is_volume = false  (bool)
  storage.bus = 'pci'  (string)
  storage.no_partitions_hint = true  (bool)
  storage.media_check_enabled = true  (bool)
  storage.automount_enabled_hint = true  (bool)
  linux.hotplug_type = 3  (0x3)  (int)
  storage.drive_type = 'cdrom'  (string)

```

I tried to find a way to pull out just the device file names for each of your drives, but I couldn't seem to find it. I'm pretty sure it can be done, but for you it's probably just as easy to manually look at the list yourself.

---

### Post by ukripper on 2009-12-11
> **ekswhyzee said:**
> The wonders of synchronicity. We overlapped. The forum should  develop a locking protocol :)


It would defy the whole concept of what google is trying to do with the Wave, when it comes to the collaboration. And retrospectively, in my opinion there can't be a better solution towards the coming of age.:)

you can also find your usb cd drive from > dmesg | tail after connecting it.

---

### Post by ekswhyzee on 2009-12-11
> **3rdalbum said:**
> You can find it out by using the hal-device command:

```
hal-device | less
```

Somewhere in that list you will see stuff relating to your optical drive (there's a big list of keys regarding whether your drive handles DVDs, CD-RWs, Blu-ray etc), and toward the end of that section is "block.device" which tells you what the device file name of that device is....for you it's probably just as easy to manually look at the list yourself.

Thanks for your reply but I lost the will to live!

XYZ

---

### Post by ekswhyzee on 2009-12-11
> **ukripper said:**
> It would defy the whole concept of what google is trying to do with the Wave, when it comes to the collaboration. And retrospectively, in my opinion there can't be a better solution towards the coming of age.:)

you can also find your usb cd drive from  after connecting it.

And the result is:
```

[26068.637050] usb 1-2: new high speed USB device using ehci_hcd and address 11
[26068.770898] usb 1-2: configuration #1 chosen from 1 choice
[26068.771402] scsi12 : SCSI emulation for USB Mass Storage devices
[26068.771747] usb-storage: device found at 11
[26068.771752] usb-storage: waiting for device to settle before scanning
[26073.768418] usb-storage: device scan complete
[26073.769941] scsi 12:0:0:0: CD-ROM            LITE-ON  DVDRW SOHW-1653S CS0T PQ: 0 ANSI: 0
[26073.785865] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[26073.786258] sr 12:0:0:0: Attached scsi CD-ROM sr1
[26073.786436] sr 12:0:0:0: Attached scsi generic sg2 type 5
```

And whilst it does give me some info (sr1), I can't see **/dev/cdrom2** anywhere which is the answer to my original question!.

Thanks for all of your help and hints and maybe one day we'll be "Google Wave"ing. Well actually after they've taken over the world, we'll HAVE to.

XYZ

---

### Post by ukripper on 2009-12-11
> **ekswhyzee said:**
> 
[26073.785865]** sr1**: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[/CODE]

And whilst it does give me some info (sr1), I can't see [B]/dev

It gives you **sr1** and ls -al /dev/cd* gave you the symbolic link to the /dev/cdrom2. I hope that confirms for you it is /dev/cdrom2

---

### Post by ekswhyzee on 2009-12-11
> **ukripper said:**
> It gives you **sr1** and ls -al /dev/cd* gave you the symbolic link to the /dev/cdrom2. I hope that confirms for you it is /dev/cdrom2

Yup but I didn't find the Golden Hare in the 70s either.

One day there will be a single-step way of doing simple things in Linux but we all need to get our exercise somehow even if it's keystrokes!

:)

XYZ

---

### Post by ukripper on 2009-12-11
> **ekswhyzee said:**
> Yup but I didn't find the Golden Hare in the 70s either.

One day there will be a single-step way of doing simple things in Linux but we all need to get our exercise somehow even if it's keystrokes!

:)

XYZ

There are always several ways to kill a cat in linux. 

I work on logical basis to resolve problems. Hence, the result.

---

### Post by ekswhyzee on 2009-12-11
> **ukripper said:**
> There are always several ways to kill a cat in linux. 

I work on logical basis to resolve problems. Hence, the result.

There are also several ways to execute a person, but the lethal injection method in the USA has just been redesigned due to **USER FEEDBACK!!**

:)

XYZ

---

