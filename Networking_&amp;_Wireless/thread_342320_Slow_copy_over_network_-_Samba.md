---
title: "Slow copy over network - Samba"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by stevenjo57 on 2007-01-19
Well I thought I had everything correct, but found a problem.

Have two machines running edgy.  One is a server with Samba that where I keep all of our documents and data, backed up nicely.  My workstation is mainly for work, but I do store lots of data on the network drive.

Drives are mounted on my workstation from the Samba server and mounted in the FSTAB as follows:

//192.168.0.2/music	/mnt/music cifs credentials=/root/.smbcredentials,dmask=0777,fmask=0777	0	0

They mount nicely, but man is writing to them over the network SLOW!  Today I tried to copy a disk image of 451 mb and it was going to take almost an hour!  Heck I downloaded it from the net faster than that.

The drive are both have gigabit network cards and hooked to a gigabit switch.

Oh, yes and thanks very much to anyone who tries to help.  I'm excited about UBUNTU.  I haven't booted Windows in 3 days and I'm getting most things done quite well.

I thought maybe I had a hdparm problem on the server (the workstation has sata) but the hdparm looks OK? 

Timing cache reads: 786.21 MB/sec
Timing buffered disk reads: 54.90 MB/sec

The network card for the workstation is recognized in the device manager as an RTL-8169 gigabit ethernet card.

So, I'm at kind of loss as to what could be causing this slowdown.

---

### Post by stevenjo57 on 2007-01-19
Just also discovered that only copied from my workstation to the samba shares are slow.

I copied a 691 MB file from the samba share to my workstation in about a minute!  Takes over 50 minutes to go the other way.

Thanks for any help!

---

### Post by msimon1960 on 2007-01-20
The default SAMBA setup has terrible defaults!

edit /etc/samba/smb.conf and find the line 'socket options'

change the line to read:

   socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=8192 SO_SNDBUF=8192

from a terminal line execute:

sudo /etc/init.d/samba restart

Your transfer performance should improve dramatically!

You can experiment with large send and receive buffer sizes -- try doubling 8192 to 16384 and so on until you optimize your system's performance.

I hope this helps.

---

### Post by stevenjo57 on 2007-01-20
Thanks for your help.

I've tried changing those parameters. There may have been some improvements, but there is still something seriously wrong.

I can copy a 691 MB file from the server to the client in just over a minute, but the same file takes 35-40 minutes going the other way.

Right now I am using NFS between the Linux machines, but I still would like to resolve this. I'm going to see if this situation exists between windows clients and the samba servers.

Unfortunately I still have some Windows clients (sniff. sniff.)

---

### Post by stevenjo57 on 2007-01-20
Here is more.

I used the share from a Windows maching and the problem does not exist.

So for what it's worth, the problem could be summarized like this:

Copy 600 MB file from windows client to samba server - < 2 minutes.
Copy 600 MB file from samba server to windows client - < 2 minutes.
Copy 600 MB file from linux samba client to samba server - < 2 minutes.
Copy 600 MB file from samba server to linux samba client - > 40 MINUTES!

Weird.

Thanks for any help.

---

### Post by dmizer on 2007-01-20
well, the above is somewhat confusing, but i think in know what you mean.

just for clarity, any time you have one computer connecting to another the connecting computer is a client, and the computer being connected to is a server.
always: client --> server
never: client <-- server
and never: client <--> server

so we'll ignore the windows machines because they obviously work fine in a proprietary environment that was developed for their use.  so, let's take a closer look at the two linux machines.  you have two computers, one you're calling a samba server, and one you're calling a samba client, but this is incorrect notation as per the above description.

so, i'll use a desktop and laptop notation for clarity.  so, if i understand your situation correctly, you have the following situation:

laptop -> desktop works fine. (ie, you are sitting at the laptop and copy a file to or from the desktop)
desktop -> laptop is slow. (ie, you are sitting at the desktop and copy a file to or from the laptop)

in the second example, the laptop is a samba server, and is hosting shares for the desktop (now a client) to connect to.

so, what we need to see, is the contents of /etc/samba/smb.conf file on the laptop.  otherwise, please correct me if i've made the incorrect assumptions.

---

### Post by stevenjo57 on 2007-01-20
Thank you for your comments, however I'm not sure I understand the distinction. My fault, I'm sure.

Let me try to explain it better.

Machine A is running the samba server.  Machine B is running linux, but mounts a samba share so that it can copy files to the samba server and from the samba server to itself.

When Machine B copies a 600 mb file from Machine A to its home folder, it takes less than two minutes.  However, when Machine B copies the same file from its home folder to a share on Machine A it takes 50 minutes.

Here is the smb.conf file for Machine B which is mounting the samba share being shared by Machine A. As far as I know it should be the default.  The only changes I've made were to the smb.conf on server Machine A.

