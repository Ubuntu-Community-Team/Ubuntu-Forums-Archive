---
title: "Samba: windows machine can't connect to printer"
date: 2014-10-20
forum: Networking &amp; Wireless
---

### Post by turboscrew on 2014-10-20
I have a printer shared with Samba, but a windows machine can't connect to it.
The disk shares work fine.
What's wrong?

```
root@JAAKUBUNTU:/etc/samba# smbtree
Enter root's password: 
WORKGROUP
        \\JAAKUBUNTU     
                \\JAAKUBUNTU\MP140-series       Canon MP140 series
                \\JAAKUBUNTU\print$             Printer Drivers
                \\JAAKUBUNTU\NEW VOLUME         Main share
                \\JAAKUBUNTU\SIIRTO             Aux share
                \\JAAKUBUNTU\IPC$               IPC Service (JAAKUBUNTU server (Samba, Ubuntu))




```

my smb.conf (removed comments to make it 'compact' enough to read):
```

[global]
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   wins support = yes
   dns proxy = no
   name resolve order = lmhosts wins bcast host
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   server role = standalone server
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = no
   public = yes
   create mask = 0777

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[NEW VOLUME]
   comment = Main share
   path = /mnt/newvol
   guest ok = yes
   browseable = yes
   create mask = 0777
   directory mask = 0777
   read only = no
   public = yes

[SIIRTO]
   comment = Aux share
   path = /mnt/siirto
   guest ok = yes
   browseable = yes
   create mask = 0777
   directory mask = 0777
   read only = no
   public = yes

```

---

### Post by turboscrew on 2014-10-20
Tried with IPP, abd the printer froze (Canon PIXMA MP140).
Oh, forgot: on the Kubuntu-machine itself, the printing works (from Kate).

---

