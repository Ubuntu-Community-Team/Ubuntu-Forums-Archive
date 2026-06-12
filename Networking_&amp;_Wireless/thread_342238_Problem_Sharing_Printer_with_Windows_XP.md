---
title: "Problem Sharing Printer with Windows XP"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by craz on 2007-01-19
I set up my printer to work with SAMBA.  The printer is set to share, and I have followed all of the instructions to let me use my linux printer from my Windows XP box.  When I try to set up the printer on the XP machine, my linux computer shows up under the workgroup, but the printer does not show up under the computer.  I cannot figure out why this is.  The XP machine sees the linux computer but not the printer.  Any ideas?

---

### Post by puneit on 2007-01-19
Can you briefly explain how did you set up the printer for sharing. Printer sharing works for me...
What I have done is in System --> Administrator --> Printer
On the Global Settings check share printers


Also can you post the copy of the samba.conf file 
You can find smb.conf file. ```
gedit /etc/samba/smb.conf
```
Copy the contents and paste here

---

### Post by craz on 2007-01-20
I followed this guide to set up SAMBA. 
[http://www.debian-administration.org/articles/425]("http://www.debian-administration.org/articles/425")
I can access files on the XP machine from my Ubuntu machine ok.
I do have Global Settings set to share printers.

Here is the smb.conf file:

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
   workgroup = BERUBE

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

[printers]
  browseable = yes   
  printable = yes   
  public = yes   
  create mode = 0700   
  guest only = yes   
  use client driver = yes
  guest account = smbprint   
  path = /home/smbprint 

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

Thanks. :)

---

### Post by craz on 2007-01-21
Well I am still having no luck.  Any ideas?

---

### Post by SwishyStudios on 2007-01-23
I think I just solved the same problem on my machine!  Check out Mitch.C's repsonse on this here...

