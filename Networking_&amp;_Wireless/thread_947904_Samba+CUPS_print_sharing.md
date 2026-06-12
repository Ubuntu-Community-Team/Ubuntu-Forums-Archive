---
title: "Samba+CUPS print sharing"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by xENO_ on 2008-10-14
I have recently upgraded to the Ubuntu Intrepid Ibex (8.10) beta, and despite every other feature I need working as well or better than Hardy, the sharing printers with Samba does not.

CUPS properly detected the printer, and can successfully print to it.  Samba properly detects the presence of CUPS, and requests a list of printers.  This causes nothing to appear in CUPS error log, even with CUPS in debug logging mode.

My samba configuration is as follows:
```

[global]
        workgroup = WORKGROUP
        server string = %h server
        wins support = Yes
        dns proxy = No
        name resolve order = lmhosts bcast
        bind interfaces only = Yes
        log file = /var/log/samba/log.%m
        max log size = 1000
        panic action = /usr/share/samba/panic-action %d
        security = user
        encrypt passwords = Yes
        obey pam restrictions = Yes
        unix password sync = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\spassword:* %n\n *password\supdated\ssuccessfully* .
        pam password change = Yes
        passdb backend = tdbsam
        invalid users = root
        admin users = <hidden>
        guest account = pcguest
        domain logons = No
        printcap name = cups
        socket options = TCP_NODELAY IPTOS_LOWDELAY
        interfaces = <hidden>
        null passwords = Yes
        printing = cups
        log level = 1
        client lanman auth = Yes
        client plaintext auth = Yes
        client NTLMv2 auth = Yes
        map to guest = bad user
        load printers = yes
        cups server = localhost:631

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No
        guest ok = yes

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
        read only = Yes
        guest ok = Yes
        write list = pcadmin

[public]
        comment = WiFi-accessable Files
        path = /srv/smb/public
        read only = No
        guest ok = Yes
        fstype = ext3

[internal]
        comment = WiFi-inaccessable Files
        path = /srv/smb/internal
        read only = No
        guest ok = Yes
        hosts allow = 127.0.0.0/8, 192.168.1.0/24
        fstype = ext3

```

My /etc/cups/cupsd.conf is the default.

---

### Post by cariboo on 2008-10-14
I had to enable the following lines in my /etc/samba/smb.conf in order for printing to work with samba and cups:

```
interfaces = lo eth0
```

and

```
bind interfaces only = true
```

Jim

---

### Post by xENO_ on 2008-10-14
I already have equivelant lines my configuration:
```
bind interfaces only = Yes
```
and
```
interfaces = 127.0.0.0/8 <hidden>
```

This isn't a new configuration, it's one that worked fine in Hardy Heron.

---

### Post by superprash2003 on 2008-10-15
have you tried connecting using its full address like \\x.x.x.x\printername

---

### Post by xENO_ on 2008-10-15
> have you tried connecting using its full address like \\x.x.x.x\printername

Yes.

When I try to enumerate the Samba printers using the RPC Client tool, I get:
```

<user>@<host>:~$ rpcclient -cenumprinters -N <netbios name> -q
No printers returned.

```

The following messages are appended to the CUPS log:
```
localhost - - [15/Oct/2008:16:18:54 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Printers successful-ok
localhost - - [15/Oct/2008:16:18:54 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok

```

lpstat -a yields:
```
<user>@<host>:~$ lpstat -a
HP_LaserJet_5MP accepting requests since Sat 11 Oct 2008 03:09:32 AM EDT
```

It almost certainly isn't an issue with the Windows machine, since I can connect and browse file shares, and if I connect with the admin account, install printer drivers; it doesn't see the printer because Samba doesn't.

The problem is clearly either with CUPS not responding with proper printer information, or Samba not reading it properly (or at all.)

---

