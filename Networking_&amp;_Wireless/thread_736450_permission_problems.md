---
title: "permission problems"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by linux noooob on 2008-03-26
When i try to write data to my ubuntu shared folder from windows it says that windows doesn't have the right permissions so how do i set the read/write permissions in ubuntu?

---

### Post by zeronothing on 2008-03-26
try editing the samba config file on your linux machine. if you go to /etc/samba you will find the smb.conf file for samba in there. open up the file in your favorite text editor (remember you will need to use sudo to edit the file). go down to the "authentication" section of the config file and where it says something like "security = something" change the "something" to "share". then save the file and restart samba. to restart samba open up terminal and execute sudo /etc/init.d/samba restart

---

### Post by linux noooob on 2008-03-26
the file is blank 

note: i am using ubuntu 7.04 if that makes a difference

---

### Post by zeronothing on 2008-03-26
interesting, did you make sure you install samba. open up terminal and execute this:

sudo apt-get install samba

this will install samba and to configure your shared drive you can use the samba tool for setup the shared drive under system-> administration-> shared folders.

once you have done all that you will need to edit the config file:

sudo gedit /etc/samba/smb.conf

this will open up the config file hopefully. then like i said before go to the section of the config file called "authentication". where it says "security = something" change the "something" to "share". also make sure their is no colon before "security = something". ex/

; security = something to 

security = share

---

