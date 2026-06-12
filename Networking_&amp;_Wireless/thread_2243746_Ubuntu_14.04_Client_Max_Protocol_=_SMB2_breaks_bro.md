---
title: "Ubuntu 14.04 Client Max Protocol = SMB2 breaks browsing"
date: 2014-09-10
forum: Networking &amp; Wireless
---

### Post by fl_litig8r on 2014-09-10
I'm running 14.04 LTS with all updates and I'm trying to get SMB2 working on the client side to access Windows 7 shares on other computers. With the stock smb.conf file, nautilus and smbtree see all of my shares and connect without issue, but only at SMB1 (confirmed by Wireshark). When I add the "client max protocol = smb2" line to the [global] section of smb.conf, I don't see any shares through either nautilus or when running smbtree from the command line (it returns nothing). I can connect to the shares using nautilus' "connect to server" option by manually typing them in, and it does connect at SMB2. All of the windows machines browse fine and connect at SMB2, but to each other and a nas4free computer.

What's different about browsing with an SMB2 client that would cause this problem in Ubuntu?

I have a single workgroup (no domain) and I'm running a WINS server on a separate nas4free box, which is also my master browser. My Ubuntu box is pointed to the WINS server in smb.conf. I've been messing with this for some time and I can't come up with anything. If you need my smb.conf or any smbtree -d3 output or anything, just let me know. I just can't understand how everything works under SMB1 but not SMB2.

---

### Post by fl_litig8r on 2014-09-12
Well, because it seems like I've stumped the band with my initial question, here's an easier way for anyone running 14.04 LTS and Samba with at least one other machine on the network with SMB/SMB2 shares to help me. Would anyone be so kind as to:

1. Add "Client Max Protocol = SMB2" to the [Global] section of your smb.conf -- note that the "max protocol = SMB2" only affects the server, not the client, so it needs the specific option "Client Max Protocol". ("sudo gedit /etc/samba/smb.conf")

2. Restart your smbd and nmbd ("sudo service nmbd restart" -- same command for smbd)

then either:

3a. See if "smbtree" in a terminal returns any shares or comes up blank

or

3b. Log out, log back in, then see if your network's SMB1/2 shares show up in Nautilus' "Browse Network". (The log out is to clear out any shares that may have been cached before you changed smb.conf). If they do, please make sure you can access them.

It will only take a few minutes to check, tops, but will help me out tremendously to know if someone can make this change to an SMB2 client and still browse SMB/2 shares. Don't forget to delete the line from smb.conf and restart your smbd and nmbd when you're done (assuming it screws up your browsing like it did mine).

If anyone can make this work, please post the [Global] options from your smb.conf file so I can see if you've got something I need in there.

---

### Post by bab1 on 2014-09-12
> **fl_litig8r said:**
> I'm running 14.04 LTS with all updates and I'm trying to get SMB2 working on the client side to access Windows 7 shares on other computers. With the stock smb.conf file, nautilus and smbtree see all of my shares and connect without issue, but only at SMB1 (confirmed by Wireshark). When I add the "client max protocol = smb2" line to the [global] section of smb.conf, I don't see any shares through either nautilus or when running smbtree from the command line (it returns nothing). I can connect to the shares using nautilus' "connect to server" option by manually typing them in, and it does connect at SMB2. All of the windows machines browse fine and connect at SMB2, but to each other and a nas4free computer.

What's different about browsing with an SMB2 client that would cause this problem in Ubuntu?
This doesn't appear to be an Ubuntu problem.  I'm not so sure it's even a Samba "problem".  By default SMB2 and later SMB3 is auto-negotiated with whatever host is serving the files.  This functionality has been available since Samba v3.6 (Ubuntu 12.04) and is continued in Samba v4 (Ubuntu 14.04).

