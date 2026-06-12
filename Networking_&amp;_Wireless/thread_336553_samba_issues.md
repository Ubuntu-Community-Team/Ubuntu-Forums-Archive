---
title: "samba issues"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by tophatandy on 2007-01-11
Recently made the upgrade for a couple of my computers up to wireless this required me to buy and install a wireless router.. got everything up and running.. except for one thing..

all my windows machines are running and sharing on the network perfectly, BUT my linux desktop (not server) wont let me access it from a windows machine.. i could before the router..

maybe its not the router and its just some stupid configuration I made all on my desktop..

but either way..

I can see my Linux desktop on the networks page, but it says its a "samba server" and when I try to access it, I get a box that comes up for a login, which never happened before..

I tried my username and password for my Linux account... no go.

Really am stumped here.. any help would be greatly appreciated.

---

### Post by dmizer on 2007-01-11
please past the contents of: /etc/samba/smb.conf

by the way ... any time one computer is attempting to access another, the computer being accessed is considered to be a server.  so even though your ubuntu box is a desktop install and not a cli based web server or ftp server or the like, it still IS in fact a server.  in this case, a samba server.

---

### Post by tophatandy on 2007-01-11
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



[Music and Such]
path = /home/andrew/Desktop/Music and Such
available = yes
browsable = yes
public = yes
writable = no

[Root]
path = /home/andrew/Desktop/Root
available = yes
browsable = yes
public = yes
writable = yes

```

I know..
just saying.. its not a server and its behaving as though it is a server install (my old ftp server was like this)



just not typical of any regular lan peer to peer access I have seen thus far..

---

### Post by dmizer on 2007-01-11
so essentially you're simply using a modification of the sample smb.conf file.

try changing it to something more specific to your needs.

first back up that messy modification:
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.backup
```
now, if what i suggest won't work, you can simply restore your original samba configuration by changing smb.backup to smb.conf by reversing the above line.

now edit smb.conf:
```
gksudo gedit /etc/samba/smb.conf
```
and erase every single line in the file.  paste this in it's place:
```
[global]
    ; General server settings
    netbios name = [COLOR="Red"]NAMEOFYOURUBUNTUBOX[/COLOR]
    server string =
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = [COLOR="Blue"]share[/COLOR]
    null passwords = true
    ;username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast
    wins support = no
    syslog = 1
    syslog only = yes

[Music and Such]
path = /home/andrew/Desktop/Music and Such/
available = yes
browsable = yes
public = yes
writable = no
guest ok = yes

[Root]
path = /home/andrew/Desktop/Root/
available = yes
browsable = yes
public = yes
writable = yes
guest ok = yes
```
now before you save the file, be sure to change "NAMEOFYOURUBUNTUBOX" to something which can identify it on your local network.  anything is fine, just no spaces.  this way, you will be able to find the share with windows network browser (ie. "my network places").

now save the file and close gedit.

finally, restart your samba server:
```
sudo /etc/init.d/samba restart
```
and see if you are able to browse to your shares from your windows computers now.

several things were probably working against you.  first of all, the default configuration of samba is less than adequate.  you really have to tweak it to make it work right, and it's not worth it.  it's better to start from scratch.  i always base my smb.conf files on the one found in the tutorial accessible by clicking on the first link in my sig.

second of all, shares don't normally work well when the share name has spaces in it, so you're also better off changing the "[Music and Such]" to something like [Music_and_Such] or something similar.  note: this does not effect your directory on your local ubuntu machine.  anything in the brackets is displayed as your share name, so your directory path can be /home/andrew/music, and the label in brackets can be something different like [good_tunes].  then your windows machine will see the share as "good_tunes" even though the files are actually located at /home/andrew/music.

the way it currently sits CAN work (with spaces in the share name), but it may also be buggy.  so give it a shot and if you still have difficulty, try changing the share name to something without spaces in it.

anyway, hope that gets you working.  let me know if it doesn't.

---

### Post by dmizer on 2007-01-11
sorry, i forgot two small but important lines.  i've updated the post and marked the changes in blue.

---

### Post by tophatandy on 2007-01-11
no go. 

still get the login screen..

---

### Post by dmizer on 2007-01-11
yeah ... sorry, you'll also need to add the two new lines i neglected to include.  i've updated the post, and marked in blue, the line's you'll need to add.

---

### Post by dmizer on 2007-01-11
huh ... i'm having the same problem.  it worked before.  i suspect something changed in one of the recent updates.  give me a bit and i'll find the answer for ya.

---

### Post by tophatandy on 2007-01-11
k. 

thank you very much for your time and help. =]

---

### Post by dmizer on 2007-01-12
okay ... after a lunch of udon and a bit of sake (shhh, don't tell anyone), i managed to clear my head enough to figure out what the problem was.

under global, security sould be "share", like so:
security = share

i've made the change in the smb.conf file above, and again ... marked the change in blue.  it works for me now.  let me know if you still have a problem.

---

### Post by tophatandy on 2007-01-30
sorry it took so long.. but it all works great thanks for the help. =]

---

