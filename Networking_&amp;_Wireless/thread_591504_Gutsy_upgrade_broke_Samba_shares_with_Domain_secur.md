---
title: "Gutsy upgrade broke Samba shares with Domain security"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by WhateverFits on 2007-10-25
I have a system running Samba for a file server. It authenticates to my domain using "security = domain" and I could access the shares from my Windows XP desktop without any problems until I ran the Gutsy upgrade. I re-ran net rpc join and it was successful, but still no joy. My config file is the example with a few changes. It worked perfectly yesterday. I see no errors in any log files. I have no idea where to go from here. TIA

```

[global]
   workgroup = M
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
security = domain
password server = *
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   socket options = TCP_NODELAY
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
[Share]
comment = Shared files
path = /var/share
browseable = yes
writable = yes
[WWW]
comment = Web root
path = /var/www
browseable = yes
writable = yes
[homes]
        valid users = %S
        read only = No
        browseable = no
[trac]
        path = /usr/share/trac/templates/
        read only = No
[wptemplates]
        path = /usr/share/wordpress/wp-content
        read only = No
[wpfiles]
        path = /var/www/cl
        read only = No
[webserver]
        path = /var/www
        read only = No


```

---

### Post by bigbran_45 on 2007-10-26
I am also having the same problem.

After Upgrading to Gutsy today, I can no longer access my samba shares that used AD auth.

---

### Post by bgsneeze on 2007-10-26
I am also having this problem, if i run:

sudo net -d 10 ads testjoin

I seem to have a ldap timeout.

Could not open LDAP connection to ad.net.local:389: Illegal seek
Join to domain is not valid: Operations error.

---

### Post by TheOrangeRider on 2007-11-12
I'm also having this issue. Has anyone managed to figure out what's wrong?

Thanks!

---

### Post by TheOrangeRider on 2007-11-13
For me, specifying the username as

```
username=DOMAIN/username
```

AND also specifying the domain
```
domain=DOMAIN
```

worked :). Also, I'm actually fiddling with auto mounting shared folders via fstab, so I'm not sure how helpful my information is.

---

