---
title: "Peer to peer network problem"
date: 2016-01-05
forum: Networking &amp; Wireless
---

### Post by williepabon on 2016-01-05
Hi:

I have three machines connected on my home network (wired and Wi Fi). One machine has Ubuntu 14.04 (64 bit), another has Elementary OS (Freya 64 bit) and another Windows 7 Home Premium (64 bit). I wanted to share files between them (peer-to-peer), so I installed Samba on both Linux boxes and configured samba shares on each of them. I also created shares on the  Win 7 machine.This is what happens when I try to access shared directories from one machine to the other.
[INDENT]
1. Browsing network from Elementary OS machine to Ubuntu 14.04[/INDENT]

[LIST]
[*=1]Get the Windows Network folder
[*=1]Double clicking bring the logon to WORKGROUP
[*=1]Entering password is not accepted and I don't get access to shares
[*=1]If I type in the address box the specific location of the Ubuntu box (smb://[ip address]/[directory location]) I get and unhandled error message like, Failed to mount Windows share...
[/LIST]
[INDENT]2. Browsing network from Ubuntu 14.04 to Elementary OS[/INDENT]

[LIST]
[*=1]Get the Windows network folder
[*=1]Double clicking brings the logon box to WORKGROUP
[*=1]Entering password is not accepted and I don't get access to shares.
[*=1]As above, if I type in the address box the specific location of the Ubuntu box (smb://[ip address]/[directory location]) I get and unhandled error message like, Failed to mount Windows share...
[/LIST]
[INDENT]3. Browsing network from Ubuntu 14.04 to Windows 7[/INDENT]

[LIST]
[*=1]Get the Windows network folder
[*=1]Get the Workgroup folder
[*=1]Double clicking brings the icon of the Win7 machine
[*=1]Able to see Win 7 shared directories
[/LIST]
[INDENT]4. Win 7 to Ubuntu 14.04[/INDENT]

[LIST]
[*=1]Win 7 won't see Linux machines and/or shared folders.
[/LIST]
[INDENT][/INDENT]

If it is possible to make a peer-to-peer network to work with these machines, your help will be appreciated. Thanks
wp


[INDENT]

[/INDENT]

---

### Post by bab1 on 2016-01-05
> **williepabon said:**
> If it is possible to make a peer-to-peer network to work with these machines, your help will be appreciated. Thanks
wp

No...

Windows style file sharing is not peer to peer.  Each host needs both client and server software.  The servers on all 3 machines need some configuration to function correctly.

To see if the Samba servers on the Linux machines you can run this command from the terminal```
pgrep -l mbd
```...you should see something like this```
676 smbd
684 smbd
1801 nmbd

```

You should see 2 smbd instances and 1 nmbd instance.

---

### Post by williepabon on 2016-01-05
**BAB1:**

Thanks for answering. This is the  result I get from the command.

williepabon@williepabon-Macmini:~$ pgrep -l mbd
651 smbd
911 smbd
1527 nmbd
williepabon@williepabon-Macmini:~$ 
Sorry my ignorance, but what does the numbers mean?
Really appreciate if you can help in doing this configuration if it is  possible. Thanks.
wp

---

### Post by bab1 on 2016-01-05
> **williepabon said:**
> **BAB1:**

Thanks for answering. This is the  result I get from the command.

williepabon@williepabon-Macmini:~$ pgrep -l mbd
651 smbd
911 smbd
1527 nmbd
williepabon@williepabon-Macmini:~$ 
Sorry my ignorance, but what does the numbers mean?

The numbers are the process ID numbers.  See [**here**]("http://www.linfo.org/pid.html") for more information.
> 
Really appreciate if you can help in doing this configuration if it is  possible. Thanks.
wp
What did you do to configure the host *williepabon-Macmini*?  


Post the output of this command```
cat /etc/samba/smb.conf
```

Post the output using the **[noparse]```
 
```[/noparse]** tags.  This preserves the text formatting and makes it more readable.  The easiest way to do this is to click on the [SIZE=5]**#**[/SIZE] icon at the top of the advanced reply editor and pasting the results inside of the code blocks.  Make it easy for us to help you.

---

### Post by williepabon on 2016-01-05
BAB1:

Thanks again for answering so fast. In answering your question about mac-mini, it is that I run dual-boot a Mac-mini with Ubuntu. There appeared an article a few years ago on how to do it, and I followed the instructions. Following is the information you requested.

```
williepabon@williepabon-Macmini:~$ cat /etc/samba/smb.conf#
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
    workgroup = workgroup


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
;    passdb backend = tdbsam


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
;    usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
    security = share
;    encrypt passwords = yes
;    guest ok = no
;    guest account = nobody


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
;    guest ok = no
;    read only = yes
    create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin


[Christian]
    path = /home/williepabon/Documents/Christian
;    writeable = no
;    browseable = yes
    guest ok = yes


[Documents]
    path = /home/williepabon/Documents
    writeable = yes
;    browseable = yes
    guest ok = yes
williepabon@williepabon-Macmini:~$ 

```

Thanks again for the help.
wp

---

### Post by bab1 on 2016-01-05
Before getting too deep into this we should set some design parameters. 

[I]How many users are going to use this network?  

Do you want to centralize the data (so no data is replicated) ?[/I]

In my mind an ad-hoc (what you called peer-to-peer) sharing situation is useful if the individual users want to temporarily share data with others in a network.   In this type of network the shares are configured by the user (in Samba the shares are called usershares) via the GUI interface in their own home dir (/home/<user>).  

If you want to create the shares as the  administrator (root), usually the data is stored outside of the /home directories.  The standard location is /srv.  See [**here**]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure") for the Linux File System Hierarchy.  

You could have a mix of all of this.  At home I have both user shares (between myself and wife) and a centralized server for the important data that is backed up daily. 

*Do you have a workgroup name preference?*

You should set the workgroup name the same on all of the machines serving files.  You should also explicitly declare the NetBIOS name of each server.  By default the Samba server converts the hostname into the NetBIOS name.  If the hostname is longer than 15 characters Samba chokes.  Your hostname on the Mac Mini is too long (williepabon-Macmini is 19 characters).

Both of these can be declared in the [global] section of the smb.conf file```

...
# 15 characters or less
workgroup = <name>
...
# 15 characters or less
netbios name = <netbiosname>
...
```

In these examples you would substitute you choice of names. 

You should have both a Linux user (adduser) and a Samba user (smbpasswd -a) if you want one of the hosts to be a centralized Samba server that uses user name authentication and authorization of the shares.  With ad-hoc you will have to allow everyone access unless you wish to restrict the share access by setting up a Linux and Samba user setup for each user.

The way to have stable file shares is to configure the environment first, then add the users and then share the data.  The initial design is important.  I have the same basic Samba configuration that I started with in 2008 with Samba v3.  This works with the latest Samba v4.

When you add the users, be consistent with the user names and uid/gid settings.  They should be the same across all the hosts.

Ask questions before you do anything.  I will provide the commands once we have all the design/structure questions answered.

---

### Post by williepabon on 2016-01-06
**bab1**:

In answering your questions: Essentially, one user will be using the network: myself. The reason for the peer-to-peer network is because I have my data, files and documents dispersed on three machines, and I would like to have access to all this data irrespective of the machine I am using at any given time. In other words, I want to be able to work in any of my pcs and have access to the data of the other two. By your advice, I already changed the hostnames of my machines to satisfy the 15 character limit of Samba. I hope that I have given enough information about my setup, so that you may provide help to configure Samba in my two Linux boxes (one with Ubuntu and the other with Elementary OS). Thanks in advance for your help.
wp

---

### Post by bab1 on 2016-01-06
> **williepabon said:**
> **bab1**:

In answering your questions: Essentially, one user will be using the network: myself. The reason for the peer-to-peer network is because I have my data, files and documents dispersed on three machines, and I would like to have access to all this data irrespective of the machine I am using at any given time. In other words, I want to be able to work in any of my pcs and have access to the data of the other two. 

By your advice, I already changed the hostnames of my machines to satisfy the 15 character limit of Samba. I hope that I have given enough information about my setup, so that you may provide help to configure Samba in my two Linux boxes (one with Ubuntu and the other with Elementary OS). Thanks in advance for your help.
wp
Let's focus on the Ubuntu Samba configuration first.
 
[LIST]
[*]Do have a common data store for the files on this dual boot machine?
[*]How did you change the hostname?  
[/LIST]
Post the output of these 2 terminal commands```
cat /etc/hostname

cat /etc/hosts
```

What is your username the Ubuntu host?  

Post the output of these 2 commands```

# Linux users
getent passwd | grep 100

# samba users
sudo pdbedit -L
```

Is the previous post of the smb.conf from the Ubuntu host (not OSX)?  

Post output of this command if you modified the file```
cat /etc/samba/smb.conf
```

---

### Post by williepabon on 2016-01-06
bab1:

Will try to answer your questions to the best of my knowledge.


[LIST]
[*]Do have a common data store for the files on this dual boot machine?
No.
[*]How did you change the hostname?
Editing the files that you mention in your code and then restarting the machine
[/LIST]

Here's the output of the code:

```
williepabon@WP-Macmini:~$ cat /etc/hostnameWP-Macmini
williepabon@WP-Macmini:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    WP-Macmini


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
williepabon@WP-Macmini:~$ 

```

Another problem came up this morning that might put a challenge to your help. For reasons that I don't understand, Samba crashed and stopped working. I tried to remove/reinstall using Synaptics, but that didn't work. I can double click the Samba icon but the GUI doesn't show and there is no evidence in the processes that samba server is up. Probably that is why I get the following output you requested.

```
williepabon@WP-Macmini:~$ sudo pdbedit -L[sudo] password for williepabon: 
WARNING: Ignoring invalid value 'share' for parameter 'security'
tdbsam_open: Failed to open/create TDB passwd [/var/lib/samba/private/passdb.tdb]
tdbsam_getsampwnam: failed to open /var/lib/samba/private/passdb.tdb!
User Search failed!


williepabon@WP-Macmini:~$ getent passwd | grep 100
libuuid:x:100:101::/var/lib/libuuid:
williepabon:x:1000:1000:William Pabon,,,:/home/williepabon:/bin/bash
gaelgabriel:x:1001:1001:Gael Gabriel,,,:/home/gaelgabriel:/bin/bash
```

Now, I need to find out how to do a clean install of Samba (as if it never existed before) before I can proceed further.
Your last question,
[COLOR=#000000]Is the previous post of the smb.conf from the Ubuntu host (not OSX)?
The smb.conf is from Ubuntu host. I am not working with OSX on this machine for this project. So, the smb.conf should have not changed. Don't know if the crash might have affected it. Here's the output:

[/COLOR]```
williepabon@WP-Macmini:~$ cat /etc/samba/smb.conf#
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
    workgroup = workgroup


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
;    passdb backend = tdbsam


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
;    usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
    security = share
;    encrypt passwords = yes
;    guest ok = no
;    guest account = nobody


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
;    guest ok = no
;    read only = yes
    create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin


[Christian]
    path = /home/williepabon/Documents/Christian
    writeable = yes
;    browseable = yes
    guest ok = yes


[Documents]
    path = /home/williepabon/Documents
    writeable = yes
;    browseable = yes
    guest ok = yes
williepabon@WP-Macmini:~$ 


```
[COLOR=#000000]Thanks again for your effort.
wp

[/COLOR]

---

### Post by bab1 on 2016-01-06
> **williepabon said:**
> ...

Another problem came up this morning that might put a challenge to your help. For reasons that I don't understand, Samba crashed and stopped working. I tried to remove/reinstall using Synaptics, but that didn't work. I can double click the Samba icon but the GUI doesn't show and there is no evidence in the processes that samba server is up. .

What "Samba Icon" are you referring to?  Are you referring to the samba-config tool?
> 
Probably that is why I get the following output you requested
```
williepabon@WP-Macmini:~$ sudo pdbedit -L[sudo] password for williepabon: 
WARNING: Ignoring invalid value 'share' for parameter 'security'
tdbsam_open: Failed to open/create TDB passwd [/var/lib/samba/private/passdb.tdb]
tdbsam_getsampwnam: failed to open /var/lib/samba/private/passdb.tdb!
User Search failed!

Maybe, but then again maybe not!  The response has revealed 2 things.

The first thing is that you have modified the smb.conf file incorrectly for usershares.  In the [global] section you misconfigured the following
[CODE]# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
[B][COLOR="#FF0000"]    security = share
;    encrypt passwords = yes
;    guest ok = no
;    guest account = nobody[/COLOR][/B]
```
...if you removed the part highlighted in **[COLOR="#FF0000"]red[/COLOR]** it would have removed the first error (invalid value).

The second error is far more serious.  It is possible that nothing existed in the /var/lib/samba directory.
> 
```
williepabon@WP-Macmini:~$ getent passwd | grep 100
libuuid:x:100:101::/var/lib/libuuid:
williepabon:x:1000:1000:William Pabon,,,:/home/williepabon:/bin/bash
gaelgabriel:x:1001:1001:Gael Gabriel,,,:/home/gaelgabriel:/bin/bash
```

This is good.
> 
Now, I need to find out how to do a clean install of Samba (as if it never existed before) before I can proceed further.
I would uninstall with this```
sudo apt-get purge samba
```...then reinstall with this```
sudo apt-get install samba
```
Once you have Samba installed; STOP!  Don't add anything else.  We only need to do some minor modifications to the smb.conf file with a text editor.
> Your last question,
*Is the previous post of the smb.conf from the Ubuntu host (not OSX)?*
The smb.conf is from Ubuntu host. I am not working with OSX on this machine for this project. So, the smb.conf should have not changed. Don't know if the crash might have affected it.
[COLOR=#000000]Thanks again for your effort.
wp
[/COLOR]
The crash won't change the smb.conf file.  I think the best course of action is for you to reinstall and then post the output from the following commands```
ls -l /etc/samba

ls -l /var/lib/samba
```

Then we can start with the configuration.

---

### Post by williepabon on 2016-01-06
bab1:

Thanks for your help, really. Yes, the icon I am referring to is for the samba-config tool. I already purged and re-installed Samba using your commands. This is the output of the commands you requested.

```
williepabon@WP-Macmini:~$ ls -l /etc/sambatotal 32
-rw-r--r-- 1 root root    8 Apr  3  2014 gdbcommands
-rw-r--r-- 1 root root 9788 Jan  6 09:59 smb.conf
-rw-r--r-- 1 root root 9542 Jan  6 06:54 smb.conf.ucf-dist
-rw-r--r-- 1 root root    0 Jan  6 09:55 smbusers
drwxr-xr-x 2 root root 4096 Apr  3  2014[COLOR=#3333cc]tls[/COLOR]
williepabon@WP-Macmini:~$ ls -l /var/lib/samba
total 8
drwxr-xr-x 10 root root       4096 Jan  6 19:47 [COLOR=#3333cc]printers[/COLOR]
drwxrwx--T  2 root sambashare 4096 Jan  6 19:47 [COLOR=#3333cc]usershares[/COLOR]
williepabon@WP-Macmini:~$ 



```

Will wait until further advice. Thanks.
wp

---

### Post by bab1 on 2016-01-06
> **williepabon said:**
> bab1:

Thanks for your help, really. Yes, the icon I am referring to is for the samba-config tool. I already purged and re-installed Samba using your commands. This is the output of the commands you requested.

```
williepabon@WP-Macmini:~$ ls -l /etc/sambatotal 32
-rw-r--r-- 1 root root    8 Apr  3  2014 gdbcommands
-rw-r--r-- 1 root root 9788 Jan  6 09:59 smb.conf
-rw-r--r-- 1 root root 9542 Jan  6 06:54 smb.conf.ucf-dist
-rw-r--r-- 1 root root    0 Jan  6 09:55 smbusers
drwxr-xr-x 2 root root 4096 Apr  3  2014[COLOR=#3333cc]tls[/COLOR]
williepabon@WP-Macmini:~$ ls -l /var/lib/samba
total 8
drwxr-xr-x 10 root root       4096 Jan  6 19:47 [COLOR=#3333cc]printers[/COLOR]
drwxrwx--T  2 root sambashare 4096 Jan  6 19:47 [COLOR=#3333cc]usershares[/COLOR]
williepabon@WP-Macmini:~$ 



```

Will wait until further advice. Thanks.
wp
Let's start simple.  The smbd and nmbd daemons should be running.  Let's check that.  Post the output of this command```
pgrep -l mbd
```...this should show the 2 smbd and 1 nmbd daemon (processes) running.

I don't see the /var/lib/samba/private directory, but I believe Samba will make it when we need it.  Lets add you to the Samba database with this command```
sudo smbpasswd -a <your_user_name>
```...use your Ubuntu username for the <your_user_name>.  When prompted, also use your Ubuntu password.  Then post the output of this```
sudo pdbedit -L
```

If you get errors, do not do anything to correct it, just post the errors back here.

---

### Post by williepabon on 2016-01-06
**bab1:**

Here's the output of the requested commands.

```
williepabon@WP-Macmini:~$ pgrep -l mbd1649 nmbd
williepabon@WP-Macmini:~$ sudo smbpasswd -a williepabon
[sudo] password for williepabon: 
WARNING: Ignoring invalid value 'share' for parameter 'security'
Failed to open /var/lib/samba/private/secrets.tdb
williepabon@WP-Macmini:~$ 
williepabon@WP-Macmini:~$ sudo pdbedit -L
WARNING: Ignoring invalid value 'share' for parameter 'security'
tdbsam_open: Failed to open/create TDB passwd [/var/lib/samba/private/passdb.tdb]
tdbsam_getsampwnam: failed to open /var/lib/samba/private/passdb.tdb!
User Search failed!
williepabon@WP-Macmini:~$ 



```

wp

---

### Post by bab1 on 2016-01-06
> **williepabon said:**
> **bab1:**

Here's the output of the requested commands.

```
williepabon@WP-Macmini:~$ pgrep -l mbd
1649 nmbd

williepabon@WP-Macmini:~$ sudo smbpasswd -a williepabon
[sudo] password for williepabon:
 
WARNING: Ignoring invalid value 'share' for parameter 'security'
Failed to open /var/lib/samba/private/secrets.tdb
williepabon@WP-Macmini:~$ 
williepabon@WP-Macmini:~$ sudo pdbedit -L
WARNING: Ignoring invalid value 'share' for parameter 'security'
tdbsam_open: Failed to open/create TDB passwd [/var/lib/samba/private/passdb.tdb]
tdbsam_getsampwnam: failed to open /var/lib/samba/private/passdb.tdb!
User Search failed!
williepabon@WP-Macmini:~$ 



```

wp
Interesting.  The smbd daemon is not running at this time.  I also notice that that original smb.conf file is being used!  See if you can start smbd with this command```
sudo service smbd start
```

Let's see what is in the smb.conf file.  Post the output of this```
cat /etc/samba/smb.conf
```

Let's also see what it in the smb.conf.ucf-dist file.  Post the output of this ```
cat /etc/samba/smb.conf.ucf-dist
```

I want you to add a directory at /var/lib/samba with this command```
sudo mkdir /var/lib/samba/private
```...check it and post the output with this command```
ls -l /var/lib/samba
```

---

### Post by williepabon on 2016-01-06
***bab1:***

Here are the outputs requested.

```
williepabon@WP-Macmini:~$ sudo service smbd start[sudo] password for williepabon: 
smbd start/running, process 6851
williepabon@WP-Macmini:~$ 
williepabon@WP-Macmini:~$ 



```

I couldn't find the above process in the system monitor process list.

```
williepabon@WP-Macmini:~$ cat /etc/samba/smb.conf#
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
    workgroup = workgroup


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
;    passdb backend = tdbsam


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
;    usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
    security = share
;    encrypt passwords = yes
;    guest ok = no
;    guest account = nobody


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
;    guest ok = no
;    read only = yes
    create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin


[Christian]
    path = /home/williepabon/Documents/Christian
    writeable = yes
;    browseable = yes
    guest ok = yes


[Documents]
    path = /home/williepabon/Documents
    writeable = yes
;    browseable = yes
    guest ok = yes
williepabon@WP-Macmini:~$ 



```


```
williepabon@WP-Macmini:~$ cat /etc/samba/smb.conf.ucf-dist#
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
   workgroup = workgroup


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


williepabon@WP-Macmini:~$ 



```

```
williepabon@WP-Macmini:~$ sudo mkdir /var/lib/samba/private[sudo] password for williepabon: 
williepabon@WP-Macmini:~$ ls -l /var/lib/samba
total 12
drwxr-xr-x 10 root root       4096 Jan  6 19:47 printers
drwxr-xr-x  2 root root       4096 Jan  6 21:26 private
drwxrwx--T  2 root sambashare 4096 Jan  6 19:47 usershares
williepabon@WP-Macmini:~$ 



```

wp

---

### Post by bab1 on 2016-01-06
> **williepabon said:**
> ***bab1:***

Here are the outputs requested.

```
williepabon@WP-Macmini:~$ sudo service smbd start[sudo] password for williepabon: 
smbd start/running, process 6851
williepabon@WP-Macmini:~$ 
williepabon@WP-Macmini:~$ 

```
I couldn't find the above process in the system monitor process list.

What do you get with either of these 
```
pgrep -l mbd

ps -ef|grep mbd

```
Clearly the samba process is running.  The PID is 6851 

I can see that Samba is using the original smb.conf file.  Let's change that.  Rename the smb.conf file to smb.conf.bak with this command```
sudo mv /etc/samba/smb.conf  /etc/samba/smb.conf.bak
```
Then rename the smb.conf.ucf-dist file to smb.conf with this command```
sudo mv /etc/samba/smb.conf.ucf-dist  /etc/samba/smb.conf
```
Check your work and post the output with this command```
ls -l /etc/samba
```
Make Samba use the new smb.conf configuration with this command```
sudo service smbd restart
```...note the new PID.
> 

```
williepabon@WP-Macmini:~$ sudo mkdir /var/lib/samba/private[sudo] password for williepabon: 
williepabon@WP-Macmini:~$ ls -l /var/lib/samba
total 12
drwxr-xr-x 10 root root       4096 Jan  6 19:47 printers
drwxr-xr-x  2 root root       4096 Jan  6 21:26 private
drwxrwx--T  2 root sambashare 4096 Jan  6 19:47 usershares
williepabon@WP-Macmini:~$ 

```

Great.  Try again to add your user to the Samba user database with the smbpaasswd command```
sudo smbpasswd -a <user>
```...post the output of any errors.  If none then post the output of ```
sudo pdbedit -L
```


[COLOR="#0000FF"]**Edit:  Above I had a typo which I have corrected.  The command I corrected was ```
*sudo mv /etc/samba/smb.conf    /etc/samba/smb.conf.bak*
```  I changed /etc/samba/smb.conf/bak to /etc/samba/smb.conf.bak.  Sorry for the miscue.**[/COLOR]

---

### Post by williepabon on 2016-01-07
bab1:

Good day! Well, for me is a new day (1/7/2016). turned on my pc and today the three samba processes are running.
nmbd---1436
smbd---644
smbd---1557

Now, performing your code instructions.

```
williepabon@WP-Macmini:~$ pgrep -l mdbwilliepabon@WP-Macmini:~$ ps -ef|grep mdb
williep+  3784  3769  0 09:49 pts/0    00:00:00 grep --color=auto mdb

```

The file renames, etc follows.

```
williepabon@WP-Macmini:~$ sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak[sudo] password for williepabon: 
williepabon@WP-Macmini:~$ sudo mv /etc/samba/smb.conf.ufc-dist /etc/samba/smb.conf
mv: cannot stat ‘/etc/samba/smb.conf.ufc-dist’: No such file or directory
williepabon@WP-Macmini:~$ sudo mv /etc/samba/smb.conf.ucf-dist /etc/samba/smb.conf
williepabon@WP-Macmini:~$ ls -l /etc/samba
total 32
-rw-r--r-- 1 root root    8 Apr  3  2014 gdbcommands
-rw-r--r-- 1 root root 9542 Jan  6 06:54 smb.conf
-rw-r--r-- 1 root root 9788 Jan  6 09:59 smb.conf.bak
-rw-r--r-- 1 root root    0 Jan  6 09:55 smbusers
drwxr-xr-x 2 root root 4096 Apr  3  2014 tls
williepabon@WP-Macmini:~$ sudo service smbd restart
smbd stop/waiting
smbd start/running, process 4749
williepabon@WP-Macmini:~$ 
williepabon@WP-Macmini:~$ sudo smbpasswd -a williepabon
New SMB password:
Retype new SMB password:
Added user williepabon.
williepabon@WP-Macmini:~$ 

```

Creating a user in the Samba database is shown above. Verifying user created.

```
williepabon@WP-Macmini:~$ sudo pdbedit -L[sudo] password for williepabon: 
williepabon:1000:William Pabon
williepabon@WP-Macmini:~$ 

```

Thanks. Now waiting for further instructions.
wp

---

### Post by bab1 on 2016-01-07
> **williepabon said:**
> bab1:

Good day! Well, for me is a new day (1/7/2016). turned on my pc and today the three samba processes are running.
nmbd---1436
smbd---644
smbd---1557

Now, performing your code instructions.

```
williepabon@WP-Macmini:~$ pgrep -l mdb

williepabon@WP-Macmini:~$ ps -ef|grep mdb
williep+  3784  3769  0 09:49 pts/0    00:00:00 grep --color=auto mdb

```

Computers are unforgiving things.  The argument (term we are searching for) is: mbd not mdb.  That's why you have no meaningful output.  No harm though, it looks like the system is working fine today.  :D
> 


The file renames, etc follows.

```
williepabon@WP-Macmini:~$ sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
[sudo] password for williepabon: 

williepabon@WP-Macmini:~$ sudo mv /etc/samba/smb.conf.ufc-dist /etc/samba/smb.conf
mv: cannot stat ‘/etc/samba/smb.conf.ufc-dist’: No such file or directory

williepabon@WP-Macmini:~$ sudo mv /etc/samba/smb.conf.ucf-dist /etc/samba/smb.conf

williepabon@WP-Macmini:~$ ls -l /etc/samba
total 32
-rw-r--r-- 1 root root    8 Apr  3  2014 gdbcommands
-rw-r--r-- 1 root root 9542 Jan  6 06:54 smb.conf
-rw-r--r-- 1 root root 9788 Jan  6 09:59 smb.conf.bak
-rw-r--r-- 1 root root    0 Jan  6 09:55 smbusers
drwxr-xr-x 2 root root 4096 Apr  3  2014 tls

williepabon@WP-Macmini:~$ sudo service smbd restart
smbd stop/waiting
smbd start/running, process 4749

williepabon@WP-Macmini:~$ 
williepabon@WP-Macmini:~$ sudo smbpasswd -a williepabon
New SMB password:
Retype new SMB password:
Added user williepabon.
williepabon@WP-Macmini:~$ 

```

Creating a user in the Samba database is shown above. Verifying user created.

```
williepabon@WP-Macmini:~$ sudo pdbedit -L
[sudo] password for williepabon: 
williepabon:1000:William Pabon
williepabon@WP-Macmini:~$ 

```

Thanks. Now waiting for further instructions.
wp
At this point all you need to do is add a share definition at the bottom of the smb.conf file.  For this we need to open a text editor as the root user.  To open the file use this command```
sudo nano /etc/samba/smb.conf
```...no typo's at this point.  You are editing the Samba config file.  You should see the nano commands at the bottom of the terminal.  They will look like this
```
^G Get Help    ^O WriteOut    ^R Read File   ^Y Prev Page   ^K Cut Text    ^C Cur Pos
^X Exit        ^J Justify     ^W Where Is    ^V Next Page   ^U UnCut Text  ^T To Spell

```...the ^ character stands for the "Ctrl" (control) button.  The one that is important is the  **^x**.  This will prompt you to save the file and exit when you are done.

So with the nano editor open add this to the bottom of the /etc/samba/smb.conf file```

[Documents]
        comment = Documents Directory
        path = /home/williepabon/Documents
        browseable = yes
        guest ok = yes
        force user = williepabon
        writeable = yes
        create mask = 0664
        directory mask = 0775

```
This should share the Documents directory in your home directory.  Any user will be able to access the data and modify it but you will always be the owner and have read/write permissions.

Before we finalize it, I want to see what you have done.  Post the output of this command ```
cat /etc/samba/smb.conf
```...the share definition should be at the bottom.

---

### Post by williepabon on 2016-01-07
bab1:

Ok. Sorry about the typo in the command. Its the age (dislexia):oops: . Here's the code.

```
williepabon@WP-Macmini:~$ cat /etc/samba/smb.conf#
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
   workgroup = workgroup


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


[Documents]
    comment = Documents Directory
    path = /home/williepabon/Documents
    browseable = yes
    guest ok = yes
    force user = williepabon
    writeable = yes
    create mask = 0664
    directory mask = 0775


williepabon@WP-Macmini:~$ 



```

I guess I have a couple of questions. One: Is it OK to use (for us not too familiar CLI operations) the samba system-config tool (GUI) to manage shares, or there are objections to its use? Two: As you know, I have a Win7 pc on the network. Is there a similar procedure to make my windows machine to access Linux shares? Yes, I already tested that I can access windows shares from Linux. Thanks again for the help.

Awaiting for further instructions.
wp

---

### Post by bab1 on 2016-01-07
> **williepabon said:**
> bab1:

Ok. Sorry about the typo in the command. Its the age (dislexia):oops: .

I mentioned it only for you to see how precise you need to be with these commands.  ;-)
> 
Here's the code.
```

...
[Documents]
    comment = Documents Directory
    path = /home/williepabon/Documents
    browseable = yes
    guest ok = yes
    force user = williepabon
    writeable = yes
    create mask = 0664
    directory mask = 0775

williepabon@WP-Macmini:~$ 

```

I guess I have a couple of questions. One: Is it OK to use (for us not too familiar CLI operations) the samba system-config tool (GUI) to manage shares, or there are objections to its use? Two: As you know, I have a Win7 pc on the network. Is there a similar procedure to make my windows machine to access Linux shares? Yes, I already tested that I can access windows shares from Linux. Thanks again for the help.

Awaiting for further instructions.
wp
The code looks great.  The final step is to restart the smbd daemon```
sudo service smbd restart
```...now you should be able to browse the network for the host **WP-Macmini** and the share **Documents** (//WP-Macmini/Documents).  You can do this from WP-Macmini since that machine is both a server and a client.  Then check from the other hosts.

As to your questions  [LIST]
[*]1. Yes you can install the system-config tool if we have had success seeing the share. [/LIST]
I didn't want an extra variable to diagnose.  Most of the work we have done is to get back to the default Samba install.  The share definition is less than 10 lines of text at the bottom of the smb.conf file. 

[list]
[*]2. Windows7 should have no problems accessing the Samba shares.[/LIST]
I have never had problems with Windows Vista,7, 8 or 10.  If you have problems we can work on that specific problem.

Let me know it you can access the share now.

---

### Post by williepabon on 2016-01-07
bab1:

OK. This is the experience so far. I can connect and see the local shares on my Ubuntu machine (WP-Macmini), no problems. I can connect  from my Macmini and see the shares in the HP machine with Elementary OS. From the HP machine with Elementary OS, I can connect and see the local shares, but when I try from this machine to connect to the Macmini, I get the message: "Unable to mount Folder. The server for this folder could not be located." Haven't tried with the windows machine yet. Connections between the Linux machines is my primary goal. Await for your advice. Thanks.

---

### Post by bab1 on 2016-01-07
Don't do anything to the configuration.  Sometimes this requires a reboot of the Samba server and waiting about 15 minutes for the share definition to become available.  

So reboot and wait awhile before you try again.

---

### Post by williepabon on 2016-01-07
OK. Will reboot and wait. Thanks

---

### Post by williepabon on 2016-01-07
bab1:

Well, I've waited for more than 30 mins. An the situation still persist. From the Macmini I can connect and browse shares of the HP with Elementary OS. Not possible yet, the other way around. Please, advice.  Thanks.
wp

---

### Post by bab1 on 2016-01-07
> **williepabon said:**
> bab1:

Well, I've waited for more than 30 mins. An the situation still persist. From the Macmini I can connect and browse shares of the HP with Elementary OS. Not possible yet, the other way around. Please, advice.  Thanks.
wp

Working only with the host WP-Macmini (Ubuntu) and an HP host with ElementaryOS running.  

From the HP machine terminal, what do you get with this command```
smbtree -d3
```
...this will be long -- multiple screens worth.  

If you want you can pipe this to a file and then copy it into the reply editor.  To pipe the output to a file you do this```
smbtree -Nd3 > smbtree.txt
```...this will create a file in the users home directory named smbtree.ext.

---

### Post by williepabon on 2016-01-07
bab1:

Ok. I'm writing this and the results from the HP machine as requested. When I run the command

smbtree -N d3 > smbtree.txt
this is what is in the file:

WORKGROUP
    \\WP-PAVILION            WP-Pavilion server (Samba, Ubuntu)
        \\WP-PAVILION\HL2270DW           HL2270DW
        \\WP-PAVILION\Brother_HL-2270DW_series    Brother HL-2270DW series
        \\WP-PAVILION\print$             Printer Drivers
        \\WP-PAVILION\My Documents       
        \\WP-PAVILION\Documents          
        \\WP-PAVILION\IPC$               IPC Service (WP-Pavilion server (Samba, Ubuntu))
    \\WP-MACMINI             WP-Macmini server (Samba, Ubuntu)
    \\BRW0022581D47F6        

When I run the command

smbtree -d3

this is the result I get:

```
williepabon@WP-Pavilion:~$ smbtree -d3lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=192.168.0.5 bcast=192.168.0.255 netmask=255.255.255.0
Enter williepabon's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.5 ( 192.168.0.5 )
Connecting to 192.168.0.5 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.5 ( 192.168.0.5 )
Connecting to 192.168.0.5 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\WP-PAVILION            WP-Pavilion server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name WP-PAVILION<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name WP-PAVILION<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name WP-PAVILION<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\WP-PAVILION\HL2270DW           HL2270DW
        \\WP-PAVILION\Brother_HL-2270DW_series    Brother HL-2270DW series
        \\WP-PAVILION\print$             Printer Drivers
        \\WP-PAVILION\My Documents       
        \\WP-PAVILION\Documents          
        \\WP-PAVILION\IPC$               IPC Service (WP-Pavilion server (Samba, Ubuntu))
    \\WP-MACMINI             WP-Macmini server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name WP-MACMINI<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name WP-MACMINI<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name WP-MACMINI<0x20>
resolve_hosts: getaddrinfo failed for name WP-MACMINI [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name WP-MACMINI<0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x5591b0cc0390] mpx_fde[(nil)] fd[14] - disabling
    \\BRW0022581D47F6        
resolve_lmhosts: Attempting lmhosts lookup for name BRW0022581D47F6<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name BRW0022581D47F6<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name BRW0022581D47F6<0x20>
resolve_hosts: getaddrinfo failed for name BRW0022581D47F6 [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name BRW0022581D47F6<0x20>
Got a positive name query response from 192.168.0.156 ( 192.168.0.156 )
Connecting to 192.168.0.156 at port 445
Connecting to 192.168.0.156 at port 139
williepabon@WP-Pavilion:~$ 


```

You can figure out which one is more useful to you.
Thanks.
wp

---

### Post by bab1 on 2016-01-07
What does this mean to you?```
\\BRW0022581D47F6
```

I see that WP-macmini is a known name but later it can't be resolved.  The inI will look over the information and get back to you.

[COLOR="#0000FF"]**Edit: ** Yes this is a name resolve problem.  I will post a cure in a bit.[/COLOR]

---

### Post by bab1 on 2016-01-07
Without seeing your entire hosts/DNS set up it would would be easier to just set the NetBIOS names on all the Samba servers.  It will be easier to explicitly set the NetBIOS names as all hostnames are first converted to NetBIOS names and then resolved to IP addresses anyway.

The way to set the NetBIOS name is to explicitly add a line in the [global] section of the smb.conf file.  In addition I also would set the name resolve order to only use *bcast* (broadcast).  Here are the lines you need to add to the smb.conf file```

# Declare NetBIOS name
        netbios name = <hostname>
# Set name resolve order
        name resolve order = bcast

```
I would place this directly below these lines in the smb.conf file```

[global]

## Browsing/Identification ###

```... substitute WP-pavillion for <hostname> on the HP machine and WP-minimac for the other machine.

Either restart the smbd process or reboot both machines.  Then from the HP again post the output of ```
smbtree -d3
```

---

### Post by williepabon on 2016-01-07
bab1:

Implemented the changes advised on both machines. Here is the result of smbtree on the HP-Pavilion machine:

```
williepabon@WP-Pavilion:~$ smbtree -d3lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=192.168.0.5 bcast=192.168.0.255 netmask=255.255.255.0
Enter williepabon's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.5 ( 192.168.0.5 )
Connecting to 192.168.0.5 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.5 ( 192.168.0.5 )
Connecting to 192.168.0.5 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\WP-PAVILION    		WP-Pavilion server (Samba, Ubuntu)
name_resolve_bcast: Attempting broadcast lookup for name WP-PAVILION<0x20>
Got a positive name query response from 192.168.0.5 ( 192.168.0.5 )
Connecting to 192.168.0.5 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\WP-PAVILION\HL2270DW       	HL2270DW
		\\WP-PAVILION\Brother_HL-2270DW_series	Brother HL-2270DW series
		\\WP-PAVILION\print$         	Printer Drivers
		\\WP-PAVILION\My Documents   	
		\\WP-PAVILION\Documents      	
		\\WP-PAVILION\IPC$           	IPC Service (WP-Pavilion server (Samba, Ubuntu))
	\\WP-MACMINI     		WP-Macmini server (Samba, Ubuntu)
name_resolve_bcast: Attempting broadcast lookup for name WP-MACMINI<0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x556c79a06540] mpx_fde[(nil)] fd[14] - disabling
	\\BRW0022581D47F6		
name_resolve_bcast: Attempting broadcast lookup for name BRW0022581D47F6<0x20>
Got a positive name query response from 192.168.0.156 ( 192.168.0.156 )
Connecting to 192.168.0.156 at port 445
Connecting to 192.168.0.156 at port 139
williepabon@WP-Pavilion:~$ 



```

---

### Post by williepabon on 2016-01-07
bab1:

\\BRW0022581D47F6 is a printer (Brother HL-2270) connected to the network via ethernet. It has a static IP = 192.168.0.156 and it also is WiFi.

wp

---

### Post by williepabon on 2016-01-07
bab1:

Just to let you know, after I did a reboot on the Mac-mini pc, the system put a semicolon (";") at the start of the line netbios name = Mac-mini. 
wp

---

### Post by bab1 on 2016-01-08
> **williepabon said:**
> bab1:

Just to let you know, after I did a reboot on the Mac-mini pc, the system put a semicolon (";") at the start of the line netbios name = Mac-mini. 
wp
The semicolon was **not** put there by the "system".  Nether the OS or Samba itself writes to the smb.conf file.  Only human editing (as the root user) edits that file.  The smbd daemon only *_reads_* the file and uses the parameters for the internal variables of the binary application (smbd).

It is possible that if you used samba-config,  the semicolon was added and you didn't notice.  So I changed the name and didn't see that in the last view of *smbtree -d3*.  You started with a hostname of WP-minimac.  I asked you to change that to WP-macmini and it did show the change ```
\\WP-MACMINI     		WP-Macmini server (Samba, Ubuntu)
name_resolve_bcast: Attempting broadcast lookup for name WP-MACMINI<0x20>
```

Something is not right.  If the line is commented out, what is being used by Samba for name resolution?    

At this point I can't even tell tell which machine we are diagnosing at the moment.  When this happens I go back to the beginning and start over.  :-(  

So we start with the host we are now calling** mac-mini**.  Do not use samba-config for anything,  Post the output of these terminal commands (please try and preserve the formatting and separation of command data)```

cat /etc/hosts

cat /etc/hostname

cat /etc/samba/smb.conf

smbtree -d3

nmblookup wp-minimac

nmblookup wp-macmini

nmblookup mac-mini

```
I am expecting to see the semicolon on the line you stated ```
;     netbios name = Mac-mini. 
```

FYI -- it is best to use lower case and no dash ( - ) or underscores ( _ ).  The name would be macmini, not Macmini or MacMini or even MACMINI.  Samba will transform the name into what it needs.  Linux is case sensitive and Windows is case in-sensitive (it doesn't care).  If we are to be consistent then always use the Linux preferred way of lower case.  I have a theme for computer names.  I name my machines for the beaches I have spent time at, so my computers are: kona, maui, malibu, rincon, etc.  I can find them in the logs and speak of them in simple human terms.  If I was to name your machines I would name them: *mini* and *hp*.  We can do that, if you want, after I look at your command output.

---

### Post by williepabon on 2016-01-08
bab1:

I am really sorry for the confusion created by my mistakes. Will try to be more careful. I'm showing below the only modifications I made to smb.conf of both machines (WP-Macmini, and WP-Pavilion) as you suggested in the last post. After that, no changes have been made.

On WP-Macmini:
```
[global]

## Browsing/Identification ###


# Declare NetBios name
;    netbios name = WP-Macmini
# Set name resolve order
    name resolve order = bcast


# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = workgroup



```

On WP-Pavilion:
```
[global]

## Browsing/Identification ###


# Declare NetBios name
    netbios name = WP-Pavilion
# Set name resolve order
    name resolve order = bcast


# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = workgroup



```

Please, advice if you want me to take out the semicolon from the WP-Macmini smb.conf file before I run the other commands you are instructing to do. Thanks.
wp

---

### Post by bab1 on 2016-01-08
> **williepabon said:**
> bab1:

I am really sorry for the confusion created by my mistakes. Will try to be more careful. I'm showing below the only modifications I made to smb.conf of both machines (WP-Macmini, and WP-Pavilion) as you suggested in the last post. After that, no changes have been made.

On WP-Macmini:
```
[global]

## Browsing/Identification ###


# Declare NetBios name
;    netbios name = WP-Macmini
# Set name resolve order
    name resolve order = bcast


# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = workgroup



```

On WP-Pavilion:
```
[global]

## Browsing/Identification ###


# Declare NetBios name
    netbios name = WP-Pavilion
# Set name resolve order
    name resolve order = bcast


# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = workgroup



```

Please, advice if you want me to take out the semicolon from the WP-Macmini smb.conf file before I run the other commands you are instructing to do. Thanks.
wp

Yes I want you to remove the semicolon.  You will have to restart the smbd process on WP-Macmini also.  The command to do that is```
sudo service smbd restart
```

Remember that the other commands are only for WP-Macmini at this time.

---

### Post by williepabon on 2016-01-08
bab1:
OK. Here are the results for the commands on the WP-Macmini pc:

```
williepabon@WP-Macmini:~$ cat /etc/hosts127.0.0.1    localhost
127.0.1.1    WP-Macmini


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
williepabon@WP-Macmini:~$ cat /etc/hostname
WP-Macmini
williepabon@WP-Macmini:~$ 



```


```
williepabon@WP-Macmini:~$ cat /etc/samba/smb.conf#
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


# Declare NetBios name
    netbios name = WP-Macmini
# Set name resolve order
    name resolve order = bcast


# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = workgroup


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
;    passdb backend = tdbsam


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
;    usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
    username map = /etc/samba/smbusers


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
;    guest ok = no
;    read only = yes
    create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin


[Documents]
    comment = Documents Directory
    path = /home/williepabon/Documents
    browseable = yes
    force user = williepabon
    writeable = yes
    create mask = 0664
    directory mask = 0775




williepabon@WP-Macmini:~$ 



```

```
williepabon@WP-Macmini:~$ smbtree -d3lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.0.4 bcast=192.168.0.255 netmask=255.255.255.0
Enter williepabon's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.5 ( 192.168.0.5 )
Connecting to 192.168.0.5 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.5 ( 192.168.0.5 )
Connecting to 192.168.0.5 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\WP-PAVILION            WP-Pavilion server (Samba, Ubuntu)
name_resolve_bcast: Attempting broadcast lookup for name WP-PAVILION<0x20>
Got a positive name query response from 192.168.0.5 ( 192.168.0.5 )
Connecting to 192.168.0.5 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\WP-PAVILION\HL2270DW           HL2270DW
        \\WP-PAVILION\Brother_HL-2270DW_series    Brother HL-2270DW series
        \\WP-PAVILION\print$             Printer Drivers
        \\WP-PAVILION\My Documents       
        \\WP-PAVILION\Documents          
        \\WP-PAVILION\IPC$               IPC Service (WP-Pavilion server (Samba, Ubuntu))
    \\WP-MACMINI             WP-Macmini server (Samba, Ubuntu)
name_resolve_bcast: Attempting broadcast lookup for name WP-MACMINI<0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fed51ca91e0] mpx_fde[(nil)] fd[14] - disabling
    \\BRW0022581D47F6        
name_resolve_bcast: Attempting broadcast lookup for name BRW0022581D47F6<0x20>
Got a positive name query response from 192.168.0.156 ( 192.168.0.156 )
Connecting to 192.168.0.156 at port 445
Connecting to 192.168.0.156 at port 139
williepabon@WP-Macmini:~$ 



```

```
williepabon@WP-Macmini:~$ nmblookup wp-minimacname_query failed to find name wp-minimac
williepabon@WP-Macmini:~$ 
williepabon@WP-Macmini:~$ nmblookup wp-macmini
name_query failed to find name wp-macmini
williepabon@WP-Macmini:~$ 
williepabon@WP-Macmini:~$ nmblookup mac-mini
name_query failed to find name mac-mini
williepabon@WP-Macmini:~$ 
williepabon@WP-Macmini:~$ nmblookup WP-Macmini
name_query failed to find name WP-Macmini
williepabon@WP-Macmini:~$ 



```
Included name_query for this host too.
Waiting for further instructions. Thanks.
wp

---

### Post by bab1 on 2016-01-08
You must have a firewall on for this machine.  Turn it off and try the ***smbtree -d3*** and ***nmblookup*** commands again.  All the rest is good.

---

### Post by williepabon on 2016-01-08
bab1:

After turning off the firewall, these are the results:

```
williepabon@WP-Macmini:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.0.4 bcast=192.168.0.255 netmask=255.255.255.0
Enter williepabon's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
Connecting to 192.168.0.4 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
Connecting to 192.168.0.4 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\WP-MACMINI             WP-Macmini server (Samba, Ubuntu)
name_resolve_bcast: Attempting broadcast lookup for name WP-MACMINI<0x20>
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
Connecting to 192.168.0.4 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\WP-MACMINI\Edif_Juncos        
        \\WP-MACMINI\Brother-HL-2270DW    Brother HL-2270DW series
        \\WP-MACMINI\print$             Printer Drivers
        \\WP-MACMINI\Documents          
        \\WP-MACMINI\IPC$               IPC Service (WP-Macmini server (Samba, Ubuntu))
    \\BRW0022581D47F6        
name_resolve_bcast: Attempting broadcast lookup for name BRW0022581D47F6<0x20>
Got a positive name query response from 192.168.0.156 ( 192.168.0.156 )
Connecting to 192.168.0.156 at port 445
Connecting to 192.168.0.156 at port 139
williepabon@WP-Macmini:~$ 



```

```
williepabon@WP-Macmini:~$ nmblookup wp-minimac
name_query failed to find name wp-minimac
williepabon@WP-Macmini:~$ nmblookup wp-macmini
192.168.0.4 wp-macmini<00>
williepabon@WP-Macmini:~$ nmblookup mac-mini
name_query failed to find name mac-mini
williepabon@WP-Macmini:~$ nmblookup WP-Macmini
192.168.0.4 WP-Macmini<00>
williepabon@WP-Macmini:~$ 



```

Ok. By turning the firewall to off, now I have connectivity between this machine and the rest! Now I see the files in the other pcs on the network and they see my files. So, the peer-to-peer network problem is solved. But, I guess It created a small problem. I need to have the firewall turned on. So, I need to know how to configure the firewall to accept the comm protocols required by Samba while limiting the ones that I have already configured on the firewall. If you can help on that, you are very welcome. Thanks.
wp

---

### Post by bab1 on 2016-01-08
> **williepabon said:**
> ..

Ok. By turning the firewall to off, now I have connectivity between this machine and the rest! Now I see the files in the other pcs on the network and they see my files. So, the peer-to-peer network problem is solved. But, I guess It created a small problem. I need to have the firewall turned on. So, I need to know how to configure the firewall to accept the comm protocols required by Samba while limiting the ones that I have already configured on the firewall. If you can help on that, you are very welcome. Thanks.
wp


I don't have any host based firewalls in my network.  My firewall is an edge device that is not Linux based.  What firewall specifically are you using?   If you have a GUFW (UFW) based front end to IPtables then maybe [**this listing**]("https://www.google.com/search?q=gufw+allow+samba&btnG=Go!&gws_rd=ssl#q=ubuntu+14.04+gufw+allow+samba&nfpr=1") will help.
[COLOR="#0000FF"]
Edit: I just found that you can add a pre-configured rule for samba with GUFW.  From the first listing of the list I just sent[/COLOR]```

[B]Gufw offers the following in the Preconfigured tab:
[/B]
    ftp
    http
    imap
    nfs
    pop 3
    samba
    smtp
    ssh
    vnc
    zeroconf

```

---

### Post by williepabon on 2016-01-08
bab1:

Thanks for answering my last question. First of all, I really want thank you for all the help and your effort to solve this problem. In addition to the solution, I received a good educational experience on how the Samba application works. So, I should say, CONGRATULATIONS, you solved my problem. Thanks.\\:D/

PS
Out of sheer curiosity, how did you come about with the idea that I might have a firewall obstruction?

wp

---

### Post by bab1 on 2016-01-08
> **williepabon said:**
> bab1:

Thanks for answering my last question. First of all, I really want thank you for all the help and your effort to solve this problem. In addition to the solution, I received a good educational experience on how the Samba application works. So, I should say, CONGRATULATIONS, you solved my problem. Thanks.\\:D/

PS
Out of sheer curiosity, how did you come about with the idea that I might have a firewall obstruction?

wpEducation and experience.  The formal education taught me the basics and the experience honed my skills.  This is the tip off```
    \\WP-MACMINI             WP-Macmini server (Samba, Ubuntu)
name_resolve_bcast: Attempting broadcast lookup for name WP-MACMINI<0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fed51ca91e0] mpx_fde[(nil)] fd[14] - disabling
```
With the system configured as we have it.  The above situation of knowing the NetBIOS name but unable to connect to the service  is not possible without outside intervention (the firewall app).  

The above is all on one machine.  No external networking problems at all.  My style of diagnosis is to start with a known configuration on a single machine and add other machines after I have success with the first one.  

That's why we started with the single machine (WP-macmini) and later added a second machine.  I almost never guess at a solution.   I didn't guess this time either.  ;-)

---

