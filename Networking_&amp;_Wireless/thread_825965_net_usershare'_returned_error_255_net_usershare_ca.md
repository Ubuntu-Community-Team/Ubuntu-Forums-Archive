---
title: "net usershare' returned error 255: net usershare: cannot open usershare directory /va"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by Shoek on 2008-06-11
I try to share a folder by right clicking on it, then going to share. I get this error. 


'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.


What do I do?

---

### Post by jetsam on 2008-06-11
This is a known bug when you first install Samba on Hardy.  Restart and you should be able to share folders.  

More details are available in this thread:
[Simple File Sharing over a Home Network]("http://ubuntuforums.org/showthread.php?t=772706")

---

### Post by Shoek on 2008-06-11
Ok. I did that. Now I need to configure samba. I managed to find the config file, but it won't let me save it. Nor does it poke me for my password. Also, do you know where I can set this? Now I can't share my folder because of this.

'net usershare' returned error 255: net usershare add: cannot share path /opt/foldingathome as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

I tried finding it in smb.cof. But I don't see anything interesting when I do a ctrl f for usershare.

Here is my smb.conf:

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
;   security = share

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

Or should I make a new thread about this?

Edit:

I managed to save my file by using the command "gksu gedit /etc/samba/smb.conf". I still, however, need to do this.

'net usershare' returned error 255: net usershare add: cannot share path /opt/foldingathome as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

---

### Post by jetsam on 2008-06-11
I don't think you need to mess with the usershare settings in the smb.conf.  If you've restarted, the error message should no longer happen when you right click and try to share a folder.  The problem is a group membership issue, and should be fixed by the restart alone.  

Unless you run into further trouble, the only change I recommend you make to the smb.conf is to set your workgroup name correctly.  Change the workgoup in the line **workgroup = MSHOME** to your correct workgroup name.

Probably the reason you can't save the smb.conf is because you're not editing with gksu or sudo. 

Open a terminal and type:```
gksu gedit /etc/samba/smb.conf
``` 

You might want to backup the file before you make changes.  Again, from a terminal, you can do this with:
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.orig
```

---

### Post by Shoek on 2008-06-11
I have tried restarting (twice), after I edited the config file. But I still get the error. I tried doing what the error said litterally, so here's how my global looks like:

```
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

; "usershare owner only = False

#### Networking ####
```

That didn't solve it. The folder I'm trying to share is in /opt by the way.

---

### Post by jetsam on 2008-06-11
OK.  /opt/ is owned by root and should be, so I guess you need to do what you're doing if you really want to share it.

The problem now I think is you still have a **;** in the line **; "usershare owner only = False**.  This makes it a comment.  Try taking the **;** and the **"** out and saving, then restarting Samba with:

```
sudo /etc/init.d/samba restart
```

Is there any particular reason you want to share /opt/?  It's a pretty obscure part of the directory structure.

What is the folder you want to share?  Did you create it yourself?  Another, possibly better approach would be to change the ownership of the directory you are sharing.

---

### Post by Giak on 2008-06-12
Ok now it worked. Brilliant! :) The only thing was that I'd already set "security = share", but it still prompted me for a password the first time. That's ok, I solved it by allowing guest access for that particular folder. The reason I wanted to share a folder in opt is because [fah_install](https://help.ubuntu.com/community/FoldingAtHome#head-d40f4db6af2075cd654d647894fdb5ee931fbf91) set a program called Folding@Home there. As this is a server I wanted to share the results in my network so that I can monitor Folding@Home's progress from my XP machine. Thanks for the help, I really didn't expect to get an answer around here. :)

Edit: by the way I am Shoek, I don't know why I have two accounts here. But I changed my web browser now and the passwords didn't come with it so I searched for Ubuntu in my e-mail and this is what came up.

---

### Post by jetsam on 2008-06-12
Cool.  That's an interesting use for Samba.  Glad you got it working.  :)

Not all questions find answers on the forums, but it's amazing to me how many of them do.

---

### Post by pravinbravi on 2008-07-31
> **Giak said:**
> Ok now it worked. Brilliant! :) The only thing was that I'd already set "security = share", but it still prompted me for a password the first time. That's ok, I solved it by allowing guest access for that particular folder. The reason I wanted to share a folder in opt is because [fah_install]("https://help.ubuntu.com/community/FoldingAtHome#head-d40f4db6af2075cd654d647894fdb5ee931fbf91") set a program called Folding@Home there. As this is a server I wanted to share the results in my network so that I can monitor Folding@Home's progress from my XP machine. Thanks for the help, I really didn't expect to get an answer around here. :)

Edit: by the way I am Shoek, I don't know why I have two accounts here. But I changed my web browser now and the passwords didn't come with it so I searched for Ubuntu in my e-mail and this is what came up.

You can also install and try the following package 

```
sudo apt-get install system-config-samba
```a.k.a. Samba Server Configuration Tool 1.2.50

its a nice gui tool (repository present in hardy universe) for configuring and setting share in samba similar to editing samba.conf file.

GNOME menu listing: System>Administration>Samba

Enjoy!

---

### Post by zeezam on 2008-08-02
> **pravinbravi said:**
> You can also install and try the following package 

```
sudo apt-get install system-config-samba
```a.k.a. Samba Server Configuration Tool 1.2.50

its a nice gui tool (repository present in hardy universe) for configuring and setting share in samba similar to editing samba.conf file.

GNOME menu listing: System>Administration>Samba

Enjoy!

Omg, that was a brilliant tool. Glad I found this thread!

---

### Post by Zuuted on 2008-08-13
The samba server config tool is very handy as a GUI... but IMO the fastest way to setup a shared folder with any other comp/network access is via command line:

```

