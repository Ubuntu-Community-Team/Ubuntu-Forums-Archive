---
title: "SAMBA share Problems after Gutsy Gibbon upgrade"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by HeinekenPissr on 2007-10-21
I had working SAMBA shares under Feisty Fawn then i opted for the upgrade to Gutsy Gibbon and now my SAMBA shares don't work. 

I can see the Ubuntu Server when I view workgroup computers under "My Nework Places" in WinXP.  However when I try to access this share I get the following error: 

 \\xxx-desktop is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions. The network path was not found.


My FAT32 Shares, which are auto-mounted on boot-up,  are set to be public folders with read/write permission and no authentication required.  I followed the following guide to do this and it worked like a charm in Feisty.

 How to share public folders with read/write permissions (Authentication=No)

    * Read #General Notes
    * Read #How to install Samba Server for files/folders sharing service
    * If sharing a FAT32 partition, read #How to mount Windows partitions (FAT) on boot-up, and allow all users to read/write 

sudo mkdir /home/public
sudo chmod 777 /home/public/
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
gksudo gedit /etc/samba/smb.conf

    * Find this line 

...
;  security = user
...

    * Replace with the following line (make sure it does not begin with a semicolon) 

  security = share

    * Append the following lines at the end of file 

[public]
  comment = Public Folder
  path = /home/public
  guest ok = yes
  read only = no
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup


    * Save the edited file 

sudo testparm
sudo /etc/init.d/samba restart

Here is my current smb.conf file
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
   workgroup = K-1

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
### Originally set as "security = user"
   security = share

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
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

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
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

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



#[DATA]
#path = /media/DATA
#available = yes
#browsable = yes
#public = yes
#writable = yes
#create mask = 0777
#directory mask = 0777
#force user = nobody
#force group = nogroup

[Share]
path = /home/errol/Desktop/Share
available = yes
browsable = true
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

[35GB_FAT32]
path = /media/35GB_FAT32
available = yes
browsable = true
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup


[FAT_120]
path = /media/FAT_120
available = yes
browsable = true
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

[160_GigR]
path = /media/160_GigR
available = yes
browsable = true
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

[MUSIC_111GB]
path = /media/MUSIC_111GB
available = yes
browsable = true
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

Please help.  I have searched around and cannot find the answer.

---

### Post by Wiebelhaus on 2007-10-21
First:

```
sudo apt-get install samba
```

Add this to the bottom:

#replace with your info and shared locations of course.



```
 [global]

workgroup = MSHOME

netbios name = UBUNTU_SERVER

security = SHARE

auth methods = guest

domain master = No

wins support = Yes

[share1]

comment = mi home

path = /home/USERNAME IN LOWERCASE

 

read only = No

guest ok = Yes

  


```

---

### Post by mont on 2007-10-21
so true, it only works for me to when trying to connect from windows XP if I skip the password thing. IF i make the share totally public it connects.

I did not try Samba in Feisty so dont know how it was there.
but this solution is not good, no security at all.

Did you find out something yet? I've tried all kind of configuration for 3 hours now with no luck at all.

After all I think it is all connected to encrypted passwords, but still a guess.

( I have no problem connecting locally via smbclient.

---

### Post by HeinekenPissr on 2007-10-21
@MONT 
I think you misunderstood.  I CAN'T get the SAMBA working at all under GUTSY.  I will try the other posters suggestion but it's not too different from what i have already

---

### Post by Wiebelhaus on 2007-10-21
> **HeinekenPissr said:**
> @MONT 
I think you misunderstood.  I CAN'T get the SAMBA working at all under GUTSY.  I will try the other posters suggestion but it's not too different from what i have already


Just remove your eveything from under ...../cdrom.

Add my suggestion to the bottom with your information , then Open your home directory and right click the folders you want to broadcast over your LAN and set the permissions manually , it's like 3 clicks and apply to all contents.

---

### Post by mont on 2007-10-21
OK, sorry :) I wish you good luck then.

---

### Post by HeinekenPissr on 2007-10-21
The folders or rather hard drives i want to be accessible on the network are not mounted in my home directory.  They are mounted in the /media directory.  Do i have to mount them in my home dir?

---

### Post by HeinekenPissr on 2007-10-21
after implementing your suggested changes it stil doesn't work.  In fact now the server is not even listed when i view workgroup computers from winxp.  Strange because i didn't change the workgroup.

---

### Post by Wiebelhaus on 2007-10-21
> **HeinekenPissr said:**
> The folders or rather hard drives i want to be accessible on the network are not mounted in my home directory.  They are mounted in the /media directory.  Do i have to mount them in my home dir?

