---
title: "Samba Network Share - advice needed"
date: 2016-04-24
forum: Networking &amp; Wireless
---

### Post by vaguely_clear on 2016-04-24
Hello!

I need some advice on setting up a home server with a file share. 

**What I Have Now**
I currently have an Ubuntu 15.10 Desktop machine set up like this:
[LIST]
[*]System installed on small SSD
[*]Large 2 TB hard drive used solely for file storage on local network
[*]Multiple machines on home network, primarily 2 Macs running OS X 10.11
[*]Sharing is enabled on the root level of the 2 TB drive via the check box in Nautilus, but does not seem to be working; it did work at one point
[/LIST]
This machine and the storage drive have been configured with the Nautilus sharing check box, as well as with a custom Samba configuration in the past. It has been both password protected and open to guest access at different times.


**Problems**
I have encountered a number of problems:
[LIST]
[*]My biggest problem at the moment is that the shared folder doesn't seem to be working. It shows up in the network area of my other computers, but I cannot access the network share.
[*]I use the 2 TB storage drive both locally (backing up music and movies on the Ubuntu machine) and remotely (sharing files between machines) which seems to be causing a permissions issue. Some files are locked and only editable from either the local Ubuntu machine or connected desktops. Perhaps this is because at one point there was a specific Samba user configured? Maybe locally created content was owned by the local user and content created on the share remotely was owned by the Samba user? Not sure.
[/LIST]

[B]What I Need
[/B]
[LIST]
[*]A folder on this machine that is accessible, both read and write, by the local machine and machines connected on the local network. Password protected would be nice, but it's not essential. There are only two of us in the house and there is mutual trust.
[*]The ability to continue also using this machine as a desktop linux computer, as I use it to backup CDs and DVDs, as well as for other Desktop Linux applications as needed.
[/LIST]
I will be reinstalling with Ubuntu 16.04 LTS, most likely mid May. I cannot for the life of me find a clear guide for setting up this type of share, at least not one that addresses my use case. How should I go about this? Should I consider something radically different? Open to any ideas.

---

### Post by bab1 on 2016-04-25
> **vaguely_clear said:**
> Hello!

I need some advice on setting up a home server with a file share. 

**What I Have Now**
I currently have an Ubuntu 15.10 Desktop machine set up like this:
[LIST]
[*]Large 2 TB hard drive used solely for file storage on local network
[*]Multiple machines on home network, primarily 2 Macs running OS X 10.11
[*]Sharing is enabled on the root level of the 2 TB drive via the check box in Nautilus, but does not seem to be working; it did work at one point
[/LIST]

How is this 2TB HDD attached?  USB or SATA?
You should account for all machine types on the network.  Will there any Windows machines accessing the shared data?
How is the 2TB partition mounted in the local machine's file system; via fstab or ?  What is the mountpoint in the file system?   
>  
This machine and the storage drive have been configured with the Nautilus sharing check box, as well as with a custom Samba configuration in the past. It has been both password protected and open to guest access at different times.

Most likely this will not work for what you want to do.  You will probably you will have to configure the file sharing manually via configuration files for the protocol you use. 
> 
**Problems**
I have encountered a number of problems:
[LIST]
[*]My biggest problem at the moment is that the shared folder doesn't seem to be working. It shows up in the network area of my other computers, but I cannot access the network share.
[*]I use the 2 TB storage drive both locally (backing up music and movies on the Ubuntu machine) and remotely (sharing files between machines) which seems to be causing a permissions issue. Some files are locked and only editable from either the local Ubuntu machine or connected desktops. Perhaps this is because at one point there was a specific Samba user configured? Maybe locally created content was owned by the local user and content created on the share remotely was owned by the Samba user? Not sure.
[/LIST]

This is easily addressed.  What you are attempting to do is create network attached storage (NAS).  This means that any user that needs access to the NAS needs to be a local user on the NAS. 
> 

