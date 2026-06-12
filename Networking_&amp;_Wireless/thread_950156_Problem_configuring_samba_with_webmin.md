---
title: "Problem configuring samba with webmin"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by tstack77 on 2008-10-16
I am trying to set up a NAS using hardy server. So far I have samba and webmin successfully installed. I've created a file share and set up the security and access control as writable and made myself a 'valid user'. 

The way it is now I can see the share on my xp machine but I cannot write to the disk (access denied/driving me nuts!).

What am I missing?

smb.conf:

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	socket options = TCP_NODELAY
	obey pam restrictions = yes
	map to guest = bad user
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	server string = %h server (Samba, Ubuntu)
	invalid users = root
	unix password sync = yes
	workgroup = SHARE
	os level = 20
	syslog = 0
	preferred master = no
	usershare allow guests = yes
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	pam password change = yes

## Browsing/Identification ###

;   wins support = no

;   wins server = w.x.y.z

;   name resolve order = lmhosts host wins bcast

#### Networking ####

;   interfaces = 127.0.0.0/8 eth0

;   bind interfaces only = true

#### Debugging/Accounting ####

;   syslog only = no


####### Authentication #######

;   guest account = nobody

########## Domains ###########

;   domain logons = yes

;   logon path = \\%N\profiles\%U

;   logon path = \\%N\%U\profile

;   logon drive = H:
;   logon home = \\%N\%U

;   logon script = logon.cmd

; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

[Public]
	valid users = stack
	writeable = yes
	path = /mnt/Folders/Public

---

### Post by tstack77 on 2008-10-17
Anyone? Happily accept a guess ;-)

---

### Post by superprash2003 on 2008-10-18
what are the current permissions of the Public folder?

---

