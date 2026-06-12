---
title: "Re: Linux client can not browse Samba shares"
date: 2015-12-17
forum: Networking &amp; Wireless
---

### Post by gararda on 2015-12-17
I have a samba server sharing folders that is working fine. Other Linux and Windows clients access the shares without problem in the same network and IP subnet.
I have installed a new Linux client with ubuntu 14.04, but is not capable to browse samba shares. I tested all, and it seems to be configured correctly.

**1 - client ubuntu version**
```

**[COLOR=#0000cd]lsb_release -a[/COLOR]**
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty

```

[B]2 - conectivity with the server by IP and name
[/B]```

**[COLOR=#0000cd]ping 192.168.12.1[/COLOR]**
PING 192.168.12.1 (192.168.12.1) 56(84) bytes of data.
64 bytes from 192.168.12.1: icmp_seq=1 ttl=64 time=0.460 ms
64 bytes from 192.168.12.1: icmp_seq=2 ttl=64 time=0.428 ms
^C
--- 192.168.12.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.428/0.444/0.460/0.016 ms



[COLOR=#0000cd]**ping servidor**[/COLOR]
PING servidor (192.168.12.1) 56(84) bytes of data.
64 bytes from servidor.liberico.com (192.168.12.1): icmp_seq=1 ttl=64 time=0.386 ms
64 bytes from servidor.liberico.com (192.168.12.1): icmp_seq=2 ttl=64 time=0.361 ms
64 bytes from servidor.liberico.com (192.168.12.1): icmp_seq=3 ttl=64 time=0.316 ms
^C
--- servidor ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.316/0.354/0.386/0.032 ms

```

[B]3 - testparm seems to be OK

[/B]```

testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
[COLOR=#006400]Loaded services file OK.[/COLOR]
Server role: [COLOR=#006400]ROLE_STANDALONE[/COLOR]
[global]
        workgroup = [COLOR=#006400]LIBERICO[/COLOR]
        server string = %h server (Samba, Ubuntu)
        server role = standalone server
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        [COLOR=#006400]name resolve order = lmhosts, wins, bcast, host[/COLOR]
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb


[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        print ok = Yes
        browseable = No


[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

```

**4 - List shares on the server by smbclient command**
I can list de shares in the server by server name and by IP

