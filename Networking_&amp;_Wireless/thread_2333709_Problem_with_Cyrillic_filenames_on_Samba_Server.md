---
title: "Problem with Cyrillic filenames on Samba Server"
date: 2016-08-12
forum: Networking &amp; Wireless
---

### Post by grubstuck on 2016-08-12
Hi,
I have cross-compiled samba 3.6.25 for my ARM board. When I connect a pendrive containing Cyrillic filenames in it to the board and try to access it through my Ubuntu PC, the folders having Cyrillic names are not shown at all. While on windows machine the filenames are replaced with '?' (question mark)
Linux 2.6.36 

Here is my smb.conf file 


[global]
	netbios name = openwrt 
	workgroup = openwrt
	server string = openwrt
	syslog = 10
	encrypt passwords = true
	passdb backend = smbpasswd
	obey pam restrictions = yes
	socket options = TCP_NODELAY
 	unix charset = UTF-8
        dos charset = CP850 
        display charset = UTF-8
        ##client code page = 949
	##unix charset = ISO-8859-1
	preferred master = yes
	os level = 20
	#security = share
	security = user
	guest account = nobody
	invalid users = root
	smb passwd file = /etc/samba/smbpasswd
	use sendfile = yes
	min receivefile size = 1024
	mangled names = no
	allocation roundup size = 268435456
	client lanman auth = yes
	client ntlmv2 auth = no


[homes]
	comment = Home Directories
	browseable = no
	read only = no
	create mode = 0750
	read only = no
	guest ok = no
	create mask = 0755
	directory mask = 0755


I am a newbie.

---

