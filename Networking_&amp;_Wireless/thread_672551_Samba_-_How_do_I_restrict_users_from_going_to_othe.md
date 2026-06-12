---
title: "Samba - How do I restrict users from going to other paths?"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by Roasted on 2008-01-19
I have 4 paths on my Samba server.

Jason
Mom
Curt
Tyler

Jason = me.

I set it up so they can just type my computer name in the run prompt and they'll see those 4 folders. They go to their designated folder and drop their stuff in and it gets written to my desktop.

Problem is, Mom can roam around anywhere she wants. Considering I have 14,000 pictures in my home directory, and my home directory is my path, it kind of worries me.

I'd like to restrict Mom to only opening Mom's folder, Curt only opening Curt's, and Tyler only opening Tyler's.

How can I go about this?

---

### Post by blueridgedog on 2008-01-20
Post your smb.conf file and and ls -al while in the parent directory containing the folders mentioned in your post.

---

### Post by Roasted on 2008-01-20
```

jason@desktop:~$ cd /media/driveb
jason@desktop:/media/driveb$ ls -al
total 2004
drwxr-xr-x 60 jason jason    4096 2008-01-19 17:38 .
drwxr-xr-x  8 root  root     4096 2008-01-19 17:45 ..
drwxr-xr-x  5 jason jason    4096 2007-05-26 12:35 .audacious
-rw-r--r--  1 jason jason    1000 2007-10-19 00:05 .audacity
drwxr-xr-x  4 jason jason    4096 2007-12-03 20:20 .audacity-data
drwxr-xr-x  2 jason root     4096 2007-05-26 23:16 .automatix
drwxr-xr-x  9 jason jason    4096 2007-11-09 10:48 .azureus
-rw-------  1 jason jason    9885 2007-12-11 01:34 .bash_history
-rw-r--r--  1 jason jason     220 2007-05-26 06:32 .bash_logout
-rw-r--r--  1 jason jason    2298 2007-05-26 06:32 .bashrc
drwx------  6 jason jason    4096 2007-06-11 02:53 .BitTornado
drwxr-xr-x  4 jason jason    4096 2007-11-01 20:36 .cache
drwx------  7 jason jason    4096 2007-11-06 01:09 .config
drwx------  2 jason jason    4096 2007-06-01 02:32 .cups
drwxr-xr-x 29 jason jason   16384 2007-12-21 20:30 curt
drwx------  2 jason jason    4096 2007-12-06 23:43 .dbus-keyrings
-rw-------  1 jason jason      27 2007-12-06 23:46 .dmrc
drwxr-xr-x  4 jason jason    4096 2007-07-11 21:34 .dvdcss
drwxr-xr-x  3 jason jason    4096 2007-05-26 11:44 .elisa
drwxr-xr-x  4 jason jason    4096 2007-12-07 18:49 .emerald
-rw-------  1 jason jason      16 2007-05-26 10:36 .esd_auth
drwxr-xr-x  7 jason jason    4096 2007-12-06 23:46 .evolution
drwx------  2 jason jason    4096 2007-12-08 16:41 .filezilla
drwxr-xr-x  2 jason jason    4096 2007-11-01 23:10 .fontconfig
drwxr-xr-x  5 jason jason    4096 2007-12-07 09:28 .frostwire
drwx------  3 jason jason    4096 2007-05-31 21:45 .gaim
drwx------  4 jason jason    4096 2007-12-06 23:46 .gconf
drwx------  2 jason jason    4096 2007-12-11 01:34 .gconfd
drwxr-xr-x  7 jason jason    4096 2007-06-01 10:08 .gdesklets
drwxr-xr-x 21 jason jason    4096 2007-10-31 10:28 .gimp-2.2
drwxr-xr-x 20 jason jason    4096 2007-12-07 19:22 .gimp-2.4
drwxr-xr-x  5 jason jason    4096 2007-05-26 11:50 .gkrellm2
-rw-r-----  1 jason jason       0 2007-12-09 21:20 .gksu.lock
drwxr-xr-x  4 jason jason    4096 2007-06-01 02:19 .gnome
drwx------ 16 jason jason    4096 2007-12-07 01:17 .gnome2
drwx------  2 jason jason    4096 2007-05-26 10:36 .gnome2_private
drwx------  2 jason jason    4096 2007-07-23 22:07 .gnupg
drwx------  5 jason jason    4096 2007-11-30 11:26 .googleearth
drwxr-xr-x  2 jason jason    4096 2007-11-22 11:50 .gstreamer-0.10
-rw-------  1 jason jason      33 2007-07-18 21:12 .gtk-bookmarks
-rw-r--r--  1 jason jason      87 2007-05-26 10:36 .gtkrc-1.2-gnome2
-rw-------  1 jason jason    9225 2007-12-09 17:54 .ICEauthority
drwxr-xr-x  3 jason jason    4096 2007-12-06 19:31 .icons
drwxr-x---  2 jason jason    4096 2007-09-26 00:56 .inkscape
drwxr-xr-x 55 jason jason    4096 2008-01-16 00:12 jason
drwxr-xr-x  4 jason jason    4096 2007-05-31 20:16 .java
drwx------  3 jason jason    4096 2007-05-26 23:19 .kde
-rw-r-----  1 jason jason       6 2007-10-20 21:42 .ktorrent.lock
-rw-------  1 jason jason      35 2007-07-22 00:21 .lesshst
drwxr-xr-x  5 jason jason    4096 2007-09-15 20:37 .limewire
drwx------  3 jason jason    4096 2007-05-26 12:07 .local
drwx------  3 jason jason    4096 2007-06-01 02:19 .loki
drwx------  3 jason jason    4096 2007-05-26 10:57 .macromedia
drwxr-xr-x  3 jason jason    4096 2007-05-27 14:41 .mcop
-rw-------  1 jason jason      31 2007-12-09 16:31 .mcoprc
drwx------  3 jason jason    4096 2007-05-26 10:36 .metacity
drwxrwxrwx  2 root  root     4096 2008-01-19 17:38 mom
drwx------  3 jason jason    4096 2007-05-26 10:38 .mozilla
drwxr-xr-x  2 jason jason    4096 2007-08-12 22:29 .mplayer
drwxr-xr-x  3 jason jason    4096 2007-12-05 00:22 .nautilus
drwx------  3 jason jason    4096 2007-12-07 19:11 .openoffice.org2
-rw-r--r--  1 jason jason     566 2007-05-26 06:32 .profile
drwx------  5 jason jason    4096 2007-12-11 01:27 .purple
drwxr-xr-x  2 jason jason    4096 2007-11-16 09:02 .qt
-rw-------  1 jason jason  111131 2007-11-16 10:48 .recently-used
-rw-r--r--  1 jason jason 1391153 2007-12-11 01:24 .recently-used.xbel
-rw-r--r--  1 jason jason       0 2007-05-26 10:36 .sudo_as_admin_successful
drwxr-xr-x 13 jason jason    4096 2007-12-11 01:24 .themes
drwx------  4 jason jason    4096 2007-09-17 18:37 .thumbnails
drwx------  2 jason jason    4096 2007-12-11 01:24 .Trash
drwx------  2 jason jason    4096 2007-12-27 01:35 .Trash-jason
drwxrwxrwx  2 root  root     4096 2008-01-19 17:38 tyler
drwxr-xr-x  2 jason jason    4096 2007-05-26 10:36 .update-manager-core
drwx------  2 jason jason    4096 2007-06-03 18:13 .update-notifier
drwxr-xr-x  3 jason jason    4096 2007-05-26 20:54 .vlc
drwx------  2 jason jason    4096 2007-11-01 20:02 .w3m
-rw-------  1 jason jason     116 2007-12-06 23:46 .Xauthority
drwxr-xr-x  2 jason jason    4096 2007-06-11 22:46 .xine
-rw-r--r--  1 jason jason  200268 2007-12-07 00:59 .xsession-errors


```



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
   netbios name = desktop

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
;   browseable = yes

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = yes

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