```

[COLOR=#0000cd]**smbclient -L 192.168.12.1 -U dani.gg**[/COLOR]
Enter dani.gg's password: 
[COLOR=#006400]Domain=[LIBERICO] OS=[Unix] Server=[Samba 4.1.10][/COLOR]
[COLOR=#006400]
[/COLOR]
[COLOR=#006400]        Sharename       Type      Comment[/COLOR]
[COLOR=#006400]        ---------       ----      -------[/COLOR]
[COLOR=#006400]        sysvol          Disk      [/COLOR]
[COLOR=#006400]        luiscarlos.cm   Disk      luiscarlos.cm[/COLOR]
[COLOR=#006400]        silvia.mo       Disk      silvia.mo[/COLOR]
[COLOR=#006400]        Incidencias-Resueltas Disk      Incidencias-Resueltas[/COLOR]
[COLOR=#006400]        javier.gs       Disk      javier.gs[/COLOR]
[COLOR=#006400]        gabriel.ms      Disk      gabriel.ms[/COLOR]
[COLOR=#006400]        natalia.ac      Disk      natalia.ac[/COLOR]
[COLOR=#006400]        teresa.gr       Disk      teresa.gr[/COLOR]
[COLOR=#006400]        raquel.em       Disk      raquel.em[/COLOR]
[COLOR=#006400]        teresa.dm       Disk      teresa.dm[/COLOR]
[COLOR=#006400]        laura.rc        Disk      laura.rc[/COLOR]
[COLOR=#006400]        Incidencias-Pendientes Disk      Incidencias-Pendientes[/COLOR]
[COLOR=#006400]        Recursos-TIC    Disk      Recursos-TIC[/COLOR]
[COLOR=#006400]        miguelangel.sm  Disk      miguelangel.sm[/COLOR]
[COLOR=#006400]        Biblioteca      Disk      Biblioteca[/COLOR]
[COLOR=#006400]        elena.ga        Disk      elena.ga[/COLOR]
[COLOR=#006400]        julian.dc       Disk      julian.dc[/COLOR]
[COLOR=#006400]        fanny.al        Disk      fanny.al[/COLOR]
[COLOR=#006400]        TIC             Disk      TIC[/COLOR]
[COLOR=#006400]        rosa.mf         Disk      rosa.mf[/COLOR]
[COLOR=#006400]        carlota.pm      Disk      carlota.pm[/COLOR]
[COLOR=#006400]        isabel.on       Disk      isabel.on[/COLOR]
[COLOR=#006400]        victor.mp       Disk      victor.mp[/COLOR]
[COLOR=#006400]        esther.rr       Disk      esther.rr[/COLOR]
[COLOR=#006400]        Administracion  Disk      Administracion[/COLOR]
[COLOR=#006400]        fernando.rp     Disk      fernando.rp[/COLOR]
[COLOR=#006400]        ana.ra          Disk      ana.ra[/COLOR]
[COLOR=#006400]        luis.lt         Disk      luis.lt[/COLOR]
[COLOR=#006400]        IPC$            IPC       IPC Service (Zentyal Server)[/COLOR]
Domain=[LIBERICO] OS=[Unix] Server=[Samba 4.1.10]


        Server               Comment
        ---------            -------
        SERVIDOR             Zentyal Server


        Workgroup            Master
        ---------            -------
        AULAMAX              PEREZGALDOS
        LIBERICO        


[COLOR=#0000cd]**smbclient -L servidor -U dani.gg**[/COLOR]
Enter dani.gg's password: 
[COLOR=#006400]Domain=[LIBERICO] OS=[Unix] Server=[Samba 4.1.10][/COLOR]
[COLOR=#006400]
[/COLOR]
[COLOR=#006400]        Sharename       Type      Comment[/COLOR]
[COLOR=#006400]        ---------       ----      -------[/COLOR]
[COLOR=#006400]        sysvol          Disk      [/COLOR]
[COLOR=#006400]        luiscarlos.cm   Disk      luiscarlos.cm[/COLOR]
[COLOR=#006400]        silvia.mo       Disk      silvia.mo[/COLOR]
[COLOR=#006400]        Incidencias-Resueltas Disk      Incidencias-Resueltas[/COLOR]
[COLOR=#006400]        javier.gs       Disk      javier.gs[/COLOR]
[COLOR=#006400]        gabriel.ms      Disk      gabriel.ms[/COLOR]
[COLOR=#006400]        natalia.ac      Disk      natalia.ac[/COLOR]
[COLOR=#006400]        teresa.gr       Disk      teresa.gr[/COLOR]
[COLOR=#006400]        raquel.em       Disk      raquel.em[/COLOR]
[COLOR=#006400]        teresa.dm       Disk      teresa.dm[/COLOR]
[COLOR=#006400]        laura.rc        Disk      laura.rc[/COLOR]
[COLOR=#006400]        Incidencias-Pendientes Disk      Incidencias-Pendientes[/COLOR]
[COLOR=#006400]        Recursos-TIC    Disk      Recursos-TIC[/COLOR]
[COLOR=#006400]        miguelangel.sm  Disk      miguelangel.sm[/COLOR]
[COLOR=#006400]        Biblioteca      Disk      Biblioteca[/COLOR]
[COLOR=#006400]        elena.ga        Disk      elena.ga[/COLOR]
[COLOR=#006400]        julian.dc       Disk      julian.dc[/COLOR]
[COLOR=#006400]        fanny.al        Disk      fanny.al[/COLOR]
[COLOR=#006400]        TIC             Disk      TIC[/COLOR]
[COLOR=#006400]        rosa.mf         Disk      rosa.mf[/COLOR]
[COLOR=#006400]        carlota.pm      Disk      carlota.pm[/COLOR]
[COLOR=#006400]        isabel.on       Disk      isabel.on[/COLOR]
[COLOR=#006400]        victor.mp       Disk      victor.mp[/COLOR]
[COLOR=#006400]        esther.rr       Disk      esther.rr[/COLOR]
[COLOR=#006400]        Administracion  Disk      Administracion[/COLOR]
[COLOR=#006400]        fernando.rp     Disk      fernando.rp[/COLOR]
[COLOR=#006400]        ana.ra          Disk      ana.ra[/COLOR]
[COLOR=#006400]        luis.lt         Disk      luis.lt[/COLOR]
[COLOR=#006400]        IPC$            IPC       IPC Service (Zentyal Server)[/COLOR]
Domain=[LIBERICO] OS=[Unix] Server=[Samba 4.1.10]


        Server               Comment
        ---------            -------
        SERVIDOR             Zentyal Server


        Workgroup            Master
        ---------            -------
        AULAMAX              PEREZGALDOS
        LIBERICO                 

```

