---
title: "No Domain Logins for Samba"
date: 2022-01-19
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2022-01-19
I have been having problems with my Domain Controller, it has problems with a file share located on it. Sometimes some computers cannot access a share on it. I thought this was because when I ping the server by name it responds with a IPv6 address. When I access the server by IPv4 I can mount the share and everything works. So I started fooling around with my smb.conf file  to disable IPv6 access and now I have some commuters where some users which can't log into the Domain. I get a domain unavailable error.

All Windows clients are Windows 10 the Server is Ubuntu 18.04 smb versions is Version 4.7.6-Ubuntu running as an NT4 style domain.

Testparm doesn't find anything wrong with my globals section, here is the output;

```
# Global parameters
[global]
        bind interfaces only = Yes
        client min protocol = NT1
        dns proxy = No
        domain logons = Yes
        domain master = Yes
        interfaces = eth1 lo 192.168.1.1
        ldap ssl = no
        log file = /var/log/samba/log.%m
        logging = syslog@0 file@4
        logon drive = U:
        logon home = \\REMUS\%U
        logon path = \\REMUS\profiles\%U
        max log size = 1000
        name resolve order = wins host bcast
        obey pam restrictions = Yes
        os level = 64
        panic action = /usr/share/samba/panic-action %d
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        passwd program = /usr/bin/passwd %u
        preferred master = Yes
        security = USER
        server min protocol = NT1
        server string = Egroupware Server (Samba,Ubuntu)
        time server = Yes
        wins support = Yes
        workgroup = ORLEANS
        idmap config * : range = 10000-20000
        idmap config * : backend = tdb
        admin users = root administrator
        create mask = 0664
        directory mask = 0775
        hosts allow = 192.168.1.0/255.255.255.0

```

This smb.conf has been working for a long time. This time I mostly added

      ```
bind interfaces only = Yes

```
and edited the

  ```
  interfaces = eth1 lo 192.168.1.1
```

From

   ```
  interfaces = enp1s0 192.168.1.0/24

```
Which I think was wrong because there is no interface enp1s0, not sure where that came from or why it's there unless the previous version of Ubuntu had a different name for the interface..

---

