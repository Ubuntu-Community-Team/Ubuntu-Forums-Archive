---
title: "Samba/Browse Network Computers...paging Babs1!"
date: 2013-11-08
forum: Networking &amp; Wireless
---

### Post by Hedon James on 2013-11-08
Per our discussion, I'm posting this on the forum.  Hopefully, this will help someone else with similar issues?!  :)  Copy & paste of our previous PM is as follows:

  	 	 	 	   > **bab1]I don't know about appropriateness, but I do like to pass this type of info on to others. If I did all the diagnosis via PM then you would have and nothing to follow in the first place. If we can solve this quickly and there is nothing interesting to enlighten the masses then okay. If it gets out of hand I'll advise you to post on the forum. Fair enough? 

Post back here (via PM) the output of```
smbtree -d3
```...this turns on a moderate amount of debug info.

> jim@Asus:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:razz:m_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::12bf:48ff:fe78:4797%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.37 bcast=192.168.1.255 netmask=255.255.255.0
Enter jim's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.33 ( 192.168.1.33 )
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.33 ( 192.168.1.33 )
Connecting to host=192.168.1.33
Connecting to 192.168.1.33 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
MSHOME
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.33 ( 192.168.1.33 )
Connecting to host=192.168.1.33
Connecting to 192.168.1.33 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
\\HP101F745E29B8 
Connecting to host=HP101F745E29B8
name_resolve_bcast: Attempting broadcast lookup for name HP101F745E29B8<0x20>
cli_start_connection: failed to connect to HP101F745E29B8<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
\\DF7TB761 Studio
Connecting to host=DF7TB761
name_resolve_bcast: Attempting broadcast lookup for name DF7TB761<0x20>
Got a positive name query response from 192.168.1.33 ( 192.168.1.33 )
Connecting to 192.168.1.33 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
\\DF7TB761\Printer hp deskjet 845c
\\DF7TB761\print$ Printer Drivers
\\DF7TB761\IPC$ Remote IPC
\\DF7TB761\My Documents 

