---
title: "Samba help"
date: 2015-03-11
forum: Networking &amp; Wireless
---

### Post by penny3 on 2015-03-11
I have recently run into a problem with my printer very similar to the one included in this previous post.
[http://ubuntuforums.org/showthread.php?t=2268145&highlight=canon](http://ubuntuforums.org/showthread.php?t=2268145&highlight=canon) 

It is weird because, up until yesterday, I was able to print just fine on the network (printer is connected to another computer). All of a sudden, it's not working. 

It appears that the bios name is too long on my system as well. I tried to follow the instructions that worked for the previous poster but I am stuck at the point where it refers to changing the bios name under [global]. Once I get to the advice given to the other poster that says: :
"gksudo gedit /etc/samba/smb.conf
    Add to [global] section
netbios name = (whatever you want to call the computer)"

I do not understand where the 'add to [global] section would be. When the screen pops up, at the top there are the usual menu options like 'file, view, edit, tools, etc.' but when I use the drop down menu, I cannot see anywhere where 'global' is listed. I am obviously missing something here. Could someone please outline for me where I find this [global] menu so that I can change the bios name?

Thank you!

---

### Post by SeijiSensei on 2015-03-11
It's a section in the Samba configuration file /etc/samba/smb.conf. If you use the "gksudo gedit" command you mentioned, you would add this line to the text of the file so it ends up looking something like this:
```

# This is the main Samba configuration file.
# more comments omitted

#======================= Global Settings =====================================
[global]

**netbios name = my-computer**

etc.

```
replacing "my-computer" with your machine's actual hostname.  The name should only include letters, numbers, and if needed, the hyphen.  It is case-insensitive.

Save the file, then restart Samba with the commands
```

sudo service smbd restart
sudo service nmbd restart

```

---

### Post by Mike_Walsh on 2015-03-11
Hallo, penny3.

I'm by no means an expert with Samba, being relatively new to its use myself. However, I believe I can help you with this one.

The first line; 'gksudo gedit /etc/samba/smb.conf'. You're using the text editor, gedit, to open the /etc/samba/smb.conf' configuration file WITH root permission. You can VIEW the file in question by going to that location, but you can't change it as a normal user; this is why 'sudo' is required. I don't know why the other poster has used 'gksudo'; this is normally reserved for opening graphical, or GUI-based applications. This is simply a text file.

Anyway; to get to the 'meat' of the matter. The 'global menu' that you're looking for is NOT a part of the text editor itself. It is a part of the document that you have just opened. You need to scroll down through the document itself until you reach where the 'global menu' section is mentioned. There, you SHOULD find the section you want.....and then it is simply a matter of editing the appropriate lines until they read the way you want them to.

Admittedly, when you mention the word 'menu' to most people, they immediately start hunting around the application controls to try and locate it.....

Hope that helps.


Regards,

Mike. :)

---

### Post by SeijiSensei on 2015-03-11
> **Mike_Walsh said:**
> I don't know why the other poster has used 'gksudo'; this is normally reserved for opening graphical, or GUI-based applications.

He used gksudo in order to launch gedit, the graphical editor that comes standard on GNOME-based systems.  To launch a text-based editor like nano after opening a terminal window, you would use "sudo nano".

---

### Post by penny3 on 2015-03-11
I cannot seem to find a 'netbios name' under Global settings ... here is what pops up ... (by the way, the computer name that shows up in the terminal is 'penny@penny-Satellite-A200:~$' which, as I understand from the other posters problem, is too long for Samba to work with). 

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

My computer is a duel boot ... is this the problem?

---

### Post by bab1 on 2015-03-12
> **penny3 said:**
> I cannot seem to find a 'netbios name' under Global settings ... here is what pops up ... (by the way, the computer name that shows up in the terminal is 'penny@penny-Satellite-A200:~$' which, as I understand from the other posters problem, is too long for Samba to work with). 

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

My computer is a duel boot ... is this the problem?

You **ADD** the line to the [global] section of the file.  The NETBIOS name can be any name that is 15 characters or less.

