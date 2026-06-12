---
title: "Possible NetBIOS name issue in Samba"
date: 2014-05-31
forum: Networking &amp; Wireless
---

### Post by carl_schulze on 2014-05-31
Four computers: 2 Ubuntu 14.04 and 2 Windows 7 all sharing a network thru a single router.  Although all have defined themselves as members of WORKGROUP (all caps), the Win7 computers do not find the Ubuntu machines in Explorer:Network.  The Win7 machines see each other but none of the Ubuntu machines.  The Ubuntu machines can navigate Files > Browse Network > Windows Network > WORKGROUP, but clicking on the latter opens a dialog box "Password required for workgroup," showing username "carl," Domain "WORKGROUP," but there is no password that works.  Even though I've got "carl" as username in Samba with a familiar password, it does not work.

One thing I've noticed is that both the Ubuntu machines have full names that exceed 16 characters, which is apparently a Samba no-no.  Question: If I put "netbios name = (name<16 chars) just under "workgroup = WORKGROUP" in "Global Settings" of smb.conf, do I also need to change my root username, or is the "netbios name = (name<16 chars)" just a Samba definition and thus independent of my actual Ubuntu username?  I've tried "netbios name = EliteBook" and it still doesn't work.  Suggestions?

---

### Post by bab1 on 2014-05-31
> **carl_schulze said:**
> Four computers: 2 Ubuntu 14.04 and 2 Windows 7 all sharing a network thru a single router.  Although all have defined themselves as members of WORKGROUP (all caps), the Win7 computers do not find the Ubuntu machines in Explorer:Network.  The Win7 machines see each other but none of the Ubuntu machines.  The Ubuntu machines can navigate Files > Browse Network > Windows Network > WORKGROUP, but clicking on the latter opens a dialog box "Password required for workgroup," showing username "carl," Domain "WORKGROUP," but there is no password that works.  Even though I've got "carl" as username in Samba with a familiar password, it does not work.

As far as I know there is no password for a WORKGROUP.  The workgroup is not a security mechanism.  How have you configured Samba4?  Are you running the server as "standalone" or ADS domain?
> 
One thing I've noticed is that both the Ubuntu machines have full names that exceed 16 characters, which is apparently a Samba no-no.  Question: If I put "netbios name = (name<16 chars) just under "workgroup = WORKGROUP" in "Global Settings" of smb.conf, do I also need to change my root username, or is the "netbios name = (name<16 chars)" just a Samba definition and thus independent of my actual Ubuntu username?  I've tried "netbios name = EliteBook" and it still doesn't work.  Suggestions?

The NETBIOS name is what Samba ultimately uses to create add its name to the Master Browse List.  If your Linux hostname is longer than 15 characters the ***nmbd*** daemon has trouble converting the hostname into a proper NETBIOS name.  When you define a 15 character NETBIOS name as you suggested the ***nmbd ***daemon is not used for conversion.  You use 15 characters because there is a 1 character suffix that is appended depending upon the type of host (server, client and/or master browser).

You need to restart the smbd (Samba) daemon after configuring the smb.conf file.  You can restart Samba like this```
sudo service smbd restart
```

---

### Post by carl_schulze on 2014-06-01
> **bab1 said:**
> As far as I know there is no password for a WORKGROUP.  The workgroup is not a security mechanism.  How have you configured Samba4?  Are you running the server as "standalone" or ADS domain?

First, thanks so much for tackling my issue.
Second, I should have revealed earlier my lack of Linux expertise.  I've been running Ubuntu for about three years, but my tinkering has extended only as far as enabling my Ubuntu machines to print to a printer attached to one of the Win7 machines.  I found out how to do that through Ubuntu Forums. :p
Third, your use of "server" confuses me slightly.  All four machines are standalone, linked through a router; none is designated as a server.  If you mean "Samba server," then that would be the Ubuntu machine I defined as "netbios name = EliteBook" in [global] of smb.conf.  I do have 2 machines running Ubuntu 14.04, both having Samba installed.

Here's smb.conf for EliteBook:
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
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = WORKGROUP
	netbios name = EliteBook

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
;	dns proxy = no

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
	security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

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

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

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
;	printing = cups
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
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	username map = /etc/samba/smbusers
	guest ok = yes
	guest account = whoopsie

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
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
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
	username = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

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
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

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

[Public]
	path = /home/carl/Public
	writeable = yes
;	browseable = yes
	guest ok = yes

[home]
	comment = home folder on Carl EliteBook
	path = /home
	writeable = yes
;	browseable = yes
	valid users = carl

[Public]
	path = /home/carl/Public
	writeable = yes
;	browseable = yes
	guest ok = yes

[home-1]
	path = /home
	writeable = yes
;	browseable = yes
	valid users = whoopsie