**5 - smb.conf file**
I can not see problems in the configuration of [B]smb.conf
[/B]```

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
   workgroup = [COLOR=#006400]**liberico**[/COLOR]
   netbios name = [COLOR=#006400]**m8-homero**[/COLOR]
# server string is the equivalent of the NT Description field
        server string = %h server (Samba, Ubuntu)


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no
**[COLOR=#006400]name resolve order = lmhosts wins bcast host[/COLOR]**


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = 192.168.12.1


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

```

**6 - smbtree command fails**
smbtree dot not show the shares in the server "servidor"
```

[COLOR=#0000cd]**smbtree -d3**[/COLOR]
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth1 ip=192.168.12.124 bcast=192.168.12.255 netmask=255.255.255.0
Enter root's password: 
resolve_lmhosts: Attempting lmhosts lookup for name LIBERICO<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name LIBERICO<0x1d>
[COLOR=#ff0000]**name_resolve_bcast: Attempting broadcast lookup for name LIBERICO<0x1d>**[/COLOR]
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb7e9e160] mpx_fde[(nil)] fd[7] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name LIBERICO<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name LIBERICO<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
[COLOR=#ff0000]**name_resolve_bcast: Attempting broadcast lookup for name LIBERICO<0x1b>**[/COLOR]
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb7e9e168] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.12.50 ( 10.0.101.4 192.168.12.50 10.0.100.3 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0xb7e9d878] mpx_fde[(nil)] fd[7] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.12.50 ( 10.0.101.4 192.168.12.50 10.0.100.3 )
Connecting to 192.168.12.50 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
WORKGROUP
Connecting to 192.168.12.50 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
        \\ESTHER-PC      
resolve_lmhosts: Attempting lmhosts lookup for name ESTHER-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name ESTHER-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name ESTHER-PC<0x20>
Got a positive name query response from 192.168.12.50 ( 10.0.101.4 192.168.12.50 10.0.100.3 )
Connecting to 192.168.12.50 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure

[COLOR=#0000cd]**smbtree**[/COLOR]
Enter root's password: 
AULAMAX
        \\M8-HOMERO                     m8-homero server (Samba, Ubuntu)
                \\M8-HOMERO\Canon-imageRunner-2200      Canon imageRunner 2200
                \\M8-HOMERO\print$              Printer Drivers

```

