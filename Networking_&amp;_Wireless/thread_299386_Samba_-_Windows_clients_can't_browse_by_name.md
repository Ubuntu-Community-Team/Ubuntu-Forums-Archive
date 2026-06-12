---
title: "Samba - Windows clients can't browse by name"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by HeWhoWalks on 2006-11-14
I have a bit of an odd problem.  I have a mostly-Windows network, with my Ubuntu Edgy box acting as a fileserver (among other things).  One day (I think after a round of Ubuntu's automatic updates), my Windows boxes suddenly couldn't access my Ubuntu server.  I hammered at everything I could find, and I've got it cobbled together now, but it's not quite ideal.  Here's where I currently stand:

Windows boxes can see my linux box when they browse for shares, but when they double-click the computer in the Explorer, they get an "Unable to connect" message.  It's not the usual "you don't have permission" message I'm used to having to fix with each new distro, though.  It's "can't find server" -- even though the machine shows up in the list.  It's not cached information, either -- if I update anything about the machine, the new info shows on the Windows boxes.  And if I enter the IP address, the shares come up and read fine.  It's just that somehow the name doesn't resolve (even though it shows up in the explorer).

Now, I've got a temporary fix -- I've added the ubuntu boxes IP address to all the Windows machines' hosts files... but it's bugging the hell out of me that I have to do that, cause it should work.  And before the updates (and the huge list of stuff I did to fix that, and allow my ubuntu box to browse the windows networks by name) it was working fine.

Anyone have any thoughts?  Here's my smb.conf:

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
	log file = /var/log/samba/log.%m
	printer = SCX-4200
	load printers = yes
	name resolve order = lmhosts host wins bcast
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	socket options = TCP_NODELAY
	username map = /etc/samba/smbusers
	encrypt passwords = true
	public = yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	wins support = true
	dns proxy = no
	printing = cups
	server string = Rebellion
	invalid users = root
	path = /tmp
	workgroup = REALM
	os level = 20
	syslog = 0
	security = share
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000

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

# Put a capping on the size of the log files (in Kb).

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
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


;   guest account = nobody

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

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

[printers]
	printer = 
	comment = All Printers
	printable = yes
	writeable = yes
	create mode = 0700
	use client driver = yes

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


[Media]
	browsable = yes
	path = /media/chunk/Media
	available = yes
	public = yes
	writable = no


```

---

### Post by FrodoB on 2006-11-14
This is probably all about: Browsing/Identification

wins support = yes

# If you have a wins server put its address in the following line. If you don't then don't uncomment it.

wins server = XXX.XXX.XXX.XXX


The restart samba:

$ sudo /etc/init.d/samba restart

Then in a few minutes it may work.

I don't have Samba installed so this is all from memory, best of luck.

---

### Post by HeWhoWalks on 2006-11-14
Not sure what you're getting at here, whether I'm supposed to have WINS enabled or not... regardless, I get the same issue both ways.  Windows boxes can't browse to the Ubuntu box by name.

---

### Post by FrodoB on 2006-11-14
If you have one put in its IP address, it you don't then you can't.

---

### Post by FrodoB on 2006-11-14
Add these two lines and then restart Samba and it should start to work:

wins support = yes
domain master = yes

---

### Post by dbott67 on 2006-11-14
A few things to verify:

1. Make sure you have samba, smbfs and smbclient installed

Run the command smbtree and post the output here:
```
dbott@thedrake:~$ smbtree
Password:
MSHOME
        \\THEDRAKE                      thedrake server (Samba, Ubuntu)
                \\THEDRAKE\print$               Printer Drivers
                \\THEDRAKE\dbott-P4
                \\THEDRAKE\IPC$                 IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\ADMIN$               IPC Service (thedrake server (Samba, Ubuntu))
        \\DAPPER                        dapper server (Samba, Ubuntu)
                \\DAPPER\print$                 Printer Drivers
                \\DAPPER\ndis
                \\DAPPER\IPC$                   IPC Service (dapper server (Samba, Ubuntu))
                \\DAPPER\ADMIN$                 IPC Service (dapper server (Samba, Ubuntu))

```

Also, some issues arise because of the way SMB shares "announce" themselves to the network.  Generally, connecting via IP address works properly, but browsing by 'computer name' can occasionally fail.  Windows uses WINS service to allow users to browse by computer name (also known in Windows-speak as Netbios name).  WINS binds the computer name to the IP address.  For the most part, this has been superceded by DNS, which binds the fully-qualified domain name to the IP address. The problem is that DNS resolution requires that:

a) You're running a DNS server
b) Each client is registered in the DNS server

The problem here is that most people don't run their own DNS server and if you have any Windows computers on the network (or Samba shares), you really should have a WINS server or 'winbind' installed.

There is a package in the repositories called 'winbind' that will allow you to browse by computer name.

This info is provided by 'featherking' from [this thread]("http://www.ubuntuforums.org/showthread.php?t=288022"): 

```
sudo gedit /etc/nsswitch.conf
```

find this line (it may not be exactly that)

```
hosts:          files dns mdns
```

and add wins, so now it looks like

```
hosts:          files dns mdns wins
```

then install winbind
```

sudo apt-get install winbind
```

Now trying connecting to "Places->Network Servers".

-Dave

---

### Post by HeWhoWalks on 2006-11-15
Thank you all for your replies.  I want to make something clear:  The Ubuntu box can browse fine.  It's the Windows boxes that have a problem seeing the Ubuntu box.

If it's important, here's my smbtree output:

```

REALM
        \\WEEONE         
                \\WEEONE\C$                     Default share
                \\WEEONE\ADMIN$                 Remote Admin
                \\WEEONE\My Videos      
                \\WEEONE\My Music       
                \\WEEONE\IPC$                   Remote IPC
                \\WEEONE\My Documents   
                \\WEEONE\FMA 1-26 (D)   
        \\REBELLION                     Rebellion
                \\REBELLION\SCX-4200            SCX-4200
                \\REBELLION\ADMIN$              IPC Service (Rebellion)
                \\REBELLION\IPC$                IPC Service (Rebellion)
                \\REBELLION\Media          
                \\REBELLION\print$              Printer Drivers
        \\MUNCHLET       
                \\MUNCHLET\C$                   Default share
                \\MUNCHLET\ADMIN$               Remote Admin
                \\MUNCHLET\My Videos      
                \\MUNCHLET\dvd            
                \\MUNCHLET\Share          
                \\MUNCHLET\IPC$                 Remote IPC
        \\ENTERTAINMENT  


```

...and nsswitch.conf is:

```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

# hosts:          files dns
hosts:          files dns wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

---

### Post by dmizer on 2006-11-16
add the option:
```
netbios name = Rebellion
```
to your smb.conf file under [global]

---

### Post by HeWhoWalks on 2006-11-16
Okay, I've added:

```

netbios name = REBELLION

```

...to smb.conf.

Restarted Samba, flushed DNS cache on one of the Windows boxes.  Here's what I get from the Windows box:

```

C:\Somedir>net view
Server Name            Remark

-------------------------------------------------------------------------------
\\ENTERTAINMENT
\\MUNCHLET
\\REBELLION            Rebellion
\\WEEONE
The command completed successfully.

```
Which shows the Ubuntu server (Rebellion).  I can see shares on the other Windows boxes:
```

C:\Somedir>NET VIEW \\MUNCHLET
Shared resources at \\MUNCHLET



Share name  Type  Used as  Comment

-------------------------------------------------------------------------------
dvd         Disk
My Videos   Disk
Share       Disk
The command completed successfully.

```

But when I try to view shares on the Ubuntu box, I get this:
```

C:\Somedir>NET VIEW \\REBELLION
System error 53 has occurred.

The network path was not found.

```

I'm pretty puzzled.

...

Okay, just had another odd development.  I temporarily turned off Firestarter, not expecting it to make a difference (I had Samba listed to allow from 192.168.0.1/16).  Suddenly I can browse the Ubuntu shares from Windows.  Re-enabling Firestarter blocks browsing by name (but not IP) from the Windows boxes after a few minutes.

I'm using very simple Firestarter configuration.  Have the following services set:
uTorrent / 19935 / everyone
Samba (SMB) / 137-139 445 / 192.168.0.1/16

And made one change earlier to /etc/firestarter/inbound/setup to allow replies from WINS broadcasts.  I added:

```

$IPT -A INBOUND -s $NET -p udp -m state --state NEW -j ACCEPT

```

My thought is that something about Firestarter's config changed when I did a regular package update a while ago.  Anyone have any ideas?

---

### Post by dmizer on 2006-11-16
your samba filter in firestarter should read:
> 192.168.0.1/24
unless you are running on the 255.255.0.0 subnet and want 65000 some odd hosts.

in other words, the /16 does not mean you want to allow 192.168.0.1 through 192.168.0.16

---

### Post by HeWhoWalks on 2006-11-16
Yes, I am intending to allow 192.168.*.* access.  I sometimes have VPN connections that require this.

Thanks for your comment, though. :D

---

### Post by dmizer on 2006-11-16
it's a mistake i see often enough that i thought it should be mentioned.

well, at this point i think it's fairly apparent that the problem is related to your firewall configuration.  and unfortunately, this is beyond my ability to assist you.

---

### Post by HeWhoWalks on 2006-11-17
Yeah, it would seem to be.  I'm just not sure what to think at this point.  I guess I'll try ripping / reinstalling Firestarter, just in case some of the settings there are pooched.  Will comment again once I've tried that...

---

### Post by HeWhoWalks on 2006-11-17
Okay, I think I've finally got it.  After much, much digging (ripping/reinstalling Firestarter, then using tcpdump and repeatedly pinging the Ubuntu hostname from the Windows machine while I watched logs and toggled options) I've finally got it working.  The culprit?

Firestarter -> Edit -> Preferences -> Firewall -> Advanced Options -> Block broadcasts from external network

Once I unchecked this, it magically started working.  I can only guess that "external network" means anything outside the PC, on the outside of the firewall.  I'd interpreted it in my head as anything outside the local subnet.  Oh well, it's fixed now.

As a note, there were absolutely no reject messages in the logs to indicate that any kind of traffic from the Windows box (or the router, for that matter) was being blocked.  Weird.

Hopefully this helps someone else.  Thanks all, for your suggestions.

---

### Post by dmizer on 2006-11-17
heh ... half the battle is figuring out where the problem is.  good to see you got it sorted.

---

### Post by rkdss on 2006-11-22
Hi, I ended on this conversation "googling" for the answer of exactly the same problem, but with another distro, using firestarter too and also I coudn't use name resolution in samba (direct IPs working right too).

Make this:

Preferences > Advanced options > uncheck "Block broadcast traffic" even in the external net.

Someway, seems windows use broadcast traffic to recognise  by name.

After that, for me it works like a charm

---

### Post by sefs on 2006-12-20
I am here laughing so badly and clapping my hands with glee!!!!

This has bothered me since breezy badger i could NEVER understand why the darn thing didnt work properly ... I also thought external meant external to my LAN.  So with a little hope i unchecked that box and lo and behold the network has finally sprang to life!!!!

YOU ARE THE MAN!!!!!!!  MERRY CHRISTMAS TO ALL ... LOL.

but on a short note...

what is this?

```

$IPT -A INBOUND -s $NET -p udp -m state --state NEW -j ACCEPT

```

and do i need it?  I can't ever remember adding any rule like this.  Should I?

Thanks.

---

### Post by HeWhoWalks on 2006-12-20
> **sefs said:**
> I am here laughing so badly and clapping my hands with glee!!!!

YOU ARE THE MAN!!!!!!!  MERRY CHRISTMAS TO ALL ... LOL.

but on a short note...

what is this?

```

$IPT -A INBOUND -s $NET -p udp -m state --state NEW -j ACCEPT

```

and do i need it?  I can't ever remember adding any rule like this.  Should I?

Thanks.

Glad this was helpful.  :)

As for needing that line, I needed to add that to be able to browse my Windows network by name from my Ubuntu box.  If yours is already working fine, you don't need to add it.  (IE:  without that line, smbtree returns nothing, whereas with it, I see all the local shares on the network).  On the other hand, if you can browse by IP address from your linux box, but not by name, try adding it.  Hint:  It's read-only by default, so you'll need to chmod +w to change it.

Good luck :)

---

### Post by ruffneck on 2007-02-15
Thank you HeWhoWalks! I couldn't figure it out but you did...thanks again.

---

