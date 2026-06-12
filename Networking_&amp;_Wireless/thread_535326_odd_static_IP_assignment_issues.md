---
title: "odd static IP assignment issues"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by reckless2k2 on 2007-08-26
on my one kubuntu box when i switch the interface from dhcp to static, i reboot and the desktop takes forever to load and my fstab smbfs mounts don't seem to work. i don't have this issue with my other ubuntu machines so it's probably something simple that i'm over looking.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=4d9f3c29-ed6c-4254-8d49-fb4d0b47793e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=e7290eb5-f4cb-4ae9-b631-5a1dc1e2ddce /home           ext3    defaults        0       2
# /dev/hda1
UUID=4AF08078F0806BCF /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=dbd36a69-a1e8-4195-a408-5a3961e08690 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

//ipofserver/share /mount/point	smbfs	credentials=/root/.smbpasswd,gid=grpname,dmask=775,fmask=775	0	0

//ipofserver/share2 /mount/point2	smbfs	credentials=/root/.smbpasswd,gid=grpname,dmask=770,fmask=770	0	0

//ipofserver/share3 /mount/point3	smbfs	credentials=/root/.smbpasswd,gid=grpname,dmask=770,fmask=770	0	0


```

---

### Post by reckless2k2 on 2007-08-26
this was corrected using cifs with dir_mode and file_mode:

example:

```
//ipofserver/share2 /mount/point   cifs	credentials=/root/.smbpasswd,gid=grpname,dir_mode=0770,file_mode=0770	0	0
```

---

