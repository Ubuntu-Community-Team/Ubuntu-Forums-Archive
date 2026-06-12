---
title: "[SOLVED] Samba Error"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by jose158 on 2008-02-02
When I try to connect to my brother's laptop, it gives me this error:```
**The folder contents could not be displayed.**
Sorry, couldn't display all contents of "Music".
```Any ideas?

---

### Post by jose158 on 2008-02-03
Any ideas?

---

### Post by swerdna on 2008-02-03
> **jose158 said:**
> Any ideas?
I imagine one is Linux, maybe both?? More info please:
What's running on your computer. What's running on bro's laptop?
And
Please post the contents of bro's smb.conf if it's Linux and of your computer's smb.conf if it's linux.

Before that make sure the line:
**workgroup = whatever_is_workgroup_name_on_laptop**
exists in [global] of your smb.conf (located at /etc/samba/smb.conf) if it's Linux.
Together with the line:
**name resolve order = bcast lmhosts wins host**
and if there's a share on your box and if it's Linux then this line too:
**netbios name = whatever_you_want_the_box_to_be_called_on_the_network**

And reboot both boxes then wait 5/10 minutes

Swerdna

---

### Post by jose158 on 2008-02-03
> **swerdna said:**
> I imagine one is Linux, maybe both?? More info please:
What's running on your computer. What's running on bro's laptop?
And
Please post the contents of bro's smb.conf if it's Linux and of your computer's smb.conf if it's Linux.

Before that make sure the line:
**workgroup = whatever_is_workgroup_name_on_laptop**
exists in [global] of your smb.conf (located at /etc/samba/smb.conf) if it's Linux.
Together with the line:
**name resolve order = bcast lmhosts wins host**
and if there's a share on your box and if it's Linux then this line too:
**netbios name = whatever_you_want_the_box_to_be_called_on_the_network**

And reboot both boxes then wait 5/10 minutes

SwerdnaBoth are running Mint. Nothing is running on either computers. Do you want me to post the whole Smb.conf or just a specific part?

---

### Post by swerdna on 2008-02-03
> **jose158 said:**
> Both are running Mint. Nothing is running on either computers. Do you want me to post the whole Smb.conf or just a specific part?
Both :)

PS I assume Samba is installed and running. If not then do that. Can check with **sudo /etc/init.d/samba start** and see if it says OK

---

### Post by jose158 on 2008-02-04
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

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = azlan

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;    wins support = no

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
;    syslog only = no

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
    security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;    encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
    passdb backend = tdbsam

    obey pam restrictions = yes

;    guest account = nobody
    invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;    unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;    pam password change = no

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
;    logon path = \\%n\%u\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;    logon home = \\%n\%u

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
;    load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;    printing = bsd
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
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
;    socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;    domain master = auto

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
;    browseable = yes

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
    writable = yes
    username map = /etc/samba/smbusers
;    guest ok = no

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
;    public = no
;    writable = no
    create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
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
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[Network]
    path = /home/jose/Network
;    available = yes
;    browsable = yes
    public = yes
;    writable = no

available = no
browsable = no
writable = no
[To-Share]
    path = /home/jose/To-Share
;    available = yes
;    browsable = yes
    public = yes
;    writable = no

available = no
browsable = no
writable = no
[Movies]
    path = /home/jose/Videos/Movies
;    available = yes
;    browseable = yes
    guest ok = yes
    
available = yes
browsable = yes
public = yes
writable = yesThere is both of our computer's smb.conf
P.S Sorry for the big file.

---

### Post by swerdna on 2008-02-05
If you want to cut through the comments and other spurious stuff in a Samba config file run this and collect the output in a file smb.conf.txt on your desktop:
**testparm /path_to/smb.conf > /home/yourname/Desktop/smb.conf.txt**

I did that on your smb.conf and here's what it really contains, junk removed:
> [global]
	workgroup = AZLAN
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	read only = No

[printers]
	comment = All Printers
	path = /tmp
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Network]
	path = /home/jose/Network
	read only = Yes
	guest ok = Yes
	browseable = No
	available = No

[To-Share]
	path = /home/jose/To-Share
	read only = Yes
	guest ok = Yes
	browseable = No
	available = No

[Movies]
	path = /home/jose/Videos/Movies
	guest ok = Yes

Point 1: [global] is missing two of the three very important lines I advised you about in my previous post. Your network won't work reliably without them.

Point 2: the line in [global] **read only = no** will make all shares writeable by default, a bad idea.

Point 3: The lines **available = no** will switch off [Network] and [To-Share], probably as intended. So don't look for either of those on the network.

Point 4: The remaining share, [Movies] is a classic, world-readable, writeable share (good for media sharing where you can drop media into it across the network as welll as copy it out).

OK, so that implies the following clean-up file for smb.conf:
```