You can add the line right under the line with [global].

It would look *something* like this ```

[global]
netbios name = penny
```

Then you need to restart Samba with this terminal command```
sudo service smbd restart
```

You can check to see if the name shows up with this command```
smbtree
```

NOTE:  This has nothing to do with the computer's bios.  Using that term is misleading.  The term is NETBIOS which is a networking protocol.

---

### Post by penny3 on 2015-03-12
Hi Bab1 ... I followed your instructions and the following is what came up on the terminal screen:

(gedit:11092): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

---

### Post by bab1 on 2015-03-12
> **penny3 said:**
> Hi Bab1 ... I followed your instructions and the following is what came up on the terminal screen:

(gedit:11092): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

That's just the warning for GTK that you are using a GUI app in a terminal situation.  It shouldn't stop you from using **gedit**.

Did you edit the file successfully?  Did you reboot Samba?  What do you see with the command *smbtree*  ?

---

### Post by penny3 on 2015-03-12
I have pasted the terminal info below. I tried the command 'smbtree' and nothing showed up so then I used the command mentioned in the original poster's thread of 'smbtree -d3' and got the below info:

penny@penny-Satellite-A200:~$ sudo service smbd restart
[sudo] password for penny: 
smbd stop/waiting
smbd start/running, process 11333
penny@penny-Satellite-A200:~$ smbtree
Enter penny's password: 
penny@penny-Satellite-A200:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.1.218 bcast=192.168.1.255 netmask=255.255.255.0
Enter penny's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe54c414950] mpx_fde[(nil)] fd[7] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe54c414900] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe54c414890] mpx_fde[(nil)] fd[7] - disabling
penny@penny-Satellite-A200:~$

---

### Post by bab1 on 2015-03-12
> **penny3 said:**
> I have pasted the terminal info below. I tried the command 'smbtree' and nothing showed up so then I used the command mentioned in the original poster's thread of 'smbtree -d3' and got the below info:

penny@penny-Satellite-A200:~$ sudo service smbd restart
[sudo] password for penny: 
smbd stop/waiting
smbd start/running, process 11333
penny@penny-Satellite-A200:~$ smbtree
Enter penny's password: 
penny@penny-Satellite-A200:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.1.218 bcast=192.168.1.255 netmask=255.255.255.0
Enter penny's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe54c414950] mpx_fde[(nil)] fd[7] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe54c414900] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe54c414890] mpx_fde[(nil)] fd[7] - disabling
penny@penny-Satellite-A200:~$

hat NETBIOS name did you use?  Whatever that name was, what do you get when you use this command```
nmblookup <your_name>
```

---

### Post by JeQhdMD on 2015-03-12
Assuming your target printer is not wireless, if your goal is just to print to a printer connected to a different PC via USB,  another tack entirely would be to get an inexpensive wireless printer.   

Setting up a wireless network printer connection in ubuntu is easier (than samba) and more reliable (in my view).   And then there is always Google Cloud Print as well.

---

### Post by penny3 on 2015-03-12
This is what I get:

penny@penny-Satellite-A200:~$ nmblookup <your_name>
bash: syntax error near unexpected token `newline'
penny@penny-Satellite-A200:~$

---

### Post by bab1 on 2015-03-12
> **penny3 said:**
> This is what I get:

penny@penny-Satellite-A200:~$ nmblookup <your_name>
bash: syntax error near unexpected token `newline'
penny@penny-Satellite-A200:~$

Your supposed to use the NETBIOS name **you** selected instead of <your_name>.  ;-)

---

### Post by penny3 on 2015-03-12
Oh, good Lord! Well, I guess that speaks volumes for the kind of computer competence you are dealing with, eh? (insert blushing smilie face here)

Okay - I did it again with the name that I gave it and still no luck ... 

