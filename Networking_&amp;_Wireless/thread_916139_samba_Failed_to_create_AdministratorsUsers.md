---
title: "samba: Failed to create Administrators/Users"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by Akula on 2008-09-10
Hi,

I have ubuntu server with samba configured to share a folder. I can see it in my windows XP computer's network and read and write into it, just as I wanted. So everything is kind of ok.

The problem is these strange errors in samba.log file:

auth/auth_util.c:create_builtin_administrators(792) create_builtin_administrators: Failed to create Administrators

auth/auth_util.c:create_builtin_users(758) create_builtin_users: Failed to create Users

and lastest:

printing/print_cups.c:cups_connect(69) Unable to connect to CUPS server localhost:631 - Connection refused

this lastst error shows up not so rarely as first 2.

Here's my smb.conf:
```

[global]
netbios name = Ace
server string = Ace
workgroup = MSHOME
security = share
log file = /var/log/samba.log
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
wins support = yes

[Jako]
path = /home/akula/Jako/
writable = yes
browseable = yes
public = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = sambashare

```

I have added the user nobody to group sambashare, but not done anything other to users with samba. I also have chmoded shared folder to 777 as I want it to be shared and available to read/write in my LAN.

Can anyone help me?

---

### Post by Akula on 2008-09-11
Anyone? This is quite disturbing...

---

### Post by superprash2003 on 2008-09-11
are you sharing a printer with this pc?

---

### Post by Akula on 2008-09-11
No. There aren't any printers connected, and I thought this smb.conf of mine doesn't really configure any printers to be shared...

---

### Post by receptiveit on 2009-05-05
I recently had this issue and found that winbind was installed. Winbind is responsible for mapping RIDs to UID/GIDs. If you are not running your samba installation as a member server of an Active Directory domain, winbind is not needed, so uninstall it.

By default, samba will try and communicate with CUPS for printers. If you don't have CUPS installed, you will get that error message. It's harmless, but installing CUPS will make it go away.

---

