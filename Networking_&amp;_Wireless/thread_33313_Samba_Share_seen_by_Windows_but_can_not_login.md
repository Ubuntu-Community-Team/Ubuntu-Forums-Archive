---
title: "Samba Share seen by Windows but can not login"
date: 2005-05-10
forum: Networking &amp; Wireless
---

### Post by blindpete on 2005-05-10
Hello and thank you for a wonderfull system!

I am a total newbie to linux and I'm unsure of what is not working.

I am attemting to set up a shared folder on the linux-ubunto box.  There are macs and winXP pro machines on the network.  I followed the instructions in:

[http://www.ubuntulinux.org/wiki/SettingUpSamba](http://www.ubuntulinux.org/wiki/SettingUpSamba) 

However when I attempt 
**[FONT=Courier New]sudo smbpasswd -a *username*[/FONT]**

It appears to work BUT when I finish the second password entry I get an error message:> 
Failed to initialise SAM_ACCOUNT for user *username*. Does this user exist in the UNIX password database ?
Failed to modify password entry for user *username*

I created the share via File Sharing UI.

I can see the linux-ubunto box in the network browser on XP, however I can not log in.  The account is always rejected.

[B]Here is my smb.conf:
[/B]> 
[FONT=Courier New][global]
   workgroup = Home
   server string = %h server (Samba, Ubuntu)
;   wins support = no
;   wins server = w.x.y.z
   dns proxy = no
;   name resolve order = lmhosts host wins bcast
   log file = /var/log/samba/log.%m
   max log size = 1000
;   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
;   security = user
   encrypt passwords = true
   passdb backend = tdbsam guest
   obey pam restrictions = yes
;   guest account = nobody
   invalid users = root
;   unix password sync = no
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
;   pam password change = no
;   load printers = yes
;   printing = bsd
;   printcap name = /etc/printcap
;   printing = cups
;   printcap name = cups
;   printer admin = @ntadmin
;   preserve case = yes
;   short preserve case = yes
;   include = /home/samba/etc/smb.conf.%m
   socket options = TCP_NODELAY
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   domain master = auto
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
wins support = no
[homes]
   comment = Home Directories
   browseable = yes
   writable = yes
   create mask = 0775
   directory mask = 0775
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no
[printers]
   comment = All Printers
   browseable = no
   path = /tmp
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
;   write list = root, @ntadmin
[Home]
path = /home/benstack
comment = Ben's Desktop
available = yes
browseable = yes
public = yes
writable = yes[/FONT]


Any ideas or links would be greatly appreciated.  

Thanks!
-Pete

---

### Post by joplass on 2005-05-10
[QUOTE=blindpete]Hello and thank you for a wonderfull system!

I am a total newbie to linux and I'm unsure of what is not working.

I am attemting to set up a shared folder on the linux-ubunto box.  There are macs and winXP pro machines on the network.  I followed the instructions in:

[http://www.ubuntulinux.org/wiki/SettingUpSamba](http://www.ubuntulinux.org/wiki/SettingUpSamba) 

However when I attempt 
**[FONT=Courier New]sudo smbpasswd -a *username*[/FONT]**

It appears to work BUT when I finish the second password entry I get an error message:

I created the share via File Sharing UI.

I can see the linux-ubunto box in the network browser on XP, however I can not log in.  The account is always rejected.

[B]Here is my smb.conf:
[/B]

Any ideas or links would be greatly appreciated.  

Thanks!
-Pete[/QUOTE]

Did you create user and password for samba?

---

### Post by blindpete on 2005-05-10
Yes,
However when I attempt 
**[FONT=Courier New]sudo smbpasswd -a *username*[/FONT]**

It appears to work BUT when I finish the second password entry I get an error message:> [FONT=Courier New][B]
Failed to initialise SAM_ACCOUNT for user *username*. Does this user exist in the UNIX password database ?
Failed to modify password entry for user *username*[/B][/FONT]

---

### Post by emperor on 2005-05-10
Did you create a user account on the Linux Server for the username in question?

---

### Post by blindpete on 2005-05-10
No I did not.  I'll do that now.
**Ding!** that did it thankyou!

---