sudo su
net usershare add <sharename> <path>

```

you can also just type "net usershare" (without quotes of course) to get all the options and parameters for this utility.

---

### Post by liquidcable on 2008-08-23
Rebooting does not fix the problem on my machine, as I still get the same error.

```

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

```

---

### Post by prebbish on 2008-09-23
Damn, would have been nice to find that Samba Gui alot sooner... THX for the tip

---

### Post by wishes on 2008-09-24
basicly the directory isnt there or isnt readable.
the easy fix is
sudo chmod a+rwx /var/lib/samba/usershares/

---

### Post by C4B_ROCKs on 2008-10-10
Ubuntu users,

I'm a newb on ubuntu and I have figured out a few thingS by doing searches on google. I just wanted to say that I have followed what this site [Prashanth speaks ]("http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html") , instructed and I got the share folder issue to work and yes you have to restart ubuntu, and also when you are on a windows pc and trying to access file from ubuntu you also have to creat that username that you are logged in on your windows pc on to samba. follow the same step on that link. 

"UBUNTU ROCKS"

---

### Post by C4B_ROCKs on 2008-10-11
> **pravinbravi said:**
> You can also install and try the following package 

```
sudo apt-get install system-config-samba
```a.k.a. Samba Server Configuration Tool 1.2.50

its a nice gui tool (repository present in hardy universe) for configuring and setting share in samba similar to editing samba.conf file.

GNOME menu listing: System>Administration>Samba

Enjoy!

thanks for the SAMBA GUI Pravin, this is now going to help share all the folders I need to share out. with out typing...lol:guitar:

---

### Post by Yashiro on 2008-10-26
What is not made clear is:
**Traditional shares**, via config hacking or the samba control panel are not the same as shares created with the Ubuntu right click menu.

Shares created with the right click gnome ui are a 'new' type of share called a **usershare**. [http://wiki.suselinuxsupport.de/wikka.php?wakka=HowToSambaUsershares](http://wiki.suselinuxsupport.de/wikka.php?wakka=HowToSambaUsershares) is worth a read.

smb.conf:
```
#usershare path = /var/lib/samba/usershares
```is the path to where EXTRA information needed by samba is stored to configure these new less secure share types.



The problems with the initial setup of these usershares seem to stem from 
a) not being installed as root initially
b) being required to re-log for your group permissions to be updated

The configuration of both old and new types needs to be clarified and tidied up for normal users.
As it stands it's far from obvious and this most basic of functions needs to 'just work'.

[COLOR="Gray"]
However, do not confuse this with a secondary issue of Samba shares not appearing in Nautilus when you access the workgroup icon. Direct connection smb://sharepc/folderonshare will work in this case and seems to be a Nautilus issue.[/COLOR]

---

### Post by x4v13r on 2009-01-09
> **C4B_ROCKs said:**
> thanks for the SAMBA GUI Pravin, this is now going to help share all the folders I need to share out. with out typing...lol:guitar:

Thanks this worked for me

---

### Post by cnefer on 2009-06-17
> **pravinbravi said:**
> You can also install and try the following package 

```
sudo apt-get install system-config-samba
```a.k.a. Samba Server Configuration Tool 1.2.50

its a nice gui tool (repository present in hardy universe) for configuring and setting share in samba similar to editing samba.conf file.

GNOME menu listing: System>Administration>Samba

Enjoy!


That is a great solution! thanks

---

### Post by jschodde on 2009-09-23
Awesome! thanks for the tip!

---

### Post by roy.champion on 2010-08-01
> **jetsam said:**
> OK.  /opt/ is owned by root and should be, so I guess you need to do what you're doing if you really want to share it.

The problem now I think is you still have a **;** in the line **; "usershare owner only = False**.  This makes it a comment.  Try taking the **;** and the **"** out and saving, then restarting Samba with:

```
sudo /etc/init.d/samba restart
```Is there any particular reason you want to share /opt/?  It's a pretty obscure part of the directory structure.

What is the folder you want to share?  Did you create it yourself?  Another, possibly better approach would be to change the ownership of the directory you are sharing.

This worked like a pro! thanks for the little tidbit

---

### Post by krakonos on 2013-04-01
But what it means when I've got that error but I've never installed samba?

---

### Post by wildmanne39 on 2013-04-01
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

