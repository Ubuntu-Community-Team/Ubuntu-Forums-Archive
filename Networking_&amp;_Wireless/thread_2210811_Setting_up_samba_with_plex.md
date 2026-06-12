---
title: "Setting up samba with plex?"
date: 2014-03-12
forum: Networking &amp; Wireless
---

### Post by diebodie on 2014-03-12
Trying to follow [this guide ]("http://askubuntu.com/questions/345087/how-do-i-add-a-network-drive-to-plex") to add a network drive to plex but when i go to run ```
mount-a 
``` i get ```
Mounting cifs URL not implemented yet. Attempt to mount smb://shared/
```. Googling the issue revealed that i need to use the servers IP, however i don't know how to find it. 

```
josh@josh-Aspire-V3-571 ~ $ ping smb://shared/
ping: unknown host smb://shared/

```

Going into my ASUS network map (192.168.1.1) only shows me the ftp server address for the external HDD. How can i find the media server ip address? 

Running ubuntu 13.10 w/asus RT-n66u fw ver :3.0.0.4.374_4561. Have a 2tb seagate external HDD connected directly to the n66u usb port.

---

### Post by papibe on 2014-03-12
Hi diebodie.

My guess you have a syntax problem with your fstab. You should use the IP address, not the smb url.

Could you post the content of your fstab?

Regards.

---

### Post by diebodie on 2014-03-12
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=b742be37-7ee5-488b-98b7-452743d36692 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
#UUID=888C-A2EB  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda4 during installation
#UUID=ea2e9217-d8cc-4337-8df3-360dbb6c6726 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=888C-A2EB	/boot/efi	vfat	defaults	0	1
 

 smb://shared/ /media/Plex cifs guest 0 0
```

I have no idea how to find the ip address for my smb server. The only information provided to me in the asus page is:

 Internet FTP link:
[ftp://josh.asuscomm.com](ftp://josh.asuscomm.com)
Share in LAN:
[ftp://192.168.1.1](ftp://192.168.1.1)

---

### Post by xicarusx on 2014-03-12
On your server at the command line type ifconfig. It will display information about each of your connections. Find the correct one and not the ip address. 

Alternatively you can use the hostname of the server. 

Here is a generic fstab entry for a SAMBA share. This is for a guest share with no password. 
//servername/sharename  /media/windowsshare  cifs  guest,uid=1000 0  0
^share location                      ^mount point.                  ^filesystem ^user

This is a generic fstab entry for a share that needs a user and password.
//servername/sharename  /media/windowsshare  cifs username=bob,password=1234,sec=ntlm
^Share location.                   ^ local mount point.         ^FS                      ^Username.       ^password ^securit

---

### Post by diebodie on 2014-03-12
Apreciate you pointing me in the right direction. I managed to finally obtain the ip address using ifconfig (why didn't i think of that). When i add it to my fstab however i get the following error: > mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


Here is my new fstab entry: 
> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=b742be37-7ee5-488b-98b7-452743d36692 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
#UUID=888C-A2EB  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda4 during installation
#UUID=ea2e9217-d8cc-4337-8df3-360dbb6c6726 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=888C-A2EB	/boot/efi	vfat	defaults	0	1
 
//192.168.1.96 /media/Plex cifs ,sec=ntlm,guest,uid=1000 0 0 


I tried reading the man on this but it's in chinese.. not literally of course.

---

### Post by xicarusx on 2014-03-12
Almost there. One last thing to change.
First make sure it is all on one line. Second you need to finish the location path.
Add the share name to the end of this part. Example if th samba share is named Files. 
//192.168.1.96/Files /media/Plex cifs guest, uid=1000, sec=ntlm 0 0

---

### Post by diebodie on 2014-03-12
[IMG]/home/jewbear/Desktop/screen 2.png[/IMG]Is there an easy means of finding the location path? I didn't specify it in the fstab thinking that leaving it as 192.168.1.96 would be equivalent to the location / in the file system. 

I've been trying everything i could guess. The path on my network is > smb://seagate/seagate_expansion_drive/ so naturally i tried finishing the location path with: (seagate, seagate_expansion_drive, seagate/seagate_expansion_drive) and every combination of caps in-between. All of these options yeild 

> Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


Any ideas? I feel like i'm missing something very obvious

[IMG]http://i57.tinypic.com/20pdi4o.png[/IMG]       [IMG]http://i60.tinypic.com/dmpg2h.png[/IMG]

---

### Post by xicarusx on 2014-03-13
It is the name you gave the share in smb.conf. Post the contents of /etc/samba/smb.conf and I will post the correct line for your fstab. :)

---

### Post by diebodie on 2014-03-13
Hmm, i don't remember configuring any samba files.. Apparently i sipped an important step. Dope! 

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
   server string = %h server (Samba, Linux Mint)

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

---

### Post by xicarusx on 2014-03-13
Ok I see no shares in your smb.conf. I see you can access the share via the browser, so I will go with that.
Run these commands.
sudo mkdir -p /media/Plex
sudo chown -R user:user /media/Plex     <----- Change the user parts to your Ubuntu username example if it was bill. bill:bill
sudo chmod -R 755 /mount/Plex

Replace your line in fstab with this. Copy and paste it
```
//seagate/Seagate_Expansion_Drive /media/Plex cifs [COLOR=#000000]guest, uid=1000, sec=ntlm 0 0[/COLOR]
```

Then ```
mount -a
``` if it gives you an error like only root can mount. Use ```
sudo mount -a
```

---

### Post by diebodie on 2014-03-17
Finally got it! Apparently, my /etc/samba/sbm.conf file got corrupted.. Following your guide and making a new sample file finaly got it mounted. Thank-you, I appreciate everything, i would have tore my hair out without your guidance.

---

