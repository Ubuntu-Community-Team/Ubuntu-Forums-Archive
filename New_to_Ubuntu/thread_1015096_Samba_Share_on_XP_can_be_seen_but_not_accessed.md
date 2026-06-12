---
title: "Samba Share on XP can be seen but not accessed"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by bigtel on 2008-12-18
I am running Ubuntu 7.10 on my laptop and am running XP on my desktop. I have set up shared folders using samba, but my problem is this. I can access my Ubuntu folders via my XP computer no problem. But I can only see my XP shared folders via my Ubuntu laptop - but I can not access them - it seems like the folders are empty.

I eventually want to set up my laptop to print via the XP machine - but I need to get this sorted first.

This is doing my head in now..!!

Does anyone have any ideas??

Help..!!!

---

### Post by hailukah on 2008-12-18
Not sure, it's been awhile since I've networked with an XP machine, but it may depend in part on which version of XP you have.  XP Home uses a different file sharing protocol that, in the past at least, was not compatible with the Samba tools for linux.  May be worth looking into.

---

### Post by Kellemora on 2008-12-18
Hi BigTel

Don't fret, we'll get you up and running!

I have 8 machines in my office all networked together and all sharing folders, drives, printers, you name it.  All the machines are Ubuntu except for two Doze machines.  One is XP-HOME the other is XP-Pro.  My wife's XP machine at home is on the LAN too and we run backups back and forth for off-site backups.

Since you said your XP machine can see the Ubuntu Shares, you obviously have the network and Samba up and running.

Next step:
What is the name of your WORKGROUP!
Ubuntu sets the default name to WORKGROUP.
Most Windows machines set the default to MSHOME.
It's best to select your own UNIQUE name for your Workgroup, if you haven't done so already.

Next step:
Go into your Terminal if you prefer CLI or to Synaptic Package Manager and install 
smbclient and smbtree, if you see smbfs is checked, uncheck it, it causes problems.

The code for CLI is:
```
sudo apt-get install smbclient
```
```
sudo apt-get install smbtree
```

Next step:
Let's check your smb.conf file to make sure your Workgroup name is in there.
```
sudo gedit /etc/samba/smb.conf
```
In the Global section near the top, look for the words WORKGROUP = WORKGROUP, you will want to change it to read either WORKGROUP = MSHOME, or to your unique Workgroup name that you chose.

IF you changed the smb.conf file then:
```
sudo /etc/init.d/samba restart
```

Now, type 
```
smbtree
```
and see if all of your shares show up.
If so, you are up and running.

If your shares do not appear under Places/Network, this is an old known unresolved bug.
While in Places/Network go up to the top to Go/Location and in the box type smb://your IP number to the XP computer.  This will bring up your shares.

I'll check back later to see if you still have problems!

TTUL
Gary

---

### Post by albinootje on 2008-12-18
> **Kellemora said:**
> 
Go into your Terminal if you prefer CLI or to Synaptic Package Manager and install 
smbclient and smbtree, if you see smbfs is checked, uncheck it, it causes problems.

For you smbfs has been causing problems ? Can you tell some more about this ?
> 
The code for CLI is:
```
sudo apt-get install smbclient
```
```
sudo apt-get install smbtree
```

Interesting, i had never heard of smbtree before, but..

dpkg -S $(which smbtree)
smbclient: /usr/bin/smbtree

It's included in the package smbclient.

---

### Post by bigtel on 2008-12-19
Hi - Thanks for your help so far - I have had a few problems with the code you gave me..

> sudo apt-get install smbtree

..gave me this from my terminal..

> terry@terry-laptop:~$ sudo apt-get install smbtree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package smbtree


I am not sure if this means I have type it incorrectly or my laptop just can not find it..?


Here is the output from my smb.conf file...



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
   wins support = yes

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

# Cap the size of the individual log files (in KiB).
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
   security = user

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

# This option controls how nsuccessful authentication attempts are mapped 
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
   printing = cups
   printcap name = cups

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
   comment = Home Directories
   browseable = yes
   path = /home/terry




# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

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

[Guest Share]

        comment = Guest share
        path = /home/terry
        browseable = yes
        read only = yes
        guest ok = yes

```


My WORKGROUP name is MSHOME which is the same on both Ubuntu laptop and on the XP machine.

I have managed to copy some files from the laptop (Ubuntu) using the XP machine as I can see the share files on the laptop through the XP machine. Sorry if this is confusing.

If I browse using 'places' then 'network' I can see the workgroup MSHOME and I can also see the XP machines PC name. But when I click on it there is nothing inside and it says 0 items

I tried typing in SMBtree into terminal ad I got the following output...

```
MSHOME
	\\TJBLEANPC      		TJB Lean Office PC 1
