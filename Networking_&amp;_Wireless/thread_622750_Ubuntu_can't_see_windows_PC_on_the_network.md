---
title: "Ubuntu can't see windows PC on the network"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by The Pinny Parlour on 2007-11-25
Hi

How does Ubuntu see windows PC's on the network?  With each release of Ubuntu, networking is the thing that just never seems to work reliably.  Last 3-4 releases I have had major issues with networking, it just hardly works.   Can anyone show me how to make it work please?  

It worked up until recently, there where some updates which I installed and that seems to have borked it.  Places>Network>windows Network>  nothing  grrrr.

Thank you.

---

### Post by wjp.reg on 2007-11-25
It's difficult to make any suggestions as you don't give any details about your setup.  What are we to assume?  That you have samba installed? Is there a workgroup set up on Windows? Have you got a username/password setup on Windows?

Can you show us your /etc/samba/smb.conf file too.

If you see no workgroups it suggests you haven't set one up.

Here's a [Samba Wiki]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by sartic on 2007-11-25
> **wjp.reg said:**
> It's difficult to make any suggestions as you don't give any details about your setup.  What are we to assume?  That you have samba installed? Is there a workgroup set up on Windows? Have you got a username/password setup on Windows?

Can you show us your /etc/samba/smb.conf file too.

If you see no workgroups it suggests you haven't set one up.

Here's a [Samba Wiki]("https://help.ubuntu.com/community/SettingUpSamba")

My friend got same problem. I didn't get any idea why because samba is configured as mine. He got xfiles problems like i width lowend machine (slow transfer from xp to linux, reverse ok). So he decide to update to gutsy, after few resolved problems he lost connection to xp machines he can only see workgroup nothing inside (he pings all machines in that lan). He is so mad, his words "why linux when i can not use simple stuff as lan?" He stuffed disk width important files, so he is now burning all files and then he will  make retro 2 winblows.

---

### Post by The Pinny Parlour on 2007-11-25
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
   workgroup = MSHOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

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

# Put a capping on the size of the log files (in Kb).
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
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

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
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


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
;
; The following was the default behaviour in sarge
; but samba upstream reverted the default because it might induce
; performance issues in large organizations
; See #368251 for some of the consequences of *not* having
; this setting and smb.conf(5) for all details
;
;   winbind enum groups = yes
;   winbind enum users = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
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
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

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

---

### Post by wjp.reg on 2007-11-25
So it would appear you have referenced a Windows workgroup named MSHOME.

Have you set any folders as shared in windows?  You don't have any ubuntu shares defined.

Do you have smbfs installed, along with smbclient and samba?

---

### Post by The Pinny Parlour on 2007-11-25
> **wjp.reg said:**
> So it would appear you have referenced a Windows workgroup named MSHOME.

Have you set any folders as shared in windows?  You don't have any ubuntu shares defined.

Do you have smbfs installed, along with smbclient and samba?

It would?

Yes

???? No idea what *smbf*s  etc even is.

---

### Post by The Pinny Parlour on 2007-11-25
All I know is I installed Gutsy at the end of October.  All worked fine.  Some recent updates appear to have borked it.   :mad:

---

### Post by wjp.reg on 2007-11-25
> **The Pinny Parlour said:**
> All I know is I installed Gutsy at the end of October.  All worked fine.  Some recent updates appear to have borked it.   :mad:

Works fine here.

---

### Post by The Pinny Parlour on 2007-11-25
> **wjp.reg said:**
> Works fine here.

Lucky you.  Thanks for trying.

---

### Post by The Pinny Parlour on 2007-11-25
Bump

---

### Post by heat84 on 2007-11-26
That Samba Wiki needs updating or something because it says: Tick Enable Windows networking on the general tab. But there's nothing to tick on that tab. Infact, the whole network network settings window/applet whatever you call it in the wiki is different from the one I have.  

I think the Linux geeks don't wanna see it become mainstream and popular so they're doing (or not doing) anything they can to discourage and make things harder for the rest of us.

I've started a couple threads here and they've ignored me. Don't expect to get any help around here.:mad:

---

### Post by tact on 2007-11-26
> **heat84 said:**
> That Samba Wiki needs updating or something because it says: Tick Enable Windows networking on the general tab. But there's nothing to tick on that tab. Infact, the whole network network settings window/applet whatever you call it in the wiki is different from the one I have.  

I think the Linux geeks don't wanna see it become mainstream and popular so they're doing (or not doing) anything they can to discourage and make things harder for the rest of us.

