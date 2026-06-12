---
title: "Samba starts ok than keeps dropping to zero: Ubuntu Server OSX client Iperf 97MBytes"
date: 2017-07-09
forum: Networking &amp; Wireless
---

### Post by manselem on 2017-07-09
Need Help With Samba/Cifs sharing; Great throughput but terrible transfers.
[ATTACH=CONFIG]275926[/ATTACH]

Have MacOSX El Cap client w/ 4790k, samsung evo ssd, 16gb ram
Ubuntu 16.10 w/ i3-4130, 8GB ram, kingston ssd for OS and 4TB 7200 Desktar for Serving the Files
All connected with Intel Pro Gigabit PCI card Server side and onboard Gigabit client side using Cat6 with Linksys 1900ac-wrt doing routing.

Ive checked drives, and cables, working. In fact Ive seen hi transfers as hi as 90MBytes/sec.
Testing w/ iperf3 reveals an average of around 60MBytes which is what I get when it does work. 
Usually sending one large file at a time is fine but when I load a few hundred pictures to transfer is where network speeds will drop within a minute and come all the way to zero.

I have been trying to get this NAS working for about a year, lol and I have recently made some changes for the better. At first I was having terrible time browsing folders client side(osx) but think I found the solution was adding these lines
client signing = disabled
server signing = disabled
vfs objects =  streams_xattr
 on the server side to /etc/samba/smb.conf.
And on the client side I also inputted in terminal:
smbutil statshares -a
signing_required=no

Reading some forums with samba issues Ive seen it could be with issues with my mount points w/ the NAS Desktar, DNS issues(which btw server is static IP, and client is DHCP), Ive also seen mabye changing TCP window size can help w larger transfers containing many small files. Do not know enough about any of this to know for sure.

Other thing to note is I was having terrible time with file permissions and eventually just did a sudo nautilus and enabled the whole Drive to be 777. Ive read that using a mix of nautilus permissions w/ smb permissions can cause trouble. I dont have anything in networkmanager.conf or etc/network/interfaces. The only thing in resolv.conf is 127.0.0.1


