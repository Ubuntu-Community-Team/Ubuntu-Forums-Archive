---
title: "Samba Problems"
date: 2015-12-27
forum: Networking &amp; Wireless
---

### Post by HDTimeshifter on 2015-12-27
I have a server running Ubuntu 12.03 LTS desktop version with a shared drive that I set up a couple of years ago and shared a second drive on it and folders on that drive. I am able to read and write files from both a PC and laptop running Ubuntu 14.04 LTS desktop and Windows 7. It cannot be upgraded beyond 12.03 because it has old integrated graphics that the newer versions don't support. I recently built a newer server, loaded Ubuntu 14.04 LTS on it and added a second data drive as well.

1.  I'm not very familiar with the Linux drive partition types, but the old server data drive was partitioned as Ext 3/4 and I didn't see a similar option in Ubuntu 14.04, so partitioned it's data drive as NTFS. Should I partition it a different type?
2.  I tried renaming the old server name to "OldServer", but it won't let me and gives an error message like "can't do this from backend".
3.  I also tried renaming the new server name, but it also won't let me.
4.  I was able to copy all the shared data folders from the old server drive to the new server drive.
5.  I shared the new server data drive as well as the folders on it, downloading/activating SAMBA to do that, however can't access the new data drive folders from my Ubuntu 14.04 LTS PC. I can see the new data drive and folders from my PC, but it times out whenever I try to connect with my password.

---

### Post by TheFu on 2015-12-27
For Unix-to-Unix file sharing, NFS is the best choice on a LAN, not samba.  Is there a reason you need samba?
NTFS file systems should only be used if the disk will be directly accessed from Windows (physically connected). For network access, any Linux-based file system should be used with ext4 as the default for 95% of the people.

12.03? Could that be a typo?   If you have AMD GPU (integrated), 14.04 works with that using the F/LOSS drivers fine, BTW. Intel GPUs "just work" these days.  Stay LTS.

If you want help with samba, please post config files, so we don't have to guess what you've actually done, but samba really should only be used if there are Windows clients. For Unix-based clients, NFS is faster and more capable AND easier to setup.

---

### Post by HDTimeshifter on 2015-12-27
If I a Windows client can access an NFS drive then I'll try that. I'm just familiar with Samba and that's what it defaults to when I enable local sharing. I don't see ext4 as a partition option in the Drives utility, just EFI GPT, EFI (FAT), Linux Swap, Linux, Linus lVM, various Windows options, and Other (Mac, Solaris, etc.). I guess I should just select Linux if I repartition?

The old server is actually 12.04 LTS, but is old and slow (Pentium 4 2.5 GHz 2 GB) and doesn't support wake on LAN, so will be reformatted and given away once I get the new server working to replace it.

The other thing I noticed on the new server is that when I click on Properties of the drive or folders, the group access defaults to "none" and whenever I try to click on any of the other accesses (create/delete, etc), it jumps back to "none". On the old server, it is set to create/delete. I thought I could set it up just with checking the "local sharing" box, but checked the properties, just to be sure.

---

### Post by bab1 on 2015-12-27
> **HDTimeshifter said:**
> If I a Windows client can access an NFS drive then I'll try that.  I'm just familiar with Samba and that's what it defaults to when I enable local sharing.

You should use Samba for file sharing with a Windows client.
> 
I don't see ext4 as a partition option in the Drives utility, just EFI GPT, EFI (FAT), Linux Swap, Linux, Linus lVM, various Windows options, and Other (Mac, Solaris, etc.). I guess I should just select Linux if I repartition?

The* partition type* is Linux.  The Ubuntu *default file system type (format) is ext4* for that partition.> 
The other thing I noticed on the new server is that when I click on Properties of the drive or folders, the group access defaults to "none" and whenever I try to click on any of the other accesses (create/delete, etc), it jumps back to "none". On the old server, it is set to create/delete. I thought I could set it up just with checking the "local sharing" box, but checked the properties, just to be sure.
Is this at the local host?  It sounds like some of your questions are server side (local to that host) and others are client side that deal withthe server's shares (mapped drive in Windows speak). The user ownership and permissions for a NTFS formatted file system can be set only at mount time (when made available) on the server.

