---
title: "howto? network: ubuntu + printer + mac OSX"
date: 2005-10-19
forum: Networking &amp; Wireless
---

### Post by dr.drake on 2005-10-19
hello,

I need help with setting up a network...
it's hard being a noob, especially when I used to help people set up windows,
but I'm stuck with a Linux problem once again...

at my house I have:
- a Zyxel Prestige multiPC modem/router
- an AMD PC running Ubuntu (breezy with KDE) 
- a mac powerbook with OSX
- an Epson printer connected to the PC 

what I want is 2 things:
1. that the mac can use the printer connected to the serial out of my PC
2. that the mac and the PC can share files quickly.

I have read and tried many options in the ubuntuguide and did a couple of searches,
but I still couldn't find a simple solution to what I want done.
is there anybody out there that can describe it to me in Noob language?

many many thanks,
eric.

---

### Post by dr.drake on 2005-10-22
in searches I have only found reverences to linking a Linux PC with a Windows PC that has a printer...
...but this should also be easy to do right?

eric.

---

### Post by Joe_lurker on 2005-10-22
This shouldn't be much of a problem.
Printing: Make sure you can print locally first.  From OSX add a "IP Printing" printer using the "Printer Setup Utility".  For the Printer type choose "Internet Printing Protocol".  Enter the ip address of the Ubuntu box that you want to print to in the "Printer Address" box.  "Enter printers/<queue name>" in the "Queue Name" box replaceing <queue name> with the name of the printer you want to print to.  For some odd reason OSX uses a slightly different URI for the queues so you have to manually edit the /etc/cups/printers.conf file.  Change the line:
DeviceURI ipp://<ip address>/ipp/printers/<queue name>
to
DeviceURI ipp://<ip address>/printers/<queue name>
(just deleting the /ipp from the URI.)
Restart CUPS - just reboot the computer if you like and you should be good to go.

File sharing:
You will need to have on of the computers act as a file server.  This computer will stay on all of the time so the files are available.  Depending on which computer you use as the file server the procedure will differ.  Either way you just need to create a shared folder. Let me know which computer will be the file server and I will post instructions.

Joe

---

### Post by Joe_lurker on 2005-10-22
Forgot one thing.  The default setup on the Ubuntu machine does not make the printers available on the network.  You will have to edit the /etc/cups/cupsd.conf file.  Find the line "#Port 631" (about line 450) and remove the #.  About 2 lines down there will be a line "Listen 127.0.0.1:631".  Put a # in front of this line to comment it out.  Next find the line "<Location />" (about line 796) and after the line "Deny From All" add a line "Allow From <network address/mask>" where network address is your network ip address - for instance 192.168.1.0 and mask is your net mask  bit - for instance 24:
Allow From 192.168.1.0/24

save the file and restart cups:
sudo /etc/init.d/cupsys restart

Joe

---

### Post by mjwood0 on 2005-10-22
Wow.  That's great info!  Perhaps a Wiki page is in order!!!

I've been trying to figure out this for a while as I thought it couldn't be too hard <grin>.  I'll give it a shot when I get home! :p

---

### Post by dr.drake on 2005-10-23
hello and thank you for your reply.

in the meantime I have the sharing part working, thanks to remmelt (I'll explain later for those who had the same question), but the printing doesn't work yet.

*edit: I only just saw your second post, I will try that as soon as I post this one....

my printer (connected to my Linux PC on LP0) is working fine on the PC, I just can't get to it work on the mac.
as you can see in my smb.conf file, I tried to open it as much as I could.
on the mac I can see the printer, I have put it as the default printer, but when it is trying to print I get the: NT_STATUS_BAD_NETWORK_NAME message. that's as far as I get.
I know I must be close, just a questions of adding a line or a 'yes' somewhere...

I would appreciate a bit of help there, please :)

thanks, 
eric.

************************************************************************

what you can do to get the sharing working:

- install 'samba' and all the plugins using synaptic
- open a console, make a backup and changed the samba/smb.conf file by typing:

