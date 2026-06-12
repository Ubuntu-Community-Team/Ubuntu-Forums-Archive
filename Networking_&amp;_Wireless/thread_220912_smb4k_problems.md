---
title: "smb4k problems"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by idorux on 2006-07-22
Hi, I am using ubuntu 6.06 and I have tried virtually all of the possibilities listed in many of the forum posts with no or partial success in mounting windows xp shares. In the past I have always used SMB4K with debian distributions without any issues but I can not get SMB4K to work properly under ubuntu. When I initially install SMB4K I can mount the drives without problems. After that on subsequent boots I can no longer mount the drives. When I try to (using sudo and root settings in SMB4K) the mount icon appears for a split second then disappears. The drives are not mounted. I have tried removing references to my server and shared windows drives but to no avail. Is there a way to mount the windows shares through Nautilus ? Any help would be appreciated.

---

### Post by jshein on 2006-07-22
In order for smb4k to work properly as a user, smbmnt and smbumount need to be suid root

#sudo chmod +s /usr/bin/smbmnt
#sudo chmod +s /usr/bin/smbumount

---

### Post by idorux on 2006-07-24
Thank you that seems to work once I removed the checks under 
settings - actions - superuser in SMB4K. Thanks very much.

---