My guess is there is a configuration problem. > 
I have a single workgroup (no domain) and I'm running a WINS server on a separate nas4free box, which is also my master browser. My Ubuntu box is pointed to the WINS server in smb.conf. I've been messing with this for some time and I can't come up with anything. If you need my smb.conf or any smbtree -d3 output or anything, just let me know. I just can't understand how everything works under SMB1 but not SMB2.

In fact Samba sharing is working whether you used SMB1 or SMB2.  What is not working is "Browsing for Shares".  This is a part of the overall experience but it is not file sharing per se.

Yes, Post the *smb.conf* file and the output of *smbtree -d3*.  First add the  ""client max protocol = smb2" line in and restart both smbd and smbd like this```
sudo service smbd restart

sudo service nmbd restart
```...then use *smbtree -d3*

---

### Post by fl_litig8r on 2014-09-12
Here's my smb.conf:
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
   workgroup = HOME

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
   wins server = 192.168.8.188

# My additions -- Allow SMB2 to be used
    unix extensions = no
;    follow symlinks = yes
;    wide links = yes
    client max protocol = SMB2
    server max protocol = SMB2
;    client ntlmv2 auth = yes
    client signing = auto
    server signing = auto
     name resolve order = wins hosts bcast lmhosts

# This will prevent nmbd to search for NetBIOS names through DNS.
;   dns proxy = no
    dns proxy = yes

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

[bob]
    comment = Home Folder - BOB1-UBUNTU
    path = /home/bob
    writeable = yes
    browseable = yes
    valid users = bob

```

and smbtree -d3 output:
```

bob@bob1-ubuntu:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth1 ip=192.168.8.105 bcast=192.168.8.255 netmask=255.255.255.0
Enter bob's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name HOME<0x1d>
Got a positive name query response from 192.168.8.188 ( 192.168.8.188 )
Connecting to 192.168.8.188 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215

```

Any help would be appreciated. I've turned the "client ntlmv2 auth" option on and off, and I've tried various permutations of the "name resolve order", none of which made any difference.

---

### Post by bab1 on 2014-09-12
> **fl_litig8r said:**
> smbtree -d3 output:

```

bob@bob1-ubuntu:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth1 ip=192.168.8.105 bcast=192.168.8.255 netmask=255.255.255.0
Enter bob's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name HOME<0x1d>
Got a positive name query response from 192.168.8.188 ( 192.168.8.188 )
Connecting to 192.168.8.188 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215

```

This should have had errors of some sort.  Is should net just stop.  

Let's just change one section of the smb.conf file.  Comment out both of the "max protocol " lines ```

# My additions -- Allow SMB2 to be used

;    client max protocol = SMB2
;    server max protocol = SMB2
;    client ntlmv2 auth = yes

```...now restart the smbd and nmbd daemons
```

sudo service smbd restart

sudo service nmbd restart

```
Post the output or this```
sudo pdbedit -L 
```

Post again the output of this```
smbtree -d3
```

[COLOR="#0000FF"]Edit: Just for my curiosity; what is the IP address of this machine?  Is this a single segment LAN (e.g. only one IP range)?  Post the output of [/COLOR]```
ifconfig -a
```

---

### Post by fl_litig8r on 2014-09-12
I made the changes to smb.conf and restarted the services. Here's the output of pdbedit:

```

bob@bob1-ubuntu:~$ sudo pdbedit -L
[sudo] password for bob: 
nobody:65534:nobody
bob:1000:bob
bob@bob1-ubuntu:~$

```

As you can see, user bob is there. Here's smbtree -d3 (sorry, it's long):

```

