---
title: "Trouble with local samba share with windows guest"
date: 2016-08-28
forum: Networking &amp; Wireless
---

### Post by hermes5 on 2016-08-28
Hi everyone,

I recently followed an online video guide [here]("https://www.youtube.com/watch?v=zTujwRSsIBw") to get a local share with my windows guest up and running. I succeeded after some tinkering with permissions, but then all of a sudden it just stopped working. Now my windows 8 guest cannot even see my host through the inbuilt Network folder. I'm using a kvm/qemu virt setup.

Here is the relevant parts of my smb.conf file 

```

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

[share]
    comment = samba share for windows guest
    path = /path/to/share
    public = yes
    writable = yes

```

Result of sudo pdbedit -L

```
user:1000:user
```

Result of testparm

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[share]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions

# Global parameters
[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
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
    idmap config * : backend = tdb


[share]
    comment = samba share for windows guest
    path = /path/to/share
    read only = No
    guest ok = Yes


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


```

I have attempted fixing the issue with an old smb.conf file, turning off my firewall on both ends, but to no avail. I'm perplexed as to how I got it working originally and then it just stopped working all of a sudden. If anyone has an experience with similar issues I would really appreciate an advice that could be given, thanks.

EDIT - I found a workaround, creating a shortcut directly to my i.p address. I would like to fix whatever the problem is but until it breaks again I'm happy.

---

### Post by mook765 on 2016-08-28
> path = /path/to/share
Here you have to enter the path to the folder you are going to share.
For example: you want to share the folder "Public" which is in your home directory (~/Public)
Then you would have to set it to
```
path = ~/Public
```

---

### Post by SeijiSensei on 2016-08-28
Is the virtual host configured to use a "bridged" network adapter, one that appears directly on the same network the host itself is on?  The symptoms suggest it was originally configured that way, but now it's not.  What IP address does the virtual host have?  Is it one on the main network, or not?

---

