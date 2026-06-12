---
title: "File Sharing in Edgy with Windows XP"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by vixenk on 2006-11-03
I can't seem to figure it out. I can access the shares on the Windows XP machine but the Windows XP machine can't access my shares - instead it gives an error message about not having permission to access the server. I *would* set up permissions for it to access my Ubuntu machine but I don't know how and for some reason can't find out how (tried searching the forums & Google). Since I'm a migrating KDE user and used Samba (Smb4k) for my file sharing before I'm unfamiliar with configuring the actual smb protocol.

So far, I have figured out one thing - how to change my workgroup in Gnome's configuration editor (I think). The exact change was made to system > smb > workgroup. I changed the value from being blank to MSHOME. Unfortunately, the only results I've seen from that is the inability to access the Windows XP machines shares and the changing of its location from smb://*WinXP machine's name* to smb://MSHOME/*WinXP machine's name*. Gnome returns the error "Sorry, couldn't display all the contents of *WinXP machines name*"

Under Smb4k the only changes I had to make were to the workgroup name (which is MSHOME) and to the accepted IP range in smb.conf since I have an unusual LAN IP range. 

I would greatly appreciate help in this or a link to documentation on how to work with this.

---

### Post by amohanty on 2006-11-04
Can you post the contents of:
/etc/samba/smb.conf

AM

---

### Post by vixenk on 2006-11-04
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
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
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
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
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
```

---

### Post by amohanty on 2006-11-04
Ok first off you dont seem to be sharing anything. Try the following:
1. Backup your smb.conf file
**sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.orig**
2. Copy the following onto a file on your desktop:
> 
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic
# errors.
#
#======================= Global Settings =======================
[global]
  workgroup = WORKGROUP
  server string = %h Samba Server
  hosts allow = <put subnet>

  log file = /var/log/samba/log.%m
  max log size = 1000
  syslog = 0

  share modes = yes

;  security = user
  encrypt passwords = true
  invalid users = root
  smb passwd file = /etc/samba/smbpasswd

  interfaces = <put machine ip>
;  bind interfaces only = yes

  socket options = TCP_NODELAY

#======================= Share Definitions =======================

[shared]
  comment = <put comment>
  path = <put absolute path>
  public = yes
  read only = no
  writable = yes
  browseable = yes
  create mask = 0664
  directory mask = 0775

3. Replace the subnet with your LAN subnet. To do so:
**ifconfig**
Use the first three parts of the IP e.g. 192.168.0.
4. Create a samba user: 
**sudo smbpasswd -a <ubuntu username>**
5. Copy the file over to /etc/samba
**sudo cp ~/Desktop/smb.conf /etc/samba**
6. Restarts samba
**sudo /etc/init.d/samba restart**

That should do it.

HTH
AM

---

### Post by vixenk on 2006-11-05
> Ok first off you dont seem to be sharing anything.
Sorry, guess I should've noted I left that part out as it isn't part of the problem I'm having. That part of the file is set up correctly, and the WinXP machine can see my shares, just doesn't have permission to access them. 

> interfaces = <put machine ip>
One problem here - my machine doesn't have a static IP on the network, and creating one isn't feasable as the other person on this network prefers to stay dynamic.

Here's a new copy of my smb.conf file integrating the info given:

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
hosts allow = 192.168.15.
smb passwd file = /etc/samba/smbpasswd

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
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
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
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
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
   share modes = yes

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


[Pictures]
path = /home/vk/Documents/Pictures
available = yes
browsable = yes
public = yes
writable = no
```

I also created the samba user and restarted samba. I will be able to tell you in a few minutes if it worked or not. :)

---

### Post by vixenk on 2006-11-05
*sighs* Didn't work. I'll try the given smb.conf file now.

---

### Post by vixenk on 2006-11-05
The given smb.conf didn't work either. Here's a copy of that:

```
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic
# errors.
#
#======================= Global Settings =======================
[global]
workgroup = WORKGROUP
server string = %h Samba Server
hosts allow = 192.168.15.

log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0

share modes = yes

; security = user
encrypt passwords = true
invalid users = root
smb passwd file = /etc/samba/smbpasswd

interfaces = 192.168.15.
; bind interfaces only = yes

socket options = TCP_NODELAY

#======================= Share Definitions =======================

[Pictures]
comment = <Pictures>
path = </home/vk/Documents/Pictures>
public = yes
read only = no
writable = yes
browseable = yes
create mask = 0664
directory mask = 0775
```

The exact error message given to me on the WinXP machine is this:

