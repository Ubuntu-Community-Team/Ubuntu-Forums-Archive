---
title: "Smb share unmounts after some time"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by pivot@pivpoint.no on 2008-07-12
Hey

I have all my files hosted at a ubuntu server. Im running a ubuntu htpc (7.10) that mounts the smb shares through fstab. Problem is that it unmounts after some time. Why is that? It didnt do that before...

Heres my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/sda1
UUID=83c7cfb9-804e-4e3e-8388-9608c98223b7  /               ext3         defaults,errors=remount-ro  0  1  
# /dev/sda5
UUID=5e0476e2-c807-45bf-8deb-08dbf4bff763  none            swap         sw                          0  0  
/dev/hda                                   /media/cdrom0   udf,iso9660  user,noauto,exec            0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec         0  0  
/dev/sdb1                                  /media/sdb1     ntfs         nls=iso8859-1,umask=000     0  0  
/dev/sdg1                                  /media/sdg1     ntfs         nls=iso8859-1,umask=000     0  0  
/dev/sdc1                                  /media/sdc1     ntfs         nls=iso8859-1,umask=000     0  0  
//pivot/pivot   /media/pivotshare   smbfs   credentials=/etc/samba/user,rw,uid=pivot   0   0
//pivot/download   /media/pivotdownload   smbfs   credentials=/etc/samba/user,rw,uid=$
//pivot/music   /media/pivotmusic   smbfs   credentials=/etc/samba/user,rw,uid=$
//pivot/pictures   /media/pivotpictures   smbfs   credentials=/etc/samba/user,rw,uid=$
```

---

