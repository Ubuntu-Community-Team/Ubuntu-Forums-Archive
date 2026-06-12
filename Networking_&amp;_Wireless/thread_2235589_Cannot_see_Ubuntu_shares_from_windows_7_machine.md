---
title: "Cannot see Ubuntu shares from windows 7 machine"
date: 2014-07-21
forum: Networking &amp; Wireless
---

### Post by bruce_clymer on 2014-07-21
**Re: Cannot see Ubuntu shares from windows 7 machine…or, map a drive to these shares via ip or name**

**Hi All** – I consider myself a quick study. I don’t mind reading the manual, researching and trying all things technical and am really at a quandary how I’m stumped on this one.  I appreciate your ideas. I thought I’d covered about every article on this subject and read the Samba manual til I’m flummoxed. Lol
 
I have a dual boot xp machine with zorin 8/linux on it and a Win7 home premium machine on my home network.  I expected to connect the w7 to shares on the linux machine with no problem. 
 
I have Samba 3.6.18 on the linux machine. 
 
Net view …shows both windows7 and Ubuntu machines
Workgroup = woodbine …both machines
Ubuntu Share names less than 12 characters (bruce)
Ubuntu computername is less than 15 characters (zorin8)
 
Ping Ubuntu from windows command line fine
Ping Windows from Ubuntu fine
 
