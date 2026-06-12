---
title: "Sharing Local Printer through Samba"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by all4linux on 2007-01-30
I have set up my Ubuntu 6.10 machine to share files on a windows network, and configured it to NOT require passwords. I am now trying to share a local printer which is attached to the Ubuntu machine, with the other computers on the network. My smb.conf file is as follows:

```

#======================= Global Settings =======================

[global]
wins server =
wins support = no
netbios name = ecs755
workgroup=BERGER
server string=%h (Xandros Desktop)
announce version = 5.0
dns proxy=no
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

name resolve order=lmhosts host wins bcast 
log file=/var/log/samba/log.%m
max log size=1000
syslog=0
panic action=/usr/share/samba/panic-action %d

security=SHARE
null passwords = true
username map = /etc/samba/smbusers
encrypt passwords=true
passdb backend=tdbsam guest
obey pam restrictions=yes
invalid users=root
map to guest=Bad User
passwd program=/usr/bin/passwd %u
passwd chat=*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
client use spnego=no
load printers=no
printing=cups
printcap name=cups
dos filetimes=yes

display charset=iso8859-1
unix charset=iso8859-1
preserve case=yes
case sensitive=no
short preserve case=yes
os level=20
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[home]
  public=yes
  browseable=yes
  path=/home
  writeable=yes
  max connections=0
  available=yes
  guest ok = yes

[hda6]
path = /media/hda6
comment = The big backup drive
available = yes
browsable = yes
public = yes
writable = yes
  max connections=0
guest ok = yes
create mask = 0644
directory mask = 0755

```


In addition, I have edited the Listen directives in /etc/cups/cupsd.conf file as suggested in another thread to look like the following code:

```
#Listen localhost:631
Listen *:631
Listen /var/run/cups/cups.sock

```

When I go to any other machine on my network, Whether its a linux machine, or a windows 2000 machine, I am able to view my shared "hda6" drive, but I cannot view my shared printers. The printers folder doesn't show up on my other Linux machine, and on the Windows 2000 machine, the folder is there, but it is empty.

I am unable to use the wizard on my Linux machine (Xandros) to add any printer shared by the Ubuntu machine, and the same holds true for the W2K machine.

Before editing the /etc/cups/cupsd.conf file, I had gone to:
System - Administration - printers - Global Settings, and I had enabled "share Printers". Since editing cupsd.conf, That option is now greyed out.

Does anyone know how to fix my problem. I suspect it lies in the smb.conf file, but I don't know that much about configuring Samba to share printers.

---

### Post by all4linux on 2007-01-30
Excuse the error above... I posted the old smb.conf file. What I actually have in my smb.conf file follows:

```
#======================= Global Settings =======================

[global]
wins server =
wins support = no
netbios name = ecs755
workgroup=BERGER
server string=%h (Xandros Desktop)
announce version = 5.0
dns proxy=no
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

name resolve order=lmhosts host wins bcast 
log file=/var/log/samba/log.%m
max log size=1000
syslog=0
panic action=/usr/share/samba/panic-action %d

security=SHARE
null passwords = true
username map = /etc/samba/smbusers
encrypt passwords=true
passdb backend=tdbsam guest
obey pam restrictions=yes
invalid users=root
map to guest=Bad User
passwd program=/usr/bin/passwd %u
passwd chat=*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
client use spnego=no
load printers=no
printing=cups
printcap name=cups
dos filetimes=yes

display charset=iso8859-1
unix charset=iso8859-1
preserve case=yes
case sensitive=no
short preserve case=yes
os level=20
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

; NOTE: Here you may build a printer driver repository for
; Windows - Find this topic in another HOWTO
[print$]
  path = /var/lib/samba/printers
  browseable = yes
  guest ok = yes
  read only = yes
  write list = root
  create mask = 0664
  directory mask = 0775

; This part is included if you want to share printers
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

[home]
  public=yes
  browseable=yes
  path=/home
  writeable=yes
  max connections=0
  available=yes
  guest ok = yes

[hda6]
path = /media/hda6
comment = The big backup drive
available = yes
browsable = yes
public = yes
writable = yes
  max connections=0
guest ok = yes
create mask = 0644
directory mask = 0755

```

Also, the file /etc/printcap is as follows:
```
# This file was automatically generated by cupsd(8) from the
# /etc/cups/printers.conf file.  All changes to this file
# will be lost.
LQ-570+|Tractor Feed Epson Printer:rm=ECS755:rp=LQ-570+:
LQ-850|LQ-570-580:rm=ECS755:rp=LQ-850:
Z22|Lexmark Z22:rm=ECS755:rp=Z22:

```

Still looking for help.

---

### Post by pksings on 2007-02-01
edit /etc/cups/printers.conf

add the line (without quotes) "AllowUser samba"

restart cupsys.


On mine windows is printing as user "samba"

---

### Post by Das Oracle on 2007-02-09
hi, I have followed this and my printing works just fine but when a windows user tries to see my printers none show up.

smb.conf:
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



cupsd.conf

```

#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
Listen localhost*:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
#


```

printers.conf

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
</Printer>


```

---

