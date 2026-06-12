---
title: "Samba Server Issue"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by fattymatty on 2008-12-29
Ive setup my samba Server and it gets the it works thing when i type in my ip address but it doesnt show my folders when i type in 192.168.0.99/homes for some reason just states 404 error

here is my /etc/samba/smb.conf

[global]
	workgroup = "HALLIDAY"
	netbios name = "HOMESVR"
	obey pam restrictions = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
	log level = 3
	log file = /var/log/samba.log
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[homes]
	comment = Home Directories
	read only = No
	create mask = 0700
	security mask = 0700

---

### Post by cmnorton on 2008-12-29
How are you accessing this folder? 404 sounds like an http protocol error.

---

### Post by jimmy the saint on 2008-12-29
try
```
smb://192.168.0.99/homes
```

---

