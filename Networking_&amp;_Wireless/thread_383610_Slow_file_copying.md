---
title: "Slow file copying"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by fahadmp on 2007-03-13
Hi!

I finally got samba to see my windows folders and vice versa but when I copy some files over it takes forever! I know something is missing! I use the Places>Network Servers to copy files from Windows to a local ubuntu folder

Why is it so slow? 

Here is my smb.conf:

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
   netbios name = olympus	
   socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
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

# Put a capping on the size of the log files (in Kb).
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
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
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
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

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

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
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

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = yes

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = yes

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
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

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

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
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

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


[fahadmp]
path = /home/fahadmp
available = yes
browsable = yes
public = yes
writable = yes

```

Please Help!

Thanks,
fajad

---

### Post by Mr. C. on 2007-03-13
See the recent thread about benchmarking and samba that I participated in.

MrC

---

### Post by dannyboy79 on 2007-03-13
well you are going to get faster tranfers by mounting a drive using cifs ([http://ubuntuforums.org/showthread.php?t=288534)](http://ubuntuforums.org/showthread.php?t=288534)). also, this topic is being discussed here ([http://www.ubuntuforums.org/showthread.php?t=379913](http://www.ubuntuforums.org/showthread.php?t=379913)) and it can relate to many things. I also see that you have the socket options = TCP_NODELAY
listed twice, once in the begining and once like above. use the 1 that contains all of it in 1 line and just comment out this one or remove the 1 from the top and make this one complete, this may or may not help.

---

### Post by dannyboy79 on 2007-03-13
> **Mr. C. said:**
> See the recent thread about benchmarking and samba that I participated in.

MrC

MrC, wouldn't you think it would be a little more helpful to have provided a link? If I view every thread you've been involed in, I am sure I'll see tons of them. Just a thought for next time you try to help someone.

---

### Post by Mr. C. on 2007-03-13
The post is trivial to find for anyone who uses Search.  Please don't bother pursuing your desire to provoke a fight.  It does not serve you well.

MrC

---

### Post by dannyboy79 on 2007-03-13
> **Mr. C. said:**
> The post is trivial to find for anyone who uses Search.  Please don't bother pursuing your desire to provoke a fight.  It does not serve you well.

MrC
you need to understand that everyone isn't aware of the search function and even if they were, using MrC as the username to search for and samba as a keyword still resulted in over 9 pages of results. According to the Ubuntu Forum  Code of Conduct number 10 specifically states:
Please strive to communicate with other users as effectively as possible: 
what you did was far from that. Then you couldn't just be a professional about this and say, "you're right, next time when I suggest something I'll provide a link because I expect some people don't know that there is a search function within this forum" instead you had to make some irrelevant comment. I wasn't trying to provoke a fight at all, I was merely trying to be helpful for users in the future that you help as providing such vague info to them isn't helping them at all.

---

### Post by fahadmp on 2007-03-13
Thanks guys!

I'm trying to follow the cifs guide but I get stuck when perfroming the

sudo mount -t cifs //netbiosname/sharename /media/sharename -o username=winusername,password=winpassword,iocharset=utf8,file_mode=0777,dir_mode=0777

when i execute the above line all I get is usage instructions...lol

also my win computer doesn't have a password so do I just omit that line?

---

### Post by fahadmp on 2007-03-13
my smbtree

```

MSHOME
        \\OLYMPUS                       achilles server (Samba, Ubuntu)
                \\OLYMPUS\print$                Printer Drivers
                \\OLYMPUS\fahadmp        
                \\OLYMPUS\IPC$                  IPC Service (achilles server (Samba, Ubuntu))
                \\OLYMPUS\ADMIN$                IPC Service (achilles server (Samba, Ubuntu))
        \\FAHADMP-LAPTOP                Fahad's Laptop
                \\FAHADMP-LAPTOP\Printer                HP PSC 950
                \\FAHADMP-LAPTOP\C$                     Default share
                \\FAHADMP-LAPTOP\ADMIN$                 Remote Admin
                \\FAHADMP-LAPTOP\My Music       
                \\FAHADMP-LAPTOP\SharedDocs     
                \\FAHADMP-LAPTOP\print$                 Printer Drivers
                \\FAHADMP-LAPTOP\IPC$                   Remote IPC

```

sudo mount -t cifs //FAHADMP-LAPTOP/My Music /media/music -o username=fahadmp,iocharse t=utf8,file_mode=0777,dir_mode=0777

Thanks alot guys for your help!

---

### Post by dannyboy79 on 2007-03-13
> **fahadmp said:**
> Thanks guys!

I'm trying to follow the cifs guide but I get stuck when perfroming the

sudo mount -t cifs //netbiosname/sharename /media/sharename -o username=winusername,password=winpassword,iocharset=utf8,file_mode=0777,dir_mode=0777

when i execute the above line all I get is usage instructions...lol

also my win computer doesn't have a password so do I just omit that line?

it states it right there if the winpassword doesn't exist.

sudo mount -t cifs //netbiosname/sharename /media/sharename -o guest,iocharset=utf8,file_mode=0777,dir_mode=0777

also, make sure you don't have any extra spaces etc etc. did you install smbfs and follow the guide word for word?

---

### Post by fahadmp on 2007-03-13
> **dannyboy79 said:**
> it states it right there if the winpassword doesn't exist.

sudo mount -t cifs //netbiosname/sharename /media/sharename -o guest,iocharset=utf8,file_mode=0777,dir_mode=0777

also, make sure you don't have any extra spaces etc etc. did you install smbfs and follow the guide word for word?

Now I get this:

"mount error: can not change directory into mount target /media/music"

after I created the etc/fstab file

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2a7fe277-53f8-49b5-ac05-99db14b9e9de /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c9189774-b83e-438d-bd0c-ab57bde87491 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
//192.168.1.100/My_Music /media/music       cifs    guest,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0


```

