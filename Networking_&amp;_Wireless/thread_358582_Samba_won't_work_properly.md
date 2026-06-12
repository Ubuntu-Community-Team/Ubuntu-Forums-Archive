---
title: "Samba won't work properly"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by yeoheric on 2007-02-11
Hi all,

My boss asked me to do a Samba share for some users and computers to connect to. The target machine is running Ubuntu 6.06-1 LTS Server, all patched up and has no firewall. Here is my smb.conf:

[global]
	workgroup = WORKGROUP
	server string = Peanuts
	username map = /etc/samba/smbusers
	
[printers]
	comment = All Printers
	path = /tmp
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[data]
	comment = Data
	path = /opt/saas/localq
	valid users = fred
	force user = fred
	force group = users
	writeable = yes
	create mask = 0777
	directory mask = 0777
	
The physical share location has the following permissions:
eyeoh@peanuts:/opt$ ls -al saas
total 12
drwxr-xr-x 3 fred users 4096 2007-02-11 21:54 .
drwxr-xr-x 3 fred root  4096 2007-02-11 21:54 ..
drwxr-xr-x 2 fred users 4096 2007-02-11 21:54 localq

When I try to connect via Nautlus I get an error message that I cannot connect properly. I gotta hit the refresh button to get the authentication dialog. I key the info in and then I get connected. 

Also, from one of the Gentoo machines I put in the following in the fstab:
//10.1.5.189/localq    /opt/saas/share/peanuts/localq  smbfs auto,credentials=/root/smb,uid=1004,nodev,noatime               1 2

A text file named smb, with the login credentials to login to the Ubuntu server was created in the /root directory.

When I do a mount -a command on the Gentoo machine I get Authentication refused. The uid for the user fred is 1004 on the Ubuntu server. The Gentoo server server is running Shorewall with ports 135:139 and 445 enabled outgoing (i.e. ACCEPT  fw  net:10.1.5.189          tcp  135:139,445)

Please help.

Eric

---

