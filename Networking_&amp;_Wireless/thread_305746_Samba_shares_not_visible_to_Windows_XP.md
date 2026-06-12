---
title: "Samba shares not visible to Windows XP"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by wactuary on 2006-11-23
I have 2 Ubuntu machines (server and desktop) and a Windows Laptop.  From the server I had 2 directories shared via Samba that both the desktop and XP laptop could access.  Recently, the shares stopped being visible to the laptop.  I'm not sure what configuration changed that would cause this.  I've checked that the Samba shares are visible to the other Ubuntu desktop, so I think the shares are configured OK on the server.  I see the SMBD and NMBD services running OK.  But the laptop is not recognizing the computer names as they had previously (Samba announced the names to the WINS server, I believe?).  Now, to access the server I need to type the IP address directly.

I'm not sure what else I can do to debug this?  Any help out there?  What should I post that would help understand what is going wrong?

Thanks,
Chris
:confused:

---

### Post by livestockPimp on 2006-11-23
is the server set up as a wins server?
can i see you smb.conf?

---

### Post by wactuary on 2006-11-24
> **livestockPimp said:**
> is the server set up as a wins server?
can i see you smb.conf?

Sure thing.  Here is what I currently have.  I've fiddled a bit with the setttings since it stopped working, but it still passes testparm.  It was originally set to "security = user" with a user.map file, but I opened that up to see if that was my problem.  I also upped the logging level.  Also, in the interest of space, I've pulled out sections that are fully commented out like Printing and CDROM.

My home network is configured off of 192.168.13.*

The windows machine sees the Nosnhoj workgroup, but takes a long time come back and returns no visible machines.  

Thanks for helping me look into this.

```
[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = Nosnhoj

# server string is the equivalent of the NT Description field
   server string = %h server (Samba %v)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes 

# line added by cj based on a howto article.  should be redundant.
   remote announce = 192.168.13.255

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = lmhosts host wins bcast


#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m
   log level = 2
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
   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

   guest account = smbguest
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
;          SO_RCVBUF=8192 SO_SNDBUF=8192
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

[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0770

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0770

[music]
	path = /media/audio
	comment = "Music Folders"
	browseable = yes
	writeable = yes
	create mask = 0775
	directory mask = 0775

[photos]
	path = /media/photos
	comment = "Picture Folders"
	browseable = yes
	writeable = yes
	create mask = 777
	directory mask = 777

```

---

### Post by wactuary on 2006-12-03
After wasting way too much time on the Linux side, I finally realized that the problem was with the Windows Laptop.  Somehow the File and Print Sharing was disabled from the wireless card settings.  Binding that service to the connection and restoring the original Samba settings brought everything back to normal.  ](*,)

---

