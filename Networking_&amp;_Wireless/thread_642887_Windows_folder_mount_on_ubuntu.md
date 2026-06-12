---
title: "Windows folder mount on ubuntu"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by darkrad on 2007-12-17
in fstab i wrote: 

```
//192.168.0.2/Temp /home/xxx/Desktop/Shared/Temp smbfs username=xxx,password=yyy 0 0
```

and on boot /home/xxx/Desktop/Shared/Temp is empty.
If i write 

```
sudo mount -t smbfs -o username=xxx //192.168.0.2/Temp /home/xxx/Desktop/Shared/Temp
```

 it works, i can access the windows shared dir from  /home/xxx/Desktop/Shared/Temp dir.
What's wrong with fstab file? Thanks

---

### Post by darkrad on 2007-12-17
nobody know? :(

i post the entire fstab, maybe there is something wrong elsewhere:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=e1f6712f-57a5-41e4-aed9-3a43f4d23d55 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=4bb40acb-bcb1-4b3f-b8fe-1bbb996d93c2 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//192.168.0.2/Temp      /home/xxx/Desktop/Shared/Temp  smbfs   username=zzz,password=yyy 0       0
//192.168.0.2/Temp1 /home/xxx/Desktop/Shared/Temp1 smbfs   username=zzz,password=yyy 0       0
//192.168.0.2/Temp2 /home/xxxDesktop/Shared/Temp2 smbfs   username=zzz,password=yyy 0       0
```

any idea??

---

### Post by darkrad on 2007-12-18
i just replaced "smbfs" with "cifs" and now it works good.

---

