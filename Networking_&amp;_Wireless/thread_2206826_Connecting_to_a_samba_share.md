---
title: "Connecting to a samba share?"
date: 2014-02-21
forum: Networking &amp; Wireless
---

### Post by thault on 2014-02-21
I have an Ubuntu server running samba and I can see it on windows. How do I go about accessing it from my Ubuntu laptop, 12.04?

---

### Post by papibe on 2014-02-21
Hi thault.

Open Nautilus (the file manager), and select 'Browse Network' from the bottom left.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by thault on 2014-02-21
I did that and i got this error:

Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again.

---

### Post by papibe on 2014-02-21
Could you open a  terminal, run this command, and post its results (you can copy/paste the output):
```
apt-cache policy smbclient
```
Regards.

---

### Post by thault on 2014-02-21
smbclient:
  Installed: 2:3.6.3-2ubuntu2.9
  Candidate: 2:3.6.3-2ubuntu2.9
  Version table:
 *** 2:3.6.3-2ubuntu2.9 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2:3.6.3-2ubuntu2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main amd64 Packages

---

### Post by thault on 2014-02-21
I did run a sudo apt-get upgrade. Now it finds the windows network, but won't go any deeper than that.

---

### Post by thault on 2014-02-21
Now it's saying that it failed to retrieve the share list from the server workgroup, under the windows network. grrr >.<

---

