---
title: "Cannot see other PC's from Network Command On Ubuntu machine"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by wpqc213 on 2008-08-06
I am having a strange problem with this. I can access data from the Ubuntu machine just fine but the Ubuntu machine cant see the other pc's in the network. Everything was working fine last session but after being turned off for an extended period it now does this. No router changes have been made. Only exception would be going to DSL from cable but that didn't require any changes in the router.

When I click on network it delays for awhile then displays the network choices and when it drills down to Windows Network I click on that but it errors out and says it cannot connect to that folder. I was able to see everything on my network from there until whatever happened. I haven't had a chance to play with it much but I figured some one else may have encountered similar problems.

Thanks!

Wayne

---

### Post by jhazlecary on 2008-08-07
Did you try pinging maybe its a firewall issue on your outbound?

---

### Post by jualin on 2008-08-07
Try booting with a LiveCD and checking if you can see other computers on your network. Also make sure that the Network Configuration on the other computers haven't changed. Good luck!

---

### Post by wpqc213 on 2008-08-07
> **jualin said:**
> Try booting with a LiveCD and checking if you can see other computers on your network. Also make sure that the Network Configuration on the other computers haven't changed. Good luck!


Thanks! I didn't even think of that! Mind as totally blank!

I'll give that a try!

Wayne

---

### Post by wpqc213 on 2008-08-07
No I sure havent. In fact I'll turn off the firewall and check it later on just to be sure. I can access it from the Win machines but it cant see them..Anythings possible LOL!

Thanks!
Wayne

---

### Post by wpqc213 on 2008-08-12
> **wpqc213 said:**
> No I sure havent. In fact I'll turn off the firewall and check it later on just to be sure. I can access it from the Win machines but it cant see them..Anythings possible LOL!

Thanks!
Wayne
I'm sorry to be slow in responding but other more pressing problems came up
and I'm just now getting back to this.
Summary:

I switched from Cable Internet to TELCO DSL  but it is still DHCP
and I can see the Ubuntu box from my windows machine but I cant see the Windows Box from my Ubuntu Box.

I disables all the firewalls and it still is a no go.

I haven't mader any setting changes to either OS or router.

Still digging for the root...cause that it !


Wayne

---

### Post by jualin on 2008-08-13
Do you get a response when you ping your Windows machines from Ubuntu. In my case, my router assigns IPs starting with 192.168.2.X-99.

---

### Post by wpqc213 on 2008-08-13
Yes ,
If I ping the IP of one of the other PC's I do get 100% packet transmission..Although the first ping is a little slow at 3.44ms the other 4 are around.15ms.

When I first put this system inplace when I clicked on the network tab I got a list of all the computers on the net..Linux and Windows. Now all I get is a windows network icon and if I click it I get another called Mshome. If I click that it errors out finally and says the folder contents cant be opened..but they are shared.

Still digging!

Thanks for the help and ideas!

Wayne

---

### Post by jualin on 2008-08-14
My last idea would be some Windows related problem. Can you see your other Windows Machines when you try opening Network Places in Windows?

---

### Post by wpqc213 on 2008-08-14
Yes,
I can see all my other PC's including the Ubuntu machine. And I can also get data from each of them including the Ubuntu Machine . I can also ping to the closest (works with all of em ) Win XP machine from the Ubuntu box just fine. I just can not see the any of the other boxes in the network pane under Ubuntu.

Only other strange thing I can recall is that I can access any of the shared files on the Ubuntu box immediately without having to log onto the box. It was originally setup to require a password..now it never prompts for one. 

I really see no reason for the other boxes not to be visible under Ubuntu now!  they used to work that way just fine..

Strange Happenings!

Thanks!

Wt

---

### Post by jualin on 2008-08-15
I have no other ideas that can help you, like you said "strange happenings", Have you tried using a LiveCD? I suspect that the problem lies under some configuration file on your Ubuntu machine but I don't know what else to suggest, sorry :(. Maybe someone else on the forums could give you a better suggestion. If when you boot using a Live CD shows the other computers under the Network on Ubuntu, then we can have an idea if the problem is completely Ubuntu related (a bug) or some configuration on your machine. Good luck!

