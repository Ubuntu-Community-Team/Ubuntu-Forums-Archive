---
title: "Samba problems"
date: 2014-06-28
forum: Networking &amp; Wireless
---

### Post by Owain_Parry on 2014-06-28
Hey. I'm using Lubuntu and I'm having some trouble with Samba. On both my desktop and laptop I've marked my 'public' folder for sharing, will full access to everyone, and set their permissions so that anyone can view content, change content and access content. However when I try to access my desktop's public folder from my laptop (or visa versa) I get a dialouge saying 'Failed to mount Windows share: Permission denied'. What have I done wrong?

---

### Post by Owain_Parry on 2014-06-29
Bump

---

### Post by Morbius1 on 2014-06-29
Please post the output of the following command:
```
testparm -s
```
And this one since it doesn't sound like a Samba problem but a Linux permissions issue:
```
ls -dl $HOME/Public
```

---

### Post by Owain_Parry on 2014-06-29
testparam -s:

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Public]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
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

[Public]
    path = /home/owain/Public
    read only = No
    guest ok = Yes


```

ls -dl $HOME/Public:

```
drwxrwxrwx 2 owain owain 4096 Jun 28 21:33 /home/owain/Public
```

---

### Post by Morbius1 on 2014-06-29
Well, everything seems to be in order doesn't it?

Um ..... did you by any chance encrypt your home directory when you installed?

If you did this might work: Edit /etc/samba/smb.conf and add a line to the share definition:
> [Public]
    path = /home/owain/Public
    read only = No
    guest ok = Yes
    [COLOR=#0000cd]**force user = owain**[/COLOR]

Then restart samba:
```
sudo service smbd restart
```

You could also create a share outside your home directory like /home/Shared and share that directory.

---

### Post by Owain_Parry on 2014-06-29
Thanks, that solved the problem.

---