I've started a couple threads here and they've ignored me. Don't expect to get any help around here.:mad:

Ya such terrible people around here I am sure.  *chuckle*

Ok from a terrible person first a few general tips.  Specific assistance when some of you with problems give specific information about your setups.  (can't get much more helpful than that huh - and free some more).  hehehe

1.  do remember that windows networking is.... WINDOWS networking.  Linux is not windows and yet trying to give you services that are compatible.

2.  in WINDOWS networking, even between 2 WINDOWS machines on a simple home network, it can  take 40 minutes to have a workgroup appear and machines in the workgroup to appear in the network browsers.  its a function of how WINDOWS peer networking works.  Its no fault of linux or ubuntu.  

3. If it CAN take that long for the results of a good WINDOWS peer network setup to show up all the WINDOWS machines - dont expect linux machines to show up any faster on a WINDOWS network.

(can I stop typing windows in CAPS now?  Hope the point has sunk in.)  ;)

[B](huge cut/edit - barking up the wrong tree.  Cut a lot out and added the below:)

When you go Places>Network do you see the "Windows Network" icon in the folder?  What happens when you double click it?  Do you even one or more workgroups?  When you double click them - what happens?

Nothing?  Not what you expect?
To try and get around any uncertainty that its just windows networking being slow to show shares - Places>Network  in the location bar type:
```
smb://machine_name
```
where "machine_name" is the name of the windows machine you are looking for...

Does that find your windows machine?  If so then the problem is not in your ubuntu config.[/B]

---

### Post by tact on 2007-11-26
deleted - barking up the wrong tree

---

### Post by heat84 on 2007-11-26
I did have it working at one time though.  And I didn't have to do anything to get it working.  I'm not really concerned with Ubuntu shares only being able to see the WIndows PC over the network.

