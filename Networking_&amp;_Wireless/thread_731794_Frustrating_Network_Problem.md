---
title: "Frustrating Network Problem"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by kecterman on 2008-03-22
I have no background at all with home networking.  I have 6.06 on my storage PC where I have all my movies.

I want to be able to watch movies from my laptops (Ubuntu 7.10 on one and XP Pro on the other).

I have configured samba and I can get into my shared movie folder on the storage PC with no problem at all from the XP laptop.  I can see the computer and folder and can play files.
 
From the Ubuntu 7.10 laptop, I can see the shared folder, but w I get when I click on it the following error message :

"The folder contents could not be displayed.  'Movies' couldn't be yfound.  Perhaps it has recently been deleted"


Well that is BS, because it's there.

Please help?

Here is my smb.conf data:

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
   workgroup = BODHIEM

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

# security = share is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
;   security = share

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
browseable = yes

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


[ShareTest]
path = /home/lecterman/ShareTest
available = yes
browseable = yes
public = yes
writable = no

[Movies]
path = /media/usbdisk/Movies
available = yes
browseable = yes
public = yes
writable = yes

---

### Post by Eiríkr on 2008-03-22
Hello kecterman --

Just to be sure before getting too far into this, the smb.conf file here is the one from your 6.06 Samba server, correct?  The conf file from your 7.10 laptop client machine won't help.  (I only ask because some folks get confused. :))

Cheers,

Eiríkr

---

### Post by kecterman on 2008-03-22
> **Eiríkr said:**
> Hello kecterman --

Just to be sure before getting too far into this, the smb.conf file here is the one from your 6.06 Samba server, correct?  The conf file from your 7.10 laptop client machine won't help.  (I only ask because some folks get confused. :))

Cheers,

Eiríkr

Yes, the smb.conf I posted is from my 6.06 box.

---

### Post by Eiríkr on 2008-03-22
Alrighty then.  I've got Gutsy 7.10 with Samba v3.026 on my end, so that's all I can presently speak to.  That said, here's what I've noticed in looking over your smb.conf file.

```
[global]
   workgroup = BODHIEM
   server string = %h server (Samba, Ubuntu)
   
   dns proxy = no
   
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   
   panic action = /usr/share/samba/panic-action %d
   
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   
   socket options = TCP_NODELAY
   
#   browseable = yes    # <-- Problematic.  This does not belong in the [global] section.

   wins support = no
   
[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
#   writable = no       # Same as "read only = yes", but since this is already the default,
                        # you should leave this out and simplify your conf file.
   create mode = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
#   browseable = yes    # Already the default, so you should leave this out and simplify your conf file.
#   read only = yes     # Already the default, so you should leave this out and simplify your conf file.
   guest ok = no
   
[ShareTest]
   path = /home/lecterman/ShareTest
#   available = yes     # Already the default, so you should leave this out and simplify your conf file.
#   browseable = yes    # Already the default, so you should leave this out and simplify your conf file.
#   public = yes        # <-- Problematic.  Same as "guest ok = yes", 
                        # but requires the guest user to be defined - mising in your conf file.
#   writable = no       # Same as "read only = yes", but since this is already the default,
                        # you should leave this out and simplify your conf file.

[Movies]
   path = /media/usbdisk/Movies
#   available = yes     # Already the default, so you should leave this out and simplify your conf file.
#   browseable = yes    # Already the default, so you should leave this out and simplify your conf file.
#   public = yes        # <-- Problematic.  Same as "guest ok = yes", 
                        # but requires the guest user to be defined - mising in your conf file.
   writable = yes
```

If you aren't actually sharing your printer via your 6.06 Samba server, I'd recommend that you remove the two printer-related share sections to simplify matters.  

As far as your connection problem, I suspect it might be related to user authentication.  You've defined [Movies] as a "public" share, but you haven't defined the guest user.  This defaults to the value of "nobody", as noted [here in the man page](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTACCOUNT).  And since it is highly unlikely that user "nobody" has any permissions on the /media/usbdisk directory on your server, attempting to access this way would produce an error.

Are you accessing from Ubuntu using a specific username and password, or as a guest?

Cheers,

Eiríkr

---