Thanks in advance to any tips or pointers. This has been really irritating me. If i transfer a 3gb.iso file on the root directory of the sambashare it used to go at 60MB/s. But the deeply buried directories were taxing the network(i think this was fixed by dealing with the client AFS settings that apple was using to implement SMB. But I have never really been able to send a ton of files at one time without having issues. Lately I only see 20MB/s than drops down to idle and than stops.


here is the entire smb.conf settings
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

client signing = disabled
server signing = disabled

vfs objects =  streams_xattr

## Browsing/Identification ###

# usershare owner only = false

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

#socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536 SO_KEEPALIVE
##tried with and without this line above


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
;   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
  directory mask = 0775

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
```

---

### Post by TheFu on 2017-07-09
Please post the output from **testparm**. Use 'code tags' so things line up and are readable.

Is there a reason you are using samba?  You have 2 Unix systems. NFS is the native network file sharing protocol for Unix systems - it honors normal Unix file permissions and it performs better than CIFS.  Not saying you should change, just throwing out an option.

I'm inclined to think it is a router issue.  You can get a cheap, unmanaged GigE switch for $15, connect both systems to it and the switch to the router and test again. If that works, you've just found the issue.  No other network changes are needed.

Internet ---> Router ---> Switch ---> (2) BOTH computers.

CAT5e cabling is fine. It provides 2x what is necessary for GigE speeds.  Sadly, CAT6 only moves to the next 10Ge stuff over very short distances.  I say this looking at all my CAT6 connected systems, knowing the thicker cables won't help my next network upgrade.

---

### Post by manselem on 2017-07-09
Really appreciate the suggestions..
> **TheFu said:**
> Please post the output from **testparm**. Use 'code tags' so things line up and are readable.

Is there a reason you are using samba?  You have 2 Unix systems. NFS is the native network file sharing protocol for Unix systems - it honors normal Unix file permissions and it performs better than CIFS.  Not saying you should change, just throwing out an option.

I'm inclined to think it is a router issue.  You can get a cheap, unmanaged GigE switch for $15, connect both systems to it and the switch to the router and test again. If that works, you've just found the issue.  No other network changes are needed.

Internet ---> Router ---> Switch ---> (2) BOTH computers.

CAT5e cabling is fine. It provides 2x what is necessary for GigE speeds.  Sadly, CAT6 only moves to the next 10Ge stuff over very short distances.  I say this looking at all my CAT6 connected systems, knowing the thicker cables won't help my next network upgrade.


1) I'm using Samba because i thought that was my only choice for cross platform continuity(OSX client with Ubuntu server plus also want to hook up Windows devices to it in future)
    According to this [article]("https://www.helios.de/web/EN/news/AFP_vs_SMB-NFS.html") and other sources it doesnt work that way...but after taking your word I researched some more and found this [article]("http://blog.fosketts.net/2015/03/20/using-nfs-to-share-data-between-unix-and-mac-os-x/") that says its possible. I may try giving this a try if it works better....hmmmm

2) I dont think its the router, but for testing purposes I hooked up my [trendnet(TEG-s5) ]("https://www.amazon.com/gp/product/B002HH0W5W/ref=oh_aui_search_detailpage?ie=UTF8&psc=1")10gb switch but unfortunately encountered the same issue.
[ATTACH=CONFIG]275932[/ATTACH]
 Although iperf reported a little more consistent throughput althrough what I find interesting is that the first interval transfer always was around 80% throughput testing with the router but only about 30% throughput with the switch....

[ATTACH=CONFIG]275931[/ATTACH]
3) As far as the cat6 it had better supply/choices/price on amazon plus I have plans on buying some 10g pcie cards and its short enough distances for it be ok.

TESTPARM output:
```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions

# Global parameters
[global]
    server string = %h server (Samba, Ubuntu)
    log file = /var/log/samba/log.%m
    max log size = 1000
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    usershare allow guests = Yes
    client signing = No
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server signing = No
    unix password sync = Yes
    dns proxy = No
    idmap config * : backend = tdb
    create mask = 0775
    directory mask = 0775
    read only = No
    vfs objects = streams_xattr


[printers]
    comment = All Printers
    path = /var/spool/samba
    browseable = No
    printable = Yes
    create mask = 0700
    read only = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    read only = Yes


```

---

### Post by TheFu on 2017-07-09
Which system did you run testparm on?  It isn't showing **any** samba/cifs shares listed, so I suspect a setup method of which I'm not familiar was used.
If you add a stanza like this to the end of the /etc/samba/smb.conf :
```
[homes]
  comment = Home Directories
  hosts allow = 127.0.0.1 172.22.22.0/24 
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S
```
Then you'll have access to your HOME directory, based on the login credentials.  The [homes] section is special in Samba. In other share stanzas.  A few other things need to be handled.  
1) fix the "*hosts allow*" line for your subnet. This protects against accidental internet incursions.
2) use the **smbpasswd** program to set the userid and password for any Samba users.
3) after any change to the config file, restarting samba on the samba server is required.
**sudo service samba  restart**

For other shared locations, you'd need a 
```
[Data]
   path = /raid/media

``` line.  The "Data" is just what the share name will look like over the network. Other lines as shown above are still needed. 

There are some guidelines that I follow for what should be shared via Samba.  
* Don't share directories mounted under any HOME directories, except through the [homes] stanza.  
* Only share permanently mounted storage, not temporary mounts.
* Only share Linux file systems, never NTFS or FAT-whatever.
* Be careful using non-ASCII characters in any filenames or directories. Not all client machines can handle the same characters.  I also avoid spaces and punctuation in directory and file names.

BTW, "browseable" is spelled correctly for Samba.

Could the issue be a permissions problem?  Using almost any GUI program with sudo is a common way to introduce permission problems.  Just guessing, since something is clearly working.  But if root owns any directories then there will likely be issues.

NFS is a huge hassle from Windows. It can be done, but it is non-trivial and I've not succeeded without using commercial NFS clients. That was over 15 yrs ago.

Well, that's probably enough for now.

---

### Post by Morbius1 on 2017-07-09
Before you create a [homes] share you might want to post the output of this command just in case this "server" has a DE and you created the share in Nautilus:
```
net usershare info --long
```

---

### Post by manselem on 2017-07-09
> **Morbius1 said:**
> Before you create a [homes] share you might want to post the output of this command just in case this "server" has a DE and you created the share in Nautilus:
```
net usershare info --long
```

I did use Nautilus to set up permissions on the sambashare because I was having difficulty with the smb.conf file. Since than I think the smb.conf might have been deleting giving me these troubles im having.... In hindsight I probably should have just came to the forums first...

```
info_fn: file /var/lib/samba/usershares/baracuda backup is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[Documents]
path=/home/mansel/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y


[Downloads]
path=/home/mansel/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=n

[Shared]
path=/Shared
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Picture Backup]
path=/Shared/Picture Backup
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/wd backup is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/linuxbackupdrive is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[heather phone backup]
path=/Shared/heather phone backup
comment=
usershare_acl=Everyone:F,
guest_ok=y

[HandM_Cloud]
path=/home/mansel/HandM_Cloud
comment=
usershare_acl=Everyone:F,
guest_ok=y



