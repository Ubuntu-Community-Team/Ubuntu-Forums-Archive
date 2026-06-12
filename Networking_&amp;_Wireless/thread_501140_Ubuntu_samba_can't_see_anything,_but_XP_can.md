---
title: "Ubuntu samba can't see anything, but XP can"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by meshellwm on 2007-07-14
Hey. I just installed Ubuntu 7.04 x64 on an AMD Athlon PC. I set up a samba share for 1 folder. My XP machines can see it and read/write. My problem is that Ubuntu can't see anything and I can't print to my HP DJ 5550 printer on a XP machine.  Also, my laptop with Kubuntu on it, was working fine with samba and it has stopped working with the same problem. It is almost as if samba just died on my network! Only the XP machines can see each other and print to each other! I've spent several days trying to get this to work. Any help would be much appreciated....

---

### Post by ukripper on 2007-07-16
can you post your smb.conf here

---

### Post by punky on 2007-07-16
Sorry, double post. Please delete!

---

### Post by punky on 2007-07-16
I am having a similar prob.

Set samba up and it worked a treat. All of a sudden, it stopped. The mounted dir was empty. fstab didn't complain, and it showed up as a mounted share in mount. I restarted, and the same. fstab didn't complain and it showed in the mount list. Sometimes I got an input/output error when doing a ls

Came on here to post, and it suddenly started working... With no alterations to anything

I'll keep you guys posted if I can supply any more background to this. I'll keep an eye on it.

---

### Post by meshellwm on 2007-07-16
Thanks for answering. Here is my samba file...

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
   workgroup = WGM

# server string is the equivalent of the NT Description field
#   server string = %h server (Samba, Ubuntu)
   server string = %h

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;wins server = w.x.y.z

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
;   security = user

security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
 ;  encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
 ;  passdb backend = tdbsam

 ;  obey pam restrictions = yes

;   guest account = nobody
 ;  invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
 ;  passwd program = /usr/bin/passwd %u
 ;  passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

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
   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

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


[Shared]
path = /usr/Shared
comment = General Purpose Folder
available = yes
browsable = yes
public = yes
writable = yes
guest ok = yes
case sensitive = no

---

### Post by punky on 2007-07-17
I had this problem again. It was working fine. The machine was just idle with nothing running and it happened.

I try a ls it freezes and then it comes up with input/output error. Also, when you press tab for the autocomplete, as if you was going to cd into the dir, the autocomplete freezes. Other machines can access the share so there's nothing wrong there.

I did a mount -a and nothing changed. I tried to unmount it but it said the device was busy. tried to unmount with the -f force option, but still said it was busy.

Any ideas? 

Thanx.

---

### Post by Xizorbg on 2007-07-22
Hello all-

I had a similar problem.  I have a 64-bit 7.04 on my desktop, and the 32-bit w/ Windows XP Pro Dual boot on my notebook.  Desktop sees both Ubuntu and Windows shares w/o a problem.  Laptop will only "see" Desktop shares when in Windows mode.  Weird.  I have changed permissions in firestarter to allow the traffic, but no help.  If anyone has any ideas please share!

Thanks,
X

---

### Post by meshellwm on 2007-07-30
Hi,

I finally got all of my Linux issues resolved over the weekend. I have created a web page with all that I did to my laptop for anyone who is interested at:

[http://home.earthlink.net/~meshellwg/w/www/html/LinLT.html](http://home.earthlink.net/~meshellwg/w/www/html/LinLT.html)

I learned a lot from this "mini" project; I hope it helps someone.

---

### Post by linuxgeoff on 2008-01-30
> 

I try a ls it freezes and then it comes up with input/output error. Also, when you press tab for the autocomplete, as if you was going to cd into the dir, the autocomplete freezes. Other machines can access the share so there's nothing wrong there.

I did a mount -a and nothing changed. I tried to unmount it but it said the device was busy. tried to unmount with the -f force option, but still said it was busy.

Any ideas? 

Thanx.

I have the exact same problem accessing a SAMBA drive on a mounted Iomega server.  All was fine for weeks, and then this intermitant fault starts up.  In addition automount via fstab no longer works; I can manually mount and unmount.  I can then see the directories on the server for a few attempts, then back to the situatin above.

Any ideas?  Did the previous posters find a solution?

I'm so desparate, I'm close to doing a fresh install!

Thanks,  Geoff

---

### Post by ukripper on 2008-01-31
> **linuxgeoff said:**
> I have the exact same problem accessing a SAMBA drive on a mounted Iomega server.  All was fine for weeks, and then this intermitant fault starts up.  In addition automount via fstab no longer works; I can manually mount and unmount.  I can then see the directories on the server for a few attempts, then back to the situatin above.

Any ideas?  Did the previous posters find a solution?

I'm so desparate, I'm close to doing a fresh install!

Thanks,  Geoff

Post output of the following :

```
sudo blkid
```

```
sudo cat /etc/fstab
```

```
sudo fdisk -l
```

l is small ell not 1

---

### Post by lungdart on 2008-01-31
Also here I see no mention of anyone configuring the firewall for Samba shares.

Easiest way to do it is to install firestarter, and under the ports section click add, and then from the drop down menu choose the samba/smb entry, and confirm changes.

I also like to add a global allow of 192.168.0.1/24 to allow my entire network through no matter the port, as I don't care too much for internal security. (Its just a desktop machine for gods sake, not a banking server)

---

### Post by ukripper on 2008-01-31
> **lungdart said:**
> Also here I see no mention of anyone configuring the firewall for Samba shares.

Easiest way to do it is to install firestarter, and under the ports section click add, and then from the drop down menu choose the samba/smb entry, and confirm changes.

I also like to add a global allow of 192.168.0.1/24 to allow my entire network through no matter the port, as I don't care too much for internal security. (Its just a desktop machine for gods sake, not a banking server)
 
Whats the point of firewall when you have to give global access to your network? I rather not have firewall in this case

---

### Post by lungdart on 2008-02-05
You dont have to.

The linux firewall opens a port when ever something on your system asks. Then it keeps that port open for communications to come back. When the program no longer requests the port, it closes.

The problem is when someone wants to initiate the communication with you. Then you need the port open to at least that IP address.

Since I do a lot of ******* around on my network, I like to keep the internal wide open to my desktop machine. This still leaves protection from the outside (Since my router has its firewall disable since its very bad.). I trust my network, and I dont require the bullet proof security you get when you take your time to set it up. I enjoy the quick and easy way.

Again it is what I do, many will disagree with me that its not proper, but I really dont care about it that much. There's nothing on this machine worth protecting from to be honest. All my important **** is on a fileserver.

---

