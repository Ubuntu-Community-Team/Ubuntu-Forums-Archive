---
title: "Unable to get Samba to work"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by GumbyX on 2008-02-24
: sighs: I am having a problem with Samba and have spent the last 4 hours trying to figure this out on my own. I have found several solution in the forums, but none seem to work.

When I was running Edgy I had a samba network setup to share some videos with my Xbox (which is running XBMC). After a bit of tweaking, it work perfectly. Later on in the year, I upgraded ot 7.10. Recently I have dug my xbox out of the closet and decided to set it up again. The share folders were still configured, so I thought all I would have to do is start it up and I could start streaming. Sadly, it did not work out this way. For some reason, I am unable to see the SMB share on my linux box on ANY of the computers on my network (the Xbox and my laptop). Its as if the daemon isn't even running. I have check this a bunch of times, used new sbm.conf files, and even prayed a bit and nothing seems to work. If someone can help me out, I would greatly appreciate it.

I am currently running 7.10 64-bit. Below is my old smb.conf file:

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
   workgroup = WORKGROUP
   netbios name = ubuntu_share

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
[homes]
 comment = Home Directories
 browseable = yes

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


[Anime Download]
path = /media/Data/Anime Download
available = yes
browsable = yes
public = yes
writable = no

comment = Anime, Hentai, and Eechi
[Freddy Vs Ghostbusters]
path = /media/Data/Freddy Vs Ghostbusters
available = yes
browsable = yes
public = yes
writable = no

comment = Fanmade Ghostbusters Movie
[Return of the Ghostbusters]
path = /media/Data/Return of the Ghostbusters
available = yes
browsable = yes
public = yes
writable = no
comment = Fanmade Ghostbusters Movie

[Vids]
path = /home/gumby/Desktop/Vids
comment = Extra Videos
available = yes
browsable = yes
public = yes
writable = no
```

If you can help me out, I would greatly appreciate it. I just want to be able to stream some vids to my Xbox once in a while. Nothing serious.:(

PS Can anyone post the default smb.conf with no edits? I want to try and see if I can start from scratch and see if that helps any.

---

### Post by CRCarl on 2008-02-24
First of all - did you install Samba? (the smb.conf file is there before samba is installed, don't know why)

```
sudo aptitude install samba
```

After you install samba and share some folders you have to restart samba to pick up the changes - 
```

sudo /etc/init.d/samba restart
```

Let us know.

---

### Post by GumbyX on 2008-02-24
> **CRCarl said:**
> First of all - did you install Samba? (the smb.conf file is there before samba is installed, don't know why)

```
sudo aptitude install samba
```

After you install samba and share some folders you have to restart samba to pick up the changes - 
```

sudo /etc/init.d/samba restart
```

Let us know.

Yes Samba is installed. I had it inistalled before I started and reinstalled it a number of times to see if there was something wrong with the install. Nothing worked. :(

---

### Post by Iowan on 2008-02-24
**smbpasswd** file is current?  You might try changing to **security=share** to see if it helps.  Also, check [here]("http://ubuntuforums.org/showthread.php?t=190542") to see if it's related.  In the meantime, I'll try to get the original **smb.conf** file from my server.

---

### Post by lnx4me on 2008-02-24
This appears to be a permissions problem. what are the permissions on the files and subfolders of the directories you wish to share? Also is there a firewall on the linux box and is it allowing traffic to the samba server?

---

### Post by GumbyX on 2008-02-24
> **lnx4me said:**
> This appears to be a permissions problem. what are the permissions on the files and subfolders of the directories you wish to share? Also is there a firewall on the linux box and is it allowing traffic to the samba server?

I am running a firewall, but I have opened ports for Samba. As for file permissions, they are set to access for other users and read only. I just want to stream the files to XBMC, so there is no need to allow them to be edited.

---

### Post by Eiríkr on 2008-02-24
This is something I've run into myself, and from what I've read it seems to be related to how Microsoft changed their SMB implementation with WinXP (which I gather is common to the XBox).  I think it might also happen when you've got sharing turned on for the XP side, but I'm not sure (can't test it right now).  It seems that both the XP machine and the SMB server both claim to be master browsers, and since they can't agree, share browsing just plain doesn't work.  You should still be able to *access* your shares just fine -- I certainly can -- but opening Windows -> My Networks Places -> Entire Network -> Microsoft Windows Network -> Your_Workgroup_Name (sheesh, how far do we need to drill down...), you won't see *anything*.  Now open a Windows terminal and check your [font=courier]nbtstat -a[/font] results -- they should look something like the following:
```

C:\>nbtstat -a SMB_Server

Local Area Connection:
Node IpAddress: [192.168.10.12] Scope Id: []

           NetBIOS Remote Machine Name Table

       Name               Type         Status
    ---------------------------------------------
    SMB_SERVER       <00>  UNIQUE      Registered
    SMB_SERVER       <03>  UNIQUE      Registered
    SMB_SERVER       <20>  UNIQUE      Registered
    ..__MSBROWSE__.<01>  GROUP       Registered
    WORKGROUP    <1D>  UNIQUE      Registered
    WORKGROUP    <1B>  UNIQUE      Registered
    WORKGROUP    <1E>  GROUP       Registered
    WORKGROUP    <00>  GROUP       Registered

    MAC Address = 00-00-00-00-00-00


C:\>nbtstat -a SMB_Client

Local Area Connection:
Node IpAddress: [192.168.10.12] Scope Id: []

           NetBIOS Remote Machine Name Table

       Name               Type         Status
    ---------------------------------------------
    SMB_CLIENT       <00>  UNIQUE      Registered
    SMB_CLIENT       <20>  UNIQUE      Registered
    ..__MSBROWSE__.<01>  GROUP       Registered
    WORKGROUP    <1D>  UNIQUE      Registered
    WORKGROUP    <1E>  GROUP       Registered
    WORKGROUP    <00>  GROUP       Registered

    MAC Address = 00-00-00-00-00-00


C:\>

```

I'm still trying to figure out a solution.  It's only a minor annoyance for me, as again I can still access my shares just fine -- I just open an Explorer window and type [font=courier]\\SMB_Server\[/font], and bam, I can see all the shares.  I just can't get there via My Network Places.  

'Tain't much, but I hope it helps nonetheless.  I'm also vastly relieved to hear about someone else running into this problem recently -- though it's mentioned online in various places (found via Google), most of the posts are older, and there are no indications for how to fix the issue.  I had it with Samba v3.024 on Xubuntu 7.04, and again with Samba v3.026 on Xubuntu 7.10.  I hope the next Samba version includes a fix.  

Good luck and keep us posted if you find any solutions,

Eiríkr

---

### Post by GumbyX on 2008-02-24
Not sure if we are having the same problem. I'm not able to find the server at all, no matter where I look.I can't even access it on the box the server is supposed to be on. That is why I am getting so fustrated about it.

---

### Post by Eiríkr on 2008-02-24
Okaaay...  Open a terminal on the SMB server, and type in [font=courier]nmblookup -S SMB_Server[/font] -- what do you get?  It should look similar to [font=courier]nbtstat -a SMB_Server[/font] from the Windows box:
```
username@SMB_Server:~$ nmblookup -S SMB_Server
querying SMB_Server on 127.255.255.255
192.168.10.10 SMB_Server<00>
Looking up status of 192.168.10.10
        SMB_SERVER        <00> -         B <ACTIVE>
        SMB_SERVER        <03> -         B <ACTIVE>
        SMB_SERVER        <20> -         B <ACTIVE>
        ..__MSBROWSE__. <01> - <GROUP> B <ACTIVE>
        WOLKENHAFEN     <1d> -         B <ACTIVE>
        WOLKENHAFEN     <1b> -         B <ACTIVE>
        WOLKENHAFEN     <1e> - <GROUP> B <ACTIVE>
        WOLKENHAFEN     <00> - <GROUP> B <ACTIVE>

        MAC Address = 00-00-00-00-00-00

username@SMB_Server:~$
```
If nothing, check that *both* smbd and nmbd are running:
```
username@SMB_Server:~$ ps aux | grep mbd
root     15493  0.0  0.1   6428  1336 ?        Ss   14:21   0:00 /usr/sbin/nmbd -D
root     15495  0.0  0.2   9900  2256 ?        Ss   14:21   0:00 /usr/sbin/smbd -D
root     15496  0.0  0.0   9900   920 ?        S    14:21   0:00 /usr/sbin/smbd -D
username   15503  0.0  0.3  10272  3192 ?        S    14:21   0:00 /usr/sbin/smbd -D
username   15513  0.0  0.0   2972   748 pts/5    R+   14:23   0:00 grep mbd
username@SMB_Server:~$
```

What luck with these?

Cheers,

Eiríkr

---

### Post by GumbyX on 2008-02-24
> **Eiríkr said:**
> Okaaay...  Open a terminal on the SMB server, and type in [font=courier]nmblookup -S SMB_Server[/font] -- what do you get?  It should look similar to [font=courier]nbtstat -a SMB_Server[/font] from the Windows box:
```
username@SMB_Server:~$ nmblookup -S SMB_Server
querying SMB_Server on 127.255.255.255
192.168.10.10 SMB_Server<00>
Looking up status of 192.168.10.10
        SMB_SERVER        <00> -         B <ACTIVE>
        SMB_SERVER        <03> -         B <ACTIVE>
        SMB_SERVER        <20> -         B <ACTIVE>
        ..__MSBROWSE__. <01> - <GROUP> B <ACTIVE>
        WOLKENHAFEN     <1d> -         B <ACTIVE>
        WOLKENHAFEN     <1b> -         B <ACTIVE>
        WOLKENHAFEN     <1e> - <GROUP> B <ACTIVE>
        WOLKENHAFEN     <00> - <GROUP> B <ACTIVE>

        MAC Address = 00-00-00-00-00-00

