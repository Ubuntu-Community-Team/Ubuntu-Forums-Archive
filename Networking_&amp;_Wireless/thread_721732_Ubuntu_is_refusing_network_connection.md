---
title: "Ubuntu is refusing network connection"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by dschul on 2008-03-11
I have been unable to connect to my ubuntu box (Athlon) from any computer on my network. Samba is configured and I can see the network OK from ubuntu. Using Ubuntu 7.10. I have created a share called Share in my smb.conf:

[Share]
path = /home/david/Documents/Shared
comment = Access from windows PC
available = yes
public = yes
writable = yes
browsable = yes

Running smblient I get this (very odd that it reports 127.0.1.1 instead of 127,0.0.1)

david@Athlon:~$ smbclient -NL //Athlon/Share -U david
Error connecting to 127.0.1.1 (Connection refused)
Connection to Athlon failed (Error NT_STATUS_CONNECTION_REFUSED)

---

### Post by Eiríkr on 2008-03-11
A couple questions:
[list][*]The "NT_STATUS" bit tells us that it's Samba (masquerading as an NT server) that's giving you the error, rather than you running into network difficulties.  With this in mind, have you added username "david" to the smbpasswd file?
```
sudo smbpasswd -a david
```
Note that the username must also exist as a regular Ubuntu username.
[*]Guest / public access is not as simple as it seems, since the Samba guest username still needs to be mapped to a regular Ubuntu username for access to work.  From the [man page]("http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTACCOUNT"):
> guest account (G)

This is a username which will be used for access to services which are specified as guest ok (see below). Whatever privileges this user has will be available to any client connecting to the guest service. This user must exist in the password file, but does not require a valid login. The user account "ftp" is often a good choice for this parameter. 
Is this global option properly defined?
[*]You might want to post us your whole smb.conf file contents, as we need to see more than just the share definition for proper diagnosis.[/list]

Cheers,

Eiríkr

---

### Post by dschul on 2008-03-11
Samba password has been set for 'david' which is the user I log on to ubuntu with,
Here is my smb.conf file

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
   workgroup = SCHULBERG

# server string is the equivalent of the NT Description field
   server string = %h server

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
interfaces = lo eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
bind interfaces only = true



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
;   username map = /etc/samba/smbusers

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
   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

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

[Share]
path = /home/david/Documents/Shared
comment = Access from windows PC
available = yes

public = yes
writable = yes
browsable = yes

```

---

### Post by Eiríkr on 2008-03-11
Just looking over the file, I noted that, due to commenting and uncommenting, the keys [font=courier]valid users = %S[/font] and [font=courier]writable[/font] have wound up in the [global] sectionrather than the [homes] section as initially intended (about 2/3s of the way down).  I wonder if the valid users key might be part of your trouble here?

---

### Post by dschul on 2008-03-12
I uncommented the [homes] line and two subsequent lines. 
I restarted the samba service - made no difference.
:(

---

### Post by Eiríkr on 2008-03-13
Okay, now I've gone over this scenario a number of different ways, and have realized that I've got some yummy egg on my face.  Good thing I've got a bottle of hot sauce to hand.  :-|

Less metaphorically and more specifically, I'd misinterpreted the [font=courier]NT_STATUS_CONNECTION_REFUSED[/font] error message from your earlier post; this is apparently what [font=courier]smbclient[/font] itself spits out, and has nothing to do with the Samba server.  

However, in attempting to replicate your symptoms just on the basis of your smb.conf file, I've been unable to get the same error result, which is beginning to make me think that it's the precise something-with-your-network that I mistakenly thought was counter-indicated by the [font=courier]smbclient[/font] error.  

**So,** we must check on a couple other possibilities then.  In your [font=courier]smbclient[/font] example, you seem to be trying to access the share from the server machine itself.  A connection error here makes me wonder if you might:
[list][*]have more success with [font=courier]smbclient[/font] by specifying the server machine's LAN IP address?  If so, problem partially solved.  :)
[*]be able to access the share from a different machine on your LAN?  If so, again, problem partially solved.  
[*]be running a firewall that's getting in the way?  If so, try opening ports 137,139, and 445.  This strikes me as the most likely possibility, now that I've taken the time to think this all through.  
[*]be having other network issues?  To confirm, try pinging yourself, like so:
```
ping -c 4 127.0.0.1
ping -c 4 127.0.1.1
```
The first is our old friend the loopback, and the second seems to be some new variation of the loopback that uses your hostname for local (i.e. same-machine) purposes.  If these fail out, you've got something screwy in your network config that'd need sorting out before any work on Samba can succeed.[/list]

Anyway, apologies for my previous confusion, and I hope this post instead might help get the investigation on a more promising track towards a solution.  

Cheers,

Eiríkr

---

