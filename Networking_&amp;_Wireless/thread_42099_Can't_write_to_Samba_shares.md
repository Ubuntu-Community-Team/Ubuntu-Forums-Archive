---
title: "Can't write to Samba shares"
date: 2005-06-16
forum: Networking &amp; Wireless
---

### Post by mglukhovsky on 2005-06-16
I'm a bit of a newcomer to Samba, and am just starting to get the hang of The opnly real problem I'm experiencing is that I'm getting read-only access to my Samba shares. I'm suspecting that it's either a problem with my smb.conf or the users that have been created. The appropriate sections of /etc/ssamba/smb.conf are as follows:

```
[alpha]
   comment = Alpha share
   path = /mnt/alpha
   public = yes
   writable = yes
   create mask = 0777
   directory mask = 0777
   force user = nobody
   force group = nogroup


[beta]
   comment = Beta share
   path = /mnt/beta
   public = yes
   writable = yes
   create mask = 0777
   directory mask = 0777
   force user = nobody
   force group = nogroup
```

Can anyone offer insight?

---

### Post by netrattler on 2005-06-16
If you right click on the folder you want to share and click share folder, then change "do not share" to "smb", put the name in what you want to call your new share, and put a check by allow browsing, and make sure you don't have the Read Only checked.

Joe

---

### Post by mglukhovsky on 2005-06-16
When I went to the sharing settings, everything appeared to be configured correctly, except that the option to allow folder browsing wasn't checked. I tried enabling it, but  I'm still not able to write to those shares.

---

### Post by netrattler on 2005-06-16
Here is a copy of my smb.conf so you can match it up. You might see the public on my share but I've also edited permissions on my home folders only so other users can't look anywhere else but there own home directories.

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
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = domination

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# If we receive WINS server info from DHCP, override the options above. 
   include = /etc/samba/dhcp.conf

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
;   security = user

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


[netrattler]
path = /home/netrattler
comment = netrattler's home
available = yes
browseable = yes
public = yes
writable = yes

---

### Post by mglukhovsky on 2005-06-18
Thanks so much for trying to help. However, another symptom showed up that clears the smb.conf from responsibility for the read-only access. When I browse my network via Nautilus (directly, i.e. //ubuntu64-server/alpha) I have full read/write access. However, when I mount the shares with smbfs, I have read-only access. What mount command ought to be used (for comparison with mine)?

---

### Post by netrattler on 2005-06-19
I searched around a little bit on this forum and came across something, read the bottom post by DoorOpener and see if this will work for you.

[http://ubuntuforums.org/showthread.php?p=207317#post207317](http://ubuntuforums.org/showthread.php?p=207317#post207317)

Joe

---

### Post by mglukhovsky on 2005-06-19
DoorOpener was using anonymous guest access, and this gives extremely limited access. However, I now suspect that I haven't created any Samba users, despite my having issued the "smbpasswd -a <username>" command. I created a user called "michael", and when I try and enter the password to access the share with the mount command, the password I assigned doesn't work... I'm very much at a loss here.

Here's the command I used: ```
mount -t smbfs //ubuntu64-server/alpha /home/michael/alpha -o "michael,fmask=0777,dmask=0777"
```

---

### Post by mglukhovsky on 2005-06-19
I solved my problem, finally! The issue was that the folder that the share was being mounted to belonged to the root user, and simply accessing that folder from Nautilus   accessed the folder as a regular user... and since the root owned the folder, the regular user couldn't write to it.

smbmount has an option to override the group and user ownership, with the "gid" and "uid" options. My smbmount command is now:
```
mount -t smbfs -o username=michael,uid=michael,gid=michael //ubuntu64-server/alpha /media/network/alpha/
```
where michael is the name of the user... and as it turned out I had created a user using smbpasswd, I just didn't assign the correct password.

Thanks for all your help, it led me to the right answer!

---

### Post by holomorph on 2005-06-21
I'm also having trouble writing to smb shares, here's my process:

brows to the folder I want to share, (eg my home folder say) right click on the folder and click share folder. Change "do not share" to "smb", pick a name (bjorn_home), and put a check by allow browsing.  Read Only is not checked.  Click OK as required.

This results in a /etc/samba/smb.conf file which is, as far as I can tell, practically identical to that which netrattler posted.  Of course my share name is different, I'm also missing the include = /etc/samba/dhcp.conf bit, but I don't think that's relevant.

So now I go to places->Network Servers  (or netwokr:/// in nautilus) and brows to my share (smb://wight/bjorn_home in this case).  Now right click and select "Create Folder".  I get a dialogue that says I don't have permission to write to the destination.  

Any ideas what changes I need to make so that I can actually write to the folders I share? 

looking at the log I think mb it's connecting as user 'nobody', which may be the problem, but I'm not sure.  If someone could try the procedure I outlined above and see if they get the same results and maybe figure out what needs to be changed I'd be grateful.

Thanks, 
Bjorn

---

### Post by holomorph on 2005-07-02
I finally got things working, should have looked here a long time ago:
[http://www.ubuntuguide.org/#sambaserver](http://www.ubuntuguide.org/#sambaserver)

adding these three lines to my share definition in /etc/samba/smb.conf 
valid users = bjorn
create mask = 0700
directory mask = 0700

I'm not sure which was the key line (though I suspect it was the valid users bit, thougth I'd tried that before though)

---

