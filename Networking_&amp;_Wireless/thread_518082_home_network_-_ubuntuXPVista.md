---
title: "home network - ubuntu/XP/Vista"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by apathy999 on 2007-08-05
Hello all;

First I'd like to say hello to all the members here, as I am new here. I decided to try out Linux instead of XP and as I am new to the system, I have decided to have a dual boot with XP and Ubuntu on this machine. Let me quickly go through my setup here at the house and get to the problem at hand. 
There are three main computers in the house all linked to a router (Linksys). Two desktop machines have wired connections and my laptop has a wireless connection. The main desktop has a dual boot (Ubuntu / Win XP), the other desktop has Win XP  and the laptop works on Vista. Last night I tried to connect the main desktop with Ubuntu to the laptop. I was successful in the fact that I could see the Ubuntu shared files from Vista. I left it at that for now. Next, I tried to connect the two desktops, main on Ubuntu and the other on XP. This did not work. Now, the only way I can see the other desktop in Ubuntu is if the Laptop is on and connected to the network, otherwise no dice. Can anyone help me out here?

---

### Post by MrFSL on 2007-08-05
Sounds like a master browser election issue...

If you aren't familiar, in Windows File Sharing computers hold an election to determine who gets to be the "Master Browser." This person contains the available share information for the network in a table. There is a setting in your smb.conf file something like:
```
; local master = no
```
You might set it to yes to force an election and give the ubuntu box local master or you could disconnect the laptop (which appears to be your local master) and force an election on your Windows box.... (maybe by restarting the file sharing service...) -- I am sketchy on this. I remember back in the Win2000 days there used to be a command line utility put out by M$ to deal with this issue.

Regardless, this is just ONE of the reasons that I discourage the use of Windows File Sharing.

---

### Post by MrFSL on 2007-08-05
Here are a few links dealing with samba, "master browser" configurations, and the Windows Computer Brower service...
[http://support.microsoft.com/kb/188305](http://support.microsoft.com/kb/188305)
[http://support.microsoft.com/kb/188001](http://support.microsoft.com/kb/188001)
[http://art-design.smsu.edu/duss/config/mac/samba/](http://art-design.smsu.edu/duss/config/mac/samba/)

Hope this helps...
Most people think that Windows File Sharing works on a true Peer-To-Peer basis but the lines are grayed. The master browser/local master browser election system really obfusticates things. To avoid this entirely you can force a Master Browser of use a different method to share your files.

---

### Post by apathy999 on 2007-08-05
Ok, I think it might just be something else. I just came back home, turned all the systems on again and now I see nothing. Maybe I should post my previous problems which may spark something. So here it is:
The first problems with the network began with Windows. The first home network I created was one with two computers, both using Windows platform. I created a network by the name of FRIENDS on the XP machine. I followed the simple wizard on XP in order to make the workgroup and basically named the main computer ROSS. After that, I joined the workgroup FRIENDS with my laptop that runs Vista. It worked at first. But the next day, as I turned on both machines nothing seemed to work other than printer sharing. I tried pinging the computers by IP and by name and all worked. Than I tried nbstat -n, which seemed fine on the desktop but not on the laptop, as the line with GROUP seemed to have disappeared. So I thought I might try Ubuntu and Vista, and like I said before, it worked fine the day I made the workgroup. But now I see that both computers seem to be working on the same workgroup, but now once again I can't see anything on the Vista machine. It's like Vista has its moods, sometimes it detects the network and shows the computers, and sometimes nothing. Yet the printer sharing works when XP is running here. So to sum it all up, I don't think it is the Master Browser issue, more of something else with the network. I might try to setup a new workgroup on the XP box and try to connect the Ubuntu and the XP box first. If that works, I will try to add the Vista laptop at the end. Unless anyone has seen issues like this before, or maybe knows another way...? I never had such problems before and I don't know which of the comps is messing it up. Anyway, thanks for the quick replies. ;)

---

### Post by MrFSL on 2007-08-05
Here is some more advise...

get used to using the Windows command line 'net use' command. The frustrating part is that I know exactly what you are going through. Anyone who has ever had to manage a large Windows File Sharing server for any period of time knows exactly what you are going through.

Good luck.

---

### Post by apathy999 on 2007-08-05
The frustrating thing is that the two XP machines see each other, no problem. So now it's only the laptop that seems to have the problem. I doubt that it's the wireless issue, so it must be the Vista issue. I don't mind Vista thus far. Sure, it has it's small bugs at times since it is a fairly new system, but all in all it's ok. But I don't know what it's really doing. Maybe it is setting the master browser, but it doesn't have the browser stat or anything to check that. Or at least no options that I can find... Maybe I should get on some Vista forums and find out more about this issue. For now I will try to set up a network between the two desktops. I'll have to reset the smb.conf file and make some changes there. Ech... this just reminds me of why I switched to Linux in the first place... Everything here seems to be so much simpler. Once I get a hold of all the terminal controls and all, I think life will be so much simpler. :)

---

### Post by apathy999 on 2007-08-06
Here is a newb question... Could someone give me some terminal commands to check the status of the network? So far I have used smbtree to check the connected computers. When I go to 'Places" and 'Network', I can see Windows Network, but nothing inside. I would like to check things like the workgroup that the computer belongs to and the connected computers.

---

### Post by apathy999 on 2007-08-06
Ok, so I setup a new network on XP, called the workgroup 'HOMENET' and added the other XP box (excluded the laptop that works on Vista). Changed the smb.conf to the new settings. I pasted my smb.conf file below and highlighted some of the main things I changed. But as I did that, when I open Places > Network > Windows Network, I find two Workgroups inside (FRIENDS and HOMENET, while before... this folder was empty...) Below the smb.conf I also post the results of my 'smbtree' command.

**smb.conf FILE**

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   [COLOR="Red"]workgroup = HOMENET[/COLOR]

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   [COLOR="Red"]wins support = yes[/COLOR]

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
   security = user

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
   [COLOR="Red"]load printers = yes[/COLOR]

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
   [COLOR="Red"]browseable = yes[/COLOR]

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   [COLOR="Red"]writable = yes[/COLOR]

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


[shared konrad]
path = /home/konrad
available = yes
browsable = yes
public = yes
writable = no

**'smbtree' output**

konrad@ROSS:~$ smbtree
Password: 
HOMENET
FRIENDS
        \\MONICA         
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine MONICA.  Error was NT_STATUS_ACCESS_DENIED
        \\BRAMEL         
cli_start_connection: failed to connect to BRAMEL<20> (0.0.0.0)

P.S. MONICA = laptop, ROSS = the main comp with Ubuntu and BRAMEL = Desktop with XP

---

