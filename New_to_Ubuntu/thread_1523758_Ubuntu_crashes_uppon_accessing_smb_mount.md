---
title: "Ubuntu crashes uppon accessing smb mount"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by dvdhaar on 2010-07-04
Hi there,

I've recently reinstalled Ubuntu and I'm now trying to mount my smb shares in my /etc/fstab, I used this guide : [http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)

A couple of lines from my /etc/fstab:

```

//192.168.1.100/home /media/Home cifs auto,iocharset=utf8,uid=daniel,gid=users,credentials=/root/.credentials,file_mode=0775,dir_mode=0775 0 0
//192.168.1.100/root /media/Server cifs auto,iocharset=utf8,uid=daniel,gid=users,credentials=/root/.credentials,file_mode=0775,dir_mode=0775 0 0

```

I can access the Home share without any problems, but as soon as I access the Server (/root) mountpoint Ubuntu freezes - nothing works, no other virtual terminals or nothing, hard resetting is the only option. The funny thing is when I access the same share using nautilus - smb://server/root/ I do NOT have any problems.

A couple of lines from my smb.conf on the server:

```


# General

	netbios name = server
	workgroup = WORKGROUP
	server string = 

# Print

	disable spoolss = yes

# Authentication

	security = user
	encrypt passwords = true
	map to guest = bad user

[home]

	comment = Daniel's Home Directory
	path = /home/daniel/
	browseable = no
	read only = no

[root]

	comment = /
	path = /
	read only = no
	browseable = no


```

Desktop runs 10.04
Server runs 9.04

I tried to check the logfiles but couldn't find anything, besides I don't know which one to check to be honest!

---

### Post by dvdhaar on 2010-07-08
*bump* :)

---

