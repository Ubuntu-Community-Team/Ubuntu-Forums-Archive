---
title: "Samba Installed, can't connect to mshome work groups"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by theyain on 2007-06-09
Hi, I am trying to connect to a shared folder on a Windows computer from my UbuBox.  As the title says, I have Samba installed and I can see my own shared folder on the network too.  But for some reason I can't access any of the shared folders on the network.  Any help?

---

### Post by ukripper on 2007-06-09
> **theyain said:**
> Hi, I am trying to connect to a shared folder on a Windows computer from my UbuBox.  As the title says, I have Samba installed and I can see my own shared folder on the network too.  But for some reason I can't access any of the shared folders on the network.  Any help?

Paste your smb.conf here by issuing following in terminal:

```
sudo gedit /etc/samba/smb.conf
```

---

### Post by bigken on 2007-06-09
try this in a terminal

sudo smbpasswd -e yourname


sudo smbpasswd -a yourname

---

### Post by theyain on 2007-06-09
> **ukripper said:**
> Paste your smb.conf here by issuing following in terminal:

Here,

```
sudo gedit /etc/samba/smb.conf
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

wins support = yes
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



[Dumpsta!]
path = /home/theyain/Dumpsta!
comment = A Dumpster To Help eillo
available = yes
browsable = yes
public = yes
writable = yes
```



Does that help?

---

### Post by ukripper on 2007-06-09
Follow this guide :
[http://ubuntuforums.org/showthread.php?t=202605&highlight=Howto+samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=Howto+samba)


and enable WINS support from no to yes

---

### Post by dmizer on 2007-06-10
you can edit smb.conf all day long and still not be able to view shares on windows computers.  configuring samba merely means that you have configured your computer to allow windows computers to view your ubuntu machine.

further ... wins support should be "no" in smb.conf unless you have a static network AND you have edited your hosts file to include all your network machine ip addresses and names.

to connect to shares on a windows computer, you'll need to check out the 2nd link in my sig.

---

### Post by theyain on 2007-06-10
Well, it seems that just showing the conf file for samba seemed to of fixed the problem.  Now it not only shows the files in the smhome network directory, but it also shows them in just the "network:///" directory.  So some how, some way, everything is fixed and working better then it did before!

---

### Post by ukripper on 2007-06-11
Depends on how you have configured your network. The link i pasted above worked for me perfectly and I have added Wins server support on windows machines by just adding my ubuntu ip on wins  makes it much reliable in my case. I am using Static Ip as i have also got FTP server running behind NAT. Anyhow, good to hear your samba works again.

Besides, if you enable wins server support and add ip to windows machines it just automatically updates your host records.

---

### Post by Dedoimedo on 2007-06-11
Hello,


First, make sure you have shared folders on Windows ...

You can see this for more details:
[http://ubuntuforums.org/showthread.php?t=465896](http://ubuntuforums.org/showthread.php?t=465896)

Try this:

First, install Samba:

apt-get install samba

After the Samba server is installed, you will need to edit a few options in the configuration file to allow sharing privileges.

cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
gedit /etc/samba/smb.conf

In the configuration file, you will need to setup a number of parameters:

* workgroup = workgroup_name - the name of the Workgroup for your LAN (e.g. HOME)
* netbios name = netbios_name - without spaces; computer alias by which you will be able to call it across the network
* security = user

After saving the configuration file, you will have to restart the Samba server:

/etc/init.d/samba restart

Now, via home folder, select a folder that you wish to share. If you have ticked the option Writable, you will be able to modify the contents of this folder.

Finally, to be able to connect to this share from Windows, you will have to create a Samba user:

smbpasswd -a 'name'

Under 'name' you should specify an existing UNIX user. Do not forget the apostrophes! You will be asked to create a password. And finally, restart the Samba server again, for the changes to take effect.

Now, the sharing itself. Very simple.

Windows > Linux

Start > Run > \\xxx.xxx.xxx.xxx OR \\netbios_name


When asked for username and password, provide the Samba user name and the relevant password. And that's it. Browse to the shared folder. If the shared folder is writable, you will be able to modify the contents.

Linux > Windows

Press Alt + F2.

This will bring up the Run Command window. In the Command line, specify the IP address or the name of the computer that you wish to connect.

Dedoimedo

---

