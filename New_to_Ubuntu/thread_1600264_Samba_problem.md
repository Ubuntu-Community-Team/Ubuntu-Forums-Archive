---
title: "Samba problem"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by narthir on 2010-10-18
Hello everyone,

i am trying since a few days to create a home network but i thing i made it only worst. I want to connect a Windows XP and Ubuntu 10.04 system (between them a router, XP on wireless, Ubuntu on cable, all in the same workgroup). A the beginning i could see my linux and windows shares on my laptop (also Ubuntu 10.04) but not on windows. Now after messing a lot with samba (and firewall) i cant see my linux shares and i get "Unable to mount location. Failed to retrieve share list from server" when i double click on "Windows Network".

My samba.conf:

[global]
; Uncomment this if you want a guest account
;    guest account = nobody
    log file = /var/log/samba-log.%m
    lock directory = /var/lock/samba
;    share modes = yes
    usershare owner only = false
    workgroup = nerv
;    server string = samba 3.4.7
    security = share
;    encrypt passwords = yes
;    guest ok = no

[Public]
    comment = PublicShare
    path = /home/narthir/Public
    writeable = yes
;    browseable = yes
    valid users = narthir

Thanks for any help.

P.S. I think it would be a good idea if i could reset network/firewall/samba configuration for starters :P

---

### Post by Der Ritter on 2010-10-18
Is that your whole smb.conf? For starters you should define an option "netbios name = COMPUTER_NAME" under [global]. The Windows computer isn't going to see your Linux computer in a million years if the Linux computer doesn't have a name.

If you have further problems, see [this HOWTO]("http://ubuntuforums.org/showthread.php?t=202605"). You might want to replace your smb.conf with the one given in there. Even though the HOWTO is old, Samba hasn't changed all that much yet; it still worked recently for setting up file-sharing between a Linux box, a Windows 7 computer, and a Windows XP computer.

---

### Post by sandyd on 2010-10-18
> **narthir said:**
> Hello everyone,

i am trying since a few days to create a home network but i thing i made it only worst. I want to connect a Windows XP and Ubuntu 10.04 system (between them a router, XP on wireless, Ubuntu on cable, all in the same workgroup). A the beginning i could see my linux and windows shares on my laptop (also Ubuntu 10.04) but not on windows. Now after messing a lot with samba (and firewall) i cant see my linux shares and i get "Unable to mount location. Failed to retrieve share list from server" when i double click on "Windows Network".

My samba.conf:

[global]
; Uncomment this if you want a guest account
;    guest account = nobody
    log file = /var/log/samba-log.%m
    lock directory = /var/lock/samba
;    share modes = yes
    usershare owner only = false
    workgroup = nerv
;    server string = samba 3.4.7
    security = share
;    encrypt passwords = yes
;    guest ok = no



Thanks for any help.

