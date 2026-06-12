---
title: "File Sharing in 15.10"
date: 2016-04-17
forum: Networking &amp; Wireless
---

### Post by Infamshxr on 2016-04-17
Hey everyone. Having some issues setting up my new Kubuntu 15.10 installation. Mostly because I haven't used Linux much in the last 5 years or so.

What I have:
120SSD with Kubuntu install on it
1TB Media Drive
1TB Backup Drive

What I'm trying to do is share the media drive over the network so every computer, phone, tablet, etc can access the files. In Dolphin, I went to the folder properties, chose to share the folder, set to allow guests, Basically I don't want/need any security on this folder. Just complicates things. 

So I did that, didn't work. Noticed samba wasn't installed by default. Looked up a tutorial about setting up samba for file sharing (I don't remember it being this difficult). Got it done, and now I can see the media drive from other devices, but can't access it. On my Kubuntu box, if I got to the smb:// folder and access the media drive from there I get an error saying "The file or folder smb://aaron-desktop/Media Drive does not exist."

I followed this guide after the obvious way didn't work.. [https://www.howtoforge.com/tutorial/samba-server-ubuntu/](https://www.howtoforge.com/tutorial/samba-server-ubuntu/)

So... I'm at a loss now. I've scoured the web but haven't found a working answer. Thanks in advance for any help!

Here is my smb.conf file
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

# server string is the equivalent of the NT Description field
	server string = Samba Server %v

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no
   
   netbios name = ubuntu
   security = user
   map to guest = bad user

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

[Media Drive]
path = '/media/aaron/Media Drive/'
browsable =yes
writable = yes
guest ok = yes
read only = no
force user = nobody
public = yes
writable = yes
available = yes

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

### Post by Infamshxr on 2016-04-17
Forgot to subscribe to my thread, sorry for double posting

---

### Post by bab1 on 2016-04-18
> **Infamshxr said:**
> ... I'm trying to share the media drive over the network so every computer, phone, tablet, etc can access the files. ...Basically I don't want/need any security on this folder. Just complicates things. 

This is a working share definition as long as the path is correct. I tested it with a different path```

[Media Drive]
path = '/media/aaron/Media Drive/'
guest ok = yes
browseable = yes
writeable = yes
create mask = 0666
directory mask = 777
force user = nobody

```...the force user line is redundant.  The guest user is already the user nobody.  I'm sure the tutorial was just being a bit paranoid. After you make the changes you need to restart the Samba server (smbd) with this command```
sudo service smbd restart
``` 

For neatness I would move the share definition to the very bottom of the smb.conf file.  Then, if I want to look at my share configuration I can use the tail command like this```
tail -n10 /etc/samba/smb.conf
```...this shows just the last 10 lines of the smb.conf file.

---

### Post by Infamshxr on 2016-04-18
Ok, so it does work, replacing my personal folder paths with yours... Good news there, so samba is working. As far as the redundancy, I looked at two tutorials while troubleshooting, one was slightly different but same basic idea....

So of its not my samba config file, what could it be? The two 1tb drives are identical WD Blue drives and are NTFS from when I was running Windows. They are both automounted at startup using gnome disk utility cuz I read there isn't an easy way to do it in straight KDE 5 right now. Disks does the job, so I don't care lol. 
What other info could I give that might explain why it's working for you and not for me?

Edit: also, I looked at your code you sent, it is slightly different than mine. I will change mine to match in the morning and report back wether it worked or not.

---

### Post by bab1 on 2016-04-18
If this works on a partition that the ownership and permissions allow you to access the data, but not on the 2 drives in question then problem is a file system ownership and permissions issue.  Samba share access permissions can't override Linux permissions.  An additional problem is the NTFS formatting on your HDD's.  This just complicates the problem as you can only set the permissions when the partitions on the HDD's are mounted.  This means you have to be concerned with how these disks are mounted when Kubuntu boots up.  The proper mount is via /etc/fstab file configuration rather than the *"disks"* utility.

---

### Post by Infamshxr on 2016-04-18
Hmm.... Maybe I should just format those drives into ext4? Would that make things easier? And if I do format them to ext4, will Windows still be able to access the drives and all that jazz?

---

### Post by bab1 on 2016-04-18
> **Infamshxr said:**
> Hmm.... Maybe I should just format those drives into ext4? Would that make things easier? And if I do format them to ext4, will Windows still be able to access the drives and all that jazz?
All that jazz?  What does that mean?

The file system format is important to the OS when partition is locally mounted at boot time.  Remote access is a little different.  Windows doesn't know or care about that formatting other than whether the user has access permissions to the (server) share(s).

Since you are using a Linux OS it's best to format the partitions as EXT4 and have them mount at boot time via /etc/fstab static file configuration.

---

### Post by Infamshxr on 2016-04-18
Sorry figure of speech lol. I'll give that a go though in the morning. I'll change the coding in my config file then switch everything over to ext4. I'll get rid of disks and then edit my fstab for automounting. Then I'll test everything and report back. Thanks for the help so far! Much appreciated!

---

### Post by Infamshxr on 2016-04-18
Well, switched everything over to ext4, setup automounting in fstab, and changed my smb.conf file. Unfortunately, same problem. I did discover something while editing my fstab and was wondering if I need to do the same thing in my smb.conf file... for my file path of /dev/sda1 I had to change '/media/aaron/Media Drive' to /media/aaron/Media\040Drive. Maybe I need to do the same thing in my smb.conf file too?

EDIT: Crap, no luck trying that. Maybe it's something I changed in the global settings? 

```

   netbios name = ubuntu
   security = user
   map to guest = bad user

```

That's what I added to the global settings as I followed in the tutorial.

EDIT: Added another folder location and I get the same problem. So the path is not the problem. Not sure if it's permissions or what...

From my Windows 10 laptop, it shows everything updated correctly. Shows aaron-desktop, I open that up and lists Documents and Media Drive. When I try opening one of those two folders, I get an error saying Windows can't access \\AARON-DESKTOP\Media Drive, click the details button and says that The network path was not found. Tried on my android phone with ES File Explorer and similar issue. I just don't get an error message on that. I tap on a folder and it just doesn't do anything.

EDIT: Made some changes after reading some other threads regarding this subject.

```

[global]
        server string = Samba Server %v
        server role = standalone server
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb

[Media Drive]
        path = '/media/aaron/Media Drive/'
        force user = nobody
        read only = No
        create mask = 0777
        directory mask = 0777
        guest ok = Yes

[Documents]
        path = '/media/aaron/Documents/'
        force user = nobody
        read only = No
        create mask = 0777
        directory mask = 0777
        guest ok = Yes

```

So that's my new smb.conf file and now I'm getting an error from my Windows 10 laptop saying I don't have permission to access Media Drive or Documents. Not sure if I made progress or took a step backwards here... Gonna keep researching and troubleshooting while I wait for a reply.

---

### Post by bab1 on 2016-04-18
> **Infamshxr said:**
> Well, switched everything over to ext4, setup automounting in fstab, and changed my smb.conf file. Unfortunately, same problem. I did discover something while editing my fstab and was wondering if I need to do the same thing in my smb.conf file... for my file path of /dev/sda1 I had to change '/media/aaron/Media Drive' to /media/aaron/Media\040Drive. Maybe I need to do the same thing in my smb.conf file too?

EDIT: Crap, no luck trying that. Maybe it's something I changed in the global settings? 

```

   netbios name = ubuntu
   security = user
   map to guest = bad user

```

That's what I added to the global settings as I followed in the tutorial.

EDIT: Added another folder location and I get the same problem. So the path is not the problem. Not sure if it's permissions or what...

From my Windows 10 laptop, it shows everything updated correctly. Shows aaron-desktop, I open that up and lists Documents and Media Drive. When I try opening one of those two folders, I get an error saying Windows can't access \\AARON-DESKTOP\Media Drive, click the details button and says that The network path was not found. Tried on my android phone with ES File Explorer and similar issue. I just don't get an error message on that. I tap on a folder and it just doesn't do anything.

EDIT: Made some changes after reading some other threads regarding this subject.

```

[global]
        server string = Samba Server %v
        server role = standalone server
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb

[Media Drive]
        path = '/media/aaron/Media Drive/'
        force user = nobody
        read only = No
        create mask = 0777
        directory mask = 0777
        guest ok = Yes

[Documents]
        path = '/media/aaron/Documents/'
        force user = nobody
        read only = No
        create mask = 0777
        directory mask = 0777
        guest ok = Yes

```

So that's my new smb.conf file and now I'm getting an error from my Windows 10 laptop saying I don't have permission to access Media Drive or Documents. Not sure if I made progress or took a step backwards here... Gonna keep researching and troubleshooting while I wait for a reply.
Whacking away at this doesn't help much.  There are only 3 parts to a successful set up[LIST=1]
[*]Create both Linux and Samba users if needed
[*]Configure file system that the share data resides on (ownership and permissions)
[*]Create Samba share definitions
[*]
[/LIST]
The order is somewhat important.  You need owners to set the ownership of the directory.

---

### Post by Infamshxr on 2016-04-18
Well reading into some threads, I created a samba user aaron (which is my username on the Kubuntu box) I'm not sure if I need to create any other users in there for my Windows 10 laptop, my phone, my FireStick, or my Kodi HTPC to access the share as well. I was messing with the permissions and such of the Media Drive folder (haven't touched the Documents folder, since it was just a test to see if the Media Drive location was a problem) and first did
```
sudo chown -R nobody:nogroup '/media/aaron/Media Drive'

```
That just messed things up while I was using the Kubuntu box, wasn't able to paste anything into the folder. So I changed it to
```
sudo chown -R aaron: '/media/aaron/Media Drive'

```
As far as the share definitions. Isn't that already done? I know I did it out of order while troubleshooting, though. What other info can I give you to help figure why this still isn't working?

---

### Post by bab1 on 2016-04-19
> **Infamshxr said:**
> Well reading into some threads, I created a samba user aaron (which is my username on the Kubuntu box) I'm not sure if I need to create any other users in there for my Windows 10 laptop, my phone, my FireStick, or my Kodi HTPC to access the share as well. I was messing with the permissions and such of the Media Drive folder (haven't touched the Documents folder, since it was just a test to see if the Media Drive location was a problem) and first did
```
sudo chown -R nobody:nogroup '/media/aaron/Media Drive'

```
That just messed things up while I was using the Kubuntu box, wasn't able to paste anything into the folder. So I changed it to
```
sudo chown -R aaron: '/media/aaron/Media Drive'

```
As far as the share definitions. Isn't that already done? I know I did it out of order while troubleshooting, though. What other info can I give you to help figure why this still isn't working?
We can just step through the first 2 sections.  Let's start with posting the output of these commands (#=my comments only)```

# users 
tail -n5 /etc/passwd
sudo pdbedit -L

#file system
cat /etc/fstab
sudo blkid -c /dev/null -o list

# ownership and permissions
ls -l /media
ls -l /media/aarron

```

FWIW -- I never use /media for permanently mounted file systems (partitions).  That directory (/media) is for the **temporary** mount of removable media, such as flash cards and sticks or CD and DVD players.  Depending on what the administrator is using the mounted partition the proper place can be /srv (file server) /data (all data) or some other logical name.  I have all my Samba and NFS shared data at /srv.

---

### Post by Infamshxr on 2016-04-19
```

#users

aaron@aaron-desktop:~$ tail -n5 /etc/passwd
rtkit:x:115:124:RealtimeKit,,,:/proc:/bin/false
saned:x:116:125::/var/lib/saned:/bin/false
sddm:x:117:126:Simple Desktop Display Manager:/var/lib/sddm:/bin/false
usbmux:x:118:46:usbmux daemon,,,:/var/lib/usbmux:/bin/false
aaron:x:1000:1000:Aaron Loewer,,,:/home/aaron:/bin/bash

aaron@aaron-desktop:~$ sudo pdbedit -L
[sudo] password for aaron: 
aaron:1000:Aaron Loewer

```

```

#file system

aaron@aaron-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc2 during installation
UUID=6a4d1c42-321e-478b-8e66-0b232579045c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdc1 during installation
UUID=A495-8C42  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sdc3 during installation
UUID=3d8b10fa-206b-49d9-bc23-7e6e8f679daa none            swap    sw              0       0
#automount Media Drive
/dev/sda1 /media/aaron/Media\040Drive ext4 defaults 0 0
#automount Backup Drive
/dev/sdb1 /media/aaron/Backup\040Drive ext4 defaults 0 0

aaron@aaron-desktop:~$ sudo blkid -c /dev/null -o list
device         fs_type label    mount point        UUID
----------------------------------------------------------------------------------------
/dev/sda1      ext4    Media Drive /media/aaron/Media Drive 2959cb20-8073-4496-8305-ed1bc8019a4f
/dev/sdb1      ext4    Backup Drive /media/aaron/Backup Drive 6c5fa86e-bf0e-4059-bacc-dc39e80d0420
/dev/sdc1      vfat             /boot/efi          A495-8C42
/dev/sdc2      ext4             /                  6a4d1c42-321e-478b-8e66-0b232579045c
/dev/sdc3      swap             [SWAP]             3d8b10fa-206b-49d9-bc23-7e6e8f679daa

```

```

#ownership and persmissions

aaron@aaron-desktop:~$ ls -l /media
total 8
drwxr-x---+ 4 root root 4096 Apr 18 21:16 aaron
drwxr-x---+ 2 root root 4096 Apr 18 19:25 root

aaron@aaron-desktop:~$ ls -l /media/aaron
total 8
drwxr-xr-x 10 aaron root  4096 Apr 18 19:26 Backup Drive
drwxrwxrwx 10 aaron aaron 4096 Apr 18 21:18 Media Drive


```

So I do notice a discrepancy in the permissions, I just don't know what to do to fix them. They just don't look like they match the way they should. Maybe it would be easier to just change the mount point of the Media Drive and Backup Drive and see if that works? (I know the Backup Drive has nothing to do with the samba share, but I'd like both those drives in the same location. But moving the mount point to /srv or /mnt, wouldn't that mess things up since they are owned by root? Like could I just mount them in /home/aaron?

---

### Post by bab1 on 2016-04-19
> **Infamshxr said:**
> ```

#file system

aaron@aaron-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
[COLOR="#FF0000"]# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).[/COLOR]
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc2 during installation
UUID=6a4d1c42-321e-478b-8e66-0b232579045c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdc1 during installation
UUID=A495-8C42  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sdc3 during installation
UUID=3d8b10fa-206b-49d9-bc23-7e6e8f679daa none            swap    sw              0       0
[COLOR="#0000FF"][B]#automount Media Drive
/dev/sda1 /media/aaron/Media\040Drive ext4 defaults 0 0
#automount Backup Drive
/dev/sdb1 /media/aaron/Backup\040Drive ext4 defaults 0 0[/B][/COLOR]

aaron@aaron-desktop:~$ sudo blkid -c /dev/null -o list
device         fs_type label    mount point        UUID
----------------------------------------------------------------------------------------
[COLOR="#0000FF"]/dev/sda1[/COLOR]      ext4    Media Drive /media/aaron/Media Drive [COLOR="#0000FF"]2959cb20-8073-4496-8305-ed1bc8019a4f[/COLOR]
[COLOR="#0000FF"]/dev/sdb1[/COLOR]      ext4    Backup Drive /media/aaron/Backup Drive [COLOR="#0000FF"]6c5fa86e-bf0e-4059-bacc-dc39e80d0420[/COLOR]
/dev/sdc1      vfat             /boot/efi          A495-8C42
/dev/sdc2      ext4             /                  6a4d1c42-321e-478b-8e66-0b232579045c
/dev/sdc3      swap             [SWAP]             3d8b10fa-206b-49d9-bc23-7e6e8f679daa

```

The above in red explains why you need to mount partitions using the UUID rather than the device (/dev).  The device ID can change but the UUID stays the same.  You should also take the time to make the mount point at least a "lowercase no-spaces" name at the location you decided on (see below) 
> 
```

#ownership and permissions
aaron@aaron-desktop:~$ ls -l /media
total 8
drwxr-x[COLOR="#008000"]---[/COLOR]+ 4 root root 4096 Apr 18 21:16 aaron
drwxr-x[COLOR="#008000"]**---**[/COLOR]+ 2 root root 4096 Apr 18 19:25 root

```

No user other than the owner is allowed past the /media directory (see green).  In one case it is *root* and in the other case it is *aaron*.  In both cases the user nobody has no rights to traverse (descend) into the subdirectories).  This is by design on media. :-(  Another reason to use a different location to mount these 1TB drives.
> 
So I do notice a discrepancy in the permissions, I just don't know what to do to fix them. They just don't look like they match the way they should.

Maybe it would be easier to just change the mount point of the Media Drive and Backup Drive and see if that works? (I know the Backup Drive has nothing to do with the samba share, but I'd like both those drives in the same location. But moving the mount point to /srv or /mnt, wouldn't that mess things up since they are owned by root? Like could I just mount them in /home/aaron?
You are correct in that the mount point should be different.  As root (via sudo) you can (an should) change the permissions of the mount point when the partition is mounted.  You do not want to mount these partitions inside of your home directory.

So the first thing is go create a mount point at /srv or if you wish /data. I'll just call it <basedir> and you can use either /srv or /data```
sudo mkdir -p /<basedir>/share/media
```...This will create the directorys **share/media** and you should be able to access these subdirectories.  We just need to give write permission to everyone.  We can do that with this command```
sudo chmod 777 /<basedir>/share/media
``` 

If you want you can make a mount point for the backup drive in the same way using */<basedir>/backup*

Once you have done that you just need to change the share definition path directive in the smb.conf file to match the new shared directory location (e.g /data/share/media or /srv/share/media).  Try to access the shares.

Post the same file system and ownership/permissions command output as originally requested so I can see your work.

---

### Post by Infamshxr on 2016-04-19
```

aaron@aaron-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc2 during installation
UUID=6a4d1c42-321e-478b-8e66-0b232579045c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdc1 during installation
UUID=A495-8C42  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sdc3 during installation
UUID=3d8b10fa-206b-49d9-bc23-7e6e8f679daa none            swap    sw              0       0
#automount Media Drive
UUID=2959cb20-8073-4496-8305-ed1bc8019a4f /srv/media ext4 defaults 0 0
#automount Backup Drive
UUID=6c5fa86e-bf0e-4059-bacc-dc39e80d0420 /srv/backup ext4 defaults 0 0

aaron@aaron-desktop:~$ sudo blkid -c /dev/null -o list
[sudo] password for aaron: 
device         fs_type label    mount point        UUID
----------------------------------------------------------------------------------------
/dev/sda1      ext4    Media Drive /srv/media      2959cb20-8073-4496-8305-ed1bc8019a4f
/dev/sdb1      ext4    Backup Drive /srv/backup    6c5fa86e-bf0e-4059-bacc-dc39e80d0420
/dev/sdc1      vfat             /boot/efi          A495-8C42
/dev/sdc2      ext4             /                  6a4d1c42-321e-478b-8e66-0b232579045c
/dev/sdc3      swap             [SWAP]             3d8b10fa-206b-49d9-bc23-7e6e8f679daa

```

```

aaron@aaron-desktop:~$ ls -l /srv
total 8
drwxr-xr-x 10 aaron root  4096 Apr 18 19:26 backup
drwxrwxrwx 10 aaron aaron 4096 Apr 18 21:18 media

aaron@aaron-desktop:~$ ls -l /srv/media
total 68
drwxrwxrwx  17 aaron aaron  4096 Apr 19 00:43 Comedy Specials
drwxrwxrwx   2 aaron aaron 16384 Apr 18 18:01 lost+found
drwxrwxrwx   5 aaron aaron 12288 Apr 19 00:43 Movies
drwxrwxrwx 589 aaron aaron 20480 Apr 19 00:43 Music
drwxrwxrwx  68 aaron aaron  4096 Apr 19 00:43 Pictures
drwxrwxrwx  13 aaron aaron  4096 Apr 19 00:43 Shared
drwxrwxrwx  22 aaron aaron  4096 Apr 19 00:43 TV Shows

```

Ok so, I got it all taken care of, still same problem. In the output of ls -l everything listed is highlighted in green except backup...

Ok, so just checked something... I opened dolphin and went to smb://aaron-desktop and it showed Documents and Media Drive folders, just like it does from Windows and on my phone. Tried opening Media Drive and popped up an error in Dolphin saying that the file or folder smb://aaron-desktop/Media Drive doesn't exist. Same thing with Documents. Seems weird that my Kubuntu box can't even find the location...

---

### Post by bab1 on 2016-04-19
> **Infamshxr said:**
> ```

aaron@aaron-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc2 during installation
UUID=6a4d1c42-321e-478b-8e66-0b232579045c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdc1 during installation
UUID=A495-8C42  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sdc3 during installation
UUID=3d8b10fa-206b-49d9-bc23-7e6e8f679daa none            swap    sw              0       0
#automount Media Drive
UUID=2959cb20-8073-4496-8305-ed1bc8019a4f /srv/media ext4 defaults 0 0
#automount Backup Drive
UUID=6c5fa86e-bf0e-4059-bacc-dc39e80d0420 /srv/backup ext4 defaults 0 0

aaron@aaron-desktop:~$ sudo blkid -c /dev/null -o list
[sudo] password for aaron: 
device         fs_type label    mount point        UUID
----------------------------------------------------------------------------------------
/dev/sda1      ext4    Media Drive /srv/media      2959cb20-8073-4496-8305-ed1bc8019a4f
/dev/sdb1      ext4    Backup Drive /srv/backup    6c5fa86e-bf0e-4059-bacc-dc39e80d0420
/dev/sdc1      vfat             /boot/efi          A495-8C42
/dev/sdc2      ext4             /                  6a4d1c42-321e-478b-8e66-0b232579045c
/dev/sdc3      swap             [SWAP]             3d8b10fa-206b-49d9-bc23-7e6e8f679daa

```

```

aaron@aaron-desktop:~$ ls -l /srv
total 8
drwxr-xr-x 10 aaron root  4096 Apr 18 19:26 backup
drwxrwxrwx 10 aaron aaron 4096 Apr 18 21:18 media

aaron@aaron-desktop:~$ ls -l /srv/media
total 68
drwxrwxrwx  17 aaron aaron  4096 Apr 19 00:43 Comedy Specials
drwxrwxrwx   2 aaron aaron 16384 Apr 18 18:01 lost+found
drwxrwxrwx   5 aaron aaron 12288 Apr 19 00:43 Movies
drwxrwxrwx 589 aaron aaron 20480 Apr 19 00:43 Music
drwxrwxrwx  68 aaron aaron  4096 Apr 19 00:43 Pictures
drwxrwxrwx  13 aaron aaron  4096 Apr 19 00:43 Shared
drwxrwxrwx  22 aaron aaron  4096 Apr 19 00:43 TV Shows

```

Ok so, I got it all taken care of, still same problem. In the output of ls -l everything listed is highlighted in green except backup...

Ok, so just checked something... I opened dolphin and went to smb://aaron-desktop and it showed Documents and Media Drive folders, just like it does from Windows and on my phone. Tried opening Media Drive and popped up an error in Dolphin saying that the file or folder smb://aaron-desktop/Media Drive doesn't exist. Same thing with Documents. Seems weird that my Kubuntu box can't even find the location...You did this backwards.  You need to use UUID instead of /dev/sd*

---

### Post by Infamshxr on 2016-04-19
Huh? Did what backwards? I did use the uuid instead of /dev/sd* for automounting the partitions in fstab...

---

### Post by bab1 on 2016-04-19
> **Infamshxr said:**
> Huh? Did what backwards? I did use the uuid instead of /dev/sd* for automounting the partitions in fstab...
My mistake, I took a quick look as I was leaving home.  I though the output of  the command for blkid was part of the fstab.  :-(

The fstab section looks correct.
> Ok so, I got it all taken care of, still same problem. In the output of ls -l everything listed is highlighted in green except backup...

Ok, so just checked something... I opened dolphin and went to smb://aaron-desktop and it showed Documents and Media Drive folders, just like it does from Windows and on my phone. Tried opening Media Drive and popped up an error in Dolphin saying that the file or folder smb://aaron-desktop/Media Drive doesn't exist. Same thing with Documents. Seems weird that my Kubuntu box can't even find the location...

Post the output of this command```
tail -n 20 /etc/samba/smb.conf
```

---

### Post by Infamshxr on 2016-04-19
Oh ok, lol. No problem. As for the output of the command, it's the same as the last lines of my cmb.conf file. Except I changed it to 45 so it shows the Media Drive, but everything is the same as it was... No changes from the last time I posted my smb.conf file. But question is why is it when I go to smb://aaron-desktop/Media Drive/ on the Kubuntu computer it says the location doesn't exist? But when I go to smb://aaron-desktop/ it shows the Media Drive folder, but when I go to open it, I get the same error, that it doesn't exist... Doesn't make any sense.

---

### Post by bab1 on 2016-04-19
> **Infamshxr said:**
> Oh ok, lol. No problem. As for the output of the command, it's the same as the last lines of my cmb.conf file. Except I changed it to 45 so it shows the Media Drive, but everything is the same as it was... No changes from the last time I posted my smb.conf file. But question is why is it when I go to smb://aaron-desktop/Media Drive/ on the Kubuntu computer it says the location doesn't exist? But when I go to smb://aaron-desktop/ it shows the Media Drive folder, but when I go to open it, I get the same error, that it doesn't exist... Doesn't make any sense.
I can't see the file output I asked for so I can say with any certainty what the problem is.  Do you want to post the output of this```
tail -n 20 /etc/samba/smb.conf
```

---

### Post by Infamshxr on 2016-04-19
Here ya go... As  Isaid, I changed the lines to 45 cuz 20 didn't show enough.

```

aaron@aaron-desktop:~$ tail -n 45 /etc/samba/smb.conf
;   create mask = 0600
;   directory mask = 0700

[Media Drive]
path = '/srv/media/'
guest ok = yes
browseable = yes
writeable = yes
create mask = 777
directory mask = 777
force user = nobody

[Documents]
path = '/media/aaron/Documents/'
guest ok = yes
browseable = yes
writeable = yes
create mask = 777
directory mask = 777
force user = nobody

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

### Post by bab1 on 2016-04-19
```
[Media Drive]
[COLOR="#FF0000"]path = '/srv/media/'[/COLOR]
guest ok = yes
browseable = yes
writeable = yes
create mask = 777
directory mask = 777
force user = nobody
```
Please try and mount the Lubuntu Samba share using Lubuntu itself.  Samba can be a client to its own server.  You should be able to browse the network and see both shares.  If not that, like you said,  you should be able to use ```
smb://aaron-desktop/"Media Drive"
```
[/CODE]
I'm not sure that this means anything but, I never use trailing / for share path definitions.  Try the part in red without the trailing /.  Also, there is no need to have the create mask at 777 it only needs 666 permissions to be read and writeable by all users.

Please post the exact errors you get, if any.

Have you restarted the Samba server each time you make a change to the smb.conf file?  You should use ```
sudo service smbd restart
```

---

### Post by Infamshxr on 2016-04-19
I'm not sure what you mean about the Lubuntu share. I'm running Kubuntu. Maybe it was a typo? But also, I'm not sure what you mean by mounting it. As for the smb://aaron-desktop/Media Drive, that's what I type into Dolphin as a folder path. That's where I get the error. Can I do it in the terminal to output an error? And yes, I have been restarting samba each time I make a change to fstab and/or smb.conf.

---

### Post by bab1 on 2016-04-19
> **Infamshxr said:**
> I'm not sure what you mean about the Lubuntu share. I'm running Kubuntu.  Maybe it was a typo? 
Yes that is a typo.> 
But also, I'm not sure what you mean by mounting it. As for the smb://aaron-desktop/Media Drive, that's what I type into Dolphin as a folder path. That's where I get the error. 

That is mounting it.  The thing you are calling a folder path is not a path it is a SMB resource (//NETBIOS_NAME/Share_Name)
> 
Can I do it in the terminal to output an error? And yes, I have been restarting samba each time I make a change to fstab and/or smb.conf.
There are a couple of things you can check.  Using testparm you check the smb.conf file.  Post the output of this command```
testparm -s
```

This command tries to browse the entire Samba/Windows network.  Post all of the output of this```

smbtree -d3
```

---

### Post by Infamshxr on 2016-04-19
Oh ok, well if I go to /srv/media from Dolphin, works fine. If I go to smb://aaron-desktop, works fine. Shows just like it does in windows. If I go to smb://aaron-desktop/Media Drive, that's where it throws me the error saying the location doesn't exist. It wouldn't have to do with the space in the name Media Drive, would it? Would changing it to just media-drive or just media help?

Here's the output you asked for...

This seems all ok, I guess.

```

aaron@aaron-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[Media Drive]"
Processing section "[Documents]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        server string = Samba Server %v
        server role = standalone server
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb

[Media Drive]
        path = '/srv/media'
        force user = nobody
        read only = No
        create mask = 0666
        directory mask = 0666
        guest ok = Yes

[Documents]
        path = '/media/aaron/Documents'
        force user = nobody
        read only = No
        create mask = 0666
        directory mask = 0666
        guest ok = Yes

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        print ok = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

```

This one is long and I've never seen it before, but I see some login failures... Not sure if that's particularly a good thing.

```

aaron@aaron-desktop:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface enp3s0 ip=192.168.1.210 bcast=192.168.1.255 netmask=255.255.255.0
Enter aaron's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.25 ( 192.168.1.25 )
Connecting to 192.168.1.25 at port 445
Doing spnego session setup (blob length=320)
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
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.25 ( 192.168.1.25 )
Connecting to 192.168.1.25 at port 445
Doing spnego session setup (blob length=320)
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
        \\KODIBUNTU                     KODI-PC server (Samba, KODI)
resolve_lmhosts: Attempting lmhosts lookup for name KODIBUNTU<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name KODIBUNTU<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name KODIBUNTU<0x20>
Connecting to 198.105.254.11 at port 445
Connecting to 198.105.254.11 at port 139
Connecting to 104.239.213.7 at port 445
Connecting to 104.239.213.7 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x56070cc58950] mpx_fde[(nil)] fd[12] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x56070cc59ad0] mpx_fde[(nil)] fd[13] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x56070cc5a650] mpx_fde[(nil)] fd[14] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x56070cc5b0e0] mpx_fde[(nil)] fd[15] - disabling
        \\DORENE-LAPTOP  
resolve_lmhosts: Attempting lmhosts lookup for name DORENE-LAPTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name DORENE-LAPTOP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name DORENE-LAPTOP<0x20>
Connecting to 192.168.1.25 at port 445
Doing spnego session setup (blob length=320)
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
        \\AARON-LAPPY    
resolve_lmhosts: Attempting lmhosts lookup for name AARON-LAPPY<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name AARON-LAPPY<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name AARON-LAPPY<0x20>
Connecting to 192.168.1.128 at port 445
Connecting to 192.168.1.128 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x56070cc5b1f0] mpx_fde[(nil)] fd[15] - disabling
Doing spnego session setup (blob length=320)
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
        \\AARON-DESKTOP                 Samba Server 4.1.17-Ubuntu
resolve_lmhosts: Attempting lmhosts lookup for name AARON-DESKTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name AARON-DESKTOP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name AARON-DESKTOP<0x20>
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
                \\AARON-DESKTOP\IPC$            IPC Service (Samba Server 4.1.17-Ubuntu)
                \\AARON-DESKTOP\print$          Printer Drivers
                \\AARON-DESKTOP\Documents      
                \\AARON-DESKTOP\Media Drive 

```

SIDE NOTE: If it helps any, I can access my Windows 10 laptop Network shares from the Kubuntu box. Just not vice versa.

---

### Post by bab1 on 2016-04-19
> **Infamshxr said:**
> Oh ok, well if I go to /srv/media from Dolphin, works fine. If I go to smb://aaron-desktop, works fine. Shows just like it does in windows. If I go to smb://aaron-desktop/Media Drive, that's where it throws me the error saying the location doesn't exist. It wouldn't have to do with the space in the name Media Drive, would it? Would changing it to just media-drive or just media help?

Either way as long as there are no spaces.  I prefer as few keystrokes as possible so I would use ***media***.  No upper case either (e.g. MEDIA)
> 

Here's the output you asked for...

This seems all ok, I guess.

```

aaron@aaron-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[Media Drive]"
Processing section "[Documents]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        server string = Samba Server %v
        server role = standalone server
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb

[Media Drive]
        path = '/srv/media'
        force user = nobody
        read only = No
        create mask = 0666
        directory mask = 0666
        guest ok = Yes

[Documents]
        path = '/media/aaron/Documents'
        force user = nobody
        read only = No
        create mask = 0666
        directory mask = 0666
        guest ok = Yes

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        print ok = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

```

This one is long and I've never seen it before, but I see some login failures... Not sure if that's particularly a good thing.

```

aaron@aaron-desktop:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface enp3s0 ip=192.168.1.210 bcast=192.168.1.255 netmask=255.255.255.0
Enter aaron's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.25 ( 192.168.1.25 )
Connecting to 192.168.1.25 at port 445
Doing spnego session setup (blob length=320)
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
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.25 ( 192.168.1.25 )
Connecting to 192.168.1.25 at port 445
Doing spnego session setup (blob length=320)
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
        \\KODIBUNTU                     KODI-PC server (Samba, KODI)
resolve_lmhosts: Attempting lmhosts lookup for name KODIBUNTU<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name KODIBUNTU<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
[COLOR="#FF0000"]resolve_hosts: Attempting host lookup for name KODIBUNTU<0x20>
Connecting to 198.105.254.11 at port 445
Connecting to 198.105.254.11 at port 139
Connecting to 104.239.213.7 at port 445
Connecting to 104.239.213.7 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x56070cc58950] mpx_fde[(nil)] fd[12] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x56070cc59ad0] mpx_fde[(nil)] fd[13] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x56070cc5a650] mpx_fde[(nil)] fd[14] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x56070cc5b0e0] mpx_fde[(nil)] fd[15] - disabling[/COLOR]
        \\DORENE-LAPTOP  
resolve_lmhosts: Attempting lmhosts lookup for name DORENE-LAPTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name DORENE-LAPTOP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name DORENE-LAPTOP<0x20>
Connecting to 192.168.1.25 at port 445
Doing spnego session setup (blob length=320)
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
        \\AARON-LAPPY    
resolve_lmhosts: Attempting lmhosts lookup for name AARON-LAPPY<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name AARON-LAPPY<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name AARON-LAPPY<0x20>
Connecting to 192.168.1.128 at port 445
Connecting to 192.168.1.128 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x56070cc5b1f0] mpx_fde[(nil)] fd[15] - disabling
Doing spnego session setup (blob length=320)
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
        \\AARON-DESKTOP                 Samba Server 4.1.17-Ubuntu
resolve_lmhosts: Attempting lmhosts lookup for name AARON-DESKTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name AARON-DESKTOP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name AARON-DESKTOP<0x20>
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
                \\AARON-DESKTOP\IPC$            IPC Service (Samba Server 4.1.17-Ubuntu)
                \\AARON-DESKTOP\print$          Printer Drivers
                \\AARON-DESKTOP\Documents      
                \\AARON-DESKTOP\Media Drive 

```
It is all good except for the part in red, but that is another issue not related to what we have been talking about. 

Remember to restart the Samba server when you change the share name.

Let me know if it works now.

---

### Post by Infamshxr on 2016-04-19
I'm not worried about the KODIBUNTU PC problem. It's because it's supposed to be on the network, but I have temporarily stolen the network cable to plug this computer in while using the internet lol. So that problem will go away once it's plugged back in, I'm sure. What about a space in the Drive Label on those drives? Since I changed the mounting point from /media/Media Drive to /srv/media, should the Drive Label be changed to Media as well? Or will that make any difference?

And ok, changed, checked, same problem... This is crazy. I don't remember this being this difficult last time I used Kubuntu on my desktop for file sharing lol.

---

### Post by bab1 on 2016-04-19
> **Infamshxr said:**
> ...What about a space in the Drive Label on those drives? Since I changed the mounting point from /media/Media Drive to /srv/media, should the Drive Label be changed to Media as well? Or will that make any difference?
> What are you calling a "Drive Label"?  I'm not a Windows person at all so Windows terms are lost on me.

And ok, changed, checked, same problem... 
Try and be more specific.  What error did you get for what command?  GUI browsing or command line.  I assume you know the difference between local access and remote (via Samba) access even if we are just using the 1 Kubuntu machine.

How can you go from > well if I go to /srv/media from Dolphin, works fine. If I go to smb://aaron-desktop, works fine. Shows just like it does in windows... which I guess mean thats "it works" to having the  "same problem"?  What changes from success to failure?  Or could it be that I misunderstand what you are saying?

---

### Post by Infamshxr on 2016-04-19
Sorry, maybe I'm not explaining it correctly. I'm in GUI here. I do most my work in GUI. I only use the terminal if I absolutely have to lol. If I open Dolphin and type in the location bar "/srv/media" (without the quotes of course) and it opens to that folder location just like it should. In the same situation, if I type in "smb://aaron-desktop", again it opens like it should (and just like it does in Windows). It shows two folders, Documents and media-drive. If I open up the media-drive folder or type in "smb://aaron-desktop/media-drive" into the location bar, I get the same result; a error pops up on the top of the Dolphin saying "The file or folder smb://aaron-desktop/media-drive does not exist." If you need a screenshot or something, just let me know.

[https://drive.google.com/file/d/0B1ulahJIlMPgU1h1R0ttOEJ6NGM/view?usp=sharing](https://drive.google.com/file/d/0B1ulahJIlMPgU1h1R0ttOEJ6NGM/view?usp=sharing)

---

### Post by bab1 on 2016-04-19
Let's stay where I can see the command and the results in text.  Post the output of this command```
smbclient -L aaron-desktop
```

---

### Post by Infamshxr on 2016-04-19
So, I noticed my Windows 10 laptop is not listed here, but another laptop on the network is... Is there a reason behind that?

```

aaron@aaron-desktop:~$ smbclient -L aaron-desktop
Enter aaron's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.17-Ubuntu]

        Sharename       Type      Comment
        ---------       ----      -------
        media-drive     Disk      
        Documents       Disk      
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (Samba Server 4.1.17-Ubuntu)
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.17-Ubuntu]

        Server               Comment
        ---------            -------
        AARON-DESKTOP        Samba Server 4.1.17-Ubuntu
        DORENE-LAPTOP        

        Workgroup            Master
        ---------            -------
        WORKGROUP            DORENE-LAPTOP

```

---

### Post by bab1 on 2016-04-19
> **Infamshxr said:**
> So, I noticed my Windows 10 laptop is not listed here, but another laptop on the network is... Is there a reason behind that?
What are listed is the SMB servers on the LAN.  In fact I want you to turn off the host DORENE-LAPTOP.  If this is a Windows machine, it may not be correctly configured.  Let's leave it off for the time being. [QUOTE]

With the host DORENE-LAPTOP off, I want you to add a comment parameter in the *aaron-desktop * host's ***/etc/samba/smb.conf*** listing of the **media-drive **share.  


You can see there isn't one in this listing ```
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.17-Ubuntu]

        Sharename       Type      Comment
        ---------       ----      -------
        media-drive     Disk      
        Documents       Disk      
        print$          Disk      Printer Drivers
```

The comment can be placed just under the share name.  Like this```

[My Share Name]
        comment = My Personal Share
```...Caps and spaces are okay here.


Then post back this command again```
smbclient -L aaron-desktop
```

---

### Post by Infamshxr on 2016-04-19
I will have to get back to this tomorrow. I need to some sleep then go to work tonight. I'll post back what happens tomorrow and let you know if that fixed it or not.

---

### Post by bab1 on 2016-04-19
> **Infamshxr said:**
> I will have to get back to this tomorrow. I need to some sleep then go to work tonight. I'll post back what happens tomorrow and let you know if that fixed it or not.
I may not be available tomorrow.  I'm on the road.  I will check when I have time and hopefully it's fixed.

---

### Post by Infamshxr on 2016-04-20
Well I managed to fix it without fixing it lol. I thought hey, this can't be normal, so I installed Debian Jessie alongside Kubuntu to see if I could get sharing working in there following the same directions you taught me. VIOLA! It works in Debian without a problem. So screw Kubuntu, I'll just stick with Debian KDE. Basically the same thing anyways. Now just need to reinstall all my programs and set everything up again like I had it in Kubuntu. Only downside of going with Debian is I lost KDE5 which looks soooo pretty. Back to KDE4 for now I guess. Maybe something I'll look into ;-) Thanks again for all your help though. Much appreciated and glad to learn some new things!

---

### Post by bab1 on 2016-04-20
> **Infamshxr said:**
> Well I managed to fix it without fixing it lol. I thought hey, this can't be normal, so I installed Debian Jessie alongside Kubuntu to see if I could get sharing working in there following the same directions you taught me. VIOLA! It works in Debian without a problem. So screw Kubuntu, I'll just stick with Debian KDE. Basically the same thing anyways. Now just need to reinstall all my programs and set everything up again like I had it in Kubuntu. Only downside of going with Debian is I lost KDE5 which looks soooo pretty. Back to KDE4 for now I guess. Maybe something I'll look into ;-) Thanks again for all your help though. Much appreciated and glad to learn some new things!
I'm glad you successfully resolved your problem.  Kubuntu is Ubuntu with the KDE Desktop.  Ubuntu itself is based on Debian.   I think the latest DE is the problem and it will be solved in the future  I usually wait for the LTS versions so these kinds of problems are resolved.  For all we know the problem is already fixed in Kubuntu 16.04 LTS.  I tend to wait a year before I upgrade my working machines.

---

### Post by Infamshxr on 2016-04-20
Thanks. Yea, the only thing I miss is kde5. Well the looks of it anyways lol. It's so pretty. So quick question, maybe you know the answer. Once 16.04 comes out, how long do you think it'll take before Debian sees kde5? They seem to be behind on stuff since their main goal is stability instead of cutting edge, which I can definitely appreciate, but a big part of me also likes to run the latest and greatest. Unfortunately it's not a perfect world and I can't have both lol.

---

### Post by bab1 on 2016-04-21
> **Infamshxr said:**
> Thanks. Yea, the only thing I miss is kde5. Well the looks of it anyways lol. It's so pretty. So quick question, maybe you know the answer. Once 16.04 comes out, how long do you think it'll take before Debian sees kde5? They seem to be behind on stuff since their main goal is stability instead of cutting edge, which I can definitely appreciate, but a big part of me also likes to run the latest and greatest. Unfortunately it's not a perfect world and I can't have both lol.
I have used both.  As you say, Debian is more conservative if you use the current release.  You can use Debian sid (testing) for the cutting edge).  The big difference is that Ubuntu (all flavors) allow the use of closed code binary blobs (e.g video drivers) and Debian will not.  I use Ubuntu because I like the audio codecs and the Unity Interface eye candy.

Ubuntu 16.04 (which means 2016.04 (April))) is to be released April 21, 2016 (Thursday).  Debian is not driven by Ubuntu.  In fact Ubuntu is a derivative of Debian and most developers Debian based rather than Ubuntu.  Ubuntu adds its extras to the Debian tools.  If you read the man pages and look and some of the source code you will see the Debian stamp all over the files.

---

### Post by Infamshxr on 2016-04-21
Codecs eh? Hopefully I don't run into any codec problems with Debian. I only really use mp3, flac, WMA, wmv, mpeg2, mkv, and avi. I don't foresee any problems though.

Yea, I know Ubuntu and a whole bunch of others are based off Debian. But I figure if kubuntu and many others switch over to kde5, Debian will eventually follow or at least allow people to upgrade kde.

---

### Post by Infamshxr on 2016-04-21
Oh crap. Sorry for the double post, but I made an oopsie that I can't fix. When installing Debian alongside kubuntu I didn't realize kubuntu was EFI and Debian was not. So I had sdc1 which was the EFI boot partition, sdc2 which was kubuntu, sdc3 which was BIOS grub, and sdc4 which was Debian. So I wanted my space back from kubuntu, so I deleted the partitions for it, finding out I had to delete the grub partition in order to merge them, so I redid the partitions and got that the way I want, but now I can't figure out how to install grub one the new sdc1... I tried mounting it then using grub-install /dev/sdc1 and grub-install /dev/sdc1. Both give me errors saying...
Grub-probe: error: failed to get canonical path of 'auths'
Could not find device for /boot: not found or not a block device.

I've googled and googled. Nothing works.

---

### Post by bab1 on 2016-04-21
You're not going to get much response as this thread is posted "solved".  Also, this problems is not related to the OP.  I suggest you open a new thread for this problem

---

### Post by Infamshxr on 2016-04-21
I was hoping you had the answer lol, but I can create a new thread

---

