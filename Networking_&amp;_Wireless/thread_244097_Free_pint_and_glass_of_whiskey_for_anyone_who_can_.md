---
title: "Free pint and glass of whiskey for anyone who can help me network 2 dappers and a xp"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by tmtjjhnsn on 2006-08-25
I am detemined to share files among my 2 Dapper machines and my XP laptop.  I have been reading posts and typing in terminals for three days, with no success.  I have installed Samba on both dapper machines.  I have right clicked my home folders on both dappers and clicked Share.  I have given the home folders names,and clicked on Do Not Use Wins, or something to that effect.  I have opened terminals on both Dapper boxes and typed sudo smbpasswd -a *username[I]*[/I], and entered a new password.  I have enabled file and printer sharing on my Windows XP laptop.  When I first completed these steps, I was able to access my XP files from both Dappers, but I was unable to share files between the two dappers.  Trying to access my Dapper machines from the XP laptop resulted in a message something like "This network resource is inaccessible.  Check with your administator to see if you have permission and bring a note from your mother.  You are a bad person."

Things have gotten worse since then.   I typed the sudo smbpasswd line on both dapper machines.  Was that right?  What user name should I have used in the smbpasswd line?  Should it have been the same username on both machines?  Is there a plain-English guide, somewhere, that can give me step-by-step instructions?  Why can't there be a Samba wizard to guide my sorry a** through this?  Does it matter what name I give the shared folders?  

Now, I can't even access my XP files from either Dapper box.

I need help.  Please direct me to a resource or hold my hand.  A pint and a glass of whiskey are your reward.  Thank you, in advance.

---

### Post by tmtjjhnsn on 2006-08-26
Okay, I was just joking about the beer and whiskey.  You don't have to come to Brighton to redeem your free drinks.  Just please help with the networking question.  Thanks much.

---

### Post by boots17 on 2006-08-27
the woes of samba, right are all the macines in the same workgroup and od they all have individual names etc, i will await your reply and see if i can help ya further

---

### Post by tribaal on 2006-08-27
I think zou should trz to install samba on both dapper machines.
Samba is software that makes the machines you install it on behave like a windows file-sharing server.

You should then be able to create shared folders like in windows, by editing the /etc/smb/smb.conf file.

To install samba:

sudo apt-get install samba 

:)

Hope this helps :)

- trib'

---

### Post by tmtjjhnsn on 2006-08-27
> **boots17 said:**
> the woes of samba, right are all the macines in the same workgroup and od they all have individual names etc, i will await your reply and see if i can help ya further

Thanks boots and tribaal for your replies.  Samba is installed on both machines.  One Dapper machine is named Ricky, and one Bobby, and the XP laptop is Racquel.  The workgroup is Bud on all three machines.  The primary user login name on both Dappers is Ricky, and I used Ricky as the Samba login on both.  I thought that the  two login names being the same might be creating a problem, so I tried creating a new user named Penny on the machine named Ricky, and created a Samba login named Penny, but that didn't change anything.  Wow, that was confusing.  I hope that you are still awake.

---

### Post by funchords on 2006-08-28
> **tmtjjhnsn said:**
> Thanks boots and tribaal for your replies.  Samba is installed on both machines.  One Dapper machine is named Ricky, and one Bobby, and the XP laptop is Racquel.  The workgroup is Bud on all three machines.  The primary user login name on both Dappers is Ricky, and I used Ricky as the Samba login on both.  I thought that the  two login names being the same might be creating a problem, so I tried creating a new user named Penny on the machine named Ricky, and created a Samba login named Penny, but that didn't change anything.  Wow, that was confusing.  I hope that you are still awake.

Having a machine named Ricky and an account named Ricky could cause problems, as SMB queries generally are made for WORKGROUPS, MACHINES, and USERS.  This is so that you can send a WinPopup message to "Ricky" and find the user Ricky somewhere on the network.  

