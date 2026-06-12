---
title: "Samba and file access for guests"
date: 2016-06-19
forum: Networking &amp; Wireless
---

### Post by Jason_Stickler on 2016-06-19
Hello,
I am unfortunately extremely lost, I feel like I am starting to figure out a few of these items but I need to get all the pieces together.  I am running Ubuntu Server 14.04.  I have mounted my internal hard drives - possibly foolishly - under my user account specifically media/username/NAS/media.  I have no problems accessing using my user account on my Windows PC.  I created an account for my wife as well and she is unable to access these drives.

I also am trying to create a samba share to share only specific folders out to any network account.  I have been able to see the shares when I browse the network on a Windows PC but when I click on them it gives me an error that it cannot connect check the share name blah blah.  Below are some of the contents of my smb.conf.

security = user
map to guest = bad user

[share]
comment = share
path = /media/username/NAS/Media/Share
public = yes
only guest = yes
writeable = no

I have tried to figure this out but I still don't fully understand the permissions and groups quite well enough.

Thanks in advance for your assistance.
Jason

---

### Post by bab1 on 2016-06-19
> **Jason_Stickler said:**
> Hello,
I am unfortunately extremely lost, I feel like I am starting to figure out a few of these items but I need to get all the pieces together.  I am running Ubuntu Server 14.04.  
Does this mean there is no GUI interface?  > I have mounted my internal hard drives - possibly foolishly - under my user account specifically media/username/NAS/media.  

You do not mount drives.  You mount file systems that reside on partitions (sda1 or sdb1 or sdb2).  Post the output this terminal command```
df -h
```  
> 
I have no problems accessing using my user account on my Windows PC.  I created an account for my wife as well and she is unable to access these drives.
Do you mean that you can access the shares on Ubuntu from your Windows machine, but your wife can't?> 
I also am trying to create a samba share to share only specific folders out to any network account.  I have been able to see the shares when I browse the network on a Windows PC but when I click on them it gives me an error that it cannot connect check the share name blah blah.  Below are some of the contents of my smb.conf.
Let's see the entire smb.conf file.  I hate to spend time only to find a little misconfiguration is causing a problem.  Post the output of both of these commands```

cat /etc/samba/smb.conf

smbtree -d3

``` > 
I have tried to figure this out but I still don't fully understand the permissions and groups quite well enough.

We will get to this in just a bit.

When you post text based output you should post the data between [noparse]```
  
```[/noparse] blocks.  This is easily done using the [SIZE=5]**#**[/SIZE] icon that you see in center top of the advanced editor that you use to respond to this post.

---

### Post by Frogs Hair on 2016-06-19
Moved to *Networking & Wireless *

---

### Post by Jason_Stickler on 2016-06-19
> **bab1 said:**
> Does this mean there is no GUI interface?  
I am running gnome, it is still quite a different experience for me since my only real experience in computers up until this was Windows.  I am looking for something completely stable and I seem to have found that in Ubuntu.  Now I just need to learn more about it.
> You do not mount drives.  You mount file systems that reside on partitions (sda1 or sdb1 or sdb2).  Post the output this terminal command```
df -h
```  

```

Filesystem                       Size  Used Avail Use% Mounted on
/dev/mapper/The1337NAS--vg-root  101G   13G   84G  14% /
none                             4.0K     0  4.0K   0% /sys/fs/cgroup
udev                             7.8G  4.0K  7.8G   1% /dev
tmpfs                            1.6G  1.8M  1.6G   1% /run
none                             5.0M     0  5.0M   0% /run/lock
none                             7.8G  164K  7.8G   1% /run/shm
none                             100M   96K  100M   1% /run/user
/dev/sdb2                        237M  156M   69M  70% /boot
/dev/sdb1                        511M  3.4M  508M   1% /boot/efi
/dev/sda                         7.3T  4.5T  2.5T  65% /media/jason/NAS

```
> Do you mean that you can access the shares on Ubuntu from your Windows machine, but your wife can't?
Yes.  More specifically, I setup two accounts on the server itself and on login I am the only one that can see the data in /dev/sda.  From a Windows PC I could see the share in /dev/sda but could also only access with my server account - my wife could not access with her server account.

Thanks!

---

### Post by bab1 on 2016-06-19
And the rest????  I have edited the original post for clarity.  I need the 2 other outputs for proper diagnosis.

---

### Post by Jason_Stickler on 2016-06-19
My apologies, I missed those when I was going through:
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

    security = user
;    encrypt passwords = yes
    map to guest = bad user
;    guest account = nobody

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = workgroup

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
    username map = /etc/samba/smbusers
;    guest ok = no

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
[homes]
    comment = Home Directories
;    browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
    read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
    create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
    directory mask = 0775

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

[Media]
    comment = Media
    path = /media/jason/NAS/Media
    writeable = yes
;    browseable = yes
    valid users = cassy, jason
[TV]
    comment = TV
    path = /media/jason/NAS/Media/TV
;    writeable = yes
    browseable = yes
    guest ok = yes
    read only = yes
    write list = jason cassy
;    valid users = cassy, jason
    create mask = 0755
[Movies]
    comment = Movies
    path = /media/jason/NAS/Media/Movies
;    writeable = yes
    browseable = yes
    guest ok = yes
    read only = yes
    write list = jason cassy
;    valid users = cassy, jason
    create mask = 0755

[Music]
    comment = Music
    path = /media/jason/NAS/Media/Music
    public = yes
    only guest = yes
    writeable = no

```