[INDENT]name@computer:~$ sudo cp /etc/samba/smb.conf/etc/samba/smb.conf_backup
Password:
name@computer:~$ sudo gedit /etc/samba/smb.conf[/INDENT] 

- then exchange the file with the one pasted on the end of this message...
[INDENT]the very last part in the file is the one that you should edit to your own settings:
the [Sharedname] is how it will show up on the other computer...
the 'path' should be the path of the shared folder.[/INDENT]

- safe the file and exit
- now set a password to access the files on the mac:

[INDENT]name@computer:~$ sudo smbpasswd -a username[/INDENT]

- then restart samba by typing:

[INDENT]name@computer:~$ sudo /etc/init.d/samba restart[/INDENT]

to check if it worked you can open konqueror (or any other browser) and type in the address:  smb://computername/
you should see both the www and the shared folder there.

- now we go to the mac
- open 'system preferences' -> 'sharing' -> 'services' -> check the boxes: 'personal file sharing' and 'windows sharing' (this is samba)
- open FINDER and in the column on the left click 'Network' and after a short while the Linux PC will show up. click it and click 'connect'

[INDENT]Workgroup/domain:  WORKGROUP
Username:               the username of the LinuxPC
Password:                the smbpasswd[/INDENT]

DONE!!! now you can browse the linux machine from the mac.

************************************************************************

to browse the mac from your PC:

- on the mac goto: 'system preferences' -> 'sharing' -> 'services'
- click on 'Windows sharing', you should see a line in the bottom of the screen saying:

[INDENT]Windows users can access your computer at \\ip.ip.ip.ip\name[/INDENT]

- write down the \\ip.ip.ip.ip\name and the computername
- on the LinuxPC open konqueror and type at the addressbar: 

[INDENT]smb://computername@ip.ip.ip.ip/name[/INDENT]

- enter the mac-password and you're in!!!!!!

************************************************************************

---

### Post by dr.drake on 2005-10-23
and this is the /etc/samba/smb.conf file:

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
# "testparm" to check that you have not many any basic syntactic
# errors.
#

#======================= Global Settings =======================

[global]


## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
  workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
  server string = %h

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
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
  encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
  passdb backend = tdbsam guest

  obey pam restrictions = yes

;   guest account = nobody
  invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
  passwd program = /usr/bin/passwd %u
  passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @ntadmin

######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
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

#======================= Share Definitions =======================

[homes]
  comment = Home Directories
  browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
  writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
  create mask = 0644

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
  directory mask = 0755

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
  comment = All Printers
  path = /var/spool/samba
  browseable = yes
  public = yes
  guest ok = yes
  writable = yes
  printable = yes
  printer admin = root, @ntadmins


# Windows clients look for this share name as a source of downloadable
# printer drivers
; [print$]
;    comment = Printer Drivers
;    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
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
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[www]
       comment = www-root
       writable = yes
       path = /var/www/html
       public = yes
       create mask = 0664
       directory mask = 0775

[Sharedname]
       comment = Sharedname on computername
       writable = yes
       path = /home/sharedFolder
       public = yes
       create mask = 0664
       directory mask = 0775