username@SMB_Server:~$
```
If nothing, check that *both* smbd and nmbd are running:
```
username@SMB_Server:~$ ps aux | grep mbd
root     15493  0.0  0.1   6428  1336 ?        Ss   14:21   0:00 /usr/sbin/nmbd -D
root     15495  0.0  0.2   9900  2256 ?        Ss   14:21   0:00 /usr/sbin/smbd -D
root     15496  0.0  0.0   9900   920 ?        S    14:21   0:00 /usr/sbin/smbd -D
username   15503  0.0  0.3  10272  3192 ?        S    14:21   0:00 /usr/sbin/smbd -D
username   15513  0.0  0.0   2972   748 pts/5    R+   14:23   0:00 grep mbd
username@SMB_Server:~$
```

What luck with these?

Cheers,

Eiríkr

Here are the results I got, substituting my hostname for SMB_Server

**nm-lookup**
```
gumby@gumby-linux-desktop:~$  nmblookup -S gumby-linux-desktop
querying gumby-linux-desktop on 192.168.1.255
name_query failed to find name gumby-linux-desktop

```
A note, I get the same results when I use SMB_Server.

**ps aux | grep mbd**
```
gumby@gumby-linux-desktop:~$ ps aux | grep mbd
root     25947  0.0  0.1  54848  1288 ?        Ss   18:42   0:00 /usr/sbin/nmbd -D
root     25949  0.0  0.2  75160  2316 ?        Ss   18:42   0:00 /usr/sbin/smbd -D
root     25953  0.0  0.0  75160  1020 ?        S    18:42   0:00 /usr/sbin/smbd -D
gumby    26007  0.0  0.0   5120   832 pts/0    S+   18:43   0:00 grep mbd

```

: sighs:  not really understand the results of the second command, but I am surprised about something about the first. I do not know why it is querying the IP 192.168.1.225. None of my machines on the network have that IP. I have IPs set by the DHCP n my router by MAC Adress, so I know nothing on the network has that IP right now. Anyone think they can shed some light on this? Is that my entire problem right there?

---

### Post by Eiríkr on 2008-02-24
> **GumbyX said:**
> Here are the results I got, substituting my hostname for SMB_Server

**nm-lookup**
```
gumby@gumby-linux-desktop:~$  nmblookup -S gumby-linux-desktop
querying gumby-linux-desktop on 192.168.1.255
name_query failed to find name gumby-linux-desktop

```
A note, I get the same results when I use SMB_Server.

Ah, my bad, I should have been explicit that "SMB_Server" was only meant as a placeholder.  Doh!  So good that you tried running the command with your actual hostname.  :)  But not so good that nmblookup isn't finding it.  

> **GumbyX said:**
> **ps aux | grep mbd**
```
gumby@gumby-linux-desktop:~$ ps aux | grep mbd
root     25947  0.0  0.1  54848  1288 ?        Ss   18:42   0:00 /usr/sbin/nmbd -D
root     25949  0.0  0.2  75160  2316 ?        Ss   18:42   0:00 /usr/sbin/smbd -D
root     25953  0.0  0.0  75160  1020 ?        S    18:42   0:00 /usr/sbin/smbd -D
gumby    26007  0.0  0.0   5120   832 pts/0    S+   18:43   0:00 grep mbd

```

: sighs:  not really understand the results of the second command, but I am surprised about something about the first. I do not know why it is querying the IP 192.168.1.225. None of my machines on the network have that IP. I have IPs set by the DHCP n my router by MAC Adress, so I know nothing on the network has that IP right now. Anyone think they can shed some light on this? Is that my entire problem right there?

One thing about the IP nmblookup is using is that it's a broadcast address -- any IPv4 address quad with the last one as 255 is a broadcast address -- so naturally none of your hosts would have that particular address.  What's worth asking here though is if the 192.168.1 part is correct?  If so, then the problem is with nmblookup and possibly your smb.conf file somewhere; if your network is *not* on that subnet, then something else is going on.  

A breakdown of the second command, the compound [font=courier]ps aux | grep mbd[/font]:
[list][*][font=courier]ps[/font] = "**p**rocess li**s**t" -- like [font=courier]ls[/font], only it shows running processes instead of files in the current directory.  The [font=courier]aux[/font] switch tells the command to show **a**ll processes, even those without a terminal (the **x**), and to display which **u**ser the process is running as.  
[*][font=courier]|[/font] (the pipe) = pass the output of the command on the left to the command on the right -- a great way to string commands together, and one of the wonders and joys of the Unixy CLI.
[*][font=courier]grep[/font] = search through whatever input we're using for the specified string, in this case "mbd".[/list]
So all together, [font=courier]ps aux | grep mbd[/font] looks through all running processes, and only displays those that have "mbd" in them -- in this case, neatly picking out the [font=courier]nmbd[/font] and [font=courier]smbd[/font] listings.  

If you'd like to learn a heck of a lot more about either [font=courier]ps[/font] or [font=courier]grep[/font], have a look at their respective man pages.  

Anyway, back to the problem at hand, let us know if 192.168.1 is the proper subnet, and we'll go from there.  

Incidentally, was this Ubuntu Server 6.06 install a fresh one, or an update over an existing install?  I've had my network functionality go all funny on me in the past with an update, and it took a fresh install to fix things.  

Cheers,

Eiríkr

---

### Post by Eiríkr on 2008-02-24
*Boy* I can be a nimrod -- it's right there in your smb.conf:
```
netbios name = ubuntu_share
```
This tells the Windows naming daemon (the nmbd thingy) to use "ubuntu_share" instead of your hostname.  Try running [font=courier]nmblookup -S ubuntu_share[/font] instead and post the output.  

Cheers,

Eiríkr

---

### Post by GumbyX on 2008-02-24
> **Eiríkr said:**
> *Boy* I can be a nimrod -- it's right there in your smb.conf:
```
netbios name = ubuntu_share
```
This tells the Windows naming daemon (the nmbd thingy) to use "ubuntu_share" instead of your hostname.  Try running [font=courier]nmblookup -S ubuntu_share[/font] instead and post the output.  

Cheers,

Eiríkr

When I nmblookup with it, I get the following:
```
querying ubuntu_share on 192.168.1.255
name_query failed to find name ubuntu_share
```

PS I am not running Ubuntu server 6.06 or ever did. Just Ubuntu desktop 6.06 and 7.10 (which i am runnign now)

PSS the Subnet should be right. All IPs are given on that subset on this network.

---

### Post by Iowan on 2008-02-24
May need to have **winbind** running...

---

### Post by Eiríkr on 2008-02-25
@Iowan: I dunno, nmblookup runs just fine on my SMB server and I don't have winbind running...  

@GumbyX: I just went back through your [Global] smb.conf section to see if I found anything else.  What happens if you remove the [font=courier]netbios name = ubuntu_share[/font] line and restart Samba?  Does [font=courier]nmblookup -S gumby_linux_desktop[/font] work then?  Also, what does [font=courier]nmblookup -M -- -[/font] return?  This looks for the IP of the master browser on your Samba workgroup.  It should look something like this:
```
admin@SMB_Server:~$ nmblookup -M -- -
querying __MSBROWSE__ on 127.255.255.255
192.168.10.10 __MSBROWSE__<01>
admin@SMB_Server:~$
```
What IP do you get?  Is it actually the IP of your SMB server, or something else?

Cheers,

Eiríkr

PS -- Also try [font=courier]nmblookup -A [IP of your SMB server][/font].  The "-A" switch tells nmblookup to search for the IP instead of the netbios name.  If all of these come up blank, we'll have to figure out something else to try.

---

### Post by jhetrick62 on 2008-02-25
First, does this share work properly when accessed by IP number rather than netbios name?

Map it to //192.168.2.255/Vids and see if this works.

I see my Samba server with my winXP laptop by it's netbios name, no issues.  But I also keep my samba server set to be a WINS server and the Master Browser on the network.  I don't want Winblows attempting to be the dominant force on the network.

My rule of thumb for Samba is to always start VERY SIMPLE, then add complexity after you establish that it is working, one piece at a time.

Jeff

---

### Post by GumbyX on 2008-02-25
> **jhetrick62 said:**
> First, does this share work properly when accessed by IP number rather than netbios name?

Map it to //192.168.2.255/Vids and see if this works.

I see my Samba server with my winXP laptop by it's netbios name, no issues.  But I also keep my samba server set to be a WINS server and the Master Browser on the network.  I don't want Winblows attempting to be the dominant force on the network.

My rule of thumb for Samba is to always start VERY SIMPLE, then add complexity after you establish that it is working, one piece at a time.

Jeff

Thats the idea I try and stick with myself. It was working at one time (I think even under 7.10) and then it just ... broke. I want to start from scratch, hence the request for a default, un-edited smb.conf, which I just realized I have on my laptop. I will try all the stuff you guys posted before I swap in the original smb.conf file. That will have to wait till tonight. I will post an update at that time. Wish me luck.

---

### Post by GumbyX on 2008-02-25
> **Eiríkr said:**
> @Iowan: I dunno, nmblookup runs just fine on my SMB server and I don't have winbind running...  

@GumbyX: I just went back through your [Global] smb.conf section to see if I found anything else.  What happens if you remove the [font=courier]netbios name = ubuntu_share[/font] line and restart Samba?  Does [font=courier]nmblookup -S gumby_linux_desktop[/font] work then?  Also, what does [font=courier]nmblookup -M -- -[/font] return?  This looks for the IP of the master browser on your Samba workgroup.  It should look something like this:
```
admin@SMB_Server:~$ nmblookup -M -- -
querying __MSBROWSE__ on 127.255.255.255
192.168.10.10 __MSBROWSE__<01>
admin@SMB_Server:~$
```
What IP do you get?  Is it actually the IP of your SMB server, or something else?

Cheers,

Eiríkr

PS -- Also try [font=courier]nmblookup -A [IP of your SMB server][/font].  The "-A" switch tells nmblookup to search for the IP instead of the netbios name.  If all of these come up blank, we'll have to figure out something else to try.

Here are the results of the suggested commands:

**nmblookup -M -- -**
```
gumby@gumby-linux-desktop:~$ nmblookup -M -- -
querying __MSBROWSE__ on 192.168.1.255
name_query failed to find name __MSBROWSE__#01

