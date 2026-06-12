---
title: "accessing NTFS drive over network"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by GordonBooker on 2010-09-13
I am trying to access the shared folders on my ubuntu 10.04 machine from a windows 7 machine.
I used samba to allow  access.

I can get access to folders on the drive that Ubuntu is installed on.

I cannot get access to my data drive (a 2TB drive formatted to NTFS)
I get the message (for example)  "windows cannot access \\kitchenbox\video"

Thanks for any help.

---

### Post by Morbius1 on 2010-09-13
How are you mounting the drive and what method of samba sharing ( there are two ) are you using.

If you post the output of the following commands it will tell us what samba method you're using and how the shares are defined:
```
net usershare info
```
```
testparm -s
```

---

### Post by GordonBooker on 2010-09-13
Hi,
net usershare info did not return anything. ( I don't know what I'm doing with the terminal at all)

testparm -s returned :
> Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Video]"
Processing section "[Pictures]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
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

[Video]
	comment = videos on keith kitchen
	path = /media/Data/Video
	read only = No
	guest ok = Yes

[Pictures]
	comment = pictures folder on linux disk not data
	path = /home/keith/Pictures
	read only = No
	guest ok = Yes



---

### Post by Morbius1 on 2010-09-13
Edit smb.conf as root:
```
 gksu gedit /etc/samba/smb.conf
```Find the share definition for Video:
> [Video]
    comment = videos on keith kitchen
    path = /media/Data/Video
    read only = No
    guest ok = YesAdd a line to that share definition so that it looks like this:
> [Video]
    comment = videos on keith kitchen
    path = /media/Data/Video
[COLOR=Blue]force user = morbius[/COLOR]
    read only = No
    guest ok = Yes*Change [COLOR=Blue]morbius[/COLOR] to your own login user name.*

Save smb.conf, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```See if the remote user can access the video share.

---

### Post by GordonBooker on 2010-09-13
Wahey ! Thanks very much, you solved it for me. That's great and very kind of you.

---