[B]What I Need
[/B]
[LIST]
[*]A folder on this machine that is accessible, both read and write, by the local machine and machines connected on the local network. Password protected would be nice, but it's not essential. There are only two of us in the house and there is mutual trust.
[*]The ability to continue also using this machine as a desktop linux computer, as I use it to backup CDs and DVDs, as well as for other Desktop Linux applications as needed.
[/LIST]
I will be reinstalling with Ubuntu 16.04 LTS, most likely mid May. I cannot for the life of me find a clear guide for setting up this type of share, at least not one that addresses my use case. How should I go about this? Should I consider something radically different? Open to any ideas.
There are 2 NAS protocols available if you are only using MAC and Ubuntu.  If there are Windows machines that need access then only 1 of those protocols can be used.  With Windows machines you must use SMB/CIFS (Samba (Windows Sharing).  This is what Nautilus uses when it sets up sharing.  Their configuration is not very precise and it does not really work for multiple users accessing the same data.   Samba can be configured to do this, but you have to do it via the Samba server config file (/etc/samba/smb.conf

If you only have MAC and Ubuntu then you can use Samba (SMB/CIFS) or you can use Network File System (NFS).  The configuration of the users must be consistent across the network (the users UID and GID must match on all machines).  The security is by user id only.  Traditionally these are called NFS exports.

To summarize; you setup the users that will have access, then create the data store on NAS file system and then share (or export) the directory or directories.

There are a million variations to this so there is no howto that will fit each and every situation.  If you want to post replies to the questions I asked, I will advise you on how to accomplish your goal.

---

### Post by vaguely_clear on 2016-04-25
Thank you so much for your thorough response!

> **bab1 said:**
> How is this 2TB HDD attached?  USB or SATA?
You should account for all machine types on the network.  Will there any Windows machines accessing the shared data?
How is the 2TB partition mounted in the local machine's file system; via fstab or ?  What is the mountpoint in the file system?

I do have a Windows install that I boot into sometimes. Ideally yes, it would be able to access this share as well. If it's apples to oranges, then I suppose Samba will be the way to go.

The 2TB drive is connected internally via SATA. Actually, at the moment it is two 2TB drives set up in a software RAID 1, though I will be disassembling that when I reinstall the server and moving one 2TB drive to another machine. It's all mounted via FSTAB at /media/netdrive.

> **bab1 said:**
> Most likely this will not work for what you want to do.  You will probably you will have to configure the file sharing manually via configuration files for the protocol you use.

No problem. I like easy, but I'm not afraid to edit configuration files if needed.

> **bab1 said:**
> This is easily addressed.  What you are attempting to do is create network attached storage (NAS).  This means that any user that needs access to the NAS needs to be a local user on the NAS.

Will it be best to create one single user (called 'sambauser' or something) for everyone on the local network to connect with, or would it be better to actually create a user on the server for each person who might connect? The former would be easier for me if I could get the permissions issues resolved, but I'm open to whatever will work best.

> **bab1 said:**
> There are 2 NAS protocols available if you are only using MAC and Ubuntu.  If there are Windows machines that need access then only 1 of those protocols can be used.  With Windows machines you must use SMB/CIFS (Samba (Windows Sharing).  This is what Nautilus uses when it sets up sharing.  Their configuration is not very precise and it does not really work for multiple users accessing the same data.   Samba can be configured to do this, but you have to do it via the Samba server config file (/etc/samba/smb.conf

If you only have MAC and Ubuntu then you can use Samba (SMB/CIFS) or you can use Network File System (NFS).  The configuration of the users must be consistent across the network (the users UID and GID must match on all machines).  The security is by user id only.  Traditionally these are called NFS exports.

To summarize; you setup the users that will have access, then create the data store on NAS file system and then share (or export) the directory or directories.

There are a million variations to this so there is no howto that will fit each and every situation.  If you want to post replies to the questions I asked, I will advise you on how to accomplish your goal.

So Samba seems to be the direction I need to go. Perhaps I could try setting this up on my current 15.10 install as a test before installing 16.04. How would I go about thoroughly removing Samba so I can start fresh?

---

### Post by vaguely_clear on 2016-04-25
After some research... would this be sufficient to remove samba + config files and get me back to a starting point?

```
sudo apt-get remove --purge samba
```

Also, I'm curious to know if the graphical Samba config tools such as Samba Server Configuration work reliably and will do what I need. I can handle config files, but I really prefer graphical front ends when possible. I'm interested in any experience people might have had with these.

---

### Post by bab1 on 2016-04-25
> **vaguely_clear said:**
> Thank you so much for your thorough response!

I do have a Windows install that I boot into sometimes. Ideally yes, it would be able to access this share as well. If it's apples to oranges, then I suppose Samba will be the way to go.

As Windows can't easily use NFS your only choice is Samba.
> 

The 2TB drive is connected internally via SATA. Actually, at the moment it is two 2TB drives set up in a software RAID 1, though I will be disassembling that when I reinstall the server and moving one 2TB drive to another machine. It's all mounted via FSTAB at /media/netdrive.

The data on the RAID volume should be backed up.  RAID provides no security at all.  When you install 16.04 and break the RAID volume you will need to reformat each 2TB HDD.  Backup, backup, backup all the data all the time.
> 
Will it be best to create one single user (called 'sambauser' or something) for everyone on the local network to connect with, or would it be better to actually create a user on the server for each person who might connect? The former would be easier for me if I could get the permissions issues resolved, but I'm open to whatever will work best.

I create a user for each human that is going to login.  This way I have an audit trail if there is a problem.  It takes so little time to do that I don't even consider the alternative of having a single login for all human users.
> 
So Samba seems to be the direction I need to go. Perhaps I could try setting this up on my current 15.10 install as a test before installing 16.04. How would I go about thoroughly removing Samba so I can start fresh?
There is no need to remove Samba via purge or otherwise.  The whole thing is configured with 1 file, the */etc/samba/smb.conf* file.> 
Also, I'm curious to know if the graphical Samba config tools such as Samba Server Configuration work reliably and will do what I need. I can handle config files, but I really prefer graphical front ends when possible. I'm interested in any experience people might have had with these. 

There are literally only 10 simple text lines in the *smb.conf *file that need adding or altering.  You can do more harm than good using  the GUI tool.  I'd start with editing the smb.conf file with a simple test editor.  The smb.conf file that you have will work as a starting point.

In all you will need to edit 2 files (fstab and smb.conf).  First you mount the partition (fstab).  Then you create the users as both Linux users (adduser) and Samba user (smbpasswd -a).  Next you need to create the data structure that you will be sharing.  Last you will edit the smb.conf file to share the directory that holds all the data.  That's it.

If you are going to reinstall using 16.04 and break up the RAID you will need to use backups of the data.  You will not be able to preserve the data as it is on one of the HDD's.  The samba install will also be gone as you are reinstalling so just make a backup of the smb.conf as a starting point.

---

### Post by vaguely_clear on 2016-04-26
> **bab1 said:**
> The data on the RAID volume should be backed up.  RAID provides no security at all.  When you install 16.04 and break the RAID volume you will need to reformat each 2TB HDD.  Backup, backup, backup all the data all the time.

Yes, the data on this RAID 1 has always been backed up on multiple other locations. The important stuff has been, anyway. It was an experiment that turned out to be unnecessary. I will be duplicating everything on this volume to another location before wiping both drives and starting fresh.

> **bab1 said:**
> I create a user for each human that is going to login.  This way I have an audit trail if there is a problem.  It takes so little time to do that I don't even consider the alternative of having a single login for all human users.
There is no need to remove Samba via purge or otherwise.  The whole thing is configured with 1 file, the */etc/samba/smb.conf* file.
There are literally only 10 simple text lines in the *smb.conf *file that need adding or altering.  You can do more harm than good using  the GUI tool.  I'd start with editing the smb.conf file with a simple test editor.  The smb.conf file that you have will work as a starting point.

In all you will need to edit 2 files (fstab and smb.conf).  First you mount the partition (fstab).  Then you create the users as both Linux users (adduser) and Samba user (smbpasswd -a).  Next you need to create the data structure that you will be sharing.  Last you will edit the smb.conf file to share the directory that holds all the data.  That's it.

Got it, I think I can handle all that. I will try this on 15.10 tomorrow if I have a chance. Should I do anything to clean up the existing permissions problems on the netdrive volume?

> **bab1 said:**
> If you are going to reinstall using 16.04 and break up the RAID you will need to use backups of the data.  You will not be able to preserve the data as it is on one of the HDD's.  The samba install will also be gone as you are reinstalling so just make a backup of the smb.conf as a starting point.

10-4. I'll make sure everything is backed up before starting over with 16.04. Your help is greatly appreciated!

---

### Post by bab1 on 2016-04-26
> **vaguely_clear said:**
> Yes, the data on this RAID 1 has always been backed up on multiple other locations. The important stuff has been, anyway. It was an experiment that turned out to be unnecessary. I will be duplicating everything on this volume to another location before wiping both drives and starting fresh.

Good.  Rather than restating all of the steps you can see them [here]("http://ubuntuforums.org/showthread.php?t=2313205") (from post #4 on).  Ask questions **before **you start if you don't understand.
> 
.I will try this on 15.10 tomorrow if I have a chance. Should I do anything to clean up the existing permissions problems on the netdrive volume?
Not just yet.  That can be done with a few simple terminal commands later on.

I won't be able to answer until tomorrow afternoon so take your time.

---

### Post by vaguely_clear on 2016-04-26
> **bab1 said:**
> Good.  Rather than restating all of the steps you can see them [here]("http://ubuntuforums.org/showthread.php?t=2313205") (from post #4 on).  Ask questions **before **you start if you don't understand.

I do have a question about this. With only two users and no real need for each to have private home directories on the share, how should I go about setting up groups? That is, do I need any new groups and what should I call them?

Also, the only user account on the server machine currently is in my name. Can I go ahead and use that for me, or should I make a new user account for accessing the share?

---

### Post by bab1 on 2016-04-26
> **vaguely_clear said:**
> I do have a question about this. With only two users and no real need for each to have private home directories on the share, how should I go about setting up groups? That is, do I need any new groups and what should I call them?

By default there is a user-group named ***users ***that you can add both you and the other user to that account .  I would have a user account for each user.
> 

Also, the only user account on the server machine currently is in my name. Can I go ahead and use that for me, or should I make a new user account for accessing the share?
Your existing account is fine.  Just create another account for the other user.

---

### Post by vaguely_clear on 2016-04-26
Okay, on the 15.10 server this evening, I have:
[LIST]
[*]Removed the old "smbuser" user account, both from the system and from smbpasswd
[*]Added a user for the other human
[*]Added both human users to smbpasswd
[*]Run ```
sudo pdbedit -L -v
``` to ensure that both users are there
[*]Opened /etc/samba/smb.conf to see if I could get things going
[*]Run ```
sudo service smbd restart
``` after making a few changes
[/LIST]

I added a section at the bottom of smb.conf for my share like this:

```
[netdrive]
path = /media/netdrive
valid users = user1, user2
read only = no
```

I don't know if this is at all correct, just following what I could find via some research.

Here are some other lines that looked important from my smb.conf:

```
workgroup = Workgroup
security = user
hosts allow = 127. 192.168.0.
interfaces = 127.0.0.1/8 192.168.0.0/24
```

I'm wondering about the hosts and interfaces lines. My local network is on an Apple Airport Extreme router which uses network addresses in the range of 10.0.1.1 and up (my server is 10.0.1.12, for example). Do these lines need to be changed to reflect that?

What else should I look at changing in smb.conf?

Currently the share does not seem to work from OS X 10.11. The server shows up under network, but when I try to connect it says "The server may not exist or it is unavailable at this time. Check the server name or IP address, check your network connection, and then try again." I don't get the option to put in a username or password.

Also, I haven't set up any groups. Not sure what, if anything, I need to do there.

I'd be happy to post the entire contents of smb.conf if that would be helpful.

---

### Post by vaguely_clear on 2016-04-26
> **vaguely_clear said:**
> Also, I haven't set up any groups. Not sure what, if anything, I need to do there.

Oh, just kidding. I remembered your suggestion about the user-group ***users*** right after posting:

> **bab1 said:**
> By default there is a user-group named ***users ***that you can add both you and the other user to that account .

Both user accounts have now been successfully added to the group users per the instructions you linked to previously.

---

### Post by bab1 on 2016-04-26
Post the entire smb.conf file and I will compare it with a known good copy.  Then we can continue.

---

### Post by vaguely_clear on 2016-04-26
Sure, here is my /etc/samba/smb.conf:

```
[global]
netbios name = netdrive
server string = Samba file server
workgroup = Workgroup
security = user
hosts allow = 127. 192.168.0.
interfaces = 127.0.0.1/8 192.168.0.0/24
bind interfaces only = yes
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
printcap name = cups
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 6
password level = 6
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = no
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
passdb backend = tdbsam
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no


[homes]
comment = Home Directories
path = /home
valid users = %U
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
locking = no
strict locking = no


[netlogon]
comment = Network Logon Service
path = /var/lib/samba/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
strict locking = no


[profiles]
comment = User Profiles
path = /var/lib/samba/profiles
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
create mode = 0600
directory mask = 0700
locking = no
strict locking = no


[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
locking = no
strict locking = no


[pdf-documents]
path = /var/lib/samba/pdf-documents
comment = Converted PDF Documents
admin users = %U
available = yes
browseable = yes
writeable = yes
guest ok = yes
locking = no
strict locking = no


[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gadmin-samba-pdf %s %u
lpq command =
lprm command =


[netdrive]
path = /media/netdrive
valid users = ian, emily
read only = no



```

---

### Post by bab1 on 2016-04-27
There are many things that are either wrong or outdated with the smb.conf file you supplied.  For example these warnings are a result of testing your smb.conf file```
WARNING: socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
This warning is printed because you set one of the
following options: SO_SNDBUF, SO_RCVBUF, SO_SNDLOWAT,
SO_RCVLOWAT
Modern server operating systems are tuned for
high network performance in the majority of situations;
when you set 'socket options' you are overriding those
settings.
Linux in particular has an auto-tuning mechanism for
buffer sizes (SO_SNDBUF, SO_RCVBUF) that will be
disabled[I][COLOR="#FF0000"][B] if you specify a socket buffer size. This can
potentially cripple your TCP/IP stack.[/B][/COLOR][/I]

Getting the 'socket options' correct can make a big
difference to your performance, but getting them wrong
can degrade it by just as much. As with any other low
level setting, if you must make changes to it, make
 small changes and test the effect before making any
large changes.

WARNING: **[COLOR="#800080"]You have some share names that are longer than 12 characters.[/COLOR]**
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE

```
There is no need to make the changes that it appears GADMIN-SAMBA has made.  

Also, as a rule of thumb no names should be longer than 12 characters.  That will keep both Samba and Windows from choking on longer names.

My suggestion is that you use the default vanilla *smb.conf*.  I will supply that as a .txt attachment.  I'd just make the minimal edits I suggest and add a single share definition at the very bottom of the new smb.conf file.

I would add these [global] parameters```

# Declare NetBIOS name
        netbios name = NETDRIVE
# Set name resolve order
        name resolve order = bcast

```

Let's just add this share definition```

[netdrive]
path = /media/netdrive
        valid users = @users    [COLOR="#FF0000"]# you can use the users group rather than the individual users [/COLOR]
        browseable = yes        [COLOR="#FF0000"]# make this share visible when browsing the network shares[/COLOR]
        force group = users     [COLOR="#FF0000"]# forces the users group on any file operations[/COLOR]
        writeable = yes
        create mask = 0664      [COLOR="#FF0000"]# sets the file permissions on new files[/COLOR]
        directory mask = 2775    [COLOR="#FF0000"]# sets the directory permissions and sgid bit on new directories[/COLOR]

```
Remember that we need to setup the permissions on this directory and the partition needs to be mounted before this will work.
I have annotated the parameters in red.  You do not add the red to the share definition.

---

### Post by vaguely_clear on 2016-04-27
> **bab1 said:**
> There is no need to make the changes that it appears GADMIN-SAMBA has made.

Wow, no kidding, it must have really messed things up. I have heard elsewhere that the GUI utilities for Samba are not great. Now I know for sure I guess.

Here is my current smb.conf based on your vanilla text file and suggested modifications:

```
## Sample configuration file for the Samba suite for Debian GNU/Linux.
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


# Declare NetBIOS name
        netbios name = NETDRIVE
        
# Set name resolve order
        name resolve order = bcast


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
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[netdrive]
path = /media/netdrive
        valid users = @users
        browseable = yes
        force group = users
        writeable = yes
        create mask = 0664
        directory mask = 2775
```

And here is the output from testparm:

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[netdrive]"
Loaded services file OK.
Server role: ROLE_STANDALONE


Press enter to see a dump of your service definitions


# Global parameters
[global]
    netbios name = NETDRIVE
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = bcast
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb




[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No




[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers




[netdrive]
    path = /media/netdrive
    valid users = @users
    force group = users
    group = users
    read only = No
    create mask = 0664
    directory mask = 02775
    directory mode = 02775
```

After restarting Samba, the network entry that was previously visible on my other machines (the one that threw an error) is no longer visible. What's next?

---

### Post by bab1 on 2016-04-27
> **vaguely_clear said:**
> 
After restarting Samba, the network entry that was previously visible on my other machines (the one that threw an error) is no longer visible. What's next?
What OS is the client that you are using?  I don't know what client tools are available to test.  I haven't had problems with Windows clients, but I hear that there is a nasty bug in Samba v4.3.8 in the current Ubuntu packages.  I have zip experience thei OSX  Samba clients.  On the other hand we may have a simple problem with the server.

We can debug that pretty quicly.   Let's start with you posting the output of these commands from The Ubuntu command line```

ifconfig -a

smbtree -d3

```

---

### Post by vaguely_clear on 2016-04-27
> **bab1 said:**
> What OS is the client that you are using?  I don't know what client tools are available to test.  I haven't had problems with Windows clients, but I hear that there is a nasty bug in Samba v4.3.8 in the current Ubuntu packages.  I have zip experience thei OSX  Samba clients.

Hmm... okay, interesting development: I tried connecting via Go > Connect to Server in Finder, which allows me to specify the address (smb://10.0.1.12). This accepted my credentials and mounted the share just fine. So I guess the Samba share is working on the server! It's more likely an issue with OS X. All the Macs in the house are running OS X 10.11 El Capitan, but I cannot figure out what version of Samba they are running.

Actually, now that I'm thinking about it, I believe there are a few Linux packages related to broadcasting network shares to Macs on a local network, like netatalk, maybe. That may be the ticket.

> **bab1 said:**
> On the other hand we may have a simple problem with the server.

WE can debug that pretty quicly.   Let's start with you posting the output of these commands from The Ubuntu command line

Here's the output of ifconfig -a:

```
 enp0s25   Link encap:Ethernet  HWaddr 00:15:58:b9:a3:1c            inet addr:10.0.1.12  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:feb9:a31c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3432163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3303672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1971140152 (1.9 GB)  TX bytes:2663905760 (2.6 GB)
          Interrupt:20 Memory:effc0000-effe0000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:436982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:436982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84907380 (84.9 MB)  TX bytes:84907380 (84.9 MB)

```

Does the name of that first network interface look okay? It looks strange to me. I was expecting something like en0.

smbtree was not installed, but I was prompted to install smbclient which worked. Here is the output of smbtree -d3:

```
lp_load_ex: refreshing parametersInitialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface enp0s25 ip=10.0.1.12 bcast=10.0.1.255 netmask=255.255.255.0
Enter ian's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
```

Just in case those are still helpful.

---

### Post by vaguely_clear on 2016-04-27
> **vaguely_clear said:**
> Actually, now that I'm thinking about it, I believe there are a few Linux packages related to broadcasting network shares to Macs on a local network, like netatalk, maybe. That may be the ticket.

Scratch that, avahi is what I was thinking of and avahi-daemon appears to be installed already. Netatalk is for implementing AFP which I definitely don't want to do.

---

### Post by bab1 on 2016-04-27
> **vaguely_clear said:**
> Hmm... okay, interesting development: I tried connecting via Go > Connect to Server in Finder, which allows me to specify the address (smb://10.0.1.12). This accepted my credentials and mounted the share just fine. So I guess the Samba share is working on the server!

The file server is working.  Only the browsing service is not.
> 
 It's more likely an issue with OS X. All the Macs in the house are running OS X 10.11 El Capitan, but I cannot figure out what version of Samba they are running.

Actually, now that I'm thinking about it, I believe there are a few Linux packages related to broadcasting network shares to Macs on a local network, like netatalk, maybe. That may be the ticket.

Nope.  The browsing is a Samba thing not a nettalk or any other protocol.
> 



Here's the output of ifconfig -a:

```
 enp0s25   Link encap:Ethernet  HWaddr 00:15:58:b9:a3:1c            inet addr:10.0.1.12  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:feb9:a31c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3432163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3303672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1971140152 (1.9 GB)  TX bytes:2663905760 (2.6 GB)
          Interrupt:20 Memory:effc0000-effe0000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:436982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:436982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84907380 (84.9 MB)  TX bytes:84907380 (84.9 MB)

```

Does the name of that first network interface look okay? It looks strange to me. I was expecting something like en0.

Not okay but kind of expected.  It is the new (and much hated) "simple naming" system.  The traditional name is eth0.  Samba is smart enough to understand and use the name enp0s25.  

> 

smbtree was not installed, but I was prompted to install smbclient which worked. Here is the output of smbtree -d3:

```
lp_load_ex: refreshing parametersInitialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface [COLOR="#FF0000"]enp0s25[/COLOR] ip=10.0.1.12 bcast=10.0.1.255 netmask=255.255.255.0
Enter ian's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
```

Just in case those are still helpful.
There should have been more of this.  Can you run ***smbtree -d3*** again?

Edit:  Note that Samba sees the interface (see red).

---

### Post by vaguely_clear on 2016-04-27
> **bab1 said:**
> The file server is working.  Only the browsing service is not.

Nope.  The browsing is a Samba thing not a nettalk or any other protocol.

No okay but kind of expected.  It is the new (and much hated) "simple naming" system.  The traditional name is eth0.  Samba is smart enough to understand and use the name enp0s25.  


There should have been more of this.  Can you run ***smbtree -d3*** again?

Edit:  Note that Samba sees the interface (see red).

Interesting. I'm learning a lot today.

I ran smbtree -d3 again and got the exact same results. I saw the "Permission denied" line and tried sudo smbtree -d3. Results were the same but without the permission denied line. In both cases, it drops back to a prompt when it finishes the third "Attempting broadcast" line.

---

### Post by bab1 on 2016-04-27
> **vaguely_clear said:**
> 
I ran smbtree -d3 again and got the exact same results. I saw the "Permission denied" line and tried sudo smbtree -d3. Results were the same but without the permission denied line. In both cases, it drops back to a prompt when it finishes the third "Attempting broadcast" line.
That's not good, or anything I have seen that I can remember.

I wonder what else is not installed.  Post the output of this```
dpkg -l cifs-utils
```

And let's see what we get from this also```
smbclient -d3 -L netdrive
```

---

### Post by vaguely_clear on 2016-04-27
> **bab1 said:**
> That's not good, or anything I have seen that I can remember.

I should note that the _MSBROWSE_ bit appears to have some strange characters that did not make it over via copy and paste. I have attached a screenshot.

> **bab1 said:**
> I wonder what else is not installed.  Post the output of this```
dpkg -l cifs-utils
```

```
Desired=Unknown/Install/Remove/Purge/Hold| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name             Version       Architecture  Description
+++-================-=============-=============-=====================================
un  cifs-utils       <none>        <none>        (no description available)
```

> **bab1 said:**
> And let's see what we get from this also```
smbclient -d3 -L netdrive
```

```
lp_load_ex: refreshing parametersInitialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface enp0s25 ip=10.0.1.12 bcast=10.0.1.255 netmask=255.255.255.0
Client started (version 4.3.8-Ubuntu).
Enter ian's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name netdrive<0x20>
Connection to netdrive failed (Error NT_STATUS_UNSUCCESSFUL)
```

---

### Post by bab1 on 2016-04-27
> **vaguely_clear said:**
> I should note that the _MSBROWSE_ bit appears to have some strange characters that did not make it over via copy and paste. I have attached a screenshot.

Thanks.  I know what _MSBROWSE_ is sanyway.  ;-)
> 
```
Desired=Unknown/Install/Remove/Purge/Hold| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name             Version       Architecture  Description
+++-================-=============-=============-=====================================
[COLOR="#FF0000"]un[/COLOR]  cifs-utils       <none>        <none>        (no description available)
```
[QUOTE]
THE un (in red) means this is not installed.  Let's install that and one other package with this command```
sudo apt-get install cifs-utils samba-common 
```


```
lp_load_ex: refreshing parametersInitialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface enp0s25 ip=10.0.1.12 bcast=10.0.1.255 netmask=255.255.255.0
Client started (version 4.3.8-Ubuntu).
Enter ian's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name netdrive<0x20>
Connection to netdrive failed (Error NT_STATUS_UNSUCCESSFUL)
```[/QUOTE]
Not locating the name netdrive.  Let's revisit this after installing the cifs-utils.

---

### Post by vaguely_clear on 2016-04-27
The install seemed to work. The new output for [COLOR=#000000][FONT=Ubuntu Mono]dpkg -l cifs-utils:

[/FONT][/COLOR]```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name             Version       Architecture  Description
+++-================-=============-=============-=====================================
ii  cifs-utils       2:6.4-1ubuntu amd64         Common Internet File System utilities

```

Output for smbtree -d3 and smbclient -d3 -L netdrive do not appear to be different than before, but I can paste them if needed.

---

### Post by bab1 on 2016-04-27
What do you get from this```
smbclient -d3 -L 10.0.1.12
```

---

### Post by vaguely_clear on 2016-04-27
> **bab1 said:**
> What do you get from this```
smbclient -d3 -L 10.0.1.12
```

```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface enp0s25 ip=10.0.1.12 bcast=10.0.1.255 netmask=255.255.255.0
Client started (version 4.3.8-Ubuntu).
Enter ian's password: 
Connecting to 10.0.1.12 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'spnego' registered
GENSEC backend 'schannel' registered
GENSEC backend 'naclrpc_as_system' registered
GENSEC backend 'sasl-EXTERNAL' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'ntlmssp_resume_ccache' registered
GENSEC backend 'http_basic' registered
GENSEC backend 'http_ntlm' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.8-Ubuntu]


    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    netdrive        Disk      
    IPC$            IPC       IPC Service (ian-UbuntuServer server (Samba, Ubuntu))
Connecting to 10.0.1.12 at port 139
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.8-Ubuntu]


    Server               Comment
    ---------            -------
    BRN30055C2B32F8      
    IAN-UBUNTUSERVE      ian-UbuntuServer server (Samba, Ubuntu)


    Workgroup            Master
    ---------            -------
    WORKGROUP      

```

---

### Post by bab1 on 2016-04-28
You can see by this last output that the naming services are not working properly.  This what you should get when you use the NETBIOS name.  On the other hand the nmbd (Samba) naming precess should be disabled as you have explicitly provided the NETBIOS name with ```
netbios name = netdrive
```

So, from a pragmatic point of view I think you should just purge this install of Samba.  GADMIN-SAMBA has profoundly screwed up this install.  This isn't the first time this has happened.  When kind of thing happens it's  just easier to purge the whole thing and start over.  I would not want to spend the time messing with it.

We can leave the thread open and continue after you reinstall Samba, smbclient, samba-common and cifs-utils.  I'd use the new default smb.conf file and add the 2 netbios and resolve lines in the [global] section and the share definition at the bottom.

What say you?

[COLOR="#0000FF"]Edit:  DO NOT USE TASKSEL TO INSTALL SAMBA.  Use apt-get itself.  I think part of the problem is that this install of Samba has been provisioned for Active Directory - Domain Controller (AD-DC).  You do not want that for a standalone Samba file server. [/COLOR]

---

### Post by vaguely_clear on 2016-04-28
> **bab1 said:**
> You can see by this last output that the naming services are not working properly.  This what you should get when you use the NETBIOS name.  On the other hand the nmbd (Samba) naming precess should be disabled as you have explicitly provided the NETBIOS name with ```
netbios name = netdrive
```

So, from a pragmatic point of view I think you should just purge this install of Samba.  GADMIN-SAMBA has profoundly screwed up this install.  This isn't the first time this has happened.  When kind of thing happens it's  just easier to purge the whole thing and start over.  I would not want to spend the time messing with it.

We can leave the thread open and continue after you reinstall Samba, smbclient, samba-common and cifs-utils.  I'd use the new default smb.conf file and add the 2 netbios and resolve lines in the [global] section and the share definition at the bottom.

What say you?

[COLOR=#0000FF]Edit:  DO NOT USE TASKSEL TO INSTALL SAMBA.  Use apt-get itself.  I think part of the problem is that this install of Samba has been provisioned for Active Directory - Domain Controller (AD-DC).  You do not want that for a standalone Samba file server. [/COLOR]

I say that sounds like a good plan. Thanks so much for your guidance. I will have to give this a try tomorrow evening and report back. Should I use this to do the purge?

```
sudo apt-get remove --purge samba
```

---

### Post by bab1 on 2016-04-28
> **vaguely_clear said:**
> I say that sounds like a good plan. Thanks so much for your guidance. I will have to give this a try tomorrow evening and report back. Should I use this to do the purge?

```
sudo apt-get remove --purge samba
```

Yes.  I'd like to see what is in these directories after you reinstall but before we start to reconfigure (using ls -l to list)```

ls -l /etc/samba

ls -l /var/lib/samba

```

---

### Post by vaguely_clear on 2016-04-29
> **bab1 said:**
> Yes.  I'd like to see what is in these directories after you reinstall but before we start to reconfigure (using ls -l to list)```

ls -l /etc/samba

ls -l /var/lib/samba

```

Here are the results from both after purging but before reinstalling, just in case that's relevant:

```
ian@ian-UbuntuServer:~$ ls -l /etc/samba
total 40
-rw-r--r-- 1 root root     8 Aug 10  2015 gdbcommands
-rw-r--r-- 1 root root 12787 Apr 27 15:31 smb.conf
-rw-r--r-- 1 root root  9542 Apr 21 21:35 smb.conf.old.gadmin-samba-0.3.2
-rw-r--r-- 1 root root    91 Apr 21 21:35 smbusers
drwxr-xr-x 2 root root  4096 Aug 10  2015 tls
ian@ian-UbuntuServer:~$ ls -l /var/lib/samba
total 1364
-rw------- 1 root root       421888 Oct 30 21:53 account_policy.tdb
-rw------- 1 root root          696 Oct 30 21:53 group_mapping.tdb
drwxr-xr-x 2 root root         4096 Apr 21 21:36 netlogon
drwxr-xr-x 3 root root         4096 Apr 19 16:24 private
drwxr-xr-t 3 root root         4096 Apr 21 21:36 profiles
-rw------- 1 root root       528384 Apr 24 10:15 registry.tdb
drwxr-xr-x 2 root root         4096 Apr 21 21:36 root
-rw------- 1 root root       421888 Oct 31 10:59 share_info.tdb
drwxrwx--T 2 root sambashare   4096 Apr 21 21:25 usershares

```

And here are the results of both after reinstalling:

```
ian@ian-UbuntuServer:~$ ls -l /etc/samba
total 40
-rw-r--r-- 1 root root     8 Aug 10  2015 gdbcommands
-rw-r--r-- 1 root root 12787 Apr 27 15:31 smb.conf
-rw-r--r-- 1 root root  9542 Apr 21 21:35 smb.conf.old.gadmin-samba-0.3.2
-rw-r--r-- 1 root root    91 Apr 21 21:35 smbusers
drwxr-xr-x 2 root root  4096 Aug 10  2015 tls
ian@ian-UbuntuServer:~$ ls -l /var/lib/samba
total 1368
-rw-------  1 root root       421888 Oct 30 21:53 account_policy.tdb
-rw-------  1 root root          696 Oct 30 21:53 group_mapping.tdb
drwxr-xr-x  2 root root         4096 Apr 21 21:36 netlogon
drwxr-xr-x 10 root root         4096 Apr 29 16:08 printers
drwxr-xr-x  3 root root         4096 Apr 19 16:24 private
drwxr-xr-t  3 root root         4096 Apr 21 21:36 profiles
-rw-------  1 root root       528384 Apr 24 10:15 registry.tdb
drwxr-xr-x  2 root root         4096 Apr 21 21:36 root
-rw-------  1 root root       421888 Oct 31 10:59 share_info.tdb
drwxrwx--T  2 root sambashare   4096 Apr 21 21:25 usershares

```

Edit: Also, everything appears to be working now! The share showed up as "netdrive" on my network right after installation. My smb.conf has not changed (I guess purge did not remove it...) and my credentials were accepted. I appear to be able to both read and write.

---

### Post by bab1 on 2016-04-29
> **vaguely_clear said:**
> Here are the results from both after purging but before reinstalling, just in case that's relevant:

```
ian@ian-UbuntuServer:~$ ls -l /etc/samba
total 40
-rw-r--r-- 1 root root     8 Aug 10  2015 gdbcommands
-rw-r--r-- 1 root root 12787 Apr 27 15:31 smb.conf
-rw-r--r-- 1 root root  9542 Apr 21 21:35 smb.conf.old.gadmin-samba-0.3.2
-rw-r--r-- 1 root root    91 Apr 21 21:35 smbusers
drwxr-xr-x 2 root root  4096 Aug 10  2015 tls
ian@ian-UbuntuServer:~$ ls -l /var/lib/samba
total 1364
-rw------- 1 root root       421888 Oct 30 21:53 account_policy.tdb
-rw------- 1 root root          696 Oct 30 21:53 group_mapping.tdb
drwxr-xr-x 2 root root         4096 Apr 21 21:36 netlogon
drwxr-xr-x 3 root root         4096 Apr 19 16:24 private
drwxr-xr-t 3 root root         4096 Apr 21 21:36 profiles
-rw------- 1 root root       528384 Apr 24 10:15 registry.tdb
drwxr-xr-x 2 root root         4096 Apr 21 21:36 root
-rw------- 1 root root       421888 Oct 31 10:59 share_info.tdb
drwxrwx--T 2 root sambashare   4096 Apr 21 21:25 usershares

```

And here are the results of both after reinstalling:

```
ian@ian-UbuntuServer:~$ ls -l /etc/samba
total 40
-rw-r--r-- 1 root root     8 Aug 10  2015 gdbcommands
-rw-r--r-- 1 root root 12787 Apr 27 15:31 smb.conf
-rw-r--r-- 1 root root  9542 Apr 21 21:35 smb.conf.old.gadmin-samba-0.3.2
-rw-r--r-- 1 root root    91 Apr 21 21:35 smbusers
drwxr-xr-x 2 root root  4096 Aug 10  2015 tls
ian@ian-UbuntuServer:~$ ls -l /var/lib/samba
total 1368
-rw-------  1 root root       421888 Oct 30 21:53 account_policy.tdb
-rw-------  1 root root          696 Oct 30 21:53 group_mapping.tdb
drwxr-xr-x  2 root root         4096 Apr 21 21:36 netlogon
drwxr-xr-x 10 root root         4096 Apr 29 16:08 printers
drwxr-xr-x  3 root root         4096 Apr 19 16:24 private
drwxr-xr-t  3 root root         4096 Apr 21 21:36 profiles
-rw-------  1 root root       528384 Apr 24 10:15 registry.tdb
drwxr-xr-x  2 root root         4096 Apr 21 21:36 root
-rw-------  1 root root       421888 Oct 31 10:59 share_info.tdb
drwxrwx--T  2 root sambashare   4096 Apr 21 21:25 usershares

```

Edit: Also, everything appears to be working now! The share showed up as "netdrive" on my network right after installation. My smb.conf has not changed (I guess purge did not remove it...) and my credentials were accepted. I appear to be able to both read and write.
That's great news!  How about posting the current (what is working) smb.conf.  My guess is that it left smb.conf file we created and it now works.  I just want to be sure.  ;-)

---

### Post by vaguely_clear on 2016-04-29
> **bab1 said:**
> That's great news!  How about posting the current (what is working) smb.conf.  My guess is that it left smb.conf file we created and it now works.  I just want to be sure.  ;-)

Yes, it did leave the old smb.conf I believe. Here it is in it's current form:

```
## Sample configuration file for the Samba suite for Debian GNU/Linux.
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


# Declare NetBIOS name
        netbios name = NETDRIVE


# Set name resolve order
        name resolve order = bcast


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


[netdrive]
path = /media/netdrive
        valid users = @users
        browseable = yes
        force group = users
        writeable = yes
        create mask = 0664
        directory mask = 2775

```

I did try accessing the share from two other Macs, but did not see it in the Network section of either. They are both connected via wireless vs wired; the Mac that can see the share is wired. Any idea why it would broadcast over ethernet but not wifi?

Also, should I do anything about permissions on the shared drive?

---

### Post by bab1 on 2016-04-29
> **vaguely_clear said:**
> Yes, it did leave the old smb.conf I believe. 

Indeed it did.  It is fine just as it is.
> 
I did try accessing the share from two other Macs, but did not see it in the Network section of either. They are both connected via wireless vs wired; the Mac that can see the share is wired. Any idea why it would broadcast over ethernet but not wifi?
[/QUOTE
Wired vs WiFi is not the question.  There is something else.  All of this uses TCP/IP and the  Ethernet is both Wired (Fast Ethernet or better) or WiFi (802.11 b/g/n).  Always Ethernet.

Ye need to see why you can't browse but you should always be able to connect directly.


Also, should I do anything about permissions on the shared drive?[/QUOTE]
This a a shared folder at the root of the partition. eh?  What do you get from these commands (nothing should have changed)```

ls -l /media

ls -l /media/netdrive

```
Add some files and folders and then check the ownership and permissions (again with the commands above.

---

### Post by vaguely_clear on 2016-04-29
> **bab1 said:**
> Indeed it did.  It is fine just as it is.

This a a shared folder at the root of the partition. eh?  What do you get from these commands (nothing should have changed)```

ls -l /media

ls -l /media/netdrive

```
Add some files and folders and then check the ownership and permissions (again with the commands above.

Here is the output from the two ls commands. Note that the file Test.pdf was added by me after connecting to the share right before my last post.

```
ian@ian-UbuntuServer:~$ ls -l /mediatotal 8
drwxr-x---+  2 root root 4096 Apr 24 17:50 ian
drwxrwxrwx  24 ian  ian  4096 Apr 29 21:12 netdrive
ian@ian-UbuntuServer:~$ ls -l /media/netdrive
total 180
drwxrwxrwx  4 ian ian    4096 Jun 11  2014 Audiobooks
drwxrwxrwx  3 ian ian    4096 Oct 31 11:01 Backup
drwxrwxrwx  3 ian ian    4096 Mar 28 12:00 Books
drwxrwxr-x  7 ian ian    4096 Feb 23 21:41 Broadcasting Work
drwxrwxrwx 10 ian ian    4096 Apr  9  2014 Fonts
drwxrwxrwx  2 ian ian   16384 Apr  9  2014 lost+found
drwxrwxrwx  5 ian ian    4096 Jan  1 14:13 Movies
drwxrwxrwx  7 ian ian    4096 Apr 19 17:06 Music
drwxrwxrwx  3 ian ian    4096 Apr  9  2014 Music Videos
drwxrwxrwx  5 ian ian    4096 Apr 21 22:10 Operating System Images
drwxrwxrwx  6 ian ian    4096 Sep 17  2015 Photos
drwxrwxrwx  2 ian ian    4096 Apr  9  2014 Podcasts
drwxrwxrwx  5 ian ian    4096 Jul 16  2015 Shared Documents
drwxrwxrwx  2 ian ian    4096 Sep  9  2014 Shell Scripts
drwxrwxrwx  3 ian ian    4096 Oct 31 11:06 Software
drwxrwxrwx  8 ian ian    4096 Aug 26  2014 Sync
-rw-rw-r--  1 ian users 92737 Mar 23 16:18 Test.pdf
drwxrwxrwx  4 ian ian    4096 Apr  9  2014 TV Shows
drwxrwxrwx  3 ian ian    4096 Apr  9  2014 Videos
drwxrwxrwx  4 ian ian    4096 May 18  2014 Workout Videos

```

I can connect to the share directly via IP with no trouble on the two wireless Macs. All three Macs are on the same version of OS X. After fiddling around on one of them, netdrive just suddenly showed up and worked. It may be OS X, honestly. I'll see if netdrive sticks around in the file navigator for a few days and go from there unless you have any other ideas.

---

### Post by bab1 on 2016-04-30
> **vaguely_clear said:**
> Here is the output from the two ls commands. Note that the file Test.pdf was added by me after connecting to the share right before my last post.

```
ian@ian-UbuntuServer:~$ ls -l /mediatotal 8
drwxr-x---+  2 root root 4096 Apr 24 17:50 ian
drwxrwxrwx  24 ian  ian  4096 Apr 29 21:12 netdrive
ian@ian-UbuntuServer:~$ ls -l /media/netdrive
total 180
drwxrwxrwx  4 ian ian    4096 Jun 11  2014 Audiobooks
drwxrwxrwx  3 ian ian    4096 Oct 31 11:01 Backup
drwxrwxrwx  3 ian ian    4096 Mar 28 12:00 Books
drwxrwxr-x  7 ian ian    4096 Feb 23 21:41 Broadcasting Work
drwxrwxrwx 10 ian ian    4096 Apr  9  2014 Fonts
drwxrwxrwx  2 ian ian   16384 Apr  9  2014 lost+found
drwxrwxrwx  5 ian ian    4096 Jan  1 14:13 Movies
drwxrwxrwx  7 ian ian    4096 Apr 19 17:06 Music
drwxrwxrwx  3 ian ian    4096 Apr  9  2014 Music Videos
drwxrwxrwx  5 ian ian    4096 Apr 21 22:10 Operating System Images
drwxrwxrwx  6 ian ian    4096 Sep 17  2015 Photos
drwxrwxrwx  2 ian ian    4096 Apr  9  2014 Podcasts
drwxrwxrwx  5 ian ian    4096 Jul 16  2015 Shared Documents
drwxrwxrwx  2 ian ian    4096 Sep  9  2014 Shell Scripts
drwxrwxrwx  3 ian ian    4096 Oct 31 11:06 Software
drwxrwxrwx  8 ian ian    4096 Aug 26  2014 Sync
-rw-rw-r--  1 ian users 92737 [COLOR="#FF0000"]Mar 23[/COLOR] 16:18 Test.pdf
drwxrwxrwx  4 ian ian    4096 Apr  9  2014 TV Shows
drwxrwxrwx  3 ian ian    4096 Apr  9  2014 Videos
drwxrwxrwx  4 ian ian    4096 May 18  2014 Workout Videos

```

I can connect to the share directly via IP with no trouble on the two wireless Macs. All three Macs are on the same version of OS X. After fiddling around on one of them, netdrive just suddenly showed up and worked. It may be OS X, honestly. I'll see if netdrive sticks around in the file navigator for a few days and go from there unless you have any other ideas.
Except for the funny creation date (see red) the file ownership is good.  All files and folders should have the user-group and *users* from now on.  Ne folders should have the SGID set (drwxrw**[SIZE=4]s[/SIZE]**r-w (see MY bold).

The network browsing may take a bit of time (15 to 20 minutes) to start working.  This is because Samba resets the Master Browse List around that frequency.  So even having start to work after some time is reasonable.  I'd just keep using it for tonight and see if all is well.

---

### Post by vaguely_clear on 2016-04-30
> **bab1 said:**
> Except for the funny creation date (see red) the file ownership is good.  All files and folders should have the user-group and *users* from now on.  Ne folders should have the SGID set (drwxrw**[SIZE=4]s[/SIZE]**r-w (see MY bold).

Sorry, yes, the creation date is not recent. I just uploaded a random PDF from my computer and changed the name thinking that the user I connected with would have ownership. I didn't think to make a fresh file.

I made a new folder on a remote machine and the permissions listed via ls -l are drwxrwxr-x, so is that not what should have happened? I apologize for my ignorance, I have no idea what all those x's and w's mean.

So in order for both users to have full access to all existing files, should I go through and update permissions on what's already there? Should the existing files be owned by the group Users? The other user is able to both read and write existing files, so I guess don't fix what's not broken?

> **bab1 said:**
> The network browsing may take a bit of time (15 to 20 minutes) to start working.  This is because Samba resets the Master Browse List around that frequency.  So even having start to work after some time is reasonable.  I'd just keep using it for tonight and see if all is well.

That appears to be the case. All machines are actually working fine now! I'll start making detailed notes about how it's all set up so I can rebuild the share when I upgrade.

---

### Post by bab1 on 2016-04-30
> **bab1 said:**
> Except for the funny creation date (see red) the file ownership is good.  All files and folders should have the user-group and *users* from now on.  Ne folders should have the SGID set (drwxrw**[SIZE=4]s[/SIZE]**r-w (see MY bold).

We can set the proper owners and permissions from the command line if you want.  To set the user-group to *users* on the entire netdrive file system we do this (from the ubuntu command line)```
sudo chgrp -R users /media/netdrive
```...now use this command to check your work```
ls -l /media/netdrive
```

Now we can set the permission on the same netdrive file system with this command
```
sudo chmod -R ug=rwX,o=rX /media/netdrive
```...make sure you use the upper case X in this command.

The last thing is to set the SGID bit on all the group directories with this command```
[s]sudo chmod -R g=s /media/netdrive[/s]
# should be
sudo chmod -R g+s /media/netdrive
```...check the work using the the same ls -l command```
ls -l /media/netdrive
```

Post the last one back for me to see.

---

### Post by bab1 on 2016-04-30
> **vaguely_clear said:**
> Sorry, yes, the creation date is not recent. I just uploaded a random PDF from my computer and changed the name thinking that the user I connected with would have ownership. I didn't think to make a fresh file.

There can be a difference between old files and newly created files.  In your case the old file was recreate on the share so it does have the logged in user and the users group as owners.
> 
I made a new folder on a remote machine and the permissions listed via ls -l are drwxrwxr-x, so is that not what should have happened? I apologize for my ignorance, I have no idea what all those x's and w's mean.

I think what you mean is you made a folder FROM a remote machine.  The folder resides on the share?  The rwx are read write and eXecute permissions for [COLOR="#0000FF"]user[/COLOR] (creator) and [COLOR="#008000"]group[/COLOR] and [COLOR="#800080"]others[/COLOR] (everyone).  So we have **[COLOR="#0000FF"]rwx[/COLOR][COLOR="#008000"]rwx[/COLOR][COLOR="#800080"]r-x[/COLOR]**
> 


---

### Post by vaguely_clear on 2016-04-30
> **bab1 said:**
> We can set the proper owners and permissions from the command line if you want.  To set the user-group to *users* on the entire netdrive file system we do this (from the ubuntu command line)```
sudo chgrp -R users /media/netdrive
```...now use this command to check your work```
ls -l /media/netdrive
```

Now we can set the permission on the same netdrive file system with this command
```
sudo chmod -R ug=rwX,o=rX /media/netdrive
```...make sure you use the upper case X in this command.

The last thing is to set the SGID bit on all the group directories with this command```
sudo chmod -R g=s /media/netdrive
```...check the work using the the same ls -l command```
ls -l /media/netdrive
```

Post the last one back for me to see.

```

ian@ian-UbuntuServer:~$ ls -l /media/netdrivetotal 320
drwx--Sr-x  4 ian   users   4096 Jun 11  2014 Audiobooks
drwx--Sr-x  3 ian   users   4096 Oct 31 11:01 Backup
drwx--Sr-x  3 ian   users   4096 Mar 28 12:00 Books
drwx--Sr-x  7 ian   users   4096 Feb 23 21:41 Broadcasting Work
drwx--Sr-x 10 ian   users   4096 Apr  9  2014 Fonts
drwx--Sr-x  2 ian   users  16384 Apr  9  2014 lost+found
drwx--Sr-x  5 ian   users   4096 Jan  1 14:13 Movies
drwx--Sr-x  7 ian   users   4096 Apr 19 17:06 Music
drwx--Sr-x  3 ian   users   4096 Apr  9  2014 Music Videos
drwx--Sr-x  5 ian   users   4096 Apr 29 22:28 Operating System Images
drwx--Sr-x  6 ian   users   4096 Sep 17  2015 Photos
drwx--Sr-x  2 ian   users   4096 Apr  9  2014 Podcasts
drwx--Sr-x  5 ian   users   4096 Jul 16  2015 Shared Documents
drwx--Sr-x  2 ian   users   4096 Sep  9  2014 Shell Scripts
drwx--Sr-x  3 ian   users   4096 Oct 31 11:06 Software
drwx--Sr-x  8 ian   users   4096 Aug 26  2014 Sync
-rw---Sr--  1 emily users 132984 Mar 12  2013 Test.jpeg
-rw---Sr--  1 ian   users  92737 Mar 23 16:18 Test.pdf
drwx--Sr-x  4 ian   users   4096 Apr  9  2014 TV Shows
drwx--Sr-x  3 ian   users   4096 Apr  9  2014 Videos
drwx--Sr-x  2 ian   users   4096 Apr 29 22:36 wocka
drwx--Sr-x  2 ian   users   4096 Apr 29 22:36 wocka2
drwx--Sr-x  4 ian   users   4096 May 18  2014 Workout Videos

```

> **bab1 said:**
> There can be a difference between old files and newly created files. In your case the old file was recreate on the share so it does have the logged in user and the users group as owners.

I think what you mean is you made a folder FROM a remote machine. The folder resides on the share? The rwx are read write and eXecute permissions for [COLOR=#0000FF]user[/COLOR] (creator) and [COLOR=#008000]group[/COLOR] and [COLOR=#800080]others[/COLOR] (everyone). So we have **[COLOR=#0000FF]rwx[/COLOR][COLOR=#008000]rwx[/COLOR][COLOR=#800080]r-x[/COLOR]**

Yes, sure enough, I made the folder on the share FROM the remote machine.

Thank you for the very simple explanation of the permissions. I have a few questions.

1. After running the commands above, it looks like group (Users, I assume) no longer has read or write. Does this mean that the other user will have trouble modifying my files?

2. Does the capital S affect this somehow?

3. What does the lowercase d in front of the permissions signify?

---

### Post by bab1 on 2016-04-30
> **vaguely_clear said:**
> ...
Thank you for the very simple explanation of the permissions. I have a few questions.

1. After running the commands above, it looks like group (Users, I assume) no longer has read or write. Does this mean that the other user will have trouble modifying my files?

Ahhhh, that's my mistake.  To correct that we need to go through the chmod commands again.  First you use this command which sets the permissions correctly (note: the ug=rwX sets both the user and group at read write and eXecute)```
sudo chmod -R ug=rwX,o=rX /media/netdrive
```
[COLOR="#0000FF"]Edit: I have corrected this in the original post.[/COLOR]

Now we want to **add** the SGID bit with this ```
sudo chmod -R g+s /media/netdrive
```...note this is a + to add the sgid bit.  My original instruction was with a = which *sets *the overall permissions.  Two different things.

Post the output of this command ```
ls -l /media/netdrive
```...we should see a much better result (rwx for user and user-group (user-group will be rws as there are only 3 characters dsiplayed).
> 
2. Does the capital S affect this somehow?

The S or s is the sgid bit settiing.  The s is used if the eXecute bit is set.  If the eXecute bit is not set the upper case S is set.  This allows the human to see at a glance whether the eXecute bit is set when the SGID bit is also set.
> 
3. What does the lowercase d in front of the permissions signify?
The d is shown if the entry is a directory.  If line is for a file then there is a blank space.  In the rwx setting the absence is show as a - so a read only permission would be r-- and and execute would be r-x.  The eXecute bit is used on directories to allow the user to access the directory.  Without that the user is denied access or traversal to subdirectories.

---

### Post by vaguely_clear on 2016-04-30
> **bab1 said:**
> Ahhhh, that's my mistake.  To correct that we need to go through the chmod commands again.  First you use this command which sets the permissions correctly (note: the ug=rwX sets both the user and group at read write and eXecute)```
sudo chmod -R ug=rwX,o=rX /media/netdrive
```
[COLOR=#0000FF]Edit: I have corrected this in the original post.[/COLOR]

Now we want to **add** the SGID bit with this ```
sudo chmod -R g+s /media/netdrive
```...note this is a + to add the sgid bit.  My original instruction was with a = which *sets *the overall permissions.  Two different things.

Post the output of this command ```
ls -l /media/netdrive
```...we should see a much better result (rwx for user and user-group (user-group will be rws as there are only 3 characters dsiplayed).

The S or s is the sgid bit settiing.  The s is used if the eXecute bit is set.  If the eXecute bit is not set the upper case S is set.  This allows the human to see at a glance whether the eXecute bit is set when the SGID bit is also set.

The d is shown if the entry is a directory.  If line is for a file then there is a blank space.  In the rwx setting the absence is show as a - so a read only permission would be r-- and and execute would be r-x.  The eXecute bit is used on directories to allow the user to access the directory.  Without that the user is denied access or traversal to subdirectories.

Enlightening, thanks for the clarification! Here is the output of the ls command:

```
ian@ian-UbuntuServer:~$ ls -l /media/netdrivetotal 320
drwxrwsr-x  4 ian   users   4096 Jun 11  2014 Audiobooks
drwxrwsr-x  3 ian   users   4096 Oct 31 11:01 Backup
drwxrwsr-x  3 ian   users   4096 Mar 28 12:00 Books
drwxrwsr-x  7 ian   users   4096 Feb 23 21:41 Broadcasting Work
drwxrwsr-x 10 ian   users   4096 Apr  9  2014 Fonts
drwxrwsr-x  2 ian   users  16384 Apr  9  2014 lost+found
drwxrwsr-x  5 ian   users   4096 Jan  1 14:13 Movies
drwxrwsr-x  7 ian   users   4096 Apr 19 17:06 Music
drwxrwsr-x  3 ian   users   4096 Apr  9  2014 Music Videos
drwxrwsr-x  5 ian   users   4096 Apr 29 22:28 Operating System Images
drwxrwsr-x  6 ian   users   4096 Sep 17  2015 Photos
drwxrwsr-x  2 ian   users   4096 Apr  9  2014 Podcasts
drwxrwsr-x  5 ian   users   4096 Jul 16  2015 Shared Documents
drwxrwsr-x  2 ian   users   4096 Sep  9  2014 Shell Scripts
drwxrwsr-x  3 ian   users   4096 Oct 31 11:06 Software
drwxrwsr-x  8 ian   users   4096 Aug 26  2014 Sync
-rw-rwSr--  1 emily users 132984 Mar 12  2013 Test.jpeg
-rw-rwSr--  1 ian   users  92737 Mar 23 16:18 Test.pdf
drwxrwsr-x  4 ian   users   4096 Apr  9  2014 TV Shows
drwxrwsr-x  3 ian   users   4096 Apr  9  2014 Videos
drwxrwsr-x  2 ian   users   4096 Apr 29 22:36 wocka
drwxrwsr-x  2 ian   users   4096 Apr 29 22:36 wocka2
drwxrwsr-x  4 ian   users   4096 May 18  2014 Workout Videos

```

I also have another question for when I reinstall. Earlier in this thread, you linked to another post where you were helping someone with a Samba share. In that conversation, there is talk of mounting the share at /srv/nas. Should I consider mounting mine at /srv/netdrive or something similar in the future? Are there functional or organizational reasons to do this?

---

### Post by bab1 on 2016-04-30
> **vaguely_clear said:**
>  I also have another question for when I reinstall. Earlier in this thread, you linked to another post where you were helping someone with a Samba share. In that conversation, there is talk of mounting the share at /srv/nas. Should I consider mounting mine at /srv/netdrive or something similar in the future? Are there functional or organizational reasons to do this?
There is no functional reason, but there sure is an organizational and, from my point of view, cultural reasons ( how we do things here).  The organizational reason is described [**here**]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard").  The /srv branch of the file system is used for all data servers provide to others on a network (i.e file servers).  As a systems administrator, if I am looking at a host that I am not familiar with, I at least expect to find the file system configured to the Linux File System Hierarchy standards.

The /media branch is where udev processes auto mounts temporarily used media (USB flash drives or CD/DVD drives).  You can configure those items to show up on your desktop.

---

### Post by vaguely_clear on 2016-04-30
> **bab1 said:**
> There is no functional reason, but there sure is an organizational and, from my point of view, cultural reasons ( how we do things here).  The organizational reason is described [**here**]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard").  The /srv branch of the file system is used for all data servers provide to others on a network (i.e file servers).  As a systems administrator, if I am looking at a host that I am not familiar with, I at least expect to find the file system configured to the Linux File System Hierarchy standards.

The /media branch is where udev processes auto mounts temporarily used media (USB flash drives or CD/DVD drives).  You can configure those items to show up on your desktop.

Got it. I'll mount to /srv/netdrive when I install 16.04.

Everything seems to be working quite well now. Thanks for committing so much time to helping me fix this Samba share. I will probably be back if something goes awry when configuring 16.04, but for now, I think this is resolved!

---

### Post by vaguely_clear on 2016-06-13
Well, I hate to revive an old thread, but I just got around to installing 16.04 and I cannot get the Samba share working. Would it be best to revive this thread or start a new one?

---

### Post by vaguely_clear on 2016-06-13
> **vaguely_clear said:**
> Well, I hate to revive an old thread, but I just got around to installing 16.04 and I cannot get the Samba share working. Would it be best to revive this thread or start a new one?

Apparently I spoke a few minutes too soon. I forgot to add users to Samba with smbpasswd. Everything appears to be working now; please disregard.

---

