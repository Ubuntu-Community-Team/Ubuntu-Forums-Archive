---
title: "Samba Made Simple?"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by fish2ways on 2007-11-01
Is there a definitive, straightforward, guide to setting up Samba?
We have three machines. The two main ones, my wife's and mine, both running Ubuntu 7.10. 
The third an older machine with W2K that has very occasional use.
All are connected via ethernet cables through a router. All in the same room so no need for wireless.
The issue is, I want to enable file sharing, read and write, between my wife's machine and my own. 
I've got all necessary Samba files installed on both machines. I've set up shares and we can see and read each others files. But no matter what I do I cannot copy a file from my machine to my wife's or from hers to mine. 
For example, I can sit at her machine open my home folder via the network and copy/paste from it into her home folder,  but if I sit at my machine, open her home folder via the network and try to paste the same file from my home folder into hers I get an  - Error "Access denied" message. 
I am set up as a user on her machine and she is likewise on mine. 
I've Googled, searched forums and am, as a result, totally confused. There's a wealth of info out there but none of it clear or consistent  and every 'solution' is subtly different to the others. 
How difficult can this be?
We currently share files via usb  stick which is absurd considering the two machines are no more than eight feet apart!
Here's a copy of my smb.conf file 
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

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
  name resolve order = lmhosts host wins bcast

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
  security = user

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
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

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


[roger]
path = /home/roger
available = yes
browsable = yes
public = yes
writable = yes



[Music]
path = /Media/Music
available = yes
browsable = yes
public = yes
writable = yes

[Images]
path = /Media/Images
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by tact on 2007-11-01
Ok a point or two...

With both your machines you dont need to actually (yourself) install and set up samba to just share files as you describe.

From a pure vanilla install of 7.10 all you (did) need to do was System>Administration>Shared folders.

Select the folder to share.  v7.10 would then ask if you want to share that folder via NFS or SMB.  Feel free to choose SMB or tick both boxes... doesnt matter.  Then there will be a little activity while the system (not you) installs necessary software and configures it.  Somewhere there is a check box too - to enable read only or read write.

Too easy.  Sometimes google is not your friend...there is so much info out there its hard to find the right info.

Now..  you have gone further and installed things and configured them.  Nothing looks too astray.  So a second pointer...

File and folder permissions.  These are as much a showstopper for file/folder sharing as ill-configured samba.

No matter how correctly samba (or nfs) is set up...no matter if you have username and password set up on the remote machine.  If THE folder (or file) is not set to allow those "others" write access...  it aint going to happen.

Hope this points you in the right direction.  :)

---

### Post by ericartman on 2007-11-01
I used this guide for sharing  maybe it will help. Good luck
[http://ubuntuforums.org/showthread.php?t=218630&highlight=backing+up](http://ubuntuforums.org/showthread.php?t=218630&highlight=backing+up)

cart

Sorry that wasn't he question you asked I know but I had nothing but headaches  with Samba, file permissions and all, so I left the link. I know it wasn't what you asked for and I apologize.

C

---

### Post by fish2ways on 2007-11-01
No matter how correctly samba (or nfs) is set up...no matter if you have username and password set up on the remote machine. If THE folder (or file) is not set to allow those "others" write access... it aint going to happen.

Thanks tact. 'Problem' fixed.
Talk about not being able to see the wood for the trees. 
As it so often turns out,  the answer is so simple that you can't see it 'cause you're looking for a complicated one.
Lesson learned, till the next time.
Thanks again.

---

### Post by bionnaki on 2007-11-02
so, how would a windows and an osx connect to the shared folder on ubuntu? everything is installed like tact said...

---

### Post by SpiritIsReality on 2007-11-02
howdy
ericartman ... thanks for the link
trails

---

### Post by leona on 2007-11-02
> **bionnaki said:**
> so, how would a windows and an osx connect to the shared folder on ubuntu? everything is installed like tact said...
Yep this is what I'm trying to do to, make a windows machine 'see' a Linux drive that I've shared, samba is installed and setup, but no joy, it can't see it, what have I missed?
smb.conf (part of)
```

[data]
path = /media/hda5
available = yes
public = yes
writable = yes
comment = Linux Box
browsable = yes

```

---

### Post by tact on 2007-11-02
> **bionnaki said:**
> so, how would a windows and an osx connect to the shared folder on ubuntu? everything is installed like tact said...

Hey there...

The windows machine connecting to a shared folder on a linux box is covered already.  Does that work for you now?

Just to reiterate:
If you are running 7.04 or 7.10 following the process above (System>Administration>Shared folders) and sharing a folder (optionally giving write access) letting the system install SMB support and thats about all you need to do.  Perhaps afterwards double check the actual permissions for that folder to be sure "others" have read or read/write access.

If thats working then you got windows or SMB sharing working.  Sorry I dont know anything about Mac OSX.   If it can support access to windows or SMB shares then if your windows box can access the linux box share, then so should OSX be able.

There used to be native linux support for Mac networking protocol ...  I think the software was called "netatalk"  I used it about 9yrs ago to share folders between linux and Apple IIe machines whilst  simultaneously sharing the same folder with Windows machines also.   So if the Mac box cannot do windows or SMB file sharing them perhaps yo can have linux share the same folder to SMB and netatalk.

---

### Post by Salpiche on 2007-11-02
[http://www.youtube.com/watch?v=Ad17kma8rNM]("http://www.youtube.com/watch?v=Ad17kma8rNM")

may this help?

It has worked for me on Feisty and now on Gusty

---

### Post by tact on 2007-11-02
> **leona said:**
> Yep this is what I'm trying to do to, make a windows machine 'see' a Linux drive that I've shared, samba is installed and setup, but no joy, it can't see it, what have I missed?
smb.conf (part of)
```

[data]
path = /media/hda5
available = yes
public = yes
writable = yes
comment = Linux Box
browsable = yes

```

Hi Leona,

Looks like you want to share a whole drive (hda5).  Your config there refers to a folder (/media/hda5).   I presume you have mounted /dev/hda5 (the drive) to the mountpoint folder /media/hda5 (?)

Until you do the "mount", the folder /media/hda5 will be empty to both local and remote users.  To check the mount has worked you can either:
CLick on "places>Home folder" and then navigate to /media/hda5 to see whether the folder has the expected files from /dev/hda5 inside (or is it empty?)
or...
in a terminal type "ls -l /media/hda5" and see whether expected files are there.

You would need to check the permissions for /media/hda5 to ensure its read or read/write

While there right click on the folder /media/hda5 , click "Share Folder" and see it is properly shared via SMB

---

