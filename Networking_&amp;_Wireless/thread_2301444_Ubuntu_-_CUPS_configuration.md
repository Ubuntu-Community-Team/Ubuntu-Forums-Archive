---
title: "Ubuntu - CUPS configuration"
date: 2015-11-02
forum: Networking &amp; Wireless
---

### Post by johns2 on 2015-11-02
Hello,

I have Samsung M2022 printer. I installed CUPS on my ubuntu server: Linux homeserver 3.13.0-66-generic #108-Ubuntu SMP Wed Oct 7 15:21:40 UTC 2015 i686 i686 i686 GNU/Linux. I download drivers from samsung page for linux. I installed printer correctly in CUPS. I was able to print test page as well with no problems.

BUt when it comes that i want to configure this remote printer on myh windows xp i cannot. I am using IPP. and i see jobs are going to printer, but printer
does not print the DATA, but some details related to a job.

Gotta some logs like this:


192.168.1.102 - - [02/Nov/2015:08:21:39 -0600] "POST /admin HTTP/1.1" 401 346 - -
192.168.1.102 - - [02/Nov/2015:08:21:39 -0600] "POST /admin HTTP/1.1" 200 346 - -
192.168.1.102 - homeserver [02/Nov/2015:08:21:40 -0600] "POST /admin HTTP/1.1" 200 346 - -
localhost - - [02/Nov/2015:08:21:40 -0600] "POST /admin/ HTTP/1.1" 401 34895 CUPS-Add-Modify-Printer successful-ok
localhost - homeserver [02/Nov/2015:08:21:40 -0600] "POST /admin/ HTTP/1.1" 200 34895 CUPS-Add-Modify-Printer successful-ok
192.168.1.102 - homeserver [02/Nov/2015:08:21:40 -0600] "POST /admin HTTP/1.1" 200 2662 - -
localhost - - [02/Nov/2015:08:21:54 -0600] "POST /jobs HTTP/1.1" 200 145 Restart-Job successful-ok
192.168.1.102 - homeserver [02/Nov/2015:08:22:32 -0600] "POST /admin HTTP/1.1" 200 158 - -
localhost - - [02/Nov/2015:08:22:33 -0600] "PUT /admin/conf/cupsd.conf HTTP/1.1" 401 0 - -
localhost - homeserver [02/Nov/2015:08:22:33 -0600] "PUT /admin/conf/cupsd.conf HTTP/1.1" 201 3135 - -
192.168.1.102 - homeserver [02/Nov/2015:08:22:32 -0600] "POST /admin HTTP/1.1" 200 2472 - -
localhost - - [02/Nov/2015:08:25:47 -0600] "POST /printers/samsung HTTP/1.1" 200 418 Print-Job successful-ok
192.168.1.102 - homeserver [02/Nov/2015:08:26:31 -0600] "POST /admin/ HTTP/1.1" 200 62 - -
192.168.1.102 - homeserver [02/Nov/2015:08:26:31 -0600] "POST /admin/ HTTP/1.1" 200 10697 - -

