---
title: "[SOLVED] sharing folders"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by xyrer on 2007-03-13
Hi, i've been trying to share a folder from my home directory but i want Windows users to be able to get in without providing a password, i checked and have noticed that Windows XP uses a default user, as I speak Spanish the user the windows uses is "invitado", so i tried to create it in samba, using webmin i created a user on my machine called "invitado" and that went well, but when i tried to convert the user to samba user i get this:

```
Failed to save user : The user was successfully saved, but an error occured in another module : samba::useradmin_create_user failed : /usr/bin/pdbedit failed :

NULL guest account!?!?
could not create account to add new user invitado

at ../web-lib-funcs.pl line 971.
```

and looking at google I got 2 pages in some weird language wich means nothing to me, I really want to install Ubuntu on several user desktops in the company but things like this stop me to do so, please someone shade a light about this on me.

---

### Post by bernied on 2007-03-13
Hola
Hmmm, does invitado translate to guest in ingles? I think the samba guest account is enabled by default, maybe that's why you get the error. 

I have a samba config on a server that I can't reach right now (it has been turned off for months and I've changed ssh keys since). If you can wait a couple minutes I'll hack into it and fetch the config file...

---

### Post by bernied on 2007-03-13
This is what I used:
```
[global]
	workgroup = blah
	server string = File Store
	security = SHARE
	null passwords = Yes
	guest account = guest
	log file = /var/log/samba/log.%m
	comment = Linux Samba Server
	hosts allow = 192.168.0., 127.

[share]
	comment = Shared files
	path = /mnt/hdb8/Share 
	read only = No
	guest only = Yes
	guest ok = Yes
```
Does this help?

---

### Post by xyrer on 2007-03-14
Hi, indeed Invitado translates to guest. but the configuration you put didn't work either, I have been able before to share a folder introducing a user and null password, but I want it without even the user, I put your configuration on my smb.conf and this screenshot comes out in the windows XP box, same as before.
it says connecting to systemlab wich is the name of the ubuntu box, it ask for password but it's no use to put anything or even nothing.

---

### Post by bernied on 2007-03-14
I see you have the user as 'systemlab\Invitado'. Have you tried this as just 'invitado' (note no capitals). You should only need to do this once, if I recall correctly (without a password), for each machine.
Can you post your smb.conf?

---

### Post by xyrer on 2007-03-14
the "systemlab/invitado" I assume is how WinXP resolves invitado user in systemlab pc, anyways that's something Windows takes out, is not like that on ubuntu, my smb,conf is:

#======================= Global Settings =======================

[global]
	log file = /var/log/samba/log.%m
	guest account = guest
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	socket options = TCP_NODELAY
	force directory mode = 777
	sync always = yes
	null passwords = yes
	public = yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	dns proxy = no
	netbios name = systemlab
	server string = %h
	writeable = yes
	locking = no
	delete readonly = yes
	invalid users = root
	force create mode = 777
	workgroup = sistemas
	os level = 20
	create mode = 777
	security = share
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	directory mode = 777
	hosts allow = 192.168.15., 127.

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# server string is the equivalent of the NT Description field

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth1

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects

# Put a capping on the size of the log files (in Kb).

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.

# Do something sensible when Samba crashes: mail the admin a backtrace


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


;   guest account = nobody

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

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


[share]
	browsable = yes
	path = /home/xyrer/share
	comment = Shared files 
	read only = No
	guest only = Yes
	guest ok = Yes

---

