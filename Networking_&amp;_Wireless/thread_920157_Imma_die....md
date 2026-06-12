---
title: "Imma die..."
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by leutnant on 2008-09-15
Oh MY GOD! This question has already been asked a bunch of times as I can see from the search results. However, I'm relatively new to Linux and I really need someone to help me with my particular circumstances. 

What should be relatively easy is so hard: All I want to do is print from my ubuntu (hardy) machine to a printer attached to a windows XP machine. Sound pretty simple, eh... WRONG!!! <-- I hope I'm not sounding like a whiner but it may help for you to know where I'm coming from: for two days now I've been at it and still no results. I've read a bunch of threads; tried a bunch of things, but still no success.

Both my ubuntu and xp machines are on a workgroup called "MSHOME." I can go to places-->network and see both my ubuntu and xp machines. However, when I click on my xp machine, it just shows me a blank screen:

[[IMG]http://img181.imageshack.us/img181/7981/screenshotwj2.th.png[/IMG]](http://img181.imageshack.us/my.php?image=screenshotwj2.png)

The thing is that I can browse my ubuntu machine just fine from my XP box. So, something's wrong with my ubuntu machine. 

How can I setup up Ubuntu machine to be able to see the shared stuff that's on my xp machine?:confused:

---

### Post by Aearenda on 2008-09-15
Is the firewall set to allow file and print sharing on the Windows XP box?

---

### Post by leutnant on 2008-09-15
There's no firewall or "helpful" programs running on the xp machine. However, when I go to network connections on my windows machine it says that the computer is connected through a gateway (which I suppose is my router). My router also has a built in firewall. 

Also, here's a screenshot of the SMB browser:

[[img=http://img228.imageshack.us/img228/5348/smbbrowseryk2.th.png]](http://img228.imageshack.us/my.php?image=smbbrowseryk2.png)

Both computers "madiha"(xp) and "Aakif"(hardy) are on a workgroup named "HOME." The printer is connected to "Madiha"

---

### Post by Aearenda on 2008-09-15
On Madiha, if you press <WINDOWS> and R to bring up the 'run' box, and type \\madiha<enter>, can Madiha see its own shares and printers?

Likewise, on Aakif, if you press <ALT> and <F2> to bring up the 'run' box, and type smb://aakif<enter>, can Aakif see its own shares?

---

### Post by leutnant on 2008-09-15
yeah, when I do that, a window pops up on each of the machines and I can see the stuff that they are sharing, however, on the ubuntu machine, here's what I get:

[[IMG]http://img141.imageshack.us/img141/2961/screenshotbl6.th.png[/IMG]](http://img141.imageshack.us/my.php?image=screenshotbl6.png)

It's asking me for my username and password when I click on the folder that the machine is sharing. I put in the username and password that I use to sign into my computer, however, that doesn't work :confused:

Also,why is it saying that my domain is "MSHOME?" As far as I know, "MSHOME" is the name of the workgroup that I'm on.

---

### Post by Aearenda on 2008-09-16
It's OK, MSHOME is your workgroup, but in some scenarios it gets called a domain name. Just ignore that box.

Here's what I think you should try next:
1. On the Ubuntu system, start system->administration->printing
2. Click on the 'New Printer' button
3. Click on 'Windows printer via Samba'
4. Click on the 'Browse' button at the right
5. In the list, open up the workgroup by clicking on the triangular arrow next to it and find your XP computer
6. Open up the XP computer by clicking on the arrow next to it
7. The printer should show in the list. If it does not, try clicking the 'Refresh' button at the bottom of the list area. If it still does not appear, let us know.
8. Click the 'OK' button, which returns to the previous screen with the printer details filled in.
9. Fill in the username and password (from the XP system) if required, after checking the authentication box. I think this will be needed unless your XP system's guest account is turned on.
10. Click the 'Verify' button. It should tell you that the print share is accessible. If this fails, let us know the message it gives.
11. Click 'Forward'.
12. Select the make, and then the model on the next two screens.
13. Set the printer name, as it is to be know on Ubuntu.
14. Click 'Apply'. That should be it.

Please let us know how you get on!

---

### Post by leutnant on 2008-09-16
> 
6. Open up the XP computer by clicking on the arrow next to it
7. The printer should show in the list. If it does not, try clicking the 'Refresh' button at the bottom of the list area. If it still does not appear, let us know.

When I click on the xp computer "by clicking on the arrow next to it" nothing shows up:

[[IMG]http://img181.imageshack.us/img181/6610/screenshotsmbbrowserco0.th.png[/IMG]](http://img181.imageshack.us/my.php?image=screenshotsmbbrowserco0.png)

When I go to Places-->Network, I can see the XP machine (Madiha), but when I click on it, all I get is a blank page.

[[IMG]http://img228.imageshack.us/img228/5656/networkju9.th.png[/IMG]](http://img228.imageshack.us/my.php?image=networkju9.png)

My XP machine (Madiha) can access the shared content on my ubuntu machine (Aakif), but my Ubuntu machine can't even see the content that's on the XP machine.

EDIT: 
Ok, pressed alt+F2 and then typed "smb://192.168.1.2/madshared" 
192.168.1.2 is the IP address of the xp machine (Madiha) and "madshared" is a shared folder on that machine. After I did this, I got this messagebox:

[[IMG]http://img231.imageshack.us/img231/1479/sharedql4.th.png[/IMG]](http://img231.imageshack.us/my.php?image=sharedql4.png)

It asked me for authentication, so I put in the username and password that I use to log on to my XP machine... It doesn't accept it!! What?! I really don't know what else to do anymore.

---

### Post by Aearenda on 2008-09-16
Are you absolutly certain that the XP firewall is set to allow file and print sharing?  What happens if you turn the firewall off temporarily, and then try to connect?

Is it XP Home or Pro?

---

### Post by leutnant on 2008-09-17
It's XP pro and I'm SURE the firewall is off so that shouldn't be an issue. 

In other news, I set up a virtual xp machine on my ubuntu box via virtual box. I put this virtual machine (called Vaakif) on the same workgroup as my ubuntu box and my other XP machine. Thing is that I can see this virtual machine from Places-->Network, but I when I click on it, just like when I click on my other XP machine, it just brings me to a blank page. 

This makes me think that something is wrong with my ubuntu machine because it can't see the shared content thats on the XP machines.

EDIT:

Alright, I think this might be the problem. I used the following command: 

smbclient -L Madiha -N and here's what I got:

[[IMG]http://img397.imageshack.us/img397/4039/smbclientcd6.th.png[/IMG]](http://img397.imageshack.us/my.php?image=smbclientcd6.png)

I'm looking into what this error means but in the meanwhile, what do you guys think?

EDIT 2: 

Here's a copy of my smb.conf file

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
   workgroup = MSHOME

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
   browseable = yes
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

```

---

### Post by Aearenda on 2008-09-17
I don't think the smb.conf file really affects connecting to other systems - it's more for the shares you offer to others.

On my system, I have repeated your command, substituting the name of an XP home system ('One1'=an Acer Aspire One) and I get:
```

Domain=[ONE1] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       Remote IPC
	print$          Disk      Printer Drivers
	SharedDocs      Disk      
Domain=[ONE1] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------

```
This still points at something not being right on the XP end - maybe Ubuntu is supplying the wrong credentials. I tried with the firewall on, and it gave a timeout - so you're right, it's not a firewall issue. Do you have simple file sharing in use on XP? ([http://support.microsoft.com/kb/304040](http://support.microsoft.com/kb/304040) shows how to tell.)

By the way, you can select all the text in an error message like this and just paste it in to the reply box - you don't need a screen shot every time :-)

Can you try ```
smbclient -L madiha -U=Guest
```If it prompts for a password, just press <Enter>.

---

### Post by leutnant on 2008-09-17
lol, thanks for the tip:)

Here's what I got when I put in that command:

```
Anonymous login successful
Domain=[MSHOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Anonymous login successful
Domain=[MSHOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------

```

I was reading HOW TO Documentation on Samba's website: ([http://us1.samba.org/samba/docs/using_samba/ch03.html#samba2-CHP-3-FIG-56](http://us1.samba.org/samba/docs/using_samba/ch03.html#samba2-CHP-3-FIG-56)) and it said something about removing netware protocols; I'm gonna try to remove them and see what happens.

---

### Post by Aearenda on 2008-09-17
Your error message actually corresponds exactly to what I get if I get the password wrong on purpose!

---

### Post by Aearenda on 2008-09-17
On your XP system, assuming getting rid of the Netware protocols didn't help, what are the permissions showing for the print$ share? You can see them like this:
1. right-click on 'My Computer' 
2. choose 'Manage'
3. open up the 'Shared Folders' node under 'System tools'
4. click on 'Shares'
5. right-click on the print$ share in the right-hand pane
6. choose 'Properties'. 
7. Go to the middle tab. 

Mine shows 'Full Control' for 'Power Users' and 'Administrators' and 'Read' for 'Everyone'. I'm NOT using 'Simple file sharing'.

---

### Post by leutnant on 2008-09-17
^^^same here.

and the plot thickens... Remember how I said that I had created a virtual xp machine... well, things just got more complicated.

My virtual installation, which is running on top of ubuntu, can see files that my ubuntu desktop is sharing BUT ubuntu can't see the shared files from the virtual machine.

Also, the virtual XP machine can see the real xp machine, but when I click to access it, it gives me this error:

[[IMG]http://img261.imageshack.us/img261/7964/virtualxpui0.th.png[/IMG]](http://img261.imageshack.us/my.php?image=virtualxpui0.png)

So, the problem is two pronged:

1) There's something wrong with the ubuntu machine that it can't see files that are on an XP computer.
2) There's something wrong with the real XP machine... probably something to do with user permissions/log in names/etc

---

### Post by Aearenda on 2008-09-17
Good move. I think the failure to browse the shares on Ubuntu is a known problem with Nautilus and gvfs, which does not prevent you from connecting to the shares themselves - which is why I wanted to browse using something other than nautilus way back. [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/209520](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/209520) and many similar ones touch on this.
Once we have the XP sharing sorted, the thing to do in Nautilus is smb://madiha/<your-share-name> and that should work. However, browsing when connecting using the printer dialog, or using the command line, should still work. You can test all this using vaakif now that you have your VM.

You still haven't told me whether you have simple file sharing on or off on Madiha! The following assumes it is 'off'.

Here's a possible solution I found (from [http://www.techsupportforum.com/networking-forum/file-application-sharing/66647-win-xp-home-logon-failure-user-has-not-been-granted-requested-logon-type-2.html):](http://www.techsupportforum.com/networking-forum/file-application-sharing/66647-win-xp-home-logon-failure-user-has-not-been-granted-requested-logon-type-2.html):)

1. Click start->run, type regedit.exe
2. When the registry editor appears, click HKEY_LOCAL_MACHINE.
3. Open the subfolder System.
4. Open CurrentControlSet and then Control.
5. Click, don't open, Lsa, inside Control. You should see many keys on the right.
6. On the right, double-click restrictanonymous. (NOT restrictanonymoussam)
7. Value Data should be a 0. 
If it is already 0, this isn't the problem.

If isn't set to 0, just setting it to zero will not fix the problem. Instead, you will need to go into the policy editor and set it from there (although it seems some viruses apparently muck with this setting too - but this may be due to a misunderstanding of how the policy system works).

Here's how:
1. Start->Run and type gpedit.msc<Enter>
2. Open up 'Computer configuration' then 'Windows Settings' then 'Security settings' then 'Local policies' then 'User rights assignment'.
3. In the right-hand pane, check the 'Deny access from the network' key - on my XP Pro system with simple file sharing off, it contains only the support_388945a0 user.
4. Now go the 'Security Options' node, which is the one immediately below 'User rights assignment' in the left-hand pane.
5. Check 'Do not allow anonymous enumeration of SAM accounts and shares' - on my XP Pro, this is disabled. It is the policy that controls the regedit key mentioned above. If it is 'enabled' on Madiha, disable it.
6. The policy immediately above, 'Do not allow anonymous enumeration of SAM accounts' is enabled on my system - so don't muck with it.
7. If you have changed the policy, close the policy editor and then do start->run and type 'gpupdate<enter>'
8. In theory the changes should now take effect, but it doesn't hurt to restart the computer, and because of the policy caching mechanism you may need to restart twice, so don't give up until you have done that!

---

### Post by leutnant on 2008-09-18
Thanks for the advice bro. I'm not at my computer right now but when I am, I'll definitely give this a go. BTW, I'm not using simple share either.:)

---

