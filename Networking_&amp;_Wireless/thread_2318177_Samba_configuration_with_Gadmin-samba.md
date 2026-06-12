---
title: "Samba configuration with Gadmin-samba"
date: 2016-03-23
forum: Networking &amp; Wireless
---

### Post by andrea102 on 2016-03-23
Hi, 
My Samba seems to start at boot but only for the localhost, not for other network machines. 
```
telnet locahost 445
```
opens

```
telnet my.machine.ip 445
```
connection failed.

If I open up Gadmin-samba and do Deactivate-Activate, then it opens up ports 445 and 139 for other machines.

I did 
```
ln /etc/samba/smb.conf /usr/share/samba/smb.conf
```
for linking the config file of Gadmin-samba to the smb daemon starting at boot.

How to have autoboot? 
What does Deactivate-Activate does in Gadmin-samba?

---

### Post by bab1 on 2016-03-23
I can't stress this too strongly -- DO NOT USE Gadmin-samba TO CONFIGURE A SAMBA FILE SERVER.

You are doomed to failure.

Why did you do think the following would help?
> ln /etc/samba/smb.conf /usr/share/samba/smb.conf

Hopefully you have unmolested smb.conf files for both locations saved somewhere.  

I recommend you purge everything related to the Samba server install (not including the data you wish to share).  Then you can start over.  The default /etc/samba/smb.conf file is all you need to configure a simple file server (sharing files).  All you need to do is add the share definition at the bottom of that file.

---

### Post by andrea102 on 2016-03-24
Hi, thanks for your answer.

Is the Gadmin-samba still being developed? I don't understand...I am a Windows graphical fan, but sometimes I can't do without Linux.
Just the basic graphical configuration coming with Ubuntu is not so flexible. I need to have write permissions.

How can *start over, *as you say?

---

### Post by bab1 on 2016-03-24
> **andrea102 said:**
> Hi, thanks for your answer.

Is the Gadmin-samba still being developed? I don't understand...I am a Windows graphical fan, but sometimes I can't do without Linux.
Just the basic graphical configuration coming with Ubuntu is not so flexible. I need to have write permissions.

How can *start over, *as you say?
I don't believe Gadmin-samba is being developed or maintained.  Most of the references are older than 3 years.  I'm not sure what you mean by *"...sometimes I can't do without Linux"*.  Can you enlighten us.   Nothing regarding Samba is created by Ubuntu.  Samba is an separate project of Samba.org.  There are 3rd party GUI interfaces that are really not needed for basic configuration of Samba file sharing.  

Samba itself does not determine the file system permissions.  That is always ultimately determined at the file and directory (folder) level.

I would at least get rid of all the Gadmin-samba stuff.  If you have not installed Synaptic (the GUI package manager), I encourage you to do so.  You can search on Gadmin and see all of the items you installed.  Then you can just purge them.  I will keep the CLI commands to a minimum, but you will find that the easiest and most precise method to configure any Linux host is with terminal commands.

To install Synaptic it's best to just install at the command line with this ```
sudo apt-get install synaptic
```

I don't know what version you Ubuntu you have install so I can only guess how to find Synaptic.  With Ubuntu (Unity) you can just click on the DASH icon and type synaptic in the search box and a click will open it.

Use Purge, not just remove Gadmin.  Once you have done that, we can look and see how damage Samba itself is.  My guess is that Samba itself is okay and all that is needed is new configuration files.  There may be some Samba tools that need to be removed later on.  There are simple tests that we can employ to check on that later on.

The first thing is to look at the existing smb.conf file(s).  Post the text output back here for these 3 terminal commands```

ls -l /etc/samba

cat /etc/samba/smb.conf

cat /usr/share/samba/smb.conf

```

What are your file permission problems?

---

### Post by andrea102 on 2016-03-26
Ok, reloaded from base. Same error with Nautilus share management: I can't delete the files from another computer. And I had to enable Guest access for being able to view.

The 2 smb.conf are identical:

```

-rw-r--r-- 1 root root 9542 &#1084;&#1072;&#1088; 26 18:22 /etc/samba/smb.conf
andre@andre-VirtualBox:~$ ll /usr/share/samba/smb.conf 
-rw-r--r-- 1 root root 9542 &#1084;&#1072;&#1088;  3 20:07 /usr/share/samba/smb.conf
andre@andre-VirtualBox:~$ ll -h /usr/share/samba/smb.conf 
-rw-r--r-- 1 root root 9,4K &#1084;&#1072;&#1088;  3 20:07 /usr/share/samba/smb.conf

```


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
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

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
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

########## Domains ###########

#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#

# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

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
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin



```