```
jason@The1337NAS:/etc/samba$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface em1 ip=192.168.1.200 bcast=192.168.1.255 netmask=255.255.255.0
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.200 ( 192.168.1.200 )
Connecting to 192.168.1.200 at port 445
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
Got a positive name query response from 192.168.1.200 ( 192.168.1.200 )
Connecting to 192.168.1.200 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\THE1337NAS             The1337NAS server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name THE1337NAS<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name THE1337NAS<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name THE1337NAS<0x20>
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
        \\THE1337NAS\jason              Home Directories
        \\THE1337NAS\homes              Home Directories
        \\THE1337NAS\Media              Media
        \\THE1337NAS\TV                 TV
        \\THE1337NAS\Movies             Movies
        \\THE1337NAS\Music              Music
        \\THE1337NAS\IPC$               IPC Service (The1337NAS server (Samba, Ubuntu))
    \\OMGWTFBBQ              
resolve_lmhosts: Attempting lmhosts lookup for name OMGWTFBBQ<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name OMGWTFBBQ<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name OMGWTFBBQ<0x20>
resolve_hosts: getaddrinfo failed for name OMGWTFBBQ [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name OMGWTFBBQ<0x20>
Got a positive name query response from 192.168.1.66 ( 192.168.1.66 192.168.100.9 )
Connecting to 192.168.1.66 at port 445
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
    \\CASSY-PC               
resolve_lmhosts: Attempting lmhosts lookup for name CASSY-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name CASSY-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name CASSY-PC<0x20>
resolve_hosts: getaddrinfo failed for name CASSY-PC [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name CASSY-PC<0x20>
Got a positive name query response from 192.168.1.67 ( 192.168.1.67 )
Connecting to 192.168.1.67 at port 445
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure

```

Thanks!

---

### Post by bab1 on 2016-06-19
I think my original post was unclear.  No apologies needed.  It also looks like there isn't any problem with the smb.conf file (not including the share configs).

I'd like to see what Samba users you have configured.  Post the output of this command```
sudo pdbedit -L
```

Are you committed to using* /media* for all your shares?  The */media* section of the file system is traditionally for temporarily mounting removable media that is managed by udev controls.  Since this is for serving files I would use the traditional location of */srv* (such as ***/srv/nas***).  Let me see the current fstab file with this command```
cat /etc/fstab
```... and the blkid info for the partitions with this command```
sudo blkid -c /dev/null -o list
```

---

### Post by Jason_Stickler on 2016-06-19
Here is the additional information.  I am okay with moving the shares to a different location, most of my thing was I got it working and so it was good enough at the time, now I want to dig deeper.
```

   jason@The1337NAS:/etc/samba$ sudo pdbedit -L 
 [sudo] password for jason:  
 jason:1000:Jason Stickler 
 cassy:1001:Cassy Stickler 
 
``` 

 
```
 

 # /etc/fstab: static file system information. 

 # 
 # Use 'blkid' to print the universally unique identifier for a 
 # device; this may be used with UUID= as a more robust way to name devices 
 # that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 /dev/mapper/The1337NAS--vg-root /               ext4    errors=remount-ro 0       1 
 # /boot was on /dev/sdb2 during installation 
 UUID=0b410eb3-3a99-4042-a7a1-523290922d05 /boot           ext2    defaults        0       2 
 # /boot/efi was on /dev/sdb1 during installation 
 UUID=1529-553B  /boot/efi       vfat    defaults        0       1 
 /dev/mapper/The1337NAS--vg-swap_1 none            swap    sw              0       0 
 
``` 

 ```
 

 device     fs_type label    mount point    UUID 
 ------------------------------------------------------------------------------- 

 /dev/sda   ext4    NAS      /media/jason/NAS 1bcdd709-a424-41f4-a53c-4d5db326005f 
 /dev/sdb1  vfat             /boot/efi      1529-553B 
 /dev/sdb2  ext2             /boot          0b410eb3-3a99-4042-a7a1-523290922d05 
 /dev/sdb3  LVM2_member      (in use)       F0MDsq-ExmQ-nGKb-N9dl-tCrl-irKw-83e6hW 
 /dev/mapper/The1337NAS--vg-root 
            ext4             /              f39c5a92-5ffc-4a79-b308-461dccee87e6 
 /dev/mapper/The1337NAS--vg-swap_1 
            swap             <swap>         3771cdd2-ce31-4898-8d27-1448b21ec749

```

---

### Post by bab1 on 2016-06-19
I think that I have documented exactly what you need [***here***]("http://ubuntuforums.org/showthread.php?t=2313205").  Read though the thread and see what you think.  It's a lot to take in, but you can ask all the questions you want.  I will be able to help you at every step even if you need specific commands.  If you only work with the users group and the mountpoint at ***/srv/nas*** you can't get into too much trouble.  I will help you with the fstab part and walk you through the remounting of the partition NAS.

---

### Post by Jason_Stickler on 2016-06-21
Sorry for the delay in response.  I have been reading the other post you linked to and I believe it is starting to make some sense.  I essential will change the mount for /dev/sda so that it no longer points to /media/jason/NAS/Media and instead points to /srv/NAS.  My biggest concern right now is not losing the data on these drives since we have family pictures,etc on them.  I was thinking I do:
```
sudo mount --move /media/jason/NAS /srv/NAS 
```

I was not completely clear on if I crear the subdirectory first:
```
sudo mkdir -p /srv/nas
```

Thanks again.  My biggest thing is getting my public share setup by this weekend.

---

### Post by bab1 on 2016-06-21
> **Jason_Stickler said:**
> Sorry for the delay in response.  I have been reading the other post you linked to and I believe it is starting to make some sense.  I essential will change the mount for /dev/sda so that it no longer points to /media/jason/NAS/Media and instead points to /srv/NAS.  My biggest concern right now is not losing the data on these drives since we have family pictures,etc on them.  I was thinking I do:
```
sudo mount --move /media/jason/NAS /srv/NAS 
```

I was not completely clear on if I crear the subdirectory first:
```
sudo mkdir -p /srv/nas
```

Thanks again.  My biggest thing is getting my public share setup by this weekend.
The "mount --move" command won't do what you want to do.  The partition data is not affected by the mount process.  The partition is mounted every time you boot up anyway. 

Yes.  You need a mount point to mount the partition,  After you create the mountpoint post the output of these commands```