However, try this command (replace password with ricky's password)

sudo smbtree --user ricky%password

and

sudo smbtree --user Guest%

Do either give you a response?

---

### Post by tmtjjhnsn on 2006-08-28
Robb,

Here is what I get when I type sudo smbtree --rickypassword:

BUD
        \\RACQUEL                       laptop
                \\RACQUEL\Printer               Lexmark 510 Series
                \\RACQUEL\print$                Printer Drivers
                \\RACQUEL\SharedDocs
                \\RACQUEL\IPC$                  Remote IPC
                \\RACQUEL\My Documents

Notice that I left out the % after Ricky.  Leaving it in gives no response.
This only works on the machine named Ricky.  The command gives no response on the machine named Bobby.  Neither sudo smbtree --Guest nor sudo smbtree --Guest% give any response on either machine.

---

### Post by tmtjjhnsn on 2006-08-28
Did I mention that I have two users named Ricky, one on the machine named Ricky, and one on the machine named Bobby?  That probably has things all screwed up, doesn't it?

---

### Post by funchords on 2006-08-28
> **tmtjjhnsn said:**
> Robb,

Here is what I get when I type sudo smbtree --rickypassword:

[...]

That should be **sudo smbtree [B]--user** acctname%password[/B] ... the --user should preceed the username.

Let's re-run those commands correctly.  I'm a little surprised that the localhost Samba server didn't respond, but perhaps it was because the command was botched.

> **tmtjjhnsn said:**
> Did I mention that I have two users named Ricky, one on the machine named Ricky, and one on the machine named Bobby? That probably has things all screwed up, doesn't it?

No.  If anything, it will help.

If the username/password matches on a Windows machine, generally you'll get the access privileges of that user.  Otherwise, you'll often get "Guest" privileges, if any.

---

### Post by tmtjjhnsn on 2006-08-28
> **funchords said:**
> That should be **sudo smbtree [B]--user** acctname%password[/B] ... the --user should preceed the username.

Let's re-run those commands correctly.  I'm a little surprised that the localhost Samba server didn't respond, but perhaps it was because the command was botched.



No.  If anything, it will help.

If the username/password matches on a Windows machine, generally you'll get the access privileges of that user.  Otherwise, you'll often get "Guest" privileges, if any.

sudo smbtree --user ricky%password results in no response on either Dapper machine.  It prompts for a password, there is a delay of a few seconds, and then a new command line appears, waiting for another command.  Same result with bobby%password, racquel%password, and guest% on both machines.  Of course, I typed the actual password, not the word "password."

Thanks for your help, so far.  I am determined to make this work.

---

### Post by funchords on 2006-08-28
> **tmtjjhnsn said:**
> sudo smbtree --user ricky%password results in no response on either Dapper machine.  It prompts for a password, there is a delay of a few seconds, and then a new command line appears, waiting for another command.  Same result with bobby%password, racquel%password, and guest% on both machines.  Of course, I typed the actual password, not the word "password."

That's strange.  Raquel responded yesterday.  

Pardon me for asking (and forgive the pun), **but is RACQUEL turned on?** \\:D/ (Maybe if we spoke sweetly to her...)

Let's also run this command on the two Ubuntu machines.  You should not get something substantially different than this:

robb@TOPOL016:~$ **ps ax | grep smb**
 4635 ?        Ss     0:00 /usr/sbin/smbd -D
 4693 ?        S      0:00 /usr/sbin/smbd -D
27403 pts/0    S+     0:00 grep smb

---

### Post by tmtjjhnsn on 2006-08-29
> **funchords said:**
> That's strange.  Raquel responded yesterday.  

Pardon me for asking (and forgive the pun), **but is RACQUEL turned on?** \\:D/ (Maybe if we spoke sweetly to her...)

Let's also run this command on the two Ubuntu machines.  You should not get something substantially different than this:

robb@TOPOL016:~$ **ps ax | grep smb**
 4635 ?        Ss     0:00 /usr/sbin/smbd -D
 4693 ?        S      0:00 /usr/sbin/smbd -D
27403 pts/0    S+     0:00 grep smb

Yes, Racquel was very much so turned on, as usual. :cool:  

Interestingly, I tried typing sudo smbtree, with nothing after it,  and I got the same response from Racquel that I had posted before.    A few minutes later, I typed the exact same thing, and got no response.  Racquel was on my lap the entire time, and, of course, she was turned on.

I am not clear what command you are suggesting that I type on the two Dapper machines, now.

---

### Post by funchords on 2006-08-29
> **tmtjjhnsn said:**
> Interestingly, I tried typing sudo smbtree, with nothing after it, and I got the same response from Racquel that I had posted before. A few minutes later, I typed the exact same thing, and got no response. 

Okay, we'll get to that down the road.  It means that RAQUEL and another machine are arguing over who gets to be the domain Master Browser. 

As a precaution, let's make sure we don't run any tests for about 5 minutes after starting or rebooting any computer on your network.  This will allow time for the network to elect a Master Browser.

Later, we'll give a command to tell the laptop never to become a Master Browser, but until we get your two Linux machines up and running with Samba, it's better to keep things as they are.

> **tmtjjhnsn said:**
> I am not clear what command you are suggesting that I type on the two Dapper machines, now.

**ps ax | grep smb**

---

### Post by tmtjjhnsn on 2006-08-29
> **funchords said:**
> Okay, we'll get to that down the road.  It means that RAQUEL and another machine are arguing over who gets to be the domain Master Browser. 

As a precaution, let's make sure we don't run any tests for about 5 minutes after starting or rebooting any computer on your network.  This will allow time for the network to elect a Master Browser.

Later, we'll give a command to tell the laptop never to become a Master Browser, but until we get your two Linux machines up and running with Samba, it's better to keep things as they are.



**ps ax | grep smb**

Here' the response to that command:

4704 ?        Ss     0:00 /usr/sbin/smbd -D
 4752 ?        S      0:00 /usr/sbin/smbd -D
 8221 pts/0    R+     0:00 grep smb

---

### Post by funchords on 2006-08-29
Hmmm.  Any firewalls running?

Okay, even more commands.  I'll show you my output, you show me yours...

This will tell us if Samba is even listening...

```
robb@TOPOL016:~$ **sudo netstat --listening --tcp --udp --numeric --programs**
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:58626         0.0.0.0:*               LISTEN     3983/python
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     4245/smbd
tcp        0      0 0.0.0.0:5901            0.0.0.0:*               LISTEN     4290/xinetd
tcp        0      0 0.0.0.0:19150           0.0.0.0:*               LISTEN     4188/gkrellmd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     4048/cupsd
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     4245/smbd
tcp        0      0 127.0.0.1:51869         0.0.0.0:*               LISTEN     3980/hpiod
tcp6       0      0 :::19150                :::*                    LISTEN     4188/gkrellmd
udp        0      0 192.168.177.116:137     0.0.0.0:*                          4243/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                          4243/nmbd
udp        0      0 192.168.177.116:138     0.0.0.0:*                          4243/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                          4243/nmbd
udp        0      0 0.0.0.0:68              0.0.0.0:*                          3347/dhclient3

```

This is the Samba configuration file.

```
robb@TOPOL016:~$ **cat /etc/samba/smb.conf**
;following guide at http://www.ubuntuforums.org/showthread.php?t=202605

[global]
    ; General server settings
    netbios name = TOPOL016
    server string =
    workgroup = TOPOLSKINET
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=16384 SO_SNDBUF=16384
    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

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
    force user = robb
    force group = robb
robb@TOPOL016:~$       
```

---

### Post by tmtjjhnsn on 2006-08-30
Yes to firewalls.  Firestarter and Zone Alarm.

Here is the response to the first command.

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State PID/Program name
tcp        0      0 0.0.0.0:768             0.0.0.0:*               LISTEN     7 794/rpc.statd
tcp        0      0 127.0.0.1:4097          0.0.0.0:*               LISTEN     4 064/hpiod
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     4 763/smbd
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     7 742/portmap
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     2 0526/cupsd
tcp        0      0 127.0.0.1:4729          0.0.0.0:*               LISTEN     4 085/python
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     4 763/smbd
udp        0      0 192.***.*.*:**7         0.0.0.0:*                          4 761/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                          4 761/nmbd
udp        0      0 192.***.*.*:**8         0.0.0.0:*                          4 761/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                          4 761/nmbd
udp        0      0 0.0.0.0:68              0.0.0.0:*                          3 294/dhclient3
udp        0      0 0.0.0.0:111             0.0.0.0:*                          7 742/portmap
udp        0      0 0.0.0.0:762             0.0.0.0:*                          7 794/rpc.statd
udp        0      0 0.0.0.0:765             0.0.0.0:*                          7 794/rpc.statd

And the samba configuration file:

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = BUD

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
security = user
username map = /etc/samba/smbusers


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
   printing = cups
   printcap name = cups

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
  writable = yes

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
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom




[bud]
path = /home/ricky
available = yes
browseable = yes
public = yes
writable = yes
ricky@ricky-desktop:~$

---

### Post by funchords on 2006-08-30
That config file is a mess.  It is missing key settings (e.g. netbios name) and some of the service settings are interspersed among other settings.  It appears that you have worked on it quite a lot, but it's pretty broken now.  

Here are my suggestions:

1.  **Start simple,** then add the complexity.  Turn off the firewalls at the beginning, then after Samba is working, we'll put them back up knowing all we have to do is open the correct ports.

2.  **Start over,** go to [http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605) and complete the steps between "2. Getting samba configured" and "2. Changing network settings in Windows" (*yeah, there are two step 2s!*).  When you get to the 2nd "step 2," then stop -- don't complete that section.  The only thing I want you to do different is to set "wins support = yes" to "wins support = no."  

If you do 1 & 2, then I think you'll be a lot closer to working than you are now.

---

### Post by tmtjjhnsn on 2006-08-30
> **funchords said:**
> That config file is a mess.  It is missing key settings (e.g. netbios name) and some of the service settings are interspersed among other settings.  It appears that you have worked on it quite a lot, but it's pretty broken now.  

Here are my suggestions:

1.  **Start simple,** then add the complexity.  Turn off the firewalls at the beginning, then after Samba is working, we'll put them back up knowing all we have to do is open the correct ports.

2.  **Start over,** go to [http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605) and complete the steps between "2. Getting samba configured" and "2. Changing network settings in Windows" (*yeah, there are two step 2s!*).  When you get to the 2nd "step 2," then stop -- don't complete that section.  The only thing I want you to do different is to set "wins support = yes" to "wins support = no."  

If you do 1 & 2, then I think you'll be a lot closer to working than you are now.


Okay, I think we are really getting somewhere, but what do I enter as the netbios name:  the machine name, or user name?  Do I repeat this on each Dapper machine?  Thanks, Funchords.

---

### Post by funchords on 2006-08-30
The machine name.  e.g. ricky

Let's just do one of the Ubuntu's for now, get it working, and that should make getting the other one going really easy.  (Just my opinion -- reduce the number of variables)

---

### Post by tmtjjhnsn on 2006-08-30
> **funchords said:**
> The machine name.  e.g. ricky

Let's just do one of the Ubuntu's for now, get it working, and that should make getting the other one going really easy.  (Just my opinion -- reduce the number of variables)


Okay, I followed the first step two on bobby.  I did not, however, do this step: 

"In case you need other users to be able to access the share you need to add them to your system AND samba as well. Make sure you use the very same Windows usernames and passwords!

NOTE: Windows XP doesn't set passwords for its useraccount per default. If you haven't set a password on your XP box just press enter when prompted to enter a password for the user account you're about to create!

In the following example we will add an user called "mark" ..."

---

### Post by huygens on 2006-08-30
So what is the current status now? Did you manage to have it working between at least your Windows box and one Dapper box? It seems that you are close to it, isn't it?

I wanted to precise that you can have Ricky as a user name on all your computer without any impact for SMB. SMB - it is actually called CIFS nowadays - authentify user by machine name and user name. So if you want to access the share directories which are on Bobby, you then put as login: Bobby\Ricky :-)
And if you want to access the share on Ricky, you put Ricky\Ricky etc.

