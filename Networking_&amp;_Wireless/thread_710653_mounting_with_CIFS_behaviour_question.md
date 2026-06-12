---
title: "mounting with CIFS behaviour question"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by captkirk on 2008-02-28
I originally mounted a cifs drive with the /noperms option.
#//bigdrive/public /media/bigdrive cifs   noperm,guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

I used /noperms because I could not read and write to the drive any other way.

At some point, I realized I did not set an owner and thought that might be my problem.  I then used the /gid option to make my group the owner of the drive.  I removed /noperms and tried /gid but that did not work.  Nobody in the group could read and write to the drive.

I then added myself as the owner of the drive using the /uid option.  Now, both the /uid and the /gid option work as documented.  All of the users can read and write to the drive.

I think I am missing something about setting up cifs drives that I have not seen.  Can someone point me to something to help me out, or explain what I am overlooking?  I doubt this is a bug, but I am confused!

Thanks!

---

### Post by Eiríkr on 2008-02-28
When you say "cifs drive", do you mean a share on a Samba server you have access to?  If so, it'd be very helpful if you could post two things: the [font=courier]/etc/samba/smb.conf[/font] file for the //bigdrive server, and the actual filesystem permissions for the //bigdrive/public directory (UID, GID, and r/w/x perms -- type [font=courier]ls -ld /path/to/public[/font] in a terminal while logged into the bigdrive server).  

Cheers,

Eiríkr

---

### Post by captkirk on 2008-02-28
Ok, I realize by your question that I was not very clear and I am sorry.

I am using a western digital mybookworld. I think it set up to support windows file sharing.

I can run an ls - ld, but I can't log into it via rlogin or telnet to see the native file structure, if I understand your question correctly.

ls -ld output
drwxrwxr-x 25 n users 0 2008-02-23 23:11

My smb.conf is below.  I don't seem to know how to put it in a box, but I took a shot at it.

Thanks for your assistance.

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
   workgroup = MAXWHEAT

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

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

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
   path = /var/spool/samba
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


[cdrom0]
path = /media/cdrom0
available = yes
browsable = yes
public = yes
writable = no
```

---

### Post by Eiríkr on 2008-02-28
Okay, this looks like the default sample smb.conf that comes with Ubuntu, and is probably from the machine you're trying to connect *from*, when what we need is the smb.conf of the machine you're trying to connect *to*, which is your mybookworld machine. 

**That said,** the output of [font=courier]ls -ld[/font] looks useful here.  It tells us that the directory you ran it on has the owner username **n** and the owner groupname **users**, with read/write/execute permissions granted to group members (the second set of "rwx" at the beginning of the line).  As such, any username that is also a member of the "users" group should have full access to that directory.  If your own username is not part of this group, run the following to add it:
```
sudo usermod -aG users USERNAME
```

Then try to write to the shared drive and let us know if it works.  

Cheers,

Eiríkr

---

### Post by captkirk on 2008-02-29
Ok, that works for me.  I can add users pretty easily now!

I would love to post the smb.conf but I am using a Western Digital Worldbook and the best I can tell is that it only supports MS windows file sharing, so that explains some of its odd behavior.  I am unable to log into it, at least without a hack.

When mounting  from the other machine, and using cifs, does the mount command require both a uid and a gid?  I tried just a gid and could not read and write to the drive. I have to either use noperms or both a gid and uid.

Thanks!

---

### Post by Eiríkr on 2008-02-29
Let me make sure I understand -- once you added yourself to the [font=courier]users[/font] group, could you access the share as a read/write/execute, *without* specifying UID and GID in the [font=courier]mount[/font] options?

If so, then you should be able to just add yourself to the [font=courier]users[/font] group on the other machine as well.  

If no, that's pretty wacky, and nothing I've run across -- but then again my experience is far from broad.  The need to specify UIDs and GIDs right in the [font=courier]mount[/font] command is possibly a quirk of your Worldbook's configuration.  Normal Samba setups don't usually rely on those to define permissions.  

Cheers,

Eiríkr

---

### Post by captkirk on 2008-02-29
> Let me make sure I understand -- once you added yourself to the users group, could you access the share as a read/write/execute, *without* specifying UID and GID in the mount options?


Exactly.  I had to use the noperms option to on the mount, but that let me (and every other user) read and write to the drive.

> If no, that's pretty wacky, and nothing I've run across -- but then again my experience is far from broad. The need to specify UIDs and GIDs right in the mount command is possibly a quirk of your Worldbook's configuration. Normal Samba setups don't usually rely on those to define permissions.

Thanks, I sort of guessed at that, but I was not certain.  I suspect the permissions are weaker because the worldbook is a windows share, but I might be wrong.  The worldbook won't let me log into it and take a look, so I have no way of knowing for certain and I can't find the answer directly anywhere else.

Thanks for filling in my lack of knowledge, I greatly appreciate it!

---

### Post by Eiríkr on 2008-02-29
So even as group "users", you still had to specify "noperms" in [font=courier]mount[/font] options or it wouldn't mount?  Huh.  Some setup they've got there.  I wonder if you call their tech dept if they'd part with any clues.  

Cheers,

Eiríkr

---

### Post by captkirk on 2008-03-09
Ok, the weirdness continues.

The owner can read and write to the drive, but the users can only read the drive.

For the moment, I gave up and went back to /noperms.

I am ready to blame the properties of the world book and move on.  The /noperms at least lets us use the drive.

Unless someone has a quick fix or something I overlooked, I will consider this a problem with the drive.

Thanks for the help! :)

---

### Post by Eiríkr on 2008-03-09
Hey there again --

I assume you mean, without /noperms, only the owner gets r/w access.  In this case, is the owner the same "n" username seen before?  When you run [font=courier]ls -ld /SHARE[/font], do you get the same output seen earlier:
```
ls -ld
drwxrwxr-x 25 n users 0 2008-02-23 23:11 /SHARE
```

The output above clearly shows that owner "n" has r/w/x, members of group "users" have r/w/x, and anyone else only has r/x (no writing).  Note that *everyone* who needs write access needs to be members of the "users" group.  You can double-check by using the [font=courier]id[/font] command.  Output looks like this:
```
admin@ubuntu:~$ id USERNAME
uid=1000(USERNAME) gid=1000(USERNAME) groups=1000(USERNAME),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),100(users),104(scanner),108(lpadmin),109(admin),115(netdev),118(powerdev)
admin@ubuntu:~$
```

If the users in question are *not* part of the "users" group, you can add them by running the same [font=courier]usermod[/font] command from before:
```
sudo usermod -aG users USERNAME
```

If the users having trouble writing are in fact part of the "users" group, and if the shared directory is actually owned by group "users" as seen earlier, then [font=courier]ls -ld[/font] output for *only* the owner username having r/w permission would look like this:
```
ls -ld
drwxr-xr-x 25 n users 0 2008-02-23 23:11 /SHARE
```

Note that the second perms triplet here does *not* have the "w", and instead only shows a "-" in its place.

It is possible for directories created *within* the share to have no write permission for group members, depnding on something called your [font=courier]umask[/font], which defines your username's default creation permissions.  If [font=courier]ls -ld[/font] on the share directory itself shows group write, but sub-directories do not, that's fixable by changing the mode -- using the [font=courier]chmod[/font] command.  Let me know if that's your trouble and we'll go from there.  

Cheers,

Eiríkr

---