ls -l /srv

```
We can do this step by step.  I takes me about 15 minutes to do (and check) everything.  The delay will be our problem to work out.

[COLOR="#0000CD"]Edit: do not use CAPS or SPACES for names in Linux.  Poor form and you will not notice it when we are done.  Linux is case sensitive, Windows is not.[/COLOR]

---

### Post by Jason_Stickler on 2016-06-22
> **bab1 said:**
> 
Yes.  You need a mount point to mount the partition,  After you create the mountpoint post the output of these commands```

ls -l /srv

```
We can do this step by step.  I takes me about 15 minutes to do (and check) everything.  The delay will be our problem to work out.

[COLOR=#0000CD]Edit: do not use CAPS or SPACES for names in Linux.  Poor form and you will not notice it when we are done.  Linux is case sensitive, Windows is not.[/COLOR]

Understood, I have seen a few instances where the caps can be problematic.

```
jason@The1337NAS:~$ sudo mkdir /srv/nas[sudo] password for jason: 
jason@The1337NAS:~$ ls -l /srv
total 4
drwxr-xr-x 2 root root 4096 Jun 22 14:50 nas

```
I do apologize for the delays in time for me to respond to you.  Between work and other items time has been tight.  I appreciate your time and assistance on this.

---

### Post by bab1 on 2016-06-22
> **Jason_Stickler said:**
> Understood, I have seen a few instances where the caps can be problematic.

```
jason@The1337NAS:~$ sudo mkdir /srv/nas[sudo] password for jason: 
jason@The1337NAS:~$ ls -l /srv
total 4
drwxr-xr-x 2 root root 4096 Jun 22 14:50 nas

```
I do apologize for the delays in time for me to respond to you.  Between work and other items time has been tight.  I appreciate your time and assistance on this.
Now change the user group ownership of the directory with this command```
sudo chgrp users /srv/nas
```...then change the permissions with this  command```
sudo chmod 2775 /srv/nas
``` (this also sets the sgid bit on the empty directory)

Let's check your work now.  Post the output of this command ```
ls -l  /srv
```

---

### Post by Jason_Stickler on 2016-06-22
Here is the results:
```
jason@The1337NAS:~$ ls -l /srvtotal 4
drwxrwsr-x 2 root users 4096 Jun 22 14:50 nas
```

---

### Post by bab1 on 2016-06-22
> **Jason_Stickler said:**
> Here is the results:
```
jason@The1337NAS:~$ ls -l /srvtotal 4
drwxrwsr-x 2 root users 4096 Jun 22 14:50 nas
```
Perfect!  That is all that is needed for the mount point.  Now we need to work on the users.

Post the output of this this command to see the user group we are going to use```
getent group users
```

---

### Post by Jason_Stickler on 2016-06-22
Here you go:
```
jason@The1337NAS:~$ getent group users
users:x:100:

```

---

### Post by bab1 on 2016-06-23
> **Jason_Stickler said:**
> Here you go:
```
jason@The1337NAS:~$ getent group users
users:x:100:

```
We add the users (one by one ) with this commanad```
sudo addgroup <user_name> users
```

Then post the output again of ```
getent group users
```You should see each user listed.

---

### Post by Jason_Stickler on 2016-06-23
I was able to get both users added:
```
jason@The1337NAS:~$ getent group users
users:x:100:jason,cassy
```

---

### Post by bab1 on 2016-06-23
> **Jason_Stickler said:**
> I was able to get both users added:
```
jason@The1337NAS:~$ getent group users
users:x:100:jason,cassy
```
Great.  Our next task is to mount the NAS partition at its new location.  Before we do that I need to know how you mounted that partition originally.  What did you do to facilitate that action?

---

### Post by Jason_Stickler on 2016-06-23
> **bab1 said:**
> Great.  Our next task is to mount the NAS partition at its new location.  Before we do that I need to know how you mounted that partition originally.  What did you do to facilitate that action?

It was partitioned and mounted through the GUI.  I was just looking through the Disks GUI and saw that it was set to Auto-Mount - Yes.  I set the machine up almost a year ago and it was working so I didn't really mess with it but had little idea of the steps that I was doing.  I was following some tutorials online and a bit of the I will just try to figure it out method.  I don't recall the exact steps that I did but I know it was all through the GUI.

---

### Post by bab1 on 2016-06-23
> **Jason_Stickler said:**
> It was partitioned and mounted through the GUI.  I was just looking through the Disks GUI and saw that it was set to Auto-Mount - Yes.  I set the machine up almost a year ago and it was working so I didn't really mess with it but had little idea of the steps that I was doing.  I was following some tutorials online and a bit of the I will just try to figure it out method.  I don't recall the exact steps that I did but I know it was all through the GUI.
Unfortunately I don't know where the information for the present mount of NAS is located.  It's not in the fstab file which is processed first so I think we can just ignore what you have done.  We will have to unmount the NAS partition.  That is very simple.  The data will become unavailable for a bit, but it will not be destroyed,  just temporarily not available.

To unmount the partition use this command```
sudo umount /media/jason/NAS
```
Once that is done you can check that it is indeed unmounted with these two commands```

