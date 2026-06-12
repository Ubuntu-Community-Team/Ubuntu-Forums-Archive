---
title: "Win 10 can access shared folders on ubuntu 21.10 but cannot open folders"
date: 2021-11-26
forum: Networking &amp; Wireless
---

### Post by naiqor0-people on 2021-11-26
I had ubuntu 21.10 working well on my desktop, could see win 10 laptop and open and copy shared files, win 10 could open and copy shared files on Ubuntu. So as 21.10 was an update of an update of a update i decided to do a new clean install of ubuntu 21.10. As i felt confident I could get it all up and running properly again.
After clean Ubuntu install I can see win 10 folders and files etc. and my OLD (at least 9 years) PVR that runs linux and Samba, see folders and files.
But Win 10 can see old PVR folders and files, and can see folders on the Ubuntu machine. But when i click to open a folder i get the following Message:-
"NETWORK ERROR
Windows cannot access \\computer name\folder name you do not have permissions to access \\computer name\folder name. Contact your network administrator to request access.

For more information about permissions, see Windows Help and Support" (usual MS help make more confusion)

But if i need some thing that is on the Ubuntu Machine I can copy it to the Windows machine, just cannot copy from the Ubuntu machine.

What am I missing

Thank You

---

### Post by Morbius1 on 2021-11-26
Please post the output of the following commands so the folks here can see how your Samba server is set up:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by naiqor0-people on 2021-11-27
```
testparm -s
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed
Server role: ROLE_STANDALONE


# Global parameters
[global]
	client max protocol = SMB3
	client min protocol = NT1
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
Net usershare info --long
cnijfilter2-5.50-1-deb]
path=/home/bucky/CanonStuff/cnijfilter2-5.50-1-deb
comment=
usershare_acl=Everyone:F,
guest_ok=y


[MedicalShirl]
path=/home/bucky/MedicalShirl
comment=
usershare_acl=Everyone:F,
guest_ok=y


info_fn: file /var/lib/samba/usershares/medical brian is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[MyAcc]
path=/home/bucky/MyAcc
comment=
usershare_acl=Everyone:F,
guest_ok=y


info_fn: file /var/lib/samba/usershares/medicalshirley is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[MedicalBrian]
path=/home/bucky/MedicalBrian
comment=
usershare_acl=Everyone:F,
guest_ok=y


[Videos]
path=/home/bucky/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=y


[packages]
path=/home/bucky/CanonStuff/cnijfilter2-5.50-1-deb/packages
comment=
usershare_acl=Everyone:F,
guest_ok=y


[My Pictures]
path=/home/bucky/My Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y


[Public]
path=/home/bucky/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y


[resources]
path=/home/bucky/CanonStuff/cnijfilter2-5.50-1-deb/resources
comment=
usershare_acl=Everyone:F,
guest_ok=y


[Templates]
path=/home/bucky/Templates
comment=
usershare_acl=Everyone:F,
guest_ok=y


[Downloads]
path=/home/bucky/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=y


[SambaConf]
path=/home/bucky/SambaConf
comment=
usershare_acl=Everyone:F,
guest_ok=y


[documents]
path=/home/bucky/CanonStuff/cnijfilter2-5.50-1-deb/documents
comment=
usershare_acl=Everyone:F,
guest_ok=y


[Tesla]
path=/home/bucky/Tesla
comment=
usershare_acl=Everyone:F,
guest_ok=y


[CanonStuff]
path=/home/bucky/CanonStuff
comment=
usershare_acl=Everyone:F,
guest_ok=y
```

---

### Post by naiqor0-people on 2021-11-27
```
testparm -s
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed
Server role: ROLE_STANDALONE


# Global parameters
[global]
    client max protocol = SMB3
    client min protocol = NT1
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
Net usershare info --long
cnijfilter2-5.50-1-deb]
path=/home/bucky/CanonStuff/cnijfilter2-5.50-1-deb
comment=
usershare_acl=Everyone:F,
guest_ok=y


[MedicalShirl]
path=/home/bucky/MedicalShirl
comment=
usershare_acl=Everyone:F,
guest_ok=y


info_fn: file /var/lib/samba/usershares/medical brian is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[MyAcc]
path=/home/bucky/MyAcc
comment=
usershare_acl=Everyone:F,
guest_ok=y


info_fn: file /var/lib/samba/usershares/medicalshirley is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[MedicalBrian]
path=/home/bucky/MedicalBrian
comment=
usershare_acl=Everyone:F,
guest_ok=y


[Videos]
path=/home/bucky/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=y


[packages]
path=/home/bucky/CanonStuff/cnijfilter2-5.50-1-deb/packages
comment=
usershare_acl=Everyone:F,
guest_ok=y


[My Pictures]
path=/home/bucky/My Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y


[Public]
path=/home/bucky/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y


[resources]
path=/home/bucky/CanonStuff/cnijfilter2-5.50-1-deb/resources
comment=
usershare_acl=Everyone:F,
guest_ok=y


[Templates]
path=/home/bucky/Templates
comment=
usershare_acl=Everyone:F,
guest_ok=y


[Downloads]
path=/home/bucky/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=y


[SambaConf]
path=/home/bucky/SambaConf
comment=
usershare_acl=Everyone:F,
guest_ok=y


[documents]
path=/home/bucky/CanonStuff/cnijfilter2-5.50-1-deb/documents
comment=
usershare_acl=Everyone:F,
guest_ok=y


[Tesla]
path=/home/bucky/Tesla
comment=
usershare_acl=Everyone:F,
guest_ok=y


[CanonStuff]
path=/home/bucky/CanonStuff
comment=
usershare_acl=Everyone:F,
guest_ok=y
```

---

### Post by Morbius1 on 2021-11-27
Ubuntu 21.10 made a change to the default permissions on home directories. It changed it from 755 to 750. 

What this does is prohibit everyone other than the owner of one's home directory to gain any type of access to that directory and any of it's contents. All of your shares allow guest access and since "guest" is not "bucky" samba allows access but Linux does not.

Two ways out of this:

[1] You can either allow "others" to at least traverse the /home/bucky directory so that the subdirectories can be accessed:
```
chmod o+x /home/bucky
```

[2] Or force the guest user to appear to be bucky - [COLOR="#0000FF"]at least for these samba shares.[/COLOR] You can do that by:

** Editing /etc/samba/smb.conf and right under the **workgroup = WORKGROUP** line add this one:
```
force user = bucky
```
** Then restart smbd:
```
sudo service smbd restart
```

Since all your shares allow guest access anyway I would go with option [2].

*[COLOR="#0000FF"]Since your original Ubuntu 21.10 was an upgrade to an upgrade I'm guessing that the original 755 permissions were maintained with each upgrade and only became a problem when you did a fresh install.[/COLOR]*

---

### Post by naiqor0-people on 2021-11-28
:P Thank you Morbius you have saved my day again, the reason i set the share with everyone is that I only have a home network with 2 computers, i only share with windows and they keep changing things and at times have been ask for a password, with no hint as to a win password or a ubuntu password.

---

### Post by danielusa on 2022-07-01
i also installed ubuntu 21.10 and had the same problem as yours. I have read the comments under your post, it's good that they helped me to fix the omission issue. [COLOR=#000000][FONT=Arial][sedecordle]("https://sedecordle.io/") [wordle]("https://wordle-2.com/")[/FONT][/COLOR]

---