May I suggest that you have a look here: [http://www.ubuntuforums.org/showthread.php?p=1333185#post1333185](http://www.ubuntuforums.org/showthread.php?p=1333185#post1333185)
It describes how to share file using Samba on a step-by-step basis. If all of your firewall are deactivated, it should work like a charm.

After that, you can try activating your firewall computer by computer. Perhas, one of the firewall is configured not to allow share drive network transmission...

Huygens

---

### Post by tmtjjhnsn on 2006-08-30
> **huygens said:**
> So what is the current status now? Did you manage to have it working between at least your Windows box and one Dapper box? It seems that you are close to it, isn't it?

I wanted to precise that you can have Ricky as a user name on all your computer without any impact for SMB. SMB - it is actually called CIFS nowadays - authentify user by machine name and user name. So if you want to access the share directories which are on Bobby, you then put as login: Bobby\Ricky :-)
And if you want to access the share on Ricky, you put Ricky\Ricky etc.

May I suggest that you have a look here: [http://www.ubuntuforums.org/showthread.php?p=1333185#post1333185](http://www.ubuntuforums.org/showthread.php?p=1333185#post1333185)
It describes how to share file using Samba on a step-by-step basis. If all of your firewall are deactivated, it should work like a charm.

After that, you can try activating your firewall computer by computer. Perhas, one of the firewall is configured not to allow share drive network transmission...

Huygens


Thanks for the clarification on the user names and machine names.  Thanks, also, for suggesting the thread, but that is exactly where I started, and it did not work for me.  I kept getting messages saying that the contents of the folder could not be displayed on the Dapper machines, and that the network resource was inaccessible from the Windows machine.

The current status is that I can access the files on Ricky from Bobby, but not the files on Bobby from Ricky.  Both are Dapper machines.  Both Dappers are still inaccessible from Windows.

---

### Post by tmtjjhnsn on 2006-08-30
Update:  I can now view all three of my machines in My Network Places on my XP laptop.  When I double-click on Bobby (a Dapper machine), XP prompts me for a username and password and then lets me access my share on Bobby!  Progress!  When I click on Ricky, however, it prompts for a username and password, but when I enter ricky as my username and enter my password, Ricky/ricky appears in the username box.  When I hit enter again, the same dialog box  keeps appearing, with Ricky/ricky in the username field, and my password, represented by circles, in the password field.

---

### Post by funchords on 2006-08-30
Wow, you've come a long way!

Even if you did this before, repeat it:  On the Ricky machine...

sudo smbpasswd -L -a ricky
sudo smbpasswd -L -e ricky

After the first command, you will be prompted for a password 2-3 times.  (Depending on whether you've been sudo recently).

---

### Post by tmtjjhnsn on 2006-08-30
I HAVE come a long way, thanks especially to funchords, and the others who have posted on this thread.

I repeated the commands:

sudo smbpasswd -L -a ricky
sudo smbpasswd -L -e ricky

on the ricky machine.  Now, from the bobby machine, when I go to network servers, only the ricky machine appears, for some reason.  When I double-click on ricky, the folder "homefolderonricky" appears.  When I click on it I get a message saying, "Sorry, not all of the contents of the folder could be accessed."  When I click on ricky in XP's Network Places, it keeps replacing the user name ricky, which I type, with Ricky/ricky, and won't let me access it.

I can access Bobby from either ricky or racquel (XP), as long as firestarter is not running.

---

### Post by tmtjjhnsn on 2006-08-30
Oh, and whatever it may mean, I got a long message upon rebooting each dapper machine that began with, "User's $HOME/.dmrc file is being ignored..."

---

### Post by tmtjjhnsn on 2006-08-31
Update:  I can access all machines from every other machine, except that I can not access Ricky from any machine.

---

### Post by funchords on 2006-08-31
But you are getting prompted for passwords from Ricky ... 

Take a look at /var/log/auth.log and see if there's anything that relates to that.  You can also increase the logging level in the smb.conf, restart Samba, and then look in teh /var/log/samba/smbd.log or the /var/log/daemon.log (or both, I can't remember)

---

### Post by tmtjjhnsn on 2006-08-31
> **funchords said:**
> But you are getting prompted for passwords from Ricky ... 

Take a look at /var/log/auth.log and see if there's anything that relates to that.  You can also increase the logging level in the smb.conf, restart Samba, and then look in teh /var/log/samba/smbd.log or the /var/log/daemon.log (or both, I can't remember)

