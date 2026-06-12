---
title: "dapper winxp samba not playing ball"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by ahh_Jebubs on 2006-10-01
I'm not sure why but recently my Dapper installation has been playing up and my network (plus 3d support on my graphics card) no longer works. It seems to have been since running the updates but I can't be sure. I've been trying to get the network back up for a while now and have had no luck. I don't care about the graphics card, I just want to get my files off this machine.

So I have 1 machine running dapper (192.168.1.1) and 1 running XP pro (192.168.1.2), both connected to my ADSL router. Dapper has no items listed in Windows Network where I could previously see the Windows box. If I alt-F2 and try smb://192.168.1.2/testShare, I get a message saying the contents of the test share folder could not be displayed.

I was following various guides trying to fix it but I probably just made things worse. My smb.conf currently looks like:
```

[global]
    ; General server settings
    netbios name = BILL
    server string =
    workgroup = TEHGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = my_username
    force group = my_username

```

Most of that is from Stormbringers guide posted on the forum (obviously with my_username showing actual username).

On the xp box, if I connect to the workgroup I get a message saying it is not accessible, network path not found. At one stage I could get in and see the Dapper box but couldn't connect, I then went through Storm's guide and changed the smb.conf file and back to square one, workgroup not accessible.
I've tried with and without wins support, and tried mapping network drive with ip/hostname as applicable but it always sais the network path could not be found. 

Can anyone help? I've been searching the net and trying anything to get it going but my patience has totally run out by now.

Thanks for your time.



// edit
Okay, problem half solved. I've now (finally) got access to Dapper from XP and can get my files back. I think I'll go back to XP on both machines, but that's for another day ](*,)

---

### Post by Melcar on 2006-10-01
I'm facing a similar issue with my Ubuntu laptop; Samba just is not working.  Funny thing is that my Kubuntu and Xubuntu PCs all work flawlessly (the Samba part at least).  What's even odder is that Samba on my Ubuntu machine sometimes works and sometimes doesn't, which makes me believe that it's a problem with Samba itself and not an error on my part.  I really don't want to switch to Kubuntu, but network sharing is rather important to me.  I will keep on looking for a fix and post my results here (I made another thread on this particular issue but I guess nobody saw it).

---

### Post by podunk on 2006-10-01
I'm having a hard time with Samba too. 

I have a Kubuntu dapper trying to connect with a Ubuntu Dapper both using a built in Ethernet connection. The machines are on a hub (not a router) which is connected to my dsl modem.

I've followed how tos all over the place and I can't get Samba to work. Is it because I don't have Windows on my network?

Is there another way to connect 2 Linux machines together without installing Apache or something?

Thanks!

---

### Post by tagra123 on 2006-10-01
> **podunk said:**
> I'm having a hard time with Samba too. 

I have a Kubuntu dapper trying to connect with a Ubuntu Dapper both using a built in Ethernet connection. The machines are on a hub (not a router) which is connected to my dsl modem.

I've followed how tos all over the place and I can't get Samba to work. Is it because I don't have Windows on my network?

Is there another way to connect 2 Linux machines together without installing Apache or something?

Thanks!


I had the same problem earlier this week, thank goodness for backups.

[http://ubuntuforums.org/showthread.php?t=267159](http://ubuntuforums.org/showthread.php?t=267159)

NFS sharing should get you up and running quickly.

SSHFS is another way to share but is a little slow for my tastes.

---

### Post by podunk on 2006-10-01
What is so weird about it is - sometimes it's there - sometimes it's not. For some reason the Ubuntu machine can read the Kubuntu machine fairly reliably, but will only share with the Kubuntu machine every once in a while.. 

Sometimes I just click on network and go to the shared folders, and sometimes it asks for a password and user name - and none of the user names password combos I have will work. Sometimes the network is there – sometimes it isn't.

Sometimes the network is there, and you click on a folder and it will say the folder doesn't really exist.

If you reboot both computers at the same time the network will be there for a bit – then it goes away. :-) It's just utterly flaky, I haven't changed a thing while all this is going on.

---

### Post by Melcar on 2006-10-02
What I noticed is that the smb.conf file under Ubuntu (once properly configured) is rather short and simple compared to the ones under Xubuntu and Kubuntu.  What I did was copy the smb.conf file from one of my Xubuntu laptops and transfer it over to Ubuntu, having first made a back-up of the original of course.  Once I made the appropiate changes to the file I rebooted and to my surprise Samba was working (I could now browse and acces my Windows network).  So far everything has been fine.  Here is the actual file I'm using; you are free to use it too, just make the necessary changes.  I still get the "Nautilus not displaying networks" error once in a while, but I can still access my Ubuntu shared folders from my Windows machines.



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
   workgroup = Chiwiworld

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
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
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
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

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
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
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
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

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

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /tmp
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



[Share]
path = /home/to-go/Desktop/Share
comment = Linux share
available = yes
browseable = yes
public = yes
writable = yes

---

### Post by dmizer on 2006-10-02
> **ahh_Jebubs said:**
> Can anyone help? I've been searching the net and trying anything to get it going but my patience has totally run out by now.

