---
title: "smb problems"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by forgreatsource on 2007-06-17
hi everyone i had a smb server running and it was working fine.
i then followed this guide 
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

to get all the other shares in my place mounted.

now the problem is that i can see all the shares on other computers but when anyone trys to access my shares the error 

An error occurred while loading smb://source/MyFiles:
The file or folder smb://source/MyFiles does not exist.

it was working perfectly before i followed the above stated guide.

thanks

---

### Post by dmizer on 2007-06-17
please post the contents of: /etc/samba/smb.conf

also ... describe the rest of the computers in your network.  all windows? some windows some linux? what are their names?

---

### Post by forgreatsource on 2007-06-17
all computers are linux.
all are ubuntu.

```
[global]
    ; General server settings
    netbios name = Source
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

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
    path = /media/hdd2
    browseable = yes
    read only = yes
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = dream
    force group = dream

[upload]
    path = /media/hdd2/upload
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = dream
    force group = dream


```

---

### Post by dmizer on 2007-06-17
okay ... change this option:
```
wins support = yes
```
to:
```
wins support = no
```

second, you have "security = user" but your shares are listed as "guest ok = yes"
with "security = user" you should be using "guest ok = no"

if you want non-password protected shares, you should change:
```
security = user
```
to:
```
security = share
```

restart samba after making changes:
```
sudo /etc/init.d/samba restart
```
and see if you can get to your shares with your other machines.

also, have you installed firestarter on the server?  if so, that would block access to your samba shares.

---

### Post by forgreatsource on 2007-06-17
followed your advice but im still having the same problem.
all the guides i have followed are the ones in your sig.

and i don't have a firewall running on the server

---

### Post by dmizer on 2007-06-17
from one of your other computers, what happens if you run this command (make sure there is a folder in /media called "source"):
```
sudo mount -t cifs //Source/MyFiles /media/source -o guest,ro,iocharset=utf8,file_mode=0777,dir_mode=0777
```

---

### Post by forgreatsource on 2007-06-18
mount error 5 = Input/output error
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

i do appreciate the help you are giving.

it just seems my samba server is not running properly.

---

### Post by dmizer on 2007-06-19
sorry for my delay, i had to go out of town.

from one of the clients as well as the server, please post the contents of: /etc/hosts

also from one of the clients, please post the output of the following command:
```
smbtree
```
and:
```
ping source
```

---

### Post by p_quarles on 2007-06-19
You need to specify a netbios name. Linux machines won't be able to find the share unless that's on. Personally, I just use the internal IP address of the server. You can then mount it by going to Places > Connect to Server and then entering the IP address.

---

### Post by forgreatsource on 2007-06-19
to respond to p_quarles i do have a netbios name.
the server was running perfectly but stoped when i mounted the other network shares.

and in response to dmizer don't worry about the delay.

smbtree = 

```
WORKGROUP
        \\UBUNTU
                \\UBUNTU\IPC$                   IPC Service ()
                \\UBUNTU\music
                \\UBUNTU\MyFiles
                \\UBUNTU\DVD-ROM Drive
                \\UBUNTU\print$
        \\SOURCE
                \\SOURCE\IPC$                   IPC Service ()
                \\SOURCE\upload
                \\SOURCE\MyFiles
                \\SOURCE\print$

```

source is me.
while the ubuntu server is my roommates.
i currently have them mounted in folders in my media directory.


PING source (192.168.1.110) 56(84) bytes of data.
64 bytes from 192.168.1.110: icmp_seq=1 ttl=64 time=0.026 ms
64 bytes from 192.168.1.110: icmp_seq=2 ttl=64 time=0.043 ms
64 bytes from 192.168.1.110: icmp_seq=3 ttl=64 time=0.039 ms


my host files has

