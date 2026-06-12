---
title: "Network Sharing Stopped"
date: 2020-02-06
forum: Networking &amp; Wireless
---

### Post by Jonners59 on 2020-02-06
This keeps cropping up for me over the years, and somehow old fixes do not seem to work.  I had a power outage and since restoring the machine(s) I can not share drives with other machines on the network.

I have a pc that I run continuously to do two things:
1. run a virtual machine that runs an IP-PBX - that is working fine.
2. As a local shared storage for the family; photos, videos and stuff like that.

A ```
uname -a
``` comes up with:  ```
Linux server 5.3.0-29-generic #31-Ubuntu SMP Fri Jan 17 17:27:26 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```  Not sure why it is saying server...

The directory I wish to share is:  Store/Documents/Documents

fstab entry is:
```
UUID=xxxxxxx    /media/Documents           ext4    relatime,noexec   1  2
```
Have tried and that was the old:
```
relatime,noexec,guest,uid=1000
```

Old Samba that did work, but not now:
```
[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   netbios name = Store
   workgroup = xxxxxxxxxxxxxx
   name resolve order = bcast host lmhosts wins
#  socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

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

[Documents]
    comment = Documents
    path = /media/Documents/Documents
    available = yes
    browsable = yes
#    public = yes
    writable = yes
    read only = no
    locking = no
    guest ok = yes
        directory mask = 0777
#    force user = server
#    force group = xxxxxxxxxxxxxxx



[OS]
;    comment = OS Backup
;    path = /media/Backup/OS
;    available = yes
;    browsable = yes
;    public = yes
;    writeable = yes
;    locking = no
;    guest ok = yes
#    force group = xxxxxxx

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


And the new one that I created yesterday after finding an app that created such - not sure of the IP addresses, where they came from:
```

[global]
netbios name = Store
server string = Samba file and print server
workgroup = xxxxxxx
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

[Documents]
    comment = Documents
    path = /media/Documents/Documents
    available = yes
    browsable = yes
#    public = yes
    writable = yes
    read only = no
    locking = no
    guest ok = yes
        directory mask = 0777
#    force user = server
#    force group = xxxxxxxx

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


