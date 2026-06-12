---
title: "Samba and Feisty don't play nice!"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by Alcopops on 2007-08-07
Hi,

I'm having trouble with samba on Feisty, it defaults to the domain MSHOME whereas the xp boxes in my house are on a workgroup called "workgroup". So I changed MSHOME to workgroup in smb.conf (as sudo) and this seems to have broken samba. Now when I try to browse the network on my linux box there are no servers listed (before I could see the linux box was working on, called "jaime-desktop" and my linux laptop called "jaime-laptop";  now I cant see either, just a globe called windows network which returns no files when clikcked). Restarting samba did not help, nor did setting security to "share" in smb.conf. I even tried reinstalling samba and it's components but to no avail. About all I can do is manually connect to a server in ubuntu by specifying the server name. I can also mount shares in ubuntu via the terminal.

I suspect samba is working on some level since I can mount network shares with my linux boxes. However I would like to be able to browse the machines by clicking on the  network icon, and my housemates would like to access my shared folders from xp boxes At the moment some can see my machine in their network places window, but clicking it just gives a message about access being denied.

as far as I can tell on the forums this is not a widely known bug, has anyone encountered a similar problem, does anyone have a fix for it.

Cheers,

Jaime

---

### Post by noob12 on 2007-08-07
Hmm.  I run mine on a workgroup that is not MSHOME.  I'm on Feisty desktop edition and using the standard Samba distro from Feisty.  I haven't seen this issue.

I suspect you may inadvertently have introduced some other minor syntax error into the smb.conf file.  Try running **tail -f /var/log/samba/log.smbd** while restarting Samba, see if it spits out any sign of unhappiness.  Also you could try starting smbd manually in non-daemon debug mode.

EDIT:  If you post your smb.conf, I can review it.

---

### Post by Alcopops on 2007-08-07
Hi, 

Thanks for the reply,

I ran  <tail -f /var/log/samba/log.smbd>  and restarted samba with <sudo /etc/init.d/samba restart>

It spits out the following

smbd version 3.0.24 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2007/08/07 21:28:10, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2007/08/07 21:28:10, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!

not sure how to start samba manually in non-daemon debug mode.

My smb.conf file is shown below.

----------------------------------------------------------------------------------

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
   workgroup = workgroup

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
   security = share

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


[Pictures]
path = /home/jmassane/Pictures
available = yes
browsable = yes
public = yes
writable = no

[TV]
path = /media/hda1/TV
available = yes
browsable = yes
public = yes
writable = no

[Music]
path = /media/hdb1/Music
available = yes
browsable = yes
public = yes
writable = no

[Movies]
path = /media/hda1/Movies
available = yes
browsable = yes
public = yes
writable = no

-----------------------------------------------------------------------

testparm returns:

Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Pictures]"
Processing section "[TV]"
Processing section "[Music]"
Processing section "[Movies]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[Pictures]
        path = /home/jmassane/Pictures
        guest ok = Yes

[TV]
        path = /media/hda1/TV
        guest ok = Yes

[Music]
        path = /media/hdb1/Music
        guest ok = Yes

[Movies]
        path = /media/hda1/Movies
        guest ok = Yes
-----------------------------------------------------------------------

Hope you can spot something here

Many thanks,

Jaime

---

### Post by noob12 on 2007-08-07
Can you post the output of **netstat -utnl**

---

### Post by Alcopops on 2007-08-07
That would be:

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:58068           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:8760            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:795             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:46622           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN     
udp        0      0 0.0.0.0:32768           0.0.0.0:*                          
udp        0      0 0.0.0.0:2049            0.0.0.0:*                          
udp        0      0 0.0.0.0:32770           0.0.0.0:*                          
udp        0      0 0.0.0.0:32771           0.0.0.0:*                          
udp        0      0 192.168.0.4:137         0.0.0.0:*                          
udp        0      0 0.0.0.0:137             0.0.0.0:*                          
udp        0      0 192.168.0.4:138         0.0.0.0:*                          
udp        0      0 0.0.0.0:138             0.0.0.0:*                          
udp        0      0 0.0.0.0:792             0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:870             0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:111             0.0.0.0:*   

