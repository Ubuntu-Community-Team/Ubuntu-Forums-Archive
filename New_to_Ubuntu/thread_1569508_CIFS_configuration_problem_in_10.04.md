---
title: "CIFS configuration problem in 10.04"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by netwidget on 2010-09-06
I am trying to configure a CIFS/SMB file server and am getting the following message after installing Samba, setting up the smb.conf on the server, and the fstab file on the client computer:

>  mount: wrong fs type, bad option, bad superblock on //192.168.0.2/business,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

smb.conf file on server looks like this:

> # Samba config file created 
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

and the lines added to the fstab file on the client look like this:

> //192.168.0.2/business /home/james/business cifs credentials=/home/james/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0 
//192.168.0.2/av /home/james/av cifs credentials=/home/james/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

The credentials file is located in /home/james/.smbcredentials simply has:

username=james
password=mypassword

Can tell me why I am getting these errors?

---