```

**nmblookup -A [IP of your SMB server]**
```
gumby@gumby-linux-desktop:~$ nmblookup -A 192.168.1.126
Looking up status of 192.168.1.126
        GUMBY-LINUX-DES <00> -         H <ACTIVE> 
        GUMBY-LINUX-DES <03> -         H <ACTIVE> 
        GUMBY-LINUX-DES <20> -         H <ACTIVE> 
        WORKGROUP       <1e> - <GROUP> H <ACTIVE> 
        WORKGROUP       <00> - <GROUP> H <ACTIVE> 

        MAC Address = 00-00-00-00-00-00


```

As you can see, the second had some better results. It looks like it actually sees the samba workgroup *Workgroup*. Or am I just reading this wrong?

---

### Post by Eiríkr on 2008-02-25
> As you can see, the second had some better results. It looks like it actually sees the samba workgroup Workgroup. Or am I just reading this wrong?
No, you're reading that right -- when a computer designates itself as the master browser, it adds a line like this to its nmblookup / nbtstat -a results:
```
Local Area Connection:
Node IpAddress: [192.168.10.12] Scope Id: []

           NetBIOS Remote Machine Name Table

       Name               Type         Status
    ---------------------------------------------
    SMB_SERVER       <00>  UNIQUE      Registered
    SMB_SERVER       <03>  UNIQUE      Registered
    SMB_SERVER       <20>  UNIQUE      Registered
**    ..__MSBROWSE__.<01>  GROUP       Registered**
    WORKGROUP    <1D>  UNIQUE      Registered
    WORKGROUP    <1B>  UNIQUE      Registered
    WORKGROUP    <1E>  GROUP       Registered
    WORKGROUP    <00>  GROUP       Registered

    MAC Address = 00-00-00-00-00-00
```
Since that line is missing, it's clear that your SMB server is currently *not* the master browser for your workgroup.  I also wonder if the truncation of your hostname (shows up as [font=courier]GUMBY-LINUX-DES[/font]) might have been part of why running lookups based on that hostname was failing?

Anyway, it looks like you might want to play around with some of the global options in your smb.conf file, specifically the options related to becoming a master browser.  Have a look at [this online page describing the smb.conf file options]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html"), and search through for "master browser" to find the relevant sections.  Of particular note:
> Note that Windows NT Primary Domain Controllers expect to be able to claim this workgroup specific special NetBIOS name that identifies them as domain master browsers for that workgroup by default (i.e. there is no way to prevent a Windows NT PDC from attempting to do this). This means that if this parameter is set and nmbd claims the special name for a workgroup before a Windows NT PDC is able to do so then cross subnet browsing will behave strangely and may fail.
I don't know if you have any WinNT machines on your network, but if you do they might be part of this trouble you're having.  

Also, could you post the results of this command:
[font=courier]grep "master browser" /var/log/samba/log.nmbd[/font]

Feels like we're getting warmer...  

Cheers,

Eiríkr

---

### Post by GumbyX on 2008-02-25
> **Eiríkr said:**
> No, you're reading that right -- when a computer designates itself as the master browser, it adds a line like this to its nmblookup / nbtstat -a results:
```
Local Area Connection:
Node IpAddress: [192.168.10.12] Scope Id: []

           NetBIOS Remote Machine Name Table

       Name               Type         Status
    ---------------------------------------------
    SMB_SERVER       <00>  UNIQUE      Registered
    SMB_SERVER       <03>  UNIQUE      Registered
    SMB_SERVER       <20>  UNIQUE      Registered
**    ..__MSBROWSE__.<01>  GROUP       Registered**
    WORKGROUP    <1D>  UNIQUE      Registered
    WORKGROUP    <1B>  UNIQUE      Registered
    WORKGROUP    <1E>  GROUP       Registered
    WORKGROUP    <00>  GROUP       Registered

    MAC Address = 00-00-00-00-00-00
```
Since that line is missing, it's clear that your SMB server is currently *not* the master browser for your workgroup.  I also wonder if the truncation of your hostname (shows up as [font=courier]GUMBY-LINUX-DES[/font]) might have been part of why running lookups based on that hostname was failing?

Anyway, it looks like you might want to play around with some of the global options in your smb.conf file, specifically the options related to becoming a master browser.  Have a look at [this online page describing the smb.conf file options]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html"), and search through for "master browser" to find the relevant sections.  Of particular note:

I don't know if you have any WinNT machines on your network, but if you do they might be part of this trouble you're having.  

Also, could you post the results of this command:
[font=courier]grep "master browser" /var/log/samba/log.nmbd[/font]

Feels like we're getting warmer...  

Cheers,

Eiríkr

I have no windows boxes on the network at all.

But here is the output from [font=courier]grep "master browser" /var/log/samba/log.nmbd[/font]:

```
gumby@gumby-linux-desktop:~$ grep "master browser" /var/log/samba/log.nmbd
  Samba name server UBUNTU_SHARE is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.126
  Samba name server UBUNTU_SHARE is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.126
  Samba name server UBUNTU_SHARE is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.126
  Samba name server GUMBY-LINUX-DESKTOP is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.126

```

So now I am totally confused..... the server is the local master browser, but doesn't show up when I look for a samba network on ANY computer on the network (even the server itself)?

---

### Post by Eiríkr on 2008-02-25
Definitely strange...

Three options I can think of off the top of my head that you might want to set in the Global section of your smb.conf:

[font=courier]preferred master = yes
domain master = yes
local master = yes[/font]

Try them all, try them one at a time, restarting Samba ([FONT="Courier New"]sudo /etc/init.d/samba restart[/FONT]) or at least reloading the conf file ([FONT="Courier New"]sudo /etc/init.d/samba reload[/FONT]) each time you change the options.  Give the server processes a moment's time to establish themselves before trying the nmblookup again.  

:confused:

Cheers,

Eiríkr

---

### Post by GumbyX on 2008-02-25
> **Eiríkr said:**
> Definitely strange...

Three options I can think of off the top of my head that you might want to set in the Global section of your smb.conf:

[font=courier]preferred master = yes
domain master = yes
local master = yes[/font]

Try them all, try them one at a time, restarting Samba ([FONT="Courier New"]sudo /etc/init.d/samba restart[/FONT]) or at least reloading the conf file ([FONT="Courier New"]sudo /etc/init.d/samba reload[/FONT]) each time you change the options.  Give the server processes a moment's time to establish themselves before trying the nmblookup again.  

:confused:

Cheers,

Eiríkr

We have some success! Here is the output from nmlookup after adding the listed lines to sbm.conf:

```
gumby@gumby-linux-desktop:~$ nmblookup -A 192.168.1.126
Looking up status of 192.168.1.126
        ..__MSBROWSE__. <01> - <GROUP> H <ACTIVE> 
        GUMBY-LINUX-DES <00> -         H <ACTIVE> 
        GUMBY-LINUX-DES <03> -         H <ACTIVE> 
        GUMBY-LINUX-DES <20> -         H <ACTIVE> 
        WORKGROUP       <1d> -         H <ACTIVE> 
        WORKGROUP       <1b> -         H <ACTIVE> 
        WORKGROUP       <1e> - <GROUP> H <ACTIVE> 
        WORKGROUP       <00> - <GROUP> H <ACTIVE> 

        MAC Address = 00-00-00-00-00-00
```

So MSBROWSE is now showing up. But I cannot seem to find the server when I bring up smb:// on my linux box.

:( results of nmblookup -M -- -:
```
gumby@gumby-linux-desktop:~$ nmblookup -M -- -
querying __MSBROWSE__ on 192.168.1.255
name_query failed to find name __MSBROWSE__#01
```

Lastly the log:
```
gumby@gumby-linux-desktop:~$ grep "master browser" /var/log/samba/log.nmbd
  Samba name server UBUNTU_SHARE is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.126
  Samba name server UBUNTU_SHARE is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.126
  Samba name server UBUNTU_SHARE is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.126
  Samba name server GUMBY-LINUX-DESKTOP is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.126
  Attempting to become domain master browser on workgroup WORKGROUP, subnet UNICAST_SUBNET.
  become_domain_master_browser_wins: querying WINS server from IP 192.168.1.126 for domain master browser name WORKGROUP<1b> on workgroup WORKGROUP
  Samba server GUMBY-LINUX-DESKTOP is now a domain master browser for workgroup WORKGROUP on subnet UNICAST_SUBNET
  Attempting to become domain master browser on workgroup WORKGROUP on subnet 192.168.1.126
  become_domain_master_browser_bcast: querying subnet 192.168.1.126 for domain master browser on workgroup WORKGROUP
  Samba server GUMBY-LINUX-DESKTOP is now a domain master browser for workgroup WORKGROUP on subnet 192.168.1.126
  Attempting to become domain master browser on workgroup WORKGROUP, subnet UNICAST_SUBNET.
  become_domain_master_browser_wins: querying WINS server from IP 192.168.1.126 for domain master browser name WORKGROUP<1b> on workgroup WORKGROUP
  Samba server GUMBY-LINUX-DESKTOP is now a domain master browser for workgroup WORKGROUP on subnet UNICAST_SUBNET
  Attempting to become domain master browser on workgroup WORKGROUP on subnet 192.168.1.126
  become_domain_master_browser_bcast: querying subnet 192.168.1.126 for domain master browser on workgroup WORKGROUP
  Samba server GUMBY-LINUX-DESKTOP is now a domain master browser for workgroup WORKGROUP on subnet 192.168.1.126
  Samba name server GUMBY-LINUX-DESKTOP is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.126

