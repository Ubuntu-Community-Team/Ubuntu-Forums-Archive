---
title: "Samba: default group on shares"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by blackrax on 2008-07-25
Hi,

How do I assign a default group to my shares when allowing anonymous (password-less) logins? At the moment, the group defaults to *nogroup*. I've tried the force directive, but when it's in place I can't access the share.

*smb.conf* follows...
```

[global]
        workgroup = BLAKE
        server string = %h server (Samba, Ubuntu)
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
#       invalid users = root


[storage]
        comment = Nexus Storage
        path = /usr/storage
        browseable = yes
        create mode = 0660
        directory mode = 0770
#       force group = users
        read only = No
        guest ok = Yes
        hosts allow = 192.168.0.0/255.255.255.0


```

I've searched the forums and google:d, but I can't seem to get the right search criteria. Any help would be greatly appreciated.

Respectfully,
Adrian

---

### Post by Endwin on 2008-07-25
Is your security in the smb.conf file set to share?

security = share

---

