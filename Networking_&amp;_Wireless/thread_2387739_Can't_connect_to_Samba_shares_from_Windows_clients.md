---
title: "Can't connect to Samba shares from Windows clients"
date: 2018-03-23
forum: Networking &amp; Wireless
---

### Post by marcerickson on 2018-03-23
This is my smb.conf


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
    unix password sync = yes
    log file = /var/log/samba/log.%m
    passdb backend = tdbsam
    writeable = yes
    netbios name = POWEREDGE1800
    server role = standalone server
    os level = 20
    max log size = 1000
    syslog = 0
    server string = %h server (Samba, Ubuntu)
    dns proxy = no
    encrypt passwords = yes
    panic action = /usr/share/samba/panic-action %d
    map to guest = bad user
    pam password change = yes
    passwd program = /usr/bin/passwd %u
    workgroup = WORKGROUP
    usershare allow guests = yes
    obey pam restrictions = yes
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# server string is the equivalent of the NT Description field

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.

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

# Cap the size of the individual log files (in KiB).

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.

# Do something sensible when Samba crashes: mail the admin a backtrace


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

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections

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

[500GB]
    path = /mnt/500GB
    directory mask = 0777
        create mask = 777
    writeable = yes
    browseable = yes
    guest ok = yes
    read only = no

[data]
    path = /mnt/data/
    directory mask = 0777
        create mask = 777
    writeable = yes
    browseable = yes
    guest ok = yes
    read only = no

[data2]
    path = /mnt/data2
        directory mask = 0777
        create mask = 777
    writeable = yes
        browseable = yes
    guest ok = yes
        read only = no
```

---

### Post by marcerickson on 2018-03-23
Edited so as to get email notifications.

---

### Post by Morbius1 on 2018-03-23
We have no idea what version of Ubuntu you are using, what version of Windows you are using, and the exact nature of the problem.

"Can't connect" can mean anything. You can't see the Linux machine? You can see it but Windows says it can't find it? You can find it but you can't access it? Nobody knows.

---

### Post by marcerickson on 2018-03-23
~ $ lsb_release -a
No LSB modules are available.
Distributor ID:    LinuxMint
Description:    Linux Mint 18 Sarah
Release:    18
Codename:    sarah

 ~ $ uname -mrs
Linux 4.4.0-21-generic x86_64

My Windows 10 box can't connect.  Neither can my two Windows 7 boxes.  They were able to connect previously.  They can't see the Ubuntu (Linux Mint) machine at all by name.  If I go to the Ubuntu (Linux Mint) machine by IP address, I get "Enter network credentials" and then "The user name or password is incorrect"  The user accounts and passwords on the Ubuntu (Linux Mint) machine and Windows machines are identical.

---

### Post by Morbius1 on 2018-03-23
I don't know why you are getting a credentials prompt for a guest share. Maybe the Linux permissions on /mnt/500GB, /mnt/data, and /mnt/data2 do not allow access to "other".

In any event there are two passwords in a samba server. The users login password to the local box and the samba password to the share. You need to add the user to the samba password database:
```
sudo smbpasswd -a your-user-name
```

---

### Post by marcerickson on 2018-03-24
OK.  Did that. Now I see the shares again when I try to access the  Ubuntu computer by IP address - still nothing when I try to access it by  its name.  When I try to access the share, I get "Windows cannot access  \\192.168.1.xxx\data2".  Details are: "Error code 0x80070043 The  network name cannot be found"

~ $ sudo pdbedit -L -v
[sudo] password for marc: 
---------------
Unix username:        nobody
NT username:          
Account Flags:        [U          ]
User SID:             S-1-5-21-3383513149-1377938082-3774525732-501
Primary Group SID:    S-1-5-21-3383513149-1377938082-3774525732-513
Full Name:            nobody
Home Directory:       
HomeDir Drive:        (null)
Logon Script:         
Profile Path:         
Domain:               POWEREDGE1800
Account desc:         
Workstations:         
Munged dial:          
Logon time:           0
Logoff time:          never
Kickoff time:         never
Password last set:    0
Password can change:  0
Password must change: 0
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
---------------
Unix username:        marc
NT username:          
Account Flags:        [NUX        ]
User SID:             S-1-5-21-3383513149-1377938082-3774525732-1000
Primary Group SID:    S-1-5-21-3383513149-1377938082-3774525732-513
Full Name:            marc
Home Directory:       \\<computername>\marc
HomeDir Drive:        
Logon Script:         
Profile Path:         \\<computername>\marc\profile
Domain:               <COMPUTERNAME>
Account desc:         
Workstations:         
Munged dial:          
Logon time:           0
Logoff time:          Wed, 06 Feb 2036 07:06:39 PST
Kickoff time:         Wed, 06 Feb 2036 07:06:39 PST
Password last set:    Sun, 11 Feb 2018 23:19:59 PST
Password can change:  Sun, 11 Feb 2018 23:19:59 PST
Password must change: Mon, 18 Jan 2038 19:14:07 PST
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF

---

### Post by Morbius1 on 2018-03-24
Check the Linux permissions of the target shared folder:
```
ls -dl /mnt/data2
```
On second thought you might want to check the permissions of the parent folder and everything under it:
> ls -al /mnt

---

### Post by marcerickson on 2018-03-24
OK.  Did that. Now I see the shares again when I try to access the  Ubuntu computer by IP address - still nothing when I try to access it by  its name.  When I try to access the share, I get "Windows cannot access  \\192.168.1.xxx\data2".  Details are: "Error code 0x80070043 The  network name cannot be found"

~ $ sudo pdbedit -L -v
[sudo] password for marc: 
---------------
Unix username:        nobody
NT username:          
Account Flags:        [U          ]
User SID:             S-1-5-21-3383513149-1377938082-3774525732-501
Primary Group SID:    S-1-5-21-3383513149-1377938082-3774525732-513
Full Name:            nobody
Home Directory:       
HomeDir Drive:        (null)
Logon Script:         
Profile Path:         
Domain:               POWEREDGE1800
Account desc:         
Workstations:         
Munged dial:          
Logon time:           0
Logoff time:          never
Kickoff time:         never
Password last set:    0
Password can change:  0
Password must change: 0
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
---------------
Unix username:        marc
NT username:          
Account Flags:        [NUX        ]
User SID:             S-1-5-21-3383513149-1377938082-3774525732-1000
Primary Group SID:    S-1-5-21-3383513149-1377938082-3774525732-513
Full Name:            marc
Home Directory:       \\<computername>\marc
HomeDir Drive:        
Logon Script:         
Profile Path:         \\<computername>\marc\profile
Domain:               <COMPUTERNAME>
Account desc:         
Workstations:         
Munged dial:          
Logon time:           0
Logoff time:          Wed, 06 Feb 2036 07:06:39 PST
Kickoff time:         Wed, 06 Feb 2036 07:06:39 PST
Password last set:    Sun, 11 Feb 2018 23:19:59 PST
Password can change:  Sun, 11 Feb 2018 23:19:59 PST
Password must change: Mon, 18 Jan 2038 19:14:07 PST
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF

---

### Post by marcerickson on 2018-03-24
Thanks!!!! That was it.  The shares weren't mounted under /mnt - they were mounted under /media.  I edited the smb.cfg and Bob's your uncle.

Thanks a lot!

---

