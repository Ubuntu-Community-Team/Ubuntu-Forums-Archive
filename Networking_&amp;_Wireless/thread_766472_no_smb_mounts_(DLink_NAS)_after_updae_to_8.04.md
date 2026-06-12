---
title: "no smb mounts (DLink NAS) after updae to 8.04"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by Poldi on 2008-04-25
hi, all.

I always mount the shares on my dlink 323 NAS like this:

from /etc/fstab:

[...]
//DLINK-ED4246/Medien /media/Medien smbfs credentials=/home/carsten/.smbcredentials,iocharset=utf8,uid=1000,gid=1000 0 0
[...]

even on a fresh install of 8.04, Ubuntu does not like this any more. I get a 

mount error: could not find target server. TCP name DLINK-171039/Videos not found
No ip address specified and hostname not found

message. smbfs and samba are installed. carsten is owner of /media/Medien/.

suggestions?
kind regards,
Poldi

---

### Post by kaivalagi on 2008-04-25
I have a similar issue, I am looking through all the samba posts at the mo, and will post back if I find anything out.

I have the following lines in my fstab which worked in gutsy but not in hardy:


```
//landisk/public      /media/landisk-public     smbfs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//landisk/private     /media/landisk-private    smbfs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```

I get the following response when running "sudo mount -a":

```

Warning: mapping 'guest' to 'guest,sec=none'
mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

Anyone know why this doesn't work in hardy anymore?

---

### Post by kaivalagi on 2008-04-25
Found the fix for my samba woes, not sure whether it will work for yourself.

I modified my fstab entries to have a nounix option in them:

```
//landisk/public      /media/landisk-public     smbfs    guest,rw,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//landisk/private     /media/landisk-private    smbfs    credentials=/root/.smbcredentials,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

Hope that helps...

---