bob@bob1-ubuntu:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth1 ip=192.168.8.105 bcast=192.168.8.255 netmask=255.255.255.0
Enter bob's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name HOME<0x1d>
Got a positive name query response from 192.168.8.188 ( 192.168.8.188 )
Connecting to 192.168.8.188 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
HOME
name_resolve_bcast: Attempting broadcast lookup for name HOME<0x1d>
Got a positive name query response from 192.168.8.188 ( 192.168.8.188 )
Connecting to 192.168.8.188 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\NAS4FREE               NAS4Free Server
resolve_wins: using WINS server 192.168.8.188 and tag '*'
Got a positive name query response from 192.168.8.188 ( 192.168.8.199 )
Connecting to 192.168.8.199 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\NAS4FREE\IPC$               IPC Service (NAS4Free Server)
        \\NAS4FREE\WD1TB1             1st 1TB Western Digital Caviar Black Drive on nas4free
        \\NAS4FREE\WD1TB2             2nd 1TB Western Digital Caviar Black Drive on nas4free
    \\MEDIAPC                
resolve_wins: using WINS server 192.168.8.188 and tag '*'
Got a positive name query response from 192.168.8.188 ( 192.168.8.158 )
Connecting to 192.168.8.158 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\MEDIAPC\Users              
        \\MEDIAPC\Toshiba (i)        Toshiba (i) drive on mediapc
        \\MEDIAPC\Recorded TV        
        \\MEDIAPC\My Videos          
        \\MEDIAPC\My Pictures        
        \\MEDIAPC\mediapc_j          J drive on Mediapc
        \\MEDIAPC\mediapc_h          H drive on mediapc
        \\MEDIAPC\mediapc_g          G drive on mediapc
        \\MEDIAPC\mediapc_e          E drive on mediapc
        \\MEDIAPC\mediapc_d          D drive on Mediapc
        \\MEDIAPC\mediapc_c          C drive on mediapc
        \\MEDIAPC\J$                 Default share
        \\MEDIAPC\IPC$               Remote IPC
        \\MEDIAPC\I$                 Default share
        \\MEDIAPC\H$                 Default share
        \\MEDIAPC\G$                 Default share
        \\MEDIAPC\F$                 Default share
        \\MEDIAPC\E$                 Default share
        \\MEDIAPC\D$                 Default share
        \\MEDIAPC\C$                 Default share
        \\MEDIAPC\ADMIN$             Remote Admin
    \\FREENAS                Freenas
resolve_wins: using WINS server 192.168.8.188 and tag '*'
Got a positive name query response from 192.168.8.188 ( 192.168.8.188 )
Connecting to 192.168.8.188 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\FREENAS\IPC$               IPC Service (Freenas)
        \\FREENAS\NAS1TBSpinpointF1    1TB Samsung Spinpoint F1 Drive on freenas
        \\FREENAS\NASSS2TB           2TB Samsung F3 Drive on freenas
        \\FREENAS\NASF4S2TB          2TB Samsung F4 Drive on freenas
        \\FREENAS\NAS1TBWD           1TB Western Digital Caviar Black Drive on freenas
    \\CHROMEBOX              XBMC
resolve_wins: using WINS server 192.168.8.188 and tag '*'
Got a positive name query response from 192.168.8.188 ( 192.168.8.204 )
Connecting to 192.168.8.204 at port 445
Connecting to 192.168.8.204 at port 139
    \\BOB1-UBUNTU            bob1-ubuntu server (Samba, Ubuntu)
resolve_wins: using WINS server 192.168.8.188 and tag '*'
Got a positive name query response from 192.168.8.188 ( 192.168.8.105 )
Connecting to 192.168.8.105 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\BOB1-UBUNTU\IPC$               IPC Service (bob1-ubuntu server (Samba, Ubuntu))
        \\BOB1-UBUNTU\bob                Home Folder - BOB1-UBUNTU
        \\BOB1-UBUNTU\print$             Printer Drivers
    \\BOB-A64                
