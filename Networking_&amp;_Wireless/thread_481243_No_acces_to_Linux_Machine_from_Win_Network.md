---
title: "No acces to Linux Machine from Win Network"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by DrScum on 2007-06-22
I have a Linux Box with Ubuntu 7.04 running being part of a small office workgroup running under WinXP. I can access the Windows shares from the Linux Box but I can't logon to the Linux shares from the Windows machines. All I get is a login window where I enter the login/password combination but nothing happens.

---

### Post by McNils on 2007-06-22
Have you added the users with smbpasswd on the linux box?

---

### Post by DrScum on 2007-06-22
I wouldn't know how to do that.

---

### Post by crane on 2007-06-22
Check on this page. Good guide to getting started
[http://ubuntuguide.org/wiki/http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service")

---

### Post by DrScum on 2007-06-22
Following the advice in the link given:

when I do

sudo smbpasswd -a system_username
gksudo gedit /etc/samba/smbusers


all I get  is:

root@LinuxBox:/home/joe# sudo smbpasswd -a LinuxBox_joe
New SMB password:
Retype new SMB password:
Failed to modify password entry for user LinuxBox_joe

obviously I am doing something wrong.

samba is installed and running by the way.

---

### Post by rhuarch on 2007-06-24
I am getting the same error when I try this.  I think we must be interpreting the instructions incorrectly, but I'm not sure what I am doing wrong.  I would really appreciate some further explanation on this one.  Alternatively, maybe someone can point us to a good utility for managing samba users/passwords through the GUI?  That would be nice for some who is very much from the WIMP generation. :)

---

