---
title: "cups, samba and hardy"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by janrito on 2008-05-09
I have been fighting with Hardy for the past couple of days to reconfigure my samba and cups print server. It was working perfectly on Gutsy, but Hardy has something new with samba which tightens security on samba shares (or so I hear). 
The case is that Cups seems to be configured correctly, Samba does too, but for some unknown reason, samba panics when I try to authenticate on the web admin interface.

I have a ubuntu-server install on an old computer, so managing it locally is out of the question. I would like it to be accessible from my mac, but password protected.

The printer is unimportant as it works with a .ppd file, which just needs to be dropped in the appropriate directory.

Samba is working, I have a shared folder, and shared homes, which are authenticated through os X and can be accessed without a problem.

Cups works, I can access the web-admin, it is only when an action requires authentication that it goes down.

Here is exactly what happens when I try to authenticate:

```


janrito@rata:/etc/cups$ sudo /usr/sbin/cupsd -f
sh: /usr/share/samba/panic-action: Permission denied
Aborted


```

Here is the cups.conf file:
 ```

#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel info

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
# Listen localhost:631
Listen 631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

DefaultEncryption Never

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow From All
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow From All
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow From All
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
#

```


And, Here is the smb.conf file:

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
  workgroup = RATON

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
   security = user

#  You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
;  passdb backend = tdbsam guest
   passdb backend = tdbsam

  obey pam restrictions = yes

;   guest account = nobody
  invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

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
   printer admin = @lpadmin

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
  create mask = 0755

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
  writable = no
  printable = yes


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


;[www]
;       comment = www-root
;       writable = yes
;       path = /var/www/html
;       public = yes
;       create mask = 0664
;       directory mask = 0775


[ratashare]
       comment = Sharedname on computername
       writable = yes
       path = /home/shared
       public = yes
       create mask = 0775
       directory mask = 0775


```



Any help would be appreciated

---

### Post by malcollins on 2008-05-16
I am having similar problems.  Desktop has two printers (both brother) working OK.  Laptop is XP.  I can see and setup the printer,but I cannot get them to be accessible.  
On the windows machine it says access denied.  Gutsy worked straight away.
What has changed?
Have you managed to solve it?

---

### Post by gurubob on 2008-08-09
Hi guys ...

Was getting the same thing, was driving me batty.  I don't have a solution but I do have a workaround and some clues that might help someone work it out.

My vital stats:
```

root@pandora:/etc/cups# uname -a
Linux pandora 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686 GNU/Linux
root@pandora:/etc/cups# dpkg --list|grep cups
ii  cupsddk                               1.2.0-0ubuntu1              CUPS Driver Development Kit
ii  cupsddk-drivers                       1.2.0-0ubuntu1              CUPS Driver Development Kit - Driver files
ii  cupsys                                1.3.7-1ubuntu3              Common UNIX Printing System(tm) - server
ii  cupsys-bsd                            1.3.7-1ubuntu3              Common UNIX Printing System(tm) - BSD comman
ii  cupsys-client                         1.3.7-1ubuntu3              Common UNIX Printing System(tm) - client pro
ii  cupsys-common                         1.3.7-1ubuntu3              Common UNIX Printing System(tm) - common fil
rc  cupsys-driver-gutenprint              5.0.2-2ubuntu1              printer drivers for CUPS
ii  libcupsimage2                         1.3.7-1ubuntu3              Common UNIX Printing System(tm) - image libs
ii  libcupsys2                            1.3.7-1ubuntu3              Common UNIX Printing System(tm) - libs

```


I noticed like you did that this was happening when the authentication was taking place.  The panic-action file is part of samba, I have no idea why it can't execute it as it has a+x permissions.  That file is responsible for mailing a backtrace of samba to root for diagnostics.

My workaround was to edit the cupsd.conf file, rip out any mention of authentication, swap the deny,allow bits to allow,deny and then start cups up again.  Something else that will drive you nuts is that Firefox 3 remembers when you were accessing a page with authentication and will resend those credentials, causing cups to repeatedly crash.  My solution for this has been to Tools | Clear Private Data | Authenticated Sessions, and then restart Firefox.  On a side note I was very pleased to see that cups worked well with lynx as a text browser :)

I've finally managed to add my printer and print a test page.  My next step is to share it via samba for Windows PC to use so we'll see how that goes.

Here's my butchered cupsd.conf file - not recommended for production use:
```
#
# "$Id: cupsd.conf.in 7199 2008-01-08 00:16:30Z mike $"
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
# DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Order allow,deny
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    Order allow,deny
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    Order allow,deny
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Order allow,deny
  </Limit>

  <Limit All>
    Order allow,deny
  </Limit>
</Policy>

#
# End of "$Id: cupsd.conf.in 7199 2008-01-08 00:16:30Z mike $".
#

```

Cheers,

- Bob -

[www.scmdemo.com](www.scmdemo.com)

---

### Post by venik212 on 2008-09-11
I have similar problems with Kubuntu 8.04. The CUPS web interface prevents me from sharing printers.  Since I am using KDE4.1.1, in which the PRINTERS section of System Settings was removed, I cannot share printers... This seems to be a very old problem, and it is frustrating that it is still with us.

---