sudo blkid -c /dev/null -o list

df -h

```
Post the results so I can see.  At this point do not turn the computer off or the partition will be remounted.

---

### Post by Jason_Stickler on 2016-06-23
> **bab1 said:**
> Unfortunately I don't know where the information for the present mount of NAS is located.  It's not in the fstab file which is processed first so I think we can just ignore what you have done.  We will have to unmount the NAS partition.  That is very simple.  The data will become unavailable for a bit, but it will not be destroyed,  just temporarily not available.

To unmount the partition use this command```
sudo umount /media/jason/NAS
```


Well, I hit a snag.  When trying to do an unmount I am receiving the following error.  I tried to shut all of my automated services that would connect to this drive but it is still showing the same:
```
jason@The1337NAS:~$ sudo umount /media/jason/NASumount: /media/jason/NAS: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

---

### Post by Jason_Stickler on 2016-06-23
I also ran the following if this helps as well:
```

jason@The1337NAS:~$ fuser -m /dev/sda
/dev/sda:             5331c 20999c
jason@The1337NAS:~$ fuser -m /media/jason/NAS
/media/jason/NAS:     5331c 20999c
jason@The1337NAS:~$ ps auxw|grep 5331c
jason    13382  0.0  0.0  11748  2156 pts/14   S+   11:03   0:00 grep --color=auto 5331c
jason@The1337NAS:~$ ps auxw|grep 20999c
jason    13385  0.0  0.0  11748  2164 pts/14   S+   11:04   0:00 grep --color=auto 20999c
jason@The1337NAS:~$ who
jason    :0           2015-09-05 12:54 (:0)
jason    pts/14       2016-06-22 14:47 (192.168.1.66)
jason    pts/3        2016-06-19 23:00 (:0)
jason    pts/25       2016-06-19 00:39 (:0)

```

---

### Post by bab1 on 2016-06-23
> **Jason_Stickler said:**
> I also ran the following if this helps as well:
```

jason@The1337NAS:~$ fuser -m /dev/sda
/dev/sda:             5331c 20999c
jason@The1337NAS:~$ fuser -m /media/jason/NAS
/media/jason/NAS:     5331c 20999c
jason@The1337NAS:~$ ps auxw|grep 5331c
jason    13382  0.0  0.0  11748  2156 pts/14   S+   11:03   0:00 grep --color=auto 5331c
jason@The1337NAS:~$ ps auxw|grep 20999c
jason    13385  0.0  0.0  11748  2164 pts/14   S+   11:04   0:00 grep --color=auto 20999c
jason@The1337NAS:~$ who
jason    :0           2015-09-05 12:54 (:0)
jason    pts/14       2016-06-22 14:47 (192.168.1.66)
jason    pts/3        2016-06-19 23:00 (:0)
jason    pts/25       2016-06-19 00:39 (:0)

```
Someone, most likely you, have a directory or file file open from that partiition.  Close everything and make sure that you are only in your home directory.  Then try again.

[COLOR="#0000CD"]Edit: You may need to use the GUI to delete the mount that you created by deleting the share definition.[/COLOR]

---

### Post by Jason_Stickler on 2016-06-23
Ok, I was able to log off some of the other sessions and then I tried again and it worked this time:
```

jason@The1337NAS:/$ sudo blkid -c /dev/null -o list
device                             fs_type      label         mount point                            UUID
------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda                           ext4         NAS           (not mounted)                          1bcdd709-a424-41f4-a53c-4d5db326005f
/dev/sdb1                          vfat                       /boot/efi                              1529-553B
/dev/sdb2                          ext2                       /boot                                  0b410eb3-3a99-4042-a7a1-523290922d05
/dev/sdb3                          LVM2_member                (in use)                               F0MDsq-ExmQ-nGKb-N9dl-tCrl-irKw-83e6hW
/dev/mapper/The1337NAS--vg-root    ext4                       /                                      f39c5a92-5ffc-4a79-b308-461dccee87e6
/dev/mapper/The1337NAS--vg-swap_1  swap                       <swap>                                 3771cdd2-ce31-4898-8d27-1448b21ec749

``````

jason@The1337NAS:/$ df -h
df: â€˜/root/.gvfsâ€™: Permission denied
Filesystem                       Size  Used Avail Use% Mounted on
/dev/mapper/The1337NAS--vg-root  101G   13G   84G  14% /
none                             4.0K     0  4.0K   0% /sys/fs/cgroup
udev                             7.8G  4.0K  7.8G   1% /dev
tmpfs                            1.6G  6.9M  1.6G   1% /run
none                             5.0M     0  5.0M   0% /run/lock
none                             7.8G  168K  7.8G   1% /run/shm
none                             100M   92K  100M   1% /run/user
/dev/sdb2                        237M  156M   69M  70% /boot
/dev/sdb1                        511M  3.4M  508M   1% /boot/efi
```

---