I poked around in my smb.conf file, but I didn't know what to change.  I opened the daemon.log with sudo gedit and had a look.  I don't know what 90% of that stuff means.  I'm so close to being able to access my entire network.  All I need to do is solve this problem with the ricky machine, and to configure firestarter properly, and I will be in business.  I'll keep trying.

---

### Post by funchords on 2006-08-31
In the [global] section of your smb.conf, add these lines, and comment out any existing lines that match the same names:

log file = /var/log/sambadebug.log
log level = 4
syslog only = no

*Don't forget that you did this.*  ;)  These files log a lot of unnecessary data.  Once you've got it working, comment out these new lines and restore your previous lines.

---

### Post by funchords on 2006-08-31
PS:  I had to look these up myself, so don't feel bad.  To see the description of these commands, at a shell command line...

man smb.conf

... to see other commands and files related to samba ...

man -k samba
man -k smb

... and, yes, you can even do ...

man man

---

### Post by tmtjjhnsn on 2006-08-31
Okay, I added:

log file = /var/log/sambadebug.log
log level = 4
syslog only = no

and commented out syslog = yes
I haven't checked out man -k samba, et al, just yet.  Keep me posted on your plan, funchords.

---

### Post by funchords on 2006-09-01
Okay, now reboot that system -- wait about 5-10 minutes after the reboot -- and try to connect to it.  It should fail as it has before. 