### Post by Morbius1 on 2014-02-21
If you want to access a Linux samba server from another Linux box bypass all the Windows stuff and access it directly:
```
nautilus smb://server-host-name.local
```
[COLOR=#0000cd]*Changing server-host-name to it's actual host name - and don't forget the ".local"*[/COLOR]

These DBUS errors looks like a 4 year old bug that has to do with saving the credentails for this share in seahorse. Run seahorse:
```
seahorse
```
There may be other passwords in there but do you see one for the samba server? If you do delete it.

---

### Post by thault on 2014-02-21
The nautilus code didn't work, brought up the error that it failed to retreive the share from the server and try a different viewer.


Also there were no keys in seahorse.

---

### Post by bab1 on 2014-02-22
> **thault said:**
> The nautilus code didn't work, brought up the error that it failed to retreive the share from the server and try a different viewer.


Also there were no keys in seahorse.

Let's debug this.  From the terminal post the output of ```

smbtree -d3

```

---

### Post by Morbius1 on 2014-02-22
>                           The nautilus code didn't work, brought up the error that it failed to  retreive the share from the server and try a different viewer.
I don't even know how that's possible between 2 linux systems unless you've closed the mDNS port - 5353.

You might want to take a step back and see if samba on both ends is working by trying to access the server by ip address:
```
nautilus smb://192.168.0.100
```
[COLOR=#0000cd]*Change 192.168.0.100 to the ip address of the samba server.*[/COLOR]

To see if mDNS is working run this command from the client:
```
avahi-browse -at | grep IPv4
```
It should list your server in there somewhere.

Or just do a simple ping:
```
ping server-host-name.local
```
[COLOR=#0000cd]*Change server-host-name to its real value.*[/COLOR]

---

### Post by thault on 2014-02-24
tault@ubuntu:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fe80::226:c6ff:fe0e:1cde%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.0.114 bcast=192.168.0.255 netmask=255.255.255.0
Enter tault's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.111 ( 192.168.0.111 )
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to host=192.168.0.111
Connecting to 192.168.0.111 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.0.111 ( 192.168.0.111 )
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.111 ( 192.168.0.111 )
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to host=192.168.0.111
Connecting to 192.168.0.111 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.111 ( 192.168.0.111 )
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to host=192.168.0.111
Connecting to 192.168.0.111 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\THAULTSERV             ThaultServ server (Samba, Ubuntu)
Connecting to host=THAULTSERV
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name THAULTSERV<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name THAULTSERV<0x20>
resolve_wins: Attempting wins lookup for name THAULTSERV<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name THAULTSERV<0x20>
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to 66.152.109.110 at port 445
Connecting to 66.152.109.110 at port 139
Error connecting to 66.152.109.110 (Success)
Connecting to 198.105.251.210 at port 445
Connecting to 198.105.251.210 at port 139
Error connecting to 198.105.251.210 (Success)
cli_start_connection: failed to connect to THAULTSERV<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
    \\THAULT                 
Connecting to host=THAULT
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name THAULT<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name THAULT<0x20>
resolve_wins: Attempting wins lookup for name THAULT<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name THAULT<0x20>
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to 66.152.109.110 at port 445
Connecting to 66.152.109.110 at port 139
Error connecting to 66.152.109.110 (Success)
Connecting to 198.105.251.210 at port 445
Connecting to 198.105.251.210 at port 139
Error connecting to 198.105.251.210 (Success)
cli_start_connection: failed to connect to THAULT<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
    \\BIG_BOY                
Connecting to host=BIG_BOY
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name BIG_BOY<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name BIG_BOY<0x20>
resolve_wins: Attempting wins lookup for name BIG_BOY<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name BIG_BOY<0x20>
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to 66.152.109.110 at port 445
Connecting to 66.152.109.110 at port 139
Error connecting to 66.152.109.110 (Success)
Connecting to 198.105.251.210 at port 445
Connecting to 198.105.251.210 at port 139
Error connecting to 198.105.251.210 (Success)
cli_start_connection: failed to connect to BIG_BOY<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

---

### Post by thault on 2014-02-24
The samba share I'm looking for is on ThaultServ

---

### Post by bab1 on 2014-02-24
```

Connecting to [COLOR="#FF0000"]198.105.251.210 [/COLOR]at port 445
cli_start_connection: failed to connect to THAULT<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

Connecting to [COLOR="#FF0000"]66.152.109.110 [/COLOR]at port 445
cli_start_connection: failed to connect to BIG_BOY<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

```

These are public facing IP addresses (in red).  I doubt you are trying to run Samba over the Internet.  What do you do to resolve the NETBIOS names THAULT and BIG_BOY in you LAN?  Do you use static IP addressing or do the hosts all use DHCP?

> The samba share I'm looking for is on ThaultServ 

I don't see a  host named *ThaultServ*

---

### Post by thault on 2014-02-24
\\THAULTSERV ThaultServ server (Samba, Ubuntu)
Connecting to host=THAULTSERV
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name THAULTSERV<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name THAULTSERV<0x20>
resolve_wins: Attempting wins lookup for name THAULTSERV<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name THAULTSERV<0x20>
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to 66.152.109.110 at port 445
Connecting to 66.152.109.110 at port 139
Error connecting to 66.152.109.110 (Success)
Connecting to 198.105.251.210 at port 445
Connecting to 198.105.251.210 at port 139
Error connecting to 198.105.251.210 (Success)
cli_start_connection: failed to connect to THAULTSERV<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

the  wifi router does the DHCP Fodor the network

---

### Post by bab1 on 2014-02-24
> **thault said:**
> \\THAULTSERV ThaultServ server (Samba, Ubuntu)
Connecting to host=THAULTSERV
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name THAULTSERV<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name THAULTSERV<0x20>
resolve_wins: Attempting wins lookup for name THAULTSERV<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name THAULTSERV<0x20>
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to 66.152.109.110 at port 445
Connecting to 66.152.109.110 at port 139
Error connecting to 66.152.109.110 (Success)
Connecting to 198.105.251.210 at port 445
Connecting to 198.105.251.210 at port 139
Error connecting to 198.105.251.210 (Success)
cli_start_connection: failed to connect to THAULTSERV<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

the  wifi router does the DHCP Fodor the network

The host THAULTSERV has the same problem
```

Error connecting to [COLOR="#FF0000"]198.105.251.210 [/COLOR](Success)
cli_start_connection: failed to connect to THAULTSERV<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

```
There seems to be no setting for broadcast lookup of names.

Post the *entire* output of ```
cat /etc/samba/smb.conf
```

---

### Post by thault on 2014-02-25
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


```

---

### Post by thault on 2014-02-25
[QUOTE=Morbius1;12936430]I don't even know how that's possible between 2 linux systems unless you've closed the mDNS port - 5353.

You might want to take a step back and see if samba on both ends is working by trying to access the server by ip address:
```
nautilus smb://192.168.0.100
```
[COLOR=#0000cd]*Change 192.168.0.100 to the ip address of the samba server.*[/COLOR][QUOTE=Morbius2;12936430]

 
This actually brought up the share, but I don't want to have to do this everytime.

---

### Post by bab1 on 2014-02-25
> **thault said:**
> ```
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


```
What is the host name of this computer?  Do you have GUI created shares on this host?

---

### Post by Morbius1 on 2014-02-25
.

---

### Post by Morbius1 on 2014-02-25
.

---

### Post by Morbius1 on 2014-02-25
> You might want to take a step back and see if samba on both ends is working by trying to access the server by ip address:
```
nautilus smb://192.168.0.100
```
[COLOR=#0000cd]*Change 192.168.0.100 to the ip address of the samba server.*[/COLOR]

> **thault said:**
> This actually brought up the share, but I don't want to have to do this everytime.
Agreed, and if only you would have told us if a "ping THAULTSERV.local" worked we could perhaps find a resolution to this that does not require workgroups, netbios, master browsers , *[COLOR=#0000cd]name resolve order[/COLOR]* and all the rest of the Windows baggage. All Linux machines can connect to each other with a hostname.local so all should be able to connect to each others samba share with a nautilus smb://hostname.local. At that point you can Bookmark it so it shows up as a sort of "mapped drive" in Nautilus sort of like it does in Windows Explorer. You can even set this up so it automatically shows up under networks in all your Linux clients. They key here is that they are in fact "local".

Which leads me to the next question. The very first sentence on your very first post stated:
> I have an Ubuntu server running samba and I can see it on windows.
Are all these machines on a local lan or are you in fact trying to access a Samba server remotely over the Internet? The reason I'm asking this is because your other posts suggest you are trying to do this remotely: [I connect to my server outside of the network]("http://ubuntuforums.org/showthread.php?t=2206747&p=12934831#post12934831")

I may be reading to much into that. Perhaps you are just trying to administer the server remotely.

---

### Post by bab1 on 2014-02-25
> **Morbius1 said:**
> .
.
.

@Morbuis1 -- maybe we should diagnose these things together in the background via PM or some other means.  ;-)

My guess is that the OP has multiple problems.  The *smbtree -d3* output shows that the search for available shares never goes past using the /etc/hosts file```
resolve_lmhosts: Attempting lmhosts lookup for name THAULTSERV<0x20>
[COLOR="#FF0000"]resolve_wins: Attempting wins lookup for name THAULTSERV<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name THAULTSERV<0x20>[/COLOR]
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to 66.152.109.110 at port 445
Connecting to 66.152.109.110 at port 139
Error connecting to 66.152.109.110 (Success)
Connecting to 198.105.251.210 at port 445
Connecting to 198.105.251.210 at port 139
Error connecting to 198.105.251.210 (Success)
cli_start_connection: failed to connect to THAULTSERV<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
```...and it is incorrectly looking to the Internet for resolution (check the IP addresses listed).

On top of that I believe some of the diagnostic feedback is from a host that is not the Samba server.

I will be away for most of the day, so I will not have any comments until much later.

---

### Post by thault on 2014-02-25
I was trying to connect within the LAN, I use SSH to connect to the server during class. This is my first experience with Linux, sorry to be causing unnecessary work. I do appreciate the help you guys, and the Forums, has offered.

---

### Post by Morbius1 on 2014-02-25
@Bab1, I've disabled PM so that won't work.

I'm going to take one more shot at this then you can get to the bcast first in name resolve order thingy. My way doesn't require it.

@ thault, Can you or can you not ping the Linux server from the Linux client by name:
```
ping THAULTSERV.local
```
If you cannot and both of these systems are both connected to the same router then disable both machine's firewalls and try it again.

[COLOR=#0000cd] **EDIT**: Then make sure avahi-daemon is running on both systems:[/COLOR]
```
 sudo service avahi-daemon restart
```
And try it again.

---

### Post by bab1 on 2014-02-25
> **thault said:**
> I was trying to connect within the LAN, I use SSH to connect to the server during class. This is my first experience with Linux, sorry to be causing unnecessary work. I do appreciate the help you guys, and the Forums, has offered.

It doesn't matter whether you are connected to the console of the host that is the Samba server or connected to that server via ssh, you are still only connected to a local host.  They are functionally the same in that context. 

You are doing something completely different when you mount a portion of the remote server's file system (a share) via SMB/CIFS to your local machine's file system.

Using mDNS (.local) successfully means you need to have DNS working correctly to resolve the hostname first.  Your network does not seem to be able to do that.

---

### Post by bab1 on 2014-02-25
> **Morbius1 said:**
> @Bab1, I've disabled PM so that won't work.

I'm going to take one more shot at this then you can get to the bcast first in name resolve order thingy. My way doesn't require it.

@ thault, Can you or can you not ping the Linux server from the Linux client by name:
```
ping THAULTSERV.local
```
If you cannot and both of these systems are both connected to the same router then disable both machine's firewalls and try it again.

I believe that mDNS is wounded (no DNS resolution at all).  That's why there is no hosts lookup success and it hangs at that point.

Have at it with the OP.  I'll check back later in the day.

---

### Post by Morbius1 on 2014-02-25
If you are talking about the output of smbtree it's not looking for mDNS so we don't know from that what state it's in. 

mDNS isn't dependent on another DNS it is a DNS. 

It's automatic in Linux and you would have to take extra - ordinary steps to disable it. Or put a firewall in it's way. Or be in a different subnet than everyone else.
[COLOR=#0000cd]**EDIT**[/COLOR]: Or avahi-daemon isn't running either on the server or the client.

---

### Post by thault on 2014-02-25
```
tault@ubuntu:~$ ping THAULTSERV.local
ping: unknown host THAULTSERV.local
tault@ubuntu:~$ ping 192.168.0.111
PING 192.168.0.111 (192.168.0.111) 56(84) bytes of data.
64 bytes from 192.168.0.111: icmp_req=1 ttl=64 time=18.6 ms
64 bytes from 192.168.0.111: icmp_req=2 ttl=64 time=1.27 ms
64 bytes from 192.168.0.111: icmp_req=3 ttl=64 time=1.21 ms
64 bytes from 192.168.0.111: icmp_req=4 ttl=64 time=1.19 ms
64 bytes from 192.168.0.111: icmp_req=5 ttl=64 time=4.49 ms
64 bytes from 192.168.0.111: icmp_req=6 ttl=64 time=1.18 ms
64 bytes from 192.168.0.111: icmp_req=7 ttl=64 time=1.77 ms
^C
--- 192.168.0.111 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6007ms
rtt min/avg/max/mdev = 1.189/4.257/18.664/5.985 ms
tault@ubuntu:~$ ping thaultserv
PING thaultserv (66.152.109.110) 56(84) bytes of data.
^C
--- thaultserv ping statistics ---
27 packets transmitted, 0 received, 100% packet loss, time 26208ms



thault@ThaultServ:~$ sudo service avahi-daemon restart
avahi-daemon: unrecognized service

```

The first  block is the pings. pinging THAULTSERV.local didn't work. Pinging the LAN address of the server worked. Pinging thaultserv ended in packets dissapearing.

also the server doesn't have avahi.

---

### Post by bab1 on 2014-02-26
> **Morbius1 said:**
> If you are talking about the output of smbtree it's not looking for mDNS so we don't know from that what state it's in. 

mDNS isn't dependent on another DNS it is a DNS. 

I was in a hurry to leave earlier in the day.  Let me restate my position.   If DNS services are *misconfigured* or absent, then DNS Service Discovery (DNS-SD) and mDNS won't work.  

Quoting dns-sd.org:   
*"DNS Service Discovery is a way of** using standard DNS programming interfaces, servers, and packet formats** to browse the network for services.*
See [here]("http://www.dns-sd.org/") and [here]("http://www.multicastdns.org/").  I'm sure you have read [this]("http://avahi.org/wiki/AboutAvahi").  The last item refers to the first 2 items.

The OP does not have any mapping between IP address and hostname.  His last post is evidence of that. 
> 

It's automatic in Linux and you would have to take extra - ordinary steps to disable it. Or put a firewall in it's way. Or be in a different subnet than everyone else.
[COLOR=#0000cd]**EDIT**[/COLOR]: Or avahi-daemon isn't running either on the server or the client.
Another possibility is that the /etc/nsswitch.conf file is not configured correctly.```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files [COLOR="#FF0000"]mdns4_minimal [NOTFOUND=return][/COLOR] dns [COLOR="#FF0000"]mdns4[/COLOR]
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```
For what it's worth, my Ubuntu 12.04 "server edition" hosts have an nsswitch.conf file that looks like this```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```...no Avahi references at all.  So even if the avahi daemon was running it would not be queried.

I think it will be simpler in the end to diagnose what the OP really has wrong and fix that as opposed to just proposing things to try.  All the options are still there for the user to apply in the end.  My own personal opinion is to set everything up correctly and let the end user select what methods work best for them (e.g Avahi, bookmarking, network browsing, etc.).

Don't take the above in the wrong way.  Most of what I speak of is only my interpretation of the documentation we both have.

---

### Post by bab1 on 2014-02-26
> **thault said:**
> ```
tault@ubuntu:~$ ping THAULTSERV.local
ping: unknown host THAULTSERV.local


tault@ubuntu:~$ ping 192.168.0.111
PING 192.168.0.111 (192.168.0.111) 56(84) bytes of data.
64 bytes from 192.168.0.111: icmp_req=1 ttl=64 time=18.6 ms
64 bytes from 192.168.0.111: icmp_req=2 ttl=64 time=1.27 ms
64 bytes from 192.168.0.111: icmp_req=3 ttl=64 time=1.21 ms
64 bytes from 192.168.0.111: icmp_req=4 ttl=64 time=1.19 ms
64 bytes from 192.168.0.111: icmp_req=5 ttl=64 time=4.49 ms
64 bytes from 192.168.0.111: icmp_req=6 ttl=64 time=1.18 ms
64 bytes from 192.168.0.111: icmp_req=7 ttl=64 time=1.77 ms
^C
--- 192.168.0.111 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6007ms
rtt min/avg/max/mdev = 1.189/4.257/18.664/5.985 ms

tault@ubuntu:~$ ping thaultserv
PING thaultserv (66.152.109.110) 56(84) bytes of data.
^C
--- thaultserv ping statistics ---
27 packets transmitted, 0 received, 100% packet loss, time 26208ms



thault@ThaultServ:~$ sudo service avahi-daemon restart
avahi-daemon: unrecognized service

```

The first  block is the pings. pinging THAULTSERV.local didn't work. Pinging the LAN address of the server worked. Pinging thaultserv ended in packets dissapearing.

also the server doesn't have avahi.
It's pretty obvious at this point that you do not have DNS services that map the hostname (or hostname.local) to an IP address.  You do have IP addressing however.

At this point you can fix the /etc/hosts file if you have immutable (non-changing) IP addresses and thus use hostnames.  Or you can use NETBIOS name services via broadcast.  Either one will provide you with the ability to interact with the Samba server using an assigned name.  I do not recommend installing avahi at all.

Previously you said you assigned IP addresses via the router.  Do you use a reserved address for this Samba server (THAULTSERV I suppose)?

Post the output of the following from THAULTSERV so we can advise on the proper way to go on this issue.```

cat /etc/hosts

cat /etc/network/interfaces

```

To summarize, you can use either DNS hosts or NETBIOS broadcasts to allow browsing of the network shares one THAULTSERV.  The DNS hosts method traditionally uses fixed IP addressing while the NETBIOS method can use dynamic IP addressing (DHCP).

It is interesting to note that the DNS hostname is converted internally to a NETBIOS name  by Samba.  I don't see any reason to use this extra step on a small LAN as Samba uses the NETBIOS name in the end anyway.

---

### Post by Morbius1 on 2014-02-26
> **thault said:**
> ```
tault@ubuntu:~$ ping THAULTSERV.local
ping: unknown host THAULTSERV.local
...


thault@ThaultServ:~$ sudo service avahi-daemon restart
avahi-daemon: unrecognized service

```

The first  block is the pings. pinging THAULTSERV.local didn't work. Pinging the LAN address of the server worked. Pinging thaultserv ended in packets dissapearing.

also the server doesn't have avahi.
**First**: I don't know which version of the server you are using so start the service instead of restarting it just to make sure it is in fact missing:
```
sudo service avahi-daemon start
```
**Second**: If it's truly missing install it:
```
sudo apt-get install avahi-daemon
```
**Third**: Then see if it's running:
```
sudo service avahi-daemon status
```
If it's not running start it. If for some reason it refuses to start reboot the box.

Go through the exact same thing on the client machine. Then try the ping again. [COLOR=#0000cd]*It would be a shame if avahi is disabled on your network since among other things CUPS now uses it to automatically discover and create local print queues for all enabled network printers.*[/COLOR]

[COLOR=#0000cd]***Question***[/COLOR]: Did you at any time ever receive an error message that looked something like this:
> Network service  discovery disabled - current network has a .local  domain, which is not  recommended + incompatible with Avahi network. The service has been disabled.
If you did then that would explain why avahi isn't starting. The problem is the DNS server - or rather how it was configured - by your ISP. You can correct this only by changing the DNS servers to something like OpenDNS or Google's DNS which is something you might not be willing to do. You can also modify a system file to override it's desire to shut down avahi but I try to avoid things that might be reset after an update in the future.

Another way to verify this is by running the following command:
```
host -t SOA local
```
If your ISP is not the culprit it should come back with this:
> Host local not found: 3(NXDOMAIN)
If your ISP is capturing the .local assignment it will come back with something like this: 
> local has SOA record...
[COLOR=#0000cd]*Side note: Based on your other post it appears you also use OSX. In OSX avahi is called Bonjour and Bonjour faces the same dilemma as avahi but it handless it seamlessly so .local can be used regarless of how the ISP was configured.*[/COLOR]

---

### Post by thault on 2014-02-26
```
tault@ubuntu:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

tault@ubuntu:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

We use DHCP, so netbios looks to be the better option.

---

### Post by bab1 on 2014-02-26
> **thault said:**
> ```
tault@ubuntu:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```

This is what I expected to see.
> 

```



tault@ubuntu:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

This is NOT what I expected to see.
> 
We use DHCP, so netbios looks to be the better option.

To use NETBIOS names you have to edit the /etc/samba/smb.conf file to add one line and modify another.  To open up the file for editting you do this```
sudo nano /etc/samba/smb.conf
```...then look for the line in the [global] section that looks like this (it's about the 56th line down in the smb.conf file)```
;   name resolve order = lmhosts host wins bcast
```

You edit that line and add a line above it so it now looks like this```

netbios name = THAULTSERV
name resolve order = bcast
```...now save the edited file and close nano.

The restart the Samba service```
sudo service smbd restart
```

After a few minutes you should be able to see THAULTSERV by browsing the network shares.

FYI -- This will not make pinging by name work.  You need DNS hostnames working for ping to be successful.

---

### Post by thault on 2014-02-27
is this what it should look like?
```
# What naming service and in what order should we use to resolve host names
# to IP addresses
    netbios name = THAULTSERV
;   name resolve order = bcast


```

---

### Post by bab1 on 2014-02-27
> **thault said:**
> is this what it should look like?
```
# What naming service and in what order should we use to resolve host names
# to IP addresses
    netbios name = THAULTSERV
;   name resolve order = bcast


```

Remove the semicolon from the second line.

---

### Post by thault on 2014-02-27
I made the changes, the only thing that shows up in browse networks is windows network.

---

### Post by bab1 on 2014-02-27
> **thault said:**
> I made the changes, the only thing that shows up in browse networks is windows network.
Click on that.  The share will eventually show up as a stand alone share but for now it is located by "windows network">>workgroup>>share

---

