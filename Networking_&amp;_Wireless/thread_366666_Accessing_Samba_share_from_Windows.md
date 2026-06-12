---
title: "Accessing Samba share from Windows"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by twhayes on 2007-02-21
I'm trying to set up my LAN so that I can access a Samba share on my Ubuntu box directly from programs in Windows XP.  I've followed the advice given in this post - [http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605) and everything works, except when I access the Ubuntu files they are read only.  For example, I open OpenOffice on my WinXP box and navigate using the File Open dialog box to the Ubuntu Samba share and open a file.  But, it is only read only.

I've set up the LAN to work the other way, too.  Direct access from within OpenOffice on my Ubuntu box to shared directories on my WinXP box.  That works fine.

I've listed my smb.conf file below.  You'll see two shares, data-kubuntu & Windows-kubuntu.  The Windows-kubuntu share is a fat32 partition on another hard drive on the ubuntu box.  I have complete read/write access to it, even from my WinXP box.  The other share, data-kubuntu, is a directory in /home and the one that I can only get read-only access to from the WinXP box.

I've searched the forums and changed smb.conf several times, but all to no avail.  

I'd appreciate any advice on what I've done wrong or how to fix this problem.

Here's a listing of my smb.conf.

> # Sample configuration file for the Samba suite for Debian GNU/Linux.
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
workgroup = HOME

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
   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
passdb backend = smbpasswd

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
security = share
restrict anonymous = no
domain master = no
preferred master = no
max protocol = NT
ldap ssl = No
server signing = Auto

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

[printers]
comment = All Printers
browseable = no
path = /tmp
printable = yes
create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers

[data-kubuntu]
case sensitive = no
guest ok = yes
msdfs proxy = no
read only = no
path = /home/tim/data-kubuntu

[Windows- Kubuntu]
case sensitive = no
guest ok = yes
msdfs proxy = no
read only = no
comment = Windows on Kubuntu
path = /home/tim/windows

---

### Post by bernied on 2007-02-21
I'm a bit rusty on this but I suspect that this is a permissions problem on the kubuntu machine. I'm guessing that when you connect to both shares, you are connecting as user guest (because this is the default in Windows), so the samba server is applying permissions to you as user guest. What are the permissions in those two directories?
```
cd /home/tim/windows
ls -al
cd /home/tim/data-kubuntu
ls -al
```
If you want to connect as yourself (tim?), you'll have to instruct windows that that's how you want to connect, and I suspect that you'll have to supply your kubuntu password before you can connect. You'll also have to add yourself to the samba server's list of users, which is not the same as linux's list of users in /etc/passwd (though it is possible to set it up so that it is the same, but this is way beyond me). I think the command to use (on the kubuntu server) is smbpasswd, but you'd better research that yourself (try 'man smbpasswd' for starters). Or you may be able to manage samba users with some GUI.

The other alternative is to change the permissions on those files, but then anyone on the network can change them - is that what you want?

---

### Post by dmizer on 2007-02-21
you haven't followed the howto very closely.

aside from two things you need to change to the in order to provide for non password protected samba shares, you should use the same exact smb.conf file given in that howto.

change 1: under [global], security = share instead of security = user
change 2: as you've already discovered ... guest = ok for each of the share configurations.

so your share definition should look like this:
```
[data-kubuntu]
    path = /home/tim/data-kubuntu
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = tim
    force group = tim
```

also, make sure that the share definition in brackets -> [] does not have spaces in it as it can cause problems.  currenlty there is a space in your [Windows-Kubuntu] definition.

this will give you non password challenged shares on your ubuntu computer.  so, as long as your ubuntu computer remains safely behind your router firewalled local home network, you will be okay ... but if that machine connects directly to the internet, or if you ever take it anywhere other than your local network, you will be exposing yourself to root kit attacks.

root kit = you lose everything on your ubuntu box.

---

### Post by twhayes on 2007-02-21
dmizer - thanks much for your reply.  interestingly enough I had removed the force user statements because I was being asked for a username and pw when trying to access the ubuntu samba share from my WinXP box.

But, i took your advice and added them back into smb.conf.  The first time I tried to access the ubuntu samba share from WinXP I got a request for a pw for a user account.  That failed.  Then I tried to access a file on the ubuntu samba share from within openoffice.  This time I was prompted for a username and pw.  I gave it the credentials for 'tim' and everything worked fine.

Maybe I wasn't being patient enough and waiting for the systems to 'settle down' after being configured.

In any event, it is now working to my satisfaction.  i really appreciate your help.  Now I can start working on printer sharing, which has been a challenge before for me.  But, that was with Debian.  Hopefully, Ubuntu will make this task a bit easier.

Thanks again.  TwHayes

---

### Post by dmizer on 2007-02-21
you shouldn't have gotten challeged with a password if you change
security = user
to 
security = share

after making changes, did you restart samba?
sudo /etc/init.d/samba restart

---