Then look at the log using "less" or an editor.  See if you can find the log entries associated with your attempt.  Post that part/those parts here and lets see where they lead.

---

### Post by tmtjjhnsn on 2006-09-01
[2006/09/01 07:57:51, 3] libsmb/ntlmssp.c:ntlmssp_server_auth(662)
  Got user=[Bear] domain=[RACQUEL] workstation=[RACQUEL] len1=24 len2=24
[2006/09/01 07:57:51, 4] lib/username.c:map_username(143)
  Scanning username map /etc/samba/smbusers
[2006/09/01 07:57:51, 3] auth/auth.c:check_ntlm_password(219)
  check_ntlm_password:  Checking password for unmapped user [RACQUEL]\[Bear]@[RACQUEL] with the new password interface
[2006/09/01 07:57:51, 3] auth/auth.c:check_ntlm_password(222)
  check_ntlm_password:  mapped user is: [BERNIE]\[Bear]@[RACQUEL]

[2006/09/01 07:57:51, 3] auth/auth_sam.c:check_sam_security(264)
  check_sam_security: Couldn't find user 'Bear' in passdb.
[2006/09/01 07:57:51, 2] auth/auth.c:check_ntlm_password(317)
  check_ntlm_password:  Authentication for user [Bear] -> [Bear] FAILED with error NT_STATUS_NO_SUCH_USER

   user=[Bear] domain=[RACQUEL] workstation=[RACQUEL] len1=24 len2=24