Cheers,

Jaime

---

### Post by noob12 on 2007-08-08
Looks fine.  Haven't seen any problem so far.  Check for firewalls: **sudo iptables -nL**

---

### Post by Alcopops on 2007-08-08
Hi, cheers for looking I will check iptables when I get home. On the windows side it made no difference if firewalls were on or off, I could still see the server machine in network places but get an access denied message when I attempt to browse it. The only other firewall is on my adsl modem/router but since all the machines are "behind" this, it shouldn't be getting in the way, should it?

---

### Post by noob12 on 2007-08-08
Do check the firewall thing.

I tried duplicating the behavior you described.  I was able to duplicate what sounds like the same local Nautilus behavior  by switching the workgroup setting,  but this was apparently because Nautilus somehow gets out of sync.  Restarting my whole session via CTRL-ALT-BACKSPACE brought Nautilus back in sync.  The server was always fine.

---

### Post by Alcopops on 2007-08-08
Hi,

Output from sudo iptables -nL is below

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

I tend to agree that the sever is OK because I can manually mount shares on other Linux boxes. Browsing them graphically from within ubuntu is hit and miss though. One thing I have found is that if  I  mount a server's own shares using connect to server in the places menu this somehow makes the server browsable again. If I unmount a the server by right clicking on the desktop icon and choosing unmount then the server can no longer be browsed graphically (it disappears from the network window). The above applies only when you mount a share on the box that holds that sharet in the first place (so you would not do this in the normal course of events). Nothing I've done makes the server accessible in windows.

Thanks for all the help so far, if it's a bug, and not just me screwing something up I'm surprised its not been reported. But I've done quite a bit of searching and not found the problem reported elsewhere.

Cheers,

Jaime

---

### Post by MetalMusicAddict on 2007-08-08
I think its case-sensitive. Change it to **WORKGROUP**. Also make sure it says WORKGROUP in the Networking application.

---

### Post by Alcopops on 2007-08-09
This works..to a degree.  Changing to upper case in the smb.conf file and entering WORKGROUP in network admin makes my server browsable by other linux boxes, but not by my windows box. Also the window where you specify the WORKGROUP domain in system>administration>networking keeps clearing itself so I have to keep entering workgroup all the time.  Does that gui write to a config file that I can edit manually or do I need to do something else.

I appreciate all the help, I think we are getting closer to a solution,

If I can just get windows to play nice as well.

cheers,

Jaime.

---

### Post by noob12 on 2007-08-09
It actually writes to your /etc/samba/smb.conf (!)  (I assume you're talking about the panel System | Administration | Shared Folders | General Properties..

---

### Post by Alcopops on 2007-08-09
the domain name in smb.conf is stable but when I change the domain name via

system>administration>network

the window in the general tab for my wired connection keeps becoming blank.

I was wondering where this property is written to, since changing it goes someway to solving my problem (although as I said it does not not enable windows sharing)

Thanks,

Jaime

---

### Post by MetalMusicAddict on 2007-08-09
> **Alcopops said:**
> the domain name in smb.conf is stable but when I change the domain name via

system>administration>network

the window in the general tab for my wired connection keeps becoming blank.

I was wondering where this property is written to, since changing it goes someway to solving my problem (although as I said it does not not enable windows sharing)

Thanks,

Jaime

Do you also have Network Manager in use? Is this a wired machine?

---

### Post by noob12 on 2007-08-10
Alcopops:  The sharing window I pointed at is the Samba config.  The domain name in Network Administration refers to your host's configured name service domain suffix, which gets used for a couple of things, mainly it ends up in your /etc/resolv.conf and is automatically appended to unqualified names in DNS lookups.

EDIT:  Also of course, your own host's entry in /etc/hosts

---

### Post by Alcopops on 2007-08-10
MetalMusicAddict: It's a wired machine.
noob12: Thanks 4 the info, next time that window goes blank I,ll check in resolv.conf and see if it has been changed.

---

