---
title: "Sharing My Printer with Windows via Samba/Cups"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by Das Oracle on 2007-02-10
I have a printer that is all nice and working in linux and I am trying to share it over my network to a few MS computers. I had a look at this post [http://ubuntuforums.org/showthread.php?p=2130577#post2130577]("http://ubuntuforums.org/showthread.php?p=2130577#post2130577") of who had a similar problem to mine. At first windows would see my printer but some permissions would not allow the machine to connect remotely to the printer. After a bit of tweaking I thought to have solved that, however now the printer doesn't show up on Windows computers at all. Here are my config files and hopefully someone can help

smb.conf:
```
#======================= Global Settings =======================

[global]
## Browsing/Identification ###
   workgroup = MSHOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

   wins support = no

   wins server = 
   dns proxy = no
   name resolve order = lmhosts host wins bcast
#### Networking ####
;   interfaces = lo eth0
;   bind interfaces only = true
#### Debugging/Accounting ####
   log file = /var/log/samba/log.%m
   max log size = 1000
;   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
####### Authentication #######
   security = SHARE
   username map = /etc/samba/smbusers
   map to guest = Bad User
   encrypt passwords = true
   null passwords = true
   passdb backend = tdbsam guest
   obey pam restrictions = yes
;   guest account = nobody
   invalid users = root
;   unix password sync = no
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   client user spnego = no
;   pam password change = no
########## Domains ###########
;   domain logons = yes
;   logon path = \\%N\profiles\%U
;   logon path = \\%N\%U\profile
;   logon drive = H:
;   logon home = \\%N\%U
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
########## Printing ##########

   load printers = no

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups
   dos filetimes = yes
   display charset = iso8859-1
   unix charset = iso8859-1
   preserve case = yes
   case sensitive = no
   short preserve case = yes
   os level = 20
;   printer admin = @lpadmin


############ Misc ############

;   include = /home/samba/etc/smb.conf.%m

   socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================
[Jamey's Storage]
;   comment = Home Directories
   public = yes
   path = /home/jamey/Storage
   browseable = yes
   available = yes
   guest ok = yes
   writable = yes
   max connections = 0

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700
   printcap name = /etc/printcap
   print command = /usr/bin/lpr -P%p -r %s
   printing = cups

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
  path = /var/lib/samba/printers
  browseable = yes
  guest ok = yes
  read only = yes
  write list = root
  create mask = 0664
  directory mask = 0775
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




```




cupsd.conf:

```
#======================= Global Settings =======================

[global]
## Browsing/Identification ###
   workgroup = MSHOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

;   wins support = no

   wins server = 
   dns proxy = no
   name resolve order = lmhosts host wins bcast

#### Networking ####
   interfaces = lo eth0
;   bind interfaces only = true



#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
;   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######
   security = SHARE
   map to guest = Bad User
   encrypt passwords = true
   null passwords = true
   passdb backend = tdbsam guest
   obey pam restrictions = yes
;   guest account = nobody
   invalid users = root
;   unix password sync = no
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   client user spnego = no
;   pam password change = no

########## Domains ###########
;   domain logons = yes
;   logon path = \\%N\profiles\%U
;   logon path = \\%N\%U\profile
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = no

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups
   dos filetimes = yes
   display charset = iso8859-1
   unix charset = iso8859-1
   preserve case = yes
   case sensitive = no
   short preserve case = yes
   os level = 20
;   printer admin = @lpadmin


############ Misc ############

;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================
[home]
;   comment = Home Directories
   public = yes
   path = /home
   browseable = yes
   available = yes
   guest ok = yes
   writable = yes
   max connections = 0

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

wins support = no
[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700
   printcap name = /etc/printcap
   print command = /usr/bin/lpr -P%p -r %s
   printing = cups

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
  path = /var/lib/samba/printers
  browseable = yes
  guest ok = yes
  read only = yes
  write list = root
  create mask = 0664
  directory mask = 0775
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
```



printers.conf:

```
# Printer configuration file for CUPS v1.2.4
# Written by cupsd on 2007-02-09 16:18
<Printer DeskJet-D1300>
Info Bitchin HP
Location 
DeviceURI usb://HP/Deskjet%20D1300%20series?serial=CN69F1Q4T204SN
State Idle
StateTime 1171055906
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
AllowUser samba            *note* was suggested by a user in the link i used.
</Printer>
```

---

### Post by Das Oracle on 2007-02-10
ok, so i got it to show back up in windows by changing 'load printers' to yes but I am still having the 'access denied' issue

---

### Post by Das Oracle on 2007-02-11
I'm wondering, because it prints partially (mainly html only) would it be from me manually installing the drivers on the xp machine? Is there a way to have xp drivers for my printer on the linux machine and push them to the xp machine? I believe so but not really sure howto or how this works.

---

