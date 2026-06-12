---
title: "windows cannot access my ubuntu shared files: samba"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by arju305 on 2010-10-24
Guys I am having a problem with samba.
firstly i installed it :
$sudo apt-get install samba
$sudo apt-get install system-config-samba
then i restarted the server.
from administrator-> samba i customized it for access to every one.
I found that.
from my ubuntu, I could access windows 7
but from windows 7 I cannot access ubuntu.
need your help.
Thanking you in advance.
*************************************

arjan@arjan-MS-7514:~$ testparm -sp
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[Myshare]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Pictures]"
Processing section "[Downloads]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = Ubuntu Server
    security = SHARE
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

[Myshare]
    comment = Myshare
    path = /myshare
    read only = No
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Pictures]
    path = /home/arjan/Pictures
    read only = No
    guest ok = Yes

[Downloads]
    path = /home/arjan/Downloads
    read only = No
    guest ok = Yes



********************************************************************
[music]
path=/home/arjan/Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

[sharing]
path=/home/arjan/Pictures/sharing
comment=
usershare_acl=Everyone:F,
guest_ok=y
*****************************************

---