```

BTW, here is a screenshot showing the sequence Files > Browse Network > Windows Network > WORKGROUP > "Password required for workgroup" dialog box.
[IMG]\\carl\files\pictures\Screenshot 2014-06-01 06:21.png[/IMG]
Hmmm, not sure if I did that right.

The NETBIOS name is what Samba ultimately uses to create add its name to the Master Browse List.  If your Linux hostname is longer than 15 characters the ***nmbd*** daemon has trouble converting the hostname into a proper NETBIOS name.  When you define a 15 character NETBIOS name as you suggested the ***nmbd ***daemon is not used for conversion.  You use 15 characters because there is a 1 character suffix that is appended depending upon the type of host (server, client and/or master browser).

You need to restart the smbd (Samba) daemon after configuring the smb.conf file.  You can restart Samba like this```
sudo service smbd restart
```

I did define "netbios name = EliteBook" in [global] and restarted Samba, but my Ubuntu machines are still invisible on the Win7 machines, and I still get the "Password required for wotkgroup" box on the Ubuntu machines.

Just to make sure: I did NOT change the actual name of my Ubuntu machine; it's still >16 characters.  All I did was to define the machine as "netbios name = EliteBook" in smb.conf.

---

### Post by bab1 on 2014-06-01
> **carl_schulze said:**
> ... your use of "server" confuses me slightly. All four machines are standalone, linked through a router; none is designated as a server. If you mean "Samba server," then that would be the Ubuntu machine I defined as "netbios name = EliteBook" in [global] of smb.conf. I do have 2 machines running Ubuntu 14.04, both having Samba installed.

In this context a server is a process that is continually running; waiting for a request for services (i.e to serve files).  The client is the requester of the services.  Any machine can be a server or a client, or both!  Ubuntu by default has the Samba client software installed.  When you "install samba" you are installing the server component.
> 
I did define "netbios name = EliteBook" in [global] and restarted Samba, but my Ubuntu machines are still invisible on the Win7 machines, and I still get the "Password required for wotkgroup" box on the Ubuntu machines.

Just to make sure: I did NOT change the actual name of my Ubuntu machine; it's still >16 characters.  All I did was to define the machine as "netbios name = EliteBook" in smb.conf.
The smb.conf file does not look to be the original file that comes with the default Ubuntu 14.04 install.  It also has a few configuration errors in it.  As a practical matter it would be much easier for you to revert to the default smb.conf file and start over.  I have attached a copy of the default unmolested smb.conf file for 14.04 if you need it.

There are elements of the [homes] share that are uncommented and others that are not.  Why is that?  You have shared directories that  are below other shared directories.  This should not be done.  Did you mean to do that?  Why have you shared the same directory multiple times?

I do not think you should provide *public * shares (multiple users) from your own home (/home/carl) directory nor should you share your entire /home directory using the name [home].  I place my Samba shares outside the /home filesystem.  I use /srv for that type of thing.  As the system administrator (sudoer) you can control the ownership and access of all the users on each of the hosts (computer).

Explain what you want to accomplish an we can create the correct shares.

What users?  What shares (public, semi-private and private)?

---

### Post by carl_schulze on 2014-06-02
> In this context a server is a process that is continually running; waiting for a request for services (i.e to serve files).  The client is the requester of the services.  Any machine can be a server or a client, or both!  Ubuntu by default has the Samba client software installed.  When you "install samba" you are installing the server component.


Thanks for such a clear, concise definition of server.  I get it now.

> The smb.conf file does not look to be the original file that comes with the default Ubuntu 14.04 install.  It also has a few configuration errors in it.  As a practical matter it would be much easier for you to revert to the default smb.conf file and start over.  I have attached a copy of the default unmolested smb.conf file for 14.04 if you need it.

There are elements of the [homes] share that are uncommented and others that are not.  Why is that?  You have shared directories that  are below other shared directories.  This should not be done.  Did you mean to do that?  Why have you shared the same directory multiple times?

I do not think you should provide *public * shares (multiple users) from your own home (/home/carl) directory nor should you share your entire /home directory using the name [home].  I place my Samba shares outside the /home filesystem.  I use /srv for that type of thing.  As the system administrator (sudoer) you can control the ownership and access of all the users on each of the hosts (computer).

For several days before I posted my issue, I tried to solve the issue on my own by looking around the internet for solutions, and I'm afraid what you saw in my smb.conf was the residue of those attempts.  Foolishly I did not make a copy of the unedited file and name it smb.original or something like that.  I'll be more cautious in the future.  

Anyway, I compared my smb.conf to yours and made sure that all my commands are the same as yours, even though some of the commentary differs between our two files ("smbstatus" in terminal gives me version 4.1.6).  I've also cleaned up my Samba Server Configuration files now, with only /carl/home/public now available.  Think that's all right?  Herewith my smb.conf

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
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
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
	security = user
	server role = standalone server

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

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

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

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
;	printing = cups
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
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
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
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;	username = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

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
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

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

[public]
	comment = public folder on Carl EliteBook
	path = /home/carl/Public
	writeable = yes
;	browseable = yes
	valid users = carl

```


> Explain what you want to accomplish an we can create the correct shares.

What users?  What shares (public, semi-private and private)?

What I want is to be able to drop files into folders like /public on the Ubuntu machines and /users/public on the Win7's and be able to browse to and copy them across the separate platforms.

Privacy inhouse is not really an issue, as all computers are in my residence and shared transparently by 3 family members. Beyond that I'm assuming that my Verizon FIOS firewall keeps our files secure from the outside.

---

### Post by bab1 on 2014-06-02
> **carl_schulze said:**
> 
```

[public]
	comment = public folder on Carl EliteBook
	path = /home/carl/Public
	writeable = yes
;	browseable = yes
	valid users = carl

```

What I want is to be able to drop files into folders like /public on the Ubuntu machines and /users/public on the Win7's and be able to browse to and copy them across the separate platforms.

Privacy inhouse is not really an issue, as all computers are in my residence and shared transparently by 3 family members. Beyond that I'm assuming that my Verizon FIOS firewall keeps our files secure from the outside.

At this point the Samba server and it's share should be visible, but only accessible by the user carl.  If you comment out the valid user then only the users that are Samba users will be able to access the share.  Have you made Samba users on the Ubuntu machine?  Post the output of this
```
sudo pdbedit -L 
```

I think it is important to differentiate between users and humans.  The system doesn't know that Sissy is using your account named *carl*.  I am only interested in user accounts.  You get to sort out what humans use them.  

Privacy is not really what I'm are talking about either when I use the share terms private or public.  It's more a matter of single user access versus multiple user access.

Can you see the Samba server from Windows?  Can you see the Samba server if you browse the network using the Ubuntu machine?

---