```

So ya, I am confused. The server is being implemented on the subnet, but not showing up? Can you help me understand this? Am I interpreting the output correctly?

---

### Post by jhetrick62 on 2008-02-25
Have you tried manually mounting this with cifs rather than smbfs?

sudo mount //xxx.xxx.xxx.xxx/sharename /mnt/yourmountpoint -t cifs -o rw,user=your_user,password=your_password  0 0

Does this work?
Can you ping the server address from any other machine?
Are you running a firewall and if so, what software are you managing it with, firestarter?

Here is the exact smb.conf file that runs on my server for the last 3 years.  It is a Fedora Core server, but that should not matter very much.  I access it from other Fedora, Ubuntu, WinXP, Win 2000 boxes.  I took out some of the shares as each user in the household has their own shares as this is meant to be a file server.

```
======================= Global Settings =====================================
[global]


   workgroup = MDKGROUP
   netbios name = jhserver

   server string = Samba Server

   security = user
   load printers = yes
   cups options = raw

   log file = /var/log/samba/%m.log
   max log size = 50

   obey pam restrictions = yes

   local master = yes

   preferred master = yes

   wins support = yes

   dns proxy = no 


#============================ Share Definitions ==============================
[homes]
   comment = Home Directories
   browseable = no
   writable = yes

# Un-comment the following and create the netlogon directory for Domain Logons
; [netlogon]
;   comment = Network Logon Service
;   path = /usr/local/samba/lib/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no


# Un-comment the following to provide a specific roving profile share
# the default is to use the user's home directory
;[Profiles]
;    path = /usr/local/samba/profiles
;    browseable = no
;    guest ok = yes


# NOTE: If you have a BSD-style print system there is no need to 
# specifically define each individual printer
[printers]
   comment = All Printers
   path = /usr/spool/samba
   browseable = yes
# Set public = yes to allow user 'guest account' to print
   guest ok = no
   writable = no
   printable = yes


[music]
   comment = Music Shares
    browseable = yes
    path = /mnt/jhraid/music
    writable = yes
    guest ok = yes
    create mask = 0775
    directory mask = 0775
    force directory mode = 0774
    valid users = jeff aaron josh jordan janice music
;   public = no
;   printable = no

[share]
	comment = /mnt/share
	browseable = yes
	path = /mnt/share
	writeable = yes
	create mask=0775
	valid users = root jeff remotejh janice

[aaron]
	comment = aaron's network file storage
	browseable = yes
	path = /mnt/jhraid/aaron
	writeable = yes
	create mask=0750
	valid users = aaron

```

If you answer the above questions I may have some advice.  I never use Winbind or any of the other stuff suggested, but it has always just worked.  I do run Iptables on this box to limit it's access points as it is publicly accessible for other services, so I had to open the proper ports to make samba work properly.

Hope this helps,
Jeff

---

### Post by GumbyX on 2008-02-25
> **jhetrick62 said:**
> Have you tried manually mounting this with cifs rather than smbfs?

sudo mount //xxx.xxx.xxx.xxx/sharename /mnt/yourmountpoint -t cifs -o rw,user=your_user,password=your_password  0 0

Does this work?
Can you ping the server address from any other machine?
Are you running a firewall and if so, what software are you managing it with, firestarter?

Here is the exact smb.conf file that runs on my server for the last 3 years.  It is a Fedora Core server, but that should not matter very much.  I access it from other Fedora, Ubuntu, WinXP, Win 2000 boxes.  I took out some of the shares as each user in the household has their own shares as this is meant to be a file server.

```
======================= Global Settings =====================================
[global]


   workgroup = MDKGROUP
   netbios name = jhserver

   server string = Samba Server

   security = user
   load printers = yes
   cups options = raw

   log file = /var/log/samba/%m.log
   max log size = 50

   obey pam restrictions = yes

   local master = yes

   preferred master = yes

   wins support = yes

   dns proxy = no 


#============================ Share Definitions ==============================
[homes]
   comment = Home Directories
   browseable = no
   writable = yes

# Un-comment the following and create the netlogon directory for Domain Logons
; [netlogon]
;   comment = Network Logon Service
;   path = /usr/local/samba/lib/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no


# Un-comment the following to provide a specific roving profile share
# the default is to use the user's home directory
;[Profiles]
;    path = /usr/local/samba/profiles
;    browseable = no
;    guest ok = yes


# NOTE: If you have a BSD-style print system there is no need to 
# specifically define each individual printer
[printers]
   comment = All Printers
   path = /usr/spool/samba
   browseable = yes
# Set public = yes to allow user 'guest account' to print
   guest ok = no
   writable = no
   printable = yes


[music]
   comment = Music Shares
    browseable = yes
    path = /mnt/jhraid/music
    writable = yes
    guest ok = yes
    create mask = 0775
    directory mask = 0775
    force directory mode = 0774
    valid users = jeff aaron josh jordan janice music
;   public = no
;   printable = no

[share]
	comment = /mnt/share
	browseable = yes
	path = /mnt/share
	writeable = yes
	create mask=0775
	valid users = root jeff remotejh janice

[aaron]
	comment = aaron's network file storage
	browseable = yes
	path = /mnt/jhraid/aaron
	writeable = yes
	create mask=0750
	valid users = aaron

```

If you answer the above questions I may have some advice.  I never use Winbind or any of the other stuff suggested, but it has always just worked.  I do run Iptables on this box to limit it's access points as it is publicly accessible for other services, so I had to open the proper ports to make samba work properly.

Hope this helps,
Jeff

That mount command just causes the mount help text to be displayed. Its not accepting it as a vaild mount command. I have never mounted a network *anything* in this way, so I don't understand what you are trying to get me to do or why it is not accepting it.

To answer your other questions, I am running firestarter, but with the problems I have been having, I have disabled it when I try doing the stuff you guys tell me to try. Also, I have Samba port open in Firestarter and it did work in the past, so I don't think that is the problem.

---

### Post by jhetrick62 on 2008-02-25
Ok, sorry!  I added the "  0 0" at the end which is only used in an fstab mount statement.  Should be:

sudo mount //xxx.xxx.xxx.xxx/sharename /mnt/mountpoint -t cifs -o rw,user=youruser,password=yourpassword

What OS are you issuing the mount statment from?

Jeff

---

### Post by GumbyX on 2008-02-25
> **jhetrick62 said:**
> Ok, sorry!  I added the "  0 0" at the end which is only used in an fstab mount statement.  Should be:

sudo mount //xxx.xxx.xxx.xxx/sharename /mnt/mountpoint -t cifs -o rw,user=youruser,password=yourpassword

What OS are you issuing the mount statment from?

Jeff

Ah ok. The command when through this time.Sadly it didnt work:

```
gumby@gumby-linux-desktop:~$ sudo mount //192.168.1.126/gumby-linux-desktop /mnt/tmp -t cifs -o rw,user=gumby,password=mmpr
mount: //192.168.1.126/gumby-linux-desktop is not a valid block device

