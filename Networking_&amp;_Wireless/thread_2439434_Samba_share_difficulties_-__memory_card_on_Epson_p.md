---
title: "Samba share difficulties -  memory card on Epson printer"
date: 2020-03-27
forum: Networking &amp; Wireless
---

### Post by Andrew F in Australia on 2020-03-27
Hi All,

I've never had to configure Samba before.

At home, I have a 6 year old Epson multi-function centre that (until about 4 years ago) used to work as a Samba Share if you entered a random anonymous password on connection.  

by doing this, I could access scans on the memory card.

With an upgrade to Ubuntu (v16.04 or earlier) it no longer allowed me to connect to the memory card on this printer.  Wasn't a biggie, but more a pain as to get a scan, I either had to log in to Windows (dual boot machine) or take the SD card out of the scanner and put it into my laptop.

Working from home now, (a high school teacher,) I've been trying to re-establish this connection as I'm needing to access the scanner many times a day.

(Started working with computers as an engineer in 1982 - am familiar with basic troubleshooting and command line, as everything was DOS back then - have been working with them daily ever since.)

Please see the below:

Any help or assistance you could provide to assist in this would be gratefully appreciated.

Regards,

A

Printer: Epson WF-7520

```
Setup on this machine is:
Printer Name EpsonFB6152
Connection Status: Wi-Fi-72Mbps
Signal Strength: Excellent
Obtain IP Address: Manual
IP Address:192.168.2.81
Subnet Mask: 255.255.255.0
Default Gateway:192.168.2.1
DNS Server Setting:Manual
Primary DNS Server:192.168.2.1
Secondary DNS Server: 
Proxy Server: Do Not Use
Wi-Fi Setup: Manual
Communication Mode: Infrastructure
SSID:not-you-2.4GHz
Security Level:WPA-PSK(AES)
Password:***************
File Sharing: Enable
File Sharing Mode: Read/Write
MAC Address: A4:EE:57:FB:61:

```

Output of 
ls - la samba
testparm
contents of /etc/samba/smb.conf
below


```
horace@horace-GE75-Raider-9SE://home/horace$ ls -la /samba/

total 12
drwxr-xr-x  3 root   root    4096 Mar 28 06:35 .
drwxr-xr-x 21 root   root    4096 Mar 28 06:35 ..
drwxrwxr-x  2 nobody nogroup 4096 Mar 28 06:35 anonymous

==========================================================================

horace@horace-GE75-Raider-9SE://home/horace$ testparm >> /mnt/Data/samba_for_forum.txt

Unknown parameter encountered: "dhs proxy"
Ignoring unknown parameter "dhs proxy"
Load smb config files from /etc/samba/smb.conf
Unknown parameter encountered: "dhs proxy"
Ignoring unknown parameter "dhs proxy"
Loaded services file OK.
Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions

# Global parameters
[global]
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    netbios name = UBUNTU
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    security = USER
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    usershare allow guests = Yes
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[sambashare]
    comment = Samba on Ubuntu
    path = /home/horace/sambashare
    read only = No


[anonymous]
    force user = nobody
    guest ok = Yes
    path = /samba/anonymous
    read only = No

==============================================================

$/etc/samba/smb.conf

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

# We want Samba to only log to /var/log/samba/log.{smbd,nmbd}.
# Append syslog@1 if you want important messages to be sent to syslog too.
   logging = file

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d

##### vvvvv MANUALLY ADDED THE BELOW 28 MAR 2020 vvvvvv #######
netbios name = ubuntu
security = user
map to guest = bad user
dhs proxy = no
##### ^^^^^^^^^^^^ END OF MANUALLY ADDED TEXT ^^^^^^^^^^^ #####

####### Authentication #######

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone server" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server

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
;   idmap config * :              backend = tdb
;   idmap config * :              range   = 3000-7999
# vvvvv Changed the network here to ours
;   idmap config 192.168.2.1 : backend = tdb
;   idmap config 192.168.2.1 : range   = 100000-999999
# ^^^^^^ Changed the nework to ours above 28 Mar 2020
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 means that usershare is disabled.
#   usershare max shares = 100

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

# MANUALLY ADD BELOW.
[sambashare]
comment = Samba on Ubuntu
path = /home/horace/sambashare
read only = no
browsable = yes

[anonymous]
path = /samba/anonymous
browsable = yes
writable = yes
guest ok = yes
read only = no
force user = nobody

==============================================================
$dir /home/horace
Desktop    Downloads  Pictures    sambashare  Templates
Documents  Music      Public    snap        Videos


```