P.S. I think it would be a good idea if i could reset network/firewall/samba configuration for starters :P
```

 This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options (perhaps too
# many!) most of which are not shown in this example
#
# For a step to step guide on installing, configuring and using samba, 
# read the Samba-HOWTO-Collection. This may be obtained from:
#  http://www.samba.org/samba/docs/Samba-HOWTO-Collection.pdf
#
# Many working examples of smb.conf files can be found in the 
# Samba-Guide which is generated daily and can be downloaded from: 
#  http://www.samba.org/samba/docs/Samba-Guide.pdf
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentry and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command "testparm"
# to check that you have not made any basic syntactic errors. 
#
#======================= Global Settings =====================================
[global]

# workgroup = NT-Domain-Name or Workgroup-Name, eg: MIDEARTH
   workgroup = **YOUR_WORKGOUP**

# server string is the equivalent of the NT Description field
   server string = **COMPUTERDESCRIPTION**

# Security mode. Defines in which mode Samba will operate. Possible 
# values are share, user, server, domain and ads. Most people will want 
# user level security. See the Samba-HOWTO-Collection for details.
   security = share

# This option is important for security. It allows you to restrict
# connections to machines which are on your local network. The
# following example restricts access to two C class networks and
# the "loopback" interface. For more examples of the syntax see
# the smb.conf man page
;   hosts allow = 192.168.1. 192.168.2. 127.

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = yes

# you may wish to override the location of the printcap file
;   printcap name = /etc/printcap

# on SystemV system setting printcap name to lpstat should allow
# you to automatically obtain a printer list from the SystemV spool
# system
;   printcap name = lpstat

# It should not be necessary to specify the print system type unless
# it is non-standard. Currently supported print systems include:
# bsd, cups, sysv, plp, lprng, aix, hpux, qnx
;   printing = cups

# Uncomment this if you want a guest account, you must add this to /etc/passwd
# otherwise the user "nobody" is used
;  guest account = pcguest

# this tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 50

# Use password server option only with security = server
# The argument list may include:
#   password server = My_PDC_Name [My_BDC_Name] [My_Next_BDC_Name]
# or to auto-locate the domain controller/s
#   password server = *
;   password server = <NT-Server-Name>

# Use the realm option only with security = ads
# Specifies the Active Directory realm the host is part of
;   realm = MY_REALM

# Backend to store user information in. New installations should 
# use either tdbsam or ldapsam. smbpasswd is available for backwards 
# compatibility. tdbsam requires no further configuration.
;   passdb backend = tdbsam

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting.
# Note: Consider carefully the location in the configuration file of
#       this line.  The included file is read at that point.
;   include = /etc/samba/smb.conf.%m

# Configure Samba to use multiple interfaces
# If you have multiple network interfaces then you must list them
# here. See the man page for details.
;   interfaces = 192.168.12.2/24 192.168.13.2/24 

# Browser Control Options:
# set local master to no if you don't want Samba to become a master
# browser on your network. Otherwise the normal election rules apply
;   local master = no

# OS Level determines the precedence of this server in master browser
# elections. The default value should be reasonable
;   os level = 33

# Domain Master specifies Samba to be the Domain Master Browser. This
# allows Samba to collate browse lists between subnets. Don't use this
# if you already have a Windows NT domain controller doing this job
;   domain master = yes 

# Preferred Master causes Samba to force a local browser election on startup
# and gives it a slightly higher chance of winning the election
;   preferred master = yes

# Enable this if you want Samba to be a domain logon server for 
# Windows95 workstations. 
;   domain logons = yes

# if you enable domain logons then you may want a per-machine or
# per user logon script
# run a specific logon batch file per workstation (machine)
;   logon script = %m.bat
# run a specific logon batch file per username
;   logon script = %U.bat

# Where to store roving profiles (only for Win95 and WinNT)
#        %L substitutes for this servers netbios name, %U is username
#        You must uncomment the [Profiles] share below
;   logon path = \\%L\Profiles\%U

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable it's WINS Server
;   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
#    Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# WINS Proxy - Tells Samba to answer name resolution queries on
# behalf of a non WINS capable client, for this to work there must be
# at least one    WINS Server on the network. The default is NO.
;   wins proxy = yes

# DNS Proxy - tells Samba whether or not to try to resolve NetBIOS names
# via DNS nslookups. The default is NO.
   dns proxy = no 

# These scripts are used on a domain controller or stand-alone 
# machine to add or delete corresponding unix accounts
;  add user script = /usr/sbin/useradd %u
;  add group script = /usr/sbin/groupadd %g
;  add machine script = /usr/sbin/adduser -n -g machines -c Machine -d /dev/null -s /bin/false %u
;  delete user script = /usr/sbin/userdel %u
;  delete user from group script = /usr/sbin/deluser %u %g
;  delete group script = /usr/sbin/groupdel %g


#============================ Share Definitions ==============================
[homes]
   comment = Home Directories
   browseable = no
   writable = yes

# Un-comment the following and create the netlogon directory for Domain Logons
; [netlogon]
;   comment = Network Logon Service
;   path = /var/lib/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no


# Un-comment the following to provide a specific roving profile share
# the default is to use the user's home directory
;[Profiles]
;    path = /var/lib/samba/profiles
;    browseable = no
;    guest ok = yes


# NOTE: If you have a BSD-style print system there is no need to 
# specifically define each individual printer
[printers]
   comment = All Printers
   path = /var/spool/samba
   browseable = no
   public = yes
   guest ok = no
   writable = no
   printable = yes

# This one is useful for people to share files
;[tmp]
;   comment = Temporary file space
;   path = /tmp
;   read only = no
;   public = yes

# A publicly accessible directory, but read only, except for people in
# the "staff" group
;[public]
;   comment = Public Stuff
;   path = /home/samba
;   public = yes
;   writable = yes
;   printable = no
;   write list = @staff

# Other examples. 
#
# A private printer, usable only by fred. Spool data will be placed in fred's
# home directory. Note that fred must have write access to the spool directory,
# wherever it is.
;[fredsprn]
;   comment = Fred's Printer
;   valid users = fred
;   path = /homes/fred
;   printer = freds_printer
;   public = no
;   writable = no
;   printable = yes

# A private directory, usable only by fred. Note that fred requires write
# access to the directory.
;[fredsdir]
;   comment = Fred's Service
;   path = /usr/somewhere/private
;   valid users = fred
;   public = no
;   writable = yes
;   printable = no

# a service which has a different directory for each machine that connects
# this allows you to tailor configurations to incoming machines. You could
# also use the %U option to tailor it by user name.
# The %m gets replaced with the machine name that is connecting.
;[pchome]
;  comment = PC Directories
;  path = /usr/pc/%m
;  public = no
;  writable = yes

# A publicly accessible directory, read/write to all users. Note that all files
# created in the directory by users will be owned by the default user, so
# any user with access can delete any other user's files. Obviously this
# directory must be writable by the default user. Another user could of course
# be specified, in which case all files would be owned by that user instead.
[Public]
    comment = PublicShare
    path = /home/narthir/Public
public= yes
    writeable = yes
browseable = yes
    valid users = narthir

```ive already added your share onto the config.

