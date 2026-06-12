---
title: "Samba installed but will not launch"
date: 2016-04-28
forum: Networking &amp; Wireless
---

### Post by pat4 on 2016-04-28
I have installed Samba on 16.04 [sudo apt-get install samba]  together with the GUI configuration tool  [sudo apt-get install system-config-samba]
I now have an icon in launcher.  Clicking the icon brings up a password box. I enter my password then nothing happens. Samba does not open

I have installed this earlier this week on my laptop - also running 16.04 - without problem. 

I accept that configuring Samba  can be problematic but so far I can't get into the setup box to allow me to configure it. I am also aware that some changes may have to be made to the conf file . I can open that in gedit no problem. 

I have tried uninstall / reinstall but that made no difference. 

Can anyone help point me at some way of getting samba to open?

Thanks  Pat.

---

### Post by ken76 on 2016-04-28
I know this is no help to you at all, pat4, but I feel your pain! I'm in exactly the same situation - i.e. running Xubuntu 16.04 (32-bit version) and going mad trying to make anything visible to my other machines. Samba does the same thing to me: asks for my password and then does nothing at all.

I've got the following packages onboard:

samba
system-config-samba
vsftpd
gksu

...and I've read numerous step-by-step guides and tried out various other advice on how to get things working (most of which, alas, is based on earlier versions of Xubuntu), but so far no dice, so I'll be watching this thread with interest.

It's a real shame, because otherwise I was really starting to like Xubuntu.  This experience makes me wish I'd chosen a different distro now... :(

I don't suppose this info is relevant, but I'm dual-booting with Win7 on an Acer Aspire V3-731 laptop

---

### Post by pat4 on 2016-04-28
Hello Ken76
Thanks for your reply... 
I haven't even got around to making stuff visible. I just wish I could get the Samba config screen to load onto the desktop.
I get to the point of inputting the password, click OK then.. nothing.

I have set up Samba shares in the past and although fiddly, I have managed to set up a home network / file sharing system involving Ubuntu and Windoze machines. 

Daft thing is that I have exactly the same setup on my laptop - 16.04 with Samba - and have no problem accessing files.

Kind regards,  Pat.

---

### Post by mikewhatever on 2016-04-28
Ken, please post your problem, this is a Help and Support, not a pain feeling forum.

Pat, what happens if you try <sudo -H system-config-samba>?

---

### Post by T.J. on 2016-04-28
I would never use a new release of Ubuntu for anything other than testing it.

Ubuntu is usually based on the Debian Unstable (or Debian Testing for an LTS release).  That means that Ubuntu copies the buggiest, unreleased versions of Debian for each Ubuntu release.  Canonical only officially supports a few thousand packages out of Debian's 44,000+ repository.  That means that what can happen is that you get a buggy package with little or no support, until it is patched by Debian upstream, and then recopied into an Ubuntu update.  Since Debian takes things slowly and carefully to release a quality product, it might be some time before a patch makes its way into Debian Testing from Debian Unstable.  You might be waiting some time for a patch.

I'm not trying to annoy or cast disputations at  Ubuntu, but that is essentially the situation.

I've found that I can configure Samba far more easily with a text editor.  I'd be happy to help you configure your service properly.  As a token of goodwill, I am including my configuration as an example: 


/etc/samba/smb.conf

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

[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# The following parameter makes sure that only "username" can connect
# to \\server\username
# This might need tweaking when using external authentication schemes
   valid users = %S

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

[Shared]
   comment = Shared Folder
   path = /home/tj/Shared
   browseable = yes
   read only = no
   valid user = @tj


```

---

### Post by ken76 on 2016-04-28
> **mikewhatever said:**
> Ken, please post your problem, this is a Help and Support, not a pain feeling forum.Merely letting the OP know that their issue is not unique to them - relevant information, I would have thought.

FWIW, I've just tried <sudo -H system-config-samba> and got the following:

[COLOR=#800000]Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 45, in <module>
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 121, in __init__
    self.basic_preferences_win = basicPreferencesWin.BasicPreferencesWin(self, self.xml, self.samba_data, self.samba_backend, self.main_window)
  File "/usr/share/system-config-samba/basicPreferencesWin.py", line 97, in __init__
    self.admin = libuser.admin()
SystemError: could not open configuration file `/etc/libuser.conf': No such file or directory[/COLOR]

---

### Post by Morbius1 on 2016-04-28
Um ...... try running it from the terminal like I did. You may be missing a file:

> tester@vub1604:~$ gksu system-config-samba
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 121, in __init__
    self.basic_preferences_win = basicPreferencesWin.BasicPreferencesWin(self, self.xml, self.samba_data, self.samba_backend, self.main_window)
  File "/usr/share/system-config-samba/basicPreferencesWin.py", line 97, in __init__
    self.admin = libuser.admin()
[COLOR=#0000cd]SystemError: could not open configuration file `/etc/libuser.conf': No such file or directory[/COLOR]
tester@vub1604:~$ [COLOR=#0000cd]**sudo touch /etc/libuser.conf**[/COLOR]
[sudo] password for tester: 
tester@vub1604:~$ gksu system-config-samba
Now it opens

EDIT:
(1) Did not see the previous post. Sorry
(2) system-config-samba hasn't been updated since the Korean War and at least one of it's options hasn&#8217;t been relevant since Version 3 ( or maybe 2 ) of Samba so it either needs to be rewritten which is not likely or just removed from the repository.

---

### Post by ken76 on 2016-04-28
Morbius1, many thanks for your help - it opens for me now, too. :smile:

---

### Post by pat4 on 2016-04-29
All,
Thank you for your replies...  I will try and answer points made within.

T.J....  Thanks for your insight and the offer of help with the .conf file.  Unfortunately, I don't consider myself sufficiently well versed in  Ubuntu yet to delve too deeply into such files. I am learning fast but  don't consider myself competent enough at this time.

Ken76.. Good to know that I'm not the only one with the problem.

Mikewhatever  & Morbius 1 ...  Ran the script in terminal, got the error message  documented here by Ken76. A bit of digging led me to a bug page here   [[https://bugs.launchpad.net/ubuntu/+source/libuser/+bug/214959]](https://bugs.launchpad.net/ubuntu/+source/libuser/+bug/214959])     and  after some small amount of research
I ran   sudo touch /etc/libuser.conf   which launched the programme.  It now launches OK when I want it.

I  have to admit that I don't know enough to understand the fix.  I don't  yet know why the fix worked - it is something I need to learn.  

Thank you to all who helped and contributed.

Kind regards,     Pat.

---