### Post by dannyboy79 on 2007-03-14
check this out for some hints:
[http://www.oreilly.com/catalog/samba/chapter/book/ch06_03.html](http://www.oreilly.com/catalog/samba/chapter/book/ch06_03.html)

i would suggest using like only 4 options in your smb.conf, then after you get that working, slowly add one or 2 options at a time and then you'll know why it's not working.

also, I noticed here [http://www.mepis.org/node/3045](http://www.mepis.org/node/3045)
that you can add a second password database, the link shows guest as an option. despite this being for Mepis, it'll work as samba is samba. good luck.

also, make sure you have no rules for your iptables firewall. 
sudo iptables -L
will show you if you have any rules. also, make sure you can ping each of the boxes. i will also point out that nautilus has a glitch where it won't let you "browse" your windows shares when you go thru the pull down, then pick windows network, then you pick your windows computer option. most of the time you'll get contents could not be displayed. not sure why, you'll just have to mount it manually using cifs ([http://ubuntuforums.org/showthread.php?t=288534)](http://ubuntuforums.org/showthread.php?t=288534)). then you can share files. don't forget about the permissions of the folders are critical.

---

### Post by bernied on 2007-03-14
> **xyrer said:**
> [global]
	log file = /var/log/samba/log.%m
	guest account = guest
Have you tried logging in as 'guest', rather than 'invitado'?

---

### Post by dannyboy79 on 2007-03-14
> **bernied said:**
> Have you tried logging in as 'guest', rather than 'invitado'?


i believe he's already told us that invitado is guest.

---

### Post by xyrer on 2007-03-14
Hi, I got lost in some point of your post dannyboy, I can ping the windows box and the iptables shows: ```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
``` but I don't have a clue of what it means.

you say I could use only 4 options, You mean entirely? would you be so kind to show me an example of how the entire smb.conf should be?

and I have no problem browsing windows shares, in fact, the windows pc has some shared folders I can access from ubuntu, but not viceversa.

I'm kind of newbie at this so i don't understand about the password database and the samba documentation is not completely clear although I understand some things.

I appreciate all your time.

---

### Post by dannyboy79 on 2007-03-14
all of this is already in the guide that I linked for you. if you read thru this link, you'll be on your way and it's way more understandable than the man pages trust me. don't forget about the owne: group of a share as well as the permissions of it that will matter also. [http://www.oreilly.com/catalog/samba/chapter/book/ch05_01.html](http://www.oreilly.com/catalog/samba/chapter/book/ch05_01.html)

ok, so it's more than 4 but try this:
[global]
      security = share
      workgroup = SIMPLE
      encrypt password=yes
[share]
      path = /home/xyrer/share 
      read only = no


WARNING: If you are presented with a dialog requesting the password for a user IPC$, then Samba did not accept the password that was sent from the client. In this case, the username and the password that were created on the client side must match the username/password combination on the Samba server. If you are using Windows 98 or Windows NT Service Pack 3 or above, this is probably because the client is sending encrypted passwords instead of plaintext passwords. You can remedy this situation by performing two steps on the Samba server. First, add the following entry to the [global] section of your Samba configuration file: encrypt password=yes. Second, find the smbpasswd program on the samba server (it is located in /usr/local/samba/bin by default) and use it to add an entry to Samba's encrypted password database. For example, to add user steve to Samba's encrypted password database, type **smbpasswd -a steve**. The first time you enter this password, the program will output an error message indicating that the password database does not exist; it will then create the database, which is typically stored in /usr/local/samba/private/smbpasswd.

using the guest option in samba can be tricky because sometimes you won't be able to write to the share with guest access so make sure you read about guest in samba., good luck

---

### Post by xyrer on 2007-03-14
well, I solved it by accident when I tried to look into the guest account to see how it was configured, see if that could give me a clue and i noticed linux had no guest account, so I created it and bam! the Windows box gets in without even noticing it is a linux share.

Thank you all for your precious time, I always learn a lot in every question I put in this forums, I hope to help others when my time comes.

---

### Post by dannyboy79 on 2007-03-14
so you created a linux user with the name of guest? then you added guest to your smbpasswd database? and then when it asked you for a password you just hit enter again without entering anything? please answer all this so if some1 else reads this thread they'll have a specific answer and will be able to solve there issue as well. I am glad you got it working.

---

### Post by xyrer on 2007-03-14
Well, I have to give credit to webmin for a couple things, I created the user like it's showed on the screenshot but before that i enabled user synchronisation as I show in the other screenshot, I put my smb.conf changes here:
```

[global]
	log file = /var/log/samba/log.%m
	guest account = guest
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	socket options = TCP_NODELAY
	force directory mode = 777
	sync always = yes
	null passwords = yes
	public = yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	dns proxy = no
	netbios name = systemlab
	server string = %h
	writeable = yes
	locking = no
	delete readonly = yes
	invalid users = root
	force create mode = 777
	workgroup = sistemas
	os level = 20
	create mode = 777
	security = share
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	directory mode = 777
	hosts allow = all

;   security = user

;   guest account = guest

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = yes

[share]
	guest account = guest
	comment = Shared files
	locking = yes
	browsable = yes
	path = /home/xyrer/share
available = yes
public = yes
writable = yes
guest ok = yes
guest only = yes

```

I got to say that all those changes to smb.conf alone were useless, nevertheless they may be important to someone.

everything I did got me into the same error until I created the user guest in my machine, the webmin has this great option to synchonice so I don't know exactly what happened there, anyways now the windows users get into my shared folders without even knowing it's a linux box, it doesn ask for either a user or password.

Hope this helps. any question, don't hesitate.

---

### Post by dannyboy79 on 2007-03-14
all that did was basically when you created the user guest within webmin, it created the samba user as well which is what we were trying to tell you. we thought you knew that since you were trying to use he gues account from winxp, that you would have added the guest account on your samba server. i noticed that you tried doing that but you tried adding it as the different langauge instead of adding the guest in english. so you could have just done a normal add user on your ubuntu machine, then like I said before, "smbpasswd -a steve" but with guest you would have been good to go. glad you got it!

---

### Post by xyrer on 2007-03-14
well, I first thought that was it, but this screens confused me, the number1 is before i created the guest account in linux, and the number2 is after I tried to convert linux users to samba users.
As you can see, the number2 says "guest is already the same", it might be because the sync between users but the guest account was in samba before anyways, I will try to do it from a clean install on another pc and post it.

---