### Post by carl_schulze on 2014-06-02
> **bab1 said:**
> At this point the Samba server and it's share should be visible, but only accessible by the user carl.  If you comment out the valid user then only the users that are Samba users will be able to access the share.  Have you made Samba users on the Ubuntu machine?  Post the output of this
```
sudo pdbedit -L 
```

I think it is important to differentiate between users and humans.  The system doesn't know that Sissy is using your account named *carl*.  I am only interested in user accounts.  You get to sort out what humans use them.  

Privacy is not really what I'm are talking about either when I use the share terms private or public.  It's more a matter of single user access versus multiple user access.

Can you see the Samba server from Windows?  Can you see the Samba server if you browse the network using the Ubuntu machine?

Here's the output from ```
pdbedit -L
```
file:///home/carl/Pictures/Screenshot%202014-06-02%2018:37:32.png
[IMG]file:///home/carl/Pictures/Screenshot%202014-06-02%2018:37:32.png[/IMG]
Hope that came through. If not, the response was:
```
carl:1000:Carl W Schulze
whoopsie:105:
avahi:107:Avahi mDNS daemon

```

whoopsie and avahi are residues of early attempts to get things working, but they are currently not assigned any shares.


Except for the two Win7's being able to see and browse each other, no visibility yet.  Clicking on Files in the Ubuntu machines and then Browse Network, I get only an icon for Windows Network, but don't forget we have not done anything about the >16 chars usernames on the 2 Ubuntu machines.  For example, opening Terminal on U#1 I get "carl@carl-HP-Elitebook-2570p:~$" prompt and on U#2 I get "carl@carl-HP-Compaq-dx2250-Microtower:~$" prompt.  Shouldn't I insert a "netbios username = x" under "workgroup = WORKGROUP" in [global] first??

---

### Post by bab1 on 2014-06-02
> **carl_schulze said:**
> Here's the output from ```
pdbedit -L
```
file:///home/carl/Pictures/Screenshot%202014-06-02%2018:37:32.png
[IMG]file:///home/carl/Pictures/Screenshot%202014-06-02%2018:37:32.png[/IMG]
Hope that came through. If not, the response was:
I prefer the text only.  I don't need to see pictures at all.  So the following is great!> 
```
carl:1000:Carl W Schulze
whoopsie:105:
avahi:107:Avahi mDNS daemon

