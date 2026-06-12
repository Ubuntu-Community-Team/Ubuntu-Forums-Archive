---
title: "laptop cannot mount usb drive connected to ubuntu box"
date: 2005-06-15
forum: Networking &amp; Wireless
---

### Post by wiljen on 2005-06-15
Hello all...

I installed ubuntu (hoary) on my desktop computer and am using my laptop (toshiba satellite 1555 running simplymepis 3.3 ) with samba to share files on each box. I can mount the partitions on my internal drive on the ubuntu box just fine, but i cannot mount the external drive (a usb drive that is connected to the ubuntu box) from my laptop. 

for some reason, the usb drive shows up on my desktop on the ubuntu box...but is not listed in the fstab... and shows up in the places>comptuer window not as folders, but with drive icons..with names like 63G Media.

how do i need to enter this into smb.conf so that i can mount it from my laptop?

Thanks in advance :)

---

### Post by zoofields on 2005-06-16
I'm having a similar problem.  Anyone out there have an answer?

---

### Post by wiljen on 2005-06-16
Well, not many humans seem interested in this topic...

I believe that the problem may be found in the /etc/mtab:  

/dev/hda6 / ext3 rw,user_xattr,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev/hda2 /mnt/Mepis ext3 rw 0 0
/dev/hda1 /mnt/Windblows ntfs rw,umask=0222 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
usbfs /proc/bus/usb usbfs rw 0 0
none /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sda1 /media/usbdisk vfat rw,nosuid,nodev,quiet,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
/dev/sda2 /media/usbdisk-1 ext3 rw,nosuid,nodev 0 0
/dev/sda4 /media/usbdisk-2 ext3 rw,nosuid,nodev 0 0


However, I do not know how to rewrite the approriate lines so that the local ubuntu box and the laptop can both have access to the external drive.

Thanks for any help you can give :-P

---

### Post by Dali on 2005-07-17
I'm having the same issues.  

Anyone?

---

### Post by enfield on 2006-07-11
Same issue here!

---

### Post by slider on 2006-07-11
> **wiljen said:**
> Well, not many humans seem interested in this topic...

I believe that the problem may be found in the /etc/mtab:  


/etc/mtab is written out by the mount command. Modifying it won't change anything. I've had success adding usb and firewire drives to /etc/fstab so that they are mounted at launch. My firewire drive shows up as a scsi device and so gets entered as /dev/sdc1. Here's the fstab entry.

```
/dev/sdc1     /media/FEST     vfat    defaults       0 0 
```

Only problem with doing this is that, if the drive is disconnected and reconnected, it shows up as a different device and is automatically remounted at a different mount point. I haven't figured out a way around this yet.

EDIT: 

More searching found this thread on consistent device naming with udev. Haven't tried it yet.
[http://ubuntuforums.org/showthread.php?t=168221]("http://ubuntuforums.org/showthread.php?t=168221")

---

### Post by slider on 2006-07-11
Figured some stuff out and figured I'd post it here.

pmount is what automounts your usb and firewire drives when they are hotplugged. By default it mounts them into /media/<partition name> as long as the drive isn't already mapped in /etc/fstab and there isn't a file or directory of that name in /media (there's a few other restrictions - see man pmount.)

You can use the /media/<partition name> mount point in smb.conf without problems. It is probably preferable to creating a mount point and putting an entry in /etc/fstab. With a pmounted drive, when a client tries to mount an smbshare for a disconnected drive, it raises an error. If there is a hard mount point as required for entries in fstab the empty mount point is shared.

---

### Post by lparsons on 2006-07-17
I'm having a similar issue.  Right now I have the pmounted drive (/media/usbdisk) mounted in smb.conf.  

The problem I'm having is that without an entry in fstab (relying on pmount) the drive is not available if no one is logged on to the desktop.  This is an issue.  If I add the drive to fstab, however, then it is not properly remounted after being removed and reconnected.

Does anyone know of a way to have an external USB drive mounted at system startup (before user login) and have it automatically unmount/remount when disconnected/connected?  Thanks.

---

