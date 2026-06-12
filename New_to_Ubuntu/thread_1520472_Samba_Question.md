---
title: "Samba Question"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by Thelasko on 2010-06-29
I have a folder shared with Samba.  This folder is located in my /home directory.  When a user of a Windows machine makes changes to a file in that folder, and saves them, the file becomes owned by the username "nobody".

This wouldn't be a problem, except the permissions on the file are changed so the file is read only for all users except nobody.  If I want to make changes to the file, I have to change the permissions with sudo first.

Is there a way to make it so everybody can read and write to this file without having to change the permissions every time?

---

### Post by Morbius1 on 2010-06-29
One way to do this is to add a line to smb.conf:
```
force user = morbius
```[COLOR=Blue]*Changing "morbius" to you own login user name.*[/COLOR]

Where you put that line depends on how you shared the folder. There are two methods to create samba shares in Ubuntu:

**Nautilus-share** ( right click a folder > Sharing options):
If you used this method then the line needs to be added to the **[COLOR=Blue][global] [/COLOR]**section of smb.conf:
```
gksu gedit /etc/samba/smb.conf
```Add the force user line, save the file, exit gedit, and restart samba:
```
sudo service smbd restart
```**Classic-shares** have the share definitions in smb.conf itself so you need to add the line to the share definition portion directly.

force user will act as a mask and convert "nobody" to "morbius"

---

### Post by Thelasko on 2010-07-07
That worked.  Thanks!

---

### Post by ubunterooster on 2010-07-07
This does work for me also; please mark this thread as "solved" (under thread tools) so others can use it for reference more easily

---

### Post by Thelasko on 2010-07-11
The problem appears to have returned.  I set the guest account = my user name.  Let's see what that does.

---

### Post by Thelasko on 2010-07-14
I'm still having issues with this.  If anybody has any suggestions, I'd appreciate it.

---

### Post by Morbius1 on 2010-07-15
Please post the output of the following commands:
```
net usershare info
sudo net usershare info
testparm -s
```

---

### Post by Thelasko on 2010-07-16
shared folder location and
```
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

---

### Post by Morbius1 on 2010-07-17
I need the full output of:
```
net usershare info
```and
```
testparm -s
```

---

### Post by Thelasko on 2010-07-19
```
net usershare info
[shared stuff]
path=/home/lasko/Shared stuff
comment=
usershare_acl=Everyone:F,
guest_ok=y
```

```
testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Shared stuff]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = MSHOME
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	guest account = lasko
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	read only = No

[Shared stuff]
	comment = Shared Folder
	path = /home/lasko/Shared stuff
	force user = lasko
	read only = No
```

---

### Post by Morbius1 on 2010-07-20
2 different methods of sharing folders in Samba and you're using both with different parameters on the same target directory.

One is Nautilus-share ( the output of **net usershare info** shows you how that is set up ) and the other is Classic-share ( which hows up in **testparm -s **). 

I suppose the easiest thing to do is eliminate the Nautilus-share:
```
 net usershare delete "shared stuff"
```Or you could just go back into Nautilus and "unshare" /home/lasko/Shared stuff.

There's no need to restart samba or reboot. See if that fixes things.

---

### Post by Thelasko on 2010-07-22
I think that fixed it.  Thanks!

---

