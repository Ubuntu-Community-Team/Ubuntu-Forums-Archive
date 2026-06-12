---
title: "CIFS permissions for Windows Share - fstab"
date: 2013-12-01
forum: Networking &amp; Wireless
---

### Post by robhux on 2013-12-01
[COLOR=#000000][FONT=Arial]I am running a Ubuntu 12.04 virtual box and trying to mount some Windows shares in fstab.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The shares mount fine, however I only have read permissions. For write permissions I must use sudo. I have tried various settings in fstab, but to no avail. However if I go through GUI, and add a server in the file browser, I have all permissions (rwx) as my normal user - media.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Fstab is[/FONT][/COLOR]
```
//10.0.1.10/f$  /media/tv  cifs username=administrator,password=******,domain=WORKGROUP,rw,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0  0
```
[COLOR=#000000][FONT=Arial]I am aware about using a credentials file however at this stage I just want to get it working correctly. I have tried specifying uid and gid as media also. Any help appreciated.[/FONT][/COLOR]

---

