---
title: "Me too, on Samba problems since update"
date: 2016-04-20
forum: Networking &amp; Wireless
---

### Post by Lloydb39 on 2016-04-20
I see others have similar problems so I might as well get in on this: I have a Windows 7 computer connected to a Ubuntu 14.04 computer by Ethernet. Worked fine at sharing files and a printer until the last Samba update. Now, I can't print over the wire and can not share files. Trying to access my Windows shares from Linux results in a demand for a Workgroup password, which I don't have and never have used. (I tried the obvious, like "admin" and "password" and my name.) Quite annoying. Would appreciate any help or troubleshooting tips.

---

### Post by bab1 on 2016-04-21
> **Lloydb39 said:**
> I see others have similar problems so I might as well get in on this: I have a Windows 7 computer connected to a Ubuntu 14.04 computer by Ethernet. Worked fine at sharing files and a printer until the last Samba update. Now, I can't print over the wire and can not share files. Trying to access my Windows shares from Linux results in a demand for a Workgroup password, which I don't have and never have used. (I tried the obvious, like "admin" and "password" and my name.) Quite annoying. Would appreciate any help or troubleshooting tips.
I'm not going to say this isn't a problem, but I will say I have 3 working Samba  servers on Ubuntu 14.04.3 fully updated hosts running with no problems.  The Samba version maybe the key here.  The version I have on all 3 hosts is ```
samba -V
Version 4.1.6-Ubuntu

```What version of Samba are you using?  How did you create your shares?  Post the output of this command```
cat /etc/samba/smb.conf
```What ownership and permissions are used on the Linux directories that you are sharing via Samba?  Are you allowing guests or are the users both Linux users and Samba users?

---

### Post by Lloydb39 on 2016-04-21
I'm using version 4.3.8

Here is the cat output:

