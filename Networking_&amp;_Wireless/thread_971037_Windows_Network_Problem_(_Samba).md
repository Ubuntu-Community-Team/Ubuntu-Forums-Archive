---
title: "Windows Network Problem ( Samba)"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by RaptorITA on 2008-11-04
Hi all, it's about 5 months I'm using ubuntu, and I have a problem that in all this time I wasn't able to solve. Since Ubuntu 8.04 and now with 8.10 I wasn't able to see the windows pc in my lan.With Ubuntu 8.04 I wasn't able neither to see the Lan, neither the single PCs, while with ubuntu 8.10 sometime(don't know why), my pc and the network appears, but no windows PCs, and at the same time no windows PCs can see me in my lan. I can ping the windows pc and they can ping me too, but also the direct connection doesn't work. Here it is my smb.conf :

```
[global]
	workgroup = APPARTAMENTO 4
	server string = Francesco
	interfaces = lo, eth0
	bind interfaces only = Yes
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	wins support = Yes
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


```

I search lot of time for a solutions but nothing help.

So I hope you can give me the right tips :)

Thx in advance

---

### Post by bab1 on 2008-11-04
This sounds like you setup sharing via the Gnome GUI interface.  No shares are listed in you smb.conf file. GUI setup in Gnome is broken at this time. For more information see [[COLOR="Blue"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=784259&page=8").  From post #78 on, the discussion is on proper setup of smb.conf

---

