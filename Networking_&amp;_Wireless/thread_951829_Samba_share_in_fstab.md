---
title: "Samba share in fstab"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by tendrousbeastie on 2008-10-18
Hello,


I'm an occasional dabbler in linux and I have just stuck Ubuntu (8.04) on my desktop PC.

I'm having a little difficulty in automounting a couple of shares from a WinK2003 server through my fstab file. 

As an new (or at least vastly inexperienced) linux user, I'm not sure where to look to find the error message for the fstab system - I presume there's a terminal command I can run to show some error logs.


I'll post a copy of my fstab below (passwords blanked). When I run the same paramters through a sudo mount command the mount works fine. It just doesn't seem to do anything in the fstab file.




```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=df32d390-5e78-4f7f-916f-9055335b93cd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=5aa6cc88-cff5-415e-ab03-ddb23d87d7e6 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
//pilate/www            /shares/pilate/www      smbfs   username=judas,password=XXXXXXX 0 0
//pilate/servers        /shares/pilate/servers  smbfs   username=judas,password=XXXXXXX 0 0
```




Thanks for any help....

---