I can tell you right now, one of your problems is *name services*. Most folks don't understand this and so they use the IP address instead of this format: //NETBIOS_NAME/share_name, What do you get with this```
smb://IP_ADDRESS/share_name
```

> I don't typically access server locations with //IP_ADDRESS/ conventions, but rather with Netbios names. However, utilizing your conventions from the terminal, here is the output of your request, as well as my typical access method (note that Asus is my main machine, which in this case would be both client and server to itself):

jim@Asus:~$ smb://192.168.1.37/'Asus Home'
bash: smb://192.168.1.37/Asus Home: No such file or directory
jim@Asus:~$ smb://Asus/
bash: smb://Asus/: No such file or directory

I also ran this from the terminal without the quotation marks, in order to determine if my syntax was wrong, but same result was given.

Alternatively, searching for the server within nautilus/browse network shows the Windows Network icon, but typically yields the "unable to mount location..." message. However, TODAY, in order to account for all variables, I have turned on my WinXP machine (which is the ONLY machine in MSHOME workgroup), which is a dedicated DAW recording station for music. MSHOME shows up in the Windows Network group, as well as the computer name 'Studio', but WORKGROUP does not, nor any of the computers in the WORKGROUP, which is where ALL my linux machines and/or Win7 virtual machines reside.

Finally, clicking Go>Location within nautilus, and entering the SAME information (smb://Asus/) shows EXACTLY what I'm looking for...the shared Home Directory of Asus, as well as shared printer folder. If I didn't have 9 machines on my home network, I'd just use this method as a workaround said:**
> 

...if you don't get anything at all, you might check to see if the Samba daemon is really up (working).

To see if Samba is really running you can do this```
pgrep -l  mbd
```...that's a lowercase "ell".

[QUOTE]jim@Asus:~$ pgrep -l mbd
2700 smbd
2702 smbd
2720 nmbd
3693 smbd
4088 smbd
4127 smbd

All of this is to test the server. I assume that you know which tests are from the server command line and which you can test from an Ubuntu client. I don't have any Windows or Mac machines so all of my tests are via a Linux host.

If you want you can post the "current" smb.conf file. By default I assume you mean the one that is provided when you first install. I know what is in that one.  :wink:

[QUOTE]By default, I do indeed mean the "virgin" config file. I only mention that I have it in the event my current config is so bastardized that it's easier to restore the virgin file and move from there. I'm sending my CURRENT "smb.conf" file via separate correspondence, as I can't figure out how to attach file, and including here makes the text too long to send.


I'm warning you now that you might have multiple problems and not all of them will be directly Samba related. 

One last thing. Describe what you use for name services for your hosts in the LAN. For example all of my hosts are named after beaches here in California. Some of these are: malibu, ventura, rincon, balboa. If I want to ping a host I use this format ```
ping -c2 ventura
```
All DNS resolution can be handled either by /etc/hosts or via a local DNS server. Samba on the other hand converts hostnames to netbios names or you can set the netbios name explicitly. Explain in your own words what method you are using.[/QUOTE]

> I like your beaches theme! Living in south-central PA, I wish I was at the beach now!  :wink: I'm not that clever, however. With so many machines in the house, I will typically name them by the manufacturer/brand, such as "Asus"; when I have 2 of the same brand I'll also use the model number, such as "Dimension4600" or "DellVostro"; when I have 2 of the same brand & model number, I'll prefix with the user of the machine, such as "jim-GatewayNV75s" or "lisa-GatewayNV75S". This model name is usually given at the time of computer setup/installation of Ubuntu; I'll typically add the Netbios name in smb.conf when setting up shares. In this manner, I can usually keep my "ssh" logons and nautilus shares similar enough that I can keep them all straight. Note the 'netbios name = Asus' entry in my smb.conf file attached above. I do this for all my network machines that I intend to share content between. My kids machines remain "virgin", as I don't want them cruising the home network, potentially mucking things up, without my permission and oversight.

PM won't let me respond, as I'm WAY over the text limit, and I can't trim it enough to send it through.  I'm going to post my responses in the Forum and hope the forum will allow my responses.  Maybe someone else will also be helped?!

---

### Post by Hedon James on 2013-11-08
Also per your request, here is my CURRENT smb.conf file:

> #
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
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = bcast
   netbios name = Asus
    lanman auth = Yes
    ntlm auth = No
    client NTLMv2 auth = No
    client lanman auth = Yes
    client plaintext auth = Yes

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

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

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
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

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
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


---

### Post by bab1 on 2013-11-08
I have reconstructed this as the forum reply mechanism does not transfer the nested replies.  :-(  

> **Hedon James said:**
> I'm going to post my responses...

Results from the command: smbtree -d3```
jim@Asus:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.cm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::12bf:48ff:fe78:4797%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.37 bcast=192.168.1.255 netmask=255.255.255.0
Enter jim's password:
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.33 ( 192.168.1.33 )
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.33 ( 192.168.1.33 )
Connecting to host=192.168.1.33
Connecting to 192.168.1.33 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
MSHOME
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.33 ( 192.168.1.33 )
Connecting to host=192.168.1.33
Connecting to 192.168.1.33 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
\\HP101F745E29B8
[COLOR="#FF0000"]Connecting to host=HP101F745E29B8
name_resolve_bcast: Attempting broadcast lookup for name HP101F745E29B8<0x20>
cli_start_connection: failed to connect to HP101F745E29B8<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME[/COLOR]
\\DF7TB761 Studio
Connecting to host=DF7TB761
name_resolve_bcast: Attempting broadcast lookup for name DF7TB761<0x20>
Got a positive name query response from 192.168.1.33 ( 192.168.1.33 )
Connecting to 192.168.1.33 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
\\DF7TB761\Printer hp deskjet 845c
\\DF7TB761\print$ Printer Drivers
\\DF7TB761\IPC$ Remote IPC
\\DF7TB761\My Documents 
```

See above in red.  This error means that name is not configured correctly.  I don't see any mention of the host Asus at all.  That's not right either.   
> 
I don't typically access server locations with //IP_ADDRESS/ conventions, but rather with Netbios names. However, utilizing your conventions from the terminal, here is the output of your request, as well as my typical access method (note that Asus is my main machine, which in this case would be both client and server to itself):

jim@Asus:~$ smb://192.168.1.37/'Asus Home'
bash: smb://192.168.1.37/Asus Home: No such file or directory
jim@Asus:~$ smb://Asus/
bash: smb://Asus/: No such file or directory

I also ran this from the terminal without the quotation marks, in order to determine if my syntax was wrong, but same result was given.

The term *smb://* is not valid from the CLI.  It is a GNOME (Nautilus) method.  The response from the CLI you got was correct. 
> 

Alternatively, searching for the server within nautilus/browse network shows the Windows Network icon, but typically yields the "unable to mount location..." message. However, TODAY, in order to account for all variables, I have turned on my WinXP machine (which is the ONLY machine in MSHOME workgroup), which is a dedicated DAW recording station for music. MSHOME shows up in the Windows Network group, as well as the computer name 'Studio', but WORKGROUP does not, nor any of the computers in the WORKGROUP, which is where ALL my linux machines and/or Win7 virtual machines reside.

I don't see a host named Studio.  I see DF7TB761 and I see this: \\DF7TB761 Studio, but no Studio.  Why have do you have 2 workgroups? 
> 

Finally, clicking Go>Location within nautilus, and entering the SAME information (smb://Asus/) shows EXACTLY what I'm looking for...the shared Home Directory of Asus, as well as shared printer folder. If I didn't have 9 machines on my home network, I'd just use this method as a workaround; but I can't remember the exact Netbios name of each machine, and/or shared directories, without going to each machine and poking around (which defeats the purpose of "browsing" the network, IMO). 

Samba is really a suite of applications.  Network Browsing is separate from the connecting (mounting) [to] the share.  I think we should work on why Asus is not showing up in the smbtree display.  Although it is going to be very large, I want to see the output from the Asus terminal of this ```
smbtree -d4
``` ... we are increasing the amount of debug info.  I would like you to direct the output to a file and attach that to the forum reply.  You can create the file in your home directory like this```
smbtree -d4 > smbdebug.txt
```
I think it might be helpful if we concentrate on Asus first.  We should start by making it visible to itself.
> 
**regarding name services setup --**I like your beaches theme! Living in south-central PA, I wish I was at the beach now! I'm not that clever, however. With so many machines in the house, I will typically name them by the manufacturer/brand, such as "Asus"; when I have 2 of the same brand I'll also use the model number, such as "Dimension4600" or "DellVostro"; when I have 2 of the same brand & model number, I'll prefix with the user of the machine, such as "jim-GatewayNV75s" or "lisa-GatewayNV75S". This model name is usually given at the time of computer setup/installation of Ubuntu; I'll typically add the Netbios name in smb.conf when setting up shares. In this manner, I can usually keep my "ssh" logons and nautilus shares similar enough that I can keep them all straight. Note the 'netbios name = Asus' entry in my smb.conf file attached above. I do this for all my network machines that I intend to share content between. My kids machines remain "virgin", as I don't want them cruising the home network, potentially mucking things up, without my permission and oversight. 

There is a 15 character limit for the NETBIOS NAME.  This is a limitation built in to the SMB/CIFS protocol.  This may be part of your problems.  The use of human friendly is to help you remember their names.  For example, the host ventura is a virtual host and the the host rincon is a play on words too.  Rincon is my backup server (rincon is spanish for corner or nook) so I store my backups in the corner @ /srv/backups.  If I shared that directory it would be //RINCON/backups.  Themes are nice because the all relate.  Double meanings are even better!   A hostname like mywhitebox_1219452 is not much better than the IP address of 192.168.2.48 in my opinion.

---

### Post by Hedon James on 2013-11-08
> > **bab1 said:**
> I have reconstructed this as the forum reply mechanism does not transfer the nested replies.  :-(  

See above in red.  This error means that name is not configured correctly.  I don't see any mention of the host Asus at all.  That's not right either.   

FWIW, the lines in red reference a wireless HP all-in-one printer/copier/scanner/fax that is connected to my wife's work computer.  Her work computer is NOT part of our home network, and the wireless HP device isn't used by anyone except her.  Ubuntu machines can see the printer when "add printer" is selected, but no one except her uses it.  I don't care about this machine, unless this is the source of my problems.  It concerns me that my main machine, Asus, doesn't even see itself.  If we can get the Asus working, I can translate the remedy to my other machines.

 [QUOTE]The term *smb://* is not valid from the CLI.  It is a GNOME (Nautilus) method.  The response from the CLI you got was correct. 

I thought so, but wanted to be thorough.

> I don't see a host named Studio.  I see DF7TB761 and I see this: \\DF7TB761 Studio, but no Studio.  Why have do you have 2 workgroups? 

They are the same WinXP machine.  WinXP default workgroup is MSHOME; the default device ID is DF7TB761, but WinXP allows you to rename your machine, so I chose "Studio" based on its location...recording studio.  Windows 7 and Linux workgroups default to WORKGROUP.  I never bothered to change anything; it wasn't broken, so I didn't fix it!  Nautilus shows a Windows Network icon; clicking on that icon USED to reveal a MSHOME and a WORKGROUP icon; clicking on either used to show icons for each computer in that group...similar to a file hierarchy.  Now, it's just "unable to mount" the WORKGROUP.  For whatever reason, MSHOME mounts and displays just fine...working as I think it should.  The MSHOME>Studio machine is rarely on.  I turned it on today for 2 reasons:  to give you a FULL view of my network setup AND because I think it's a clue that MSHOME machines are displayed as they always have, while WORKGROUP machines are not.

> Samba is really a suite of applications.  Network Browsing is separate from the connecting (mounting) [to] the share.  I think we should work on why Asus is not showing up in the smbtree display.  Although it is going to be very large, I want to see the output from the Asus terminal of this ```
smbtree -d4
``` ... we are increasing the amount of debug info.  I would like you to direct the output to a file and attach that to the forum reply.  You can create the file in your home directory like this```
smbtree -d4 > smbdebug.txt
```
I think it might be helpful if we concentrate on Asus first.  We should start by making it visible to itself.


File smbdebug.txt attached for your reference.

> There is a 15 character limit for the NETBIOS NAME.  This is a limitation built in to the SMB/CIFS protocol.  This may be part of your problems.  The use of human friendly is to help you remember their names.  For example, the host ventura is a virtual host and the the host rincon is a play on words too.  Rincon is my backup server (rincon is spanish for coner or nook) so I store my backups in the corner @ /srv/backups.  If I shared that directory it would be //RINCON/backups.  Themes are nice because the all relate.  Double meanings are even better!   A hostname like mywhitebox_1219452 is not much better than the IP address of 192.168.2.48 in my opinion.[/QUOTE]

I understand where you're coming from, but my naming system is a theme to me.  I KNOW the black laptop is "Toshiba", my wife's white laptop is Lisa-NV75S while my white lapton is Jim-NV75S, etc...  To ME, it IS a themed naming convention!  I love the beach, but if I used a beach naming theme, my ADD mind would wander to warmer locales and never get any work done!  ha, ha.. :P

---

### Post by Hedon James on 2013-11-08
The only thing in the smbdebug.txt is "MSHOME" and that can't be right!  Copy & paste of terminal activity is as follows:

jim@Asus:~$ smbtree -d4 > smbdebug.txt
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = WORKGROUP
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter name resolve order = bcast
doing parameter netbios name = Asus
handle_netbios_name: set global_myname to: ASUS
doing parameter lanman auth = Yes
doing parameter ntlm auth = No
doing parameter client NTLMv2 auth = No
doing parameter client lanman auth = Yes
doing parameter client plaintext auth = Yes
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter encrypt passwords = true
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
pm_process() returned Yes
added interface eth0 ip=fe80::12bf:48ff:fe78:4797%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.37 bcast=192.168.1.255 netmask=255.255.255.0
Enter jim's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
Unable to find master browser for workgroup WORKGROUP, falling back to broadcast
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
nmb packet from 192.168.1.33(35072) header: id=25270 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=__MSBROWSE__<01> rr_type=32 rr_class=1 ttl=300000
    answers   0 char .....!   hex E000C0A80121
Got a positive name query response from 192.168.1.33 ( 192.168.1.33 )
nmb packet from 192.168.1.33(35072) header: id=2772 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=No trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=*<00> rr_type=33 rr_class=1 ttl=0
    answers   0 char .DF7TB761          hex 06444637544237363120202020202020
    answers  10 char .D.DF7TB761        hex 00440044463754423736312020202020
    answers  20 char    D.MSHOME        hex 20202044004D53484F4D452020202020
    answers  30 char     ...MSHOME      hex 2020202000C4004D53484F4D45202020
    answers  40 char       ...MSHOME    hex 2020202020201EC4004D53484F4D4520
    answers  50 char         .D...__M   hex 20202020202020201D440001025F5F4D
    answers  60 char SBROWSE__.......   hex 5342524F5753455F5F0201C400001217
    answers  70 char ................   hex 92948C00000000000000000000000000
    answers  80 char ................   hex 00000000000000000000000000000000
    answers  90 char ...........   hex 0000000000000000000000
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
nmb packet from 192.168.1.33(35072) header: id=16171 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=MSHOME<1d> rr_type=32 rr_class=1 ttl=300000
    answers   0 char `....!   hex 6000C0A80121
