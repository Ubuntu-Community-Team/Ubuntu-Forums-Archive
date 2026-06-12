---
title: "Ubuntu can see windows - but not the other way arround"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by longtom on 2009-02-05
Hi,

2 questions:

1.  I can see everybody and everything shared on my windows network from my Ubuntu machine.  When I try to share a folder in Ubuntu 8.10 however, it goes through all the motions it is supposed to go through according to [this](https://help.ubuntu.com/community/SettingUpSamba) page, but once I log in again the folder is not shared and samba files have not been downloaded (evidently...).   Any ideas?

2.  I have shared printers on some of the Windows machines but do not be able to access them, also I can see the PC and all shared folders.  Any ideas for that?

Thanks for your patience

longtom

---

### Post by yeleek on 2009-02-05
1) If you mean you can't access the Ubuntu samba share from windows, try disabling your firewall and then see if you can see the folders? Rules out if its a config issue or not then.

---

### Post by longtom on 2009-02-05
> **yeleek said:**
> 1) If you mean you can't access the Ubuntu samba share from windows, try disabling your firewall and then see if you can see the folders? Rules out if its a config issue or not then.

Nope - no firewall issue.  It also appears that my ability to edit my desktop was shot in the process and who nows what else....quite a mess tbh.

Looks like a reinstall is on the cards....:(

---

### Post by Voland on 2009-02-05
1) Could you post your smb.conf file?
2) Check permissions on windows shared folders and printers. Check that ubuntu username is in list  of allowed users.

---

### Post by lswest on 2009-02-05
A note on the printers:

For some reason Nautilus will not display connected printers, but if you add a printer in the printer manager and choose "Windows Share" or words to that affect, and give in the right information for it, it will print to the correct printer.

At least, that is my experience with samba-shared printers and Ubuntu.

---

### Post by longtom on 2009-02-05
> **Voland said:**
> 1) Could you post your smb.conf file?
2) Check permissions on windows shared folders and printers. Check that ubuntu username is in list  of allowed users.

Can't post that file right now...am in Windows again to download Ubuntu 8.04...maybe that'll help.

Permissions are universal - everybody can have fun, no need to specify anything.

Thanks for your ideas.

longtom

---

### Post by longtom on 2009-02-05
> **lswest said:**
> A note on the printers:

For some reason Nautilus will not display connected printers, but if you add a printer in the printer manager and choose "Windows Share" or words to that affect, and give in the right information for it, it will print to the correct printer.

At least, that is my experience with samba-shared printers and Ubuntu.

I'll keep that in mind once I get on again.

Thank you.

longtom

---

### Post by longtom on 2009-02-05
> **Voland said:**
> 1) Could you post your smb.conf file?
2) Check permissions on windows shared folders and printers. Check that ubuntu username is in list  of allowed users.

Alright - I'm back.  Which one should I post?

got one in:

/usr/share/samba
/usr/share/doc/nautilus-share/examples
/etc/samba

pick'n choose....

longtom

---

### Post by Voland on 2009-02-05
In /etc/samba

---

### Post by longtom on 2009-02-05
> **Voland said:**
> In /etc/samba

I'm not sure this is what you want...but here you are:

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
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

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
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

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


longtom

---

### Post by Voland on 2009-02-05
In Share Definitions section there are only printers' shares, not folders.
If you want to share folder under Ubuntu, you should add its definition into this section or use shares-admin application.

---

### Post by longtom on 2009-02-05
> **Voland said:**
> In Share Definitions section there are only printers' shares, not folders.
If you want to share folder under Ubuntu, you should add its definition into this section or use shares-admin application.

Thank you.  I'm not quite sure how to do that so.  How do I add a folder definition or use the shares-admin application?

Sorry - I am an absolute beginner....

longtom

---

### Post by Voland on 2009-02-06
Here it is my section:
> [share]
path = /home/voland/shares
available = yes
browsable = yes
public = yes
writable = yes
[aspir$]
path = /media/sda5/post-graduate
available = yes
browsable = yes
public = yes
writable = yes
Simply add it editing /etc/samba/smb.conf with command```
 gksu gedit /etc/samba/smb.conf
```

---

### Post by longtom on 2009-02-06
Thank you, Voland, for your valiant efforts to get this poor newbie going - much appreciated.

