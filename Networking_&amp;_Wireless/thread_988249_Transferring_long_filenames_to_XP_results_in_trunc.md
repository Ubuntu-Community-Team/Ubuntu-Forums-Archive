---
title: "Transferring long filenames to XP results in truncated filenames?"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by Cheule on 2008-11-20
Hi folks,

I have an Ubuntu 6.06LTS server, when transferring files to the XP machine for backup, those with long filenames get truncated to the old MS-DOS style naming convention.

What's causing this?

---

### Post by dgoosens on 2008-11-20
hi,

in Windows, you can not have more than 255 chars in a path or filename...

an easy solution... Zip them...

---

### Post by Cheule on 2008-11-22
> **dgoosens said:**
> hi,

in Windows, you can not have more than 255 chars in a path or filename...

an easy solution... Zip them...

Ah well they're not quite that long...maybe 30 characters?

Thanks for the Zip suggestion, it's probably the only thing I can do in the meantime while I work out what's causing it!

---

### Post by gTinker on 2008-11-22
[QUOTE=Cheule]
I have an Ubuntu 6.06LTS server, when transferring files to the XP machine for backup, those with long filenames get truncated to the old MS-DOS style naming convention.

What's causing this?[/QUOTE]

It probably would be easier for people to suggest answers if you would give an example of what you mean. What gets truncated to what?

It can't hurt to also mention the method you are using for this transfer as it may be related to method.

I would expect to see something like what you describe due to a limitation of a filesystem. By any chance are you doing this transfer with a CD or a FAT16 formatted media of some kind?

---

### Post by Hobgoblin on 2008-11-22
Possibly it's something to do with [these options](http://www.faqs.org/docs/samba/ch08.html#samba2-CHP-8-TABLE-5).

Can you post your /etc/samba/smb.conf

---

### Post by Cheule on 2008-11-23
> **gTinker said:**
> It probably would be easier for people to suggest answers if you would give an example of what you mean. What gets truncated to what?

It can't hurt to also mention the method you are using for this transfer as it may be related to method.

I would expect to see something like what you describe due to a limitation of a filesystem. By any chance are you doing this transfer with a CD or a FAT16 formatted media of some kind?

Right, sorry. Here's what I'm doing and what I'm using...

First off, I'm using a desktop running Ubuntu 6.06LTS as a server. On occasion, the disk gets full and I then move the files to an XP Home machine as a backup.

Secondly, I am moving the files by browsing to the Server's shared folder from the XP side using just plain old Windows Explorer. I select the files I want then just drag and drop them onto the directory of choice on the XP machine. When they arrive however they now have the 8.3 naming convention of MS-DOS which makes identifying them quite difficult :)

---

### Post by Cheule on 2008-11-23
> **Hobgoblin said:**
> Possibly it's something to do with [these options](http://www.faqs.org/docs/samba/ch08.html#samba2-CHP-8-TABLE-5).

Can you post your /etc/samba/smb.conf

Certainly :) I've had a look through myself but I'm not sure I've missed anything, didn't see any options relating to file mangling at all?

Here you go:

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
   workgroup = LAN

# server string is the equivalent of the NT Description field
   server string = %h server (Samba)

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
   security = share

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
wins support = no
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

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
   create mask = 0664

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0775

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
[cdrom]
   comment = Rain's CD-ROM
   writable = no
   locking = no
   path = /cdrom
   public = yes

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
   preexec = /bin/mount /cdrom
   postexec = /bin/umount /cdrom


available = no
browseable = no
[LinuxShare]
path = /home/cheule
available = yes
browseable = yes
public = yes
writable = yes

[Forums]
path = /var/www/forums
comment = Share
available = yes
browseable = yes
public = yes
writable = yes

[www]
path = /var/www
available = yes
browseable = yes
public = yes
writable = yes
comment = yes


```

---

### Post by Cheule on 2008-11-23
One more thing, when I try to send the file FROM the server to the XP machine, I get an "Invalid Parameters" error message.

---

### Post by Hobgoblin on 2008-11-23
> **Cheule said:**
> 
Secondly, I am moving the files by browsing to the Server's shared folder from the XP side using just plain old Windows Explorer. I select the files I want then just drag and drop them onto the directory of choice on the XP machine. When they arrive however they now have the 8.3 naming convention of MS-DOS which makes identifying them quite difficult :)

This is making me think there is something screwey on the XP side.

Is it just on the one XP machine?

Can you give us some examples of the original and mangled filenames?  Might point at what is doing the mangling.

If, for instance thisreallylongfile.dat became thisre~1.dat I would suspect something on the Windows end.

---

### Post by Cheule on 2008-11-23
Hmm, interesting idea. I hadn't thought to check transfers to other machines, I'll do that in the morning when I get a spare moment.

The filenames are simple enough, mostly mp3's.

Original: Metallica-"Wherever I May Roam".mp3
Altered: METAL~1.mp3

Now this presents a problem as anything by Metallica is then all given the same filename! :)

---

### Post by cariboo on 2008-11-23
To trensfer the files from the server to the  windows computer, especially if they have spaces in the file names enclose the long file name in quotation marks, if you have your windows share mounted on the server:

```
mv "long file name.mp3" /media/windows
```

Linux on the command line doesn't deal well with spaces in file names.

Another thing you can do is replace the spaces with underscores using a script like this:

```
#!/bin/sh
# remove spaces from mp3 file name
for i in *.mp3; do mv "$i" `echo $i | tr ' ' '_'`; done
```

this will fix truncated file names also.

Jim

---

### Post by Hobgoblin on 2008-11-23
> **Cheule said:**
> 
Original: Metallica-"Wherever I May Roam".mp3
Altered: METAL~1.mp3

Now this presents a problem as anything by Metallica is then all given the same filename! :)

Do all these files have quotes (or other special characters) in the filename?  Quotes aren't allowed in DOS/Windows filenames.  Linux isn't too keen on them either but can cope with them.  The spaces won't be a problem unless you are using the command line.

This (attached) is what happens when I try to rename a file in Windows to one with a quote included.

---

### Post by Hobgoblin on 2008-11-24
OK, I get a similar effect but my 8.3 filenames are even more garbled.

> **cariboo907 said:**
> 
```
#!/bin/sh
# remove spaces from mp3 file name
for i in *.mp3; do mv "$i" `echo $i | tr ' ' '_'`; done
```


To get rid of the quotes you need to add.

```

for i in *.mp3; do mv "$i" `echo $i | tr '"' '_'`; done

```

That line doesn't work unless you remove the spaces first so just tag it onto the above script.

---

### Post by Cheule on 2008-11-24
Thanks everyone for your input, between you guys and the peeps over at ThinkBroadband you've found the problem, it's the fact that Windows doesn't like quotes in filenames, which I have to admit I've been blissfully unaware of.

Simply changing the quotes to single quotes has fixed the problem :)

Thanks to everyone that helped me find the cause!

---