[ATTACH=CONFIG]267990[/ATTACH]

[ATTACH=CONFIG]267991[/ATTACH]

---

### Post by bab1 on 2016-03-26
> **andrea102 said:**
> Ok, reloaded from base. Same error with Nautilus share management: I can't delete the files from another computer. And I had to enable Guest access for being able to view.

Same error?  I don't remember you mentioning either a permissions error or that you wanted to used Samba user shares.

There are significant limitations to using Samba usershares.  The main one is that you can only create shares in your home directory.  Another is that it has limited access for all users but the creator.

But..., I'm sure Samba is up and running.  You can check it with this simple terminal command```
pgrep -l mbd
```

If you want to create Samba shares that multiple users have read and write (rw) access to, you will need to configure the share by editing the smb.conf file.  Here is an annotated example of the text you *could* add to the bottom of the smb.conf file```

# Basic share
;[Test_Share]  [COLOR="#FF0000"]<-- the name of the share [/COLOR]
;comment = A simple test share  [COLOR="#FF0000"]<-- A comment about the purpose of the share[/COLOR]
;path=/data/test  [COLOR="#FF0000"]<-- Linux path to the directory that is shared[/COLOR]
;guest ok = yes  [COLOR="#FF0000"]<-- This allows all users access to the share[/COLOR]
;writeable = yes  [COLOR="#FF0000"]<-- This allows all users write capability[/COLOR]
;
;  [COLOR="#FF0000"]<-- Comment marker (all text after the ; is just a comment)[/COLOR]
;  [COLOR="#FF0000"]<-- If you want the line to be active just remove the semi-colon (;) [/COLOR] 

```
The complexity is planing for the share.  Where in the file system to locate it?  How do I control user permissions?  How do I use a multiple user group?

This might help you get the idea: [http://ubuntuforums.org/showthread.php?t=2313205&highlight=andrew283]("http://ubuntuforums.org/showthread.php?t=2313205&highlight=andrew283")  ...Start at post #4.  I'm sure you will have questions after you read the thread.  Ask here and I will help you with your share(s).

FWIW, the terminal (CLI) is not all that hard to learn if you keep notes of the commands are used.

---

### Post by andrea102 on 2016-03-27
Which smb.conf? In etc or in usr?

The Nautilus config creates an extra file in /var/lib/samba/usershares/downloads
which I have tried to edit:

> 
root@andre-VirtualBox:~# cat /var/lib/samba/usershares/downloads 
#VERSION 2
path=/home/andre/Downloads
comment=
;usershare_acl=S-1-1-0:F
sharename=Downloads
read only = no
browseable = yes
force user = andre
writable = yes



---

### Post by andrea102 on 2016-03-27
I have linked the 2 files
```

root@andre-VirtualBox:~# ll /etc/samba/smb.conf 
lrwxrwxrwx 1 root root 25 &#1084;&#1072;&#1088; 27 11:20 /etc/samba/smb.conf -> /usr/share/samba/smb.conf

```

Added the following

```

[Downloads]
#VERSION 2
path=/home/andre/Downloads
comment= Home Downloads
;usershare_acl=S-1-1-0:F
;sharename=Downloads
read only = no
browseable = yes
writeable = yes
root@andre-VirtualBox:~# cat /usr/share/samba/smb.conf


```

with the following result
```

root@andre-VirtualBox:~# testparm 
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Downloads]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Downloads]
    comment = Home Downloads
    path = /home/andre/Downloads
    read only = No



```

did 

```

root@andre-VirtualBox:~# /etc/init.d/samba restart 
root@andre-VirtualBox:~# /etc/init.d/smbd restart 
root@andre-VirtualBox:~# pgrep -l mbd
929 smbd
27413 smbd
27451 nmbd
27490 smbd


```

Still i cannot erase those files from Windows.

---

### Post by bab1 on 2016-03-27
> **andrea102 said:**
> I have linked the 2 files
```

root@andre-VirtualBox:~# ll /etc/samba/smb.conf 
lrwxrwxrwx 1 root root 25 &#1084;&#1072;&#1088; 27 11:20 /etc/samba/smb.conf -> /usr/share/samba/smb.conf

```

This should not be done.  I'm not sure where you got this idea that this is something that needs to be done.  No tutorial that I've ever seen recommends it  _The only file that is used to configure Samba file sharing is */etc/samba/smb.conf*_.  The conf files for most Linux applications are in /etc/.  The file located at /usr/share/samba/smb.conf file is for reference only.  I'd return the /usr/share/samba/smb.conf file back to it's defaults. 
> 
Added the following

```

