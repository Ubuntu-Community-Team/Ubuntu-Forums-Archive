---
title: "Sharing folders in Ubuntu 13.10"
date: 2014-07-14
forum: Networking &amp; Wireless
---

### Post by tmontney on 2014-07-14
I would like to share a folder from Ubuntu to Windows computers. I've tried to follow tutorials, but they haven't worked.

I have samba installed, and edited the config file to...

[images]
comment = Windows Image Backups
path = /home/tyler/Images
browseable = yes
guest ok = no
writeable = yes
force group = users
create mask = 0664

Then did a sudo service smbd restart.

I can browse the Ubuntu computer, and see the share. When I try to connect, I get access denied. I use the account I use to log into the Ubuntu computer. I've even done computerName\userName for the Username field, still cannot get access.

---

### Post by TheFu on 2014-07-15
First, did you set the password for all users via **smbpasswd**?

a) 13.10 support ends this month. time to move to 14.04 to maintain the system and have patches available.

b) CIFS Sharing folders under Ubuntu desktop has become really easy. Open Nautilus, right click on the directory to be shared ... click sharing ... may want to check the box that keeps the share live always.

Or

c) [http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/](http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/)

Trying to share files to different users under a HOME directory is generally a bad idea. HOME is meant for 1 user, unless the person doing the sharing understands file/directory permissions very well.

When it comes to troubleshooting CIFS connections, there are others here much better than me. They usually wait until just after I've written something stupid to respond.  So .... let me see if I can help in that regard. ;)

Please post the output from **testparm** and from **smbtree**.

My working setup to CIFS share the HOME for individual users is this:
```
[global]
	workgroup = WORKGROUP
	server string = %h server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	unix extensions = No
	dns proxy = No
	usershare allow guests = No
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[homes]
	comment = Home Directories
	valid users = %S
	read only = No
	create mask = 0644
#	hosts allow = 127.0.0.1, 172.22.22.27
	hosts allow = 127.0.0.1, 172.22.22.0/24
	hosts deny = 0.0.0.0/0
```

---

### Post by tmontney on 2014-07-15
See, I read the opposite (that sharing in the home folders was recommended).

I'm going to have a few shared folders, and need to make sure only certain users can access certain ones. Nautilus didn't give me an option for user permissions.

Option C is what I need. I remembered that exact solution, but couldn't remember how I could get it.

---

### Post by bab1 on 2014-07-15
> **tmontney said:**
> See, I read the opposite (that sharing in the home folders was recommended).

It's not really a matter of recommendation.  More a matter of what you want todo.  If you want users to make their own shares then you use usershares via a GUi interface.  If you want shares that are managed by the root user (admin) then you should use the traditional smb.conf file to configure them.

You can (as the root user) make an area in the file system that is available for all users to create usershares outside of /home, but for the most part most users do not understand how to do this.
> 
I'm going to have a few shared folders, and need to make sure only certain users can access certain ones. Nautilus didn't give me an option for user permissions.

Option C is what I need. I remembered that exact solution, but couldn't remember how I could get it.
That should work fine as long as you have a host that is running a full desktop.  If you wanted (or needed) to run a server with  no GUI then you should learn how to do this via the command line.  In that scenario all you need is the *samba package* and a txt editor.

I have several machines that no GUI will run on them (think P3).  The run all the time as NAS units with both Samba and NFSv4 on them.

---

