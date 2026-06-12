---
title: "Networking with Windows XP"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by jpe2000 on 2006-10-19
Okay, I have Samba all setup. I have these settings in my shared folder options. 

File path:  "/home/josh"
Name:  "josh"
Share with:  "SMB"
Checked "Allow broswing folder"
Assuming the password is my root or user password (used them both)


In Windows I have used the user name:
JOSH/GUEST
josh
Josh
UBUNTU-LINUX\josh
Ubuntu-Linux\josh
Ubuntu-linux\josh

And I have tryed my root and user password. NONE of them work. Windows sees that I have a Windows network going on here but I cannot log in! PLEASE help me with this.

---

### Post by jpe2000 on 2006-10-20
bump before i go to bed

---

### Post by hopstah on 2006-10-20
you need to create samba user and passwords.

[http://ubuntuguide.org/wiki/Dapper#How_to_add.2Fedit.2Fdelete_network_users](http://ubuntuguide.org/wiki/Dapper#How_to_add.2Fedit.2Fdelete_network_users)

edit: and i'm pretty sure that the samba user name has to be the same as a user on your ubuntu install, but the password can be different.  so for me to share music with my housemates, i made my samba password 'share' so that i didn't have to tell them my logon password.

---

### Post by jpe2000 on 2006-10-20
When I type this:

sudo smbpasswd -a system_username

It gives me this error message:

New SMB password:
Retype new SMB password:
Failed to initialise SAM_ACCOUNT for user system_username. Does this user exist in the UNIX password database ?
Failed to modify password entry for user system_username
josh@Ubuntu-Linux:~$ gksudo gedit /etc/samba/smbusers

---

### Post by Abhi Kalyan on 2006-10-20
Am having this serious Problem too.
Have a windows 2003 server running a doamin and i dont know how to connect my uduntu system to this so as to enagble file sharing, Print sharing.
Internet sharing is happening, thats how am in thi fforum.
So some body HELP PLEASE:-k :( :confused: :-#

---

### Post by jpe2000 on 2006-10-20
...

---

### Post by hopstah on 2006-10-23
[QUOTE=hopstah]edit: and i'm pretty sure that **the samba user name has to be the same as a user on your ubuntu install**, but the password can be different.  so for me to share music with my housemates, i made my samba password 'share' so that i didn't have to tell them my logon password.[/QUOTE]
re-read.  you can't make a samba user by the name of system_username unless you happen to have a user on your computer by that same name.  if you use, for example, the name 'ryan' to log on with, then your samba user name has to be 'ryan' as well.

---

### Post by Abhi Kalyan on 2006-10-25
Dear jpe2000,
Try using IP address instead of the system name, It worked for me both ways.

---

