---
title: "[SOLVED] can't access my own shared disc"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by swotie on 2008-03-22
I can't access my own shared disc. It come with a box .... with a guest account and want domain and password to access the disc ... I don't know what I must write there .... I would like to remove this box, but can I do that and make free access from other computers ?

---

### Post by Eiríkr on 2008-03-22
Hello swotie --

Unfortunately, your post tells us nothing that would allow us to help you.  "It come with a box" could mean a dialog box that appears on your screen, the hardware case in which a standalone computer comes, or even just the cardboard box that products are packaged in.  We have no idea what you're talking about here.  

What kind of shared disk is it?  Who makes it?  What's the model number?  How do you access it?  What version of Ubuntu are you running?  What *exactly* do you see in any dialogs?  How many computers do you have on your LAN that you want to share this disk with?  Is the shared disk a standalone NAS, pretty much it's own computer connected to others over the network, or is it an external hard drive attached to a USB port?  etc. etc.

Please remember that, when you're posting here on the boards, it is best to give as **much** detail as you possibly can.  ;)

Cheers,

Eiríkr

---

### Post by swotie on 2008-03-22
I have local network with 3 computers, with a shared drive of each machine. The 2 others Computers are installed with Windows XP . 

At my Ubuntu installation I can see and access the shared drives at the Windows computers. I use Samba. Then I try to access the shared drive at the Ubuntu installation, I get a dialog box ... 
In the dialog box, there is 3 fields:

Name: guest
Domaine:
Password:

I don't know there I find the informations for this dialog box .... best of all ... Can I remove this dialog box, so the others computers have access to the shared Ubuntu drive, without passwords.

Hope this description of my problem can help You to solve  my problem.

---

### Post by Eiríkr on 2008-03-22
Thank you swotie, this gives us more to work with.  So if I understand this correctly, your shared files are on an XP machine, and you are trying to access them from Ubuntu.  When you say you "use Samba", do you mean that you type [font=courier]smb://XPMACHINENAME[/font] into the location bar in Nautilus?  Or do you mean that you have installed the [font=courier]samba[/font] package (not what you need here)?

Please give as much detail as possible.  What do you mean by "I try to access the shared drive at the Ubuntu installation" -- please explain what *exactly* you do when you try to access like this.  

Thank you,

Eiríkr

---

### Post by swotie on 2008-03-23
I can access the shared file at my windows machines from ubuntu .... but then I try to access my shared files at my ubuntu machine from windows, I get a message that I have no authority to access this computer (my Ubuntu)  

In Ubuntu I have been in "system -> administration -> shared folders" I have marked that all can access my shared drive and unmarked that it is write protected. It is through SMB.

---

### Post by Eiríkr on 2008-03-23
GUI tools are unfortunately still pretty buggy for certain sharing setups, I'm afraid.  Sounds like we'll have to get at the Samba configuration file itself to find out exactly what's happening here.  Open a terminal and type the following, then copy and paste the contents of the file here in this thread.  Don't change anything yet.  
```
sudo gedit /etc/samba/smb.conf
```
Once we have a look at that, we'll be able to tell what needs to change.

Cheers,

Eiríkr

---

### Post by swotie on 2008-03-23
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
	workgroup = mshome

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
	encrypt passwords = no

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

[hdb6]
path = /media/hdb6
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by Eiríkr on 2008-03-23
Okay, I think this is a simple case of your username not being recognized by the Samba server on your Ubuntu machine.  This is relatively easy to fix.  

Open a terminal and type the following.  Replace USERNAME with your Ubuntu login username.
```
sudo smbpasswd -a USERNAME
```
You'll be prompted to enter a Samba password.  Enter whatever you want.  Security-wise, some people recommend that your Samba password be different than your usual Ubuntu login password, but for most home use it doesn't really matter.  

Once you've done this, restart Samba:
```
sudo /etc/init.d/samba restart
```

Now try again to access from XP.  You should be prompted for your username and password, as you described in your first post.  For name, enter your Ubuntu login username.  For password, enter your Samba password.  For domain, if there's nothing there, enter the name of your workgroup.  

Does this work for you?

Cheers,

Eiríkr

---

### Post by swotie on 2008-03-23
There is no dialog box I can write in at my windows computer anymore. There comes a message that I have no Authority to access the Computer (Ubuntu pc) . I must contact the server administrator ... The server administrator must be me ... but I don't not know somethimg about it ;)

---

### Post by Eiríkr on 2008-03-23
Ah, the very hated garbage Windows error messages.  How I loathe those.  "Contact your system administrator..."  Feh.

Anyway, in your previous post, when you mentioned a dialog box:
> In the dialog box, there is 3 fields:

Name: guest
Domaine:
Password:

Was this dialog box appearing on your XP machine?  If so, then Windows has (surprise, surprise) done the wrong thing and cached your failed login attempt.  I'm afraid you'll have to remove a few settings files to force Windows to "forget", and thereby ask you again for the login.  After much research, user KennedyM wrote up [thread=720889]this HOWTO[/thread] about bitch-slapping Windows into behaving better.  For your case, we only need to remove existing login caches.  Follow KennedyM's instructions for this:

