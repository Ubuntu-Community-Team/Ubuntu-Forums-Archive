---
title: "[SOLVED] samba fun!!"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by tomski on 2008-05-26
Well i seem to joined all the other people out there who are having issue's with good ol samba!!

you may recognise parts of this issue from other post's but after reading them & failing to fix the issue im left with no alternative than to ask you great people for a lil help.

since the hardy upgrade i cant access any samba share or even view it from within a windows pc that can access the samba server via ssh,webmin also the samba server is my gateway to the internet so all is ok with the connection & the firewall it has on it (shoreline)



here is my smb.conf:

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
   workgroup = 2tomz

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
   interfaces = 127.0.0.1/8 192.168.0.1/24

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
   bind interfaces only = true

  smb ports = 139


#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
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
   security = user
   username map = /etc/samba/smbusers

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
;   usershare max shares = 100

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
   writable = yes
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
   guest ok = no
   read only = yes
   create mask = 0700

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
##added by tom###
[public]
   comment = public
   path = /public
   browseable = yes
   writable = yes

```


i have reinstalled samba since this issue popped up

here is my old (gutsy) smb.conf that worked before the upgrade:

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
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n
	obey pam restrictions = yes
	hosts allow = 127.0.0.1, 192.168.0.0/24
	passwd program = /usr/bin/passwd %u
	dns proxy = no
	netbios name = fwall
	writeable = yes
	invalid users = root
	default = public
	remote announce = 192.168.0.10/2tomz
	workgroup = 2tomz
	os level = 20
	socket address = 192.168.0.1
	hosts deny = 0.0.0.0/0
	security = user
	max log size = 1000
	log file = /var/log/samba/log.%m
	guest account = tom
	socket options = TCP_NODELAY
	interfaces = 127.0.0.1, 192.168.0.0/24
	username map = /etc/samba/smbusers
	encrypt passwords = true
	public = yes
	passdb backend = tdbsam 
	keepalive = 60
	netbios aliases = firewall
	server string = %h server (Samba, Ubuntu)
	path = /public
	comment = fwall
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	bind interfaces only = yes

[homes]
	create mask = 0777
	comment = Tom's Home
	browseable = yes
	directory mask = 0777
	writable = yes
	path = /home/tom
	valid users = tom

[public]
	writable = yes
	force group = users
	force user = tom
	create mask = 0777
	directory mask = 0777
	comment = public on Fwall
	valid users = tom
	public = yes
	user = tom
	

path = /public
available = yes
browseable = yes
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
#[cdrom]
#   comment = Fwall's CD-ROM
#   writable = no
#   locking = no
#   path = /cdrom
#   public = yes

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
   preexec = /bin/mount /cdrom
   postexec = /bin/umount /cdrom



available = yes
browseable = yes

#[Docs]
#path = /home/tom
#comment = tom on Fwall
#available = yes
#browseable = yes
#public = yes
#writable = yes


#[tomshome]
#path = /home/tom
#comment = private
#available = yes
#browseable = yes
#public = yes
#writable = yes


#[Root]
#path = /
#comment = / on fwall
#available = yes
#browseable = yes
#public = yes
#writable = yes

[tom]
	comment = tom home
	path = /home/tom

[logs]
	comment = fwall logs
	path = /var/log/

```

when i restart the service this is what i see:
```
tom@fwall:~$ sudo /etc/init.d/samba restart
[sudo] password for tom: 
 * Stopping Samba daemons                                                       start-stop-daemon: warning: failed to kill 15168: No such process
                                                                         [ OK ]
 * Starting Samba daemons                                                [ OK ] 

```

when i look in the log file i see this:

```
[2008/05/26 16:09:42, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/05/26 16:09:42, 0] lib/util_sock.c:open_socket_in(830)
  bind failed on port 139 socket_addr = 192.168.0.1.
  Error = Address already in use

```

when i run smbtree i see this:

```
tom@fwall:~$ smbtree
Password: 
2TOMZ
	\\UBUNTU2        		ubuntu2

		\\UBUNTU2\D              	

	\\FWALL          		fwall server (Samba, Ubuntu)
Receiving SMB: Server stopped responding
failed negprot

```

when i right click on a folder in nautilus & try to add a share i get this error:

```
'net usershare' returned error 255: [2008/05/26 16:10:40, 0] libsmb/clientgen.c:cli_receive_smb(112)
  Receiving SMB: Server stopped responding
net usershare add: cannot convert name "Everyone" to a SID. NT_STATUS_IO_TIMEOUT.

```

