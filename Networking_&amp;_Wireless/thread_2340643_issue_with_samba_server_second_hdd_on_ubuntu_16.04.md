---
title: "issue with samba server second hdd on ubuntu 16.04 being accessible to an el capitan"
date: 2016-10-20
forum: Networking &amp; Wireless
---

### Post by manselem on 2016-10-20
Hi everyone. Having issue with samba server second hdd on ubuntu 16.04 being accessible to an el capitan osx client machine. The ubuntu primary ssd folders are able to have read/write access but when I added the second hdd I am getting an error from osx saying you dont have permissions to access this server. My folder is called Shared and the second hdd is located at sdb using ext4. Thanks in advance for any help

my etc/samba/smb.conf settings:
[global]

## Browsing/Identification ###

# usershare owner only = false

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no
issue with samba server second hdd on ubuntu 16.04 being accessible to an el capitan osx client machine
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


issue with samba server second hdd on ubuntu 16.04 being accessible to an el capitan osx client machine
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
;   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = no

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
# You may need to replace 'lpadmin' with the name of th# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=d4b91cd3-9a54-4108-be5e-a24625a3c5ee /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=E0C2-4F8E  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=95976ead-fd52-470a-b4c8-38e9fd9403a0 none            swap    sw              0       0
/dev/sdb /Shared ext4 defaults 0 0
e group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin


settings in etc/fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=d4b91cd3-9a54-4108-be5e-a24625a3c5ee /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=E0C2-4F8E  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=95976ead-fd52-470a-b4c8-38e9fd9403a0 none            swap    sw              0       0
/dev/sdb /Shared ext4 defaults 0 0

---

### Post by Morbius1 on 2016-10-20
Well, maybe it's just me but you don't have any shares defined in smb.conf.

Maybe you created them in Nautilus:
```
net usershare info --long
```

In any event I don't know what to make of this section at the end of smb.conf:
> # Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of th# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=d4b91cd3-9a54-4108-be5e-a24625a3c5ee /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=E0C2-4F8E  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=95976ead-fd52-470a-b4c8-38e9fd9403a0 none            swap    sw              0       0
/dev/sdb /Shared ext4 defaults 0 0
e group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin
Almost looks like /etc/fsab was inserted in smb.conf for some reason. Samba will just ignore those entries because it has no idea what they mean.

---

### Post by manselem on 2016-10-20
> **Morbius1 said:**
> Well, maybe it's just me but you don't have any shares defined in smb.conf.

Maybe you created them in Nautilus:
```
net usershare info --long
```

In any event I don't know what to make of this section at the end of smb.conf:

Almost looks like /etc/fsab was inserted in smb.conf for some reason. Samba will just ignore those entries because it has no idea what they mean.

Hey thanks for the help. So the part at the end was not in the smb.conf file. I pasted the etc/fstab file info thinking it may be pertinent information to anyone trying to help me. As far as Nautilus goes. I have used both. I have defined some shares in smb.conf but not that new folder Shared on the primary drive. I have used Nautilus to try to define the whole drive as allow access to group without a password. Basically anyone on this network i want to read/write. Isnt the smb.conf file only if you want to set different permissions for different groups? At any rate here is the output of net usershare info -l-long:

[Documents]
path=/home/mansel/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Downloads]
path=/home/mansel/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=n

info_fn: file /var/lib/samba/usershares/shared is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/linuxbackupdrive is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[HandM_Cloud]
path=/home/mansel/HandM_Cloud
comment=
usershare_acl=Everyone:F,
guest_ok=y

---

### Post by Morbius1 on 2016-10-20
> info_fn: file /var/lib/samba/usershares/shared is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/linuxbackupdrive is not a well formed usershare file.
info_fn: Error was Path is not a directory.
It can't find the path to the shared folder. Doesn't exist. At least it doesn't exist any longer. Maybe it did once.

