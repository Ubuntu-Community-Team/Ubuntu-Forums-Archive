---
title: "Windows can't log into ubuntu"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by SonicSteve on 2006-10-14
Hi again,
I know that one of you will probably point out some wiki or thread that outlines exactly this but... I can't find it. So please make me feel silly!

It's fairly simple,
From ubuntu networking I've sucessfully accessed all shares on my Windows XP pc. I even got the whole read write access going well now. 
But...
I've never been able to access my ubuntu pc share from my windows pc.
I can use start, run, //hostname and see the ubuntu pc. I can browse the network and there it is in the same workgroup. When I try to access the shares it asks for username and password (all well and good) but no username or password will grant access. 
So please help. I'm sure it's not a big thing but I don't know what it is either.
Here is my smb.conf file.

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
;   valid users = steve

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = yes

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


[UbSh]
path = /home/steve/UbSh
comment = Ubuntu Share folder
available = yes
browseable = yes
public = yes
writable = yes


So does anyone know if the problem is here or perhaps somewhere else.
Steve

---

### Post by kidders on 2006-10-14
Have you set up any samba users?

Creating a Linux user doesn't necessarily create a corresponding Samba account ... unless of course you've done something to arrange things that way. Try using **smbpasswd** to give yourself a Samba password.

---

### Post by SonicSteve on 2006-10-14
steve@ubuntu:~/Benchmarking/cachebench$ sudo smbpasswd
Password:
New SMB password:
Retype new SMB password:
Unable to open/create TDB passwd
pdb_getsampwnam: Unable to open TDB passwd (/var/lib/samba/passdb.tdb)!
Failed to find entry for user root.
Failed to modify password entry for user root

I totally took this for granted.
However how do you get past this error?

---

### Post by apjone on 2006-10-15
me@me:~$sudo smbpasswd steve


You need to tell it who's password you want to set

---

### Post by SonicSteve on 2006-10-15
I think were onto something here but..
A very similar error is happening

steve@ubuntu:~$ sudo smbpasswd steve
New SMB password:
Retype new SMB password:
Unable to open/create TDB passwd
pdb_getsampwnam: Unable to open TDB passwd (/var/lib/samba/passdb.tdb)!
Failed to find entry for user steve.
Failed to modify password entry for user steve

So why can't I create/open this file?

---

### Post by SonicSteve on 2006-10-15
OK so I fixed it. 
Here is what i did. Searched the interent for this error and found that if you change one entry in the smb.conf file 
from
passdb = tbsam (or whatever it is by default)
to 
passdb = smbpasswd

you can then create samba users and give them passwords.
My question is this; Why isn't it this way by default?
Is the default way for using NFS or linux based file sharing and not samba?

---

### Post by kidders on 2006-10-16
> **SonicSteve said:**
> OK so I fixed it. 
Searched the internet for this error and found that if you change one entry in the smb.conf file 
from
passdb = tbsam (or whatever it is by default)
to 
passdb = smbpasswd
you can then create samba users

Yep... if you remove the need for the problem file, by switching to a different passwording mechanism, Samba will stop complaining :-)

Imo it's tough to choose a "default" way for Samba to manage authentication, since every second user wants slightly different things. For instance, *I* like to use the tbsam back end. NFS, however, authenticates its users in a completely different way, so you don't need to worry about undesirable knock-on effects of your changes.

Glad you sorted your problem!

---

### Post by apjone on 2006-10-17
it was default on my 6.06 install, hmm, package must of canged.

---

### Post by tjr on 2006-10-17
or automatically sync unix with samba passwords. on ubuntu 6.06.1:

/etc/samba/smb.conf
[homes]
writable = yes #not required, but makes it more useful


apt-get install libpam-smbpass


/etc/pam.d/common-password
#password   required   pam_unix.so nullok obscure min=4 max=8 md5
password   requisite    pam_unix.so shadow md5 try_first_pass obscure min=4
password   required     pam_smbpass.so nullok use_authtok try_first_pass  obscure min=4


#BUG: freshly created users will still not be able to log in via samba (need to do similar magic to pam_useradd.so)
#workaround: have them change passwords

---

