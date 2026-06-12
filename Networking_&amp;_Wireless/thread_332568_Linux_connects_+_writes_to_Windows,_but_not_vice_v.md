---
title: "Linux connects + writes to Windows, but not vice versa"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by Ubuntiac on 2007-01-06
I seem to have a similar problem to this thread:
[http://www.ubuntuforums.org/showthread.php?t=198221&highlight=samba+help](http://www.ubuntuforums.org/showthread.php?t=198221&highlight=samba+help)

Basically, I'm trying to make my home directory available over our Windows network via Samba. I can read and write files on the window$ boxes from Kubuntu but not the other way around. It asks for login details and none seem to work. I get "\\mymachine is not accessible. You might not have permissions to use this network resource." I have:

- A linux box (Kubuntu Edgy)
- An XP box
- A workgroup that works fine between Window$ machines
- smbfs and smb server installed

I've also:
- Made the share folder permissions 777
- created a user in KDE's user manager (sheryl)
- Added user to samba (sudo smbpasswd -a sheryl)
- Created /etc/samba/smbusers file, contents of which are (sheryl = "sheryl")
- In smb.conf, uncommented (security = user) and appended (username map = /etc/samba/smbusers) after it and...
- set the workgroup to my local workgroup name
- Set home directories to browseable

My smb.conf looks like this:

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
workgroup = RPNET

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
security = user
username map = /etc/samba/smbusers

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
passdb backend = tdbsam

obey pam restrictions = yes

guest account = nobody
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
comment = All Printers
path = /tmp/
printable = yes
create mask = 0700
case sensitive = no
msdfs proxy = no

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers

[SILVERDDSKTP]
path = /home/silverado/Desktop/
comment = /home/silverado/Desktop
guest ok = yes
read only = no
case sensitive = no
msdfs proxy = no

[DOCUMENTS]
path = /home/silverado/documents
comment = /home/silverado/documents
guest ok = yes

[SILVERDPCTRS]
path = /home/silverado/Pictures
comment = /home/silverado/Pictures
guest ok = yes

[SILVERADOTMP]
path = /home/silverado/temp
comment = /home/silverado/temp
guest ok = yes
wide links = no

```

Any ideas? I've been searching these forums and the Samba site long enough that my brain is ready to implode... :-k 

Thanks!

---

### Post by meng on 2007-01-06
Have you tried connecting by IP address and not by hostname? I can't remember the WIndows equivalent of /etc/hosts, but you have to make sure there's an IP-hostname translation in that config file if you want to use hostname.

---

### Post by Ubuntiac on 2007-01-06
I've only tried by browsing in an Explorer window to:

My Network Places->Microsoft Windows Network ->workgroup->mymachine->shared_folder

When I have security = share, it seems to allow reading files (but not writing) fine, so it seems the it's resolving, but permissions or authentication are going wierd somewhere, or at least thats my rather inexperienced guess...

---

### Post by meng on 2007-01-06
Well I found that connecting by IP address is more straightforward. Worth trying if you haven't done so already.

---

### Post by Ubuntiac on 2007-01-06
First up, thanks for the advice! Could you explain what you mean by "connecting by IP address", in this case? Are you talking about connecting from the windows box via ftp, browser, explorer, something else entirely like a change in the smb.conf?... :-k 

Thanks!

---

### Post by meng on 2007-01-06
No I mean if your Ubuntu box is at internal IP address 196.168.0.3, then type into the explorer window:
\\192.168.0.3

:D

---

### Post by Ubuntiac on 2007-01-06
Ahhh... gotcha.

Just gave it a try but no go. It asks for the username and password. I tried entering the user/pass that I created in ubuntu (and recreated in smbuser), the original ubuntu admin user/pass and the local windows box user/pass. It just goes back to the log in dialogue with the username prefixed with the ubuntu box's name (ie the ubuntu box is called silverado. If I try to log in a sheryl it goes back to the login screen with SILVERADO\sheryl in the user name field)

---

### Post by Davenow on 2007-01-12
I am having the EXACT same problem. I can read/write to the windows box, I can SEE the linux box from the XP machine, but if I try to access it, I get the login box and no login I try works.

I want to get rid of the login box altogether...

---

### Post by Davenow on 2007-01-13
I went to Stormbringers thread, Followed his guide and its up and running now :)

---

