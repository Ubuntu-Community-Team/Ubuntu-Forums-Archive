---
title: "samba will not authenticate"
date: 2024-11-05
forum: Networking &amp; Wireless
---

### Post by bobdale on 2024-11-05
I installed samba 4.19.5-Ubuntu on Ubuntu Desktop 24.04.1 (box 1).

I can NOT connect to any of the shares - even on the local machine. I continually get the "Authentication Required" dialog. I get the same response when trying to connect from Windows 11 (Box 2), Windows 10 (Box 3) and another Ubuntu Desktop 24.04.1 (Box 4).

UFW is enabled with samba open to IPv4 & IPv6

I have purged and reinstalled samba.

Any hints on what to try next?

Thanks in advance

Bob

---

### Post by Morbius1 on 2024-11-05
Why not tell the folks here how samba is configured so they don't have to guess.

Please post the out put of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by bobdale on 2024-11-05
testparm -s
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed by GnuTLS (e.g. NTLM as a compatibility fallback)

Server role: ROLE_STANDALONE

# Global parameters
[global]
        log file = /var/log/samba/log.%m
        logging = file
        map to guest = Bad User
        max log size = 1000
        obey pam restrictions = Yes
        pam password change = Yes
        panic action = /usr/share/samba/panic-action %d
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        passwd program = /usr/bin/passwd %u
        server role = standalone server
        server string = %h server
        unix password sync = Yes
        usershare allow guests = Yes
        idmap config * : backend = tdb


[printers]
        browseable = No
        comment = All Printers
        create mask = 0700
        path = /var/tmp
        printable = Yes


[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers


[Music]
        comment = Music
        path = /home/robert-dale/Music
        read only = No


[RED-BU]
        comment = RED HP sync BU
        path = /media/Hitach1_4GB/RED_HP-23
        read only = No


[hitach-copy]
        create mask = 0777
        directory mask = 0777
        path = /home/robert-dale/hitach-copy
        read only = No

net usershare info --long comes back blank (empty) 

I have been using Webmin to look at the server. It lists samba users and groups. Why don't i see anything in /var/lib/samba/usershares/

Sorry, my forehead is sore from beating it on a brick wall over this.

---

### Post by bobdale on 2024-11-05
I tried to add a user with sudo adduser --no-create-home --disabled-password --disabled-login sambausernam
No joy it returns that the user already exists

---

### Post by Morbius1 on 2024-11-05
> 
[Music]
comment = Music
path = /home/robert-dale/Music
read only = No

[hitach-copy]
create mask = 0777
directory mask = 0777
path = /home/robert-dale/hitach-copy
read only = No

The only user that is going to be able to access these shares is robert-dale because of the permissions on the /home/robert-dale folder.

If you plan on accessing them as robert-dale from the client you need to add that user to the samba password database:
```
sudo smbpasswd -a robert-dale
```

If you want multiple registered user to have access you need to add them to smbpasswd as well but you need to adjust your share definitions to make them all look like robert-dale:
> 
[Music]
comment = Music
path = /home/robert-dale/Music
**[COLOR="#FF0000"]force user = robert-dale[/COLOR]**
read only = No

[hitach-copy]
create mask = 0777
directory mask = 0777
path = /home/robert-dale/hitach-copy
**[COLOR="#FF0000"]force user = robert-dale[/COLOR]**
read only = No

As for this one I don't know:
> [RED-BU]
comment = RED HP sync BU
path = /media/Hitach1_4GB/RED_HP-23
read only = No
Does robert-dale have access to the path?

---

### Post by bobdale on 2024-11-05
Thank you!

I added robert-dale and now have access. Life will continue now.

Have a great evening.

---