[QUOTE=HDTimeshifter (first post)] Should I partition it a different type?[/QUOTE]My advice is to reformat the new partition for the server as ext4.

---

### Post by TheFu on 2015-12-28
+1 for what bab1 says.

I've never seen the "Drives" utility, sorry. **gparted** is pretty easy to use and very popular - it would be worth installing if it isn't already there. Sometimes newer GUI tools in stock Ubuntu are dumbed down too much, IMHO, sounds like "Drives" does this, but I dunno.  

Don't mix up partition types and file system types. These are different things (like a container for a container), if that makes sense.

Hard drives and file are organized thus:
* HDD - the physical drive
** Partitioning scheme - MBR/GPT
*** Partitions - there are about 100 different types including LVM, RAID, Solaris, Linux Swap, Linux
**** File Systems - ext2, ext3, ext4, btrfs, zfs, reiserfs, NTFS, fat16, fat32, xfat, and probably 20-50 others
***** Directories
****** Files

Hopefully that clears things up a bit?  At the partitions and File Systems levels, other elements can be added for in creased flexibility -  LVM does this.
Samba presents a network file system in the expected Windows Sharing manner, but the actual file system used on the system hosting those directories and files doesn't matter too much. It is generally best to use a Linux-style file system for Samba storage since that is what native Unix/Linux will expect and there are some features that the samba view simply does not provide.

You asked about NFS clients for Windows. They do exist, but usually aren't worth the hassle. I don't believe there are any free NFS clients for Windows either. I've only used commercial versions and only in a mainly Unix network. For Windows clients, samba is the best answer, but for Linux/Unix/OSX clients, NFS would provide native permissions support for the remote storage. I didn't see/remember your Window dual-boot reference, sorry.

Should say - I use both NFS and Samba here.  NFS for Unix/Linux clients and Samba for Windows. Both can be used for the same storage. ;) Of course, samba is supported by more systems, so starting with that would be smart if there are Windows clients.

---

