---
title: "Unable to browse SAMBA workgroup/clients"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by marx2k on 2007-05-17
Hello. I'm not sure what has changed but I am no longer able to see my SAMBA workgroup

Here is a copy of my smb.conf
```

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

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
;   interfaces =  localhost, eth1

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
   syslog only = yes

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 1

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
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
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
;   socket options =  TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
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
   create mask = 0664

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0775

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


[games]
path = /media/hdb1/games
comment = Emulator ROMS
read only = no
browseable = yes
public = yes
writable = yes
force user = marx2k

[ReadWrite]
path = /home/marx2k/Desktop/ReadWrite
read only = no
browseable = yes
public = yes
writable = yes
force user = marx2k

[Applications]
path = /media/hdb1/Applications
comment = Windows XP Application
read only = no
browseable = yes
public = yes
writable = yes
force user = marx2k

```

smbtree gives me no information: 
```

marx2k@Commodore-64:/etc/samba$ sudo smbtree
Password: 
marx2k@Commodore-64:/etc/samba$ 

```

There is no firewall running:
```

marx2k@Commodore-64:/etc/samba$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

```

Obviously, there are computers set up in the workgroup...
```

marx2k@Commodore-64:/etc/samba$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.11.2    ILPENGUINO     [WORKGROUP] [Unix] [Samba 3.0.22]
192.168.11.4    COMMODORE-64   [WORKGROUP] [Unix] [Samba 3.0.24]
192.168.11.7    LIVINGROOMBUNTU [WORKGROUP] [Unix] [Samba 3.0.24]

```

So I am unsure as to why this would be happening. I am also unable to see the workgroup under Places/Network
The only item in there is Windows Network, and when I go there it gives me nothing under smb:///


I should also mention that I *am* able to mount remote samba shares with smbmount and under fstab so samba functionality is obviously working, I just am unable to browse the workgroup from any of the participating samba servers/clients

Any help would be greatly appreciated!!

[EDIT: By the way, I dont know if this info will help?]
```

marx2k@Commodore-64:/etc/samba$ cat /var/cache/samba/browse.dat
"WORKGROUP"               c0001000 ""                            "WORKGROUP"
"COMMODORE-64"            40819a03 "Commodore-64 server (Samba, Ubuntu)" "WORKGROUP"

```

---

### Post by marx2k on 2007-05-17
I am also seeing this as an issue...
```

smbclient -L livingroombuntu
Password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.24]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       IPC Service (LivingRoomBuntu server (Samba, Ubuntu))
        Movies          Disk      
        Documents       Disk      
        Music6          Disk      
        Music5          Disk      
        Music4          Disk      
        Music3          Disk      
        Music2          Disk      
        Music1          Disk      
        print$          Disk      Printer Drivers
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.24]

        Server               Comment
        ---------            -------
        LIVINGROOMBUNTU      LivingRoomBuntu server (Samba, Ubuntu)

        Workgroup            Master
        ---------            -------
        WORKGROUP            ILPENGUINO

```

ILPENGUINO is a laptop, also in the domain but am not sure why LivingroomBuntu has it as master??

---

### Post by marx2k on 2007-05-17
OK... now it works except... I didnt *DO* anything except look at config files and updated samba to the latest on LivingroomBuntu

But now smbtree and all of the other lookup methods for browsing a workgroup works on both machines. This doesnt make any sort of sense.

While this is obviously a GOOD thing, this could also be bad if it stops working just as mysteriously as it started working.

---

### Post by marx2k on 2007-05-17
Okay, more weirdness...

in smbtree I am able to see the SAMBA network:
```

marx2k@Commodore-64:~$ smbtree
Password: 
WORKGROUP
        \\LIVINGROOMBUNTU               LivingRoomBuntu server (Samba, Ubuntu)
                \\LIVINGROOMBUNTU\IPC$                  IPC Service (LivingRoomBuntu server (Samba, Ubuntu))
                \\LIVINGROOMBUNTU\Movies         
                \\LIVINGROOMBUNTU\Documents      
                \\LIVINGROOMBUNTU\Music6         
                \\LIVINGROOMBUNTU\Music5         
                \\LIVINGROOMBUNTU\Music4         
                \\LIVINGROOMBUNTU\Music3         
                \\LIVINGROOMBUNTU\Music2         
                \\LIVINGROOMBUNTU\Music1         
                \\LIVINGROOMBUNTU\print$                Printer Drivers
        \\C64_SMB_SERVER                Commodore-64 server (Samba, Ubuntu)
                \\C64_SMB_SERVER\LaserJet-5             HP_LJ5
                \\C64_SMB_SERVER\LaserJet-4             LaserJet-4
                \\C64_SMB_SERVER\IPC$                   IPC Service (Commodore-64 server (Samba, Ubuntu))
                \\C64_SMB_SERVER\NintendoDS     
                \\C64_SMB_SERVER\Applications           Windows XP Application
                \\C64_SMB_SERVER\ReadWrite      
                \\C64_SMB_SERVER\games                  Emulator ROMS
                \\C64_SMB_SERVER\print$                 Printer Drivers

```