---

### Post by dannyboy79 on 2007-03-13
do you own the music folder you created in linux? 
ls -la /media/
 not sure if that matters? 
sudo chown username:username /media/music 
will make it owned by your user and your group. 
also, what happens when you do
smbclient -L FAHADMP-LAPTOP
then when it asks for a password, hi enter (don't put in password) what happens? and then
smbclient -L FAHADMP-LAPTOP -U guest
does this result in anonymious login successful but then say Error returning browse list: NT_STATUS_ACCESS_DENIED? what are your permissions for this windows share? i am not sure how the guest thing works? I use usernames and passwords on all my machines?

---

### Post by fahadmp on 2007-03-13
This is what happens after smbclient -L FAHADMP-LAPTOP

```

Domain=[FAHADMP-LAPTOP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        SharedDocs      Disk      
        My Music        Disk      
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        Printer         Printer   HP PSC 950
Domain=[FAHADMP-LAPTOP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

```

this is what happens after smbclient -L FAHADMP-LAPTOP -U guest

```

Domain=[FAHADMP-LAPTOP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        SharedDocs      Disk      
        My Music        Disk      
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        Printer         Printer   HP PSC 950
Domain=[FAHADMP-LAPTOP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

```

There wasn't an error or anything

this is my etc/ftab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2a7fe277-53f8-49b5-ac05-99db14b9e9de /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c9189774-b83e-438d-bd0c-ab57bde87491 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
//192.168.0.100/My_Music /media/music       cifs    guest,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```

---

### Post by Mr. C. on 2007-03-13
You will never be able to mount the share "**My Music**" with the mount command specifying "**My_Music**".

You need **My\040Music** in your fstab.

MrC

---

### Post by dannyboy79 on 2007-03-13
thanks for catching this, I thought he had renamed his share name when I saw the underscore in his fstab. couldn't he also use "My Music"? i thought quotes around a name with a space works also?

---

### Post by Mr. C. on 2007-03-14
Nope, unfortunately quotes won't work.  From **man fstab**:

```
The second field, (fs_file), describes the mount point for the filesys-
tem.  For swap partitions, this field should be specified as `none'. If
the  name  of  the  mount point contains spaces these can be escaped as
`\040'.
```

But this isn't made terrible obvious, as it is the first field that was problematic here.  Both fields require \40 escaping for spaces.

MrC

---

### Post by dannyboy79 on 2007-03-14
ok, glad to know that. well it doesn't specifically say it doesn't work, I'd be interested to give it a try and post back because i do however know that when using the terminal, the quotes do work for various commands when names with spaces in them are used in the command. or is it maybe single quotes ('). anyway, thanks for the info.

---

### Post by fahadmp on 2007-03-14
Well guys it finally worked!! Thanks alot for your help!

---

### Post by dannyboy79 on 2007-03-14
> **fahadmp said:**
> Well guys it finally worked!! Thanks alot for your help!
Can you PLEASE specifically write down how you got this resolved. Think about this when it may have happened to you, you thought to yourself, "why do people do this, what the heck is the solution???" Another user feels the same way as you may have, they read thru 2 pages of posts and then get to the end and simply read, "I got it figured out." without any explaination as to what the solution was. If it hasn't happened to you yet be thankful but it has happned to me and this is why I suggest to everyone to always write down the solution.Thanks and I am glad you got it.

---

### Post by Mr. C. on 2007-03-14
> **dannyboy79 said:**
> o...well it doesn't specifically say it doesn't work

The number of things that don't work would be infinite.  Documentation generally tries to only state how things work, and what is possible.

>  do however know that when using the terminal, the quotes do work for various commands when names with spaces in them are used in the command. or is it maybe single quotes (').

It is the SHELL that handles quotes, unless they are escaped.  In general, most commands know nothing about quotes.  Its all about argument passing, words, and metacharacters.  See:

See week 4 notes: "Quoting in Detail" : [http://cis68b1.mikecappella.com/calendar.php](http://cis68b1.mikecappella.com/calendar.php)
and week 10 notes: "Advanced Shell Usage":  [http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/)

MrC

---

### Post by fahadmp on 2007-03-14
> **dannyboy79 said:**
> Can you PLEASE specifically write down how you got this resolved. Think about this when it may have happened to you, you thought to yourself, "why do people do this, what the heck is the solution???" Another user feels the same way as you may have, they read thru 2 pages of posts and then get to the end and simply read, "I got it figured out." without any explaination as to what the solution was. If it hasn't happened to you yet be thankful but it has happned to me and this is why I suggest to everyone to always write down the solution.Thanks and I am glad you got it.

haha...yeah of course!

It was the \040 I used instead of the space...that seemed to do it

---

