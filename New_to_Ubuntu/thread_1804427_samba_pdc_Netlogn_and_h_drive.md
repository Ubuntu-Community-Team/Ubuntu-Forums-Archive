---
title: "samba pdc Netlogn and h drive ?"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-07-14
used to get win7 on domain [http://wiki.samba.org/index.php/Windows7](http://wiki.samba.org/index.php/Windows7)
used 
[https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html) and [http://www.youtube.com/watch?v=8MWBhlaLIxQ](http://www.youtube.com/watch?v=8MWBhlaLIxQ)
to conifgure samba

my netlogon an H (home) dirve do not connect when I logon onto wind7 which is on the domain. 

I have a file in my netlogon
called leanne.cmd it contains
@echo off
echo off
NET USE J: \\192.168.2.7\leanne

The file has been unix2dos /samba/netlogon/logon.cmd




my smb.conf is below 


#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = LBERMUDEZ

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

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
   domain logons = yes
   domain master = yes
   local master = yes
   preferred master = yes
   os level = 64 

   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
   logon drive = H:
   logon home = \\%N\%U


   logon script = %U.cmd


# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
 add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
[homes]
   comment = Home Directories
   browseable = no
   writable = yes 


# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
[netlogon]
   comment = Network Logon Service
   path = /home/lance/500gb/mombackup/samba/netlogon
   guest ok = yes
   read only = yes

[leanne]
   path = /home/lance/500gb/mombackup/windows
#   valid users = @leanne
   writable = yes
   create mask = 0775
   directory mask = 0775

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
[profiles]
   comment = Users profiles
   path = /home/lance/500gb/mombackup/samba/profiles
   guest ok = no
   browseable = no
   create mask = 0600
   directory mask = 0700

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

---

### Post by lance bermudez on 2011-07-19
the above works just copy only files you need into the new profile don't try to use the old one.

---

