---
title: "Samba Access Denied"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by layer_923 on 2007-05-18
I have a file server in small office and just want it as a "dumping Ground" 

What i want is a full read & Write access to users on shared folder, at the moment i see it and i can map to it but wont let me put any files from a XP machine, At the moment it keeps saying access denied, i also don't want my users having to input a password at any stage.

cheers in advance

#======================= Global Settings =======================

[global]

workgroup = ******

server string = %h server (Samba, Ubuntu)

wins support = no
dns proxy = no

#### Debugging/Accounting ####

log file = /var/log/samba/log.%m

max log size = 1000

syslog = 0

panic action = /usr/share/samba/panic-action %d


####### Authentication #######

security = share

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
; passdb backend = tdbsam

obey pam restrictions = yes

guest account = nobody
invalid users = root

# passdb is changed.
; unix password sync = no


; passwd program = /usr/bin/passwd %u
; passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# 'passwd program'. The default is 'no'.
; pam password change = no


############ Misc ############

; include = /home/samba/etc/smb.conf.%m

socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

#======================= Share Definitions =======================

;[homes]
; comment = Home Directories
browseable = yes

; valid users = %S


writable = yes


create mask = 0777


directory mask = 0777

;[netlogon]
; comment = Network Logon Service
; path = /home/samba/netlogon
; guest ok = yes
; writable = no
; share modes = no

;[profiles]
; comment = Users profiles
; path = /home/samba/profiles
; guest ok = no
; browseable = no
; create mask = 0600
; directory mask = 0700

wins support = no


[Samba]
comment = Public
path = /home/*******/Samba
available = yes
read only = no
browsable = yes
public = yes
writable = yes
create mask = 777
directory mask = 777
force user = nobody
force group = nogroup

---

### Post by noMScraig on 2007-05-25
yep...have the same problem here...still looking through the threads for some shred of help.

-c

---

