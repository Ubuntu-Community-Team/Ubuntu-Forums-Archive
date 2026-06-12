---
title: "Need Help with Samba please"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by MannyL on 2008-08-21
At home I have a 2003 domain. I wanted a NAS to store files on the network but decided with the amount of spare drives I have  it would be better to juts build a network server...

So now I have a Ubuntu system that I want to access from my PC's. 

Here is the information that I think is important. If you need more info please ask

1) The user accounts on the Linux system use the same names and passwords and the domain

2) uname -a shows 
Linux dumpster 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

3) Current mount info
emanuel@dumpster:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/mapper/storage-data on /var/shared type reiserfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdd1 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)
emanuel@dumpster:~$


4) The location of the share on the Ubuntu system in /var/shared

emanuel@dumpster:/var/shared$ ls -la
total 5
drwxr-xr-x 10 root root  232 2008-05-11 20:44 .
drwxr-xr-x 19 root root 4096 2008-05-24 13:50 ..
drwxrwxrwx  3 root root  120 2008-08-13 13:14 Applications
drwxrwxrwx  2 root root   48 2008-05-10 23:41 Books
drwxrwxrwx  3 root root  176 2008-08-02 16:53 common
drwxrwxrwx 11 root root  280 2008-08-02 18:12 Karaoke
drwxrwxrwx 21 root root  704 2008-08-02 16:42 Music
drwxrwxrwx  5 root root  128 2008-05-11 21:49 Video


Ok now for my smb.conf file which I'm sure has errors because I have no clue what I'm doing

#
 Sample configuration file for the Samba suite for Debian GNU/Linux.
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
	log file = /var/log/samba/log.%m
	idmap gid = 10000-20000
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	socket options = TCP_NODELAY
	obey pam restrictions = yes
	wins server = 192.168.3.3
	username map = /etc/samba/user.map
	map to guest = bad user
	winbind trusted domains only = yes
	encrypt passwords = yes
	smb passwd file = /etc/samba/smbpasswd
        public = yes
	realm = LEVY.HOME
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	dns proxy = no
	writeable = yes
	server string = %h server (Media)
	idmap uid = 10000-20000
	password server = kds.LEVY.HOME
	invalid users = root
	unix password sync = yes
	os level = 20
	syslog = 0
	security = share
	usershare allow guests = yes
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	debuglevel = 2
	pam password change = yes
# Winbind settings
# For testing
#	workgroup = levy.home

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# server string is the equivalent of the NT Description field

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.

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

# Cap the size of the individual log files (in KiB).

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.

# Do something sensible when Samba crashes: mail the admin a backtrace


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


   guest account = nobody

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.

# This option controls how nsuccessful authentication attempts are mapped 
# to anonymous connections

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
   domain logons = yes
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
usershare max shares = 998

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones

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
   create mask = 0777

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0777

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





[Music]
	comment = Music
	writable = yes
	public = yes
	path = /var/shared/Music
	available = yes
        browseable = yes
        guest ok = yes
        guest account = nobody
[Video]
	comment = Video Files
	writable = yes
	public = yes
	path = /var/shared/Video
	available = yes
        browseable = yes
        guest ok = yes
        guest account = nobody
[Books]
	comment = E-Books and Documentation
	writable = yes
	public = yes
	path = /var/shared/Books
	available = yes
        browseable = yes
        guest ok = yes
guest account = nobody

[Common]
	comment = Common Files
	writable = yes
	public = yes
	path = /var/shared/common
	available = yes
        browseable = yes
        guest ok = yes
guest account = nobody

[Applications]
	comment = Applications
	writable = yes
	public = yes
	path = /var/shared/Applications
	available = yes
guest account = nobody
[Karaoke]
        comment = Karaokes
        writable = yes
        public = yes
        path = /var/shared/Karaoke
        available = yes
        guest ok = yes
        browseable = yes
 guest account = nobody



What I want to happen is have any user on my local network be able to access any shared folder on the Ubuntu system.

---

### Post by Iowan on 2008-08-21
```
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic
# errors. 
```

