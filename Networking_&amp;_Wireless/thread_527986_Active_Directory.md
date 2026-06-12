---
title: "Active Directory"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by kingpoiuy on 2007-08-17
I know there are tons of AD posts but none of them have gotten me on the netowork here.  So if anyone is willing to help me that would be great.

Here is the situation:

I have set up a couple servers here at work for doing backups on windows machines.  (I work for IT at a large corporation)  It works great.  I have samba and everything set up just fine.  The problem is that DNS doesn't work throughout the entire network.  I can use the computer name here in the office and it will broadcast that just fine.  But if I go to a computer on another switch then I have to use the IP address to access the server.  The IP address is bound to change in the near future causing me to change all my scripts again.  

Anyway my main goal is to join these computers to the domain so I can get name resolution.  

```
# smb.conf
# SAMBA CONFIG FILE
# SADMS
# 2007-06-21

[global]

# netbios name
        netbios name = aashbyctest

# server string is the equivalent of the NT Description field
        server string = Samba Server aashbyctest

# realm = Kerberos realm
        realm = AG.NA.FOO.COM

# workgroup = NT-Domain-Name or Workgroup-Name
        workgroup = AGNA

# Security mode.
        security = ADS

# Use password server option only with security = server
        password server = *

# Password encryption
        encrypt passwords = yes

# This option is important for security. It allows you to restrict
# connections to machines which are on your local network.
        hosts allow = 10.20.25.0/255.255.255.0 127.
        hosts deny = 0.0.0.0/0.0.0.0

# Uncomment this if you want a guest account, you must add this to /etc/passwd
# otherwise the user "nobody" is used
        guest account = nobody

# this tells Samba to use a separate log file for each machine
# that connects
;       log file = /var/log/samba/%m.log;
        log file = /var/log/samba/samba.log

# The following are needed to allow password changing from Windows to
# update the Linux system password also.
# noTE: Use these with 'encrypt passwords' and 'smb passwd file' above.
# noTE2: You do noT need these to allow workstations to change only
#        the encrypted SMB passwords. They allow the Unix password
#        to be kept in sync with the SMB password.
;       unix password sync = yes
;       passwd program = /usr/bin/passwd %u
;       passwd chat = *New*UNIX*password* %n\n *ReType*new*UNIX*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*

# Unix users can map to different SMB User names
        username map = /etc/samba/user.map

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;       include = /etc/samba/smb.conf.%m

# Most people will find that this option gives better performance.
# See speed.txt and the manual pages for details
        socket options = TCP_noDELAY SO_RCVBUF=8192 SO_SNDBUF=8192

# All NetBIOS names must be resolved to IP Addresses
# 'Name Resolve Order' allows the named resolution mechanism to be specified
# the default order is "host lmhosts wins bcast". "host" means use the unix
# system gethostbyname() function call that will use either /etc/hosts OR
# DNS or NIS depending on the settings of /etc/host.config, /etc/nsswitch.conf
# and the /etc/resolv.conf file. "host" therefore is system configuration
# dependant. This parameter is most often of use to prevent DNS lookups
# in order to resolve NetBIOS names to IP Addresses. Use with care!
# The example below excludes use of name resolution for machines that are noT
# on the local network segment
# - OR - are not deliberately to be known via lmhosts or via WINS.
;       name resolve order = wins lmhosts bcast

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable it's WINS Server
;       wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
#       note: Samba can be either a WINS Server, or a WINS Client, but noT both
;       wins server =

# if you want to automatically load your printer list rather
# than setting them up individually then you'll need this
        printcap name = /etc/printcap
        load printers = yes

# It should not be necessary to spell out the print system type unless
# yours is non-standard. Currently supported print systems include:
# bsd, sysv, plp, lprng, aix, hpux, qnx
;       printing = lprng

# DNS Proxy - tells Samba whether or not to try to resolve NetBIOS names
# via DNS nslookups. The built-in default for versions 1.9.17 is yes,
# this has been changed in version 1.9.18 to no.
        dns proxy = no

# PAM-related
        obey pam restrictions = yes
        pam password change = yes

# Winbind separator
        winbind separator = /

# Winbind use default domain
# This parameter specifies whether the winbindd daemon should
# operate on users without domain component in their username.
# Users without a domain component are treated as is part of
# the winbindd server's own domain. While this does not benefit
# Windows users, it makes SSH, FTP and e-mail function in a way
# much closer to the way they would in a native unix system.
# Default: winbind use default domain = no
        winbind use default domain = yes
:
# RID to UID map
        idmap backend = rid:"BUILTIN=1000-9999,AGNA=10000-60000"

;       idmap domains = AGNA
;       idmap config AGNA:backend = rid
;       idmap config AGNA:range = 10000-60000
;       idmap config BUILTIN:backend = rid
;       idmap config BUILTIN:range = 1000-9999

# RID idmap does not work with trusted domains
        allow trusted domains = no

# Domain user id range
        idmap uid = 1000-60000

# Domain group id range
        idmap gid = 1000-60000

# Allow enumeration of domain users and groups
        winbind enum users = yes
        winbind enum groups = yes

# Allow nested groups
;       winbind nested groups = yes

# Winbind templates
# This parameter is designed to control how Winbind retrieves
# Name Service Information to construct a user's home directory
# and login shell. Currently the following settings are available:
# - template - The default, using the parameters of template shell
# and template homedir)
# - sfu - When Samba is running in security = ads and your Active
# Directory Domain Controller does support the Microsoft "Services
# for Unix" (SFU) LDAP schema, winbind can retrieve the login shell
# and the home directory attributes directly from your Directory
# Server. Note that retrieving UID and GID from your ADS-Server
# requires to use idmap backend = idmap_ad as well.
;       winbind nss info = template

# When filling out the user information for a Windows NT user, the
# winbindd(8) daemon uses this  parameter  to  fill  in  the  home
# directory  for that user. If the string %D is present it is sub-
# stituted with the userâs Windows NT domain name. If  the  string
# %U  is present it is substituted with the userâs Windows NT user
# name.
        template homedir = /home/%U

# When filling out the user information for a Windows NT user, the
# winbindd(8)  daemon  uses  this  parameter  to fill in the login
# shell for that user.
        template shell = /bin/bash

# This option defines the default primary group for each user cre-
# ated  by winbindd(8)âs local account management functions (simi-
# lar to the âadd user scriptâ).
;       template primary group = "AGNA/Domain Users"
;       template primary group = "Domain Users"

# Services
        default service = homes
        preload = global homes printers

# Default share values
        valid users = @"AGNA/Domain Users"
        admin users = "AGNA/aashbyc"

#==================


[homes]
        comment = Home Directory
        browseable = no
        writable = yes
        valid users = @"AGNA/Domain Users"
;       read only = No
;       create mask = 0664
;       directory mask = 0775

[users]
        path = /home
        comment = All Home Directories
        browseable = yes
        writable = yes
        valid users = @"AGNA/Domain Users"
        admin users = "AGNA/aashbyc"
        read list = @"AGNA/Domain Users"
        write list = @"AGNA/Domain Users"

[data]
        path = /data
        comment = Data
        browseable = yes
        writable = yes
        valid users = @"AGNA/Domain Users"
        admin users = "AGNA/aashbyc"
        read list = @"AGNA/Domain Users"
        write list = @"AGNA/Domain Users"

;[tmp]
;       comment = Temporary file space
;       path = /tmp
;       read only = no
;       public = yes

# NOTE: If you have a BSD-style print system there is no need to
# specifically define each individual printer
[printers]
        comment = All Printers
        path = /var/spool/samba
        browseable = no
        guest ok = no
        writable = no
        printable = yes
        ;public = yes
        ;to allow user 'guest account' to print

```

