---
title: "More samba woes"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by Cellwind929 on 2008-05-09
I recently reformated my server PC. I installed a fresh new 8.04.

None of my machines can hit my samba share. I have no clue why, here is my config file:

```
[global]
# NetBIOS and name resolution options
   netbios name = cellserver
   workgroup = MSHOME
   wins support = yes
   dns proxy = no
   name resolve order = wins lmhosts bcast
# Network access options
   #hosts allow = 127. 192.168.1.
   #interfaces = eth0
# Logging options
   log file = /var/log/samba/samba.log
   max log size = 1000
# Master browser options
   local master = yes
   domain master = yes
   preferred master = yes
# Username and password security options
   guest account = smbguest
   username map = /etc/samba/smbusers
   encrypt passwords = true
   obey pam restrictions = yes
   smb passwd file = /etc/samba/smbpasswd
   passwd program = /usr/bin/passwd '%u'
   passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
   passwd chat timeout = 120
# Miscellaneous options
   preserve case = no
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   follow symlinks = no

[Storage]
	comment = Storage
	valid users = cellwind929,patron
	writeable = yes
	read list = patron
	path = /mnt/storage
	write list = cellwind929

```

Any help would be awesome!

---

### Post by superprash2003 on 2008-05-10
firstly check if those machines can first ping the server or not

---

### Post by Cellwind929 on 2008-05-10
Ping goes through just fine

---

### Post by superprash2003 on 2008-05-10
to ensure samba is running type sudo /etc/init.d/samba start

---

### Post by Cellwind929 on 2008-05-10
Yes the samba service is running.

---