```


Symptom, before I started downloading everything and anything, was that directories were visible, but all content was root, so could not add, move, delete or change anything, just view.
Now, I can't evebn find the machine on the network.

---

### Post by HermanAB on 2020-02-06
Whenever I see a Samba configuration file, it reminds me of Sendmail...  OK, OK, not quite as bad, but still.

To me, the easiest solution is to install NFS instead of bothering with Samba/CIFS.  NFS configuration is so simple, it is typically a one liner:
/home    *(rw,sync,no_root_squash)

Here is a little guide that explains it better:
[https://help.ubuntu.com/stable/serverguide/network-file-system.html](https://help.ubuntu.com/stable/serverguide/network-file-system.html)

---

### Post by Morbius1 on 2020-02-06
>  And the new one that I created yesterday after finding an app that  created such - not sure of the IP addresses, where they came from:
I would bet the farm you used gadmin-samba. It doesn't belong in the repositories. It goes back to the olden tymes ( Version 3 .. maybe Version 2 ) of samba when there were 3" thick books on the care and feeding of Samba. None of that applies today.

You don't have to take my word for it just run:
```
testparm -s
```
You will get a long list of "I have no idea what that option is", "That option is deprecated", and "You really shouldn't add this option anymore, we fixed that back when Jimmy Carter was president" - or words to that affect.

Go back to your original smb.conf. 

The share in question will work:
> [Documents]
    comment = Documents
    path = /media/Documents/Documents
    available = yes
    browsable = yes
#    public = yes
    writable = yes
    read only = no
    locking = no
    guest ok = yes
        directory mask = 0777
#    force user = server
#    force group = xxxxxxxxxxxxxxx
Assumming the path exists and the guest user as read / write access. To confirm run:
```
ls -al /media/Documents
```

Two side notes:
[1] Your original idea of adding a "force user" is a good idea and resolves a number of permissions issues.

[2] More of a bookkeeping issue but edit smb.conf and comment out [OS]:
> [COLOR=#ff0000]**#**[/COLOR][OS]
;    comment = OS Backup
;    path = /media/Backup/OS
;    available = yes
;    browsable = yes
;    public = yes
;    writeable = yes
;    locking = no
;    guest ok = yes
#    force group = xxxxxxx

If you run "testparm -s" on your old smb.conf it will eliminate this error message:
> WARNING: No path in service OS - making it unavailable!
NOTE: Service OS is flagged unavailable.


---

### Post by Jonners59 on 2020-02-06
> **HermanAB said:**
> Whenever I see a Samba configuration file, it reminds me of Sendmail...  OK, OK, not quite as bad, but still.

To me, the easiest solution is to install NFS instead of bothering with Samba/CIFS.  NFS configuration is so simple, it is typically a one liner:
/home    *(rw,sync,no_root_squash)

Here is a little guide that explains it better:
[https://help.ubuntu.com/stable/serverguide/network-file-system.html](https://help.ubuntu.com/stable/serverguide/network-file-system.html)

You are not far wrong.  I'll look at that at some point.  A bit too new for me at this stage.  Thank you.

---

### Post by slickymaster on 2020-02-06
*Thread moved to **Networking & Wireless**.*

---

### Post by Jonners59 on 2020-02-06
> **Morbius1 said:**
> I would bet the farm you used gadmin-samba. It doesn't belong in the repositories. It goes back to the olden tymes ( Version 3 .. maybe Version 2 ) of samba when there were 3" thick books on the care and feeding of Samba. None of that applies today.

You don't have to take my word for it just run:
```
testparm -s
```
You will get a long list of "I have no idea what that option is", "That option is deprecated", and "You really shouldn't add this option anymore, we fixed that back when Jimmy Carter was president" - or words to that affect.

Go back to your original smb.conf. 

The share in question will work:

Assumming the path exists and the guest user as read / write access. To confirm run:
```
ls -al /media/Documents
```

Two side notes:
[1] Your original idea of adding a "force user" is a good idea and resolves a number of permissions issues.

[2] More of a bookkeeping issue but edit smb.conf and comment out [OS]:

If you run "testparm -s" on your old smb.conf it will eliminate this error message:


Morbius
How fantastic to hear from you.  Been an age.  Does that mean I am improving!!!!!!!!  The number of times you have bailed me out.

OK, so seems a tad of admin there.  Changed the OS by adding #, so now reads #OS

```
public = yes
;    writable = yes
;       browsable = yes
#[OS]
;    comment = OS Backup
;    path = /media/Backup/OS
;    available = yes
;    browsable = yes
```

Ran and got...
```
sudo samba restart
WARNING: No path in service Backup Documents - making it unavailable!

