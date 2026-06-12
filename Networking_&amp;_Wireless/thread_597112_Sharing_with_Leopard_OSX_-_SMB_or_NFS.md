---
title: "Sharing with Leopard OSX - SMB or NFS"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by JungMin on 2007-10-30
OK,

Well, I was previously using Tiger OSX and I was able to access the SMB shares on my Feisty box.  I just upgraded to Leopard and I can now not connect to the SMB shares.  NFS shares would be alright too (Leopard can now automount them)

I need the shares to be public (no password) as my media player access the share and does not allow me to enter usernames and passwords.

But when I try to connect to the share, Leopard asks for a username and password - But there isnt one!!  And if I try to access them as a guest, it says that the server doesnt accept guests.

Here is my smb.conf.  I have been playing around with security = user, encryped passwords, guest acces, but all no luck.  

Also, I tried setting up NFS shares so my media player could access them, it works (no username or password needed), but if I try to connect to them with Leopard it says a password or username is incorrect.

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
;  security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
 
   encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

   guest account = yes
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

[Other]
path = /media/hdc1
available = yes
browsable = yes
public = yes
writable = yes

[Media]
path = /media/hdd1
available = yes
browsable = yes
public = yes
writable = yes

[MP3's]
path = /media/hdc1/MP3's
available = yes
browsable = yes
public = yes
writable = yes

[Photo's]
path = /media/hdc1/Photo's
available = yes
browsable = yes
public = yes
writable = yes

[Storage]
path = /media/hdb1
available = yes
browsable = yes
public = yes
writable = yes


[Media2]
path = /media/hda5
available = yes
browsable = yes
public = yes
writable = no
```

Cheers, thanks for any help you can give.

---

### Post by JungMin on 2007-10-30
This has really got me stumped.  I can access the shares via my media player perfectly fine.  It's just accessing them through my MacBook running Leopard - It wants to use a username and password!?!?

---

### Post by dacap06 on 2007-10-30
According to my reading of your /etc/samba/smb.conf file, you need to make the following changes in it:

1.  change security=user to say security=share

2.  comment out    "passdb backend = tdbsam" and "obey pam restrictions = yes"

3.  Add a line saying "map to guest = bad user"

4.  Comment out the lines beginning    "passwd program =" and "passwd chat = "

5.  In your specific shares, you use "writeable = yes" while I use "read only = no".  I expect that once you get past the password stuff, your shares will work fine.  If you find you can read but not write, try changing this line.

I hope I found everything.  Good luck!

---

### Post by JungMin on 2007-10-31
Brilliant dude!!!!!!  Thank you SOOO MUCH!!  It's been a frustrating go, but it works perfectly.  

Just needed to change #'s 1 ~ 4.  

I really appreciate it.....Thanks a million.   I'd buy ya a beer, but well.....you prolly don't live in Seoul.

Again, much appreciated!!!

---

### Post by LadyFox on 2007-10-31
Oh my lord - thanks for this fix,  dacap06!

Recently got Leopard myself and couldnt figure out why i couldnt connect to my shares!  Cheers!

---

### Post by xyverz on 2007-11-01
*snip* I read this thread the wrong way.  Removing my posts.

---

### Post by xyverz on 2007-11-02
*snip!* I read this thread the wrong way.  Removing my posts.

---

### Post by dacap06 on 2007-11-04
> **JungMin said:**
> I'd buy ya a beer, but well.....you prolly don't live in Seoul.
Again, much appreciated!!!

LOL.  I'd except but I'm half way 'round the world.  You'll just have to drink it for me.  Cheers!

DaCAP

---

### Post by Usey User on 2007-11-05
Hello,

I also just upgraded to Leopard and Gusty Gibbon.  I can still access my shared folders on Leopard from Ubuntu, but when I try to access shared folders on Ubuntu from Leopard, I keep getting "sorry, you have entered an invalid username or password" .  Here's my smb.conf:
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
	workgroup = mshome

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;	wins support = no

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
;	syslog only = no

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
;   security=share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
#  passdb backend = tdbsam

#   obey pam restrictions = yes

;	guest account = nobody
	invalid users = root

# Added November 5 7:00PM by Aaron 
;	map to guest = bad user

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;	unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
#   passwd program = /usr/bin/passwd %u
#   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;	pam password change = no

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
;	logon path = \\%n\%u\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;	logon home = \\%n\%u

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
;	load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;	printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
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
;	socket options = tcp_nodelay

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;	domain master = auto
	username map = /etc/samba/smbusers
	security = user
;	guest ok = no

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
# This might need tweaking when using external authentication schemes
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
;	public = no
;	writable = No
	create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
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
	security = share

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





[myusername]
	path = /home/myusername
;	available = yes
;	browseable = yes
	guest ok = yes
	

available = yes
browsable = yes
public = yes
writable = yes

[File System]
path = /
available = yes
browsable = yes
public = yes
writable = yes
```

I've tried dacap06's fix but no luck.  I've only been using Ubuntu since 6.06 so any help would be appreciated.  

Thanks in advance!

---

### Post by kitsos on 2007-11-09
your file has two lines for the security option: security = user and security = share further down. You need to make sure it has only one. 

Have you tried using smbclient to connect from your mac to ubuntu? If you can't connect with smbclient, that means that your SAMBA server is not set up right. R u running a firewall in ubuntu?

I had the same problem and the above fix worked. However, I managed to make it work with security =user. Apparently the problem is the password. Apple's version of samba on leopard cannot handle characters like %. Keep it plain and simple with characters and numbers and it should be fine! Now that's what I call security :lolflag:

---

### Post by Usey User on 2007-11-13
THANKS!!!\\:D/
I've even got secure screen sharing working.
Again, thanks for helping my upgrade to Gusty and Leopard smoother.

---

### Post by vcasinha on 2008-01-18
> **dacap06 said:**
> According to my reading of your /etc/samba/smb.conf file, you need to make the following changes in it:

1.  change security=user to say security=share

2.  comment out    "passdb backend = tdbsam" and "obey pam restrictions = yes"

3.  Add a line saying "map to guest = bad user"

4.  Comment out the lines beginning    "passwd program =" and "passwd chat = "

5.  In your specific shares, you use "writeable = yes" while I use "read only = no".  I expect that once you get past the password stuff, your shares will work fine.  If you find you can read but not write, try changing this line.

I hope I found everything.  Good luck!

This worked perfectly for me too. :)
thanx man I was going crazy with this problem.

---

### Post by YoG%*@ on 2008-01-19
> **vcasinha said:**
> This worked perfectly for me too. :)
thanx man I was going crazy with this problem.