i have followed numerous thread's & howto's trying to fix this problem but just cant seem to get it working???

any comments or thoughts would greatly be appreciated
sorry to add to the amount of samba based threads but the error's im receiving don't appear to received by others

---

### Post by mapes12 on 2008-05-26
I couldn't get sharing to work at all across my home LAN therefore I gave up on Samba network shares. Having read a number of posts my network now accesses clients using Secure Shell - SSH. I find it much easier. There are utilities to connect XP and Ubuntu boxes via this protocol.

These links may be helpful:

[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[http://www.openssh.org/](http://www.openssh.org/)

[http://ubuntuforums.org/showthread.php?t=793308&highlight=ssh](http://ubuntuforums.org/showthread.php?t=793308&highlight=ssh)

:guitar:

---

### Post by superprash2003 on 2008-05-26
many samba setups crash after upgrade.. if nothing helps you might want to reinstall samba again and try..

---

### Post by tomski on 2008-05-26
> **mapes12 said:**
> I couldn't get sharing to work at all across my home LAN therefore I gave up on Samba network shares. Having read a number of posts my network now accesses clients using Secure Shell - SSH. I find it much easier. There are utilities to connect XP and Ubuntu boxes via this protocol.

These links may be helpful:

[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[http://www.openssh.org/](http://www.openssh.org/)

[http://ubuntuforums.org/showthread.php?t=793308&highlight=ssh](http://ubuntuforums.org/showthread.php?t=793308&highlight=ssh)

:guitar:

many thanks for the prompt response :)
i do already use ssh from my win xp box but mainly for editing config's & admin work

looks like ill be using scp to transfer files from my ubuntu gateway too :(
it was just so much easier to map a network drive to my winxp box
& grab the files i needed

---

### Post by tomski on 2008-05-26
> **superprash2003 said:**
> many samba setups crash after upgrade.. if nothing helps you might want to reinstall samba again and try..

i did mention that i had re-installed samba after my first attempt at fixing this issue!
thanks for the response though :)

---

### Post by jetsam on 2008-05-26
I think I'd be tempted to try a bit more to get the old smb.conf to work.  I don't know of any important changes to the config format between the Gutsy and Hardy versions of Samba.  

My eye keeps landing on this as possibly causing trouble:
```
socket address = 192.168.0.1
```
Try commenting it out?

I think I'd change this line as well:
```
	interfaces = 127.0.0.1, 192.168.0.0/24
```

to:
```
interfaces = 127.0.0.0/8 eth0
```
But you should change eth0 to the interface name you have on the lan side of your firewall.  (I'm guessing it's a firewall.)

---

### Post by tomski on 2008-05-26
for those who are interested here is a link to WinSCP:

[winscp407setup.exe]("http://heanet.dl.sourceforge.net/sourceforge/winscp/winscp407setup.exe")

---

### Post by tomski on 2008-05-26
> **jetsam said:**
> I think I'd be tempted to try a bit more to get the old smb.conf to work.  I don't know of any important changes to the config format between the Gutsy and Hardy versions of Samba.  

My eye keeps landing on this as possibly causing trouble:
```
socket address = 192.168.0.1
```
Try commenting it out?

I think I'd change this line as well:
```
	interfaces = 127.0.0.1, 192.168.0.0/24
```

to:
```
interfaces = 127.0.0.0/8 eth0
```
But you should change eth0 to the interface name you have on the lan side of your firewall.  (I'm guessing it's a firewall.)

thanks for the response jetsam

yea i tried those too :(
eth1 is my lan 
something seems to make the smb server crash coz even when i restart it it fails to stop the old process
im reluctant to give up though

---

### Post by jetsam on 2008-05-26
> something seems to make the smb server crash coz even when i restart it it fails to stop the old process

...that sounds bad.  Did the upgrade leave you with two versions of samba?

What do you get when you do ```
sudo /etc/init.d samba stop
```

and then```
ps aux | grep mbd
```

If there's samba stuff still running, you could force samba to quit with:
```
sudo killall smbd
sudo killall nmbd
```

---

### Post by tomski on 2008-05-26
no i only got 1 install of samba since the upgrade

what made me think it was crashing was because of this error i get in nautilus:
```
'net usershare' returned error 255: [2008/05/26 16:10:40, 0] libsmb/clientgen.c:cli_receive_smb(112)
  Receiving SMB: Server stopped responding
net usershare add: cannot convert name "Everyone" to a SID. NT_STATUS_IO_TIMEOUT.
```

im looking for reason that may give this error & i'll post my findings here.

Here is the output of the commands you asked me to run:



```
tom@fwall:~$ sudo /etc/init.d/samba stop
 * Stopping Samba daemons                                                                                               start-stop-daemon: warning: failed to kill 8364: No such process
                                                                                                                 [ OK ]
```

```
tom@fwall:~$ ps aux | grep smbd
tom       9010  0.0  0.1   3008   768 pts/0    S+   18:28   0:00 grep smbd

```

---

### Post by jetsam on 2008-05-26
OK.  Samba is stopping just like it should.  That listing from **ps aux | grep mbd** is showing only the ps command itself.  

There's a known bug with error 255, but I'm not sure it's the same problem you have.  The errors seem slightly different.  The fix seems to be to log out and back in again or to reboot after you install Samba.  

More info here:
[http://ubuntuforums.org/showthread.php?t=772706]("http://ubuntuforums.org/showthread.php?t=772706") 

and the bug report here:
[https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/215810]("https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/215810")

---

### Post by tomski on 2008-05-26
yep thats what i found with a google search lol
oh well look like i am just gonna have to wait it out

ive email a couple of my friends & sent them all my configs for samba & they work for them but they run debian 4.0 so it must be a bug in the ubuntu release :(

---

### Post by jetsam on 2008-05-26
Your old config works for me on Hardy if I comment out:
```
#	passwd program = /usr/bin/passwd %u
```

and
```
#	socket address = 192.168.0.1
```

I think the passwd program line made the difference. I commented out socket address because I don't really understand the line.  

I made some other I think trivial changes (different subnet address/workgroup.)

Samba would crash instantly with the passwd program line, and work without it.

---

### Post by LawrenceSalberg on 2008-05-26
I've been reading this thread after experiencing a similar problem today. It started off as a different problem where certain administrative programs would hang (see this [thread where I outlined the prob]("http://ubuntuforums.org/showthread.php?t=802388")), but based on another's comments there, along with these here, I'm wondering if they Network / Host file he mentioned there has anything to do with it. 

I don't notice anything odd there, but I haven't enough experience to notice it anyway.

Anyway, just thought I'd bring it to the attention of this thread in case it solves the Samba issue.

Mine was working a-ok until this morning when I installed 22 updates. I was running the beta 8.04, then the official release version, and everything was fine until today's update. (Although I don't know what was updated or how long they had been sitting there - maybe about five days since I turned on this machine).

Which reminds me... anyone know where the detailed release notes for Ubunta are kept? By which I mean, not the basic versioned releases (8.04, 7.10, etc), but every single little update to every package and kernal? I'd like to see what was just foisted upon my machine today to see if I can isolate the issue.

---

### Post by tomski on 2008-07-14
very odd this is!!!

after pulling my hair our for weeks over this i fixed it but in a odd way:

i connected to my firewall/server via a SSH tunnel from a windows pc then forwarded port 139 to my local desktop winxp via the additional loopback adapter 
full instructions:
(you will need local admin rights on the xp box)
1: install the loopback adapter
start->control panel->add hardware->yes it's connected->search list for net adapters->install from list->select microsoft->select loopback adapter
2: configure loopback adapter
start->control panel->network connections->look for a new adapter here->right click->properties->REMOVE THE TICK FOR ALL SERVICES EXCEPT INTERNET PROTOCOL(TCP/IP)->give it a static ip but dont worry about default gateway or dns servers->Advanced->remove tick for 'Automatic metric'->type in metric value = 9999->WINS tab->disable NetBios over TCP/IP->ok->ok->ok
3: REBOOT YOUR PC
4: tunnel to server
download & install putty on the windows box
start putty
create a tunnel using:
source port = IP FROM LOOPBACK ADAPTER:139
destination = 127.0.0.1:139 (this is the localhost on the samba server)
click on the add button then go back to the sessions list & type in the ip of your samba server (mine was 192.168.0.1) give this a name (mine was fwall samba tunnel) click on save then open
login as root or as a user with samba access
5: connect to share
start->run...->\\ipofloopbackadapter\share\on\samba\server

BINGO 

now if this does not kick some life into your samba mess at least you will have access to it.

If you would like to know why i chose to install the loopback adapter on the windows box this is because i did not want to stop the share service on my winxp box & i did not want to change any thing that was already configured.

Hope this helps you all

---

