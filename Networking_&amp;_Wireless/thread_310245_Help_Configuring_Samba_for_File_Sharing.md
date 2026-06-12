---
title: "Help Configuring Samba for File Sharing"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by TheBigBakedBean on 2006-11-30
So I have been searching (using the wrong keywords, I'm sure) for a few days now for an answer and have only just worked up the guts to ask.

My home network consists of a hodgepodge of machines that I use for various tasks.  I have 2 desktops running Windows XP, 1 desktop running Kubuntu Dapper, and a laptop running Xubuntu Edgy.

The Kubuntu machine and the XP machines all communicate nicely amongst themselves.  Each machine has at least one directory shared via samba. I've only recently installed xubuntu on the laptop, and I can't seem to configure samba correctly on it.

I'm having no trouble with accessing the internet on any of the machines, and they are all communicating with the router correctly.  Additionally, I know that they are able to "see" eachother in some fashion because I was able to configure rhythmbox to access the daap music share I have running on one of the xp machines.

Currently, when I browse the workgroup on either of the xp machines, I can see but not access the xubuntu laptop.  Curiously, however, when I browse the workgroup in xbox media center on my modded xbox, I can't see the laptop at all.  When I browse the network (the file manager defaults to network:///, which doesn't display anything, and neither does smb:///) on the xubuntu machine, I can't see a thing.

I have taken the following steps thus far:
1.) [This thread](http://ubuntuforums.org/showthread.php?t=308426) explains a problem similar to mine, but I think this guy is using gnome so I wasn't able to find the options that they referenced.
2.) I tried using the same configurations I found in the smb.conf file from the kubuntu machine, to no avail.
3.) I tried manually editing the smb.conf file with what I thought would be most appropriate given the descriptions, but that didn't do anything so I reverted to the original version, fearing I had done more harm than good.  In both instances of editing the smb.conf file, I restarted samba via the terminal.

Here are the contents of my smb.conf file currently.  The only thing I have added is the location of the directory I would like to share and I've changed the workgroup name.
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
   workgroup = UNICHRON

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



[dump]
path = /home/penguin/dump
available = yes
browsable = yes
public = yes
writable = yes

```

I'm most interested in being able to browse the xp shares from the xubuntu machine, but of course I would really like for everything to work together.

I've also tried to mount the shares using mount -t smbfs in the terminal, and none of them were accessible.

Any help you could provide would be very much appreciated.

---

### Post by KingBahamut on 2006-11-30
well try any one of these three. 

[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)
[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/windows-networking.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/windows-networking.html)
[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by Iowan on 2006-12-01
I, too, speak from the Gnome side of Ubuntu (sorry)... Have you installed the Samba server?  SMBFS?  Samba client comes pre-installed, but some of the others do not.

---

### Post by rumour88 on 2006-12-08
This is a good guide for mounting drives not sure It will be perfect for what you need but it helped me allot when trying to create a shared drive

[http://www.smorgasbord.net/how_to_install_second_hard_drive_ubuntu_linux]("http://www.smorgasbord.net/how_to_install_second_hard_drive_ubuntu_linux")

although you do need to change *default* in fstab to *umask=0000* and that will alow you to write to that file like a standard windows share

---

### Post by jvc26 on 2006-12-08
@KingBahamut thanks very much for the links, I followed the guides you linked to, and the setup works so that I can access the files on my Ubuntu desktop from the XP computer. Is it possible for me to set it up so I can access the XP computer's shared documents from my Ubuntu Desktop as I havent been able to find a link to this setup.

*EDIT* All is well have managed to work that one out too.

Thanks,
Il

---

### Post by jvc26 on 2006-12-14
Hi there I ran though the [http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba) post and it worked the first time (see my above post) however due to a problem with update-manager my filesystem got corrupted, and now I have a vanilla install of 6.10 My problem comes with this - I have followed the guide, and when I go to <places> <network servers> <windows network> I can see the HOME workgroup (there is a small icon of what looks like a piece of paper) but when 
I click on it I get the error message :
Couldn't display "smb:///home". The location is not a folder.

Any ideas of what may be wrong? This occurs both with the firewall on the windows computer disabled and when it is on. Its strange as it used to work before the system died, and also worked when I was rescuing my files when it broke using the live cd.

Cheers,
Il

---

### Post by tweedledee on 2006-12-17
> **Illuvator said:**
> Couldn't display "smb:///home". The location is not a folder.

I also have this problem, I don't know if it's a bug or feature.  Anyway, the problem is the triple slash "///".  Change it "smb://home" and it should work.  For some reason my Edgy install always uses the triple instead of double slash via Nautilus, which means I end up typing all the addresses in.

---

### Post by WakkiTabakki on 2007-01-12
I had sort of the same problem. If I did a refresh in the folder a few times, suddenly the icon network appeared as it should and it worked (seems like a race condition or something).

I did this to fix it:
```
sudo gedit /etc/gnome-vfs-2.0/modules/smb-module.conf
```
and change
```
smb: [daemon] libsmb
```
to
```
smb: libsmb
```

Reboot or restart samba.

Cheers
/N

---

### Post by msimon1960 on 2007-01-14
Neither SAMBA or NFS work -- I've tried.

I've been working on it for 5-6 weeks.  Tried Ubuntu Drake and Kubuntu 6.10.  Tried different computers, different NIC's, even a different router.

Nothing.

I'd like to hear from someone, anyone, who actually has been able to setup a server that allows users to share a common directory with full R/W access.

I don't believe it's possible and the zillions of posts in the forum seem to suggest that.  I haven't found one yet that said they actually got it working.

I live in hope that I'm wrong.  I'm trying Mandriva next but I'm noted in their forums that they are having the same problem.

Is there anyway to converse with the folks that developed SAMBA -- maybe they can address the problem in some systematic fashion and/or fix whatever the problem is.

Matt.

---

