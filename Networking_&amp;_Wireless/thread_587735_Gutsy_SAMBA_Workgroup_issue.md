---
title: "Gutsy SAMBA Workgroup issue"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by marx2k on 2007-10-23
My issue is that this computer has samba shares.  The name of its' workgroup is "WORKGROUP" but the workgroup name does appear in any smb:/// listings.

My roommate's SAMBA server does show up, but mine does not.

This seems to have only happened since upgrading to Gutsy.

I do not see the network under smbtree


This computer is 192.168.11.4, btw..

```

marx2k@Commodore-64:~$ nmblookup -L -M -- -
querying __MSBROWSE__ on 127.255.255.255
querying __MSBROWSE__ on 192.168.11.255
192.168.11.5 __MSBROWSE__<01>

```

This works fine:
```

marx2k@Commodore-64:~$  smbclient //localhost/downloads -U marx2k
Password: 
Domain=[COMMODORE64] OS=[Unix] Server=[Samba 3.0.26a]
smb: \> 

```

But this does not...
```

marx2k@Commodore-64:~$ smbclient //Commodore64/downloads -U marx2k
Connection to Commodore64 failed (Error NT_STATUS_BAD_NETWORK_NAME)

```

```

marx2k@Commodore-64:~$ nmblookup -U commodore64 -R 'WORKGROUP'
querying WORKGROUP on 0.0.0.0
name_query failed to find name WORKGROUP

```

```

marx2k@Commodore-64:~$ sudo findsmb -d


                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
===============================================================
Looking up status of 192.168.11.5
        SIDUXBOX        <00> -         B <ACTIVE> 
        SIDUXBOX        <03> -         B <ACTIVE> 
        SIDUXBOX        <20> -         B <ACTIVE> 
        ..__MSBROWSE__. <01> - <GROUP> B <ACTIVE> 
        SIDUX           <1d> -         B <ACTIVE> 
        SIDUX           <1e> - <GROUP> B <ACTIVE> 
        SIDUX           <00> - <GROUP> B <ACTIVE> 

        MAC Address = 00-00-00-00-00-00

Domain=[SIDUX] OS=[Unix] Server=[Samba 3.0.25b]
Domain=[SIDUX] OS=[Unix] Server=[Samba 3.0.25b]
Anonymous login successful

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       IPC Service (Samba 3.0.25b)
        print$          Disk      Printer Drivers
        sidux_hda       Disk      SIDUXBOX
        homes           Disk      Home Directories
Anonymous login successful

        Server               Comment
        ---------            -------
        SIDUXBOX             Samba 3.0.25b

        Workgroup            Master
        ---------            -------
        SIDUX                SIDUXBOX
192.168.11.5    SIDUXBOX      +[SIDUX] [Unix] [Samba 3.0.25b]
===============================================================
Looking up status of 192.168.11.7
        MEDIACENTER     <00> -         B <ACTIVE> 
        MEDIACENTER     <03> -         B <ACTIVE> 
        MEDIACENTER     <20> -         B <ACTIVE> 
        WORKGROUP       <1e> - <GROUP> B <ACTIVE> 
        WORKGROUP       <00> - <GROUP> B <ACTIVE> 

        MAC Address = 00-00-00-00-00-00

Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.26a]
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.26a]
Anonymous login successful

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       IPC Service (Mediacenter server (Samba, Ubuntu))
        print$          Disk      Printer Drivers
        LaserJet-5      Printer   HP_LJ5
Anonymous login successful

        Server               Comment
        ---------            -------
        MEDIACENTER          Mediacenter server (Samba, Ubuntu)

        Workgroup            Master
        ---------            -------
        WORKGROUP            COMMODORE64
192.168.11.7    MEDIACENTER    [WORKGROUP] [Unix] [Samba 3.0.26a]
===============================================================
Looking up status of 192.168.11.8
        TANDYCOCO       <00> -         B <ACTIVE> 
        TANDYCOCO       <03> -         B <ACTIVE> 
        TANDYCOCO       <20> -         B <ACTIVE> 
        WORKGROUP       <1e> - <GROUP> B <ACTIVE> 
        WORKGROUP       <00> - <GROUP> B <ACTIVE> 

        MAC Address = 00-00-00-00-00-00

Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.26a]
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.26a]
Anonymous login successful

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (Samba 3.0.26a)
        PDF             Printer   PDF
Anonymous login successful

        Server               Comment
        ---------            -------
        TANDYCOCO            Samba 3.0.26a

        Workgroup            Master
        ---------            -------
        WORKGROUP            
192.168.11.8    TANDYCOCO      [WORKGROUP] [Unix] [Samba 3.0.26a]

```





Here's my testparm output:

```

[global]
        netbios name = COMMODORE64
        server string = %h server (Samba, Ubuntu)
        interfaces = 127.0.0.0/8, eth0
        bind interfaces only = Yes
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = hosts wins bcast
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        os level = 200
        wins support = Yes
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[Downloads]
        path = /home/marx2k/Desktop/Downloads
        read only = No
        guest ok = Yes

```

