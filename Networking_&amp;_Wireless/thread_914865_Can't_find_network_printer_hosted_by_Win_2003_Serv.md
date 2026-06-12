---
title: "Can't find network printer hosted by Win 2003 Server"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by whickey on 2008-09-09
Hello All,
    I didn't see a printer category so if I'm in the wrong place, let me know. I am new to Ubuntu so I'll need specifics. I am a volunteer at a private school and I am trying to set up an Edubuntu environment for evaluation. We are considering converting the school to Ubuntu and Open Source.

I have set up a workstation running Edubuntu (Hardy Heron).

We have a Win2003 Server and about 60 or so Workstations running either XP home or Pro. 

The server hosts a network printer (Brother HL-2140).

When I add printer on the Ubuntu system, the shared network printer does not show up.

I can see network printers of the same type shared on some of the other XP systems.

I can see the Win2003 Printer from the XP systems so I know it is shared.

The issue seems to be between Win2003 Server and Ubuntu.

I have added a printer of the same type directly to the Ubuntu system with no problems.

I have added network printers of the same type hosted by XP systems with no problems.

We are running Workgroup and I have made sure the user and password on the Ububtu system and the server are the same.

I can mount network drives on the server from Ubuntu so Samba seems to be working properly.

Any more suggestions?

Thanks

---