### Post by HDTimeshifter on 2015-12-29
I repartitioned as Linux and reformatted as ext4, then was able to change the group sharing to create/delete. For some reason, the Drive utility wouldn't let me partition or format (I forget where I had that option) with encryption like I did with the old server drive. I still wasn't able to access the drive from another Ubuntu client, so tried rebooting the new server, but it reports a SMART error "about to fail" upon startup. When I launched the Disk utility again, it also reports SMART "error about to fail" regarding reallocated sectors on the data drive (if I hadn't made it clear, I built both of these servers with a system disk and a separate disk for data). So I'm wondering if the SMART error is why I couldn't encrypt it and also resulted in the access problems. I'm running an extended disk test and may just toss the drive and use another (smaller) spare.

Regarding renaming the server computer names, yes, I tried doing that directly from each server (local host).

---

### Post by bab1 on 2015-12-29
> **HDTimeshifter said:**
> I repartitioned as Linux and reformatted as ext4, then was able to change the group sharing to create/delete. For some reason, the Drive utility wouldn't let me partition or format (I forget where I had that option) with encryption like I did with the old server drive. I still wasn't able to access the drive from another Ubuntu client, so tried rebooting the new server, but it reports a SMART error "about to fail" upon startup. When I launched the Disk utility again, it also reports SMART "error about to fail" regarding reallocated sectors on the data drive (if I hadn't made it clear, I built both of these servers with a system disk and a separate disk for data). So I'm wondering if the SMART error is why I couldn't encrypt it and also resulted in the access problems. I'm running an extended disk test and may just toss the drive and use another (smaller) spare.

Regarding renaming the server computer names, yes, I tried doing that directly from each server (local host).
The drive utility (disks) is not as full featured as the tool **gparted**.   I would use that to create the partition and then format it with the ext4 file system.  Encryption is something else.  I have never encrypted any of my partitions on my servers, so I'm the wrong guy to talk to about that.

If you have a hard drive that is showing "about to fail" I would not trust that disk for any future use.  You can use it, but failure will happen, most likely at the most inopportune time   Hopefully you have the data backed up somewhere else.

Normally when I rename a host (change the hostname), I do that from that host.  The hostname is defined in the /etc/hostname file and should also be mapped to the IP address (typically using eth0) in the /etc/hosts.  You must do both or bad things will happen.  If you don't setup the /etc/hosts file correctly you will loose your sudo rights.

The hostname is not the same as the NetBIOS name (COMPUTER NAME in Windows).  The NetBIOS name can be defined in the smb.conf file. 

>  error message like "can't do this from backend". Sorry, I've never seen that error message.  What exactly were you doing when you got that message?  What app were you using?  I configure my shares by editing the smb.conf file on my servers.  I have temporarily shared directories using the GUI to create user shares.  Were you using the GUI to create usershares?

---

### Post by TheFu on 2015-12-29
I encrypt all portable computing devices using dm-crypt (whole disk encryption). I've only used the **cryptsetup** tool for this, outside automatic stuff during an install. Don't think there is a GUI tool that does it, but I don't know. HOME directory encryption complicates things, has slower performance and isn't nearly as secure (IMHO) as dm-crypt. If samba shares are encrypted, they need to be available(opened/decrypted) before samba starts.

Whenever using encrypted storage, excellent backups are mandatory. When bad things happen to encrypted data, there isn't much that can be done to get it back, except to restore from a backup.

If SMART says a disk is about to fail, I'd replace it within a day.   By the time SMART realizes a disk is going to fail, it is well beyond being safe to use for anything important. I wouldn't trust it for backups either.

I've never used any GUI to setup samba.  GUIs change too quickly for me, but basically the same smb.conf file that I've used since 1996 is still working. Plus, GUIs don't work on "server" installations, so for my needs, learning 2 things doesn't make sense (for me).

---

### Post by HDTimeshifter on 2015-12-29
I set up the computer names when I initially installed Ubuntu on them. I was attempting to rename them through the GUI (either right-clicking or on the properties page). I choose to use the Ubuntu desktop installation rather than the Ubuntu server installation since I'm not very familiar with Linux command line, plus it's much easier to use the GUI for drag and drop file manipulation. I guess I'll have to rename the hosts by editing the /etc/hostname file and remapping the IP address in the /etc/hosts file using eth0. Since I'm not familiar with that process, I wanted to do it through the GUI to avoid bad things happening.

The Disks utility worked fine for my previous server setup, but I'll take a look at gparted. My old server seemed to work fine with encryption, but with the performance and other issues mentioned, I guess I'll forgo it with the new server. I'll probably toss that bad drive, but need to finish going through and saving files off another disk so that I can re-purpose it and format it to use in the new server, so it may be a week or few before I can finish my new server build. It's a good thing this disk started failing before I started using the new server.

I was using the GUI to create local shares of directories on my data drive, but they did disappear every time I rebooted the server and I had to re-share them. I'll look at the smb.conf file and see if I can edit it to make the shares permanent.

---

### Post by bab1 on 2015-12-29
> **HDTimeshifter said:**
> I set up the computer names when I initially installed Ubuntu on them. I was attempting to rename them through the GUI (either right-clicking or on the properties page). I choose to use the Ubuntu desktop installation rather than the Ubuntu server installation since I'm not very familiar with Linux command line, plus it's much easier to use the GUI for drag and drop file manipulation. I guess I'll have to rename the hosts by editing the /etc/hostname file and remapping the IP address in the /etc/hosts file using eth0. Since I'm not familiar with that process, I wanted to do it through the GUI to avoid bad things happening.

The Disks utility worked fine for my previous server setup, but I'll take a look at gparted. My old server seemed to work fine with encryption, but with the performance and other issues mentioned, I guess I'll forgo it with the new server. I'll probably toss that bad drive, but need to finish going through and saving files off another disk so that I can re-purpose it and format it to use in the new server, so it may be a week or few before I can finish my new server build. It's a good thing this disk started failing before I started using the new server.

I was using the GUI to create local shares of directories on my data drive, but they did disappear every time I rebooted the server and I had to re-share them. I'll look at the smb.conf file and see if I can edit it to make the shares permanent.
It's pretty simple to set up the shares via the smb.conf file.  After you finish the new server build just ask here and we can show you.

You can use the GUI to rename the host too.  You do have to use a text editor so I find using a terminal based editor just as easy.  We can show you how to do that task too.

---

### Post by TheFu on 2015-12-29
To rename a host (hostname), I think there are normally 3 places. Of course, since Linux/Unix is infinitely configurable, there could be many other places that need it too. For example, if you run any servers (DB, web, email, proxies, routing, DNS, DHCP, sudoers ... ) then each of those configurations might need to be updated with any hostname change too. Make a backup of the files to be changed before starting - or just make a system-level backup if you didn't last night anyway.

1) sudo hostname {new-host-name}
2) sudoedit /etc/hosts
3) sudoedit /etc/hostname

