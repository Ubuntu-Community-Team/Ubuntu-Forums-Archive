---
title: "Mount cifs problems with users and permissions"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by Meson on 2008-03-02
I'm having some problems mounting windows shares using cifs.

First of all, is it recommended to user mount -t cifs our just mount.cifs?

I would like my mount command to look something like this:
```
sudo mount -t cifs -ouid=LocalUser,user=RemoteUser //remote/host /mnt/mountpoint
#or
sudo mount.cifs //remote/host /mnt/mountpoint -ouid=LocalUser,user=RemoteUser
```

One problem is the the permissions become 777 for every file of the mount.  I would like them to be 600 with the owner being LocalUser.

Another major issue I have is this:  If the RemoteUser is an invalid user, ie one that doesn't exist on the windows machine, then it will still ask me for my password and accept any password I give it.  typing the mount command indicates that the remote location is indeed mounted to the mountpoint.  However if I try to cd into the mountpoint it says "not a directory"

So it's a good thing that nothing actually mounts with an invalid user, however shouldn't the entire mount fail?  What's going on here?

---

### Post by Eiríkr on 2008-03-02
These sound very much like problems with the smb.conf file on the serving machine.  File perms can be granted by the SMB server program (depending on the perms of the underlying filesystem), so the 777 -> 600 change should be easy enough.  Accepting bad passwords suggests that your SMB server is configured to map such logins to the guest account, which might then not have the right permissions (on the server's filesystem itself) to access the mounted share.  

If you could post your /etc/samba/smb.conf file, we can get into the nitty gritty and most likely fix your issues.  :)

Cheers,

Eiríkr

---

### Post by Meson on 2008-03-02
Ok, I see the line that is setting invalid users to root, is there a way to change it to fail on invalid users?

I don't really see anything about setting the permissions.  However I'd really like to be able to do this from the command line, is that not possible?  I know the umask argument does not apply to cifs.