### Post by Calabresi on 2008-09-09
Hi, do you have CUPS installed? try [http://localhost:631/](http://localhost:631/) in EDUbuntu station to check, if not, install it (I dont know how in EDUbuntu, if EDU have Synaptic there's where you will find it) and access the localhost again, the rest is very intuitive, you will see, even then if you found difficult, ask again.

Good Luck

---

### Post by superprash2003 on 2008-09-09
try adding the printer by entering its full link.. like ip/printername

---

### Post by whickey on 2008-09-10
Thanks Calabresi and superprash2003,
    Yes, I can run CUPS, but am still not having success. I have also tried entering the full link for the printer through the system->Administration->Printing window. Maybe I have the URI wrong. 
The printer is shared using the name BrotherLab
I am using smb://workgroup/server/BrotherLab
Do I need to specify a port? If so, how do I find out which port to use?

Also, superprash2003, How do I enter the full name using IP address? When I select Windows printer via SAMBA, the smb:// is pre-entered and I am told to enter workgroup/server/printer.

Thanks

---

### Post by Calabresi on 2008-09-10
Hi again,

Strange enough, that really should be out-of-the-box, but let's go to basics, I know you should have that set as you have other's stations plugged already and working. Sorry if I'm beeing too basic, but sometimes I see that we forget to fill the gas tank and try to fix things is already working.

Another thing to check, did you set some FW (firewall) in EDUBuntu station? The Edu eth0 address and subnet mask the same, DHCP set and receiving correct address? Workgroup? if yes, specify in >Network Settings>DNS tab>Search Domains (entry with your group).

Internal DNS? If yes, is it being received by Edu correctly in the tab DNS?

Now try some basic search in Edu using your file manager, type, please pay attention on slash quantity, the first line network should be enough to show all your net, but if that not the case than you should consider compare 2 files in /etc/samba/ folder with my configuration that I'll include in the foot of this post:

```
network:///
smb:///
smb://name_of_your_server
smb://workgroup/name_of_your_server
smb://workgroup/name_of_your_server/printer_name_set_in_winserver
```

Are you the server adm? if not, ask the admin if he/she changed any port of printer and group.

Windows Firewall: Allow File and Print Sharing exception

This will open up the following ports on the client machines:

TCP Port 139 (Netbios Session Service)
TCP Port 445 (RPC)
UDP Port 137 (Netbios Name Service)
UDP Port 138 (Netbios Datagram Service) 

backup your file:///etc/samba/smbusers and file:///etc/samba/smb.conf with the name you like, .backup .old, and here are my configuration, if you want you can copy and paste in a new file proper place /etc/samba/, but if you do, again, dont forget to backup both cited files, and you need to know you workgroup name and edit smb.conf, in file manager ctrl-F and search workgroup = include_here_workgroup_name save and reboot the machine:

**/etc/samba/smb.conf**
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
workgroup = **yourworkgroup**
# server string is the equivalent of the NT Description field
server string = %h Unix Server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
name resolve order = bcast wins lmhosts host

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

# Cap the size of the individual log files (in KiB).
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
encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
passdb backend = tdbsam

obey pam restrictions = yes

guest account = nobody
invalid users = root

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
pam password change = no

# This option controls how nsuccessful authentication attempts are mapped
# to anonymous connections
map to guest = Bad User

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
load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
printing = cups
printcap name = cups

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
;	socket options = SO_RCVBUF=8192
;	socket options = SO_SNDBUF=8192
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

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
usershare allow guests = yes
restrict anonymous = no
domain master = no
preferred master = no
max protocol = NT
acl compatibility = winnt
ldap ssl = No
server signing = Auto

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
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
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
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
path = /var/spool/samba
printable = yes
create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers

[PUBLIC - SHARED FOLDER]
path = /home/username/Public/
guest ok = yes
read only = no
comment = Public Shared Folder
```

**/etc/samba/smbusers**
```
# Unix_name = SMB_Name1 SMB_Name2 ...
root = administrator
nobody = guest smbguest pcguest
```

---

### Post by Calabresi on 2008-09-11
Was managing one SMB client now and remembered that you could take a look about "winbind" also. It's in synaptic also. Check if you have:

"samba" - "samba-common" - "smbclient" - "smbfs"

All in synaptic.

---

### Post by superprash2003 on 2008-09-11
basically as you said, you will find the smb:// already present.. there you type x.x.x.x/printername where x.x.x.x is the ip address of the windows 2003 server which has the printer connected and printername is the name of the network printer.. incase you are not sure about that, you could go to the windows 2003 server and open windows explorer and type \\127.0.0.1 and there you should see the printer name with the printer symbol or it could be under a folder called Printer.
For reference: [http://prash-babu.blogspot.com/2008/07/how-to-connect-to-network-printer-in.html](http://prash-babu.blogspot.com/2008/07/how-to-connect-to-network-printer-in.html)

---

### Post by whickey on 2008-09-12
Spent the day Thursday chasing down a rogue PC that brought down our network. Didn't have much time to investigate this.
Here is what I have tried so far:

Calabresi, I installed Ubuntu Hardy Heron as default and have made no changes other that the Edubuntu Add-on. Is a firewall loaded by default? How do I access?

The network configuration is not using DHCP. Addresses are assigned and fixed manually. Settings are correct. Yes, I am the network administrator, but only by default and not a good one. I am strictly a volunteer and am trying to get them to hire someone more knowledgeable than me. School has no budget so I don't see that happening.

I checked synaptic for:
"samba" - "samba-common" - "smbclient" - "smbfs"

"samba-common" and "smbclient" were already loaded, "samba" and "smbfs" were not so I loaded them. Rebooted but still no luck.

The rest of your suggestions and code samples are WAY above my head.

Superprash2003, I used the IP as you suggested but no luck.
I took a look at your documentation at:
[http://prash-babu.blogspot.com/2008/07/how-to-connect-to-network-printer-in.html](http://prash-babu.blogspot.com/2008/07/how-to-connect-to-network-printer-in.html)

Excellent documentation, THANK YOU!

I think my problem might be at step 8 - "Authentication Required"
I "assumed" that authentication was handled like it would be in windows. Make sure login and password match on both machine. I did not have proper understanding of this "authentication" field but I do now. I will not be able to try this until Monday but I suspect that may be the problem. I have been prompted for a password in the past but after entering it, it never seemed to connect. I was not sure if I was being asked by the server or sudo on the client. That is still a little confusing for me.

Thanks so much for your help guys! I am learning and that is good!

Tony

---

### Post by whickey on 2008-09-12
Problem solved! It was the authentication. After checking this field and entering the username and password for the Server, the Printer connected as it should.
Many thanks for the superb help!

Tony

---