[http://ubuntuforums.org/showthread.php?t=268245](http://ubuntuforums.org/showthread.php?t=268245)

Good luck!

---

### Post by craz on 2007-01-23
Thanks, that partially worked.  Now it asks me to use either an anonymous account or a username and password, like stated by some others.  Root and my username does not work. It just says "You do not have access to the printer, please try a different username or password."  I tried logging in as smbprint also and it did not work.  What do I do now?

Also, here is my smb.conf file:
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
   workgroup = BERUBE

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

[printers]
  browseable = yes   
  printable = yes   
  public = yes   
  create mode = 0700   
  guest only = yes   
  use client driver = yes
  guest account = smbprint   
  path = /home/smbprint 

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

### Post by craz on 2007-01-23
Also, when I try to share files, I can access the Windows XP computer from the Ubuntu and transfer files fine, but when I try to access the Ubuntu from the Windows XP, the computer shows up in the workgroup but it says that it is not accessible and that I may not have permissions to use the network resource.  The network path was not found.

So this, and the printer problem :( 
Any ideas?
THANK YOU!

---

### Post by SwishyStudios on 2007-01-24
Try this out...I'm pretty sure I had the same problem and this fixed it.  Make sure you're in Root and type this into the terminal...

```
sudo smbpasswd -a user
```

That allows you to set a username and password for Samba which can then be told to the Windows XP computer.

Worked for me!  I hope it does for you too!

---

### Post by craz on 2007-01-24
I replaced user with my own username...not sure if this is the right thing to do, since there is no user named user.  I think I have tried this before, not sure.  I went to try it again, but now on the Windows XP machine, it recognizes there is a printer there but it spits out an error message "Windows could not connect to the printer.  Operation could not be completed."  Nothing has changed from the other day either.  I also cannot access my Ubuntu files from the XP computer.  What is going on?  This shouldn't be so hard.. :(
Thank you for the help though, I really need it.

---

### Post by SwishyStudios on 2007-01-24
I think you probably already know this, but just to be sure, the username and password that you set for Samba have nothing to do with the username and password for your computer.

In other words, Windows doesn't care what you log into Ubuntu as, it only wants to know the username and password you set for Samba

You probably already knew that but if not that could do the trick!!

---

### Post by craz on 2007-01-24
Well I did BUT I was trying to use my Ubuntu login with a SAMBA password..Do I need a special SAMBA user?  If so how do I make one?

Also, I am still getting the "Windows could not connect to the printer. Operation could not be completed." message, which I did NOT get yesterday.  So I cannot test this.

---

### Post by SwishyStudios on 2007-01-24
I may be wrong on this,  but I think that your Samba username will now be "user".  If you were able to create a password with that last code I sent, it probably created it for the username "user"

See if that works on XP, and if not, this should tell you everything you would ever need to know about Samba!!

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

As far as the printer goes, I'm not sure what would cause the error.  When I set mine up though, I went into my XP web-browser and typed in [http://192.168.0.105:631/printers/](http://192.168.0.105:631/printers/) (assume that that is your IP address for the Ubunto computer) and found the printer address that way.  Before that I had trouble finding out exactly what the path was!!

I really hope that helps!

---

### Post by SwishyStudios on 2007-01-24
Hang on a second, maybe your Samba password is associated with your login name like you assumed a few posts ago?  And all you have to set is the password for Samba?  In that case use...

> sudo smbpasswd -a [your username]

And then set the password.  I bet that's what you already did!!  I've honestly only been using Ubuntu for a couple days so this is all confusing me too!!  Sorry if I've thrown you off

Best of luck, I hope that that link helps you!

---

### Post by craz on 2007-01-25
Not sure..thanks alot for the replies.  I still am not able to get XP to connect to the Ubuntu printer, even though it recognizes that it is there.  Funny, because it connected fine just a couple days ago and nothing has changed.

---

### Post by DoorGunner on 2007-01-26
I just did mine using instructions from this site. It works well. 

All you have to do is save your current smb.config and replace it with the simple suggested one. and follow instructions on the cups config. 

[http://www.enterprisenetworkingplanet.com/netsysm/article.php/3621876](http://www.enterprisenetworkingplanet.com/netsysm/article.php/3621876)

Hopefully it helps

---

### Post by craz on 2007-01-26
Thanks, I tried that.  No luck.  Many people have had this problem, but no solutions are working for me.  I dont have any firewalls on and I have tried myriads of different smb.conf files - and yes i restarted the service.  Nothing works.  The XP computer recognizes the Ubuntu computer but it wont connect.  It says it cannot connect to the printer and network path cannot be found when I try to access my Samba share.  Can anyone offer any insight?  I would be very grateful.

---

### Post by DoorGunner on 2007-01-27
If you followed the last instructions and go to My Network Places... what do you see?

Lets try to get Samba working first then we can adjust your cups and dll files as required.

Right now i am looking for any indication that samba might provide in My Network Places. You may have a popup for a password..... or a Share1 file that appears there.

Dont forget. Sometimes it may take a couple of minutes for the network to broadcast its changes.

---

### Post by craz on 2007-01-28
I have followed all instructions.  In My Network Places I see Lan File and Printer Server (Ubuntu).  When I click on it to access the share it says it is not accessible, I might not have correct permissions, the network path was not found.  When I browse printers in XP the printer does not show up, but the computer does recognize it when I type in the address manually, but it gives me the error message "Cannot connect to printer.  Operation could not be completed."  It didn't used to do this - it would ask for a username and password.  For some reason it stopped doing that and it now gives me that error message.  This was before I followed those instructions.  It still does not work.  All printer drivers compiled successfully on the Ubuntu machine.

---

### Post by DoorGunner on 2007-01-28
mine asked for a password as well
it can be turned off in the /etc/samba/smb.conf by doing the following
> 
[global] 
security = user 

change it to read

security = share


then 
> # sudo /etc/init.d/samba restart

so far it looks as though your samba is working as advertised with the acception of some fine tuning.

Once we get rid of the password issue we can work on cups if needed. 

3 questions

1.   What do you see now in My Network Places?

2.   Were you able to get the cups.dll files installing in windows?

3.   Are you on a wireless router?

---

### Post by craz on 2007-01-29
1. In My Network Places I see Lan File and Printer Server (Ubuntu).  Cannot access this.
2. No, because the XP computer will not connect to the printer, but it realizes that its there.  The driver IS compiles under /etc/cups/drivers on Ubuntu machine.  Printer still does not show up under browse printers in XP even though it is set up to.
3. Yes, I am on a wireless router.  Wireless G.

---

### Post by DoorGunner on 2007-01-29
Be aware that the add printer option is extremely slow in most cases. And can give a lot of grief. However, once you do get your printer you can get going. 

Ok Im assuming at this point you have cups printers in
/usr/share/cups/drivers...
and in windows C:\WINDOWS\system32\spool\drivers\w32x86\

your should see several cups*.dll files there and you should confirm that. if not let me know.

Here is my cups config file
Save your config somewhere if you want to try mine.
---------------------------------------------------------------------------------------------------
> 
# Show general information in error_log.
LogLevel info
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow localhost
  Allow 192.168.1.*	
</Location>
<Location /admin>
AuthType Basic
AuthClass System
  Allow From 127.0.0.1
  # Restrict access to the admin pages...
  Order allow,deny
Deny From All
</Location>
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  # Restrict access to the configuration files...
  Order allow,deny
  Allow localhost
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  # Only the owner or an administrator can cancel a job...
  <Limit Cancel-Job>
    Order deny,allow
    Require user @OWNER @SYSTEM
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

mime.convs:

# The following line is found at near the end of the file. Uncomment it.
application/octet-stream        application/vnd.cups-raw        0       -

mime.types:

# Again near the end of the file.
application/octet-stream  

-----------------------------------------------------------------------

as well in /etc/cups/mime.convs and /etc/cups/mime.types should reflect the last lines here.
ensure they are uncommented

then reboot

sudo /etc/init.d/samba restart
sudo /etc/init.d/cupsys restart

---

### Post by craz on 2007-01-30
The printer drivers are in those locations.  My cups file has those octet-stream lines uncommented at the end.  I tried yours too but the same error occured, so I switched back to mine, which did work once.  Could it be a problem on the Windows side?  There are no firewalls on during this process and the router is not blocking anything.

---

### Post by DoorGunner on 2007-01-31
Just to let you know that I do have wireless g. I think that yours works. Any time ive tried to modify it .... it will seem to take forever. Once it is set up it locks on like a pit bull and you will never have a problem.....just when you try to set everything up..... sometimes i find by shutting everything down and starting it up it seems to help.... the service not my patients...LOL

---