resolve_wins: using WINS server 192.168.8.188 and tag '*'
Got a positive name query response from 192.168.8.188 ( 192.168.8.100 )
Connecting to 192.168.8.100 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\BOB-A64\Z$                 Default share
        \\BOB-A64\Users              
        \\BOB-A64\print$             Printer Drivers
        \\BOB-A64\N$                 Default share
        \\BOB-A64\mp3_comedy         
        \\BOB-A64\mp3cds             
        \\BOB-A64\mp3                
        \\BOB-A64\M$                 Default share
        \\BOB-A64\L$                 Default share
        \\BOB-A64\K$                 Default share
        \\BOB-A64\J$                 Default share
        \\BOB-A64\IPC$               Remote IPC
        \\BOB-A64\I$                 Default share
        \\BOB-A64\H$                 Default share
        \\BOB-A64\G$                 Default share
        \\BOB-A64\F$                 Default share
        \\BOB-A64\E$                 Default share
        \\BOB-A64\D$                 Default share
        \\BOB-A64\Canon MF4100 Series UFRII LT    Canon MF4100 Series UFRII LT
        \\BOB-A64\Canon MF4100 Series (FAX)    Canon MF4100 Series (FAX)
        \\BOB-A64\C$                 Default share
        \\BOB-A64\BOB_MP3s           
        \\BOB-A64\BOBM-A64           M Drive (MISC) on BOB-A64
        \\BOB-A64\BOBH-A64           H drive (Workspace) on Bob-A64
        \\BOB-A64\BOBE-A64           E Drive on Bob-A64
        \\BOB-A64\BOBC-A64           C Drive on Bob-A64
        \\BOB-A64\ADMIN$             Remote Admin
bob@bob1-ubuntu:~$ 

```

Here's the ifconfig output (IP is correct):

```