[jason]
path = /home/jason
writeable = yes
browseable = yes

[curt]
path = /media/driveb/curt
writeable = yes
browseable = yes

[tyler]
path = /media/driveb/tyler
writeable = yes
browseable = yes

[mom]
path = /media/driveb/mom
writeable = yes
browseable = yes


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

### Post by blueridgedog on 2008-01-20
So, the core of what you have is the following:

You have some files:


```
drwxr-xr-x 29 jason jason   16384 2007-12-21 20:30 curt
drwxr-xr-x 55 jason jason    4096 2008-01-16 00:12 jason
drwxrwxrwx  2 root  root     4096 2008-01-19 17:38 mom
drwxrwxrwx  2 root  root     4096 2008-01-19 17:38 tyler
```

Shared via samba as:

```
[jason]
path = /home/jason
writeable = yes
browseable = yes

[curt]
path = /media/driveb/curt
writeable = yes
browseable = yes

[tyler]
path = /media/driveb/tyler
writeable = yes
browseable = yes

[mom]
path = /media/driveb/mom
writeable = yes
browseable = yes
```

Can I assume that you have users named jason, curt, tyler and mom?  If not, then curt, tyler and mom are connecting using the jason credentials and would be able to see everything.

If you have valid users for them, 

```
chown curt:curt /media/driveb/curt -R
chown tyler:tyler /media/driveb/tyler -R
chown mom:mom /media/driveb/mom -R
```

