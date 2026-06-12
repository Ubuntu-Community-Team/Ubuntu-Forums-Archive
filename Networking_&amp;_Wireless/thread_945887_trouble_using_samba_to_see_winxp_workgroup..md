---
title: "trouble using samba to see winxp workgroup."
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by splitlenz on 2008-10-12
Hey, hows everyone enjoying their ubuntu. 

So call me crazy, but i installed ubuntu 8.10, I know, its still 18 days , but whats 18 days? lol. anyway, if your still reading , thanx. 

I installed samba, samba-common, samba-doc,samba-tools,smbclient,smbfs,swat.

I can't even get swat to work, i tried going to htt://localhost:901/ and nothing shows up. Firefox just says it failed to connect. 

Im running a T42p IBM laptop and i just want to access to workgroup i have setup between win xp machines. no domain, they just exist on the workgroup. 

Below is my smb.conf file and my inetd.conf and host.conf, and smbusers file.

My Situation: I can see the laptop with my windows machinese. I can access the shared folders and see inside.  

I CAN see the windows machines with the ubuntu laptop. I can get into the workgroup, i can click on the windows computers name but, dum dum dum, I can't access the shared folders on those computers. Let me explain my setup a bit more. 

One windows machine has simple file sharing on, no username and password needed. I can see the shared folders but when i double click on the folder it says it cannot mount location. Second win xp machine has username and password turned on, not simple filesharing. I can't even see the shared folders on the last one.

I have put the laptop on the same workgroup, i added the lan ip and names to the host file and i tried setting up swat, which apparently didn't work. 

Take a look and hopefully can help. Its my first time setting it up, so be prepared for noob moments. All the files are how they came in ubuntu, i didn't change much. i have no idea what goes in or goes out of smb.conf, im not looking to have my laptop to be a network server, i just want to see the other computers and get some files. Seems easy enough on mac and windoz, dunno what happen to ubuntu lol. 

Thanx for your patience.

#======================= Global Settings =======================

[global]
   workgroup = ROUNDSEAT
   server string = %h server (Samba, Ubuntu)
#   wins support = no

;   wins server = w.x.y.z

   dns proxy = no

;   name resolve order = lmhosts host wins bcast

#### Networking ####

;   interfaces = 127.0.0.0/8 eth0

;   bind interfaces only = yes



#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m

   max log size = 1000

#   syslog only = no

   syslog = 0

   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

security = user   username map = /etc/samba/smbusers

 encrypt passwords = true
 
 passdb backend = tdbsam

obey pam restrictions = yes


   unix password sync = yes

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

   pam password change = yes

map to guest = bad user

########## Domains ###########


;   domain logons = yes

;   logon path = \\%N\profiles\%U

#   logon path = \\%N\%U\profile


;   logon drive = H:
#   logon home = \\%N\%U


;   logon script = logon.cmd


; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########


#   load printers = yes


;   printing = bsd
;   printcap name = /etc/printcap


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
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

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


**inetd.conf**
netbios-ssn	stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/smbd
	# swat is the Samba Web Administration Tool
swat stream tcp nowait.400 root /usr/sbin/swat swat

**hostf.conf**
# Server personal
192.168.0.170 NATINGTI-9669F6


**smbusers**
sysusername = "alex"

---

### Post by splitlenz on 2008-10-15
can someone close this thread? 

i went back to 8.04 hardy heron and its working better. a few glitches here and there, but its working much better. 

this is irrelevant thread since im not on intrepid aymore.

thank you.

---

