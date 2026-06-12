---
title: "Windows Can't View my SMB Shared Folders"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by bothebobo on 2006-11-21
Im running dapper drake and wanted to share some folders on the windows network etup at my dorm. So i right-click on the corresponding folders and do the whole smb share thang and make sure they are shared in the correct workgroup. Now when i go in and find my computer on the network on my own computer I can see the folders I shared. When I use one of my friends windows machines and try to access my comp, it asks for a password and a username. I can't figure out what user name and pwd combo it wants. I figure that I have to define some allowable usernames and pwds in smb.conf, but don't know how. I really want no username and pwd, while maintaining write-protection.

Here's my smb.conf (i removed some of the irrelavent jazz):
[COLOR="Red"]#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = egmont

# server string is the equivalent of the NT Description field
   

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
;   security = user

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
server string = bobobobo
[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = no

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


[trainwreck]
path = /home/bo/train wreck
comment = hiphop, new ****, techno, raggae, blues...
available = yes
browseable = yes
public = yes
writable = no


[rocka-j]
path = /home/bo/1uno
comment = alm. rock
available = yes
browseable = yes
public = yes
writable = no

[rockk-å]
path = /home/bo/2dos
comment = alm. rock
available = yes
browseable = yes
public = yes
writable = no
[/COLOR]

---

### Post by x64Jimbo on 2006-11-21
Please read this wiki entry:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server)
For passwordless sharing with read-only, read the section titled 
[SIZE=3] "How to share public folders with read only permission (Authentication=No)"[/SIZE]

---

### Post by adamkane on 2006-11-21
You need to add a samba user with a samba password.

```

sudo smbpasswd -a system_username
gksudo gedit /etc/samba/smbusers

```

Insert the following line into the new file:

```

system_username = "network username"

```

Save the edited file.

---

### Post by x64Jimbo on 2006-11-21
> **adamkane said:**
> You need to add a samba user with a samba password.

```

sudo smbpasswd -a system_username
gksudo gedit /etc/samba/smbusers

```

Insert the following line into the new file:

```

system_username = "network username"

```

Save the edited file.
None of that is necessary following the directions from the wiki article. It doesn't authenticate at all, thus a username is not needed.

---

### Post by adamkane on 2006-11-21
I don't think that's an option. Not every wiki is well written or usable.

See:
[http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)

---

### Post by x64Jimbo on 2006-11-21
It's an option both in the wiki link I listed and in the one you just posted.
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29](http://easylinux.info/wiki/Ubuntu_dapper#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29)
It's the widely accepted method of adding public shares with read-only permissions for anonymous (no login) users.
I have personally used this very same method on my home machines to make them share across the network. It's how all my roomies can browse my music and movies without being able to delete them or replace them.

---

### Post by adamkane on 2006-11-21
Read-only Samba share? WTH? :)

---

### Post by x64Jimbo on 2006-11-21
> **adamkane said:**
> Read-only Samba share? WTH? :)
Yeah, that's what the OP was asking about. 
[QUOTE=bothebobo] I really want no username and pwd, while maintaining write-protection.[/QUOTE]

---

### Post by bothebobo on 2006-11-22
Thanx guys, everything worked perfectly using the wiki. i realized a bunch just got busted in a dorm not too far away by the anti piracy group, they got fined for about 100 thousand €, so i think im going to put a passwd on my computer and i think i can figure out how. Thanks again

---

### Post by x64Jimbo on 2006-11-22
If you're worried about getting busted with questionable content in your hard drive, you may want to (read: you probably should) encrypt your filesystem.

---