cli_start_connection: failed to connect to TJBLEANPC<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\TERRY-LAPTOP   		terry-laptop server (Samba, Ubuntu)
		\\TERRY-LAPTOP\terry1         	
		\\TERRY-LAPTOP\PDF            	PDF
		\\TERRY-LAPTOP\S600           	Cannon upstaires
		\\TERRY-LAPTOP\Stylus         	Stylus
		\\TERRY-LAPTOP\IPC$           	IPC Service (terry-laptop server (Samba, Ubuntu))
		\\TERRY-LAPTOP\Guest Share    	Guest share
		\\TERRY-LAPTOP\print$         	Printer Drivers

```




I hope all this info helps you to see what my problem is...!

---

### Post by philinux on 2008-12-19
smbtree is already available from smbclient there is no separate app in Intrepid.

Just try 

man smbtree

from a terminal.

---

### Post by Iowan on 2008-12-19
I'm also running 7.10 - I have better luck using "Connect to Server" than "Network".

---

### Post by bigtel on 2008-12-19
> I'm also running 7.10 - I have better luck using "Connect to Server" than "Network". 

What exactly do you type for this to work??

---

### Post by Kellemora on 2008-12-19
Hi albinootje

> For you smbfs has been causing problems ? Can you tell some more about this ?

I have 8 machines in my office here, Ubuntu is installed on 6 of them as the only OS.
On ALL SIX of those machines, if smbfs is installed, then when you type smbtree about 1/2 of the shares do not show up.
Uninstall smbfs and they all show up again.
Install smbfs and they disappear again.
Uninstall smbfs and they appear again.

So I make sure smbfs is UNINSTALLED!

Need I say more?????

I'm running the stable Hardy 8.04 LTS version.

There is a bug in Places/Network also that has gone unresolved for like 2 years now.  I think they finally fixed it though.  Although there have been a few posts lately with the same problems.

If you can PING, if you can smbtree, if you can Go/Location using IP and if you can Go/Location using sharename and it always works, but the shares don't show up in Places/Network all the time, only sometimes, there is nothing the user can do to correct an intermittent display in Places/Network.
Although rebooting three times in quick succession sometimes cures the problem until the next update.

TTUL
Gary

---

### Post by Kellemora on 2008-12-19
Hi BigTel

To use Connect to Server you would type
```
Samba, Ubuntu
```
as the Server Name.  That's what appeared in your smbtree listing as the server name.

The other names to use in the boxes are also listed in your smbtree listing.  It didn't show the share due to an error.  
Someone else will have to help with that error as I've never seen it before in XP-Home or XP-Pro and we won't have Vista anything this side of the property line, hi hi...........

As a test, I would make a NEW shared folder, put something in it small and make sure you give it all privileges including guest read and write.

I did notice a guest entry at the end of your smb.conf file which I don't think is necessary?

Good Luck!

TTUL
Gary

---

### Post by albinootje on 2008-12-20
> **Kellemora said:**
> 
I have 8 machines in my office here, Ubuntu is installed on 6 of them as the only OS.
On ALL SIX of those machines, if smbfs is installed, then when you type smbtree about 1/2 of the shares do not show up.
Uninstall smbfs and they all show up again.
Install smbfs and they disappear again.
Uninstall smbfs and they appear again.

So I make sure smbfs is UNINSTALLED!

Need I say more?????

I never used smbtree, and never had a use or need for it.

However i have smbfs + autofs in use successfully on a dozen Ubuntu-machines at work since *years*.

Your suggestion to uninstall smbfs and never use it, is not the way forward.
You should however file a bug-report for this smbfs and smbtree conflict. [http://launchpad.net/](http://launchpad.net/)

---

### Post by Kellemora on 2008-12-20
Hi albi

From what I understand, the reason it don't work is that it has not been maintained in the past few years.  And was also dropped from the Kernel as well!  It's now a separate install for those who still need it for something.

They have moved on to CIFS now, if you need it!
It's supposed to be better?

TTUL
Gary

---

### Post by bigtel on 2008-12-20
Hi there. What do you mean by this..?

> They have moved on to CIFS now, if you need it!
It's supposed to be better?

Is this a file / share system I can install?

---

### Post by Iowan on 2008-12-20
> **bigtel said:**
> What exactly do you type for this to work??Under Places (on top panel), I have options to connect to:
Home Folder
Desktop
...
Network
Connect to Server...
Search for Files...
Recent Documents

I have better luck when clicking on Connect to Server than when I click on Network.

Re: smbfs
Apparently the smbfs package must sometimes be installed (I thought it came pre-loaded) when sharing files from a box.  It actually configures CIFS.  More CIFS info [here]("http://ubuntuforums.org/showthread.php?t=288534").

---

