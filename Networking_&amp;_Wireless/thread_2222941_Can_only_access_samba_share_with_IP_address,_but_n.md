---
title: "Can only access samba share with IP address, but not hostname"
date: 2014-05-08
forum: Networking &amp; Wireless
---

### Post by c_xy on 2014-05-08
Hello,


I'm having trouble accessing a samba share folder. It is Ubuntu 10.04 linux server. We've been able to connect from several Windows 7 machines to the share folder on our linux server. However, this past week we can no longer access it.


Every time we try to access it from a Windows 7 machine we get the following error message:


[HTML]The folder  you entered does not appear to be valid. Please chose another location[/HTML]


If type in a Windows 7 Command Prompt window I get the following error message:


> 


net view \\server_name 
System error 53 has occured
The network path was not found





However, if I use the ip address of the server instead of the hostname, I can access the share with samba and the net view command works. Another strange thing is that I CAN ping the hostname successfully. I can only ping it. Nothing else.


So, I'm not sure what is going on. It was working a fine for the past 3 years up until this week. I can access our other servers with the same configurations as the problematic one using samba with no problems. Could it have been a recent update?








Here is my smb.conf file:


> 
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
# - When such options are commented with ";", the proposed setting
# differs from the default Samba behaviour
# - When commented with "#", the proposed setting is the default
# behaviour of Samba but the option is considered important
# enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#




#======================= Global Settings =======================




[global]




## Browsing/Identification ###




# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = WORKGROUP




# server string is the equivalent of the NT Description field
server string = %h server (Samba, Ubuntu)




# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
# wins support = no




# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
; wins server = w.x.y.z




# This will prevent nmbd to search for NetBIOS names through DNS.
dns proxy = no




# What naming service and in what order should we use to resolve host names
# to IP addresses
; name resolve order = lmhosts host wins bcast




#### Networking ####




# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
; interfaces = 127.0.0.0/8 eth0




# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself. However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
; bind interfaces only = yes












#### Debugging/Accounting ####




# This tells Samba to use a separate log file for each machine
# that connects
log file = /var/log/samba/log.%m




# Cap the size of the individual log files (in KiB).
max log size = 1000




# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
# syslog only = no




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




# You may wish to use password encryption. See the section on
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
; domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
; logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
# logon path = \\%N\%U\profile




# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
; logon drive = H:
# logon home = \\%N\%U




# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
; logon script = logon.cmd




# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe. The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u




# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe. 
# The following assumes a "machines" group exists on the system
; add machine script = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u




# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe. 
; add group script = /usr/sbin/addgroup --force-badname %g




########## Printing ##########




# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
# load printers = yes




# lpr(ng) printing. You may wish to override the location of the
# printcap file
; printing = bsd
; printcap name = /etc/printcap




# CUPS printing. See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
; printing = cups
; printcap name = cups




############ Misc ############




# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
; include = /home/samba/etc/smb.conf.%m




# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
# SO_RCVBUF=8192 SO_SNDBUF=8192
# socket options = TCP_NODELAY




# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
; message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &




# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
# domain master = auto




# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
; idmap uid = 10000-20000
; idmap gid = 10000-20000
; template shell = /bin/bash




# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
; winbind enum groups = yes
; winbind enum users = yes




# Setup usershare options to enable non-root users to share folders
# with the net usershare command.




# Maximum number of usershare. 0 (default) means that usershare is disabled.
; usershare max shares = 100




# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
usershare allow guests = yes




#======================= Share Definitions =======================




# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
; comment = Home Directories
; browseable = no




# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
; read only = yes




# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
; create mask = 0700




# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
; directory mask = 0700




# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
; valid users = %S




# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
; comment = Network Logon Service
; path = /home/samba/netlogon
; guest ok = yes
; read only = yes
; share modes = no




# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
; comment = Users profiles
; path = /home/samba/profiles
; guest ok = no
; browseable = no
; create mask = 0600
; directory mask = 0700




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
; write list = root, @lpadmin




# A sample share for sharing your CD-ROM with others.
;[cdrom]
; comment = Samba server's CD-ROM
; read only = yes
; locking = no
; path = /cdrom
; guest ok = yes




# The next two parameters show how to auto-mount a CD-ROM when the
# cdrom share is accesed. For this to work /etc/fstab must contain
# an entry like this:
#
# /dev/scd0 /cdrom iso9660 defaults,noauto,ro,user 0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
# is mounted on /cdrom
#
; preexec = /bin/mount /cdrom
; postexec = /bin/umount /cdrom




[shared_folder]
comment = Ubuntu File Server Share
path = /data
valid users = my_name
browsable = yes
guest ok = no
read only = no
writeable = yes
create mask = 0755















I've tried uninstalling and then re-installing samba several times with no success. Not sure what else to do at this point. We are using the same setup above for other servers with no issues. I presume it is probably something simple i'm overlooking,but I haven't pinpointed it just yet.


Any input, feedback, or suggestions would be of great help.


Thank you.


c

---

### Post by TheFu on 2014-05-08
DNS working?
Please run **testparm** and post the output.

---

### Post by c_xy on 2014-05-08
Here is the output from testparm

```

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[data]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions


[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d


[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[COLOR=#000000]*[data]*[/COLOR]
	comment = Ubuntu File Server Share
	path = /data
	valid users = [COLOR=#000000]* my_name*[/COLOR]
	read only = No
	create mask = 0755








```

---

### Post by TheFu on 2014-05-08
So - how does the testparm output from systems that still work compare?
How do the clients 'locate' the server - WINS, DNS, /etc/hosts, lmhosts?

---

### Post by bab1 on 2014-05-08
> **c_xy said:**
> Hello,


I'm having trouble accessing a samba share folder. It is Ubuntu 10.04 linux server. We've been able to connect from several Windows 7 machines to the share folder on our linux server. However, this past week we can no longer access it.


Every time we try to access it from a Windows 7 machine we get the following error message:
```
The folder  you entered does not appear to be valid. Please chose another location
```

If type in a Windows 7 Command Prompt window I get the following error message:
```
net view \\server_name
System error 53 has occured
The network path was not found
```
However, if I use the ip address of the server instead of the hostname, I can access the share with samba and the net view command works. Another strange thing is that I CAN ping the hostname successfully. I can only ping it. Nothing else.

So, I'm not sure what is going on. It was working a fine for the past 3 years up until this week. I can access our other servers with the same configurations as the problematic one using samba with no problems. Could it have been a recent update?

I've tried uninstalling and then re-installing samba several times with no success. Not sure what else to do at this point. We are using the same setup above for other servers with no issues. I presume it is probably something simple i'm overlooking,but I haven't pinpointed it just yet.

Any input, feedback, or suggestions would be of great help.

Thank you.

c
It's definitely a name services problem. Have you moved the machine to another subnet?  Pinging the host by name shows connectivity.  In the background Samba has to convert the hostname to a NETBIOS name.  That is the problem here.  Connection via IP address is ultimately the end result of name services.  So you have the connectivity but somehow have lost the NETBIOS name services.  From the Samba server itself you should be able to see using this at the command line```
smbtree -d3
```...post all of the output back here.  Place it between the code blocks.  That's the [SIZE=5]#[/SIZE] icon at the top of the reply editor.

Testparm just tests the correctness of the smb.conf file.  The file seems right to me.

---

### Post by c_xy on 2014-05-09
Guys, thank you for the responses and feedback. I'll try to answer the questions as best I can:


> 
***TheFu:***

So - how does the testparm output from systems that still work compare?
How do the clients 'locate' the server - WINS, DNS, /etc/hosts, lmhosts?



I'm not sure how the windows machines locate the server. How could I check that? Is there an option, settings in Windows where I can check this? Or would that be on the server end?

The testparm ouput from the other systems looks the same. One server has only one share folder, and the other server has two share folders. Other than that, the two working servers ouput from testparm look identical.

Here is a testparm from the working server with 1 accessible share folder:

```

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[data]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions


