---
title: "I can't see WinXP shared folders on my desktop from my ubuntu laptop"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by xcesarfrancox on 2008-07-05
Hi everyone, I have this problem:

I have samba installed, I have both computers on the same Workgroup, and named desktop and laptop respectively, but when I got to Places -> Network -> Windows Network -> Desktop none of my shared folders on XP are shown from Ubuntu

Also, If I try to share folders from Ubuntu, I see them from XP, but when I try to open them, I'm prompted for user/password, so I write in my ubuntu user and password, but the prompt shows up again...

I'm trying to have all of my media files stored on my desktop, and listen to music or watch videos in my laptop over the lan or wlan, some kind of media server... but I need the desktop to be the server, and I need it to be Windows XP... I need to be able to see my Music and Videos folder from my laptop

EDIT: Here's my smb.conf file:
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
   workgroup = MATUTE

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


```

---

### Post by xcesarfrancox on 2008-07-06
***BUMP***

Please people, I have reinstalled both windows and ubuntu and everything's the same, I can't share files between my desktop and my laptop...

---

### Post by Drate on 2008-07-09
I'm still trying to see shared files on my LOCAL computer, not even gotten to including another computer yet... mine keeps saying "can't retrieve share list from server"...

Evidently the developers removed the working file sharing system and replaced with a less than working nautilus-share.  I'm not quite sure why yet...

---

### Post by superprash2003 on 2008-07-09
you need to add samba users firstly and the change 
; security = user

to 
 security = user

remove the ; .. to add samba user and place it in the /etc/samba/smbusers file please refer here [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by xcesarfrancox on 2008-07-10
> **superprash2003 said:**
> you need to add samba users firstly and the change 
; security = user

to 
 security = user

remove the ; .. to add samba user and place it in the /etc/samba/smbusers file please refer here [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

As you may find on my first post, I actually can access to my linux shared folders from windows without any trouble, but I can't do the same from linux, I have installed smbclient, smbfs and samba packages, but even trying to browse to the desktop by the IP I can't...

I will post some screenshots:

**Places -> Network:**
[IMG]http://img73.imageshack.us/img73/1456/pantallazorednavegadordho1.png[/IMG]

**Opening Windows Network:**
[IMG]http://img510.imageshack.us/img510/5402/pantallazoreddewindowsnww4.png[/IMG]

**Going inside "CASA" Workgroup:**
[IMG]http://img68.imageshack.us/img68/9145/pantallazocomparticionepo2.png[/IMG]

**Opening desktop shares (trying with the desktop IP instead of hostname I get same results, and IP responds to ping):**
[IMG]http://img68.imageshack.us/img68/6720/pantallazocomparticionesl5.png[/IMG]

_And some screenshots from Network Places in windows:_

**Windows Network:**
[IMG]http://img55.imageshack.us/img55/677/windowsnetworkaa4.jpg[/IMG]

**"CASA" Workgroup:**
[IMG]http://img295.imageshack.us/img295/9457/casaworkgroupnf5.jpg[/IMG]

**Browsing my Ubuntu GNU/Linux Laptop:**
[IMG]http://img295.imageshack.us/img295/5797/laptopcomputerne7.jpg[/IMG]

**And Browsing my windows local shares:**
[IMG]http://img66.imageshack.us/img66/7670/desktopcomputermv6.jpg[/IMG]

My only choice so far is giving write permission to my linux shares so I can transfer files on both directions...

Also, I'd like to point out that I've tried both wireless and wired, and I get nothing different...

---

### Post by hroblesa on 2008-07-18
I'm new at the Ubuntu world but I had the same problem today while I was trying to share some files form my laptop (Win XP home) to my desktop (Ubuntu 8) and the cause of the problem was the firewall running on Win XP. 

If you have a firewall running maybe you can try turn it off. If it work you can still configure you firewall settings to have it running and be able to share you files between the PC.

---

### Post by Anthony M on 2008-07-18
I am having this exact problem.  Could you give an update this if you have made any progress?

---

### Post by xcesarfrancox on 2008-07-19
@hroblesa: I've tried with firewall disabled and I still have the same problems, I can't see the folders...

@Anthony M: Actually I found out in another thread, that I can access my shared folders by typing the entire path this way:

smb://(XP computer's IP)/(name of shared folder)

I have added the XP computer's IP in /etc/hosts file so I can use both the IP or the hostname, in this case the hostname is desktop, so if I have shared folder named stuff, I can access it by typing the following:

```
nautilus smb://desktop/stuff
```

but still, if I type
```
nautilus smb://desktop
```

it doesn't show any shared folders...

I haven't tried another file manager like thunar... it could be the file manager, I'll try and I'll post my results :)

---

### Post by rushikesh988 on 2008-07-19
> **hroblesa said:**
> I'm new at the Ubuntu world but I had the same problem today while I was trying to share some files form my laptop (Win XP home) to my desktop (Ubuntu 8) and the cause of the problem was the firewall running on Win XP. 

If you have a firewall running maybe you can try turn it off. If it work you can still configure you firewall settings to have it running and be able to share you files between the PC.


Brother I installed ubuntu on one computer into my brothers cafe it is taking all the files and folders from the windows network ..  and yes, I can use shared printer on samba (windows) in ubuntu 

I think you should check your network is Correct or not 

And if yes , 
then open SYSTEM-->ADMINISTRATION-->Network tools 
check out bytes traffic is occring or not??

---

### Post by xcesarfrancox on 2008-07-19
*** BUMP ***

I've tried with both Thunar and PC Man, but they don't seem to be able to use samba... so I tried with midnight commander from CLI and it shows the shared folders properly, so I guess my problem is related to nautilus instead of samba...

---

### Post by rushikesh988 on 2008-07-19
xcesarfrancox brother, you should check and configure  your network too!!


by the way , 
which medium you are using to connect your laptop and desktop??

---

### Post by xcesarfrancox on 2008-07-19
I use both wired and wireless, but I can't see my XP shared folders unless I do it the way I said in my previous post, I have to type the hole path to the folder, weird, isn't it???

---

