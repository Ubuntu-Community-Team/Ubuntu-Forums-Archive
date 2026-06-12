---
title: "Network file share is forcing read only to files. Why?"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by powel212 on 2009-03-26
Hi

I have many computer conected to a Ubuntu file share server that I built at work. I use Ubuntu on my laptop to axcess files on the server from my office and other people in other rooms on the same network need to axcess and modify those same files. Some other people use Ubuntu and others use OSX and others use Windows-XP,Vista or Seven. 

If I put files in the share from my Ubuntu box I can again modify them in the share folder but only others using Ubuntu can modify those files from other locations. Same thing with people on the same network saving files from Windows or OSX. The files they create can only be modified again by other computers using the same OS. 

I need everyone to access and modify the files from different locations on the same network but The Ubuntu server keeps forcing read only the files. 

If I create a new folder from a windows box on the Ubuntu server any other windows box can access and modify but other ubuntu users cannot. If I then go to the server and modify that windows created folder's permissions by using "sudo nautilus" and change folder's permissions to all users read and write then anyone can access and modify the files but the next time a windows or mac boc drop a new file in there it imediatly becomes read only.

Please help.

powel

---

### Post by tarps87 on 2009-03-26
I am assuming you are using samba to share the files, what are the samba settings for this share?
Specifically the folder/file create permissions.

---

### Post by powel212 on 2009-03-26
I don't know the answer to that question. 

"     what are the samba settings for this share?
     Specifically the folder/file create permissions"

How can I find out?

Actually the only way I know how to configure file sharing is to right click a folder and tick "Share", "allow other to write" and "allow guest access" and "apply permissions automatically".

I have never found a GUI for Samba in ibex, though I think there was one back in Gutsy.

Thanks for your help.

Powel

---

### Post by Flimm on 2009-03-26
The GUI for Samba is launched by running
```
shares-admin
```

---

### Post by tarps87 on 2009-03-26
> **powel212 said:**
> I don't know the answer to that question. 

"     what are the samba settings for this share?
     Specifically the folder/file create permissions"

How can I find out?

Actually the only way I know how to configure file sharing is to right click a folder and tick "Share", "allow other to write" and "allow guest access" and "apply permissions automatically".

I have never found a GUI for Samba in ibex, though I think there was one back in Gutsy.

Thanks for your help.

Powel

Sorry I assumed you were using the Ubuntu server edition (no GUI). It could well be a config issues then.
The config file is this one /etc/samba/smb.conf if you haven't changed it there will be no password or sensitive information stored in it. The section I'm looking for will look something like this

[share]
    comment = Ubuntu File Server Share
    path = /media/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

If you can find this section could you post the whole config file wrapped in code tags

---

### Post by powel212 on 2009-03-26
Hey thanks for the feedback.

I am home now and will get the info from the smb.conf in the morning and post it here. I really appreciate your help.

I am in Asia and it is now 9pm. 

Thanks again.

Powel

By the way I don't know how to 

    "If you can find this section could you post the whole config file wrapped in code tags"

Sorry

---

### Post by powel212 on 2009-03-26
Code:

Test Test

__________________

---

### Post by tarps87 on 2009-03-26
> **powel212 said:**
> 
"If you can find this section could you post the whole config file wrapped in code tags"


In advanced view the # button
or
[/CODE]
after the text
[CODE]
before the text

---

### Post by powel212 on 2009-03-26
```
test
```

---

### Post by tarps87 on 2009-03-26
That's the one ;)

---

### Post by powel212 on 2009-03-26
Okay, here is my smb.conf

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
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
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
#   wins support = no

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
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

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
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

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

# This option controls how unsuccessful authentication attempts are mapped 
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
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

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
#   load printers = yes

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
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

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

Thanks again for your help

Powel

---

### Post by tarps87 on 2009-03-27
Is this file from the file server?
I appears the shares are not being stored in the default samba configuration file. I don't have access to a Ubuntu machine at the moment, when I get home I will experiment with the graphical share options.
What version of Ubuntu are you using?

---

### Post by powel212 on 2009-03-27
Yes. This smb.conf is from the server itself which is running Ubuntu 8.10 intrepid ibex.

I have 3 Ubuntu machines at home too, which can be booted into windows for testing, so I can try some reconfiguring if I can learn how to understand this smb.conf

Thanks again.

Powel

---

### Post by powel212 on 2009-03-27
May have found a solution:

I have tested this on 2 of my home computers and it seems to work.

after following these steps I can now drop a document from windows into the share folder on Ubuntu and it is no longer read only.

On Monday I will try it with one folder on the server at work.

```
sudo apt-get install system-config-samba

launch system-config-samba

add desired folder

allow guest write access

under preferences - server settings - security - 
set authorization to: share
passwd encrypt: yes
guest account: "current user" (i mean the current logged in user)

sudo /etc/init.d/samba restart 


```

Thanks to all those who helped and I am still interested in more feedback to further my understanding of samba.

---

### Post by tarps87 on 2009-03-27
I've had a look at the share bit but don't know why there isn't anything in the config file.

This page may help, it is what I used to set up my file server. (It is from the server documentation by will work on the desktop version)
[https://help.ubuntu.com/8.10/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/8.10/serverguide/C/samba-fileserver.html)

There are some GUI's, it looks like you have found one.
The permissions bit you are looking for will be the create mask options, this will set what user/groups can access and write to the files.

There is more information here:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Sorry I haven't been much help, things are a little busy at the moment.

---

### Post by powel212 on 2009-03-28
Thanks for your help tarps87.

I really appreciate it. 

I'm pretty sure I got it sorted. 

I feel like a tool most of the time but I am the only one of the 60 or so people at my office that have even a clue about networking computers and sharing files and printers. But with the limited knowledge that I have it is a miracle our file share even works at all. Haha

Thanks again.

and Thanks to Ubuntu for making my life easier.

Powel

---

