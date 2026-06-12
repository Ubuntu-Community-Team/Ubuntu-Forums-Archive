---
title: "Accessing files in 14.04.1. LTS from Win8.1 ( 2 computers, 1 network)"
date: 2014-08-21
forum: Networking &amp; Wireless
---

### Post by chris278 on 2014-08-21
I'm really sorry if this is an obvious question for you guys but I'm completely new to Linux and this is the first time I've ever tried to network two computers and I've been trying to figure this out for a couple of hours and now I don't know weather I should throw my computer out of the window or myself.

I'm trying to access files on Xubuntu 14.04.01 LTS from a second computer running Windows 8.1.

I can see the other computers' folder in both operating systems but neither will let me access the other OS's folder.

Mainly I need to access the files on my Linux machine from my Windows 8.1 machine but when I click on the folder I get the following message:

> \\ is not accessible. You might not have permissions to use this network resource. Contact the administrator of this server to find out if you have access permission.

The parameter is incorrect.

Help would be greatly appreciated,

---

### Post by matt_symes on 2014-08-21
Hi

I assume you have been trying to configure samba.

Can you post all the steps you have taken so far, any tutorials you have followed and any configuration files you have changed.

If you can tell us what you have done, it should be easier to fix, although i may not be able to look until tomorrow.

Kind regards

---

### Post by roger_1960 on 2014-08-21
Hi

Have you installed samba on your linux PC?  You need to.  On your linux PC right click on the folder ( your home ?) that you wish to share and you should be given the option to install it.

Roge

---

### Post by chris278 on 2014-08-21
I really don't know what I've changed. I guess it's a catch 22: if I'd arrived knowing nothing I would have been told to Google it but because I Googled it I seem to be in a bigger mess. :0/

I was running a command line to try and get to a host folder as per instructions from one webpage but nothing seemed to be popping up; another command line was just coming back as not recognised.

Xubuntu doesn't have the permissions option on the right click menu so I tried to configure it through options and found a list of acronyms. I just picked the one that looked most intuitive.

Is there really not a definitive set of instructions on how to do this? All I can find through Google are incorrect solutions to similar problems and no responses to questions posted with the specific error messages I'm getting.