Here's my actual smb.conf:
```

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = workgroup
	netbios name = Commodore64

	server string = %h server (Samba, Ubuntu)
	os level = 200

	wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;  wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	;dns proxy = yes

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
	name resolve order = hosts wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
   interfaces = 127.0.0.0/8 eth0
	;interfaces = lo, eth0
 ;announce version = 5.0
# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
	bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
	log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
	max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;	syslog only = no

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
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
	passdb backend = tdbsam

	obey pam restrictions = yes

;	guest account = nobody
	invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;	unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;	pam password change = no

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;  domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;	logon path = \\%n\%u\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;	logon home = \\%n\%u

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
;	load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;	printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
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
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;	domain master = auto
;	guest ok = no

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;
; The following was the default behaviour in sarge
; but samba upstream reverted the default because it might induce
; performance issues in large organizations
; See #368251 for some of the consequences of *not* having
; this setting and smb.conf(5) for all details
;
;   winbind enum groups = yes
;   winbind enum users = yes

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
# This might need tweaking when using external authentication schemes
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

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

[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
;	public = no
;	writable = No
	create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
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


[Downloads]
	path = /home/marx2k/Desktop/Downloads
        ;path = /tmp
	available = yes
	browsable = yes
        public = yes
        writable = yes
	guest ok = yes
	
	;force user = marx2k
	;force password = marx2k

```

I really hope someone can help me out... I am on day 3 of trying to deal with this

---

### Post by Blackcomb on 2007-10-23
I've set up samba myself today on a desktop and a laptop, but I have'nt got any issues.

marx2k, your testparm output shows no "workgroup = ..." 

-> what's the location of the smb.conf file you have pasted here?
-> are you sure there are no duplicate server string's or netbios names in the workgroup?

regards

---

### Post by marx2k on 2007-10-23
I noticed that too, though it IS in there. 

I did get it working, though I used a different method.  I downloaded from the repositories the program called GSAMBAD.  I allowed it to create a brand new smb.conf for me and I changed the workgroup name, and I made this computer the local, domain and preferred master on the network.

Everything seems to be working out fine. (By the way, if you haven't tried out GSAMBAD, I would highly suggest it. It is NICE!)

Here is my smb.conf:
```

[global]
netbios name = Commodore64
server string = All your friends will be knocking down your door to play with your Commodore 64
workgroup = RollingRock
security = user
hosts allow = 127. 192.168.11.
interfaces = eth0, lo
remote announce = 192.168.11.255
remote browse sync = 192.168.11.255
printcap name = /etc/printcap
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 8
password level = 8
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = yes
domain master = yes
preferred master = yes
domain logons = no
os level = 200
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = no
wins server = 
wins proxy = no
dns proxy = no
preserve case = no
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
smb passwd file = /etc/samba/smbpasswd
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no

[homes]
comment = Home Directories
path = /home
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
share modes = no
locking = no

[profiles]
comment = User Profiles
path = /var/samba/profiles
read only = no
available = yes
browseable = no
writable = yes
guest ok = no
public = no
printable = no
locking = no
create mode = 0600
directory mask = 0700

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
share modes = no
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
browseable = yes
writeable = yes
guest ok = yes

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gsambadpdf %s %u
lpq command =
lprm command =

[Downloads]
path = /home/marx2k/Desktop/Downloads
comment = Network Downloads
valid users =
write list =
admin users =
read only = no
available = yes
browseable = yes
writable = yes
guest ok = yes
public = yes
printable = no
share modes = no
locking = no

```

---

### Post by mgmiller on 2007-10-24
There is now a nice gui for configuring samba.  it is system-config-samba
```
sudo apt-get install system-config-samba
```
Once it's installed, look under System > Administration > Samba
It lets you adjust damn near everything and lets you change work group names, etc.

After I upgraded from Festy to Gutsy, my server was no longer seen on any of the windows or Ubuntu machines on my network.  By running this app, I quickly set everything back up again. and changed the workgroup name back to the microsoft "standard" of MSHOME.  There are check boxes for make browsable, discoverable, etc.  really nicely done.

---

### Post by phirestalker on 2007-10-31
> **mgmiller said:**
> There is now a nice gui for configuring samba.  it is system-config-samba
```
sudo apt-get install system-config-samba
```
Once it's installed, look under System > Administration > Samba
It lets you adjust damn near everything and lets you change work group names, etc.

After I upgraded from Festy to Gutsy, my server was no longer seen on any of the windows or Ubuntu machines on my network.  By running this app, I quickly set everything back up again. and changed the workgroup name back to the microsoft "standard" of MSHOME.  There are check boxes for make browsable, discoverable, etc.  really nicely done.

ya I ran that program and changed something and everything worked great, but then I restart later on and it didn't work again, however running this program again fixes it again, I'm not sure if you have to change something or if just running it is enough, have you restarted since you "fixed" it?

---

### Post by phirestalker on 2007-10-31
the problem is caused by nmbd not being running, I haven't discovered if it never starts or if it crashes. The reason this program "fixes" the problem is that it starts nmbd

---

