---
title: "PLEASE! Can someone help them see each other?"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by Emceay on 2007-08-01
I've been using Ubuntu since Dapper and networking between my windows PC and Ubuntu has run very smoothly up until about two months ago. The connection and sharing mysteriously broke between the two. I haven't been able to pinpoint why it's broken, to my knowledge I haven't done any tweaking on either side until the disconnect happened.

I've googled the problem and searched the forum for ways to fix it, but they're all multi-step and very complex. Every time, I follow the steps and then one step fails. I'm not a Linux master, so I get stumped and move on to trying another solution.

Most recently, I just got sick of having a useless linux box (all of my media is in it!!!) and uninstalled and reinstalled samba altogether.

Now, this had the effect that briefly one of the wireless windows PCs (Fralin) could see the Ubuntu share (Darklight), but could not actually explore it. Meanwhile, the windows PC (Duelsolo) wired, and sitting right next to the Ubuntu one acts as if Ubuntu (Darklight) isn't even connected to the network - it's entirely invisible to windows (Duelsolo).

Darklight, my Ubuntu system, can see the workgroup it's supposed to be in (home) but when I try to browse it in nautilus, I get an error message saying: Could not display the contents of "Windows Network: home"

Both Windows computers, of course, can see and share with each other fine.

I am extremely frustrated with my deficient network, as I've tried to get this ironed out before, but couldn't find help. But, it's been two weeks since, so I'm trying again.

I get the feeling the answer is something very simple, as I had the computers sharing peacefully for almost a year prior to the collapse.

Can anyone help me get back on track and have access to music, and movies with sound??

I've already spent 3 hours dicking around with it unsuccessfully tonight. And I really don't want to stop using Linux altogether just because Windows won't share. Hopefully what I described will help someone out there more adept at Ubuntu than myself deduce what's wrong...

---

### Post by fredj on 2007-08-02
Post your smb.conf file.

---

### Post by Emceay on 2007-08-02
Here's my current smb.conf
> [global]
    ; General server settings
    workgroup = HOME
    netbios name = DARKLIGHT
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = yes
    writable = yes
    read only = no
    veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes



[Music]
path = /home/mark/Music
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by Emceay on 2007-08-02
Is there anything else I could post that would help reveal the problem?

---

### Post by Emceay on 2007-08-07
All of these great technical minds and no one can tell me what could be wrong with my Feisty?
Did I miss some details? :confused:

---

### Post by Alcopops on 2007-08-07
hi,

your problem seems similar to mine

[here]("http://ubuntuforums.org/showthread.php?t=519468")

I have no answers, do you have two linux boxes that can talk to each other, or is the problem just between windows and linux.

---

### Post by Emceay on 2007-08-08
Just between windows Windows and Linux. There's only one Ubuntu trying to share on the network, the Windows computers can see each other and share. The Ubuntu computer can connect to the internet, but can't see nor share with the Windows computers.

---

### Post by Emceay on 2007-08-09
I re-ran the configuration wizard on both windows computers, now they're on the default MSHOME network. When I try to view the network with Ubuntu I get:
> Sorry, couldn't display all the contents of "Windows Network: mshome"
The windows computers can't see the Ubuntu on the network either. All systems have been reset since making changes, still no luck.

---

### Post by Emceay on 2007-08-10
Okay, reinstalling samba doesn't work either.
I'm just bouncing the same ideas around, and getting nowhere.... For the past 2 months now. I really want to listen to music and watch movies again.
No one out there can tell what's wrong with my configuration?

---

### Post by Emceay on 2007-08-10
Okay, seriously, where's the love? I'm beginning to see why people say that Ubuntu isn't ready for prime time. Resolving a once working network connection should be easy as pie, but there's no one out there that knows how to fix it apparently. Networking should be easier than this. :mad:

---

### Post by citaworvk on 2007-08-13
I have a similar problem, my network was working fine but now my XP machine can't see my ubuntu machine. I made no changes or tweaks it just stopped working. 

Here's my config file

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
;   security = share

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


[Shares]
writable = yes
public = yes
guest ok = yes
guest only = yes
guest account = nobody
browsable = yes
path = /home/citaworvk/Shares
available = yes
force user = nobody
force group = nobody

---

### Post by V. Wayne on 2007-08-22
I agree, evidently Ubuntu is not ready for prime time if you can't get a simple networking issue resolved.  I'm having the same problem with my Windows XP PC accessing files on my Ubuntu 7.04 PC on a LAN.

The Ubuntu PC can access the Windows XP folders with no problem, yet when I am working from the Windows XP desktop... it will not let me access the shared files on the Ubuntu PC.

What happens is when attempting to access a shared folder from the Windows PC, a small pop-up window appears with User Name and Password fill-in blocks.  Even when I fill in the blocks with different user names and passwords, that I think will work... the same pop-up window appears which prevents access to the Ubuntu PC.  What's up with that? Where's the documentation to resolve this?  And let's not blame this on Windows.

I'm a Linux and Windows novice but it seems like Windows to Windows or Ubuntu to Windows networking is much easier to configure than Windows to Ubuntu.

If someone out there resolves this problem in "easy-to-understand" instructions please post in ALL CAPS!!

:confused:

---

### Post by A$h X on 2007-08-22
Chill out guys Ash-man is here to save the day...  :)

I had the same problem as V.Wayne and I solved it quite simply by doing the following:

Edit the smb.conf file to the following:

# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = *name of windows network*
security=share

Then goto system > administration> shared folders and add a folder that you want to be accessible to the windows network, and make sure that the "read-only" checkbox is unchecked. 

Now you should be able to read/write to that folder via windows.

---

