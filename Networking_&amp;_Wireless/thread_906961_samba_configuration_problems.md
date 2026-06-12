---
title: "samba configuration problems"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by thefacelesswarrior on 2008-09-01
I am trying to network my laptop to my desktop computer. My laptop connects to our wireless modem wirelessly, and the desktop connects to the modem via cable.

I can't find anywhere where someone can tell me in plain english how im supposed to configure my samba file or what im supposed to do to get them to share files over the network.

This is what my current smb.conf file looks like:

> # Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2008/09/01 14:23:24

[global]
	workgroup = MSHOME
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	wins server = 192.168.1.1
	wins support = Yes
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[LapDocuments]
	path = /home/eshy/LapDocuments
	read only = No
	guest ok = Yes

Also, I am running Ubuntu 7.04 Feisty Fawn, and the desktop computer is running Windows XP

Any ideas?

---

### Post by dmizer on 2008-09-01
Please take a look at the first link in my sig.

---

