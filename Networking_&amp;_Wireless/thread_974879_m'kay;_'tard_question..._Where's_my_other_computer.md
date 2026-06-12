---
title: "m'kay; 'tard question... Where's my other computers?"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by buccaneere on 2008-11-07
When I click on Places/network , I don't get all my machines coming up to log on to them. In fact, I get only the Windows machine, of 4 machines.

The router 'page' shows all 4 logged on.

What am I doing wrong? File share setting? Drive/partition share setting? Users and groups  setting? Holding my tongue wrong? :confused:

Tutorial? Link?
 
Thanks...

---

### Post by psycosmyth on 2008-11-07
silly thought but can the other boxes see this one?
what router u got?

---

### Post by buccaneere on 2008-11-07
Router is eHome100 ('tard router too).

No, I haven't pinged each machine yet... Where does each machine show it's IP address to ping?

Edit:
I found the IP addresses for my 4 machines on the router log page. 2 machines I have in front of me can each ping to the other 2 machines, but cannot ping each other. Ping response defaults to it's own address (unreachable)!!!

---

### Post by buccaneere on 2008-11-08
Anybody?

---

### Post by buccaneere on 2008-11-09
Anybody?

---

### Post by Iowan on 2008-11-09
For us REALLY dense ones...
Your network has 4 machines - 1 windows and 3 Ubuntu?
Which 2 machines are in front of you?
What do you mean by:> Ping response defaults to it's own address (unreachable)!!!

**ifconfig** on the Ubuntu machines should give that machine's IP address.  If one or more of the (Ubuntu) machines fails to get IP address from the router, it may get an avahi address instead (169.17X.X.X).

---

### Post by htmlland on 2008-11-09
I know its not related to the IP address possible problem but if you are using samba and windows computers ensure that they are all on the same workgroup. This usually defaults to "workgroup" but some dont; if they are not the same then your ubuntu box might not see them (i know mine didnt :P!).

Michael

---

### Post by buccaneere on 2008-11-09
> **Iowan said:**
> For us REALLY dense ones...
Your network has 4 machines - 1 windows and 3 Ubuntu?Yes, that's correct.



> **Iowan said:**
> Which 2 machines are in front of you? 2 Ubuntuboxes; IP's 192.168.0.105, and 192.168.0.103



> **Iowan said:**
> What do you mean by:
> Ping response defaults to it's own address (unreachable)!!!
I mean nothing - I read the 'return' wrong. 


This is the ping result from the 2 Ubuntuboxes in front of me.

This **is** what's returning, if FROM machine .103, I ping .105, the return is:
[HTML]chuckbhp@chuckbhp-laptop:~$ ping 192.168.0.105
PING 192.168.0.105 (192.168.0.105) 56(84) bytes of data.
From 192.168.0.103 icmp_seq=2 Destination Host Unreachable
From 192.168.0.103 icmp_seq=3 Destination Host Unreachable
From 192.168.0.103 icmp_seq=4 Destination Host Unreachable

--- 192.168.0.105 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3999ms
, pipe 3
chuckbhp@chuckbhp-laptop:~$ [/HTML]

***[COLOR="Blue"]FROM .105, .103 is 'unreachable. (and vice versa).[/COLOR]*** 

 

> **Iowan said:**
> **ifconfig** on the Ubuntu machines should give that machine's IP address.  If one or more of the (Ubuntu) machines fails to get IP address from the router, it may get an avahi address instead (169.17X.X.X).How do I determine if this is the problem?


I think htmlland might also have the solution, but I'm not sure how to make sure the Ubuntu machines are in 'WORKGROUP' (which they seem NOT to be).

???

---

### Post by tylermenezes on 2008-11-09
> **buccaneere said:**
> How do I determine if this is the problem?

You need to open a terminal (I think it's in Accessories -> Utilities or something like that in Ubuntu, I'm using Xubuntu now which has a different menu structure) and issue the command he gave you on all of the boxes. You should see their IPs somewhere there.

---

### Post by buccaneere on 2008-11-10
Now what do I know?

---

### Post by cariboo on 2008-11-10
What about the rest of the computers?

So far all you've shown use is the one  computer with an ip address of 192.168.0.103 which looks to be a laptop.

to find the ip address of your windows computer go to Start-->Run and type **cmd** then press enter. This will open a DOS window in that window at the prompt type:

```
ipconfig
```

this will show you it's ip address

Then  just post the ip address of all the computers.

Jim

---

### Post by htmlland on 2008-11-10
> **buccaneere said:**
> 
I think htmlland might also have the solution, but I'm not sure how to make sure the Ubuntu machines are in 'WORKGROUP' (which they seem NOT to be).


The workgroup setting is found in the config for samba. Im not too sure whereabouts the config is however :(. This is becasue the workgroup system is a windows thing not a linux thing so it will not be in the main linux config.

---

### Post by PreviousN on 2008-11-10
I'm interested in this solution. 

I no longer have this problem because I mount samba shares on boot using fstab and have static ips for my desktop computers...

But in the past I've been unable to fully solve this problem...So I'm interested. 

I do believe that the workgroup may something to do with it...

Post the output of this for your ubuntu boxes...
cat /etc/samba/smb.conf | grep workgroup

AND, compare the workgroup settings on the windows boxes.

---

### Post by buccaneere on 2008-11-10
> **cariboo907 said:**
> What about the rest of the computers?

So far all you've shown use is the one  computer with an ip address of 192.168.0.103 which looks to be a laptop.

to find the ip address of your windows computer go to Start-->Run and type **cmd** then press enter. This will open a DOS window in that window at the prompt type:

```
ipconfig
```

this will show you it's ip address

Then  just post the ip address of all the computers.

Jim

Yes, I thought of the other IP's, after logging onto my pillow for the night.

Is that all I need - IP's?

1, 3, 4 are Ubuntu. 1, 3, 4 are wireless.
2 is Windows, hardwire.

NOW, do I know why they don't see each other???

Hopefully, none of you are in my neighborhood...:-s

---

### Post by buccaneere on 2008-11-10
> **PreviousN said:**
> I'm interested in this solution. 

I no longer have this problem because I mount samba shares on boot using fstab and have static ips for my desktop computers...

But in the past I've been unable to fully solve this problem...So I'm interested. 

I do believe that the workgroup may something to do with it...

Post the output of this for your ubuntu boxes...
cat /etc/samba/smb.conf | grep workgroup

AND, compare the workgroup settings on the windows boxes.


Entire samba config file contents: (from .103 machine)
[HTML]

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
   workgroup = MSHOME

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
;   security = user

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
;   postexec = /bin/umount /cdrom[/HTML]

---

### Post by buccaneere on 2008-11-10
Anybody see anything wrong?

---

### Post by cariboo on 2008-11-10
Yes, you are not showing us the ip addresses from the individual computers. Go to each computer and run ifconfig for the ubuntu computers and ipconfig on the windows computer, note the ip addresses of each one and post them in your next post. Never assume because they are showing up on the router, that those are the actual ip addresses.

I had that happen last week,The client ip address list on my router showed that my server ip address was 192.168.1.103, I had set a static address of 192.168.1.200 and was connected via ssh using the static ip address. I clicked the refresh button and it changed the ip address to 192.168.1.106 with out changing the ip address of the server.

Jim

---

### Post by buccaneere on 2008-11-10
.105 machine (red desktop)...

.104 machine (purple desktop)...

and .103 machine again (3rd attachment)...

Windows machine: .101 machine[HTML]
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Owner>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.0.101
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1

C:\Documents and Settings\Owner>[/HTML]

So, NOW what do I know???

---

### Post by buccaneere on 2008-11-11
OoooK... Got the IP's identified. Anybody got any additional ideas?

---

### Post by Iowan on 2008-11-11
Stating the obvious, only the Windows machine seems to have an IP address for eth0.  The other 192.168.X.X addresses seems to be on purple's wireless (.104) and blue's eth2 (.103). Red has avahi address (169.254.X.X)on eth1 - no 192.168.0.105 address seen.

---

### Post by buccaneere on 2008-11-11
> **Iowan said:**
> Stating the obvious, only the Windows machine seems to have an IP address for eth0.  The other 192.168.X.X addresses seems to be on purple's wireless (.104) and blue's eth2 (.103). Red has avahi address (169.254.X.X)on eth1 - no 192.168.0.105 address seen.

Well, sometimes the answer IS derived from what's obvious, but I'm not seeing it.

Long ago, I had to change a Windows LAN to static from dynamic IP's, for this very reason.

What do I have to do now, to see, read, write, save, etc, to the other boxes?

---

### Post by Iowan on 2008-11-11
Sorry - I'm not suggesting that you missed anything - only that I'm not adding anything significant...
I recently saw a thread about a NIC that didn't communicate with a router. [http://ubuntuforums.org/showthread.php?t=974397]("http://ubuntuforums.org/showthread.php?t=974397")  Wondering if this is root of problem.

---

### Post by cariboo on 2008-11-11
What does /etc/network/interfaces on red look like. It should look something like this:

```
 cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
```

Also make sure your network cable is OK.

Purple looks to be wireless.

The 3rd machine, check to see if /etc/network/interfaces looks the same as above in the code block.

THe Windows computer looks OK.

Jim

---

### Post by buccaneere on 2008-11-11
Windows box is on hardwire.
Yup - purple is wireless desktop.
3rd machine? Interfaces? [HTML]
auto lo
iface lo inet loopback


iface eth1 inet dhcp
wpa-psk (PW)
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid cobweb

auto eth1

iface eth2 inet dhcp
wpa-psk (PW)
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid cobweb



auto eth2[/HTML]

'Red' network interfaces:
[HTML]
auto lo
iface lo inet loopback


#iface eth0 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


iface eth0 inet dhcp

iface eth1 inet dhcp
wpa-psk (mypassword)
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid cobweb

auto eth1[/HTML]

Thanks again there...

---

### Post by buccaneere on 2008-11-11
Here we go, from this book I have (weighs about 8 lbs / 1200 pages UGHHH)...

I. Set up hardware: Done.

II. Configure each system.
   NIC ID'ed and activation: Done.

   System info: System's IP address (computer? AP?). Subnet mask for   
                system's address. IP Address of the gateway. IP addresses of
                the nameservers. System's hostname.

   If you have a DHCP server, YOU DO NOT NEED THE PRECEEDING INFO.

 Q: Is my router set up as a DHCP server? Yes, 'Enable DHCP server is checked.

 DHCP server is broadcast based, so both client and server must be on the same subnet. Both are at 255.255.255.0. Done.

---

### Post by buccaneere on 2008-11-11
Each box gets info from server when logging on.

 dhcp3-client (package) must be installed... CHECK!

(skipping ahead - this is the client-server connection process)
-----------------------------------
back to system configuration...

Private IP ranges...
   understood...

I'm in the wrong chapter.:lolflag:

---

### Post by buccaneere on 2008-11-11
Chap 23; setting up NFS file sharing systems (I presume this is what I need to do, since I want to read, write, save to, etc, other computers on my network).

Client set-up:
   Install nfs-common (package). Marked, applied, downloading... Done.

Q: Now must I make each machine an NFS server also? That is the next section in the NFS chapter?

---

### Post by buccaneere on 2008-11-11
I'm presuming each machine must have 'NFS client', and 'NFS server' packages installed. Done.

I now have new 'Places' to log in, but they are not specified.

???

After client and server package installation, directory heirarchies must be 're-listed', be re-starting the nfsd daemon thusly:

sudo /etc/init.d/nfs-kernel-server restart

---

### Post by buccaneere on 2008-11-11
Okay... 

"Securing a server from remote system access."

Are each of my machines on my LAN considered 'remote', to the  other 3 machines???

Apparently, I must modify files **/etc/hosts.allow**, and **/etc/hosts.deny**, to facilitate NFS functioning.

Any input here?

---

### Post by buccaneere on 2008-11-11
AHA!

I betcha' this file must be modified:[HTML]

# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID[/HTML]

Am I correct?

Is there an 'All except for...' entry? Or is that what the 'Allow' file is for?

What is the format of an entry in either file??? Begins with'**#**'?

---

### Post by buccaneere on 2008-11-11
Share creation errors:

What does each mean?

---

### Post by cariboo on 2008-11-12
You should really slow down a bit, it's hard to follow what you are doing.

Purple?

> uto lo
iface lo inet loopback


iface eth1 inet dhcp
wpa-psk (PW)
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid cobweb

auto eth1

iface eth2 inet dhcp
wpa-psk (PW)
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid cobweb


Change to this:

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-psk (PW)
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid cobweb

```

Red?

> auto lo
iface lo inet loopback


#iface eth0 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


iface eth0 inet dhcp

iface eth1 inet dhcp
wpa-psk (mypassword)
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA


Change to:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

Your setup was a dog's breakfast, you have things only needed for wireless and more interfaces than you would ever need. For network basics have a look here:

[http://tldp.org/HOWTO/NET3-4-HOWTO.html](http://tldp.org/HOWTO/NET3-4-HOWTO.html)

Jim

---

### Post by buccaneere on 2008-11-12
Thanks again there Jim...

I like knowin' what I'm doin' as I go (see signature), since that helps if/when I have to do it again, and since I can help others in the future. AND, if something doesn't work I can reverse what I've done. 

Yes, I'm aware of 'extra' interfaces on some machines. They are of default creation. 




I changed 'red' interfaces. I didn't like the new config, but tried anyway. It dumped me pronto from the connection. I re-started networking twice, and no-go. I did a backup of original configuration, and we're back up with 'red'.

So I see we are trying to remove extra interfaces from configuration. Copy on that part...

I'll post back up later...

---

### Post by TechnoJunky on 2008-11-12
any chance you've modified the hosts files on any of your computers?  I did that and somehow did it incorrectly.  The result was the same as you are having "destination host unreachable".  I could ping all other computers, but not the one that I added to the hosts file.  Check it and make sure that nothing other than the local computer's info is in it.

---

### Post by buccaneere on 2008-11-12
> **TechnoJunky said:**
> any chance you've modified the hosts files on any of your computers?  I did that and somehow did it incorrectly.  The result was the same as you are having "destination host unreachable".  I could ping all other computers, but not the one that I added to the hosts file.  Check it and make sure that nothing other than the local computer's info is in it.

I don't think so TechnoJ... Everything is as default as can be. I tried adding the 'users' of each machine to the other machines, but that apparently wasn't what caused 'unreachable-ness', so I reversed that too (till I get a 'user denied', or something like that).

And Jim; how can 'extra' interfaces prevent ping response?

---

### Post by buccaneere on 2008-11-12
OK; I got the interfaces files 'cleaned up' in 2 boxes:
What do I know now?

---

### Post by buccaneere on 2008-11-12
OKAY... Progress. On these 2 machines in front of me red.105, blue.103, I'm gettin' a ping response from each other.

So are we now looking for 'users and groups' settings mods? Or a 'file share' issue? See post 31 above 'share creation errors'...

???

---

### Post by buccaneere on 2008-11-12
More progress (blue.103 machine)

Appearing in its own network locations tho'...

Red .105 machine doesn't appear. 

Nor does red.103, or blue.105 it appear on red.105 network locations...

---

### Post by buccaneere on 2008-11-12
Even more progress...

The share creation error seems to be resolved on blue.103. One folder accepted share setting.

Wish I knew how I fixed it - got 3 more machines to do here uh huh...

---

### Post by buccaneere on 2008-11-13
Okay; what package is this called, that I need to install???

This is red.105 box.

Holy COW - what a REAL 'tard. It says right there "Install service" Dang.

(It was a different message yesterday yup - see post 31)

---

### Post by buccaneere on 2008-11-13
No joy.

---

### Post by buccaneere on 2008-11-13
Okay - why was I able to do a file share mod GUI on one machine, and apparently it has to be done CLI on another machine???

All user permissions are identical to the other machine.

---

### Post by buccaneere on 2008-11-13
Uh huh, Uh HUH!!! Some LAN network joy!

There's lots of progress goin' down here yup!

The share error was a bug. Don't know why it was on one box, and not the other...

---

### Post by buccaneere on 2008-11-13
Again, NO joy.

On the blue.103 machine, the network locations has reverted to 'Windows network'. Blue.103 has disappeared from its own network locations list.

Hello Vista and XP...[IMG]http://www.stripers247.com/phpBB2/images/smilies/10187.gif[/IMG]

Ubuntu [IMG]http://www.stripers247.com/phpBB2/images/smilies/10186.gif[/IMG]

---

### Post by buccaneere on 2008-11-13
Okay, I checked the interfaces file; no funny business dog's breakfast interface list, like Jim was sayin'; it's still clean.

So I restarted the NFS kernel server, and no reloading of blue.103 in its own network locations. 

All I did was restart the machine, to see if that solved the problem, just as the restart for the other machine's red.105 bug fixed it.

Not cool.

Time to take a break...

Any ideas? ANY body???

---

### Post by buccaneere on 2008-11-13
Okay, this AM, the situation is reversed from last night.

Blue has itself, and red, and 'Windows network' showing up in network locations.

Red has 'Windows network'.

Anybody here?

---

### Post by buccaneere on 2008-11-13
I restarted both machines.

Red.105 still brings up no locations (except 'Windows Network (might be a hint)).

Blue.103 has lost locations - itself, and red, and still shows 'Windows Network' (I think I'm gettin' a hint here uh huh).

Anybody?

---

### Post by buccaneere on 2008-11-13
On blue.103 :

Well, the network location / filepaths are changed, and I have changed nothing.

Whereas I once had this (first attachment), I now have only 'Windows Network' appearing. (Places / network)

HOWEVER, if I double-click 'Windows Network', it open to 'MSHOME', and again, THAT opens to my 2 machines in front of me blue.103, and red.105 (second attachment).

Why have the filepaths / network paths changed? Will they change back on a whim also? Why is this doing this? Where are my computers? What's wrong? What's right?

Anybody?

---

### Post by buccaneere on 2008-11-13
wow

Another click, another trick. Why am I not surprised?

Where did this icon come from?

---

### Post by buccaneere on 2008-11-13
Let's go back to the book again, since progress seems to have come to a standstill.

Chap 24 - Samba. I'm choosing this section since the OCCASIONAL appearances of one machine, in the other, has begun with 'smb://' in the location path. AND, because access **TO** the shared files in this machine, **FROM** this machine, appears to be following proper protocols - filepath, password prompt, etc. (if only the other machines too:confused:)

Cross your fingers. Cross yer piggies. Cross your eyes, yer hair, yer teeth, cross 'em ALL...

Samba package necessities:
samba...  done
smbclient...   done
smbfs...    [COLOR="Red"]WAS NOT INSTALLED on blue.103[/COLOR]  now done
swat... optional, useful ...     

===================================================================
Time out again...

I tried a different approach  here...
A new level of success LOGON, but no image display (that's all that's in the folder, is images)

Ideas?

EDIT: Exact same result for the other machine red.105, to access blue.103 shared files.

---

### Post by buccaneere on 2008-11-13
Images are now accessible from each other computer.

I didn't do anything.

[IMG]http://www.digitalcorvettes.com/forums/images/smilies/smilie_thud.gif[/IMG]

---

### Post by buccaneere on 2008-11-13
I moved a text file into the pictures folder about 15 minutes ago. I could not open it, for permission / authority reasons.

Now, I can open it.

I didn't do anything. again...

:confused:

How long will it last?

---

### Post by jonobr on 2008-11-13
Hello

Stupid suggestion for you, IMHO,
I would recommend taking all you have learned and summarize in one succinct post with observations, relevant steps taken , conclusions and current status.

The thread is laid out like a ransom note.
No fault of yours as you are learning as you go, but its hard to follow whats happened and where you are now.
It may even be worth starting a new thread as you may or may not be experiencing something new or different from the start.
Somebody who may have the issue may not have the time to read through the entire thread..

I would also recommend keeping an eye on posting screencaps of your entire desktop.
You may inadvertently post personal info...

---

### Post by buccaneere on 2008-11-13
Yes, I'm trying to keep tabs on what I'm doing, to do exactly that - summarization thread. You should have seen the threads / info assembly process by which I had a car tech how-to thread made into a sticky. THAT was ugly.

Finished product here:
[http://forums.corvetteforum.com/c4-tech-performance/1848666-headlight-repair-w-pic.html](http://forums.corvetteforum.com/c4-tech-performance/1848666-headlight-repair-w-pic.html)

And I have checked for personal info, passwords, mac addresses, etc, ... Did I miss something?

Thanks!

---

### Post by buccaneere on 2008-11-13
Where does this go, in my samba configuration file?

'net usershare' returned error 255: net usershare add: cannot share path /home as we are restricted to only sharing directories we own.
	**[COLOR="Red"]Ask the administrator to add the line "usershare owner only = False" [/COLOR]**
	to the [global] section of the smb.conf to allow this.

[HTML]


#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

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
;   security = user

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
;   postexec = /bin/umount /cdrom[/HTML]

---

### Post by buccaneere on 2008-11-13
> **cariboo907 said:**
> You should really slow down a bit, it's hard to follow what you are doing.


Jim

Hey there Jim!

Hope I'm not goin' too fast for me here...:)

Have I completely lost ya'? Me too! But we're makin' some semblance of progress here uh huh!

Anyway, I think we have only a samba config issue left to solve. That is, until I get on the 2 machines in the other room.

When I do those, I'm gonna' try to re-compile this thread into another. We'll see how it goes.

So back to the chap 24; samba configuration...

From post 50:[HTML]
Let's go back to the book again, since progress seems to have come to a standstill.

Chap 24 - Samba. ...

Samba package necessities:
samba... done
smbclient... done
smbfs... WAS NOT INSTALLED on blue.103 now done
swat... optional, useful ...  [/HTML]

swat...    done
openbsd-inetd...   done
samba-doc...   done
samba-doc-pdf...    done

M Sobel, the book's author, says nothing of package 'samba-dbg'. It has the Ubuntu symbol next to it in Synaptic, so I am installing it also.

samba must be re-started after configuration:
[HTML]sudo /etc/init.d/samba restart[/HTML]

Both machines in front of me have all samba packages, necessary and optional.

Restart both machines, and check ...

---

### Post by buccaneere on 2008-11-13
Both machines in front of me can now access/read shared files in the other computers. The second machine was a little slow getting going, but now is allowing access. 

I have not yet tried to write or save to shared folders.

The login process needs improvement:
Places/computer/go (from menubar) /location (from 'go' dropdown)/ (in address bar) smb://[IPAddress] ,  then login to the folder, and login to the file; username and password, twice UGH.

I imagine that users and groups setting will reduce this process. Are there also filepath shortcuts that I can create? Can I also change the username in the 3 Ubuntuboxes to the same name, en mass? 

Break time. Will try to re-compile the thread as I configure my other Ubuntubox, and Windowsbox tomorrow...

---

### Post by buccaneere on 2008-11-14
They're gone.

Didn't do a thing, except shutdown, and tonight they're gone.

Where's the computers?

Why is this happening like this?

---

### Post by buccaneere on 2008-11-14
Okay... Troubleshooting the 2 machines that were sharing properly  yesterday...

Restarted samba
sudo /etc/init.d/samba restart
Did not work.

---

### Post by buccaneere on 2008-11-14
The 2 that have already been configured for samba sharing have found each other, after several attempts to establish connectivity.

Any ideas?


The second machine, as I attempt to open an accessible file, has just prompted me to allow an app to access my keyring. Yes, it is okay. But my question is, "What is keyring"?

---

### Post by buccaneere on 2008-11-15
Keyring is gonna' have to wait. That, like username and password, seem to come up only after total connectivity.

One thing I've noticed when there is total connectivity - an icon presents itself on the desktop, in much the same way as a mounted removable drive.

Is this connectivity problem related to mtab / fstab configuration???

I have restarted both machines which are configured, without re-starting samba. Let's see if they can connect...


EDIT:
The first machine blue.103 connected right away to machine red.105.
> 
Places/computer/go (from menubar) /location (from 'go' dropdown)/ (in address bar) smb://[IPAddress]

The red.105 logged right into the blue.103 machine. Both prompted for necessary username and password. No revelation.

At this boot, neither machine had an icon on the desktop for the network LAN location. After loggin' each way, both machines had a desktop icon for the other machine's networked (shared) files.

So the question is unanswered from above:
Is this connectivity problem related to mtab / fstab configuration???

I have figured nothing out...

---

### Post by buccaneere on 2008-11-15
Let's try LAN inside speed, vs server speed (outside)...

==================

Red pinging blue:
chuckdl@chuckdl-laptop:~$ ping 192.168.0.103
PING 192.168.0.103 (192.168.0.103) 56(84) bytes of data.
64 bytes from 192.168.0.103: icmp_seq=1 ttl=64 time=38.3 ms
***
64 bytes from 192.168.0.103: icmp_seq=18 ttl=64 time=25.8 ms

--- 192.168.0.103 ping statistics ---
18 packets transmitted, 18 received, 0% packet loss, time 17010ms
rtt min/**[COLOR="Red"]avg[/COLOR]**/max/mdev = 18.598/**[COLOR="Red"]64.477[/COLOR]**/114.430/30.411 ms
chuckdl@chuckdl-laptop:~$

===============================

blue ping red:
chuckbhp@chuckbhp-laptop:~$ ping 192.168.0.105
PING 192.168.0.105 (192.168.0.105) 56(84) bytes of data.
64 bytes from 192.168.0.105: icmp_seq=1 ttl=64 time=6.66 ms
***
64 bytes from 192.168.0.105: icmp_seq=19 ttl=64 time=8.11 ms

--- 192.168.0.105 ping statistics ---
19 packets transmitted, 19 received, 0% packet loss, time 18000ms
rtt min/**[COLOR="Red"]avg[/COLOR]**/max/mdev = 4.075/**[COLOR="Red"]6.148[/COLOR]**/9.550/1.704 ms
chuckbhp@chuckbhp-laptop:~$


Does ping time discrepancy tell me anything? Maybe only hardware difference? Or network config settings? BOTH???:confused:

===============

red ping yahoo.com:
--- yahoo.com ping statistics ---
19 packets transmitted, 19 received, 0% packet loss, time 18004ms
rtt min/**[COLOR="Red"]avg[/COLOR]**/max/mdev = 127.080/**[COLOR="Red"]127.639[/COLOR]**/128.960/0.594 ms
chuckdl@chuckdl-laptop:~$

===================

blue ping yahoo.com:
--- yahoo.com ping statistics ---
19 packets transmitted, 19 received, 0% packet loss, time 17991ms
rtt min/**[COLOR="Red"]avg[/COLOR]**/max/mdev = 126.016/**[COLOR="Red"]126.941[/COLOR]**/127.564/0.455 ms
chuckbhp@chuckbhp-laptop:~$


Looks like both machines have equal link speed to an external target, but when pinging to each other, blue is faster by a factor of 10.

Does this tell me anything? Seems to me that this indicates configuration discrepancies, not hardware...

---

### Post by buccaneere on 2008-11-16
Skipping ahead to troubleshooting in Samba chapter in Ubuntu bible...

(both machines (blue, red) are in front of me again, neither is connecting to the others' shares at the moment, and neither has a location icon **[COLOR="Red"]on the desktop[/COLOR], which seems to always indicate active share connection**)

1. Restart Samba daemons.
   sudo /etc/init.d/samba restart

================================================

On red, after restarting samba, network location icons did not access the shares (NOT the same icons as the ones referred to above!!!).

On blue, I attempted the connection differently:
> Places/computer/go (from menubar) /location (from 'go' dropdown)/ (in address bar) smb://[IPAddress] 
Blue displayed red's shares promptly, and after username/password login to red's shares, a location icon then appeared on blue desktop.

After blue is accessing to red's shares, red STILL IS NOT displaying blue's *locations*. Manual address entry is not working either:> Places/computer/go (from menubar) /location (from 'go' dropdown)/ (in address bar) smb://[IPAddress]

Red cannot ping blue right now; unreachable.

---

### Post by buccaneere on 2008-11-16
troubleshooting samba 

2. Run testparm to check syntax of samba config file:

==============================================

Both of mine are default config'ed, so there can be no problem there. Apparently, if all is well, then services will load OK. An error will return an unknown error ignored.

Blue and red service definitions are identical, no errors noted.

=============================

3. Ping requests; done. Problem noted; now what???

Interesting note about ping in Ch 10 networking: 
"Use ping6 to test IPv6 networks".
Wonderful. Does samba use protocol 6?

---

### Post by buccaneere on 2008-11-18
Ping failure section had no leads. After that is a reference to NFS client setup, which I began earlier...

I think my ping failure is attributable to this:

(on blue)
> chuckbhp@chuckbhp-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          [COLOR="Red"]Access Point: Not-Associated[/COLOR]   
          THIS
chuckbhp@chuckbhp-laptop:~$

I think this is why red does not see blue.


EDIT:
OR, it might be this:
> 
chuckbhp@chuckbhp-laptop:~$ ifconfig
eth0      ...

eth2      Link encap:Ethernet  HWaddr 00:1a:73:59:97:e1  
          inet addr:192.168.0.**[COLOR="Red"]100[/COLOR]**  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe59:97e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48620 errors:0 dropped:0 overruns:0 frame:30321
          TX packets:19999 errors:27 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29431360 (28.0 MB)  TX bytes:4119731 (3.9 MB)
          Interrupt:9 

lo        ...

chuckbhp@chuckbhp-laptop:~$

HOW WHY WHEN DID MY IP CHANGE FROM .103 TO .100??? :confused::confused::confused:

And how do I re-establish association with my access point???

---

### Post by buccaneere on 2008-11-18
Consistent file share connection is at hand here ...

This address bar entry mounts my other machines' shared files:

> Places/computer/go (from menubar) /location (from 'go' dropdown)/ (in address bar) smb://[IPAddress of target share] 

and then places a location icon on the desktop. 

I presume that NFS client and NFS server packages in their default configurations are sufficient, (remember to re-start nfsd daemon, which I think re-lists directory hierarchies

sudo /etc/init.d/nfs-kernel-server restart ) 

and samba as well, in its default configuration is sufficient

Samba package necessities:
samba... done
smbclient... done
smbfs... WAS NOT INSTALLED on blue.103 now done
swat... optional, useful ...

swat... done
openbsd-inetd... done
samba-doc... done
samba-doc-pdf... done

So now let's try to make this share mount an 'auto-mount' process... 

[COLOR="Red"]Q:[/COLOR] Is this an 'export / import' file configuration?

And can we shorten the login / access without compromising security???

Does anyone have any help? Is anyone getting anything from this? Is there any need to re-compile this thread, as I am considering?

---