-------------------------------------------------------------------------------------------

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

----------------------------------------------------------------------------------------------------

Thanks.

---

### Post by dmizer on 2007-01-21
looks to me like you're missing a portion off the end of that smb.conf file.  i don't see any active shares listed.

also with machine B, how are you mounting the share?  nautilus? fstab?  and what protocol are you using (smbfs, cifs)?

---

### Post by stevenjo57 on 2007-01-21
Thank you for your help.

The smb.conf file is on the "client" linux machine.  The one that is mounting the samba share.

I am mounting it as a smbfs share and using nautilus for the copy.

---

### Post by dmizer on 2007-01-21
okay ... let's take a peak at the smb.conf file on the host machine as well.

please encase your smb.conf file in [code] markups so that your post doesn't scroll to infinity.

does either your host or your client have a firewall (eg. firestarter) enabled?

---

### Post by Truster on 2007-02-15
hello.

i have almost the same problem using an W2K3 as PDC and Fileserver

Transfer from my Linux WS to PDC is very fast
Transfer from PDC to my Workstation is horrible slow (300kb/s)

This happens only, when i try to transfer the data over VFS in Konqueror (smb://plah/plah).

If i do a smbmount, it works correctly

---

### Post by dmizer on 2007-02-15
no ... i think your problems is probably different because you have a mixed network. the op had an all linux network.

smbmount is the only way to go.  if that works, add the mount command to /etc/fstab and call it good ... don't use vfs in konqueror.

you'll also likely have much more speedy results if you try cifs instead.  second link in my sig.

---

### Post by siikah on 2007-02-26
I think I have exactly the same problem with my Workstation running Edgy. I also have two boxes running Windows XP.

My fileserver is running Debian (etch).

SMB To server from workstation (WinXP) = 100-150Mbps
SMB To server from workstation (Edgy) = 250-300Mbps
FTP To server to workstation (Edgy) = 250-300Mbps
     SCP To server to workstation (Edgy) = 80-100Mbps

SMB From server to workstation (WinXP) = 100-150Mbps
SMB From server to workstation (Edgy) = **0,4 - 1,0Mbps**
FTP From server to workstation (Edgy) = 250-300Mbps
SCP From server to workstation (Edgy) = 100-120Mbps

I've tried mounting the shares as both smbfs and cifs. No difference.

As you see, the problem for me occurs while using Samba *from* server to Edgy, no problems with the opposite direction.

The REALLY weird thing is this:
If I run ANY other bandwidth-intensive task while copying the "slow files" (Debian -> Edgy) the speed jumps to much higher speeds ~80-120Mbps. What I'm talking about is such tasks as running iperf towards some server (or the Debian-one for that matter), copying from/to a WinXP-box to the Edgy-workstation or anything.

**stevenjo57:** It'd be great if you could try running an iperf while copying the direction which is slow for you and see if the speed gets better.

I really don't have a clue why this happens, but it's probably the most annoying thing I've ever stepped across while using Linux. Don't know if there are some strange queues which behave weird with Samba... :confused:

---

### Post by dmizer on 2007-02-27
siikah ... can you post your smb.conf from your debian server, as well as the mount command (from fstab if applicable) on your edgy workstation please?

also ... what are ping times like from your debian server to your edgy workstation?

anyone here using opendns dns servers by chance?

---

### Post by siikah on 2007-02-27
> **dmizer said:**
> siikah ... can you post your smb.conf from your debian server, as well as the mount command (from fstab if applicable) on your edgy workstation please?

also ... what are ping times like from your debian server to your edgy workstation?

I'm not using any local dnsserver.

192.168.0.123 = debian server
192.168.0.137 = edgy workstation

#/etc/fstab (client)
```

//192.168.0.123/320 /mnt/160 cifs credentials=/etc/samba/clientsettings-twig,uid=1000,iocharset=utf8 0 0
//192.168.0.123/320 /mnt/320 cifs credentials=/etc/samba/clientsettings-twig,uid=1000,iocharset=utf8 0 0

```
#/etc/smb.conf (server)
```

[global]
   workgroup = family
   server string = %h server (Samba %v)
   dns proxy = no

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

   socket options = TCP_NODELAY 

[homes]
   comment = Home Directories
   browseable = no
   writable = no
   create mask = 0760
   directory mask = 0700

[160]
   path = /mnt/160
   locking = yes
   public = yes
   writable = yes
   mangled names = yes
   hide unreadable = yes
[320]
   path = /mnt/320
   locking = yes
   public = yes
   writable = yes
   mangled names = yes
   hide unreadable = yes

```ping 192.168.0.123 -c 50
```

--- 192.168.0.123 ping statistics ---
50 packets transmitted, 50 received, 0% packet loss, time 49007ms
rtt min/avg/max/mdev = 0.125/0.150/0.165/0.019 ms

```

---

### Post by matt91 on 2007-02-28
i am having these same problems. reading is fine and full speed however writing to ubuntu server with xp or ubuntu is slow. my config files are basicly the same as what these are.

---

### Post by sliipy on 2007-03-27
I'm experiencing the same problem.
I have a Windows XP client (tried with other machines, linux/windows aswell) and a Ubuntu Feisty (was dapper and edgy before, same problems) Fileserver.

When i copy files from the server to the client i get ~30-40MB/s (megabytes/sec)
When i copy files from the client to the server i get ~2-6MB/s

The strange thing is, that when i run strace -p [pid of smb user process] while copying files from client to server i get ~20-30MB/s

I have disabled IPV6 by blacklisting the module, didn't help.
I have tried playing around with socket options with no/little change.

It seems like when samba is running in the background i get slow transfers (since strace -p puts the process in the foreground).
BUT i have tried running samba in the foreground using the -i command line switch without any change of speed.

The server ran gentoo linux before using the very same smb.conf with full speed.
Can it be something in the kernel?

Seems like lots of people has this kind of problems, would be nice if we could find a sollution once and for all.

Thanks!

Here's my smb.conf:


```

root@elefant:~# cat /etc/samba/smb.conf| grep -v ^\;| tr -s [:space:]
[global]
 workgroup = katlan
 netbios name = elefant
 server string = elefant
 log file = /var/log/samba/log.%m
 max log size = 50
 hosts allow = 192.168.69. 127.
 security = user
 encrypt passwords = yes
 smb passwd file = /etc/samba/smbpasswd
 socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=8192 SO_SNDBUF=8192
 local master = yes
 domain master = yes
 preferred master = yes
 dns proxy = no
[homes]
 comment = Home Directories
 browseable = no
 writable = yes

```

---

### Post by dmizer on 2007-03-28
well frankly, it turns out that after testing, i'm having the same problem.

unfortunately i haven't had time to work on a solution for this yet as i've been pulling 13 hour work days.

i am still watching this thread, and if i find something i'll post.

---

### Post by beazer on 2007-04-03
Hi

We have had significant speed increases (particularly with some apps that use flat file databases) when we removed 

[code] SO_RCVBUF=8192 SO_SNDBUF=8192 [code]

from the socket options.  Ours looks like

[code] socket options = TCP_NODELAY [code]

There is a thread in the samba mailing list at lists.samba.org where they say that modern kernels are better at choosing these values automatically, and the 8192 stuff is a hangover from ancient history.

Cheers
Rob

---

### Post by fyleow on 2007-04-08
Any progress on this issue?  I have the same problem as well.

---

### Post by cobray on 2007-04-08
I have this same probelm...however
I think the problem may be related to the Realtek hardware/driver.

I think it may be the realtek because along, with this problem I cant set the mtu to 9000 even though they support jumbo frames.

My 3coms and systems with onboard nics all run great.  Its just the realtek interfaces that act screwy

---

### Post by tictacman on 2007-04-11
I'm having the same problems, I can get files fine but copying across is running at b/s instead of k/s; at this rate it will take me 56 days to copy my directory across:lolflag: 

lspci says my on-board network device is:

ALi Corporation M5263 Ethernet Controller (rev 40)


No luck changing from default line to just:

socket options = TCP_NODELAY

After googling I found a thread suggesting that by adding the following lines they got samba to play fair:

oplocks = no
level2 oplocks = no

didn't work for me. Hope this is not XP messing me around once again :(

---

### Post by tictacman on 2007-04-11
Problem Solved for me. On the host (windows XP) I went into the nik settings and changed the speed/duplex settings from force 100 full duplex to Full auto-negotiation.  Samba has since worked fine with both edgy and feisty and knoppix.

---

### Post by m-y-t-h-o-s on 2007-04-19
i have the sambe problem here with feisty (not with edgy). 

[server] [client] [speed]
feisty winxp ~300kb/s 
feisty win2k3 ~300kb/s
feisty etch ~300kb/s
edgy winxp ~20mb/s (on the same machine with the same config)
edgy win2k3,etch ~20mb/s

i havn't any ideas. this must be a bug.

greez
mythos

---

### Post by fyleow on 2007-04-24
Problem still exists with Feisty.  Anyone have any ideas?

---

### Post by teeks99 on 2007-04-27
I also have this problem...due to the fact that I messed up the search (I had firefox's noscript blocking scripting on ubuntufourms.org) I didn't see this thread....I've started my own, with some relevant details:

[http://ubuntuforums.org/showthread.php?p=2546109](http://ubuntuforums.org/showthread.php?p=2546109)

You will note that I don't experience the same slowdown when transferring the same file with FTP between the same machines.

Also, I'm running the 64bit version, not the i386 version if that matters.  What do other people with problems have?

---