---

### Post by wpqc213 on 2008-08-15
Thanks for all your help and ideas!
I will locate my Live Cd and load that hopefully I can see the other machines that way.

I have a large chunk of the data mirrored on another machine so it's looking more and more like I am going to be forced into baking up whats left and reinstall. This problem is in a Dell PowerEdge Server that I have had troubles with before! Sounds like time to build another one LOL!

Thanks again!

Wt

---

### Post by scradock on 2008-08-15
Are you using Samba as a networking protocol? The config file for that should be /etc/samba/smb.conf

I recall having a similar problem a while ago - turned out that smb.conf was telling samba to look for a network called MSHOME and the other computers thought it was called WORKGROUP.

Might be worth checking, before you write the server off.....

---

### Post by wpqc213 on 2008-08-15
Thats correct my shares are handled by Samba and it no longer asks for a password when I log on to the server. I think you may be onto something:)

I will look into the info you gave momentarily. I am assuming you enter that command in terminal correct ?

Meanwhile I did find a way to log into the machine I needed data from via the linux box.. I used the Connect to server prompt and used that as a windows share for the location with the ip of the machine I want and it works...for now. I found that info elsewhere on the forum but I can
t recall the person to thank for it..but I will find it!

Thanks again for the idea! I am looking into that right now.

Now if I could just remember the password of my back up machine:(

I've got to start making notes!  My mind is too garbled to remember anymore it seems :)

Wayne

---

### Post by jualin on 2008-08-16
> **wpqc213 said:**
> Thats correct my shares are handled by Samba and it no longer asks for a password when I log on to the server. I think you may be onto something:)

I will look into the info you gave momentarily. I am assuming you enter that command in terminal correct ?

Meanwhile I did find a way to log into the machine I needed data from via the linux box.. I used the Connect to server prompt and used that as a windows share for the location with the ip of the machine I want and it works...for now. I found that info elsewhere on the forum but I can
t recall the person to thank for it..but I will find it!

Wayne

At least you found a fix for your problem, glad to hear it! What scradock suggests might worth checking it out. You can do it to ways, if you want to just read the file then go to the terminal and type > cat /etc/samba/smb.conf and to edit the file just open it using a text editor such as gedit > sudo gedit /etc/samba/smb.conf

---