To add more, 
run this
```

sudo apt-get install system-config-samba
gksudo system-config-samba
```press the "+" button

make sure you set the visible and writable flags, you forgot that in your initial config.

YOUR_WORKGOUP and COMPUTERDESCRIPTION should be changed to the correct values for your computer


and then
Reset Firewall
```

sudo iptables --flush

```

Dont ever touch the firewall unless your computer is WAN facing, because ubuntu automatically opens and closes ports

---

### Post by narthir on 2010-10-19
Ok, i used the samba file (changed the net bios name, network, desc etc) and flushed my firewall. I can see now the shares, and access the windows shares. But the windows pc cant see me (i set up wins, but i also tried over the ip), and i cant access my own shares (the one from the linux box i sitting on). I created a smb user same as my linux user but cant log in.

---

### Post by luvshines on 2010-10-19
Just make sure that the shared path has permission 0755(atleast) at each directory starting from / upto Public

Can you access the shares from terminal:
```
smbclient //<server-ip>/<share-name> -U<narthir>%<samba-pwd-for-narthir>
```

---

### Post by CharlesA on 2010-10-19
> **narthir said:**
> Ok, i used the samba file (changed the net bios name, network, desc etc) and flushed my firewall. I can see now the shares, and access the windows shares. But the windows pc cant see me (i set up wins, but i also tried over the ip), and i cant access my own shares (the one from the linux box i sitting on). I created a smb user same as my linux user but cant log in.

Can you connect by typing in the ip address instead of the hostname?

---

### Post by narthir on 2010-10-19
luvshines: They all are 755 (Public ist even 777)
using sthe smbclient gives me that:

Domain=[NERV] OS=[Unix] Server=[Samba 3.4.7]
Server not using user level security and no password supplied.
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: NT_STATUS_ACCESS_DENIED

and as it says i wanted to use share, not user level security (the other XP pc is from my roommate and i dont want him to have an account on my pc)

CharlesA: i cant acces them by typing in the ip (nor from windows or another linux).

---

### Post by luvshines on 2010-10-19
> **narthir said:**
> luvshines: They all are 755 (Public ist even 777)
using sthe smbclient gives me that:

Domain=[NERV] OS=[Unix] Server=[Samba 3.4.7]
Server not using user level security and no password supplied.
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: NT_STATUS_ACCESS_DENIED

and as it says i wanted to use share, not user level security (the other XP pc is from my roommate and i dont want him to have an account on my pc)


OK, so you want your roommate to use your name to connect to the shares ?

---

### Post by narthir on 2010-10-19
I was thinking of something like giving him an samba account but no linux user account, is that possible?

---

### Post by CharlesA on 2010-10-19
> **narthir said:**
> 
CharlesA: i cant acces them by typing in the ip (nor from windows or another linux).

It's not only a name resolution problem then.

Is there anything listed for port 445 and 139 in netstat?

```
netstat -ln
```

> **narthir said:**
> I was thinking of something like giving him an samba account but no linux user account, is that possible?

