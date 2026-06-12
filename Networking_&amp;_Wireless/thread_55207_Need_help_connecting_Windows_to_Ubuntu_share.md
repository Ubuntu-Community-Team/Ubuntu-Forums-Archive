---
title: "Need help connecting Windows to Ubuntu share"
date: 2005-08-07
forum: Networking &amp; Wireless
---

### Post by Hig on 2005-08-07
I have my network set up with a windows XP fileserver and my laptop over wireless with Ubuntu.

I can ping inside and outside my network with no problems whatsoever, I even have my shares from my XP filesystem mounted successfuly through fstab. I can also ping my laptop successfuly from my XP box through IP add. but not netbios name.

My smb.conf file is as follows:
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
   workgroup = Workgroup
netbios name = Laptop

# server string is the equivalent of the NT Description field
   server string = Ubuntu Laptop

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
   browseable = yes

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


[share]
path = /home/david/share
available = yes
browseable = yes
public = yes
writable = no

```

I have tried connecting through IP and netbios name on my server but nothing is connecting. I have also tried smbclient -L but I just get connection refused errors.

---

### Post by varunus on 2005-08-08
Do you have a Firewall running on the Ubuntu machine?  You may want to get Firestarter from Synaptic, and configure it to allow Samba packets.  I think Ubuntu is set up very conservative packet-wise out of box; install firestarter and add an exception for samba ports.

---

### Post by Hig on 2005-08-08
I added in exceptions for the SMB ports but still I get "The network path was not found" through windows and ```
david@laptop:~$ smbclient -U david -L 192.168.0.4
Error connecting to 192.168.0.4 (Connection refused)
Connection to 192.168.0.4 failed

```

Damnit, this is the last hurdle for me going completely to Ubuntu

---

### Post by al7kz on 2005-08-08
corrected errors

---

### Post by Hig on 2005-08-08
I can ping 'laptop' which indicates netbios is working, but I can't list available samba shares.

How does one do a complete removal of everything samba so that I could reinstall.

```
david@laptop:~$ ping laptop
PING localhost.localdomain (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=1 ttl=64 time=0.082 ms64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=2 ttl=64 time=0.044 ms
--- localhost.localdomain ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.044/0.063/0.082/0.019 ms
david@laptop:~$ smbclient -L laptop
Error connecting to 127.0.0.1 (Connection refused)
Connection to laptop failed
david@laptop:~$

```

---

### Post by al7kz on 2005-08-08
corrected errors

---

### Post by Hig on 2005-08-09
Bitchin dude.

My server will be running ubuntu before tomorrow is finished.

Seriously, you guys rock.

---

### Post by Hig on 2005-08-10
I think I got my problem sussed. After a little playing around I noticed the following series of events after rebooting.

```
david@laptop:~$ smbclient -L laptop
Error connecting to 127.0.0.1 (Connection refused)
Connection to laptop failed
david@laptop:~$ sudo /etc/init.d/samba restart
Password:
 * Stopping Samba daemons..                                              [ ok ]
 * Starting Samba daemons..                                              [ ok ]
david@laptop:~$ smbclient -L laptop
Password:
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.10-Ubuntu]

        Sharename       Type      Comment
        ---------       ----      -------
        share           Disk
        IPC$            IPC       IPC Service (Ubuntu Laptop)
        ADMIN$          IPC       IPC Service (Ubuntu Laptop)
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.10-Ubuntu]

        Server               Comment
        ---------            -------
        LAPTOP               Ubuntu Laptop
        SERVER

        Workgroup            Master
        ---------            -------
        WORKGROUP            SERVER
david@laptop:~$

```

It would appear that samba isn't starting on boot.

Whats the easiest way to fix this?

---

### Post by jetpeach on 2005-08-11
arg, I'm having the same problems.  my share seems to show up, but when I click on my Ubuntu machine from windows, it asks for a login and password and nothing works.  Isn't there a simpler way of configuring all this stuff, maybe an application with check boxes that can be selected easily with mouse clicks and such for different settings?

---

### Post by Hig on 2005-08-11
I'm having the same problem as the guy above. The shares show up in my network places but no combination of username/password will let me log in.

I'm also still trying to fix the whole needing to restart the samba service problem.

(Is ubuntuguide not working for anyone else?)

---

### Post by Hig on 2005-08-14
So no-one has any idea whats causing this then?

---

### Post by jetpeach on 2005-08-23
ubuntu community? help?  thanks!

---

### Post by s_p_a_r_k_y on 2005-08-23
unix accounts are separate from samba accounts.

to add a samba account
```
 sudo smbpasswd -a username 
```
it'll ask for a password. THis is the username/password you need from the windows boxen. I think you need a unix account wiht the same name as the samba account. Hope this helps...but there is TONS of samba documentation available on the web, a bit of googling and you would have your answer as well : )

---

### Post by Hig on 2005-08-24
Yeah, I found my answer already. I was forced into a reformat and it just worked afterwards.

---