> On XP, click on Start, Run, Type "Control Userpasswords2" (without the quotes!), [Enter]:
[list=1][*]Advanced tab, Manage Passwords.
[*]Remove any Locations/IPs/Servers already logged.[/list]

Now try again to connect to your Ubuntu share.  Post here and let us know how that goes.

Cheers,

Eiríkr

---

### Post by swotie on 2008-03-23
The dialog box

Name: guest
Domaine:
Password:

appears when I try to log on the shared Ubuntu drive, from the Ubuntu Pc .... 

I can see, I have wrote something wrong before ... sorry

My windows xp is a "home" version, maybe this can be a problem.

I still got the answer ... No access then I try to log on  the shared ubuntu drive from windows ... I can see the Ubuntu pc in windows xp -> search -> search a computer ... but I can't log on 

I can log on the shared windows drives from all 3 computers (1 ubuntu - 2 windows xp home)

---

### Post by swotie on 2008-03-23
I have followed this instructions video [URL="http://youtube.com/watch?v=Ad17kma8rNM"]http://youtube.com/watch?v=Ad17kma8rNM[/URL

I find all my computers (1 unbuntu (desktop) 1 win xp home (desktop) 1 win xp home (laptop) in my SMB network at my ubuntu machine .. The Network group name is "Mshome" ....

But then I go to the 2 windows machine and will access the workgroup Mshome .... I receive a answer .. 

"Mshome isn't avaible ... perhaps You don't have permission to use this network resource ... contact your admin ... ect.

The account has no authority to log on from this computer"



if I from win xp laptop search for win xp desktop computer, I find it and can access it.

If I from win xp laptop search for ubuntu computer, I find it but can't access it

If I from win xp desktop search for win xp laptop,I find it and can access it.

If I from win xp desktop search for ubuntu computer, I find it but can't access it

From ubuntu computer I find all 3 computers in Mshome network , and can access both windows computers

I haven't firewall and anti virus at any of these computers

---

### Post by Eiríkr on 2008-03-23
Okay, swotie --

Did you follow the directions I borrowed from KennedyM in [post=4569058]this post[/post] earlier in this thread?  I think you need to remove any data from your Win XP machines about previous attempts at connecting to the Ubuntu machine.  Follow the steps described there.  

*Then*, open Explorer, click the address bar (the text entry area at the top), and type:
```
\\UBUNTUNAME
```
Replace UBUNTUNAME with the name of your Ubuntu machine.  

What happens, exactly, when you do this?

Cheers,

Eiríkr

---

### Post by swotie on 2008-03-23
There were nothing to delete i the password manager as KennedyM describe 

Then I type \\ubuntuname (the name of my ubuntu machine) in explore,it open the box with no access .. contact admin ... etc

---

### Post by Eiríkr on 2008-03-23
Okay great then, I think I've figured it.  Since your XP machine is clearly not using old authentication information, it must be that your [font=courier]hdb6[/font] share is marked:
```
public = yes
```
This is the same as:
```
guest ok = yes
```

However, in your [font=courier][global][/font] section, there is no line defining who the guest account should be (it's commented out), meaning it reverts to the default:
```
; guest account = nobody
```

The username "nobody" should exist by default on all Ubuntu systems (and most Linux distros in general), but it's also a very restricted account.  In your case, I strongly suspect that this username has no access permissions to the files on your server (unless you've deliberately run [font=courier]chmod[/font] on your [font=courier]/media/hdb6[/font] directory).  

So, if you are the *only* user of your setup, change the guest account line in your smb.conf file.  Edit the file like so:
```
sudo gedit /etc/samba/smb.conf
```

Scroll down until you see this line:
```
; guest account = nobody
```

... and change it so that it looks like this:
```
guest account = USERNAME
```

Replace USERNAME with your usual Ubuntu login username.  Then save the file, and close gedit.

Now restart your Samba server:
```
sudo /etc/init.d/samba restart
```

Try again to access from XP, and let me know what you see.  

HTH,

Eiríkr

---

### Post by Victormd on 2008-03-23
Ok, I'm going to try to piggy back on this issue...
I have two desktops and 1 laptop at home, one with XP and the other with Ubuntu (Hardy) and the laptop with Vista, all connected through a router. The XP machine acts as a sharepoint for my printer and as a backup for my ubuntu machine and the vista laptop. With Gutsy, I was able to access all shared folders on all comps., now, I can "see" the windows workgroup but won't "see" past it. I just tried to install my printer and amazingly, Ubuntu found the printer that is connected to the XP machine but was not able to print (I'm using the same driver as I did for gutsy so I'm guessing it's also a network issue)...
I have samba installed but still, no go...

I have this on the hardy development but nobody responded so I'm going to give it a try here...

---

### Post by Eiríkr on 2008-03-23
So far as I have read , the full-on [font=courier]samba[/font] package is only useful for serving shares, not for accessing (acting as a client).  For that, you need [font=courier]smbclient[/font] and [font=courier]smbfs[/font] (plus whatever dependencies they install).  