So far, so good (still not sure how that happened)...

using LinNeighborhood, I am able to see the Workgroup and the client computers for Workgroup

So far so good...

using smb4k I am able to see the Workgroup and the client computers for Workgroup

HOWEVER...

Using good old Nautilus, under Places/Network under Windows Network/Workgroup

All it shows me are the current shares I have on the local computer and not the 2 SAMBA servers on the network

and when I try to click on any of those shares, I get an error dialog: (replace ReadWrite with any of the shares listed)
```

The filename "ReadWrite" indicates that this file is of type "x-directory/smb-share". The contents of the file indicate that the file is of type "desktop configuration file". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "desktop configuration file", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

```

So now the question is... why is Nautilus not showing me the correct information? Why am I not seeing my SAMBA servers under Windows Network?

---

### Post by Fitzcarraldo on 2007-05-19
I have a similar problem. If I click on Places > Network Servers and double-click on the Windows Network icon in the main part of the window, the window that opens has nothing in it. However, it used to display the icons of the other PCs on my home network. Fortunately, some time ago, long before the problem started, I instanced some of the shared folders ("shares") in the Side Pane of the window, so I can still access the shares on some of the other PCs by double-clicking on the small folder icons in the Side Panel, but I would like to be able to see all the PCs in the main window. I have no idea why the PCs suddenly stopped appearing in the window, especially given that, as with you, I can see them and access them using other means. Why Nautilus does not display them in the Windows Network window is a mystery. :confused:  

It has been reported as a bug (see the link to a bug report in _[this](http://ubuntuforums.org/showthread.php?t=430806)_ thread).

There seem to be quite a few threads in the Ubuntu Forums about this problem. I've tried the solutions that some people have stated worked for them, but none have helped me. I'm still hopeful that someone will discover that it's a 'feature' with a work-around rather than a bug, but have lost so much time trying to get it working that I've given up.

---

### Post by macabro22 on 2007-05-22
Yeah, I used to be able to see other network terminals, but now I can't. One more Ubuntu bug. This is getting commonplace.

---

### Post by macabro22 on 2007-05-22
I also can navigate via konqueror but not via nautilus. Seems lika bug.

---

### Post by lox on 2007-05-24
same problem here: konqueror works, nautilus doesn't

---

### Post by noMScraig on 2007-05-25
ok..I can copy files from my xp machines to my shares on my feisty machine.

I can see my SAMBA Workgroup and clients from Ubuntu via

Places --> Network --> Windows Network --> @home (My workgroup)

Unfortunately I CANNOT open any of the machines in my workgroup

The following is my smb.conf...I am trying to start as simple as possible and work from there...any help would be great.


[global]
workgroup = @home
security = share

wins support = no

[Share]
path = /home/craig/Desktop/Share
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by noMScraig on 2007-05-28
Bump...lttle help here!

---

### Post by noMScraig on 2007-05-30
Another low-tech answer to my problem...meaning no editing configs etc.

I tried konquerer to view my network shares and still could not get the shares to work.

I finally loaded smb4k and now I can access my windows shares

I had to configure smb4k to mount the windows shares as a super user (sudo) but now I can view through conqueror.

Anyway, that's how I got it to work.

-c

---

### Post by Suncat2000 on 2007-12-29
Make sure your workgroup computers have access to port **139**/tcp on the Samba server. Otherwise, you'll get the "*<workgroup> is not accessible*" error. Apparently the Windows browsers rely on this NetBIOS service for determining workgroup membership and won't let you at it otherwise :mad:.

Sometimes firewalls will block Windows File and Printer Sharing ports by default. My problem was that I was using the newer 445 port and disabled the older 139 port without knowing it was needed :confused:. Access to the shares worked, but my Samba server wouldn't show up in the browse list. Making sure both ports were enabled solved my problem.

Summary: default ports serviced by Samba are **445 **and **139**. Both are necessary for complete access by Windows (SMB) clients.

---