> Ok from a terrible person first a few general tips. Specific assistance when some of you with problems give specific information about your setups. (can't get much more helpful than that huh - and free some more). hehehe
How am I supposed to give specific information if nobody's telling me what specific information I need to give? Apparently none of the "experts" around here are even bothering to read the threads I started anyway.

---

### Post by tact on 2007-11-26
deleted - barking up the wrong tree

---

### Post by tact on 2007-11-26
deleted - barking up the wrong tree

---

### Post by tact on 2007-11-26
> **heat84 said:**
> I did have it working at one time though.  And I didn't have to do anything to get it working.  I'm not really concerned with Ubuntu shares only being able to see the WIndows PC over the network.


How am I supposed to give specific information if nobody's telling me what specific information I need to give? Apparently none of the "experts" around here are even bothering to read the threads I started anyway.

Are your windows and ubuntu machines on the same subnet, and on the same physical segment?
i.e. are all wired connections to the LAN and all via the same hub?   Or are all wireless, connected via the same wifi accesspoint?  How are the ubuntu and windows machines connected?

I once had a problem where I could not see my wife's XP machine shares when she was on wifi and I was on wired - even tho we were on the same LAN subnets.   But when we were both on wifi, or both wired, no problem.   Is your situation similar in any way?

---

### Post by heat84 on 2007-11-26
They're connected via a crossover cable. I forgot about that subnet thing. I'll have to check that. But when I double click on the Windows network icon, nothing happens instead of another window opening. That should indicate what the problem is. 

 I 'm booted into windows right now. I edited  xorg.conf and didn't back it up first:oops:  and now I have no internet access in Ubuntu.

---

### Post by michaelzap on 2007-11-26
Do you have Firestarter installed? I've found that it interferes with accessing shares on my network (Windows and Samba servers), and usually allowing incoming connections from each share's ip address resolves this (although sometimes I've had to open up ports as well). If you stop Firestarter and your shares magically appear, then this is the cause of your problems.

---

### Post by tact on 2007-11-26
> **heat84 said:**
> They're connected via a crossover cable. I forgot about that subnet thing. I'll have to check that. But when I double click on the Windows network icon, nothing happens instead of another window opening. That should indicate what the problem is. 

 I 'm booted into windows right now. I edited  xorg.conf and didn't back it up first:oops:  and now I have no internet access in Ubuntu.

ok... if connected by crossover cable...  I guess you have hardcoded the IP addresses?  You need to have both machines on the same subnet.    This is not a ubuntu limitation - windows networking is not generally routable between subnets.

You can set your ubuntu box up as a WINS server (very easily) and that overcomes the issue.  I do that at home on the LAN and on the corporate WAN.

michaelzap has a point also in that firewall can interfere.  I have mine set up as "permissive by default" for outgoing connections and as a result I can see and access all the windows shares on LAN/WAN but while they can see my ubuntu machine exists on the LAN then get a "no route to resource" if they try to access.

---

### Post by tact on 2007-11-26
The Pinny Parlor - whats happening with you?  All under control?  Give us something to work with and see if we cannot resolve things...

---

### Post by SteveHillier on 2007-11-26
> **heat84 said:**
> How am I supposed to give specific information if nobody's telling me what specific information I need to give? Apparently none of the "experts" around here are even bothering to read the threads I started anyway.

Hang on fella!
Not every one on these fora (yes the plural of forum) are experts.  A lot of us are floundering around just like you.
One day you will have expertise, I just hope you are prepared to share it.

---

### Post by SteveHillier on 2007-11-26
> **tact said:**
> 
1.  do remember that windows networking is.... WINDOWS networking.  Linux is not windows and yet trying to give you services that are compatible.

2.  in WINDOWS networking, even between 2 WINDOWS machines on a simple home network, it can  take 40 minutes to have a workgroup appear and machines in the workgroup to appear in the network browsers.  its a function of how WINDOWS peer networking works.  Its no fault of linux or ubuntu.  

3. If it CAN take that long for the results of a good WINDOWS peer network setup to show up all the WINDOWS machines - dont expect linux machines to show up any faster on a WINDOWS network.[/B]

I think this makes the point very well.  I have spent long hours trying to get stable data exchange between Windows and Linux platforms.  This was not helped by Samba problems in Edgy.  No problem in Feisty & Gutsy and I am working on a domain based Windows network.

The big problem is this.  In the Linux world we expect to see and share data with Windows machines.  In the Windows world it does not like to recognise Linux, therefore they make little effort to accommodate Linux systems.  You might call this short sighted and I would probably agree with you but the reality is that there is no easy solution.  

If you find something that works lets share it on the forum.

---

### Post by tact on 2007-11-26
> **SteveHillier said:**
> I think this makes the point very well.  I have spent long hours trying to get stable data exchange between Windows and Linux platforms.  This was not helped by Samba problems in Edgy.  No problem in Feisty & Gutsy and I am working on a domain based Windows network.

The big problem is this.  In the Linux world we expect to see and share data with Windows machines.  In the Windows world it does not like to recognise Linux, therefore they make little effort to accommodate Linux systems.  You might call this short sighted and I would probably agree with you but the reality is that there is no easy solution.  

If you find something that works lets share it on the forum.

hehehe....  the point I was trying to make there is that even when working with windows boxes on a windows LAN - it can take a very long time before shares/computers appear in network browsers.  It can cause headaches/confusion whether settings are correct and things are working or not - and ubuntu/linux is not even a factor.  :)

Actually I have had great success getting my linux laptop to work/share with windows boxes, from my home LAN that is quite simple, to the corporate LAN/WAN in the office.

I am based in Kuala Lumpur and I need to access shares hosted on corporate servers (windows file shares) in other countries.  It all works nicely - I even have shares located overseas mounting at boot via CIFS automatically if I am in the office on the company LAN, or even in a hotel room once I bring up the VPN.

Hopefully I am able to share whats relevant and working.  If not then I am a poor communicator.  :)

