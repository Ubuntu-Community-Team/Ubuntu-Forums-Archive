---
title: "Network between 2 computers"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by Motorhead Kaze on 2008-03-25
Howdy, I would like to set up a network between my desktop and laptop.  I tried following a thread from a year ago, when people were using Edgy. What is the current way to set up a network (Gutsy)?

The reason I could not use the older tutorial is that the person who wrote it said I needed to use the IP address for each computer.  The IP for each computer is my DNS server number right?  No?  If yes, then both my laptop and desktop have the same address "192.168...."  so I can't add separate numbers. I am running both computers through the router that came with my new fiber optic hookup.  (Sorry, I don't know what to call it in English, here it is called "Light fiber")  Both computers are running gutsy, and the laptop is an HP, Compaq nc6000 if that tells you anything.

Anyway, I could use a good tutorial.  I tried going through the Network settings but saw nothing that said, "Hey! Hook up to that computer over there! Just push this button."

Thanks in advance.  Let me know if I need to give any more info.

---

### Post by secondstage on 2008-03-25
Before you go and do this, please let someone else check me as I am just as new to this as you are. I don't under stand if a lan via fiber optics is the same as a lan via ethernet cable(cat5)

*****You will need two fiber optics or 2 ethernet cables to make this work*****
> The IP for each computer is my DNS server number right?
From what I understand, no.
> ...new fiber optic hookup. (Sorry, I don't know what to call it in English, here it is called "Light fiber")
I call it fiber optics, but that's just me.

My solution was to have to router be a hub for both computers and use the router to give each computer a static ip address. Look around the settings (if you don't know how to get into the settings please refer to the manual) and you should find it; make sure both PCs are connected prior to looking. After that, install 2 packages by going to terminal(Applications>Accessories>Terminal) and typing
```
sudo apt-get install openssh-client openssh-server
```
(that will install binaries to use each computer as a "server" and have a connection)
Finally go to connect to the other computer (Places>Connect to Server...). You will get a pop-up. In the drop down box, click on SSH. Where it says "Server:" fill it in with the static ip address from before and where it says "User Name:" type the user name of the other computer (the name you log-in with).Click "Connect". Wait for it to establish a connection, and an icon on your desktop ought to to appear, if not you either did something wrong or it is in "Places" on the bar at the top of the screen.

I hope this helps.

ps. if you can't get to the internet after an established ssh connection, check [http://ubuntuforums.org/showthread.php?t=727384](http://ubuntuforums.org/showthread.php?t=727384)

---

### Post by Motorhead Kaze on 2008-03-25
Hello again!

I was about to follow this when a friend happened to Skype me and said "Oh, just go to Admin/shared folders"  I didn't have a network (obviously) yet but Ubuntu (so smart) just had SMB and NFS ticked off and ready to download the software, all I had to do was say yes.  Ubuntu loaded both these within a couple minutes.  I did the same thing on the laptop, and then selected the folders to share.  It took a minute or so for the files to appear.

Interestingly enough, I assumed that NFS or the Unix connection was the right one, but the folders that were shared this way did not show up.  So under the properties for the folders I wanted to share, and under "Share through" I switched to SMB and then in a minute my folders showed on the network folder of the other computer.  Oh how cool.  (My first network)

But thank you for posting your help, I still appreciate the fact that you replied within a short time!

Peace.

---

### Post by Eiríkr on 2008-03-25
NFS has no built-in "hi I'm here" broadcasting capability, so no, NFS shares wouldn't automatically appear anywhere.  They have to be manually mounted via the command line (or by configuring the [font=courier]/etc/fstab[/font] file) before they can be used, but then they look and act just like local folders.  

Samba (SMB), meanwhile, replicates a lot of Windows behaviours, which makes sense since Samba is designed for sharing with Windows computers.  One of these behaviours is broadcasting share availability over the network, which is how the shares just seem to show up in your browser.  

&#12376;&#12419;&#12289;

Eiríkr

---

### Post by Nidding on 2008-03-25
> **Motorhead Kaze said:**
> Hello again!

I was about to follow this when a friend happened to Skype me and said "Oh, just go to Admin/shared folders"  I didn't have a network (obviously) yet but Ubuntu (so smart) just had SMB and NFS ticked off and ready to download the software, all I had to do was say yes.  Ubuntu loaded both these within a couple minutes.  I did the same thing on the laptop, and then selected the folders to share.  It took a minute or so for the files to appear.

Interestingly enough, I assumed that NFS or the Unix connection was the right one, but the folders that were shared this way did not show up.  So under the properties for the folders I wanted to share, and under "Share through" I switched to SMB and then in a minute my folders showed on the network folder of the other computer.  Oh how cool.  (My first network)

But thank you for posting your help, I still appreciate the fact that you replied within a short time!

Peace.

Hey.
I tried doing the same, but no folders show up in my network folder (apart from a folder named "Windows Network" with nothing in it). Do I need to mount the shared folders or something like that?

---

### Post by SpaceTeddy on 2008-03-26
quick question between the lines just to make sure that i understand it... 
both computers are in the ip-range and can ping each other (trivial network reachability test...)?

as for fibre Optic cables, they work just the same as ethernet does - the only differences are that the use light (duh - what a joke) and that most older hardware does NOT support port speed autosensing - so make sure both ends are set to the same speed.

---

### Post by Nidding on 2008-03-26
> **SpaceTeddy said:**
> quick question between the lines just to make sure that i understand it... 
both computers are in the ip-range and can ping each other (trivial network reachability test...)?
.

Yep. They can both ping eath other. 

ps. I'm going through ethernet cables and a router, if that is of any importance?

---

### Post by Eiríkr on 2008-03-26
It's much more likely a problem in your Samba configuration than with your hardware.  I suspect it's the [font=courier]wins support[/font] option.  Please post the contents of your [font=courier]/etc/samba/smb.conf[/font] file and we can go from there.  

Cheers,

Eiríkr

---

### Post by Nidding on 2008-03-26
This one? 

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
	workgroup = home

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;	wins support = no

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
;	syslog only = no

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
	passdb backend = tdbsam

	obey pam restrictions = yes

;	guest account = nobody
	invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;	unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;	pam password change = no

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
;	logon path = \\%n\%u\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;	logon home = \\%n\%u

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
;	load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;	printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
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
;	socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;	domain master = auto
	username map = /etc/samba/smbusers
;	guest ok = no

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
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

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



[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
;	public = no
;	writable = no
	create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
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




[niddinglaptop]
	path = /home/nidding
;	available = yes
;	browseable = yes
	writeable = yes
	guest ok = yes
```

---

### Post by Eiríkr on 2008-03-26
Yep, that's the one.  Looking this over, most things look good and proper.  I would recommend you try uncommenting the [font=courier]wins support[/font] line and changing the value to "yes".  If you're not sharing a printer via your laptop, you can (and maybe should) delete the printer-related share definitions.  

Also, is there any specific reason you have [font=courier]guest ok = yes[/font] set in your laptop share definition?  That might be interfering here; guest logins wind up using the guest account, which, unless specified otherwise in the [font=courier][global][/font] section using the [font=courier]guest account = XXXXX[/font] option, defaults to the "nobody" user, which is very limited and a common culprit in Samba share permission problems.  To wit, if you don't need to allow unknown users to access your share, either comment out or delete this line.  

Try those changes, then restart Samba:
```
sudo /etc/init.d/samba restart
```
... and let us know how it goes.

Cheers,

Eiríkr

---

### Post by Nidding on 2008-03-26
Hey. Thanks for the help. 
The advise hasn't helped though. I can still see the "Windows Network" folder, when opening my network but that's it. Any new ideas? I'd really appreciate it.

---

### Post by Eiríkr on 2008-03-26
Other things to try include rebooting (sometimes settings persist in odd ways that I haven't been able to figure out), and checking to see if you have any firewall running.  Here's a sampling from my conf file for reference, just in case there's a difference here that I haven't thought to point out.
```
[global]
   workgroup = homelan
   server string = %h server

   wins support = yes
   
   interfaces = lo eth0
   bind interfaces only = true

   panic action = /usr/share/samba/panic-action %d

   security = user
   username map = /etc/samba/user.map

   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes

   invalid users = root

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

   socket options = TCP_NODELAY

   unix extensions = yes
   unix charset = UTF8
   
   preferred master = yes
   domain master = yes
   local master = yes

   syslog = 0
   debug level = 0
   log file = /var/log/samba/log.%m
   max log size = 1000

[shared]
   path = /data/shared
   valid users = @users
   comment = Shared directory with forced group.
```

HTH,

Eiríkr

---

### Post by A$h X on 2008-03-26
Have you run the home network setup on your XP machine? After I ran it and rebooted, my XP machines showed up in my network window. HTH.

---

### Post by Nidding on 2008-03-27
I dualboot my desktop, so I went to xp and created a windows network. This seems to allow access  to the shared folders on the desktop from the laptop, but not the opposite. And it only works when I'm in XP, which I'm not planning on being ;)
It seems to me, that the network is working ok, but it's the sharing that's messed up, could I be right on this?

---

### Post by Eiríkr on 2008-03-27
If you set up sharing on the desktop, then yes, that allows sharing access **to** the desktop.  If you want sharing access to the laptop, then you need to set up sharing on the laptop.  If the laptop is XP, you need to do something similar to whatever you did on the desktop.  If the laptop is Linux, you need to set up a Samba server.  

Cheers,

Eiríkr

---

### Post by Nidding on 2008-03-27
They're both Ubuntu machines. I tried both the SMB and NFS options, but can't get any of them to show up on the other machine.
I found another thread where you (Eiríkr), advised someone to get the SSH package and share via that. This works just perfect for me, so I'm good for now. Thanks for the help.

[Eiríkr's advise](http://ubuntuforums.org/showthread.php?t=730290&highlight=nfs+server)

---

### Post by Eiríkr on 2008-03-27
No trouble, glad it came in handy.  :)

Note that Samba is built for Windows sharing, and thus replicates a lot of Windows behaviours, such as broadcasting the availability of the shares.  NFS is Unixy all the way, and has no built-in broadcasting.  You can add broadcasting via the Avahi zeroconf daemon, as described in [post=4387032]this post[/post] -- but note that the Nautilus browser is rather limited, and has no ability to browse NFS shares unless they've been mounted onto the local filesystem, and probably because of this, it doesn't display Avahi-advertised NFS shares.  Konqueror, meanwhile, can browse unmounted NFS shares.  You *can* however add SFTP shares to your Avahi setup, as described in [post=775340]this post[/post], which *will* show up in Nautilus.  

HTH,

Eiríkr

---

