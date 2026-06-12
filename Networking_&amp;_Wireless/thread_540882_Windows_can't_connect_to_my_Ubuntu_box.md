---
title: "Windows can't connect to my Ubuntu box"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by synd7 on 2007-09-02
I'm trying to share some files between Ubuntu and XP but windows gives me an error saying i don't have the correct permissions and the server can't be found.

heres my smb.conf
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
   workgroup = MSHOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

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

# Put a capping on the size of the log files (in Kb).
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
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

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

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


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
;
; The following was the default behaviour in sarge
; but samba upstream reverted the default because it might induce
; performance issues in large organizations
; See #368251 for some of the consequences of *not* having
; this setting and smb.conf(5) for all details
;
;   winbind enum groups = yes
;   winbind enum users = yes

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

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Restrict access to home directories 
# to the one of the authenticated user
# This might need tweaking when using external authentication schemes
   valid users = %S

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

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
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


[Public]
path = /home/ben/Public
guest ok = yes
read only = no
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup
available = yes
browsable = yes
public = yes
writable = yes
```

I've done  
```
chmod 0777 /home/ben/Public
```
I've tried using System->Admin->Shared folders
I can't get to the files from the Ubuntu box through Network->BEN-DESKTOP, it gives me a login window i can't get past


All i want to do is have a shared folder (/home/ben/Public) that anyone on my LAN can connect to without having to log in or manually enter all their users into a database.

Thanks in advance

---

### Post by HermanAB on 2007-09-02
See this guide: [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

H.

---

### Post by synd7 on 2007-09-02
That guide really didn't help at all. It explains how to set usernames and passwords but i don't want that. The aim is to have it like windows (i can't believe i typed that) so that any user on the network can browse that folder

I've had this set up properly on feisty but i can't remember what i did :)

---

### Post by HermanAB on 2007-09-02
In Linux, change the permissions on the shared directory to be liberal:
$ sudo chmod -R 777 directoryname

Then in smb.conf set "public = yes" for that share.

Then reboot Samba:
$ sudo service smb restart

Cheers,

H.

---

### Post by loaderboy on 2007-09-02
I had the same prob. In my smb.conf file I changed the values under shre to:
browseable=yes
readable=yes
writeable=yes
That seemed to do the trick.
Make sure to uncomment those lines as well

---

### Post by synd7 on 2007-09-03
nope, no luck with any of that stuff
IMO this is one of the things that should work out of the box, for some reason it never has for me.

heres my smb.conf now
```

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
   workgroup = MSHOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

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

# Put a capping on the size of the log files (in Kb).
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
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

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

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


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
;
; The following was the default behaviour in sarge
; but samba upstream reverted the default because it might induce
; performance issues in large organizations
; See #368251 for some of the consequences of *not* having
; this setting and smb.conf(5) for all details
;
;   winbind enum groups = yes
;   winbind enum users = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
   comment = Home Directories
   browseable = yes

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes
   readbale = yes
# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Restrict access to home directories 
# to the one of the authenticated user
# This might need tweaking when using external authentication schemes
;   valid users = %S

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

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
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


