---
title: "Ubuntu 14.04 can't see samba shares across network"
date: 2015-09-25
forum: Networking &amp; Wireless
---

### Post by mzak on 2015-09-25
Hi everyone,

I've had no end of issues getting my Ubuntu box to share out 2 folders across my network under 14.04.  Sometimes it works, then it falls over usually after restarting.  It seems to be more reliable when I limit access to my samba user 'zak'.  

On the network I have the following machines, which currently respond as follows:
 - another Ubuntu 14.04 box.  From that box, smbclient (SERVER IP) gives an IO timeout, and smbclient (SERVER DNS) gives NT_STATUS_UNSUCCESSFUL.  
 - a WDTV that currently can't see the server
 - a WIN7/KODI box that also can't see the server

As shown in smb.conf, TeraII and TeraIII are ntfs drives that are configured in fstab to be owned by '1000', me. 

When I do an smbclient (DNS) from the server itself it lists my shares and workgroup of WORKGROUP and all is seemingly well there.  Firewall is enabled and 137, 138, 139 and 445 are all open.

First post, please bear with me.  Looking to get it sorted and hopefully understand what's creating the bizarre issues I'm experiencing.

Thanks

Zak

---

### Post by mzak on 2015-09-25
Here's my smb.conf

```

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = WORKGROUP


# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;    wins support = no


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
;    passdb backend = tdbsam

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
;    usershare max shares = 100

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
;    guest ok = no
;    read only = yes
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

[MoviesII]
    path = /media/zak/TeraII/Movies
;    writeable = no
;    browseable = yes
    valid users = zak

[MoviesIII]
    path = /mnt/TeraIII/MoviesIII
;    writeable = no
;    browseable = yes
    valid users = zak

[Music]
    path = /mnt/TeraIII/Music
;    writeable = no
;    browseable = yes
    valid users = zak
```

---

### Post by bab1 on 2015-09-26
> **mzak said:**
> Hi everyone,

I've had no end of issues getting my Ubuntu box to share out 2 folders across my network under 14.04.  Sometimes it works, then it falls over usually after restarting.  It seems to be more reliable when I limit access to my samba user 'zak'.  

On the network I have the following machines, which currently respond as follows:
 - another Ubuntu 14.04 box.  From that box, smbclient (SERVER IP) gives an IO timeout, and smbclient (SERVER DNS) gives NT_STATUS_UNSUCCESSFUL.  
 - a WDTV that currently can't see the server
 - a WIN7/KODI box that also can't see the server

As shown in smb.conf, TeraII and TeraIII are ntfs drives that are configured in fstab to be owned by '1000', me. 

Qwned by 1000 = zak.  Is the user zak have uid = 1000?  Post the output of ```
cat /etc/fstab
```
> 

When I do an smbclient (DNS) from the server itself it lists my shares and workgroup of WORKGROUP and all is seemingly well there.  Firewall is enabled and 137, 138, 139 and 445 are all open.

First post, please bear with me.  Looking to get it sorted and hopefully understand what's creating the bizarre issues I'm experiencing.

Thanks

Zak
Post the output of the following commands```
smbtree -d3

sudo pdbedit -L

ls -l /media/zak/TeraII

ls -l /mnt/TeraIII/
```

---

### Post by mzak on 2015-09-26
Thanks for assisting

> **bab1 said:**
> Qwned by 1000 = zak.  Is the user zak have uid = 1000?  Post the output of ```
cat /etc/fstab
```
```

zak@ZAKLIN:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb6 during installation
UUID=1ce5eb55-fde6-4cad-adf1-48fbfb9b9e37 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=f13ccc43-0f65-450c-8f56-f5ecb502df6d none            swap    sw              0       0
LABEL=TeraIII /mnt/TeraIII auto uid=1000,gid=1000,dmask=027,fmask=137,x-gvfs-show 0 0

```
Sorry, it was set up for TeraIII, not TeraII.  Happy however to leave TeraII out of the equation from here on in.

> 
Post the output of the following commands 


```

smbtree -d3:
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.0.101 bcast=192.168.0.255 netmask=255.255.255.0
Enter zak's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f4220deba10] mpx_fde[(nil)] fd[7] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f4220deba10] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f4220deba10] mpx_fde[(nil)] fd[7] - disabling

sudo pdbedit -L:
zak:1000:zak

ls -l /media/zak/TeraII:
drwx------ 1 zak zak    77824 Dec  5  2014 Movies
drwx------ 1 zak zak     4096 Mar  8  2015 Music
drwx------ 1 zak zak     4096 Dec 24  2013 Pictures
drwx------ 1 zak zak     4096 Apr 27 13:57 Pivotal
and so forth...

ls -l /mnt/TeraIII
drwxr-x--- 1 zak zak   4096 Sep 22 19:40 Documents
drwxr-x--- 1 zak zak  20480 Sep 13 20:09 MoviesIII
drwxr-x--- 1 zak zak      0 Sep  8 22:31 Pictures
and so forth...




```

---

### Post by bab1 on 2015-09-26
> **mzak said:**
> Thanks for assisting

```

zak@ZAKLIN:~$ cat /etc/fstab
...
LABEL=TeraIII /mnt/TeraIII auto uid=1000,gid=1000,dmask=027,fmask=137,x-gvfs-show 0 0

```
Sorry, it was set up for TeraIII, not TeraII.

You have mounted only the one partition via fstab.  The other is mounted via udev rules.  This partition is only accessible by by the user zak (uid=1000)
> 

```

smbtree -d3:
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.0.101 bcast=192.168.0.255 netmask=255.255.255.0
Enter zak's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f4220deba10] mpx_fde[(nil)] fd[7] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f4220deba10] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f4220deba10] mpx_fde[(nil)] fd[7] - disabling

```

Not quite sure yet what is happening here yet.  Did you enter your password or just hit enter (anonymous)?   Try *_anonymous_* access and post back here the results.
> 
```
sudo pdbedit -L:
zak:1000:zak

```

The user zak is the only Samba user.  To use Samba effectively all users need a Linux account (adduser) and a Samba account (smbpasswd -a).
> 
```

ls -l /media/zak/TeraII:
drwx------ 1 zak zak    77824 Dec  5  2014 Movies
drwx------ 1 zak zak     4096 Mar  8  2015 Music
drwx------ 1 zak zak     4096 Dec 24  2013 Pictures
d[COLOR="#FF0000"]**rwx**[/COLOR]**[COLOR="#0000FF"]------[/COLOR]** 1 [COLOR="#FF0000"]**zak**[/COLOR] **[COLOR="#0000FF"]zak[/COLOR]**     4096 Apr 27 13:57 Pivotal
and so forth...

```

The user zak is the only user with access (see rwx above in red).  The group-user and others have no permissions to do anything (see blue above)
> 
```

ls -l /mnt/TeraIII
drwxr-x--- 1 zak zak   4096 Sep 22 19:40 Documents
drwxr-x--- 1 zak zak  20480 Sep 13 20:09 MoviesIII
drwxr-x--- 1 zak zak      0 Sep  8 22:31 Pictures
and so forth...

```
The same applies here.  Only the user and user-group zak (uid=1000 and gid=1000) have any permissions.

What users do you want to have access.  If you want "guest" access (e.g anyone on your network) then you need to change permissions for the others group (all others) to rwx.  It might look something like this ```

drwxrwxrwx 1 zak zak   4096 Sep 22 19:40 Documents

```

I'm not a big believer in having "guest" access however.  All guest access files created are owned by nobody:nogroup.  Both the user and group are system users.  You end up fighting to keep the ownership and permissions correct.  If you want to share a directory in you own home directory you can certainly do that.  I do that on an temporary ad hoc basis.  This type of guest share I delete after the guest is no longer on the network.

I know this has not given you a direct answer.  I think you need to rethink how (and why) you are sharing these directories.  The NTFS directories are problematical.  Since you have to set the permissions at mount time at the partition level you have to (a) mount both of them using fstab and (b) decide what user-group you want to have permissions to the all the partition's directories.  Have you thought about backing up the data and reformatting the partition to ext4?

