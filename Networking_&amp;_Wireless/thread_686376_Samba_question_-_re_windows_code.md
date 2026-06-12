---
title: "Samba question - re windows code"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by Znort_Ubern00b on 2008-02-03
I'm having real problems getting samba to work between my ubuntu and xp pc's. Have read somewhere that samba team now have the code from windoze. when will the new version be out??

have followed different guides to get it to work, even just looked at the how to geek guide which seemed simple enough, but still didn't work...i am still fairly new to all this so maybe i'm doing it completely wrong. would love a complete step by step how to if anyone has one.

---

### Post by njparton on 2008-02-03
I use samba to share between vista, xp and ubuntu - it's fine.

Post your smb.conf file here so we can see what you're trying to do.

Also be aware that each xp user trying to access shared files needs to both have an ubuntu account and a samba password.

There are loads of samba how to's out there including in this forum please search for them.

---

### Post by Znort_Ubern00b on 2008-02-03
#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
wins support = no
[homes]
   comment = Home Directories
   browseable = no

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


[shared]
path = /home/shared
available = yes
browsable = yes
public = yes
writable = no


i only want to share that folder with the other pc it has all mp3s etc in it.

---

### Post by njparton on 2008-02-03
The changes I would suggest are below in bold

#======================= Share Definitions =======================
[B][global]
workgroup = MSHOME  #change as relevant
security = user
encrypt passwords = true[/B]

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
wins support = no
[homes]
comment = Home Directories
browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
; valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
; writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
; create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
**directory mask = 0550**

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
; comment = Network Logon Service
; path = /home/samba/netlogon
; guest ok = yes
; writable = no
; share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
; comment = Users profiles
; path = /home/samba/profiles
; guest ok = no
; browseable = no
; create mask = 0600
; directory mask = 0700

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
; write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
; comment = Samba server's CD-ROM
; writable = no
; locking = no
; path = /cdrom
; public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
# cdrom share is accesed. For this to work /etc/fstab must contain
# an entry like this:
#
# /dev/scd0 /cdrom iso9660 defaults,noauto,ro,user 0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
# is mounted on /cdrom
#
; preexec = /bin/mount /cdrom
; postexec = /bin/umount /cdrom


[shared]
path = /home/shared
available = yes
browsable = yes
public = yes
writable = no
**valid users = bill,bob,tracey  #add relevant users here for belt and braces approach**
**hosts allow = 192.168.1.10 192.168.1.11  #add client IP addresses here again for belt and braces and for extra security**

_____

can you also confirm that you've set up a samba password for all relevant users via "smbpasswd"?

---

### Post by swerdna on 2008-02-03
I hope that you all take this as constructive criticism. The suggested changes are good as far as they go, but htey don't get to the nub of the problm, which is adequate name resolution. 

The 'valid users' and 'hosts allow' are security tools that limit who can access the share. They don't improve network resolution.

I endorse this change to [global] because it allows to synch to windows netbios names:
workgroup = whatever_windows_is_using

To use 'security = share' is inconsistent with using smbpasswd and 'valid users', it's deprecated and a relic from win95/98/me. You should leave it out in which case the default security, security = user, will operate. That's consistent with the share security changes suggested by njparton for [shared].

The mask 550 makes the share writeable only to owner, which is consistent with the existing definition in [shared].

All very fine but may I suggest these two extra lines in [global] which are useful for making the share visible on the network:
netbios name = name_by_which_you_want_server_known_on_network
name resolve order = bcast lmhosts wins host

Then restart Samba after the chages with **sudo /etc/init.d/samba restart**. That might take 5/10 mins to seep around the LAN. I ususally get frustrated and restart all machines in the lan in sequence but that's not vital.

Hope that all helps along with njparton's, including the important **smbpasswd -a username/s**

Swerdna

---

### Post by Znort_Ubern00b on 2008-02-05
Ok, have added those lines to my smb.conf file.

when adding users do i use there xp or ubuntu login details??? do they have to be exactly the same?

All users have both an ubuntu and xp login(which are different) what i want to do is share all the music etc files on ubuntu pc with the xp machine.

---

### Post by swerdna on 2008-02-05
> **Znort_Ubern00b said:**
> Ok, have added those lines to my smb.conf file.

when adding users do i use there xp or ubuntu login details??? do they have to be exactly the same?

All users have both an ubuntu and xp login(which are different) what i want to do is share all the music etc files on ubuntu pc with the xp machine.

The owner of the folder /home/shared change to a legitimate normal user, e.g. your_name
Then add your name to the samba user database. Then from windows, supply the ubuntu user name and password when challenged.

In fact edit the share to be like this and you should get access for everyone.
```
[shared]
path = /home/shared
guest ok = yes
read only = no
force user = your_name
```
And make the permissions on the folder "shared" to equal drwxrwxrwx and user/group = your_name/your_name

---

### Post by Znort_Ubern00b on 2008-02-05
ok i get most of that the only bit i dont know how to do is the drwxrwxrwx bit...what do i write in terminal to arrange that???

---

### Post by jonallport on 2008-02-05
Run testparm, looks like browseable is spelled wrong to me, default would be =no

---