```
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

---

### Post by Nahuel_ on 2016-04-21
I just dug out an old drive with Ubuntu 15.10 installed but not updated since nov 6 2015, compared the smb.conf file on that drive with mine and they're **identical** (and they should be, since I never did any configuration, everything worked out of the box).

So, clearly the problem is not in smb.conf (at least not with its default configurations)

---

### Post by bab1 on 2016-04-21
> **Nahuel_ said:**
> I just dug out an old drive with Ubuntu 15.10 installed but not updated since nov 6 2015, compared the smb.conf file on that drive with mine and they're **identical** (and they should be, since I never did any configuration, everything worked out of the box).

So, clearly the problem is not in smb.conf (at least not with its default configurations)
The smb.conf file configures the variables used by the smbd daemon (Samba server).  The smb.conf in itself is not the problem in any case.  The interesting thing is the Samba version I'm running on my 3 servers is Samba 4.1.6.  The OP is Using Samba  4.3.8.  How did that happen.  Maybe it was part ot the 14.04.3 ISO.  There my be a bug in the  Samba (smbd)  4.3.8 version.  Samba.org is moving to a new smbd binary and this may be the the first bug in it.

---

### Post by dr_shred on 2016-04-21
I have the same problem:  samba suddenly stopped working.

I have windows,  ubuntu and osx machines, all of which could access my share
and now they can't, since 18 Apr 2016, after an update.

Tried uninstalling, reinstalling, etc.  Looking at the syslog:

Apr 21 14:12:28 randolph kernel: [102476.168385] init: smbd main process (9105) terminated with status 1
Apr 21 14:12:28 randolph kernel: [102476.168400] init: smbd main process ended, respawning
Apr 21 14:12:28 randolph kernel: [102476.240128] init: smbd main process (9125) terminated with status 1
...
Apr 21 14:12:29 randolph kernel: [102476.588976] init: samba-ad-dc main process (9204) terminated with status 1
Apr 21 14:12:29 randolph kernel: [102476.606328] init: smbd main process (9207) terminated with status 1
Apr 21 14:12:29 randolph kernel: [102476.606343] init: smbd main process ended, respawning
Apr 21 14:12:29 randolph kernel: [102476.652558] init: smbd main process (9215) terminated with status 1
...
Apr 21 14:12:29 randolph kernel: [102476.749823] init: smbd respawning too fast, stopped

This happens each time I restart smbd and nmdb.  There was a non-ubuntu forum web post from way back
in 2010 which mentioned something like this, but it didn't apply directly.  Something about samba
not finding a another service, or searching for the service too often and not finding it.

---

### Post by scpatl4now on 2016-04-21
I am having the same problem also running 4.3.8 
Is there a way to go back to a previous version?  I have also uninstalled reinstalled...also on my windows box netstat shows the Ubuntu machine, but it wont connect.  My guess is that there is a permission problem somewhere but dont know where to look

---

### Post by scpatl4now on 2016-04-21
Seems a bug has been reported
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1573221](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1573221)

---

### Post by Nahuel_ on 2016-04-22
Read **Morbius1**'s post. He gives a temporary solution to mount the Windows shares until this is fixed. Worked great for me.
[http://ubuntuforums.org/showthread.php?t=2321029&page=2&p=13474661#post13474661](http://ubuntuforums.org/showthread.php?t=2321029&page=2&p=13474661#post13474661)

---

### Post by scpatl4now on 2016-04-22
Thats not the problem.  I have no problem seeing the windows shares on the Ubuntu box.  The problem is that windows doesnt see the server on 14.04.  On 15.10 it sees them but wont connect saying I dont have access permission

---

### Post by Morbius1 on 2016-04-22
See if my post on your other thread does anything: [http://ubuntuforums.org/showthread.php?t=2321048&p=13474349#post13474349](http://ubuntuforums.org/showthread.php?t=2321048&p=13474349#post13474349)

---

### Post by matus-milos on 2016-04-27
Hi, this helped me: [COLOR=#242729][FONT=Arial]Change "security = share" to "security = user"[/FONT][/COLOR]

---

### Post by matus-milos on 2016-04-28
and then backup your samba config file, remove and install samba again.

---

### Post by Lloydb39 on 2016-05-01
I'll describe the behavior if that will help. From the Linux machine, I can see the Windows workgroup and the folders I want but when I try to access them, it asks for the password. (By the way, I dug what is supposed to be the Workgroup password out of Windows, but it does not work. Not sure it is the right one because Microsoft doesn't make it at all clear the difference between passwords for "workgroup" "homegroup" and the machine itself.) From the Windows machine I can see the actual files in the Linux machine but can't open any of them. On top of all this, Linux now frequently reports a system failure, although it does not usually require a reboot. Don't know if it is related to the Samba problem or not.

---

### Post by Lloydb39 on 2016-05-01
Two other facts that may help solve this problem.
I noticed most conf files for samba have the term "security - user" in them. Mine does not.
My Windows machine has been set to NOT ask for a password when sharing files. But Ubuntu does anyway and, as stated, I have no idea what the password might be.

---

### Post by kdxensen on 2016-05-02
Me too. Exactly as described, when I try to access a Windows 7 share it asks for a non-existent password. The temporary work-around described by Morbius1 worked for me.... This on 14.04 and a fresh install of 16.04.

---

### Post by Lloydb39 on 2016-05-04
I just updated to 4.3.9 version of Samba. Still no fix.

---

### Post by Lloydb39 on 2016-05-06
New development. Windows computer can now see and use Linux computer files. Still does not work in reverse. I have no idea what changed.

---

### Post by RallyDarkstrike on 2016-05-06
@Lloyd - did you make any changes or anything? I also updated to the supposed 'fix' version of Samba, and all three of my Linux Mint 17.3 MATE machines are still asking for passwords when accessing unpassworded Windows shares....

---

### Post by Lloydb39 on 2016-05-10
Another new development. I can print from the Linux computer to the printer attached to the Windows computer now. Slowly, something is fixing the problems, but I still can't access the Windows shares from Linux.

---

### Post by bab1 on 2016-05-10
> **Lloydb39 said:**
> Another new development. I can print from the Linux computer to the printer attached to the Windows computer now. Slowly, something is fixing the problems, but I still can't access the Windows shares from Linux.
At this point Samba is fully patched and all regressions have been fixed.  If you still have problems they should be due to some configuration errors.

For simple sharing the default smb.conf file with shares defined at the bottom should work. If you want a unique workgroup you can change that.   Samba should now "just work".

---

### Post by RallyDarkstrike on 2016-05-10
I just replaced my smb.conf with the default and then re-added my Share settings...I am still being asked for passwords on non-passworded Windows shares...?

---

### Post by bab1 on 2016-05-10
> **RallyDarkstrike said:**
> I just replaced my smb.conf with the default and then re-added my Share settings...I am still being asked for passwords on non-passworded Windows shares...?
Since you are not the OP,  I'd suggest starting your own thread.  Thread hijacking is poor form around here.

---

