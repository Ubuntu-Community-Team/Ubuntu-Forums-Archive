---
title: "Ubuntu sharing issue"
date: 2021-09-26
forum: Networking &amp; Wireless
---

### Post by dennnic on 2021-09-26
Hello,

I'm new to Ubuntu, after several years of using Mints. I appologize if this question seems kind of basic to some of you.

I am trying to convert my pc into some kind of NAS, just to share several folders from it's hard drive. I've seen that sharing procedure is straightforward, it instals samba, modify share and that's it. Folders do show up on android browsers, but I am unable to get any access to them! 

I figure it must be something to do with permissions, however I can't get to the bottom of it. Running nautilus as sudo and looking at permissions tab displays that pretty much everything is set on read/write already.

Any idea on how to proceed?? 

Thanks in advance,

Stefan

---

### Post by Morbius1 on 2021-09-26
Need to see how samba is set up to answer the question. Please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

And what version of Ubuntu are you using. Each release has it's own version of Samba and things can change over time.

---

### Post by dennnic on 2021-09-26
TESTPARM

visnja@Visnjinprvikomp:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Server role: ROLE_STANDALONE


# Global parameters
[global]
	log file = /var/log/samba/log.%m
	logging = file
	map to guest = Bad User
	max log size = 1000
	obey pam restrictions = Yes
	pam password change = Yes
	panic action = /usr/share/samba/panic-action %d
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	passwd program = /usr/bin/passwd %u
	server role = standalone server
	server string = %h server (Samba, Ubuntu)
	unix password sync = Yes
	usershare allow guests = Yes
	idmap config * : backend = tdb




[printers]
	browseable = No
	comment = All Printers
	create mask = 0700
	path = /var/spool/samba
	printable = Yes




[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
visnja@Visnjinprvikomp:~$ 


USERSHARE

visnja@Visnjinprvikomp:~$ net usershare info --long
[Filmovi]
path=/media/visnja/Podaci/Filmovi
comment=
usershare_acl=Everyone:F,
guest_ok=n


[Muzika]
path=/media/visnja/Podaci/Muzika
comment=
usershare_acl=Everyone:F,
guest_ok=n


[Slike]
path=/media/visnja/Podaci/Slike
comment=
usershare_acl=Everyone:F,
guest_ok=n

---

### Post by dennnic on 2021-09-26
Just installed it this week - 20.04

Thanks for your help!

---

### Post by Morbius1 on 2021-09-26
All of your shares are of the form:
> path=/media/visnja/Podaci/XXX
Where visnja is your user name.

When Linux creates the /media/$USER ( /media/visnja in your case ) folder it places special permissions settings on that folder such that only that user can traverse the folder to get to what is beyond it.

So in this case for example:
> [Filmovi]
path=/media/visnja/Podaci/Filmovi
comment=
usershare_acl=Everyone:F,
guest_ok=n
The only samba client user that can access that folder would be visnja only because of the /media/visnja issue ... and only if you added visnja to the samba password database:
```
sudo smbpasswd -a visnja
```

If you have multiple users to this share a modification to smb.conf would be necessary.

---

### Post by dennnic on 2021-09-27
This solved the problem. Would it work as well if I select guest access / without asking for password?

---

### Post by Morbius1 on 2021-09-27
You can do guest access but ...............

You will need to edit /etc/samba/smb.conf and add a line -- I usually add it right under the workgroup = WORKGROUP line:
```
force user = visnja
```
Then restart smbd:
```
sudo service smbd restart
```

The only issue is some of the Android file managers really don't do guest access very well. You can try it. Maybe passing a fake password if you need it?

---

### Post by dennnic on 2021-09-28
It seems too much of a hassle, I will just continue using visnja and password. Thank you for your help!

---