```

---

### Post by Eiríkr on 2008-02-26
Hey there GumbyX --

The "sharename" part of the mount command should be the name of one of your shares as defined at the bottom of your /etc/samba/smb.conf file.  The "xxx.xxx.xxx.xxx" part used to be either the IP of your SMB server, or its name, but it sounds like the shift to the newer "cifs" type (the "-t cifs" part) means that you now have to use your SMB server IP *only*.  At any rate, I haven't had much success using names since the switch.  

So to try this again, let's try using your Vids share.  Type the following into a terminal:
[font=courier]sudo mount //192.168.1.126/Vids /mnt/tmp -t cifs -o rw,user=youruser,password=yourpassword[/font]

I know a lot of the CLI stuff looks plug-ugly, but given how much more direct it all is, it often works better than a GUI, and generally gives you more informative error messages when it doesn't.  :)

Anyway, [font=courier]mount[/font] is your basic command for mounting filesystems.  It's great for mounting all kinds of things, from SMB shares to NFS shares, and even other directories.  Here we're having you use [font=courier]sudo[/font] first becuase usually only root is allowed to mount things, unless they're explicitly defined as user-mountable in the /etc/fstab file.  Try typing [font=courier]less /etc/fstab[/font] just to see what that looks like.  

After the initial [font=courier]mount[/font] command itself come the arguments.  The [font=courier]//192.168.126/Vids[/font] part tells [font=courier]mount[/font] what it's going to mount, and the next [font=courier]/mnt/tmp[/font] part tells it where to mount it.  Then we see [font=courier]-t cifs[/font], which says the filesystem **t**ype is "cifs" (short for "Common Internet FileSystem" if memory serves, an attempt at a(nother) standard online share format).  The the [font=courier]-o[/font] switch tells [font=courier]mount[/mount] that we're providing a bunch of **o**ptions, in this case [font=courier]rw[/font] for read-write access (as opposed to [font=courier]ro[/font] or read-only), and then the obvious [font=courier]user[/font] and [font=courier]password[/font] options.  

HTH,

Eiríkr

PS -- If the above [font=courier]mount[/font] command works, you should be able to see the contents of your Vids share by typing [font=courier]ls /mnt/tmp[/font].  It's probably not important, but it might be best to remember to unmount the share when you're done by typing [font=courier]sudo umount /mnt/tmp[/font].

---

### Post by jhetrick62 on 2008-02-26
Ditto to Eriikr!  If that works, we can eventually talk about using the netbios name vs. the ip address.  I will admit, that I just use the IP address in all of my networks as I didn't take the time to figure the rest out when it didn't work at first.

Good first step and my guess is that smbfs isn't installed as it gave you an error message.

Jeff

---

### Post by GumbyX on 2008-02-26
> **Eiríkr said:**
> Hey there GumbyX --

The "sharename" part of the mount command should be the name of one of your shares as defined at the bottom of your /etc/samba/smb.conf file.  The "xxx.xxx.xxx.xxx" part used to be either the IP of your SMB server, or its name, but it sounds like the shift to the newer "cifs" type (the "-t cifs" part) means that you now have to use your SMB server IP *only*.  At any rate, I haven't had much success using names since the switch.  

So to try this again, let's try using your Vids share.  Type the following into a terminal:
[font=courier]sudo mount //192.168.1.126/Vids /mnt/tmp -t cifs -o rw,user=youruser,password=yourpassword[/font]

I know a lot of the CLI stuff looks plug-ugly, but given how much more direct it all is, it often works better than a GUI, and generally gives you more informative error messages when it doesn't.  :)

Anyway, [font=courier]mount[/font] is your basic command for mounting filesystems.  It's great for mounting all kinds of things, from SMB shares to NFS shares, and even other directories.  Here we're having you use [font=courier]sudo[/font] first becuase usually only root is allowed to mount things, unless they're explicitly defined as user-mountable in the /etc/fstab file.  Try typing [font=courier]less /etc/fstab[/font] just to see what that looks like.  

After the initial [font=courier]mount[/font] command itself come the arguments.  The [font=courier]//192.168.126/Vids[/font] part tells [font=courier]mount[/font] what it's going to mount, and the next [font=courier]/mnt/tmp[/font] part tells it where to mount it.  Then we see [font=courier]-t cifs[/font], which says the filesystem **t**ype is "cifs" (short for "Common Internet FileSystem" if memory serves, an attempt at a(nother) standard online share format).  The the [font=courier]-o[/font] switch tells [font=courier]mount[/mount] that we're providing a bunch of **o**ptions, in this case [font=courier]rw[/font] for read-write access (as opposed to [font=courier]ro[/font] or read-only), and then the obvious [font=courier]user[/font] and [font=courier]password[/font] options.  

HTH,

Eiríkr

PS -- If the above [font=courier]mount[/font] command works, you should be able to see the contents of your Vids share by typing [font=courier]ls /mnt/tmp[/font].  It's probably not important, but it might be best to remember to unmount the share when you're done by typing [font=courier]sudo umount /mnt/tmp[/font].

First, thanks for explaining Eiríkr. 

Second: It worked!!! SWEET!!! So the server is running, but the netbios name isn't taking for some reason. I shall wait for any ideas you guys have about fixing the problem, but I wanted to say thanks for sticking with my to try and figure this all out. Doesn't happen all the time, but its nice when it does. Thanks.

---

### Post by jhetrick62 on 2008-02-26
Glad to see as this one got dragged out.  It's a ton easier to establish that the server is working and narrow down the problems.  I may leave the netbios one to someone more expert than I as I do not mount my shares with their name, I mount with their IP address as it never changes anyway on my network.

My suggestion for now is to get your shares listed in fstab so that you can more easily mount them either automatically on boot or manually.  Once listed in fstab, you can mount a share by the command "sudo mount /mnt/tmp", meaning by asking for the mount point rather than remembering all of the individual ones.  Your fstab will be read then and all the info that is there will be used to mount the share.  You will also need a different mount point for each share that you want to mount.

In fstab it would be:
mount //192.168.1.126/Vids /mnt/tmp   cifs   rw,user=youruser,password=yourpassword,noauto 0 0

Do the same for every mount.  Use "auto" in place of noauto if you want them automatically mounted at boot time.

Goodluck,
Jeff

---

### Post by Eiríkr on 2008-02-26
@Jeff --

I think smbfs comes by default as part of the Ubuntu Samba package, so it seems unlikely that it wouldn't be installed.  I may be wrong, but I suspect GumbyX's error message happened because he slightly misunderstood your suggestion, and tried to mount not one of his shares, but his SMB servername instead:
```
gumby@gumby-linux-desktop:~$ sudo mount //192.168.1.126/**gumby-linux-desktop** /mnt/tmp -t cifs -o rw,user=gumby,password=xxxx
mount: //192.168.1.126/gumby-linux-desktop is not a valid block device
```
So [font=courier]mount[/font]'s response here is perfectly correct: [font=courier]gumby-linux-desktop[/font] is in fact **not** a block device (i.e. disk drive or share) at all.  :)


@GumbyX --

For that [font=courier]/etc/fstab[/font] file I mentioned earlier, have a look at the contents of that file, and if you want to mount your SMB shares automatically at boot, open the file for editing (something like [font=courier]sudo gedit /etc/fstab[/font] should do nicely) and add a line like the following to the bottom:
```
//192.168.1.126/Vids /shares/Vids cifs auto,rw,iocharset=utf8,username=gumby,password=YOURPASSWORD
```
This is similar syntax to the [font=courier]mount[/font] command -- the first argument tells [font=courier]mount[/font] what to mount, the second tells it where (make sure whatever directory you specify exists!), then we get the filesystem type (the [font=courier]-t[/font] part for the [font=courier]mount[/font] command when you run it manually), and then come the options (the [font=courier]-o[/font] part for [font=courier]mount[/font]).  The fstab options include the [font=courier]auto[/font], [font=courier]noauto[/font], and [font=courier]user[/font] instructions.  Auto / noauto refer to how the share is mounted -- automatically at boot, or not.  "User" on its own (i.e. not [font=courier]user=USERNAME,[/font] but rather just [font=courier]user,[/font]) tells the OS that the share should be mountable / unmountable by users -- otherwise only root can do this.  

If you have any filenames with extra non-ASCII characters to them such as ö or ñ or Æ or &#272; or anything in Japanese, you might need the [font=courier]iocharset=utf8,[/font] option here (assuming of course that you're using UTF-8 encoding for your filesystem), otherwise you can leave that part out.  Also, some folks have reported that if the [font=courier]cifs[/font] filesystem type doesn't work, using [font=courier]smb[/font] might work instead.  Be sure to run [font=courier]mount[/font] manually to test your selection of filesystem type and your options first, before you add the line to /etc/fstab.  :)

HTH,

Eiríkr

PS -- Don't know what's wrong with my browser / connection, but something hiccupped when I loaded this thread this morning and I didn't even see the last two posts by Jeff and GumbyX.  Doh!  Sorry for the resulting repetition folks, but glad to hear that things are finally working.  :D

---

### Post by Eiríkr on 2008-02-26
> **GumbyX said:**
> First, thanks for explaining Eiríkr. 

Second: It worked!!! SWEET!!! So the server is running, but the netbios name isn't taking for some reason. I shall wait for any ideas you guys have about fixing the problem, but I wanted to say thanks for sticking with my to try and figure this all out. Doesn't happen all the time, but its nice when it does. Thanks.

No trouble at all.  ;)

And I may have found a lead regarding the netbios name problem.  Have a look at [thread=707377]this thread[/thread] and see if changing your /etc/hosts file helps at all.  

Cheers,

Eiríkr

---

### Post by JESii on 2008-02-27
NETBIOS names are limited to 15 characters long or less... that's why your name "gumby_linux_desktop" is getting truncated to "gumby_linux_des" -- I believe you're going to have to rename your system to match that limitation -- try that and see if it helps.

cheers....jon

---

### Post by Eiríkr on 2008-02-27
@JESii --

The other (possibly simpler?) option is to just specify a different name via the [font=courier]netbios name[/font] global attribute in the smb.conf file.  GumbyX originally had this specified as [font=courier]netbios name = ubuntu_share[/font], but I suggested he remove it as part of the process of trying to figure out what was going wrong.  I didn't know about the netbios name length limitation, so thank you for mentioning that.  I don't suppose you have any ideas as to why GumbyX's SMB server netbios name has not been showing up properly, regardless of what it's been set to?


@GumbyX --

From what JESii says, you'll probably want to add that [font=courier]netbios name[/font] line back into your smb.conf file.  

Cheers,

Eiríkr

---

### Post by JESii on 2008-02-27
Well... I recently had a problem myself; upgraded from 7.04 to 7.10 and my working samba config went down in flames.  I finally took the simple approach: pare the smb.conf file down to the bare minimum and see if I could get the basics to work? I did. Here's the very basic smb.conf file I used:
```
        workgroup = EDP

        netbios name = EDP15

        netbios aliases = edplist idealist edp-idealist

        interfaces = eth0

        log level = 10
```
I found in my case that I needed the "interfaces = eth0" directive because the documentation said (V3.x of samba) that there was no default for an interface, the lack of which blew nmbd out of the water. I found this out by looking at the log files
```
/var/log/samba/log.nmbd
```
and noticing the error mesages:
```
nmbd/nmbd_subnetdb.c:create_subnets(190)
  create_subnets: No local interfaces !
nmbd/nmbd_subnetdb.c:create_subnets(191)
  create_subnets: Waiting for an interface to appear ...
```
I keep having to remind myself to:

1. Simplify, simplify, simplify -- particularly when I have a problem
2. Check the logs
3. See if there's a debug mode to get LOTS of log information
4. RTDocs

And it's still a challenging process :-)

HTH...jon

---

### Post by Eiríkr on 2008-02-28
Good advice.  Monitoring the logs didn't provide much of a clue even with output set at 10 (though it's possible I was just missing it in the deluge), but simplifying is definitely something I should try.  :)

Cheers,

Eiríkr

---

### Post by GumbyX on 2008-02-29
I will be trying this stuff over the weekend. Its been a very *VERY* long week and I haven't been able to try anything. :( I thank you guys for all the help and hope you continue to help me if I find I still need it. :) Will post the results this weekend. Wish me luck!

JESii, i will probably try your idea first, just too see if it makes my life easier. Heck, all I need is to share files, not printers or any of that other stuff.

---

### Post by GumbyX on 2008-03-01
> **GumbyX said:**
> I will be trying this stuff over the weekend. Its been a very *VERY* long week and I haven't been able to try anything. :( I thank you guys for all the help and hope you continue to help me if I find I still need it. :) Will post the results this weekend. Wish me luck!

JESii, i will probably try your idea first, just too see if it makes my life easier. Heck, all I need is to share files, not printers or any of that other stuff.

I have tested and have results! If I type in my desktops IP as a SMB network address (IE smb://192.168.blaah.blah) I can access my shares through XBMC. Oddly enough, I cannot do this on the desktop but thats ok. So it seems to be a problem with the netbios name sadly. Here is the simplified smb.conf I am using

**smb..conf**
```
##workgroup = gumby
netbios name = XBMC_Share
netbios aliases = XBMC Share XBMCShare XBMCshare
server string = XBMC
interfaces = eth0
log level = 10

