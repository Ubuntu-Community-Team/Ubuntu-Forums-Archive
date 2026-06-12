---
title: "file sharing between iMac and 2 ubuntu 10.10 PCs over network {new to networking}"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by debray6379 on 2011-01-02
Hi, how do I fix this problem please?
I have 3 computers on my home network 2 Ubuntu computers and an iMac.
both ubuntu PCs are acer aspire L320's with ubuntu 10.10
and the iMac is a 24" with snow leopard.
names of PCs
Debrays iMac ~wired
shaun-L320 ~wired
acer1~ usb wireless dongle
my problem is
1. I'm new to networking
2. the one ubuntu pc can not see the other
so far it's like this
Debrays iMac can access both ubuntu pc folders & files ok
acer1 can access shaun-L320 & Debrays iMac fine
shaun-L320 can Debrays iMac but it can't access acer1

both ubuntu 10.10 PCs sharing are setup by right clicking folder and then sharing options then checking share this folder also allow others to create and delete files in this folder.

my mopdem router is a Dlink DSL-2730B  [http://www.dlink.com.au/products/?pid=804](http://www.dlink.com.au/products/?pid=804)

I have been searching but I fear I may not be using the right search terms [through lack of knowledge or all the right terms to search for]

sorry if I've done the wrong thing by asking, I am very nervous about posting on forums as you all seem to know so much and me so little. and I feel like I shouldn't bother you all.

if I have missed something in search just point me in the right direction please.
and if I have left out vital information let me know and I will post what you require.

sorry and thank you!:confused:

---

### Post by bioterror on 2011-01-02
Is your computers under the same workgroup in samba?
/etc/samba/smb.conf is worth to check out on every computer.

[https://help.ubuntu.com/9.10/serverguide/C/samba-fileserver.html]("https://help.ubuntu.com/9.10/serverguide/C/samba-fileserver.html") that's worth of checking out.

---

### Post by debray6379 on 2011-01-02
> **bioterror said:**
> Is your computers under the same workgroup in samba?
/etc/samba/smb.conf is worth to check out on every computer.

yes I think it is.

acer1's smb.conf
```

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
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
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
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

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

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


[acer1]
path = /home/acer1
comment = Family
available = yes
browsable = yes
public = yes
writable = yes

[Downloads]
path = /home/acer1/Downloads
comment = acer1-downloads
available = yes
browsable = yes
public = yes
writable = yes

[Music]
path = /home/acer1/Music
available = yes
browsable = yes
public = yes
writable = yes

[Videos]
path = /home/acer1/Videos
available = yes
browsable = yes
public = yes
writable = no

[Pictures]
path = /home/acer1/Pictures
available = yes
browsable = yes
public = yes
writable = no

[Torrents]
path = /home/acer1/Torrents
available = yes
browsable = yes
public = yes
writable = no

[FrostWire]
path = /home/acer1/FrostWire
available = yes
browsable = yes
public = yes
writable = no

[Public]
path = /home/acer1/Public
available = yes
browsable = yes
public = yes
writable = no

[backgrounds]
path = /usr/share/backgrounds
comment = destop wallpapers
available = yes
browsable = yes
public = yes
writable = yes

shaun-L320's smb.conf

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
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
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
    security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
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
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

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

---

### Post by luvshines on 2011-01-02
From a terminal in shaun Ubuntu PC can you paste the output of following commands
```

# List the shares of acer1 PC
smbclient -L <acer1-ip-address> -U<samba-user>%<samba-passwd>

# Try accessing any one of the listed shares
smbclient //<acer1-ip-address>/<share-name> -U<samba-user>%<samba-passwd>
```

---

### Post by debray6379 on 2011-01-02
smbclient -L <acer1-ip-address> -U<samba-user>%<samba-passwd>
```
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.4]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    acer1           Disk      
    IPC$            IPC       IPC Service (acer1 server (Samba, Ubuntu))
    acer1-home      Disk      
    pictures        Disk      
    downloads       Disk      
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.4]

    Server               Comment
    ---------            -------
    ACER1                acer1 server (Samba, Ubuntu)
    DEBRAYS-MAC          Debray's Mac

    Workgroup            Master
    ---------            -------
    WORKGROUP            DEBRAYS-MAC

