---
title: "Samba Problems"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by adtrakmike on 2008-07-11
Note - I'm using Hardy Heron 8.04 Desktop as the Samba machine.

Hey all, not sure if this is the right place to post regarding Samba problems, I am not talkabout samba installed on the server version of Ubuntu, so I did not post in the server section.

We have about 11 users using Samba on a new installation of Ubuntu, the computer is a 2.8ghz celeron with 512mb RAM, it also runs apache and MySQL (though I'm pretty sure this makes no difference to Samba).

When our users (who all use Windows XP SP2 or SP3) are saving or updating files on the Samba machine, intermittently they are having issues, these can be any one of the following:

- Being told files are read-only and can't be saved (even if saving to a new file)
- Files not saving correctly
- Delayed write failures

Also, Samba can be quite slow to respond.

The computers that are using Samba are on a domain, the Samba machine is not associated in any way with this domain and has only one local account with which all 10 XP machines use to log on, the account is called administrator (a historical reason for choosing that name).

Does anyone have any ideas? Thanks

---

### Post by adtrakmike on 2008-07-11
I've been doing some digging and it seems that samba is crashing constantly, something like 450 times in less than 2 days with moderate use. I've included a transcript of one of the log files:

> [2008/07/11 15:21:05, 1] smbd/service.c:make_connection_snum(1033)
  mickwhitby (192.168.101.39) connect to service data initially as user administrator (uid=1001, gid=1001) (pid 19663)
[2008/07/11 15:21:08, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/data failed. Permission denied
[2008/07/11 15:21:08, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/data failed. Permission denied
[2008/07/11 15:21:08, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/data failed. Permission denied
[2008/07/11 15:21:08, 0] lib/substitute.c:alloc_sub_basic(463)
  alloc_sub_basic: NULL source string!  This should not happen
[2008/07/11 15:21:08, 0] lib/fault.c:fault_report(41)
  ===============================================================
[2008/07/11 15:21:08, 0] lib/fault.c:fault_report(42)
  INTERNAL ERROR: Signal 11 in pid 19663 (3.0.28a)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2008/07/11 15:21:08, 0] lib/fault.c:fault_report(44)
  
  From: [http://www.samba.org/samba/docs/Samba3-HOWTO.pdf](http://www.samba.org/samba/docs/Samba3-HOWTO.pdf)
[2008/07/11 15:21:08, 0] lib/fault.c:fault_report(45)
  ===============================================================
[2008/07/11 15:21:08, 0] lib/util.c:smb_panic(1633)
  PANIC (pid 19663): internal error
[2008/07/11 15:21:08, 0] lib/util.c:log_stack_trace(1737)
  BACKTRACE: 12 stack frames:
   #0 /usr/sbin/smbd(log_stack_trace+0x2d) [0x828ab6d]
   #1 /usr/sbin/smbd(smb_panic+0x5d) [0x828ac9d]
   #2 /usr/sbin/smbd [0x827551a]
   #3 [0xb7f3f420]
   #4 /usr/sbin/smbd(volume_label+0x54) [0x809b314]
   #5 /usr/sbin/smbd(handle_trans2+0x25a) [0x80ecb8a]
   #6 /usr/sbin/smbd(reply_trans2+0x69c) [0x80f364c]
   #7 /usr/sbin/smbd [0x810f90e]
   #8 /usr/sbin/smbd(smbd_process+0x89b) [0x8110d6b]
   #9 /usr/sbin/smbd(main+0xa18) [0x835ebf8]
   #10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7b53450]
   #11 /usr/sbin/smbd [0x8094331]
[2008/07/11 15:21:08, 0] lib/util.c:smb_panic(1638)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 19663]
[2008/07/11 15:21:08, 0] lib/util.c:smb_panic(1646)
  smb_panic(): action returned status 0
[2008/07/11 15:21:08, 0] lib/fault.c:dump_core(181)
  dumping core in /var/log/samba/cores/smbd
[2008/07/11 15:21:08, 1] smbd/service.c:make_connection_snum(1033)


My smb.conf is as follows, one thing to note is I can;t find for the life of me where Ubuntu stores the share definitions for samba, they aren't in this file thats for usre, because my shares are called data and web-server:

> #
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Mick config changes ##
hide dot files = no

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

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
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

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
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

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

# This option controls how nsuccessful authentication attempts are mapped 
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
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
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
;   load printers = yes

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
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

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
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
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
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
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

;[printers]
;   comment = All Printers
;   browseable = no
;   path = /var/spool/samba
;   printable = yes
;   guest ok = no
;   read only = yes
;   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
;[print$]
;   comment = Printer Drivers
;   path = /var/lib/samba/printers
;   browseable = yes
;   read only = yes
;   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

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



---

### Post by jamesnichols3 on 2008-07-11
hi there,

I'm seeing the same issue on my samba server, also the ubuntu desktop install.

Are you also seeing entire system crashes due to this?  Going by the marks in /var/log/messages, it looks like when the nightly backup from one of my Vista laptops run, it's crashing samba with the same exact error messages you describe, and the the entire OS crashes.

I just upgraded to version 3.0.28a, which had some sort of stability patch associated with a regression from some security bug fix a few revs back.  I'm not sure if I even had the version that got the bug fix, but I'm hopeful that the stability issue was the one I was encountering.

Have you tried updating samba to the latest?  Also, are you too seeing entire system crashes?

---

### Post by BrowneR on 2008-07-12
adtrakmike: I am also having all sorts of unrelated problems with Samba but I can hopefully help you with one of your questions at least...

When sharing files from nautilus using the right click menu the share definitions are not added to smb.conf! This is because Ubuntu is now using a new samba feature called usershares which allows normal users to create and manage their own shares (root is required to edit smb.conf). Shares are now added with the 'net usershare add' command and their definitions can be found in /usr/lib/samba/usershares.

I suggest as a possible fix for your crashes (well maybe just something you might like to try :p) removing your two usershares...

```
net usershare delete data
net usershare delete web-server
```

...and then re-adding them as normal old style system wide shares in smb.conf.

```

[data]
   comment = Data Store
   path = /path/to/data
   browseable = yes
   read only = yes
   guest ok = no

[web-server]
   comment = www-data
   path = /path/to/www-data
   browseable = yes
   read only = yes

```

it's worth a shot at least...

---

### Post by adtrakmike on 2008-07-14
Ahh, ok, I'll give this a go - thanks for the info, I was slightly confused....

---

### Post by adtrakmike on 2008-07-14
Well, spot on! This fixed it a treat (I think), no panics whatsoever this morning, usually they would be in the tens.

Fingers crossed it stays that way :)

One other thing that hasn't fixed itself is that Dreamweaver seems to think that files have been modified on disk (if you leave the file open), even when they haven't. It prompts you to reload often, which is very odd. I can confirm no-one else has edited the files, any ideas for that one? :)

Thanks for your help!

---

### Post by adtrakmike on 2008-07-14
> **adtrakmike said:**
> One other thing that hasn't fixed itself is that Dreamweaver seems to think that files have been modified on disk (if you leave the file open), even when they haven't. It prompts you to reload often, which is very odd. I can confirm no-one else has edited the files, any ideas for that one? :)

Found this to just be a slightly out-of-sync clock, I thought that windows machnioe would transmit the modified time to the server, turns out this is never the case, even with windows servers, so I changed the clock on Ubuntu and all works nicely now.

Cheers!

---

### Post by BrowneR on 2008-07-14
Glad you got it all sorted! :)

---

### Post by adtrakmike on 2008-07-14
Sorry I didn't see this post!

> **jamesnichols3 said:**
> Are you also seeing entire system crashes due to this?  Going by the marks in /var/log/messages, it looks like when the nightly backup from one of my Vista laptops run, it's crashing samba with the same exact error messages you describe, and the the entire OS crashes.

Nope - just Samba repeatedly crashing, even when backup exec backs it up overnight.

---