### Post by Eiríkr on 2008-03-26
Setting security to share doesn't necessarily help, unless you're going for a specific guest login setup, and even then you have to be careful about which guest account is specified (it's the very limited "nobody" account by default) and what permissions that account has on the server's filesystem.  

Have a look at [post=4496702]this post[/post] for an explanation of how to set up filesystem permissions for sharing purposes.  

And incidentally, run the following in a terminal to check again on your smb.conf file.  An empty smb.conf file shouldn't allow any sharing at all.
```
less /etc/samba/smb.conf
```
If that still comes up empty, but you can see your Ubuntu machine from your Windows machine, something *very* strange is going on.  

Cheers,

Eiríkr

---

### Post by linux noooob on 2008-03-26
well it is blank and i remember installing samba and when i am looking through the network it says the windows file with a little smb icon on it this is really messed

---

### Post by Eiríkr on 2008-03-26
Not that it matters at this point, but out of curiosity, does the file even exist?

Given your somewhat bizarre symptoms, I'd recommend you fire up Synaptic, do a *full* removal of the Samba package, reboot, install Samba again, reboot for good measure, and then check your smb.conf file.  

Cheers,

Eiríkr

---

### Post by linux noooob on 2008-03-26
ok

---

### Post by linux noooob on 2008-03-26
there is stuff in it but it won't show up in gedit :P

---

### Post by Eiríkr on 2008-03-26
That's likely because the file is owned by root with no write permissions for anyone else.  That's why you'll need to either just use the [font=courier]less[/font] CLI viewer command I suggested above, or use [font=courier]sudo[/font] with gedit.  [font=courier]less[/font] is the safer option, as that way you can't accidentally change the file.  

Cheers,

Eiríkr

---

### Post by linux noooob on 2008-03-26
i was root when i tried gedit and it didn't work but thats ok because the nano command works well. But more problems 1 i can write to the folder but when i try to download world of warcraft to the folder it won't let me and the permission thing comes up (using windows to download because for some reason on windows i get 500+ kb/s and ubuntu i only get 100kb/s)

---

### Post by Eiríkr on 2008-03-26
> i can write to the folder but when i try to download world of warcraft to the folder it won't let me and the permission thing comes up

If the folder you're talking about here is your Ubuntu share, this depends half on your smb.conf setup and half on your filesystem permissions.  Let's start with the Samba half.  Please post the contents of your [font=courier]/etc/samba/smb.conf[/font] file and we'll go from there.

Cheers,

Eiríkr

---

### Post by zeronothing on 2008-03-26
This is true, in order for stuff to show up in gedit you have to use sudo before it to edit the file. 

but in order to fix your problem you will need to edit the file /etc/samba/smb.conf. now in order to edit that file with gedit you can execute this command in terminal to edit it with gedit. just copy and plaste this in terminal

sudo gedit /etc/samba/smb.conf

or you can use the next command to edit the file in a commanline text editor called "nano"

sudo nano /etc/samba/smb.conf

I had this same problem that you are having. the problem is because samba by default uses a user authentication where as windows uses just simple file sharing. in order for ubuntu to act the same way you need to change the part in the samba config file 

####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = share

---

### Post by zeronothing on 2008-03-26
remember, in order for changes to take in samba you need to restart the server too. in order to do that you need to execute this next command (you can copy and paste this into terminal)

sudo /etc/init.d/samba restart

---

### Post by zeronothing on 2008-03-26
also make sure that under system->administration-> shared folders, then you will see what folders you have sharing. highlight one of them and make sure you don't have them set to read-only. uncheck that check box.

I have attached a smb.conf file to my post so you can look at what my config looks like. towards the bottom of the config file you going to see the shared folders I have setup but compair them to yours to see the differences

---

### Post by Eiríkr on 2008-03-26
@zeronothing --

Unfortunately, simply changing [font=courier]security[/font] to "share" is not enough.  If a share definition is set up for guest access, you also need to specify a guest account in your [font=courier][global][/font] options, or guest shares will use the default guest account, "nobody", which is extremely limited and almost guaranteed to cause problems.  "user" security is easy enough to set up if done correctly, and can actually be less error prone.  

PS -- Your attachment appears to be missing...?

@linux noooob --

It would be very helpful if you could post your [font=courier]/etc/samba/smb.conf[/font] file.  You can display it by typing one of the following lines into a terminal:
```
sudo gedit /etc/samba/smb.conf
less /etc/samba/smb.conf
```
Copy and paste into a post here in this thread.  

Cheers,

Eiríkr

---

### Post by linux noooob on 2008-03-27
> #
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
;   wins support = yes

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
   security = share

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
;   writable = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = yes
;   browseable = yes
;   create mask = 0600
;   directory mask = 0700

wins support = yes

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   public = yes
   writable = yes
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = no
   guest ok = yes
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


[share]
path = /home/andy/Desktop
comment = andrew's file folder on his computer
available = yes
browsable = yes
public = yes
writable = yes


There is the contents of my smb.conf file and thanks i got gedit to work i had the same problem with a bunch of files so i reinstalled gedit and it worked

---

### Post by zeronothing on 2008-03-27
Ok, I think I have a solution for you. I have been doing some testing with a setup just like yours (looking at you config file). So I just want to get an idea of what you want to make share able. are you looking to share you home directory, or are you looking to just share you home directory's desktop folder? this will help me get you running hopefully. 

try this:

make sure under system->administration-> shared folders, you have the shared folder you want being shared set, and with the nothing check in the read-only check box. next:

open up the samba config file in gedit command: sudo gedit /etc/samba/smb.conf

find the setting "security = something" and changed "something" to "user"

down at the bottom of the config file make sure the folder setting for the shared folder are set to:

Available = yes
browseable = yes
public = yes
writable = yes

after that you will need to set a password to the shared folder for samba. to do this you will need to execute the command:

sudo smbpasswd "your username on ubuntu" (without quotes): press enter
next: its going to ask you to enter a password for your username

after all that you need to restart samba using this command: sudo /etc/init.d/samba restart

now from the windows machine locate you ubuntu machine on the network. now when you click on you ubuntu machine it should ask you for a username and password. input your username on the ubuntu machine, then enter the password you made up for samba in the directions i just gave you. and this should give you permission to access and read, write and delete.

---

### Post by Eiríkr on 2008-03-27
@zeronothing --

Totally minor point, but the [font=courier]available = yes[/font] and [font=courier]browseable = yes[/font] settings are both the default values, so you don't need to include these lines at all.  :)

Cheers,

Eiríkr

---