[2006/09/01 07:57:51, 3] auth/auth.c:check_ntlm_password(219)
  check_ntlm_password:  Checking password for unmapped user [RACQUEL]\[Bear]@[RACQUEL] with the new password interface
[2006/09/01 07:57:51, 3] auth/auth.c:check_ntlm_password(222)
  check_ntlm_password:  mapped user is: [BERNIE]\[Bear]@[RACQUEL]
[2006/09/01 07:57:51, 3] smbd/sec_ctx.c:push_sec_ctx(256)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2006/09/01 07:57:51, 3] smbd/uid.c:push_conn_ctx(393)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2006/09/01 07:57:51, 3] smbd/sec_ctx.c:set_sec_ctx(288)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2006/09/01 07:57:51, 3] smbd/sec_ctx.c:pop_sec_ctx(386)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2006/09/01 07:57:51, 3] auth/auth_sam.c:check_sam_security(264)
  check_sam_security: Couldn't find user 'Bear' in passdb.
[2006/09/01 07:57:51, 2] auth/auth.c:check_ntlm_password(317)
  check_ntlm_password:  Authentication for user [Bear] -> [Bear] FAILED with error NT_STATUS_NO_SUCH_USER
[2006/09/01 07:57:51, 3] smbd/process.c:timeout_processing(1447)
  timeout_processing: End of file from client (client has disconnected).
[2006/09/01 07:57:51, 3] smbd/sec_ctx.c:set_sec_ctx(288)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2006/09/01 07:57:51, 2] smbd/server.c:exit_server(614)
  Closing connections
[2006/09/01 07:57:51, 3] smbd/connection.c:yield_connection(69)
  Yielding connection to 
[2006/09/01 07:57:51, 3] smbd/server.c:exit_server(655)
  Server exit (normal exit)
 
Got secblob of size 40
[2006/09/01 07:57:59, 3] libsmb/ntlmssp.c:debug_ntlmssp_flags(63)
  2006/09/01 07:57:59, 3] libsmb/ntlmssp.c:ntlmssp_server_auth(662)
  Got user=[ricky] domain=[BERNIE] workstation=[RACQUEL] len1=24 len2=24
[2006/09/01 07:57:59, 4] lib/username.c:map_username(143)
  Scanning username map /etc/samba/smbusers
[2006/09/01 07:57:59, 3] lib/username.c:map_username(184)
  Mapped user ricky to system username
[2006/09/01 07:57:59, 3] auth/auth.c:check_ntlm_password(219)
  check_ntlm_password:  Checking password for unmapped user [BERNIE]\[ricky]@[RACQUEL] with the new password interface
[2006/09/01 07:57:59, 3] auth/auth.c:check_ntlm_password(222)
  check_ntlm_password:  mapped user is: [BERNIE]\[system username]@[RACQUEL]
[check_sam_security: Couldn't find user 'system username' in passdb.
[2006/09/01 07:57:59, 2] auth/auth.c:check_ntlm_password(317)
  check_ntlm_password:  Authentication for user [ricky] -> [system username] FAILED with error NT_STATUS_NO_SUCH_USER
 Server exit (normal exit)

---

### Post by tmtjjhnsn on 2006-09-01
Please note, 

I changed the name of the machine that used to be ricky to bernie.  Also, I have no idea how those images got in there.  I had to edit out most of the log due to length.  Hope this helps.

---

### Post by funchords on 2006-09-03
Sorry for the delay.  I lost a hard drive.  My second 250 GB Western Digital drive this week!  

> **tmtjjhnsn said:**
> Please note, 

I changed the name of the machine that used to be ricky to bernie.  Also, I have no idea how those images got in there.  I had to edit out most of the log due to length.  Hope this helps.

Helps?  This tells the story!  

If you couldn't see it, I highlighted the parts. 

You need to, either

1) create a linux account for bear.  Then you need to use smbpasswd to add and enable a user named "bear" on Bernie.  Use 3 three commands:

sudo useradd -s /bin/true bear
sudo smbpasswd -L -a bear
sudo smbpasswd -L -e bear

or 

2) use the "username map" parameter in smb.conf to point to a file that maps a windows account to a differently named linux account.

