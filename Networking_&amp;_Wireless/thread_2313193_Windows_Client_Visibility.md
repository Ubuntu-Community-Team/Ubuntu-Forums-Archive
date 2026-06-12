---
title: "Windows Client Visibility"
date: 2016-02-10
forum: Networking &amp; Wireless
---

### Post by kazz2 on 2016-02-10
I hope this is in the right section. I'm replacing aging Windows-based servers with Ubuntu Server 14.04.3 LTS - which is very, very new to me. My problem is client visibility of the Ubuntu server. It seems the Win7 clients can see it but the Win10 clients cannot. I've not checked very many devices, but this is my first impression.

Even with Win10 I can create a desktop shortcut to the Ubuntu server by name with no issues. But in File Explorer, refreshing, etc., it doesn't appear.

Any ideas?

I rejected domain and workgroup functionality in this tiny network long ago as it created more issues than it solved. And if someone wants something shared or backed up it went to one of the two little servers. Is it strongly recommended I go that route? If so, what are the pluses and minuses?

Otherwise, I just want users to be able to browse easily and find their shares.

Thanks!

---

### Post by blueridgedog on 2016-02-10
You may want to post your samba config for others to look at.

---

### Post by kazz2 on 2016-02-10
I can do that, if necessary. But it's default with two or three shares added is all. I just put this all together last week.

Here she is:

```
## Sample configuration file for the Samba suite for Debian GNU/Linux.
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


# Server Samba Shares
[admin]
        path = /home/xyz/admin
        browseable = yes
        guest ok = no
        writeable = yes
        valid users = xyz
[zp5]
        path = /mnt/zp5
        browseable = no
        guest ok = no
        writeable = yes
        valid users = abc, xyz
[common]
        path = /mnt/common
        browseable = yes
        valid users = @common
        guest ok = no
        writeable = yes
        create mode = 0770
        directory mode = 0770



```

---

### Post by bab1 on 2016-02-10
> **kazz2 said:**
> My problem is client visibility of the Ubuntu server. It seems the Win7 clients can see it but the Win10 clients cannot. I've not checked very many devices, but this is my first impression.

Even with Win10 I can create a desktop shortcut to the Ubuntu server by name with no issues. But in File Explorer, refreshing, etc., it doesn't appear.

Any ideas?

If you can browse using Ubuntu and/or Windows 7 clients, but not Windows 10 clients, I would say that the Windows 10 client needs configuring.  Specifically to allow NetBIOS over TCP (NBT).  This is the traditional way of broadcasting a service on the network.  I have a Windows 10 client that works correctly.  It is not in my possession right now so I can't check on the exact steps, but they should be similar to [**this**]("http://www.tenforums.com/network-sharing/5747-w10-not-discovering-samba-devices-starting-10049-a.html") site's instructions. 

> 
I rejected domain and workgroup functionality in this tiny network long ago as it created more issues than it solved. And if someone wants something shared or backed up it went to one of the two little servers. Is it strongly recommended I go that route? If so, what are the pluses and minuses?

The default smb.conf file makes it so you do have a WORKGROUP and all of it's functionality (whatever that means).  The default smb.conf file configures Samba for a small network already.  You don't need to do anything but add your shares; just as you have done.  I assume you know that one of the shares is not browseable because you have set that parameter in the share definition ```
[zp5]
        path = /mnt/zp5
       **[COLOR="#FF0000"] browseable = no[/COLOR]**
        guest ok = no
        writeable = yes
        valid users = abc, xyz
```

---

### Post by kazz2 on 2016-02-10
That didn't fix my problem, bab1. But NetBIOS, WINS, etc. is something I started looking into as to configuration differences between the affected PC and those that can see the server. I just need to set aside a bit more time to look into this project, I think. But you did find something out there I couldn't find in my searches. Thanks!

And good catch. Yes, it's configured that way intentionally.

I did, just for grins, change the workgroup on both the Ubuntu server and the Win10 PC in case there was something wrong there. I put them in their own workgroup and still no joy. Again, I'll put more time into it tomorrow. Today didn't afford enough opportunity.

Thanks for the info!

---

### Post by bab1 on 2016-02-10
> **kazz2 said:**
> That didn't fix my problem, bab1. But NetBIOS, WINS, etc. is something I started looking into as to configuration differences between the affected PC and those that can see the server. 
If this is a single segment LAN you don't need a WINS server.  The information is best left to a broadcast of SMB resources.