Got a positive name query response from 192.168.1.33 ( 192.168.1.33 )
found master browser MSHOME, 192.168.1.33
Connecting to host=192.168.1.33
Connecting to 192.168.1.33 at port 445
Connecting to 192.168.1.33 at port 139
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1b>
Cannot find master browser for workgroup MSHOME
jim@Asus:~$

---

### Post by bab1 on 2013-11-08
> **Hedon James said:**
> The only thing in the smbdebug.txt is "MSHOME" and that can't be right!  

Hmmmmm, it's not redirecting all of the stdout (i/o stream) to the file.  The copy and paste is great! 
> 

Copy & paste of terminal activity is as follows:

jim@Asus:~$ smbtree -d4 > smbdebug.txt
...
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1b>
[COLOR="#FF0000"]Cannot find master browser for workgroup MSHOME[/COLOR]
jim@Asus:~$
The red is the first  problem.  I'll explain this if you want.  For now is it possible to disconnect the HP wireless from the network and turn off as many of the other machines as possible.  This is a test  for Asus.  It should become the master browser in 10 to 15 minutes or less.  At that time try```
smbtree -d4 
```... and show me what you get (cut and paste),

---

### Post by Hedon James on 2013-11-08
> **bab1 said:**
> The red is the first  problem.  I'll explain this if you want.  

I'm not too concerned about the MSHOME workgroup, given how infrequently that machine is used.  However, I would appreciate the knowledge about Master Browsers.  I've seen this reference pop up numerous times in many troubleshooting threads regarding samba & nautilus. I've inferred what it is, and the importance of it, but I don't have a full grasp of it.  I'm always looking to learn something new, so lay it on me!

> **bab1 said:**
> For now is it possible to disconnect the HP wireless from the network and turn off as many of the other machines as possible.  This is a test  for Asus.  It should become the master browser in 10 to 15 minutes or less.  At that time try```
smbtree -d4 
```... and show me what you get (cut and paste),

I've turned off the wireless from the HP AIO, shutdown the WinXP/MSHOME machine, and shut down every other machine in the house except for 2, which are media servers that take forever to shutdown and reboot.  I'll shut them down too, if it's absolutely necessary, but I'm hoping we don't have to (fingers crossed)!  At this point the ONLY machines running are this box, 'Asus'; a media server named 'jim-VostroDesktop'; and a media server named 'Dimension4600'.  After a 30 minute wait (+/-) smbtree -d4 output as follows:

jim@Asus:~$ smbtree -d4
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = WORKGROUP
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter name resolve order = bcast
doing parameter netbios name = Asus
handle_netbios_name: set global_myname to: ASUS
doing parameter lanman auth = Yes
doing parameter ntlm auth = No
doing parameter client NTLMv2 auth = No
doing parameter client lanman auth = Yes
doing parameter client plaintext auth = Yes
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter encrypt passwords = true
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
pm_process() returned Yes
added interface eth0 ip=fe80::12bf:48ff:fe78:4797%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.37 bcast=192.168.1.255 netmask=255.255.255.0
Enter jim's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
Unable to find master browser for workgroup WORKGROUP, falling back to broadcast
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Unable to find master browser by broadcast
jim@Asus:~$

---

### Post by bab1 on 2013-11-08
> **Hedon James said:**
> I'm not too concerned about the MSHOME workgroup, given how infrequently that machine is used.  However, I would appreciate the knowledge about Master Browsers.  I've seen this reference pop up numerous times in many troubleshooting threads regarding samba & nautilus. I've inferred what it is, and the importance of it, but I don't have a full grasp of it.  I'm always looking to learn something new, so lay it on me!

Browsing in general works like this:  The Master Browser is the host that holds the The Master Browse List (MBL).  The MBL is a list that is comprised of all the hosts (by NETBIOS NAME) and all the shares on all the those hosts.  The MBL resides on the MB that wins the election to be the MB.  This election is between all the hosts that are up in the network.  Once this election is completed there are no *unforced*  elections for a new MB.  As machines come and go on the network they announce themselves and are added or deleted from the MBL.  Name conflicts are resolved at this point.

When the host that is the MB goes offline it looses the right to be the MB, this can be when it is temporarily shut off or rebooted.  At that point the election is held and a  new MB is elected and a new MBL is created.  Asus is in a state right now where it is not the MB and it can't find it.  The MBL is not available so it can't display the hosts or the shares.

All of my hosts are in the same workgroup.  Sometimes I start my Windows VIsta laptop (maui) before I start my Ubuntu Desktop (malibu).  This makes the Vista machine the MB and I can see that when I query the Ubuntu host.  It's all seemless.  It doesn't matter whether it's Windows or Samba.  I can see the MB using this ```
smbclient -L malibu
```...it returns this```

