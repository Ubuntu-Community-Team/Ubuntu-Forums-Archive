---
title: "Shared windows folders keep asking for passwords"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by Bishma on 2008-02-28
The file server in my office is a windows XP box with shared folders. About 60% of the time when I try to connect to one of these folders or copy files from them (using Samba) I get prompted to enter a user name and password. There is no authentication set up on the windows machine, so there's no user name or password to enter. Clicking on OK with blank fields doesn't work. If I cancel and retry enough times it will eventual work but it's annoying. Is there anything I can change on my end to make it stop prompting me for a password?

---

### Post by swerdna on 2008-02-28
> **Bishma said:**
> The file server in my office is a windows XP box with shared folders. About 60% of the time when I try to connect to one of these folders or copy files from them (using Samba) I get prompted to enter a user name and password. There is no authentication set up on the windows machine, so there's no user name or password to enter. Clicking on OK with blank fields doesn't work. If I cancel and retry enough times it will eventual work but it's annoying. Is there anything I can change on my end to make it stop prompting me for a password?
Please do 3 things:
1: Post the contents of your Samba configuration file, smb.conf, located at /etc/samba/smb.conf
2: What is the name of the windows workgroup as specified on the windows machines (R-click My Computer --> Properties --> Computer Name)
3: check windows file shares "allow other users to change my files" enabled (probably you have)

Swerdna

---

### Post by Bishma on 2008-02-28
In reverse order (because they're easiest to answer that way)

3. Yes, "allow other users to change my files" is checked
2. Workgroup name is IDX
1. Here's the conf file. I'm pretty sure that that only thing I've change in it since putting Kubuntu on this machine is the work group name.

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
   workgroup = IDX
   null passwords = yes
   security = share

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

Thank you for your time

---

### Post by Eiríkr on 2008-02-28
Hey there --

Your smb.conf file doesn't do much, but it appears to be irrelevant here anyway as it's all about the Samba serving side of things, only you're not using your Ubuntu machine as a server.  

You say "There is no authentication set up on the windows machine", but even so there will be a username and some sort of password (possibly blank?) on the Windows side.  Windows provides an option to make the machine behave as a one-user gig, thereby skipping the whole formal username and password logon, but these still exist.  I suspect that is what Windows is looking for -- I don't think it's the Ubuntu side that's the issue here.  

I also don't know of any setting to change this, since the issue appears to be on the XP side.  Your best bet is to figure out what the primary XP logon username is, and to figure out if there's a password.  So, go over to your XP machine, and click Start -> Control Panels -> User Accounts.  From here, figure out which is the primary logon account, and next time your try to access from your Ubuntu machine, try typing in that username.  

If anyone else has any ideas, by all means chime in.  :)

Cheers,

Eiríkr

---

### Post by Bishma on 2008-02-28
I've tried using just the windows machine's login with no password to no avail (I am sure tha machine has no password). I'm I'm sure the shared directory doesn't have a password either.

---

### Post by Eiríkr on 2008-02-29
Another thought -- are you connecting via a GUI app, or using [font=courier]mount[/font] in a terminal?  If you're using a GUI, there might be lots of other stuff getting in the way behind the scenes.  Try this and see if it gives you any more reliable connectivity.
```
mount -t cifs //SERVERNAME/SHAREPATH /LOCAL/SHARE/MOUNT -o rw,user=WIN_USERNAME,password=PASSWORD
```
Replace the caps with your own values.  And if you're certain there's no Windows password, try using either nothing after the equals, or empty double quotes "" and see which works.  

HTH,

Eiríkr

PS -- You might need to replace SERVERNAME above with the server's IP address instead.

---

### Post by swerdna on 2008-02-29
And also another two cents worth: turn off any third party firewall on the windows box to test whether that is interfering (and I suppose on Linux box too)

---

### Post by Loosewheel on 2008-02-29
Hi Bishma,
 Have a look at the man page for smbclient. (Type 'man smbclient' in a console)
Here is some of it:

 "There is no default password. If no password is supplied on the com&#8208;
          mand line (either by using this parameter or adding  a  password  to
          the  -U  option (see below)) and the -N option is not specified, the
          client will prompt for a password, even if the desired service  does
          not  require one. (If no password is required, simply press ENTER to
          provide a null password.)"
Looks like you need to type 'smbclient -Uusername'

Good luck with this.

---

### Post by Eiríkr on 2008-03-01
> ... the client will prompt for a password, **even if the desired service does not require one**.

Fascinating.  Thank you for pointing this out; it never would have occurred to me to look in the smbclient man page for this.  And rather odd decision on the devs' part to build in this behaviour; maybe the thinking is that it somehow increases security?  Anyway, thanks again!

Cheers,

Eiríkr

---

### Post by Giak on 2008-04-23
[http://ubuntuforums.org/showthread.php?t=710599](http://ubuntuforums.org/showthread.php?t=710599)

---

### Post by bazzieb on 2008-04-23
Has this been sorted yet? 

I have a couple of questions for postee.
 1. Is the windows machine part of a domain
 2. Is the ubuntu machine part of the domain

Whenever i tried to connect to windows pc's on my domain i need to use a username and password because my ubuntu machine doesnt authenticate to my microsoft domain. But i never had to change anything on the smb.conf.

---

