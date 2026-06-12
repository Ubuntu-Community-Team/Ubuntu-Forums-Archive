---
title: "No connection to Samba after 12.04 -&gt; 14.04 upgrade"
date: 2014-10-20
forum: Networking &amp; Wireless
---

### Post by GrayJack on 2014-10-20
Dear Sirs!

I'm expecting problem after upgrade to Ubuntu 14.04. Here is *testparam -s* output: 

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
WARNING: [printers] service MUST be printable!
WARNING: No path in service printers - making it unavailable!
NOTE: Service printers is flagged unavailable.
Processing section "[print$]"
WARNING: No path in service print$ - making it unavailable!
NOTE: Service print$ is flagged unavailable.
Processing section "[Share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        workgroup = OFFICE
        netbios name = SERVER
        server string = Server
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        username map = /etc/samba/smbusers
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = lmhosts, host, wins, bcast
        dns proxy = No
        wins server = 192.168.61.1
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb
        create mask = 00
        directory mask = 00

[printers]
        printable = Yes
        print ok = Yes
        browseable = No
        available = No

[print$]
        available = No

[Share]
        path = /home/intdon/Share
        read only = No
        create mask = 0677
        directory mask = 0777
        guest ok = Yes
        hosts allow = 192.168.61.
        hosts deny = ALL
```

There is a small network 192.168.61.0/255.255.255.0 with Windows 7  workstations. They should be able to connect to Share folder at Ubuntu  with read and write permissions. And they did it - right before update.  As for now they could find "Server" within network, but cannot connect  to it - error code 0&#1093;80070035 - "network path was not found".

Commenting "hosts allow" and "hosts deny" just for testing did not solve the problem.

Please advise how to fix it.

---

