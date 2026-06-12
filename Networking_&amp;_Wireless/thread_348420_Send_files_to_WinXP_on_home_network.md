---
title: "Send files to WinXP on home network"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by valkarin on 2007-01-28
I have looked everywhere and had no luck trying to find out how I can send files to an XP laptop on my home network from Ubuntu 6.06.  I have samba installed and it says it's running.  I have a firewall that blocks all connections, but I can fix that.  Can somebody please tell me how to send these files to the laptop.

---

### Post by kosmic on 2007-01-28
First you need to open the Ports so Samba can comunicate with you laptop.

Ports necessary for samba work -> 138-139 445

Then you need to put you linux box and laptop in the same workgroup in linux edit the file /etc/samba/smb.conf and define what you whant to share and also the workgroup name.

The Workgroup name **HAS TO BE THE SAME** in both machines so they can see each other.

After that just restart samba wait 2,3 minutes and you should be ready to go :)
** sudo /etc/init.d/samba restart**

---

### Post by valkarin on 2007-01-28
What setup is needed on the XP machine?

---

### Post by kosmic on 2007-01-28
Im windows in Network if i'm not mistake you need to define to what workgroup you Windows box belong to.

For default it should be MSHOME if i'm not mistake you need to change it so that both workgroup are the same.

I'm sorry but i don't use windows for about 3 month and can't remember where is this option.

But i Will search and tell you, just hang on ;)

---

### Post by kosmic on 2007-01-28
ok where it is :

Go to Start->Setting->Control Panel  and Open "Network" and in the second tab "Identification" note the "Computer Name",  This is the name to use from Linux to access shares on this machine.

This should be the same name in both ;)

---

### Post by valkarin on 2007-01-29
No joy.  It still doesn't work.  When I try to ping or traceroute the XP machine I get nothing.  100% loss of packets.  Also port 445 on the ubuntu machine is udp.  Is that correct?

---

### Post by kosmic on 2007-01-29
Yes 445 UDP :)

Just one silly question are both computers in the same network ??

How is the IPs configured it's static or by dhcp ??

Both computer must be in the same network, something like

Computer 1 IP -> **192.168.1**.100
Computer 2 IP -> **192.168.1**.150 (For example)

They can only comunicate if they are in the same network ;)

---

### Post by valkarin on 2007-01-29
I feel like an idiot.  The firewall on the windows computer was up.  Now that I have it down all the computers can see each other.  However, I still cannot access the linux machine.  It says that I don't have permission.  Is this something I have to edit on the linux machine or the windows machine?  Also, is there a better way such as ssh?  I would like to get Samba up and running now that it has ticked me off, but I would also like to learn if there is a better way.

To answer your question they are on the same network and they get their IPs by DHCP.

---

### Post by tgm4883 on 2007-01-29
Did you share a folder on your win xp machine?  Do you have samba shares setup on your linux machine?  Did you try entering your LINUX username and password when it asked you (when you tried to access it from the win xp machine)

---

### Post by valkarin on 2007-01-29
Yes and yes to the first question.  It never gave me a login promt.  When I clicked on the computer in network places it said I didn't have permisssion

---

### Post by kosmic on 2007-01-29
Hi, can you post the here the file -> /etc/samba/smb.conf so we can see how you have it configured.

The easy way to acess files from Windows/Linux is with Samba :) SSH is for remote login (you can also get files with ssh, with the **scp** command)

---

### Post by valkarin on 2007-01-29
Here is the file.

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

wins support = no
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


[Shares]
path = /home/valkarin
available = yes
browseable = yes
public = yes
writable = yes


---

### Post by kosmic on 2007-01-30
It's all ok with your Samba configuration.

The [Shares] partition can be browsable by anyone.

I don't understand why the windows box says you dont have permissions.

Try looking at the log of samba in /var/log/samba/log.smbd or in /var/log/samba/log.NAME_OF_WINDOWS_BOX.

In a last resort, reboot your linux box, the router and then windows, wait 2,3 minutes and then try to access again the share.

---

### Post by valkarin on 2007-01-30
Didn't work.  More info.  When I right click on the icon for the linux box in windows and select properties, it says that the linux box does not accept remote requests.  I can ssh in and everything.  Is this some sort of linux or windows problem or does it deal with samba?

---

### Post by tgm4883 on 2007-01-30
For the moment, disable your firewalls on both your linux machine and your windows machine and let us know if it works then.

---

### Post by valkarin on 2007-01-30
Not running firewalls.  Turned them off yesterday.  Here is a little more info.  this came from the log.nmbd file.

> [2007/01/30 14:59:56, 0] nmbd/nmbd_incomingdgrams.c:process_local_master_announce(311)
  process_local_master_announce: Server DD47N071 at IP 192.168.1.104 is announcing itself as a local master browser for workgroup MSHOME and we think we are master. Forcing election.
[2007/01/30 14:59:56, 0] nmbd/nmbd_become_lmb.c:unbecome_local_master_success(149)
  *****
  
  Samba name server VALKARIN-DESKTOP has stopped being a local master browser for workgroup MSHOME on subnet 192.168.1.103
  
  *****
[2007/01/30 15:00:13, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396)
  *****
  
  Samba name server VALKARIN-DESKTOP is now a local master browser for workgroup MSHOME on subnet 192.168.1.103

It is interesting to note that there is no 192.168.1.104 computer on this network.  I have 3 computers on it and .103 is the highest number assigned to a computer.  The router is of course .1

---