Do you have backups of all your data?  If not you should seriously think about creating a backup routine.  Over the years I have had a few disks crash and data accidentally deleted, but I have never permanently lost any data.  Backup, Backup, Backup!

---

### Post by mzak on 2015-09-26
> **bab1 said:**
> You have mounted only the one partition via fstab.  The other is mounted via udev rules.  This partition is only accessible by by the user zak (uid=1000)
I just need to access the share on the media players and figured that setting up the one samba user 'zak' would be enough.  All i've been doing when my shares are discoverable is logging in with 'zak' + pw and away we go.  I don't need any other users to access the shares.


> 
Not quite sure yet what is happening here yet.  Did you enter your password or just hit enter (anonymous)?   Try *_anonymous_* access and post back here the results.

Hmm yeah I tried without entering a password and the same thing happened.  This is a pretty fresh install too.

> 
The user zak is the only Samba user.  To use Samba effectively all users need a Linux account (adduser) and a Samba account (smbpasswd -a).

Ok so just to check, my linux account is 'zak' and I created a samba user in system-config-samba (aka smbpasswd afaik) also called 'zak' with the same password.  The idea is that I can access my samba shares as though I'm logging into the pc, same creds.   

> 
The user zak is the only user with access (see rwx above in red).  The group-user and others have no permissions to do anything (see blue above)


> 
The same applies here.  Only the user and user-group zak (uid=1000 and gid=1000) have any permissions.

Given the above, is that enough? I just need to access the shares and assume this is a no-frills way of setting things up...

> 
What users do you want to have access.  If you want "guest" access (e.g anyone on your network) then you need to change permissions for the others group (all others) to rwx.  It might look something like this ```

drwxrwxrwx 1 zak zak   4096 Sep 22 19:40 Documents

```

I just want my samba user 'zak' to have access, else everyone, I just want to fire up the WDTV or Kodi and access my shares.  After it's all working for a while I'd probably look at locking down permissions if they're not locked down, but for now I just want to be able to read my shares from the clients. 

> 
I'm not a big believer in having "guest" access however.  All guest access files created are owned by nobody:nogroup.  Both the user and group are system users.  You end up fighting to keep the ownership and permissions correct.  If you want to share a directory in you own home directory you can certainly do that.  I do that on an temporary ad hoc basis.  This type of guest share I delete after the guest is no longer on the network.

I know this has not given you a direct answer.  I think you need to rethink how (and why) you are sharing these directories.  The NTFS directories are problematical.  Since you have to set the permissions at mount time at the partition level you have to (a) mount both of them using fstab and (b) decide what user-group you want to have permissions to the all the partition's directories.  Have you thought about backing up the data and reformatting the partition to ext4?

Hmm actually I have.  The current scenario (probably predictably) is that this is a dual-boot system and I share the same TeraIII directories when I'm logged into Windows 7.  What I'd ultimately be happy to do is use Windows purely for gaming, and do everything else in Ubuntu, and no need for NTFS media partitions.  Happy to pull the pin and do it, especially if it means I can speed up progress towards a fix. 

> 
Do you have backups of all your data?  If not you should seriously think about creating a backup routine.  Over the years I have had a few disks crash and data accidentally deleted, but I have never permanently lost any data.  Backup, Backup, Backup!
[/QUOTE]
I don't, I set up nightly backups on my partners 14.04 pc using a bash script.  The idea will be to use the Windows 7 KODI/Steam box in the livingroom to handle backups from both ubuntu machines.  Just need to grab another HDD and figure out how to do it, that's half the fun!

Cheers

Zak

---

### Post by bab1 on 2015-09-26
> ...I tried without entering a password and the same thing happened. This is a pretty fresh install too.

Let's dig a little deeper then.  Post the output of this (use zak and the pw) ```
smbtree -d7
```...and also post the output of this```
ps -ef | grep mbd | grep -v color
```

---

### Post by mzak on 2015-09-26
> **bab1 said:**
> Let's dig a little deeper then.  Post the output of this (use zak and the pw) ```
smbtree -d7
```

...and also post the output of this```
ps -ef | grep mbd | grep -v color
```

Here we go:
```

zak@ZAKLIN:~$ smbtree -d7
INFO: Current debug levels:
  all: 7
  tdb: 7
  printdrivers: 7
  lanman: 7
  smb: 7
  rpc_parse: 7
  rpc_srv: 7
  rpc_cli: 7
  passdb: 7
  sam: 7
  auth: 7
  winbind: 7
  vfs: 7
  idmap: 7
  quota: 7
  acls: 7
  locking: 7
  msdfs: 7
  dmapi: 7
  registry: 7
  scavenger: 7
  dns: 7
  ldb: 7
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
INFO: Current debug levels:
  all: 7
  tdb: 7
  printdrivers: 7
  lanman: 7
  smb: 7
  rpc_parse: 7
  rpc_srv: 7
  rpc_cli: 7
  passdb: 7
  sam: 7
  auth: 7
  winbind: 7
  vfs: 7
  idmap: 7
  quota: 7
  acls: 7
  locking: 7
  msdfs: 7
  dmapi: 7
  registry: 7
  scavenger: 7
  dns: 7
  ldb: 7
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
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
doing parameter username map = /etc/samba/smbusers
pm_process() returned Yes
lp_servicenumber: couldn't find homes
added interface eth0 ip=192.168.0.101 bcast=192.168.0.255 netmask=255.255.255.0
Enter zak's password: 
Opening cache file at /var/cache/samba/gencache.tdb
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
gencache_init: Opening cache file /var/cache/samba/gencache.tdb read-only.
Opening cache file at /var/run/samba/gencache_notrans.tdb
no entry for WORKGROUP#1D found.
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_hosts: not appropriate for name type <0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 1
    SO_BROADCAST = 1
    Could not test socket option TCP_NODELAY.
    Could not test socket option TCP_KEEPCNT.
    Could not test socket option TCP_KEEPIDLE.
    Could not test socket option TCP_KEEPINTVL.
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_REUSEPORT = 1
    SO_SNDBUF = 212992
    SO_RCVBUF = 212992
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    Could not test socket option TCP_QUICKACK.
    Could not test socket option TCP_DEFER_ACCEPT.
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8a84d92a40] mpx_fde[(nil)] fd[7] - disabling
no entry for WORKGROUP#1B found.
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: not appropriate for name type <0x1b>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 1
    SO_BROADCAST = 1
    Could not test socket option TCP_NODELAY.
    Could not test socket option TCP_KEEPCNT.
    Could not test socket option TCP_KEEPIDLE.
    Could not test socket option TCP_KEEPINTVL.
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_REUSEPORT = 1
    SO_SNDBUF = 212992
    SO_RCVBUF = 212992
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    Could not test socket option TCP_QUICKACK.
    Could not test socket option TCP_DEFER_ACCEPT.
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8a84d92b70] mpx_fde[(nil)] fd[7] - disabling
Unable to find master browser for workgroup WORKGROUP, falling back to broadcast
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 1
    SO_BROADCAST = 1
    Could not test socket option TCP_NODELAY.
    Could not test socket option TCP_KEEPCNT.
    Could not test socket option TCP_KEEPIDLE.
    Could not test socket option TCP_KEEPINTVL.
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_REUSEPORT = 1
    SO_SNDBUF = 212992
    SO_RCVBUF = 212992
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    Could not test socket option TCP_QUICKACK.
    Could not test socket option TCP_DEFER_ACCEPT.
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8a84d92920] mpx_fde[(nil)] fd[7] - disabling
Unable to find master browser by broadcast

```

```

zak@ZAKLIN:~$ ps -ef | grep mbd | grep -v color
root      6731     1  0 13:50 ?        00:00:00 smbd -F
root      6733  6731  0 13:50 ?        00:00:00 smbd -F
root      6753     1  0 13:50 ?        00:00:00 nmbd -D

```

---

### Post by bab1 on 2015-09-26
> **mzak said:**
> 
```

zak@ZAKLIN:~$ ps -ef | grep mbd | grep -v color
root      6731     1  0 13:50 ?        00:00:00 smbd -F
root      6733  6731  0 13:50 ?        00:00:00 smbd -F
root      6753     1  0 13:50 ?        00:00:00 nmbd -D

