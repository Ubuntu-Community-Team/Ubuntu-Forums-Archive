---
title: "configuring network Printer"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by Papillonrus on 2007-10-22
I have windows XP installed on a file sharing print server.  Sharing photos, music and downloaded applications also a HP5510 all in oneder if it will work.  All joking aside how do I connect to the printer from 7.10 and schedule or print on demand.  I would like to get this lined out so I can get rid of windoze.  Thanks in advance, Darrell

---

### Post by Papillonrus on 2007-10-22
This is the printer I would like to print from by default.  A good clear walk thru would be great.  Thanks, Darrell

darrell@Dell-GX260:~$ smbclient -L SMITH -N
Connection to SMITH failed (Error NT_STATUS_BAD_NETWORK_NAME)
darrell@Dell-GX260:~$ smbclient -I 192.168.1.120 -L Smith -N
Domain=[SMITH] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        E$              Disk      Default share
        IPC$            IPC       Remote IPC
        File Storage~1  Disk      
        File Storage~2  Disk      
        print$          Disk      Printer Drivers
        hpoffice        Printer   hp officejet 5500 series
        F$              Disk      Default share
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
session request to SMITH failed (Called name not present)
Domain=[SMITH] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

---

