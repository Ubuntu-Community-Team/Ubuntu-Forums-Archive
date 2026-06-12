---
title: "FreeBSD and Ubunut Netoworking"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by appzattak on 2007-08-02
Hey all, I have a FreeBSD 6 (latest Stable) and an Ubuntu 7.04 workstation. I can access shares from FreeBSD to the Ubuntu box, and I can access the FreeBSD box from within VMware (xp pro), as well as from my 2003 server machine. My problem is that from Ubuntu I cannot access the FreeBSD shares, I get " the folder contents could not be displayed. Sorry couldn't display all of the contents of " Windows Network: boaz".

I made sre the FreeBSD samba is pretty much wide open, and I know it works from windows boxes.

Any ideas, I'm at a lost.

--Steve

---

### Post by appzattak on 2007-08-03
any one??

I have to say, I've posted like 3 or 4 times on this board and I've never got any response on any of them, ended up just figuring it out......

---

### Post by noob12 on 2007-08-03
This happened to me once, but I'm not sure I remember what I did exactly. I think in my case it was due to a stale key in my keyring.  I think my username/password info was being sent even though it wasn't required, but because the password was wrong the connection failed.

Try **smbget -a *smbpath*** (**man smbget** for details), and if that works it's an indication that you should look in your keyring (System | Administration | Keyring Manager) and see if you have a key for that specific smb share.  Try deleting it and then connecting again.

---

### Post by appzattak on 2007-08-03
thanks mate, I'll look at that when I get home this evening.

--Steve

---

### Post by appzattak on 2007-08-10
well I did that and get this.

steve@2nd2none:~$ smbget -a smb://boaz
Using workgroup MARINTECH, guest user
smbc_open: Connection timed out
steve@2nd2none:~$ 


There is no keyring entry for that server. This is driving me crazy that I cannot access it.

Anyone else have any ideas I can try. How can I manually enter the info needed.

I seen something like this but not sure of the correct syntax.

smb://mydomina;username:password@server/share


Here is my smb config file

> # This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options (perhaps too
# many!) most of which are not shown in this example
#
# For a step to step guide on installing, configuring and using samba, 
# read the Samba-HOWTO-Collection. This may be obtained from:
#  [http://www.samba.org/samba/docs/Samba-HOWTO-Collection.pdf](http://www.samba.org/samba/docs/Samba-HOWTO-Collection.pdf)
#
# Many working examples of smb.conf files can be found in the 
# Samba-Guide which is generated daily and can be downloaded from: 
#  [http://www.samba.org/samba/docs/Samba-Guide.pdf](http://www.samba.org/samba/docs/Samba-Guide.pdf)
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
	log file = /var/log/samba/log.%m
	dns proxy = no 
	load printers = yes
	netbios name = Boaz
	socket options = TCP_NODELAY
	hosts equiv = 172.16.0.120
	default = homes
	wins server = 172.16.0.10
	workgroup = MARINTECH
	os level = 20
	null passwords = yes
	username map = /usr/local/etc/user.map
	winbind trusted domains only = yes
	max log size = 50

# workgroup = NT-Domain-Name or Workgroup-Name, eg: MIDEARTH

# server string is the equivalent of the NT Description field

# Security mode. Defines in which mode Samba will operate. Possible 
# values are share, user, server, domain and ads. Most people will want 
# user level security. See the Samba-HOWTO-Collection for details.

# This option is important for security. It allows you to restrict
# connections to machines which are on your local network. The
# following example restricts access to two C class networks and
# the "loopback" interface. For more examples of the syntax see
# the smb.conf man page
;   hosts allow = 192.168.1. 192.168.2. 127.

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this

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

# Put a capping on the size of the log files (in Kb).

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
;   include = /usr/local/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See the chapter 'Samba performance issues' in the Samba HOWTO Collection
# and the manual pages for details.
# You may want to add the following on a Linux system:
;   socket options = SO_RCVBUF=8192 SO_SNDBUF=8192

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
#	Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# WINS Proxy - Tells Samba to answer name resolution queries on
# behalf of a non WINS capable client, for this to work there must be
# at least one	WINS Server on the network. The default is NO.
;   wins proxy = yes

# DNS Proxy - tells Samba whether or not to try to resolve NetBIOS names
# via DNS nslookups. The default is NO.

# Charset settings
;   display charset = koi8-r
;   unix charset = koi8-r
;   dos charset = cp866

# Use extended attributes to store file modes
;    store dos attributes = yes
;    map hidden = no
;    map system = no
;    map archive = no

# Use inherited ACLs for directories
;    nt acl support = yes
;    inherit acls = yes
;    map acl inherit = yes 

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
;   path = /usr/local/samba/lib/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no


# Un-comment the following to provide a specific roving profile share
# the default is to use the user's home directory
;[Profiles]
;    path = /usr/local/samba/profiles
;    browseable = no
;    guest ok = yes


# NOTE: If you have a BSD-style print system there is no need to 
# specifically define each individual printer
[printers]
   comment = All Printers
   path = /var/spool/samba
   browseable = no
# Set public = yes to allow user 'guest account' to print
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
;[public]
;   path = /usr/somewhere/else/public
;   public = yes
;   only guest = yes
;   writable = yes
;   printable = no

# The following two entries demonstrate how to share a directory so that two
# users can place files there that will be owned by the specific users. In this
# setup, the directory should be writable by both users and should have the
# sticky bit set on it to prevent abuse. Obviously this could be extended to
# as many users as required.
;[myshare]
;   comment = Mary's and Fred's stuff
;   path = /usr/somewhere/shared
;   valid users = mary fred
;   public = no
;   writable = yes
;   printable = no
;   create mask = 0765

[share]
	comment = Server Share
	writeable = yes
	public = yes
	create mode = 777
	path = /home/share
	directory mode = 777


---

### Post by appzattak on 2007-08-11
**bump**

Any gurus here that can lend a helping hand??

---

### Post by appzattak on 2007-08-11
dang...guess no one knows...........

---

### Post by appzattak on 2007-08-14
bump

---

