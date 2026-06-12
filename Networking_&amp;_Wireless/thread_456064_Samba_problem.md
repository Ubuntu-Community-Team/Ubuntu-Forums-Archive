---
title: "Samba problem"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by t2000kw on 2007-05-27
I've tried setting up Samba for a home network to share files with a Windows 98 system. 

I set up a password and username (same as I  use in Ubuntu) and when I try to access the Linux system I get asked for only my password, not a username. The password comes back as invalid.

I'm guessing that the Linux system is getting a different username from the Windows system since it is not asking me for any username. The password is the same as I set it up for. 

I did restart the server before I tried this, and I can see the Ubuntu computer on the network from the Windows 98 computer, though I don't see the Windows computer on its own Network Neighborhood for some reason. 

I used the technique in the Ubuntu Linux Bible, which covers Edgy, but I'm using Feisty, which I would not think should be a problem, but I thought I'd mention it. 

It sure would be nice to have an automatic way to set this up.

I did save my original smb.conf file so I can bring it back if I need to start over. 

I'll paste my current config file below in case it helps. 

I do not use WINS, I use DHCP, without static IP addresses. The Linux box is wired to the router, the Win 98 box is wireless. 

Thanks in advance for anyone's help. I did some checking in the forum archives but I didn't see where I might have gone wrong. 

And if it's easier to get read/write access on the Windows machine and do the transfers from the Ubuntu machine, I will set that up first.  But for now I can't "see" the Windows computer from Ubuntu (yet). 

Donald

-----------------------------
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
wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = yes

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
 load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

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

wins support = no
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


[donald]
path = /home/donald
available = yes
browsable = yes
public = yes
writable = no

---

### Post by coxy on 2007-05-27
You could force the Samba user; just remove the lines after your path and replace them with

```

force user = sambauser
read only = No
guest ok = Yes

```

That should allow any Windows machine on your network to connect.

---

### Post by t2000kw on 2007-05-27
I did try that suggestion and I still get asked for a password and still get told it's not correct. 

In case this is useful, in Windows' Network Neighborhood, when I open this computer (named "donald" in Ubuntu), I get this:

Resource: \\Donald\IPC$
Password:

When I cancel I can see this . . .

Just under the top left in the window are the words

donald server
(Samba, Ubuntu) \\Donald

So, let's try it form the other direction. How can I get to the Windows box from my Linux box so I can do the work from here?

---

### Post by dolphin_oracle on 2007-05-27
the problem is likely the win98 box.  If I recall correctly (its been a very long time), there is more than one login type for windows networking.  I believe the default one will try to pass the username that you log into win98 with as the username for networking.  I can't rember exactly, but check under network properties and see what login  our using.  I believe it may even give you a short description.

I don't have a win98 box to check this out, but I would definely look there.

OR, i suppose you could create a ubuntu and samba user to match the user on the win box and give that a try.  If the win box is sending the user login as the username, it should then match up.

---

### Post by t2000kw on 2007-05-27
I'm not using a login, but maybe I'll have to go back and set that up.

---

### Post by t2000kw on 2007-05-27
Well, I can print from the Windows machine through the Ubuntu machine to my Canon i850 printer.

Partial success!!!

Now, if I can just be able to transfer files directly over the network.

I did set up a user account in the Windows laptop that uses the very same username and passwords in Ubuntu.

Still, I get a bad password message when trying to log into Ubuntu over the netowrk to transfer files.

---

### Post by t2000kw on 2007-05-27
Also, I can "see" the other computer in PyNeighborhood, a GUI for network browsing.

---

### Post by dolphin_oracle on 2007-05-27
if the win98 machine is setup correctly, all you should have to do is right click on the folder you want to share and select something like "share..." or properties and then a share tab.  It should be relatively apparent.

Incidentally, on Win 98, file and printer sharing is not enabled by default.  I think you have to install that as a network component.  This would apply weather you want to share other folders or let other machines browse yours.

---

### Post by t2000kw on 2007-05-27
File and printer sharing was set up a long time ago for sharing between our home computers. I do have sharing enabled already on the drive and some folders and can see the shared folders, but can't access them from Ubuntu. I get a message about not being able to mount the folder/drive.  From Windows I get the message about a bad password. 

But I CAN print now from the Windows laptop over the wireless connection, through the cabled part to the Ubuntu computer where the printer is attached to. So I can't be too far from getting this to work.

---

### Post by dmizer on 2007-05-27
first, on your ubuntu server, add your ubuntu user name to the samba group with the following commands:
```
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username
```

take a look here for instructions on how to map your network drive in win98: [http://www-jerry.oit.duke.edu/linux/docs/samba/mapping_network_drive_ms_windows.html](http://www-jerry.oit.duke.edu/linux/docs/samba/mapping_network_drive_ms_windows.html)

---

### Post by t2000kw on 2007-05-28
I thought I set up the smbpasswd thing yesterday and it didn't work, but I tried it again today in case I did it wrong.

It still doesn't let me connect. I get the "incorrect password, please try again" message.

And, since I can't connect, I can't map any folder on the Ubuntu computer as a network drive. 

I'm familiar with mapping network drives--did it between two laptops and a desktop, all Windows computers. 

The network is working or I wouldn't be able to see this computer in Network Neighborhood and I wouldn't be able to print from the WIndows laptop to the Ubuntu desktop computer. 

It's a matter of some sort of authentication problem.

---

### Post by dolphin_oracle on 2007-05-28
check out this thread - the O.P. updated samba and it cleared up his login problem.

[http://ubuntuforums.org/showthread.php?t=449861](http://ubuntuforums.org/showthread.php?t=449861)

---