/etc/hosts
```


127.0.0.1       aashbyctest.ag.na.foo.com       localhost       aashbyctest

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
10.20.25.186            aashbyctest.ag.na.foo.com
10.20.25.186            aashbyctest.ag.na.foo.com
10.20.25.186            aashbyctest.ag.na.foo.com
10.20.25.186            aashbyctest.ag.na.foo.com

```

/etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```



When I run Sadms I get

> 
got ticket-granting ticket for principal krbtgt/AG.NA.FOO.COM@AG.NA.FOO.COM
blah
blah
blah
join failed and returned 255

 
Well....what else you guys need to see?

Any ideas?  Thanx for any help!

---

### Post by ihristov on 2007-08-17
I might be wrong, but frankly I don't see why would DNS resolution be dependant on joining the domain.

It is all a matter of the DHCP server updating the DNS server.

I have a setup with Windows 2000 Server Active directory server and it works fine regarding the resolution of names, no matter if the DHCP client is a linux box or an embedded Netburner module or a hardware SIP VoIP phone. And no one is joining the domain either.

---

### Post by destr0y on 2007-08-29
> I might be wrong, but frankly I don't see why would DNS resolution be dependant on joining the domain.

It is all a matter of the DHCP server updating the DNS server.



Yep, thats correct.  I came across this problem today, and for me, it was a case of my /etc/nsswitch.conf file not being configured properly.  I half suspect this was caused by the installation of either samba, smbclient or winbind.  The offending part of my nsswitch.conf file read:

> 
hosts:      files files


but I needed to change it to: 

> 
hosts:      dns files


to restore name resolution.

I found this at [http://www.faqs.org/docs/securing/chap6sec71.html](http://www.faqs.org/docs/securing/chap6sec71.html), but after searching these forums for "nsswitch.conf" have found others confirming the same thing here.

Hope this helps..

Brett

---