Do this:

a. First, the command: 

**sudo useradd -s /bin/true guest**

b. Then edit smb.conf and add this line in the [global] section:

        **username map = /etc/samba/smbusers**

c. Then create or edit that file, and add this line:

**guest = ***

This way, any remote user that doesn't have an account, will be given user privileges under the name of Guest.  

> **tmtjjhnsn said:**
> [2006/09/01 07:57:51, 3] libsmb/ntlmssp.c:ntlmssp_server_auth(662)
  Got user=[Bear] domain=[RACQUEL] workstation=[RACQUEL] len1=24 len2=24
[2006/09/01 07:57:51, 4] lib/username.c:map_username(143)
  Scanning username map /etc/samba/smbusers
[2006/09/01 07:57:51, 3] auth/auth.c:check_ntlm_password(219)
  check_ntlm_password:  Checking password for unmapped user [RACQUEL]\[Bear]@[RACQUEL] with the new password interface
[2006/09/01 07:57:51, 3] auth/auth.c:check_ntlm_password(222)
  check_ntlm_password:  mapped user is: [BERNIE]\[Bear]@[RACQUEL]

[B][2006/09/01 07:57:51, 3] auth/auth_sam.c:check_sam_security(264)
  check_sam_security: Couldn't find user [COLOR="Red"]'Bear'[/COLOR] in passdb.[/B]
[2006/09/01 07:57:51, 2] auth/auth.c:check_ntlm_password(317)
  check_ntlm_password:  Authentication for user [Bear] -> [Bear] FAILED with error NT_STATUS_NO_SUCH_USER

   user=[Bear] domain=[RACQUEL] workstation=[RACQUEL] len1=24 len2=24
[2006/09/01 07:57:51, 3] auth/auth.c:check_ntlm_password(219)
  check_ntlm_password:  Checking password for unmapped user [RACQUEL]\[Bear]@[RACQUEL] with the new password interface
[2006/09/01 07:57:51, 3] auth/auth.c:check_ntlm_password(222)
  check_ntlm_password:  mapped user is: [BERNIE]\[Bear]@[RACQUEL]
[2006/09/01 07:57:51, 3] smbd/sec_ctx.c:push_sec_ctx(256)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2006/09/01 07:57:51, 3] smbd/uid.c:push_conn_ctx(393)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2006/09/01 07:57:51, 3] smbd/sec_ctx.c:set_sec_ctx(288)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2006/09/01 07:57:51, 3] smbd/sec_ctx.c:pop_sec_ctx(386)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2006/09/01 07:57:51, 3] auth/auth_sam.c:check_sam_security(264)
  check_sam_security: Couldn't find user 'Bear' in passdb.
[2006/09/01 07:57:51, 2] auth/auth.c:check_ntlm_password(317)
  check_ntlm_password:  Authentication for user [Bear] -> [Bear] FAILED with error NT_STATUS_NO_SUCH_USER
[2006/09/01 07:57:51, 3] smbd/process.c:timeout_processing(1447)
  timeout_processing: End of file from client (client has disconnected).
[2006/09/01 07:57:51, 3] smbd/sec_ctx.c:set_sec_ctx(288)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2006/09/01 07:57:51, 2] smbd/server.c:exit_server(614)
  Closing connections
[2006/09/01 07:57:51, 3] smbd/connection.c:yield_connection(69)
  Yielding connection to 
[2006/09/01 07:57:51, 3] smbd/server.c:exit_server(655)
  Server exit (normal exit)
 
Got secblob of size 40
[2006/09/01 07:57:59, 3] libsmb/ntlmssp.c:debug_ntlmssp_flags(63)
  2006/09/01 07:57:59, 3] libsmb/ntlmssp.c:ntlmssp_server_auth(662)
  Got user=[ricky] domain=[BERNIE] workstation=[RACQUEL] len1=24 len2=24
[2006/09/01 07:57:59, 4] lib/username.c:map_username(143)
  Scanning username map /etc/samba/smbusers
[2006/09/01 07:57:59, 3] lib/username.c:map_username(184)
  **[COLOR="Red"]Mapped user ricky to system username[/COLOR]**
[2006/09/01 07:57:59, 3] auth/auth.c:check_ntlm_password(219)
  check_ntlm_password:  Checking password for unmapped user [BERNIE]\[ricky]@[RACQUEL] with the new password interface
[B][2006/09/01 07:57:59, 3] auth/auth.c:check_ntlm_password(222)
  check_ntlm_password:  mapped user is: [BERNIE]\[system username]@[RACQUEL]