No sir  , basically what you had but modified.

```
 [global]

workgroup = MSHOME

netbios name = UBUNTU_SERVER

security = SHARE

auth methods = guest

domain master = No

wins support = Yes

[share1]

comment = mi home

path = /home/USERNAME IN LOWERCASE

[B][I][U][U][share2]

comment = disgusting porn

path = /media/drives name/disgusting porn[/U][/U][/I][/B]

 

read only = No

guest ok = Yes


```

you'll need to set the permissions of the entire path to allow "others" "file access" to read &/or write.

or yea , you could mount them in your home directory which may be easier to keep track of.

---

### Post by bandyo on 2007-10-21
I have the same problem. I upgraded from 7.04 to 7.10 after the final Gutsy came out. Now my file and printer sharing will not work. I have a shared folder in a windows XP SP2. I have a shared folder in the Ubuntu box called home\ddrive. I have a printer connected to the Ubuntu box that I was sharing with the Windows box. Now they are not shared!

From the Ubuntu box, I can't see the Windows shared folder. From the top menu if I got "Places" > Network, I see a "Windows Network" which is empty.  My workgroup is called KAAJ, but it does not show up in the Network folder.

From the Windows box. If I go to my network places, I see my workgroup KAAJ and inside I see my Windows1 and Ubuntu1 boxes. If I click on Windows box I see the shared folder. If I click on the Ubuntu1 box I get an error message: 
"\\Ubuntu1 not accessible. You might not have permission to use this network resource. ... Network path not found."

My smb.conf is below. I have deleted all the comments in it.

Thanks in advance.

Bandyo

-------------- begin file ----------------
[global]

   workgroup = KAAJ

   server string = %h server (Samba, Ubuntu)

   log file = /var/log/samba/log.%m

   max log size = 1000

   syslog = 0

   panic action = /usr/share/samba/panic-action %d

   security = share

   encrypt passwords = true

   passdb backend = tdbsam

   obey pam restrictions = yes

   invalid users = root

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

   printing = cups
   printcap name = cups

   socket options = TCP_NODELAY

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[ddrive]
  comment = Public Folder
  path = /home/ddrive
  guest ok = yes
  read only = no
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

available = yes
browsable = yes
public = yes
writable = yes

-------------- end file ----------------

---

### Post by Wiebelhaus on 2007-10-21
NOTE:

Something we all neglect to do...


you absolutely must restart for the changes to take effect , I just completely re-setup my ubuntu server which runs from the same desktop I use for internet activity to verify what I'm telling you folks and it's working perfectly.

---

### Post by HeinekenPissr on 2007-10-21
It still doesn't work

I did like you said 

I also added permissions by adding the following for each share
create mask = 0777
directory mask = 0777

i'm getting very frustrated.  In Feisty everything was so easy to set up and worked so well.  Feel like this was a downgrade.

---

### Post by Wiebelhaus on 2007-10-21
> **HeinekenPissr said:**
> It still doesn't work

I did like you said 

I also added permissions by adding the following for each share
create mask = 0777
directory mask = 0777

i'm getting very frustrated.  In Feisty everything was so easy to set up and worked so well.  Feel like this was a downgrade.


Now for the locations you want to share in your home or media folder , you must set "Others" folder access to the level that you want , but if you set Pictures and not [COLOR="Red"]/home[/COLOR]/picutres it won't work.

After you set the permissions you must restart and you'll need to back out and refresh you network browser in windows because windows will still be trying to talk to the old settings.

---

### Post by HeinekenPissr on 2007-10-21
Yup bandyo looks like we have the exact same problems.  I didn't mention it before but i can't see my windows shares from my ubuntu box either.  

I guess we'll just have to wait a few days until more people upgrade and figure out the problem.  I'm stuck.

---

### Post by bandyo on 2007-10-21
Yes Heinekenpisser it looks like we have the same problem.

sx66gns: Thanks for trying to help. I tried your smb.conf and it didn't work either. On the Ubuntu side I have the shared folder with all the permissions to everyone. I think its called 777. It is set as a shared folder with shared through" Windows Network SMB" in the Gnome GUI. I have restarted samba after each edit of smb.conf. and I have rebooted / logged out and in, on the Windows box to refresh it. Still no dice.

With your smb.conf the Ubuntu box doesn't even show up in the Windows' file manager (Windows Explorer). With the old smb.conf I can see the Ubuntu box in the workgroup from the Windows box, but can't see the shared folder and printer in it. 

