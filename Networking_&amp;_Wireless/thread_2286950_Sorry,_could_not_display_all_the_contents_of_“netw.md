---
title: "Sorry, could not display all the contents of “network:///”: The specified location is"
date: 2015-07-15
forum: Networking &amp; Wireless
---

### Post by cnar on 2015-07-15
I'm running a Win7 machine, “toshiba”, and two Ubuntu 14.04 32 bit "homebuilt" machines, “ubuntu-tv” (running Serviio) and “emach” (running Zoneminder). All three were Samba-sharing nicely when suddenly the two ubuntu machines stopped working with the Samba network.  I have been working on the “emach” trying to get Samba networking back. After about 2 weeks the “ubuntu-tv” machine suddenly started working with the Samba network again - without my making any changes to it!!  But “emach” is still being recalcitrant. Perhaps my tinkering has preventing whatever it was that fixed “ubuntu-tv” from fixing the same problem on “emach.” Ubuntu 14.04 can't see Samba shares and Samba shares can't be seen by other Samba machines. My Android phone using Total Commander works with everything.

Anyway, I have been searching all the Ubuntu sites I could find for a similar problem, making changes that worked for others, all to no avail. I think the logs could pinpoint the problem if I had more knowledge.  Help would be appreciated at this point.

Using Gnome Commander I get  [Failed to browse the network. Is the SMB module installed?].