```
THe Samba server is working correctly.

```

zak@ZAKLIN:~$ smbtree -d7
...
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
...
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
...
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
...
Unable to find master browser by broadcast

```
The Samba server browses SMB Resources by using a BROWSE LIST.  It has looked for this list and can't find it.  Typically this happens when that other host which is the Master Browser (MB) is not working correctly.  

What do you get with this command```
smbclient -L 192.168.0.101 
```
What are the IP addresses of the other hosts?  

The problem is pretty clear.  The name resolution is not working correctly.  All SMB resources are added to and deleted from the MBL (Master Browse List) using NetBIOS names.  The conversion from hostnames (DNS) is done by the *nmbd* daemon.

Another test would be to shut down all the other hosts> 
- another Ubuntu 14.04 box. 
- a WDTV that currently can't see the server
- a WIN7/KODI box that also can't see the server

...and restart both the smbd and nmbd daemons on this host```
sudo service smbd restart

sudo service nmbd restart
```
Allow some time for the Samba server to rebuild the Master Browse List (10 minutes or so) and then browse for the shares or run *smbtree*.

---

### Post by mzak on 2015-09-26
> **bab1 said:**
> The Samba server browses SMB Resources by using a BROWSE LIST.  It has looked for this list and can't find it.  Typically this happens when that other host which is the Master Browser (MB) is not working correctly.  

What do you get with this command```
smbclient -L 192.168.0.101 
```
What are the IP addresses of the other hosts?  

```

zak@ZAKLIN:~$ smbclient -L 192.168.0.101
Enter zak's password: 
Connection to 192.168.0.101 failed (Error NT_STATUS_IO_TIMEOUT)

And just for information:
zak@ZAKLIN:~$ smbclient -L ZAKLIN
Enter zak's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

    Sharename       Type      Comment
    ---------               ----         -------
    print$                Disk      Printer Drivers
    MOVIESLIN       Disk      MOVIESLIN
    MUSICLIN        Disk      
    IPC$            IPC       IPC Service (ZAKLIN server (Samba, Ubuntu))
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

    Server                 Comment
    ---------                  -------
    ZAKLIN               ZAKLIN server (Samba, Ubuntu)

    Workgroup            Master
    ---------                   -------
    WORKGROUP            


```

Other IP's are as follows:
Wifeys Ubuntu box: 192.168.0.100
WDTV: 192.168.0.104
KODI/W7 box: 192.168.0.105

> The problem is pretty clear.  The name resolution is not working correctly.  All SMB resources are added to and deleted from the MBL (Master Browse List) using NetBIOS names.  The conversion from hostnames (DNS) is done by the *nmbd* daemon.

Another test would be to shut down all the other hosts
...and restart both the smbd and nmbd daemons on this host```
sudo service smbd restart

sudo service nmbd restart
```
Allow some time for the Samba server to rebuild the Master Browse List (10 minutes or so) and then browse for the shares or run *smbtree*.

Ok so I unplugged the other 14.04 box from the network and the the WDTV, the KODI box is hibernating.  Then restarted smbd and nmbd on ZAKLIN.

Waited 15 min, then:

```

zak@ZAKLIN:~$ smbclient -L 192.168.0.101
Enter zak's password: 
Connection to 192.168.0.101 failed (Error NT_STATUS_IO_TIMEOUT)

```

```

zak@ZAKLIN:~$ smbtree
Enter zak's password: 
zak@ZAKLIN:~$ 

```

---

### Post by bab1 on 2015-09-26
> **mzak said:**
> ```

zak@ZAKLIN:~$ smbclient -L 192.168.0.101
Enter zak's password: 
Connection to 192.168.0.101 failed (Error NT_STATUS_IO_TIMEOUT)

```

Other IP's are as follows:
Wifeys Ubuntu box: 192.168.0.100
WDTV: 192.168.0.104
KODI/W7 box: 192.168.0.105



Ok so I unplugged the other 14.04 box from the network and the the WDTV, the KODI box is hibernating.  Then restarted smbd and nmbd on ZAKLIN.

Waited 15 min, then:

```

zak@ZAKLIN:~$ smbclient -L 192.168.0.101
Enter zak's password: 
Connection to 192.168.0.101 failed (Error NT_STATUS_IO_TIMEOUT)

```

```

zak@ZAKLIN:~$ smbtree
Enter zak's password: 
zak@ZAKLIN:~$ 

```
Sorry, I meant smbtree with the diagnostics enabled.  Post back the output of ```
smbtree -d7
```

---

### Post by mzak on 2015-09-26
> **bab1 said:**
> Sorry, I meant smbtree with the diagnostics enabled.  Post back the output of ```
smbtree -d7
```

Oh, no problem (I re-tested smb.conf by adding 'local master = yes' and 'preferred master = yes' as reflected below - no noticeable difference):

```

zak@ZAKLIN:~$ smbtree -d7
INFO: Current debug levels:
  all: 7
  tdb: 7
  printdrivers: 7
  lanman: 7
  smb: 7
  rpc_parse: 7
  rpc_srv: 7
  rpc_cli: 7
  passdb: 7
  sam: 7
  auth: 7
  winbind: 7
  vfs: 7
  idmap: 7
  quota: 7
  acls: 7
  locking: 7
  msdfs: 7
  dmapi: 7
  registry: 7
  scavenger: 7
  dns: 7
  ldb: 7
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
INFO: Current debug levels:
  all: 7
  tdb: 7
  printdrivers: 7
  lanman: 7
  smb: 7
  rpc_parse: 7
  rpc_srv: 7
  rpc_cli: 7
  passdb: 7
  sam: 7
  auth: 7
  winbind: 7
  vfs: 7
  idmap: 7
  quota: 7
  acls: 7
  locking: 7
  msdfs: 7
  dmapi: 7
  registry: 7
  scavenger: 7
  dns: 7
  ldb: 7
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter local master = yes
doing parameter preferred master = yes
doing parameter workgroup = WORKGROUP
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter server role = standalone server
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
doing parameter username map = /etc/samba/smbusers
doing parameter security = user
pm_process() returned Yes
lp_servicenumber: couldn't find homes
added interface eth0 ip=192.168.0.101 bcast=192.168.0.255 netmask=255.255.255.0
Enter zak's password: 
Opening cache file at /var/cache/samba/gencache.tdb
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
gencache_init: Opening cache file /var/cache/samba/gencache.tdb read-only.
Opening cache file at /var/run/samba/gencache_notrans.tdb
no entry for WORKGROUP#1D found.
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_hosts: not appropriate for name type <0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 1
    SO_BROADCAST = 1
    Could not test socket option TCP_NODELAY.
    Could not test socket option TCP_KEEPCNT.
    Could not test socket option TCP_KEEPIDLE.
    Could not test socket option TCP_KEEPINTVL.
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_REUSEPORT = 1
    SO_SNDBUF = 212992
    SO_RCVBUF = 212992
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    Could not test socket option TCP_QUICKACK.
    Could not test socket option TCP_DEFER_ACCEPT.
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f5135697a00] mpx_fde[(nil)] fd[7] - disabling
no entry for WORKGROUP#1B found.
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: not appropriate for name type <0x1b>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 1
    SO_BROADCAST = 1
    Could not test socket option TCP_NODELAY.
    Could not test socket option TCP_KEEPCNT.
    Could not test socket option TCP_KEEPIDLE.
    Could not test socket option TCP_KEEPINTVL.
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_REUSEPORT = 1
    SO_SNDBUF = 212992
    SO_RCVBUF = 212992
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    Could not test socket option TCP_QUICKACK.
    Could not test socket option TCP_DEFER_ACCEPT.
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f51356979b0] mpx_fde[(nil)] fd[7] - disabling
Unable to find master browser for workgroup WORKGROUP, falling back to broadcast
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 1
    SO_BROADCAST = 1
    Could not test socket option TCP_NODELAY.
    Could not test socket option TCP_KEEPCNT.
    Could not test socket option TCP_KEEPIDLE.
    Could not test socket option TCP_KEEPINTVL.
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_REUSEPORT = 1
    SO_SNDBUF = 212992
    SO_RCVBUF = 212992
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    Could not test socket option TCP_QUICKACK.
    Could not test socket option TCP_DEFER_ACCEPT.
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f5135697910] mpx_fde[(nil)] fd[7] - disabling
Unable to find master browser by broadcast


