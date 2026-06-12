---
title: "Ubuntu 14.04 Samba 4 ADDC Can't Map Drives to Shares on Windows"
date: 2014-05-28
forum: Networking &amp; Wireless
---

### Post by Scott_Dawson on 2014-05-28
Hello,

I have set up an AD DC using Ubuntu 14.04 and Samba 4.  I have the following in my smb.conf file:
# Global parameters
[global]
        workgroup = OPOSLTD
        realm = oposltd.local
        netbios name = OPOSDOMAIN
        server role = active directory domain controller
        dns forwarder = 8.8.8.8
        encrypt passwords = yes
        smb passwd file = /etc/smbpasswd
[netlogon]
        path = /usr/local/samba/var/locks/sysvol/oposltd.local/scripts
        read only = No
[sysvol]
        path = /usr/local/samba/var/locks/sysvol
        read only = No
[homes]
        root preexec = echo hello >> /Users/test.log
        comment = Home Directories
        path = /Users/sdawson
        read only = no
        browseable = yes
        writable = yes
        create mode = 0600

I am trying to map to the "homes" share from windows 8 and I am getting a response saying that the drive cannot be found and to check the spelling.  The windows 8 machine is a member of the domain and I am logged in as a domain user.  Am I missing something obvious here?

Thanks,

Scott.

---