Then tweek your smb.conf:


```
[jason]
path = /home/jason
writeable = yes
browseable = yes
valid users = jason

[curt]
path = /media/driveb/curt
writeable = yes
browseable = yes
valid users = curt

[tyler]
path = /media/driveb/tyler
writeable = yes
browseable = yes
valid users = tyler

[mom]
path = /media/driveb/mom
writeable = yes
browseable = yes
valid users = mom

```

Read the samba howto in my signature. 

Don't forget to create users accounts on the linx box that MATCH the accounts on the windows system or remote linux system that will be connecting from (not required, but it makes life easy) and don't forget to create samba user accounts with the smbpasswd command.

---

### Post by Roasted on 2008-01-20
Okay, cool. I'm booted into XP at the moment but once I get back to Linux I'll give it a shot.

Other question I have is, the reason for sharing "jason" is so my laptop can retrieve information from my linux desktop.

But what if I have information on my XP laptop that I want the Linux desktop to retrieve? How do I do that? Up until now I've only had the need for a 1 way share...

---

### Post by blueridgedog on 2008-01-20
You can create a shared drive/folder on the XP system and access it via the linux system.  Click Places, then Network

---

### Post by Roasted on 2008-01-25
Operating not permitted when I tried to chown curt:curt and tyler:tyler, etc.

This is starting to get frustrating. I don't see what the big complication is. I just want Curt to only be limited to see that. Why can't I put some kind of a command in the smb.conf and it'll respond that way?

Also, something really stupid I just realized... even if driveb is unmounted, users can still log into the drive from the run prompt and browse around. It's restricted to write at this point, saying access denied, but wtf? If the drive is unmounted, I don't want anybody in there. If it's mounted, then I want them to ONLY to have access to their particular folder.

---

### Post by salazar on 2008-01-25
> Operating not permitted when I tried to chown curt:curt and tyler:tyler, etc.
 add "sudo " after the commands posted by blueridgedog 
      ex: sudo chown curt:curt /media/driveb/curt -R

that should do !

 tyler, mom,jason, tyle  must be  linux users 

then you can delete the lines  " valid users " in you smb.conf

[tyler]
path = /media/driveb/tyler
writeable = yes
browseable = yes
# valid users = tyler      >>>> comment this on all users, because linux permissions will do the trick


and then on smb.conf, you may uncommnet the next line

;   security = user

---