I am completely prepared to re-install my Xubuntu OS if that's really what it takes (it's a new install) I just can't believe there's not an easier way (I don't understand why this is so difficult).

Should I re-install Xubuntu and come back with the fresh install or is there an easier way? I think re-installing and starting from scratch might be the easier way. Maybe I should install a different flavour Ubuntu?

> **roger_1960 said:**
> Hi

Have you installed samba on your linux PC? You need to. On your linux PC right click on the folder ( your home ?) that you wish to share and you should be given the option to install it.

RogeXubuntu dosn't have a share option when you right click. The closest I've found is a set of choices under "Options" (basically a list of acronyms). I did install Samba, but the command lines I've found haven't helped.

Edit: Sorry, I mean "Permissions" Under "Properties" when I right click on the folder (sorry, I've only got one mouse for the two computers (long story) so I'm switching between the two). I right click on the folder and I've got a "permissions" tab in the "properties" menu.

Edit: The options I have in the Permissions tab under Properties when I right click on the folder are;

Chris
lpadmin
sambashare

adm
cdrom
dip
plugdev
sudo

Should I be looking to set it to Sambashare?

When I try and access the 8.1 folder it tells me it's timing out.

Edit: I'm going to check to see if a typeface error might have caused me to enter an incorrect password in the network settings.

Edit:
/etc/samba/smb.conf
bash: /etc/samba/smb.conf: Permission denied

...Ugh!

---

### Post by matt_symes on 2014-08-21
Hi

You you tried rogers advice in the post above ?

If that does not fix it can you please post the output of

```
dpkg -l | egrep "samba|cifs|smb"
```

and 

```
cat /etc/samba/smb.conf
```

That will give a place to start looking.

Kind regards

---

### Post by chris278 on 2014-08-21
I did install samba but will run that process again to see if there's any kind of difference.

I'll re-boot and run that command line and post the output.

If it's easier I can just do a fresh reinstall and start from scratch.

(Apologies for my frustration)

---

### Post by chris278 on 2014-08-21
I just found this also ([http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)) so will work through it and see if it'll make a difference.

Again, my apologies for my frustration, I'm just in the midsts of crisis management from the tail end of a streak of bad luck.

chris@chris-GB-BXBT-2807:~$ SAMBA
SAMBA: command not found
chris@chris-GB-BXBT-2807:~$ sudo apt-get install samba
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 8 not to upgrade.
chris@chris-GB-BXBT-2807:~$

chris@chris-GB-BXBT-2807:~$ dpkg -l | egrep "samba|cifs|smb"
ii  libsmbclient:i386                          2:4.1.6+dfsg-1ubuntu2.14.04.3          i386         shared library for communication with SMB/CIFS servers
ii  python-samba                               2:4.1.6+dfsg-1ubuntu2.14.04.3          i386         Python bindings for Samba
ii  python-smbc                                1.0.14.1-0ubuntu2                      i386         Python bindings for Samba clients (libsmbclient)
ii  samba                                      2:4.1.6+dfsg-1ubuntu2.14.04.3          i386         SMB/CIFS file, print, and login server for Unix
ii  samba-common                               2:4.1.6+dfsg-1ubuntu2.14.04.3          all          common files used by both the Samba server and client
ii  samba-common-bin                           2:4.1.6+dfsg-1ubuntu2.14.04.3          i386         Samba common files used by both the server and the client
ii  samba-dsdb-modules                         2:4.1.6+dfsg-1ubuntu2.14.04.3          i386         Samba Directory Services Database
ii  samba-libs:i386                            2:4.1.6+dfsg-1ubuntu2.14.04.3          i386         Samba core libraries
ii  samba-vfs-modules                          2:4.1.6+dfsg-1ubuntu2.14.04.3          i386         Samba Virtual FileSystem plugins
ii  smbclient                                  2:4.1.6+dfsg-1ubuntu2.14.04.3          i386         command-line SMB/CIFS clients for Unix
chris@chris-GB-BXBT-2807:~$ 


chris@chris-GB-BXBT-2807:~$ cat /etc/samba/smb.conf
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

chris@chris-GB-BXBT-2807:~$


Edit: This is another problem I'm experiencing...

chris@chris-GB-BXBT-2807:~$ sudo /etc/init.d/samba stop
chris@chris-GB-BXBT-2807:~$ sudo touch /etc/samba/smb.conf
chris@chris-GB-BXBT-2807:~$ sudo gedit /etc/samba/smb.conf
sudo: gedit: command not found
chris@chris-GB-BXBT-2807:~$

---

### Post by roger_1960 on 2014-08-21
Hi

The xubuntu text editor is "mousepad" not gedit.

Maybe you shold install a GUI for dealing with samba shares:

> sudo apt-get update
sudo apt-get install system-config-samba

(I dont run xubuntu but would think this is in the repos)

Roger

---

### Post by Morbius1 on 2014-08-21
For one thing your host name is too long making it invisible on the network:
> chris-GB-BXBT-2807
Edit /etc/samba/smb.conf and enter the following lines - right under the workgroup line - towards the top of the file:
```
netbios name = chris-2807
name resolve order = bcast host lmhosts wins
```
[COLOR=#0000cd]The netbios name doesn't have to be exactly that but it does have to be 15 characters or less in length.[/COLOR]

Then restart samba:
```
sudo service smbd restart
```
```
sudo service nmbd restart
```
Wait 5 minutes - seriously. Then try to access your Linux machine again.

[COLOR=#0000cd]**EDIT**[/COLOR]: BTW, you have no shares defined and Thunar doesn't allow you to create one within it but you should be at least able to see the Linux machine - not that you can do anything with it.

---

### Post by chris278 on 2014-08-22
Thanks guys, but this is making my head spin. I'm going to move to a different Linux OS...

...can you recommend the most vanilla, most user-friendly, most straightforward Linux OS? (something I can Google answers to more easily and which might have tutorials and/or walkthroughs)?

Would that be standard Ubuntu, or is there something even more straight forward?

I literally know virtually nothing about Linux so I don't have any of the background to understand the posted solutions (I'm grateful for them but I'm unable to contextualise them).

Thanks :0)

P.S. Also I don't like the Xubuntu mouse theme (we had mice a while ago and it blew monkey-nuts).

---

### Post by Morbius1 on 2014-08-23
Well, [COLOR=#0000cd]roger_1960[/COLOR] suggested installing system-config-samba for share creation which has a gui but if you don't want to do that then moving to Ubuntu will allow you to create the samba share through it's file manager ( nautilus ).

You would still have to edit smb.conf I'm afraid if you keep your host name length that long and you still may have to change the name resolve order so ....

OSX is a fine OS and most of it's users aren't even aware that there is a terminal. Up front cost is rather high but OS upgrades are free. ;)

---

### Post by chris278 on 2014-08-23
I'll switch to Ubuntu and go from there.

My host name wasn't really a choice, I just went with the default it gave me (I had no idea it would make any difference so I just went with the default the system generated).

Anyway, this time around, when I install Ubuntu I'll shorten the name. Are there other things I should know in advance, to make the process a little smoother?

---

### Post by alias2234 on 2014-08-23
> **chris278 said:**
> I'll switch to Ubuntu and go from there.

Good choice.
I run only Ubuntu 14.04 LTS on my machine and have not regrett it. 

To be a newbie is a must before we learn to be pros. ):P

---

### Post by chris278 on 2014-08-23
> **alias2234 said:**
> Good choice.
I run only Ubuntu 14.04 LTS on my machine and have not regrett it. 

To be a newbie is a must before we learn to be pros. ):PI guess so. :0/

I think my expectations as to what Linux is and isn't probably needs to be modified (I didn't realise it was as complex as this).

---

### Post by QIII on 2014-08-23
It's not more complex.  It's just not a drop-in replacement for Windows as many expect.

Windows is your "native language".  You did not learn it in a day.

Now you are learning a different language.

As a native English speaker, you can't expect to walk in to your first German class and expect to write a Nobel Prize winning novel in German.

---

### Post by chris278 on 2014-08-23
To be honest I wasn't expecting it to be in German. ;0P

---