### Post by jualin on 2008-08-16
This is part of my samba configuration file, and as you can see the workgroup is in bold letters. Every Linux configuration file have "comment lines" (lines starting with #), those lines are just for you to read and they are not a command. Good luck! > #
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
   workgroup = **WORKGROUP_NAME_GOES_HERE**

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

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

# Cap the size of the individual log files (in KiB).
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

# This option controls how nsuccessful authentication attempts are mapped 
# to anonymous connections
map to guest = bad user

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

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
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
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
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
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

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


---

### Post by wpqc213 on 2008-08-16
It gets even sillier!
When I type in the command to configure Samba from terminal it gives me a permission not allowed response. Thats really weird since I am logged in as admin anyway! If I go to install Samba it says that it IS up to date. Any attempt to bring up configuration information fails. Any ideas on that?? I had considered removing Samba and re installing it but the way it's been responding it likely wouldn't let me remove the program:(

This has been nightmare for sure! I was going to retrieve the back up data(archive) from another box that has been off lined for awhile but now I can't remember the password to it!! Geesh what an ordeal:)

Thanks for all the help! I think we're at least on the right road!
We just need to find the exit LOL!

Wayne

---

### Post by wpqc213 on 2008-08-16
> **jualin said:**
> At least you found a fix for your problem, glad to hear it! What scradock suggests might worth checking it out. You can do it to ways, if you want to just read the file then go to the terminal and type  and to edit the file just open it using a text editor such as gedit

I get a reply " No Such Fire Or Directory" from entering the edit or view prompt!

Weird....

Wayne

---

### Post by scradock on 2008-08-16
> **wpqc213 said:**
> I get a reply " No Such Fire Or Directory" from entering the edit or view prompt!

Weird....

Wayne

Try doing the following in a terminal:
```
cd /etc/samba

```
If that fails you probably have to re-install samba!

If not (ie.e it doesn't give a failure message), then type 

```
ls -la

```
That should show you list of all the files in /etc/samba, which SHOULD include smb.conf

If there isn't a file called smb.conf in the list, you probably need to re-install samba.

If there is, type 

```
less smb.conf
```

and look for the workgroup identification line.

If it's not correct (i.e., the same as the other machines think it should be, do

```
sudo gedit /etc/samba/smb.conf
``` 

and fix it.

If it is correct, then there must be some other problem, and you'll probably have to re-install samba - and check it all over again....

HTH

---

### Post by wpqc213 on 2008-08-16
It's heading toward a reinstall of Samba.. I still get the no such directory or file error. I seriously do not know what went wrong here! All as fine until this popped up.

Which would be the best way to uninstall samba??

Wt

---

### Post by scradock on 2008-08-17
> **wpqc213 said:**
> It's heading toward a reinstall of Samba.. I still get the no such directory or file error. I seriously do not know what went wrong here! All as fine until this popped up.

Which would be the best way to uninstall samba??

Wt

You should not need to uninstall samba - but you should check first that you have all the necessary parts installed to begin with:

samba
samba-common
smbclient
libsmbclient

should all be listed in your Synaptic - do a search on "samba" in Name and description to make sure.

If one or more is missing, check it/them to install and then Apply.

If they all seem to be there, check them all to reinstall, Apply and then check for the smb.conf file.....

---

### Post by wpqc213 on 2008-08-17
Thanks for the update!  I am still looking into this problem. I have ran the apt-get command and tried a refresh of Samba using that function and it always come back with a 0 updated so it thinks that all the files are there.
I haven't tried the on on one file method you just described. I will try that next. I was able to get into my machine that I didnt have the password for and get off the files I needed. I done a fresh install of 7.10 ( Have not down loaded Hardy as yet) and the network function works fine on it...I am able to see all the machines I have on line and communicate with them. It has to be some sor t of corruption within Samba causing the problem. I did a complete reset of the windows and the suspect Linux box including disconnecting from the AC mains and that did give me back my log in/password function. Still having truobles with the rest of it though.. 

Thanks for all your help!  Actually everyone s help that's been given on this little problem!  At least I am posting this from the newly loaded Ubuntu machine so things maybe are looking up !

Wayne

---

### Post by sosipator on 2008-08-17
Now I have absolutely the same problem. Until awhile ago, Ubuntu used to display not only one workgroup, but many different workgroups with all the machines on the network. But then started to display only the stupid "Windows Network" stuff and when you click on it, it's empty. Also when i type: "smbtree" in the console, ask for a password, and then nothing. 
I have a mandriva installed along with ubuntu, and on mandriva sambashares work just fine. All the machines on the network are visible. When I reboot to Ubuntu, everything dissapears. It use to do this before, and reinstalled completely the entire OS, and now it does it again. 
Please people, if anybody has any idea, post it here, because I'm thinking to move permanently to another distro just because of this.
Here is the content of my smb.conf file
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
	workgroup = WORKGROUP

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

# Cap the size of the individual log files (in KiB).
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
	encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
	passdb backend = tdbsam

	obey pam restrictions = yes

;	guest account = nobody
	invalid users = root

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

# This option controls how nsuccessful authentication attempts are mapped 
# to anonymous connections
	map to guest = bad user

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
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;	printing = cups
;   printcap name = cups

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

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
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
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
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
;	guest ok = no
;	read only = yes
	create mask = 0700

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
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

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

```

Thank you all.

---

### Post by wpqc213 on 2008-08-17
I am still working on that problem on one of my servers here. when I come up with a resolution ( with the help of the community here ) I will definitely send it your way! If you stumble upon the culprit I would appreciate the fix info. Mine was fine until a week or so ago I needed to add something from one of the other machines and needed to do so via network instead of direct entry.

Wt

---

### Post by sosipator on 2008-08-17
I will keep digging. If anything comes up, I'll post it right away.
Though it's a bit frustrating when mandriva (which in my opinion is inferior to ubuntu) recognizes everything on the network, and Ubuntu plays microsoft tricks.

---

### Post by wpqc213 on 2008-08-17
Know what you mean!
Thanks for the help!

Wt

---

### Post by simplr on 2008-08-23
Have you set the "Search Domain" in the System->Administration->Network->DNS to your Windows or Samba name server? You can use an IP address instead of a name.

---

### Post by wpqc213 on 2008-08-23
> **simplr said:**
> Have you set the "Search Domain" in the System->Administration->Network->DNS to your Windows or Samba name server? You can use an IP address instead of a name.


Yes I had done that originally BUT as with lots of other parameters in this machine they were somehow corrupted. The value shown befre correction was something completely outside of the network..don't know what it was actually:)

Anyway after re entering the correct address values it works!

Thanks for the help!

Wayne

---

### Post by wpqc213 on 2008-08-26
After a couple of days using the fix info obtained here I have considered this problem repaired!..

I did have some corrupted files in the server that were in question and I was able to rebuild those with no trouble.. Biggest thing that happened was during the switch from Cable ISP to DSL all the DNS addresses and search orders got corrupted. Only reason I can give for that is that the cable modem operated in bridge mode and assigned the ip to my router and it translated that into it's DHCP assigned addresses and DNS info the DSL modem is working in router mode and assigns a private IP 192.1.. to the router and thats where the process went crazy!

Anyway many Thanks to everyone here for taking time to lend a hand in getting to the root of this problem! Sorry I didn't realize the big difference right off but we live and learn I guess LOL!

Wayne

---

### Post by theDaveTheRave on 2008-12-06
Hi all,

This seems like a similar problem to mine, however slightly different.

My problem related to "seeing" the various machines on the network.

From the windows  and Mac terminals, they can "see" all the other windows shared drives in the "network places", but not the Ubuntu terminals?

The same (but opposite) is true of the Ubuntu machine, they see each other but not the windows shares, but can access them quite happily?

However... they can happily connect to the terminals by entering in the IPaddress/sharedFolderName they will be prompted for a name and password and everything is fine, but they still don't show up in the network places

System setup.

All terminal are on static IP addresses.
All IP's are served from the same nameserver.
All terminals are part of the same workgroup.
All terminals have the same default gateway.

Netmask is different for Windows machines compared to the Ubuntu machines.

On ubuntu the netmask is 255.255.255.128
on windows / mac  it is 255.255.255.0


my understanding of the netmask is that the machines will only accept an IP address within the range of the last triplet of digits;

So ubuntu will only accept from 0 up to 128.

with the 0 for the windows they will accept anyting from 0 to255

Please correct me if I am wrong.

I can confirm that in fact all the pc's IP addresses are in fact between 0 and 128.

OK now for the real sillyness!

I recently did a re-instal of XP for a colleague (her machine was on a major go slow so we formated and started again).

When it was first hooked to the network it received the IP address dynamically, and it could see everything within the workgroup just fine.

As soon as I set its static IP and the netmask, only the windows / macs are visibly?

I am guessing this is somehow related to the netmask thing, but I don't understand why it has this difference?

Is it somehow related to the fact that the ubuntu machines are "servers" on the system and the all the others are "clients" and "servers"

If anyone can shed light on this I would be really pleased.

Is there a command line tool that will tell me what the terminal thinks its workgroup is (for both Ubuntu and windows) as I think it may be somehow related to how the settings are retained.

Also the Ubuntu terminals don't get turned off, as they hold various databases, and I intend to have them auto update with master data held on an FTP site.... blah blah blah... but that will be once I get the scripts working properly (or how I want them too !).

We have a very security conscious IT staff, with a seriously locked down firewall, could that be causing me an issue?

This isn't really causing an issue for me / the team, as I guess I can simply load the ubuntu shares onto the machines using a <net use...> command. or maybe ask everyone to change their network mask??

Or another alternative, is to mount all the network shares onto the ubuntu main file server with fstab, and then everyone only needs a single access point for everything?

Ultimately I may even be allowed to set the main ubuntu system up as a name server, and tell it to give out the requied IP's.

there is no rush to sort this issue as I am now out of office until the new year.... I'm off to join the other half of my research team elsewhere. 

I look forward to you thought and suggestions.

David

---