penny@penny-Satellite-A200:~$ nmblookup <Satellite>
bash: syntax error near unexpected token `newline'
penny@penny-Satellite-A200:~$

I just find it very strange that I *was *able to print until just a couple of days ago and have done nothing (too scared to even try!) except the software updating that has come up. Am beginning to seriously re-think the whole Ubuntu experience based solely on my lack of computer expertise. sigh ...

---

### Post by bab1 on 2015-03-12
> **penny3 said:**
> Oh, good Lord! Well, I guess that speaks volumes for the kind of computer competence you are dealing with, eh? (insert blushing smilie face here)

Okay - I did it again with the name that I gave it and still no luck ... 

penny@penny-Satellite-A200:~$ nmblookup <Satellite>
bash: syntax error near unexpected token `newline'
penny@penny-Satellite-A200:~$
More blushing needed.  :-)

The <> are not needed.  ALL terminal command arguments are stand alone.  The <> denote that it is a variable.  The command should be```
nmblookup Satellite
```

---

### Post by penny3 on 2015-03-12
Well, my face is definitely red but don't know if it is from the 'blush' or from the 'frustration' ... I re-did the command again (the RIGHT way this time!) and this is what I got ... 

penny@penny-Satellite-A200:~$ nmblookup Satellite
name_query failed to find name Satellite
penny@penny-Satellite-A200:~$ 

No surprise as I tried to print something out just a few minutes ago and nothing happened. I am off to bed now to ponder the ineptitude of the elderly and if this OS is simply to much for this old brain to handle. I may be relegated to grumbling and b**ching about the Microsoft monopoly again after all ... or, even worse, do a complete system restore to factory settings and start from scratch again. 

Thank you so much for all your help, BAB1. It has been greatly appreciated.

---

### Post by bab1 on 2015-03-12
> **penny3 said:**
> Well, my face is definitely red but don't know if it is from the 'blush' or from the 'frustration' ... I re-did the command again (the RIGHT way this time!) and this is what I got ... 

penny@penny-Satellite-A200:~$ nmblookup Satellite
name_query failed to find name Satellite
penny@penny-Satellite-A200:~$ 

No surprise as I tried to print something out just a few minutes ago and nothing happened. I am off to bed now to ponder the ineptitude of the elderly and if this OS is simply to much for this old brain to handle. I may be relegated to grumbling and b**ching about the Microsoft monopoly again after all ... or, even worse, do a complete system restore to factory settings and start from scratch again. 

Thank you so much for all your help, BAB1. It has been greatly appreciated.
Age is not the problem here.  I'm in my late 60's myself.  Experience with the "Linux way" is more like it.  I assumed a certain level of experience.  This is why Microsoft and Apple exist.  I've found that most of the time it is either "Time or Money".  Everyone has to start at the beginning when learning this stuff.

My guess is that you have NOT configured Samba to have an appropriate NETBIOS name.  You don't have to reinstall Samba.  There is only one file to configure and that is the /etc/samba/smb.conf file.

You can post the contents of that file so we can see what needs to be fixed.  Post the output of this command```
cat /etc/samba/smb.conf > Desktop/smb.txt
```...This puts a copy of the smb.conf file on your desktop.  The file is named smb.txt.

You can post the contents here by using clicking on the [SIZE=6] **#** [/SIZE] icon and pasting the contents in between the [noparse]```
 
```[/noparse]  blocks in the advanced reply editor.   An alternative is to just post the smb.txt file as an attachment.

---

### Post by penny3 on 2015-03-12
Thanks for the words of encouragement. Here is the info ... 

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
netbios name = Satellite

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

### Post by bab1 on 2015-03-12
> **penny3 said:**
> Thanks for the words of encouragement. Here is the info ... 

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
netbios name = Satellite

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

The file looks clean. The only change is the one we made.  You also learned to use the code blocks to preserve the fixed width font formatting of text files; yea!  :-)

I assume that the machine was turned off last night and restarted this morning.  If so post using code blocks the output of **smbtree -d3 **again.  Remember that sometimes that failure leads use to the correct answer.

---

### Post by penny3 on 2015-03-12
Well, I'm relieved to hear that the file looks clean. Here is the further info ...

```
penny@penny-Satellite-A200:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.1.218 bcast=192.168.1.255 netmask=255.255.255.0
Enter penny's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f81065c8950] mpx_fde[(nil)] fd[7] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f81065c8900] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f81065c8890] mpx_fde[(nil)] fd[7] - disabling
penny@penny-Satellite-A200:~$ 