```and smbclient //<acer1-ip-address>/<share-name> -U<samba-user>%<samba-passwd>

```
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.4]
smb: \>
```when I go to menu>places>network> then go>location and type in smb://<acer1-ip-address>/acer1/ I have full access to all files and folders?

---

### Post by luvshines on 2011-01-03
> **debray6379 said:**
> smbclient -L <acer1-ip-address> -U<samba-user>%<samba-passwd>
```
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.4]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    acer1           Disk      
    IPC$            IPC       IPC Service (acer1 server (Samba, Ubuntu))
    acer1-home      Disk      
    pictures        Disk      
    downloads       Disk      
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.4]

    Server               Comment
    ---------            -------
    ACER1                acer1 server (Samba, Ubuntu)
    DEBRAYS-MAC          Debray's Mac

    Workgroup            Master
    ---------            -------
    WORKGROUP            DEBRAYS-MAC

```and smbclient //<acer1-ip-address>/<share-name> -U<samba-user>%<samba-passwd>

```
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.4]
smb: \>
```when I go to menu>places>network> then go>location and type in smb://<acer1-ip-address>/acer1/ I have full access to all files and folders?

OK, so it is working from command line and through smb:// ...

What was the other method thru which it was failing ?

---

### Post by debray6379 on 2011-01-03
On shaun-L320 if I go to Places >> Network>> only Debrays Mac shows up.

But if I do the same on acer1 both Debrays Mac and shaun-L320 are shown.

I just don't understand why?

and I'm the only one in our home that knows a little about command line, so the rest of my family who use the 3 computers cannot get access to their shared files folders.

the mac seems to be the easiest to use, as all I have to do to gain access to the shared folders is click on the computers name in network 
eg: acer1 and log-in with user name acer1 with password acer1 and everything is available.

from acer1 computer I can go to Places>> Network choose shaun-L320 login with username and password and everything is shown.

from shaun-L320 only Debrays Mac is shown and not acer1.

thank you for your great help!

---

### Post by debray6379 on 2011-01-03
> **fanlynne said:**
> My suggestion would be to boot off of a Ubuntu LiveCD and create the USB with the built in USB Creater tool. IMO this is had the highest level of success for me.

I'm very sorry but I don't understand how a liveUSB would help????
I am having a network issue not a install issue. sorry if I misunderstood you post. :confused:

---

### Post by luvshines on 2011-01-04
> **debray6379 said:**
> On shaun-L320 if I go to Places >> Network>> only Debrays Mac shows up.

But if I do the same on acer1 both Debrays Mac and shaun-L320 are shown.

I just don't understand why?

and I'm the only one in our home that knows a little about command line, so the rest of my family who use the 3 computers cannot get access to their shared files folders.

the mac seems to be the easiest to use, as all I have to do to gain access to the shared folders is click on the computers name in network 
eg: acer1 and log-in with user name acer1 with password acer1 and everything is available.

from acer1 computer I can go to Places>> Network choose shaun-L320 login with username and password and everything is shown.

from shaun-L320 only Debrays Mac is shown and not acer1.

thank you for your great help!

Though I am not sure why it doesn't show up in network but I think the workaround of bookmarking the folder after accessing it with smb://... method from nautilus may help since then it should be available as a folder always

See if that helps

---

### Post by debray6379 on 2011-01-04
ok thanks mate will do that.

what is the easiest simplest way to share files/folders between two ubuntu 10.10 PCs? please

---

### Post by luvshines on 2011-01-05
There are many ways to share data:
1. SCP the files - simplest of all. Requires ssh daemon on machines(atleast on server)
2. NFS shares - Another simple way. Need to install nfs-kernel(need to check exact name). Just define the exports, mount and start using
3. Samba shares - A bit of configuration in the beginning but once you know how to do it, becomes pretty simple :)

SCP and Samba share will allow access from Windows machine too
NFS will allow only between linux(unless you install some NFS client for windows)

---