### Post by kecterman on 2008-03-23
> **Eiríkr said:**
> Alrighty then.  I've got Gutsy 7.10 with Samba v3.026 on my end, so that's all I can presently speak to.  That said, here's what I've noticed in looking over your smb.conf file.

As far as your connection problem, I suspect it might be related to user authentication.  You've defined [Movies] as a "public" share, but you haven't defined the guest user.  This defaults to the value of "nobody", as noted [here in the man page](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTACCOUNT).  And since it is highly unlikely that user "nobody" has any permissions on the /media/usbdisk directory on your server, attempting to access this way would produce an error.

Are you accessing from Ubuntu using a specific username and password, or as a guest?

Cheers,

Eiríkr

I just want my other computers to be able to see my 6.06 shared folders and watch movies etc from wherever they are in the house.  A username and password is just a hinderance to what I want.  No printer sharing required for now.  I just want to be able to get in with my 7.10 laptop as easily as I can with my Windows XP (work) laptop.

---

### Post by Eiríkr on 2008-03-23
I'm guessing you have the share mapped as a drive on your XP machine?  If so, you must have entered username and password info when first doing so; after that, Windows holds onto authentication info so you don't have to enter it ever again (convenient, but this gives rise to very difficult situations if the Samba username or password ever change).  That's likely why access from XP is so simple.

Gnome (the default Ubuntu desktop environment) seems to have similar capabilities.  In Nautilus, you can access your Samba share by typing [font=courier]smb://SERVER/SHARE[/font] into the location bar (usually hidden by default; display by hitting Ctrl+L or clicking View -> Location Bar).  Nautilus should show an authentication dialog, prompting for username and password, and giving you the option of storing this info forever so you don't need to enter it again next time.  This is why I asked how you are accessing your Samba shares from your Ubuntu laptop.  

In Samba (and actually in Windows too, technically speaking), you *cannot* not have a username at some point in the equation.  With true "guest" access, there's still a username involved, only the client (the person connecting) never sees it -- but it must still be defined somewhere, since Samba needs to know what Unix user is accessing in order to figure out permissions.  The default Samba guest is user "nobody", which is very restricted indeed.  If the smb.conf file does not specify a different user, any guest connection will use this default.  Note that the share definitions must *also* specify "guest ok = yes", or they *will not* allow guest access.  In the end, though, it can be easier to set up, *and* more secure, to use proper user security, and simply have Gnome (or KDE or whatever) save your login credentials so you'll only have to enter them once.  

Since you don't need any printer sharing, I'd recommend removing those two sections.  Also be sure to enter the edits suggested in my previous post.  

If you have any trouble getting Gnome to save your login info, let me know and we'll go from there.

Cheers,

Eiríkr

---

### Post by kecterman on 2008-03-23
That's the thing that puzzles me. I never ddid *anything* to get XP to connect, it was just there and has been ever since.  Same with my eMac on the same network.  XP just sees everything and can get in.

On the other hand, the Linux machines can see each others shared folders but not the files.

I cannot even get it to prompt me for usernames and passwords.  I just get the error message.

I tried adding usernames to the smb.conf using the "sudo smbpasswd -a "username"" command, but it does not do me any good as I am not being prompted for the information.



> **Eiríkr said:**
> I'm guessing you have the share mapped as a drive on your XP machine?  If so, you must have entered username and password info when first doing so; after that, Windows holds onto authentication info so you don't have to enter it ever again (convenient, but this gives rise to very difficult situations if the Samba username or password ever change).  That's likely why access from XP is so simple.

Gnome (the default Ubuntu desktop environment) seems to have similar capabilities.  In Nautilus, you can access your Samba share by typing [font=courier]smb://SERVER/SHARE[/font] into the location bar (usually hidden by default; display by hitting Ctrl+L or clicking View -> Location Bar).  Nautilus should show an authentication dialog, prompting for username and password, and giving you the option of storing this info forever so you don't need to enter it again next time.  This is why I asked how you are accessing your Samba shares from your Ubuntu laptop.  