I can see the win7 shared folders and access them from the linux machine.
[COLOR=#0000ff]I CANNOT see shares on the linux machine from windows.[/COLOR]
 
I have done smbtree …on the linux and shares show on both machines.
I have verified ports…
 
$ **netstat -an | egrep ':(137|138|139|445)'**
tcp 0 0 *:139 *:* LISTEN
tcp 0 0 *:445 *:* LISTEN
udp 0 0 *:137 *:*
udp 0 0 *:138 *:*
 
I have permissions set to guest access on linux. 
I did try having a user of same name and pw on both machines and tried simplifying from there.
 
**Question…**
 
What is the purpose of smb.conf in both /etc/samba and /usr/share/samba ?…
 
I am assuming they should be the same… and have ensured that they are.
I run testparm after changes and sudo restart smbd ..sudo restart nmbd after changes.
I reboot …just to make sure I didn’t miss something. Lol
 
I am learning a lot of new (to me) linux commands…that’s good. 
 
I have been thru a lot …many times and feel pretty good about being able to say…it’s just the linux shares from win7 that I can’t see.  But HEY! 
 
I appreciate any suggestions on things that can keep win7 from seeing shares on linux…given all this.

Thanks in advance...

---

### Post by QIII on 2014-07-21
Hello!

What file system is used on the directories on your LInux machine you would like to view from the Windows machine?

---

### Post by bab1 on 2014-07-22
> **bruce_clymer said:**
> **Re: Cannot see Ubuntu shares from windows 7 machine…or, map a drive to these shares via ip or name**

**Hi All** – I consider myself a quick study. I don’t mind reading the manual, researching and trying all things technical and am really at a quandary how I’m stumped on this one.  I appreciate your ideas. I thought I’d covered about every article on this subject and read the Samba manual til I’m flummoxed. Lol
 
I have a dual boot xp machine with zorin 8/linux on it and a Win7 home premium machine on my home network.  I expected to connect the w7 to shares on the linux machine with no problem. 
 
I have Samba 3.6.18 on the linux machine. 
 
Net view …shows both windows7 and Ubuntu machines
Workgroup = woodbine …both machines
Ubuntu Share names less than 12 characters (bruce)
Ubuntu computername is less than 15 characters (zorin8)
 
Ping Ubuntu from windows command line fine
Ping Windows from Ubuntu fine
 
I can see the win7 shared folders and access them from the linux machine.
[COLOR=#0000ff]I CANNOT see shares on the linux machine from windows.[/COLOR]
 
I have done smbtree …on the linux and shares show on both machines.
Did you run smbtree with any debug?  I usually use this to debug Samba```
smbtree -d3
``` > 
I have verified ports…
 
$ **netstat -an | egrep ':(137|138|139|445)'**
tcp 0 0 *:139 *:* LISTEN
tcp 0 0 *:445 *:* LISTEN
udp 0 0 *:137 *:*
udp 0 0 *:138 *:*
 
I have permissions set to guest access on linux. 
I did try having a user of same name and pw on both machines and tried simplifying from there.

Each user of the Samba server shares (Ubuntu host) needs to have both an Ubuntu user account (Linux) and a Samba user account (smbpasswd).  If there is no user then Samba will allow anonymous access (some call this a guest) as the user *nobody* with the group set to *nogroup*. 
> 
 
**Question…**
 
What is the purpose of smb.conf in both /etc/samba and /usr/share/samba ?…

The  smb.conf file at /usr/share/samba is a reference copy.  A backup if needed.  It should be left as it was originally (default).
> 
 
I am assuming they should be the same… and have ensured that they are.
Oooooooops!  Revert it back to the default.  You do have an unmolested original copy of smb.conf; right? > 
I run testparm after changes and sudo restart smbd ..sudo restart nmbd after changes.
I reboot …just to make sure I didn’t miss something. Lol
 
I am learning a lot of new (to me) linux commands…that’s good. 
 
I have been thru a lot …many times and feel pretty good about being able to say…it’s just the linux shares from win7 that I can’t see.  But HEY! 
 
I appreciate any suggestions on things that can keep win7 from seeing shares on linux…given all this.

Thanks in advance...
Can you see the shares from the file manager (browser) using smb://ip_address/share-name ???  if you can then the problem can be fixed by configuring the NETBIOS NAME service.

FWIW:  Linux is case sensitive, but Windows is case IN-sensitve.  Windows ether uses or converts these namespace names to CAPS.  Linux on the other hand sees these as two differing names: NAME :: name.  I always name objects with Linux naming in mind.  Mostly I use lowercase as that is the unix/linux convention.  If it is a name that is to be displayed (e.g a description of an object) I use first letter caps like this: Samba Server or Public Share).  You can use any set of letters for the share name as it the browser will accept any combination.  Public or puBlic or PUBLIC are the same when it comes to share names.  Finally, you don't really need to use the same WORKGROUP name.  Network Neighborhood in Windows will see both and using Linux you have to look under "Windows Network" to see all the different WORKGROUPS.  For a small network it's most likely easier to have all the shares one WORKGROUP however.

---

### Post by bab1 on 2014-07-22
> **QIII said:**
> Hello!

What file system is used on the directories on your LInux machine you would like to view from the Windows machine?

I believe that you will find that the formatting of the *remote * partition is not relevant.  The **remote file system** is what is mounted via CIFS to the ***local * file system**.  The system mounts file systems not partitions.  CIFS understands how to translate EXT to NTFS and visa versa.

---

### Post by bruce_clymer on 2014-07-22
> **QIII said:**
> Hello!

What file system is used on the directories on your LInux machine you would like to view from the Windows machine?

File system is Ext4...on the Linux machine

---

### Post by bruce_clymer on 2014-07-22
Thanks for your comments... 

I reverted my /usr/share/samba ..smb.conf file ...actually I just renamed it smb.conf.master to get it out of the way. 
Somewhere along my journey I read something about keeping this file the same as smb.conf in /etc/samba ...
That never made a lot of sense to me...and as I continued to read more in the samba manual, etc., I never got another confirmation of WHY I needed the addt'l smb.conf file in /usr/share/samba.  **[COLOR=#0000ff]Bottomline:  What you're saying makes sense... That file is out of the way now.  Thanks...[/COLOR]**

on the smb://ip_address/share-name... Yes early on I configured the netbios name service with the hostname and on win7 added zorin8 *.*.*.* reference in the hosts file.  That got me the ability to ping by name on both machines successfully.  

I try mapping a drive by the ip addr now....just to see if I can see shares by the ip... NO luck though. 
The name service works fine... I can ping by name both ways; win7 to zorin8 and vice versa.  

This is the result of testparm on smb.conf in the /etc/samaba directory... 

[global]
	workgroup = WOODBINE
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	username map = /etc/samba/smbusers
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = wins bcast
	wins support = Yes
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb
	guest ok = Yes


[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[bruce]
	comment = home dir on zorin
	path = /home/bruce
	read only = No
	create mask = 0755

The share [bruce] is the share I'm hoping to see from Windows7 eventually...  
I cannot see any smb share from windows7... 
I can however ping both the machine name and ip addr successfully from windows7 and I can NETVIEW \\zorin8 (the linux) from my windows7 machine. 

very strange... lol

---

### Post by bab1 on 2014-07-22
> **bruce_clymer said:**
> Thanks for your comments... 

I reverted my /usr/share/samba ..smb.conf file ...actually I just renamed it smb.conf.master to get it out of the way. 
Somewhere along my journey I read something about keeping this file the same as smb.conf in /etc/samba ...
That never made a lot of sense to me...and as I continued to read more in the samba manual, etc., I never got another confirmation of WHY I needed the addt'l smb.conf file in /usr/share/samba.  **[COLOR=#0000ff]Bottomline:  What you're saying makes sense... That file is out of the way now.  Thanks...[/COLOR]**

on the smb://ip_address/share-name... Yes early on I configured the netbios name service with the hostname and on win7 added zorin8 *.*.*.* reference in the hosts file.  That got me the ability to ping by name on both machines successfully.  

I try mapping a drive by the ip addr now....just to see if I can see shares by the ip... NO luck though. 
The name service works fine... I can ping by name both ways; win7 to zorin8 and vice versa.  

This is the result of testparm on smb.conf in the /etc/samaba directory... 

```
[global]
	workgroup = WOODBINE
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	username map = /etc/samba/smbusers
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = wins bcast
	wins support = Yes
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb
	guest ok = Yes


[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[bruce]
	comment = home dir on zorin
	path = /home/bruce
	read only = No
	create mask = 0755
```

The share [bruce] is the share I'm hoping to see from Windows7 eventually...  
I cannot see any smb share from windows7... 
I can however ping both the machine name and ip addr successfully from windows7 and I can NETVIEW \\zorin8 (the linux) from my windows7 machine. 

very strange... lol
Ping is a **not** good test of NETBIOS name services.  In fact ping knows nothing of NETBIOS.  Testparm does **not** tell whether you have configured your server completely correctly either.  It only shows misconfigured parameters.

When you post output from terminal commands you should place it inside of ```
 blocks.  See how I have done that above in this reply.  To do this you click on the [SIZE=5]**#**[/SIZE]  icon at the top of the advanced editor and place the text between the opening and closing [code] blocks.

Post the output of these 2 commands[CODE]cat /etc/samba/smb.conf 
```...the entire smb.conf file.  
```
smbtree -d3 
```...the results of a NETBIOS scan of the shares with debug information.

What are the IP addresses and hostnames of the 2 hosts (computers)?

---

### Post by bruce_clymer on 2014-07-22
Thanks for your help... 

Below is the result for ... [COLOR=#0000ff]cat /etc/samba/smb.conf [/COLOR]

```


[global]

## Browsing/Identification ###


	workgroup = woodbine
	server string = %h server (Samba, Ubuntu)
	wins support = yes


# This will prevent nmbd to search for NetBIOS names through DNS.
;	dns proxy = no


	netbios name = zorin8
	name resolve order = wins bcast


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
;   bind interfaces only = yes






#### Debugging/Accounting ####


# This tells Samba to use a separate log file for each machine
# that connects


	log file = /var/log/samba/log.%m


# Cap the size of the individual log files (in KiB).


	max log size = 1000


# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no


# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.


	syslog = 0


# Do something sensible when Samba crashes: mail the admin a backtrace


	panic action = /usr/share/samba/panic-action %d


####### Authentication #######


	security = user


# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes


# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam


;	obey pam restrictions = yes


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
#	unix password sync = yes


# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
#	passwd program = /usr/bin/passwd %u
#	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
#	pam password change = yes


# This option controls how unsuccessful authentication attempts are mapped
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
# (this is Samba's default)
#   logon path = \\%N\%U\profile


# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U


# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd


# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u


# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u


# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g


########## Printing ##########


# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes


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
#   socket options = TCP_NODELAY


# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &


# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto


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
	guest ok = yes
;	guest account = nobody


#======================= Share Definitions =======================


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
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
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S


# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)


;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes


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
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin


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


[bruce]
	path = /home/bruce
	writeable = yes
;	browseable = yes
	comment = home dir on zorin
	guest ok = yes
	create mask = 0755



```

Below is the result for ... [COLOR=#0000ff]smbtree -d3[/COLOR]

```

bruce@zorin8:/usr/share/samba$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::212:3fff:fe70:12d6%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.9 bcast=192.168.1.255 netmask=255.255.255.0
Enter bruce's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WOODBINE<0x1d>
Got a positive name query response from 192.168.1.6 ( 169.254.234.34 192.168.1.6 )
Connecting to host=192.168.1.6
Connecting to 192.168.1.6 at port 445
Doing spnego session setup (blob length=293)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.6 ( 169.254.234.34 192.168.1.6 )
name_resolve_bcast: Attempting broadcast lookup for name WOODBINE<0x1d>
Got a positive name query response from 192.168.1.6 ( 169.254.234.34 192.168.1.6 )
Connecting to host=192.168.1.6
Connecting to 192.168.1.6 at port 445
Doing spnego session setup (blob length=293)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WOODBINE
name_resolve_bcast: Attempting broadcast lookup for name WOODBINE<0x1d>
Got a positive name query response from 192.168.1.6 ( 169.254.234.34 192.168.1.6 )
Connecting to host=192.168.1.6
Connecting to 192.168.1.6 at port 445
Doing spnego session setup (blob length=293)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\ZORIN8         		zorin8 server (Samba, Ubuntu)
Connecting to host=ZORIN8
resolve_wins: Attempting wins lookup for name ZORIN8<0x20>
resolve_wins: using WINS server 127.0.0.1 and tag '*'
Got a positive name query response from 127.0.0.1 ( 192.168.1.9 )
Connecting to 192.168.1.9 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\ZORIN8\EpsonNX110     	Epson 9-Pin
		\\ZORIN8\print$         	Printer Drivers
		\\ZORIN8\bruce          	home dir on zorin
		\\ZORIN8\IPC$           	IPC Service (zorin8 server (Samba, Ubuntu))
	\\SIRIUS         		ASUS QuadCore
Connecting to host=SIRIUS
resolve_wins: Attempting wins lookup for name SIRIUS<0x20>
resolve_wins: using WINS server 127.0.0.1 and tag '*'
Negative name query response, rcode 0x03: The name requested does not exist.
name_resolve_bcast: Attempting broadcast lookup for name SIRIUS<0x20>
Got a positive name query response from 192.168.1.6 ( 169.254.234.34 192.168.1.6 )
Connecting to 192.168.1.6 at port 445
Doing spnego session setup (blob length=293)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\SIRIUS\Users          	
		\\SIRIUS\print$         	Printer Drivers
		\\SIRIUS\IPC$           	Remote IPC
		\\SIRIUS\EPSON NX110 Series	EPSON NX110 Series
		\\SIRIUS\D$             	Default share
		\\SIRIUS\C$             	Default share
		\\SIRIUS\ADMIN$         	Remote Admin



```

hostnames win7 and linux below...
sirius 192.168.1.6    zorin8 192.168.1.9

I appreciate your help...
Bruce

---

### Post by Bucky Ball on 2014-07-23
*Thread moved to **Networking & Wireless**.*

---

### Post by bab1 on 2014-07-25
> **bruce_clymer said:**
> Thanks for your help... 

Below is the result for ... [COLOR=#0000ff]cat /etc/samba/smb.conf [/COLOR]

```


[global]
## Browsing/Identification ###

	workgroup = woodbine
	server string = %h server (Samba, Ubuntu)
[COLOR="#FF0000"]	wins support = yes
[/COLOR]


	netbios name = zorin8
	name resolve order = [COLOR="#FF0000"]wins[/COLOR] bcast

...


#======================= Share Definitions =======================

[COLOR="#006400"][B]# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
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
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S

[/B][/COLOR]

...

[COLOR="#800080"][bruce]
	path = /home/bruce
	writeable = yes
;	browseable = yes
	comment = home dir on zorin
	guest ok = yes
	create mask = 0755
[/COLOR]


```

Comment out the references to wins (red above) and delete it from the *name resolve order *line.  Bcast is all you need anyway.

You do not need to create your own home directory share (purple above).  The home directory share you should use is the [homes] directory (green above) it only needs to be set up once and any user that logs in will be able to access ONLY his/her home directory with this: //severname/login_name. 
> 

Below is the result for ... [COLOR=#0000ff]smbtree -d3[/COLOR]

```

bruce@zorin8:/usr/share/samba$ smbtree -d3
lp_load_ex: refreshing parameters


...



name_resolve_bcast: Attempting broadcast lookup for name WOODBINE<0x1d>
Got a positive name query response from 192.168.1.6 ( 169.254.234.34 192.168.1.6 )
[COLOR="#0000ff"]*** bcast working ***[/COLOR]

...
resolve_wins: Attempting wins lookup for name SIRIUS<0x20>
resolve_wins: using WINS server 127.0.0.1 and tag '*'
Negative name query response, rcode 0x03: The name requested does not exist.
[COLOR="#FF0000"]*** wins NOT working ***[/COLOR]

```


---

### Post by gordintoronto on 2014-07-25
On average, I try about one Linux distro or version a month. I always set up a shared folder, and it always works. I have never used the command line (except with Ubuntu Server, no GUI) and I have never edited smb.conf, except in Ubuntu Server.

In Nautilus, for example, I right-click a folder and select "Sharing Options."  I click "Share this Folder" I give it a name. I click "Allow other..." and "Guest access..." then "Create Share." Reboot. All done.

One trick: I use the same username and password on all my computers.

---

### Post by bruce_clymer on 2014-07-26
Thanks gordintoronto....  Thanks for the response...  Totally agree on having same usernames/passwords on both machines. I've tried several linux versions in VirtualBox and thought I was being cool by using Zorin on an old XP machine; takes less resources, read a couple articles on it being a perfect replacement for XP, etc.   ...and I'm sure it is.  I just got myself in one of those sticky-wickets that I refuse to give up without finding the answer.  lol   I always figure I'll learn something.  ...and I usually do but this one seems so simple in its ultimate goal, yet it just keeps on evading resolution. 

I may bite the bullet and revert to a version that is more gui and user friendly.  ...I'm close to a solution... I think.  
I'm gonna make one more shot at it today... got wins working and looking like I may have an issue on windows port 139. I will do another round and post another version of smbtree -d3 and see if I can find the problem.  

Then, it's back to GUI...

---