[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[data]
    comment = Ubuntu File Server Share
    path = /data
    valid users = my_name2
    read only = No
    create mask = 0755




```


> 
[B]babs1:
[/B]
[COLOR=#000000]Have you moved the machine to another subnet? 
[/COLOR]


No, we did not make any changes on our end at all. Just some routine updates and a reboot.

Here is the output from smbtree -d3. I had cut out a lot of it because the output contained other compters/servers in our office network that we don't use. Also, I blocked out the ip address names. 



```
  
smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface virbr0 ip=fxxx::xxxx:xxxx:xxxx:xxxx%virbr0 bcast=fe80::ffff:ffff:ffff:ffff%virbr0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=fe80::fxxx:xxxx:fe3d:xxxx%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=server_ip_address bcast=xxx.xxx.xx.xxx netmask=xxx.xxx.xxx.0
added interface virbr0 ip=xxx.xxx.xxx.x bcast=xxx.xxx.xxx. netmask=xxx.xxx.xxx.0
Enter my_name's password:
tdb(unnamed): tdb_open_ex: could not open file /
var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from yyy.yyy.yy.yy( yyy.yyy.yy.yy)
Connecting to host=yyy.yyy.yy.yy
Connecting to yyy.yyy.yy.yyat port 445
Doing spnego session setup (blob length=58)
got OID=x.x.x.x.x.x.xxx.x.x.xx
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608axxxx
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x6008xxxx
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x6008xxxx
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from yyy.yyy.yy.yy( yyy.yyy.yy.yy)
Got a positive name query response from xxx.xx.xx.xxx (xxx.xx.xx.xxx )
Got a positive name query response from xxx.xx.xx.xx (xxx.xx.xx.xx )
Got a positive name query response from xxx.xx.xx.xx (xxx.xx.xx.xx )
Got a positive name query response fromxxx.xx.xx.xx (xxx.xx.xx.xx )
Got a positive name query response fromxxx.xx.xx.xxx (xxx.xx.xx.xxx )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from yyy.yyy.yy.yy( yyy.yyy.yy.yy)
Connecting to host=yyy.yyy.yy.yy
Connecting to yyy.yyy.yy.yy at port 445
Doing spnego session setup (blob length=58)
got OID=x.x.x.x.x.x.xxx.x.x.xx
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608axxxx
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x6008xxxx
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x6008xxxx
SPNEGO login failed: Logon failure

...
...

  \\SERVER_HOSTNAME               SERVER_HOSTNAME server (Samba, Ubuntu)Connecting to host=SERVER_HOSTNAME
resolve_lmhosts: Attempting lmhosts lookup for name SERVER_HOSTNAME<0x20>
resolve_wins: Attempting wins lookup for name SERVER_HOSTNAME<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SERVER_HOSTNAME<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=58)
got OID=x.x.x.x.x.x.xxx.x.x.xx
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608axxxx
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x6008xxxx
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x6008xxxx
        \\SERVER_HOSTNAME\IPC$               IPC Service (SERVER_HOSTNAME server (Samba, Ubuntu))
        \\SERVER_HOSTNAME\data               Ubuntu File Server Share
        \\SERVER_HOSTNAME\print$             Printer Drivers




```


Comparing the output with our other servers, I noticed "virbr0". I don't see this in the output of smbtree for our other workable servers. Also, they IP address yyy.yyy.yy.yyy, is the ip address for our other server. It is also listed as the Master in the output for smbclient -L server_hostname. Also, I noticed a "[COLOR=#000000][FONT=Ubuntu Mono]SPNEGO login failed: Logon failure" statement. Is this part of the problem?[/FONT][/COLOR]

For clarification purposes:

other_hostname = second server, other,  that i can access samba share folders
server_hostname = name of server where we are having issues accessing samba share folders by hostname. In the past, we had them both working together via NFS. However, we stopped using NFS several months back. Maybe some packages lurking around have creeped up and created this problem? Not sure, just throwing that idea out there.


```