```

Also tried to run "Lucky Backup Super user, but getting errors about permissions...
```
rance/May 2016/
 

 

 [COLOR=#ff0000]r[/COLOR][COLOR=#ff0000]sync: chgrp "/media/Backup/Documents/Baroni Ltd/Administration" failed: Operation not permitted (1) rsync: failed to set times on "/media/Backup/Documents/Baroni Ltd/Administration/Company Information/Baroni Certificates/Insurance": Operation not permitted (1) rsync: failed to set times on "/media/Backup/Documents/Baroni Ltd/Administration/Company Information/Baroni Certificates/Insurance/Indemnity Insurance": Operation not permitted (1) rsync: failed to set times on "/media/Backup/Documents/Baroni Ltd/Administration/Company Information/Baroni Certificates/Insurance/Indemnity Insurance/May[/COLOR]


```

And tried to access via another PC and it says [HTML]Failed to mount Windows share invalid argument[/HTML]

Also, I have noticed a couple of things
1.  The directories, when accessed via the PC where the directories are hosted, they are owned by said same machine, BUT when accessed via the network they are owned by root and can not be changed.

2.  Passwords seem to be involved.  I did ```
smb://IP address/Documents...
```
 and it askes for a password

---

### Post by Morbius1 on 2020-02-06
> WARNING: No path in service Backup Documents - making it unavailable!
You have no service called [Backup Documents] in either your old or new smb.conf. If you changed your smb.conf file you need to post it again.

---

### Post by Jonners59 on 2020-02-07
> **Morbius1 said:**
> You have no service called [Backup Documents] in either your old or new smb.conf. If you changed your smb.conf file you need to post it again.
Morning, Morbius.
OK, but it is a tad of legacy, kept in case I want to use it again.  I thought that ```
;
``` was the same as ```
#
``` and they blanked out the line.  Is this a wrong assumption.

No changes to the file, other than adding the ```
;
``` in front of the OS, as instructed and pasted below.

Also, I have tried to search and connect to the "Store" (IP ending 50) via both my wife's Windows laptop and this xfce PC (Linux PC 5.3.0-29-generic #31-Ubuntu SMP Fri Jan 17 17:27:26 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux).  As below, my PC comes back with the error message:  [HTML]Failed to mount Windows share invalid argument[/HTML], and my wife's laptop can not find it or this one on the network at all.  This is worse than before as with before I could find the machines but the folders/directories were all owned by root and I could not make any changes to contents or the contents, just view.

During my "try anything" stage, I did follow some instruction and downloaded something (can't recall exactly) to the Store and I notice that when I ```
uname -a
``` it says [HTML]Linux server 5.3.0-29-generic #31-Ubuntu SMP Fri Jan 17 17:27:26 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux[/HTML] which is not what I would have ex-expected.

PS:  This PC was affected by the power crash and have been restoring it back.

What have I done?!?!?

---

### Post by Morbius1 on 2020-02-07
My only suggestion at this point is to rebuid your samba server by first setting it to the way it is set up by default.

But before we do that ( and it's not as hard as it sounds ) I need some verification that some basic settings are correct.

[1] Open a terminal and run the following to get the IP address of your Linux machine:
```
hostname -I
```
[2] Then go to your client machine and run [highlight]ping 192.168.0.100[/highlight] substituting the result you got from step [1] for 192.168.0.100

Is the ping successful or do you get errors?

[3] I need to see the permissions of where all your shared folders are located so please post the output of the this command:
```
ls -al /media
```
And:
```
ls -al /media/Documents
```

---

### Post by Jonners59 on 2020-02-07
> **Morbius1 said:**
> My only suggestion at this point is to rebuid your samba server by first setting it to the way it is set up by default.

But before we do that ( and it's not as hard as it sounds ) I need some verification that some basic settings are correct.

[1] Open a terminal and run the following to get the IP address of your Linux machine:
```
hostname -I
```
[2] Then go to your client machine and run [highlight]ping 192.168.0.100[/highlight] substituting the result you got from step [1] for 192.168.0.100

Is the ping successful or do you get errors?

[3] I need to see the permissions of where all your shared folders are located so please post the output of the this command:
```
ls -al /media
```
And:
```
ls -al /media/Documents
```

OK, here goes.  First the ping:
[HTML]ping 123.456.7.89 PING 123.456.7.89 (123.456.7.89) 56(84) bytes of data.64 bytes from xxx.xxx.x.xx: icmp_seq=1 ttl=64 time=0.185 ms[/HTML]

And directory permissions...
[HTML]total 36
drwxr-xr-x   7 root  root   4096 Jan 31 21:58 .
drwxr-xr-x  26 root  root   4096 Jan  8 06:34 ..
drwxr-xr-x  22 root  root   4096 Jan  6  2018 3CXExt
drwxr-xr-x   6 store store  4096 Jul 12  2019 Backup
drwxrwxrwx   6 store store  4096 Aug 25 08:26 Documents
drwxrwx---   5 store store 12288 Oct  2 18:10 Ext
drwxrwxr-x+  2 store store  4096 Jan 31 21:55 store
[/HTML]

And lastly...

[HTML]ls -al /media/Documents
total 23604
drwxrwxrwx  6 store store     4096 Aug 25 08:26 .
drwxr-xr-x  7 root  root      4096 Jan 31 21:58 ..
-rw-rw-r--  1 root  root  24133632 Jun 16  2019 core
drwxrwxr-x 11 store root      4096 May 17  2019 Documents
drwxrwxr-x  2 root  root     16384 Apr 15  2019 lost+found
drwxrwxr-x  4 root  root      4096 Apr 19  2019 .Trash-0
drwxrwxr-x  5 store store     4096 Jan 24 14:46 .Trash-1000
[/HTML]

---

### Post by Morbius1 on 2020-02-07
> OK, here goes.  First the ping:
     HTML Code:

     ping 123.456.7.89PING 123.456.7.89 (123.456.7.89) 56(84) bytes of data.64 bytes from 192.168.1.50: icmp_seq=1 ttl=64 time=0.185 ms 

OK, I have no idea what's going on there. 192.168.1.50 is the local LAN and 123.456.7.89 is something outside your own network. Your server isn't in your own network?

---

### Post by Jonners59 on 2020-02-07
> **Morbius1 said:**
> OK, I have no idea what's going on there. xxx.xxx.x.xx is the local LAN and 123.456.7.89 is something outside your own network. Your server isn't in your own network?
OOOHH, No, sorry, I changed all the IP addresses.  Must have missed one.  Will xxx it out.

---

### Post by Morbius1 on 2020-02-07
Now I really don't know what's going on. [COLOR=#ff0000]I'm going to assume all of your machines are in your own home network behind your only router.[/COLOR]

We are going to start with the default smb.conf that came with your system:

[1] Make sure the following file exists: [highlight]/usr/share/samba/smb.conf[/highlight]

[2] Make a backup of your current smb.conf
```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
```
[3] Copy the reserved default to the working location:
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```
Then we are going to make some additions to the new smb.conf:

[4] Edit /etc/samba/smb.conf and right under the workgroup = WORKGROUP line add these:
```
name resolve order = bcast host lmhosts wins
netbios name = STORE
```
[5] Then at the bottom of the file add your share definition:
```
[Documents]
    path = /media/Documents/Documents
    force user = store
    guest ok = Yes
    locking = No
    read only = No
```
[6] Save the file.

[7] Restart samba in this order:
```
sudo service smbd restart
```
```
sudo service nmbd restart
```

Now from the client machine access the server by its ip address:
\\xxx.xxx.x.xxx in Windows Explorer
smb://xxx.xxx.x.xxx in thunar

---

### Post by Jonners59 on 2020-02-07
[COLOR=#000000][COLOR=#222222][FONT=Verdana]> **Morbius1 said:**
> Now I really don't know what's going on. [/FONT][/COLOR][COLOR=#ff0000][FONT=Verdana]I'm going to assume all of your machines are in your own home network behind your only router.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Yes, that is correct. All are behind the Router.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]> **Morbius1 said:**
> We are going to start with the default smb.conf that came with your system[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][1] Make sure the following file exists: [highlight]/usr/share/samba/smb.conf[/highlight][/CODE][/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#222222][FONT=Verdana]Yes, it is.[/FONT][/COLOR]

[/COLOR]> **Morbius1 said:**
> 
[COLOR=#000000][COLOR=#222222][FONT=Verdana][2] Make a backup of your current smb.conf[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
```[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][3] Copy the reserved default to the working location:[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#222222][FONT=Verdana]2 & 3 completed, no issues[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]> **Morbius1 said:**
> 
[COLOR=#000000][COLOR=#222222][FONT=Verdana]Then we are going to make some additions to the new smb.conf:[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana][4] Edit /etc/samba/smb.conf and right under the workgroup = WORKGROUP line add these:[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]```
name resolve order = bcast host lmhosts wins
```[/FONT][/COLOR]```

[COLOR=#222222][FONT=Verdana]netbios name = STORE[/FONT][/COLOR]
```
[COLOR=#222222][FONT=Verdana][5] Then at the bottom of the file add your share definition: [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]```
[Documents]
```[/FONT][/COLOR]```

[COLOR=#222222][FONT=Verdana]path = /media/Documents/Documents[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]force user = store[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]guest ok = Yes[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]locking = No[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]read only = No[/FONT][/COLOR]
```
[COLOR=#222222][FONT=Verdana][6] Save the file.[/FONT][/COLOR][/COLOR]

[COLOR=#000000][COLOR=#222222][FONT=Verdana]4, 5, and 6 done, though changed workgroup = to the one we use as well[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]> **Morbius1 said:**
> [7] Restart samba in this order:[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]```
sudo service smbd restart
```[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]```
sudo service nmbd restart
```[/FONT][/COLOR][/COLOR]

[COLOR=#000000][COLOR=#222222][FONT=Verdana]Done, no issues.[/FONT][/COLOR]

[/COLOR]> **Morbius1 said:**
> 
[COLOR=#000000][COLOR=#222222][FONT=Verdana]Now from the client machine access the server by its ip address:[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]\\xxx.xxx.x.xxx in Windows Explorer[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]smb://xxx.xxx.x.xxx in thunar[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#222222][FONT=Verdana]Done and the file system appears on both Windows and Ubuntu[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#222222][FONT=Verdana]Issue now is everything is listed as &#8220;root&#8221; and so I can not add or change anything.[/FONT][/COLOR][/COLOR]

---

### Post by Morbius1 on 2020-02-07
Yes, it will show everything as owned by root ( or "unknown" depending on the file manager ). But you can still add / remove content. It's a gvfs thing.

---

### Post by Jonners59 on 2020-02-07
No, I can't.  I have tried in Windows and Ubuntu.  I can navigate, see stuff, but can not move it, change it, delete it anything....  Any thoughts how to corrcet this

---

### Post by Morbius1 on 2020-02-07
No. I cannot reproduce your symptom.

Your target on the server is owned by "store":
> ls -al /media/Documents
total 23604
drwxrwxrwx  6 store store     4096 Aug 25 08:26 .
drwxr-xr-x  7 root  root      4096 Jan 31 21:58 ..
-rw-rw-r--  1 root  root  24133632 Jun 16  2019 core
[COLOR=#0000cd]drwxrwxr-x 11 **store** root      4096 May 17  2019 Documents[/COLOR]
Your client user is coming across as store and is set to be writeable:
> [COLOR=#000000][COLOR=#222222][FONT=Verdana]path = /media/Documents/Documents[/FONT][/COLOR]
[COLOR=#0000cd][FONT=Verdana]force user = **store**[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]guest ok = Yes[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]locking = No[/FONT][/COLOR]
[COLOR=#0000ff][FONT=Verdana]read only = **No**[/FONT][/COLOR][/COLOR]
What you see is what you get.

---

### Post by Jonners59 on 2020-02-07
SO what else could it be?  Must be a setting in fstab or users, maybe???????

---

### Post by Morbius1 on 2020-02-07
There aren't any ownership settings in fstab for an ext4 partition. You can post it if you want.

---

### Post by Jonners59 on 2020-02-08
OK, got the read-write to work by adding ```
    directory mask = 0770
``` to the Documents argument in smb.conf

It now reads:
```
[Documents]
    path = /media/Documents/Documents
    force user = store
    guest ok = Yes
    locking = No
    read only = No
    directory mask = 0770
```

On the "Store" fstab entry is...
[HTML]UUID=xxxxxxxxxxxxxxxxxxx  /media/Documents           ext4    relatime,noexec   1  2[/HTML]
where UUID has been xxxx


So next task is to get it to auto mount on the Ubuntu machine, so looking at fstab

This worked:

```

//"IP address xxx.xxx.x.xxx"/"Directory"	/media/"Mount point folder"	cifs	guest,uid=1000,iocharset=utf8	0	0

//"IP Address xxx.xxx.x.xxx"/"Directory"	             /media/"Mount point folder"	cifs	noauto,user,guest,uid=1000,iocharset=utf8	0	0

```
What is also nice is, if the remote device is not working/on then it does not go into fail mode, it the PC/Laptop starts normally

Also tried below, but that failed.
# Samba
#  //server/share  /media/samba  cifs  user=user,uid=1000,gid=100  0  0
# "Server" = Samba server (by IP or name if you have an entry for the server in your hosts file
# "share" = name of the shared directory
# "user" = your samba user
# This set up will ask for a password when mounting the samba share. If you do not want to enter a password, use a credentials file.
# replace "user=user" with "cred  entials=/etc/samba/credentials" In the credentials file put two lines
# username=user
# password=password
# make the file owned by root and ro by root (sudo chown root.root /etc/samba/credentials && sudo chmod 400 /etc/samba/credentials)

---