On the Ubuntu side the workgroup KAAJ does not show up. How do I tell Ubuntu that it is part of the warkgroup KAAJ and should mount the shared folder in the Windows box in KAAJ? Other than in samba I don't think I have any reference to KAAJ in Ubuntu.

Thanks again

Bandyo

---

### Post by HeinekenPissr on 2007-10-21
still no luck for me

I am considering a fresh install

Sx66gns your profile lists you as being a Feisty Fawn user.  Have you upgraded to Gutsy and gotten SAMBA to work?  I only ask because the users of this thread didn't have problems with samba in Feisty.  It was the upgrade to gutsy that got us in.

---

### Post by Wiebelhaus on 2007-10-21
> **bandyo said:**
> Yes Heinekenpisser it looks like we have the same problem.

sx66gns: Thanks for trying to help. I tried your smb.conf and it didn't work either. On the Ubuntu side I have the shared folder with all the permissions to everyone. I think its called 777. It is set as a shared folder with shared through" Windows Network SMB" in the Gnome GUI. I have restarted samba after each edit of smb.conf. and I have rebooted / logged out and in, on the Windows box to refresh it. Still no dice.

With your smb.conf the Ubuntu box doesn't even show up in the Windows' file manager (Windows Explorer). With the old smb.conf I can see the Ubuntu box in the workgroup from the Windows box, but can't see the shared folder and printer in it. 

On the Ubuntu side the workgroup KAAJ does not show up. How do I tell Ubuntu that it is part of the warkgroup KAAJ and should mount the shared folder in the Windows box in KAAJ? Other than in samba I don't think I have any reference to KAAJ in Ubuntu.

Thanks again

Bandyo


```
[global]

[COLOR="Red"]This option is how you identify your workgroup[/COLOR]

workgroup = [COLOR="Red"](change to your workgroup)[/COLOR]

netbios name = UBUNTU_SERVER

security = SHARE

auth methods = guest

domain master = No

wins support = Yes

[share1]

comment = mi home

[COLOR="Red"]This option is how yu identify the user these rules apply to[/COLOR]

path = /home/([COLOR="Red"]change to your usernamein lower case[/COLOR])

 

read only = No

guest ok = Yes
```


* workgroup; Lets you specify the windows workgroup
* netbios name; Lets you specify the name with your Linux PC will be seen by windows PCs
* security; specifies the level of security, default is user, but if the users on the windows PCs are not the same as the ones on the Linux PC, you better use share instead
* auth methods; Possible options include guest (anonymous access), sam (lookups in local list of accounts based on netbios name or domain name), winbind (relay authentication requests for remote users through winbindd), ntdomain (pre-winbindd method of authentication for remote domain users; deprecated in favour of winbind method), trustdomain (authenticate trusted users by contacting the remote DC directly from smbd; deprecated in favour of winbind method)
* domain master; Lets you configure your PC as a domain master or not, in this case we prefer not, as our goal is only to share files
* wins support; If you want or not to have wins enabled or not

Now comes the shares section, the string you put between the [] will be how windows will sees the share, in this case share1

* path; You put here the path you may want to share

* read only; yes or no, depending if you want to permit other users to write on this directories.

* guest ok; It is a boolean field, and will permit or not guest users to access this resource.

---

### Post by Wiebelhaus on 2007-10-21
> **HeinekenPissr said:**
> still no luck for me

I am considering a fresh install

Sx66gns your profile lists you as being a Feisty Fawn user.  Have you upgraded to Gutsy and gotten SAMBA to work?  I only ask because the users of this thread didn't have problems with samba in Feisty.  It was the upgrade to gutsy that got us in.

Yes , I'm using 7.10... that's my bad ,  forgot to change it :)

---

### Post by HeinekenPissr on 2007-10-21
Sx66gns are you a Gutsy user or are you still on Feisty?

---

### Post by Wiebelhaus on 2007-10-21
> **HeinekenPissr said:**
> Sx66gns are you a Gutsy user or are you still on Feisty?

Gusty.

---

### Post by rocket777 on 2007-10-21
Ok, just a guess, since it sounds like you are running a samba server. 

Do you have firestarter installed? I did, and all my servers wouldn't work after the upgrade. I checked the logs and I saw that the firewall was blocking them. I am not sure, but i could swear I saw something about samba as well, but i don't usually try to get to my ubuntu files from windows, rather I go the other way, from ubuntu.

I do know that after I clicked the off button in firestarter, all my servers immediately began working. Remote desktop and sshd.

It's an easy enough try, install firestarter and toggle the firewall to off and see if this makes it work. If not, you can just toggle it back on.

---

