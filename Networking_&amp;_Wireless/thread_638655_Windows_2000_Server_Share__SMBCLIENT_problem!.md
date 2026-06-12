---
title: "Windows 2000 Server Share / SMBCLIENT problem!"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by sieber on 2007-12-12
Hello ppl!
I've go a problem accessing a windows 2000 server share with smbclient.
When I use the comand:

root@sdab165:~# smbclient -L 10.228.108.1
Password: 
Anonymous login successful
Domain=[GABAER] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        GC3$            Disk      
        GCDA$           Disk      
        SFIN$           Disk      
        SPADAER$        Disk      
        E$              Disk      Default share


So, this way its working fine... But if a try to authenticate using a user and pass I got some problems:

root@sdab165:~# smbclient -L 10.228.108.1 -U user%pass -W GABAER -d 3
lp_load: refreshing parameters
Initialising global parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface ip=10.140.48.165 bcast=10.140.51.255 nmask=255.255.252.0
Client started (version 3.0.26a).
Connecting to 10.228.108.1 at port 445
Doing spnego session setup (blob length=112)
got OID=1 2 840 48018 1 2 2
got OID=1 2 840 113554 1 2 2
got OID=1 2 840 113554 1 2 2 3
got OID=1 3 6 1 4 1 311 2 2 10
got principal=gabaer01$@GABAER.INTRAER
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
session setup failed: NT_STATUS_LOGON_FAILURE

Testparm result:
root@sdab165:~# testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
 
[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers

        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

The server is a windows 2k server with AD, and i tried to access the sharing with windows xp, and it works... This way, I know that the username and pass are valid.
That's all. I Hope somebody can help me!
Thank you!

---

