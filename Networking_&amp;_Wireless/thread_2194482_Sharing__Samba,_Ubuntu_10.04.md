---
title: "Sharing / Samba, Ubuntu 10.04"
date: 2013-12-18
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2013-12-18
I have asked this before, but I never received an answer. I have samba set up on my Ubuntu 10.04 desktop. I am sharing several folders to other computers as well as media players such as the CCrane WiFi Radio. 

This used to work just fine. Now, although my computers can see the names of the folders being shared, whenever I click on one or on Windows Network, I get "Unable to Mount Location: Failed to retrieve share list from server". I can still manually mount these from the command line, but that does not help with devices such as the CCrane radio. It also doesn't help if one does not know or remember the exact location that needs to be mounted. 

Network:// shows:

backup.drive
christmas
multimedia
print$
shop_docs
Windows Network


My hosts file (if important) is:
```

127.0.0.1	localhost
127.0.1.1	shop

192.168.1.13	www.RobotsAndComputers.com

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

smb.conf is:
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
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
;   netbios name = shop

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

# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = lmhosts hosts wins bcast
#   name resolve order = hosts bcast

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

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user
#   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true
#   encrypt passwords = false

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
#   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
#   passwd program = /usr/bin/passwd %u
#   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user

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

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

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
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

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
   usershare owner only = false

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

   lanman auth = Yes
   client lanman auth = Yes
   client plaintext auth = Yes

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

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

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

```

I had it working for a few days by changing 'name resolve order = lmhosts host wins bcast' to 'name resolve order = lmhosts hosts wins bcast' in the smb.conf file (as it is now) and it worked fine for a couple of days. Then, all of a sudden, for no reason, while the CCrane radio was connected and playing, it just quit working!

If SOMEONE... nah... ANYONE... could offer me ANY advice WHATSOEVER I would be ETERNALLY grateful!!!! 

Thank you in advance and &#10014; Merry Christmas &#10014;

---

### Post by Bucky Ball on 2013-12-18
Slightly off-topic, but if you've asked this before you were probably advised that 10.04 LTS is no longer supported. If not, it isn't. Unless you are using the server version, but you explicitly state 10.04 desktop so I'll assume you're not.

---

### Post by rebeltaz on 2013-12-18
Actually, I don't believe that I ever received ANY response to my previous request. I'm not sure if this is the desktop version or the server version. I know that I do have the server version installed on my server, so it is possible that I just used the same version on my desktop. When I said 'desktop' earlier, I only meant that it is on my desktop computer. The output of 'lsb_release -a' is "Ubuntu 10.04.4 LTS" ... not much help. Sorry.

I didn't think about the obsolescence of the OS being an issue, but if I had, I would probably have hoped that maybe this was a samba issue as opposed to an OS issue. ??? 

I do apologize if this request is unwanted or unable to be fulfilled. Thanks anyway... :(

---

### Post by Bucky Ball on 2013-12-19
No, no. As I said, I was off-topic. Server version supported until 2015. Desktop is out of support so was just figuring that if you are using an unsupported release you'd be better to upgrade to a supported one (12.04 LTS for instance) and that may fix your issues anyhow. But then again, maybe not.

This certainly does look like a networking issue, but it could be because of out of date samba packages was my thought. If it is the desktop version then the Samba you are using is also obsolete (and possibly a security vulnerability). Are you still getting updates (kernel and security updates in particular) for your 10.04? If so, it is probably server edition as updates for the desktop finished in April.

Anyhow, good luck. ;)

* PS: as you can manually mount things it does sound like a problem on the 10.04 box and probably to do with Samba. I don't use it so leaving it alone (unless I see something obvious).

---

### Post by Morbius1 on 2013-12-19
This is going to be a tough one since I no longer remember the specifics of 10.04 but ....

