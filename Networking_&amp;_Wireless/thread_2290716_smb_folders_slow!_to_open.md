---
title: "smb folders slow! to open?"
date: 2015-08-14
forum: Networking &amp; Wireless
---

### Post by kurja on 2015-08-14
I have a desktop machine and a couple laptops here with fresh ubuntu 14.04 installs on them, and I shared the default "Public" folders on each, and it works out of the box - if you consider it working when it takes over a minute to open the shared folder from another machine. I click 'browse network' in file browser and I can see the other machines in the network, click one of them and I get a 'Opening <machine>' popup... and it literally takes almost a minute just to show me the shared folder. And when I click to open that, it's another just as long wait to see the actual files.

After that, I can copy files to and fro with acceptable speed and I can even close the Files browser, the next time I open it I get instant access to the shared folders, without a minute long wait. But when I log out and back in, the waiting is there again. Happens with wifi or wired connections and the behavior is exactly the same regardless of which machine I use to access which.

What could possible be wrong here? Any ideas?

---

### Post by TheFu on 2015-08-14
DNS (really hostname resolution) - is Avahi working or /etc/hosts setup on each machine?

or do you have "green" HDDs that spin down every 8 seconds?

Why use CIFS when you can use **NFS**?!!!!!!!

---

### Post by kurja on 2015-08-15
> **TheFu said:**
> DNS.
or do you have "green" HDDs that spin down every 8 seconds?

Why use CIFS when you can use NFS?!!!!!!!

By saying DNS you're saying that the behavior is expected unless I run a dns server?? I don't think that's even an option in my case, it's just three to four home computers that are not always on.

The delay is the same between two machines with SSD's in them, I don't think those are spinning down ;)

Smb/cifs is the default in Ubuntu, it's what you get when a user right clicks a folder and tries to share it's content to the local net.

---

### Post by SeijiSensei on 2015-08-15
Create an /etc/hosts file on each machine that includes the names and IP addresses of all the machines on the network.

---

### Post by kurja on 2015-08-15
I suppose I should lock the ip's to the mac addresses on the router too for that.

So is it normal that smb takes a really long time to find a machine in local net? And even to show the shared folder after a machine has been found?

---

### Post by bab1 on 2015-08-15
> **kurja said:**
> I suppose I should lock the ip's to the mac addresses on the router too for that.

So is it normal that smb takes a really long time to find a machine in local net? And even to show the shared folder after a machine has been found?
No it is not normal.  However, there is no way to tell what your problem is without knowing what your Samba configuration is really like.  Samba does ***not*** use DNS for name resolution,  By default it uses the /etc/hosts file to convert the local hostname to a NETBIOS name if this is available, but it is not the only way, nor is it even the preferred way some of the time  You may have a name service problem, but for sure it is not a DNS name problem.

Rather than guess or opine, let's diagnose the problem.  Post the output of this terminal command to start with```
cat /etc/samba/smb.conf
```

Please post the output using [noparse]```
  
```[/noparse] code blocks.  The easiest way to do this is to click on the **[SIZE=5]# [/SIZE]** icon at the top of the advanced editor that you use to reply to this post.  You will have to scroll back a bit to get all of the text.

[COLOR="#0000FF"]Edit:  FWIW, you do not need a fixed IP address with NETBIOS; even for the server.  The name is registered dynamically along with the hosts current IP address when that host is available on the network (i.e. when it is booted up).[/COLOR]

---

### Post by kurja on 2015-08-15
This is from my desktop machine that has had 14.04 since it came out, I'm pretty sure I never edited it though. As said the laptops have brand new 14.04 installs.

```
# Sample configuration file for the Samba suite for Debian GNU/Linux.#
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

---

### Post by bab1 on 2015-08-15
So either this machine has no shares or it uses user defined shares via the GUI interface (usershares).  What is the hostname of this machine?  Post the output of these commands```

hostname

cat /etc/hosts

ls -l /var/lib/samba/usershares

```

Let's take a look at all the machines in the network with this command.  Post the output of this```
smbtree -d3
```

---

### Post by kurja on 2015-08-16
> **bab1 said:**
> So either this machine has no shares or it uses user defined shares via the GUI interface (usershares).  What is the hostname of this machine?  Post the output of these commands```

hostname

cat /etc/hosts

ls -l /var/lib/samba/usershares

```

Let's take a look at all the machines in the network with this command.  Post the output of this```
smbtree -d3
```

All shares that have now been created were made through the stock gui (right click, properties, share this folder).

hostname
```
desktop
```

cat /etc/hosts
```
127.0.0.1    localhost
127.0.1.1    desktop


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters



```
ls -l /var/lib/samba/usershares


```
total 4
-rw-r--r-- 1 k k 108 huhti 30  2014 public

```

smbtree -d3
```
:~$ smbtree -d3lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.1.2 bcast=192.168.1.255 netmask=255.255.255.0
Enter k's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.2 ( 192.168.1.2 )
Connecting to 192.168.1.2 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.2 ( 192.168.1.2 )
Connecting to 192.168.1.2 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\TUXKONE                tuxkone server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name TUXKONE<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name TUXKONE<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name TUXKONE<0x20>
resolve_hosts: getaddrinfo failed for name TUXKONE [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name TUXKONE<0x20>
Got a positive name query response from 192.168.1.6 ( 192.168.1.6 )
Connecting to 192.168.1.6 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\TUXKONE\Julkinen           
        \\TUXKONE\IPC$               IPC Service (tuxkone server (Samba, Ubuntu))
        \\TUXKONE\print$             Printer Drivers
    \\KIOSKI                 kioski server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name KIOSKI<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name KIOSKI<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name KIOSKI<0x20>
resolve_hosts: getaddrinfo failed for name KIOSKI [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name KIOSKI<0x20>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\KIOSKI\Public             
        \\KIOSKI\print$             Printer Drivers
        \\KIOSKI\IPC$               IPC Service (kioski server (Samba, Ubuntu))
    \\DESKTOP                desktop server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name DESKTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name DESKTOP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name DESKTOP<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\DESKTOP\Public             
        \\DESKTOP\Samsung-CLP-310-Series    Samsung CLP-310 Series
        \\DESKTOP\print$             Printer Drivers
        \\DESKTOP\IPC$               IPC Service (desktop server (Samba, Ubuntu))

```

In there I notice ```
[COLOR=#000000][FONT=Ubuntu Mono]could not open file /var/cache/samba/gencache.tdb: Permission denied[/FONT][/COLOR]
```

and that file is owned by root, so I ran the command again with sudo, here's the output of that, if it helps:

```
lp_load_ex: refreshing parametersInitialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.1.2 bcast=192.168.1.255 netmask=255.255.255.0
Enter root's password: 
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.2 ( 192.168.1.2 )
Connecting to 192.168.1.2 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
Connecting to 192.168.1.2 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\TUXKONE                tuxkone server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name TUXKONE<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name TUXKONE<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name TUXKONE<0x20>
resolve_hosts: getaddrinfo failed for name TUXKONE [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name TUXKONE<0x20>
Got a positive name query response from 192.168.1.6 ( 192.168.1.6 )
Connecting to 192.168.1.6 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\TUXKONE\Julkinen           
        \\TUXKONE\IPC$               IPC Service (tuxkone server (Samba, Ubuntu))
        \\TUXKONE\print$             Printer Drivers
    \\KIOSKI                 kioski server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name KIOSKI<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name KIOSKI<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name KIOSKI<0x20>
resolve_hosts: getaddrinfo failed for name KIOSKI [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name KIOSKI<0x20>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to 192.168.1.4 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\KIOSKI\Public             
        \\KIOSKI\print$             Printer Drivers
        \\KIOSKI\IPC$               IPC Service (kioski server (Samba, Ubuntu))
    \\DESKTOP                desktop server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name DESKTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name DESKTOP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name DESKTOP<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\DESKTOP\Public             
        \\DESKTOP\Samsung-CLP-310-Series    Samsung CLP-310 Series
        \\DESKTOP\print$             Printer Drivers
        \\DESKTOP\IPC$               IPC Service (desktop server (Samba, Ubuntu))



```

---

### Post by kurja on 2015-08-16
> **TheFu said:**
> is Avahi working or /etc/hosts setup on each machine?!

Apparently my network has a .local domain and avahi is not compatible, or so it tells me when I power up a computer. I have done nothing to set up /etc/hosts on any of the machines.

---

### Post by TheFu on 2015-08-16
Looks like **smbtree** doesn't work the way it used to. I don't know when this changed (or perhaps the default options changed?), but it is less useful today for showing shares on a network.  I have a few different systems with samba shares here and none were shown running smbtree. That was unexpected to me.  It used to work, promise.

I have both DNS on the router (for the DHCP reservation systems) and /etc/hosts which tell all my systems about each other. Use a tiny ansible playbook to keep them all updated.

Updates:
* Figured out that smbtree only works from a client machine (thinking it has client-side dependencies). Ran it from a server last time. This server is a client, but it uses **autofs** to mount CIFS from a Windows machine and uses an IP address (I wasn't able to get name resolution working for it even with /etc/hosts correctly setup).
* Ran it from a client and did get the list of file and printer shares - took under 4 sec to locate and show shares from 5 systems without any password provided.
* I've never used a "usershare" in my life. Shares are **always** configured in /etc/samba/smb.conf. Also not using an "domain", just a custom workgroup.

---

### Post by bab1 on 2015-08-17
> **kurja said:**
> All shares that have now been created were made through the stock gui (right click, properties, share this folder).

Yes, these are called usershares.
> 

hostname
```
desktop
```

cat /etc/hosts
```
127.0.0.1    localhost
127.0.1.1    desktop

```

This is good.  The hostname is less than 15 characters. That is a problem for Samba.
> 


ls -l /var/lib/samba/usershares


```
total 4
-rw-r--r-- 1 k k 108 huhti 30  2014 public

```
This is the usershare definition file> 

smbtree -d3
```
:~$ smbtree -d3
...
[B][COLOR="#008000"]name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.2 ( 192.168.1.2 )
Connecting to 192.168.1.2 at port 445[/COLOR][/B]
...
WORKGROUP
...
Got a positive name query response from 192.168.1.2 ( 192.168.1.2 )
Connecting to 192.168.1.2 at port 445
Doing spnego session setup (blob length=74)
..
    \\TUXKONE                tuxkone server (Samba, Ubuntu)
...
[B][COLOR="#FF0000"]resolve_hosts: Attempting host lookup for name TUXKONE<0x20>
resolve_hosts: getaddrinfo failed for name TUXKONE [Name or service not known][/COLOR][/B]
[B][COLOR="#008000"]name_resolve_bcast: Attempting broadcast lookup for name TUXKONE<0x20>
Got a positive name query response from 192.168.1.6 ( 192.168.1.6 )
Connecting to 192.168.1.6 at port 445[/COLOR][/B]
...
        \\TUXKONE\Julkinen           
        \\TUXKONE\IPC$               IPC Service (tuxkone server (Samba, Ubuntu))
        \\TUXKONE\print$             Printer Drivers
    \\KIOSKI                 kioski server (Samba, Ubuntu)
...
[B][COLOR="#FF0000"]resolve_hosts: Attempting host lookup for name KIOSKI<0x20>
resolve_hosts: getaddrinfo failed for name KIOSKI [Name or service not known][/COLOR][/B]
[COLOR="#008000"][B]name_resolve_bcast: Attempting broadcast lookup for name KIOSKI<0x20>
Got a positive name query response from 192.168.1.4 ( 192.168.1.4 )
Connecting to 192.168.1.4 at port 445[/B][/COLOR]
...
        \\KIOSKI\Public             
        \\KIOSKI\print$             Printer Drivers
        \\KIOSKI\IPC$               IPC Service (kioski server (Samba, Ubuntu))
    \\DESKTOP                desktop server (Samba, Ubuntu)
...
[B][COLOR="#0000FF"]resolve_hosts: Attempting host lookup for name DESKTOP<0x20>
Connecting to 127.0.1.1 at port 445[/COLOR][/B]
...
        \\DESKTOP\Public             
        \\DESKTOP\Samsung-CLP-310-Series    Samsung CLP-310 Series
        \\DESKTOP\print$             Printer Drivers
        \\DESKTOP\IPC$               IPC Service (desktop server (Samba, Ubuntu))

```
[QUOTE]
In there I notice ```
[COLOR=#000000][FONT=Ubuntu Mono]could not open file /var/cache/samba/gencache.tdb: Permission denied[/FONT][/COLOR]
```
and that file is owned by root, so I ran the command again with sudo, here's the output of that, if it helps:

No the Permission Denied response is not relevant in this context.

I have stripped out the unnecessary lines form the smbtree response.  As you can see all hosts (computers) have have been found and displayed. 
The listings in **[COLOR="#FF0000"]red[/COLOR]** are where Samba unsuccessfully attempted to resolve the NETBIOS name (along with the IP address) and failed.  Samba will move on and try the next available resolution type.  In this case it is via bcast.  The [COLOR="#008000"]**green**[/COLOR] is the successful lookup and connection.  The [COLOR="#0000FF"]**blue**[/COLOR] is where the hosts file lookup was successful, as the listing for the localhost was in the local /etc/host file.

Everything is working as is expected.  The delay seems to be due to the lack of any previous "Master Browse List" (MBL).   The Samba network needs to elect a Master  Browser and populate the MBL and wait for you to access a particular share.  It is all normal.  If the system has older slower hardware then the election time and MBL population can be delayed.  I really don't pay attention to "boot time, first time share display" at home.  Some of my shares are dynamic like yours.  I just wait a bit.  Some of my shares are mounted via fstab.  Those are almost instantaneous as the fstab defines the parameters and accesses the remote share.

To summarize, there is no problem with Samba.  When it is first started it takes some time to for Samba to fully populate the database it uses to resolve names and find available IP addresses.  FWIW:  I configured this laptop exactly like yours and it takes about the same time to initially see the Public share.  This laptop has a Core 2 Duo 2Ghz CPU with 4GB RAM and a 128GB Micron MX100 SSD.

---

### Post by bab1 on 2015-08-17
> **TheFu said:**
> Looks like **smbtree** doesn't work the way it used to. I don't know when this changed (or perhaps the default options changed?), but it is less useful today for showing shares on a network.  

Can you explain this a little more?  How is it "***different***"?  What doesn't work as it used to?  I've seen no change in the way it works or displays information.  I'm interested in hearing what you see as different of changed with smbtree.
> 
I have a few different systems with samba shares here and none were shown running smbtree. That was unexpected to me.  It used to work, promise.

Every time I see this it is because something is not configured correctly.  How about posting the smb.conf file of one of the servers with a missing Samba share. 
> 

I have both DNS on the router (for the DHCP reservation systems) and /etc/hosts which tell all my systems about each other. Use a tiny ansible playbook to keep them all updated.
Samba really doesn't care how the hosts with DNS are listed.  You don't need to have fixed IP addresses with Samba at all.  Samba will search the list of methods set in the smb.conf file.  The default is```
name resolve order = lmhosts, wins, host, bcast
```Most casual setups pass on lmhosts and wins parameters while only using the last 2 types (host, bcast).

Guaranteed you don't need DNS or even hosts for a small single segment LAN when using Samba.  Most of the time bcast is the only lookup parameter needed.  The OP's setup is very much like that.  The only host lookup was the local machine.  All the computers were ID's.  I'd be curious to see your Samba setup for your LAN.

---

### Post by kurja on 2015-08-17
> **bab1 said:**
> 
Samba really doesn't care how the hosts with DNS are listed.  You don't need to have fixed IP addresses with Samba at all.  Samba will search the list of methods set in the smb.conf file.  The default is```
name resolve order = lmhosts, wins, host, bcast
```Most casual setups pass on lmhosts and wins parameters while only using the last 2 types (host, bcast).


I would suppose that if I edit smb.conf to try bcast first instead of last, it would speed things up. I'll try that when I get home in the evening. And thanks for your help!

---

### Post by bab1 on 2015-08-17
> **kurja said:**
> I would suppose that if I edit smb.conf to try bcast first instead of last, it would speed things up. I'll try that when I get home in the evening. And thanks for your help!
You need to add the line in the global section of the smb.conf file.  In the default configuration the line is not needed.  it is just assumed.  If you are going to add the line I would just add this```
name resolve order = bcast
```... all the rest is irrelevant as bcast will certainly find the 3 servers you have.

I don't think you will find any real difference however.  The problem is more due to the system populating the Master Browser with the needed data on initial use.

In fact the share is most likely mounted immediately.  To see the share do this```
ls -l /run/user/1000/gvfs
```
In other words, the share is mounted and available, but it takes some time for the browsing parts to work.

---

### Post by kurja on 2015-08-17
I marked the thread as solved. For me it's not a problem per se that it's slow to discover a shared folder in the lan, I'm just surprised that it can take that long, when viewing a couple file names in a folder over wired lan is about as quick as it was opening a video file on dial up this doesn't exactly seem like 2015 ;)

---

### Post by bab1 on 2015-08-17
> **kurja said:**
> I marked the thread as solved. For me it's not a problem per se that it's slow to discover a shared folder in the lan, I'm just surprised that it can take that long, when viewing a couple file names in a folder over wired lan is about as quick as it was opening a video file on dial up this doesn't exactly seem like 2015 ;)
Yes there are some things that we just have to live with.  On the other hand you could just open the file browser (files - aka = nautilus) and then just hit Ctrl+l and type this in the location bar```
smb://<server_name>/<share_name>
```...where <server_name> and <share_name> is whatever you have named them. For example, my laptop is named *maui*, my access is like this *smb://maui/public*.  This should be instantaneous.

---