### Post by bab1 on 2016-06-23
> **Jason_Stickler said:**
> Ok, I was able to log off some of the other sessions and then I tried again and it worked this time:
```

jason@The1337NAS:/$ sudo blkid -c /dev/null -o list
device                             fs_type      label         mount point                            UUID
------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda                           ext4         NAS           (not mounted)                          1bcdd709-a424-41f4-a53c-4d5db326005f
/dev/sdb1                          vfat                       /boot/efi                              1529-553B
/dev/sdb2                          ext2                       /boot                                  0b410eb3-3a99-4042-a7a1-523290922d05
/dev/sdb3                          LVM2_member                (in use)                               F0MDsq-ExmQ-nGKb-N9dl-tCrl-irKw-83e6hW
/dev/mapper/The1337NAS--vg-root    ext4                       /                                      f39c5a92-5ffc-4a79-b308-461dccee87e6
/dev/mapper/The1337NAS--vg-swap_1  swap                       <swap>                                 3771cdd2-ce31-4898-8d27-1448b21ec749

``````

jason@The1337NAS:/$ df -h
df: â€˜/root/.gvfsâ€™: Permission denied
Filesystem                       Size  Used Avail Use% Mounted on
/dev/mapper/The1337NAS--vg-root  101G   13G   84G  14% /
none                             4.0K     0  4.0K   0% /sys/fs/cgroup
udev                             7.8G  4.0K  7.8G   1% /dev
tmpfs                            1.6G  6.9M  1.6G   1% /run
none                             5.0M     0  5.0M   0% /run/lock
none                             7.8G  168K  7.8G   1% /run/shm
none                             100M   92K  100M   1% /run/user
/dev/sdb2                        237M  156M   69M  70% /boot
/dev/sdb1                        511M  3.4M  508M   1% /boot/efi
```

Now we need to edit the /etc/fstab file to mount the partition at boot time.  You need to at this at the bottom of the file```

# NAS partitition mounted at /srv/nas
1bcdd709-a424-41f4-a53c-4d5db326005f  /srv/nas  ext4  defaults  0  0 
```
Your fstab file will look like this when done```
# /etc/fstab: static file system information. 

 # 
 # Use 'blkid' to print the universally unique identifier for a 
 # device; this may be used with UUID= as a more robust way to name devices 
 # that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 /dev/mapper/The1337NAS--vg-root /               ext4    errors=remount-ro 0       1 
 # /boot was on /dev/sdb2 during installation 
 UUID=0b410eb3-3a99-4042-a7a1-523290922d05 /boot           ext2    defaults        0       2 
 # /boot/efi was on /dev/sdb1 during installation 
 UUID=1529-553B  /boot/efi       vfat    defaults        0       1 
 /dev/mapper/The1337NAS--vg-swap_1 none            swap    sw              0       0
[COLOR="#0000CD"]# NAS partitition mounted at /srv/nas
1bcdd709-a424-41f4-a53c-4d5db326005f  /srv/nas  ext4  defaults  0  0 [/COLOR]
```The part in blue is what you added.

You can use nano to edit the file like this```
sudo nano /etc/fstab
```

Then remount everything with this command ```
sudo mount -a
```You should see the new location with this ```
df -h
```

---

### Post by Jason_Stickler on 2016-06-23
Got it - I did have to add UUID= in front of the fstab entry (I figured it out without asking!!!) and was able to mount and see the files:
```
jason@The1337NAS:/$ df -hdf: â/root/.gvfsâ: Permission denied
Filesystem                       Size  Used Avail Use% Mounted on
/dev/mapper/The1337NAS--vg-root  101G   13G   84G  14% /
none                             4.0K     0  4.0K   0% /sys/fs/cgroup
udev                             7.8G  4.0K  7.8G   1% /dev
tmpfs                            1.6G  6.9M  1.6G   1% /run
none                             5.0M     0  5.0M   0% /run/lock
none                             7.8G  168K  7.8G   1% /run/shm
none                             100M   92K  100M   1% /run/user
/dev/sdb2                        237M  156M   69M  70% /boot
/dev/sdb1                        511M  3.4M  508M   1% /boot/efi
/dev/sda                         7.3T  4.5T  2.5T  65% /srv/nas



```

---

### Post by bab1 on 2016-06-23
> **Jason_Stickler said:**
> Got it - I did have to add UUID= in front of the fstab entry (I figured it out without asking!!!) and was able to mount and see the files:
```
jason@The1337NAS:/$ df -hdf: â/root/.gvfsâ: Permission denied
Filesystem                       Size  Used Avail Use% Mounted on
/dev/mapper/The1337NAS--vg-root  101G   13G   84G  14% /
none                             4.0K     0  4.0K   0% /sys/fs/cgroup
udev                             7.8G  4.0K  7.8G   1% /dev
tmpfs                            1.6G  6.9M  1.6G   1% /run
none                             5.0M     0  5.0M   0% /run/lock
none                             7.8G  168K  7.8G   1% /run/shm
none                             100M   92K  100M   1% /run/user
/dev/sdb2                        237M  156M   69M  70% /boot
/dev/sdb1                        511M  3.4M  508M   1% /boot/efi
/dev/sda                         7.3T  4.5T  2.5T  65% /srv/nas



```let's do some housekeeping.  Post the output of this command```
ls -l /var/lib/samba/usershares
```

---

### Post by Jason_Stickler on 2016-06-23
There is nothing in there:
```

jason@The1337NAS:/$ ls -l /var/lib/samba/usershares
total 0

```

---

### Post by bab1 on 2016-06-23
> **Jason_Stickler said:**
> There is nothing in there:
```

jason@The1337NAS:/$ ls -l /var/lib/samba/usershares
total 0