```

---

### Post by manselem on 2017-07-09
> **TheFu said:**
> Which system did you run testparm on?  It isn't showing **any** samba/cifs shares listed, so I suspect a setup method of which I'm not familiar was used.
If you add a stanza like this to the end of the /etc/samba/smb.conf :


I ran testparm on Ubuntu server. I think I accidentally deleted the contents in the smb.conf because i wanted nautilus to handle the permissions. I should have came to forums first before I tried such a thing. I just need to set this up again all over maybe using NFS if that method is better.....

> **TheFu said:**
> 
For other shared locations, you'd need a 
```
[Data]
   path = /raid/media

``` line.  The "Data" is just what the share name will look like over the network. Other lines as shown above are still needed. 

So the samba share im assuming is by default mounted to the main OS drive(in my case ssd) and so you have to add any other paths/Drives(in my case 4tb Deskstar) with this code? I would like to share the entire drive to users.
I'll try implementing your stanza lines and see what happens and report back.

---

### Post by manselem on 2017-07-09
> **TheFu said:**
> [CODE]
**sudo service samba  restart**


When I do this i get a failed to restart samba.service: unit samba.service is masked

> **TheFu said:**
> 

Could the issue be a permissions problem?  Using almost any GUI  program with sudo is a common way to introduce permission problems.   Just guessing, since something is clearly working.  But if root owns any  directories then there will likely be issues.

NFS is a huge hassle from Windows. It can be done, but it is non-trivial  and I've not succeeded without using commercial NFS clients. That was  over 15 yrs ago.


Also I mean regardless of how poorly Ive set the file sharing permissions and amateur knowledge on samba server I think its safe to assume the samba share works as well as the network. iperf shows decent speeds 60-80MBytes and is reiterated with Samba if I share 1 large file at a time. Really what bogs it down is when I try to transfer many files at one time. Even so I have had success in the past with larger batch file transfers. However what Ive been working on lately is some files were written as 0 bytes. meaning the name and metadata was there but no real content. So i have to go through and select the correct files(pics) and replace them. When I do this Samba freaks out. In fact the upload speeds on the client go up to 30MBytes/sec and download just drops to 2MBytes to 8MBytes fluctuating bigtime and over time will eventually drop to zero if the batch is large enough. The CPU's are not taxed at all or the ram. The network can handle it. Thats why I think either its some network setting i need to tweak in Samba like the TCP window size or there is some kind of other network anomoly im not aware of bogging down the network but seriously it only happens when i transfer large batches so it has to be a Samba setting issue and by that i dont think permission issue but a network layer protocol...

---

### Post by TheFu on 2017-07-09
In a home environment, I've never needed to tweak samba settings for 65+MBps transfers to work until the disk buffers on the server-side are full. At that point, the speed of the storage device will be the limiting factor.  The only way to change that is to have more RAM for disk buffers.

All my samba use is on a 14.04 machine. I don't have any newer systems running samba - that's the samba.service error you are seeing - you are on a newer OS.  You just need to restart the samba service however that is required on your system to get the config files re-read (and used).

Don't mix methods for sharing via samba.  Either use the GUI and get only GUI help (not from me) or NEVER use the GUI and do it with the smb.conf file - which I've already provided answer for.  Your choice.  GUIs aren't always better, IMHO.  Most GUIs on Linux handle about 20-40% of the situations whereas the config file method handles 100% of the different situations.

---

### Post by manselem on 2017-07-09
> **TheFu said:**
> In a home environment, I've never needed to tweak samba settings for 65+MBps transfers to work until the disk buffers on the server-side are full. At that point, the speed of the storage device will be the limiting factor.  The only way to change that is to have more RAM for disk buffers.

All my samba use is on a 14.04 machine. I don't have any newer systems running samba - that's the samba.service error you are seeing - you are on a newer OS.  You just need to restart the samba service however that is required on your system to get the config files re-read (and used).

Don't mix methods for sharing via samba.  Either use the GUI and get only GUI help (not from me) or NEVER use the GUI and do it with the smb.conf file - which I've already provided answer for.  Your choice.  GUIs aren't always better, IMHO.  Most GUIs on Linux handle about 20-40% of the situations whereas the config file method handles 100% of the different situations.

If you are willing I really would appreciate it going the non GUI route. I have updated the code you gave me though and it didnt work. That is encouraging to hear you dont have issues getting 65+MBps transfers! I would love to see that and judging by iperf i should be as well. It could be because of the mountpoint i suppose but here is my testparm code:
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[Data]"
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE


Press enter to see a dump of your service definitions


# Global parameters
[global]
    server string = %h server (Samba, Ubuntu)
    log file = /var/log/samba/log.%m
    max log size = 1000
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    usershare allow guests = Yes
    client signing = No
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server signing = No
    unix password sync = Yes
    dns proxy = No
    idmap config * : backend = tdb
    vfs objects = streams_xattr




[Data]
    path = /raid/media




[homes]
    comment = Home Directories
    create mask = 0775
    directory mask = 0775
    guest ok = Yes
    hosts allow = 127.0.0.1 192.168.1.1 192.168.1.0/24
    hosts deny = 0.0.0.0/0
    read only = No




[printers]
    comment = All Printers
    path = /var/spool/samba
    browseable = No
    printable = Yes
    create mask = 0700




[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers



```
Update:
Ive tested and tested the directories using different size batches and files and can confirm the culprit is something to do with caching, etc. 1 big file or even a batch of files in a new folder transfer fine around 80MBytes/sec give or take. But what happens over time is the more files that get written to the new directory somehow bogs down the network as its cached almost looking for ACK's the whole time. You can visibly see the files in the folder constantly updating and reshuffling erratically. 

