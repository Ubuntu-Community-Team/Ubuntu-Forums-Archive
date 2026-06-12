---
title: "[SAMBA] Users can read other users' folders"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by brechtvb on 2007-04-23
I made a samba file server with dapper drake. It acts as member server. Everything works, login with active directory account, setting file permissions with ntfs-like acl's and stuff.

Samba is working to, but not the way i want it to.

```

[global]
	workgroup = DOMAIN
	realm = DOMAIN.NET
	server string = %h
	password server = DC.DOMAIN.NET
	enable privileges = yes
	obey pam restrictions = yes
	allow trusted domains = no
	name resolve order = host bcast
	log file = /var/log/samba/log.%m
	max log size = 1024
	log level = 1
	security = ADS
	encrypt passwords = true
	socket options = TCP_NODELAY IPTOS_LOWDELAY
	map to guest = never
	winbind enum users = no
	winbind enum groups = no
	template shell = /bin/bash
	template homedir = /home/DOMAIN/%U
	winbind use default domain = yes
	hide dot files = yes

[homes]
	browsable = no
	read only = no
	guest ok = no
	inherit acls = yes
	inherit owner = yes
	inherit permissions = yes
	force user = %U
	force group = domain admins

```

Let's presume there are 2 users, A and B. User B can manually browse to user A's files and only read them. I don't want him to. So i tried to do like this:

[homes]
        ....
	valid users = %S

But now no single user can access his or her share. (if i put %S into the comment, i get _IPC)

Now i can fix this by changing the folder permissions to 'Domain Admins' manually but when a new user is added to the active directory and samba makes a new folder for him, it write with the 'Domain Users' as group owner. Is there a way to change that ?

This is probably by the three times inherit-stuff @ the homes-section. But the users need read-permission on the users-folder-directory, but not on a user-directory.

Sorry, i dont have real ls-output for this, but i looks like this:

```

/home/DOMAIN
user : root : rwx
group : Domain users : r-x
other : ---

```

and

```

/home/DOMAIN/userA
user : userA : rwx
group : Domain users : r-x
other : ---

```

the second one should look like this:


```

/home/DOMAIN/userA
user : userA : rwx
group : Domain Admins : rwx
other : ---

```

---