The problem seems to be there in the "smbtree -d3" command:
[B][COLOR=#0000cd]name_resolve_bcast: Attempting broadcast lookup for name LIBERICO<0x1b>
[/COLOR][/B]Why 192.168.12.1 (servidor) do not response to broadcast if nmblookup command works fine?

```

[COLOR=#0000cd]**nmblookup -S servidor**[/COLOR]
192.168.12.1 servidor<00>
Looking up status of 192.168.12.1
        SERVIDOR        <00> -         B <ACTIVE> 
        SERVIDOR        <03> -         B <ACTIVE> 
        SERVIDOR        <20> -         B <ACTIVE> 
        ..__MSBROWSE__. <01> - <GROUP> B <ACTIVE> 
        LIBERICO        <00> - <GROUP> B <ACTIVE> 
        LIBERICO        <1c> -         B <ACTIVE> 
        LIBERICO        <1d> -         B <ACTIVE> 
        LIBERICO        <1e> - <GROUP> B <ACTIVE> 

[COLOR=#0000cd]**nmblookup -S liberico**[/COLOR]
192.168.12.124 liberico<00>
Looking up status of 192.168.12.124
        M8-HOMERO       <00> -         B <ACTIVE> 
        M8-HOMERO       <03> -         B <ACTIVE> 
        M8-HOMERO       <20> -         B <ACTIVE> 
        ..__MSBROWSE__. <01> - <GROUP> B <ACTIVE> 
        LIBERICO        <00> - <GROUP> B <ACTIVE> 
        LIBERICO        <1d> -         B <ACTIVE> 
        LIBERICO        <1e> - <GROUP> B <ACTIVE> 


        MAC Address = 00-00-00-00-00-00


192.168.12.1 liberico<00>
Looking up status of 192.168.12.1
        SERVIDOR        <00> -         B <ACTIVE> 
        SERVIDOR        <03> -         B <ACTIVE> 
        SERVIDOR        <20> -         B <ACTIVE> 
        ..__MSBROWSE__. <01> - <GROUP> B <ACTIVE> 
        LIBERICO        <00> - <GROUP> B <ACTIVE> 
        LIBERICO        <1c> -         B <ACTIVE> 
        LIBERICO        <1d> -         B <ACTIVE> 
        LIBERICO        <1e> - <GROUP> B <ACTIVE> 


        MAC Address = 00-00-00-00-00-00


```

Also, no problem with samba processes:

```

[COLOR=#0000cd]**/etc/init.d/samba status**[/COLOR]
 * nmbd is running
 * smbd is running

```

Can any one give me some help on how to troubleshoot and get this working? Please¡¡¡¡ :?:?


Cheers

I can access to the shares vía cli

```

[COLOR=#0000cd]**smbclient --user=dani.gg //192.168.12.1/TIC**[/COLOR]
Enter dani.gg's password: 
Domain=[LIBERICO] OS=[Unix] Server=[Samba 4.1.10]
smb: \> ls
  .                                   D        0  Sat Jul  4 19:39:33 2015
  ..                                  D        0  Sat Jul  4 19:39:34 2015


                64000 blocks of size 8192. 63998 blocks available
smb: \> 
[COLOR=#0000cd][/COLOR][COLOR=#0000cd]**smbclient --user=dani.gg //servidor/TIC**[/COLOR]
Enter dani.gg's password: 
Domain=[LIBERICO] OS=[Unix] Server=[Samba 4.1.10]
smb: \> ls
  .                                   D        0  Sat Jul  4 19:39:33 2015
  ..                                  D        0  Sat Jul  4 19:39:34 2015


                64000 blocks of size 8192. 63998 blocks available



```

Also, no problem with local FW:

```

[COLOR=#0000cd]**sudo iptables -L**[/COLOR]
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

```

Can be thar te problem is a windows machine acting as a Master Browser?

```

[COLOR=#0000cd]**nmblookup -M -- -**[/COLOR]
192.168.12.50 __MSBROWSE__<01>   // IP of the windows machine in the same IP subnet
192.168.12.126 __MSBROWSE__<01> // itself
10.0.101.4 __MSBROWSE__<01>  // IP of the windows machine in another IP subnet
10.0.100.3 __MSBROWSE__<01>  // IP of the windows machine in another IP subnet

```

I have configured the server 192.168.12.1 to be the WINS server, but is not responding....
The server is a Zentyal 3.2

---

### Post by gararda on 2015-12-17
New edit,

The following is showed in the client log.nmbd file
```

[2015/12/17 22:45:04,  0] ../source3/nmbd/nmbd_nameregister.c:138(register_name_response)
  register_name_response: WINS server at IP 192.168.12.1 rejected our name registration of LIBERICO<00> IP 192.168.12.124 with error
 code 1.
[2015/12/17 22:45:04,  0] ../source3/nmbd/nmbd_workgroupdb.c:220(fail_register)
  fail_register: Failed to register name LIBERICO<00> on subnet UNICAST_SUBNET.
[2015/12/17 22:45:04,  0] ../source3/nmbd/nmbd_namelistdb.c:320(standard_fail_register)
  standard_fail_register: Failed to register/refresh name LIBERICO<00> on subnet UNICAST_SUBNET
[2015/12/17 22:45:04,  0] ../source3/nmbd/nmbd_nameregister.c:138(register_name_response)
  register_name_response: WINS server at IP 192.168.12.1 rejected our name registration of LIBERICO<1e> IP 192.168.12.124 with error
 code 1.
[2015/12/17 22:45:04,  0] ../source3/nmbd/nmbd_workgroupdb.c:220(fail_register)
  fail_register: Failed to register name LIBERICO<1e> on subnet UNICAST_SUBNET.
[2015/12/17 22:45:04,  0] ../source3/nmbd/nmbd_namelistdb.c:320(standard_fail_register)
  standard_fail_register: Failed to register/refresh name LIBERICO<1e> on subnet UNICAST_SUBNET
[2015/12/17 23:05:27,  0] ../source3/nmbd/nmbd_nameregister.c:138(register_name_response)
  register_name_response: WINS server at IP 192.168.12.1 rejected our name registration of M8-HOMERO<00> IP 192.168.12.124 with erro
r code 1.
[2015/12/17 23:05:27,  0] ../source3/nmbd/nmbd_namelistdb.c:320(standard_fail_register)
  standard_fail_register: Failed to register/refresh name M8-HOMERO<00> on subnet UNICAST_SUBNET
[2015/12/17 23:05:27,  0] ../source3/nmbd/nmbd_nameregister.c:138(register_name_response)
  register_name_response: WINS server at IP 192.168.12.1 rejected our name registration of M8-HOMERO<03> IP 192.168.12.124 with erro
r code 1.
[2015/12/17 23:05:27,  0] ../source3/nmbd/nmbd_namelistdb.c:320(standard_fail_register)
  standard_fail_register: Failed to register/refresh name M8-HOMERO<03> on subnet UNICAST_SUBNET
[2015/12/17 23:05:27,  0] ../source3/nmbd/nmbd_nameregister.c:138(register_name_response)
  register_name_response: WINS server at IP 192.168.12.1 rejected our name registration of M8-HOMERO<20> IP 192.168.12.124 with erro
r code 1.
[2015/12/17 23:05:27,  0] ../source3/nmbd/nmbd_namelistdb.c:320(standard_fail_register)
  standard_fail_register: Failed to register/refresh name M8-HOMERO<20> on subnet UNICAST_SUBNET

```

and this is showed in the WINS server
```

  process_name_registration_request: unicast name registration request received for name LIBERICO<00> from IP 192.168.12.124 on subnet UNICAST_SUBNET. Error - should be sent to WINS server
  process_name_registration_request: unicast name registration request received for name LIBERICO<1e> from IP 192.168.12.124 on subnet UNICAST_SUBNET. Error - should be sent to WINS server

```

---

### Post by gararda on 2015-12-23
The WINS check was marked in my Zentyal configuration to send the Zentyal IP the WINS server for this IP range, this not activate my Ubuntu Zentyal as a WINS server. I make the fowolling:

- Create a new stub

```

mkdir -p /etc/zentyal/stubs/samba
cp  /usr/share/zentyal/stubs/samba/smb.conf.mas /etc/zentyal/stubs/samba/

```

Add the following code at [global] level to: /etc/zentyal/stubs/samba/smb.conf.mas
```

    domain master = yes
    wins support = yes
    local master = yes
    os level = 255
    preferred master = yes

```

Hope this help somoeone.

Regard.

---

