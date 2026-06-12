---
title: "automatically mount network drive"
date: 2015-08-09
forum: Networking &amp; Wireless
---

### Post by alain.roger on 2015-08-09
Hi,

i'm having issue trying to auto mount network drive under KUbuntu.
Network drive are from my NAS.

i'm using CIFS for that and i updated /etc/fstab as following:
```
//n4200eco/Storage /media/storage cifs iocharset=utf8,credentials=/home/alain/.smbcredentials, uid=1000 0 0
```

where /home/alain/.smbcredentials holds my username and password (with only chmod 600 permissions to avoid hacking)

when running: "sudo mount -a" i get:
 [FONT=monospace][COLOR=#000000]```
mount: /etc/fstab: parse error: ignore entry at line 14. 
```[/COLOR]```

mount error(13): Permission denied 
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

- if i ping n4200eco everything is ok
- /media/storage is empty folder
- /home/alain.smbcredentials file exists and holds data

i also tried /etc/fstab like that one:
```
//n4200eco/Storage /media/storage cifs auto,iocharset=utf8,credentials=/home/alain/.smbcredentials,uid=1000,gid=users,file_mode=0775,dir_mode=0775 0 0
```

but i always get:
[/FONT]```
 [FONT=monospace][COLOR=#000000]mount error(13): Permission denied [/COLOR]
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
[/FONT]
```


i checked the documentation of mount.cifs but i saw nothing special there.
Any idea where is my mistake?[FONT=monospace]

thx




[/FONT]

---

### Post by alain.roger on 2015-08-09
Ok, i found the problem... in fact for some unknown reason the network shared drive was keeping in memory former password. I upgraded it and not it works correctly.

---

