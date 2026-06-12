---
title: "Samba - network shares not visable - timeout on direct smb:// - smbtree returns null"
date: 2014-05-03
forum: Networking &amp; Wireless
---

### Post by kgb-technologies on 2014-05-03
Hi folks,

I hope someone can help me. I recently updated from ubuntu 13 to ubuntu 14.
When I did this all of my windows shares stopped showing up in the networking section.

I had a play around with samba settings and followed the '[Howto: Fix Windows share browsing issues]("http://ubuntuforums.org/showthread.php?t=1169149")' thread.
I've followed every point on this thread and couldn't figure it out.

After getting frustrated and deciding I wanted to play with KDE anyway, I formatted and installed Kubuntu 14.04.

This install didn't even have samba installed.
So I've installed samba and it's running.
Yet still no windows shares.

I am also not running a firewall on anything and can ping the computers I want to connect to.

I'm not sure what data to post to help in figuring it out.
smbtree returns absolutely nothing.

smbtree -d4 returns
```

kris@kgblinux:~$ smbtree -d4
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = WORKGROUP
doing parameter security = user
doing parameter netbios name = kgblinux
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
added interface eth0 ip=192.168.0.104 bcast=192.168.0.255 netmask=255.255.255.0
Enter kris's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
nmb packet from 192.168.0.75(35072) header: id=27301 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WORKGROUP<1d> rr_type=32 rr_class=1 ttl=300000
    answers   0 char .....K   hex 0000C0A8004B
Got a positive name query response from 192.168.0.75 ( 192.168.0.75 )
Connecting to 192.168.0.75 at port 445
nmb packet from 192.168.0.75(35072) header: id=2155 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=No trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=*<00> rr_type=33 rr_class=1 ttl=0
    answers   0 char .KGBSERVER         hex 064B4742534552564552202020202020
    answers  10 char ...WORKGROUP       hex 000400574F524B47524F555020202020
    answers  20 char   ...KGBSERVER     hex 20200084004B47425345525645522020
    answers  30 char      ..WORKGROUP   hex 20202020200400574F524B47524F5550
    answers  40 char       ...WORKGRO   hex 2020202020201E8400574F524B47524F
    answers  50 char UP      .....__M   hex 55502020202020201D040001025F5F4D
    answers  60 char SBROWSE__......N   hex 5342524F5753455F5F02018400E0CB4E
    answers  70 char ................   hex C69E9300000000000000000000000000
    answers  80 char ................   hex 00000000000000000000000000000000
    answers  90 char ...........   hex 0000000000000000000000
Connecting to 192.168.0.75 at port 445

 
```

My smb.conf file is as follows:

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
   netbios name = kgblinux

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


Any ideas would be fantastic

---

### Post by smss on 2014-05-04
Nobody read your post!
IT IS TOO LONG!
brief it and tell whats your problem directly.

---

### Post by kgb-technologies on 2014-05-04
> **smss said:**
> Nobody read your post!
IT IS TOO LONG!
brief it and tell whats your problem directly.

Freaking serious? How is anyone supposed to be able to help me with out the information?

I can't see windows shares + no information is completely useless.

---

### Post by bab1 on 2014-05-05
> **kgb-technologies said:**
> Hi folks,

I hope someone can help me. I recently updated from ubuntu 13 to ubuntu 14.
When I did this all of my windows shares stopped showing up in the networking section.

I had a play around with samba settings and followed the '[Howto: Fix Windows share browsing issues]("http://ubuntuforums.org/showthread.php?t=1169149")' thread.
I've followed every point on this thread and couldn't figure it out.

After getting frustrated and deciding I wanted to play with KDE anyway, I formatted and installed Kubuntu 14.04.

This install didn't even have samba installed.
So I've installed samba and it's running.
Yet still no windows shares.

I am also not running a firewall on anything and can ping the computers I want to connect to.

I'm not sure what data to post to help in figuring it out.
smbtree returns absolutely nothing...

Any ideas would be fantastic
Why respond to the previous poster/  Anybody can post from real help to complete idiots.

I didn't see any Samba shares defined in your smb.conf file.  Did you make them using the GUI (right click etc)?