```

---

### Post by dr.drake on 2005-10-23
ok, I was trying to use the printer through samba, but IP printing seems to be a cleaner solution, so I have set the mac to the IP printing protocol...

[QUOTE=Joe_lurker] For some odd reason OSX uses a slightly different URI for the queues so you have to manually edit the /etc/cups/printers.conf file. Change the line: DeviceURI ipp://<ip address>/ipp/printers/<queue name> to DeviceURI ipp://<ip address>/printers/<queue name> (just deleting the /ipp from the URI.)

Joe[/QUOTE]

hmmm ok,
I might be looking in the wrong spot, but on my linux machine in the /etc/cups/printers.conf file I cannot find the line with **Device URI**... the only thing remotely close I could find was this:

# FileDevice: determines whether the scheduler will allow new printers
# to be added using ***device URIs*** of the form "file:/foo/bar". The default
# is not to allow file devices due to the potential security vulnerability
# and due to the fact that file devices do not support raw printing.

[QUOTE=Joe_lurker]...and after the line "Deny From All" add a line "Allow From <network address/mask>" where network address is your network ip address - for instance 192.168.1.0 and mask is your net mask bit - for instance 24:  Allow From 192.168.1.0/24[/QUOTE]

do you mean the network IP address from the mac or the PC?
and I have no clue as to find out what the net-mask is...
(I am the forever noob :( )

eric.

---

### Post by Joe_lurker on 2005-10-23
1.  Device URI - Look for this on the Mac in the file /etc/cups/printers.conf after you have added the printer per the previous post.

2.  IP address and netmask - this is on the Ubutnu machine (PC?).  To find your network and netmask enter 'ifconfig' ona ternminal.  You will see you interfaces listed.  The listing for eth0 is what you want (assuming you have only one NIC.)  Note the line:

 'inet addr:xxx.xxx.xxx.xxx Bcast:xxx.xxx.xxx.xxx Mask:xxx.xxx.xxx.xxx'

This inet addr is the IP address of your computer and Mask is your netmask.  You can enter the line in the form 'nnn.nnn.nnn.nnn/mmm.mmm.mmm.mmm'.  Normally you want to use the network address for the IP address but I believe that you can use the machine IP address.  On my machine I would enter:
'Allow from 192.168.111.0/255.255.255.0'
or
'Allow from 192.168.111.0/24'
in the '/etc/cups/cupsd.conf' file per previous post.  Both are equivelent.

I hope this clarifies things.

-Joe

---

### Post by pauljwells on 2005-11-01
This all looks very involved... I tried various things before getting Samba to work. I have a similar setup. I originally struggled to get the mac to print on an HP printer connected to the PC running XP. I found all the right info on [www.ifelix.co.uk](www.ifelix.co.uk) tech pages. The bit that's not obvious is I  had to set up ghostscript on the mac to work with the hpijs drivers (there's a link to these on the ifelix site). It's quite straightforward for an HP printer because HP have released OS drivers. There are some Epson printers n the list of supported printers too so yu might be lucky. What I found then was that when I booted into Breezy, with the rigt changes to smb.conf I could print just the same. I had to set up the printer again from the mac because I used a different host name for breezy than for xp, but the printer just showed up in 'windows printers' 

> ########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
   printer admin = @paulwells



paulwells is my user name on the breezy box.

---

### Post by dr.drake on 2005-11-04
oh, but the printer shows up on the mac...
I can see it, I can send a print job, it just won't get there!!!
right now I just share the file and then print from the linux pc, but it's too much work for my girlfriend whose mac it is...

I tried all the things Joe said, but still no success :(
and I don't think I should install printer drivers on the mac for a printer that's at my PC now, do i?

eric.

---

### Post by Joe_lurker on 2005-11-04
One the Mac:
Can you please post your the file '/etc/cups/printers.conf'?

On the Ubuntu machine with the printer:
Watch the output from the log file '/var/log/cups/error_log' while you try to print from the Mac.  Run the command:
```
tail -f /var/log/cups/error_log
```
then print from the Mac.  If there are any errors please post them.

As far as drivers, that depends on the printer model.  Try the drivers that come with OSX.  Failing that go to the support page on the web for the printer and see if there are any OSX specific drivers.  If there are follow the install procedure for the drivers.  The ppd files from Ubuntu probably will not work.  The OSX CUPS system has been tweaked quite a bit.

-Joe

---

### Post by john280z on 2005-11-10
Joe_lurker - you are the man!  Thanks for this info(mods to cupsd.conf), now my Ubuntu desktop will accept print jobs from a Redhat test boxen.

thanks,
john280z

---

### Post by Scrambler on 2005-12-23
Hello,

I still have the problem that my Mac is not sending the proper username along with it's connection command to cups. The line to use the proper user name in /etc/cups/printers.conf on the Mac would have to be:

```

DeviceURI ipp://user:password@server/printers/printername

```

or is there another way of generically passing the correct username to the ubuntu cups server? Because other users will use this username as well and this is not quite what I want...

Thanks for your help,

     Uwe

---

