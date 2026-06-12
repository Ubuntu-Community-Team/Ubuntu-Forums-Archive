---
title: "XP and Ubuntu Netwroking"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by RudolfMDLT on 2006-08-26
Hi,

2 Months ago I actually helped people network their XP-Ubuntu systems but this time I really just can't get Samba to work. Whenever i go to "network servers" it finds the Windows-Network, but no computers are in it. Before my upgrade to dapper, the command "smbtree" would display all the shared folders on my network and who they belong to. All it does now is give an error messages, asks for a password. takes about 5 seconds and then gives me a knew line in the terminal. :

rudolf@rudolf:~$ smbtree
WARNING: The "printer admin" option is deprecated
Password:
rudolf@rudolf:~$

Here's my setup. I have 2 network cards, the on board one is broken so I don't use it anymore. The second one has got 2 IP - address's bound to it. Samba is enabled, 3 folders are shared, my Workgroup has been set the same for all machines on my network, the users have been added to my user's list and to the samba users list. I can even VNC to all the windows machines wich proves that the hardware works. But, I need file sharing! Attached are my network config file and my samba config file.

Any help will really be appreciated,

Thanks,

Rudolf

rudolf@rudolf:~$ /etc/network/interfaces

[PHP]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static

address 10.0.0.7
netmask 255.255.255.0
gateway 10.0.0.2

auto eth1:0
iface eth1:0 inet static

address 192.168.10.47
netmask 255.255.255.0 

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

[/PHP]

Samba

[PHP]#
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
   workgroup = homenet

# server string is the equivalent of the NT Description field
   server string = rh

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = no

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
  interfaces = eth1

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
   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = false

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

   guest account = Guest
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
;   domain logons = no
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
   printing = bsd
   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
   printer admin = rudolf


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
wins support = no
[homes]
   comment = Home Directories
   browseable = yes

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
   create mask = 0664

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0775

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = yes

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
   public = yes
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes
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


[rudolfhome]
path = /home/rudolf
available = yes
browseable = yes
public = yes
writable = yes

[vid]
path = /home/rudolf/videdit
available = yes
browseable = yes
public = yes
writable = yes

[Stuff]
path = /stuff
available = yes
browseable = yes
public = yes
writable = yes
[/PHP]

---

### Post by RudolfMDLT on 2006-08-27
Okay, as I'm not getting any replies - I can ping every machine on the network - any geuses why i can ping the other windows machines but not see them in Network servers like I used to?

---

### Post by tmtjjhnsn on 2006-08-27
I have no idea.  I have the same problem, which I have been trying to solve for five days, but I am not getting any bites on my post, and none of the threads that I have read have solved my problem, yet.

---

### Post by dannyboy79 on 2006-08-28
i believe you can somehow tie an ip address to your WINXP box in a hosts file and then maybe you'll be able to see the machine. Can you ping it by computer name as well as ip? Do you have your guest account on for your WINXP box? Also, if all else fails, go to this website, it's what I used to set up samba between my 3 computers, WINXP, Xubuntu, Ubuntu! [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/54415-fileserver-samba-printserver-cups-howto.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/54415-fileserver-samba-printserver-cups-howto.html)

---

### Post by mkquist on 2006-08-30
In case your still having problems, this one solved mine quick and easy.. 
[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=file+sharing](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=file+sharing)

---

### Post by huygens on 2006-08-30
Hi RudolfMDLT,

You could try the attached smb.conf file (bzip2 compressed). I merged the smb.conf shipped by default on Dapper with your modification. As I unerstood that you had the problem since upgrading to Dapper, this should probably solve it.
What to do with the attached file, download it to the root of your home directory (I guess it is /home/rudolf) and then perform this inside a terminal (Applications->Accesories->Terminal):```
sudo cp /etc/samba/smb.{conf,backup-forum}
cd $HOME
bunzip2 smb.conf.bz2
sudo cp smb.conf /etc/samba/
sudo /etc/init.d/samba reload
``` OK some explanation, I first make a backup of your file (which will be called smb.backup-forum). Then, I go to your home directory and uncompress the file. Finally I copy it in place of your previous Samba configuration and tell the Samba daemon to reload its configuration file.
Wait a minute ;-) the SMB protocol is sometimes slow when a new computer enter a network, because the computers on this network need to elect one as the "master" and of course they - like humans - all want to be it :-)... So give it time to settle down their dispute ;-)

Huygens

PS: I have seen that you are using clear password on your Samba network :-( well if you want to use encrypted one (it would require that you have at least Windows 98 or better on all your computer, Linux is of course better ;-) ) you could try this thread: [http://www.ubuntuforums.org/showthread.php?t=228454](http://www.ubuntuforums.org/showthread.php?t=228454) Check for the second post (mine)

---

### Post by RudolfMDLT on 2006-09-02
Hi! Sorry for the late reply but the ADSL system in my area was out for 5 days!:frown: 

Anyway, thanks for all the replies! I really apreciate them!

Thnx!

---

### Post by RudolfMDLT on 2006-09-02
Back again! I got the system working again on my own 3 days ago - just hacking away at all the config f1iles one by one and disabling the onboard network card I finally got the thing working. Thanks for the detailed help huygens! I'm still pretty new to Linux and I really love it when you old hat's explain yourselves! - the thing with the Samba network being slow, I'm not running any other Linux machines on the network(the family won't convert! :) ). Isn't there supossed to be an Ethernet standerd or ISO that windows, mac and linux all need to conform to? I've expiernced the slowness whenever i try to access the Windows machines from my box, nut from the windows machines to the linux box everything flies!? Whats up with that?

Thanx again for the help though - I'm saving the config file anyway (just incase)! :)

---

### Post by huygens on 2006-09-04
Hmmm... strange. It is rather the opposite on my network, but the slowliness under Windows is not that important. It just rather feel slower to display the content, but not too slow to be annoying. So I never bothered to find out. I guess this is just the Windows explorer which is slow to display items, rather than the underlying network protocol which has some impacts... At least in my case.
Samba is a program that is able to interoperate with the CIFS/SMB protocol. This is a Microsoft defined protocol. I do not think it is ISO as the Samba team had to reverse-engineered it. Mac OS X is using Samba underneath to communicate with Windows, just as Linux does. Of course, Windows has its own program in the heart of its OS to handle this protocol.

Eventhough Samba reverse-engineered the CIFS protocol, it has been proven in many case faster than Microsoft own implementation (at least before Windows XP was out, I do not know the current status)

What I would advise you if you are bothered with the speed, it is to open a new thread about it. I cannot help you further, and perhaps someone else will bump into the new thread and might be able to help you.

Sorry,

Huygens

---