```

---

### Post by bab1 on 2015-09-26
Well that's not good.  :-(

What are the firewall setttings?  Post the output of this command```
sudo iptables -L -n
```

Try turning the firewall completely off and running smbtree -d7 again.

---

### Post by mzak on 2015-09-26
> **bab1 said:**
> Well that's not good.  :-( 

Yep, got me completely stumped, especially as a newbie.  

> What are the firewall setttings?  Post the output of this command```
sudo iptables -L -n
```

```

zak@ZAKLIN:~$ sudo iptables -L -n
[sudo] password for zak: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-input  all  --  0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
PIA_KILLSWITCH_OUTPUT_RULES  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain PIA_KILLSWITCH_OUTPUT_RULES (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            109.201.154.139     
RETURN     all  --  0.0.0.0/0            127.0.0.0/8         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:137
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:138
ufw-skip-to-policy-input  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:139
ufw-skip-to-policy-input  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:445
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:67
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:68
ufw-skip-to-policy-input  all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 3
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 4
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 11
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 12
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8
ufw-user-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0            ctstate INVALID
DROP       all  --  0.0.0.0/0            0.0.0.0/0            ctstate INVALID
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 3
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 4
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 11
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 12
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
ufw-not-local  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     udp  --  0.0.0.0/0            224.0.0.251          udp dpt:5353
ACCEPT     udp  --  0.0.0.0/0            239.255.255.250      udp dpt:1900
ufw-user-input  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ufw-user-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW ALLOW] "

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ctstate INVALID limit: avg 3/min burst 10
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type LOCAL
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type MULTICAST
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-track-forward (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            ctstate NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            ctstate NEW

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:139
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:445
ufw-user-logging-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:137
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:137
ufw-user-logging-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:138
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:138

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 5 LOG flags 0 level 4 prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (2 references)
target     prot opt source               destination         
LOG        udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:137 ctstate NEW limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW ALLOW] "
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:137
LOG        udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:138 ctstate NEW limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW ALLOW] "
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:138

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination  

```

> Try turning the firewall completely off and running smbtree -d7 again.

```

zak@ZAKLIN:~$ smbtree -d7
INFO: Current debug levels:
  all: 7
  tdb: 7
  printdrivers: 7
  lanman: 7
  smb: 7
  rpc_parse: 7
  rpc_srv: 7
  rpc_cli: 7
  passdb: 7
  sam: 7
  auth: 7
  winbind: 7
  vfs: 7
  idmap: 7
  quota: 7
  acls: 7
  locking: 7
  msdfs: 7
  dmapi: 7
  registry: 7
  scavenger: 7
  dns: 7
  ldb: 7
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
INFO: Current debug levels:
  all: 7
  tdb: 7
  printdrivers: 7
  lanman: 7
  smb: 7
  rpc_parse: 7
  rpc_srv: 7
  rpc_cli: 7
  passdb: 7
  sam: 7
  auth: 7
  winbind: 7
  vfs: 7
  idmap: 7
  quota: 7
  acls: 7
  locking: 7
  msdfs: 7
  dmapi: 7
  registry: 7
  scavenger: 7
  dns: 7
  ldb: 7
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter local master = yes
doing parameter preferred master = yes
doing parameter workgroup = WORKGROUP
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter server role = standalone server
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
doing parameter username map = /etc/samba/smbusers
doing parameter security = user
pm_process() returned Yes
lp_servicenumber: couldn't find homes
added interface eth0 ip=192.168.0.101 bcast=192.168.0.255 netmask=255.255.255.0
Enter zak's password: 
Opening cache file at /var/cache/samba/gencache.tdb
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
gencache_init: Opening cache file /var/cache/samba/gencache.tdb read-only.
Opening cache file at /var/run/samba/gencache_notrans.tdb
no entry for WORKGROUP#1D found.
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_hosts: not appropriate for name type <0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 1
    SO_BROADCAST = 1
    Could not test socket option TCP_NODELAY.
    Could not test socket option TCP_KEEPCNT.
    Could not test socket option TCP_KEEPIDLE.
    Could not test socket option TCP_KEEPINTVL.
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_REUSEPORT = 1
    SO_SNDBUF = 212992
    SO_RCVBUF = 212992
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    Could not test socket option TCP_QUICKACK.
    Could not test socket option TCP_DEFER_ACCEPT.
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8a02e99a00] mpx_fde[(nil)] fd[7] - disabling
no entry for WORKGROUP#1B found.
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: not appropriate for name type <0x1b>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 1
    SO_BROADCAST = 1
    Could not test socket option TCP_NODELAY.
    Could not test socket option TCP_KEEPCNT.
    Could not test socket option TCP_KEEPIDLE.
    Could not test socket option TCP_KEEPINTVL.
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_REUSEPORT = 1
    SO_SNDBUF = 212992
    SO_RCVBUF = 212992
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    Could not test socket option TCP_QUICKACK.
    Could not test socket option TCP_DEFER_ACCEPT.
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8a02e999b0] mpx_fde[(nil)] fd[7] - disabling
Unable to find master browser for workgroup WORKGROUP, falling back to broadcast
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 1
    SO_BROADCAST = 1
    Could not test socket option TCP_NODELAY.
    Could not test socket option TCP_KEEPCNT.
    Could not test socket option TCP_KEEPIDLE.
    Could not test socket option TCP_KEEPINTVL.
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_REUSEPORT = 1
    SO_SNDBUF = 212992
    SO_RCVBUF = 212992
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    Could not test socket option TCP_QUICKACK.
    Could not test socket option TCP_DEFER_ACCEPT.
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f8a02e99910] mpx_fde[(nil)] fd[7] - disabling
Unable to find master browser by broadcast


```

---

### Post by bab1 on 2015-09-26
> ...got me completely stumped, especially as a newbie. 

This is an unusual problem.  If you have all the other machines offline then the Master Browser is the localhost.  If you can't broadcast to the local host then something is internally wrong.  You might check the from the console, do you have TCP/IP connectivity?  Can you ping 192.168.0.101?  What does this command show```
ifconfig -a
```Can you ping a location on the Internet?

 I think I would return the firewall to its default state and make sure it is off.  Check all the logs at /var/log/samba.  Reboot the machine and wait another 15 minutes, then do smbtree -d7 again.  You might try smbclient -L <ipaddress> again.  When I do that I get this```

smbclient -L 192.168.1.152
Enter bab's password: 
Anonymous login successful
Domain=[BEACHES] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (maui server (Samba, Ubuntu))
	print$          Disk      Printer Drivers
	PDF             Printer   PDF
	HP-LaserJet-2200 Printer   HP LaserJet 2200
	Public          Disk      
Anonymous login successful
Domain=[BEACHES] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Server               Comment
	---------            -------
	MAUI                 maui server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	BEACHES            MAUI

```
In this case the Master Browser is MAUI

The bcast is for the NetBIOS name so the the IP address can be found.  Exactly the opposite of DNS where you are matching the IP address to the hostname.

At this point I don't really have any ideas.  Post the outputs and we will soldier on.  In the end we may have to purge all of Samba and restore the UFW firewall to its defaults to get this to work.  If it helps; all the searches I have done indicate this is a FW problem.

---

### Post by mzak on 2015-09-26
> **bab1 said:**
> This is an unusual problem.  If you have all the other machines offline then the Master Browser is the localhost.  If you can't broadcast to the local host then something is internally wrong.  You might check the from the console, do you have TCP/IP connectivity?  Can you ping 192.168.0.101?  What does this command show```
ifconfig -a
```

Ok, firewall has been reset and disabled.
Do you mean ping myself?:
```

zak@ZAKLIN:~$ ping 192.168.0.101
PING 192.168.0.101 (192.168.0.101) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
etc...

```



> Can you ping a location on the Internet?
Yep, pinged google aok.


 > I think I would return the firewall to its default state and make sure it is off.  Check all the logs at /var/log/samba.  
log.nmbd:
```