---

### Post by TheFu on 2020-03-27
Just a wild guess, but have you tried forcing SMB1 connections?   Old printers seldom get patched like they should and even when they do, stuff like samba, usually isn't the updates.

i don't know enough about samba to suggest how to do that. Sorry.  Plus, it is just a guess.

---

### Post by Andrew F in Australia on 2020-03-28
Thanks Fu

Will try it out in a few hours and let you know.

Has anyone else had similar issues?

Regards,

A

---

### Post by TheFu on 2020-03-28
Just to be clear, my linux system mounts a samba v2.1 capable system using an fstab entry.  Here it is:

```
//172.22.22.14/D       /misc/D       cifs       x-systemd.automount,x-systemd.idle-timeout=600s,sec=ntlmv2,iocharset=utf8,rw,vers=2.1,uid=tf,gid=tf,file_mode=0664,dir_mode=0775,credentials=/etc/samba/win7lap-D.credentials        0       2
```
Lots of caveats go along with this line, it must be 1 line to start.  No line wrap allowed. Those are posted in these forums.  Don't forget the last 2 fields at the end of the line!  i exaggerated the spaces as a way to show certain parts of the line cannot have ANY spaces at all.
[https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156](https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156) has more details.

Probably don't want the sec=xxxxxx part and need to change the vers=1.0 along w/ the uid/gid to match yours.  ip address, mount location, and a credentials file.

To my knowledge, the smb.conf is only used for samba servers and has nothing to do with clients, so doubt it has anything to do with your Ubuntu system as a client trying to mount storage on a the printer which would be the samba server.

---

### Post by Morbius1 on 2020-03-29
To the extent the last Epson printer I worked on for someone matches yours you are in bit of a pickle.

Epson appears to be using a version of Samba that goes back a decade so you need to dumb things down a bit on the Ubuntu samba client.

What worked on that earlier Epson model was adding two options under the workgroup = WORKGROUP line in smb.conf on the Ubuntu client machine:
```
client lanman auth = yes
client ntlmv2 auth = no
```
Then restart smbd: 
```
sudo service smbd restart
```
THat will force the Ubuntu samba client to connect to the Epson server with a security mode ( share level security ) consistent with an earlier version of samba.

That worked for that person but he had earlier versions of Windows and Linux in his network as well.

The problem here is what happens when you introduce a modern SMB / SMBx / Samba server to your network. lanman is out so you will have a hard time connecting to them.

A better approach is a cifs mount for which you have more control and is independent of smb.conf and the samba client:

Create a mount point ... /mnt/EpsonMem
Then do a temporary mount just to make sure everything works:
```
sudo mount -t cifs -o guest,uid=1000,vers=1.0,sec=ntlm //epson-ip-address/share-name /mnt/EpsonMem
```
If that works you can add the equivalent to /etc/fstab:
```
 //epson-ip-address/share-name /mnt/EpsonMem cifs guest,uid=1000,vers=1.0,sec=ntlm,nounix,noauto,x-systemd.automount 0 0
```

---

### Post by Andrew F in Australia on 2020-03-29
Thanks Morbius (and Fu)

I didn't have much luck with your approach, Fu, but will have one last crack at it tonight.

Morbius - like the lateral approach -> will also try that out - looks simple and seems as though it could work. 

Regards,

A

---

### Post by Andrew F in Australia on 2020-03-31
THanks all,

Overnight, the latest Windows 10 update (19.09 - updating to current distribution) broke the shared folder access as well between Windows and the network drives.

Morbius - had NTFS compatibility errors thrown up repeatedly - every time I fixed one, another would come up.

At which point I gave up and bought a new multifunction printer as I'm trying to work from home.

Thanks again for all your help.

Regards,

A

---