[check_sam_security: Couldn't find user '[COLOR="Red"]system username[/COLOR]' in passdb.
[2006/09/01 07:57:59, 2] auth/auth.c:check_ntlm_password(317)[/B]
  check_ntlm_password:  Authentication for user [ricky] -> [system username] FAILED with error NT_STATUS_NO_SUCH_USER
 Server exit (normal exit)


I don't know what that last error is all about (the system username one).   It may mean that you have unwanted data in your smbpasswd file.  Possibly, you can ignore it. 

Let's see how you come out so far and see if that error causes any problems.

---

### Post by tmtjjhnsn on 2006-09-03
Sorry to hear about your hard drives.  I hope that everything was backed up and that you were able to restore your data without a hitch.

Now, finally, success!  My three machines can share files freely among them, including Bernie (nee Ricky)!  I never thought about creating a user and password for Bear, I guess because I never did that on Bobby, and yet Bobby and Racquel have been able to share freely.  That's my excuse, anyway, although maybe the real reasons  are that I am not that smart and I drink all day.

As for you, Funchords, you have been a tremendous help.  What took me a week and a half would have taken a year and a half without your help.  Thank you, very much.  You are a credit to our Ubuntu community.

Here is a synopsis of what I have learned about using Samba to network Ubuntu linux with Windows XP:

First, install Samba on each Ubuntu machine.  Then, jettison the Samba config file that comes with Samba, and replace it with the one in this thread:  [http://www.ubuntuforums.org/showthread.php?t=202605://]("http://www.ubuntuforums.org/showthread.php?t=202605://")  
Using sudo gedit /etc/samba/smb.conf, modify the new Samba config file on each Ubuntu machine by replacing YOUR_HOSTNAME in the netbios name field with the name of the machine, and replacing YOUR_WORKGROUP, with the name of your XP workgroup.  Change Wins support = yes to Wins support = no.  At least, that is what I was instructed to do, and it worked for me.  I don't even know what Wins support is. Down in the [MyFiles] section,  force user and force group should both equal the log-in user name for that machine.

Next, follow the instructions in this post to establish what folders you would like to share on each Ubuntu machine:  [http://www.ubuntuforums.org/showthread.php?p=1333185#post1333185]("http://www.ubuntuforums.org/showthread.php?p=1333185#post1333185") 

Add a Samba password for the user log-in name on each Ubuntu machine using the commands smbpasswd -L -a username, and smbpassed -L -e username, as explained previously in this thread.  Also, add the user log-in name of each XP machine to each Ubuntu machine by using the commands:  
sudo useradd -s /bin/true username
sudo smbpasswd -L -a username
sudo smbpsswd -L -e username

On each XP machine, run the "Setup a Home or Small Office Network" utility in My Network Places to allow file and printer sharing.  Be sure to use the same workgroup name on all machines.
Right-click any XP folders you want to share and choose Sharing and Security...  Click the box to share the folder on the network.  

On the Ubuntu machines, click Places, then Network Servers to see if all of the networked machines appear.  If not, disable all firewalls.  If the networked machines become available after disabling the firewalls, enable the firewalls one-by-one to determine which ones are responsible for blocking the network.  Reconfigure any offending firewalls.  On each XP machine, click on My Network Places, and then View Workgroup computers to see all networked macines.

Here are some helpful links:  

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

[http://www.ubuntuforums.org/showthread.php?p=1333185#post1333185](http://www.ubuntuforums.org/showthread.php?p=1333185#post1333185)
  
[http://www.samba.org/samba/docs/using_samba/toc.html](http://www.samba.org/samba/docs/using_samba/toc.html)

---

### Post by tmtjjhnsn on 2006-12-06
I recently tried to access one of my Dapper machines from my XP box, and recieved a message that ****p**ath ://ernie is unavailable.  Check with the Network administrator to see if you have permission to access this device** (or something very similar to this.)  Trying to access the XP machine from Ernie produced a message saying **Could not access Rachael.  Sorry, not all the contents of this folder could be displayed** (or something similar.) ](*,)  After pulling out my hair, I checked my samba config file on Ernie by typing *sudo gedit /etc/samba/smb.conf*.  The file was identical to my backup copy of smb.conf.  Nothing had changed there.  I tried the Network troubleshooter on the XP machine, but that was useless.  I disabled Zone Alarm on the XP machine, and, boom, I could access Ernie from Rachael and Rachael from Ernie!  Further investigation revealed that machine Ernie, IP address 192.168.1.4 had mysteriously disappeared from the list of trusted IP addresses in Zone Alarm.  Adding Ernie and its IP address to the Trusted Zone in Zone Alarm solved the problem.

---