```
whoopsie and avahi are residues of early attempts to get things working, but they are currently not assigned any shares.
Neither of these should be part of you Samba users database. We should remove them.  You can remove the user with this command```
sudo pdbedit -x -u <user-name> 
```...where <user-name> is one of the users you want to delete.
> 
Except for the two Win7's being able to see and browse each other, no visibility yet.  

Clicking on Files in the Ubuntu machines and then Browse Network, I get only an icon for Windows Network, but don't forget we have not done anything about the >16 chars usernames on the 2 Ubuntu machines.  For example, opening Terminal on U#1 I get "carl@carl-HP-Elitebook-2570p:~$" prompt and on U#2 I get "carl@carl-HP-Compaq-dx2250-Microtower:~$" prompt.  Shouldn't I insert a "netbios username = x" under "workgroup = WORKGROUP" in [global] first??

Yes you should and each machine should have a unique NETBIOS name obviously.  ;-)

I would also recommend  that right under that you add this line so that the Samba uses broadcasts only.  
```
name resolve order = bcast
```Just like it is done on Windows.

You need to restart Samba for it all to work.  The restart command is ```
sudo service smbd restart
```

---

### Post by carl_schulze on 2014-06-02
> **bab1 said:**
> I prefer the text only.  I don't need to see pictures at all.  So the following is great!Neither of these should be part of you Samba users database. We should remove them.  You can remove the user with this command```
sudo pdbedit -x -u <user-name> 
```...where <user-name> is one of the users you want to delete.


Yes you should and each machine should have a unique NETBIOS name obviously.  ;-)

I would also recommend  that right under that you add this line so that the Samba uses broadcasts only.  
```
name resolve order = bcast
```Just like it is done on Windows.

You need to restart Samba for it all to work.  The restart command is ```
sudo service smbd restart
```

Okay, "whoopsie" and "avahi" are toast, and pdbedit -L confirms that only "carl:1000:Carl W Schulze" remains,  U#1 now has "netbios name = EliteBook" and U#2 has "netbios name = Microtower" and both have "name resolve order = bcast"

Still no cross-platform visibility though.  

Don't know how significant, but here are the user names (system, not Samba) for the four computers:
U#1 has only "carl"
U#2 has only "carl"
Win7 #1 has only "Lydia"
Win7 #2 has only "Carl" (note uppercase 'C')

Also, in Samba on U#1 in the Samba Server Configuration/Preferences/Samba Users, only "carl" is listed, and is listed as "Unix name = carl" and "Windows Username = Carl" and password protected.  Anything wrong with these usernames??

---

### Post by bab1 on 2014-06-02
> **carl_schulze said:**
> Okay, "whoopsie" and "avahi" are toast, and pdbedit -L confirms that only "carl:1000:Carl W Schulze" remains,  U#1 now has "netbios name = EliteBook" and U#2 has "netbios name = Microtower" and both have "name resolve order = bcast"

Still no cross-platform visibility though.  

Don't know how significant, but here are the user names (system, not Samba) for the four computers:
U#1 has only "carl"
U#2 has only "carl"
Win7 #1 has only "Lydia"
Win7 #2 has only "Carl" (note uppercase 'C')

Also, in Samba on U#1 in the Samba Server Configuration/Preferences/Samba Users, only "carl" is listed, and is listed as "Unix name = carl" and "Windows Username = Carl" and password protected.  Anything wrong with these usernames??

I Have no Windows machines up and running.  My only Windows machine is a Vista laptop that does see the entire Samba/Windows Sharing network.

Do both Ubuntu machines have identical configurations?  What do you get from U1 with this```
smbtree -d3
```  That's a lot of text to capture but if you redirect it to a file you can cut and past the information back into the terminal.  To redirect the output to a file you can do this```
smbtree -d3 >smbtree.txt
```...of course you could also just attach the file to the reply.

From that same machine; what do you get with this command```
smbclient -L EliteBook 
```  You can redirect the output the same way as the last command if you like.

FYI it is best on Linux machines if the user has the same uid and gid (user/group).  The user name is for us humans.  What do you get on the 2 different Ubuntu's (Ubunti ???) with this command```
getent passwd carl
```  Since they are the first mortal user they should have the uid of 1000.  If you add users, be careful of the order and make sure they have the same uid/gid

---

### Post by carl_schulze on 2014-06-02
> **bab1 said:**
> I Have no Windows machines up and running.  My only Windows machine is a Vista laptop that does see the entire Samba/Windows Sharing network.

Do both Ubuntu machines have identical configurations?  What do you get from U1 with this```
smbtree -d3
```  That's a lot of text to capture but if you redirect it to a file you can cut and past the information back into the terminal.  To redirect the output to a file you can do this```
smbtree -d3 >smbtree.txt
```...of course you could also just attach the file to the reply.

From that same machine; what do you get with this command```
smbclient -L EliteBook 
```  You can redirect the output the same way as the last command if you like.

FYI it is best on Linux machines if the user has the same uid and gid (user/group).  The user name is for us humans.  What do you get on the 2 different Ubuntu's (Ubunti ???) with this command```
getent passwd carl
```  Since they are the first mortal user they should have the uid of 1000.  If you add users, be careful of the order and make sure they have the same uid/gid

Both Ubuntu machines are 14.04 and I suppose are identically configured (?).

"smbtree -d3" on U#1 produces

[ATTACH]253686[/ATTACH]

and "smbclient -L" gives

[ATTACH]253687[/ATTACH]

(I hope I did those attachments correctly)

"getent passwd carl" on U#1 results in ```
carl:x:1000:1000:Carl W Schulze,,,:/home/carl:/bin/bash"
```
"getnet passwd carl" on U#2 produces absolutely the IDENTICAL result!

Is this the identiticality of UID & GID you want?

---

### Post by bab1 on 2014-06-02
> **carl_schulze said:**
> Both Ubuntu machines are 14.04 and I suppose are identically configured (?).

"smbtree -d3" on U#1 produces

```
Enter carl's password: 
WORKGROUP
	\\LYDIA-DESK     		
		\\LYDIA-DESK\Users          	
		\\LYDIA-DESK\Q$             	Default share
		\\LYDIA-DESK\IPC$           	Remote IPC
		\\LYDIA-DESK\C$             	Default share
		\\LYDIA-DESK\ADMIN$         	Remote Admin
	\\EXTRA          		
	\\ELITEBOOK      		carl-HP-EliteBook-2570p server (Samba, Ubuntu)
		\\ELITEBOOK\Seivom         	
		\\ELITEBOOK\Ant Videos     	
		\\ELITEBOOK\S_S            	
		\\ELITEBOOK\Documents      	
		\\ELITEBOOK\carl_lap       	
		\\ELITEBOOK\PrintOne       	HP LaserJet p2055d
		\\ELITEBOOK\print$         	Printer Drivers
		\\ELITEBOOK\public         	
		\\ELITEBOOK\IPC$           	IPC Service (carl-HP-EliteBook-2570p server (Samba, Ubuntu))
	\\               		carl-HP-Compaq-dx2250-Microtower server (Samba, 
```

This should have shown that debug (-d3) and it did not.  I can see the shares on both ELITEBOOK and LYDIA.  I can't see the server or the shares of MICROTOWER.  I'm sure you did not do this correctly.  Just run it for yourself to see.  It should look something like this  ```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::223:54ff:fe52:1a6e%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.3 bcast=192.168.1.255 netmask=255.255.255.0
Enter bab's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.3 ( 192.168.1.3 )
Connecting to host=192.168.1.3
Connecting to 192.168.1.3 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.3 ( 192.168.1.3 )
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>

...etc...etc...etc...


```> 

and "smbclient -L" gives

```
Enter carl's password: 
session setup failed: NT_STATUS_LOGON_FAILURE
```

Let's try this with debug also.  Post the output of this ```
smbclient -d3 -L ELITEBOOK
```

(I hope I did those attachments correctly)

The best way is to post them directly.  You can use the [SIZE=4]#[/SIZE] icon at the top of this editor (advanced) to provide the |code] [/code| blocks.  Then you just paste the text.

"getent passwd carl" on U#1 results in ```
carl:x:1000:1000:Carl W Schulze,,,:/home/carl:/bin/bash"
```
"getnet passwd carl" on U#2 produces absolutely the IDENTICAL result!

Is this the identiticality of UID & GID you want?  Yes the uid and gid should be the same so that the file ownership is consistent.  If you are 1000 on one machine and 1001 on the other then you might not get the proper ownership and permissions.

If you have any firewalls active on any of these machines you should stop them for the testing period.  In fact that is a test in itself.

---

### Post by carl_schulze on 2014-06-03
> **bab1 said:**
> This should have shown that debug (-d3) and it did not.  I can see the shares on both ELITEBOOK and LYDIA.  I can't see the server or the shares of MICROTOWER.  I'm sure you did not do this correctly.  Just run it for yourself to see.  It should look something like this  ```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::223:54ff:fe52:1a6e%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.3 bcast=192.168.1.255 netmask=255.255.255.0
Enter bab's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.3 ( 192.168.1.3 )
Connecting to host=192.168.1.3
Connecting to 192.168.1.3 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.3 ( 192.168.1.3 )
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>

...etc...etc...etc...


```  Yes the uid and gid should be the same so that the file ownership is consistent.  If you are 1000 on one machine and 1001 on the other then you might not get the proper ownership and permissions.

If you have any firewalls active on any of these machines you should stop them for the testing period.  In fact that is a test in itself.

Definitely something screwy with the suffix ">smbclient.txt" to a Terminal command as the text file continues to show only a very truncated version of what I actually see in terminal, so instead I've gone to recording things in Terminal with the "script text.log" command so I can cut/paste output into our discussions.

Anyway, smbtree -d3 produces this on U#1

```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=192.168.1.4 bcast=192.168.1.255 netmask=255.255.255.0
Enter carl's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.9 ( 192.168.1.9 )
Connecting to 192.168.1.9 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.9 ( 192.168.1.9 )
Connecting to 192.168.1.9 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\EXTRA          		
name_resolve_bcast: Attempting broadcast lookup for name EXTRA<0x20>
Got a positive name query response from 192.168.1.6 ( 192.168.1.6 )
Connecting to 192.168.1.6 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
	\\ELITEBOOK      		carl-HP-EliteBook-2570p server (Samba, Ubuntu)
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
		\\ELITEBOOK\Seivom         	
		\\ELITEBOOK\Ant Videos     	
		\\ELITEBOOK\S_S            	
		\\ELITEBOOK\Documents      	
		\\ELITEBOOK\carl_lap       	
		\\ELITEBOOK\PrintOne       	HP LaserJet p2055d
		\\ELITEBOOK\print$         	Printer Drivers
		\\ELITEBOOK\public         	
		\\ELITEBOOK\IPC$           	IPC Service (carl-HP-EliteBook-2570p server (Samba, Ubuntu))
	\\               		carl-HP-Compaq-dx2250-Microtower server (Samba, 
name_resolve_bcast: Attempting broadcast lookup for name <0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f5d8ac46ef0] mpx_fde[(nil)] fd[16] - disabling
]0;carl@carl-HP-EliteBook-2570p: ~carl@carl-HP-EliteBook-2570p:~$ exit
exit

