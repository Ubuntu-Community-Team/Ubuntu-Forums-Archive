---
title: "Samba configuration and file sharing issue"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by Palcrypt on 2008-01-07
I'm trying to share with my Mac. I've got the configuration file setup so that the workgroups match, but I can't get either machine to recognize the other. This is a major issue. Any help would be great. Just let me know what info you need me to post to be able to help.

---

### Post by Palcrypt on 2008-01-07
here's some info from my smb.conf file if that will help:

```

[global]
   workgroup = OURHOME
   server string = %h server (Samba, Ubuntu)
;   wins support = no
;   wins server = w.x.y.z
   dns proxy = no
;   name resolve order = lmhosts host wins bcast
;   interfaces = wlan0
;   bind interfaces only = false
   log file = /var/log/samba/log.%m
   max log size = 1000
;   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
;   guest account = nobody
   invalid users = root
;   unix password sync = no
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
;   pam password change = no
;   domain logons = yes
;   logon path = \\%N\profiles\%U
;   logon path = \\%N\%U\profile
;   logon drive = H:
;   logon home = \\%N\%U
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u


;[homes]
;   comment = Home Directories
;   browseable = no
;   valid users = %S
;   writable = no
;   create mask = 0700
;   directory mask = 0700

```

---

### Post by medic8ted on 2008-01-07
Try uncommenting line:
Name Resolve order

---

