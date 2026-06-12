---
title: "Sharing Files Via CAT5?(Help)"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by bouta on 2008-05-15
Hello there, i have been googling for hours, i need to a simplified tutorial to share files only between ubuntu hardy 8.04 and vista using a Crossover cable.
Back then when i shared between xp and vista,  i used to assign each computer an IP address, and then share the folder by right clicking on the desired folder, then open start > run > IP address.hence opening shared folder.
I need something similar, do i need to assing IP for ubuntu and how ? i already installed samba and smbf.

Thanks

---

### Post by superprash2003 on 2008-05-15
yes you would need to assign ips on both windows and ubuntu.. you could set windows to an ip like 10.0.0.1 and ubuntu to 10.0.0.2 .. this is just an example.. then ensure they can ping each other.. follow this samba guide.. [http://ubuntuguide.org](http://ubuntuguide.org) and to access windows files from ubuntu type smb://10.0.0.1 under location in places->computer

---

### Post by bouta on 2008-05-15
> **superprash2003 said:**
> yes you would need to assign ips on both windows and ubuntu.. you could set windows to an ip like 10.0.0.1 and ubuntu to 10.0.0.2 .. this is just an example.. then ensure they can ping each other.. follow this samba guide.. [http://ubuntuguide.org](http://ubuntuguide.org) and to access windows files from ubuntu type smb://10.0.0.1 under location in places->computer

ok i guess its under admin>network> wired connection> static ip right ? thanks

---

### Post by superprash2003 on 2008-05-19
yes

---