### Post by tad1073 on 2008-01-25
@blueridgedog
I followed the tut you have [here](http://ubuntuforums.org/showthread.php?t=202605) but I am unable to access the windows box from linux and vice versa.

---

### Post by Roasted on 2008-01-25
Okay. So I added the valid users = jason, etc etc to each user and also did the chown command for each one. 

I wanted to test this out, yet I'm confused over something.

So I logged in as me (jason) and I could access my folder. Great. So I back out, I double click curt's folder and it prompts me for username and password. I put in CURT'S VALID INFORMATION and it came back with the following error.

\\desktop\curt is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions. Multiple connections to a server or shared resource by the same user, using more than one user name, are not allowed. Disconnect all previous connections to the server or shared resource and try again.

Can somebody just clarify that for me? I don't understand why, since I put in Curt's information, it blocked me out. Is it because it doesn't support 2 connections and I technically was still connected as Jason from my previous login?

---

### Post by blueridgedog on 2008-01-26
> **Roasted said:**
> 

So I logged in as me (jason) and I could access my folder. Great. So I back out, I double click curt's folder and it prompts me for username and password. I put in CURT'S VALID INFORMATION and it came back with the following error.

\\desktop\curt is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions. Multiple connections to a server or shared resource by the same user, using more than one user name, are not allowed. Disconnect all previous connections to the server or shared resource and try again.

Can somebody just clarify that for me? I don't understand why, since I put in Curt's information, it blocked me out. Is it because it doesn't support 2 connections and I technically was still connected as Jason from my previous login?

OK, when you say you logged in, are you referring to the logging in to the windows system?

If so, then the error above was displayed on the windows system while you were logged in, but trying to give Curt's credentials.  Will it work if Curt is logged in?

How did you specify Curts credintials?  was it just curt and a password or did you do curt@nameoflinuxbox and password?

---

### Post by blueridgedog on 2008-01-26
> **tad1073 said:**
> @blueridgedog
I followed the tut you have [here](http://ubuntuforums.org/showthread.php?t=202605) but I am unable to access the windows box from linux and vice versa.

Can you post your smb.conf or at least the portions of it that specify the shares?

---

### Post by Roasted on 2008-01-26
blue - here's step by step what I was referring to. I'll throw out generic passwords just for sake of making this smoother.

User =  Password
Jason = Hooters
Curt = Fourwheeler

So I log onto my laptop, which has a designated password for the user. Windows starts up. I go to run, type the path to my desktop, and I'm prompted with a username/password screen.

So I log in via Jason/Hooters, which is the established username/password for the user Jason on my Samba machine.

Jason can access Jason. Great. Fine. However, when I go to double click Curt's folder (or Tyler's or Mom's) it prompts me for another username and password.

So, since I'm trying to get into Curt's stuff, I log in as Curt. 

Curt = Fourwheeler.

THEN it prompts me with that error. Is it giving me that error due to the fact I already previously logged in as Jason? If I log out of windows and log back into windows, THEN go back to the run prompt... if I type in Curt first and log in as Curt, I can get to Curt's things. However, I'm blocked out of Jason's things (my stuff) due to the fact I logged in as Curt. EVEN WHEN IT PROMPTS ME FOR A NEW USERNAME/PASSWORD after clicking on Jason's folder, and I put in Jason's legit information, it gives me that error.

Is that because I logged in as Curt initially?

Nobody else knows anybody else's information. I just know it all since I set everything up. So realistically, there shouldn't be any problems with this. So I guess what I should do, if I wanted to get to Curt, Tyler, or Mom's stuff, is to set Jason as a valid user on every one of their folders. That way for Curt's folder, only Curt/Jason can get to it. For Tyler, only Tyler/Jason can get to it, and for Mom, only Mom/Jason can get to it.

I'm just wondering if what I have above is absolutely correct. 

The other question I have is... if I log in as Curt initially, it says something about unable to have two usernames logged in at once. Okay, fine. But how do I log OUT of Curt so I can get re-prompted and log in as Jason?? The only way I can seem to do this is by logging out/back in of Windows. Ideas? 

Long post, but I tried to be very descriptive. My apologies!

---

### Post by Iowan on 2008-01-26
IMHO,making** jason** a valid user on the other folders would be the easiest way to do it.

There's also the **invalid users=** option to block certain users from certain folders.

---

### Post by tad1073 on 2008-01-26
```

[global]
    ; General server settings
    netbios name = thomas
    
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, wifi0
    bind interfaces only = true
    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = thomas
    force group = thomas
available = yes
browsable = yes
public = no
writable = yes

```

---

### Post by Roasted on 2008-01-26
I think everything is working now. I set up valid users as well as invalid users for each path. Then I tested each one by logging into each username and testing out the results I get from trying to log in to other folders.

Everything looks good now. Thanks fellas.

---

