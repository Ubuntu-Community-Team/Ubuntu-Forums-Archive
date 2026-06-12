---
title: "Cannot mount samba"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by lemonsCC on 2006-12-02
I am trying to mount a samba partition and keep getting errors as follows.
```

$ sudo mount -t  smbfs -o username=chris //192.168.1.150/ /mnt/shared/
mount: wrong fs type, bad option, bad superblock on //192.168.1.150/,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$ dmesg | tail
[   99.303760] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   99.303799] md: bitmap version 4.39
[  103.731838] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[  104.993479] NET: Registered protocol family 10
[  104.994585] lo: Disabled Privacy Extensions
[  104.996179] IPv6 over IPv4 tunneling driver
[  106.659069] cdrom: open failed.
[  115.663812] eth0: no IPv6 routers present
[  133.716239] Program wdm tried to read /dev/mem between 100000->102000.
[18545.527065] smbfs: mount_data version 1919251317 is not supported
campbell@campbell-old:~$ dmesg | tail
[   99.303760] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   99.303799] md: bitmap version 4.39
[  103.731838] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[  104.993479] NET: Registered protocol family 10
[  104.994585] lo: Disabled Privacy Extensions
[  104.996179] IPv6 over IPv4 tunneling driver
[  106.659069] cdrom: open failed.
[  115.663812] eth0: no IPv6 routers present
[  133.716239] Program wdm tried to read /dev/mem between 100000->102000.
[18545.527065] smbfs: mount_data version 1919251317 is not supported

```

---

### Post by sgusev on 2006-12-02
I had a similar issue where trying to mount the root Samba share did not work, but mounting the subdirectory (//host/dir) worked fine. I still don't know how to mount the root folder, but at least this way I was able to access my files.

---