smbclient -L server_hostname
Enter my_name's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]


    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    data            Disk      Ubuntu File Server Share
    data2           Disk      Ubuntu File Server Share
    IPC$            IPC       IPC Service (server_hostname server (Samba, Ubuntu))
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]


    Server               Comment
    ---------            -------
    OTHER_HOSTNAME       other_hostname server (Samba, Ubuntu)
    SERVER_HOSTNAME      server_hostname server (Samba, Ubuntu)


    Workgroup            Master
    ---------            -------
    WORKGROUP            other_hostname


```



Thank you for your time, and your help is greatly appreciated.

c

---

### Post by TheFu on 2014-05-09
Bab1 is the expert on this stuff. You are in good hands.

nfs is NOT interfering at all. Don't worry about that.

---

### Post by c_xy on 2014-05-09
TheFu, thanks for the assurance and your input as well.

Also,

I wanted to add one more thing.

I noticed in my /ets/samba directory, there was a dhcp.conf file. For our other two servers where samba is working fine, this file is blank. But for the server giving us problems, the dhcp.conf file contains:

```

wins server =  eth0:xxx.xxx.xx.xx eth0:xxx.xxx.1.xx4 eth0:xxx.xxx.1.xx6


```

The first ip address listed i don't recognize. It is not the windows pc I try from which I try to connect to the server. The next two ip addresses have the same numbers, except for the last digit. Not sure why this file is there. Never really paid much attention to it in this directory. Only used the smb.conf in the /etc/samba directory.

---

### Post by bab1 on 2014-05-09
> **c_xy said:**
> Guys, thank you for the responses and feedback. I'll try to answer the questions as best I can:

I'm not sure how the windows machines locate the server. How could I check that? Is there an option, settings in Windows where I can check this? Or would that be on the server end?

All SMB/CIFS clients locate the available shares via the Master Browse List.  The MBL is held on only one machine in the network.  If the host that is holding the MBL goes off line then an election is held to determine the holder of the new MBL.  One MBL is all that should be available per subnet (broadcast domain).  In the output of your smbtree command you show 2 Master Browsers. 
> 
No, we did not make any changes on our end at all. Just some routine updates and a reboot. 

The changes don't  have to be "at your end" for you to have problems.  If you don't have total control of the entire network then you should be talking to someone who does and can see the complete picture.
> 
Here is the output from smbtree -d3. I had cut out a lot of it because the output contained other compters/servers in our office network that we don't use. Also, I blocked out the ip address names. 

```
  
smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface [COLOR="#800080"]**virbr0 ip=fxxx::xxxx:xxxx:xxxx:xxxx%virbr0 bcast=fe80::ffff:ffff:ffff:ffff%virbr0 netmask=ffff:ffff:ffff:ffff::**[/COLOR]
added interface eth0 ip=fe80::fxxx:xxxx:fe3d:xxxx%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=server_ip_address bcast=xxx.xxx.xx.xxx netmask=xxx.xxx.xxx.0
added interface virbr0 ip=xxx.xxx.xxx.x bcast=xxx.xxx.xxx. netmask=xxx.xxx.xxx.0
Enter my_name's password:
tdb(unnamed): tdb_open_ex: could not open file /
var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
**[SIZE=2]name_resolve_bcast:[/SIZE]** Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from yyy.yyy.yy.yy( yyy.yyy.yy.yy)
Connecting to host=yyy.yyy.yy.yy
Connecting to yyy.yyy.yy.yyat port 445
Doing spnego session setup (blob length=58)
got OID=x.x.x.x.x.x.xxx.x.x.xx
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608axxxx
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x6008xxxx
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x6008xxxx
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
[COLOR="#008000"]**Got a positive name query response from yyy.yyy.yy.yy( yyy.yyy.yy.yy)**[/COLOR]
[COLOR="#0000FF"]**Got a positive name query response from xxx.xx.xx.xxx (xxx.xx.xx.xxx )**[/COLOR]
Got a positive name query response from xxx.xx.xx.xx (xxx.xx.xx.xx )
Got a positive name query response from xxx.xx.xx.xx (xxx.xx.xx.xx )
Got a positive name query response fromxxx.xx.xx.xx (xxx.xx.xx.xx )
Got a positive name query response fromxxx.xx.xx.xxx (xxx.xx.xx.xxx )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from yyy.yyy.yy.yy( yyy.yyy.yy.yy)
Connecting to host=yyy.yyy.yy.yy
Connecting to yyy.yyy.yy.yy at port 445
Doing spnego session setup (blob length=58)
got OID=x.x.x.x.x.x.xxx.x.x.xx
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608axxxx
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x6008xxxx
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x6008xxxx
SPNEGO login failed: Logon failure


  \\SERVER_HOSTNAME               SERVER_HOSTNAME server (Samba, Ubuntu)Connecting to host=SERVER_HOSTNAME
resolve_lmhosts: Attempting lmhosts lookup for name SERVER_HOSTNAME<0x20>
resolve_wins: Attempting wins lookup for name SERVER_HOSTNAME<0x20>
resolve_wins: WINS server resolution selected and** no WINS servers** listed.
[COLOR="#FF0000"][B]resolve_hosts: Attempting host lookup for name SERVER_HOSTNAME<0x20>
Connecting to 127.0.1.1 at port 445[/B][/COLOR]
Doing spnego session setup (blob length=58)
got OID=x.x.x.x.x.x.xxx.x.x.xx
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608axxxx
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x6008xxxx
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x6008xxxx
        \\SERVER_HOSTNAME\IPC$               IPC Service (SERVER_HOSTNAME server (Samba, Ubuntu))
        \\SERVER_HOSTNAME\data               Ubuntu File Server Share
        \\SERVER_HOSTNAME\print$             Printer Drivers

```

Comparing the output with our other servers, I noticed "virbr0". 

This is a interface to a virtual host.  I'll bet the host is using bridging to be seen in your subnet.  It can be benign, or not. 
> 
I don't see this in the output of smbtree for our other workable servers. Also, they IP address yyy.yyy.yy.yyy, is the ip address for our other server. It is also listed as the Master in the output for smbclient -L server_hostname. Also, I noticed a "[COLOR=#000000][FONT=Ubuntu Mono]SPNEGO login failed: Logon failure" statement. Is this part of the problem?[/FONT][/COLOR]
Sure it can.

For clarification purposes:

other_hostname = second server, other,  that i can access samba share folders
server_hostname = name of server where we are having issues accessing samba share folders by hostname. In the past, we had them both working together via NFS. However, we stopped using NFS several months back. Maybe some packages lurking around have creeped up and created this problem? Not sure, just throwing that idea out there.
If you look at the various colors and bold text you will see what I will mention here.  Samba is using broadcasts to announce and locate various hosts.  This means every host needs to be in one broadcast domain.  Since you should have only 1 MBL per domain you should not have what I have highlighted in blue and green.   The 127.n.n.n subnet (highlighted in red) is reserved for the local host only Samba should not be connecting to that interface for any service.> 
```


smbclient -L server_hostname
Enter my_name's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]


    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    data            Disk      Ubuntu File Server Share
    data2           Disk      Ubuntu File Server Share
    IPC$            IPC       IPC Service (server_hostname server (Samba, Ubuntu))
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]


    Server               Comment
    ---------            -------
    OTHER_HOSTNAME       other_hostname server (Samba, Ubuntu)
    SERVER_HOSTNAME      server_hostname server (Samba, Ubuntu)


    Workgroup            Master
    ---------            -------
    WORKGROUP            other_hostname


