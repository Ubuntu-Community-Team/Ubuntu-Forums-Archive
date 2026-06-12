---
title: "Sharing a Hidden Folder"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by chalewa on 2008-07-12
Is there anything special I need to do to share a folder that is hidden? My permissions are all the same for this folder as for the ones that are not hidden, but for some reason when I try to access the folder on a client computer, it asks me for login credentials. 

Ideas?

---

### Post by chalewa on 2008-07-14
bump

---

### Post by dmizer on 2008-07-14
what hidden folder are you attempting to share?  by what method are you sharing the hidden folder (nfs, samba, ftp, scp/fuse)?  are both computers ubuntu?  are both computers linux?

---

### Post by chalewa on 2008-07-14
im just trying to share a folder that is named .folder and i have tried to share it via samba and fuse. 


i just keep getting an error telling me i don't have the right permissions but i know i do...

---

### Post by dmizer on 2008-07-14
okay ... where is ".folder" located? /home/chalewa/.folder or /.folder?

again ... are both computers linux? are both computers ubuntu?

---

### Post by chalewa on 2008-07-15
> **dmizer said:**
> okay ... where is ".folder" located? /home/chalewa/.folder or /.folder?

again ... are both computers linux? are both computers ubuntu?

.folder is located in /media/sda2/chalewa4bambu/.folder

yea both computers are running ubuntu, but i wouldn't mind having access to it on windows


thanks

---

### Post by dmizer on 2008-07-15
on the computer with /media/sda2/chalewa4bambu/.folder, please post the contents of:
```
/etc/samba/smb.conf
```

also, please post the output of:
```
ls -al /media/sda2/chalewa4bambu
```

---

### Post by chalewa on 2008-07-15
/etc/samba/smb.conf

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

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

guest ok = yes


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
   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

   guest account = nobody
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
guest ok = yes


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
    guest ok = yes
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
    guest ok = yes
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes
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
    guest ok = yes

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

[Guest Share]
	comment = Guest access share
	path = /media/sda2/chalewa4bambu/Hellanzb/.hellanzb/done
	browseable = yes
	read only = yes
	guest ok = yes
```




```
ls -al /media/sda2/chalewa4bambu
total 24
drwxr-xr-x  6 chalewa4bambu chalewa4bambu 4096 2008-07-03 07:13 .
drwxrwxrwx  7 root          root          4096 2008-05-09 22:12 ..
drwxrwxrwx  3 chalewa4bambu chalewa4bambu 4096 2008-07-15 18:50 Hellanzb
drwxrwxrwx 68 chalewa4bambu chalewa4bambu 4096 2008-07-15 18:23 Music
drwxrwxrwx  2 chalewa4bambu chalewa4bambu 4096 2008-07-14 20:38 Torrents
drwxrwxrwx  4 chalewa4bambu chalewa4bambu 4096 2008-07-02 20:27 .Whatnot
```



Thanks

---

### Post by dmizer on 2008-07-15
since you are using samba fuse, i don't know how to help you, other than offering some suggestions for things too look into.

i assume you are trying to share /media/sda2/chalewa4bambu/.Whatnot rather than /media/sda2/chalewa4bambu/.folder because /media/sda2/chalewa4bambu/.folder doesn't appear to exist on your computer.

remember that linux is case sensitive, so /media/sda2/chalewa4bambu/.Whatnot is not the same as /media/sda2/chalewa4bambu/.whatnot

---

### Post by chalewa on 2008-07-15
yea, ive tried pretty much everything i can think of. 

it doesn't work with just the regular gnome network browswer either, the reason i use fuse is the ease of loading networked files through various programs and saving files to the network through firefox. 

and yes, i am trying to share .Whatnot, and not .folder, the .folder was just an example. 


that said, what is interesting to me is that fuse has no problem sharing the folder /Hellanzb/.hellanzb/done so maybe if i create a regular folder around .Whatnot (not hidden) it will appear as tho the folder is empty, but .Whatnot will actually be shared. who knows, i will have to try it.

---

### Post by dmizer on 2008-07-16
don't get me wrong, i am by no means condemning your use of samba fuse, i have simply never used it.  just because i don't have a need for samba fuse, doesn't mean you don't have a valid reason for using it.

just out of curiosity.  what is the purpose of sharing hidden folders?

---

### Post by chalewa on 2008-07-16
> **dmizer said:**
> don't get me wrong, i am by no means condemning your use of samba fuse, i have simply never used it.  just because i don't have a need for samba fuse, doesn't mean you don't have a valid reason for using it.

just out of curiosity.  what is the purpose of sharing hidden folders?


there really is not that huge of a reason, i could just as well make the folder visible i guess, but i was just wondering if there was any big secret to sharing a hidden folder that i didn't know about. 

it seems as though it is a rather seldom used situation as I have found pretty much nothing anywhere about it.

---

### Post by dmizer on 2008-07-16
no ... i have a hidden folder shared on at least one server, but i don't use samba fuse.  i was just wondering if there was a specific reason for it.

after all, even if the folder is shown as hidden on your file system, that does not mean it is hidden on the network.

---