Here's my config, it's all defaults:

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
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

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
;
; The following was the default behaviour in sarge
; but samba upstream reverted the default because it might induce
; performance issues in large organizations
; See #368251 for some of the consequences of *not* having
; this setting and smb.conf(5) for all details
;
;   winbind enum groups = yes
;   winbind enum users = yes

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
# This might need tweaking when using external authentication schemes
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

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
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom
```

---

### Post by chaumurky on 2008-03-02
No, it's saying 'root' is not a valid user. It will fail if an attempt is made as user 'root'.

---

### Post by Eiríkr on 2008-03-02
What you've sent is almost definitely the smb.conf file from your client machine (the one you're typing [font=courier]mount -t cifs...[/font] into), and *not* from your SMB server.  The clue is that all this conf file is sharing is your printer.  Moreover, there's no way this conf file would produce the behaviour you're describing, unless your smbd executable is a complete custom compilation after extensive rewriting of the source code.  :shock:

If you've got access to it (i.e. can log in and open a terminal [or ssh in], and cd over to /etc/samba), log into your SMB server and send us the smb.conf file from *that* machine.  :)

Cheers,

Eiríkr

[size=3]**Doh!**[/size]

I've been an ijimit.  Had I properly read your initial post, I would have noted the following:
> Another major issue I have is this: If the RemoteUser is an invalid user, ie one that doesn't exist on the **windows machine**, then it will still ask me for my password and accept any password I give it.
So ixnay on any smb.conf files; those are only relevant for the serving machine, never for the client machine.  Looking again at your initial post:

> One problem is the the permissions become 777 for every file of the mount. I would like them to be 600 with the owner being LocalUser.
I'm not sure this is possible, since the perms are defined by however the Windows machine decides to serve them up.  I suspect you might be able to change this by changing the permissions on the relevant folders and files from within the Windows machine itself.  

> Another major issue I have is this: If the RemoteUser is an invalid user, ie one that doesn't exist on the windows machine, then it will still ask me for my password and accept any password I give it. typing the mount command indicates that the remote location is indeed mounted to the mountpoint. However if I try to cd into the mountpoint it says "not a directory"
I think this is another quirk of how Windows talks -- rather than failing on a bad username, it instead *pretends* to let you in but then won't let you see anything.  There might be some setting on the Windows side similar to the [font=courier]guest ok = no[/font] option for Samba, but I'm not familiar enough with Windows to say.  

Any Windows experts reading this thread?

Cheers,

Eiríkr

---

### Post by Meson on 2008-03-02
The server is a Windows XP box.  There is no samba config.

---

### Post by Eiríkr on 2008-03-02
Yep, sorry 'bout that, I must have been in the midst of editing my duh-duh post when you replied.  :shock:

---

### Post by Eiríkr on 2008-03-03
The more I dig into this, the odder some of it looks.  Let's look again:

> **Meson said:**
> I'm having some problems mounting windows shares using cifs.

First of all, is it recommended to user mount -t cifs our just mount.cifs?

They're synonyms.  From the mount.cifs man page:

> mount.cifs  mounts  a  Linux  CIFS  filesystem.  It  is  usually invoked indirectly by the **mount**(8) command when using the "-t cifs" option.

> **Meson said:**
> I would like my mount command to look something like this:
```
sudo mount -t cifs -ouid=LocalUser,user=RemoteUser //remote/host /mnt/mountpoint
#or
sudo mount.cifs //remote/host /mnt/mountpoint -ouid=LocalUser,user=RemoteUser
```

One problem is the the permissions become 777 for every file of the mount.  I would like them to be 600 with the owner being LocalUser.

Perms get complicated, because they work quite differently under Windows than they do on a Linux system.  Run [font=courier]ls -l[/font] on the mounted share, and you should see perms a bit uglier even than 777:
```
drwxrwxrwx 1 username root          0 2008-03-03 08:14 dell/
-r-xr-Sr-t 1 eirikr root       5901 2006-04-28 10:48 dell.sdr*
drwxrwxrwx 1 username root          0 2007-12-21 23:00 Documents and Settings/
drwxrwxrwx 1 username root          0 2007-06-03 11:15 Downloads/
drwxrwxrwx 1 username root          0 2006-04-28 10:44 drivers/
-rwxrwSrwt 1 username root   32948931 2007-07-13 11:10 FEYU.m4a*
```

Executables are set to run with the permissions of the owning group, an interesting wrinkle.  (Never mind that an m4a file is audio...)  

However, running [font=courier]ls -ld[/font] right in the mounted directory itself shows that, while the "other" perms are rwx, the *parent* directory perms are defined according to whatever you've set up.  So say you mount the share to [font=courier]/mnt/share[/font].  The only users that can get into this directory are those that have "x" permission on the [font=courier]/mnt[/font] directory.  

> **Meson said:**
> Another major issue I have is this:  If the RemoteUser is an invalid user, ie one that doesn't exist on the windows machine, then it will still ask me for my password and accept any password I give it.  typing the mount command indicates that the remote location is indeed mounted to the mountpoint.  However if I try to cd into the mountpoint it says "not a directory"

So it's a good thing that nothing actually mounts with an invalid user, however shouldn't the entire mount fail?  What's going on here?

This is the really odd part.  I tried to duplicate this on my end, and the only way I could get it to work was when the permissions on the Windows side were set to allow "Everyone" access to the shared folder (I haven't tested it, but I suspect allowing access to "Guest" or "Guests" on the Windows side instead of "Everyone" might also work)
 -- this way it doesn't matter *what* your username or password is in the mount command -- ***and*** I mounted something that wasn't a directory.  Then, naturally, trying to cd into it won't work.  Take this example:
```
sudo mount -t cifs -o uid=1000,user=rutabagasareverynice, //WINBOX/share/readme.txt ~/share
```
In this case, the Windows-side perms on the "share" folder allow read access to "Everyone", so it doesn't matter that user "rutabagasareverynice" doesn't exist.  I still see a password prompt, but it's being ignored on the Windows fileserver side.  The file "readme.txt" is clearly a file, *not* a directory, so while it gets mounted just fine, any attempt at cd-ing into it results in the "Not a directory" error. But running [font=courier]ls -lF ~/share[/font] (adding the "-l" long-format option and the "-F" classify option) clearly shows that ~/share is a regular file that is also executable (how Windows classifies all .txt files) rather than a directory.  
```
username@ubuntu:~$ ls -lF ~/shared
-rwxrwxrwx 1 username root 27851 1998-03-15 15:00 /home/username/shared*
```

HTH,

Eiríkr

PS -- Apparently the "executable" bit is how Samba translates what is the "Archive-ready" option in Windows-World.  Weird.

---

### Post by Eiríkr on 2008-03-04
Okay, after reading through the man page (a good idea in any case), it looks like the [font=courier]file_mode[/font] and [font=courier]dir_mode[/font] options are the ones you want.  So your mount command would look something like this:
```
sudo mount -t cifs -o uid=LOCALUID,gid=LOCALGID,user=REMOTEUSER,file_mode=0600,dir_mode=0700 //remote/host /mnt/mountpoint
```

HTH,

Eiríkr

---

### Post by Meson on 2008-03-04
Yeah, I saw those in the man page too.  Something about the language made me think they were for something else.  I'm not home right now but I'll try when I get there.

fyi, the windows share has full permissions for only one user and nothing for anyone else, including everyone.  I've always wondered what the difference between not having Allow and explicitly checking Deny is though...

---

### Post by Eiríkr on 2008-03-04
I've found the whole Allow / Deny thing a bit confusing as well, but when clicking Deny for Everyone, it pops up with a message that such group-wide denial trumps individual user-assigned perms, so I think it might be set up that way to allow a differently organized approach to how groups work...?

Cheers,

Eiríkr

---

### Post by Meson on 2008-03-04
Ah yeah, I guess if deny is set it will go through and make changes lower in the tree but if it isn't it won't make changes.

Everything is working great, thanks Eirikr.

Now I just need to figure out why adding the s bit to mount.cifs isn't working to let me mount a share from fstab under a normal user account.

---

### Post by Eiríkr on 2008-03-04
Frankly I think the folks working on the mount.cifs package (as opposed to mount.smbfs) screwed the pooch with that one -- the "user" option is described right there in the [font=courier]mount[/font] manpage as the mechanism to allow a user to mount and then unmount, but then they go and redefine it *just for mount.cifs* to be an unneeded synonym for "username".  Just dumb, really.  I've tried using [font=courier]mount -t cifs[/font] with triple --verbose options to get the most detail, and sure enough, mount.cifs parses "user" as an empty "username" and ignores it, instead of accurately reading it as "allow a user to mount / umount".  Given that the fstab options are explained in the man page as the mount options, I figure this must be what's happening there too.  

As for the "users" option instead, I'm really not sure what happens, but with this test setup in my /etc/fstab file:
```
//boreas/bookshelf      /mnt/bookshelf  cifs    users,ro,sec=none
```
... mounting worked fine, but attempting to unmount gave me a nonsense "this resource is busy" error and seriously borked the kernel's understanding of this part of the filesystem -- "ls -l" on the parent of the mounted directory showed question marks instead of the usual filetype indicators, and "ls -l" of the mounted directory itself raised errors that it wasn't a directory.  

I don't know about you, but I don't like it when my filesystem gets so messed up the only solution is to reboot.  Color me unhappy -- whatever its faults, I never had this with the old mount.smbfs executable.  (*And* null passwords used to work properly -- c.f. the posts from [post=4438064]this one[/post] on down.)

Anyway, good luck with the "users" option, but be forewarned that (at least in my experience) you might wind up needing to reboot to get shares mounted this way to unmount.

Cheers,

Eiríkr

---

### Post by Meson on 2008-03-04
I agree, I don't like the relationship between mount.cifs and mount.  The reason I'm using it is because samba seems to limit transfers to about 4 MB/s on my 1Gigabit network.

To avoid the user(s) confusion, and for convenience, I'm just using a credentials file.

---

### Post by Eiríkr on 2008-03-05
> **Meson said:**
> I agree, I don't like the relationship between mount.cifs and mount.  The reason I'm using **it** is because samba seems to limit transfers to about 4 MB/s on my 1Gigabit network.

To avoid the user(s) confusion, and for convenience, I'm just using a credentials file.

By "it" do you mean using [font=courier]mount.cifs[/font] vs. using [font=courier]mount -t cifs[/font]?  If the man pages are right, I think the latter just indirectly calls the former, so they're essentially synonyms.  (Except the [font=courier]mount[/font] call itself has much more informative --verbose messages.)  

Regarding transfer speeds, I recall reading some rather obscure stuff about tweaking the SO_RCVBUF and SO_SNDBUF options, among others.  Have a look at the [socket options section of the smb.conf online man page]("http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SOCKETOPTIONS") for more info.  

Cheers,

Eiríkr

---

### Post by Meson on 2008-03-05
Sorry for the ambiguity.  I meant the reason I'm using cifs and not smb.  Besides, as I understand it, cifs is supposed to be a replacement for samba in general.

---

### Post by Eiríkr on 2008-03-05
Ah yes, and in fact it looks like the older mount.smbfs executable no longer works properly -- at least, it only ever produced unusable results when I tried yesterday, no matter what the options were.  (Despite that, I never needed to reboot, as a simple umount did the trick.)  I suspect that since it's no longer being maintained, it's simply fallen behind the times in terms of what's going on in kernel development.  Oh, well.  

Cheers,

Eirík

---