### Post by swerdna on 2008-02-05
> **Znort_Ubern00b said:**
> ok i get most of that the only bit i dont know how to do is the drwxrwxrwx bit...what do i write in terminal to arrange that???
This in a terminal to make it drwxrwxrwx: **sudo chmod 777 /home/shared** and if you need to change to yourself as owner do **sudo chown your_linux_name:your_linux_name /home/shared**

You can also/alternatively get at the owner and permissions with superuser version of Nautilus and a R-click on the folder 'shared' --> select 'properties'. To start superuser Nautilus do this command: **sudo nautilus**

Swerdna

---

### Post by Znort_Ubern00b on 2008-02-05
#======================= Global Settings =======================

[global]
netbios name = **My_PC**


## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

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
   security = user

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
wins support = yes
[homes]
   comment = Home Directories
   browseable = no

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
;   directory mask = 0550

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


[shared]
path = /home/video
guest ok = yes
read only = no
force user = video


ok so i set up an account called video...transferred files to that folder added user with sudo smbpasswd -a
 did restart of samba

went to windows pc logged on and went to map network drive typed in \\My_PC\video

xp machine tells me it can't find it


really sorry to be a pain...any ideas???

---

### Post by swerdna on 2008-02-05
OK here are a few last things. I ran this terminal command: **testparm /etc/samba/smb.conf**
That does a rough check of the smb.conf file for gross errors (not for all errors) and it also parses it to be the way Samba sees the result after it cuts out all the spurious stuff. It is handy to remember because it gives you clarity/focus. Here's the result-- what Samba sees:
> [global]
	workgroup = MSHOME
	netbios name = MY_PC
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = lmhosts host wins bcast
	dns proxy = No
	wins support = Yes
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[homes]
	comment = Home Directories
	browseable = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[shared]
	path = /home/video
	force user = video
	read only = No
	guest ok = Yes

The default smb.conf supplied in Ubuntu is truly problematic when it comes to the home LAN.
Edit the file with **sudo gedit /etc/samba/smb.conf** and change these lines to be like this:
#	obey pam restrictions = Yes
#	passwd program = /usr/bin/passwd %u
#	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
That comments them out (,akes them effectively not there)

Important: You might have set up windows to speak to a Linux wins server. If so then UNDO THAT. If not then don't stress about that. Wins servers ARE NOT for new Samba users.
Change this: **wins support = yes** to this: **#      wins support = no**

This won't work unless you edit name and IP address pairs into the file /etc/samba/lmhosts:
	**name resolve order = lmhosts host wins bcast**
New users don't do that so change it to this:
	**name resolve order = bcast host wins lmhosts**

FYI: interesting that Samba sees My_PC as MY_PC. So does windows.

Check that user video got into Samba password database, run this and look for the name video: **sudo pdbedt -L**

> Then restart Samba after the chages with sudo /etc/init.d/samba restart. That might take 5/10 mins to seep around the LAN. I ususally get frustrated and restart all machines in the lan in sequence but that's not vital.

Gluck
Swerdna

---

### Post by Znort_Ubern00b on 2008-02-06
The My_PC is not real name it is actually **NothingAsCertainAs**

will attempt to do this when I get home, at wor at the moment, thank you so much for all your help. fingers crossed it works.

---

### Post by Znort_Ubern00b on 2008-02-06
Ok so I have done those changes...although wins support still says yes

Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[shared]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        passdb backend = tdbsam
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = bcast host wins lmhosts
        dns proxy = No
        wins support = Yes
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

what do i need to do on xp machine now to get share???

---

### Post by swerdna on 2008-02-06
> **Znort_Ubern00b said:**
> Ok so I have done those changes...although wins support still says yes

Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[shared]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        passdb backend = tdbsam
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = bcast host wins lmhosts
        dns proxy = No
        wins support = Yes
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

what do i need to do on xp machine now to get share???
Before the xp machine you need to edit the smb.conf file again.
I'm assuming that you haven't installed a wins server on the LAN. [COLOR="Blue"]Tell me if I am wrong about tha[/COLOR]t.
OK with the comand **sudo gedit /etc/samba/smb.conf** you get the file open again for editing.
Change this: **wins server = yes** to this **#wins server = no**. And add the line **netbios name = NothingAsCertainAs** in the [global] section.

Then run testparm again and it should look like this at the top:


> [global]
        workgroup = MSHOME
        netbios name = NOTHINGASCERTAINAS
        server string = %h server (Samba, Ubuntu)
        passdb backend = tdbsam
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = bcast host wins lmhosts
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

Reboot everything. Turn off all firewalls (until you get it working)  to keep things uncomplicated.

Then in xp network browser if you see the icon in the network browser then click/drill down to the share. If don't see icon then enter this address in the network browser: **\\nothingascertainas\shared**. It might take 5 for this to work first time.

I'm assuming in windows that you haven't adjusted the networking parameters that are located at Control Panel --> Classic View --> Network Connections --> LAN --> R-click --> Properties --> Inetrnet protocol --> Properties. That most likely will be Obtain IP automatically and then Advanced Tab will have more tabs for which WINS tab has nothing in "WINS addresses" box. [COLOR="Blue"]Is that right?[/COLOR]

Swerdna

---

