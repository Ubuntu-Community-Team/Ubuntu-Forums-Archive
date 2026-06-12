---
title: "samba server not accessible form Wan (no ip limitations)"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by ghedda on 2007-07-19
Hi there. Firsts steps on Samba server. I succesfully setup samba with user autenthincation.
Now I am testing it from windows clients only.
It works fine from LAN but I'm unable to connect from WAN. So i checked:

- smb.conf not to allow only lan hosts (even adding "allow host = all")
- firewall configuration (137, 138 UDP ports open, 139, 455 TCP ports open)
- dyndns configuration works fine (apache)

so what's wrong? maybe the path string wich I'm trying to connect to?
LAN: \\myserver\
WAN: \\myserver.dyndns.org\

some configuration..

```

[global]
   workgroup = MSHOME
   server string = %h (Samba, Ubuntu)
   wins support = true

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true

   log file = /var/log/samba/log.%m
   max log size = 1000

;   syslog only = no

   syslog = 0

   panic action = /usr/share/samba/panic-action %d

hosts allow = all

   security = user

   encrypt passwords = true

   passdb backend = tdbsam

   obey pam restrictions = true

;   guest account = nobody
   invalid users = root

;   unix password sync = no

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

;   pam password change = no

;   domain logons = yes
;   logon path = \\%N\profiles\%U

;   logon path = \\%N\%U\profile

;   logon drive = H:
;   logon home = \\%N\%U

;   logon script = logon.cmd

; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

;   load printers = yes

;   printing = bsd
;   printcap name = /etc/printcap

;   printing = cups
;   printcap name = cups

;   printer admin = @lpadmin

;   include = /home/samba/etc/smb.conf.%m

   socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=8192 SO_SNDBUF=8192

;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

;   domain master = auto

;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

# mia condivisione
[File Condivisi]
  comment = Condivisione di Samba
  path = /home/samba
  public = yes
  writable = yes
  valid users = tutti    # n.b. è il nome di un utente di sistema reale
  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup

```

thanks

---

### Post by ghedda on 2007-07-20
may be I need to set up a directory server?

---

### Post by AKA3Toes on 2007-07-24
[FONT="Times New Roman"][SIZE="2"][COLOR="DarkRed"][I]---I've found a lot of posts regarding bugs, errors, HELP!, etc regarding WAN, but to be perfectly honest with you, I think the whole SAMBA settings scenario is a little too complicated for desktop. Server application yes, but people who are running desktop are running desktop for a reason. Now, I can agree with teaching people what every setting is while they set it up, but there should be a user-friendly program (SAMbuddy or supin') that walks you through, step by step and asks you to input in boxes, the information needed to configure your networking solution.

---FWIW, I am trying to set up my workstation's available storage as networked accessible storage for an XP laptop and it has me wondering if I should "un-comment" certain areas. I'm not about testing commands on my systems and I don't know if changing/un-commenting something would leave me vulnerable or not.

---Just a thought cause I am not the least computer savy user and I am sure thousands of others who are presently under me will be or are having problems in this area...

... or maybe I'm just reading the lament descriptions wrong.[/I][/COLOR][/SIZE][/FONT]

---

