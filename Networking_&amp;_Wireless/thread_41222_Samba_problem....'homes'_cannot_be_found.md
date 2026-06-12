---
title: "Samba problem....'homes' cannot be found"
date: 2005-06-12
forum: Networking &amp; Wireless
---

### Post by Metz on 2005-06-12
I've just built a second Ubuntu build which it to effectively act as my web server at home. This is a desktop machine tucked away in a cupboard. My laptop also runs ubuntu, I need to a) vnc to the server for maintenance, etc and b) connect to the file systems on the server to copy development code, etc across.

I've got vnc running....that wasn't too tricky. However, after having followed the ubuntuguides to install and setup samba, I'm having for luck opening up a share to the other machine. Ideally, I want to share everything....I simply want to be able to treat /etc, /home, /usr and /var on the server as extenstions to my laptop's filesystem.

Am I asking too much ?

The problem is that everytime I open a connection (through places>-connect to server) to my server machine, I get a listing for the 'homes' share. But when I open said share...I simply get a message saying :-

[b]The folder contents could not be displayed.

"homes" couldn't be found. Perhaps it has recently been deleted

[/b]

Any ideas ? 


***smb.conf***
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
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = primenet
netbios name = prime-v

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
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
   security = user
   username map = /etc/samba/smbusers

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


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
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


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

wins support = no
[homes]
   comment = Home Directories
   browseable = yes
   path = /home/metz/

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

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


[Group]
   comment = Group Folder
   path = /home/group
   public = yes
   writable = yes
   valid users = metz
   create mask = 0777
   directory mask = 0777
   force user = nobody
   force group = nogroup

available = no
browseable = no
[public]
   comment = Public Folder
   path = /home/public
   public = yes
   writable = yes
   create mask = 0777
   directory mask = 0777
   force user = nobody
   force group = nogroup
available = no
browseable = no


```

---

### Post by elvis on 2005-06-24
"Homes" is a virtual mapping to a username.  Whatever username you authenticate to the Samba server with, that will be the name of the home folder presented to you.

For instance, if I connect to my machine as "elvis" with the appropriate password, then I can access //machine/elvis.  However if I connect as another user (say, "bob") then //machine/elvis doesn't exist any more, but //machine/bob does.

If you connect with no authentication, you will simply see "homes" and get the error you describe when you try to connect to it.

---

### Post by MemoryDump on 2005-07-15
I'm having a similiar problem..

I have samba running on 3 linux boxes including the one I'm on right now.

1 is Fedora Core 3
2 are Ubuntu
all are running the latest samba

all 3 are pretty much the same.. they are all part of the same workgroup and I've created the my samba users with passwords that match..

now when I browse my network on one of my ubuntu box I see all my servers including a windoze box I have setup.. when I double click my winbox I see all my shares.. but when I click on either my my other ubuntu box or fc3 box I only see the "homes" folder.. my main use folder doesn't show up.. in this case I have user "memorydump" setup on all 3 boxes with matching passwords.. I'm stomped as this used to work.. and all of a sudden stopped..

here's part of my smb.cof from one of my ubuntu boxes..

```
workgroup = MEMORYDUMP
netbios name = SKYWALKER
[homes]
   comment = Home Directories
   browseable = yes
   writable = yes
```

thxs
-MD

---

### Post by mcook2 on 2007-05-07
I'm having a similar problem.  In my case the Network File Browser on my Ubuntu Desktop 7.04 system "drops" the "homes" share from my OSX 10.4.9 box.

OSX has the latest security fix, but it's Samba is only version 3.0.10. 

I am using the same username and password on both machines. I did notice earlier that the UIDs are  different: 501 on OSX, 1000 on Ubuntu. 

I'm unable to browse my homes share //MONA/homes as Ubuntu's Network File Browser gives the error message "The folder contents could not be displayed. Perhaps it has recently been deleted."

Later on I noticed these messages on the OSX box's log.smbd about the same time:

```

[2007/05/06 23:50:05, 1] auth_ods.c:opendirectory_auth_user(208)
  User "mcook" failed to authenticate with "dsAuthMethodStandard:dsAuthSMBNTKey" (-14090) :(
[2007/05/06 23:50:05, 1] auth_ods.c:opendirectory_smb_pwd_check_ntlmv1(377)
  opendirectory_smb_pwd_check_ntlmv1: [-14090]opendirectory_auth_user
[2007/05/06 23:50:18, 0] /SourceCache/samba/samba-100.7/samba/source/smbd/server.c:main(789) 

```

My workaround is as follows:

1) I'm able to connect from a Terminal as usual and I can read/write OK:
```
smbclient //mona/homes 
```

2)This URI works in File Browser/Location and I am able to browse OK:
```
smb://mcook@mona/
```

3)This URI takes me to the home folder directly:
```
smb://mcook@mona/homes
```

So, in Network File Browser I just created a bookmark for smb://mcook@mona and I'm using that for now.

---

