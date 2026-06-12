---
title: "Can't connect to local network share"
date: 2015-05-30
forum: Networking &amp; Wireless
---

### Post by monsterjamp on 2015-05-30
I used to be able to connect to my computers through the local network but for some reason I can't anymore.
In nautilus I can still see my other computer being listed but when I double click on it, it returns an error message saying:
"Unable to access location    Failed to retrieve share list from server: Connection timed out"

I should mention the computer with Ubuntu (T400) is connected to the network via WiFi and my other computer (Windows 7 named User-PC) is connected to the network via ethernet and it has no password on it. I'm trying to access User-PC with my T400.

I've tried Googling for a solution but nothing seems to work.

---

### Post by bab1 on 2015-05-30
> **monsterjamp said:**
> I used to be able to connect to my computers through the local network but for some reason I can't anymore.
In nautilus I can still see my other computer being listed but when I double click on it, it returns an error message saying:
"Unable to access location    Failed to retrieve share list from server: Connection timed out"

I should mention the computer with Ubuntu (T400) is connected to the network via WiFi and my other computer (Windows 7 named User-PC) is connected to the network via ethernet and it has no password on it. I'm trying to access User-PC with my T400.

I've tried Googling for a solution but nothing seems to work.

Post the command line output of this command```
smbtree -d3
```...there should be a lot of output.  Cut and past it in between the [noparse]```

```[/noparse] code blocks.  The easiest way to post the data is to click on the [SIZE=5]**# **[/SIZE]icon at the top of the advanced editor and paste.

---

### Post by monsterjamp on 2015-05-31
```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=2602:306:3080:8fd0:221:6aff:fe10:7e5a bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=2602:306:3080:8fd0:51ea:b597:2c53:c810 bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.86 bcast=192.168.1.255 netmask=255.255.255.0
Enter abraham's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.69 ( 192.168.1.69 )
Connecting to 192.168.1.69 at port 445
Connecting to 192.168.1.69 at port 445

```

192.168.1.69 is the computer I'm trying to connect to so it seems that the computer is being detected but I can't access it's share.

---

### Post by bab1 on 2015-05-31
> **monsterjamp said:**
> ```
l...
Got a positive name query response from 192.168.1.69 ( 192.168.1.69 )
Connecting to 192.168.1.69 at port 445
Connecting to 192.168.1.69 at port 445

```

192.168.1.69 is the computer I'm trying to connect to so it seems that the computer is being detected but I can't access it's share.

Yes but there should be more lines in the output that list why you do not see the shares displayed.  Connecting is only part of the process.  Here is some of what I get after connecting on my network```
... Connecting to 192.168.1.6 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
...

```

---

### Post by monsterjamp on 2015-05-31
I have no idea why shares stopped working, maybe something is messed up with the network settings? Is there a way I can completely reinstall the network manager to make sure everything is installed properly?

---

### Post by bab1 on 2015-05-31
> **monsterjamp said:**
> I have no idea why shares stopped working, maybe something is messed up with the network settings? Is there a way I can completely reinstall the network manager to make sure everything is installed properly?

Why not send me the rest of the output of ***smbtree -d3***?

Network Manager has nothing to do with this problem.

---

