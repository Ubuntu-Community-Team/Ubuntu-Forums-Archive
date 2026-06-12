---
title: "I can't share two of my drives"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by cooljimy84 on 2010-08-08
Hi all, i've been having issues with this one for a while and have been sent here from another forum.  here we go  

I have Ubuntu 10.04 LTS AMD 64bit. i can share pretty much anything i want from my home location (on a software raid 1).. that works fine, 
however i have a software Raid 1 and raid 0 with large amounts of music isos etc, but i can't seem to access them from any other machine on the network, even the machine i have shared them from can't browse them access the network. 

It shows the folder i have shared, but when i click mount or double click it i get them message  
"Unable to mount location" 
"Failed to mount Windows share"  

Now one disk is in EXT3 and the other EXT4 (my root drive is also in EXT3) I also get the following error in my samba logs 
"[2010/08/08 19:52:43, 0] smbd/service.c:988(make_connection_snum) canonicalize_connect_path failed for service movies, path /media/The_Store_/Movies"

 I've had a bit of help else where [http://forums.overclockers.co.uk/showthread.php?t=18168276](http://forums.overclockers.co.uk/showthread.php?t=18168276)  

Can any one help as this is driving me mad ! and worked well in 9.10...

---

### Post by jflaker on 2010-08-08
For one, the shared folder can NOT be in your /home/UserID folder because of the permissions of the toplevel folder (UserID).  The same permission issue also applies to windows user folder.......if you are sharing off a windows box.

Create a folder off the root and give it read/execute permissions (keep others from deleting)....

Once you create a main folder, you can put other folder in there to share also......

---

### Post by Morbius1 on 2010-08-08
Why not post the the output of the following commands so we can have something to reference:

```
net usershare info
``````
tetparm -s
```

---

### Post by cooljimy84 on 2010-08-08
Below are the outputs from the commands

> james@merc-srv:~$ net usershare info
[movies]
path=/media/The_Store_/Movies
comment=
usershare_acl=Everyone:F,
guest_ok=y

[crooks ****]
path=/media/The_Store_/crooks ****
comment=
usershare_acl=Everyone:F,
guest_ok=y

[bitload]
path=/home/james/Downloads/Bit Torrent Load
comment=
usershare_acl=Everyone:F,
guest_ok=y

[bittorrent]
path=/home/james/Downloads/Bit Torrent Complete
comment=
usershare_acl=Everyone:R,
guest_ok=y

james@merc-srv:~$ 


> james@merc-srv:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


---

### Post by cooljimy84 on 2010-08-08
Ooops the might be a swear word in my folder list
[Crooks s***]
displays as [Crooks stuff]       shall we say ;)

---

### Post by cooljimy84 on 2010-08-08
> **jflaker said:**
> For one, the shared folder can NOT be in your /home/UserID folder because of the permissions of the toplevel folder (UserID).  The same permission issue also applies to windows user folder.......if you are sharing off a windows box.

Create a folder off the root and give it read/execute permissions (keep others from deleting)....

Once you create a main folder, you can put other folder in there to share also......

The folders i'm having issues with are on a seprate drive and are owned by me

"james@merc-srv:/media$ ls -la
total 36
drwxr-xr-x  9 root  root  4096 2010-07-27 19:21 .
drwxr-xr-x 22 root  root  4096 2010-08-03 18:56 ..
lrwxrwxrwx  1 root  root     6 2010-05-11 22:42 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2010-05-11 22:42 cdrom0
drwxr-xr-x  2 root  root  4096 2010-07-04 12:23 The
drwx------  2 root  root  4096 2010-06-15 19:29 The Store
drwx------  8 james james 4096 2010-05-25 19:34 The_Store_
drwxr-xr-x  2 root  root  4096 2010-07-04 01:29 VM
drwx------  2 root  root  4096 2010-06-15 19:29 VM Store
drwx------  6 james james 4096 2010-05-03 23:54 VM_Store_

i'm shareing  The_Store_

---

### Post by Morbius1 on 2010-08-08
That's your problem. Samba is authorizing guests to access the share. But no one has authority over linux file permissions and they are allowing only one user to access /media/The_Store_ and that's "james". It's never getting to the child directory of Movies.


If it's really an ext4 formatted partition you could just issue the following command:

```
sudo chmod 0755 /media/The_Store_
```

---

### Post by cooljimy84 on 2010-08-08
Woops the store is ext3 and VM store is ext4,

