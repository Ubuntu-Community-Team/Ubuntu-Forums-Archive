---
title: "Samba Shares are now read-only from client machines"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by AndyInNYC on 2010-07-24
Using 10.04 64 bit server edition.

All fine until this morning.

Shares show up under Windows, are browseable, openable, etc.
Can't be saved.

smb.conf looks like this now (which strikes me as different than it was when I set up the machine)

I'm not even using passwords right now (I was under 7.1 on the same array, but I'm using the same admin name, etc.).  Everything worked perfectly yesterday, so it's not a change from me.


# Samba config file created using SWAT
# from UNKNOWN (192.168.40.43)
# Date: 2010/07/19 18:31:38

[global]
        server string = %h server (ASB Server #1)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *$
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No
        browsable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[DataStore]
        path = /media/RAID
        read only = No
        guest ok = Yes
        writeable = Yes
        browseable = Yes

[Homefiles]
        path = /media/RAID/DATASHARE/DataCenter
        read only = No
        guest ok = Yes
        writeable = Yes
        browseable = Yes

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No
        browsable = No



Clearly this is a huge problem for me <g>.  All help appreciated.

Andrew

---

### Post by AndyInNYC on 2010-07-24
Additional piece of info:

If I use putty and access the server share /media/RAID/DATASHARE
I *can* copy files on the drive.

It appears that Samba/config is broken, not actual access to the RAID array, etc.

Andrew

---

