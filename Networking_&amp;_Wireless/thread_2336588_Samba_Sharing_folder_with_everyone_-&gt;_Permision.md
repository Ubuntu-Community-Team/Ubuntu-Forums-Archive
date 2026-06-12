---
title: "Samba: Sharing folder with everyone -&gt; Permision denied"
date: 2016-09-09
forum: Networking &amp; Wireless
---

### Post by arcanto2 on 2016-09-09
Hi all,

I'm trying to share a folder to everyone on the LAN. 

I have Lubuntu 16.04, and installed packages (with all dependencies) Samba & system-config-samba

I tried some manual editing in the smb.config, and also some editing with the gui... without success.

The samba service starts ok. If I access through localhost or even from a remote windows desktop I'm able to see the folder I shared. 
But as soon as I try to open the folder to see the contents, I'm getting permission denied.

I applied chmod -R 777 to the folder... 

I'm guessing I have something wrong with the samba configuration...

This is my /etc/samba/smb.conf :
```

[global]
    workgroup = workgroup
    server string = %h server (Samba, Ubuntu)
    dns proxy = no
    log file = /var/log/samba/log.%m
    max log size = 1000
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    server role = standalone server
    obey pam restrictions = yes
    unix password sync = yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    pam password change = yes
    map to guest = bad user
    usershare allow guests = yes
    create mask = 0777
    username map = /etc/samba/smbusers
    security = user
    guest ok = yes

[printers]
    comment = All Printers
    browseable = no
    path = /var/spool/samba
    printable = yes
    create mask = 0700

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Shared]
    path = /disk2/Shared
    writeable = yes
    guest ok = yes
    force directory mode = 2770
    comment = shared

```

I only care to share the /disk2/Shared to everyone... 

Any help would be highly appreciated.

Thanks !

---

### Post by TheFu on 2016-09-09
Did you restart samba service?
What do the samba log files say?

---