```
\\Vk\Pictures is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The network path was not found.
```

---

### Post by vixenk on 2006-11-05
Ok, on top of that... now I can't access the WinXP machines shares. When accessing the Windows Network directory I just get a blank screen - no MSHOME or anything, and I restored my smb.conf file to the default configuration.

So basically, now I'm worse off than when I started.

---

### Post by amohanty on 2006-11-05
My fault in the file that I sen tyou I wrongly mentioned the workgroup to be WORKGROUP instead of MSHOME as you had.

So if you revert the file back to your original as in post #5, create the samba user (make sure that the username is that of an existing ubuntu system user i.e. if user1 does not exist on the system you cannot use it)

Also remove the '<' and '>' characters in the path, they are used to indicate that you should set the thingy to your values.

Make the file so:

> #======================= Global Settings =======================

[global]
   workgroup = MSHOME
   server string = %h server (Samba, Ubuntu)
;   wins support = no
;   wins server = w.x.y.z
   dns proxy = no
;   name resolve order = lmhosts host wins bcast
hosts allow = 192.168.15.
smb passwd file = /etc/samba/smbpasswd

#### Networking ####
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = true

#### Debugging/Accounting ####
   log file = /var/log/samba/log.%m
   max log size = 1000
;   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######
;   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
;   guest account = nobody
   invalid users = root
;   unix password sync = no
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
;   pam password change = no

########## Printing ##########
;   load printers = yes
;   printing = bsd
;   printcap name = /etc/printcap
;   printing = cups
;   printcap name = cups
;   printer admin = @lpadmin


############ Misc ############
;   include = /home/samba/etc/smb.conf.%m
   socket options = TCP_NODELAY
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   domain master = auto
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

;[homes]
;   comment = Home Directories
;   browseable = no
;   valid users = %S
;   writable = no
;   create mask = 0600
;   directory mask = 0700

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
   share modes = yes

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
;   write list = root, @ntadmin

;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[Pictures]
comment = Pictures
path = /home/vk/Documents/Pictures
public = yes
read only = yes
writable = no
browseable = yes


Then when you try to access \\vk\Pictures you should get a login box with the option to save the password. What happens whenyou put in the password?

AM

---

### Post by vixenk on 2006-11-05
I don't get a login box or anything. On the WinXP machine, I just get that error message. On my machine (the Ubuntu machine), I create the password for my user (vk) and that's it. No questions afterwards.

The dialogue went like:
$ sudo smbpasswd -a vk
password: <typed in the password>
password: <typed in the password>
$

Oh, I should probably also add that I don't really want nor need password protected access. I use both a software and hardware firewall and this is just a small home network, with nothing major shared on the network. I would just like to be able to bind Samba to my LAN's subnet.

---

### Post by amohanty on 2006-11-05
After replacign the files did you restart samba:
**sudo /etc/init.d/samba restart**

?
AM

---

### Post by vixenk on 2006-11-05
Yup.

---

### Post by amohanty on 2006-11-05
Ok so as far as I can tell this stuff should work, if you are using the file I modified from your post and posted in #9 and restarted samba.

Can you make sure that the the folder is world readable **ls -l**
Also post the output of **testparm**

Also look in /var/log/samba and see if you can spot any problems in any of the files in there.

AM

---

### Post by vixenk on 2006-11-06
ls -l:
```
drwxr-xr-x   4 vk users    4096 2006-11-02 08:59 Pictures
```

testparm:
```
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Pictures]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

vk@vk-desktop:~/Documents$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Pictures]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root
        hosts allow = 192.168.15.

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[Pictures]
        comment = Pictures
        path = /home/vk/Documents/Pictures
        guest ok = Yes
```

I also tried going into add a network place in WinXP and under there, it shows my machine as not sharing anything.