[Public]
path = /home/ben/Public
guest ok = yes
read only = no
create mask = 0777
directory mask = 0777
force user = ben
force group = ben
available = yes
browsable = yes
public = yes
writable = yes
readable = yes
```

---

### Post by Trash_Gordon on 2007-09-03
Well no wonder that it doesn't work! You spelled it wrong! It's readable, not readbale!:rolleyes:

EDIT: Well, that's only for homes, As for the public share, you want it for ALL users to browse it. So why do you write 
```
force user = ben
force group = ben
```
in there?

---

### Post by synd7 on 2007-09-03
haha, i found that typo and corrected it, still didnt work :)


The idea was to force any other users to have my username and group and therefore have access to the folder
I've tried it with

```
force user = ben
force group = ben
```
```
force user = nobody
force group = nogroup
```
and with none of that there and none of it worked

---

### Post by MatrixShaman on 2007-09-03
I was having similar problems:
  At first windows couldn't see my server, fixed by shortening my hostname with System->Admin->Network and it could see it fine then (curiously, before the shortening, windows did register the name for a few minutes once...)
  I still couldn't get it to allow access, and I tried the various things in this post and another, all to no avail.  Finally I decided, even though I had already set up firestarter to allow the IP of my windows laptop, I turned off my firewall...

and it worked!

I turned the firewall back on, and it can still connect.

My setup of samba included basic installation, System->Admin->Shared Folders to change my workgroup name, and add the folder I wanted public.  The only change necessary to not get prompted for a password was the    security = share
although I did also add myself and enable with the sudo smbpasswd -L -a username  and  sudo smbpasswd -L -e username   commands, but with the security = share i dont think that was necessary.

sorry for my lack of formatting here, that'll be the next thing I try to learn :)

---

### Post by MatrixShaman on 2007-09-03
Ok, actually still having issues, i couldn't write to the drive, and changing stuff around and rebooting windows, now windows can't even see the samba server again... Is there a way to tuck my tail between my legs, and erase these posts?

---

### Post by MatrixShaman on 2007-09-03
Ok, still testing this issue, but this is what i've found out:
  As far as the smb.conf, I've got security = share in it's location,   in the public folder declaration i put    guest ok = yes.   
  The folder has 777 permissions

These changes alone should make it work.  

However, I'm realizing there are some other issues behind the scenes.
For the past few hours now, i've been watching the fluctuating names of IP addresses and WorkGroup designations in EtherApe.  I've watched and tested with Firestarter called and uncalled after rebooting, which I thought shouldn't matter as i've read it's only supposed to configure the iptables, but it does have some effect, sometimes..

Also, I'm running 7.04 Feisty Fawn on Desktop, and WinXPsp2 on laptop

_With the same settings_, and only changing whether or not i've opened up Firestarter, or various rebooting of both machines, or sometimes just waiting a few extra minutes, 
 I've witnessed the following:


Sometimes:
I can view  and access both machines in win network places
I can view  and access both machines in ubuntu network places
I can view neither machine in ubuntu network places
I can view neither machine in win network places
I can view only Laptop in win network places
I can view only Ubuntu in win network places
I can view but not access Ubuntu in win network places
I can view only Laptop in win network places, then waiting 5 minutes, Ubuntu suddenly shows up with no provocation anywhere...

Does Anyone know what's going on?:confused:

Synd7, can you try simplifying your settings like i've said, reboot both(or more) machines, wait 10 minutes, then try to access?  Are you using Firestarter? if so, maybe disable it from the startup menu if you put it there? Or disabling it temporarily when running the GUI?

---

### Post by HermanAB on 2007-09-03
Howdy,

As a minimum, port 445 must be open for SMB to work.  For older Windoze versions, you need port 139 open as well.

You can test this using telnet.  Windows should have telnet by default:
c:\> telnet yoursmbserveripaddress 445

You should get a prompt from Samba.  Press Ctrl-] and q to quit.
If you don't get a prompt from Samba, then the Linux firewall is blocking you.

Similarly, if you have 'server' running on Windoze (File and printer sharing turned on), then you can use telnet to test connectivity from Linux;
$ telnet yourwindozeboxipaddress 445

You should get a prompt from Windoze.  If not, the Windoze firewall is blocking you.

The only other important thing is to have all machines set to use the same workgroup.  This is set in the system/computer name wizard on Windoze and the /etc/samba/smb.conf file on Linux.

Cheers,

H.

---

### Post by bobmac on 2007-09-04
Folks,

I seem to be having the same problem. The windows boxes (xp desktop and xp laptop) can both  see (windows explorer) the mshome/ubuntu listing but when I try to access ubuntu from windows I get a user logon dialog which doesn't allow access. I've read what others have said about the smb.conf file but being totally new to ubuntu and linux I haven't a clue where this file resides.

I opened a terminal and tried whereis smb.conf but there was no result.

Any help would be much appreciated.

regards,

Bob

---

### Post by HermanAB on 2007-09-04
Easy:
/etc/samba/smb.conf

The Workgroup setting is near the top (It must be UPPERCASE).

Then restart Samba with:
sudo service smb restart

Cheers,

H.

---

### Post by bobmac on 2007-09-05
Herman,

Many thanks for the info. I eventually located the file. I'm now not sure what I should change and anyhow when I try to save the file I get a message telling me that I it's a read only file and I don't have permission to change it.

The message is:
The file "/etc/samba/smb.conf" is read-only.
Do you want to try to replace it with the one you are saving?

My file looks like this:
calban@ubuntu:/etc/samba$ cat smb.conf
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
   workgroup = mshome

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

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

# Put a capping on the size of the log files (in Kb).
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
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

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

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


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

wins support = no

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
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
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom








[calban]
path = /home/calban
available = yes
browsable = yes
public = yes
writable = no
calban@ubuntu:/etc/samba$

---

### Post by HermanAB on 2007-09-05
Change the 'mshome' part below:
# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = mshome

So that the workgroup is the same on all machines.  In Windoze, set it in the System wizard.

You should change the file permissions before you try to edit it:
sudo chmod 664 /etc/samba/smb.conf
sudo gedit /etc/samba/smb.conf

Cheers,

Herman

---

### Post by synd7 on 2007-09-05
Ok,  removed the force user and force group bits an now i can acces it from my ubuntu box (connecting to myself) through Places --> Network --> BEN-DESKTOP but i still get the error message from windows

---

### Post by MatrixShaman on 2007-09-05
with all my testing all i can figure is that i'm having an issue with my firewall NOT behaving as it should.  If i turn my firewall off,  i can access it fine, even with all connections from my windoze ip address allowed, but with firewall on, i can't even hit my print server from my ubuntu.  No matter how much i change my settings, i'm either not getting it right, or it's not working as it should.  firestarter also isn't running automatically in the background as a service as the site says it should for a binary debian(ubuntu) install..

but as long as i turn my firewall off:   changing the /etc/samba/smb.conf to security = user, [folder] ... guest ok = yes, and chmod 777 folder seems to make the desired effect of being able to access it without a pesky logon :)

Also, I wouldn't advise the 664 on the smb.conf, it might be good to keep a little extra protection from nosing around or playing with non-sudo commands,  i would just use sudo gedit /etc/samba/smb.conf to edit it,  might also be good to run a sudo cp /etc/samba/smb.conf  /etc/samba/smb.conf.orig to save a backup first to restore of use as a point of reference

---

### Post by HermanAB on 2007-09-05
Permissions of 664 on smb.conf is safe.

Test your firewall with telnet and test Samba with smbclient  As a minimum, you should have port 445/tcp open for Samba.  You may also need port 139/tcp open for some older Windows services.

Cheers,

Herman

---

### Post by MatrixShaman on 2007-09-05
i can connect via telnet to both 445 and 139, and the connection shows up in the active connection block of the status tab of my firestarter, however i am still unable to connect.

I also noticed that in order for my ubuntu network:: to work properly i had to allow connections to my windoze's ip..

I currently have connections allowed to the win IP, and samba service allowed to the same IP. 
i also changed my block broadcast preferences, from internal and external networks to block, as i had UNblocked them, and i think blocking the broadcasts, allows them...

---

### Post by MatrixShaman on 2007-09-05
*chuckles* couldn't reply again for a minute, setting outbound policy to restrictive, couldn't get the web page up :)

but from telnet on ubuntu trying to access my windoze, the connection is refused. Could this be a source of the problem, just as reflectively, i couldn't access my ubuntu network:: until i allowed connections to my windoze?  But in XP i do have file&print sharing enabled through the firewall...

---

### Post by HermanAB on 2007-09-05
If from Linux to Windows it won't work, while on Windows itself to itself it does work, then you certainly have a Windows firewall problem.

Try the connections in various ways to test them out:
telnet localhost 445
telnet externalipaddress 445

---

### Post by MatrixShaman on 2007-09-05
Actually, i reset some buried advanced tcp/ip setting in XP, and was able to open a telnet session from ubuntu, but that was unnecessary.
Everything is working proper now, safe, and convenient, and the source of the issue seems in my setting the advanced firestarter options to block broadcasts from internal and external networks.  I think those were unchecked originally, and i checked them, before i installed samba.  With those unchecked, everything is good.

Thank you so much Herman for your help and ideas,
I hope this helps the OP too (original poster) and others reading this.

_____________________________________________________________
The Daemons seem to be inline, until the next rebellion

---

### Post by bobmac on 2007-09-05
Herman,

I set the smb.conf (workgroup = windowsworkgroupname), file as you suggested but that didn't work. Looking at the windows boxes I noticed that while the Ubuntu box seems to be recognised there are never any shares under it. I wonder if this has something to do with the problem?

Also, I can access the windows boxes from the Ubuntu box it's just that I can't do the same the other way around.

Bob

---

### Post by HermanAB on 2007-09-05
Divide and conquer.

The maximum workgroup length is 15 characters and it must be UPPERCASE.

Restart Samba after changing anything with:
sudo service smb restart

Debug Samba on the Linux machine alone.  If it won't work locally, then there is no way that it is miraculously going to work remotely.  So check Samba with telnet and smbclient:
telnet ipaddress 445
smbclient -L \\ipaddress -N
smbclient \\ipaddress\sharename -U username%password

If the above three things work on Linux alone, then Samba is working and the problem lies elsewhere.

Samba is not a black box.  With smbclient, you can see exactly what it is doing or not doing.  You can also use smbclient to connect to a file share from Linux to a Windows machine, same as above.

Cheers,

H.

---

### Post by bobmac on 2007-09-05
Herman,

I've been checking out other entries in the forum and found this one

Code:

security "user"

and change it into
Code:

security "share"

Save with Strg+O and quit using Strg+X. Then reboot or simply reload samba using 'sudo /etc/init.d/samba restart'


I tried it and low and behold it seems to work.

Anyhow, many thanks for your input. I learned a lot about this smb.conf file.

Bob

---

### Post by HermanAB on 2007-09-05
Note that Windows networking is a mishmash of NetBIOS and TCP.  The NetBIOS identifiers must be defined in UPPERCASE.  The reason is that NetBIOS is case insensitive (it converts everything to upper case), while Linux is case sensitive.  Therefore, if you define a NetBIOS workgroup or NetBIOS name in mixed case in Linux, then it is impossible for Windows to connect to Linux, while it will work the other way around.

Also, avoid using: '_', '.', '/', '\', '&'and '@' (underscore, period, slash, backslash, ampersand and ampersat) in any Samba identifiers and passwords, since they may or may not work, depending on the phases of the moon and other galactic variables.

Cheers,

Herman

---

### Post by HermanAB on 2007-09-05
I'm surprised that setting 'security to share' makes any difference.  If anything, setting it to 'share' is a nuisance.  Here is why:

From security_level.txt:
A SMB server tells the client at startup what "security level" it is
running. There are two options "share level" and "user level". Which
of these two the client receives affects the way the client then tries
to authenticate itself. It does not directly affect (to any great
extent) the way the Samba server does security. I know this is
strange, but it fits in with the client/server approach of SMB. In SMB
everything is initiated and controlled by the client, and the server
can only tell the client what is available and whether an action is
allowed. 

I'll describe user level security first, as its simpler. In user level
security the client will send a "session setup" command directly after
the protocol negotiation. This contains a username and password. The
server can either accept or reject that username/password
combination. Note that at this stage the server has no idea what
share the client will eventually try to connect to, so it can't base
the "accept/reject" on anything other than:

- the username/password
- the machine that the client is coming from

If the server accepts the username/password then the client expects to
be able to mount any share (using a "tree connection") without
specifying a password. It expects that all access rights will be as
the username/password specified in the "session setup". 

It is also possible for a client to send multiple "session setup"
requests. When the server responds it gives the client a "uid" to use
as an authentication tag for that username/password. The client can
maintain multiple authentication contexts in this way (WinDD is an
example of an application that does this)


Ok, now for share level security. In share level security (the default
with samba) the client authenticates itself separately for each
share. It will send a password along with each "tree connection"
(share mount). It does not explicitly send a username with this
operation. The client is expecting a password to be associated with
each share, independent of the user. This means that samba has to work
out what username the client probably wants to use. It is never
explicitly sent the username. Some commercial SMB servers such as NT actually
associate passwords directly with shares in share level security, but
samba always uses the unix authentication scheme where it is a
username/password that is authenticated, not a "share/password".

Many clients send a "session setup" even if the server is in share
level security. They normally send a valid username but no
password. Samba records this username in a list of "possible
usernames". When the client then does a "tree connection" it also adds
to this list the name of the share they try to connect to (useful for
home directories) and any users listed in the "user =" smb.conf
line. The password is then checked in turn against these "possible
usernames". If a match is found then the client is authenticated as
that user.

---

So if it works one way, it should work either way.  My guess is that it now works, simply because you restarted smbd and nmbd.

Cheers,

H.

---

### Post by bobmac on 2007-09-05
Herman,

You're a wonder. Thank you for that explanation.

Now that I've got some idea as to what's going on I'll try out a few different options to these commands and see what happens.

Since I'm totally new to all this if things go badly wrong I can just reinstall everything and try again.

Anyhow, thanks again for all your help

Bob

---

### Post by HermanAB on 2007-09-06
Hmm, you got to read the smb.conf file carefully from top to bottom a few times.  There is a lot of information in the comments.  One other thing that you need to worry about, once you have it working, is security.  Otherwise it won't keep working for very long!

Always limit the network connections to your LAN only.  Never allow Samba connections from the WAN, since Samba is an inherently insecure protocol with many weird and wonderful, mostly unused and poorly understood functions.  If you open it to the wild wild world, then your machine will be hacked.  I always use this (my LAN is always 192.168.x.y):
hosts allow = 192.168. 127.

In the internet firewall, I drop all these ports in both directions:
135-139, 445

Cheers,

H.

---

### Post by synd7 on 2007-09-06
From the ubuntu box:
I can telnet myself
I can telnet the windows box
i can connect to myself with smbclient

From the windows box
I cannot telnet the ubuntu box on port 445 (it stays tryingt connetc for ages)

So it looks like its an ubuntu firewall problem. Except i dont have a software firewall (that i know of), i don't run iptables or firestarter or anything. WTF? :(

---

### Post by bobmac on 2007-09-06
Herman,

More good info from you. I'd certainly like to make sure that I'm isolated from the wide world but where do I set up these settings?

I can't locate a hosts tag in the smb.conf file and I haven't a clue whether or not I've got a fire wall in the Ubuntu machine. I do however, have a firewall set on my ADSL modem.

Like you my LAN is 192.168.x.y.

Bob

---

### Post by jdbg on 2007-09-13
Guys,
I've just installed a Ubuntu 7.04 Server edition on a spare PC that I have. I want to make it run a couple of shares. I installed the webmin so that it is easier to configure (or at least I though so). Created the directories I want to share, put them in the Samba config, but I cannot access them from my laptop (I'm on Win XP SP2). I see the server, but when I click on it, it asks for a password. I input my Ubuntu user/password (which are the same as the Samba user/password), but it won't let me in. 

Any ideas how to fix that? I read the myriad of threads on samba, but can't really find an answer. Thanks in advance!

---

### Post by MatrixShaman on 2007-09-13
Check your firewall, did you set up with firestarter? 
try  <CODE>sudo iptables -L</CODE> 
Can you copy/paste your /etc/samba/smb.conf?  

most of the issues i was having was from an improperly set up firewall or a check mark in blocking external broadcasts, my most recent reinstallation, all i changed in smb.conf was security = share, and my workgroup name, the System=>Admin=> Shared Folders did the rest, except if i want to change stuff, then you need to alter the permissions.

---

### Post by jdbg on 2007-09-13
I think the firewall is off (since the server is behind a firewall already). This is what I got when I checked it the way you said:

```

root@irnik:/srv/www# sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

---

### Post by MatrixShaman on 2007-09-13
ya, that looks like your firewall is off the server.. does your other firewall allow the connections? If so, the only other things i would know to check were if you enabled as well as added your user/passwd to the smbpasswd? or maybe uncommenting the security = user line?

---

### Post by jdbg on 2007-09-13
I did that. Still doesn't work :(

---

### Post by MatrixShaman on 2007-09-13
OH! I think i just remembered reading in how firestarter is only a gui configurer for iptables, and even though it seems iptables is off, the default may still be to reject any connections... maybe give firestarter a try and open the connections to the laptop or everyone, and make sure to uncheck the block external broadcasts from the advanced preferences?

---