My own experience is that basically it all worked out of the box. (Being able to see, and being seen by, windows PC's on the LAN) Only issues were:
1.  at first - on the corporate LAN I could see and access windows fileserver shares (with zero config effort), but after a few clicks here and there would find my network account auto-locked out and have to ask the network IT boffins to reset it.  Its all to do with how Windows AD domain security is handled. 
(eventually resolved when I stopped following every guide I found, stopped trying to install/configure Samba, LDAP, Kerberos, etc in vain attempts to authenticate to the domain  - and simply ensured that my username/password/domain on my laptop match the corporate username/password/domain)

2.  then there was that weird thing at home where I could only access shares on my wife's XP laptop if we were both on wired, or both on wireless, connections - even tho we had IP addresses on the same subnet.
(resolved by making my machine a WINS server - and even that may be co-incidental!  hehe)

---

### Post by The Pinny Parlour on 2007-11-26
> **tact said:**
> The Pinny Parlor - whats happening with you?  All under control?  Give us something to work with and see if we cannot resolve things...

Sorry mate.   Thank you for your help.  I tried as suggested.  It worked using smb://<insert WinPC IP>


Plot gets thicker. About 15mins after turning on both Linux and Windows PC's, I couldn't get Ubuntu to see windows network. Few hours later, it's working.  I finally got the windows network to eventually show up in the Place>Network>etc....    hmmmm I don't know WTF is going on. It certainly is NOT reliable. It was on for hours last night and still could not see anything. Thanks for the tips and help guys.


I can't explain it, but a friend of mine thinks I may have a MasterBrowser and netbios conflict.  I hope to have him sort it out for me and I will post the results and finding here.

Thank you all for your help.

---

### Post by heat84 on 2007-11-27
I booted into the Live CD session ad I can see the other computer on the network. So I'm gonna figure out everything there where I won't permanantly damage anything.

Is Firestarter necessary? Aren't you running 2 firewalls with it on unless you turn off IPtables? I only need it for ICS and DHCP. I couldn't get those working any other way.

---

### Post by tact on 2007-11-27
> **The Pinny Parlour said:**
> Sorry mate.   Thank you for your help.  I tried as suggested.  It worked using smb://<insert WinPC IP>


Plot gets thicker. About 15mins after turning on both Linux and Windows PC's, I couldn't get Ubuntu to see windows network. Few hours later, it's working.  I finally got the windows network to eventually show up in the Place>Network>etc....    hmmmm I don't know WTF is going on. It certainly is NOT reliable. It was on for hours last night and still could not see anything. Thanks for the tips and help guys.


I can't explain it, but a friend of mine thinks I may have a MasterBrowser and netbios conflict.  I hope to have him sort it out for me and I will post the results and finding here.

Thank you all for your help.

Yer....there are settings inside the samba configuration file for netbios and network browser elections ..  if you toyed with them at all you could be causing yourself grief.

If you have the original samba config file maybe revert to that.

---

### Post by tact on 2007-11-27
> **heat84 said:**
> I booted into the Live CD session ad I can see the other computer on the network. So I'm gonna figure out everything there where I won't permanantly damage anything.

Is Firestarter necessary? Aren't you running 2 firewalls with it on unless you turn off IPtables? I only need it for ICS and DHCP. I couldn't get those working any other way.

Firestarter is uses/configures iptables.  iptables is still the real firewall beneath firestarter (or guarddog et al).

---

### Post by heat84 on 2007-11-27
Ok everything's working except for being able to see the Windows computer on the network again. Nothing happens when I double click on the Windows Network. Another window is supposed to open but that's not happening. Right now I don't have Samba installed. The last 2 times Iinstalled it, my internet connection stopped working. I'm sure it'll happen again unless I figure out why it happened the last 2 times.

---

### Post by tact on 2007-11-27
> **heat84 said:**
> Ok everything's working except for being able to see the Windows computer on the network again. Nothing happens when I double click on the Windows Network. Another window is supposed to open but that's not happening. Right now I don't have Samba installed. The last 2 times Iinstalled it, my internet connection stopped working. I'm sure it'll happen again unless I figure out why it happened the last 2 times.

What happens if you open Places>Network and in the location bar you manually type in:
smb://win_pc_name

If that doesnt work... type in:
smb://111.222.333              <- replace with your windows machine IP address

While you are at it - what happens when you ping the windows machine:
- by name?
- by number?

No firewall getting in the way?

---

### Post by heat84 on 2007-11-28
**smb://win_pc_name:**  Nautilus cannot display "smb://alan".
**smb://192.168.0.122:** Nautilus cannot display "smb://192.168.0.122"
**ping computer name:** unknown host alan
Pinging the IP address works fine.

I read somewhere else to try installing another network browser. So I installed Smb4k but it still wasn't working.


Also, there's something called a DCOP server and its not running. Could that be the problem? I think this is why Kweather isn't updating anymore.

> root@Server:~# dcop KWeatherService WeatherService updateAl
ERROR: Couldn't attach to DCOP server!



BTW, once again I installed Samba and once again it killed my internet connection.


Another weird problem I've been having the last 24 hours or so is everytime I go to install a synaptic package, it says it can't be authenticated.

---

### Post by tact on 2007-11-28
> **heat84 said:**
> **smb://win_pc_name:**  Nautilus cannot display "smb://alan".
**smb://192.168.0.122:** Nautilus cannot display "smb://192.168.0.122"
**ping computer name:** unknown host alan
Pinging the IP address works fine.
[...]
Another weird problem I've been having the last 24 hours or so is everytime I go to install a synaptic package, it says it can't be authenticated.

You mentioned in another post that u r connecting the 2 computers by crossover ethernet cable. 

Sorry if this is a dumb question... How are you connecting the ubuntu box to internet?  (for the synaptic packet manager etc)....    Are you using the windows machine to  connect to internet and do some internet connection sharing or something across the cable to the ubuntu box?

Or is it just the two PC's connected together only - by the crossover cable?  No other connections..

I will whip out my trusty crossover cable and see how it all works here....

---

### Post by tact on 2007-11-28
This isn't going to help much at all but here is what I just tried...

- Got my ubuntu 7.10 laptop and my wife's XP laptop on the same table.
- Right clicked on my "nm-applet" icon and disabled networking (basically took networkmanager out of the game temporarily)
- disabled firestarter
- connected the two PC's via crossover ethernet cable
- clicked on System>Administration>Network and used the gui to configure eth0 (wired) connection for IP address 192.168.0.3 and netmask 255.255.255.0

On the XP machine:
Configured ethernet port for IP address 192.168.0.1    255.255.255.0

Opened a terminal on both machines and pinged by name and IP address.  Worked fine

Opened Places>Network on the ubuntu box...  could see and browse both machine's shares

Opened Network places on the XP box and could see and browse shares on both machines.

(Note:  Not for this test - My ubuntu machine already had winbind installed and my samba.conf and nsswitch.conf were both configured to make my ubuntu box a WINS server...  so maybe thats the difference....)

Sorry if none of this gives any help....



How are your network interfaces actually configured on the XP box and ubuntu box?  Hardcoded IP addresses?  etc...

---

### Post by heat84 on 2007-11-28
Wow you didn't have to do all that just for me. Thanks.

I'm thinking with all things that aren't working, I should just reinstall Ubuntu.I don't suppose theres anyway to do a repair instead.


As for my setup, I connect to the internet via the Ubuntu PC. I have my  modem in bridge mode because its not P2P friendly otherwise, So I had to use PPPOECONF and then PON automatically on every startup. I use DHCP to connect to the Windows PC. The Ubuntu PC has a static IP address.

---

### Post by SteveHillier on 2007-11-29
> **heat84 said:**
> I'm thinking with all things that aren't working, I should just reinstall Ubuntu.I don't suppose theres anyway to do a repair instead.


There is no repair function in Gutsy, but I did put forward the idea and it has been taken forward as an idea for Hardy Heron, or is it Hairy Heron, or Heartless Heron.  Anyway it's a Heron of some sort that come to us next.
BFN

---

### Post by heat84 on 2007-11-29
Well it doesn't matter now. I went ahead and reinstalled.

---

### Post by tact on 2007-11-29
> **heat84 said:**
> Well it doesn't matter now. I went ahead and reinstalled.

...and the result is?   Got it all going again as you wanted?  Hope so.  :)

