---
title: "Network Neighborhood doesn't display Samba Shares/Server with 10.04"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by AndyInNYC on 2010-08-02
I just upgraded from 7.x to 10.04 64 bit server.
Samba works.
My problem is the following.  From a Windows PC, I can

a) connect to a network share with \\Server\ShareName
b) in the run box type: \\Server\ShareName

and all is well.

What I can't seem to do is 'see' the Server and shares under Network Neighborhood as I could with 7.x.

My smb.conf file reads:

# Samba config file created using SWAT
# from UNKNOWN (192.168.40.43)
# Date: 2010/07/19 18:31:38

[global]
        server string = %h server (ASB Server #1)
        workgroup = WORKGROUP
;       security = user
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
        username map = /etc/samba/smbusers

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
;       valid users = server stephanie andrew
[Homefiles]
        path = /media/RAID/DATASHARE/DataCenter
        read only = No
        guest ok = Yes
        writeable = Yes
        browseable = Yes
;       valid users = server stephanie andrew
[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No
        browsable = No


There are no printers attached (nor will there be) on the server.
I don't have user level security enabled.  I'd like to get the browsing working first and solve one problem at a time.

Thanks

Andrew

---

### Post by CharlesA on 2010-08-02
Is nmbd running?

```
sudo service nmbd status
```

Also, what version of Windows are you using?

---

### Post by AndyInNYC on 2010-08-02
sudo service nmbd status returns:

nmbd start/running, process 1001

Windows machines vary - Windows 2000, XP and Vista.
Workgroup is Workgroup

nothing has changed on the Windows' machines side.

Andrew

---

### Post by CharlesA on 2010-08-02
I don't know then. I've got mine set up the same way and Windows sees it fine.

Does testparm return any errors?

This is my smb.conf file:

```
[global]
        log file = /var/log/samba/log.%m
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        obey pam restrictions = yes
        map to guest = bad user
        encrypt passwords = true
        passwd program = /usr/bin/passwd %u
        passdb backend = tdbsam
        dns proxy = no
        server string =
        unix password sync = yes
        workgroup = ASGARD
        os level = 20
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        usershare allow guests = yes
        max log size = 1000
        pam password change = yes

[Charles]
        comment = Charles' Folder
        invalid users = clone,htpc
        create mode = 660
        path = /array/charles
        write list = charles
        directory mode = 770

```

---