As for this, you can create a unix account and set the shell to /dev/null, and then add a user with ***smbpasswd -a***

---

### Post by luvshines on 2010-10-19
> **narthir said:**
> I was thinking of something like giving him an samba account but no linux user account, is that possible?

Yes, it is very much possible :)
I think you need a guest share who can read/write.
Can you remove the 'valid users' parameter from under the [Public] share section, since that can be an issue.
Also add to the [global] section:
```
map to guest = bad user
```

Do these changes, restart the service and give it a try

---

### Post by narthir on 2010-10-19
I changed the Share acces to Everyone and now i can see my samba shares from my linux boxes, but still no luck from windows.

netstat (i hope its what You meant):
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN  


My samba.conf at the time being:
netbios name gets Commented now and then after making changes with system-config-samba

```

# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options (perhaps too
# many!) most of which are not shown in this example
#
# For a step to step guide on installing, configuring and using samba, 
# read the Samba-HOWTO-Collection. This may be obtained from:
#  http://www.samba.org/samba/docs/Samba-HOWTO-Collection.pdf
#
# Many working examples of smb.conf files can be found in the 
# Samba-Guide which is generated daily and can be downloaded from: 
#  http://www.samba.org/samba/docs/Samba-Guide.pdf
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentry and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command "testparm"
# to check that you have not made any basic syntactic errors. 
#
#======================= Global Settings =====================================
[global]

# workgroup = NT-Domain-Name or Workgroup-Name, eg: MIDEARTH
    workgroup = NERV

;    netbios name = UNIT-00

# server string is the equivalent of the NT Description field
    server string = Unit-00

;    usershare owner only = false

# Security mode. Defines in which mode Samba will operate. Possible 
# values are share, user, server, domain and ads. Most people will want 
# user level security. See the Samba-HOWTO-Collection for details.
    security = share

# This option is important for security. It allows you to restrict
# connections to machines which are on your local network. The
# following example restricts access to two C class networks and
# the "loopback" interface. For more examples of the syntax see
# the smb.conf man page
;   hosts allow = 192.168.1. 192.168.2. 127.

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;    load printers = yes

# you may wish to override the location of the printcap file
;   printcap name = /etc/printcap

# on SystemV system setting printcap name to lpstat should allow
# you to automatically obtain a printer list from the SystemV spool
# system
;   printcap name = lpstat

# It should not be necessary to specify the print system type unless
# it is non-standard. Currently supported print systems include:
# bsd, cups, sysv, plp, lprng, aix, hpux, qnx
;    printing = cups

# Uncomment this if you want a guest account, you must add this to /etc/passwd
# otherwise the user "nobody" is used
;  guest account = pcguest

# this tells Samba to use a separate log file for each machine
# that connects
    log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
    max log size = 50

# Use password server option only with security = server
# The argument list may include:
#   password server = My_PDC_Name [My_BDC_Name] [My_Next_BDC_Name]
# or to auto-locate the domain controller/s
#   password server = *
;   password server = <NT-Server-Name>

# Use the realm option only with security = ads
# Specifies the Active Directory realm the host is part of
;   realm = MY_REALM

# Backend to store user information in. New installations should 
# use either tdbsam or ldapsam. smbpasswd is available for backwards 
# compatibility. tdbsam requires no further configuration.
;    passdb backend = tdbsam

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting.
# Note: Consider carefully the location in the configuration file of
#       this line.  The included file is read at that point.
;   include = /etc/samba/smb.conf.%m

# Configure Samba to use multiple interfaces
# If you have multiple network interfaces then you must list them
# here. See the man page for details.
;   interfaces = 192.168.12.2/24 192.168.13.2/24 

# Browser Control Options:
# set local master to no if you don't want Samba to become a master
# browser on your network. Otherwise the normal election rules apply
;   local master = no

# OS Level determines the precedence of this server in master browser
# elections. The default value should be reasonable
;   os level = 33

# Domain Master specifies Samba to be the Domain Master Browser. This
# allows Samba to collate browse lists between subnets. Don't use this
# if you already have a Windows NT domain controller doing this job
;   domain master = yes 

# Preferred Master causes Samba to force a local browser election on startup
# and gives it a slightly higher chance of winning the election
;   preferred master = yes

# Enable this if you want Samba to be a domain logon server for 
# Windows95 workstations. 
;   domain logons = yes

# if you enable domain logons then you may want a per-machine or
# per user logon script
# run a specific logon batch file per workstation (machine)
;   logon script = %m.bat
# run a specific logon batch file per username
;   logon script = %U.bat

# Where to store roving profiles (only for Win95 and WinNT)
#        %L substitutes for this servers netbios name, %U is username
#        You must uncomment the [Profiles] share below
;   logon path = \\%L\Profiles\%U

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable it's WINS Server
    wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
#    Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# WINS Proxy - Tells Samba to answer name resolution queries on
# behalf of a non WINS capable client, for this to work there must be
# at least one    WINS Server on the network. The default is NO.
;   wins proxy = yes

# DNS Proxy - tells Samba whether or not to try to resolve NetBIOS names
# via DNS nslookups. The default is NO.
    dns proxy = no

# These scripts are used on a domain controller or stand-alone 
# machine to add or delete corresponding unix accounts
;  add user script = /usr/sbin/useradd %u
;  add group script = /usr/sbin/groupadd %g
;  add machine script = /usr/sbin/adduser -n -g machines -c Machine -d /dev/null -s /bin/false %u
;  delete user script = /usr/sbin/userdel %u
;  delete user from group script = /usr/sbin/deluser %u %g
;  delete group script = /usr/sbin/groupdel %g


#============================ Share Definitions ==============================
[homes]
    comment = Home Directories
    browseable = no
    writable = yes

# Un-comment the following and create the netlogon directory for Domain Logons
; [netlogon]
;   comment = Network Logon Service
;   path = /var/lib/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no


# Un-comment the following to provide a specific roving profile share
# the default is to use the user's home directory
;[Profiles]
;    path = /var/lib/samba/profiles
;    browseable = no
;    guest ok = yes


# NOTE: If you have a BSD-style print system there is no need to 
# specifically define each individual printer
[printers]
    comment = All Printers
    path = /var/spool/samba
    browseable = no
    public = yes
;    writable = No
    printable = yes

# This one is useful for people to share files
;[tmp]
;   comment = Temporary file space
;   path = /tmp
;   read only = no
;   public = yes

# A publicly accessible directory, but read only, except for people in
# the "staff" group
;[public]
;   comment = Public Stuff
;   path = /home/samba
;   public = yes
;   writable = yes
;   printable = no
;   write list = @staff

# Other examples. 
#
# A private printer, usable only by fred. Spool data will be placed in fred's
# home directory. Note that fred must have write access to the spool directory,
# wherever it is.
;[fredsprn]
;   comment = Fred's Printer
;   valid users = fred
;   path = /homes/fred
;   printer = freds_printer
;   public = no
;   writable = no
;   printable = yes

# A private directory, usable only by fred. Note that fred requires write
# access to the directory.
;[fredsdir]
;   comment = Fred's Service
;   path = /usr/somewhere/private
;   valid users = fred
;   public = no
;   writable = yes
;   printable = no

# a service which has a different directory for each machine that connects
# this allows you to tailor configurations to incoming machines. You could
# also use the %U option to tailor it by user name.
# The %m gets replaced with the machine name that is connecting.
;[pchome]
;  comment = PC Directories
;  path = /usr/pc/%m
;  public = no
;  writable = yes

# A publicly accessible directory, read/write to all users. Note that all files
# created in the directory by users will be owned by the default user, so
# any user with access can delete any other user's files. Obviously this
# directory must be writable by the default user. Another user could of course
# be specified, in which case all files would be owned by that user instead.
[Public]
    comment = PublicShare
    path = /home/narthir/Public
    writeable = yes
;    browseable = yes
    guest ok = yes
    map to guest = bad user


```