[Downloads]
#VERSION 2
path=/home/andre/Downloads
comment= Home Downloads
;usershare_acl=S-1-1-0:F
;sharename=Downloads
read only = no
browseable = yes
writeable = yes
root@andre-VirtualBox:~# cat /usr/share/samba/smb.conf

```

with the following result
```

root@andre-VirtualBox:~# testparm 
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Downloads]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Downloads]
    comment = Home Downloads
    path = /home/andre/Downloads
    read only = No

```

You should use either Samba usershares or the /etc/samba/smb.conf file.  _One or the other, **NOT BOTH**!_
> 

did 

```

root@andre-VirtualBox:~# /etc/init.d/samba restart 
root@andre-VirtualBox:~# /etc/init.d/smbd restart 
root@andre-VirtualBox:~# pgrep -l mbd
929 smbd
27413 smbd
27451 nmbd
27490 smbd


```

Still i cannot erase those files from Windows.
As it will always be if you don't follow instructions.

You either didn't read carefully or maybe didn't understand the steps in the link I gave you.  You have to configure the Linux file permissions (correctly) for Samba file sharing to work properly.

The directory permissions should be 0775 (not 0755) and the file permissions should be 0664 (not 0644).  In addition the user group should be a group that all users that are sharing the directory are in.  Since this share is a sub-directory of your home directory I imagine that the ownership is andre:andre (user:user-group).  If all the users are in the sambashare group you can use that group so the ownership is andre:sambashare.

Sharing the directory is the 3rd and last thing to do.  First you need to create the user, then set the ownership and permissions of the directory you are going to share.  If all the local users can access the directory that is to be shared you can then create the share and the users should be able to access the share remotely.

One last thing.  You are better off using sudo (not sudo -i) for root user commands rather than staying logged in as root.  The user environment changes when you are logged in as the root user.  You will be forever chasing problems of ownership and permissions under those condititons.  When you're current working directory is a mortal users (human) directory you need to be logged in as that user.

---

### Post by andrea102 on 2016-03-28
> **bab1 said:**
>  I'd return the /usr/share/samba/smb.conf file back to it's defaults. 

You should use either Samba usershares or the /etc/samba/smb.conf file.  _One or the other, **NOT BOTH**!_



I don't think it make any difference, at least I am sure I am not editing the wrong file.
What about the file created by Nautilus for setting Share configuration on the Download directory?

> **bab1 said:**
> 

You either didn't read carefully or maybe didn't understand the steps in the link I gave you.  You have to configure the Linux file permissions (correctly) for Samba file sharing to work properly.

The directory permissions should be 0775 (not 0755) and the file permissions should be 0664 (not 0644).  In addition the user group should be a group that all users that are sharing the directory are in.  Since this share is a sub-directory of your home directory I imagine that the ownership is andre:andre (user:user-group).  If all the users are in the sambashare group you can use that group so the ownership is andre:sambashare.




I have put 777 for the Download directory.


> **bab1 said:**
> 

Sharing the directory is the 3rd and last thing to do.  First you need to create the user, then set the ownership and permissions of the directory you are going to share.  If all the local users can access the directory that is to be shared you can then create the share and the users should be able to access the share remotely.


What user? 
Why don't the system-config-samba or the Nautilus share tab work?


> **bab1 said:**
> 
One last thing.  You are better off using sudo (not sudo -i) for root user commands rather than staying logged in as root.  The user environment changes when you are logged in as the root user.  You will be forever chasing problems of ownership and permissions under those condititons.  When you're current working directory is a mortal users (human) directory you need to be logged in as that user.


How many times am I supposed to enter my password?

---

### Post by bab1 on 2016-03-28
> **andrea102 said:**
> I don't think it make any difference, at least I am sure I am not editing the wrong file.

How dumb is that?  ;-)  If you don't know what you are doing why not follow advice of someone who does know?
> 
What about the file created by Nautilus for setting Share configuration on the Download directory?

What about it?
> 
I have put 777 for the Download directory.
And...> 
What user?
Unless the user is the guest user (nobody) there must be both a Linux user (adduser) and a related Samba user (smbpasswd). > 
Why don't the system-config-samba or the Nautilus share tab work?

Neither of these are part of the Samba suite of apps.  System-config-samba is a 3rd party python app.  It's not written or supported by the developers of Samba.  Nautilus is part if the Gnome desktop project.  They made arbitrary decisions on how Nautilus should work.  As I said before; add users, configure the directory stucture, then configure the sharing.  It works every time.  
> 
How many times am I supposed to enter my password?
Heh, as many times as it takes to get the job done.

---