```

---

### Post by bab1 on 2015-03-12
Not what I expected this morning.  :-(

Let's try another test.  Post the output of this command```
sudo pgrep -l mbd
```... this is asking to list all running processes the have "mbd" in them.  It should list smbd (2) and nmbd (1).

---

### Post by penny3 on 2015-03-12
I knew that sooner or later I would see that 'unhappy' smilie face ... lol. 

Here is the output of that latest command:

penny@penny-Satellite-A200:~$ sudo pgrep -l mbd
[sudo] password for penny: 
670 smbd
986 smbd
1364 nmbd
penny@penny-Satellite-A200:~$

---

### Post by bab1 on 2015-03-12
> **penny3 said:**
> I knew that sooner or later I would see that 'unhappy' smilie face ... lol. 

Here is the output of that latest command:

```
penny@penny-Satellite-A200:~$ sudo pgrep -l mbd
[sudo] password for penny: 
670 smbd
986 smbd
1364 nmbd
penny@penny-Satellite-A200:~$
```

All this text from the terminal should between the code blocks we talked about.   It's a good habit as it preserves the formatting of the text (see above).

After re-reading your first post I'm wondering if the response that you are getting is not normal.  After all, you are not sharing anything with Samba so there is no reason as a Samba client that you would be looking for yourself with this Ubuntu host.  On the other hand the machine that is acting as a print server should be available to your print configuration routine on the Ubuntu machine.

I have no trouble configuring my Ubuntu hosts via System Settings >> Printer >> Add >> Network Printer.  I don't use Samba for sharing printers at all.  How did you configure the print services originally?

---

### Post by penny3 on 2015-03-13
I will remember to do the code blocks in the future. This seemed so short that I didn't think it mattered as much. 

I originally configured the printer via the same Printer / Add / Network Printer and used the same information that I used in Windows. The really weird thing is that I was printing with no problems at all until early this week when it suddenly stopped working. I am at a loss ... I will try deleting the printer and re-adding and see if that solves anything.

---

### Post by bab1 on 2015-03-13
> **penny3 said:**
> I will remember to do the code blocks in the future. This seemed so short that I didn't think it mattered as much. 

I originally configured the printer via the same Printer / Add / Network Printer and used the same information that I used in Windows. The really weird thing is that I was printing with no problems at all until early this week when it suddenly stopped working. I am at a loss ... I will try deleting the printer and re-adding and see if that solves anything.
I think as a matter of diagnosis and there is a need to eliminate or confirm that this is correct.  If not we really can't eliminate this as mis-configured regardless of how it got that way.

As to the first point; the forum is also a resource base of commands and fixes for future users.  I think of placing ALL text from the terminal in [noparse]```

