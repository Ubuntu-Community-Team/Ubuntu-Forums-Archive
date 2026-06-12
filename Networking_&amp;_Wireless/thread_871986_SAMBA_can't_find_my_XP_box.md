---
title: "SAMBA can't find my XP box"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by GepettoBR on 2008-07-27
I have two computers connected to a D-Link wireless router: one desktop running Windows XP SP3, connected via an ethernet cable, and one laptop dual-booting XP SP3 and Hardy (with all the latest updates) connected via a USB wireless adapter. Both can access the internet perfectly. 

Today I tried to set up a home network between them. When both are running Windows, the network functioned perfectly. Files could be shared and altered and I even managed to use the shared printer. When I rebooted my laptop to Ubuntu, things weren't so great: Places>Network displays my workgroup, but empty. I installed pyNeighborhood and it can see my XP box and its resources, but can't mount the shares. Both computers can still go online, both successfully ping each other. I couldn't locate the printer.

No error messages are displayed, except for the pyNeighborhood "Failed to Mount"with no further information. How can I get this to work?

---

### Post by GepettoBR on 2008-07-27
BUMP

I forgot to mention that my Dual Boot machine has the same hostname on both OSes. I don't know what other information is relevant, please ask and I will comply.

If this matter is too basic for here, I'd like to ask the admins/mods/1337 haxx0rz to move it to the beginners forum, please.

---

### Post by cariboo on 2008-07-27
This problem sounds more like a sharing issue with windows, check your shares to make sure Allow network users to change my files is checked, and make sure your printer it shared. One other thing to check is to make sure both computers are in the same workgroup. Windows XP defaults to MSHOME and Ubuntu defaults to WORKGROUP.

Jim

---

### Post by GepettoBR on 2008-07-27
Thanks for the reply, Jim, but it turns out my own forgetfulness was at fault and not Windows. I had disabled all the boot-up entries I didn't use on Ubuntu a few months ago, and at that time I had no use for either CUPS or SAMBA. I've enabled them both and now I can access the shares. I've also printed a test page successfully on the remote printer.

However, while my Ubuntu box can access the XP box's resources, the XP box cant connect to the Ubuntu box, even though I've configured shared folders as root. Is this maybe a permission issue like you suspected? How do I make sure and fix it?

---

### Post by dentaku65 on 2008-07-28
Can you post your smb.conf?

```
sudo cat /etc/samba/smb.conf

```

Or you can create a new directory called testsmb in your home and try to put a simple entry in you smb.conf (at the end) like this:
```
[testsmb]
path = /home/<yourname>/testsmb
available = yes
browsable = yes
public = yes
writable = no
create mask = 0777

```

Then restart samba:
```
sudo /etc/init.d/samba restart
```

Now you can try on XP machine if you are able to access testsmb share.

---

### Post by GepettoBR on 2008-07-28
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
	workgroup = casa

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

# Cap the size of the individual log files (in KiB).
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
;	socket options = tcp_nodelay

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;	domain master = auto

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
;	guest ok = no

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