---

### Post by luvshines on 2010-10-19
Gud, atleast it works on Linux box now.

BTW, I forgot to add (now I have edited the previous post), 'map to guest' should go in the [global] section itself, **please make that change**

If now you hit the command
```
smbclient //<ip>/<share-name> -U%
```

it gives access, right ?

Also through nautilus ?

---

### Post by narthir on 2010-10-19
Ok, i changed the [global]. After some test i found out that:

auth mode: share + selcted user = doesnt work
auth mode: share + everyone =  work


auth mode: user + selcted user =  work
auth mode: user + everyone =  work

So i guess vor now i stik with auth mode user

Futhermore: "smbclient //192.../public -U"  works now for both users.

So i assume the linux to linux part works now, so thanks for that guys :)

Now the XP. Meybe its nothing but if I enter the \\192.168.0.159\ in IE, yeah he uses IE :/, i can see the shares on the pc but if i open the "Show workgroup coputers" there is none listed there, even the box itself.

UPDATE:  there is still the posibility that there ist still something with the firewall. After reboot i couldnt connect to internet. I stopped and startet (restarted) it with Firestarter and it was back to normal.

UPDATE: I just looked up firestarter:

Time: Oct 19 20:53:20 Source: 192.168.0.159 Destination: 192.168.0.101 In IF: eth0 Out IF:  Port: 137 Length: 96 ToS: 0x00 Protocol: UDP Service: Samba (SMB)
Time: Oct 19 20:55:51 Source: 192.168.0.123 Destination: 192.168.0.101 In IF: eth0 Out IF:  Port: 137 Length: 90 ToS: 0x00 Protocol: UDP Service: Samba (SMB)
Time: Oct 19 20:57:16 Source: 192.168.0.159 Destination: 192.168.0.101 In IF: eth0 Out IF:  Port: 137 Length: 96 ToS: 0x00 Protocol: UDP Service: Samba (SMB)