I think I have a problem with my samba in general.  When I type:

**sudo apt-get install samba smbfs**

This is what I get:

[b]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 2:3.2.3-1ubuntu3) but 2:3.2.3-1ubuntu3.4 is to be installed
  smbfs: Depends: samba-common (= 2:3.2.3-1ubuntu3) but 2:3.2.3-1ubuntu3.4 is to be installed
E: Broken packages[/b]

I reckon if get that fixed, I can start implementing your tips.

Anybody knows how to fix above error?  Any tips will be gratefully received.

longtom

---

### Post by anewguy on 2009-02-06
You could try having apt-get retrieve dependencies that might be missing:

sudo apt-get build-dep samba

sudo apt-get build-dep smbfs


Also, you may want to see this link on setting up a simple server.  You can probably skip to page 3, since you don't actually need to install the server version itself, but page 3 has stuff on setting up the samba config file so you can share a disk.  This may give you more information to go on for what you might be trying to do.  I set up my simple server following this, but as it states it is also important to match the workgroup names - by default Windows has (I think) MS-HOME or some such thing.  I just set both of mine to my own name - in my case dwe-work-grp.  Failure to match the work group names will result in Windows not seeing the shares as well.

EDIT: GUESS IT WOULD WORK BETTER IF I INCLUDED THE LINK :)  

[http://www.howtoforge.com/ubuntu-home-fileserver]("http://www.howtoforge.com/ubuntu-home-fileserver")

Dave :)

---

### Post by longtom on 2009-02-06
> **anewguy said:**
> You could try having apt-get retrieve dependencies that might be missing:

sudo apt-get build-dep samba

sudo apt-get build-dep smbfs


Dave :)

Thank you.  Did that and got:

csudo apt-get build-dep samba
[sudo] password for cango: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list

sudo apt-get build-dep smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list

What does Ubuntu want to tell me?

longtom

Edit:  Sorry, anewguy, can't see a link in your post

---

### Post by anewguy on 2009-02-06
Does it say "URI"s (like it eye) - I think it should be "URL".  Sounds like somehow the repositories (I can't resist - I saw a post the other day where someone called them supositories and it just cracked me up - whoops, an unintended pun there).

Not at my Linux box right now so I can't tell you right now what you may not have ticked in the sources.

Dave :)

---

### Post by anewguy on 2009-02-06
Sorry about this missed link - I edited that post so the link is there now (grinning red faced).

Dave :)

---

### Post by longtom on 2009-02-06
> **anewguy said:**
> Sorry about this missed link - I edited that post so the link is there now (grinning red faced).

Dave :)

The requested URL //www.howtoforge.com/ubuntu-home-fileserver was not found on this server.

URl was copied directly from the terminal - but I guess it wanted to say URL....

Thanks for your efforts

longtom

---

### Post by longtom on 2009-02-06
Well - you got me thinking now....dangerous...

Where is "sources.list" and what does it do?  And how did some URLs or URIs disappear from there?

really confused...but still hopeful

longtom

---

### Post by anewguy on 2009-02-06
Sorry about that - I fat-fingered the URL for the link!  I fixed it and tried it to be sure it worked this time (REALLY red-faced, embarassed grin).

As far as the sources go, there is a list of places that the update/install software looks to for update, etc..  These are in the form of URL's - [http://xxxxxxxx](http://xxxxxxxx).  When you run apt-get, or synaptic package manager, they look to this file to see where to look for what are called repositories - just like the library is a repository of books, these various links are repositories, or holding places, of the software.  This file is the sources list file.  This file in Ubuntu is /etc/apt/sources.list.  So, to try help more, please post the entire output of the following back in a reply here:

sudo cat /etc/apt/sources.list

Thanks
Dave :)

---

### Post by longtom on 2009-02-07
Hi Dave,

thank you very much for all your efforts.  In the meantime I got help from hyper_ch [here](http://ubuntuforums.org/showthread.php?t=1061723) and actually got it going.

Even managed to see my network printer on a [WinXP Network](http://ubuntuforums.org/showthread.php?t=1061773).

You guys are just to good for words...Thank you very much.

lt

---

### Post by anewguy on 2009-02-07
Glad to see hyper_ch got you to speed on your sources list - that is what was causing your problems here.

dave :)

---