Script done on Tue 03 Jun 2014 07:52:23 AM EDT
```

"smbclient -d3 -L EliteBook" produces differing results when run by a regular user or a superuser.

Regular user =

```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=192.168.1.4 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 4.1.6-Ubuntu).
Enter carl's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
session setup failed: NT_STATUS_LOGON_FAILURE
]0;carl@carl-HP-EliteBook-2570p: ~carl@carl-HP-EliteBook-2570p:~$ exit
exit

Script done on Tue 03 Jun 2014 08:15:28 AM EDT
```

Note the "session setup failed: NT_STATUS_LOGON_FAILURE" near the end.  When I run the same command prefixed with "sudo" I get past that and see more information:

```
[sudo] password for carl: 
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=192.168.1.4 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 4.1.6-Ubuntu).
Enter root's password: 
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (carl-HP-EliteBook-2570p server (Samba, Ubuntu))
	public          Disk      
	print$          Disk      Printer Drivers
	PrintOne        Printer   HP LaserJet p2055d
	carl_lap        Disk      
	Documents       Disk      
	S_S             Disk      
	Ant Videos      Disk      
	Seivom          Disk      
Connecting to 192.168.1.4 at port 139
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Server               Comment
	---------            -------
	                     carl-HP-Compaq-dx2250-Microtower server (Samba, 
	ELITEBOOK            carl-HP-EliteBook-2570p server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            
]0;carl@carl-HP-EliteBook-2570p: ~carl@carl-HP-EliteBook-2570p:~$ exit
exit

Script done on Tue 03 Jun 2014 08:18:04 AM EDT
```

As to firewalls, "sudo ufw status" produces "inactive" on both Ubuntus

To my chagrin I found that both Win7's had active firewalls, so I turned them off for home network but left them on for public networks.  I trust that is OK.

If it's any help, the ip's of the four machines are:
U#1 192.168.1.4 (EliteBook)
U#2 192.168.1.9 (Microtower)
Win7#1 192.168.1.7 (Lydia-desk)
Win7#2 192.168.1.6 (Extra)

---

### Post by bab1 on 2014-06-03
> **carl_schulze said:**
> Definitely something screwy with the suffix ">smbclient.txt" to a Terminal command as the text file continues to show only a very truncated version of what I actually see in terminal, so instead I've gone to recording things in Terminal with the "script text.log" command so I can cut/paste output into our discussions.

I think that's because there is a password in the beginning and it terminates the redirect of the final part.  So we just need to cut and paste the text in the terminal
> 

Anyway, smbtree -d3 produces this on U#1

AKA EliteBook

Just my opinion here; although it should work you are going to learn to hate CAPS using the terminal.
> 

```

...
added interface wlan0 ip=192.168.1.4 bcast=192.168.1.255 netmask=255.255.255.0
[COLOR="#FF0000"]# adding EliteBook's interface[/COLOR]

name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.9 ( 192.168.1.9 )
Connecting to 192.168.1.9 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215

WORKGROUP
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.9 ( 192.168.1.9 )
Connecting to 192.168.1.9 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\EXTRA  
[COLOR="#FF0000"]# This appears to start out looking for the workgroup (WORKGROUP), but ends up choking on 192.168.1.6 (EXTRA)[/COLOR] 
       		
	\\               		carl-HP-Compaq-dx2250-Microtower server (Samba, 
name_resolve_bcast: Attempting broadcast lookup for name <0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f5d8ac46ef0] mpx_fde[(nil)] fd[16] - disabling
[COLOR="#FF0000"]Finally dying as it can't resolve a blank name (//                )[/COLOR]
```

"smbclient -d3 -L EliteBook" produces differing results when run by a regular user or a superuser.

You shouldn't use sudo  (or the user root) for this type of testing.  Samba is for mortal users (human accounts) so that is what we need to use.
> 

Regular user =

```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=192.168.1.4 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 4.1.6-Ubuntu).
Enter carl's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
session setup failed: NT_STATUS_LOGON_FAILURE

