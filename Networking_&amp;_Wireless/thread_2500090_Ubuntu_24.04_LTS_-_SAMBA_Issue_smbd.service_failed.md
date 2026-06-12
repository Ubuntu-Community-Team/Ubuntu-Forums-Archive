---
title: "Ubuntu 24.04 LTS - SAMBA Issue: smbd.service failed to start"
date: 2024-08-22
forum: Networking &amp; Wireless
---

### Post by flavaflute on 2024-08-22
Hi all,

I have just installed Ubuntu 24.04 and am trying to share a folder through SMB with my network.
However I am unable to as samba fails to start every single time. The goal is to share the content located in /mnt/12TB/ServerFolders

In my most recent attempt I performed the following steps:
1. Followed the official ubuntu [tutorial]("https://ubuntu.com/tutorials/install-and-configure-samba#1-overview")

2. The command whereis samba gives me the following:
```
samba: /usr/sbin/samba /usr/lib/x86_64-linux-gnu/samba /etc/samba /usr/libexec/samba /usr/share/samba /usr/share/man/man7/samba.7.gz /usr/share/man/man8/samba.8.gz
```

3. My etc/samba/smb.conf file:
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
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

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

# We want Samba to only log to /var/log/samba/log.{smbd,nmbd}.
# Append syslog@1 if you want important messages to be sent to syslog too.
   logging = file

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone server" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server

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
# The following settings only takes effect if 'server role = classic
# primary domain controller', 'server role = classic backup domain controller'
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
; add user script = /usr/sbin/useradd --create-home %u

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
;   idmap config * :              backend = tdb
;   idmap config * :              range   = 3000-7999
;   idmap config YOURDOMAINHERE : backend = tdb
;   idmap config YOURDOMAINHERE : range   = 100000-999999
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 means that usershare is disabled.
#   usershare max shares = 100

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
   browseable = no
   path = /var/tmp
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

[sambashare]
    comment = Samba on Ubuntu
    path = /mnt/12TB/ServerFolders
    read only = yes
    browsable = yes
```

4. I check the conf file with testparm:
```
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed by GnuTLS (e.g. NTLM as a compatibility fallback)

Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions

# Global parameters
[global]
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    usershare allow guests = Yes
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/tmp
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[sambashare]
    comment = Samba on Ubuntu
    path = /mnt/12TB/ServerFolders

```

5. Seems good too. However when I start the service with "sudo service smbd restart" I receive the following error:
```
Job for smbd.service failed because a fatal signal was delivered causing the control process to dump core.
See "systemctl status smbd.service" and "journalctl -xeu smbd.service" for details.

```

6. Output of "systemctl status smbd.service" 
```
systemctl status smbd.service
× smbd.service - Samba SMB Daemon
     Loaded: loaded (/usr/lib/systemd/system/smbd.service; enabled; preset: enabled)
     Active: failed (Result: core-dump) since Thu 2024-08-22 14:25:23 CEST; 8s ago
       Docs: man:smbd(8)
             man:samba(7)
             man:smb.conf(5)
    Process: 96495 ExecCondition=/usr/share/samba/is-configured smb (code=exited, status=0/SUCCESS)
    Process: 96498 ExecStart=/usr/sbin/smbd --foreground --no-process-group $SMBDOPTIONS (code=dumped, signal=SEGV)
   Main PID: 96498 (code=dumped, signal=SEGV)
        CPU: 35ms

Aug 22 14:25:22 Microserver systemd[1]: Starting smbd.service - Samba SMB Daemon...
Aug 22 14:25:22 Microserver (smbd)[96498]: smbd.service: Referenced but unset environment variable evaluates to an empty string>
Aug 22 14:25:23 Microserver systemd[1]: smbd.service: Main process exited, code=dumped, status=11/SEGV
Aug 22 14:25:23 Microserver systemd[1]: smbd.service: Failed with result 'core-dump'.
Aug 22 14:25:23 Microserver systemd[1]: Failed to start smbd.service - Samba SMB Daemon.

```

7. Lastly the output of "sudo service samba status"
```
[sudo] password for microserver: 
&#9675; samba-ad-dc.service - Samba AD Daemon
     Loaded: loaded (/usr/lib/systemd/system/samba-ad-dc.service; enabled; preset: enabled)
     Active: inactive (dead) (Result: exec-condition) since Thu 2024-08-22 13:51:25 CEST; 28min ago
  Condition: start condition unmet at Thu 2024-08-22 13:51:25 CEST; 28min ago
       Docs: man:samba(8)
             man:samba(7)
             man:smb.conf(5)
    Process: 89812 ExecCondition=/usr/share/samba/is-configured samba (code=exited, status=1/FAILURE)
        CPU: 34ms

Aug 22 13:51:25 Microserver systemd[1]: Starting samba-ad-dc.service - Samba AD Daemon...
Aug 22 13:51:25 Microserver systemd[1]: samba-ad-dc.service: Skipped due to 'exec-condition'.
Aug 22 13:51:25 Microserver systemd[1]: Condition check resulted in samba-ad-dc.service - Samba AD Daemon being skipped.

```

I have spent over 5 hours getting it to work and lost count in the amount of reinstalls. My result is this. Can anyone help me get this SMB share running?

Thanks in advance

---

### Post by currentshaft on 2024-08-22
/usr

---

### Post by flavaflute on 2024-08-22
microserver@Microserver:/usr/sbin$ smbd --foreground
Segmentation fault (core dumped)

A pop up appeared but as soon as I wanted to copy the contents of the crash I had to enter my sudo password which made the window dissapear.

There is no log for smdb, only nmbd has a log:
```
 [2024/08/22 13:51:24.477291,  0] source3/nmbd/nmbd.c:901(main)
  nmbd version 4.19.5-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2023
[2024/08/22 13:51:26.485334,  0] source3/nmbd/nmbd_mynames.c:104(my_name_register_failed)
  my_name_register_failed: Failed to register my name MICROSERVER<00> on subnet 192.168.1.122.
[2024/08/22 13:51:26.485383,  0] source3/nmbd/nmbd_namelistdb.c:319(standard_fail_register)
  standard_fail_register: Failed to register/refresh name MICROSERVER<00> on subnet 192.168.1.122

```

---

### Post by currentshaft on 2024-08-22
hoo

---

### Post by flavaflute on 2024-08-23
> **currentshaft said:**
> Is there a verbose flag to try passing? man smbd

If not, try running it with "sudo strace smbd"

man smbd wase useful as it shows the program can boot with various levels of logging. However it crashes before any logs are made so no luck there.

"sudo strace smbd" gave me this however:
[https://paste.ubuntu.com/p/XC7t5vKdjM/](https://paste.ubuntu.com/p/XC7t5vKdjM/)

The forum doesnt allow me to paste the code here directly unfortunately. Seems like there are missing files and folders. Could that be the issue?
If so, how do I fix that if I perform the installation procedure according to the official tutorial?

---

### Post by currentshaft on 2024-08-23
hey

---

### Post by flavaflute on 2024-08-29
I have solved the issue by reinstalling the system with Fedora 40. On that distro the install commands for SMB worked in one go. Still no clue what caused the issues on Ubuntu, maybe it is the hardware itself (HP Microserver Gen8).

---