Thinking it might be the software firewall (Firestarter, which I've had problems with before regarding the LAN), I disabled and uninstalled it.

Still a no go. :(

---

### Post by vixenk on 2006-11-06
Oh, the contents of /var/log/samba:
```
log.0.0.0.0    
log.192.168.15.17  
log.burn-7adbf58834  
log.smbd
log.127.0.1.1  
log.192.168.15.19  
log.nmbd             
log.vk-desktop
```

---

### Post by vixenk on 2006-11-06
I don't know if this matters, but it is pretty unusual... 

I tried reinstalling Firestarter. Right off the bat, when I try to access the network, I get blocked connection attempts from varying IPs trying to access port 6881 udp and tcp (bittorrent). This only happens when I try viewing the network. Also, with Firestarter enabled, I don't even get as far as I do with it disabled. With it disabled I get as far as clicking on the WinXP machine on the network, then get some generic error message that it can't find anything at that location. With it enabled though, I get those weird connection attempts and an empty page whenever I click on "Windows Network".

Is Samba trying to use the bittorrent ports for some off the wall reason? And if so, why are the IPs showing up not related to me nor the network in any way?

This is so weird. -_-;

BTW, my machine nor the WinXP machine is currently using bittorrent.

---

### Post by vixenk on 2006-11-06
Ok *sigh of relief* it's working. I went into "add a network place", right clicked on my machine's name, and the password box popped up. 

However...

I still can't browse the WinXP machine's shares! 

Gahhhh...

The exact error message:
"The folder contents could not be displayed. Sorry, couldn't display all the contents of "Windows Network: mshome".

No firewall or anything on either computers.

This is crazy. When I started out, I could access the WinXP machine's shares but it couldn't access mine. Now it can access my shares but I can't access its shares.

---

### Post by amohanty on 2006-11-06
Can you make sure that your XP machines workgroup is called MSHOME. Right click on My Computer, select Properties and select Network... tab.

AM

---

### Post by vixenk on 2006-11-06
It is...

And it's not working again. *sighs*

I haven't changed anything since it was working... the only thing I've done is check to make sure it's MSHOME.

---

### Post by amohanty on 2006-11-06
Allright now:
1. Is windows firewall on?
2. If yes, is file and printer sharing checked in the firewall settings?
3. Is firestarter on?
4. Is samba exempted in firestarter?
5. Is Samba on?
6. Can you ping both machines?

AM

---

### Post by vixenk on 2006-11-06
*sighs* Ok, now it is working again. Firestarter was on, and evidently was blocking it. I don't understand why or how but... like I said, Firestarter doesn't seem to like my network. Not only is Samba allowed through in the rules, but all connection attempts from the network are allowed through. There's nothing in Firestarter's log. That's just how Firestarter plays with my network. :( If I knew of a decent firewall besides it I would use it but the only one I know of is Guarddog and I'm trying to refrain from KDE apps.

The Windows firewall is on, file and printer sharing is checked in the firewall settings. 

Samba is on. I can ping back and forth between both machines.

So everything is ok. Except... I still can't access the XP machine's shares.](*,)

---

### Post by amohanty on 2006-11-06
In terms of a firewall, I would suggest buying a hardware router/firewall and turning off all the firewalls on all machines. IMO, Firestarter as a usable peice of software sucks (unless of course you know stuff about iptables).

No on windows, create a dummy non-admin user, login as that user and try to hit your windows share? You could do it from another windows machine too.

Does that work?
The reason I ask is I have run into this problem many times just connecting from a windows box to a windows share too.

AM

---

### Post by vixenk on 2006-11-06
I'm behind a hardware firewall, just like to have a software firewall as well, and I've worked with iptables before, I just don't really like to, hehe.

Either way, Firestarter is gone. If I feel the urge for a firewall I'll just go the Guarddog route again. :)

Under a non-admin account on the WinXP machine... nope, same thing. "The folder contents could not be displayed. Sorry, couldn't display all the contents of "Windows Network: mshome".

---

### Post by amohanty on 2006-11-06
Ok so now at least we know that the problem is in the XP side, now try the following:
1. Unshare the dir
2. reboot
3. reshare it, make sure the sharing is applied to all subfolders as well
4. setup permissions as readable to everybody in the permissions tab and make sure that sharing is applied to all subfolder

Run the windows to windows test again.

HTH
AM

---

### Post by vixenk on 2006-11-06
Nope. Same thing. :(

I should add also that there is no permissions tab or anywhere where I can check to make sure it's readable by everyone. Just the sharing tab. I made the files shared and writable by network users.

---

### Post by amohanty on 2006-11-06
Sorry I meant the Permissions button in the sharing tab in the sharing dialog.
AM

---

### Post by amohanty on 2006-11-06
OH forgot: also instead of the hostname try using the IP ie
\\IP_OF_XP_BOX\sharename

from another windows box or from the non-admin account

AM

---

### Post by vixenk on 2006-11-06
Via  "smb://*WinXP machine's IP*/*share name*" I can access it on Ubuntu.

Don't have a Win box to try it out from.

Why is it I can't view MSHOME and get to it that way, though? :S

I could bookmark it but the IP changes frequently so I would constantly have to be rebookmarking it. :(

---

### Post by amohanty on 2006-11-06
> Via "smb://*WinXP machine's IP*/*share name*" I can access it on Ubuntu.

Ok so it works!!!
now in /etc/hosts
add a line like this:
xp_ip_address xp_hostname

now you can access it via smb://xp_host_name/share_name

HTH
AM

---

### Post by vixenk on 2006-11-06
Instead of > xp_ip_address can I use an IP range? i.e. 192.168.15. instead of 192.168.15.12 or something?

---

### Post by vixenk on 2006-11-06
I went ahead and tried the IP range thing... it didn't work and I got the same error message I got whenever trying to access MSHOME.

Like I said though the LAN IPs are not static, so trying to pin one of the computers down via its LAN IP is pretty useless. The next day it will be something different.

---

### Post by amohanty on 2006-11-06
The hosts file cannot accept a range. it basically maps a string rep of an ip.

Typically if the router has been setup as default dhcp the lease will not expire for almost 200 days and even then, it tends to stay the same unless the number of hosts on the network is 'relatively' close to 255. So for all practical purposes you do have an almost static ip. This all assumes a default setup. The dhcp server can be configured to have a shirter lease.

Of course if you can somehow finagle a static ip (yes they can co-exist) and it will look and feel like a dynamic ip (ie in the 192.168... subnet) for your machine that would work too. 

HTH
AM

---

### Post by vixenk on 2006-11-06
Ok, the router's default is 1 day. The max it will go up to is about 1 week. The client lease time is configured by minutes, with 0 equaling one day and the max being 9999 minutes. Right now the max number of IPs is set to 50.

Past experience has taught me that it does change the IPs out daily.

Believe me, if the WinXP machine was mine it would have a static IP as well as this one. But the person it belongs to doesn't like having a static IP and will change it back to DHCP should they find out it's set to static. 

Thanks for all your help. However, I'm really starting to think I'm pretty much screwed on this one.

---

### Post by amohanty on 2006-11-06
Look into **arp**. You can map the ethernet address (MAC address ) to a hostname and then discover its IP via a script. You could potentially have a cron job to regularly update your hosts file :)

thats what hacking is all about after all... scratch an itch :)

Try: **arp -a** and see if the IP and MAC addy of the XP box pop up.

**rarp** might come in handy too.

Man I keep remembering things: look at **fping** and **nmap** too

HTH
AM

---

### Post by vixenk on 2006-11-06
No.

There is no logical reason why I should have to go through all of that. I would, should it actually be *neccessary*, but I know it's not. There's a glitch somewhere in smb.conf, and I would rather fix it than jump through hoops trying to work around it.

---

### Post by amohanty on 2006-11-06
Not really.. not unless you want to configure your router as a DNS server too. The IP to hostname mapping is for a dns server to satisfy and if the ip keeps changing, unfortunately theres not much the samba or anything else (other than a dns server) can do. 

You could query the dhcp server, unfortunately the on-table routers do not really have a full blown dhcp server on them, so are quite useless from a query point of view.

Best of luck.

AM

---

### Post by Eric Boring on 2006-11-07
Hi,

Sorry to but in here, but I wanted to thank you guys for carrying out this conversation on the board. I have been having a similiar problem between XP and Samba on Ubuntu. I'm at work now, but I am going to check into Firestarter when I get home tonight. 

One question I hope you might be able to help me with:
Is Firestarter installed and turned on by default in Ubuntu? I started with an Xubuntu install and then added the Ubuntu desktop. It seems that I'd read somewhere that Ubuntu didn't consider a firewall necessary for a Linux box. Also, where would I look for that app. (I'm quite new to Linux and Ubuntu, but having a great time learning how to use the terminal and such.)

Thanks again for making this all public!

-Eric

---

### Post by amohanty on 2006-11-07
No. AFAIK firestarter is not installed or turned on by defualt. To see if it gets loaded when you startup, look in the System->Administration->Services app or in /etc/init.d

HTH
AM

---

### Post by Eric Boring on 2006-11-07
OK, this may be a bit off topic, but do you suppose my wireless router's firewall would be trying to keep my machines from talking?
Thanks,

EB

---

### Post by amohanty on 2006-11-07
Possible but highly unlikely. Can you ping your router and all machines from one another. 
On ubuntu Applications->Accessories->Terminal
ping <router_ip_address>
ping <xp_ip_address>
skip the '<' nad '>'

Same in a command window in xp
If yes, no your router is not blocking traffic.

AM

---

### Post by Eric Boring on 2006-11-07
I have not tried to ping the router, but I was successfully pinging the Ubuntu machine from the XP machine while troubleshooting my Samba server. Perhaps I'll try to post my config file here tonight, since it sounds as though VK has resolved his problem. Would you mind taking a look at it?

Thanks much. If you're tired of troubleshooting Samba setups, I'd totally understand. Let me know.

EB

---

### Post by amohanty on 2006-11-07
sure why not :)

---

### Post by vixenk on 2006-11-07
I have not had this problem in previous distros, which is why I believe it has something to do with the configuration of smb.conf. Either way it's fixed now - one of my old distro forum's members was kind enough to post the default smb.conf file from it and I borrowed from it to patch together a new configuration. :)