Don't dally - do them all quickly. I'd open 3 terminals and run both sudoedit commands first to open those files inside the editors (you could lock yourself out by accident). I'd run the **sudo hostname xyzabc1234** command last.

Then I'd reboot while all the changes were fresh in my mind and see that everything worked.

Then you'll want to change the other systems on the network to know about the new hostname.  I would add the new hostname to the hosts file and not remove the old hostname until a week later. Safer that way.

Wouldn't know where to begin to use the GUI to change all these things or if there are *issues* in doing that. Can't imagine any GUI tool properly handling all the possible situations that is easy for a human to handle.

---

### Post by HDTimeshifter on 2015-12-29
I'll wait until I finish building the new server with new drive partitioned, formatted, and all data copied over from the old server and verified that I can connect to it before renaming the hosts. Then I can remove the old server host, reformat and remove its drives.

I use the old server as a file server, mainly as remote backup.

I use the Gnome File Manager and Windows Network Manager and Explorer to browse the network and remote hosts. I just click Browse Network and/or refresh the view whenever I wake up, reboot, or turn on a remote host or add shared directories. So I don't think I have to muck with the /etc/host files - just rename the hostname and verify that it changes in the /etc/hostname file on the servers I want to rename.

---

### Post by TheFu on 2015-12-29
You **must** make at least those 3 changes, including the hosts file. Certain situations may require more changes, if those services/daemons don't honor the system /etc/hostname setting. BTW, there ARE times when this is highly desirable for services that deal with multiple aliases (think virtual web hosts).

---

### Post by bab1 on 2015-12-30
> **HDTimeshifter said:**
> I'll wait until I finish building the new server with new drive partitioned, formatted, and all data copied over from the old server and verified that I can connect to it before renaming the hosts. Then I can remove the old server host, reformat and remove its drives.

I use the old server as a file server, mainly as remote backup.

I use the Gnome File Manager and Windows Network Manager and Explorer to browse the network and remote hosts. I just click Browse Network and/or refresh the view whenever I wake up, reboot, or turn on a remote host or add shared directories. So I don't think I have to muck with the /etc/host files - just rename the hostname and verify that it changes in the /etc/hostname file on the servers I want to rename.
However you want to accomplish the task of renaming the host of your server is your choice.  In the end your host must have it's hostname changed in the file /etc/hostname.  

The tool sudo makes sure that the hostname can be resolved correctly before executing.  If you want sudo (root privileges) to work correctly the new hostname must be correctly resolved via a listing in /etc/hosts.

You can use GUI tools if you wish, however the /etc/hostname file only contains the one name on a single line.  The host I am using right now is named *[COLOR="#0000FF"][I]maui*[/COLOR][/I].  The contents of /etc/hostname is```

bab@maui:~$ cat /etc/hostname
***[COLOR="#0000FF"]maui[/COLOR]***

```
It's a simple task to edit the file using as @TheFu has described.

The /etc/hosts file is also pretty simple.  There must be at least a line referencing the new hostname like this```

bab@maui:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       [COLOR="#0000FF"]***maui***[/COLOR]

```
Substitute your hostname where I have used *maui* of course.

Once again, the GUI tools edit these same files (/etc/hostname and /etc/hosts).  If you find GUI tools that you can run as root (via sudo) you certainly can use them.

---

### Post by TheFu on 2015-12-30
> **bab1 said:**
> Once again, the GUI tools edit these same files (/etc/hostname and /etc/hosts).  If you find GUI tools that you can run as root (via sudo) you certainly can use them.

