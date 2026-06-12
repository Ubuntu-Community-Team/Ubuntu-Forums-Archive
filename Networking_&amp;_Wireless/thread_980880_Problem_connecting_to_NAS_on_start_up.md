---
title: "Problem connecting to NAS on start up"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by Satal Keto on 2008-11-13
I was hoping that someone could give me some help.

I have a Network HDD (or NAS) and I am having difficulties getting Ubuntu to automatically connect to it.
After alot of Googling and searching on this forum, I have found that I can get it to connect, the method I am currently having to use is that I have a script on my desktop which I run from the terminal as root which is this
```
modprobe cifs
echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled
mount -a
```

Although I run this code as root I still need to enter my password again for the "mount -a".

I was wondering whether anyone knows of anyway I can the NAS to be connected straight away without having to run this script (and entering my password again)

I dont know whether this will help but here is my /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=b3afaea3-c81b-420c-a66d-0e22f458bb3c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=aeb7c7ce-fbc3-4e69-aab9-92a7279fbf3a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//192.168.0.4/PUBLIC /media/EHDD/ smbfs uid=satal,gid=satal 0 0
```

Thanks for any help in advance :D

---

