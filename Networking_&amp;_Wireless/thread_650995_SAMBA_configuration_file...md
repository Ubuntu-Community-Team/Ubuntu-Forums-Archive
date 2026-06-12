---
title: "SAMBA configuration file.."
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by shishirkotkar on 2007-12-27
could anyone plz explain me this  config file



[global]
	workgroup = EXAMPLE
	netbios name = K12LTSP
	domain logons = yes
	domain master = yes
	os level = 99
	preferred master = yes
	add machine script = /usr/sbin/useradd -d /dev/null -g winmachines -s /bin/false -M %u
	logon drive = H:

[homes]
	create mask = 0600
	directory mask = 0700
	path = %H
	read only = no
	valid users = %S

[netlogon]
	path = /home/netlogon
	guest ok = yes
	writable = no
	share modes = no

---

### Post by schaumkeks on 2007-12-27
> **shishirkotkar said:**
> could anyone plz explain me this  config file

A full explanation gives
```
man smb.conf
```
> **shishirkotkar said:**
> 
[global]
	workgroup = EXAMPLE
	netbios name = K12LTSP
	domain logons = yes
	domain master = yes
	os level = 99
	preferred master = yes
	add machine script = /usr/sbin/useradd -d /dev/null -g winmachines -s /bin/false -M %u
	logon drive = H:

[homes]
	create mask = 0600
	directory mask = 0700
	path = %H
	read only = no
	valid users = %S

[netlogon]
	path = /home/netlogon
	guest ok = yes
	writable = no
	share modes = no

The most important part is the homes section which allows users to access their home directory with their username and password.
Excerpt from the sample config file:
```
# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700
```

---