Domain=[BEACHES] OS=[Unix] Server=[Samba 3.6.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	public          Disk      Shared Data
	IPC$            IPC       IPC Service (malibu server (Samba, Ubuntu))
	PDF             Printer   PDF
	HP-LaserJet-2200 Printer   LaserJet 2200

Domain=[BEACHES] OS=[Unix] Server=[Samba 3.6.3]

	Server               Comment
	---------        -------
	MALIBU               malibu server (Samba, Ubuntu)

	[COLOR="#0000FF"]Workgroup[/COLOR]           [COLOR="#FF0000"]Master[/COLOR]
	---------         -------
	[COLOR="#0000FF"]BEACHES[/COLOR]            [COLOR="#FF0000"]MALIBU[/COLOR]


``` 
The items in blue are the workgroup listing and the part in red is the Master Browser.  In this case the MB for the entire network is malibu.  Anything that changes is reflected in its MBL.  If I turn it off then the remaining machines hold an election.  If no machines are on then it will depend on what host is turned on next.  Usually I start malibu first and it finds the MB (itself).

If Asus is the only host up then it will elect itself as the MB as long as it is functioning as a Samba server (i.e. it has shares).  I didn't see any shares in the smb.conf.  Did you use the GUI to make shares on Asus?
> 
I've turned off the wireless from the HP AIO, shutdown the WinXP/MSHOME machine, and shut down every other machine in the house except for 2, which are media servers that take forever to shutdown and reboot.  I'll shut them down too, if it's absolutely necessary, but I'm hoping we don't have to (fingers crossed)!  At this point the ONLY machines running are this box, 'Asus'; a media server named 'jim-VostroDesktop'; and a media server named 'Dimension4600'.  After a 30 minute wait (+/-) smbtree -d4 output as follows:

I don't want you to shut down something that is not absolutely necessary.  Are either of these media servers also Samba servers?  If so then we do have problems with  the host ''jim-VostroDesktop'.  The name is 17characters long.  Windows will truncate that, but Samba will choke.
> 
jim@Asus:~$ smbtree -d4
...
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
Unable to find master browser for workgroup WORKGROUP, falling back to broadcast
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Unable to find master browser by broadcast
jim@Asus:~$

When the host broadcasts its request, all hosts on the network are queried.  Clearly we have a problem here.  Logically thinking, if Asus could not find a MB at all it would elect itself.  So why is that not happening?  We need to isolate Asus from the rest of the network and see if it is being restricted by others or it is wounded in some other way.

Questions:  
Do we to change the NETBIOS NAME of 'jim-VostroDesktop' to something shorter than 15 characters?  Is it a Samba server?  This way we can eliminate 'jim-VostroDesktop' as a potential problem.

Can you assign Asus an IP address in another subnet for the time being (i.e. 192.168.[COLOR="#800080"]**100**[/COLOR].37)?   This can isolate that host to a subnet all it's own and we can test and correct anything misconfigured on that specific host.

Note that this is so we don't have to down the HTPC or any host that is hard to bring down and back up.  On my system I can quickly go dark and start over.  The should achieve the same effect.

---

### Post by Hedon James on 2013-11-08
Great explanation Bab1!  You have filled in a lot of the gaps that I didn't understand.  This makes sense to me.  A couple quick questions though:

- you said the MBL typically goes to the first booted machine (it elects itself) and subsequent machines query the network for the MBL, which is the most "senior" machine.  what happens when samba services are restarted, i.e. sudo service smbd restart and/or sudo service nmbd restart?  does the smbd & nmbd restart cause the MBL machine to lose seniority, causing the remaining machines to hold ad hoc election?  or does the MBL machine retain seniority (and the MBL) due to uptime?
- can a machine be designated as the MBL host?  if so, how?
- assuming that a machine can be designated as MBL host, but is subsequently shut down, an ad hoc election moves the MBL to the next most senior machine, then the ORIGINAL MBL host is rebooted, how does the MBL get resolved?  Does it revert back to the "designated" MBL host, or does the senior machine retain the MBL until it is shutdown?
- why does my network have NO MBL host at this time?  Seems like ad hoc elections didn't take place for a replacement MBL host?  what could have caused this?

Depending on your answers to the above questions, coupled with your explanation, it is POSSIBLE that the 'jim-VostroDesktop' is the MBL host, as that was the first Ubuntu machine on my home network (a dual-boot Win/Ubuntu machine that hasn't seen Windows since 2009!); all subsequent machines were straight up Ubuntu overwrites of prior Win installations; all subsequent machines would likely have seen 'jim-VostroDesktop' when first introduced to the network; in fact, Asus is one of the newest machines, having only been built about 10 months ago.  Accordingly, it stands to reason that 'jim-VostroDesktop' may be the MBL host.  That is an Ubuntu 10.04 machine that is past end-of-life support, but it's a server that doesn't surf the internet, so it hasn't been a problem until recently.  All other Ubuntu machines are 12.04.3 LTS and the 10.04 server has gotten quirky with the 12.04.3 machines (or maybe the 12.04.3 machines have gotten quirky with the 10.04 server?!)...I've been comtemplating a clean installation of 12.04.3 on that machine and locking it down until support ends in 2017, if it survives that long!  If I do that, I'll just rename it "Vostro"; it was my first Ubuntu machine and I hadn't developed a naming scheme yet, so it's current name doesn't fit my scheme anyhow!  Alternatively, I have no problem changing the name to "Vostro", even if I don't upgrade 10.04.  I've got a tutorial around here somewhere for a name change, but it's probably been 3+ years since I did that!

Before I do that, sounds like my best bet is to shut down EVERY machine on the network (including slowpoke servers), then ENSURE that Asus is brought back online FIRST, then check to be sure it has elected itself as host of the MBL.  Then bring other machines back online, one at a time, ensuring the network "finds" them, until the network is repopulated.  It is 9:00pm here, so I will do this tonight before sleeping.  I should have a "fresh" network view in the morning.  

May I assume you'll want to see the results of smbtree -d4 in the morning?  Is there anything else you would consider helpful?  Or does it all hinge on the next results of smbtree -d4?

---

### Post by bab1 on 2013-11-08
Let's not shut anything down today.  I'll be available tomorrow.  I want to think this out and disturb as little as possible.  I will respond t your questions in your last post in just a bit.

---

### Post by bab1 on 2013-11-08
> **Hedon James said:**
> Great explanation Bab1!  You have filled in a lot of the gaps that I didn't understand.  This makes sense to me.  A couple quick questions though:

- you said the MBL typically goes to the first booted machine (it elects itself) and subsequent machines query the network for the MBL, which is the most "senior" machine?

The machine that is elected to the Master Browser role, keeps that role as long as it is up, unless there is a forced election.  Seniority is not a valid metric. 
>  
what happens when samba services are restarted, i.e. sudo service smbd restart and/or sudo service nmbd restart?  does the smbd & nmbd restart cause the MBL machine to lose seniority, causing the remaining machines to hold ad hoc election?  or does the MBL machine retain seniority (and the MBL) due to uptime?

What do you mean by seniority?  Continuous holding of the MBL is the goal here.  The MB is a minor role in the overall picture.  It only pertains to browsing the network, not to the serving of shares.  
> 
- can a machine be designated as the MBL host?  if so, how?
You can't dedicate a machine specifically.  The MB (what you are calling the MBL host) is an elected role.  You can *weight * the metrics to favor one machine over another.  We will talk about that later on.> 
- assuming that a machine can be designated as MBL host, but is subsequently shut down, an ad hoc election moves the MBL to the next most senior machine, then the ORIGINAL MBL host is rebooted, how does the MBL get resolved?

Does it revert back to the "designated" MBL host, or does the senior machine retain the MBL until it is shutdown?

Once again, there is no seniority.   If a machine is shut down, an election is held using the remaining up machines.  The winner of the election is the **new MB** and it **rebuilds the MBL**.  This machine is the MB until it is turned off.  If you reload smbd or reboot that is considered turning off the machine.  My wife is using here Dell laptop (running Ubuntu 12.04.3).  I just rebooted my desktop and her machine became the new MB.  When she turns her machine off and my machine is still on an election will be held again and my machine will become the new MB.  There is no reverting.  It is always: Win the election and become the new MB and create the new MBL.  The only time this is not followed is if the last machine up is finally shut down and it is the first to start up again later.  At that time it will look to announce itself (as one process) and it will respond as the MB (in an other process).  
> 
- why does my network have NO MBL host at this time?  Seems like ad hoc elections didn't take place for a replacement MBL host?  what could have caused this?

This is the big question.  I have no idea, but when we figure it out, you will say; 'oh yeah, I forgot to mention that" or it will be the 17 char NETBIOS NAME.  There can't be 2 MB in the network.  It is possible that it can't respond to MBL request but still hold the role of MB.  So we have a conundrum solved by changing the NETBIOS NAME and shutting it down briefly. 
> 
Depending on your answers to the above questions, coupled with your explanation, it is POSSIBLE that the 'jim-VostroDesktop' is the MBL host, as that was the first Ubuntu machine on my home network (a dual-boot Win/Ubuntu machine that hasn't seen Windows since 2009!); all subsequent machines were straight up Ubuntu overwrites of prior Win installations; all subsequent machines would likely have seen 'jim-VostroDesktop' when first introduced to the network; in fact, Asus is one of the newest machines, having only been built about 10 months ago.  Accordingly, it stands to reason that 'jim-VostroDesktop' may be the MBL host.  

This only counts if it has been the MB continuously since that time.  When the server was created is not as important as longest continuous uptime.
> 
That is an Ubuntu 10.04 machine that is past end-of-life support, but it's a server that doesn't surf the internet, so it hasn't been a problem until recently.  All other Ubuntu machines are 12.04.3 LTS and the 10.04 server has gotten quirky with the 12.04.3 machines (or maybe the 12.04.3 machines have gotten quirky with the 10.04 server?!)

For the most part Samba is the same except for some details on 10.04/12.04/13.10.  None of which should break the system. 
> 
...I've been comtemplating a clean installation of 12.04.3 on that machine and locking it down until support ends in 2017, if it survives that long!  If I do that, I'll just rename it "Vostro"; it was my first Ubuntu machine and I hadn't developed a naming scheme yet, so it's current name doesn't fit my scheme anyhow!  Alternatively, I have no problem changing the name to "Vostro", even if I don't upgrade 10.04.  I've got a tutorial around here somewhere for a name change, but it's probably been 3+ years since I did that!

You only need to change the NETBIOS NAME in the smb.conf file (netbios name = vostro) and restart smbd.  The restart just rereads the smb.conf file.
> 
Before I do that, sounds like my best bet is to shut down EVERY machine on the network (including slowpoke servers), then ENSURE that Asus is brought back online FIRST, then check to be sure it has elected itself as host of the MBL.  Then bring other machines back online, one at a time, ensuring the network "finds" them, until the network is repopulated.  It is 9:00pm here, so I will do this tonight before sleeping.  I should have a "fresh" network view in the morning.

[SIZE=3][COLOR="#0000CD"]I would start with renaming the NETBIOS NAME to 'vostro' and restarting the smbd daemon.  This might just do it.[/COLOR][/SIZE]
>   
May I assume you'll want to see the results of smbtree -d4 in the morning?  Is there anything else you would consider helpful?  Or does it all hinge on the next results of smbtree -d4?
Only after we figure out what we are going to do via PM please.  :-)

---

### Post by Hedon James on 2013-11-15
Bab1 and I took this offline, via PMs, so we didn't rehash all the troubleshooting steps that are available in several other threads.  I had followed those threads and duplicated their efforts, but couldn't resolve my network issues.  As a courtesy to future forum troubleshooters, Bab1 had me duplicate those steps yet again so he could ascertain all the steps I had previously taken and to ensure I hadn't missed something simple.  When that was complete, Bab1 had me install Zenmap and proceeded to troubleshoot various ports on my machines and protocols on my network.  Inasmuch as the ports and protocols checked out, Bab1 suspected a hardware or software issue in the router itself.  I called my ISP and procured a replacement DSL modem/router.  Upon receipt, I hooked up the new modem/router, and VOILA...my network appeared as it should be!  ISSUE RESOLVED!

If Bab1 wants to fill in the background info and the technical jargon, I have no objection to that.  It was way above my pay-grade anyhow!  ;-)  Other than that, I'd like to publicly thank Bab1 for the NUMEROUS man-hours he graciously spent helping a stranger solve this!  There's no way I would've figured this out without him conducting the show.  I imagine that tech support for that "other" OS would've incorrectly advised reinstallation of the OS.  Another victory for FOSS and linux users.  THANKS BAB1!!!

How can I mark this thread "solved"?

---

### Post by bab1 on 2013-11-16
> **Hedon James said:**
> ... Bab1 had me install Zenmap and proceeded to troubleshoot various ports on my machines and protocols on my network.  Inasmuch as the ports and protocols checked out, Bab1 suspected a hardware or software issue in the router itself.  I called my ISP and procured a replacement DSL modem/router.  Upon receipt, I hooked up the new modem/router, and VOILA...my network appeared as it should be!  ISSUE RESOLVED!

This was an interesting problem.  No test conclusively revealed any problem.  We knew that the Master Browse List was not being created on any host in the network even though there were at least 2 Samba servers present.  The correct TCP/UDP ports were open and the smbd/nmbd daemons were running.  Since nebios browsing uses UDP packets for communication there is no error checking and therefore no error messages.  At this point I concluded that the router/switch firmware had failed.  We replaced the device and the network browsing resumed.  

The take away from this is:  Know the how the protocols involved function and believe in the tests.  The diagnosis has to fit with the symptoms (or lack thereof).

---