```

Note the "session setup failed: NT_STATUS_LOGON_FAILURE" near the end. 

So now the work begins. We need to figure out why the user carl can't log in to the Samba server.
> 
As to firewalls, "sudo ufw status" produces "inactive" on both Ubuntus

To my chagrin I found that both Win7's had active firewalls, so I turned them off for home network but left them on for public networks.  I trust that is OK.

If it's any help, the ip's of the four machines are:
U#1 192.168.1.4 (EliteBook)
U#2 192.168.1.9 (Microtower)
Win7#1 192.168.1.7 (Lydia-desk)
Win7#2 192.168.1.6 (Extra)

It looks like you have 2 problems.  Name services and User Authentication.  I think we need to deal with EliteBook only at this point.  Can we turn off all the other machines (U2, W1 and W2)?  This will force EliteBook to become the Master Browser ( for name services). Also as the user *carl* just hit enter when it asks for a password.  This will force Samba to use the bad user account.  This should be the user nobody.  It should work for what we want to do.

After turning off the 3 machines, wait 15 minutes before working only from EliteBook (U1): as the root user check the Samba users.  Post the output of this```
sudo pdebedit -L
```

Test for working smb.conf file parameters.  Post the output of this```
testparm -s
```

Test that you can list the shares on EliteBook .  Post the output of this```
smbclient -d3 -L elitebook
```...The NETBIOS name can be either UPPERCASE or lowercase or a combination of both  Remember, no password; just hit enter.

My style of diagnosis is to start with on machine and make it right.  The I can expand out to the next machine and the network.

---

### Post by carl_schulze on 2014-06-04
> **bab1 said:**
> I think that's because there is a password in the beginning and it terminates the redirect of the final part.  So we just need to cut and paste the text in the terminal

AKA EliteBook

Just my opinion here; although it should work you are going to learn to hate CAPS using the terminal.

You shouldn't use sudo  (or the user root) for this type of testing.  Samba is for mortal users (human accounts) so that is what we need to use.

So now the work begins. We need to figure out why the user carl can't log in to the Samba server.


It looks like you have 2 problems.  Name services and User Authentication.  I think we need to deal with EliteBook only at this point.  Can we turn off all the other machines (U2, W1 and W2)?  This will force EliteBook to become the Master Browser ( for name services). Also as the user *carl* just hit enter when it asks for a password.  This will force Samba to use the bad user account.  This should be the user nobody.  It should work for what we want to do.

After turning off the 3 machines, wait 15 minutes before working only from EliteBook (U1): as the root user check the Samba users.  Post the output of this```
sudo pdebedit -L
```

Test for working smb.conf file parameters.  Post the output of this```
testparm -s
```

Test that you can list the shares on EliteBook .  Post the output of this```
smbclient -d3 -L elitebook
```...The NETBIOS name can be either UPPERCASE or lowercase or a combination of both  Remember, no password; just hit enter.

My style of diagnosis is to start with on machine and make it right.  The I can expand out to the next machine and the network.

Not sure where you're going with the CAPs issue, but to ease things I've revised smb.conf so that "netbios name = elitebook" from now on.

I turned off all four machines for an hour while I ran an errand and on returning fired up only U1 (elitebook).

```
carl@carl-HP-EliteBook-2570p:~$ sudo pdbedit -L
carl:1000:Carl W Schulze
```

You gave me "pdebedit" as the command, but using Google I easily figured out you had an extra "e" in it.  Also, a null entry for password here did not work; I had to enter my actual root password to continue.

```
carl@carl-HP-EliteBook-2570p:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[public]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	netbios name = ELITEBOOK
	server string = %h server (Samba, Ubuntu)
	server role = standalone server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = bcast
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[public]
	comment = public folder on Carl EliteBook
	path = /home/carl/Public
	valid users = carl
	read only = No

```

```
carl@carl-HP-EliteBook-2570p:~$ smbclient -d3 -L elitebook
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=192.168.1.4 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 4.1.6-Ubuntu).
Enter carl's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name elitebook<0x20>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	public          Disk      
	IPC$            IPC       IPC Service (carl-HP-EliteBook-2570p server (Samba, Ubuntu))
	PrintOne        Printer   HP LaserJet p2055d
	carl_lap        Disk      
	Documents       Disk      
	S_S             Disk      
	Ant Videos      Disk      
	Seivom          Disk      
name_resolve_bcast: Attempting broadcast lookup for name elitebook<0x20>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to 192.168.1.4 at port 139
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Server               Comment
	---------            -------
	ELITEBOOK            carl-HP-EliteBook-2570p server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            ELITEBOOK

