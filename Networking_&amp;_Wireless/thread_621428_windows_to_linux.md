---
title: "windows to linux"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by firewave100 on 2007-11-23
Please help I am on ubuntu 7.10
I need to connect my windows XP to ubuntu
I can connect and transfer files when in ubuntu
but not the from windows.
I see my linux mechine and get a box to log in
but what ever I type I cannot get into ubuntu

---

### Post by obrient on 2007-11-23
Once you have turned on Samba on your linux box you will need to create the users that can access the files. As root enter the following:

   1. sudo smbpasswd -e username
   2. Type and retype new Samba password 

If you have trouble writing to the folder check the permissions on the folder. The username and passsword that you set up should allow you to connect from your windows box.

If this still doesn't work you may want to check your smb.conf file at the end you should have something that looks like this.

[ShareName]
	comment = Anything you want
	path = /location/of/share
	writeable = yes
	browseable = yes
	valid users = smbuser

---