Nicely said Bab1, however we also need to warn that using plain "sudo" with GUI tools can have undesirable side-effects for some systems which prevent users from being able to run those tools as their normal userid until corrected. So .... please, please use the **sudoedit** command to edit system files. You can setup any editor you like to be used with it. Whatever the system default editor is, probably nano, will be configured for use on most systems. For this task, nano is fine.  If you want gedit or geany or some other editor, just create/make your EDITOR environment variable point to whatever you select. It is ok to use sudo {insert-editor-name} if that editor does NOT create any configuration files in the HOME directory without the user specifically asking for it.  Most GUI editors will do that and most non-GUI editors will not. The way that sudoedit works, makes this problematic behavior moot. You can read more about **sudoedit** in the manpage for that command.

Be very careful using *sudo gedit* or following instructions which recommend that method. gedit is a program that will write config files and it will create the config file directories owned by root along the way. I've seen userids not be able to login to their system when it was used.  Oddly, **sudo gedit -H** is safe and so is **gksudo gedit**.  This is one of those almost never desired outcomes, but using **sudoedit** solves.

I was unaware of this issue until about 2 yrs ago so even an old-timer UNIX user like myself can learn new tricks and problems.

All these things are standard and normal system administration tasks on any Linux system. Editing a text file is a common thing and there are many tools already installed to manipulate text as inputs and outputs on every Unix-like system. Text files are a core philosophy to Unix systems and programming.
> This is the Unix philosophy: Write programs that do one thing and do it well. Write programs to work together. Write programs to handle text streams, because that is a universal interface.[https://en.wikipedia.org/wiki/Unix_philosophy](https://en.wikipedia.org/wiki/Unix_philosophy)

---

### Post by HDTimeshifter on 2016-01-04
> **TheFu said:**
> If you want help with samba, please post config files, so we don't have to guess what you've actually done, but samba really should only be used if there are Windows clients. For Unix-based clients, NFS is faster and more capable AND easier to setup.

I rebuilt the server with a new drive and still have the same problems connecting to the new shared drive. What samba files do I need to post?

---

### Post by HDTimeshifter on 2016-01-08
> **bab1 said:**
> It's pretty simple to set up the shares via the smb.conf file.  After you finish the new server build just ask here and we can show you.

Here's my smb.conf from the new server (that I can't get local shares to work):
#
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

---

### Post by HDTimeshifter on 2016-01-08
> **bab1 said:**
> It's pretty simple to set up the shares via the smb.conf file.  After you finish the new server build just ask here and we can show you.

Here's the smb.conf file from my old server (that works for sharing):
#
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
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

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

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

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
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
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
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
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

---

### Post by bab1 on 2016-01-08
[QUOTE= HDTimeshifter]
Here's my smb.conf from the new server (that I can't get local shares to work):[/QUOTE]

What shares?  Post the output of these commands from the Samba server terminal```

cat /var/lib/samba/usershares

cat /etc/hosts

cat /etc/hostname

smbtree -d3


```

---

### Post by HDTimeshifter on 2016-01-08
ls /var/lib/samba/usershares
```
data  documents  downloads  music  pictures  videos
```

cat /etc/hosts
```
127.0.0.1	localhost
127.0.1.1	i3-Server

```

cat /etc/hostname
```
i3-Server
```

smbtree -d3
```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.1.13 bcast=192.168.1.255 netmask=255.255.255.0

```

All output is almost identical to that of the old server except the old server is named "server" and it uses eth1 instead of eth0 and there is an additional line before the added interface:
```
added interface eth1 ip=fe80::20c:f1ff:fe9b:d392%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
```

There's also an "enter [username] password" at the end of the smbtree output that I omitted.

---

### Post by bab1 on 2016-01-08
We need the smbtree -d3 data after you hit the Enter key!

---

