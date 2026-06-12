---
title: "[SOLVED] Ubuntu Samba detected from XP, but can't connect"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by ahorriblemess on 2008-02-22
I'm trying to get my files from my XP machine to my Ubuntu machine

I have Samba, I've configured it, added a user, their username and password. 

On the XP machine, if I click "view workgroup computers," it shows, 

*"Homeragon(my host name) server(Samba, Ubuntu)(Homeragon)"*

But, if I double click it to connect it says, 

[I]"\\Homeragon is not accessible, You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The account is not authorized to log in from this station"[/I]

I got frustrated and tried to setup ftp using proftpd (gproftpd actually) but I figured I would need an address like, "ftp://name@name.com" but I read that I could just use "ftp://myIPaddress" but that didn't work. I don't understand any of this. 

What I would really like to do right now is just network with the XP machine and get all my files over to my Ubuntu machine.

I am on a laptop, connected wirelessly through a Belkin wireless router. The XP machine is connected with an ethernet cable into the router. Both computers have internet access... that works fine, they just can't connect to each other. 

I've been searching the forums, I've read through and followed different Samba setup and configuration docs, and I spent around 4 hours working on it and asking questions in IRC. 

This sucks...

---

### Post by dca on 2008-02-22
Try at CLI:
 
sudo smbpasswd -a *shareusername*
sudo smbpasswd -e *shareusername*
sudo /etc/init.d/samba restart

---

### Post by ahorriblemess on 2008-02-22
The same menu came up again on XP. It doesn't even prompt for login info at all. It simply doesn't connect. But, I can ping the XP machine, and the XP machine recognizes the Ubuntu machine...

---

### Post by dca on 2008-02-22
Post the contents of /etc/samba/smb.conf file
 
Also, are you using 'Firestarter' on the Ubuntu machine?

---

### Post by Iowan on 2008-02-22
I saw a thread around here somewhere that mentioned XP not sending username, but I don't remember the fix.

---

### Post by ahorriblemess on 2008-02-22
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
;   wins support = yes

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
   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = no

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
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

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
wins server = Workgroup
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



[Ubuntu Shared]
path = /home/jason7315/Desktop/Ubuntu Shared
available = yes
browsable = yes
public = yes
writable = yes

[Ubuntushared]
path = /home/jason7315/Desktop/Ubuntushared
available = yes
browsable = yes
public = yes
writable = no

[allusers]
comment = All Users
path = /home/shares/allusers
valid users = @users
force group = users
create mask = 0660
directory mask = 0771
writable = yes

[homes]
comment = Home Directories
browseable = no
valid users = %S
writable = yes
create mask = 0700
directory mask = 0700

---

### Post by dca on 2008-02-22
What happens when you use 'map network drive' option in WinXP?
 
'Right-click' network and select map network drive.
 
Put in:
 
\\*ipaddressofubuntuserver*\Ubuntushared
 
...then click connect...

---

### Post by ahorriblemess on 2008-02-22
ok, I just tried that, I set the username as password to match the one I added to samba, but it just reloads the login window and puts my IP address before it, like 0.0.0.0.\username. It doesn't show an error or a confirmation, it just keeps refreshing the login window

---

### Post by lifewithryan on 2008-02-22
If all you reall need to do is transfer files, try using winscp.

Do a google search for WinSCP and install that on your XP box.

Then use WinSCP to copy the files from windows to your Ubuntu box.

(No this is very much a pain if you want this connection act more like a network drive etc, but if all you need to do is copy files once in while, this is a quick way to do so).

You may need to install openssh-server on your ubuntu box first, but after that you should be able to use WinSCP to login as whatever use and move the files over.

I do have Samba fired up but with out getting some information from you that you probably don't want to share of the net, it could be hard to get help.

Can you map a drive on windows via the windows command line and see if you get other errors?  (I think the command is "net use //path/to/share"

---

### Post by Rucas on 2008-02-22
Ok this is what i have done:

1) Open up Terminal
2)Type: sudo smbpasswd -a username (the username for your Ubuntu Account)
3)Terminal will ask you for the Admin Password
4)Terminal will now ask for a password for the SMB Share (you can use anything here, just remember it because you will need it.)
5)Terminal will ask to retype that password again.
6)Finished
7)Restart Machine

Now when you restart the Ubuntu Machine and after you login and all is ready, whatever folder you decided to share will now be available for WinXP

In win try to open up the share again. A log in window will pop up.
1) User: enter the name of the Ubuntu Account
2) Password: Enter the password you created for SMB Sharing (step 4 in terminal)
3) Voila, you should now be able to access the files/folders