would i still need to use the same command ?

---

### Post by cooljimy84 on 2010-08-08
Used it and it now works fine !!!

U guys are perfect....

thats been driving me mad for months now !

---

### Post by robsablah on 2010-09-19
did that and same issue
 - formatted twice

same config file from jaunty

smb.conf
> [global]

usershare owner only = false

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
   security = user

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
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supd$

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

============Misc================
# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

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
# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes
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
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0777
   writeable = yes

#[Print drivers]
#   comment = drivers for the printers
#   browseable = yes
#   path = /media/Elements/software/drivers/printers
#   guest ok = yes
#   read only = yes

[software]
   comment = software
   browseable = yes
   path = /media/Elements/software
   guest ok = yes
   read only = yes
   write list = robert

[recently downloaded]
   comment = recently downloaded
   browseable = yes
   path = /media/5/recently downloaded
   guest ok = yes
   read only = yes
   write list = robert

[dropbox]
   comment = your change to contribute - put stuff here!
   browseable = yes
   path = /media/5/dropbox
   guest ok = yes
   read only = no
   writable = yes
   create mask = 0777

[New Music]
   comment = Music
   browseable = yes
   path = /media/Elements/music
   guest ok = yes
   read only = yes
   write list = robert

[Music]
   comment = Music
   browseable = yes
   path = /media/5/music
   guest ok = yes
   read only = yes
   write list = robert

[drives]
   comment =
   browseable = no
   path = /media/
   guest ok = no
   read only = yes
   write list = robert candace



---

### Post by Morbius1 on 2010-09-19
robsablah, you may or you may not have the same issue but I can tell you that your smb.conf is never executing and here's why:
> ============Misc================
# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
usershare allow guests = yesSamba is trying to execute the line "============Misc..." and can't because there is no such parameter as =====. Put a # sign in front of that line so that the section looks like this:
> [COLOR=Blue]#[/COLOR]============Misc================
# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
usershare allow guests = yesSave smb.conf and restart samba:
```
sudo service smbd restart
```[COLOR=Blue]EDIT: While you're in smb.conf you might want to fix this as well:[/COLOR]
> [drives]
comment =
browseable = no
path = /media/
guest ok = no
read only = yes
write list = robert candaceYou have "browseable = no" so no one will know it's there - but maybe that's the way you want it to be - not sure.

---

### Post by robsablah on 2010-09-20
ha! 
yeah 

this MISC is something i threw in to shorten it.... sorry i should have known

and the share... i don't want anone but me in there... so if i have guests, i can move data easy, etc......

as the problem still stands..... boo :)
i don't get it it was fine for jaunty.. and failed on karmic also

booooo :(

---

### Post by Morbius1 on 2010-09-20
robsablah,

*[1] You have one share:*
> [drives]
comment =
[COLOR=Blue] browseable = no[/COLOR]
path = /media/
[COLOR=Blue] guest ok = no[/COLOR]
read only = yes
write list = robert candace                      The important parts in this situation is that it's not accessible by non authenticated users and it's not browseable so it's invisible to other network users.

* [2] Now you have these shares:*
> path = /media/Elements/software
path = /media/5/recently downloaded
path = /media/5/dropbox
path = /media/Elements/music
path = /media/5/music
They all have two things in common:
> [COLOR=Blue]browseable = yes
guest ok = yes[/COLOR]
All of these shares are children of the [drives] shares which are not browseable and do not allow guest access. Can't have shares within shares without getting unexpected results. Remove the [drives] share and se if you can access the other 5 shares.

---

### Post by robsablah on 2010-09-20
[1] worked before

[2] adjustments made

robert@WATTSRV:/media/Elements$ sudo nano /etc/samba/smb.conf 
robert@WATTSRV:/media/Elements$ sudo service smbd restart
[sudo] password for robert: 
smbd start/running, process 3999
robert@WATTSRV:/media/Tv Shows$ tail /var/log/samba/log.lr-uber 

[2010/09/20 19:21:36,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service software, path /media/Elements/software

fail

thanks though

the purpose of the auth is so guests cant delete data
 - and I can shift data
discoveries over time:
each share has no impact on the other - handled like a ftp folder - the one that logs in has access

do you think i should start a new thread?

---

### Post by Morbius1 on 2010-09-20
Just a wild guess but are any of these partitions you're trying to share on /media external hard drives formatted in ntfs?

Post the output of the following command please:
```
ls -al /media
```

---