### Post by monsterjamp on 2015-05-31
That is all of it :(
[IMG]http://i.imgur.com/fzECDAf.png[/IMG]

Although the first time I didn't use sudo.

---

### Post by bab1 on 2015-05-31
You do not need to use sudo.  Let's add more debug and see what we get.  Post the text output of this (not a screen capture)```
smbtree -d6
```

---

### Post by monsterjamp on 2015-05-31
```
INFO: Current debug levels:
  all: 6
  tdb: 6
  printdrivers: 6
  lanman: 6
  smb: 6
  rpc_parse: 6
  rpc_srv: 6
  rpc_cli: 6
  passdb: 6
  sam: 6
  auth: 6
  winbind: 6
  vfs: 6
  idmap: 6
  quota: 6
  acls: 6
  locking: 6
  msdfs: 6
  dmapi: 6
  registry: 6
  scavenger: 6
  dns: 6
  ldb: 6
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
INFO: Current debug levels:
  all: 6
  tdb: 6
  printdrivers: 6
  lanman: 6
  smb: 6
  rpc_parse: 6
  rpc_srv: 6
  rpc_cli: 6
  passdb: 6
  sam: 6
  auth: 6
  winbind: 6
  vfs: 6
  idmap: 6
  quota: 6
  acls: 6
  locking: 6
  msdfs: 6
  dmapi: 6
  registry: 6
  scavenger: 6
  dns: 6
  ldb: 6
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = WORKGROUP
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter server role = standalone server
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
pm_process() returned Yes
added interface wlan0 ip=2602:306:3080:8fd0:221:6aff:fe10:7e5a bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=2602:306:3080:8fd0:51ea:b597:2c53:c810 bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.86 bcast=192.168.1.255 netmask=255.255.255.0
Enter abraham's password: 
Opening cache file at /var/cache/samba/gencache.tdb
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
gencache_init: Opening cache file /var/cache/samba/gencache.tdb read-only.
Opening cache file at /var/run/samba/gencache_notrans.tdb
name WORKGROUP#1D found.
Connecting to 192.168.1.69 at port 445
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 0
    SO_BROADCAST = 0
    TCP_NODELAY = 1
    TCP_KEEPCNT = 9
    TCP_KEEPIDLE = 7200
    TCP_KEEPINTVL = 75
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_REUSEPORT = 0
    SO_SNDBUF = 87040
    SO_RCVBUF = 372480
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
    TCP_DEFER_ACCEPT = 0
namecache_status_fetch: key NBT/*#00.00.192.168.1.69 -> USER-PC
Connecting to 192.168.1.69 at port 445
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 0
    SO_BROADCAST = 0
    TCP_NODELAY = 1
    TCP_KEEPCNT = 9
    TCP_KEEPIDLE = 7200
    TCP_KEEPINTVL = 75
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_REUSEPORT = 0
    SO_SNDBUF = 87040
    SO_RCVBUF = 372480
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
    TCP_DEFER_ACCEPT = 0


```

---

### Post by bab1 on 2015-05-31
The only difference I see between my output (to that point) is with this```
SO_SNDBUF = 87040
    SO_RCVBUF = 372480
```
These are the buffer sizes.

Post the output of the Samba configuration file```
cat /etc/samba/smb.conf 
```

What version of Samba are you running?  ```
samba -V
```

---

### Post by monsterjamp on 2015-05-31
```
abraham@abraham-T400:~$ cat /etc/samba/smb.conf
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
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

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
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

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


```

```
abraham@abraham-T400:~$ samba -V
Version 4.1.13-Ubuntu


```

---

### Post by bab1 on 2015-05-31
I see no shares configured with smb.conf.  I assume you have made usershares with the GUI interface.  I would try unsharing the shares you have made and create new ones.

---

### Post by monsterjamp on 2015-05-31
I've never used the GUI interface of Samba (until your post) so I'm not exactly sure what to do. Also just to clarify, I'm trying to access shares from another computer (Windows 7) there is nothing I want to share from this computer (Ubuntu).

---

### Post by bab1 on 2015-05-31
> **monsterjamp said:**
> I've never used the GUI interface of Samba (until your post) so I'm not exactly sure what to do. Also just to clarify, I'm trying to access shares from another computer (Windows 7) there is nothing I want to share from this computer (Ubuntu).

Ahhhh, so your Ubuntu machine is a SMB client to the Windows machine file server (service).  The problem is with the Windows machine not advertising the shares.  My first check would be to see if the Windows machine has NETBIOS over TCP (NBT) operating and share discovery is working.

---

### Post by monsterjamp on 2015-05-31
It works now! I was under the impression that it was a problem with the computer running Ubuntu because I haven&#8217;t touched my Windows 7 computer in a month (and other computers running Windows was still able to connect to it). Thanks for your help.

---

### Post by bab1 on 2015-05-31
Great.  Glad I could help.

Window to Windows share browsing is slightly different than Windows to Samba.

---

