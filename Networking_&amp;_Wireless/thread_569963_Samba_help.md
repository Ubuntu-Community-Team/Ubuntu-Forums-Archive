---
title: "Samba help"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by lionround on 2007-10-07
I am a newbie, so please "Handle with care".  I am having problems with my Samba configuration.  I thought I had everything installed and configured correctly, but when I did my Update Manager and then had to reboot, I am having problems.

My smb.conf file looks like this:

[global]
    ; General server settings
    netbios name = ubuntu
    
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

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
    valid users = %S
    create mode = 0777
    directory mode = 0755
    browseable = no
    read only = no
    ;\veto files = /*.{*}/.*/mail/bin/

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
    path = /media/samba/
    path = /media/LACIE
    
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = david
    force group = david
available = yes
browsable = yes
public = yes
writable = yes


[LACIE]
path = /media/LACIE
available = yes
browsable = yes
public = yes
writable = yes

[Music]
path = /media/LACIE/Music
available = yes
browsable = yes
public = yes
writable = yes

I have added myself to the Samba userbase (I hope).  However, when I go to Places -> Network, my "Windows Network" shows up but when I click on it, there is nothing in it.

I am fairly new to this, but I do know how to run "some" things from the command line.

Any suggestions?

---

### Post by lionround on 2007-10-07
bump

---

### Post by SonicSteve on 2007-10-07
You added yourself to the Samba userbase, was it this command that you used?

sudo smbpasswd -a yourusername 

my checklist for samba is usually, 
make sure samba support is installed 
add user to samba users list
Make changes to smb.conf
If I want to mount (map a drive in windows lingo) a windows or samba share make sure smbfs is installed.
Add mounts to fstab file /etc/fstab (fstab has no extention)


I don't think that I've ever had trouble at least viewing computers on the network, but I have had trouble accessing them. Also at times I've had trouble with other computers accessing the Ubuntu shares.  Typically viewing the other computers isn't the issue you'll see.  I'm trying to remember but I think that you can at least browse networks even without installing samba.  I can't confirm this because It's been so long since I tried. 

Have you setup firewalls on your router, on the computers? If so start from basics and disable all   firewalls. Then try browsing again.
Also if you don't have passwords on your user accounts this might also be giving you trouble. I know that windows didn't like it when you share things from an account without a password.

---

### Post by pelle.k on 2007-10-07
I dont recognize the layout of that configuration file. I must be something you've created yourself? Might work, but i suggest you use the original file to build from.
It located in /usr/share/samba/smb.conf, so copy that to /etc/samba
```
sudo cp /usr/share/samba/smb.conf /etc/samba
```

include your shares in that file (at the end of it);
> [LACIE]
path = /media/LACIE
available = yes
browsable = yes
public = yes
writable = yes

[Music]
path = /media/LACIE/Music
available = yes
browsable = yes
public = yes
writable = yes

And there is only one setting i would recommend, to "ease" accesing those shares from other computers, and that is the "security = share" setting, instead of the default "security = user" (remember, the ";" is a commented line, sort of what "#" is). It's not as secure as "user", but it requires no password; in other terms "simple file sharing". **Never do this without a firewall protecting you network though.** You might want to restrict samba to ips you can trust with "interfaces = 192.168.1.1,192.168,1,2" etc..

Also you *have* installed samba right? You also have to reload samba after messing with the conf;
```
sudo /etc/init.d samba reload
```

---

### Post by lionround on 2007-10-07
Sonic Steve,

I could not figure how to mount a drive in the /etc/fstab file; however, I haven't gotten onto the network yet anyway, so that is the next step.  Everything else you suggested is done.

pelle

The smb.conf file that I am using was the original and I have "tweaked" it according to the instructions I have gotten from users on this forum as well as some of the How To's.

I could back it up and start over with the original, I suppose to see if I can get back on the network.

---

### Post by SonicSteve on 2007-10-08
Here is my smb.conf file it's quite generic and should at least give something to compare to.

> #======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

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
   load printers = yes

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


[NetworkShare]
path = /media/WD80/NetworkShare
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by SonicSteve on 2007-10-08
With my file I can browse my home network, share files and my printer (using CUPS). 
To access cups type this url into a web browser [http://localhost:631/](http://localhost:631/) once you've added a printer and a user to the cups access (all point and click) a printer should be shared. 

Troubleshooting ideas.
1. firewalls
2. network connectivity
 2.a proper IP address
 2.b is the address in the same IP range as the other computers you are trying to access
3. is the IP static or DHCP 
4. do you have a DHCP on the network, if so can your Ubuntu box get an address from it. 
 4.a if not why not? It should be able to.
 4.b. if your network DHCP is a windows 2003 server you may not have Unix/Linux access enabled. This is the case at my school, If I set the IP to static I can browse and even get Internet access but I can't get a DHCP IP address lease.

Start with these ideas and see what you come up with. Let me know what your technical level of expertise is in regards to networking, that way  I know how explicit to be in instructing you.

PS. if you are using you Ubuntu box to post these replies, you at least know that your network is working and to some extent configured.

---

