---
title: "ubuntu/windows network connection suddenly broken"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by Emceay on 2007-06-23
I had a working samba file share from a Feisty system to a WinXP system. It worked for weeks without incident up until recently. I haven't changed any of my windows network or router settings. The only thing I've tweaked is samba's settings to fix it, but to no avail. I've tried to set the password again, restart samba, and it's still not connecting. Both the Ubuntu and Windows systems can see themselves on the same domain, but not each other. Does anyone know what steps I need to take to get them working together again? I'm out of ideas.

---

### Post by scrooge_74 on 2007-06-23
You should start by posting your smb.conf file

---

### Post by Emceay on 2007-06-23
> #
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
   workgroup = HOME
   netbios name = DARKLIGHT
# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = yes

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
;   browseable = yes

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = yes

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
;   writable = yes
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


[movies]
path = /media/movies
available = yes
browsable = yes
public = yes
writable = yes

[Music]
path = /home/mark/Music
available = yes
browsable = yes
public = yes
writable = yes
comment = My music Anything out of place?

---

### Post by willough on 2007-06-23
I had a similar situation and I'm trying to figure out what happened too.  A single share that was working is now not working though another is. I'm going through some things I did in the past few days to diagnose the issue.  In Synaptic I did a bunch of recommended updates.   I think there were 44 of them that accumulated over the past couple of weeks.  I also have some kind of problem when rebooting but I'm not sure what it is either.  During reboot I get some message that something failed after 25 attempts and then it takes a few minutes to rebuild, then back into the desktop interface.  By the way, I use 7.04 server and GUI.  If you figure out anything that may be related post back.

---

### Post by scrooge_74 on 2007-06-24
I think I read somewhere about encrypted passowords been a problem with XP, I think it said something about XP needs it to be clear text.

Another idea would be to check on this[ thread]("http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138")

---

### Post by Emceay on 2007-07-09
Okay, it's been about two weeks and my Ubuntu computer is still virtually worthless since I can't share anything with it. Basically, I'm losing my linux faith now.

I don't have firestarter installed, the windows firewall is turned off. Yet, when I try to search the network on the Ubuntu side, it says it "could not display all of the contents of: home". If I try looking at the network on the windows side, it can only see itself and other windows comptuers.

Before this, both windows and ubuntu could share files, no sweat.

I really have no clue what could have caused this or how to fix it, has anyone else experienced this, or have any steps on fixing it? It's an extreme pain to have all of my music and movies on a computer without speakers.

The ubuntu system has no problem accessing the internet, only with sharing. Please help.

---

### Post by Emceay on 2007-07-09
This has gone to the point where I'm considering reinstalling feisty to fix it because there seems to be no other methods available. I've reinstalled samba several times, changed settings regarding dchp and wins, but nothing is of any help. The answer must be something simple because it has worked so smoothly since april until about 2 weeks ago.

---

### Post by willough on 2007-07-09
Do you have anything other than movies and Music folders being shared, such as printers or other devices? Can you ping any of the Windows computers from the Ubuntu box, either by IP or name?  Try making yourself a valid user of the shared folders.  If this doesn't work can you post the permissions that you have set for shared folders?

---

### Post by Emceay on 2007-07-10
I can ping the windows computer I'm trying to connect to by IP.

I'm not sure what you mean by "Try making yourself a valid user of the shared folders." so far I've made a user that matches my ubuntu login and one that matches the windows login - but, the way things are now, I don't even get prompted for a password. Ubuntu can't see windows computers and vice versa

"If this doesn't work can you post the permissions that you have set for shared folders?"
Gladly, but can you tell me where to find it?:confused:

---

### Post by Emceay on 2007-07-12
*bump* I want to love my linux again!
> 'net usershare' returned error 255: net usershare: usershares are currently disabled
Sounds like a clue.

---

### Post by willough on 2007-07-12
Check your private messages.  I sent one a couple of days ago.

---

### Post by dannyboy79 on 2007-07-12
> **scrooge_74 said:**
> I think I read somewhere about encrypted passowords been a problem with XP, I think it said something about XP needs it to be clear text.

Another idea would be to check on this[ thread]("http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138")

just to clarify this for people, windows 98 is an OS that can't use Encrypted passwords, you DO want to use encrypted password with NT based OS's, which WinXP is.

forgot to try to help if you still need it.

Please show me the output of the following commands:

smbtree

findsmb

If you can ping Windows by IP from Ubuntu and vis-versa, than that's the first step. Next we need to see if samba is running?

ps aux | grep *mbd

This should return both nmbd and smbd. and you're sure that the workgroup didn't change in Winbloz or Ubuntu? Are you using DNS internally or are you using the Hosts file or neither and you just go thru Places, say connect to server, and enter all the info manually? Are there any iptable rules?

sudo iptables -L

You're sure that the firewall didn't change on Winbloz? Let me know and I can help.

---

### Post by willough on 2007-07-12
Emceay, if you have made changes to your smb.conf since you previously posted it, which I imagine you did, can you repost it?  Preferably with comments stripped out, if possible.  Thanks.

---

### Post by satx on 2007-07-15
I am having same problems. Tried Bridging/NAT/ etc. for the network with different results- have dual booot WIN XP Feisty, with WIN XP vmshare WIN XP. Also have another WINXP box on the network. Other WIN XP box can see the vmshare WIN XP AND the Ubuntu box- communicates fine. Ubuntu box can see the WINXP vm box, but no commo; CM XP can see Ubuntu, but no commo. I feel your pain!

---