In Samba (and actually in Windows too, technically speaking), you *cannot* not have a username at some point in the equation.  With true "guest" access, there's still a username involved, only the client (the person connecting) never sees it -- but it must still be defined somewhere, since Samba needs to know what Unix user is accessing in order to figure out permissions.  The default Samba guest is user "nobody", which is very restricted indeed.  If the smb.conf file does not specify a different user, any guest connection will use this default.  Note that the share definitions must *also* specify "guest ok = yes", or they *will not* allow guest access.  In the end, though, it can be easier to set up, *and* more secure, to use proper user security, and simply have Gnome (or KDE or whatever) save your login credentials so you'll only have to enter them once.  

Since you don't need any printer sharing, I'd recommend removing those two sections.  Also be sure to enter the edits suggested in my previous post.  

If you have any trouble getting Gnome to save your login info, let me know and we'll go from there.

Cheers,

Eiríkr

---

### Post by Eiríkr on 2008-03-23
How do you access from XP?  Do you click My Network Places -> Entire Network -> Microsoft Windows Network -> WORKGROUP -> SERVER -> SHARE?

---

### Post by kecterman on 2008-03-23
> **Eiríkr said:**
> How do you access from XP?  Do you click My Network Places -> Entire Network -> Microsoft Windows Network -> WORKGROUP -> SERVER -> SHARE?

Yes.  I have mapped it since first connecting, but either way I have not had to put in any credentials.

Same thing connecting to my mac.  No credentials required, I just go right in.

---

### Post by Eiríkr on 2008-03-23
Interesting...  Can you write to the shares from XP, or only read?  I'm curious now about the permissions on your shares; could you paste in the results of the following:
```
ls -l /media/usbdisk/Movies
ls -l /home/lecterman/ShareTest
```

PS -- I just noticed that some of the lines in the edited smb.conf file example I'd posted earlier had run together.  One moment and I'll fix that.  

Cheers,

Eiríkr

---

### Post by kecterman on 2008-03-23
> **Eiríkr said:**
> Interesting...  Can you write to the shares from XP, or only read?  I'm curious now about the permissions on your shares; could you paste in the results of the following:
```
ls -l /media/usbdisk/Movies
ls -l /home/lecterman/ShareTest
```

PS -- I just noticed that some of the lines in the edited smb.conf file example I'd posted earlier had run together.  One moment and I'll fix that.  

Cheers,

Eiríkr

Read only as far as I know.  And that is all I really need for now.

Results for the first one is:

-r-x------ 2 lecterman lecterman 5168812032 2008-03-15 17:29 Death Proof.mpg
-r-x------ 2 lecterman lecterman 3542718464 2008-03-15 19:35 Harold and Kumar Got To White Castle.mpg.mpg
-r-x------ 2 lecterman lecterman 3707045888 2008-03-15 11:44 Ice Age 2.mpg
-r-x------ 2 lecterman lecterman 3168016384 2008-03-10 23:18 Ice Age.mpg
dr-x------ 1 lecterman lecterman          0 2008-03-09 22:16 Images
-r-x------ 2 lecterman lecterman 4318914560 2008-03-10 00:06 Meet The Parents.mpg
-r-x------ 2 lecterman lecterman 3163555840 2008-03-09 22:11 Open Season.mpg
-r-x------ 2 lecterman lecterman 3886196736 2008-03-09 20:15 Resident Evil Extinction.mpg
-r-x------ 2 lecterman lecterman 2725584896 2008-03-11 17:26 The Reaping.mpg
-r-x------ 2 lecterman lecterman 6455922688 2008-03-15 23:50 Way of The Gun.mpg
-r-x------ 2 lecterman lecterman 4970729472 2008-03-11 19:34 Wrong Turn 2.mpg

And I deleted ShareTest since my original post today.

---

### Post by Eiríkr on 2008-03-23
Doh!  Forgot a "d" in there (ls -l_d_).  But even so I'm a bit baffled, as only user "lecterman" should have any access at all to these files.  And your smb.conf file clearly doesn't specify that guest logins should use the "lecterman" username.  

Is there any chance your eMac and XP usernames are this very same "lecterman" username?  That might explain it.

---

### Post by kecterman on 2008-03-23
> **Eiríkr said:**
> Doh!  Forgot a "d" in there (ls -l_d_).  But even so I'm a bit baffled, as only user "lecterman" should have any access at all to these files.  And your smb.conf file clearly doesn't specify that guest logins should use the "lecterman" username.  

