---
title: "CIFS configuration problem in 10.04"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by netwidget on 2010-09-06
I am trying to configure a CIFS/SMB file server and am getting the following message after installing Samba, setting up the smb.conf on the server, and the fstab file on the client computer:

```
mount: wrong fs type, bad option, bad superblock on //192.168.0.2/business,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

smb.conf file on server looks like this:

```
# Samba config file created 
# from UNKNOWN (127.0.0.1)
# Date: 2010/07/17 18:26:29

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	hosts allow = 192.168.0.
	username map = /etc/samba/smbusers
	workgroup = dugger
	security = user
;	encrypt passwords = yes
;	guest ok = no
;	guest account = nobody

[homes]
	comment = Home Directories
	path = /home/%u/share
	valid users = %S
	read only = No
	create mask = 0664
	directory mask = 0775
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[av]
	comment = Audio Video Share
	path = /av
	force group = av
	create mask = 0660
	directory mask = 0771
	writeable = yes
;	browseable = yes
	valid users = adriene, james, patti, root

[business]
	comment = Business Directories
	path = /business
	valid users = james, patti, root
	force group = business
	create mask = 0660
	directory mask = 0771
	writeable = yes
;	browseable = yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
```

and the lines added to the fstab file on the client look like this:

```
//192.168.0.2/business /home/james/business cifs credentials=/home/james/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0 
//192.168.0.2/av /home/james/av cifs credentials=/home/james/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

The credentials file is located in /home/james/.smbcredentials simply has:

```
username=james
password=mypassword
```

Can tell me why I am getting these errors?

---

### Post by papibe on 2010-09-07
Probably there's a package not installed. Try this:
```
$ dpkg -l | grep smbfs
```
If it's not installed, you can do it like this:
```
$ sudo apt-get install smbfs
```

I don't know why this package is not installed when you install samba.

Good Luck!

---

### Post by netwidget on 2010-09-07
pabibe:  Thank you! I had to install smbfs.

---

### Post by netwidget on 2010-09-07
The above worked on one machine, however when I use this setup on a second computer and run the following command:

```
$ sudo mount -a
```

I get the following returned to me on the command line:

```
Host is down
Refer to the mount.cifs(8) manual (e.g. man mount.cifs)
```

I know the server is not down because I can see the files and data located in the av and business directories located in /home/james.  Could it be that this configuration works only for a single user?

Any thoughts

---

### Post by papibe on 2010-09-07
I assume then that homes is the share you have problems with. Are you able to connect using smbclient? Check it like this:
```
$ smbclient //192.168.0.2/homes
```

Try mounting the share manually using the verbose option to get more info:
```
$ sudo mount -t cifs //192.168.0.2/homes /home/james/business --verbose -o credentials=/home/james/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777
```

---