Just remember that there is no need to follow many of the millions of guides out there that get you installing a lot of stuff.   If all you want to do is share folders with windows users all you have to do is right click on the folder and select sharing and let your system install what it needs.

Those guides were right those days...  and for more complicated stuff (like trying to authenticate to a windows domain controller) that go beyond just sharing folders.

So many times i have googled or searched these forums and found hundreds of guides for whatever it is I am trying to do at the time - and too often there are so many guides it gets confusing and too many times I find out later that following any of the 101 complicated guides was total overkill - there was a simple and painless (new) method with ubuntu (7.04 or 7.10).

Noted how you are configured.  My DSL modem is connected to a wired/wireless router that can do the PPPOE dialup for me.  So I do not have to configure any of my PC's as a PPPOE dialler.  

The router also does the DHCP stuff for the internal network as well.  Ohhh and its a good hardware stateful packet inspecting firewall too, and print server too.   *chuckle*  So the router, DSL modem and printer sit on a corner of the desk connected 24x7.   My wife and I then just open our laptops and have broadband, and printer access,  anywhere in the house.

---

### Post by heat84 on 2007-12-02
Well I was still having no luck so I tried OpenSUSE and had more of the same problems. So then I tried PCLinuxOS and got it all working very easily.[IMG]http://www.miamiheatwave.com/forums/style_emoticons/default/dancing.gif[/IMG]

I had intended to try other distros anyway.

---

### Post by The Pinny Parlour on 2007-12-03
Still outstanding issues for others I read.   Samba really is a dog sometimes.  In all my time using Ubuntu I have NEVER EVER had Samba working reliably and for any length of time working, (it always just stops one day for whatever reason).  It ALWAYS has some issues where it just refuses to see MS PC's.  
Thankfully it's working at the moment, but who knows for how long.

---

### Post by dutch1918 on 2007-12-03
comment out this line:

; bind interfaces only = true

and it should work

---