comment = Random Vids
[global]
wins support = no

workgroup = XBMC
[Vids]
path = /home/gumby/Desktop/Vids
comment = Random Vids
available = yes
browsable = yes
public = yes
writable = no

[Azur Vids]
path = /home/gumby/Azureus Downloads
available = yes
browsable = yes
public = yes
writable = no

[Anime Vids]
path = /media/Data/Anime Download
available = yes
browsable = yes
public = yes
writable = no

[Freddy Vs Ghostbusters]
path = /media/Data/Freddy Vs Ghostbusters
available = yes
browsable = yes
public = yes
writable = no

[Return of the Ghostbusters]
path = /media/Data/Return of the Ghostbusters
available = yes
browsable = yes
public = yes
writable = no

[Videos]
path = /home/gumby/Videos
comment = Converted Vids
available = yes
browsable = yes
public = yes
writable = no

[Music]
path = /home/gumby/Music
comment = All My Music
available = yes
browsable = yes
public = yes
writable = no
```

I will need to look into that link you gave me, Eiríkr. Seems I have to something else to get the netbios to work. For now, its going to be addressing directly to my PC's IP Address. It works, and thats all I care about at the moment.

If anyone has any other ideas, I would appreciate it.

PS Should I post my log so I can get some understanding on it?

Edit: I don't get how to set up *name resolve order*. Anyone think they can help me out with that?

---

### Post by Eiríkr on 2008-03-01
Glad to hear things are working better!  :)

One suggestion -- the [font=courier][global][/font] heading might want to come *before* any global option settings, right at the top of the file.  

> Edit: I don't get how to set up name resolve order. Anyone think they can help me out with that?
The [font=courier]name resolve order[/font] option is global, so it should go towards the top of your smb.conf file under the [font=courier][global][/font] heading but before any of the share headings.  However, the default should be fine, and default settings can be left out of the smb.conf file (and probably *should* be left out to keep things from getting cluttered).  

The idea I had behind posting that link was that you might want to edit the /etc/hosts on your client machine to include the hostname and IP address of your server.  Since you're now using a specific NetBios name in your server's smb.conf file that does *not* match your hostname, you should instead edit your /etc/samba/lmhosts file on the client.  Actually, since your client seems to be an XBox, the file has the same name but a different location.  I don't have an XBox, but on WinXP, the file is [font=courier]C:\WINDOWS\system32\drivers\etc\lmhosts[/font], with a sample in the same folder named [font=courier]lmhosts.sam[/font].  Type [font=courier]man lmhosts[/font] in a Linux terminal for other details.  

HTH,

Eiríkr

---

### Post by BLTicklemonster on 2008-03-02
What gets me is, I've been using Ubuntu for 2 years now, and until recently never could get networking to work for more than one time. After connecting, it just arbitrarily stopped working every time. And would not work again after that. 

 BUT, once I found the site linked to in my sig, networking worked great! All was well. Birds chirping, cats and dogs living in harmony, you name it.

Until now. 

Fresh Ubuntu install, I do exactly what it says to do at the site in my sig, restart the computer, try to connect to any computer on the network, and it asks for my name and password, but it won't accept my password. At all. Ever. Period. Used to, and would work great. Now it won't. At all Period.

So networking worked a few months ago, but doesn't now.

What is up with that?

Why can't networking be simple? I'm not on wireless, I'm just plain simple wires and a dlink router, and 3 xp machines along with this computer. 

It is so irritating that I can boot to XP, click a few things, and bam, I'm networked. The family laughs at me now for using Linux. Gee, how cool is that? I'm not only old as sin, but my family laughs at me for using cutting edge technology that doesn't work. You all got any idea how frustrating this is?

How about the folks working on Hardy drop any fluff (that would keep it from working on older computers - anyone notice how ubuntu is moving further and further away from working on as many machines as it used to? I don't like that) they are working on, and FIX THE STINKING NETWORKING. 

I bragged in here a short time ago how I was totally XP free on this machine. Not any more. I HAD TO PUT XP ON HERE AGAIN JUST SO I CAN SHARE FILES. THANKS GUYS. :mad:

So instead of my family embracing Ubuntu, they laugh at it, and call it JUNKBUNT***PEW***.

Nice. Really really nice. And hard head that I am, I just won't go back to XP. No, for some stupid reason, I keep using Ubuntu, even though it doesn't give me anything tangible that I can point to that makes it superior to XP in the eyes of ANYONE I KNOW, FRIENDS OR FAMILY.

---

### Post by Eiríkr on 2008-03-02
> ...my family laughs at me for using cutting edge technology that doesn't work...

I've read lots of Vista stories along the same lines... but then again it's a bit of a rub when Linux is on a par with Vista.  Ugh.  :(  One point of refutation for your folks, however, is the simple fact that Microsoft has done absolutely everything in their power to play dirty and prevent anyone else from joining in.  If you were instead networking a bunch of Unixy machines together and leaving MS out of the party, you might well be describing a rather different picture.  (If you are in fact networking amongst Unixy machines, I strongly suggest NFS instead of Samba.  Have a look at [post=4387032]this post[/post] for starters.)

> I keep using Ubuntu, even though it doesn't give me anything tangible that I can point to that makes it superior to XP in the eyes of ANYONE I KNOW, FRIENDS OR FAMILY.
I certainly don't mean to start an argument, but being substantially cheaper strikes me as one possible advantage, even if it's not working terribly well for you at the moment... but anyway.  :)

As for the link you sent, it's Greek to me, ironically enough, because I always go straight to the smb.conf file and have never set up SMB sharing via the GUI.  And since I'm running Xubuntu (for its pared-down GUI, good for a lower-end server), I don't even *have* the GUI tools in place to do this.  

However, I was interested to note that the directions make no mention of the fact that this whole logon process from Windows is much simpler **when your Lin and Win usernames and passwords match**.  That's how I've got it set up here on my machine, for years running, on multiple flavors of Linux, and it's been quite convenient.  

Regarding your post, if you're venting, feel free.  When it comes to software, my approach has generally been pragmatic -- use what works for you.  If it doesn't work and can't be made to after a reasonable amount of time invested in troubleshooting, find something else that will work better.  If, on the other hand, you're looking for assistance, I for one am certainly happy to pitch in, right down to the nitty gritty of getting a sane smb.conf file in place (the file that contains all the configurations for your Samba server, the side of things that allows Windows machines to log into Ubuntu file shares).  Generally the first step in this process is to describe your symptoms (which you've done, thanks) and then post the contents of your smb.conf file (usually [font=courier]/etc/samba/smb.conf[/font]).  

Cheers,

Eiríkr

---

### Post by BLTicklemonster on 2008-03-02
Sorry, I was venting. I've removed samba, and I've tried everything anyone has ever posted (that I've seen here), and none have worked, so I'm back to just giving up and basically accepting that this is not a networked machine. I can stash stuff on my ntfs partitions, then boot to XP if I want to share something that won't fit in an email. It's just honestly not worth the time or effort to keep dicking around with this junk. Yeah, it works for a lot of people, but not me.

What really pisses me off is that it worked great a couple of months ago. Then I did an upgrade, and it stopped working. Now, even with a fresh install and no upgrades it won't work at all. Just keeps showing me the other machines and asking for a password that I have already entered that doesn't work.

Thanks for the reply, though.

---

### Post by Eiríkr on 2008-03-02
No trouble.  I'm sorry to hear SMB went belly up on you; I've often heard of such problems with GUI-based configs not surviving upgrades, which makes me wonder what's going on 1) during GUI-based configuration in the first place (I've seen some very dodgy smb.conf files created/altered by GUI tools), and then 2) during the upgrades.  I long ago learned the hard way, when an upgrade over an existing install resulted in an unbootable machine (first with RedHat, then again later with Mandrake), to keep all my user data on a separate partition, and then just wipe the root partition and start with a fresh install.  In-place upgrading has always been a problem for me.  

Re-reading your first post to this thread, one thing occurs to me -- the instructions at the site linked to in your sig describe how to set up the username and password for connecting **to** an Ubuntu SMB server, but if I understand you correctly, you're having problems connecting to Windows boxes **from** an Ubuntu machine?  If my understanding is right, the username and password you should use are the ones you'd use to log into the Windows box you're trying to connect to.

Say we've got the following setup:```
             M1: Win     M2: Win     M3: Ubuntu