*** None of the shares you mentioned are in smb.conf so can I assume you shared them in nautilus? If so you might want to post the output of the follwoing command to let the folks here see how they are set up:
```
net usershare info --long
```
*** > I had it working for a few days by changing 'name resolve order =  lmhosts host wins bcast' to 'name resolve order = lmhosts hosts wins  bcast' in the smb.conf file (as it is now) and it worked fine for a  couple of days. Then, all of a sudden, for no reason, while the CCrane  radio was connected and playing, it just quit working
The only default working name resolution mechanism is bcast so put it first:
```
 name resolve order = bcast lmhosts host wins
```
Then restart samba:
```
sudo service smbd restart
sudo service nmbd restart
```
[COLOR=#0000cd]*Note: I don't remember but once upon a time the samba daemons were all under "samba" so to restart you may have to run:*[/COLOR]
```
sudo service samba restart
```
*** I'm not sure how well developed mDNS/avahi was in 10.04 but can you access your own machine this way:
```
nautilus smb://shop.local
```

---

### Post by rebeltaz on 2013-12-19
I did share them in Nautilus. That was before I figured out how to do it from within samba. 

netshare output:
```

[backup.drive]
path=/mnt/backup
comment=
usershare_acl=Everyone:F,
guest_ok=n

[multimedia]
path=/mnt/multimedia
comment=
usershare_acl=Everyone:F,
guest_ok=n

[christmas]
path=/mnt/multimedia/Christmas/Christmas Time in Shelby
comment=
usershare_acl=Everyone:R,
guest_ok=n

[shop_docs]
path=/home/derek
comment=
usershare_acl=Everyone:F,
guest_ok=n

```

On this line:
```

 name resolve order = bcast lmhosts host wins

```

is that HOST or HOSTS? I ask because is that not a reference to the /etc/hosts file?

This - "nautilus smb://shop.local" - does work, by the way.

---

### Post by rebeltaz on 2013-12-19
I tried all night last night and I could not connect via Network or through CC radio. For some reason, it is working again now and I have not restarted any services; I have not restarted the computer, the radio or any computer on the network; installed/ modified any software or settings.. I have not done ANYTHING except run the two commands requested - "nautilus smb://shop.local" and "net usershare info --long"

Any thoughts?

---

### Post by tgalati4 on 2013-12-19
If you have at least one Windows machine on your network, it is possible that it is acting as a WINS server and that helps identify available network shares.  If the Windows machines are asleep, then you would need to activate the WINS server in your smb.conf.  I'm guessing that the network radio uses WINS for finding network shares.

---

### Post by rebeltaz on 2013-12-19
> **tgalati4 said:**
> If you have at least one Windows machine on your network, it is possible that it is acting as a WINS server and that helps identify available network shares.  If the Windows machines are asleep, then you would need to activate the WINS server in your smb.conf.  I'm guessing that the network radio uses WINS for finding network shares.

That is an interesting thought. There is, in fact, one windows laptop on my network on occasion, but.... why would that affect whether or not my Linux systems could access the network?

I will try that, though. Thank you.

---

### Post by Morbius1 on 2013-12-20
> **rebeltaz said:**
> For some reason, it is working again now and I have not restarted any services; I have not restarted the computer, the radio or any computer on the network; installed/ modified any software or settings.. I have not done ANYTHING except run the two commands requested - "nautilus smb://shop.local" and "net usershare info --long"

Any thoughts?
Neither one of those things should have done anything structural. The "usershare" command is just a reporting tool and the shop.local was just to see if mDNS was alive and well on 10.04.

The "nautilus smb://shop.local" way can be used by any of your other Linux machines if they are current. Then they can just bookmark it. It's Samba without all the Windows specific stuff.

In fact there is even a way to set up a simple file that will force your host to show up under "Network" on all your Linux ( and OSX ) machines automatically using Avahi. Again, it's hard to tell how extensive mDNS / Avahi support was in 10.04 and I don't know if it will work for the Radio either.

---

### Post by rebeltaz on 2013-12-20
sigh.... well, after working fine again last night as I reported for several hours, it just quit working. Mid-song the radio quit playing and could no longer find the computer on the network. And NOTHING had changed. The computer with the media was still running. The windows laptop was still running.... Intermittent is aggravating. Have I mentioned that?

---

