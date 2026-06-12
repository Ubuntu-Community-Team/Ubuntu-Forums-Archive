---
title: "Samba is not working, cannot authenticate from laptop or other desktop..."
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by rockmanac on 2007-08-08
**[COLOR="Red"]Edit: Never mind... Apparently, to use the account I created at install, I had to comment out " invalid users = root"[/COLOR]**

Hey all,

I just wiped and reloaded Kubuntu onto my desktop machine (thereby killing what I had left of a windows partition). 

Now.. For some reason, now that I have rebuilt the machine, re-set up Samba, etc., I am now no longer able to connect from either my Powerbook or another Kubuntu machine.

I've shared my drives, added myself as a user with smbpasswd -a *username* but my clients, while they can see the server, still cannot authenticate to my shares. 

I've checked my logs and found the following:
```
[2007/08/08 10:41:31, 0] smbd/service.c:make_connection_snum(849)
  Can't become connected user!
[2007/08/08 10:41:31, 0] smbd/service.c:make_connection_snum(849)
  Can't become connected user!
[2007/08/08 10:41:40, 0] smbd/service.c:make_connection_snum(849)
  Can't become connected user!
```

I'm not sure what to make of that.  Here's the output of my smb.conf file:

```

[global]
workgroup = BUFFYVERSE
server string = %h server (Samba, Ubuntu)
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d


####### Authentication #######

security = user
username map = /etc/samba/smbusers
encrypt passwords = yes
passdb backend = tdbsam
obey pam restrictions = yes

; guest account = nobody
 invalid users = root
; unix password sync = no

passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
; pam password change = no



########## Printing ##########

load printers = yes

printing = cups
printcap name = cups

; printer admin = @lpadmin


############ Misc ############


# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY 
restrict anonymous = no
domain master = no
preferred master = no
max protocol = NT
acl compatibility = winnt
ldap ssl = No
server signing = Auto


#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = yes
   valid users = %S
   writable = yes
   create mask = 0600
   directory mask = 0700


[printers]
comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
create mask = 0700

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers

[exthd]
path = /media/sdb1 
browsable = yes
available = yes
writable = yes
public = yes

```

Any help is appreciated!

-Adam

---