```

This time the null entry for "carl's password" worked.

Thanks again for all your work on this.

---

### Post by carl_schulze on 2014-06-04
Just noticed that at the end of "testparm -s" results an "EliteBook" spelling.  Hope I didn't screw things up by changing it to "elitebook" in [global] of smb.conf.

> [public]
	comment = public folder on Carl EliteBook
	path = /home/carl/Public
	valid users = carl
	read only = No

---

### Post by bab1 on 2014-06-04
> **carl_schulze said:**
> Not sure where you're going with the CAPs issue, but to ease things I've revised smb.conf so that "netbios name = elitebook" from now on.

Sorry about that.  I should know better than to post replies while distracted and without enough sleep.  :-(
The unix/linux culture is to never use caps for names.  As Linux is a case sensitive OS;  EliteBook is not the same as either ELITEBOOK or elitebook.  It's just easier to use all lower case with Linux.  Samba will convert to the proper case as it needs to.
> 
I turned off all four machines for an hour while I ran an errand and on returning fired up only U1 (elitebook).

```
carl@carl-HP-EliteBook-2570p:~$ sudo pdbedit -L
carl:1000:Carl W Schulze
```

You gave me "pdebedit" as the command, but using Google I easily figured out you had an extra "e" in it.  Also, a null entry for password here did not work; I had to enter my actual root password to continue.

Yes indeed.  Can I use the sleepyness excuse again?  ;-) 
> 

This time the null entry for "carl's password" worked.


I believe this machine is setup correctly as far as nameservices is concerned.  Note that the Master Browse List is now being held by this machine.  See here in red```

	Server               Comment
	---------            -------
	ELITEBOOK            carl-HP-EliteBook-2570p server (Samba, Ubuntu)

	Workgroup            [COLOR="#FF0000"]Master[/COLOR]
	---------            [COLOR="#FF0000"]-------[/COLOR]
	WORKGROUP            [COLOR="#FF0000"]ELITEBOOK[/COLOR]

```

I know this is a pain but we need to see if this host is still the Master Browser today.  Can you run this command again and check to see if ELITEBOOK is still the Master Browser (no password)```

smbclient -d3 -L elitebook
```

If we have the same output as above then repeat the command using the password for carl.  Post the output for this last command here.

---

### Post by carl_schulze on 2014-06-05
> **bab1 said:**
> Sorry about that.  I should know better than to post replies while distracted and without enough sleep.  :-(
The unix/linux culture is to never use caps for names.  As Linux is a case sensitive OS;  EliteBook is not the same as either ELITEBOOK or elitebook.  It's just easier to use all lower case with Linux.  Samba will convert to the proper case as it needs to.

Yes indeed.  Can I use the sleepyness excuse again?  ;-) 

I believe this machine is setup correctly as far as nameservices is concerned.  Note that the Master Browse List is now being held by this machine.  See here in red```

	Server               Comment
	---------            -------
	ELITEBOOK            carl-HP-EliteBook-2570p server (Samba, Ubuntu)

	Workgroup            [COLOR="#FF0000"]Master[/COLOR]
	---------            [COLOR="#FF0000"]-------[/COLOR]
	WORKGROUP            [COLOR="#FF0000"]ELITEBOOK[/COLOR]

```

I know this is a pain but we need to see if this host is still the Master Browser today.  Can you run this command again and check to see if ELITEBOOK is still the Master Browser (no password)```

smbclient -d3 -L elitebook
```

If we have the same output as above then repeat the command using the password for carl.  Post the output for this last command here.

[global] 
           sleepiness = good excuse

Anyway, repeating smbclient -d3 -L elitebook with null password gives identical results to yesterday

```
carl@carl-HP-EliteBook-2570p:~$ smbclient -d3 -L elitebook
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=192.168.1.4 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 4.1.6-Ubuntu).
Enter carl's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name elitebook<0x20>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (carl-HP-EliteBook-2570p server (Samba, Ubuntu))
	public          Disk      
	print$          Disk      Printer Drivers
	PrintOne        Printer   HP LaserJet p2055d
	carl_lap        Disk      
	Documents       Disk      
	S_S             Disk      
	Ant Videos      Disk      
	Seivom          Disk      
name_resolve_bcast: Attempting broadcast lookup for name elitebook<0x20>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to 192.168.1.4 at port 139
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Server               Comment
	---------            -------
	ELITEBOOK            carl-HP-EliteBook-2570p server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            ELITEBOOK

```

But entering root password resulted in the dreaded "session setup failed: NT_STATUS_LOGON_FAILURE"

```
carl@carl-HP-EliteBook-2570p:~$ smbclient -d3 -L elitebook
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=192.168.1.4 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 4.1.6-Ubuntu).
Enter carl's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name elitebook<0x20>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
session setup failed: NT_STATUS_LOGON_FAILURE
```

BTW, just for fun I tried Files/Network/Browse Network and got two icons, "ELITEBOOK" and "Windows Network."  Clicking on Windows Network > WORKBOOK, and clicking on WORKBOOK > ELITEBOOK, and clicking on ELITEBOOK gave a list of the folders on elitebook that I had designated as sharable.  I was NOT queried for a password at any time. :P

Subsequent to writing the above I was "required" to file up W1 (42 years of marriage trumps a lot of stuff) and found that I was able to find LYDIA-DESK (=W1) when I browsed to WORKGROUP on U1 and able to open a text file there.  Likewise, looking at "Network" on W1 I could see "ELITEBOOK" and open a text file there.  Not surprisingly running "smbclient -d3 -L elitebook" with null password now produces the same result as without W1 on the network, except that now "LYDIA-DESK" shows up in the list at the end:

Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Server               Comment
	---------            -------
	ELITEBOOK            carl-HP-EliteBook-2570p server (Samba, Ubuntu)
	LYDIA-DESK           

	Workgroup            Master
	---------            -------
	WORKGROUP            ELITEBOOK

---

### Post by bab1 on 2014-06-05
> But entering root password resulted in the dreaded "session setup failed: NT_STATUS_LOGON_FAILURE"

By this do you mean the user ***root ***?  What happens if you use the password of the user ***carl***?
> 
BTW, just for fun I tried Files/Network/Browse Network and got two icons, "ELITEBOOK" and "Windows Network." Clicking on Windows Network > WORKBOOK, and clicking on WORKBOOK > ELITEBOOK, and clicking on ELITEBOOK gave a list of the folders on elitebook that I had designated as sharable. I was NOT queried for a password at any time.

You should be able to just click on ELITEBOOK to access the shares.  Both icons lead to the same data.
> 
Subsequent to writing the above I was "required" to file up W1 (42 years of marriage trumps a lot of stuff)

Yes indeed.  I'm working on 35 years myself.  A happy wife leads to a happy life.
> 
... and found that I was able to find LYDIA-DESK (=W1) when I browsed to WORKGROUP on U1 and able to open a text file there. Likewise, looking at "Network" on W1 I could see "ELITEBOOK" and open a text file there. Not surprisingly running "smbclient -d3 -L elitebook" with null password now produces the same result as without W1 on the network, except that now "LYDIA-DESK" shows up in the list at the end
```
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]
Server Comment
--------- -------
ELITEBOOK carl-HP-EliteBook-2570p server (Samba, Ubuntu)
LYDIA-DESK

