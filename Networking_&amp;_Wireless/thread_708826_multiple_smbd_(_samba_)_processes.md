---
title: "multiple smbd ( samba ) processes"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by aBitLater on 2008-02-26
is it normal to have multiple smbd processes running? I'm not accessing any shares on other computers (can't get it to work).

this:
```
ps aux | grep -i "smb"
```

yields this:

```
root      6215  0.0  0.1   9900  2276 ?        Ss   20:49   0:00 /usr/sbin/smbd -D
root      6234  0.0  0.0   9900   916 ?        S    20:49   0:00 /usr/sbin/smbd -D
root      7124  0.0  0.1  10240  2104 ?        S    20:50   0:00 /usr/sbin/smbd -D
root      7125  0.0  0.1  10240  2120 ?        S    20:50   0:00 /usr/sbin/smbd -D
root      7191  0.0  0.1  10236  2208 ?        S    20:52   0:00 /usr/sbin/smbd -D

```

---

### Post by jhetrick62 on 2008-02-27
I have that many running on my FC file server and it has no problems.  If you are trying to access share located on OTHER computers, you don't need this anyway.  If you are trying to access shares on THIS computer, that is different.

Jeff

---

### Post by aBitLater on 2008-02-27
Thanks Jeff,

I'm using samba because I had it set up previously when windows was on my other machine.  Now I have opensuse on the other machine, and it works, but ubuntu's samba doesn't want to work.

---

### Post by dmizer on 2008-02-27
it is normal to have several active instances of smb appearing in your process list even if it is idle.

what part of samba does not work?  are you unable to see shares on opensuse, or is opensuse unable to see shares on ubuntu

---

### Post by aBitLater on 2008-02-28
NOTE: I wrote this response below, and thought it might be confusing, so I'll clarify here at the outset:  I have two computers, machine1 and machine2.

Machine1 dual boots to OpenSuse and Ubuntu.  I plan to delete Ubuntu from this machine at some point in the future.

Machine2 boots only ubuntu.  

My ultimate goal is to get machine1 (opensuse) to share with machine2 (ubuntu).

Samba works partially when machine1 is booted to ubuntu, but since ubuntu will be deleted later, this does not help my situation.

---------------------------

I *was* able to see shares from opensuse (machine1) to ubuntu (machine2) and vice-versa, though I could *not* access the shares in either direction. Then I tried setting up samba on the ubuntu (machine2) through swat, the same way I set up opensuse's samba (machine1), according to this how-to:

