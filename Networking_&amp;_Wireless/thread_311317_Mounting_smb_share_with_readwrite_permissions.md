---
title: "Mounting smb share with read/write permissions"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by Super J on 2006-12-02
I am trying to mount a samba share to a folder and have full read/write permissions. If I access the share by going to Places->Network Servers, I can see it and I have full read/write access once I enter my password. I am currently mounting the share via a script that is /etc/ini.d/. Here's what the script looks like:
```
sudo mount -t smbfs -o username=my_name,password=my_password //ubuntu-server/multimedia /home/jeremy/media
```
I own the folder /home/jeremy/media and have full access to it when the share is not mounted. The root account owns it after I run the script. 

Here is my smb.conf.
```
[global]
   workgroup = WORKGROUP
   netbios name = ubuntu-server
   server string = %h server (Samba, Ubuntu)
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   username map = /etc/samba/smbusers
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   socket options = TCP_NODELAY

[homes]
   comment = Home Directories
   browseable = no
   valid users = %S
   writable = yes

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[multimedia]
  comment = Multimedia
  path = /multimedia
  writable = yes
```
Thanks for the help.

---

### Post by Super J on 2006-12-03
bump

---