One GOTCHA I see:```
syslog = 0
[COLOR="Red"]security = share[/COLOR]
usershare allow guests = yes
```Later, the default setting overrides it:```
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
[COLOR="Red"]security = user[/COLOR]
```Dunnof if **testparm** would catch it.

---

### Post by MannyL on 2008-08-21
Testparm shows

emanuel@dumpster:~$ testparm
Load smb config files from /etc/samba/smb.conf
params.c:Parameter() - Ignoring badly formed line in configuration file: Sample configuration file for the Samba suite for Debian GNU/Linux.
Processing section "[Music]"
Global parameter guest account found in service section!
Processing section "[Video]"
Global parameter guest account found in service section!
Processing section "[Books]"
Global parameter guest account found in service section!
Processing section "[Common]"
Global parameter guest account found in service section!
Processing section "[Applications]"
Global parameter guest account found in service section!
Processing section "[Karaoke]"
Global parameter guest account found in service section!
Loaded services file OK.
Server role: ROLE_DOMAIN_PDC
Press enter to see a dump of your service definitions
[global]
        workgroup = LEVY.HOME
        realm = LEVY.HOME
        server string = %h server (Media)
        map to guest = Bad User
        obey pam restrictions = Yes
        password server = kds.LEVY.HOME
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:                                              * %n\n *password\supdated\ssuccessfully* .
        username map = /etc/samba/user.map
        unix password sync = Yes
        log level = 2
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        domain logons = Yes
        dns proxy = No
        wins server = 192.168.3.3
        usershare allow guests = Yes
        usershare max shares = 998
        panic action = /usr/share/samba/panic-action %d
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind trusted domains only = Yes
        invalid users = root
        read only = No
        create mask = 0777
        guest ok = Yes

[Music]
        comment = Music
        path = /var/shared/Music

[Video]
        comment = Video Files
        path = /var/shared/Video

[Books]
        comment = E-Books and Documentation
        path = /var/shared/Books

[Common]
        comment = Common Files
        path = /var/shared/common

[Applications]
        comment = Applications
        path = /var/shared/Applications
        browseable = No

[Karaoke]
        comment = Karaokes
        path = /var/shared/Karaoke

I don't know if I should # out the security = user or security = share

---

### Post by dmizer on 2008-08-21
Please take a look at the first link in my sig.

---

### Post by MannyL on 2008-08-21
> **dmizer said:**
> Please take a look at the first link in my sig.

I am reading the how-to but it referred to workgroup I'm using a domain. I know there are differences but I don't what to substitute for workgroup = YOUR_WORKGROUP

---

### Post by dmizer on 2008-08-21
> **MannyL said:**
> I am reading the how-to but it referred to workgroup I'm using a domain. I know there are differences but I don't what to substitute for workgroup = YOUR_WORKGROUP

Check a Windows computer on your network to see what workgroup it's connected to.  You'll most likely need to use a combination of both howto's because the howto I linked (although quite good) does not include directions for hosting across a Windows active domain.

---

### Post by MannyL on 2008-08-21
> **dmizer said:**
> Check a Windows computer on your network to see what workgroup it's connected to.  You'll most likely need to use a combination of both howto's because the howto I linked (although quite good) does not include directions for hosting across a Windows active domain.

The windows systems are not in a workgroup. The domain is levy.home

---

### Post by Iowan on 2008-08-21
> **MannyL said:**
> I don't know if I should # out the security = user or security = share I'd start by commenting out the "security = user". It's very insecure, so you may want to try it the other way later.  

I suppose you noticed **testparm** was unhappy about multiple definitions of *guest account = nobody*?

---

### Post by MannyL on 2008-08-21
Yes I noticed it but with the changes I made it still does not work

root@dumpster:~# testparm


