---
title: "Samba - access denied"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by frodemt on 2008-01-03
Hi there

I have this access problem in a samba share that I dont understand.

[svein]
	delete readonly = yes
	writeable = yes
	path = /disk3/frimappe/svein
	write list = svein,frodemt
	only user = yes
	valid users = svein,frodemt
	user = svein,frodemt

"/disk3/frimappe/svein" is 755 and owned by user "svein".

This computer use windows XP. When I browse server and enter the share "svein" with user "svein", I get asked for password. Not before even thou I am logged in with another username. I enter username "svein" and his password, but get prompted for username and password again. What did I do wrong?

What I want to do is that only user frodemt and user svein can access this share from a windows and a ubuntu system. They both have full write and read access.

---

### Post by gazj on 2008-01-03
have you created samba passwords for theese user accounts on your samba server (not to be confused with the standard linux password)

```
smbpasswd -a *username*
```

---

### Post by frodemt on 2008-01-03
Yes, and they are syncroniced when something is changed in unix user.

User "svein" is set to shell "/usr/sbin/nologin". May this be a problem? I have set him to this so he cannot login using ssh. He should only have access through samba.

---

### Post by gazj on 2008-01-03
what is the global section in your samba config like.  I will post mine as an example, i am using arch linux not ubuntu, but samba is samba, hopefully looking at mine may show where you are going wrong.

```

[global]
	workgroup = UBUNTUBOXES
	server string = Samba Server
	log file = /var/log/samba/log.%m
	max log size = 50
	domain logons = Yes
	dns proxy = No
	ldap ssl = no
	hide special files = Yes
	hide files = /$RECYCLE.BIN/

[gary]
	delete readonly = yes
	writeable = yes
	path = /data/home/gary
	force directory mode = 777
	force group = root
	force create mode = 777
	force user = root
	comment = Garys Documents
	valid users = gary
	create mode = 777
	directory mode = 777

[becky]
	writeable = yes
	delete readonly = yes
	path = /data/home/becky
	force directory mode = 777
	force group = root
	force create mode = 777
	force user = root
	comment = Beckys Documents
	valid users = becky
	create mode = 777
	directory mode = 777

[share]
	writable = yes
	delete readonly = yes
	path = /data/home/shared
	force directory mode = 777
	force group = root
	force create mode = 777
	force user = root
	comment = Shared Documents
	valid users = gary,becky
	create mode = 777
	directory mode = 777

```

I can't see why the shell path would make any difference, all of mine are set to /bin/bash so i can't reassure you on this, but if your user frodemt is working and sevin is not then i would say it is the problem

---

### Post by frodemt on 2008-01-03
[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	socket options = TCP_NODELAY
	obey pam restrictions = yes
	sync always = yes
	encrypt passwords = true
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	dns proxy = no
	netbios name = lamp2
	server string = %h server (Samba, Ubuntu)
	invalid users = root
	workgroup = MYRKROKEN1
	os level = 20
	security = user
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000

frodemt is a normal user with bash-shell. He also cannot enter the share. I'm kinda lost :)

---

