---
title: "Cannot access ubuntu samba server from other machine"
date: 2005-06-15
forum: Networking &amp; Wireless
---

### Post by hoss on 2005-06-15
Samba has started ok. I can access the samba server from the machine it's running on. However I cannot access it from another machine on the network. The other machine is running windows xp. I can see it in My Network places but when I double click it I get this:
"\\Telex is not accessible. You might not have permission to use this network resource......"

The samba logs have the following which I dont understand:

[2005/06/15 20:49:35, 0] lib/util_sock.c:get_peer_addr(1000)
  getpeername failed. Error was Transport endpoint is not connected
[2005/06/15 20:49:35, 0] lib/util_sock.c:write_socket_data(430)
  write_socket_data: write failure. Error = Connection reset by peer
[2005/06/15 20:49:35, 0] lib/util_sock.c:write_socket(455)
  write_socket: Error writing 4 bytes to socket 22: ERRNO = Connection reset by peer
[2005/06/15 20:49:35, 0] lib/util_sock.c:send_smb(647)
  Error writing 4 bytes to client. -1. (Connection reset by peer)
[2005/06/15 21:06:16, 0] lib/util_sock.c:get_peer_addr(1000)
  getpeername failed. Error was Transport endpoint is not connected
[2005/06/15 21:06:16, 0] lib/util_sock.c:write_socket_data(430)
  write_socket_data: write failure. Error = Connection reset by peer
[2005/06/15 21:06:16, 0] lib/util_sock.c:write_socket(455)
  write_socket: Error writing 4 bytes to socket 22: ERRNO = Connection reset by peer
[2005/06/15 21:06:16, 0] lib/util_sock.c:send_smb(647)
  Error writing 4 bytes to client. -1. (Connection reset by peer)

An ideas anyone?

---

### Post by deBaas on 2005-06-20
Did you try accessing it using your IP adress: \\192.168.x.x or so?
Did you open the right ports in your firwall?

---

### Post by hoss on 2005-06-20
Yes. I even tried turning the firewall off but still doesnt work

---

### Post by cwaldbieser on 2005-06-20
Does the directory you are trying to share have permissions set so anyone can read it?

If that is not the permission problem, then you probably have to fool around with the samba config to allow access.  It is probably easiest if you use one of the graphical admin tools like SWAT.  Try looking for settings like "browseable" and "guest ok".  

You can examine the config file directly (/etc/samba/smb.conf) and edit it directly if you are feeling fiesty.  Just remember to run testparm when you are finished to check and make sure you haven't made any syntax errors in the configuration.

---

### Post by hoss on 2005-06-21
[QUOTE=cwaldbieser]Does the directory you are trying to share have permissions set so anyone can read it?

If that is not the permission problem, then you probably have to fool around with the samba config to allow access.  It is probably easiest if you use one of the graphical admin tools like SWAT.  Try looking for settings like "browseable" and "guest ok".  

You can examine the config file directly (/etc/samba/smb.conf) and edit it directly if you are feeling fiesty.  Just remember to run testparm when you are finished to check and make sure you haven't made any syntax errors in the configuration.[/QUOTE]
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
   workgroup = hossbert.com

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
   encrypt passwords = no

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

[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes
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

[downloads]
    comment = download area
    writable = yes
    guest ok = yes
    path = /downloads
    public = yes

# Windows clients look for this share name as a source of downloadable
# printer drivers
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


That's my smb.conf file if it's any help

---

### Post by cwaldbieser on 2005-06-21
I don't know how important authentication is to you, but you could probably put in "security = share" under that commented out line ";security = user".  Your share should have the "guest ok = Yes" line under it, and then you should have anonymous access to the share.

---

### Post by abeowitz on 2006-02-22
If it's any help, I had very similar problems with 3.0.14 that comes with Breezy.

I installed the sama-common, samba & swat debs (3.0.21b) from samba.org and everything started working properly...  

[http://us1.samba.org/samba/ftp/Binary_Packages/Debian/samba/3/](http://us1.samba.org/samba/ftp/Binary_Packages/Debian/samba/3/)

---