```
127.0.0.1	localhost
127.0.1.1	forgreat.phub.net.cable.rogers.com	forgreat

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by dmizer on 2007-06-19
do you have any success mounting this way:
```
sudo mount -t cifs //192.168.1.110/MyFiles /media/source -o guest,ro,iocharset=utf8,file_mode=0777,dir_mode=0777
```

---

### Post by gorgor_bay on 2007-06-19
I've got about the same problem: I can browse through al the windows LAN from my Ubuntu box, but they cannot access my network shares, they end up with the same error.

I've double checked my smb.conf, also opened Firestarter ports 137-139 & 445

smb.conf
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
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = LINUX
   netbios name = LEO-LAPTOP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = lmhosts host wins bcast

announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

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
;   security = user
    security = share	

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

[partage_reseau]
path = /home/leo/partage_reseau
guest ok = yes
create mask = 0644
directory mask = 0755
available = yes
browsable = yes
public = yes
writable = no
```

Here is the result of smbtree

```
$ smbtree
Password: 
WORKGROUP
SART
        \\ISIDORE        
                \\ISIDORE\Imprimante5           HP Color LaserJet 4600 PCL 6
                \\ISIDORE\C$                    Partage par défaut
                \\ISIDORE\ADMIN$                Administration à distance
                \\ISIDORE\D              
                \\ISIDORE\SharedDocs     
                \\ISIDORE\print$                Pilotes d'imprimantes
                \\ISIDORE\IPC$                  IPC distant
                \\ISIDORE\Imprimante4           HP Color LaserJet 4600 PS
                \\ISIDORE\Imprimante3           HP Mobile Printing PS
                \\ISIDORE\Imprimante2           Créé par installation personnalisée de Lexmark,30/01/2006 17:10:28
MSM_NT
        \\SCHTROUMPF     
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine SCHTROUMPF.  Error was NT_STATUS_ACCESS_DENIED
        \\PORTCATH                      PortCath
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine PORTCATH.  Error was NT_STATUS_ACCESS_DENIED
        \\PORTAMH                       PORTAMH
cli_start_connection: failed to connect to PORTAMH<20> (0.0.0.0)
        \\OUFTI                         OUFTI
                \\OUFTI\C$              Partage par défaut
                \\OUFTI\ADMIN$          Administration à distance
                \\OUFTI\SharedDocs     
                \\OUFTI\IPC$            IPC distant
        \\NAXOS2                        NAXOS2
cli_start_connection: failed to connect to NAXOS2<20> (0.0.0.0)
        \\MAQUOI                        MAQUOI
cli_start_connection: failed to connect to MAQUOI<20> (0.0.0.0)
        \\MACRO-MOUSSES  
cli_start_connection: failed to connect to MACRO-MOUSSES<20> (0.0.0.0)
        \\JEFF           
cli_start_connection: failed to connect to JEFF<20> (0.0.0.0)
        \\GOYA2          
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine GOYA2.  Error was NT_STATUS_ACCESS_DENIED
        \\FURBY                         Furby
cli_start_connection: failed to connect to FURBY<20> (0.0.0.0)
        \\BRAQUE         
cli_start_connection: failed to connect to BRAQUE<20> (0.0.0.0)
        \\BOSCH                         Spirou
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine BOSCH.  Error was NT_STATUS_ACCESS_DENIED
MSM_LABO
timeout connecting to 139.165.123.16:445
timeout connecting to 139.165.123.16:139
Error connecting to 139.165.123.16 (Opération déjà en cours)
cli_start_connection: failed to connect to 139.165.123.16<20> (139.165.123.16)
timeout connecting to 139.165.123.16:445
timeout connecting to 139.165.123.16:139
Error connecting to 139.165.123.16 (Opération déjà en cours)
cli_start_connection: failed to connect to LABO07<20> (139.165.123.16)
MSM
        \\CAROLINE       
                \\CAROLINE\Imprimante6          Crée Adobe PDF
                \\CAROLINE\Imprimante5          HP Color LaserJet 4600 PCL 6
                \\CAROLINE\htdocs         
                \\CAROLINE\C$                   Partage par défaut
                \\CAROLINE\ADMIN$               Administration à distance
                \\CAROLINE\Imprimante           Microsoft Office Document Image Writer
                \\CAROLINE\SharedDocs     
                \\CAROLINE\print$               Pilotes d'imprimantes
                \\CAROLINE\D$                   Partage par défaut
                \\CAROLINE\IPC$                 IPC distant
                \\CAROLINE\Imprimante4          HP Color LaserJet 4600 PS
                \\CAROLINE\Imprimante3          Créé par installation personnalisée de Lexmark,06/03/2006 15:26:16
                \\CAROLINE\Imprimante2          Créé par installation personnalisée de Lexmark,06/03/2006 15:26:16
MSHOME
        \\YOUR-3A81449010
cli_start_connection: failed to connect to YOUR-3A81449010<20> (0.0.0.0)
        \\RENEE                         Le cerveau de Renée
                \\RENEE\Imprimante5     HP Color LaserJet 4600 PCL 6
                \\RENEE\C$              Partage par défaut
                \\RENEE\ADMIN$          Administration à distance
                \\RENEE\Imprimante      Microsoft Office Document Image Writer
                \\RENEE\SharedDocs     
                \\RENEE\print$          Pilotes d'imprimantes
                \\RENEE\IPC$            IPC distant
                \\RENEE\Imprimante4     HP Color LaserJet 4600 PS
                \\RENEE\Imprimante3     Lexmark T630
                \\RENEE\Imprimante2     Lexmark T630 PS3
        \\PC-VINCENT                    PC-VINCENT
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine PC-VINCENT.  Error was NT_STATUS_ACCESS_DENIED
        \\LGIH17         
M&S
        \\QUICK                         QUICK
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine QUICK.  Error was NT_STATUS_ACCESS_DENIED
        \\OBELIX                        OBELIX
                \\OBELIX\Imprimante5            Crée Adobe PDF
                \\OBELIX\BJSJBDIR$              Job directory path for Batch Job Server
                \\OBELIX\C$                     Partage par défaut
                \\OBELIX\ADMIN$                 Administration à distance
                \\OBELIX\5.2            
                \\OBELIX\Progs          
                \\OBELIX\Imprimante             Créé par installation personnalisée de Lexmark,18/10/2005 16:08:32
                \\OBELIX\SharedDocs     
                \\OBELIX\print$                 Pilotes d'imprimantes
                \\OBELIX\D$                     Partage par défaut
                \\OBELIX\IPC$                   IPC distant
                \\OBELIX\Imprimante4            HP Color LaserJet 4600 PCL 6
                \\OBELIX\Imprimante3            HP Color LaserJet 4600 PS
                \\OBELIX\Imprimante2            Créé par installation personnalisée de Lexmark,18/10/2005 16:08:32
                \\OBELIX\E$                     Partage par défaut
        \\NATACHA                       Natacha
cli_start_connection: failed to connect to NATACHA<20> (0.0.0.0)
        \\MSMSR07        
                \\MSMSR07\C$                    Partage par défaut
                \\MSMSR07\ADMIN$                Administration à distance
                \\MSMSR07\Fonder         
                \\MSMSR07\Bouffioux      
                \\MSMSR07\Zhang          
                \\MSMSR07\HAUSOUL        
                \\MSMSR07\HPLaserJ              HP LaserJet 2100 Series PS
                \\MSMSR07\Users          
                \\MSMSR07\Tedoldi        
                \\MSMSR07\Boisso         
                \\MSMSR07\Lequesne       
                \\MSMSR07\Warnotte       
                \\MSMSR07\Gens           
                \\MSMSR07\Plumier        
                \\MSMSR07\Lemaire        
                \\MSMSR07\print$                Pilotes d'imprimantes
                \\MSMSR07\D$                    Partage par défaut
                \\MSMSR07\IPC$                  IPC distant
                \\MSMSR07\Henrard        
                \\MSMSR07\SECRETARIAT    
                \\MSMSR07\diouf          
                \\MSMSR07\Eurocodes      
                \\MSMSR07\Denoel         
        \\MOWGLI         
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine MOWGLI.  Error was NT_STATUS_ACCESS_DENIED
        \\MOTARD         
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine MOTARD.  Error was NT_STATUS_ACCESS_DENIED
        \\LAM                           lam
                \\LAM\lam            
                \\LAM\SharedDocs     
                \\LAM\IPC$              IPC distant
        \\KEFLAVIK                      Portable Fred Pascon
                \\KEFLAVIK\C$                   Partage par défaut
                \\KEFLAVIK\ADMIN$               Administration à distance
                \\KEFLAVIK\IPC$                 IPC distant
        \\HELENE         
cli_start_connection: failed to connect to HELENE<20> (0.0.0.0)
        \\GRAVEUR        
                \\GRAVEUR\Colette        
                \\GRAVEUR\C$                    Partage par défaut
                \\GRAVEUR\ADMIN$                Administration à distance
                \\GRAVEUR\Jaspart        
                \\GRAVEUR\Maquoi         
                \\GRAVEUR\Zhang          
                \\GRAVEUR\Bouffioux      
                \\GRAVEUR\Villers        
                \\GRAVEUR\Marquet        
                \\GRAVEUR\Libertiaux     
                \\GRAVEUR\Users          
                \\GRAVEUR\Lam            
                \\GRAVEUR\Haremza        
                \\GRAVEUR\Cescotto       
                \\GRAVEUR\Plumier        
                \\GRAVEUR\Lemaire        
                \\GRAVEUR\SharedDocs     
                \\GRAVEUR\IPC$                  IPC distant
        \\GASTON                        DUMBO
                \\GASTON\StudioLine$            Share for StudioLine
                \\GASTON\SharedDocs     
                \\GASTON\print$                 Pilotes d'imprimantes
                \\GASTON\IPC$                   IPC distant
        \\ETUGCIV1                      ETUGCIV1
cli_start_connection: failed to connect to ETUGCIV1<20> (0.0.0.0)
        \\DUPONT         
                \\DUPONT\C$                     Partage par défaut
                \\DUPONT\ADMIN$                 Administration à distance
                \\DUPONT\HPDeskJet              HP DeskJet 970Cxi
                \\DUPONT\print$                 Pilotes d'imprimantes
                \\DUPONT\IPC$                   IPC distant
        \\CALVIN                        CALVIN
cli_start_connection: failed to connect to CALVIN<20> (0.0.0.0)
        \\ASTERIX                       ASTERIX
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine ASTERIX.  Error was NT_STATUS_ACCESS_DENIED
LINUX
LABOFEU
timeout connecting to 139.165.123.214:445
timeout connecting to 139.165.123.214:139
Error connecting to 139.165.123.214 (Opération déjà en cours)
cli_start_connection: failed to connect to 139.165.123.214<20> (139.165.123.214)
timeout connecting to 139.165.123.214:445
timeout connecting to 139.165.123.214:139
Error connecting to 139.165.123.214 (Opération déjà en cours)
cli_start_connection: failed to connect to LABOFEU01<20> (139.165.123.214)
HYDRO
        \\WOODY          
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine WOODY.  Error was NT_STATUS_ACCESS_DENIED
        \\VW                            cubitus
cli_start_connection: failed to connect to VW<20> (0.0.0.0)
        \\VOLVO          
cli_start_connection: failed to connect to VOLVO<20> (0.0.0.0)
        \\TOYOTA         
cli_start_connection: failed to connect to TOYOTA<20> (0.0.0.0)
        \\SYLVAIN        
cli_start_connection: failed to connect to SYLVAIN<20> (0.0.0.0)
        \\SNOOPY         
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine SNOOPY.  Error was NT_STATUS_ACCESS_DENIED
        \\SIMBA          
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine SIMBA.  Error was NT_STATUS_ACCESS_DENIED
        \\SEAT           
cli_start_connection: failed to connect to SEAT<20> (0.0.0.0)
        \\ROLLSROYCE     
cli_start_connection: failed to connect to ROLLSROYCE<20> (0.0.0.0)
        \\RENAUT         
cli_start_connection: failed to connect to RENAUT<20> (0.0.0.0)
        \\POSEIDON       
cli_start_connection: failed to connect to POSEIDON<20> (0.0.0.0)
        \\PORSCHE        
cli_start_connection: failed to connect to PORSCHE<20> (0.0.0.0)
        \\OPEL           
cli_start_connection: failed to connect to OPEL<20> (0.0.0.0)
        \\OLYMPE         
cli_start_connection: failed to connect to OLYMPE<20> (0.0.0.0)
        \\OLIVE          
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine OLIVE.  Error was NT_STATUS_ACCESS_DENIED
        \\NAO            
cli_start_connection: failed to connect to NAO<20> (0.0.0.0)
        \\MERCEDES       
cli_start_connection: failed to connect to MERCEDES<20> (0.0.0.0)
        \\MASERATTI      
cli_start_connection: failed to connect to MASERATTI<20> (0.0.0.0)
        \\LOTUS          
cli_start_connection: failed to connect to LOTUS<20> (0.0.0.0)
        \\LANCIA         
cli_start_connection: failed to connect to LANCIA<20> (0.0.0.0)
        \\LAMBORGHINI    
cli_start_connection: failed to connect to LAMBORGHINI<20> (0.0.0.0)
        \\KIDPADDLE      
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine KIDPADDLE.  Error was NT_STATUS_ACCESS_DENIED
        \\IDEFIX                        Serveur de backup
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine IDEFIX.  Error was NT_STATUS_ACCESS_DENIED
        \\HONDA          
cli_start_connection: failed to connect to HONDA<20> (0.0.0.0)
        \\HERMES         
cli_start_connection: failed to connect to HERMES<20> (0.0.0.0)
        \\GARFIELD       
cli_start_connection: failed to connect to GARFIELD<20> (0.0.0.0)
        \\FORD           
cli_start_connection: failed to connect to FORD<20> (0.0.0.0)
        \\FERRARI        
cli_start_connection: failed to connect to FERRARI<20> (0.0.0.0)
        \\CITROEN        
cli_start_connection: failed to connect to CITROEN<20> (0.0.0.0)
        \\CHRYSLER       
cli_start_connection: failed to connect to CHRYSLER<20> (0.0.0.0)
        \\CHEVROLET      
cli_start_connection: failed to connect to CHEVROLET<20> (0.0.0.0)
        \\BUGATTI        
cli_start_connection: failed to connect to BUGATTI<20> (0.0.0.0)
        \\BMW            
cli_start_connection: failed to connect to BMW<20> (0.0.0.0)
        \\BILL           
cli_start_connection: failed to connect to BILL<20> (0.0.0.0)
        \\BENTLEY        
cli_start_connection: failed to connect to BENTLEY<20> (0.0.0.0)
        \\BALTHAZAR      
                \\BALTHAZAR\C$                  Partage par défaut
                \\BALTHAZAR\ADMIN$              Administration à distance
                \\BALTHAZAR\Laurent        
                \\BALTHAZAR\Balthazar      
                \\BALTHAZAR\D$                  Partage par défaut
                \\BALTHAZAR\IPC$                IPC distant
        \\AUDI           
cli_start_connection: failed to connect to AUDI<20> (0.0.0.0)
        \\AQUABLUE       
cli_start_connection: failed to connect to AQUABLUE<20> (0.0.0.0)
        \\APOLLON        
cli_start_connection: failed to connect to APOLLON<20> (0.0.0.0)
        \\ALFA           
cli_start_connection: failed to connect to ALFA<20> (0.0.0.0)
        \\AKIROU                        AKIRA
cli_start_connection: failed to connect to AKIROU<20> (0.0.0.0)
        \\ADONIS         
cli_start_connection: failed to connect to ADONIS<20> (0.0.0.0)
HOME
ANAST
        \\PCSECRETARIAT                 Secretariat
cli_start_connection: failed to connect to PCSECRETARIAT<20> (0.0.0.0)
        \\MATAGNE        
                \\MATAGNE\C$                    Partage par défaut
                \\MATAGNE\ADMIN$                Administration à distance
                \\MATAGNE\Equateur_JD    
                \\MATAGNE\Imprimante            Imprimer sur ce périphérique pour envoyer une télécopie.
                \\MATAGNE\Documents      
                \\MATAGNE\print$                Pilotes d'imprimantes
                \\MATAGNE\IPC$                  IPC distant
        \\JUDITH         
                \\JUDITH\C$                     Partage par défaut
                \\JUDITH\ADMIN$                 Administration à distance
                \\JUDITH\partage        
                \\JUDITH\print$                 Pilotes d'imprimantes
                \\JUDITH\IPC$                   IPC distant
                \\JUDITH\BrotherH               Brother HL-1230 series
        \\JEAN-DAVID                    Ordinateur de Jean-David
cli_start_connection: failed to connect to JEAN-DAVID<20> (0.0.0.0)
        \\ANAST04        
timeout connecting to 139.165.123.109:445
                \\ANAST04\HP Color 5500n        HP Color LaserJet 5500 PCL 6
                \\ANAST04\AppleRIGO             laserwriterSelect360
                \\ANAST04\print$                Pilotes d'imprimantes
                \\ANAST04\Sharing File   
                \\ANAST04\IPC$                  IPC distant
                \\ANAST04\H1450rigo             Brother HL-1450 series
```

