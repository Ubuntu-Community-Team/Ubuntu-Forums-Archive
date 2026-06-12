---
title: "Samba issue"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by Blindraven on 2007-10-10
I have a bunch of shares I use for my home network to take at their leisure. but sometimes for no apparent reason all my shares just vanish and no matter what I do i just cant get them to work again until I reboot.

sudo /etc/init.d/samba restart works but does nothing.

This is my smb.conf

# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2007/09/29 20:14:16

[global]
	workgroup = MSHOME
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

wins support = no
[homes]
	comment = Home Directories
	valid users = %S
	read only = No
	browseable = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Movies]
	path = /media/sda1/Movies
	guest ok = Yes

available = yes
browsable = yes
public = yes
writable = yes
[Music]
	path = /media/sda1/Music
	guest ok = Yes

available = yes
browsable = yes
public = yes
writable = no
[Series]
	path = /media/sda1/Series
	guest ok = Yes

available = yes
browsable = yes
public = yes
writable = no
[Games]
	path = /media/sda1/Games
	guest ok = Yes

available = yes
browsable = yes
public = yes
writable = no
[Applications]
	path = /media/sda1/Applications
	guest ok = Yes

available = yes
browsable = yes
public = yes
writable = no
[Anime]
	path = /media/disk/Anime
	guest ok = Yes
available = no
browsable = no
public = no
writable = no

---

