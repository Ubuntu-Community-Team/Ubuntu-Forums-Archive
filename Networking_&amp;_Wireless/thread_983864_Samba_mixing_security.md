---
title: "Samba mixing security"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by danone on 2008-11-16
Hi together,

I am faced with the problem, that I want for one thing a security = "share" level but for another one I want security = "users". So what I want to achieve is, that everybody can see all shares without getting a password prompt (at least on windows). But accessing a "private" share like "Data2" in my smb.conf should result in an authentication prompt.

[global]
        workgroup = Test.LOCAL
        netbios name = NSLU2
        server string = %h server (Samba %v)
        map to guest = Bad User
        null passwords = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        create mask = 0700
        directory mask = 0700
        browseable = No

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[Data]
        comment = "My Data"
        path = /data/data
        read only = No
        force create mode = 0755
        force directory mode = 0755
        guest ok = Yes

[Exchange]
        comment = "Daten Exchange"
        path = /data/xchange
        read only = No
        force create mode = 0777
        force directory mode = 0777
        guest ok = Yes

[Data2]
        comment = "data"
        path = /data/data2
        valid users = neo
        read only = No


I have found a similar post in this forum and applied the suggestions made in this post. But I still get a password prompt on windows XP when I doulble click on the samba server. The strange thing is that I can enter anything for user and password and then i can see the shares. For "data2" I have to enter the correct username and password. But why do I still get the authentication dialog?

Thanks,
danone

---