bob@bob1-ubuntu:~$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:1b:21:41:c8:55  
          inet addr:192.168.8.105  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:21ff:fe41:c855/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66478200 (66.4 MB)  TX bytes:3641196 (3.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:223735 (223.7 KB)  TX bytes:223735 (223.7 KB)

bob@bob1-ubuntu:~$

```

All computers are 192.168.8.x. No subnets.

I get what you're saying about how this shouldn't just stop. From running wireshark, smbtree stops at "Tree Connect Response", which seems to succeed. Then nothing. When I switch to SMB, after "Tree Connect AndX Response", it switches to LANMAN for two entries right after that and continues on, which makes me think this may be something to do with SMB2 not being able to use LANMAN (of course, I'm not sure why SMB is using LANMAN -- that's outside my knowledge). I tried to attach the two wireshark pcap files, but it's saying "Invalid file".

---

### Post by bab1 on 2014-09-13
> **fl_litig8r said:**
> 
All computers are 192.168.8.x. No subnets.

I get what you're saying about how this shouldn't just stop. From running wireshark, smbtree stops at "Tree Connect Response", which seems to succeed. Then nothing. When I switch to SMB, after "Tree Connect AndX Response", it switches to LANMAN for two entries right after that and continues on, which makes me think this may be something to do with SMB2 not being able to use LANMAN (of course, I'm not sure why SMB is using LANMAN -- that's outside my knowledge). I tried to attach the two wireshark pcap files, but it's saying "Invalid file".

I think that part of the problem is your use of a WINS server.  I have my own theory as to why, but the bottom line is  I can use the "max protocol = SMB2" and browse the shares.  This only happens if I create an environment that has** no WINS server** and uses  a **name resolve order with only *bcast*.**

I would try adding back ```
    client max protocol = SMB2
    server max protocol = SMB2
```

Note that *client ntlmv2 auth = yes* is the default so adding this to the smb.conf file doesn't do anything.

Comment out the WINS server parameter and add this ```

    netbios name = YOUR_SERVER-NAME
    name resolve order = bcast

```...substitute the name of your server where I have YOUR_SERVER-NAME (no larger than 15 characters)

This is how a Windows machine works by default.  The only thing a WINS server is good for is netbios naming on multiple segment LAN's.  This is because you can't broadcast netbios names over all the segments.  Each segment is it's own broadcast domain.

Try this and let us know if it is successful.

---

### Post by fl_litig8r on 2014-09-13
Made the changes (netbios name BOB1-UBUNTU) and even turned off the WINS server on the nas4free box running it. No luck. Still no smbtree or nautilus browsing. Are you sure that your browsing is actually working with SMB2 turned on, because if I start with SMB at login, change to SMB2 and just restart smbd and nmbd without logging out and back in again, I'll still "see" the shares in nautilus (but it will fail to access them if I click on them). If yours is truly working (did you try smbtree as well while SMB2 was on?), can I see all the [Global] settings you're using?

As an aside, I was aware of the default settings for the commented out options. I left them there just because I was playing around with different combinations, turning them on and off, and didn't want to have to keep retyping them if I needed to test some more. I know that WINS servers are mainly for browsing across subnets (which I had to do a while ago, but no longer), but I kept using it because it seems to make my network show up faster in file browsers than just broadcast.

I'm still stumped at this point. I even tried adding client min protocol = SMB2 to the mix, which gave me different wireshark data. Without the min, the client starts protocol negotiation at SMB and then accepts SMB2 when the server offers it. With the min setting turned on, the client starts negotiation at SMB2, but it fails right at the server response with an "nt_status_invalid_parameter" error. Every time I think I might be onto something, like a "signing" issue, I run into a totally new type of failure.

Thanks for your help. This is so frustrating.

---

### Post by bab1 on 2014-09-13
> **fl_litig8r said:**
> Made the changes (netbios name BOB1-UBUNTU) and even turned off the WINS server on the nas4free box running it. No luck. Still no smbtree or nautilus browsing. Are you sure that your browsing is actually working with SMB2 turned on, because if I start with SMB at login, change to SMB2 and just restart smbd and nmbd without logging out and back in again, I'll still "see" the shares in nautilus (but it will fail to access them if I click on them). If yours is truly working (did you try smbtree as well while SMB2 was on?), can I see all the [Global] settings you're using?

As an aside, I was aware of the default settings for the commented out options. I left them there just because I was playing around with different combinations, turning them on and off, and didn't want to have to keep retyping them if I needed to test some more. I know that WINS servers are mainly for browsing across subnets (which I had to do a while ago, but no longer), but I kept using it because it seems to make my network show up faster in file browsers than just broadcast.

I'm still stumped at this point. I even tried adding client min protocol = SMB2 to the mix, which gave me different wireshark data. Without the min, the client starts protocol negotiation at SMB and then accepts SMB2 when the server offers it. With the min setting turned on, the client starts negotiation at SMB2, but it fails right at the server response with an "nt_status_invalid_parameter" error. Every time I think I might be onto something, like a "signing" issue, I run into a totally new type of failure.

Thanks for your help. This is so frustrating.

I have been using VM's for these experiments.  The default smb.conf file has been used with only this added for samba v4.1```

client max protocol = SMB2
server max protocol = SMB2

``` ... or this for samba 3.6```

max protocol = SMB2

```... and of course the addition of this```

netbios name = SOMENAME
name resolve order = bcast

```

You are correct that the setting of "client max protocol = SMB2" for Samba v4.1 is the culprit  here.  But only to the extent that it must have a strange interaction with whatever SMB servers that it is talking to in your LAN.  When this is set to the default (e.g. to auto negotiate) you are able to connect to a server.

My assumption is,  as you say, that using auto negotiation allows SMB to be used initially.  On my VM the choke point is when SMB2 is forced.  At this point the process stops when NTLMv1 is expected and apparently not used.  You can see this for yourself if you up the smbtree debug to -d9.  

I think you should be talking to the folks at samba.org.  They have their own mailing list that you can join for these kinds of [Samba]("https://lists.samba.org/mailman/listinfo/samba") questions.

---

### Post by fl_litig8r on 2014-09-13
Thanks for all your help, but please let me pester you one more time before I go off to the samba team with this. You didn't answer my question about whether you can successfully use smbtree with client SMB2 set, and whether you confirmed that your browsing actually worked or if you just assumed it did because you could still see the shares.

Also, check out the result of smbclient -L while using SMB2:
```
bob@bob1-ubuntu:~$ smbclient -L freenas
Enter bob's password: 
Domain=[FREENAS] OS=[] Server=[]

    Sharename       Type      Comment
    ---------       ----      -------
    NAS1TBWD        Disk      1TB Western Digital Caviar Black Drive on freenas
    NASF4S2TB       Disk      2TB Samsung F4 Drive on freenas
    NASSS2TB        Disk      2TB Samsung F3 Drive on freenas
    NAS1TBSpinpointF1 Disk      1TB Samsung Spinpoint F1 Drive on freenas
    IPC$            IPC       IPC Service (Freenas)
Domain=[FREENAS] OS=[] Server=[]

    Server               Comment
    ---------            -------

    Workgroup            Master
    ---------            -------
bob@bob1-ubuntu:~$

```

The shares are all listed correctly, but it lists the PC name (Freenas) as the Domain and leaves the bottom part with the info about the master browser (which also happens to be Freenas in this case) blank. Under SMB1 it gives the correct information in all fields. I suspect that this is an important clue to what's going wrong here. I don't expect you to have an answer for it, but I just thought it was interesting and should be noted in this thread for anyone who might have this problem down the road.

---

### Post by bab1 on 2014-09-14
> **fl_litig8r said:**
> Thanks for all your help, but please let me pester you one more time before I go off to the samba team with this. You didn't answer my question about whether you can successfully use smbtree with client SMB2 set, 

No you can not successfully browse the network when using client SMB2.  But in my opinion the client should not control this anyway.  If a server can't implement SMB2 completely you will have problems.
> 
... whether you confirmed that your browsing actually worked

No ibrowsing does not work.
> 
 or if you just assumed it did because you could still see the shares.

After 25 years of doing this type of diagnosis I don't assume anything, But I believe I looked at the wrong window.  I had multiple instances open.
> 
Also, check out the result of smbclient -L while using SMB2:
```
bob@bob1-ubuntu:~$ smbclient -L freenas
Enter bob's password: 
Domain=[FREENAS] OS=[] Server=[]

    Sharename       Type      Comment
    ---------       ----      -------
    NAS1TBWD        Disk      1TB Western Digital Caviar Black Drive on freenas
    NASF4S2TB       Disk      2TB Samsung F4 Drive on freenas
    NASSS2TB        Disk      2TB Samsung F3 Drive on freenas
    NAS1TBSpinpointF1 Disk      1TB Samsung Spinpoint F1 Drive on freenas
    IPC$            IPC       IPC Service (Freenas)
Domain=[FREENAS] OS=[] Server=[]

    Server               Comment
    ---------            -------

    Workgroup            Master
    ---------            -------
bob@bob1-ubuntu:~$

```

The shares are all listed correctly, but it lists the PC name (Freenas) as the Domain and leaves the bottom part with the info about the master browser (which also happens to be Freenas in this case) blank. Under SMB1 it gives the correct information in all fields. I suspect that this is an important clue to what's going wrong here. I don't expect you to have an answer for it, but I just thought it was interesting and should be noted in this thread for anyone who might have this problem down the road.
I don't see how smbclient relates to the browsing experience at all.  When you use smbtree you are **browsing **all the SMB resources.  When you use smbclient you are using a direct connection to a specific SMB resource.

As I have said before, my best guess is that the SMB2 is not fully implemented in the various servers you are using so the smbtree chokes.  This is for sure what is happening with the currently used default Linux kernel.  It's worth noting that the "in kernel" module that Samba uses (but is not maintained by any Samba developer) is cifs.ko.  Here is a link that explains this: [http://sambaxp.org/fileadmin/user_upload/SambaXP2013-DATA/thu/track1/Jeff_Layton-Linux-CIFS-Client.pdf]("http://sambaxp.org/fileadmin/user_upload/SambaXP2013-DATA/thu/track1/Jeff_Layton-Linux-CIFS-Client.pdf").  Note the kernel numbering and the security level used.

Remember, your problem is with browsing SMB shares not with accessing those shares.

---

### Post by fl_litig8r on 2014-09-14
> **bab1 said:**
> I don't see how smbclient relates to the browsing experience at all.  When you use smbtree you are **browsing **all the SMB resources.  When you use smbclient you are using a direct connection to a specific SMB resource.

It's probably just my ignorance speaking, but my thought process was that if smbclient is receiving the wrong information (or no information) about the master browser, domain/workgroup, netbios name, etc., under SMB2 that could be related to why smbtree can't browse. Even though smbclient may not be reliant on this information to perform its function, it appears to be asking for it and either getting the wrong answer or displaying the wrong answer. If smbclient and smbtree use the same method to obtain information about the workgroup and clients (an assumption that could obviously be wrong -- I'm no programmer), and that method is returning bad information under SMB2 in one, it might be doing the same in the other. For smbtree, though, this means it would stop working entirely because it needs that information to be correct to find the shares, but for smbclient, it just means that information it provides to the user (as a courtesy?) is wrong, but functionality is otherwise unaffected.

Obviously, SMB2 doesn't break smbclient completely, or even in any way that affects functionality as far as I can tell. But smbclient is definitely not working 100% under SMB2 because of the wrong (or no) information it lists about the domain/workgroup, browser and server names. That seemed to be a browsing-related issue to me. I admit that might just be a dumb assumption by a lay person.

Anyway, thanks for your time and patience. I'll take my headache over to the samba team and let you get back to helping others.

---

### Post by bab1 on 2014-09-14
> **fl_litig8r said:**
> It's probably just my ignorance speaking, but my thought process was that if smbclient is receiving the wrong information (or no information) about the master browser, domain/workgroup, netbios name, etc., under SMB2 that could be related to why smbtree can't browse.
Even though smbclient may not be reliant on this information to perform its function, it appears to be asking for it and either getting the wrong answer or displaying the wrong answer. If smbclient and smbtree use the same method to obtain information about the workgroup and clients (an assumption that could obviously be wrong -- I'm no programmer), and that method is returning bad information under SMB2 in one, it might be doing the same in the other. For smbtree, though, this means it would stop working entirely because it needs that information to be correct to find the shares, but for smbclient, it just means that information it provides to the user (as a courtesy?) is wrong, but functionality is otherwise unaffected.

Obviously, SMB2 doesn't break smbclient completely, or even in any way that affects functionality as far as I can tell. But smbclient is definitely not working 100% under SMB2 because of the wrong (or no) information it lists about the domain/workgroup, browser and server names. That seemed to be a browsing-related issue to me. I admit that might just be a dumb assumption by a lay person.

Anyway, thanks for your time and patience. I'll take my headache over to the samba team and let you get back to helping others.

Did you even attempt to read the PDF I linked to in the last post?  The first six pages should be enough for you to understand why you should be using auto negotiation for SMB versions.  Since you are not a programmer you can't really do anything about it anyway in the near term.

Have fun at Samba.org.

---

### Post by fl_litig8r on 2014-09-14
> **bab1 said:**
> Did you even attempt to read the PDF I linked to in the last post?  The first six pages should be enough for you to understand why you should be using auto negotiation for SMB versions.

Jesus. No need to get all snippy. I read it, but that's really beside the point. Telling me that I should be using auto-negotiation, which results in SMB being used instead of SMB2, is like the joke about the guy going to the doctor who says "It hurts when I go like this" and the doctor responding "Well, then don't go like this." I was merely trying to find out if it was possible to use SMB2 and keep my browsing. It appears that the answer is currently "no", but whether that has to do with the kernel module remains to be seen and doesn't mean that the smbclient issue I pointed out isn't related. Don't worry, though. I won't bother you any more.

---

