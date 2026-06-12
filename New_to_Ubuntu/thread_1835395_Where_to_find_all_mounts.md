---
title: "Where to find all mounts?"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by 4thfloorstudios on 2011-08-29
Hi,
I have a dual boot machine with Ubuntu and Windows and normally I can access the Windows partition with Nautilis, but today it does not work.

When I open GParted it shows me the partition but says it is not mounted, so I wnated to look it up in /etc/fstab but there is no entry for that.

Where do I find all mounts of the system? It seems that in the fstab file there are not all mounts because this is the fstab file:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=663a0f75-9d5b-405f-ab9f-c9c1c194b1a5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1de224c6-2508-46b3-a94b-72f6f1f46121 none            swap    sw              0       0

```And this is the output of mount:

```

/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/oliver/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=oliver)
```This is a little bit confusing. Could anyone tell me where to find all mounts?

Thank you!

Oliver

---

### Post by saltmarshlamb on 2011-08-29
Fstab will only have the system partitions moutpoints created at install, anything else you need to add yourself. 

The drives you open from nautilus get mounted as needed and into /media. 

Open a terminal, try and select the drive in nautilus as normal and then run this from the terminal - ee if it gives you any idea of what's going on. 

```
cat /var/log/syslog |tail
```

By any chance when you looked at gparted - did you notice any flags like ! against the windows partition?

---

### Post by Rhizoid on 2011-08-29
Can you post the output of:

```
sudo fdisk -l
```Should be able to tell you how and where to mount the filesystem then and how to modify /etc/fstab so it's reboot persistent.

Cheers,

---

### Post by HarrisonNapper on 2011-08-29
Usually buntu mounts to /media, but looks like the drives aren't mounted, so they would have a corresponding /dev entry for the physical drive. Previous posts should get you taken care of, but wanted the FYI for the /media mount folder in here :)

---

### Post by oldos2er on 2011-08-29
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by nothingspecial on 2011-08-29
Do something like this
```

sudo mkdir /media/windows
```

then put a line like this in /etc/fstab
```

UUID=[COLOR="Red"]blah-random-numbers-letters[/COLOR]    /media/windows     ntfs-3g       auto,users,uid=1000,gid=100,dmask=027,fmask=137,locale=[COLOR="Red"]en_GB.utf8[/COLOR]  0   0
```

The real uuid can be found with ```
sudo blkid
```

Your available locales can be found with ```
locale -a
```

---