Using Nautilus 3.10.1, when I try “Browse Network” I get the message [Sorry, could not display all the contents of “network:///”: The specified location is not supported.] If I try “Connect to Server” the Connect button remains grayed out. The Samba Server Configuration GUI keeps changing my workgroup to lowercase, I have to edit smb.conf manually to change it to uppercase. Remmina Remote Desktop works fine between the two Ubuntu machines. “Readyshare” is a USB drive on the router.

New wrinkle: As I copy the log files I am suddenly getting log files by name AND by IP Address for the same machine and time, but the logs are different.

:mad: :confused: 32 hours later: I can now see the emach from toshiba, but not the reverse. Still get the same message. I took no action during this period, we went shopping.

My smb.conf

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
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
	server string = %h emach server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

           # netbios name of this conputer must be less than 15 characters in length
	netbios name = Ubuntu_eMach
	name resolve order = bcast host lmhosts wins

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

security = user

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
	log level = 3

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

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
	server role = standalone server
;	domain master = yes
;	local master = yes
;	os level = 32

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

	obey pam restrictions = yes

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

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
	map to guest = bad user

########## Domains ###########

#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#

# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
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

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	security = user
;	encrypt passwords = yes
	guest ok = yes
	guest account = bill
	username map = /etc/samba/smbusers

# Added to let share windows files
	usershare owner only = false

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
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
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
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

[bill]
	path = /home/bill
	writeable = yes
	browseable = yes
	guest ok = yes

[Bill win emach]
	path = /mnt/6C29ADD03A9D1070/Users/Bill
	writeable = yes
	browseable = yes
	guest ok = yes
```

Testparm has no significant errors:

```
bill@bill-EMach-Ubuntu:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[bill]"
Processing section "[Bill win emach]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	netbios name = UBUNTU_EMACH
	server string = %h emach server (Samba, Ubuntu)
	server role = standalone server
	map to guest = Bad User
	obey pam restrictions = Yes
	guest account = bill
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = bcast, host, lmhosts, wins
	dns proxy = No
	usershare allow guests = Yes
	usershare owner only = No
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

[bill]
	path = /home/bill
	read only = No

[Bill win emach]
	path = /mnt/6C29ADD03A9D1070/Users/Bill
	read only = No
bill@bill-EMach-Ubuntu:~$ 
```

smbtree is a mystery to me. It looks like access to gencache.tdb is necessary, but what permissions are correct, for who, and how did they get messed up?

```
bill@bill-EMach-Ubuntu:~$ smbtree
added interface eth1 ip=192.168.1.26 bcast=192.168.1.255 netmask=255.255.255.0
Enter bill's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.1 ( 192.168.1.1 )
Connecting to 192.168.1.1 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.1 ( 192.168.1.1 )
Connecting to 192.168.1.1 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\UBUNTU_EMACH   		bill-EMach-Ubuntu emach server (Samba, Ubu
name_resolve_bcast: Attempting broadcast lookup for name UBUNTU_EMACH<0x20>
Got a positive name query response from 192.168.1.26 ( 192.168.1.26 )
Connecting to 192.168.1.26 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\UBUNTU_EMACH\billHome       	
		\\UBUNTU_EMACH\BillWindowsDrive	
		\\UBUNTU_EMACH\Canon_MX920_series	Canon MX920 series
		\\UBUNTU_EMACH\bill           	
		\\UBUNTU_EMACH\Bill win emach 	
		\\UBUNTU_EMACH\IPC$           	IPC Service (bill-EMach-Ubuntu emach server (Samba, Ubuntu))
	\\UBUNTU-TV      		Ubuntu-TV server (Samba, Ubuntu)
name_resolve_bcast: Attempting broadcast lookup for name UBUNTU-TV<0x20>
Got a positive name query response from 192.168.1.10 ( 192.168.1.10 )
Connecting to 192.168.1.10 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\UBUNTU-TV\videos         	
		\\UBUNTU-TV\Canon-MX920-series	Canon MX920 series
		\\UBUNTU-TV\2tb-tv         	
		\\UBUNTU-TV\bill           	
		\\UBUNTU-TV\IPC$           	IPC Service (Ubuntu-TV server (Samba, Ubuntu))
	\\TOSHIBA        		
name_resolve_bcast: Attempting broadcast lookup for name TOSHIBA<0x20>
Got a positive name query response from 192.168.1.5 ( 192.168.1.5 )
Connecting to 192.168.1.5 at port 445
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\TOSHIBA\Warez Downloads	
		\\TOSHIBA\Videos         	
		\\TOSHIBA\Users          	
		\\TOSHIBA\print$         	Printer Drivers
		\\TOSHIBA\IPC$           	Remote IPC
		\\TOSHIBA\Downloads      	
		\\TOSHIBA\Canon MX920 FAX WS	Canon MX920 series FAX WS
	\\READYSHARE     		readyshare
name_resolve_bcast: Attempting broadcast lookup for name READYSHARE<0x20>
Got a positive name query response from 192.168.1.1 ( 192.168.1.1 )
Connecting to 192.168.1.1 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\READYSHARE\ADMIN$         	IPC Service (readyshare)
		\\READYSHARE\IPC$           	IPC Service (readyshare)
		\\READYSHARE\USB_Storage    	read:all-no password;write:all-no password
bill@bill-EMach-Ubuntu:~$ 
```

smbclient looks ok to me.

```
bill@bill-EMach-Ubuntu:~$ smbclient -L 192.168.1.26
Enter bill's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Sharename       Type      Comment
	++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++       ++++++++++++++++++++++++++++++++++++-      ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++-
	bill            Disk      
	Bill win emach  Disk      
	IPC$            IPC       IPC Service (bill-EMach-Ubuntu emach server (Samba, Ubuntu))
	Canon_MX920_series Printer   Canon MX920 series
	BillWindowsDrive Disk      
	billHome        Disk      
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Server               Comment
	++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++            ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++-
	READYSHARE           readyshare
	UBUNTU_EMACH         bill-EMach-Ubuntu emach server (Samba, Ubuntu)

	Workgroup            Master
	++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++            ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++-
	WORKGROUP            READYSHARE
bill@bill-EMach-Ubuntu:~$ 
```

Now the log for emach, wish I knew if anything is wrong.
log.192.168.1.26      (emach)

```
[2015/07/13 14:43:39.540390,  3] ../source3/smbd/sesssetup.c:815(reply_sesssetup_and_X)
  Domain=[]  NativeOS=[Unix] NativeLanMan=[Samba] PrimaryDomain=[null]
[2015/07/13 14:43:39.540414,  3] ../source3/smbd/sesssetup.c:831(reply_sesssetup_and_X)
  sesssetupX:name=[]\[]@[ubuntu_emach]
[2015/07/13 14:43:39.548163,  3] ../source3/lib/access.c:338(allow_access)
  Allowed connection from 192.168.1.26 (192.168.1.26)
[2015/07/13 14:43:39.548597,  3] ../source3/smbd/oplock.c:870(init_oplocks)
  init_oplocks: initializing messages.
[2015/07/13 14:43:39.548919,  3] ../source3/smbd/process.c:1795(process_smb)
  Transaction 0 of length 72 (0 toread)
[2015/07/13 14:43:39.549126,  2] ../source3/smbd/reply.c:592(reply_special)
  netbios connect: name1=192.168.1.26   0x20 name2=UBUNTU_EMACH   0x0
[2015/07/13 14:43:39.549315,  2] ../source3/smbd/reply.c:633(reply_special)
  netbios connect: local=192.168.1.26 remote=ubuntu_emach, name type = 0
[2015/07/13 14:43:52.405926,  3] ../source3/lib/access.c:338(allow_access)
  Allowed connection from 192.168.1.26 (192.168.1.26)
[2015/07/13 14:43:52.406216,  3] ../source3/smbd/oplock.c:870(init_oplocks)
  init_oplocks: initializing messages.
[2015/07/13 14:43:52.406430,  3] ../source3/smbd/process.c:1795(process_smb)
  Transaction 0 of length 194 (0 toread)
[2015/07/13 14:43:52.406518,  3] ../source3/smbd/process.c:1398(switch_message)
  switch message SMBnegprot (pid 13173) conn 0x0
[2015/07/13 14:43:52.407358,  3] ../source3/smbd/negprot.c:563(reply_negprot)
  Requested protocol [PC NETWORK PROGRAM 1.0]
[2015/07/13 14:43:52.407425,  3] ../source3/smbd/negprot.c:563(reply_negprot)
  Requested protocol [MICROSOFT NETWORKS 1.03]
[2015/07/13 14:43:52.407473,  3] ../source3/smbd/negprot.c:563(reply_negprot)
  Requested protocol [MICROSOFT NETWORKS 3.0]
[2015/07/13 14:43:52.407519,  3] ../source3/smbd/negprot.c:563(reply_negprot)
  Requested protocol [LANMAN1.0]
[2015/07/13 14:43:52.407565,  3] ../source3/smbd/negprot.c:563(reply_negprot)
  Requested protocol [LM1.2X002]
[2015/07/13 14:43:52.407610,  3] ../source3/smbd/negprot.c:563(reply_negprot)
  Requested protocol [DOS LANMAN2.1]
[2015/07/13 14:43:52.407655,  3] ../source3/smbd/negprot.c:563(reply_negprot)
  Requested protocol [LANMAN2.1]
[2015/07/13 14:43:52.407700,  3] ../source3/smbd/negprot.c:563(reply_negprot)
  Requested protocol [Samba]
[2015/07/13 14:43:52.407748,  3] ../source3/smbd/negprot.c:563(reply_negprot)
  Requested protocol [NT LANMAN 1.0]
[2015/07/13 14:43:52.407823,  3] ../source3/smbd/negprot.c:563(reply_negprot)
  Requested protocol [NT LM 0.12]
[2015/07/13 14:43:52.410594,  3] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'gssapi_spnego' registered
[2015/07/13 14:43:52.410666,  3] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'gssapi_krb5' registered
[2015/07/13 14:43:52.410714,  3] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'gssapi_krb5_sasl' registered
[2015/07/13 14:43:52.410765,  3] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'schannel' registered
[2015/07/13 14:43:52.410814,  3] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'spnego' registered
[2015/07/13 14:43:52.410863,  3] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'ntlmssp' registered
[2015/07/13 14:43:52.410913,  3] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'krb5' registered
[2015/07/13 14:43:52.410958,  3] ../auth/gensec/gensec_start.c:870(gensec_register)
  GENSEC backend 'fake_gssapi_krb5' registered
[2015/07/13 14:43:52.411381,  3] ../source3/smbd/negprot.c:384(reply_nt1)
  using SPNEGO
[2015/07/13 14:43:52.411431,  3] ../source3/smbd/negprot.c:671(reply_negprot)
  Selected protocol NT LANMAN 1.0
[2015/07/13 14:43:52.412334,  3] ../source3/smbd/process.c:1795(process_smb)
  Transaction 1 of length 172 (0 toread)
[2015/07/13 14:43:52.412507,  3] ../source3/smbd/process.c:1398(switch_message)
  switch message SMBsesssetupX (pid 13173) conn 0x0
[2015/07/13 14:43:52.412604,  3] ../source3/smbd/sesssetup.c:601(reply_sesssetup_and_X)
  wct=12 flg2=0xc843
[2015/07/13 14:43:52.412690,  3] ../source3/smbd/sesssetup.c:138(reply_sesssetup_and_X_spnego)
  Doing spnego session setup
[2015/07/13 14:43:52.412778,  3] ../source3/smbd/sesssetup.c:179(reply_sesssetup_and_X_spnego)
  NativeOS=[Unix] NativeLanMan=[Samba] PrimaryDomain=[]
[2015/07/13 14:43:52.413565,  3] ../auth/ntlmssp/ntlmssp_util.c:34(debug_ntlmssp_flags)
  Got NTLMSSP neg_flags=0x60088215
[2015/07/13 14:43:52.414073,  3] ../source3/smbd/process.c:1795(process_smb)
  Transaction 2 of length 402 (0 toread)
[2015/07/13 14:43:52.414169,  3] ../source3/smbd/process.c:1398(switch_message)
  switch message SMBsesssetupX (pid 13173) conn 0x0
[2015/07/13 14:43:52.414220,  3] ../source3/smbd/sesssetup.c:601(reply_sesssetup_and_X)
  wct=12 flg2=0xc843
[2015/07/13 14:43:52.414253,  3] ../source3/smbd/sesssetup.c:138(reply_sesssetup_and_X_spnego)
  Doing spnego session setup
[2015/07/13 14:43:52.414287,  3] ../source3/smbd/sesssetup.c:179(reply_sesssetup_and_X_spnego)
  NativeOS=[Unix] NativeLanMan=[Samba] PrimaryDomain=[]
[2015/07/13 14:43:52.414354,  3] ../auth/ntlmssp/ntlmssp_server.c:358(ntlmssp_server_preauth)
  Got user=[bill] domain=[WORKGROUP] workstation=[UBUNTU_EMACH] len1=24 len2=146
[2015/07/13 14:43:52.414414,  3] ../source3/param/loadparm.c:4838(lp_load_ex)
  lp_load_ex: refreshing parameters
[2015/07/13 14:43:52.414477,  3] ../source3/param/loadparm.c:750(init_globals)
  Initialising global parameters
[2015/07/13 14:43:52.414582,  3] ../lib/util/params.c:550(pm_process)
  params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
[2015/07/13 14:43:52.414621,  3] ../source3/param/loadparm.c:3564(do_section)
  Processing section "[global]"
[2015/07/13 14:43:52.414803,  2] ../source3/param/loadparm.c:3581(do_section)
  Processing section "[printers]"
[2015/07/13 14:43:52.414890,  2] ../source3/param/loadparm.c:3581(do_section)
  Processing section "[bill]"
[2015/07/13 14:43:52.414959,  2] ../source3/param/loadparm.c:3581(do_section)
  Processing section "[Bill win emach]"
[2015/07/13 14:43:52.415044,  3] ../source3/param/loadparm.c:1773(lp_add_ipc)
  adding IPC service
[2015/07/13 14:43:52.415121,  3] ../source3/auth/user_util.c:404(map_username)
  Mapped user bill to bill
[2015/07/13 14:43:52.415199,  3] ../source3/auth/auth.c:177(auth_check_ntlm_password)
  check_ntlm_password:  Checking password for unmapped user [WORKGROUP]\[bill]@[UBUNTU_EMACH] with the new password interface
[2015/07/13 14:43:52.415242,  3] ../source3/auth/auth.c:180(auth_check_ntlm_password)
  check_ntlm_password:  mapped user is: [UBUNTU_EMACH]\[bill]@[UBUNTU_EMACH]
[2015/07/13 14:43:52.415618,  3] ../source3/passdb/lookup_sid.c:1560(get_primary_group_sid)
  Forcing Primary Group to 'Domain Users' for bill
[2015/07/13 14:43:52.416432,  3] ../source3/auth/auth.c:226(auth_check_ntlm_password)
  check_ntlm_password: sam authentication for user [bill] succeeded
[2015/07/13 14:43:52.421439,  2] ../source3/auth/auth.c:278(auth_check_ntlm_password)
  check_ntlm_password:  authentication for user [bill] -> [bill] -> [bill] succeeded
[2015/07/13 14:43:52.421519,  3] ../auth/ntlmssp/ntlmssp_sign.c:547(ntlmssp_sign_init)
  NTLMSSP Sign/Seal - Initialising with flags:
[2015/07/13 14:43:52.421552,  3] ../auth/ntlmssp/ntlmssp_util.c:34(debug_ntlmssp_flags)
  Got NTLMSSP neg_flags=0x60088215
[2015/07/13 14:43:52.421786,  3] ../source3/passdb/lookup_sid.c:1560(get_primary_group_sid)
  Forcing Primary Group to 'Domain Users' for bill
[2015/07/13 14:43:52.422273,  1] ../source3/param/loadparm.c:2936(lp_idmap_range)
  idmap range not specified for domain '*'
[2015/07/13 14:43:52.422403,  3] ../source3/auth/token_util.c:439(finalize_local_nt_token)
  Failed to fetch domain sid for WORKGROUP
[2015/07/13 14:43:52.422483,  3] ../source3/auth/token_util.c:470(finalize_local_nt_token)
  Failed to fetch domain sid for WORKGROUP
[2015/07/13 14:43:52.422866,  3] ../source3/smbd/password.c:130(register_homes_share)
  Using static (or previously created) service for user 'bill'; path = '/home/bill'
[2015/07/13 14:43:52.433358,  3] ../source3/lib/access.c:338(allow_access)
  Allowed connection from 192.168.1.26 (192.168.1.26)
[2015/07/13 14:43:52.433581,  3] ../source3/smbd/oplock.c:870(init_oplocks)
  init_oplocks: initializing messages.
[2015/07/13 14:43:52.433710,  3] ../source3/smbd/process.c:1795(process_smb)
  Transaction 0 of length 72 (0 toread)
[2015/07/13 14:43:52.433788,  2] ../source3/smbd/reply.c:592(reply_special)
  netbios connect: name1=192.168.1.26   0x20 name2=UBUNTU_EMACH   0x0
[2015/07/13 14:43:52.433846,  2] ../source3/smbd/reply.c:633(reply_special)
  netbios connect: local=192.168.1.26 remote=ubuntu_emach, name type = 0
```

Up to this point I have been successful in getting things solved through his forum and other Ubuntu help sites and documentation, but the way things keep changing with samba mystifies me! Still no outgoing success and probably unreliable for incoming.

I have restarted smbd, nmbd, samba, and occasionally rebooted.

Thanks in advance.


1. If you don't vote you let others choose your leaders.
2. Vote for the person who you can trust to do the right thing for you and the country.
3. If you aren't sure who or what that is, do a lot of research or...
                  ...DON'T VOTE!

---