And eventually

```
~$ ping leo-laptop
ping: unknown host leo-laptop
```

---

### Post by gorgor_bay on 2007-06-19
I've changed my /etc/hosts file to correct the netbios so now I can ping myself:

```
$ ping leo-laptop
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.052 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.040 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.038 ms

--- localhost ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.038/0.043/0.052/0.008 ms
```

And this solved a few issues

---

### Post by dmizer on 2007-06-19
@gorgor_bay:

would you mind terribly posting your /etc/hosts file so others can see what you changed?

---

### Post by forgreatsource on 2007-06-19
```
sudo mount -t cifs //192.168.1.110/MyFiles /media/source -o guest,ro,iocharset=utf8,file_mode=0777,dir_mode=0777
mount error 5 = Input/output error
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

it just seems that the samba server is completely failing but the service is running..

---

### Post by gorgor_bay on 2007-06-19
In fact I just realized I solved half of my problems...
my /etc/hosts file was like that :
```
127.0.0.1 localhost leo-laptop.LINUX
127.0.1.1 leo-laptop.LINUX

# The following lines are desirable for IPv6 capable hosts
#::1     ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts
```

which wasn't correctly reflecting the NetBios name, so I changed it into that:
```
127.0.0.1 localhost leo-laptop
127.0.1.1 leo-laptop