There are marked red and under blocked.
Should I:
Allow connections from source
Allow inbound service for everyone
Allow inbound service for source

---

### Post by luvshines on 2010-10-19
> **narthir said:**
> Ok, i changed the [global]. After some test i found out that:

auth mode: share + selcted user = doesnt work
auth mode: share + everyone =  work


auth mode: user + selcted user =  work
auth mode: user + everyone =  work


I am assuming by 'everyone' you mean without username/passwd, that is guest, right ??
For share + selected user, what does smbclient command complain ?

---

### Post by narthir on 2010-10-19
Yes, i meant the guest account.

smbclient gives me:

Domain=[NERV] OS=[Unix] Server=[Samba 3.4.7]
Server not using user level security and no password supplied.
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: NT_STATUS_ACCESS_DENIED

P.S. Did You see me last post update? I wrote it a few seconds before you post. Does it change something?

---

### Post by luvshines on 2010-10-19
> **narthir said:**
> Yes, i meant the guest account.

smbclient gives me:

Domain=[NERV] OS=[Unix] Server=[Samba 3.4.7]
Server not using user level security and no password supplied.
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: NT_STATUS_ACCESS_DENIED

P.S. Did You see me last post update? I wrote it a few seconds before you post. Does it change something?

My firewalls skill suck, so I best not comment on them :). Let's see if any expert can suggest something useful

For the other thing, since it says, 'client lanman auth' is disabled, adding to [global] section
```
client lanman auth = yes
```

should resolve it. Also just going through the man page again, I realised that 'map to guest' is redundant in security = share mode, you may remove that since we are allowing guest anyways

---

### Post by Morbius1 on 2010-10-19
Man, there's a little bit of everything going on in this post.

[1] lanman error

You're probably getting the lanman error because you're using share level security. "client lanman auth" would probably work but only because your running smbclient on your own server machine. "client lanman auth" is something you add to the client of the server not the server itself.

If it were me I would dump the share level security altogether and revert everything back to the defaults:
```
security = user
map to guest = Bad User
```[2] > I was thinking of something like giving him an samba account but no linux user account, is that possible?Yes:
```
sudo useradd -s /bin/true RemoteUserName
```This will create a local user on the server that has no local login password and no home directory.
Then add a samba password:
```
sudo smbpasswd -a RemoteUserName
```[COLOR=Blue]*Change RemoteUserName to whatever you want.*[/COLOR]
[3] Firestarter
It's been an impediment to samba since it's creation and it should be purged from the repositories. But that's just my opinion. I don't use it. I just run with the defaults so I can't add anything to this discussion.

If you want you can run the following command to see what ports are open on your server:
```
sudo nmap -sS -sU -T4 192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of the server*[/COLOR]

[4] As for the name resolution problem I noticed this in your smb.conf:
> wins support = yes You've turned your Linux machine into a wins server. If you made modifications to all the client machines on your network you shouldn't have any name resolution problem.  So I'm a little confused by the problem. Maybe it's firewall related.

---

### Post by narthir on 2010-10-19
Ok, I am stalling this thread for now and make a new one about the firewall problem, i think it can have something to do with it. Let see if it changes something.

---

