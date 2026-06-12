---
title: "Samba permissions problem connecting from Android device"
date: 2013-12-01
forum: Networking &amp; Wireless
---

### Post by mogdad on 2013-12-01
Hi,

I think I'm the latest in a long line of people to get caught out by Samba permissions. Just can't figure our what is wrong though.

I'm trying to connect to my desktop machine running 12.04LTS from Android (a phone and a tablet both running jelly bean). When I try to connect from Android using ES File Explorer I can see the desktop and the directory I want to share (/home/user1/Videos) but when I try to open it the message is "login fails. This may be caused by - The account has no permissions".

One recent discovery that seems to narrow down the problem is that I have also set up a new sharing director /srv/samba/share and this works no problem - I can view contents and read files.

I've not set up separate samba users or anything like that yet - just aiming for guest/anonymous login at this point to get things working. This is what I get from 'testparm /etc/samba/smb.conf':

```
[global]
    server string = %h server (Samba, Ubuntu)
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

[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    create mask = 0755
    guest ok = Yes

[videos]
    comment = Videos
    path = /home/user1/Videos
    create mask = 0755
    guest ok = Yes
```

ls -l for the two directories gives:
[share]
drwxr-xr-x 2 nobody nogroup 4096 Dec  1 19:01 share

[videos]
drwxr-xr-x  7 user1 user1   4096 Oct 13 18:07 Videos

The only other difference I can think of is that /home is on a separate hard disk.

I've been through the samba troubleshooting and various other similar forum queries but still not getting anywhere so it would be great if anyone has any suggestions! Thanks.

---

