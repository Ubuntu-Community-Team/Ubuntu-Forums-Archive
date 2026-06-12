---
title: "Can't seem to make samba work..."
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by Major_Kong on 2008-07-28
I've been trying to make samba work, but for some reason it's b0rk3d.

Here's the smb.conf:

```
[global]
; General server settings
;netbios name = none

workgroup = WORKGROUP
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

wins support = yes

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
;valid users = %S
;create mode = 0600
;directory mode = 0755
;browseable = no
;read only = no
;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
;path = /var/lib/samba/netlogon
;admin users = Administrator
;valid users = %U
;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
;path = /var/lib/samba/profiles
;valid users = %U
;create mode = 0600
;directory mode = 0700
;writeable = yes
;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
path = /var/lib/samba/printers
browseable = yes
guest ok = yes
read only = yes
write list = root
create mask = 0664
directory mask = 0775

[printers]
path = /tmp
printable = yes
guest ok = yes
browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
;path = /media/cdrom
;browseable = yes
;read only = yes
;guest ok = yes



[teste]
valid users = "my_username"
writeable = yes
path = /media
allow hosts = 192.168.1.
```

And if i run smbtree, i get no output...

Any ideas ?

---

### Post by Iowan on 2008-07-28
May need to define "b0rk3d"... 
Try **ps ax |grep mbd** to verify Samba component(s) are running.  Samba-client comes installed by default, but Samba-server must be installed.  
You can also "Run **testparm** to check that there are no basic syntactic errors. "

---

### Post by Major_Kong on 2008-07-29
> **Iowan said:**
> May need to define "b0rk3d"... 
Try **ps ax |grep mbd** to verify Samba component(s) are running.  Samba-client comes installed by default, but Samba-server must be installed.  
You can also "Run **testparm** to check that there are no basic syntactic errors. "

b0rk3d, as in doesn't work.

Already ran testparm, there are no syntactic errors. And both the samba and samba-client packages are installed.

PS: From running ps ax | grep mbd i get:
```
 5881 ?        Ss     0:00 /usr/sbin/nmbd -D
 5882 ?        S      0:00 /usr/sbin/nmbd -D
 5884 ?        Ss     0:00 /usr/sbin/smbd -D
 5901 ?        S      0:00 /usr/sbin/smbd -D
14908 pts/1    R+     0:00 grep mbd

```

---

### Post by linux6994 on 2008-07-29
Easy things to ensure that makes life nicer with samba are:

1. Ensure that security is set to share.
2. Install system-config-samba, use it for adding shares (System > Administration > Samba)
3. Ensure that the workgroup name is spelled the same on all PCs including upper or lower case.

---

### Post by Major_Kong on 2008-07-30
Just to make sure... but the program (system-config-samba) does work, and doesn't make things worse, right ?

---

### Post by superprash2003 on 2008-07-30
well few more things to try..
ensure that samba is on type sudo /etc/init.d/samba restart in the terminal.Then see if the pc you are trying to connect from is able to ping the samba machine.. also in the terminal type nautilus smb://127.0.0.1 and see if you are able to see your shares

---