```
Great.  So now you can edit the /etc/samba/smb.conf file with nano.  Just change the path part in your definition to the current path of /srv/nas and restart the smbd process with this command```
sudo service smbd restart
```

See if you can find the share now.

---

### Post by Jason_Stickler on 2016-06-23
Yes, I am able to see all the shares.  I have my credentials cached on the machine I am connected to so I won't be able to see if other users can connect until I get home.

---

### Post by bab1 on 2016-06-23
> **Jason_Stickler said:**
> Yes, I am able to see all the shares.  I have my credentials cached on the machine I am connected to so I won't be able to see if other users can connect until I get home.
Most likely we will need to edit the definition tonight.  Where are you in the world.  I am GMT-7 in California USA.

---

### Post by Jason_Stickler on 2016-06-23
I am GMT-5 in Minnesota.  I am not sure what my availability is tonight but I can test as soon as possible and let you know the results.  I know that my user account - jason works.  I will try the cassy one and an anonymous account.  Let me know if there is information to capture if they fail.
Thanks!

---

### Post by bab1 on 2016-06-23
> **Jason_Stickler said:**
> I am GMT-5 in Minnesota.  I am not sure what my availability is tonight but I can test as soon as possible and let you know the results.  I know that my user account - jason works.  I will try the cassy one and an anonymous account.  Let me know if there is information to capture if they fail.
Thanks!

I know what to do.  I just need to know what happens.

---

### Post by Jason_Stickler on 2016-06-24
I was able to do a little testing tonight and all the shares, except Media, allow users to access without credentials and they cannot create files, which is precisely what I wanted. I need to do some testing with my wife's account as I can't remember the password.  I may also want to create a share for non-authenticated users to write to. I will try setting that up tomorrow.

---

### Post by Jason_Stickler on 2016-06-24
I was able to test a little more and as stated a non-authenticated user has read rights to everywhere I wanted.  The account cassy is able to view everything but when I attempted to connect to media with her account it did not work - I did reset the password.  I also did setup a public folder, but non-authenticated users do not have access to write to it.

---

### Post by bab1 on 2016-06-24
I think the group ownership needs to be tweaked.  Let's see what your setting is now.  Post the output of this command ```
ls l /srv/nas
```

---

### Post by Jason_Stickler on 2016-06-24
Here is the output - I don't know why but during my initial installation I created a folder called Media - I think the intent is that Music/Movies/etc would go in there and other documents would be at the root.

```
jason@The1337NAS:/$ ls -l /srv/nas
total 20
drwx------  2 root  root  16384 Jul  2  2015 lost+found
drwxrwxr-x 23 jason jason  4096 Jun 24 05:38 Media

jason@The1337NAS:/$ ls -l /srv/nas/Media
total 136
drwxr-xr-x    4 jason jason  4096 Nov 17  2015 Applications
drwxr-xr-x    7 jason jason  4096 May 11 09:53 Audio Books
drwxr-xr-x    3 jason jason  4096 Apr  6 20:14 Comics
drwxrwxr-x    7 jason jason  4096 Sep 10  2015 Home Videos
drwxr-xr-x  108 jason jason 12288 Jun 23 16:04 Movies
drwxr-xr-x  224 jason jason 12288 May  5 15:25 Music
drwxrwxr-x   20 jason jason  4096 Apr  9 15:22 Pictures
drwxr-xr-x    2 jason jason  4096 Jun 24 05:37 Public
drwxr-xr-x   76 jason jason 12288 Jun 23 13:24 TV
```

---

### Post by bab1 on 2016-06-24
> **Jason_Stickler said:**
> Here is the output - I don't know why but during my initial installation I created a folder called Media - I think the intent is that Music/Movies/etc would go in there and other documents would be at the root.

```
jason@The1337NAS:/$ ls -l /srv/nas
total 20
drwx------  2 root  root  16384 Jul  2  2015 lost+found
drwxrwxr-x 23 jason jason  4096 Jun 24 05:38 Media

jason@The1337NAS:/$ ls -l /srv/nas/Media
total 136
drwxr-xr-x    4 jason jason  4096 Nov 17  2015 Applications
drwxr-xr-x    7 jason jason  4096 May 11 09:53 Audio Books
drwxr-xr-x    3 jason jason  4096 Apr  6 20:14 Comics
drwxrwxr-x    7 jason jason  4096 Sep 10  2015 Home Videos
drwxr-xr-x  108 jason jason 12288 Jun 23 16:04 Movies
drwxr-xr-x  224 jason jason 12288 May  5 15:25 Music
drwxrwxr-x   20 jason jason  4096 Apr  9 15:22 Pictures
drwxr-xr-x    2 jason jason  4096 Jun 24 05:37 Public
drwxr-xr-x   76 jason jason 12288 Jun 23 13:24 TV
```

The first thing we need to do is change the group ownership with this command```
sudo chgrp -R users /srv/nas/Media
```
Again post the output of ```
ls -l /srv/nas/Media
```
[COLOR="#0000CD"]Edit: Then test your wife's account.[/COLOR]

---

### Post by Jason_Stickler on 2016-06-24
> **bab1 said:**
> The first thing we need to do is change the group ownership with this command```
sudo chgrp -R users /srv/nas/Media
```
Again post the output of ```
ls -l /srv/nas/Media
```
[COLOR=#0000CD]Edit: Then test your wife's account.[/COLOR]

```
jason@The1337NAS:/$ ls -l /srv/nas/Mediatotal 136
drwxr-xr-x    4 jason users  4096 Nov 17  2015 Applications
drwxr-xr-x    7 jason users  4096 May 11 09:53 Audio Books
drwxr-xr-x    3 jason users  4096 Apr  6 20:14 Comics
drwxrwxr-x    7 jason users  4096 Sep 10  2015 Home Videos
drwxr-xr-x  108 jason users 12288 Jun 24 12:09 Movies
drwxr-xr-x  224 jason users 12288 May  5 15:25 Music
drwxrwxr-x   20 jason users  4096 Apr  9 15:22 Pictures
drwxr-xr-x    2 jason users  4096 Jun 24 05:37 Public
drwxr-xr-x   76 jason users 12288 Jun 23 13:24 TV