To reiterate the issue: I want to transfer new files to a new folder = fast success[ex. video folder of 25gb of a few files hums @ 115MBytes/sec]
                                 If I transfer a few old files to an established folder = usually works ok[example 20 or less pics under 300mbs does fine]
                                Want to transfer large batch of files to established folder = bad [example a batch of pics totally GBytes.

---

### Post by TheFu on 2017-07-10
For transferring large numbers of files, I would use **rsync** over ssh.  Not CIFS.  rsync is smarter. It only copies newer blocks.  There is a GUI version - grsync, but I've never used it.

If you are watching the xfers using a file manager, the file manage will try to update every few seconds, interrupting the transfers to read the file information on disk.  If the file manager also wants to get extra metadata - like length, codecs, image resolutions, then it will take longer.  All of that interrupts the file transfers even more.  Minimize the file manager - see how fast things go.

I tend to avoid GUI file managers. Personally find them too slow.

---

### Post by manselem on 2017-07-11
> **TheFu said:**
> For transferring large numbers of files, I would use **rsync** over ssh.  Not CIFS.  rsync is smarter. It only copies newer blocks.  There is a GUI version - grsync, but I've never used it.

If you are watching the xfers using a file manager, the file manage will try to update every few seconds, interrupting the transfers to read the file information on disk.  If the file manager also wants to get extra metadata - like length, codecs, image resolutions, then it will take longer.  All of that interrupts the file transfers even more.  Minimize the file manager - see how fast things go.

I tend to avoid GUI file managers. Personally find them too slow.


Yes, I have read about rsync the issue is I dont know how to set it up. I was able to install GRSYNC for Ubuntu but development for OSX stopped at snow leopard(im on el cap). I have tried playing around with the file manager to see if it helps and it doesnt seem to matter if im viewing the page or if i back out or minimize it because OSX will still cache it. I've turned off thumbnail preview which does seem to help. But whats really interesting is CIFS is all over SSH???? rsync is not? Isnt there a way to use CIFS and disable SSH on a local network? I didnt realize this. This explains why any kind of permission issues will slow it down majorly. And I still am having permission issues. Ive noticed /Shared Volume is only mounted on the Samba network but shouldnt it be mounted as a secondary hard drive on boot?
cat etc/fstab 
```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=d4b91cd3-9a54-4108-be5e-a24625a3c5ee /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=E0C2-4F8E  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=95976ead-fd52-470a-b4c8-38e9fd9403a0 none            swap    sw              0       0
UUID=e40e1b14-9503-4d95-a2a9-d1f3267e369c /Shared ext4 defaults 0 0



```


Update: I was able to finally mount my /Shared folder. I dont know how to do this via command line but I when i opened disks i hit the gear icon for additional options, edit mount options, selected show in user interface. So Im thinking this would be the proper syntax for smb.conf to access the drive, correct?:
	```
path = /media/Shared


```

---

### Post by TheFu on 2017-07-11
TL;DR

rsync - install on both systems.
Make sure ssh is working. Key-based is nice.

$ rsync -avz {path-to-source-files}  {path-to-target-directory}

Typical {path-stuff} and be local mounted storage or remote using stuff like this:

rsync -avz /etc  /Backups/$HOSTNAME/
or
rsync -avz /etc  back-srv:/Backups/$HOSTNAME/
or
rsync -avz /etc  thefu@back-srv:/Backups/$HOSTNAME/

The source can be remote too.  All traffic is automatically tunneled using ssh for network connections. If you don't setup ssh-keys and have them unlocked, a password prompt will happen.  

You can safely run the same command over and over.  It adds new files and replaces old files with newer versions. It is 1-way - source --> target.

Greatest inventions/discoveries of man:
1) Fire
2) Wheel
3) Unix
4) ssh
5) rsync
6) germ theory / vaccines

Ok, perhaps the order _could_ be debated.  ;)

The point is that Unix, ssh, rsync ARE AMAZING!!!

CIFS is never over ssh, unless you do something crazy-special.
rsync is.

---