### Post by HDTimeshifter on 2016-01-08
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.1 ( 192.168.1.1 )
Connecting to 192.168.1.1 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.1 ( 192.168.1.1 )
Connecting to 192.168.1.1 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\SERVER         		Server server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name SERVER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name SERVER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SERVER<0x20>
resolve_hosts: getaddrinfo failed for name SERVER [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name SERVER<0x20>
Got a positive name query response from 192.168.1.11 ( 192.168.1.11 )
Connecting to 192.168.1.11 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\SERVER\Pictures       	
		\\SERVER\Downloads      	
		\\SERVER\Documents      	
		\\SERVER\Music          	
		\\SERVER\data           	
		\\SERVER\Videos         	
		\\SERVER\IPC$           	IPC Service (Server server (Samba, Ubuntu))
		\\SERVER\print$         	Printer Drivers
	\\READYSHARE     		NETGEAR WNDR3700
resolve_lmhosts: Attempting lmhosts lookup for name READYSHARE<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name READYSHARE<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name READYSHARE<0x20>
resolve_hosts: getaddrinfo failed for name READYSHARE [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name READYSHARE<0x20>
Got a positive name query response from 192.168.1.1 ( 192.168.1.1 )
Connecting to 192.168.1.1 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\READYSHARE\IPC$           	IPC Service (NETGEAR WNDR3700)
	\\I3-SERVER      		i3-Server server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name I3-SERVER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name I3-SERVER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name I3-SERVER<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\I3-SERVER\Pictures       	
		\\I3-SERVER\Music          	
		\\I3-SERVER\Downloads      	
		\\I3-SERVER\Documents      	
		\\I3-SERVER\Data           	
		\\I3-SERVER\Videos         	
		\\I3-SERVER\print$         	Printer Drivers
		\\I3-SERVER\IPC$           	IPC Service (i3-Server server (Samba, Ubuntu))

---

### Post by bab1 on 2016-01-08
> **HDTimeshifter said:**
> ```
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.1 ( 192.168.1.1 )
Connecting to 192.168.1.1 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.1 ( 192.168.1.1 )
Connecting to 192.168.1.1 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\SERVER         		Server server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name SERVER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name SERVER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SERVER<0x20>
resolve_hosts: getaddrinfo failed for name SERVER [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name SERVER<0x20>
Got a positive name query response from 192.168.1.11 ( 192.168.1.11 )
Connecting to 192.168.1.11 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\SERVER\Pictures       	
		\\SERVER\Downloads      	
		\\SERVER\Documents      	
		\\SERVER\Music          	
		\\SERVER\data           	
		\\SERVER\Videos         	
		\\SERVER\IPC$           	IPC Service (Server server (Samba, Ubuntu))
		\\SERVER\print$         	Printer Drivers
	\\READYSHARE     		NETGEAR WNDR3700
resolve_lmhosts: Attempting lmhosts lookup for name READYSHARE<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name READYSHARE<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name READYSHARE<0x20>
resolve_hosts: getaddrinfo failed for name READYSHARE [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name READYSHARE<0x20>
Got a positive name query response from 192.168.1.1 ( 192.168.1.1 )
Connecting to 192.168.1.1 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\READYSHARE\IPC$           	IPC Service (NETGEAR WNDR3700)
	\\I3-SERVER      		i3-Server server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name I3-SERVER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name I3-SERVER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name I3-SERVER<0x20>
[COLOR="#FF0000"]Connecting to 127.0.1.1 at port 445[/COLOR]
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\I3-SERVER\Pictures       	
		\\I3-SERVER\Music          	
		\\I3-SERVER\Downloads      	
		\\I3-SERVER\Documents      	
		\\I3-SERVER\Data           	
		\\I3-SERVER\Videos         	
		\\I3-SERVER\print$         	Printer Drivers
		\\I3-SERVER\IPC$           	IPC Service (i3-Server server (Samba, Ubuntu))
```

This should have been sent using [noparse]```

```[/noparse].  Help me help you.  I'm too tired to want to format anything more.  If I can't read it I won't respond.

This host is only using the loopback address (see the red above (127.0.1.1)).  I believe you said that eth1 was supposed to be configured.  Post the output of ```
ifconfig -a 
```...can you ping the IP address for eth1?

---

### Post by HDTimeshifter on 2016-01-08
> **bab1 said:**
> This should have been sent using [noparse]```

```[/noparse].  Help me help you.  I'm too tired to want to format anything more.  If I can't read it I won't respond.

This host is only using the loopback address (see the red above (127.0.1.1)).  I believe you said that eth1 was supposed to be configured.  Post the output of ```
ifconfig -a 
```...can you ping the IP address for eth1?

Not sure why what the difference using CODE tags as it's all text with carriage returns.

I can ping 192.168.1.13

I'm able to see the shared directories from clients - it just won't let me browse the directories (connect with password).

Here's the ipconfig:
```
eth0      Link encap:Ethernet  HWaddr d0:67:e5:14:82:5d  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d267:e5ff:fe14:825d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41176142 (41.1 MB)  TX bytes:4033594 (4.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:434355 (434.3 KB)  TX bytes:434355 (434.3 KB)

```

---

### Post by bab1 on 2016-01-08
> **HDTimeshifter said:**
> Not sure why what the difference using CODE tags as it's all text with carriage returns.

If you want my help you need to format the fixed width font as it is shown in the terminal using the [noparse]```

```[/noparse] blocks.  It is my preference not yours.
> 

I can ping 192.168.1.13

I'm able to see the shared directories from clients - it just won't let me browse the directories (connect with password).


Then the problem is with the usershare configuration and/or the Linux permissions along the path.   You can see the usershare configuration with this command```
net usershare info --long
```

I assume you already know how to check the Linux permissions on the directory path to the share.

---

### Post by HDTimeshifter on 2016-01-08
> **bab1 said:**
> Then the problem is with the usershare configuration and/or the Linux permissions along the path.   You can see the usershare configuration with this command```
net usershare info --long
```

I assume you already know how to check the Linux permissions on the directory path to the share.

Permissions all look ok.

I Googled "samba local network share" and found this:
[http://ubuntuhandbook.org/index.php/2015/02/share-a-folder-in-ubuntu-14-04/]("http://ubuntuhandbook.org/index.php/2015/02/share-a-folder-in-ubuntu-14-04/")

I had previously done steps 1-3 without allowing others or guest access. So now I did step 4, but note that I had to follow the Software Center Reviews section Ubuntu 14.04 fix instructions just to get the Samba Server Configuration tool to show up in the side bar:
```
Fix For Ubuntu 14.04 .. Make sure Samba is not installed. Then open terminal & type "sudo apt-get install gksu"  (Without The Quotes). 

Then type gksu-properties

In the dialogue that follows set authentication mode to "sudo" and grab mode to "enable"

Now Install Samba everything should be working & it show up on Unity Bar & Search.
```

It was a PITA process, but now it works like it did in 12.04. I guess Samba doesn't support 14.04 very well to have to jump through all these hoops just to get sharing to work correctly with username and password login.

---

### Post by HDTimeshifter on 2016-07-03
I had a total network failure after an update and reboot - the networking icon completely disappeared from the status bar and when I opened the Network in System Settings, it said "The system network services are not compatible with this version" ([http://ubuntuforums.org/showthread.php?t=2329210]("http://ubuntuforums.org/showthread.php?t=2329210")), so I installed 16.04 LTS, but now can't get the above step 4 working. Ubuntu Software Center does not find "system-config-samba" and when I search on "samba", it only finds Smb4K, which I am unable to launch after installing. So now I'm stuck again...

---

### Post by HDTimeshifter on 2016-07-04
Thanks to quick response from Ji M, author of the linked article above:
```
run the command below in terminal (Ctrl+ALt+T) instead to install it:
sudo apt install system-config-samba
```

Also still had a problem getting the Sambu GUI to run (nothing happened after entering my admin password), but this link has a solution that worked:
[http://askubuntu.com/questions/655182/samba-config-gui-doesnt-show-after-entering-password]("http://askubuntu.com/questions/655182/samba-config-gui-doesnt-show-after-entering-password")

```
Run Samba from Terminal.

$ gksu system-config-samba

If returns error message with last line similar to this:

    SystemError: could not open configuration file '/etc/libuser.conf': No such file or directory

Create the missing file:

$ sudo touch /etc/libuser.conf

and run Samba again

$ gksu system-config-samba
```

---