What happens when you type:
```
smbclient -L XPNAME
```

Replace the caps with the name of your XP machine.  You should get a username / password prompt, and then see a listing of the shares on your XP machine.  

Cheers,

Eiríkr

---

### Post by Victormd on 2008-03-23
using smbclient -L gives me a connection timeout... I'm going to try to install smbclient and smbfs and see what that does. What bothers me is that I didn't have any problems with gutsy... my laptop dualboots Vista and gutsy and both can see and exchange files with the XP machine no problem...

edit: smbclient was already installed...

---

### Post by Eiríkr on 2008-03-23
Try replacing the hostname with the IP address; does that work any better?

Also, are your sure your Hardy machine is using the same workgroup as the XP machine?  You can specify the workgroup in the smbclient command like so:
```
smbclient -W WORKGROUP -L XPNAME
```

Cheers,

Eiríkr

---

### Post by swotie on 2008-03-24
I still got the message at my xp machine

"Mshome isn't avaible ... perhaps You don't have permission to use this network resource ... contact your admin ... ect.

The account has no authority to log on from this computer"

Here is my smb.conf:

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
	workgroup = mshome

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
	encrypt passwords = no

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
	passdb backend = tdbsam

	obey pam restrictions = yes

;	guest account = henrik
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
;   browseable = yes

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = yes

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

[delte filer]
path = /home/henrik/delte filer
available = yes
browsable = yes
public = yes
writable = yes

[hdb6]
path = /media/hdb6
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by swotie on 2008-03-24
Now my win xp laptop will open the workgroup Mshome, and I can see all 3 machines... I can access the win xp desktop ... when I try to access the ubuntunachine ...it says:

"Ubuntumachine isn't avaible ... perhaps You don't have permission to use this network resource ... contact your admin ... ect.

The account has no authority to log on from this computer"

this is a step forward

---

### Post by Eiríkr on 2008-03-24
Glad to hear things seem to be making progress.  I'll have to go over your whole smb.conf file later (work beckons), but one thing struck me right away that might be what is preventing access to your Ubuntu machine from the Windows machines --
```
; guest account = henrik
```

Here, you *almost* define the guest account, but it's still commented out.  In the smb.conf file, any text on a line to the right of a number symbol _**#**_ or a semicolon _**;**_ is treated as a comment and ignored when the file is read by the Samba daemon process.  To make your guest account line above work properly, remove the semicolon, save the file, and then restart Samba:
```
sudo /etc/init.d/samba restart
```

Hope that helps, and more later!  ;)

Cheers,

Eiríkr

---

### Post by swotie on 2008-03-24
I have removed the semicolon ... but it is the same 

Here is the new conf. file 

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
	workgroup = mshome

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
	encrypt passwords = no

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
	passdb backend = tdbsam

	obey pam restrictions = yes
	guest account = henrik
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
    browseable = yes

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
    writable = yes

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

[delte filer]
path = /home/henrik/delte filer
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by Eiríkr on 2008-03-24
Hello swotie --

Looking over your conf file as it currently stands, I noticed a few problems.  
[list][*]There are some share-only options that are floating around in your [font=courier][global][/font] section, specifically the [font=courier]browsable[/font] and [font=courier]writable[/font] options from the commented [font=courier][homes][/font] section.
[*]The [font=courier]wins support[/font] and [font=courier]encrypt passwords[/font] options should probably be changed to "yes".[/list]

So, open your smb.conf file for editing:
```
sudo gedit /etc/samba/smb.conf
```

Then replace the current contents with the following:
```
[global]
# Name resolution options
   workgroup = mshome
   server string = %h server (Samba, Ubuntu)
   wins support = yes       # <-- Changed from "no"
   dns proxy = no

# Logging options
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

# Username security options
   security = user
   username map = /etc/samba/smbusers
   guest account = henrik
   invalid users = root
   encrypt passwords = yes  # <-- Changed from "no"
   passdb backend = tdbsam
   obey pam restrictions = yes
   ; unix password sync = no
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

[delte filer]
   path = /home/henrik/delte filer
   public = yes
   writable = yes
```

Now restart Samba:
```
sudo /etc/init.d/samba restart
```

If this *still* doesn't work, please open a terminal in your Windows XP machine, and post the results of the following commands:
```
net view
net view ubuntumachine
dir \\ubuntumachine\"delte filer"
```

Cheers,

Eiríkr

---

### Post by swotie on 2008-03-24
When I log on my ubuntu machine from my win xp laptop ... There come a dialog box where I can type my ubuntu username and password ....  and wupti ... I'm on my ubuntu machine from win xp ....

[SIZE=5]He He IT'S WORK .... [/SIZE]

THANK YOU VERY MUCH     ** Eiríkr**

Thank you for all that energy you have put in my post .... I'm very very glad for your kind, who will help us "Dummies" ...... :)

---

### Post by Eiríkr on 2008-03-24
Excellent, I'm glad to hear it!  :D  And no worries, just be sure to help others when you can.  ;)  If this resolves your issues, please remember to mark the thread as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Cheers,

Eiríkr

---