---

### Post by amohanty on 2006-11-07
Could you possibly post that file.

Am

---

### Post by Eric Boring on 2006-11-08
Hi,

Well, I got my Shares to work last night, without any changes to the file. It continued to work after several Windows restarts, and even worked this morning. I haven't restarted the XUbuntu box since getting it to work, but so far so good. 

I have only one theory as to why it worked this time and why I kept breaking it this weekend:

Before, I could not get the XP machine to see the Xubuntu machine by its name, only by IP address. So I would map a drive by IP, and then I'd try mapping it by name, and it would find it. THen I'd restart and neither would work, nor could I repeat the process, except by seemingly random accident.

This time, I just mapped it by IP and left it at that, never worrying about the named connection. (I believe that my DSL router is essentially giving each box a static IP via DHCP)

Does it make sense to you guys that this scenario would be breaking my samba connections?

(By the way, I also was able to install the CUPS printer hooked up to my Xubuntu box. I think the problem there was just naming the computer properly. I finally simply took the address from the CUPS admin page and used that to name the printer.)

Anyway, thanks for all the info, I'll let you know if it's broken again tomorrow. ;) 

-E

---

### Post by amohanty on 2006-11-08
[http://en.wikipedia.org/wiki/Hosts_file](http://en.wikipedia.org/wiki/Hosts_file)

---

### Post by Eric Boring on 2006-11-08
So..... if I read that and understood it right (a big if, by the way), I was messing up the hosts file by putting both of them in there? Would it then reset itself after a few hours and I could start the vicious cycle all over again? Interesting....

An a tangential note, since I apparently don't have a firewall on the xubuntu machine, should I think about installing one? The DSL router has a firewall as well, is that sufficient?

Thanks for all the infos. 

E

---

### Post by vixenk on 2006-11-09
> Could you possibly post that file.

Sure. :)