# The following lines are desirable for IPv6 capable hosts
#::1     ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts
```

Now when I go and browse directly smb://leo-laptop/ it works fine like it used to do for smb://my.ip.adress

There remains an outstanding problem, since whene anyone browse my workgroup through the local network, they get the deadly error and cannot manage to list the computer within the workgroup called "LINUX" 

So if anybody is still around, I'd love to get some advice on that issue. Thanks !

---

### Post by dmizer on 2007-06-19
> **forgreatsource said:**
> ```
sudo mount -t cifs //192.168.1.110/MyFiles /media/source -o guest,ro,iocharset=utf8,file_mode=0777,dir_mode=0777
mount error 5 = Input/output error
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

it just seems that the samba server is completely failing but the service is running..

please post your problem in the samba server howto thread, and i'll continue to keep an eye on this and search for an answer to your problem.  are you running a static network by chance?

---

### Post by dmizer on 2007-06-19
> **gorgor_bay said:**
> There remains an outstanding problem, since whene anyone browse my workgroup through the local network, they get the deadly error and cannot manage to list the computer within the workgroup called "LINUX" 

So if anybody is still around, I'd love to get some advice on that issue. Thanks !

in windows, you'll need to right click on my computer and select mount network drive.  you won't be able to browse to the share unless you use "view entire windows network" or unless you have the windows computer join the "LINUX" workgroup.

---

### Post by gorgor_bay on 2007-06-19
> **dmizer said:**
> in windows, you'll need to right click on my computer and select mount network drive.  you won't be able to browse to the share unless you use "view entire windows network" or unless you have the windows computer join the "LINUX" workgroup.

But still if I browse through my own workgroup using my very own Ubuntu box (so I should be able to see only the machine that are on the same workgroup "LINUX" as me) I get the same error.

So there must be some kind of error... I've tried changing workgroups to match with the pre-existing workgroups on the local network. And when I do so, I'm turning the workgroup I join into rubbish because I cannot even list the workgroup content and get the same error.

---

### Post by gorgor_bay on 2007-06-20
**up**

---

### Post by dmizer on 2007-06-20
> **gorgor_bay said:**
> **up**
see private messages.

---