Workgroup Master
--------- -------
WORKGROUP ELITEBOOK 
```

I think the system is working okay right now.  When ELITEBOOK became the Master Browser I think the problem went away.  If we are going to have a problem it's going to be with MICROTOWER.  Boot up microtower and wait a about 15 minutes for the machine to be added to the Browse List.  The post he output of this from ELITEBOOK (using both null password and ***carl*** password)```
smbclient -d3 -L microtower
```

---

### Post by carl_schulze on 2014-06-05
> 
By this do you mean the user root ? What happens if you use the password of the user carl?

My bad.  Of course I meant password for user carl.  As it happens, that password is identical to root's password, so I used "root" when I shouldn't have.  I was entering "smbclient -d3 -L elitebook" as user carl, not as root.

> 
You should be able to just click on ELITEBOOK to access the shares. Both icons lead to the same data.

Yes, I confirmed that, but since the sequence Browse Network > Windows Network > WORKGROUP had been the source of so much frustration before, I wanted to see what would happen with that sequence now.

> I think the system is working okay right now. When ELITEBOOK became the Master Browser I think the problem went away. If we are going to have a problem it's going to be with MICROTOWER. Boot up microtower and wait a about 15 minutes for the machine to be added to the Browse List. The post he output of this from ELITEBOOK (using both null password and carl password)

doing smbclient -d3 -L microtower with null password gives:

> carl@carl-HP-EliteBook-2570p:~$ smbclient -d3 -L micrtower[K[K[K[K[Kotower
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=192.168.1.4 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 4.1.6-Ubuntu).
Enter carl's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name microtower<0x20>
Got a positive name query response from 192.168.1.9 ( 192.168.1.9 )
Connecting to 192.168.1.9 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	seivom          Disk      seivom
	root directory  Disk      
	IPC$            IPC       IPC Service (carl-HP-Compaq-dx2250-Microtower server (Samba, Ubuntu))
	HP-LaserJet-p2055d Printer   HP LaserJet p2055d
	Documents       Disk      
	Public          Disk      
name_resolve_bcast: Attempting broadcast lookup for name microtower<0x20>
Got a positive name query response from 192.168.1.9 ( 192.168.1.9 )
Connecting to 192.168.1.9 at port 139
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Server               Comment
	---------            -------
	ELITEBOOK            carl-HP-EliteBook-2570p server (Samba, Ubuntu)
	MICROTOWER           carl-HP-Compaq-dx2250-Microtower server (Samba, 

	Workgroup            Master
	---------            -------
	WORKGROUP            ELITEBOOK

with carl's password:

> carl@carl-HP-EliteBook-2570p:~$ smbclient -d3 -L microtower
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=192.168.1.4 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 4.1.6-Ubuntu).
Enter carl's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name microtower<0x20>
Got a positive name query response from 192.168.1.9 ( 192.168.1.9 )
Connecting to 192.168.1.9 at port 445
Connecting to 192.168.1.9 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f2224ead440] mpx_fde[(nil)] fd[8] - disabling
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	seivom          Disk      seivom
	root directory  Disk      
	IPC$            IPC       IPC Service (carl-HP-Compaq-dx2250-Microtower server (Samba, Ubuntu))
	HP-LaserJet-p2055d Printer   HP LaserJet p2055d
	Documents       Disk      
	Public          Disk      
name_resolve_bcast: Attempting broadcast lookup for name microtower<0x20>
Got a positive name query response from 192.168.1.9 ( 192.168.1.9 )
Connecting to 192.168.1.9 at port 139
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Server               Comment
	---------            -------
	ELITEBOOK            carl-HP-EliteBook-2570p server (Samba, Ubuntu)
	MICROTOWER           carl-HP-Compaq-dx2250-Microtower server (Samba, 

	Workgroup            Master
	---------            -------
	WORKGROUP            ELITEBOOK

Some slight differences, no?

Current state of affairs
1) W1 sees and can browse both Ubuntus
2) U2 sees and can browse both W1 and U1 (Browse Network shows 4 icons, ELITEBOOK,LYDIA-DESK,MICROTOWER, and Windows Network)
3) U1 sees and can browse both W1 and U2, though sometimes one must try more than once to get a response to a browse.

---

### Post by bab1 on 2014-06-06
> **carl_schulze said:**
> ... Some slight differences [in what is displayed], no?
The two machines (elitebook and microtower) are close enough.  The Master Browser is elitebook for the entire NETBIOS network (Samba and WIndows sharing).  This will stay that way until elitebook is shut down and drops off the network.  Then the remaining up and online hosts will hold an election to name a new Master Browser and a new list is created.

That's why I had you turn off all the machines except elitebook so it would win the election.  I think there was something wrong with the previous Master Browse List.  
> 
Current state of affairs
1) W1 sees and can browse both Ubuntus
2) U2 sees and can browse both W1 and U1 (Browse Network shows 4 icons, ELITEBOOK,LYDIA-DESK,MICROTOWER, and Windows Network)
3) U1 sees and can browse both W1 and U2, though sometimes one must try more than once to get a response to a browse.
So every host (computer) can see all the other hosts and you have access to all the shares.  Can you create or modify a file?  Can you create or delete a directory?

---