The diag from the smbtree is good.  I usually use -d3 so there is a lot of stuff I don't see or need.  How about you run it again using ```
smbtree -d3
```

Make your posts a long as you need to.  The folks that understand this stuff are here most of the time.

I can tell you right now that some 14.04 installs have problems browsing for Samba shares and others don't.  Not sure what the answer is just yet.  Thats why I'm still using 12.04.  Can you access the shares directly via smb://ip-address/share_name ?

In theory the sharing and network browsing is the same whether you use 12.04 (Samba v3.6) or 14.04 (Samba 4.1).

---

### Post by kgb-technologies on 2014-05-05
Thanks so much for the reply BAB.

I'm really just trying to browse my windows network (as my home server is windows) -- It used to work so I'm confidant that the windows side isn't the issue. As a result I haven't bothered setting up any shares on my linux box -- Is this a requirement to get the whole thing to work?

smbtree -d3 returns  --- the 192.168.0.75 listed in the smbtree is actually the server that holds my shares. Which is making this extremely frustrating. As it obviously can see it.
> 
kris@kgblinux:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.0.104 bcast=192.168.0.255 netmask=255.255.255.0
Enter kris's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.75 ( 192.168.0.75 )
Connecting to 192.168.0.75 at port 445
Connecting to 192.168.0.75 at port 445


I might make a share and test if maybe that is required while I wait for a response. Once again, thanks! ^_^

Edit: When I try to connect directly (through dolphin) I get "Timeout on server"

Edit2: My server (192.168.0.75) can see my linux box on the network (in the homegroup) and I can access the share that I just made. But the linux box to the windows server still doesn't work.

---

### Post by kgb-technologies on 2014-05-05
Ok, so problem is solved. However I'll list what I did so if someone else has the same issue it doesn't drive them crazy.

First off -- I was mucking around on the net to find a working smb.conf -- as I was convinced this was the cause.

I found one someone claimed to fix the issue.

Backed up my current smb.conf
>  sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.orig 

replaced my current smb.conf with the one they claimed to work... restarted services (smbd and nmbd) ---- Still nothing

So I figured, because I'm still waiting for help here, I'll replace the 'working' not working smb.conf with my original. But here's the strange part - While looking for another solution I tried the command smbtree -N... Behold, a full list of computers on my network.
Now - It's obvious that smbtree didn't fix it -- The new smb.conf info I got off the internet didn't fix it -- The only thing I can think of is that somehow copying and the re-overwriting the original smb.conf changed the permissions??? Perhaps?

Eitherway, this was not the end of the issues.
I still encountered an issue getting to 192.168.0.75 ---- smb://192.168.0.75/tv ----> Timeout on server

So back to terminal I went with the following:
> 
smbclient -L 192.168.0.75
protocol negotiation failed: ERRnomem


There it was, an issue on the windows end -- at this point, omg so happy to be getting an actual error I can investigate.
This error is a lack of memory for the service on the windows machine -- Similar to a post made in the samba issuse post I referenced in my original post.
The solution - regedit -- change the following
Computer\HKLM\SYSTEM\CurrentControlSet\services\LanmanServer\Parameters
Size - from 1 to 3
Computer\HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management
LargeSystemCache - from 0 to 1
Restart windows machine.

My problem is now solved. Hopefully this may help someone else as well -- I honestly don't know what made the computers start showing up in smbtree again (permission change from the copy?) -- but it all works now.

---

### Post by bab1 on 2014-05-05
> **kgb-technologies said:**
> Ok, so problem is solved. However I'll list what I did so if someone else has the same issue it doesn't drive them crazy.

First off -- I was mucking around on the net to find a working smb.conf -- as I was convinced this was the cause.

I found one someone claimed to fix the issue.

Backed up my current smb.conf


replaced my current smb.conf with the one they claimed to work... restarted services (smbd and nmbd) ---- Still nothing

So I figured, because I'm still waiting for help here, I'll replace the 'working' not working smb.conf with my original. But here's the strange part - While looking for another solution I tried the command smbtree -N... Behold, a full list of computers on my network.

Now - It's obvious that smbtree didn't fix it -- The new smb.conf info I got off the internet didn't fix it -- The only thing I can think of is that somehow copying and the re-overwriting the original smb.conf changed the permissions??? Perhaps?

Samba allows for anonymous connections (guests).  If fyou had just hit enter at the prompt instead of trying to use your password you would have seen the same thing.  That means the server was fine.  Something you found out judging by the following comments. 
> 
Eitherway, this was not the end of the issues.
I still encountered an issue getting to 192.168.0.75 ---- smb://192.168.0.75/tv ----> Timeout on server

So back to terminal I went with the following:
```
smbclient -L 192.168.0.75
protocol negotiation failed: ERRnomem 
```

There it was, an issue on the windows end -- at this point, omg so happy to be getting an actual error I can investigate.
This error is a lack of memory for the service on the windows machine -- Similar to a post made in the samba issuse post I referenced in my original post.
The solution - regedit -- change the following
Computer\HKLM\SYSTEM\CurrentControlSet\services\LanmanServer\Parameters
Size - from 1 to 3
Computer\HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management
LargeSystemCache - from 0 to 1
Restart windows machine.

My problem is now solved. Hopefully this may help someone else as well -- I honestly don't know what made the computers start showing up in smbtree again (permission change from the copy?) -- but it all works now.
Great!  Sometimes is best to just accept that it works now even if you don't really know why.  :-)

---

