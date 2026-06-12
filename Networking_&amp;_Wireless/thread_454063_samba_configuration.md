---
title: "samba configuration"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by janascii on 2007-05-25
I have been trying to get samba working how I want it to.  I need some shares which are shared with "security =  share" while one that is private, probably "security = user".  My smb.conf is attached.

```
[global]
    netbios name = JANASCII-DESK
    server string = %h on Ubuntu
    workgroup = 411NORTH
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no


[Music]
    path = /media/media/Music
    browseable = yes
    read only = yes
    guest ok = yes

[Video]
    path = /media/media/Video
    browseable = yes
    read only = yes
    guest ok = yes

[Downloads]
    path = /media/media/Downloads
    browseable = yes
    read only = yes
    guest ok = yes

[ISOs]
    path = /media/media/ISOs
    browseable = yes
    read only = yes
    guest ok = yes

[My Stuff]
    path = /home/janascii
    browseable = yes
    read only = no
    guest ok = no
    force user = janascii
```

---

### Post by dmizer on 2007-05-25
well ... i don't see your smb.conf attached, but here's my smb.conf which accomplishes the same thing you wish to do:
```
#======================= Global Settings =======================
[global]
        name resolve order = hosts wins bcast
        announce version = 5.0
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        username map = /etc/samba/smbusers
        null passwords = true
        passdb backend = tdbsam
        wins support = no
        netbios name = ipc10512
        server string =
        ; printing = cups
        workgroup = i&f
        syslog only = yes
        ; printcap name = CUPS
        security = share
        syslog = 1
    ; General server settings

[E]
    path = /home/shared/common2
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = admin
    force group = admin

[kappa$]
    path = /home/shared/kappa
    browseable = no
    read only = no
    guest ok = no
    valid users = ipc10440
    create mask = 0644
    directory mask = 0755
    force user = admin
    force group = admin
```
where:
"E" is the name of the global share.
"admin" is the name of the user on the samba server.
"kappa$" is the name of the restricted share.
"ipc10440" is the name of the user on the windows machine with access to the restricted share.

---