```

The test directory worked, thanks! Two questions, though, before I append more lines for the folders I want to share:
1) What does "create mask = 0777" mean?
2) How do I specify which user accounts have access to each folder on the network?

---

### Post by ingeva on 2008-07-28
> **GepettoBR said:**
> 
1) What does "create mask = 0777" mean?
2) How do I specify which user accounts have access to each folder on the network?

1. ) 0777 is an octal number because the first 0 defines it as such.
7 is binary 111; you could say that 1 is true and 0 is false.
Each digit is a permission bit; tells the system if the file is readable, writable and executable

The first group is for the owner, the second for group and the last for everybody else.

Thus, mask 0740 means owner can do everything, group members can read, and nobody else has access.

2.) The easy way is to comment the [homes] section and set the masks to 0755, which is generally OK.

I'm a new Ubuntu user but I've worked with Unix-like systems before, and I've just done this with Samba so it's "fresh". :)

---

### Post by GepettoBR on 2008-07-28
Thanks! One final problem, though: The XP box can now read files on the dual-boot box regardless of which OS is booted, but when I load Ubuntu it seems to randomly show or not show the shares on the other box (while it always shows them under windows). Since it comes and goes, it shouldn't be a permission issue, so what gives?

I thought this would be easier. Oh, well, it's worth the hassle if I can get it working.

---

### Post by GepettoBR on 2008-07-29
BUMP for help

Since the last post I haven't once managed to access the windows box from Ubuntu, not even the printer is accessible.

---

### Post by linux6994 on 2008-07-29
First look at this post, it might help:

[http://ubuntuforums.org/showthread.php?t=872975](http://ubuntuforums.org/showthread.php?t=872975)

Then I have found it best to have the DNS and GW of all PCs connect to the router pointing to the router such as 192.168.1.1. On your Ubuntu under networking dns add the 192.168.1.1 for instance and remove the other external ip address. Your router will do the work to get you to those dns ip address, that is it's job. You can also run with fixed or static ip addresses that way you will always know who is who.

Good luck

---

### Post by ingeva on 2008-07-29
> **GepettoBR said:**
> Thanks! One final problem, though: The XP box can now read files on the dual-boot box regardless of which OS is booted, but when I load Ubuntu it seems to randomly show or not show the shares on the other box (while it always shows them under windows). Since it comes and goes, it shouldn't be a permission issue, so what gives?

I thought this would be easier. Oh, well, it's worth the hassle if I can get it working.

When I set up shares on the XP computer I had to allow read/write access to complete folders or partitions in order to reach the files.

Also, I had to set the EnablePlainTextPassword variable in the registry. Copy this file to a file ending with the name "samba.reg" on the XP box and double-click it:

```
Windows Registry Editor Version 5.00 
 
[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\LanmanWorkstation\Parameters] 
"EnablePlainTextPassword"=dword:00000001 
 
[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\System] 
"CompatibleRUPSecurity"=dword:00000001 
```

Maybe this helps.
Oh, in your smb.conf file, switch off password encryption. If you don't know how, post your email address in a PM to me, and I'll send you my copy of smb.conf.

---

### Post by GepettoBR on 2008-07-29
Thank you, Ingeva. I did what you said, but it didn't work. The Windows PC can still access my Ubuntu machine, but not the other way around. All my machines have static IPs.

On occasion, I can see the PC on the workgroup, but when I double-click it it's empty. Most of the time, however, the workgroup appears as empty (not even including the Ubuntu machine I'm reading it from).

---

### Post by linux6994 on 2008-07-29
Have you tried to reset your router? Are you going to Places > Network using Nautilus? I had to set my dns to my router address for Samba access outboud to work 100% of the time.

Can you consistently see the Samba shared folder on yourself?

---

### Post by GepettoBR on 2008-07-30
> **linux6994 said:**
> Have you tried to reset your router? Are you going to Places > Network using Nautilus? I had to set my dns to my router address for Samba access outboud to work 100% of the time.

Can you consistently see the Samba shared folder on yourself?

No I can't consistently see the shared folders on myself, but even when I can I can't see them on the other computer. I have managed to successfully mount the shared folders by going to Places>Connect to Server, selecting Windows Share and using its (static) IP address, but that doesn't solve the main problem, which is being unable to communicate with the printer. Both computers have their DNS set to my router (192.168.0.1) and yes, I'm trying to access Places>Network via Nautilus.
Thanks a lot for all the troubleshooting :)

p.s.: I don't know if this is relevant, but Nautilus is reeeally slow when I use it to view the network, taking anywhere from a few seconds to over half a minute before the items appear (Windows Network, the Workgroup and the workgroup computers, when they appear)

---

### Post by jkhh07 on 2008-07-30
Hey **GepettoBR** I'm not sure whats the best this, the best that, for samba but After editing the smb.conf file for a while... and permissions and folders not being there I paused and looked for a super simple step by step.

You might try this link. Its cut and then you really don't have to mess with the smb.conf file too much... Just my own personal opinion but you might check it out.

[http://linuxplanet.com/linuxplanet/tutorials/6495/1/](http://linuxplanet.com/linuxplanet/tutorials/6495/1/)

---

### Post by GepettoBR on 2008-07-31
Thanks, but I had done all that before I even posted here.

The problem persists, I can only access the shares by using the computer's IP address on Connect to Server and the printer still doesn't respond.

Edit: I tried opening the "network:///" location in Dolphin instead of Nautilus, and got something interesting. The regular Dolphin window just hangs on "Loading directory", the root Dolphin returns "timeout on server" after a while.

---

### Post by GepettoBR on 2008-08-02
BUMP

Its really bugging me that I can't use the printer...

---