D [02/Nov/2015:08:26:38 -0600] [Client 17] Sending file.
D [02/Nov/2015:08:26:38 -0600] cupsd is not idle any more, canceling shutdown.
D [02/Nov/2015:08:26:38 -0600] [Client 17] cupsdWriteClient error=0, used=0, state=HTTP_STATE_GET_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=3784, response=(nil)(), pipe_pid=0, file=18
D [02/Nov/2015:08:26:38 -0600] cupsd is not idle any more, canceling shutdown.
D [02/Nov/2015:08:26:38 -0600] [Client 17] cupsdWriteClient error=0, used=0, state=HTTP_STATE_GET_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=1736, response=(nil)(), pipe_pid=0, file=18
D [02/Nov/2015:08:26:38 -0600] [Client 17] Waiting for request.
D [02/Nov/2015:08:26:38 -0600] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [02/Nov/2015:08:26:38 -0600] cupsd is not idle any more, canceling shutdown.
D [02/Nov/2015:08:26:38 -0600] [Client 17] GET /images/cups-icon.png HTTP/1.1
D [02/Nov/2015:08:26:38 -0600] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [02/Nov/2015:08:26:39 -0600] [Client 17] Authorized as homeserver using Basic
D [02/Nov/2015:08:26:39 -0600] [Client 17] Sending file.
D [02/Nov/2015:08:26:39 -0600] cupsd is not idle any more, canceling shutdown.
D [02/Nov/2015:08:26:39 -0600] [Client 17] cupsdWriteClient error=0, used=0, state=HTTP_STATE_GET_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=4888, response=(nil)(), pipe_pid=0, file=18
D [02/Nov/2015:08:26:39 -0600] cupsd is not idle any more, canceling shutdown.
D [02/Nov/2015:08:26:39 -0600] [Client 17] cupsdWriteClient error=0, used=0, state=HTTP_STATE_GET_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=2840, response=(nil)(), pipe_pid=0, file=18
D [02/Nov/2015:08:26:39 -0600] cupsd is not idle any more, canceling shutdown.
D [02/Nov/2015:08:26:39 -0600] [Client 17] cupsdWriteClient error=0, used=0, state=HTTP_STATE_GET_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=792, response=(nil)(), pipe_pid=0, file=18
D [02/Nov/2015:08:26:39 -0600] [Client 17] Waiting for request.
D [02/Nov/2015:08:26:39 -0600] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [02/Nov/2015:08:26:39 -0600] cupsd is not idle any more, canceling shutdown.
D [02/Nov/2015:08:26:40 -0600] cupsd is not idle any more, canceling shutdown.
D [02/Nov/2015:08:31:37 -0600] [Client 17] HTTP_STATE_WAITING Closing on EOF
D [02/Nov/2015:08:31:37 -0600] [Client 17] Closing connection.
D [02/Nov/2015:08:31:37 -0600] SSL shutdown successful!
D [02/Nov/2015:08:31:37 -0600] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [02/Nov/2015:08:31:37 -0600] [Client 17] Waiting for socket close.
D [02/Nov/2015:08:31:37 -0600] Report: clients=1
D [02/Nov/2015:08:31:37 -0600] Report: jobs=3
D [02/Nov/2015:08:31:37 -0600] Report: jobs-active=0
D [02/Nov/2015:08:31:37 -0600] Report: printers=1
D [02/Nov/2015:08:31:37 -0600] Report: stringpool-string-count=3181
D [02/Nov/2015:08:31:37 -0600] Report: stringpool-alloc-bytes=6808
D [02/Nov/2015:08:31:37 -0600] Report: stringpool-total-bytes=55504
D [02/Nov/2015:08:31:37 -0600] cupsd is not idle any more, canceling shutdown.
D [02/Nov/2015:08:31:37 -0600] [Client 17] HTTP_STATE_WAITING Closing on EOF
D [02/Nov/2015:08:31:37 -0600] [Client 17] Closing connection.
D [02/Nov/2015:08:31:37 -0600] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [02/Nov/2015:08:31:37 -0600] cupsd is not idle any more, canceling shutdown.
D [02/Nov/2015:08:31:38 -0600] cupsd is not idle any more, canceling shutdown.


I configured the samba as well. Below configuration file:

root@homeserver:/var/log/samba# cat /etc/samba/smb.conf
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic
# errors.


#======================= Global Settings =======================


[global]


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


[printers]
   comment = All Printers
   browseable = yes
   load printers = yes
   printing cups = yes
   printcap name = cups
   use client driver = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin



Some logs from samba:

root@homeserver:/var/log/samba# cat log.romek
[2015/11/02 04:23:40.924095,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+",)
[2015/11/02 04:23:40.927371,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\:",)
[2015/11/02 04:25:50.993316,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+",)
[2015/11/02 04:25:50.996878,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+:",)
[2015/11/02 04:26:06.924922,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+:",)
[2015/11/02 04:26:06.928337,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+:",)
[2015/11/02 04:27:30.553614,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+:",)
[2015/11/02 04:27:30.557097,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+:",)
[2015/11/02 04:28:57.038374,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+:",)
[2015/11/02 04:28:57.041690,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+:",)
[2015/11/02 04:35:33.447792,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+:",)
[2015/11/02 04:35:33.451210,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+:",)
[2015/11/02 04:35:52.619373,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+:",)
[2015/11/02 04:35:52.622950,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+:",)
[2015/11/02 05:57:33.514663,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+:",)
[2015/11/02 05:57:33.537319,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+:",)
[2015/11/02 05:57:42.316373,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+:",)
[2015/11/02 05:57:42.319891,  0] ../source3/param/loadparm.c:4346(process_usershare_file)
  process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+:",)







Are you Guys able to help me ? Whyh it is like this ?

---

### Post by TheFu on 2015-11-02
By default, CUPS only works for the localhost.  You have to allow it to talk on the network.

Inside: /etc/cups/cupsd.conf  -  add or fix  the "listen"
Listen 172.22.22.4:631

Put in your static IP of the cups server and restart the cupsd service.

---

