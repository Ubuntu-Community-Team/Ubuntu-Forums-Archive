---
title: "Incorrect parameter error"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by aprillia99 on 2009-12-22
im working with vista and samba (ubuntu) on ubuntu i can see my window files and acess them but i cant access my ubuntu files from windows. when i try to open them from the network tab i get  a "\\ is not accessible the parameter is incorrect" error.

here a screen shot of the erroe message in vista 
[http://tinypic.com/r/iw3h3q/6](http://tinypic.com/r/iw3h3q/6)
any ideas on what to do here some info



kyle@kyle-Server-Ubuntu:~$ net usershare info
[hand]
path=/home/kyle/Pictures/hand
comment=
usershare_acl=Everyone:F
guest_ok=y

kyle@kyle-Server-Ubuntu:~$ sudo netshare info
sudo: netshare: command not found
kyle@kyle-Server-Ubuntu:~$ sudo net usershare info
kyle@kyle-Server-Ubuntu:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    passdb backend = tdbsam
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
    invalid users = root

[homes]
    comment = Home Directories
    valid users = %S
    read only = No

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

---