Take a look at the share definition directly to find out where it's pointing. Is it pointing to /Shared:
```
cat /var/lib/samba/usershares/shared
```
[COLOR=#0000cd]
As a side note[/COLOR]: Not a big fan of doing this sort of thing:
>  /dev/sdb /Shared ext4 defaults 0 0         
sbd is a device not a partition. I realize may folks get away with this somehow but I would do it with a uuid number instead:
UUID=bunch-of-numbers /Shared ext4 defaults 0 0

---

### Post by manselem on 2016-10-20
> **Morbius1 said:**
> It can't find the path to the shared folder. Doesn't exist. At least it doesn't exist any longer. Maybe it did once.

Take a look at the share definition directly to find out where it's pointing. Is it pointing to /Shared:
```
cat /var/lib/samba/usershares/shared
```

Ok so this returns No such file or directory
[COLOR=#0000cd]
As a side note[/COLOR]: Not a big fan of doing this sort of thing:

sbd is a device not a partition. I realize may folks get away with this somehow but I would do it with a uuid number instead:
UUID=bunch-of-numbers /Shared ext4 defaults 0 0

I have updated using UUID=bunch-of-numbers plus replaced /Shared with none in hopes I would just get the disk drive to mount as a disk vs a folder. Honestly Im getting so lost at this point. The more I try the more I am messing things up. My goal is to be able to use the second hard drive as a samba share. the primary drive has this ability and I was able to achieve it through Nautilus but this method does not work for the second hard drive for me. 
Also under /etc/samba/smb.conf file in the part that deals with samba shares this code is here:
# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username

I interpreted this to mean if I dont create a user than anyone would logs into the server has access. And by the way Morbius1 I appreciate the help, I was looking through similar threads on here since 2009 at least you have been answering relatively the same question so sorry if this seems redundant but Im a newb and honestly trying to do the research. Thanks again for helping.

---

### Post by Morbius1 on 2016-10-21
In reverse order:

*** This section refers only to a specific type of share accessed in a specific way and does not nor should it relate to all samba shares:
> # By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
Don't do anything with that.

*** You lost me on this one:
> I have updated using UUID=bunch-of-numbers plus replaced /Shared with  none in hopes I would just get the disk drive to mount as a disk vs a  folder.

Let's do this in stages.

[1] Edit fstab to have this internal partition mount at boot time:

[a] Run this command to find the UUID number for your second "drive"
```
sudo blkid -c /dev/null
```
[b] Create the mount point if it is does not now exist:
```
sudo mkdir /Shared
```
[c] Then edit /etc/fstab to have this partition mount - something like this but with the UUID number you found in step [a]:
```
UUID=4638c269-d57d-44c0-9c0c-e7d7c330d33b /Shared ext4 defaults 0 0
```
When you boot into your system that partition should mount to /Shared.

[2] Now create a samba usershare of that folder through Nautilus just like you did with your other shares.

Then run this command to verify that it did so correctly:
```
net usershare info --long
```

---

### Post by manselem on 2016-10-21
> **Morbius1 said:**
> It can't find the path to the shared folder. Doesn't exist. At least it doesn't exist any longer. Maybe it did once.

Take a look at the share definition directly to find out where it's pointing. Is it pointing to /Shared:
```
cat /var/lib/samba/usershares/shared
```
[COLOR=#0000cd]
As a side note[/COLOR]: Not a big fan of doing this sort of thing:

sbd is a device not a partition. I realize may folks get away with this somehow but I would do it with a uuid number instead:
UUID=bunch-of-numbers /Shared ext4 defaults 0 0

> **Morbius1 said:**
> In reverse order:

*** This section refers only to a specific type of share accessed in a specific way and does not nor should it relate to all samba shares:

Don't do anything with that.

*** You lost me on this one:


Let's do this in stages.

[1] Edit fstab to have this internal partition mount at boot time:

[a] Run this command to find the UUID number for your second "drive"
```
sudo blkid -c /dev/null
```
[b] Create the mount point if it is does not now exist:
```
sudo mkdir /Shared
```
[c] Then edit /etc/fstab to have this partition mount - something like this but with the UUID number you found in step [a]:
```
UUID=4638c269-d57d-44c0-9c0c-e7d7c330d33b /Shared ext4 defaults 0 0
```
When you boot into your system that partition should mount to /Shared.

[2] Now create a samba usershare of that folder through Nautilus just like you did with your other shares.

Then run this command to verify that it did so correctly:
```
net usershare info --long
```

I'm not sure what I was doing wrong, but after following these steps one  by one everything worked! I think i was mixing a matching two different  methods getting poor results. Thank you for exposing me to some good  basic concepts to understand about using nautilus vs smb.conf to create  shares.

---