```


Thank you for your time, and your help is greatly appreciated.

c
I think you need to find out network wide what has changed.  There are changes that need to be made on your workgroup server that have been revealed even though it has been working previously.  Talk to your system admin and workout what you need to do.  

> 
I wanted to add one more thing.

I noticed in my /ets/samba directory, there was a dhcp.conf file. For our other two servers where samba is working fine, this file is blank. But for the server giving us problems, the dhcp.conf file contains:
```
wins server =  eth0:xxx.xxx.xx.xx eth0:xxx.xxx.1.xx4 eth0:xxx.xxx.1.xx6
```
The first ip address listed i don't recognize. It is not the windows pc I try from which I try to connect to the server. The next two ip addresses have the same numbers, except for the last digit. Not sure why this file is there. Never really paid much attention to it in this directory. Only used the smb.conf in the /etc/samba directory.

Since you are not using a WINS server this isn't needed at all.

In summary you need to have IT reconfigure this machine with the entire SMB/CIFS network in mind as you have multiple problems with this server.

[COLOR="#0000FF"]EDIT:  Since I can't even see all of the information, anything I would say about specific configuration would be a guess.  I don't guess at these things so I'm not your guy to fix anything specifically.[/COLOR]

---

### Post by c_xy on 2014-05-10
bab1,

Thank you for your response. It is lot to digest and to think about.

I've contacted our IT department to see what may have changed on our office network.

Aside from that, a few more things:

You stated:

> 
[COLOR=#000000]If you look at the various colors and bold text you will see what I will mention here. Samba is using broadcasts to announce and locate various hosts. This means every host needs to be in one broadcast domain. Since you should have only 1 MBL per domain you should not have what I have highlighted in blue and green. The 127.n.n.n subnet (highlighted in red) is reserved for the local host only Samba should not be connecting to that interface for any service.[/COLOR]


```

  
smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface [COLOR=#800080]**virbr0 ip=fxxx::xxxx:xxxx:xxxx:xxxx%virbr0 bcast=fe80::ffff:ffff:ffff:ffff%virbr0 netmask=ffff:ffff:ffff:ffff::**[/COLOR]
added interface eth0 ip=fe80::fxxx:xxxx:fe3d:xxxx%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=server_ip_address bcast=xxx.xxx.xx.xxx netmask=xxx.xxx.xxx.0
added interface virbr0 ip=xxx.xxx.xxx.x bcast=xxx.xxx.xxx. netmask=xxx.xxx.xxx.0
Enter my_name's password:
tdb(unnamed): tdb_open_ex: could not open file /
var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
**[SIZE=2]name_resolve_bcast:[/SIZE]** Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from yyy.yyy.yy.yy( yyy.yyy.yy.yy)
Connecting to host=yyy.yyy.yy.yy
Connecting to yyy.yyy.yy.yyat port 445
Doing spnego session setup (blob length=58)
got OID=x.x.x.x.x.x.xxx.x.x.xx
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608axxxx
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x6008xxxx
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x6008xxxx
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
[COLOR=#008000]**Got a positive name query response from yyy.yyy.yy.yy( yyy.yyy.yy.yy)**[/COLOR]
[COLOR=#0000FF]**Got a positive name query response from xxx.xx.xx.xxx (xxx.xx.xx.xxx )**[/COLOR]
Got a positive name query response from xxx.xx.xx.xx (xxx.xx.xx.xx )
Got a positive name query response from xxx.xx.xx.xx (xxx.xx.xx.xx )
Got a positive name query response fromxxx.xx.xx.xx (xxx.xx.xx.xx )
Got a positive name query response fromxxx.xx.xx.xxx (xxx.xx.xx.xxx )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from yyy.yyy.yy.yy( yyy.yyy.yy.yy)
Connecting to host=yyy.yyy.yy.yy
Connecting to yyy.yyy.yy.yy at port 445
Doing spnego session setup (blob length=58)
got OID=x.x.x.x.x.x.xxx.x.x.xx
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608axxxx
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x6008xxxx
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x6008xxxx
SPNEGO login failed: Logon failure


  \\SERVER_HOSTNAME               SERVER_HOSTNAME server (Samba, Ubuntu)Connecting to host=SERVER_HOSTNAME
resolve_lmhosts: Attempting lmhosts lookup for name SERVER_HOSTNAME<0x20>
resolve_wins: Attempting wins lookup for name SERVER_HOSTNAME<0x20>
resolve_wins: WINS server resolution selected and** no WINS servers** listed.
[COLOR=#FF0000][B]resolve_hosts: Attempting host lookup for name SERVER_HOSTNAME<0x20>
Connecting to 127.0.1.1 at port 445[/B][/COLOR]
Doing spnego session setup (blob length=58)
got OID=x.x.x.x.x.x.xxx.x.x.xx
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608axxxx
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x6008xxxx
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x6008xxxx
        \\SERVER_HOSTNAME\IPC$               IPC Service (SERVER_HOSTNAME server (Samba, Ubuntu))
        \\SERVER_HOSTNAME\data               Ubuntu File Server Share
        \\SERVER_HOSTNAME\print$             Printer Drivers

```


This is helpful,because we have other servers where samba shares work with no issues. These other servers where give similar output as the blue and green text. Right now, our servers are located on the workgroup called....WORKGROUP. Some of those ip addresses are computers within the same WORKGROUP the problematic server is located. The question is why only those select number of IP addresses, and not the entire group of computers? Also, how could I configure my samba settings that would eliminate the blue and green text output above?

I checked out this link ---->  [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

I check to see if it could possibly be a firewall relate issue (Problem 4)

Typing 

sudo iptables -L

I get the following output:


```


Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps 


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             192.168.x.x/24    state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.x.x/24     anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   


```

Could this cause the problem? We don't see this output on our other servers. I tried clearing this with the following command:

iptables -F

And it does clear the firewall. But, I still cannot connect to the shared folder. After I reboot the server, i recieve the same output above with the iptables -L command. I'm not sure how this firewall started, but we do not want it. Maybe it was started by installing another package in the past. We do not have it on our other servers. Not sure if this is related to problem, but I can't tell after rebooting the machine and the firewalls are active again. How can I continue to have firewalls disabled after every reboot?

thanks again for all of your help.

c

---

### Post by TheFu on 2014-05-10
If the samba machines and client machines are on the same subnet, then they should find each other.
If they span subnets, more work is needed to get them talking.  It appears your IT department may have 
* altered the DNS
* altered subnets
* removed/modified WINS servers
* enabled firewall rules between the subnets
any one or all of these things could impact client access to samba ... unless every client uses the IP address.

---

### Post by bab1 on 2014-05-10
> **c_xy said:**
> bab1,

Thank you for your response. It is lot to digest and to think about.

I've contacted our IT department to see what may have changed on our office network.

Aside from that, a few more things:

You stated:
> If you look at the various colors and bold text you will see what I will mention here. Samba is using broadcasts to announce and locate various hosts. This means every host needs to be in one broadcast domain. Since you should have only 1 MBL per domain you should not have what I have highlighted in blue and green. The 127.n.n.n subnet (highlighted in red) is reserved for the local host only Samba should not be connecting to that interface for any service.

This is helpful,because we have other servers where samba shares work with no issues. These other servers where give similar output as the blue and green text. Right now, our servers are located on the workgroup called....WORKGROUP. Some of those ip addresses are computers within the same WORKGROUP the problematic server is located. The question is why only those select number of IP addresses, and not the entire group of computers? Also, how could I configure my samba settings that would eliminate the blue and green text output above?
[QUOTE]
Regardless of how other servers are configured.  Samba  uses one and only one Local Master Browser per broadcast domain (IP subnet).  Your server uses broadcasts to locate the MB (name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>).   How your server should be set up is up to the IT department.   

I checked out this link ---->  [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
[/QUOTE]
That link is 5 years old and has errors.  I would not use it as a guide.
> 
I check to see if it could possibly be a firewall relate issue (Problem 4)
...
Could this cause the problem? 

I do  not use host based firewalls at all.  That's a Windows way of doing things.  I have a firewall at the edge of my networks.  If I need to protect servers from internal misdeeds I place those servers on a subnet and have a firewall at the edge of that subnet.  You need to resolve this issue using your IT department.

---

### Post by bab1 on 2014-05-10
> **TheFu said:**
> If the samba machines and client machines are on the same subnet, then they should find each other.

Just a quick note to the OP here.  The machines on a single subnet find each other via the MBL, not directly.  If the machine that holds the MBL goes off line there is an election to create a new MBL.  This is why there is not multiple MB in any subnet.  When NETBIO named machines come and go in the network they send an announce broadcast and they are added to the MBL.  When you browse you are browsing the MBL.
> 
If they span subnets, more work is needed to get them talking.  It appears your IT department may have 
* altered the DNS
* altered subnets
* removed/modified WINS servers
* enabled firewall rules between the subnets
any one or all of these things could impact client access to samba ... unless every client uses the IP address.
Most of this will impact you directly.  Since you have not configured your server for WINS that point is not relevant.

---

### Post by dmn_clown on 2014-05-11
> **c_xy said:**
> However, if I use the ip address of the server instead of the hostname, I can access the share with samba and the net view command works. Another strange thing is that I CAN ping the hostname successfully. I can only ping it. Nothing else.

So edit your hosts file to include the ipaddress and hostname of the smb share and forget about it.

---

### Post by TheFu on 2014-05-11
> **bab1 said:**
> I do  not use host based firewalls at all.  That's a Windows way of doing things.  I have a firewall at the edge of my networks.  If I need to protect servers from internal misdeeds I place those servers on a subnet and have a firewall at the edge of that subnet.  You need to resolve this issue using your IT department.

I run _some minimal_ firewall on every host. With all the javascript running around the internet, it is just a matter of time before someone figures out how to get a browser to attack internal servers from a desktop client.  Laptops, smartphones and edge routers run full firewall settings as though the are on the internet naked. deny all is the default, as specified in Bob Toxen's book and suggested by security pros around the world.  Managing this stuff is easy with any devops tool, like ansible.

---

### Post by c_xy on 2014-05-29
Thanks again for the feedback, guys. Appreciate it.

Just to update guys, we may have stumbled upon the issue.


A new windows desktop computer was added to our WORKGROUP recently. Its computer name was identical to our linux server hostname. As soon as the new desktop computer connected to the WORKGROUP via the internet, this is when we the problem arose connecting to the samba share via the linux hostname.  Was that the main culprit all along? 

The new desktop computer name was changed. 

We then rebooted  the linux server and restarted the samba service. However we still cannot access the samba share folder using the hostname. Only using the IP Address. So, the hostname conflict with the desktop on the WORKGROUP is eliminated. But the problem now remains.

Given this recent discovery, is there another step that needs to be done to get back to normal samba share usage and accessibility? Has the hostname conflict changed some configurations that need resetting? Or is there something more to this?

thanks.

c

---

### Post by c_xy on 2014-06-02
Anyone have any ideas?

---

### Post by c_xy on 2014-08-20
Update:

Another computer on our network had the same computer name as our server. Once IT changed the computer name of the other computer, that seemed to correct our problem of accessing samba regularly. We can now access samba as we did previously.

---

