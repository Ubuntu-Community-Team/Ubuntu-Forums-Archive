---
title: "Adding ubuntu desktop as a network drive using Samba"
date: 2016-02-25
forum: Networking &amp; Wireless
---

### Post by blake12 on 2016-02-25
I have been trying on and off for quite some time now in regards to getting the samba service to work on my Ubuntu machine. I have run into a raft of problems which thankfully the internet has provided me with a heap of answers and things to try. I am relatively new in regards to doing everything in the command window so that alone has made it a little difficult to fix. 

The issue i am currently having is the Ubuntu machine has the Samba service installed correctly i have also installed a GUI to manage the logins and credentials for the Samba however my MAC when trying to add the network drive everything looks like it is going swimmingly until it bombs out right at the end. I have used the Ubuntu desktop to access the MAC as a shared network drive so i know they are both on the same network and happy. I have also disabled the firewall on my ubuntu because i thought that was an issue in itself blocking the ports that the Samba service uses. 

Is there anything i have missed that i could try? Any dumps i could give you in order for a  hand? I have probably left out a few things here which i can answer if i am asked. Id appreciate any help people can give me.

Thanks,
Blake
[ATTACH=CONFIG]267485[/ATTACH]
[ATTACH=CONFIG]267486[/ATTACH]
[ATTACH=CONFIG]267487[/ATTACH]

---

### Post by Bucky Ball on 2016-02-25
*Thread moved to **Networking & Wireless**.*

---

### Post by Morbius1 on 2016-02-25
I'm confused over the sequence of the screenshots. You shouldn't have gotten to the 2nd one unless you got through the first one.

Starting with the obvious:

** Did you add the user "blake" to the samba password database:
```
sudo smbpasswd -a blake
```
** And does "blake" have Linux permissions to access the folder represented by the "Archive" share as well as the path leading to it.

You might want to post the output of the following commands so we can see how you are set up:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by blake12 on 2016-02-25
> **Morbius1 said:**
> I'm confused over the sequence of the screenshots. You shouldn't have gotten to the 2nd one unless you got through the first one.

Starting with the obvious:

** Did you add the user "blake" to the samba password database:
```
sudo smbpasswd -a blake
```
** And does "blake" have Linux permissions to access the folder represented by the "Archive" share as well as the path leading to it.

You might want to post the output of the following commands so we can see how you are set up:
```
testparm -s
```
```
net usershare info --long
```

Hi Morbius1, Thanks for trying to help mate. Apologies on the photos the filename has the timestamp which indicates which was first. 

I have added the user blake to the user list in Samba via the GUI i have been using also on the Ubuntu side as this is the username for the ubuntu system. 

Samba GUI with everyone having access and also showing blake as the user (same user and password as my login to ubuntu)

[ATTACH=CONFIG]267498[/ATTACH][ATTACH=CONFIG]267499[/ATTACH]

Ubuntu Permissions, blake as the user group and also as the main user

[ATTACH=CONFIG]267500[/ATTACH]

Just working on those outputs now :).....Alight so the output to 'testparm -s' was :

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Archive]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	server role = standalone server
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
	idmap config * : backend = tdb


[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[Archive]
	path = /media/blake/Archive
	read only = No
	guest ok = Yes

Output to usershare was:

[Videos]
path=/media/blake/Archive/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=y



I think by the looks of that there is something missing?

---

### Post by Morbius1 on 2016-02-26
Actually it looks like everything is in order - given the path of the shared folder. Unless you are doing something funky with the " 	username map = /etc/samba/smbusers" file.

Since you are allowing guest access to the share I would do the following:

** Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```
** Add a line - right under the "workgroup = workgroup" line:
```
force user = blake
```
** Save the file
** Restart smbd:
```
sudo service smbd restart
```
You don't need to pass credentials - you can access as "guest" from OSX.

---