Load smb config files from /etc/samba/smb.conf
params.c:Parameter() - Ignoring badly formed line in configuration file: Sample configuration file for the Samba suite for Debian GNU/Linux.
Processing section "[Music]"
Processing section "[Video]"
Processing section "[Books]"
Processing section "[Common]"
Processing section "[Applications]"
Processing section "[Karaoke]"
Loaded services file OK.
Server role: ROLE_DOMAIN_PDC
Press enter to see a dump of your service definitions
[global]
        workgroup = LEVY.HOME
        realm = LEVY.HOME
        server string = %h server (Media)
        map to guest = Bad User
        obey pam restrictions = Yes
        password server = kds.LEVY.HOME
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        username map = /etc/samba/user.map
        unix password sync = Yes
        log level = 2
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        domain logons = Yes
        dns proxy = No
        wins server = 192.168.3.3
        usershare allow guests = Yes
        usershare max shares = 998
        panic action = /usr/share/samba/panic-action %d
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind trusted domains only = Yes
        invalid users = root
        read only = No
        create mask = 0777
        guest ok = Yes

[Music]
        comment = Music
        path = /var/shared/Music

[Video]
        comment = Video Files
        path = /var/shared/Video

[Books]
        comment = E-Books and Documentation
        path = /var/shared/Books

[Common]
        comment = Common Files
        path = /var/shared/common

[Applications]
        comment = Applications
        path = /var/shared/Applications
        browseable = No

[Karaoke]
        comment = Karaokes
        path = /var/shared/Karaoke
root@dumpster:~#


The error I get from the PC's are 

[IMG]http://i9.photobucket.com/albums/a51/MannyLNJ/general/error.jpg[/IMG]

---

### Post by Iowan on 2008-08-21
```
#
[COLOR="Red"]Sample configuration file for the Samba suite for Debian GNU/Linux.[/COLOR]
#
#
```The # disappeared from this line.

---

### Post by MannyL on 2008-08-21
> **Iowan said:**
> ```
#
[COLOR="Red"]Sample configuration file for the Samba suite for Debian GNU/Linux.[/COLOR]
#
#
```The # disappeared from this line.

Thanks for pointing that out now testparm doesn't complain

root@dumpster:~# testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[Music]"
Processing section "[Video]"
Processing section "[Books]"
Processing section "[Common]"
Processing section "[Applications]"
Processing section "[Karaoke]"
Loaded services file OK.
Server role: ROLE_DOMAIN_PDC
Press enter to see a dump of your service definitions


Still can't get to it from the XP system. I can get to it from a 2003 server logged in as Administrator

---

### Post by bab1 on 2008-08-24
I'm a little late on this one, but I hope this helps.  I believe that [COLOR="DarkOrange"]testparam[/COLOR] will test for [COLOR="Green"]correct[/COLOR] parameters, but not as to whether they are [COLOR="Blue"]appropriate[/COLOR].

> till can't get to it from the XP system. I can get to it from a 2003 server logged in as Administrator

Make sure that you have added yourself to the smbusers database.  it has to be [COLOR="Magenta"]**exactly**[/COLOR] like your XP login.

Below is a copy (modified slightly) of my smb.conf file.  It works for me in a workgroup environment.  If you have added the sever to a domain you will need "winbind" to administer the samba to user account mapping.

```
#
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Workgroup/NT-domain name your Samba server will part of
	workgroup = <YOUR_WORKGROUP>

# server string is the equivalent of the NT Description field
   ;hostname
	server string = %h

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
	log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
	max log size = 1000

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead.
	syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
	panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server if the server is in a 
# stand alone situation.  If this server is to be used in a domain situation 
# then "winbind" should be employed.

	security = user

# For use if the server is in a stand alone situation.
# Samba will need to know what password database type you are using.  
	passdb backend = tdbsam

	obey pam restrictions = yes

#  Bad user means "user not found in unix passwd" and 
#  we will default to the guest accout that we have defined  
	map to guest = bad user
# This is the user account withthe name "nobody"
	guest account = nobody

# No root user!
	invalid users = root

# This controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
	unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;	pam password change = no

############ Misc ############

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
;	socket options = TCP_NODELAY
	username map = /etc/samba/smbusers


#======================= Share Definitions =======================

[Share]
	comment = Public Share
	path = /path/to/share
	browseable = yes

	guest ok = yes
	writeable = yes
	create mask = 0775
	force create mode = 0775
	directory mask = 0775

#============= End ======================================================

```

---

