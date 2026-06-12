---
title: "Cant Connect to Ubuntu from Windows Shares"
date: 2016-04-20
forum: Networking &amp; Wireless
---

### Post by scpatl4now on 2016-04-20
Since the update a couple of days ago I can no longer see shared files on Ubuntu 14.04 from my windows machines.  I can see and access them (windows shares) from Ubuntu.  It now asks for a password, however, to connect to the windows shares and it never used to do that.  Any ideas how to fix this?

---

### Post by May_Masters on 2016-04-20
Did you change the password to access the shares ?

Try manually connect to the shares. Open Win-Explorer and Extras -> connect share -> \\myServer\share 
If the net is ok and the Samba Server up and running you'll be prompted with the password to access the share. Check the box to remember your input.

On the server check the /var/log/samba/ logfiles for more infos

---

### Post by scpatl4now on 2016-04-20
No password changes.  The only thing different is that I added a windows 10 pc to the network.  I've checked the log files and other than multiple entries saying it has ignored security = share (which I have commented out then back in...neither worked) there isnt anything there that is relevant.  I can ping the ip address of the Ubuntu box successfully, but its not even seeing it in windows.  This all started with the last Samba update.
Using the format \\ip address\share name does not work.  It sees nothing

---

### Post by Lloydb39 on 2016-04-20
I have the same problem. Windows can see my Linux folders (connected by Ethernet) but asks for a Workgroup password, which it never did before. I have no idea what the password is and can't find it in Windows.

---

### Post by scpatl4now on 2016-04-20
Here is my smb.conf file if it helps

```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###
   browseable = true

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   netbios name = Gscott-desktop

# server string is the equivalent of the NT Description field
; server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
    wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = 10.0.1.4

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
    load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
    printing = cups
    printcap name = cups
    security = share

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
   usershare owner only = false

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
 [homes]
    comment = Home Directories
    browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
    read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
    create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
    directory mask = 0775

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
;    comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

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
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = no
   create mask = 0775

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
;   read only = yes
   guest ok = yes
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

# Lanman fix

; client lanman auth = yes
; client ntlmv2 auth = no

```

---

### Post by May_Masters on 2016-04-21
Firewall ?

Did the logfiles - on either side - reveal anything ?

open a tcpdump and check if data is getting back and forth ...

---

### Post by Lloydb39 on 2016-04-21
I had this same problem after switching to Windows 10. I typed "\\linux.local" in Windows file explorer and it made a quick access link to the Linux machine that worked. (Because of other problems I reverted back to Windows 7 and had no problems until the last Samba update).

---

### Post by scpatl4now on 2016-04-21
other than lots of entries about security = share being ignored...nothing

---

### Post by scpatl4now on 2016-04-21
I am going to take the Windows 10 pc off the network and see if that was the problem

---

### Post by scpatl4now on 2016-04-21
I just tried to access the shared folders on the Ubuntu box, and they are no longer showing as shared and when I tried to share them I got ...

```
Samba's testparm returned error 1: Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
WARNING: Ignoring invalid value 'share' for parameter 'security'
Error loading services.
```

---

### Post by scpatl4now on 2016-04-21
I think there are like 5 threads trying to fix the same problem...wish they could be combined so those of us having the same problem dont need to be checking all these threads

---

### Post by Morbius1 on 2016-04-22
You have the "security =" parameter listed twice in your smb.conf:

One here - correctly:
> # "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   **security = user**
And again here:
> # cupsys-client package.
    printing = cups
    printcap name = cups
    **security = share**
Both of them are within the [global] section of smb.conf and since samba reads sequentially "share" replaced "user"

Comment out the cups reference for "security", save smb.conf, restart smbd and pray.

---

### Post by scpatl4now on 2016-04-22
Did I mention that you are my favorite person EVER!!!!!  \\:D/

---

### Post by Morbius1 on 2016-04-22
>  Comment out the cups reference for "security", save smb.conf, restart smbd and [COLOR=#0000cd]**pray.**[/COLOR]                 

Considering how flaky the last samba update was your success may have been the result of a higher authority.

---

### Post by lordazuzu on 2016-04-25
Unfortunately, no "security = share" line in my smb.conf.

```

[global]


   workgroup = WORKGROUP

        server string = %h server (Samba, Ubuntu)


;   wins server = w.x.y.z

   dns proxy = no


;   interfaces = 127.0.0.0/8 eth0

;   bind interfaces only = yes




   log file = /var/log/samba/log.%m

   max log size = 1000


   syslog = 0

   panic action = /usr/share/samba/panic-action %d




   passdb backend = tdbsam

   obey pam restrictions = yes

   unix password sync = yes

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

   pam password change = yes

   map to guest = bad user



;   logon path = \\%N\profiles\%U

;   logon drive = H:

;   logon script = logon.cmd

; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

; add group script = /usr/sbin/addgroup --force-badname %g


;   include = /home/samba/etc/smb.conf.%m

;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
; add group script = /usr/sbin/addgroup --force-badname %g


;   include = /home/samba/etc/smb.conf.%m

;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


;   usershare max shares = 100

   usershare allow guests = yes


;[homes]
;   comment = Home Directories
;   browseable = no

;   read only = yes

;   create mask = 0700

;   directory mask = 0700

;   valid users = %S

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

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

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
;   write list = root, @lpadmin

[storage]
path = /storage
valid users = lordazuzu
read only = no

[wd3tb]
path = /wd3tb
valid users = lordazuzu
read only = no

```

nmbd log
```

[2016/04/25 12:11:25.924542,  0] ../source3/nmbd/nmbd.c:58(terminate)
  Got SIGTERM: going down...
[2016/04/25 12:11:40.342234,  0] ../lib/util/become_daemon.c:124(daemon_ready)
  STATUS=daemon 'nmbd' finished starting up and ready to serve connections
[2016/04/25 12:12:08.771320,  0] ../source3/nmbd/nmbd_become_lmb.c:397(become_local_master_stage2)
  *****

  Samba name server UBUTORRENT is now a local master browser for workgroup WORKGROUP on subnet 192.168.0.150

  *****

```

smbd log

```

[2016/04/25 12:11:40.341292,  0] ../lib/util/become_daemon.c:124(daemon_ready)
  STATUS=daemon 'smbd' finished starting up and ready to serve connections
[2016/04/25 12:25:03.917232,  0] ../lib/util/become_daemon.c:124(daemon_ready)
  STATUS=daemon 'smbd' finished starting up and ready to serve connections

```

winbindd log

```

[2016/04/25 12:11:25.926219,  0] ../source3/winbindd/winbindd.c:271(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=1)
[2016/04/25 12:11:40.296644,  0] ../source3/winbindd/winbindd_cache.c:3245(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 2
[2016/04/25 12:11:40.310941,  0] ../lib/util/become_daemon.c:124(daemon_ready)
  STATUS=daemon 'winbindd' finished starting up and ready to serve connections

```

testparm -v
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[storage]"
Processing section "[wd3tb]"
Loaded services file OK.
Server role: ROLE_STANDALONE

```

My windows desktop asks for username/password and just says the share is not accessible.

---

### Post by Morbius1 on 2016-04-25
You should start your own thread as this one is marked [SOLVED] and your situation is different.

You also might want to tell folks if you really are running:

> Ubuntu 8.04 Hardy Heron

---

### Post by lordazuzu on 2016-04-25
Lol, I'm sorry, I've been missing for a "few" years :)
Got to figure out how to change my profile ;)
I'll open my own thread, thanks!

---

