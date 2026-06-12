---
title: "[Solved}Strange SMB/SAMBA permissions problem - smbfs appears to change mount-point?"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by rhcm123 on 2009-04-07
I have been running a SMB server for 10 months now. It's been working very well, so far.

It used to be that if i accessed the share as username ussr, then only my directory "ussr" and the Public directory were accessible. The rest of the directories would have the "unacessible X" icon over them, and clicking them leads to a "permission denied" error. I liked it that way.


Then my server, and my forgotten-to-get-backed-up config file died.

Now it seems to have changed. I can click open any directory. I cannot see the contents, but the fact that i can do this and not get any permissions denied error is mildly annoying.

Another factor that annoys me is that the mount point /media/remote, which is owned by root:root and chmoded 700, changes to be owned by ussr:root whenever the drive is mounted? 

Does anybody know what on earth i've done wrong to this permissions system and what i can do to get it back to the way it was?

---

### Post by rhcm123 on 2009-04-12
3-day bump

EDIT: attached my smb.conf file, for reference.
```
# CONFIG FILE FOR SAMBA
# WRITTEN BY USSR
# LAST MODIFIED 7 JAN/09

# Global parameters
[global]
	log file = /var/log/samba/log.%m
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	map to guest = Bad User
	wins support = true
	dns proxy = No
	netbios name = USSR-MOSCOW
	server string = SMB system on USSR-MOSCOW
	client lanman auth = No
	client plaintext auth = No
	lanman auth = No
	default = Share
	local master = Yes
	workgroup = USSR
	os level = 20
	security = user
	preferred master = no
	max log size = 50
	printing = cups
	printcap name = cups
	use client driver = yes
	guest account = nobody
	load printers = yes
	interfaces = 192.168.2.193

# /SHARE CONFIGS
[share]
	browseable = yes
	read only = No
	writeable = yes
	path = /share
	create mask = 0700
	comment = Main share directory on USSR-MOSCOW.
	directory mask = 0700
	valid users = ussr,elisabeth,fred,carol,root,nobody

# BACKUP DRIVE CONFIGS
[backup]
	path = /media/backup
	valid users = root
	browseable = yes
	read only = No
	writeable = yes
	comment = Backup Drive on USSR-MOSCOW. root Access Only.
	create mask = 0777
	directory mask = 0777

# PRINTER SETTINGS
[printers]
	comment = Printers on USSR-MOSCOW
	browseable = no
	path = /printer
	printable = yes
	force user = nobody
	public = yes
	writable = no
	create mode = 0700

# CDROM SHARING
[cdrom]
	comment = CD on USSR-MOSCOW
	read only = yes
	writable = no
 	locking = no
	path = /media/cdrom
	public = yes


```

---

### Post by rhcm123 on 2009-04-17
Nevermind, i fixed the problem. It was not actually a problem with the server, but rather a problem with the clients. The shares were permanently mounted in the /etc/fstab with this line of code:
```
//192.168.2.193/share /media/remote smbfs credentials=/root/.smb1,**uid=1000**,umask=000,user,auto   0 0

```

I bolded the important part. uid=1000. I/the guide i blindly copy-pasted (as if nobody else ever does that :shock: ) focred a uid on the mount point - in this case, mine. After i removed the line and remounted the drives, there were no problems, and the system returned to normal.

Hope this helps anybody else with this problem! :)

---

