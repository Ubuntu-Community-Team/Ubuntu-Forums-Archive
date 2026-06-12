---
title: "Stop Partition from Mounting on Boot"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by docfreed on 2011-04-17
[SIZE=3]I dual boot Vista and Ubuntu 10.04.2.  At some point I must have mounted two Windows partitions and now every time I boot Ubuntu, they show on the desktop.

I can remove them with the umount command but they persist whenever I reboot.  How can I permanently unmount them or stop them from mounting?[/SIZE]

---

### Post by TeoBigusGeekus on 2011-04-17
```
gksu gedit /etc/fstab
```
Comment out the undesired entries.

---

### Post by docfreed on 2011-04-17
[SIZE=2]Thanks but that did not work - they still persist on showing up - here's the file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda2    /host    ntfs    
# defaults,nls=utf8,umask=0222,nosuid,nodev    0    0
/dev/sda3    /media/HDDRECOVERY    ntfs    
# defaults,nls=utf8,umask=0222    0    0
/dev/sda1    /media/TOSHIBA_SYSTEM_VOLUME    ntfs    defaults,nls=utf8,umask=0222    0    0
/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0

I commented out sda1 and sda3 but they still appear on boot

Hmmm!  did I comment out the wrong lines??
[/SIZE]

---

### Post by TeoBigusGeekus on 2011-04-17
Put a # at the beginning of their lines.

---

### Post by Brian Vaughan on 2011-04-17
It looks like you split two lines in the middle, and commented out the second half. An fstab line has six columns, separated by tabs or spaces, as shown by the header comment. You split the lines for /dev/sda2 and /dev/sda3 between the <type> column and the <options> column.

After fixing that, I think what you want to do is change the mount options, which is the fourth column; the options are separated by commas. "defaults" may be redundant, as it specifies several default options. One of the defaults is "auto", which means that a partition is mounted when mount is executed with the "-a" option -- which happens when the system boots. That can be overridden by specifying the "noauto" option, after "defaults" if "defaults" is there.

Commenting out the entire line in fstab is unnecessary, and once in a while it's handy to be able to mount a Windows partition on the Linux filesystem.

You can find more details in the man pages: "man 5 fstab" and "man 8 mount".

---

### Post by Leppie on 2011-04-17
> **docfreed said:**
> [SIZE=2]Thanks but that did not work - they still persist on showing up - here's the file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda2    /host    ntfs    
# defaults,nls=utf8,umask=0222,nosuid,nodev    0    0
/dev/sda3    /media/HDDRECOVERY    ntfs    
# defaults,nls=utf8,umask=0222    0    0
/dev/sda1    /media/TOSHIBA_SYSTEM_VOLUME    ntfs    defaults,nls=utf8,umask=0222    0    0
/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0

I commented out sda1 and sda3 but they still appear on boot

Hmmm!  did I comment out the wrong lines??
[/SIZE]
the fstab should look something like this:
```
[SIZE=2]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda2    /host    ntfs      defaults,nls=utf8,umask=0222,nosuid,nodev    0    0
#/dev/sda3    /media/HDDRECOVERY    ntfs      defaults,nls=utf8,umask=0222    0    0
#/dev/sda1    /media/TOSHIBA_SYSTEM_VOLUME    ntfs    defaults,nls=utf8,umask=0222    0    0
/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0[/SIZE]
```

---

