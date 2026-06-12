---
title: "Samba Share problem"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by Garf on 2007-05-22
Hi..

I want to simply be able to share a folder so people can access videos stored on my machine over the home network..

I remember I was able to do this really easily last time I tried it in 6.06...

From memory I didn't have to change anything in 6.06, it just worked.

Basically when I type in \\192.168.1.10 from the run prompt in windows it asks for a usename and password, and the only password i can think of is the username and password I use to log onto Ubuntu...

And that doesn't work... So how do I make it so people can just view whats in there without a password?

Any help much appreciated...

---

### Post by renzokuken on 2007-05-22
when that pops up it is asking for a samba username/password, not the ubuntu user account. you can either set up a samba user and password for it or you can edit your smb.conf file so that it allows anyone to access the folder without a u/n or p/w.

could you post your smb.conf and i'll show you how. its either /etc/smb.conf or /etc/samba/smb.conf, cant remember

---

### Post by Garf on 2007-05-22
> **renzokuken said:**
> when that pops up it is asking for a samba username/password, not the ubuntu user account. you can either set up a samba user and password for it or you can edit your smb.conf file so that it allows anyone to access the folder without a u/n or p/w.

could you post your smb.conf and i'll show you how. its either /etc/smb.conf or /etc/samba/smb.conf, cant remember

Cool..

I did look at the smb.conf but I must have skimmed past it...

I'll have a look and see if I can find it...

---

### Post by Garf on 2007-05-22
Ok well here is a section of it, which I figure it is somewhere in here...

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

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
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

---

### Post by AlanRogers on 2007-05-22
That's smb.conf alright but you've actually posted the least helpful part - the top half of the file contains very little bar comments.

If you scroll down to the bottom of the file, you'll see entries which you'll recognise as relating to your configured shares. Post that and you'll get replies on which entries to modify to allow what you need.

Unfortunately, I'm at work on Windows at the moment, so I can't post an example. Sorry

---

### Post by renzokuken on 2007-05-22
yeah we need the second half

---

### Post by Garf on 2007-05-22
Haha no thats ok... I appreciate the help... 


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
[netlogon]
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

wins support = yes
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


[TV]
path = /media/sda1
available = yes
browsable = yes
public = yes
writable = no


[TV_ubuntu]
path = /home/gareth/TV
comment = TV Shows on Ubuntu
available = yes
browsable = yes
public = yes
writable = no

---

### Post by Garf on 2007-05-22
Did I post the wrong bit again??

---

### Post by AlanRogers on 2007-05-22
No, you posted exactly the right bit but I haven't yet been home to compare to my own copy of the file. However, I've done a quick Google search using [howto+samba+share ]("http://www.google.co.uk/search?q=howto+samba+share&start=0&ie=utf-8&oe=utf-8")and, on [Skippy Dot Net]("http://skippy.net/linux/2000/smb-howto.html") I found this code which, IIRC, is very similar to my own.
```
 # Applications Drive 
[apps] 
   comment = Applications 
   path = /samba/apps 
   public = no 
   writable = no 
   printable = no 
   create mask = 0666 
   directory mask = 0775 
#   force group = samba 
#   force user = samba 
   hide dot files = yes 
 
 # Data Drive 
[data] 
   comment = Data  
   path = /samba/data 
   public = no 
   writable = yes 
   printable = no 
   create mask = 0666 
   directory mask = 0775 
   force group = users 
#   force user = samba 
   hide dot files = yes 
 
 # A publicly accessible directory 
[public] 
   comment = Public Stuff 
   path = /samba/public 
   public = no 
   writable = yes 
   printable = no 
   create mask = 0666 
   directory mask = 0775 
#   force user = users 
   force group = users 
   hide dot files = yes 
```Obviously, you need to change things to reflect your own setup but you'll see various entries in there that are missing from yours and possibly the reason why yours isn't working.

Useful but insecure settings which are commented out on the above file excerpt are *force user* and *force group*. If you're just looking for these shares to be readable, set the flags accordingly and use these too for a seamless integration.

HTH

---

### Post by whitetrash on 2007-05-22
I got mine working by doing this:
####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = share            <-----modified that line

added this to the end:
[_shared]  <---name of the shared folder
  comment = Public Folder
  path = /home/james/_shared  <---path where the folder is
  public = yes
  writable = yes                         <--I set mine this way so users can read\write\copy\delete files
  create mask = 0777               <--" "
  directory mask = 0777           <--" "
  force user = nobody               <--no login required this way
  force group = nogroup            <--no login required this way

Found this from the Ubuntu Wiki: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add.2Fedit.2Fdelete_network_users](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add.2Fedit.2Fdelete_network_users)

hope that makes sense...

---

### Post by Garf on 2007-05-22
> **whitetrash said:**
> I got mine working by doing this:
####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = share            <-----modified that line

added this to the end:
[_shared]  <---name of the shared folder
  comment = Public Folder
  path = /home/james/_shared  <---path where the folder is
  public = yes
  writable = yes                         <--I set mine this way so users can read\write\copy\delete files
  create mask = 0777               <--" "
  directory mask = 0777           <--" "
  force user = nobody               <--no login required this way
  force group = nogroup            <--no login required this way

Found this from the Ubuntu Wiki: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add.2Fedit.2Fdelete_network_users](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add.2Fedit.2Fdelete_network_users)

hope that makes sense...

Cool.. that worked a treat :) Thanks...

---

### Post by AlanRogers on 2007-05-23
> **Garf said:**
> Cool.. that worked a treat :) Thanks...Just be aware that ```
create  mask = 0777
directory mask = 0777
force user  = nobody
force group = nobody
``` means that your share W I D E open. I'd try reducing the permissions or forcing a real user or better yet, set valid users up as Samba users with the same password as Windows, to lock it down ... unless of course it doesn't matter.

---

### Post by whitetrash on 2007-05-23
Glade to hear it worked for you.

---

