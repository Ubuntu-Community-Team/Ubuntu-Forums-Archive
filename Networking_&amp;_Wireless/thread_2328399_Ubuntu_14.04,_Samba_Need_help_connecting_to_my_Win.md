---
title: "Ubuntu 14.04, Samba: Need help connecting to my Windows network and printer"
date: 2016-06-20
forum: Networking &amp; Wireless
---

### Post by Don_Tai on 2016-06-20
I have a windows network with a printer attached to a windows machine. I also have my ubuntu 14.04 laptop, 2 years old. I used to be able to print to the windows network without problem, but after a minor ubuntu update I now cannot figure out how to get Windows printing and networking capability back.

My windows system is still working, login credentials all work, the printer works. From Ubuntu 14.04 I can browse the windows network, see all the windows PCs, and even drill down to a windows directory on a shared windows PC, but when I try to access the lowest directory to see files I get promted for my login credentials. Even with credentials I use on other windows machines, which work, I get an "nt_status_logon_failure" error message. I have 2 printers that were installed on ubuntu 14.04 and used to work. Now when I try to add a new printer, network printer, Windows Printer via Samba, I can browse to my printer and select it, but when I verify with proper credentials, which work on Windws machines, I get Print Share inaccessible. The printer is attached to windows PC 192.168.1.104, called "Printer".

I've read a lot of threads on the subject, but I am stuck and need help.

smbtree command
```
don-w510-u@don-TP-W510-u:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface wlan0 ip=192.168.1.107 bcast=192.168.1.255 netmask=255.255.255.0
Enter don-w510-u's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name TAI<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name TAI<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name TAI<0x1d>
Got a positive name query response from 192.168.1.107 ( 192.168.1.107 )
Connecting to 192.168.1.107 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'spnego' registered
GENSEC backend 'schannel' registered
GENSEC backend 'naclrpc_as_system' registered
GENSEC backend 'sasl-EXTERNAL' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'ntlmssp_resume_ccache' registered
GENSEC backend 'http_basic' registered
GENSEC backend 'http_ntlm' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
TAI
resolve_lmhosts: Attempting lmhosts lookup for name TAI<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name TAI<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name TAI<0x1d>
Got a positive name query response from 192.168.1.107 ( 192.168.1.107 )
Connecting to 192.168.1.107 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
    \\PRINTER                
resolve_lmhosts: Attempting lmhosts lookup for name PRINTER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PRINTER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PRINTER<0x20>
resolve_hosts: getaddrinfo failed for name PRINTER [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name PRINTER<0x20>
Got a positive name query response from 192.168.1.104 ( 192.168.1.104 )
Connecting to 192.168.1.104 at port 445
Doing spnego session setup (blob length=0)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=0)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
        \\PRINTER\C$                 Default share
        \\PRINTER\ADMIN$             Remote Admin
        \\PRINTER\DeskJet932c        HP Deskjet 932c
        \\PRINTER\P2-DATA            
        \\PRINTER\D                  13G on Printer
        \\PRINTER\DATA               
        \\PRINTER\print$             Printer Drivers
        \\PRINTER\D$                 Default share
        \\PRINTER\IPC$               Remote IPC
        \\PRINTER\p1005              HP LaserJet P1005
    \\MICHAELA-PC            
resolve_lmhosts: Attempting lmhosts lookup for name MICHAELA-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name MICHAELA-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name MICHAELA-PC<0x20>
resolve_hosts: getaddrinfo failed for name MICHAELA-PC [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name MICHAELA-PC<0x20>
Got a positive name query response from 192.168.1.102 ( 192.168.1.102 )
Connecting to 192.168.1.102 at port 445
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
        \\MICHAELA-PC\Users              
        \\MICHAELA-PC\IPC$               Remote IPC
        \\MICHAELA-PC\Data               
        \\MICHAELA-PC\C$                 Default share
        \\MICHAELA-PC\ADMIN$             Remote Admin
    \\KARINA                 Karina's computer
resolve_lmhosts: Attempting lmhosts lookup for name KARINA<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name KARINA<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name KARINA<0x20>
resolve_hosts: getaddrinfo failed for name KARINA [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name KARINA<0x20>
    \\DON-TP-W510-U          don-TP-W510-u server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name DON-TP-W510-U<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name DON-TP-W510-U<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name DON-TP-W510-U<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
        \\DON-TP-W510-U\HP-Deskjet-932c    HP Deskjet 932c
        \\DON-TP-W510-U\HP-LaserJet-P1005    HP LaserJet P1005
        \\DON-TP-W510-U\IPC$               IPC Service (don-TP-W510-u server (Samba, Ubuntu))
  \\DON-TP-W510-U\print$             Printer Drivers

```

smbclient command
```
don-w510-u@don-TP-W510-u:~$ smbclient -L 192.168.1.104
WARNING: The "syslog" option is deprecated
Enter don-w510-u's password: 
session setup failed: NT_STATUS_LOGON_FAILURE
don-w510-u@don-TP-W510-u:~$ 
```

I get this "NT_STATUS_LOGON_FAILURE" with the smbclient command, and this is whereI am stuck.

/etc/samba/smb.conf, reverted to original. samba version: Samba Server Configuration Tool 1.2.63
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
    workgroup = tai

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
;    passdb backend = tdbsam

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
;    usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
    username map = /etc/samba/smbusers
#    security = domain
    security = user
;    encrypt passwords = yes
;    guest ok = no
;    guest account = nobody

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
    browseable = no
    path = /var/spool/samba
    printable = yes
;    guest ok = no
;    read only = yes
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin
```

I tried to change my workgroup name to all capitals but this made no difference, so I changed it back to original. I tried to change the security variable from security = user to security = domain to  but this made no difference, so I changed it back to original.

Whatever more info you need I can provide. Thanks in advance for any help.

---

### Post by Don_Tai on 2016-10-30
Upgraded to 16.04 and the problem persisted. Today I tracked down the problem: Windows NT does not support the higher security requirements of 14.04 and 16.04. To log into Win NT and older systems add this to your smb.conf: client use spnego = no

[URL="https://ubuntuforums.org/showthread.php?t=2324318"]https://ubuntuforums.org/showthread.php?t=2324318

http://askubuntu.com/questions/763945/cant-connect-to-smb-share-after-upgrade-to-ubuntu-gnome-16-04[/URL]

This solved the problem immediately after a reboot. I was able to successfully login to the Windows server and print, just as I did under the early 14.04.

---

