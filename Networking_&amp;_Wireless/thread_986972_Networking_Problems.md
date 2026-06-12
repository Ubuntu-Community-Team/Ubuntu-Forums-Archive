---
title: "Networking Problems"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by HDTimeshifter on 2008-11-19
Ubuntu 8.10

I have Internet access through my router.

Through Nautilus, I can see and copy files to/from XP PCs, but not Vista.  Vista shares show up blank.  I've tried various solutions posted in threads here, but none work.

I shared my printer attached to the Ubuntu PC, but can't access it from XP (haven't even tried from Vista).

I tried to share an Ubuntu folder, but get the following error:
> 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.
After this, when I browed to Network/Windows Network, in addition to my former MSHOME workgroup with my XP and Vista shares, there is now a WORKGROUP workgroup with MAIN share and print$ folder in it.  So I think Ubuntu set up its share as WORKGROUP, but I can't figure out how to rename it to MSHOME.

I installed Virtualbox and XP.  It is able to access the Internet and update XP to SP3.  I used the Networking wizard to set up everything like my other Windows PCs, but it is unable to connect to my MSHOME Workgroup.  When I run IPConfig, it displays IP address and Default Gateway of 10.0.2.x instead of 192.168.1.x like the rest of the Windows PCs on my network.  How do I change this?  When I checked my Ubuntu System/Preferences/Network Configuration and System/Administration/Network Tools, the network addresses appear to be the 192 addresses, not the 10 addresses.

---

### Post by superprash2003 on 2008-11-19
well to access your ubuntu printer from xp, try using the full path of the printer like \\x.x.x.x\printername where x.x.x.x is the ip of the ubuntu machine and printername is the name of the shared printer.. You may have some problems with your current samba setup hopefully this guide should help [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html) . To setup static ip in xp machine ( virtualbox xp).. you could follow this [http://prash-babu.blogspot.com/2008/09/internet-works-on-one-pc-but-not-on.html](http://prash-babu.blogspot.com/2008/09/internet-works-on-one-pc-but-not-on.html)

---

### Post by HDTimeshifter on 2008-11-20
I followed all your instructions on Samba setup.  There is no place to enter the password when I try to turn on sharing in Nautilus, so I tried the command line way as well.  In Nautilus, when I click the checkboxes for 
"Share this folder" and "Allow other people to write in this folder" and click the "Create Share" button, I get the following dialog:

> The folder "Documents" needs the following extra permissions for sharing to work:
  - write permission by others
Do you want Nautilus to add these permissions to the folder automatically?

When I click "Add the permissions automatically", it simply closes the dialog and goes back to the previous dialog, with "Share this folder"...


I also manually set my IP and DNS addresses in my Virtualbox XP.  In Explorer, under Entire Network, MS Windows Network, Mshome I can see my Virtual PC, but not any of my other workgroup PCs.  On my XP PC, under MSHome, I see all my Windows PCs, but not the Virtualbox PC or Ubuntu share.  On the XP PC, I also see a WORKGROUP workgroop with my Ubuntu printer.

In Ubuntu Nautilus, under Network / Windows Network I see both MSHOME and WORKGROUP, but just my other Windows PCs (the Virtualbox XP PC is not added).  Under WORKGROUP, I see MAIN, and print$ when I click on it.  The shaared folder is not showing up.

---

### Post by superprash2003 on 2008-11-20
did you try the command line way correctly?? post output of your smb.conf file..

---

### Post by HDTimeshifter on 2008-11-21
I found the workgroup = WORKGROUP and changed it to workgroup = MSHOME in smb.conf, so now MAIN is now showing up correctly in my MSHOME workgroup instead of WORKGROUP.

In Nautilus, I tried sharing an Ubuntu folder and it worked now.  I turned on Guest access in Sharing Options and I can see one shared folder, but not another one.  I don't know why it works for one, but not the other.

I changed my Virtualbox XP DNS server addresses to match those on my Windows PCs, however, when I tried to use static IP addresses of 192.168.1.x, I lost my Internet connection, so reverted back to "Obtain IP address automatically" and have Internet access again.  I don't know why it's using the 10.0.2.x addresses, unless that's what Ubuntu uses and it has to go through that layer.  I can now see all my Windows shares from Virtualbox XP, however can't see my Ubuntu share from it.  I also can't see my Virtualbox XP share from Nautilus.  That makes it rather hard to share files between Ubuntu and Virtualbox XP on the same hard disk!

Below is my smb.conf file:
> #
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
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
#   workgroup = WORKGROUP
   workgroup = MSHOME

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
security = user   username map = /etc/samba/smbusers

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

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
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

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

[Documents]   comment = Any comment you like   path = /home/roger/Documents   public = yes   writable = yes   create mask = 0777   directory mask = 0777   force user = nobody   force group = nogroup


---

### Post by superprash2003 on 2008-11-21
are the virtual xp and ubuntu able to ping each other?? post output of ifconfig from the ubuntu machine and output of ipconfig from the command prompt of virtual xp

---

### Post by HDTimeshifter on 2008-11-22
No, they are not able to ping each other.  Here is the output of each (I deleted the hardware and DNS addresses since I don't think it's safe to expose those - the Virtualbox XP DNS addresses are static and copied from my other Windows PCs):

Windows IP Configuration





        Host Name . . . . . . . . . . . . : virtualxp


        Primary Dns Suffix  . . . . . . . : 


        Node Type . . . . . . . . . . . . : Unknown


        IP Routing Enabled. . . . . . . . : No


        WINS Proxy Enabled. . . . . . . . : No


        DNS Suffix Search List. . . . . . : hsd1.co.comcast.net.





Ethernet adapter Local Area Connection:





        Connection-specific DNS Suffix  . : hsd1.co.comcast.net.


        Description . . . . . . . . . . . : AMD PCNET Family PCI Ethernet Adapter


        Physical Address. . . . . . . . . : [deleted for security]


        Dhcp Enabled. . . . . . . . . . . : Yes


        Autoconfiguration Enabled . . . . : Yes


        IP Address. . . . . . . . . . . . : 10.0.2.15


        Subnet Mask . . . . . . . . . . . : 255.255.255.0


        Default Gateway . . . . . . . . . : 10.0.2.2


        DHCP Server . . . . . . . . . . . : 10.0.2.2


        DNS Servers . . . . . . . . . . . : [deleted for security]


                                            [deleted for security]


                                            [deleted for security]


        Lease Obtained. . . . . . . . . . : Friday, November 21, 2008 10:44:30 PM


        Lease Expires . . . . . . . . . . : Saturday, November 22, 2008 10:44:30 PM

--------------------------------------------
Pinging 198.162.1.102 with 32 bytes of data:





Request timed out.


Request timed out.


Request timed out.


Request timed out.





Ping statistics for 198.162.1.102:


    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),