From that point on, any folder you create for sharing in Ubuntu will be accesable in Win.
Also remember that when creating shares, you need to state wheather they are Read only or not.
Hope this helps...

---

### Post by RD1 on 2008-02-22
Is samba actually running? The computer will show on network without samba running.
From a command line, enter ... 'sudo smbd start' then try to access from XP again.

If you want to run samba at start, you would need to go to System>Administration>Services and check 'Folder Sharing Srevice (Samba)

Hope this helps,
Rodger

---

### Post by ahorriblemess on 2008-02-22
> **Rucas said:**
> Ok this is what i have done:

1) Open up Terminal
2)Type: sudo smbpasswd -a username (the username for your Ubuntu Account)
3)Terminal will ask you for the Admin Password
4)Terminal will now ask for a password for the SMB Share (you can use anything here, just remember it because you will need it.)
5)Terminal will ask to retype that password again.
6)Finished
7)Restart Machine

Now when you restart the Ubuntu Machine and after you login and all is ready, whatever folder you decided to share will now be available for WinXP

In win try to open up the share again. A log in window will pop up.
1) User: enter the name of the Ubuntu Account
2) Password: Enter the password you created for SMB Sharing (step 4 in terminal)
3) Voila, you should now be able to access the files/folders

From that point on, any folder you create for sharing in Ubuntu will be accesable in Win.
Also remember that when creating shares, you need to state wheather they are Read only or not.
Hope this helps...

No... I've read those instructions before actually. I've done all of that.

I also restarted samba, I started samba using the command RD1 wrote and tried again. 

I enter the username and password from the XP computer, and like I said, it doesn't do anything.. it just refreshes the login window. I can enter the password and "login" a hundred times, it won't say I connected, it won't say I can't connect...

---

### Post by RD1 on 2008-02-22
Ok. I compared your smb.conf to mine (which IS working). The only thing I see wrong is under 'Authentication' , change Encrypt Passwords to 'True'

Restart samba .... sudo smbd restart

Try access from XP again

Keeping fingers crossed,
Rodger

Edit: I would also comment out the shares you have right now and simply go with ....
[homes]
   comment = Home Directories
   browseable = yes

---

### Post by vitiate34 on 2008-02-22
You can't see samba shares from XP? Can you see XP shares from linux?

Also, have you XP home or professional?

XP Home as far as I know always tries to authenticate as guest when accessing shares.

XP Pro will try to authenticates as a user if simple file sharing is off (Click view, options, advanced it should be in there from a XP file directory window [http://support.microsoft.com/kb/304040]("http://support.microsoft.com/kb/304040"))


I think that's possibly your problem, but I'm no expert. A simple test would be to set your samba server as browseable, and to allow guests (I note in your smb.config, you have security=user and homes shares as browseable=no)

I hope this is sort of useful.

---

### Post by ahorriblemess on 2008-02-23
> **RD1 said:**
> Ok. I compared your smb.conf to mine (which IS working). The only thing I see wrong is under 'Authentication' , change Encrypt Passwords to 'True'

Restart samba .... sudo smbd restart

Try access from XP again

Keeping fingers crossed,
Rodger

Edit: I would also comment out the shares you have right now and simply go with ....
[homes]
   comment = Home Directories
   browseable = yes

hahah yeah that worked. Thanks!

---

### Post by RD1 on 2008-02-23
You are quite welcome!

---

### Post by sergiom99 on 2008-02-24
> **Rucas said:**
> Ok this is what i have done:

1) Open up Terminal
2)Type: sudo smbpasswd -a username (the username for your Ubuntu Account)
3)Terminal will ask you for the Admin Password
4)Terminal will now ask for a password for the SMB Share (you can use anything here, just remember it because you will need it.)
5)Terminal will ask to retype that password again.
6)Finished
7)Restart Machine

Now when you restart the Ubuntu Machine and after you login and all is ready, whatever folder you decided to share will now be available for WinXP

In win try to open up the share again. A log in window will pop up.
1) User: enter the name of the Ubuntu Account
2) Password: Enter the password you created for SMB Sharing (step 4 in terminal)
3) Voila, you should now be able to access the files/folders

From that point on, any folder you create for sharing in Ubuntu will be accesable in Win.
Also remember that when creating shares, you need to state wheather they are Read only or not.
Hope this helps...

Thanks dude! this also helped me. I kept trying to login from XP and only got prompted for DOMAIN\user all the times.
This fixed it. 
Only that you dont need to reboot, just type>
*sudo /etc/init.d/samba restart*
Thanks!

---