```
*******************section global*****************
[global]

# Do something sensible when Samba crashes: mail the admin a backtrace
panic action = /usr/share/samba/panic-action %d
printing = cups
workgroup = no mepisgrp
server string = %h server (Samba %v)
hosts allow = 192.168.0. 192.168.1. 192.168.2. 192.168.79. 127.
socket options = IPTOS_LOWDELAY TCP_NODELAY
log level = 1
dead time = 15
wins support = yes
hide unreadable = yes
passdb backend = tdbsam guest
dns proxy = no
max log size = 1000
security = share
restrict anonymous = no
domain master = no
preferred master = no
max protocol = NT
ldap ssl = No
server signing = Auto
oplocks = No
level2 oplocks = No
;*******************section kerry*****************
[kerry]
comment = /home/kerry
path = /home/kerry
guest ok = yes
read only = no
;*******************section homes*****************
[homes]
comment = Home Directories
browseable = no
read only = no
;*******************section printers*****************
[printers]
comment = All Printers
path = /tmp
browseable = no
printable = yes
guest ok = yes
create mode = 0700
```

---

### Post by amohanty on 2006-11-12
Hey wait a minute!!!! hes got security=share and guest ok = yes everywhere (well almost everywhere :) ) + hes turned off restric anonymous. Sure you can do that... but that opens up your machine to anybody and everybody in your wireless range. 

But on the other hand if it does what you want more power to you.
<thumps himself on the head> should have thought of that.

Thanks.
AM

---

### Post by vixenk on 2006-11-12
> Hey wait a minute!!!! hes got security=share and guest ok = yes everywhere (well almost everywhere ) + hes turned off restric anonymous. Sure you can do that... but that opens up your machine to anybody and everybody in your wireless range.
First off, I'm not using wireless. Second, that's why you restrict access to only your IP subnet in Samba and in your firewall settings (iptables, firestarter, guarddog, whatever). :)

Anyways, I don't allow write access to my shares and my shares aren't confidential or anything so *shrug*.

---