==============================================================
ifconfig
eth0      Link encap:Ethernet  HWaddr [deleted for security]  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: [deleted for security] Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1037800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:573617 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:1205246948 (1.2 GB)  TX bytes:96471838 (96.4 MB)
          Interrupt:250 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2082 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2082 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:160937 (160.9 KB)  TX bytes:160937 (160.9 KB)

roger@main:~$ ping 10.0.2.15
PING 10.0.2.15 (10.0.2.15) 56(84) bytes of data.
^C
--- 10.0.2.15 ping statistics ---
381 packets transmitted, 0 received, 100% packet loss, time 381694ms

---

### Post by HDTimeshifter on 2008-11-22
I turned off the Virtualbox XP firewall and thought I could see a shared folder from Nautilus.  I've shared 2 folders:  My Documents and Downloads.  I don't know why, but I could see Downloads, but not My Documents in Nautilus.  For some strange reason, it stopped working and now I have a blank panel.

The same is true in Virtualbox XP.  In Explorer, I can see Ubuntu's main server. Downloads folder and printers, but not the Documents folder.  In fact, if I click on MAIN, I see the same thing.  I checked and both Downloads and Documents have identical file permissions.

---

### Post by superprash2003 on 2008-11-22
there is something wrong with your virtual xp machine's ip.. since your ubuntu machine is getting an ip 192.168.1.102 .. then your xp too should get a 192.168.1.x ip.. try setting the xp ip manually to something like 192.168.1.103 .. and gateway ip as your router ip.
For reference on static ip setup : [http://prash-babu.blogspot.com/2008/09/internet-works-on-one-pc-but-not-on.html](http://prash-babu.blogspot.com/2008/09/internet-works-on-one-pc-but-not-on.html)

---

### Post by HDTimeshifter on 2008-11-23
> **HDTimeshifter said:**
> In Nautilus, I tried sharing an Ubuntu folder and it worked now.  I turned on Guest access in Sharing Options and I can see one shared folder, but not another one.  I don't know why it works for one, but not the other.

I changed my Virtualbox XP DNS server addresses to match those on my Windows PCs, however, when I tried to use static IP addresses of 192.168.1.x, I lost my Internet connection, so reverted back to "Obtain IP address automatically" and have Internet access again.  I don't know why it's using the 10.0.2.x addresses, unless that's what Ubuntu uses and it has to go through that layer.

Well I was going to say again that it didn't work last time I tried it, but tried changing the addresses to 192.168.x.x again and I still have Internet access.  However I still can't see an Ubuntu shared directory from Virtual XP, and vice-versa.  I tried pinging again, and got the same "Request timed out" from Virtual XP, but "Destination Host Unreachable" from Ubuntu this time.

---

### Post by sathiya_at on 2009-01-29
How to configure primary "dns,alternate dns,dns suffix" in ubuntu

---

### Post by HDTimeshifter on 2009-04-01
Well, tonight I turned on my Vista laptop for the first time in months to make sure the virus files were up to date, and I was able to access it from the file browser (just had to enter username and password twice), so I guess one of the Ubuntu updates fixed the problem.

---

### Post by yakuini on 2009-04-01
please help me , iam a newbie for linux system , can you help me on how to network may 2 ubuntu pc and how to share printer and documents, pls. teach me the step by step configuration , kindly send to my email add , [email]ee.ramirez22@gmail.com[/email] . thank you ....

---

### Post by HDTimeshifter on 2009-12-02
After installing several updates last weekend on my server, I can no longer see it on my network.  I rebooted a couple of times and when I open the "computer" window and mount the drives, they show up with Computer Name of :/// instead of the actual computer name.  Under the permissions tab, nothing shows up allowing me to share the drives/folders.  I tried using the terminal command "shares-admin" to share the folders, but they still don't show up in my network.  I can't even see the server on its own Network browser.

---

