---
title: "Is my network secure - public folder, read/write permissions"
date: 2005-08-04
forum: Networking &amp; Wireless
---

### Post by geofff on 2005-08-04
After months of trying + re-installations etc I have finally got a network that works! I have the linux box attached to 2 Windows machines via a D-link router which is attached via broadband to the world. I have set the system up so the 3 machines can read/write to each other without authentication.

I've done this by creatiing a public folder /home/public per the unofficial advice guide [http://ubuntuguide.org/index.html#sharepublicfoldersreadwritesecurityshare](http://ubuntuguide.org/index.html#sharepublicfoldersreadwritesecurityshare) using masks 0777. I have set  security = share.  I have also in the global section of smb.conf included  hosts allow = 192.168  as recommended in one of the threads. 

While pleased I've at last got what I want I'm a bit concerned that I might have opened up my machine or the windows machines to a security risk. I would very much welcome observations!

My full smb.conf is shown below
[PHP]#
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
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = RIGLI
   netbios name = fritz

# server string is the equivalent of the NT Description field
   server string = fritz
   hosts allow = 192.168.

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
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


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
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


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

wins support = no
[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

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

[public]
 comment = Public Folder
 path = /home/public
 public = yes
 writable = yes
 create mask = 0777
 directory mask = 0777
 force user = nobody
 force group = nogroup

[/PHP]

I'm still relatively new to this so replies in simple terms please!

Thanks Geofff

---

### Post by GrumpySmurf on 2005-08-04
After a brief look, the configuration seems sane.  Make sure you are set up to use smb passwords on the samba server and that passwords are encrypted.  Here's my "public" share from my samba server for comparison to yours,

```
[export]
        comment = Server Filesystem
        path = /export
        browseable = yes
        guest ok = no
        printable = no
        write list = @users
        create mask = 0664
        directory mask = 0775

```
Note that I have a group, users, that is allowed to write files to this share.  World write permissions are usually not advised.

I see you're using a non-routable network, 192.168, that is good.  You might further lock this down to the particular subnets that you are using (192.168.1, 192.168.20, whatever).  A combination of firewall and tcpwrapper configuration will also help lock down the system.  That's another topic, and you'd have plenty of reading to do for that :).

---

### Post by geofff on 2005-08-04
Thanks for the above. A number of queries.

[QUOTE=GrumpySmurf]  Make sure you are set up to use smb passwords on the samba server and that passwords are encrypted. [/QUOTE]
I set up network users using 
$ sudo smbpasswd -a <username>
per [http://ubuntuguide.org/index.html#addeditdeletenetworkusers](http://ubuntuguide.org/index.html#addeditdeletenetworkusers) 

As my smb.conf has a line :  encrypt passwords = true 
I assume the passwords entered are encrypted? 

As the public folder has full read/write permissions set and no authentication for access I presume the only time the passwords are relevant are when the machines make initial contact through the network and the users/passwords stored on the Windows machines are validated by Samba. Is this how it works? If it is I think your point is covered?

[QUOTE=GrumpySmurf]
Note that I have a group, users, that is allowed to write files to this share.  World write permissions are usually not advised.[/QUOTE]
Can I have "group users" without requiring authentication each time a file is accessed from another machine? One of the reasons for my setup is to allow my wife to backup some of her files easily onto the linux box. If she has to enter authentication each time it won't happen!

If I leave it as it is are you saying this is "not advised"?

Just for my education what are masks 0664 and 0775?

Geofff

---

### Post by GrumpySmurf on 2005-08-04
[QUOTE=geofff]I assume the passwords entered are encrypted? [/quote]
Probably a safe assumption :). To double check, you'll need to dig into the Windows registry of the client systems, if you're that ambitious.  I dont know the registry keys off the top of my head, but they're well documented.

> As the public folder has full read/write permissions set and no authentication for access I presume the only time the passwords are relevant are when the machines make initial contact through the network and the users/passwords stored on the Windows machines are validated by Samba. Is this how it works? If it is I think your point is covered?
I don't know the innerworkings of the protocol, but that is my understanding as well.  I believe this is the case if the password is saved by the client upon creating the connection.

> Can I have "group users" without requiring authentication each time a file is accessed from another machine? One of the reasons for my setup is to allow my wife to backup some of her files easily onto the linux box. If she has to enter authentication each time it won't happen!
I have directories set up on the /export share in my config.  My wife and I point 'My Documents' to these directories.  That way the data already lives on the server.  I then back up the filesystem to tape (shameless plug: I like [BRU](http://www.bru.com)).

> Just for my education what are masks 0664 and 0775?
This should create the files and directories with rw-rw-r-- and rwxrwxr-x permissions, respectively, or owner/group read/write, other read-only.  

The smb.conf man page has a detailed description, plus the chmod and umask manpages should help as well.

> If I leave it as it is are you saying this is "not advised"?
Not only myself, but many security pundits recommend against world write permissions. There was an article last week posted on rootprompt.org that included removing world-write permissions from all files on a system to help with security.

System security is a huge topic and the best approach requires several levels of configuration, including but not limited to: secure kernel (selinux for example), firewall rules (iptables), obscuring ports (running http on port 1480 instead of 80), wrapping services to allow certain networks/ips (tcpwrappers), jailing applications (chroot jails) and more.  Full on security is beyond the scope of simple forum posts and if you're really interested in implementing it, PM me and I can send you a list of resources.

---

### Post by geofff on 2005-08-06
Thanks for the above. I haven't had time so far to look at the man pages etc as suggested. I can see I'm going to have to do a lot of reading before I really know what I'm doing with this. The message I am getting is that for the moment I would be better off restricting permissions.

[QUOTE=GrumpySmurf]
Not only myself, but many security pundits recommend against world write permissions.[/QUOTE]
What are you referring to? Is this the line: security = share, the use of 0777 masks, or writable = yes in my smb.conf public folder or something else?

> 
PM me and I can send you a list of resources.
Thanks for the offer. At the moment I think I probably wouldn't understand what I was getting! You've given me plenty of leads. I will try to follow them through first.
Understanding your smb.conf export using the man pages etc looks like being a good start!

Thanks
Geofff

---

### Post by GrumpySmurf on 2005-08-09
> What are you referring to? Is this the line: security = share, the use of 0777 masks, or writable = yes in my smb.conf public folder or something else?
Sorry - the use of the 0777 mask.  That third 7 is for the 'other' permission.  The chmod and umask man pages have far more detail about this.

---

