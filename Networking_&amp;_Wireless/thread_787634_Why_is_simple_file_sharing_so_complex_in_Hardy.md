---
title: "Why is simple file sharing so complex in Hardy?"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by sipickles on 2008-05-09
Hi,

I am puzzled. Being relatively new to Linux, I expected it to be all about networking. I thought Unix (and Linux) was BUILT for networking.

But it seems highly convoluted and inaccessible.

Even Gutsy seemed to work better.

After a more ambitious start which failed, I have lowered my initial expectations. Now I am simply trying to share folders between 3 PCs at work (2 x Ubuntu Hardy, 1 x Xubuntu Hardy - Don't even get me started on Xubuntu!)

I expected these Ubuntu machine to simply see each other. They are all on the same network - and yes, they can ping each others Static IP addresses (I have Windows Networking experience ;) )

So why on a Linux box do I have to install Samba to provide simple file sharing???

I followed that course, installed samba on each machine, edited the smb.conf to share a folder, and set user permissions. I used smbpasswd, and /etc/init.d/samba start.

Nothing

No machine will see each other.

I get a WINDOWS NETWORK icon, in which I can see some of the printer servers on the network. 

I really expected more of Hardy on this front. Here's me trying to convert work colleagues, and now I am left red-faced at the complexity of supposedly simple tasks.

And this is only the first step. Ideally, we'd be able to share with the XP and vista machines in the network too.

I should point out that we are sharing peer-to-peer, thru a network switch, not with a central fileserver.


Here's my smb.conf if that sheds any light:
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
	workgroup = mshome

# server string is the equivalent of the NT Description field
	server string = %h Ubuntu

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
	username map = /etc/samba/smbusers

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
	encrypt passwords = no

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
	passdb backend = tdbsam

	obey pam restrictions = yes

	guest account = simon
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

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
	comment = Home Directories
	browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
	read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
	directory mask = 0775

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
	valid users = %S
	guest ok = yes

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
	browseable = yes
	read only = yes
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

[Shared]
	path = /home/simon/Shared

	browseable = yes
	guest ok = yes
	available = yes
	writable = yes


```

UPDATE

pyNeighborhood sees all the Ubuntu Machines and can eve see their shared folders. Unfortunately, these all fail to mount :(

---

### Post by pmorton on 2008-05-09
Don't use Samba unless you need file access access from/to a Windows host. Not that it won't work, but it's meant for inter-operating with Windows, and that means there is a certain complexity involved, as you can see from the contents of the smb.conf file.

Instead use NFS (Network File System).

See [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by sipickles on 2008-05-09
Thanks for the quick reply.

I'll take a look.

Rebooting every machine on the network has had something of a positive effect.

Samba is actually working in most cases  - even with windows machines!

Inexplicably, some folders still fail to mount but on the whole it's passable.

My tip - REBOOT EVERYTHING!

---

### Post by revderek on 2008-05-09
Hi,

I'd agree about avoiding Samba file sharing unless using a mixed environment including Windows machines. NFS is a good way to share files under *nix and is available with some M$ installations.

However, I would disagree with the idea of rebooting everything. By all means reboot Windows machines but the fact that something worked under *nix which didn't before the reboot is usually co-incidental or because the service required restarting. Samba is an example - periodically the smb daemon re-reads the configuration file but if the "new" configuration is tested before the file is re-read, then the changes don't appear to have worked. A reboot will, of course, fix that but so, too, will restarting the daemon. Try "sudo /etc/init.d/smb restart" and the changes will propagate at once. Similarly, changes to the "/etc/exports" file used by NFS also requires the NFS service to restart - "sudo /etc/init.d/nfs-server restart".

Ideally, try to avoid rebooting *nix machines - it does no harm but isn't usually required. If the machine is a server, then keeping it online is even more important which is one of the reasons *nix makes good networking.

Your point about ease of use is well made BUT if file sharing is semi-automatic then so is hacking. A little system administration is so much safer than clicking "share".

I haven't really looked at your smb.conf sample because I think you have moved over to NFS. Samba configuration can be enormously capable and complex. I have used it in a mixed Windows/Linux/etc. environment and the server ran for 5 years non-stop. The organisation using it called me after 5 years because they needed to take the server offline and power it down and they had forgotten/lost the root password. (Solution, because I had forgotten the password as well, ctrl-alt-del and power off when it reaches the point of booting up again.)

For file sharing also consider using something like gftp in ssh mode. If NFS needs help, try [http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

Good luck,
Derek

---

### Post by revderek on 2008-05-09
P.S. I have now had a quick look at your smb.conf file. I assume you haven't made this available on a general network as it totally open. To secure it a little, move the /home/simon/shared directory out of the home environment. You may need to use sudo to move it, e.g. "sudo mv /home/simon/shared /opt/shared" then make it accessible to all "sudo chmod 777 /opt/shared". Remember, *nix systems are usually case-sensitive.

Then create a new share in smb.conf:
[shared]
   comment = Shared folder
   read only = no
   browseable = yes
   path = /opt/shared
   guest ok = yes
;   create mask = 0775
;   directory mask = 0775
You might want to look at forcing groups and permissions here, too.

Lastly, rewrite your home share as the original to repair the insecurities:
[homes]
   comment = Home Directories
   browseable = no
   read only = yes
   create mask = 0700
   directory mask = 0700
   valid users = %S

:-)

---

### Post by Iowan on 2008-05-09
One thing I noticed:```
# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
	encrypt passwords = no
```
Windows 95 is about the only OS that did not use encrypted passwords... but that should mean authentication problems - not share visibility issues.

---

### Post by persev on 2008-05-10
Searching for an answer also I have realized that NFS isn't even an option listed anymore, perhaps Ubuntu has stopped supporting it.

As for the smb sharing option, an install option came up asking for permission to install Samba. Unfortunately  once samba is installed an error message appears  > 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershare. Ask your administrator to grant you permissions to create a share. THERE IS NO ADMINISTRATOR IN UBUNTU! ONLY SUDO! 

If they are going to have a pop-up dialog asking to install a service why not go all the way and have it set up the service also? Linux for Human beings by foot.

---

### Post by sipickles on 2008-05-11
I agree Persev, that is a bad bug.

--------

rev, I guess it was the rebooting of windows machines that sorted me out.

I admit, as soon as I read instructions on setting up Samba, I feel like banging my head on a doorframe ;)

I can't honestly see the difference your samba suggestions make! Samba-noob :(

I shall report on the state of play at work on Monday morning!

---

### Post by BluShift on 2009-05-04
With PyNeighborhood, you have to edit your default mount location. By default, it is /mnt/lan/ and unless you run PyNeighborhood as root, you won't be able to mount to that location. You need to change it to your home folder ex. /home/<user name>/

Hope that helps :)

---