[http://tweakhound.com/linux/samba/page_3.htm]("http://tweakhound.com/linux/samba/page_3.htm")

After setting up samba on ubuntu (machine2) according to the link above, I can't even see shares any longer, from either machine.

I had used this how-to earlier in the year, when I had opensuse on machine1 and winxp on machine2, and it worked then. 

 I'm working with a fresh install of opensuse on machine1 now, and this machine dual boots also to ubuntu.  From this machine, if I boot to ubuntu, I can see shares on ubuntu machine2, though I can't read from or write to the shares on machine2.  I get permission errors.

When machine1 is booted to ubuntu, I can see shares on machine1 while working on ubuntu at machine2.  I can copy files from the shares on machine1 to machine2, but I can't write to the shared folders on machine1, nor can I delete files on machine1, again permission errors.

Hope that made sense.

---

### Post by Eiríkr on 2008-02-28
Please post your [font=courier]/etc/samba/smb.conf[/font] files for both machines, specifying which is which.  Once we have those we can begin the process of more detailed diagnosis.  

Cheers,

Eiríkr

PS -- In my (somewhat limited) experience autoconfig tools sometimes produce haphazard results, likely due in part to different versions of both the configuring and configured packages.  Sometimes it's best to just get your hands dirty and dive into the conf files themselves.  :)

---

### Post by aBitLater on 2008-02-29
Thanks Eiríkr

Here they are.  Machine1 first - the opensuse and ubuntu versions (dual boot). Followed by the Machine2 ubuntu smb.conf.  All your help is really appreciated.

Machine1_opensuse_smb.conf
```

# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2008/02/26 16:57:03

[global]
workgroup = MYNET
map to guest = Bad User
printcap name = cups
add machine script = /usr/sbin/useradd  -c Machine -d /var/lib/nobody -s /bin/false %m$
logon path = \\%L\profiles\.msprofile
logon drive = P:
logon home = \\%L\%U\.9xprofile
os level = 2
preferred master = No
local master = No
domain master = No
ldap ssl = no
usershare allow guests = Yes
hosts allow = 192.168.0.0/255.255.255.0
printing = cups
cups options = raw
print command = 
lpq command = %p
lprm command = 

[homes]
comment = Home Directories
valid users = %S, %D%w%S
read only = No
inherit acls = Yes
browseable = No

[profiles]
comment = Network Profiles Service
path = %H
read only = No
create mask = 0600
directory mask = 0700
store dos attributes = Yes

[users]
comment = All users
path = /home
read only = No
inherit acls = Yes
veto files = /aquota.user/groups/shares/

[groups]
comment = All groups
path = /home/groups
read only = No
inherit acls = Yes

[printers]
comment = All Printers
path = /var/tmp
create mask = 0600
printable = Yes
browseable = No

[print$]
comment = Printer Drivers
path = /var/lib/samba/drivers
write list = @ntadmin, root
force group = ntadmin
create mask = 0664
directory mask = 0775

[abitlater]
path = /home/abitlater/
inherit acls = yes
case sensitive = no
strict locking = no
msdfs proxy = no
guest ok = yes
read only = no

[DOWNLOADS]
path = /home/abitlater/downloads/
guest ok = yes
read only = no
case sensitive = no
strict locking = no
msdfs proxy = no

[BOOKS]
path = /home/abitlater/books/
guest ok = yes
read only = no
case sensitive = no
strict locking = no
msdfs proxy = no

```


Machine1_ubuntu_smb.conf
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
	workgroup = mynet

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;	wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

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
;   domain logons = yes
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
;	socket options = tcp_nodelay

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;	domain master = auto
	username map = /etc/samba/smbusers
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

wins support = no
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


;	available = yes
;	browseable = yes
[www]
	path = /var/www
;	available = yes
;	browseable = yes
	
	valid users = abitlater, root, www-data
available = no
browsable = no
public = no
writable = yes

[lapbackup]
path = /media/disk/Documents and Settings/All Users/Documents/lapbackup
available = yes
browsable = yes
public = yes
writable = no

[Documents]
path = /media/disk/Documents and Settings/All Users/Documents
available = yes
browsable = yes
public = yes
writable = yes

[abitlater]
path = /home/abitlater
available = yes
browsable = yes
public = yes
writable = yes

[storage]
path = /media/disk/storage
available = yes
browsable = yes
public = yes
writable = yes

[recordings]
path = /var/lib/mythtv/recordings
available = yes
browsable = yes
public = yes
writable = no

```


Machine2_ubuntu_smb.conf
```

# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2008/02/26 21:25:07

[global]
	workgroup = OURHOMENET
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	os level = 2
	preferred master = No
	local master = No
	domain master = No
	dns proxy = No
	ldap ssl = no
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	hosts allow = 192.168.1.0/255.255.255.0

wins support = no
[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[brianphillips]
	path = /home/brianphillips
	read only = No
	guest ok = Yes
available = no
browsable = no
public = no
writable = no

[winshare]
path = /home/brianphillips/winshare
available = yes
browsable = yes
public = yes
writable = yes

```

---

### Post by Iowan on 2008-02-29
I noticed that machine1 and machine2 are in different workgroups.
Are the machines supposed to be in different subnets? (192.168.1.x, 102.168. and 102.168.0.x)

---

### Post by Eiríkr on 2008-02-29
As Iowan pointed out, your M1 and M2 conf files define different workgroups, so it's perfectly expected that they wouldn't talk to each other.  Also, your M1OpenSuse and M2 conf files use different "hosts allow" subnets, [font=courier]192.168.1.0/24[/font] and [font=courier]192.168.0.0/24[/font] respectively, further ensuring that the two machines will have nothing to do with each other.  In fact, I'm slightly baffled that the two talk at all, but then I note that your M1Ubuntu conf does *not* specify any "hosts allow".  

So, roughly speaking, to fix this you need to:
[list][*]use the same workgroup name in all conf files
[*]use the same subnet in your networking config for all machines[/list]
That's a start.  I suspect these are the main cause of your troubles, and that your SMB connectivity will be moving along much better once you fix these.  

HTH,

Eiríkr

---

### Post by aBitLater on 2008-02-29
Thank you both for the heads-up on those two items.  I changed the M1 opensuse to correctly reflect.  Now when I open the samba link in opensuse (which is equivalent to nautilus 'smb://'), it reports "unable to find any workgroups in your local network. This might be caused by an enabled firewall."

I have stopped the firewall, and restarted samba on the opensuse machine.

I am able to type the IP of the other machine in the address line and see the shares, without the above message appearing.  Still, I can't read the files or copy or move them

From M2 Ubunutu machine, I have almost the same scenario trying to view the M1 opensuse shares.  I have to enter the IP address after 'smb://'.  Then I can see the all the shares on the M1 opensuse machine.  However, I can only access two of them, "users" and "profiles", and then only after I entered my password.  Username and another box were filled in already.  Once I enter the password, now I can write to the shares on the opensuse machine.

Thanks again for your previous input and any more help you may provide.

---

### Post by Eiríkr on 2008-03-01
I don't know why, but with the change from the deprecated mount filesystem type [font=courier]-t smbfs[/font] to the current [font=courier]-t cifs[/font], NetBios names no longer seem to work.  I first found this when connecting from a Mac OSX client after upgrading Samba a year or two ago, and just like you, I found I could only connect when using the IP address instead of name.  I thought it was just a quirk of the Mac smbclient implementation, but apparently not.  

Now to look at the individual smb.conf files.  One rule of thumb is to use as simple a configuration as possible while still meeting all your usage needs, so I'm going to prune as much as I can here.  ;)  

[[color=gray]NB: Have a look at either [font=courier]man smb.conf[/font] in a terminal or browse to [http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html) for the smb.conf manpage, an *invaluable* reference.[/color]]

---------------
[SIZE="3"]**M1OpenSuse smb.conf**[/SIZE]

****** [FONT="Courier New"][global][/FONT] options***

Your M1OpenSuse smb.conf file put together by SWAT includes a number of options that don't look like they're relevant to your setup (not surprising, as most GUI config tools are guilty of adding extraneous options).  The global options below in particular should be removable:

```
   add machine script = /usr/sbin/useradd  -c Machine -d /var/lib/nobody -s /bin/false %m$

   logon path = \\%L\profiles\.msprofile
   logon drive = P:
   logon home = \\%L\%U\.9xprofile

   ldap ssl = no
```

All of these options are related to Samba domains and / or are specific to sharing roaming profiles with Windows machines.  I assume you're not doing any of this?  :)

From what you've described, it also sounds like you don't need options to allow guest access -- it's just you accessing either way -- and as such you should probably get rid of any means for guests to get at your share to help lock out unwanted visitors.  If this assumption is correct, remove the following global options:

```
   usershare allow guests = Yes
   map to guest = Bad User
```

Follow that up by removing any [font=courier]guest ok = yes[/font] lines from the individual share option lists.  

If you're sharing a printer, you only need the printer sharing options included in the smb.conf file for the machine the printer is physically connected to.  If you have a networked printer (i.e. it's got its own IP address), you don't need any printer options at all in your smb.conf files.  

Either way, delete **all** of the following from your [FONT="Courier New"]global[/FONT] options -- they're all defined in the smb.conf manpage as [FONT="Courier New"]share[/FONT]-level options, *not* [FONT="Courier New"]global[/FONT].  

```
   printcap name = cups
   printing = cups
   cups options = raw
   print command = 
   lpq command = %p
   lprm command = 
```

While you're at it, ditch the [font=courier]os level = 2[/font] line as well, which is irrelevant since the options related to becoming a master browser are all set to "no".  

This leaves you with the following, much simpler, [FONT="Courier New"]global[/FONT] options:

```
[global]
   workgroup = MYNET

   preferred master = No
   local master = No
   domain master = No

   hosts allow = 192.168.0.0/255.255.255.0
```

****** [FONT="Courier New"][share][/FONT] options***

Now for the share options.  If you're not sharing a printer, again, you can delete all the printer-related share options (I assume here that you're not sharing a printer).  That aside, it looks like most of your shares include the following line:
```
msdfs proxy = no
```

The smb.conf manpage explains:

> **msdfs proxy (S)**
This parameter indicates that the share is a stand-in for another CIFS share whose location is specified by the value of the parameter. When clients attempt to connect to this share, they are redirected to the proxied share using the SMB-Dfs protocol.

Only Dfs roots can act as proxy shares. Take a look at the msdfs root and host msdfs options to find out how to set up a Dfs root share.

*No default*

Example: [FONT="Courier New"]msdfs proxy = \otherserver\someshare [/FONT]

So basically your conf file is telling the smb server that your share is located at "no", which is nonsense, and might well be why your shares are not behaving appropriately.  Remove these lines.

Other [font=courier]share[/font] option lines that look unnecessary or possibly even problematic are:

```
   valid users = %S, %D%w%S
```
The bit after the comma is only really relevant for logins from Windows machines.  From the man page:
> The current service name is substituted for %S. This is useful in the [homes] section.
"service name" = the folder name, which in this case = the username.  If you still have problems accessing with just [font=courier]valid users = %S[/font], try commenting out the line by placing a # in front, and then restarting Samba by typing [font=courier]sudo /etc/init.d/samba restart[/font] in a terminal.

```
   inherit acls = Yes
```
Don't really understand the smb.conf explanation, but almost certainly unneeded.

```
   create mask = 0600
   directory mask = 0700
```
Far better to use well-thought-out filesystem permissions rather than these cludges.  See more at [post=4423357]this post here[/post] about setting up permissions in the shared directories themselves.  


```
[profiles]
   ...
   store dos attributes = Yes  # Clearly irrelevant for Lin-Lin sharing anyway
```
Actually, the whole [profiles] section looks redundant, as it only provides a DOS-y access mask to your [homes] share anyway -- in "path = %H", the %H points to your home directory.

```
[users]
```
The whole [users] section also looks redundant, as it serves up the home directory that is already effectively covered by the [homes] section above.

```
   veto files = /aquota.user/groups/shares/
```
Veto files are those files within the shared directory that you want to hide, so anyone connecting to the share via Samba won't see them.  Although separated by "/" slashes, the below is *NOT* a path.  See the man page for a more detailed explanation.  These lines are likely irrelevant for your setup as we're removing this whole [users] section anyway, but now you know what this option is for if you  ever need it.

```
[groups]
```
Does your machine even have a /home/groups directory?  Is that maybe an OpenSuse thing?  If the directory doesn't exist (and I'm assuming it doesn't), just delete this whole section.

```
   case sensitive = no
```
Linux is case sensitive, so ignoring case on the share strikes me as a bad idea.

```
   strict locking = no  
```
For recent Samba versions, leaving this at the default of "auto" is probably better.  And if you're leaving it as the default, no reason to specify it at all, so leave it out to make your conf file simpler.


So after quite a bit of pruning and checking of option definitions against the man page, we arrive at the following for your share definitions:
```
[homes]
   comment = Home Directories
   valid users = %S  # Experiment with commenting this out as needed
   read only = No
   browseable = No
   
[abitlater]
   path = /home/abitlater/
   read only = no
   
[DOWNLOADS]
   path = /home/abitlater/downloads/
   read only = no
   
[BOOKS]
   path = /home/abitlater/books/
   read only = no  
```


---------------
HTH.  I strongly suggest you go through your other two smb.conf files with the same strict simplification approach, going over each option and checking against the man page to make sure it's:
[list=1][*]relevant
[*]in the right section (no share options in global, no global options in shares)
[*]defined correctly (unlike the bogus msdfs proxy settings)
[*]not just the default value (restated defaults just clutter up the file)[/list]

Let us know how things go.

---------------
Not to throw a wrench into the process after putting in all this work, but I really must ask -- **why** are you using this Rube Goldberg of a sharing app (Samba)?  I don't impugn your configuration at all, what I mean is that Windows-based file sharing is insanely complicated and error-prone.  If you *need* to share with Windows machines, Samba is vital.  Kudos to the devs by all means, for successfully reverse-engineering Microsoft's nutty conventions and deliberate obfuscations.  However, if the only machines you need to share between are all Unixy, NFS is a much simpler and saner solution.  And one we're happy to help with as well.  :)

Cheers,

Eiríkr

---

### Post by aBitLater on 2008-03-02
Thank you very much Eiríkr, I'm going through the smb.conf's right now.

You asked why I am using Samba... I had been using it already, and advice from the opensuse forums said to keep using it because NFS required a machine to act as a server and be up all the time.  

At first that made sense, because I have a couple old machines that I was thinking of connecting, and I wasn't sure if I wanted the "one" machine to be on and running NFS server just to share between 2 other machines.

Also, the advice from that forum said that NFS was much more complicated to set up.

And reason #3, is that I read somewhere that NFS had some serious security flaws.  Being a newb, I don't recall the flaw, and I'm sure I wouldn't understand it if I could recall it :) :)   And, I'm not sure of the age of the article that reported this... perhaps it's no longer an issue.

My first preference was to go NFS because I'm in a sort of "eliminate Microsoft's imprint on my life" mode since discovering GNU/Linux, in particular, Ubuntu. (opensuse is my 2nd favorite distribution at this point)

I hate to "waste" all your effort in helping me set up Samba, but since you recommend NFS, would you help me with that, or point me in the right direction?  Are there still security flaws?  At the very least, your time spent here is available for future users.

---

### Post by aBitLater on 2008-03-02
btw, your last post got everything working fine with samba.  

I have to enter my username and password when accessing shares; this isn't so bad though.  And there has to be a way to get the machines to show up on the "windows network" (smb:// ).  Neither machine shows the other in the list, but I can use the machine name or the IP and see the shares.

I had previously entered the machine names in the hosts file, so maybe that is why the machine names work.  I had seen them in the smb:// window not too long ago though, so I'm wondering if one of the deleted lines in the smb.conf file has something to do with making the machine display in this window?

---

### Post by Eiríkr on 2008-03-02
Glad things are working!  :)

> I have to enter my username and password when accessing shares; this isn't so bad though. 
If your Lin and Win usernames and passwords are identical, you can avoid this.  

> And there has to be a way to get the machines to show up on the "windows network" (smb:// ). Neither machine shows the other in the list, but I can use the machine name or the IP and see the shares.
I know that in Konqueror, typing in [font=courier]smb://WORKGROUP_NAME[/font] should show all workgroup SMB/Windows file servers.  Does that work for you at all?

Cheers, 

Eiríkr

PS -- I can get into NFS config later this evening.

---

### Post by aBitLater on 2008-03-04
> **Eiríkr said:**
> Glad things are working!  :)


If your Lin and Win usernames and passwords are identical, you can avoid this.  


I know that in Konqueror, typing in [font=courier]smb://WORKGROUP_NAME[/font] should show all workgroup SMB/Windows file servers.  Does that work for you at all?

Cheers, 

Eiríkr

PS -- I can get into NFS config later this evening.

My usernames and passwords are identical on both linux machines (opensuse and ubuntu).  I tried the 'smb://workgroup', but that didn't work... only the IP works

so you really think NFS is much better and/or simpler (for linux to linux boxes)?

---

### Post by Eiríkr on 2008-03-04
Hey there --

Sorry to keep you waiting; real life intruded and I'm way busy work-wise.  8-|

Anyway, with NFS, you're certainly less likely to run into obscure permission and access issues related to Unixy file ownership / groupship / permissions, since NFS is all about Unixy-ness.  Plus there's less overhead, it's less complicated, and that generally means less can go wrong.  :)  I've also had much better luck with sharing to Macs via NFS instead of Samba, which kinda makes sense given Mac is basically BSD with lots of fun eye candy.  I wrote a long-ish post [post=4387032]over here[/post] that goes over NFS setup with user ID and group ID mapping so user differences between systems don't prevent access (apparently a common issue with Samba).  Note that if your UID and GID is the same on all systems you're tying together this way, you can use Ubuntu's default nfs-kernel-server package.  However, this -kernel- package has various limitations specific to the Ubuntu version, and the generic NFS man pages that come with describe things the -kernel- package is actually unable to do.  So if the IDs on your various machines differ (which is both highly likely given normal home-system multiuser setups, and more secure anyway), you'll need the nfs-user-server package instead, which should show up just under the -kernel- package in the Synaptic list after searching for "nfs".  Give that post a read-through and let me know if you have any questions.  

Incidentally, for Samba browsability, see if your network setup is at all similar to what mine was when I couldn't browse shares -- I'd forgotten I had one machine set to a different broadcast address than the other.  [See here]("http://ubuntuforums.org/showthread.php?t=304402&page=2").  

Cheers,

Eiríkr

---