yes, thanks a lot, you saved me a lot of trouble. and from going mad over this... =)

---

### Post by mb108 on 2008-02-03
Another thanks here, changes 1-4 got Samba for Leopard/Gutsy working perfectly!

---

### Post by hipotermia on 2008-02-13
what does it mean comment out in g33k language?

:|

---

### Post by jetsam on 2008-02-13
hipotermia,

In this case, add a **#** or a **;** at the beginning of a line in the configuration file so that samba acts as if the line doesn't exist when it reads the file.  

Different programming languages and configuration files use different syntaxes for comments, but a '#' to comment out a line is a very common syntax in linux configuration files.  

It gives you the flexibility to take out the '#' later if you want to uncomment the line.

---

### Post by ejdanker on 2008-02-17
This thread has been a godsend.  I've been banging my head up against this very same problem.  Followed the instructions above and bingo!...everything worked.  Thanks!

---

### Post by failo on 2008-05-07
I tried your guide but it didn't help at all. Did all the following steps but with no luck. I switched fro Tiger to Leopard recently and have the same problem described in the first post - can not connect to shares which have no password set. I post my smb.conf in txt format, did try to change something with commenting out but as I said before with no luck. Running 10.5.2.
Thanks for nay help!

---

### Post by antwerx on 2008-05-17
Yet another Kudos for this post.  I too have benefit form this post. 

Thank you for sharing. :)

---