Have you made sure that there are no firewalls that could be stopping the SMB broadcasts?

---

### Post by kazz2 on 2016-02-11
Did some reading and agree about no need for a WINS server. I turned off the firewall on the Win10 machine, restarted samba, and refreshed the Network section of the Win10 machine's Explorer display. It still doesn't show. I also noticed that the Win7 machine I'm comparing it to sees many more PCs than the Win10 PC. More digging to do today!

---

### Post by blueridgedog on 2016-02-14
See the first reply to this thread:

[http://superuser.com/questions/954142/windows-10-computer-cant-connect-to-any-other-computer-on-the-network](http://superuser.com/questions/954142/windows-10-computer-cant-connect-to-any-other-computer-on-the-network)

Seems that 10's ability to see smb is disabled by default now...interesting.

---

### Post by Morbius1 on 2016-02-14
It's not turned off by default. It's a bug. It is supposedly fixed but when it will reach the retail customer seems to be the question of the day:


Cannot connect to CIFS / SMB / Samba Network Shares & Shared Folders in Windows 10 after update 1511/10586: [https://social.technet.microsoft.com/Forums/en-US/2131750e-d589-41f0-b6a3-1c7dac2361d9/cannot-connect-to-cifs-smb-samba-network-shares-shared-folders-in-windows-10-after-update](https://social.technet.microsoft.com/Forums/en-US/2131750e-d589-41f0-b6a3-1c7dac2361d9/cannot-connect-to-cifs-smb-samba-network-shares-shared-folders-in-windows-10-after-update)

Read the posts by ARUDELL for the why and the how since he's the only one in the thread with the inside knowledge of the problem and access to the folks that can fix it.

And it's not that smb / samba is broken since Win10 can access the Samba server just fine - as long as it asks for it by name. What is discombobulated is Win10's ability to "discover" or "browse" to the other hosts.

---

### Post by blueridgedog on 2016-02-15
Perhaps.  I am too old and cynical to see Windows10 not being able to browse SMB networks as an innocent bug.  Ha.  Regardless, I think this is the issue at hand.

---

### Post by kazz2 on 2016-02-15
On a related(?) note, I noticed the following at the end of the boot.log:

```
 * Starting SMB/CIFS File and Active Directory Server                    [fail]AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message

```

How can I correct this?

Thanks.

---

### Post by sandyd on 2016-02-15
Does :
```

sudo service smbd restart
```

produce any errors?

The apache error you can ignore, it is just a warning.

---

### Post by kazz2 on 2016-02-15
```
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.6" (uid=1000 pid=3858 comm="stop smbd ") interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")start: Rejected send message, 1 matched rules; type="method_call", sender=":1.7" (uid=1000 pid=3852 comm="start smbd ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

```

Oops. Just realized I needed sudo:

```
smbd stop/waitingsmbd start/running, process 3954



```

Here's the entire boot.log if it matters:

```
Begin: Loading essential drivers ... done.Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... done.
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
 * Stopping Send an event to indicate plymouth is up                     [ OK ]
 * Starting Automatically import OpenZFS pools before mountall starts.   [ OK ]
 * Stopping Automatically import OpenZFS pools before mountall starts.   [ OK ]
 * Stopping Read required files in advance                               [ OK ]
 * Starting Mount filesystems on boot                                    [ OK ]
 * Starting Populate /dev filesystem                                     [ OK ]
 * Starting Populate and link to /run filesystem                         [ OK ]
 * Stopping Populate /dev filesystem                                     [ OK ]
 * Stopping Track if upstart is running in a container                   [ OK ]
 * Stopping Populate and link to /run filesystem                         [ OK ]
 * Starting mount available cgroup filesystems                           [ OK ]
 * Starting Signal sysvinit that the rootfs is mounted                   [ OK ]
 * Starting Clean /tmp directory                                         [ OK ]
 * Stopping Clean /tmp directory                                         [ OK ]
 * Stopping Read required files in advance (for other mountpoints)       [ OK ]
 * Starting Initialize or finalize resolvconf                            [ OK ]
 * Starting set console keymap                                           [ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted         [ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted         [ OK ]
 * Starting Bridge udev events into upstart                              [ OK ]
 * Stopping set console keymap                                           [ OK ]
 * Starting Signal sysvinit that local filesystems are mounted           [ OK ]
 * Starting Signal sysvinit that remote filesystems are mounted          [ OK ]
 * Starting Flush boot log to disk                                       [ OK ]
 * Starting flush early job output to logs                               [ OK ]
 * Stopping Flush boot log to disk                                       [ OK ]
 * Starting device node and kernel event manager                         [ OK ]
 * Stopping flush early job output to logs                               [ OK ]
 * Starting load modules from /etc/modules                               [ OK ]
 * Starting cold plug devices                                            [ OK ]
 * Starting log initial device creation                                  [ OK ]
 * Stopping load modules from /etc/modules                               [ OK ]
 * Starting D-Bus system message bus                                     [ OK ]
 * Starting Bridge file events into upstart                              [ OK ]
 * Starting system logging daemon                                        [ OK ]
 * Starting SystemD login management service                             [ OK ]
 * Starting Uncomplicated firewall                                       [ OK ]
 * Starting configure network device security                            [ OK ]
 * Starting configure network device security                            [ OK ]
 * Starting configure network device security                            [ OK ]
 * Starting configure network device                                     [ OK ]
 * Starting Mount network filesystems                                    [ OK ]
 * Starting Failsafe Boot Delay                                          [ OK ]
 * Starting SMB/CIFS File Server                                         [ OK ]
 * Stopping Mount network filesystems                                    [ OK ]
 * Starting Bridge socket events into upstart                            [ OK ]
 * Starting configure network device                                     [ OK ]
 * Starting Mount network filesystems                                    [ OK ]
 * Starting Plex Media Server                                            [ OK ]
 * Starting configure network device                                     [ OK ]
 * Stopping Failsafe Boot Delay                                          [ OK ]
 * Starting Samba Winbind                                                [ OK ]
 * Stopping Mount network filesystems                                    [ OK ]
 * Starting System V initialisation compatibility                        [ OK ]
 * Starting early crypto disks...                                        [ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles                                            [ OK ]
 * Setting up X socket directories...                                    [ OK ]
 * Stopping System V initialisation compatibility                        [ OK ]
 * Starting System V runlevel compatibility                              [ OK ]
 * Starting save kernel messages                                         [ OK ]
 * Starting configure network device security                            [ OK ]
 * Starting KVM                                                          [ OK ]
 * Starting ACPI daemon                                                  [ OK ]
 * Starting configure virtual network devices                            [ OK ]
 * Starting deferred execution scheduler                                 [ OK ]
 * Starting regular background program processing daemon                 [ OK ]
 * Starting automatic crash report generation                            [ OK ]
 * Stopping save kernel messages                                         [ OK ]
 * Starting SMB/CIFS File and Active Directory Server                    [ OK ]
 * Starting MD monitoring service mdadm --monitor                        [ OK ]
 * Starting NetBIOS name server                                          [ OK ]
 * Restoring resolver state...                                           [ OK ]
 * Starting CPU interrupts balancing daemon                              [ OK ]
 * Starting OpenSSH server                                               [ OK ]
 * Stopping cold plug devices                                            [ OK ]
 * Stopping log initial device creation                                  [ OK ]
 * Starting load fallback graphics devices                               [ OK ]
 * Stopping load fallback graphics devices                               [ OK ]
 * Starting save udev log and update rules                               [ OK ]
 * Stopping save udev log and update rules                               [ OK ]
 * Starting enable remaining boot-time encrypted block devices           [ OK ]
 * Starting SMB/CIFS File and Active Directory Server                    [fail]
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
 *
 * Stopping System V runlevel compatibility                              [ OK ]



```

---

### Post by sandyd on 2016-02-15
After restarting, and not running anything, what does
```

ps ax | grep -i "smbd\|nmbd"
```
output.

I've seen instances where there is an error, but the service still starts.

---

### Post by bab1 on 2016-02-15
```
 * Starting SMB/CIFS File and Active Directory Server                    [fail]
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
```

The above means you have at least partially configured Samba to be an Active Directory DC.  Did you mean to do that?  I thought this was going to be a lightly configured standalone file server only.  You will have no end of error messages and quite probably failures with this configuration.

---

### Post by kazz2 on 2016-02-15
> **sandyd said:**
> After restarting, and not running anything, what does
```

grep -i "smbd\|nmbd"
```
output.

I've seen instances where there is an error, but the service still starts.

Issued this command. Waited a few seconds. Issued a ^C. Put sudo in front of it. Still waiting for the prompt to come back.

> **bab1 said:**
> ```
 * Starting SMB/CIFS File and Active Directory Server                    [fail]
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
```

The above means you have at least partially configured Samba to be an Active Directory DC.  Did you mean to do that?  I thought this was going to be a lightly configured standalone file server only.  You will have no end of error messages and quite probably failures with this configuration.

You're absolutely correct. I'm happy to avoid a Domain and a DC like the plague. If there was an option I missed it.

---

### Post by sandyd on 2016-02-15
Embarasing copy/paste error - fixed.

Side Note:

Ubuntu does output that, even if you don't configure it as a directory server.

After a fresh install of Ubuntu 14.04:
[IMG]https://i.imgur.com/PEKo6dx.png[/IMG]

---

### Post by bab1 on 2016-02-15
> **sandyd said:**
> Embarasing copy/paste error - fixed.

Side Note:

Ubuntu does output that, even if you don't configure it as a directory server.

After a fresh install of Ubuntu 14.04:
[IMG]https://i.imgur.com/PEKo6dx.png[/IMG]
I believe the fail message is do to either install via tasksel or running the AD activation script.

I get this (note all the ok listings)```

 * Starting SMB/CIFS File Server                                                                                         [ OK ]
 * Starting SMB/CIFS File and Active Directory Server                                                                    [ OK ]

```
The install is only a standalone file server (NO AD at all)

---

### Post by sandyd on 2016-02-15
I installed it via apt-get if it makes any difference
```

sudo apt-get install samba
```

---

### Post by bab1 on 2016-02-15
> **sandyd said:**
> I installed it via apt-get if it makes any difference
```

sudo apt-get install samba
```
Not to me. if it works for you then it works for me.  It is misconfigured in some way however.

---

### Post by kazz2 on 2016-02-15
I installed Samba during the installation, IIRC. It was a checkbox during install.

Output of the sudo ps ax | grep -i "smbd\|nmbd":

```

 2110 ?        Ss     0:00 smbd -F
 2586 ?        Ss     0:00 nmbd -D
 2692 ?        S      0:00 smbd -F
 9728 pts/1    S+     0:00 grep --color=auto -i smbd\|nmbd



```

---

### Post by bswarm2 on 2016-02-16
It's an incompatibility with SMB versions between Windows 10 and everything else. There are workarounds, but they're not recommended for the most part. This is something we have to wait for MS to fix.
[https://lists.samba.org/archive/samba/2015-September/193886.html](https://lists.samba.org/archive/samba/2015-September/193886.html)

---

### Post by Morbius1 on 2016-02-16
It is not an incompatibility issue with smb versions. When I connect to a Linux Samba Server ( 14.04 ) from Windows 10 the negotiated smb dialect is SMB 3.0.

It's something messed up with the Function Discovery Platform: From my link above:
> The issue appears that Windows 10 is not broadcasting out an NetBT or  RAP requests *[COLOR=#0000cd]when searching for the devices on the network[/COLOR]* and only uses  WSD protocol. If you navigate to Explorer > Network and changed to  Details view and then add 'Discovery Method'  to the column bar you should see that if you are discovering any  devices they are more than likely only being found via WSD.

The Function Discovery Platform is supposed to go through various protocols to "discover" what's on the network: LLMNR, WSD, SSPD, UPNP, and when all else fails Netbios. Somebody left off Netbios. But that doesn't mean Samba / SMB is broken or that name resolution using Netbios doesn't work - you just have to ask for the machine by name.
> If you are encountering an actual issue accessing a network share (such as inputting \\location\share) that is more than likely a different environment issue.

---

### Post by bswarm2 on 2016-02-16
It is a SMB incompatibility, you'll have to wait for MS and Linux to fix it on their side, or do one of the workarounds until then. You can force Windows 10 to only use SMBv1 to get Linux network shares to show up in Windows, but it's not recommended. I did the workaround as described in the link, and it does work.

"[COLOR=#000000]Windows 10 will try to negotiate SMB3_11, which Samba4 doesn't yet support [/COLOR][COLOR=#000000]except in the current 4.3 release candidate. I suspect for now disabling [/COLOR][COLOR=#000000]SMB2/3 on the Windows 10 client is your best, if not ideal, option."[/COLOR]

---

### Post by Morbius1 on 2016-02-16
Lordy lordy. Everything becomes a debatable issue on a forum.

I connect to a Xubuntu 14.04 machine with a \\xub1404\downloads from Windows 10.

I then open up Power Shell on Windows 10 to inspect the details of the connection:
> Windows PowerShell
Copyright (C) 2015 Microsoft Corporation. All rights reserved.

PS C:\WINDOWS\system32> Get-SmbConnection | Select ServerName,ShareName,Dialect

ServerName ShareName Dialect
---------- --------- -------
xub1404      downloads 3.0
If there was an SMB dialect incompatibility I wouldn't be able to connect. And I certainly wouldn't be able to connect at SMB 3.0.

---

### Post by bswarm2 on 2016-02-16
No debate intended.
I wasn't talking about not connecting. Windows 10 connects to Linux shares just fine, you just can't see them unless you enter the IP address or the computer name in explorers address bar. As the OP stated, the shares aren't showing up automatically like they did in previous versions of Windows. I've been chasing this problem since Windows 10 came out, and it's a mess. There are many workarounds that I've tried, the only one that worked was forcing Windows to only use SMBv1.

---

### Post by kazz2 on 2016-02-16
Yes. If I define a shortcut on Win10 (or a network drive, I imagine) with the hostname and/or ip address plus the share name it works. If I browse for the host and it's shares, the host doesn't appear. I'm working simply because I've created shortcuts. I look forward to MS/Linux ironing the problem out by then. I've tried many of the workarounds and they aren't successful for me.

But, again, I'm good for now.

---

### Post by Morbius1 on 2016-02-16
The good news is it's fixed: Again from MS employee ARUDELL:
> I wanted to let you know that we were able to identify the issue and  ultimately find out that a fix was already in the works and checked into  our latest builds. I tested on build 11103 in my environment and  confirmed that the machine is able to find other  devices on the networking using both NetBIOS and WSD when performing  Network Discovery.

 I see that 11102 is available for WIP so it should be contained within that build image as well. 

The bad news is when it will trickle down to the retail user is undetermined:
                 >                      I am in discussions with the PG right now to understand a possible ETA on when fix will be available. I'll keep you posted.

[HR][/HR]Adam Rudell | Windows Networking Beta | Microsoft Corporation

                                           
                                                                                 Tuesday, January 26, 2016 4:05 PM


---

### Post by kazz2 on 2016-02-16
Yes, read that as well. We're all supposed to be patient. :popcorn:

---

### Post by 1clue on 2016-02-16
That bug suggests that if your samba is recent enough win10 should connect fine.

I don't use samba at all, but it might not be too difficult to build your own samba from upstream. You might check with current status of the project on the upstream website.

---

### Post by bswarm2 on 2016-02-17
It looks like starting with Ubuntu 16.04, SMB will be updated to v4.3.3 and should work nicely with Windows 10.
[http://packages.ubuntu.com/search?keywords=samba](http://packages.ubuntu.com/search?keywords=samba)

---

### Post by Morbius1 on 2016-03-01
@kazz2,

I don't know if you are still alive and well out there but I just installed two Win10 updates today and one of them fixed this issue:

Cumulative Update for Windows 10 Version 1511 (KB3140743)
Update for Windows 10 Version 1511 (KB3139907)

I suspect it was the second one - but let's face it one doesn't really know any more what's in these updates.

If I run winver I'm now at 
> Version 1511 (OS Build 10586.122)

No need to disable smb2/3 and such ( and I'm still with Xubuntu 14.04 ) since it works as it always did.

Mind you,  I'm actually afraid to reboot Win10 for fear it will come back broken again but ....

---

### Post by kazz2 on 2016-03-01
LOL - enjoying the humor in your post. In order for comedy to work there must be some nugget of truth in it, eh?

At the moment I've decided to move my server to different hardware so that all the drivers are already baked into Ubuntu. I have a processor upgrade for the motherboard. But when I started disassembling it I realized the cooler for the CPU wasn't ideal. One will be here in two days, according to Amazon. Can't even find a CPU cooler in a town of over 100,000. Odd.

At any rate, thanks for the heads-up. I'll check it after I have the server back up and running. It will be nice to be able to browse Samba shares as it was intended!

---