Is there any chance your eMac and XP usernames are this very same "lecterman" username?  That might explain it.

The result of ls -ld is:

dr-x------ 1 lecterman lecterman 4096 2008-03-16 01:45 /media/usbdisk/Movies

The eMac and XP machine (my work computer) have different usernames that lecterman.
Totally different.  So as you can see this is completely baffling me.

I am watching a movie right now on my XP laptop through my 6.06 box, but cannot on my 7.10 laptop.  I can also play mp3s from the eMac through my XP machine.

I can see the eMac and the 6.06 box through my 7.10 laptop, but I cannot see the files on the 6.06 machine or even see the shared folders on the eMac.

Weird huh?

---

### Post by Eiríkr on 2008-03-23
I'm beginning to think this might be related to behaviour of older Samba versions... :confused:

Another thought is that, if your Samba server has been up and running for a while, it's possible that any changes to the smb.conf file haven't been applied.  If you've made any changes, be sure to restart the server to apply them:
```
sudo /etc/init.d/samba restart
```

On your eMac, what Mac OS version are you running?  How do you try to access your Samba shares?  I've got Tiger 10.4.11 on my old iBook, and in Finder, I click Network -> WORKGROUP -> SERVER -> Connect button.  Upon clicking Connect, a dialog pops up:

----------
**SMB/CIFS File System Authentication**

Enter the workgroup or domain and your user name
and password to access the server "SERVER."

Workgroup or Domain
[textbox area]

Name
[textbox area]

Password
[textbox area]

[checkbox] Remember this password in my keychain

[Cancel] [OK]
----------

Does this sound at all familiar?

PS -- Sharing from the eMac to the XP machine doesn't have any bearing on your Ubuntu setup.

---

### Post by kecterman on 2008-03-23
I restarted samba again and now I am prompted for a password.  So I added a password to the 6.06 samba file and now I CAtN get in.  However I tried to open one of the movie files via VLC (my default player) and I cannot get them to play (whole new problem).  So I think I am rolling now.

As far as OSX, I am running Panther.  I get the dialog box when I try to connect to the 6.06, but the username and password do not work.....yet.



> **Eiríkr said:**
> I'm beginning to think this might be related to behaviour of older Samba versions... :confused:

Another thought is that, if your Samba server has been up and running for a while, it's possible that any changes to the smb.conf file haven't been applied.  If you've made any changes, be sure to restart the server to apply them:
```
sudo /etc/init.d/samba restart
```

On your eMac, what Mac OS version are you running?  How do you try to access your Samba shares?  I've got Tiger 10.4.11 on my old iBook, and in Finder, I click Network -> WORKGROUP -> SERVER -> Connect button.  Upon clicking Connect, a dialog pops up:

----------
**SMB/CIFS File System Authentication**

Enter the workgroup or domain and your user name
and password to access the server "SERVER."

Workgroup or Domain
[textbox area]

Name
[textbox area]

Password
[textbox area]

[checkbox] Remember this password in my keychain

[Cancel] [OK]
----------

Does this sound at all familiar?

PS -- Sharing from the eMac to the XP machine doesn't have any bearing on your Ubuntu setup.

---

### Post by Eiríkr on 2008-03-23
> **kecterman said:**
> I restarted samba again and now I am prompted for a password.  

Great!  Do you see the password prompt on both XP and the eMac?


> **kecterman said:**
> So I added a password to the 6.06 samba file and now I CAtN get in.  

Also good.  Given your comment below, I assume you can *only* get in from XP?  And by "get in", I assume you mean you can open the share folder and see the files?


> **kecterman said:**
> However I tried to open one of the movie files via VLC (my default player) and I cannot get them to play (whole new problem).  So I think I am rolling now.

What username did you use on login?  From the [font=courier]ls -l[/font] results you posted earlier, *only* username "lecterman" has any access at all to the shared files.  


> **kecterman said:**
> As far as OSX, I am running Panther.  I get the dialog box when I try to connect to the 6.06, but the username and password do not work.....yet.

When you ran [font=courier]sudo smbpasswd -a USERNAME[/font] earlier, did you use the "lecterman" username?  Did you then try to enter this into the OSX dialog?


Cheers,

Eiríkr

---