Usernames:   fred        bob         butter
Passwords:   broccoli    gibberish   1234
                                    ("Amazing, I've got exactly the same combination 
                                       on my luggage!")
```

The site in your sig describes how to set up the Samba username and password for M3, using the same system-level username and password that you'd use to log into M3 when you boot it up -- in this case, "butter" and "1234".  This is what you'd use when accessing a share on M3, from M1 or M2.  Meanwhile, when you're on M3 and trying to access shares on M1 or M2, you'd have to instead use the usernames and passwords specific to those machines -- "fred" and "broccoli", or "bob" and "gibberish".

Does this all make sense?  Have I read your posts correctly?

(I'm never one to leave a good puzzle unsolved. :))

Cheers,

Eiríkr

PS -- Nice location shown in your profile.

---

### Post by JESii on 2008-03-02
@Gumby... I think Eirikr is on the right track here. I've found Samba to be extremely finicky about how things are defined and your mixing of [global] parameters both with and without a section header might well be the problem.  I think what you want is something like the following:

```
[global]
workgroup = ...
netbios name = ...
...

[vids]
...etc...
```

Also, it may be worth mentioning to make darned sure that your NetBIOS name matches everywhere.

Finally, I was a little surprised to see that your path names work: they seem to have spaces embedded and are not enclosed in quotes... or am I just not understanding how the parms are set up for the Vids sections?

Glad to hear that you've got parts of it working...cheers...jon

---

### Post by Eiríkr on 2008-03-02
The smb.conf file appears to be parsed differently than, say, bash scripts, and spaces in path names have never been a problem for me either.  Well, they can cause hiccups when *mounting* them on the command line, but Samba seems to be perfectly capable of serving them up without quoting or otherwise escaping in the conf file.  :)

Cheers,

Eiríkr

---

### Post by BLTicklemonster on 2008-03-02
I'm trying to be able to go from this box to XP and back. The link worked a few months ago just fine, but something changed. Now I try it, and heck, I can see the xp boxes, they can see me, but when I try to enter the username and password, it won't accept them. It's like the only thing really stopping me is that I can't get a password to work. We don't even use passwords on the xp boxes (horrors) because we treat these things like UNSECURE devices, so we don't go putting stuff on them that would get anybody anywhere if they hacked us. Besides the hardware firewall and all help, of course. 

I've got pictures, music, etc I'd like to move around here, and it would be nice to be able to bring up one of the other machines on any machine in the house at any time, regardless, and EXPECT IT TO WORK EVERY TIME I TRY IT.

Simple, basic, no frills home network. That's all I want. No big deal, you'd think. But I think that the linux network people are so wrapped up in wanting total security at all costs that this never occurs to them. And I'm not about to go assigning win stuff and edit a whole slew of stuff either. Either it works, or it doesn't. It's just irritating that I can install XP (pro), and honeslty, bam, there's the network, ready to go, as long as I don't have an ubuntu box I'm trying to get to, that is.

---

### Post by Eiríkr on 2008-03-03
I was curious, so I went and installed Nautilus and its smb connection plugins, and then created a test Windows user with no password, so I could figure out exactly what you're talking about.  :)  And yes, what you describe is blooming annoying.  :mad:

Looking at the man page for the [font=courier]smbclient[/font] CLI tool, it sounds like connections *to* Windows machines that have no password specified might be difficult for GUI tools that don't fully implement all [font=courier]smbclient[/font] options.  From the man page:

> There is no default password. If no password is supplied on the command line (either by using this parameter or adding a password to the _-U_ option (see below)) and the _-N_ option is not specified, the client will prompt for a password,  even  if  the  desired service  does  not require one. (If no password is required, simply press ENTER to provide a null password.)

< ... snip ... >

**-N**
If specified, this parameter suppresses the normal password prompt from the  client  to the user. This is useful when accessing a service that does not require a password.

Unless  a password is specified on the command line or this parameter is specified, the client will request a password.

Try as I might, I couldn't find any options for Nautilus that would allow me to specify the equivalent of the [font=courier]-N[/font] option for SMB connections.  So I also installed Konqueror to see if that did any better -- no luck.  But then reading the man page for [font=courier]mount.cifs[/font] (the CLI tool to formally mount a Windows share onto a Linux filesystem, to make it operate like a local folder), I ran across this nugget:

> password=_arg_

specifies the CIFS password. If this option is not given then the environment variable **PASSWD** is used. If the password is not specified directly or indirectly via an argument to mount **mount.cifs** will prompt for a password, unless the guest option is specified.

The mention of this "guest" option ultimately led me to try changing the permissions on the shared folder *from within Windows*, like so:
[list][*]Right-click on the folder being shared
[*]Select "Properties"
[*]Select the "Security" tab
[*]For the "Group or user names:" section on top, hit the "Add" button
[*]Type in "everyone" in the "Enter the object names to be selected" box
[*]Hit "OK"
[*]Select "Everyone in the "Group or user names" section
[*]Make sure the required permissions are set in the "Permissions for Everyone" section below (such as "Read", "Write", etc.)[/list]
And *bam*, access via Nautilus or Konqueror is no problem at all -- you don't even get the login prompt.

> **BLTicklemonster said:**
> I'm trying to be able to go from this box to XP and back. The link worked a few months ago just fine, but something changed. 

< ... snip ... >

Simple, basic, no frills home network. That's all I want. No big deal, you'd think. But I think that the linux network people are so wrapped up in wanting total security at all costs that this never occurs to them. 

There might be something to that.  However, Microsoft has also been very busy trying to make sure no one else can easily interoperate with them -- there've been years-long lawsuits in the EU about exactly this issue.  And Windows Automatic Updates make it pitifully easy for MS to shove out an "udpate" that changes something minor but undocumented, and whoops -- suddenly something someone else is trying to do doesn't work anymore.  I grant you that sometimes folks on the OSS side of the fence can have their heads stuck in interesting places, but on the flip side, MS has a vested interest in breaking things, while OSS folks ultimately want things to work -- we're not in it for the money, we're in it to get things done (well, at least I am).  :)  Case in point: I'm taking a couple hours this morning to figure out how to get your setup working, just because I'm interested in a good challenge and want things to work.  Try getting MS to explain any of the OS's myriad bugs without buying a painfully expensive support ticket.  :-P

> **BLTicklemonster said:**
> And I'm not about to go assigning win stuff and edit a whole slew of stuff either. Either it works, or it doesn't. 

I hope changing the permissions on the shared folder(s) doesn't count as "a whole slew of stuff".  Assigning perms to "Everyone" is crazy from a security standpoint, but it's the ultimate of convenience for an avowed insecure machine like what you describe.  

HTH,

Eiríkr

---

### Post by BLTicklemonster on 2008-03-04
But... nothing's changed on the XP boxes. I used to be able to connect to them, and they to me. Now, I can see them fine, but when I try to click on any of them, I'm asked for my username and password. When I enter the password I set, I'm denied. I just don't understand why the password doesn't work. I guess there's no file I can edit, huh?

---

### Post by Eiríkr on 2008-03-04
I'm not terribly familiar with GUI-based SMB browsing, so I'll have to take a look and see what config file innards look like.  Two possibilities arise in my thinking -- 1) the update you mentioned to Ubuntu included an upate to the Samba client software that changed the behaviour; or 2) an update to Windows has changed what Windows asks for.  I know I've seen numerous "Security Updates for Windows XP", and it's entirely possible that one of these has changed how permissions work for shares.  Or maybe even both 1 and 2 happened?

I'll see what I can find in terms of Ubuntu config files or settings and post back here with what I find.  

Cheers,

Eiríkr

---

### Post by BLTicklemonster on 2008-03-04
Cool, thanks. I never update windows past the sp2 disk I have. Heck, it's bad enough the way it is.

---

### Post by Eiríkr on 2008-03-04
I'd read somewhere that folks were finding XP mysteriously auto-updating itself in the background despite having Automatic Updates turned off, but I'm uncertain as to the details.  

Be that as it may, after much online perusing and googling, it looks like null-password logins are just plain seriously borked.  I set up a dummy account on my end with explicit permissions on the Windows side on a dummy share, both in terms of the filesystem ("Security" tab in Properties") and in terms of the share ("Sharing" tab then "Permissions" button in Properties), and then tried mounting that numerous different ways.  These examples all use the CLI [font=courier]mount[/font] tool to mount a Windows share, making it look and act like a local folder.  
[list][*]**With a Windows password:** The Windows user account has a password specified.  Mounting here results in the expected mount of an SMB share where indicated.
```
ubuser@ubclient:~$ sudo mount.cifs //winbox/bookshelf ~/two -o uid=1000,gid=1000,ro,username=Test
Password: ****
ubuser@ubclient:~$ ls ./two
AUTORUN.INF  BOOKS  IE4INTEG  INSHLP  README.TXT  SETUP.EXE
ubuser@ubclient:~$ sudo umount ./two
ubuser@ubclient:~$
```

[*]**No Windows password, "guest" option in client command:** The Windows user account has no password assigned at all.  Attempting this mount just wouldn't work, and what's worse, the CLI error message claimed whatever I was trying to mount wasn't a directory -- despite clear success above.  This error is just plain silly, and is about as unhelpful as Windows error messages usually are.  The only difference between the successful mount above and now is that I've removed the password from the Windows user and added the "guest" option to the mount command so it won't ask for a password.  
```
ubusuer@ubclient:~$ sudo mount.cifs //winbox/bookshelf ~/two -o uid=1000,gid=1000,ro,username=Test,guest
mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
ubusuer@ubclient:~$
```

[*]**No Windows password, password prompt in client command:** I get the same results if I leave out the "guest" and then just hit Enter in the ensuing password prompt:
```
ubusuer@ubclient:~$ sudo mount.cifs //winbox/bookshelf ~/two -o uid=1000,gid=1000,ro,username=Test
Password:
mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
ubusuer@ubclient:~$
```

[*]**No Windows password, obscure "sec=none" option in client command:** After much poking around online, I found mention that the "sec=none" command is *supposed* to indicate a completely anonymous login, with both username and password set to null values, but it seems that if a username is specified, only the password is supposed to be set to null, which is what we want here.  But still no go.
```
ubusuer@ubclient:~$ sudo mount.cifs //winbox/bookshelf ~/two -o uid=1000,gid=1000,ro,username=Test,sec=none
mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
ubusuer@ubclient:~$
```

[*]**Windows "Sharing" permissions granting "Everyone" access:** This is the ***only*** way I've been able to get no-authentication Windows sharing to work.  [list=1][*]From within Windows, right-click the folder being shared
[*]Click Properties
[*]Select the "Sharing" tab
[*]Click the "Permissions" button
[list][*]If "Everyone" is not in the "Group or user names" list, click "Add", type "everyone" and hit Enter[/list]
[*]Select "Everyone" in the "Group or user names"
[*]Make sure "Everyone" has the desired permissions for this share ("Full Control", "Change", "Read")[/list]
Now insecure logons work just fine.  You can either enter whatever you want for username and password, or just use the "sec=none":
```
ubusuer@ubclient:~$ sudo mount.cifs //winbox/bookshelf ~/two -o uid=1000,gid=1000,ro,username=MyUncleFredAteMyRutabaga,password=Limburgher
ubuser@ubclient:~$ ls ./two
AUTORUN.INF  BOOKS  IE4INTEG  INSHLP  README.TXT  SETUP.EXE
ubuser@ubclient:~$ sudo umount ./two
ubuser@ubclient:~$
```
... or ...
```
ubusuer@ubclient:~$ sudo mount.cifs //winbox/bookshelf ~/two -o uid=1000,gid=1000,ro,sec=none
ubuser@ubclient:~$ ls ./two
AUTORUN.INF  BOOKS  IE4INTEG  INSHLP  README.TXT  SETUP.EXE
ubuser@ubclient:~$ sudo umount ./two
ubuser@ubclient:~$
```
Access via Nautilus is also seamless, with no login prompting at all.  **w00t!**[/list]

If you want, Windows shares can be automatically mounted at boot-up so they are always available, but the process is a bit more involved for Ubuntu than I'd initially hoped due to the order in which things happen during boot, so I won't go into it unless you're interested.  

Sorry things aren't more automagically simple, but I hope this post might come in handy nonetheless.

Cheers,

Eiríkr

---

### Post by knitmom on 2008-03-05
> # With a Windows password: The Windows user account has a password specified. Mounting here results in the expected mount of an SMB share where indicated.
Code:

ubuser@ubclient:~$ sudo mount.cifs //winbox/bookshelf ~/two -o uid=1000,gid=1000,ro,username=Test
Password: ****
ubuser@ubclient:~$ ls ./two
AUTORUN.INF  BOOKS  IE4INTEG  INSHLP  README.TXT  SETUP.EXE
ubuser@ubclient:~$ sudo umount ./two
ubuser@ubclient:~$



I tried this but it doesn't want to mount cifs.  Do I need to change directories once I'm in terminal mode?  My prompt says "me@me-laptop:~$"  

I already entered the smbpasswords and can access ubuntu shared files from XP but not the other way around.  

Thanks

---

### Post by knitmom on 2008-03-05
> 
...my family laughs at me for using cutting edge technology that doesn't work...

I saw this and had to laugh.  My son and I are trying to convince my husband how great ubuntu is and he kinda does the same thing.....mocks us!  Meanwhile, he was having major problems with XP and I just fixed his laptop which had stopped working.  I almost loaded ubuntu 7.10, but didn't ;)  I'm still having issues with 7.10 on my laptop and didn't want to hear him complain about it.  Though, I'm learning a lot in the process of fixing the issues.

---

### Post by BLTicklemonster on 2008-03-05
> **knitmom said:**
> I saw this and had to laugh.  My son and I are trying to convince my husband how great ubuntu is and he kinda does the same thing.....mocks us!  Meanwhile, he was having major problems with XP and I just fixed his laptop which had stopped working.  I almost loaded ubuntu 7.10, but didn't ;)  I'm still having issues with 7.10 on my laptop and didn't want to hear him complain about it.  Though, I'm learning a lot in the process of fixing the issues.

Ah, a kindred spirit. Bless you. :)


Anyway, I give up. 

If they ever find a way to do this easily, I'll start trying again, but at present, it's just too "the reason I never used linux until Ubuntu came along" for me to mess with. If I HAD to home network, Windows would be worth the price.


I really thought Ubuntu would have taken care of this before they moved on to other things... like say around Dapper is where they should have had a gui rock solid networking solution, but apparently no one up there is paying attention to details any more, their outside the box chasing clouds. Success does that.

---

### Post by Eiríkr on 2008-03-05
> If they ever find a way to do this easily, I'll start trying again, but at present, it's just too "the reason I never used linux until Ubuntu came along" for me to mess with. If I HAD to home network, Windows would be worth the price.

I really thought Ubuntu would have taken care of this before they moved on to other things... like say around Dapper is where they should have had a gui rock solid networking solution, but apparently no one up there is paying attention to details any more, their outside the box chasing clouds. Success does that.

Quite possibly.  But to play devil's advocate ;), any attempt at cooperating with Windows is trying to hit a moving target, and one that's perfectly happy to pull the rug out from under you if it can.  :shock:

Good luck in the meantime, :)

Eiríkr

---

### Post by Eiríkr on 2008-03-05
> **knitmom said:**
> I tried this but it doesn't want to mount cifs.  Do I need to change directories once I'm in terminal mode?  My prompt says "me@me-laptop:~$"  

I already entered the smbpasswords and can access ubuntu shared files from XP but not the other way around.  

Thanks

Hey there knitmom --

My wife's quite the knitter too.  :)

Anyway, looking at what you describe, I'm not entirely sure what's happening on your end, but a few questions / points to note rise to mind:
[list]
[*]Entering the smbpasswords is exactly what you need to do for accessing to your Ubuntu shares from other machines, but it has nothing to do with accessing Windows shares from your Ubuntu machine.  For that, you need to enter the username and password you'd use to log in to whatevern Windows machine you're connecting to.  
[*]In the [font=courier]mount.cifs[/font] command arguments, the text after the double slash _//_ should be the name of the Windows machine, then another single slash _/_ followed by the name of the share.  You can double-check the name of the share on the Windows machine (which can optionally be totally different from the name of the actual folder) by right-clicking the shared folder from within Windows, select Properties, then the Sharing tab, and see what it says in the "Share name" text area.  So in my example, I've got a windows machine called "winbox" with a shared folder that could be called anything, but is shared under the name "bookshelf".  
[*]In the [font=courier]mount.cifs[/font] command arguments, the following argument is the path to the (empty!) directory where you'd like to mount the share.  This directory **must **exist, it will not be created by the [font=courier]mount.cifs[/font] command.  
[*]Your login prompt [font=courier]me@me-laptop:~$[/font] shows first your username ("me"), then your host name after the _@_, a bit like in email addresses (actually I think this Unixy convention is why email addresses happened the way they did), then a colon, then your present working directory (NB: also contained in the environment variable PWD, which you can see by typing [font=courier]echo $PWD[/font]), and lastly the prompt type indicator -- _$_ for normal users and _#_ for root.  On a standard-config Ubuntu machine you'll never see the _#_ prompt.  So here your PWD is your home directory, or _~_ in shorthand.  
[*]The [font=courier]~/two[/font] bit in my example tells [font=courier]mount.cifs[/font] to mount to the "two" directory that is in my home directory.  
[*]You can run the [font=courier]mount.cifs[/font] command from anywhere in your filesystem, so no worries about changing directories first.  
[*]There are *many* possible [font=courier]mount[/font] options that can be added after the _-o_ flag.  Have a look at [font=courier]man mount[/font] and [font=courier]man mount.cifs[/font] for more details.  The ones I have here include:
[list][*]**ro** for "read-only"
[*]**uid** and **gid** to specify who should have ownership of the directory into which the share is mounted (defaults to root:root if you don't specify, which can be a pain).  You can use user and group names instead of numeric IDs if you want (which I just learned myself yesterday :)).  
[*]another pair of options related to ownership and permissions that I don't use here but that can be handy are **file_mode** and **dir_mode**.  Have a look at [this Wikipedia article]("http://en.wikipedia.org/wiki/File_system_permissions") and [font=courier]man chmod[/font] for more about Unixy file permissions.  [/list]
[/list]

Hope this helps.  Post again to let us know how it goes.  

Cheers,

Eiríkr

---

### Post by webheavy on 2008-03-26
I ran into the same problems today on v7.10. My fix was to start the Live CD. That immediately connected to my two Win2K boxes to the Live CD instance when the installed 7.10 would not.

Then I mounted the hard drive and copied the smb.conf file from the running Live CD OS onto my hard drive which is the installed but at that moment, not the running OS.

After that, I ended the Live CD OS and restarted the installed  copy. I copied the smb.conf to /etc/samba and edited the domain to my workgroup name. I left everything else in smb.conf  untouched.

Then just did a sudo smbd SIGHUP which didn't help. Then did a sudo nmbd SIGHUP which put the Ubuntu access on the Win2K box. But that was just a useless attempt at avoiding a cold boot which got the whole thing running in both directions except for the nasty login from Win2K to Ubuntu failure.

Next, I opened that suspicious config applet called "Samba Server Configuration" with about:

[INDENT]Samba Server Configuration Tool 1.2.50
Copyright 2002 - 2005 (c) Red Hat, Inc. 
Copyright 2002 - 2004 (c) Brent Fox <bfox@redhat.com>
Copyright 2002 - 2004 (c) Tammy Fox <tfox@redhat.com>
Copyright 2004 - 2005 (c) Nils Philippsen <nphilipp@redhat.com>

A graphical interface for configuring SMB shares[/INDENT]

I added a share and then found my Ubuntu login name under Preferences > Samba Users. Edit User allowed me to enter a Samba Password.

Now back to Win2K add the 'Network Place' \\machineName\ShareName. That responded with the login dialog where I entered the Samba user name and password I set above.

Unfortunately that was a day's effort. I'm committed to get a web server and pretty web client all running in one cheap laptop, HP/Compaq F756NR along with dual screens to drive a projector. This goes on the road to demo a web application and I don't want to rely on an unknown wifi and I don't want to lug around another box just as a web server.

Ubuntu works so far!

Roger

PS: That avatar was dragged from a Win2K box onto this Ubuntu laptop without a hitch.

---

### Post by Eiríkr on 2008-03-26
One easier way of restarting Samba to ensure that any smb.conf file changes are properly reflected is to restart the Samba service, which will handle both the smbd and nmbd processes at once:
```
sudo /etc/init.d/samba restart
```

Note that sometimes a full-on Samba restart is *required* to get changes to be properly reflected; simply using "reload" instead of "restart" sometimes down't seem to do the trick.

Also, note that Windows is very pushy about caching authentication info (share logins), so if your Samba username and password ever change, suddenly share access will simply fail, and Windows will not ask for a different username or password.  In such a case, you might need to follow some of the steps in [post=4491515]KennedyM's useful HOWTO[/post] for forcing Windows to not be so stupid.  

Cheers,

Eiríkr

PS -- I've seen some very fugly results from GUI tools, so if things don't work the way you need them too, you'll probably have to use the CLI some.  But don't worry -- we'll help.  ;)

---