### Post by bandyo on 2007-10-21
Rocket777: Thank you very much. I had installed Firestarter under 7.04 and never used it. The moment I toggled the Firestarter to off all the problems were solved. Now my 2 computer network is whole again. The smb.conf I am using is the old one I used with 7.04 (Feisty).

Thanks Again!

Bandyo

---

### Post by HeinekenPissr on 2007-10-22
!!LOL!!  Thanks Rocket 777.  I too installed Firestarter under Feisty and forgot about it.  For some reason the network shares still worked then.  I had even considered a firewall problem for a sec but on boot it says Firestarter failed to start.  I guess it was restarting without a hitch once the GUI was loaded. 

Thanks again.

---

### Post by shot_one_pie on 2007-10-24
Same issue here after upgrading to Gutsy. I could not see my box, nor connect to it.

I added the netbios name = SERVERNAME line to my smb.conf and played with the password settings.

Here is what works for me (this shows the server in my network places on my XP laptop and allows me to access it and write to the shares)


P.S. don't forget to run this command: sudo smbpasswd -a username


========================================================


[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = HOME

# server string is the equivalent of the NT Description field
   server string = %h server (ubuntudesk)

  netbios name = UBUNTUDESK

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
   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = eth0

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
[homes]
   comment = Home Directories
   browseable = yes

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
   valid users = %S

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

---

### Post by salocinbake on 2007-10-24
I had same problem as Bandyo and HeinekenPissr;

I could see my shared folders from XP or Vista, but could not see my folders on Windows machine from Ubuntu.

Fresh install, 7.10 so I assumed no firewall.  I found this on another thread:

"I had a similar problem, which is why I found this thread... but while fiddling with it during the search I have found a solution to my particular problem: Map the network devices in your defined hosts.

System -> Administration -> Network

1. Select the "Hosts" tab.
2. Click "Add"
3. Enter the LAN IP of the device
4. Enter the aliases (host-names)
5. Hit "Ok"

Worked for me, hope it helps"



Credits to Surly [[COLOR="Red"]on this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=523456&highlight=he+folder+contents+could+displayed.&page=2")

Ciao!

Salo

---

### Post by tubasoldier on 2007-10-25
ss66gns

  ---Thanks for your smb.conf setup. I've been working on this for days. Swat was of no help neither was gsambad or system-config-samba. It was odd to me that samba quit working when I upgraded to gutsy. The devs should watch stuff like that more closely. The forums are full of samba issues on gutsy.

---

### Post by trickypicky on 2007-10-30
I was having the same problems as brandyo  and HinekenPissr.   The real solution may have been to just reboot my windows machines... Read the whole thing if you dare:

I had a share that was essentially setup for anonymous R/W (Share security) and had no problem, then I did the upgrade and none of my windows machines could reach the shares anymore.  The windows would get the same error that HinekenPissr Described "\\xxx-desktop is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions. The network path was not found."

After making a copy of my smb.conf and dorking with it... I fell back to my original, because it worked before... why would it not now?

I actually just tried to be "Dumb"

I went to system > administration > shared folders and deleted my share
Then I clicked "Add"
Put in the desired path to the folder I wanted. and unchecked the "Read only" box and clicked ok and closed the "Share Folders" window

Then I opened a term and restarted samba

I could see the share from my Windows machines but when I tried to connect to the shares I was prompted for login/password the User name would default to windowscomputername\guest (which was greyed out) I took the share out, recreated it, restarted samba then RESTARTED THE WINDOWS MACHINES.  Then everything was back to normal....

I never rebooted the windows machines after I did the Gutsy upgrade. (I did obviously reboot the ubuntu machine)  Don't know if that may have been the real solutio

Doesn't make any sense but it worked.... hope it helps

-Trickypicky

---

### Post by scarboni on 2007-11-06
I am also unable to access my Windows network since upgrading to 7.10. I double-click the "Windows Network" & it knows, in the title bar, the workgroup name, but the screen is blank. Rebooting the same box into Vista & all shares easily accessible. smbclient -N returns nothing.

---

### Post by scarboni on 2007-11-08
Update: I have booted the machine using the 7.10 64-bit live cd & can see the Windows shares just fine. Something broke in the upgrade. Can anyone tell me if there's a way to rebuild, reset, or reconfigure the smb client? Also, does the /etc/samba/smb.conf file affect the client or is this only relevant when running the server?

I have overwritten the upgraded /etc/samba/smb.conf file with the one from the livecd & tested nautilus again with no change. Also smbtree -N still reports nothing. However I have not rebooted yet so maybe that is needed. Anyone got any ideas?

---