Thanks for your time.



// edit
Okay, problem half solved. I've now (finally) got access to Dapper from XP and can get my files back. I think I'll go back to XP on both machines, but that's for another day ](*,)

stick with stormbringers guide.  it's the most comprehensive guide.  if you have problems yet, keep reading through the posts ... someone's likely run into your problem.

second, if you're using dhcp, you need to turn wins support off.

---

### Post by ahh_Jebubs on 2006-10-02
Yep, Stormbringers guide is easy to follow (and much appreciated) but there seems to be something flaky going on somewhere.
I still can't see/connect to the xp box from Ubuntu but mapped a network drive on XP to the Ubuntu shares yesterday. It was still working when I got home today and did a few bits and pieces but was completely dead and couldn't find the network path after I'd gone for dinner. I've now rebooted everything again and it's connected fine.

I've no idea where the problem is but something's not right.

---

### Post by Melcar on 2006-10-02
> **ahh_Jebubs said:**
> Yep, Stormbringers guide is easy to follow (and much appreciated) but there seems to be something flaky going on somewhere.
I still can't see/connect to the xp box from Ubuntu but mapped a network drive on XP to the Ubuntu shares yesterday. It was still working when I got home today and did a few bits and pieces but was completely dead and couldn't find the network path after I'd gone for dinner. I've now rebooted everything again and it's connected fine.

I've no idea where the problem is but something's not right.

That's the same problem I have.  Only under Ubuntu, because my Kubuntu and Xubuntu laptops work flawlessly.

---

### Post by podunk on 2006-10-02
My network is up and running perfectly. Left it on all day.

ah, my ethernet cable was slightly lose. :redface:

---

### Post by Melcar on 2006-10-03
I have to restart both my Windows box and my Ubuntu laptop so they can see each other again.

---

### Post by dmizer on 2006-10-03
> **ahh_Jebubs said:**
> I've no idea where the problem is but something's not right.

once again ... if you are using dhcp on your local network, you'll have to turn wins off:
```
wins support = no
```

it will cause the problems your experiencing.  you will still be able to get netbios name resolution, just your router will have to handle it rather than  your ubuntu box.

i suspect many of the other posters in this thread have the same problem.

---

### Post by Melcar on 2006-10-03
WINS support is off in my case and I still have the same problems.  I just did a freash install of Samba following Stormbringer's guide (again).

---

### Post by ahh_Jebubs on 2006-10-03
> **dmizer said:**
> once again ... if you are using dhcp on your local network, you'll have to turn wins off
Heh, thanks dmizer. My bad, I did still have wins support on (using dhcp) :-\" 

Hopefully that sorts it out.

---

### Post by dmizer on 2006-10-03
> **ahh_Jebubs said:**
> Heh, thanks dmizer. My bad, I did still have wins support on (using dhcp) :-\" 

Hopefully that sorts it out.

hope so too.

@Melcar
> **Melcar said:**
> WINS support is off in my case and I still have the same problems.  I just did a freash install of Samba following Stormbringer's guide (again).
the samba conf file you posted here: [http://www.ubuntuforums.org/showpost.php?p=1570238&postcount=6](http://www.ubuntuforums.org/showpost.php?p=1570238&postcount=6)

is the default conf file from ubuntu.  you'll have to replace it (erase everything that's in it currently) with the one stormbringer gave in the howto.

---

### Post by Melcar on 2006-10-03
> **dmizer said:**
> hope so too.

@Melcar

the samba conf file you posted here: [http://www.ubuntuforums.org/showpost.php?p=1570238&postcount=6](http://www.ubuntuforums.org/showpost.php?p=1570238&postcount=6)

is the default conf file from ubuntu.  you'll have to replace it (erase everything that's in it currently) with the one stormbringer gave in the howto.

I'm using Stormbringer's setup at the moment and still the same problem.

---

### Post by dmizer on 2006-10-04
> **Melcar said:**
> I'm using Stormbringer's setup at the moment and still the same problem.

if you followed the directions exactly, you should have a consistently working samba server.  mine has been up and serving about 30 clients for months.  if you tweaked it in any way, it may cause problems.

if you are able to connect, and you've followed the guide precicely and you still have problems ... i'd suggest looking into other possible causes:
firewall in windows (xp has a built in firewall)?
network card dropping the connection (windows or ubuntu).
bad router (try rebooting it).
bad ethernet cable.
bad ethernet cable connection.

---

### Post by Melcar on 2006-10-06
> **dmizer said:**
> if you followed the directions exactly, you should have a consistently working samba server.  mine has been up and serving about 30 clients for months.  if you tweaked it in any way, it may cause problems.

if you are able to connect, and you've followed the guide precicely and you still have problems ... i'd suggest looking into other possible causes:
firewall in windows (xp has a built in firewall)?
network card dropping the connection (windows or ubuntu).
bad router (try rebooting it).
bad ethernet cable.
bad ethernet cable connection.

All my home PCs have the same firewall (ZoneAlarm) and configured similarly.  Currently I'm only running Linux on my laptops so that may be a problem (but the adapters work perfectly).  Only the laptop running Ubuntu has this problem.

---