```
I will let you know if her account works as soon as possible.

---

### Post by bab1 on 2016-06-24
> **Jason_Stickler said:**
> ```
jason@The1337NAS:/$ ls -l /srv/nas/Media
total 136
drwxr-xr-x    4 jason users  4096 Nov 17  2015 Applications
drwxr-xr-x    7 jason users  4096 May 11 09:53 Audio Books
drwxr-xr-x    3 jason users  4096 Apr  6 20:14 Comics
drwxrwxr-x    7 jason users  4096 Sep 10  2015 Home Videos
drwxr-xr-x  108 jason users 12288 Jun 24 12:09 Movies
drwxr-xr-x  224 jason users 12288 May  5 15:25 Music
drwxrwxr-x   20 jason users  4096 Apr  9 15:22 Pictures
drwxr-xr-x    2 jason users  4096 Jun 24 05:37 Public
drwxr-xr-x   76 jason users 12288 Jun 23 13:24 TV



```
I will let you know if her account works as soon as possible.
As you can see the directories (and files inside) are now owned by the user-group ***users*** of which both you and your wife are members of.

---

### Post by Jason_Stickler on 2016-06-24
> **bab1 said:**
> As you can see the directories (and files inside) are now owned by the user-group ***users*** of which both you and your wife are members of.
That makes sense.  I ssh'ed in to the device and then did a cat on a file in /srv/nas/Media and was able to read it so that is working.  I tried reading through the other thread to figure out giving just the public folder write access but it went a little over my head.

---

### Post by Jason_Stickler on 2016-06-24
> **Jason_Stickler said:**
> That makes sense.  I ssh'ed in to the device and then did a cat on a file in /srv/nas/Media and was able to read it so that is working.  I tried reading through the other thread to figure out giving just the public folder write access but it went a little over my head.

Correction, I just had not gone far enough.  I found this which was EXTREMELY helpful.  My last question is where is the .smb-trash folder actually located?
```

        [COLOR=#000000][FONT=&amp][Public]  [/FONT][/COLOR][COLOR=#FF0000][FONT=&amp]<--Tthe name of the share[/FONT][/COLOR]        
        comment = Shared Data [COLOR=#FF0000]<-- Comment used in some test scripts[/COLOR]
        path = /srv/nas/public [COLOR=#FF0000]<-- Location of the data[/COLOR]
        browseable = yes  [COLOR=#FF0000]<-- Visible to all users when browsing[/COLOR]
        guest ok = yes  [COLOR=#FF0000]<-- No login needed (all users are nobody:nogroup)[/COLOR]
        force group = users  [COLOR=#FF0000]<-- Forces the user-group of your choice [/COLOR]
        writeable = yes  [COLOR=#FF0000]<-- Allows writing to the share[/COLOR]
        create mask = 0664  [COLOR=#FF0000]<-- Sets the created file permissions [/COLOR]
        force directory mode = 2775  [COLOR=#FF0000]Sets the created directory permissions[/COLOR]
        vfs objects = recycle  [COLOR=#FF0000]The following sets up a recycle bin that is a hidden directory[/COLOR]
        recycle:repository = .smb-trash [COLOR=#FF0000]<-- the hidden directory[/COLOR]
        recycle:keeptree = yes [COLOR=#000000][FONT=&amp]        
        recycle:versions = yes
[/FONT][/COLOR]
```

---

### Post by bab1 on 2016-06-24
SSH is not a good test of Samba file sharing.  You need to use Samba (CIFS/SMB) to access the directories.

Edit:
------
> where is the .smb-trash folder actually located?
At the root of the share.

---

### Post by Jason_Stickler on 2016-06-25
> **bab1 said:**
> SSH is not a good test of Samba file sharing.  You need to use Samba (CIFS/SMB) to access the directories.


You are correct - cassy is still unable to log in to the share for Media.  I logged in with her account to the server and in the GUI all folders have a lock symbol - well almost all.  I am surprised she is having permission issues to Media as it appears that the users group has full permission:
```
drwxrwxr-x 23 jason users  4096 Jun 24 05:38 Media
```

The folders beneath are a different story:
```

drwxr-xr-x    4 jason users  4096 Nov 17  2015 Applications
drwxr-xr-x    7 jason users  4096 May 11 09:53 Audio Books
drwxr-xr-x    3 jason users  4096 Apr  6 20:14 Comics
drwxrwxr-x    7 jason users  4096 Sep 10  2015 Home Videos
drwxr-xr-x  108 jason users 12288 Jun 24 12:16 Movies
drwxr-xr-x  224 jason users 12288 May  5 15:25 Music
drwxrwxr-x   20 jason users  4096 Apr  9 15:22 Pictures
drwxrwxrwx    3 jason users  4096 Jun 24 22:41 Public
drwxr-xr-x   76 jason users 12288 Jun 24 13:45 TV

```

---

### Post by bab1 on 2016-06-25
> **Jason_Stickler said:**
> You are correct - cassy is still unable to log in to the share for Media.  I logged in with her account to the server and in the GUI all folders have a lock symbol - well almost all.  

I'm sure you don't really mean exactly that.  Are you logging in using ssh or samba (the GUI is irrelevant).  Read your statement again. 

> 
I am surprised she is having permission issues to Media as it appears that the users group has full permission:
```
drwxrwxr-x 23 jason users  4096 Jun 24 05:38 Media
```

The folders beneath are a different story:
```

drwxr-xr-x    4 jason users  4096 Nov 17  2015 Applications
drwxr-xr-x    7 jason users  4096 May 11 09:53 Audio Books
drwxr-xr-x    3 jason users  4096 Apr  6 20:14 Comics
drwxrwxr-x    7 jason users  4096 Sep 10  2015 Home Videos
drwxr-xr-x  108 jason users 12288 Jun 24 12:16 Movies
drwxr-xr-x  224 jason users 12288 May  5 15:25 Music
drwxrwxr-x   20 jason users  4096 Apr  9 15:22 Pictures
drwxrwxrwx    3 jason users  4096 Jun 24 22:41 Public
drwxr-xr-x   76 jason users 12288 Jun 24 13:45 TV

```
The permissions were either not set on Ubuntu or you created the files as the root user.  In any event we can cure this problem with this command```


sudo chmod -R g+w /srv/nas

```
Try using the cassy account again.

FWIW the Public directory should not be under a restricted share.  It should be at this level /srv/nas/public

[COLOR="#0000CD"]Edit:  I re did the command.  We needed to add a write (w) permission.[/COLOR]

---

### Post by Jason_Stickler on 2016-06-25
> **bab1 said:**
> I'm sure you don't really mean exactly that.  Are you logging in using ssh or samba (the GUI is irrelevant).  Read your statement again. 

Sorry, what I meant to say is using SSH I was able to the files logged in as cassy, but through samba it did not work.

> 
The permissions were either not set on Ubuntu or you created the files as the root user.  In any event we can cure this problem with this command```


sudo chmod -R g+w /srv/nas

```
Try using the cassy account again.

FWIW the Public directory should not be under a restricted share.  It should be at this level /srv/nas/public

[COLOR=#0000CD]Edit:  I re did the command.  We needed to add a write (w) permission.[/COLOR]

I moved the public folder per your recommendation - makes sense not to put it in a restricted share.  

I still did not have luck with the cassy account.  

```

jason@The1337NAS:/$ ls -l /srv/nas/Media
total 136
drwxrwxr-x    4 jason users  4096 Nov 17  2015 Applications
drwxrwxr-x    7 jason users  4096 May 11 09:53 Audio Books
drwxrwxr-x    3 jason users  4096 Apr  6 20:14 Comics
drwxrwxr-x    7 jason users  4096 Sep 10  2015 Home Videos
drwxrwxr-x  108 jason users 12288 Jun 24 12:16 Movies
drwxrwxr-x  224 jason users 12288 May  5 15:25 Music
drwxrwxr-x   20 jason users  4096 Apr  9 15:22 Pictures
drwxrwxr-x   76 jason users 12288 Jun 24 13:45 TV
jason@The1337NAS:/$ ls -l /srv/nas
total 24
drwxrw----  2 root  root  16384 Jul  2  2015 lost+found
drwxrwxr-x 23 jason users  4096 Jun 24 05:38 Media
drwxrwxrwx  3 jason jason  4096 Jun 24 23:49 public



```

I looked deeper and found that even after running the command you provided a lot of my permissions are just messed up deeper.
```

drwxrw---- 3 jason users 4096 Feb  7 15:57 The Lord of the Rings - Fellowship of the Ring



```

---

### Post by Jason_Stickler on 2016-06-25
OK, I did fix some of the permissions - it looks like I may need to apply each at the folder level :confused:

I was then able to navigate to these on the Read only Samba share without issue, prior to the change below only a handful apparently worked.

```

sudo chmod -R ug=rwX,o=rX /srv/nas/Media/Movies

```

```

drwxrwxr-x 3 jason users 4096 Feb  7 15:57 The Lord of the Rings - Fellowship of the Ring

```

---

### Post by bab1 on 2016-06-25
> **Jason_Stickler said:**
> OK, I did fix some of the permissions - it looks like I may need to apply each at the folder level:

```

sudo chmod -R ug=rwX,o=rX /srv/nas/Media/Movies

```

```

drwxrwxr-x 3 jason users 4096 Feb  7 15:57 The Lord of the Rings - Fellowship of the Ring

```
Try not to reply until you have thought it all out.  Edit the post if you need to add additional data.

The -R is recursive -- no need to do each level.

Post the share definition you are using.

---

### Post by Jason_Stickler on 2016-06-25
> **bab1 said:**
> Try not to reply until you have thought it all out.  Edit the post if you need to add additional data.

The -R is recursive -- no need to do each level.

Post the share definition you are using.

My apologies, I need to take a bit more time to think of other possibilities.  I do appreciate you sticking through my lack of knowledge on this.

I understand that the -R is recursive, but I didn't understand why some of the levels didn't appear to be modified.  Now that I look or think about it the read permission I don't think was ever necessarily changed I don't believe.

```

[Media]
        comment = Media
        path = /srv/nas/Media
        writeable = yes
        browseable = yes
        valid users = cassy,jason
        guest ok = no



```

I know this still has the M capitalized.  I have learned my lesson on NOT doing that again.

---

### Post by bab1 on 2016-06-25
> **Jason_Stickler said:**
> My apologies, I need to take a bit more time to think of other possibilities.  I do appreciate you sticking through my lack of knowledge on this.

I understand that the -R is recursive, but I didn't understand why some of the levels didn't appear to be modified.  Now that I look or think about it the read permission I don't think was ever necessarily changed I don't believe.

```

[Media]
        comment = Media
        path = /srv/nas/Media
        writeable = yes
        browseable = yes
        valid users = cassy,jason
        guest ok = no



```

I know this still has the M capitalized.  I have learned my lesson on NOT doing that again.
Try this definition (don't forget to restart the smbd daemon)```

[Media]
        comment = Media
        path = /srv/nas/Media
        writeable = yes
        browseable = yes
        valid users = @users
        guest ok = no
        force group = users
        create mask = 0664
        directory mask = 2775
        

```
If this doesn't work, post the output of this while logged to the terminal (ssh) as cassy
```
smbtree -d3
```

---