``` [/noparse] blocks as a matter of following a style guide.  Thus future readers will be able to use the resource without having to read every line as closely as you and I would need to.

---

### Post by Bucky Ball on 2015-03-13
*Thread moved to **Networking & Wireless**.*

---

### Post by JeQhdMD on 2015-03-13
Rather than uninstalling & resinstalling the printer, it may be better to try an uninstall & resinstall of Samba first . . . If you download and install the "synaptic" package manager (the software manager used before the really dumbed-down Ubuntu Software Center), you can "entirely remove or purge" samba via Synaptic.   It would also be a good idea to intall the graphical front-end for Samba "system-config samba" and/or "gadmin-samba".   Those make it somewhat easier to edit samba than all the command line stuff (not so great for newbies).

You may not even need to use the gui front end tools for Samba after the reinstall . . . the first step should just be to see if you can see & access your network printer via the Files program (aka nautilus).   If can, then try to print again.

Another way to print to the canon is via Google Chrome (or Chromium) browsers.   The preferred method is of course wireless print (which is HIGHLY practical and simple) . . . . OR . . . . to use the Google settings manager in the browser (of the PC that the printer is physically attached to via USB) . . . . . You basically register the printer and Google will then be able to find it IF you use Chrome (or Chromium) on your other PC's.   Kind of a secondary network (making use of the PC IP as the gateway to the printer).   If you search on "Google Cloud Print" . . . you can find how to do this setup for printers that are not "Cloud Enabled" (e.g., wireless equipped).

---

### Post by bab1 on 2015-03-13
> **JeQhdMD said:**
> Rather than uninstalling & resinstalling the printer, it may be better to try an uninstall & resinstall of Samba first . . . If you download and install the "synaptic" package manager (the software manager used before the really dumbed-down Ubuntu Software Center), you can "entirely remove or purge" samba via Synptic.   It would also be a good idea to intall the graphical front-end for Samba "system-config samba" and/or "gamin-samba".   Those make it somewhat easier to edit samba with all the command line stuff (not so great for newbies).

You may not even need to use the gui front end tools for Samba after the reinstall . . . the first step should just be to see if you can see & access your network printer via the Files program (aka nautilus).   If can, then try to print again.

This is absolutely horrible advice on many levels.  First Samba (the server) is not installed presently in the OP's machine.  Only the default Samba client.  There are HUGE problems with * "system-config samba" and/or "gamin-samba"* particularly in the light of the OP not sharing any files.  Second, there is nothing to configure!  The OP is using a Windows machine as the print server.
> 
Another way to print to the canon is via Google Chrome (or Chromium) browsers.   The preferred method is of course wireless print (which is HIGHLY practical and simple) . . . . OR . . . . to use the Google settings manager in the browser (of the PC that the printer is physically attached to via USB) . . . . . to register the printer and Google will then be able to find it IF you use Chrome (or Chromium) on your other PC's.   Kind of a secondary network (making use of the PC IP as the gateway to the printer).   If you search on "Google Cloud Print" . . . you can find how to do this setup for printers that are not "Cloud Enabled" (e.g., wireless equipped).You don't need Google Chrome to do this.  It's called  Internet Printing Protocol (IPP).

---

### Post by JeQhdMD on 2015-03-13
I am familiar with IPP and have it set up via the Ubuntu network tools (as included in add printer).   I do not advocate installing the server, but perhaps the default client config is messed up.   Is it not doable to reinstall the client?   The gui admin tools are not perfect, but sometimes these are easier to work with than the cli.   If memory serves me right, one or both of the gui's also have a tab for printer config (but it's been 4 years or so since I last used . . . at home, I have zero need for samba as dropbox and cloud print do what I need).    The direction I'd like Penny to try is cloud print via the pretty well designed google web tools.   

But . . . if the functionality she has already had can be done via the samba config file tweaks, I hope it works out.   Whatever method works is great.  There is always the "sneaker-net" network . . . . ;)

---

### Post by penny3 on 2015-03-13
For a variety of reasons, trying to print the 'Google' way is not feasible here. I am either going to have to try and figure out what went wrong on my computer or accept that Ubuntu just isn't the OS for me after all. Which I will spend a great deal of time thinking about over the weekend. As mentioned before, I don't understand why it was working absolutely fine to start and then ... boom! Nothing. I do appreciate all the suggestions though!

---

### Post by penny3 on 2015-03-14
Hmm ... another glitch. Just tried to upload some photos from my camera to the Shotwelln app (which worked perfectly last week as well) and it isn't working either. I am going to do a factory reset on the laptop and try a whole new install - probably.  I just don't know what is going on or what I am doing for even the simple things to stop working like this. A big thank-you to all who have tried to help me. I really appreciate it!

---

### Post by Bucky Ball on 2015-03-14
Once you've done that and tweaked it to your liking, [clone]("http://clonezilla.org/") it. That way, you can install a working system with all your settings quickly. ;)

Good luck.

---