[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:25:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<20>
[2015/09/27 09:25:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<03>
[2015/09/27 09:25:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<00>
[2015/09/27 09:25:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<00>
[2015/09/27 09:25:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<1e>
[2015/09/27 09:26:04,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:26:04,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:26:04,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:26:04,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 09:27:04,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/09/27 09:28:41,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:28:41,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<20>
[2015/09/27 09:28:41,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<03>
[2015/09/27 09:28:41,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<00>
[2015/09/27 09:28:41,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<00>
[2015/09/27 09:28:41,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<1e>
[2015/09/27 09:28:51,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:28:51,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:28:51,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:28:51,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 09:29:51,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:31:51,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:33:51,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:33:51,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:33:51,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 09:34:51,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:38:51,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:38:51,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:38:51,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:38:51,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/09/27 09:42:38,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:42:38,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<20>
[2015/09/27 09:42:38,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<03>
[2015/09/27 09:42:38,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<00>
[2015/09/27 09:42:38,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<00>
[2015/09/27 09:42:38,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<1e>
[2015/09/27 09:42:48,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:42:48,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:42:48,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:42:48,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 09:43:48,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:45:48,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/09/27 09:45:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:45:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<20>
[2015/09/27 09:45:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<03>
[2015/09/27 09:45:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<00>
[2015/09/27 09:45:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<00>
[2015/09/27 09:45:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<1e>
[2015/09/27 09:46:04,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:46:04,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:46:04,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:46:04,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 09:46:04,  0] ../source3/nmbd/nmbd_become_dmb.c:294(become_domain_master_browser_bcast)
  become_domain_master_browser_bcast:
  Attempting to become domain master browser on workgroup WORKGROUP on subnet 192.168.0.101
[2015/09/27 09:46:04,  0] ../source3/nmbd/nmbd_become_dmb.c:307(become_domain_master_browser_bcast)
  become_domain_master_browser_bcast: querying subnet 192.168.0.101 for domain master browser on workgroup WORKGROUP
[2015/09/27 09:46:04,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:46:04,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:46:04,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1b>
[2015/09/27 09:47:04,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:49:04,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:49:30,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/09/27 09:49:30,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:50:06,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:50:06,  0] ../source3/nmbd/nmbd_become_dmb.c:294(become_domain_master_browser_bcast)
  become_domain_master_browser_bcast:
  Attempting to become domain master browser on workgroup WORKGROUP on subnet 192.168.0.101
[2015/09/27 09:50:06,  0] ../source3/nmbd/nmbd_become_dmb.c:307(become_domain_master_browser_bcast)
  become_domain_master_browser_bcast: querying subnet 192.168.0.101 for domain master browser on workgroup WORKGROUP
[2015/09/27 09:50:12,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:50:12,  0] ../source3/nmbd/nmbd_packets.c:1638(retransmit_or_expire_response_records)
  retransmit_or_expire_response_records: Failed to resend packet id 23381 to IP 192.168.0.255 on subnet 192.168.0.101
[2015/09/27 09:50:13,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:50:13,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:50:13,  0] ../source3/nmbd/nmbd_packets.c:1638(retransmit_or_expire_response_records)
  retransmit_or_expire_response_records: Failed to resend packet id 23381 to IP 192.168.0.255 on subnet 192.168.0.101
[2015/09/27 09:50:14,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:50:14,  0] ../source3/nmbd/nmbd_packets.c:1638(retransmit_or_expire_response_records)
  retransmit_or_expire_response_records: Failed to resend packet id 23381 to IP 192.168.0.255 on subnet 192.168.0.101
[2015/09/27 09:50:14,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:50:14,  0] ../source3/nmbd/nmbd_become_dmb.c:112(become_domain_master_stage2)
  *****
  
 ** Samba server ZAKLIN is now a domain master browser for workgroup WORKGROUP on subnet 192.168.0.101**
  
  *****
[2015/09/27 09:50:17,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:50:19,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:50:21,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:50:21,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:50:21,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:50:21,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name __MSBROWSE__<01>
[2015/09/27 09:51:21,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:53:21,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/09/27 09:54:42,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:54:42,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<20>
[2015/09/27 09:54:42,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<03>
[2015/09/27 09:54:42,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<00>
[2015/09/27 09:54:42,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<00>
[2015/09/27 09:54:42,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<1e>
[2015/09/27 09:54:52,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:54:52,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:54:52,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:54:52,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 09:55:52,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:57:52,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:59:53,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:59:53,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:59:53,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:00:53,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:04:53,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:04:53,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:04:53,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:04:53,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:09:53,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:09:53,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:09:53,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:09:53,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:14:57,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:14:57,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:14:57,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:15:57,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:19:57,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:19:57,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:19:57,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:22:57,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:24:57,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:24:57,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:24:57,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:29:58,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:29:58,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:29:58,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:30:58,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:34:58,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:34:58,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:34:58,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:40:01,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:40:01,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:40:01,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:40:01,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:45:02,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:45:02,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:45:02,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:50:02,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:50:02,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:50:02,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:50:02,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:55:02,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:55:02,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:55:02,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/09/27 10:58:05,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 10:58:05,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<20>
[2015/09/27 10:58:05,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<03>
[2015/09/27 10:58:05,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<00>
[2015/09/27 10:58:05,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<00>
[2015/09/27 10:58:05,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<1e>
[2015/09/27 10:58:15,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:58:15,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:58:15,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:58:15,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:59:15,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:01:15,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:03:15,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:03:15,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:03:15,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 11:04:15,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:08:15,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:08:15,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:08:15,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:08:15,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 11:13:16,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:13:16,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:13:16,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:13:16,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 11:18:16,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:18:16,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:18:16,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 11:19:16,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:23:16,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:23:16,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:23:16,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/09/27 11:23:33,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 11:23:33,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<20>
[2015/09/27 11:23:33,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<03>
[2015/09/27 11:23:33,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<00>
[2015/09/27 11:23:33,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<00>
[2015/09/27 11:23:33,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<1e>
[2015/09/27 11:23:43,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:23:43,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:23:43,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:23:43,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 11:24:43,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:26:43,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:28:43,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:28:43,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:28:43,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 11:29:43,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:33:43,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:33:43,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:33:43,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:33:43,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>

```

log.smbd
```

[2015/09/27 09:25:54,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:25:54.044610,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2015/09/27 09:28:34.708516,  0] ../lib/util/pidfile.c:153(pidfile_unlink)
  Failed to delete pidfile /var/run/samba/smbd.pid. Error was No such file or directory
[2015/09/27 09:28:34,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:28:34.727044,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2015/09/27 09:42:36.353681,  0] ../lib/util/pidfile.c:153(pidfile_unlink)
  Failed to delete pidfile /var/run/samba/smbd.pid. Error was No such file or directory
[2015/09/27 09:42:36,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:42:36.371471,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2015/09/27 09:45:52.180395,  0] ../lib/util/pidfile.c:153(pidfile_unlink)
  Failed to delete pidfile /var/run/samba/smbd.pid. Error was No such file or directory
[2015/09/27 09:45:52,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:45:52.194159,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2015/09/27 09:49:30.933376,  0] ../lib/util/pidfile.c:153(pidfile_unlink)
[2015/09/27 09:50:01,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:50:01.839423,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2015/09/27 09:50:01.892696,  0] ../source3/printing/print_cups.c:151(cups_connect)
  Unable to connect to CUPS server localhost:631 - Bad file descriptor
[2015/09/27 09:50:01.893320,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2015/09/27 09:54:40.197188,  0] ../lib/util/pidfile.c:153(pidfile_unlink)
  Failed to delete pidfile /var/run/samba/smbd.pid. Error was No such file or directory
[2015/09/27 09:54:40,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:54:40.212552,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2015/09/27 10:58:00.863029,  0] ../lib/util/pidfile.c:153(pidfile_unlink)
  Failed to delete pidfile /var/run/samba/smbd.pid. Error was No such file or directory
[2015/09/27 10:58:00,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 10:58:00.879164,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2015/09/27 11:23:29.297686,  0] ../lib/util/pidfile.c:153(pidfile_unlink)
  Failed to delete pidfile /var/run/samba/smbd.pid. Error was No such file or directory
[2015/09/27 11:23:29,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 11:23:29.310251,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option

```

log.zaklin is empty.
log.127.0.0.1 is empty

> Reboot the machine and wait another 15 minutes, then do smbtree -d7 again.  You might try smbclient -L <ipaddress> again.  When I do that I get this```

smbclient -L 192.168.1.152
Enter bab's password: 
Anonymous login successful
Domain=[BEACHES] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       IPC Service (maui server (Samba, Ubuntu))
    print$          Disk      Printer Drivers
    PDF             Printer   PDF
    HP-LaserJet-2200 Printer   HP LaserJet 2200
    Public          Disk      
Anonymous login successful
Domain=[BEACHES] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

    Server               Comment
    ---------            -------
    MAUI                 maui server (Samba, Ubuntu)

    Workgroup            Master
    ---------            -------
    BEACHES            MAUI

```
In this case the Master Browser is MAUI

The bcast is for the NetBIOS name so the the IP address can be found.  Exactly the opposite of DNS where you are matching the IP address to the hostname.

At this point I don't really have any ideas.  Post the outputs and we will soldier on.  In the end we may have to purge all of Samba and restore the UFW firewall to its defaults to get this to work.  If it helps; all the searches I have done indicate this is a FW problem.

Ok cool,happy to go as far formatting and reinstalling to get this working. Thanks for everything so far.
Interesting line log.nmbd: [B] Samba server ZAKLIN is now a domain master browser for workgroup WORKGROUP on subnet 192.168.0.101

[/B]Will restart now.

---

### Post by bab1 on 2015-09-26
> **mzak said:**
> Ok, firewall has been reset and disabled.
Do you mean ping myself?:
```

zak@ZAKLIN:~$ ping 192.168.0.101
PING 192.168.0.101 (192.168.0.101) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
etc...

```
This is the problem.  Your FW is not allowing icmp packets and who know what else via the eth0 NIC interface.  I did mean for you to ping yourself, but not the loopback interface (127.0.0.1).  When I ping my host I get this```
ping 192.168.1.152
PING 192.168.1.152 (192.168.1.152) 56(84) bytes of data.
64 bytes from 192.168.1.152: icmp_seq=1 ttl=64 time=0.054 ms
64 bytes from 192.168.1.152: icmp_seq=2 ttl=64 time=0.036 ms
64 bytes from 192.168.1.152: icmp_seq=3 ttl=64 time=0.037 ms
64 bytes from 192.168.1.152: icmp_seq=4 ttl=64 time=0.067 ms

```
Your FW is NOT off.> 



Yep, pinged google aok.


   
log.nmbd:
```

[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:25:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<20>
[2015/09/27 09:25:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<03>
[2015/09/27 09:25:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<00>
[2015/09/27 09:25:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<00>
[2015/09/27 09:25:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:25:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<1e>
[2015/09/27 09:26:04,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:26:04,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:26:04,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:26:04,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 09:27:04,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/09/27 09:28:41,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:28:41,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<20>
[2015/09/27 09:28:41,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<03>
[2015/09/27 09:28:41,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<00>
[2015/09/27 09:28:41,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<00>
[2015/09/27 09:28:41,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:28:41,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<1e>
[2015/09/27 09:28:51,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:28:51,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:28:51,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:28:51,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 09:29:51,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:31:51,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:33:51,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:33:51,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:33:51,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 09:34:51,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:38:51,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:38:51,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:38:51,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:38:51,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/09/27 09:42:38,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:42:38,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<20>
[2015/09/27 09:42:38,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<03>
[2015/09/27 09:42:38,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<00>
[2015/09/27 09:42:38,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<00>
[2015/09/27 09:42:38,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:42:38,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<1e>
[2015/09/27 09:42:48,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:42:48,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:42:48,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:42:48,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 09:43:48,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:45:48,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/09/27 09:45:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:45:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<20>
[2015/09/27 09:45:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<03>
[2015/09/27 09:45:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<00>
[2015/09/27 09:45:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<00>
[2015/09/27 09:45:54,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:45:54,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<1e>
[2015/09/27 09:46:04,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:46:04,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:46:04,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:46:04,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 09:46:04,  0] ../source3/nmbd/nmbd_become_dmb.c:294(become_domain_master_browser_bcast)
  become_domain_master_browser_bcast:
  Attempting to become domain master browser on workgroup WORKGROUP on subnet 192.168.0.101
[2015/09/27 09:46:04,  0] ../source3/nmbd/nmbd_become_dmb.c:307(become_domain_master_browser_bcast)
  become_domain_master_browser_bcast: querying subnet 192.168.0.101 for domain master browser on workgroup WORKGROUP
[2015/09/27 09:46:04,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:46:04,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:46:04,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1b>
[2015/09/27 09:47:04,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:49:04,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:49:30,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/09/27 09:49:30,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:50:06,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:50:06,  0] ../source3/nmbd/nmbd_become_dmb.c:294(become_domain_master_browser_bcast)
  become_domain_master_browser_bcast:
  Attempting to become domain master browser on workgroup WORKGROUP on subnet 192.168.0.101
[2015/09/27 09:50:06,  0] ../source3/nmbd/nmbd_become_dmb.c:307(become_domain_master_browser_bcast)
  become_domain_master_browser_bcast: querying subnet 192.168.0.101 for domain master browser on workgroup WORKGROUP
[2015/09/27 09:50:12,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:50:12,  0] ../source3/nmbd/nmbd_packets.c:1638(retransmit_or_expire_response_records)
  retransmit_or_expire_response_records: Failed to resend packet id 23381 to IP 192.168.0.255 on subnet 192.168.0.101
[2015/09/27 09:50:13,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:50:13,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:50:13,  0] ../source3/nmbd/nmbd_packets.c:1638(retransmit_or_expire_response_records)
  retransmit_or_expire_response_records: Failed to resend packet id 23381 to IP 192.168.0.255 on subnet 192.168.0.101
[2015/09/27 09:50:14,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:50:14,  0] ../source3/nmbd/nmbd_packets.c:1638(retransmit_or_expire_response_records)
  retransmit_or_expire_response_records: Failed to resend packet id 23381 to IP 192.168.0.255 on subnet 192.168.0.101
[2015/09/27 09:50:14,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:50:14,  0] ../source3/nmbd/nmbd_become_dmb.c:112(become_domain_master_stage2)
  *****
  
 ** Samba server ZAKLIN is now a domain master browser for workgroup WORKGROUP on subnet 192.168.0.101**
  
  *****
[2015/09/27 09:50:17,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:50:19,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:50:21,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:50:21,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:50:21,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:50:21,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name __MSBROWSE__<01>
[2015/09/27 09:51:21,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:53:21,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/09/27 09:54:42,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 09:54:42,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<20>
[2015/09/27 09:54:42,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<03>
[2015/09/27 09:54:42,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<00>
[2015/09/27 09:54:42,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<00>
[2015/09/27 09:54:42,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:54:42,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<1e>
[2015/09/27 09:54:52,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:54:52,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:54:52,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:54:52,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 09:55:52,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:57:52,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 09:59:53,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 09:59:53,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 09:59:53,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:00:53,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:04:53,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:04:53,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:04:53,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:04:53,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:09:53,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:09:53,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:09:53,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:09:53,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:14:57,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:14:57,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:14:57,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:15:57,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:19:57,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:19:57,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:19:57,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:22:57,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:24:57,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:24:57,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:24:57,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:29:58,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:29:58,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:29:58,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:30:58,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:34:58,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:34:58,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:34:58,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:40:01,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:40:01,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:40:01,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:40:01,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:45:02,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:45:02,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:45:02,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:50:02,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:50:02,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:50:02,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:50:02,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:55:02,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:55:02,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:55:02,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/09/27 10:58:05,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 10:58:05,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<20>
[2015/09/27 10:58:05,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<03>
[2015/09/27 10:58:05,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<00>
[2015/09/27 10:58:05,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<00>
[2015/09/27 10:58:05,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:58:05,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<1e>
[2015/09/27 10:58:15,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 10:58:15,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 10:58:15,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 10:58:15,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 10:59:15,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:01:15,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:03:15,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:03:15,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:03:15,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 11:04:15,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:08:15,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:08:15,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:08:15,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:08:15,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 11:13:16,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:13:16,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:13:16,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:13:16,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 11:18:16,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:18:16,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:18:16,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 11:19:16,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:23:16,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:23:16,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:23:16,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/09/27 11:23:33,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 11:23:33,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<20>
[2015/09/27 11:23:33,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<03>
[2015/09/27 11:23:33,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name ZAKLIN<00>
[2015/09/27 11:23:33,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<00>
[2015/09/27 11:23:33,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:23:33,  0] ../source3/nmbd/nmbd_nameregister.c:522(register_name)
  register_name: Failed to send packet trying to register name WORKGROUP<1e>
[2015/09/27 11:23:43,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:23:43,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:23:43,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:23:43,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 11:24:43,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:26:43,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:28:43,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:28:43,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:28:43,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 11:29:43,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:33:43,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 11:33:43,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 11:33:43,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 11:33:43,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>

```
Look at all those packets (IP traffic denied) tht are not permitted.  More evidence that the FW is not well.
The smbd daemon is working fine.  The nmbd daemon is being denied access by the FW for sure.> 

Ok cool,happy to go as far formatting and reinstalling to get this working. Thanks for everything so far.
Interesting line log.nmbd: [B] Samba server ZAKLIN is now a domain master browser for workgroup WORKGROUP on subnet 192.168.0.101

[/B]Will restart now.
I don't think we need to do anything except get the FW out of the picture.  Then we can setup your LAN networking.

FWIW:  I do not run any FW internally on my networks.  I run a FW on the edge of my network.  The router has a FW.  I trust all of my users.  If you are in a unknown environment or don't have control of all the users in the network then a FW is appropriate.

---

### Post by mzak on 2015-09-26
> **bab1 said:**
> This is the problem.  Your FW is not allowing icmp packets and who know what else via the eth0 NIC interface.  I did mean for you to ping yourself, but not the loopback interface (127.0.0.1).  When I ping my host I get this```
ping 192.168.1.152
PING 192.168.1.152 (192.168.1.152) 56(84) bytes of data.
64 bytes from 192.168.1.152: icmp_seq=1 ttl=64 time=0.054 ms
64 bytes from 192.168.1.152: icmp_seq=2 ttl=64 time=0.036 ms
64 bytes from 192.168.1.152: icmp_seq=3 ttl=64 time=0.037 ms
64 bytes from 192.168.1.152: icmp_seq=4 ttl=64 time=0.067 ms

```
Your FW is NOT off.Look at all those packets (IP traffic denied) tht are not permitted.  More evidence that the FW is not well.
The smbd daemon is working fine.  The nmbd daemon is being denied access by the FW for sure.
I don't think we need to do anything except get the FW out of the picture.  Then we can setup your LAN networking.

FWIW:  I do not run any FW internally on my networks.  I run a FW on the edge of my network.  The router has a FW.  I trust all of my users.  If you are in a unknown environment or don't have control of all the users in the network then a FW is appropriate.

Sorry I just removed the added rules in GUFW, I've now done the following:

```

zak@ZAKLIN:~$ sudo ufw disable
Firewall stopped and disabled on system startup
zak@ZAKLIN:~$ sudo service smbd restart
smbd stop/waiting
smbd start/running, process 7129
zak@ZAKLIN:~$ sudo service nmbd restart
nmbd stop/waiting
nmbd start/running, process 7150

```

---

### Post by bab1 on 2015-09-26
Can you see the shares?  Post the output of both of these```
smbtree -d3

smbclient -L 192.168.0.101
```

---

### Post by mzak on 2015-09-26
> **bab1 said:**
> Can you see the shares?  Post the output of both of these```
smbtree -d3

smbclient -L 192.168.0.101
```

Ok, here goes:

```

zak@ZAKLIN:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.0.101 bcast=192.168.0.255 netmask=255.255.255.0
Enter zak's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbca446d9e0] mpx_fde[(nil)] fd[7] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbca446d9e0] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbca446d9e0] mpx_fde[(nil)] fd[7] - disabling

```

```

zak@ZAKLIN:~$ smbclient -L 192.168.0.101
Enter zak's password: 
Connection to 192.168.0.101 failed (Error NT_STATUS_IO_TIMEOUT)

```

In response to your earlier post, all users on this network are trusted (aside from my 3 year old who likes to delete stuff).

---

### Post by mzak on 2015-09-26
following another reboot:

```

zak@ZAKLIN:~$ sudo ufw status
[sudo] password for zak: 
Status: inactive
zak@ZAKLIN:~$ smbclient -L 192.168.0.101
Enter zak's password: 
Connection to 192.168.0.101 failed (Error NT_STATUS_IO_TIMEOUT)

```

---

### Post by bab1 on 2015-09-27
> **mzak said:**
> following another reboot:

```

zak@ZAKLIN:~$ sudo ufw status
[sudo] password for zak: 
Status: inactive
zak@ZAKLIN:~$ smbclient -L 192.168.0.101
Enter zak's password: 
Connection to 192.168.0.101 failed (Error NT_STATUS_IO_TIMEOUT)

```

What do you get if you ping 192.168.0.101 ```
ping 192.168.0.101
```...and also lets look at the last 20 lines of /var/log/samba/nmbd.log```
tail -n20 /var/log/samba/log.nmbd
```

Edit: How about this too```
sudo iptables -nvL
```

---

### Post by mzak on 2015-09-27
> **bab1 said:**
> What do you get if you ping 192.168.0.101 ```
ping 192.168.0.101
```
```

zak@ZAKLIN:~$ ping 192.168.0.101
PING 192.168.0.101 (192.168.0.101) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

```

> ...and also lets look at the last 20 lines of /var/log/samba/nmbd.log```
tail -n20 /var/log/samba/log.nmbd
```
```

zak@ZAKLIN:~$ tail -n20 /var/log/samba/log.nmbd
[2015/09/27 14:11:58,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 14:11:58,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 14:11:58,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 14:16:58,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(138) ERRNO=Operation not permitted
[2015/09/27 14:16:58,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 14:16:58,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 14:16:58,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 14:21:59,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 14:21:59,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 14:21:59,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>

```

> Edit: How about this too```
sudo iptables -nvL
```
```

zak@ZAKLIN:~$ sudo iptables -nvL
[sudo] password for zak: 
Chain INPUT (policy ACCEPT 26012 packets, 8321K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 25290 packets, 3543K bytes)
 pkts bytes target     prot opt in     out     source               destination         
25463 3575K PIA_KILLSWITCH_OUTPUT_RULES  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain PIA_KILLSWITCH_OUTPUT_RULES (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 6940 1645K RETURN     all  --  *      *       0.0.0.0/0            109.201.152.239     
11779  884K RETURN     all  --  *      *       0.0.0.0/0            127.0.0.0/8         
 6571 1014K RETURN     all  --  *      tun+    0.0.0.0/0            0.0.0.0/0           
  173 32658 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0

```

---

### Post by bab1 on 2015-09-27
Post the output of ```
ifconfig -a
```

[COLOR="#0000FF"]**Edit:** **Do you have a VPN on this machine or a PIA app running?**[/COLOR]

---

### Post by mzak on 2015-09-27
> **bab1 said:**
> Post the output of ```
ifconfig -a
```

```

zak@ZAKLIN:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr d0:50:99:46:28:6e  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::d250:99ff:fe46:286e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8257 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4738777 (4.7 MB)  TX bytes:2118638 (2.1 MB)
          Interrupt:20 Memory:eff00000-eff20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:13931 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13931 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1042387 (1.0 MB)  TX bytes:1042387 (1.0 MB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.107.1.6  P-t-P:10.107.1.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:7136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:3546596 (3.5 MB)  TX bytes:1223673 (1.2 MB)

```

---

### Post by bab1 on 2015-09-27
Do you have a VPN on this machine and/or a PIA app running?

---

### Post by mzak on 2015-09-27
> **bab1 said:**
> Do you have a VPN on this machine and/or a PIA app running?

Yes, PIA app installed and running full-time, and always connected.

---

### Post by bab1 on 2015-09-27
Turn it off and retest.  It may be incompatible as configured with Samba.  Samba is a LAN application that is configured for a single segment LAN by default.  You can't broadcast to other subnets or networks.

For testing purposes you should return everything back to the default IP stack operation.  Then you will be able to tell if you have a Samba problem (I doubt it) or a TCP/IP connectivity problem (most likely you do).

Samba is not really compatible with internetworking (Internet access) without careful configuration.

---

### Post by mzak on 2015-09-27
```

zak@ZAKLIN:~$ ping 192.168.0.101
PING 192.168.0.101 (192.168.0.101) 56(84) bytes of data.
64 bytes from 192.168.0.101: icmp_seq=1 ttl=64 time=0.025 ms
etc

zak@ZAKLIN:~$ smbtree
Enter zak's password: 
zak@ZAKLIN:~$

zak@ZAKLIN:~$ smbclient -L 192.168.0.101
Enter zak's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    MOVIESLIN       Disk      MOVIESLIN
    MUSICLIN        Disk      
    IPC$            IPC       IPC Service (ZAKLIN server (Samba, Ubuntu))
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

    Server               Comment
    ---------                -------
    ZAKLIN               ZAKLIN server (Samba, Ubuntu)

    Workgroup            Master
    ---------                  -------
    WORKGROUP            

zak@ZAKLIN:~$ tail -n20 /var/log/samba/log.nmbd
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 14:57:01,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 15:02:07,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 15:02:07,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 15:02:07,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 15:07:31,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/09/27 15:07:31,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 15:07:54,  0] ../source3/nmbd/nmbd_become_lmb.c:397(become_local_master_stage2)
  *****
  
  Samba name server ZAKLIN is now a local master browser for workgroup WORKGROUP on subnet 192.168.0.101
  
  *****

```

Any others?
EDIT: And the server is reachable from the clients again, albeit with no vpn.

---

### Post by bab1 on 2015-09-27
> **mzak said:**
> ```

zak@ZAKLIN:~$ ping 192.168.0.101
PING 192.168.0.101 (192.168.0.101) 56(84) bytes of data.
64 bytes from 192.168.0.101: icmp_seq=1 ttl=64 time=0.025 ms
etc

zak@ZAKLIN:~$ smbtree
Enter zak's password: 
zak@ZAKLIN:~$

zak@ZAKLIN:~$ smbclient -L 192.168.0.101
Enter zak's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    MOVIESLIN       Disk      MOVIESLIN
    MUSICLIN        Disk      
    IPC$            IPC       IPC Service (ZAKLIN server (Samba, Ubuntu))
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

    Server               Comment
    ---------                -------
    ZAKLIN               ZAKLIN server (Samba, Ubuntu)

    Workgroup            Master
    ---------                  -------
    WORKGROUP            

zak@ZAKLIN:~$ tail -n20 /var/log/samba/log.nmbd
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 14:57:01,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 15:02:07,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 192.168.0.255(137) ERRNO=Operation not permitted
[2015/09/27 15:02:07,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.0.255 port 137 failed
[2015/09/27 15:02:07,  0] ../source3/nmbd/nmbd_namequery.c:245(query_name)
  query_name: Failed to send packet trying to query name WORKGROUP<1d>
[2015/09/27 15:07:31,  0] ../source3/nmbd/nmbd.c:57(terminate)
  Got SIGTERM: going down...
[2015/09/27 15:07:31,  0] ../source3/nmbd/nmbd.c:902(main)
  nmbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/09/27 15:07:54,  0] ../source3/nmbd/nmbd_become_lmb.c:397(become_local_master_stage2)
  *****
  
  Samba name server ZAKLIN is now a local master browser for workgroup WORKGROUP on subnet 192.168.0.101
  
  *****

```

Any others?

Samba is working fine.

The VPN is the problem.  You will need to deal with that.

---

### Post by mzak on 2015-09-27
> **bab1 said:**
> Samba is working fine.

Yep, as you had suspected.  Thanks for guiding me to a fix!

Does that mean no vpn connections whatsoever while sharing via samba?

---

### Post by bab1 on 2015-09-27
> **mzak said:**
> Yep, as you had suspected.  Thanks for guiding me to a fix!

Does that mean no vpn connections whatsoever while sharing via samba?

As you have it configured that is so.  NetBIOS broadcasts do not transit routers.  In fact no broadcasts of any kind pass through a router.  The broadcast domain is the single segment defined by the network ID and the subnet mask.

[COLOR="#0000FF"]**Edit:  Although we have solved the problem, we have not cured the problem.  Most unsatisfying. **[/COLOR]

---

### Post by mzak on 2015-09-27
> **bab1 said:**
> As you have it configured that is so.  NetBIOS broadcasts do not transit routers.  In fact no broadcasts of any kind pass through a router.  The broadcast domain is the single segment defined by the network ID and the subnet mask.

[COLOR=#0000FF]**Edit:  Although we have solved the problem, we have not cured the problem.  Most unsatisfying. **[/COLOR]

Well I'm very happy with the results nonetheless! :)

I can reconnect the vpn after sharing files, I'll keep testing things out but the point is I know where to look if the server can't be located, and how to troubleshoot.  Is that a conversation to have with the vpn provider or anyone else about being able to use the app and samba without any conflicts?

---

### Post by bab1 on 2015-09-27
Why do you need to use Samba via the Internet?  You can use OpenSSH (sFTP) to access the files via an encrypted tunnel.  In fact why do you need a VPN?

---

### Post by mzak on 2015-09-27
Sorry I meant connect the VPN while I'm sharing over my LAN, not connect to the share from an external address.  My country (Australia) is bringing in mandatory data retention (internet, phone, email, sms) that will likely be stored on overseas servers, I value my privacy too much. 

How relevant is this problem/fix?

[http://askubuntu.com/questions/653399/cant-connect-to-samba-server-after-setting-up-vpn](http://askubuntu.com/questions/653399/cant-connect-to-samba-server-after-setting-up-vpn)

---

### Post by bab1 on 2015-09-27
Do you have a VPN provider or ???  Why are you connecting with your LAN?   

I still don't see what you need a VPN; be it through a provider or installed by you on one of you machines at home.  I'm not saying that there aren't valid reasons for a VPN, I'm just asking you to stop and think about what your end-game is.

The question deals with OpenVPN which is an VPN server that you install and configure on whatever host you want it on.  You would be your own provider.  You can't apply the solution directly  to your situation unless you are using OpenVPN.

---

### Post by bab1 on 2015-09-27
> My country (Australia) is bringing in mandatory data retention (internet, phone, email, sms) that will likely be stored on overseas servers, I value my privacy too much.   What do you mean by that?  What does the physical location have to do with privacy in general?  I still don't get it.  I can access multiple servers around the world securely without a VPN.  What point sold you on using a VPN?

---

### Post by mzak on 2015-09-27
[http://www.crikey.com.au/2015/03/18/your-guide-to-the-data-retention-debate-what-it-is-and-why-it%E2%80%99s-bad/](http://www.crikey.com.au/2015/03/18/your-guide-to-the-data-retention-debate-what-it-is-and-why-it%E2%80%99s-bad/)  

This gives an overview of what we're looking at. 

 Gotta get the toddler to bed, will check back.

---

### Post by bab1 on 2015-09-27
> **mzak said:**
> [http://www.crikey.com.au/2015/03/18/your-guide-to-the-data-retention-debate-what-it-is-and-why-it%E2%80%99s-bad/](http://www.crikey.com.au/2015/03/18/your-guide-to-the-data-retention-debate-what-it-is-and-why-it%E2%80%99s-bad/)  

This gives an overview of what we're looking at. 

 Gotta get the toddler to bed, will check back.
Ahhhhh, I don't want to even go there.  I gave up my tinfoil hat a long time ago.  Sorry, I'm not going to be of any help on that subject.

---

### Post by mzak on 2015-09-27
Not a problem, you helped me with what I needed help with, and I appreciate it :)

---