[global]
	workgroup = AZLAN
	server string = ""
	obey pam restrictions = Yes
	passdb backend = tdbsam
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
        name resolve order = bcast host lmhosts wins
        netbios name = whatever_you_want_the_box_to_be_called_on_the_network
        socket options = IPTOS_LOWDELAY TCP_NODELAY


[printers]
	comment = All Printers
	path = /tmp
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Network]
	path = /home/jose/Network
	read only = Yes
	guest ok = Yes
	browseable = No
	available = No

[To-Share]
	path = /home/jose/To-Share
	read only = Yes
	guest ok = Yes
	browseable = No
	available = No

[Movies]
	path = /home/jose/Videos/Movies
	guest ok = Yes
        read only = no
        force user = jose
```

You should copy that to smb.conf in /etc/samba/smb.conf, changing the netbios name appropriately. BE SURE to make the permissions on folder "Movies" to be drwxrwxrwx.
Reboot all the machines consecutively, doing the first one twice, one at beginning and once at end. There may then be a 5/10 minute wait for seep around network.

Your original smb.conf file is wrecked, so I've attached a copy to archive in folder /etc/samba/

You chould add jose to the Samba user database. Add jose like this in a terminal: **sudo smbpasswd -a jose**

Swerdna

---

### Post by jose158 on 2008-02-05
```
BE SURE to make the permissions on folder "Movies" to be drwxrwxrwx.
```What do you mean?

---

### Post by swerdna on 2008-02-05
> **jose158 said:**
> ```
BE SURE to make the permissions on folder "Movies" to be drwxrwxrwx.
```What do you mean?

I'm sorry, that's wrong. I got confused because:
There are two ways to make the share writeable to a guest. One is to make every guest imitate and have the powers of the Linux owner of the folder (force user = jose). The other is to make the folder writeable for "group" and "others" (jargon is drwxrwxrwx). To do the latter you issue the command **chmod 777 /home/jose/Videos/Movies**. But my error was that I forgot I had already prescribed the force user alternative (which makes drwxrwxrwx unnecessary). So FORGET IT. :)

---

### Post by jose158 on 2008-02-05
> **swerdna said:**
> I'm sorry, that's wrong. I got confused because:
There are two ways to make the share writeable to a guest. One is to make every guest imitate and have the powers of the Linux owner of the folder (force user = jose). The other is to make the folder writeable for "group" and "others" (jargon is drwxrwxrwx). To do the latter you issue the command **chmod 777 /home/jose/Videos/Movies**. But my error was that I forgot I had already prescribed the force user alternative (which makes drwxrwxrwx unnecessary). So FORGET IT. :)oooooooh:o! Well for some reason, We can't see eachother's computers, was I suppose to change the smb.conf on BOTH computers? Cause I did only on mine.:)

---

### Post by swerdna on 2008-02-05
> **jose158 said:**
> oooooooh:o! Well for some reason, We can't see eachother's computers, was I suppose to change the smb.conf on BOTH computers? Cause I did only on mine.:)

Set them both up similar to each other. Can make the other shared folder /home/jose/etc_etc or someone else. But if someone else the change "force user = jose" on the seconf machine appropriately.

---

### Post by ChameleonDave on 2008-02-09
I'm trying to network two PCs together too (each dual-boots into Ubuntu or XP), and none of this works.

---

### Post by jose158 on 2008-02-09
THANK YOU I finally got it working!

---

### Post by swerdna on 2008-02-09
Very glad. Good for you!

Swerrdna

---

