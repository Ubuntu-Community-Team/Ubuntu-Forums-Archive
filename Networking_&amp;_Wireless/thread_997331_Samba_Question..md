---
title: "Samba Question."
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by Roasted on 2008-11-29
When Samba users write to this computer (to back up their files), they end up "owning" the files.

Is there any way I can configure Samba so ALL files that get dropped into a certain directory take on certain permissions?

My end goal is for this:

I have 4 users who back up to this computer. I want all 4 of their Samba directories to be owned by root, and to have group access with the group "sambashare" with 770 permissions.

That way, the only people who can access the files are those in the sambashare group, along with root who owns the files.

I can run command to set this up. However, when these users write additional files to their designated directory, the files take on default permissions and are owned by the user. But, like I said, I want root to own them.

How can I make this happen?

---

### Post by J172 on 2008-11-29
Shouldn't the folder permissions (the top level of the backup directory) override all subordinate files and directory's permissions? If its not working maybe make a chmodding script to run everynight? No clue, but I'd like to see the answer.

---

### Post by Coreigh on 2008-11-29
I don't know the exact answer but I can point you in the right direction. You setup the share to be a "guest only" share. The users connect to a public share so no password is needed, Samba assumes they are "guest" and the folder owner assumes control of the files on the host computer.

Here is a sample share:
> [storage]
comment = Storage (public files)
writable = yes
path = /usr/files/storage
public = yes
only guest = yes
guest account = nobody
browsable = yes 


Do some googling for > samba public share

---

### Post by Roasted on 2008-11-29
I appreciate the input with the public idea with no passwords, but I really want passwords. I just want everybody to have a direct 1 to 1 backup method without my brothers like "oh my gosh maybe mom will snoop my backed up pictures and see that picture of..." etc.

And for one, I figured out the one answer. I guess it pays to read directions! At the top of the Samba config file, it said that ; and # are comments, but ; signify comments that are more commonly changed. Guess what was commented! create mask and directory mask. No wonder they didn't work!

So I uncommented them. And bingo... everything comes through as the permissions I want, which is 770.

7 for root
7 for groups (sambashare)
0 for others (no access period)

But this mystery isn't completely solved. When I add files to this directory from my XP Pro laptop, they come through owned by Jason (me).

So even though the root server folder (in this instance, named test... I created a bogus one for testing) is owned by root and group (sambashare) has 100% access to this folder, the actual FILE within the folder that's created is owned by Jason.

Here's a picture.

[http://s2.photobucket.com/albums/y36/Roasted/?action=view&current=samba.png](http://s2.photobucket.com/albums/y36/Roasted/?action=view&current=samba.png)

The left box is the "test" server share permissions.
The right box is the "test file" (which is a bogus docx file)'s permissions.

If possible, I want the docx file (and any other files or directories I throw into this folder) to take on the permissions of the root folder (test). Which is... owned by root, and group - sambashare - full access to anything.

---

### Post by bab1 on 2008-11-29
Use:```
force user = root
force group = sambashare
```

See [**(14.3.1.2. Anonymous Read/Write)**]("http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/ref-guide/s1-samba-servers.html") This is an example from Redhat's site.

---

### Post by Roasted on 2008-11-29
Can you explain where I use that at, please?

---

### Post by bab1 on 2008-11-29
In the share directives of the /etc/samba/smb.conf file.

---

### Post by Roasted on 2008-11-30
Wouldn't force user force the actual user who logs into my server to be jason?

I want everybody to log in with their own account.
I just want the files written on ANY share of this computer to be owned by jason.

---

### Post by bab1 on 2008-11-30
> **Roasted said:**
> Wouldn't force user force the actual user who logs into my server to be jason?

What does that mean to you?  They are not logging in as a Linux user to the server.  They are only assuming the Samba user ID.  To me it means that the user has to have their own login.  Once logged in they assume the rights of jason.  As they are also forced into the group "sambashares" which has the same rwx rights I don't see a problem.  The only advantage  the user has is that they are the owner of the file and can use chmod and chown as the owner of the file.   

> 
I want everybody to log in with their own account.
They should have their own Samba account through ```
smbpasswd -a
```
> 
I just want the files written on ANY share of this computer to be owned by jason.
They will have exactly that.

I'm not sure why you need to be the owner of the files.  If you are the administrator of the server you have (or should have) root privileges and be able to manipulate the files regardless of who is the owner of the files.

I force the group and let the user keep the ownership of the files.  I go one step further and apply a stick bit to the file so that only the owner can delete the file.  Remember you have 4 users writing to this share.  I do this by the use of the "create" directive. You can do this:
```
        
create mask = 0775
directory mask = 3775

```

---

### Post by Roasted on 2008-11-30
Hmm... you make a lot of sense. The owner of the files really doesn't matter I guess.

Now I'm even starting to wonder why I have the sambashare group. What use does having a group with samba offer? Does that just allow me (being a sambashare member) have the ability to change files that are owned by another user?

---

### Post by bab1 on 2008-11-30
> What use does having a group with samba offer?
The group is an OS thing.  Samba just follows the permissions as you have set them up.  You added the group to the Linux groups; right?
>  Does that just allow me (being a sambashare member) have the ability to change files that are owned by another user?
If you have the permissions to change the files (write) then you you can modify the file without being the owner.  If the group has execute permissions then you can delete them too.  Thats why you use the sticky bit.  It stops all users except the owner of the file (and root) from deleting the file.

You should think of what security you really need.  If you want all to be able to read and modify the files then you need a common group.  If not then don't force a group.  If you want to have the group thing but do not want members of the group to delete each other files then look to the sticky bit or take away  execute rights.  If you don't want group members to modify the file then take away the write permission.

---

### Post by Roasted on 2008-11-30
Every user has their own password protected share. So Tyler cannot get into Curt's stuff and Curt cannot get into Tyler's stuff. I have a "valid users = (name)" tag under each account name that has the users listed that can access the server share in question. 

The problem I ran into was this... Tyler posts up a file on his server share. Well, I log into my server share (naturally, I granted myself access to everybody's folders :)) and there was a file he wanted me to grab. I copied and pasted it, but I got an error when I pasted it to my XP Pro's Desktop. I realized that the reasoning behind this was, I was not the owner, and I was also not in the group.

I don't care who is owner of the files anymore. I just want myself to have access to copy/paste/do whatever I want with the files. Therefore, I created the sambashare group... the only member in the group is myself (jason). That way, it seems to give me the power I want with the files, while leaving Tyler as the owner of his own documents he backs up on my server.

Make sense? So in reality, it's nice to force the group, because forcing the group I'm in (and like I said, the only member) guarantees me the priviledges over the backed up files that I want.

That's why I went with 770 rights. Because it grants full access to the owner and full access to the group (me) but no access to anybody else.

Am I on the right path? 

Just for kicks and giggles, here's my smb.conf.

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
   netbios name = jason-intrepid

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
   create mask = 0770

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0770

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no


force group = sambashare

[jason]
path = /home/jason
writeable = yes
browseable = yes
valid users = jason


[curt]
path = /media/storage/curt
writeable = yes
browseable = yes
valid users = curt, jason


[tyler]
path = /media/storage/tyler
writeable = yes
browseable = yes
valid users = tyler, jason


[pam]
path = /media/storage/pam
writeable = yes
browseable = yes
valid users = pam, jason


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

```

Curt/Tyler/Pam work off of a 250gb SATA HDD I have in my computer, while I (jason) work off of my own home directory.



ALSO - I just noticed... when I rsync my data, my permissions on my folder change... but nobody elses. Like I said, I work off of my home directory. But I have a 500gb hard drive in my computer that I rsync data to, just for backup purposes. When I rsync, my permissions on my server share go to 

owner - jason, create and delete files
group - jason, access files
other - access files

Whereas before they were preset via CLI to

owner - jason, create and delete files
group - sambashare, create and delete files
other - none

Why'd they change? Everybody else's data gets rsynced in the same manner. Why is their's okay but mine change?

---

### Post by bab1 on 2008-11-30
I see you put the "force group = sambashare" in the global section.  That is the correct way to issue a directive for all shares.  You could have added the directive in each share.  You would have to do that if you had a share where you did **not** want the group to be forced.

After all of this, i realize you have not looked into the [homes] share use.  The [homes] share allows you to set up one share for multiple users.  each user has their own directory.  You did the same but you had to make multiple accounts.

here is my [homes] share.  It's good for as many users as I add to the system:
```

[homes]
        comment = Home Directories
        path = /smb/home/%S
        browseable = no
        guest ok = no
        valid users = %S +smbusers [COLOR="Red"]<--Only a login user with the group smbusers allowed[/COLOR]
        force group = smbusers

        writable = yes
        create mask = 770
        directory mask = 770

```

---

### Post by Roasted on 2008-11-30
With the homes share, would I have had the same security for each one? Because in my mind, I'm seeing 1 share all users write to. But I don't want Curt to get into Tyler's backup... know what I mean? That's why I set them up individually with the "valid users" tag. So their stuff is... I guess you could say... confidential? How would "one" share by homes give the same security benefits?

Maybe you explained it, but I'm just not seeing it at the moment.

---

### Post by bab1 on 2008-11-30
The [homes] share allows you to create one share directive for **[COLOR="Blue"]multiple[/COLOR]** directories.  The key to it 
is the variable %S.  The variable is translated into the logged in users name.  If Pam was the logged in user it would mean Pam. If Bozo was the logged in user it would mean Bozo.  Let's use an example.

You have **4 shares** at the moment.  Samba looks to one of those shares to determine which directory to serve files from.  In other words you have **4** of these:
```
[tyler]
path = /media/storage/tyler
writeable = yes
browseable = yes
valid users = tyler, jason
```

You can do the same thing with [COLOR="Blue"]**1 share**[/COLOR].  Like this:
```

[homes]
comment = Home Directories
path = /media/storage/%S      [COLOR="Red"]<--%S = name of the logged in user[/COLOR]
browseable = no
guest ok = no
valid users = %S +sambashares  [COLOR="Red"]<-the +indicates a group[/COLOR]
force group = sambashares
writable = yes
create mask = 770
directory mask = 770

```
The directory structure would be:
```
otal 8.0K
drwxrwx--- 21 curt  sambashares 4.0K 2008-11-19 21:26 curt
drwxrwx---  3 jason sambashares 4.0K 2008-06-13 16:29 jason
drwxrwx---  3 pam sambashares 4.0K 2008-06-13 16:29 pam
drwxrwx---  3 tyler sambashares 4.0K 2008-06-13 16:29 tyler
```

[COLOR="Red"]Edit: Note that there is no browsing for the share.  You might have to map the share for the user.[/COLOR]

---

### Post by Roasted on 2008-11-30
I tried what you said, however, I am unable to log in with my account. It just bumps back to the login screen, prompting me to log in again.

Maybe you can see something I don't. I commented out the existing section and pasted in what you said.

I'm testing the login on my XP Pro laptop.

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
   netbios name = jason-intrepid

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
   create mask = 0770

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0770

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no




[backup]
comment = Home Directories
path = /media/storage/%S     
browseable = yes
guest ok = no
force group = sambashares
valid users = %S +sambashares
writable = yes
create mask = 770
directory mask = 770





force group = sambashare

#[jason]
#path = /home/jason
#writeable = yes
#browseable = yes
#valid users = jason


#[test]
#path = /media/storage/test
#writeable = yes
#browseable = yes
#valid users = test, jason


#[curt]
#path = /media/storage/curt
#writeable = yes
#browseable = yes
#valid users = curt, jason


#[tyler]
#path = /media/storage/tyler
#writeable = yes
#browseable = yes
#valid users = tyler, jason


#[pam]
#path = /media/storage/pam
#writeable = yes
#browseable = yes
#valid users = pam, jason


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

```


ALSO - If you can, look at the "test" section. While logged in as myself "jason" on my XP Pro laptop, I cannot write anything to the "test" share folder. It simply says access denied.

The folder permissions on test is identical to the other server shares.  Yet I can write to them just fine. I can't find where my error is. Note - yes, I have everything uncommented, unlike the code I posted above in response to my other question.

---

### Post by bab1 on 2008-11-30
Is your XP user and smbpasswd login name the same?

Edit: This is a problem ```
[backup]
```  It needs to be called [homes]

---

### Post by Roasted on 2008-11-30
It NEEDS to be called homes? I can't have it called anything else?

My login to my laptop is work assigned, since it's a work laptop, so it is certainly a different login to get into Windows than what I use to log in to Samba.

Also, I had logged in as jason with my smb password and hit "remember this password" so it auto-logs me in every time I start - run - \\my server, etc.

It's just weird because I used to have "test" set up. I took it out this morning when I thought I was done testing random stuff to make sure the permissions are what I wanted. I decided to add test again, so I added it in the same method I did before. But now, I get access denied.

test owns test, just like tyler owns tyler. Both test and tyler have 775 rights, and I can see that in the gui when I check permissions on each folder. I also have writeable = yes in the smb config, just like tyler does. But yet, I get access denied when I try to write folders/files to it.

---

### Post by bab1 on 2008-11-30
yes it hs to be called [homes].  You can map your XP login to your smbpasswd.  The file to map these users is at:```
/etc/samba/smbusers
```
An example of how to add names is at:```
/usr/share/ubuntu-docs/ubuntu/sample/smbusers_addeditdeletenetworkusers
```

I can't tell you what your problems are.  Samba can be complex.  You really should read all the documentation.  See [here]("http://us1.samba.org/samba/docs/") for a start.

---

### Post by Roasted on 2008-11-30
I went to gedit /etc/samba/smbusers to see if "test" is there in an attempt to troubleshoot what's going on. That directory is empty. Should it be? I have 4 other users already preloaded with Samba that should be working fine...

---

### Post by bab1 on 2008-11-30
The /etc/samba/smbusers is **normally empty**.  It's only if you need to have a host login **different** from your Samba login that you edit the file and manually add the mapping.

Edit:  Remember to restart the Samba daemon after every change to the config file -- the command is: ```
sudo /etc/init.d/samba restart
```

---

### Post by rhcm123 on 2008-11-30
> **Roasted said:**
> I appreciate the input with the public idea with no passwords, but I really want passwords. I just want everybody to have a direct 1 to 1 backup method without my brothers like "oh my gosh maybe mom will snoop my backed up pictures and see that picture of..." etc.

And for one, I figured out the one answer. I guess it pays to read directions! At the top of the Samba config file, it said that ; and # are comments, but ; signify comments that are more commonly changed. Guess what was commented! create mask and directory mask. No wonder they didn't work!

So I uncommented them. And bingo... everything comes through as the permissions I want, which is 770.

7 for root
7 for groups (sambashare)
0 for others (no access period)

But this mystery isn't completely solved. When I add files to this directory from my XP Pro laptop, they come through owned by Jason (me).

So even though the root server folder (in this instance, named test... I created a bogus one for testing) is owned by root and group (sambashare) has 100% access to this folder, the actual FILE within the folder that's created is owned by Jason.

Here's a picture.

[http://s2.photobucket.com/albums/y36/Roasted/?action=view&current=samba.png](http://s2.photobucket.com/albums/y36/Roasted/?action=view&current=samba.png)

The left box is the "test" server share permissions.
The right box is the "test file" (which is a bogus docx file)'s permissions.

If possible, I want the docx file (and any other files or directories I throw into this folder) to take on the permissions of the root folder (test). Which is... owned by root, and group - sambashare - full access to anything.

What i do is I have a main directory /share owned by root and chmod 777'ed. I then made a ussr directory for me, a mom directory for my mom, a dad directory for my dad, an elisabeth directory for my sister, etc. I then chowned them their respective owners and chmod 700ed them. This way, the only people who can access them is their respective owners (and since the usernames are the same across the network, it writes as the user on the server, so the permissions still work)

You can do this to set the permissions of subfolders:
```

sudo chmod -R 777 /share 

```
that will set all the subfolders of /share to 777

---

### Post by Roasted on 2008-11-30
rhcm - can you post your smb.conf so I can have an idea of how you set up this folder within a folder samba share? I'd just like to see how your user directories are set up within the share directory.

---

### Post by Roasted on 2008-12-01
Figure this out...

I create the test account. I had the test account before and it worked, then I removed it. But I decided, nah, I better have it for a while till I get my act together with samba. So I added test again. Now, whenever I add files to the test share via my XP Pro laptop, I get access denied.

Yet, if I rename test to "newtest" (in Ubuntu users as well as permissions) BAM... newtest works.  Yet test doesn't.

What the....

EDIT - I even granted 777 rights do the share and granted full blown ownership to jason. Yet, logged in as jason, I can't write anything to that folder. And "jason" is listed under valid users in the smb.conf... I'm so lost.

I added a user "test2" in the same manner I set up "test" and test2 works fine, whereas test still has access denied.

another edit - I'm convinced something is wrong with using "test". I've tried so many other things... test2, tester, and other random garbage, and they all work PERFECTLY. But test does not... So I'm not worried about this issue any longer. I'm assuming that it's a problem with using "test", as I said.

I have some questions about what was posted earlier in reference to the shared folders being routed automatically through the login information. I'm a little unsure about something here. In my system, I have two hard drives. 500gb (main) and 250gb (samba). I have to create the users on my local account in order for Samba to use them. That means the users are created on the 500gb hard drive, along with their home directories. Well, I want their directories to be set on the 250gb drive. If I were to use that one "S" variable to auto-route the logged in Samba users to their share, I assume it would be their home directory, right? Is there any way to have them auto-route to their directories on the 250gb drive instead of their home directories on the 500gb drive? The idea was to keep the network backup on the 250 and to keep my stuff, completely separated, on the 500gb.

Any input? Sorry if I'm beating a dead horse but I'm just trying to get this all clean and clear.

---

### Post by bab1 on 2008-12-01
> **Roasted said:**
> Figure this out...

I create the test account. I had the test account before and it worked, then I removed it. But I decided, nah, I better have it for a while till I get my act together with samba. So I added test again. Now, whenever I add files to the test share via my XP Pro laptop, I get access denied.

Yet, if I rename test to "newtest" (in Ubuntu users as well as permissions) BAM... newtest works.  Yet test doesn't.


What the....

EDIT - I even granted 777 rights do the share and granted full blown ownership to jason. Yet, logged in as jason, I can't write anything to that folder. And "jason" is listed under valid users in the smb.conf... I'm so lost.

I added a user "test2" in the same manner I set up "test" and test2 works fine, whereas test still has access denied.

another edit - I'm convinced something is wrong with using "test". I've tried so many other things... test2, tester, and other random garbage, and they all work PERFECTLY. But test does not... So I'm not worried about this issue any longer. I'm assuming that it's a problem with using "test", as I said.


I'm sure there is something that you are missing.  This problem is not normal.
> 

I have some questions about what was posted earlier in reference to the shared folders being routed automatically through the login information. I'm a little unsure about something here. In my system, I have two hard drives. 500gb (main) and 250gb (samba). I have to create the users on my local account in order for Samba to use them. That means the users are created on the 500gb hard drive, along with their home directories. Well, I want their directories to be set on the 250gb drive. If I were to use that one "S" variable to auto-route the logged in Samba users to their share, I assume it would be their home directory, right?
Wrong.  The local account is an OS based account.  It's home directory is **NOT** the same as the [homes] share.  The only part used is the login name and password for comparison.
>  Is there any way to have them auto-route to their directories on the 250gb drive instead of their home directories on the 500gb drive? The idea was to keep the network backup on the 250 and to keep my stuff, completely separated, on the 500gb.
Actually you can have the home directories wherever you want them, but I would leave them where they are.  Your brothers and sister won't even know they are there.  These home directories are only available to the local user.

To summarize:
The local account and samba user account are compared with the remote logged in user name.  This [COLOR="Blue"]authenticates[/COLOR] the user (who are you?).

The share defines a file structure in the OS file system.  It also can define the first layer of security by requiring user [COLOR="Blue"]authentication.[/COLOR]  

Beyond these authentication mechanisms,   we have the OS file system permissions.  These permissions define [COLOR="Green"]authorization[/COLOR] (do you have permission).

In other words you have [COLOR="Blue"]accounts[/COLOR] for [COLOR="Blue"]authentication[/COLOR] and the underlying [COLOR="Green"]file system[/COLOR] for [COLOR="Green"]authorization[/COLOR]

> 

Any input? Sorry if I'm beating a dead horse but I'm just trying to get this all clean and clear.

Please post your share section of the smb.conf file and the relevant directory/file structure and I'll check it out.

---

### Post by Roasted on 2008-12-01
bab1 - I gotta say, thanks a lot for your time and patience with all of this input. I really appreciate it!

I'm at work right now but I shall post the section you asked about from my smb.conf file.

And about the homes/home dir confusion... is the default path for the "homes" share for each user just their home directory? Maybe that's where I got confused... by seeing the default listed as their home directory and thought that was required... So in my instance, I could put /media/storage/%S as the path... because all users are housed in /media/storage, and from there they just have their designated user shares.



About the test account error I'm getting... I'm not missing a step... I know this because I set up the test account at the same time I set up "tester" account. I literally would do this...

sudo smbpasswd -a test
sudo smbpasswd -a tester
sudo chown -R test:sambashare test
sudo chown -R tester:sambashare tester

etc... I did each command, 1 at a time until I was finished with both accounts. Test gave me an error. Tester did not. Also their settings in smb.conf is the same, too. It's just odd because I've had no errors with any other bogus account I create. It's ONLY test...

And for the record, before I started all of this with comparing test and tester, I deleted their home directories, the ubuntu user account for them, and the ubuntu group that gets created when you make a new user. So realistically there was no trace of them on the system. I also ran sudo smpbasswd -x on both of them so they were deleted off of Samba before I started. I'm just flat out confused over this one...

---

### Post by rhcm123 on 2008-12-01
> **Roasted said:**
> Hmm... you make a lot of sense. The owner of the files really doesn't matter I guess.

Now I'm even starting to wonder why I have the sambashare group. What use does having a group with samba offer? Does that just allow me (being a sambashare member) have the ability to change files that are owned by another user?

Ok, permissions 101.
In linux, there are 3 classes of permissions, the Owner, the Group, and The Others (lost reference!). 

The owner: The owner is typically the creator of the file, although that can be changed with the chown command. Don't go around chowning randomly, as some things are owned by different users for a reason.

The Group: Anybody in the group set by the owner. There is a command line command for this, i just don't know it. This is what you were asking about. I'll explain the types of permissions in a moment.

The Others: Everybody else. You put a file on the interwho, this is who gets the permissions.


Now, there are 4 different accesibility levels granted by linux.
0 - Cannot even read the file. Can see it exists, but nothing more.
1 - Can read the code of the file.
2 - Can write to the file
3 - (NO 3, you'll see in a minute)
4 - Can execute the file.

The permissions are changed with the chmod command.
When using the chmod command, i must do the following format (there are others, but this is the basic one): chmod xyz /path/to/file
If the file is not owned by you, you must use sudo. (Root has overwhelming authority to change and override permissions.)

The x variable is the value you assign to yourself, the owner.
the y variable is the value you assign to your group.
the z variable is the value you assign for everybody else.


This may seem counter intuitive, but if i want to make the file /root/example executable, i would have to do chmod 777 /root/example. Why? Because with chmod, if you use an argument, such as 4 you also have to give it all the other arguments beneath it, like 2 and 1, lest you get permissions errors (if you just did 4, it could run the file but not read it.)

For instance, if I did wanted to make a file readable and writeable, I would have to do 2 and 1. For efficiency, however, have to add them together in one command. Two and One add up to three, so I would use 3.
So, if I wanted to make the file executable for me, readable for my group, and readable and writeable for everybody else I would do chmod 713 /root/example

I think i explained this well enough. Ask me if you have any problems.

---

### Post by bab1 on 2008-12-01
> **rhcm123 said:**
> Ok, permissions 101.
In linux, there are 3 classes of permissions, the Owner, the Group, and The Others (lost reference!). 

The owner: The owner is typically the creator of the file, [COLOR="Blue"]Not trying to be picky, but in the interests of accuracy -- The owner is ALWAYS the creator[/COLOR]

> although that can be changed with the chown command. Don't go around chowning randomly, as some things are owned by different users for a reason.

The Group: Anybody in the group set by the owner.
[COLOR="Blue"]The group is not set by the owner.  It is set by the sysadmin.  It is the primary group specified when the user is added to the system[/COLOR]
>  There is a command line command for this, i just don't know it. This is what you were asking about. I'll explain the types of permissions in a moment.

The Others: Everybody else. You put a file on the interwho, this is who gets the permissions.
[COLOR="Blue"]Or others on the host or network LAN.[/COLOR]
> 


Now, there are 4 different accesibility levels granted by linux.

[COLOR="Blue"]These are not levels although they may appear to be.  They are bitwise operators on the file. for the owner 7 bits gets rwx, 6 bits gets rw, 5 bits gets r-x ,4 bits gets r-- and 1 bit gets --x.  This looks to be added up but it is really not.  It's **anded** not added  This same convention is then applied to the group and the "other" users. [/COLOR]
> 

0 - Cannot even read the file. Can see it exists, but nothing more.
1 - Can read the code of the file.
2 - Can write to the file
3 - (NO 3, you'll see in a minute)
4 - Can execute the file.

The permissions are changed with the chmod command.
When using the chmod command, i must do the following format (there are others, but this is the basic one): chmod xyz /path/to/file
If the file is not owned by you, you must use sudo. (Root has overwhelming authority to change and override permissions.)

The x variable is the value you assign to yourself, the owner.
the y variable is the value you assign to your group.
the z variable is the value you assign for everybody else.


This may seem counter intuitive, but if i want to make the file /root/example executable, i would have to do chmod 777 
[COLOR="Blue"]Executable by whom?  You can make it executable but not writable by the group and readable only by the owner and others.  that would be chmod 454 (r-- r-x r--).  [/COLOR]
> /root/example. Why? Because with chmod, if you use an argument, such as 4 you also have to give it all the other arguments beneath it, like 2 and 1, lest you get permissions errors (if you just did 4, it could run the file but not read it.)

[COLOR="Blue"]This make no sense at all.[/COLOR]
> 

For instance, if I did wanted to make a file readable and writeable, I would have to do 2 and 1. For efficiency, however, have to add them together in one command. Two and One add up to three, so I would use 3.
So, if I wanted to make the file executable for me, readable for my group, and readable and writeable for everybody else I would do chmod 713 /root/example
[COLOR="Blue"]The correct mode for executable only  (--x) by the owner and readable and writeable (rw-) by both the the group and others is: 166.  This obviously makes no sense.  I believe the poster really meant this: owner = read, write, execute (rwx) group = read, write (rw-) and others = read, write (rw-).  This would set the bits to 766 - try it: chmod 766 <file> gets exactly that. [/COLOR]

> 



I think i explained this well enough. Ask me if you have any problems.

[COLOR="Blue"]On last thing - there are 4 digits representing file permission modes.  Most think of 3 but there is a 4th group.  It is the leading digit. This is a legit permissions mode -- 3755.  The trailing 755 we have discussed.  The leading 3 is for the sticky bit, This leading digit can be 0, 1, 2, 3 or 4. See the chmod man pages for more info.[/COLOR]

---

### Post by Roasted on 2008-12-02
Even though the SysAdmin* has the ability to change the group, you can also do that through chown.

Example... here's what I did...

sudo chown -R jason:sambashare jason

sudo - root
chown - change ownership
-R - recursive (files/folders within the main one I'm changing)
jason - owner of the directory in question
:sambashare - group who has access to the folder
jason #2 - folder in question is named "jason"

*What kind of command would I use with sysadmin to set group access WITHOUT the chown command like I did above? 

FYI - Say Curt owned a folder that I wanted him to own, but I wanted sambashare to be that group. I would just keep him as the owner in the command... ex - sudo chown -R curt:sambashare curt




EDIT - Gotta love google.

"This manual page documents the GNU version of chown. chown changes the user and/or group ownership of each given file. If only an owner (a user name or numeric user ID) is given, that user is made the owner of each given file, and the files' group is not changed. If the owner is followed by a colon and a group name (or numeric group ID), with no spaces between them, the group ownership of the files is changed as well. If a colon but no group name follows the user name, that user is made the owner of the files and the group of the files is changed to that user's login group. **If the colon and group are given, but the owner is omitted, only the group of the files is changed; in this case, chown performs the same function as chgrp. If only a colon is given, or if the entire operand is empty, neither the owner nor the group is changed."**

---

### Post by bab1 on 2008-12-02
> **Roasted said:**
> Even though the SysAdmin* has the ability to change the group, you can also do that through chown.

Example... here's what I did...

sudo chown -R jason:sambashare jason

sudo - root
chown - change ownership
-R - recursive (files/folders within the main one I'm changing)
jason - owner of the directory in question
:sambashare - group who has access to the folder
jason #2 - folder in question is named "jason"

*What kind of command would I use with sysadmin to set group access WITHOUT the chown command like I did above? 
:-) ...  [COLOR="Blue"]I think we need to step back and look at this from a wider perspective.  If we are talking about and already existing  file with inappropriate ownership and group settings then *chown <user>:<group>* is the correct way.  To change the group only we can use *chgrp*.

But; consider this -- How can we produce this same end result when the file is originally created? Two ways come to mind. 

The sysadmin has the ability to **assign the  primary group** when the user is created.  This will be the group setting on the file when the user creates it.

When administering Samba you can use the "force group = <group>" to achieve the desired group during file creation regardless of the users primary group.[/COLOR]
> 

FYI - Say Curt owned a folder that I wanted him to own, but I wanted sambashare to be that group. I would just keep him as the owner in the command... ex - sudo chown -R curt:sambashare curt




EDIT - Gotta love google.

"This manual page documents the GNU version of chown. chown changes the user and/or group ownership of each given file. If only an owner (a user name or numeric user ID) is given, that user is made the owner of each given file, and the files' group is not changed. If the owner is followed by a colon and a group name (or numeric group ID), with no spaces between them, the group ownership of the files is changed as well. If a colon but no group name follows the user name, that user is made the owner of the files and the group of the files is changed to that user's login group. **If the colon and group are given, but the owner is omitted, only the group of the files is changed; in this case, chown performs the same function as chgrp. If only a colon is given, or if the entire operand is empty, neither the owner nor the group is changed."**

[COLOR="Blue"]You don't need to search Google for this.  This information installed along with the OS.  These are the man (manual) pages.  Try this from the command line of the terminal:[/COLOR]```
man chown
```

---

### Post by Roasted on 2008-12-03
What are the average transfer speeds of NFS, Samba, etc? 

I'm getting 7.7mb/sec. Is that considered good?

---

### Post by bab1 on 2008-12-03
> 7.7mb/sec. Is this Mega bits (Mb) or Mega Bytes (MB)?

I assume you mean MBs as in megabytes per second. The equivalent in megabits  is roughly 60 Mbs. Fast Ethernet is 100 Mbs.  There are too many factors to be considered when assessing average speed. I don't  really have a yardstick on what average speeds are.  I/O, CPU and network configuration are just a few of the variables in the equation.

I know this does not directly answer your question, but average speed is not a valid criterion for choosing either Samba or NFS. Functionality in your network is a more important consideration.

If you have system that is much slower than you other hosts I would not look to either Samba or NFS as the culprit.

---

### Post by Roasted on 2008-12-04
Well, I am running 8.10 on an old 256mb system behind me which I was testing the push/pull speeds from.

I was just curious on if 7mb was looked at as half decent or if it was  like "Whoa, that's slow!" despite the slow computer I'm working with.

---

### Post by rhcm123 on 2008-12-04
> **Roasted said:**
> Well, I am running 8.10 on an old 256mb system behind me which I was testing the push/pull speeds from.

I was just curious on if 7mb was looked at as half decent or if it was  like "Whoa, that's slow!" despite the slow computer I'm working with.

Yeah, that's close enough for government work. Mine typically pulls out about 170 mbps over gigabit, 80-ish over mbit.

---

### Post by rhcm123 on 2008-12-04
> **Roasted said:**
> rhcm - can you post your smb.conf so I can have an idea of how you set up this folder within a folder samba share? I'd just like to see how your user directories are set up within the share directory.

I'll have to get back to you on this, perhaps in a day or so. I'm using windows because i have to do some actual work on it that i can't do on ubuntu, so i'll be offline for a while (and my samba server is headles.. :) )

---

### Post by rhcm123 on 2008-12-04
> **bab1 said:**
> [COLOR="Blue"]Not trying to be picky, but in the interests of accuracy -- The owner is ALWAYS the creator[/COLOR]

Unless it is changed :)


> **bab1 said:**
> [COLOR="Blue"]
The group is not set by the owner.  It is set by the sysadmin.  It is the primary group specified when the user is added to the system[/COLOR]
The user's group is set by the sysadmin (aka anybody with root access). The file's group can be changed with chgrp.

> **bab1 said:**
> [COLOR="Blue"]
Or others on the host or network LAN.[/COLOR]
Agreed. Essentially, anybody else.

> **bab1 said:**
> [COLOR="Blue"]
These are not levels although they may appear to be.  They are bitwise operators on the file. for the owner 7 bits gets rwx, 6 bits gets rw, 5 bits gets r-x ,4 bits gets r-- and 1 bit gets --x.  This looks to be added up but it is really not.  It's **anded** not added  This same convention is then applied to the group and the "other" users. [/COLOR]
I was trying to avoid getting to technical, but yes, this is true.

> **bab1 said:**
> [COLOR="Blue"]
Executable by whom?  You can make it executable but not writable by the group and readable only by the owner and others.  that would be chmod 454 (r-- r-x r--).  [/COLOR]
This is true. I belive I got a twill bit confusing at the end.

> **bab1 said:**
> [COLOR="Blue"]
This make no sense at all.[/COLOR]
I'm sorry, I got too complicated by making it too simple.

> **bab1 said:**
> [COLOR="Blue"]
The correct mode for executable only  (--x) by the owner and readable and writeable (rw-) by both the the group and others is: 166.  This obviously makes no sense.  I believe the poster really meant this: owner = read, write, execute (rwx) group = read, write (rw-) and others = read, write (rw-).  This would set the bits to 766 - try it: chmod 766 <file> gets exactly that. [/COLOR]
You are right. I thought I typed 766 :).

> **bab1 said:**
> [COLOR="Blue"]
On last thing - there are 4 digits representing file permission modes.  Most think of 3 but there is a 4th group.  It is the leading digit. This is a legit permissions mode -- 3755.  The trailing 755 we have discussed.  The leading 3 is for the sticky bit, This leading digit can be 0, 1, 2, 3 or 4. See the chmod man pages for more info.[/COLOR]
I was, again, trying to avoid technicality.

---

### Post by Roasted on 2008-12-04
> **rhcm123 said:**
> Yeah, that's close enough for government work. Mine typically pulls out about 170 mbps over gigabit, 80-ish over mbit.

Wait, are you agreeing with me 7 meg is decent, yet you're saying 80-ish is what you get??

---

### Post by bab1 on 2008-12-05
@Roasted and rhcm123,

> Wait, are you agreeing with me 7 meg is decent, yet you're saying 80-ish is what you get??

Shouldn't we try and be a little more precise in our statements.  There are 8 bits in a byte.  When one says meg, the first thing I think is; Meg of what?  If we say 100 Mbs (100 Mega bits per second(Fast Ethernet)) we are also saying 1250000 bits/sec, 125 Kilo Bytes/sec or 12.5 Mega Bytes/sec.  

> ...Mine typically pulls out about 170 mbps over gigabit, 80-ish over mbit.  If we meant Mega Bytes here then 170 would be 1.36 GB.  Not very likely.  So we must be referring to Mega bits, eh.  Then we have 170 Mega bits which is  21.25 Mega Bytes per second (a rough reference would be 2 times fast Ethernet).  Not bad, but not full Giga bit potential. On the other hand 80 Mbs can be stated as 10MBs which is just about the full potential of Fast Ethernet (see above).  Draw your own conclusions from the data, but please try and be more precise in your definition.

So why are some things measured in bits and others in bytes?  Bits are used to measure the capacity to carry the bit stream across buses and NICs.  Humans don't need to read the data.

Bytes are used to measure human readable data.  A byte is the smallest unit that can define a ASCI character (letters, numbers, etc.).  In other words you need 8 bits or 1 byte to define an ASCI character.  A 2KB ASCI text document has roughly 2000 characters (including spaces and a little for overhead).

---

### Post by Roasted on 2008-12-05
Not to be a smartass here, but... really? Do people still talk in terms of bytes? 

I'm in IT support and the only terms I use, and need to use, are megabyte, gigabyte, terabyte...

---

### Post by bab1 on 2008-12-05
> Not to be a smartass here, but... really? Do people still talk in terms of bytes? No, I don't think your being a smartass. Lack of experience is not crime.  At least you ask.  As I stated previously, the term bit is used in when referring to speed of physical buses and in particular NIC's.  See the Gigabit reference [here]("http://www.intel.com/network/connectivity/products/desktop_adapters.htm?cid=cim:ggl|lad_dsktp_adap|kAD3|s#s1=Gigabit&s2=all&s3=all") and [here]("http://whitepapers.techrepublic.com.com/abstract.aspx?docid=85366").

Typically the byte is the lowest size used when referring to data stored in either RAM or in the form of a file.

> I'm in IT support and the only terms I use, and need to use, are megabyte, gigabyte, terabyte...

Do you provide customer support?  Most of the time people are referring to stored data and byte would be a proper term.  

Our discussion, on the other hand was regarding the speed from NIC to NIC. Speed or Storage...hmmm. I agree that it was ultimately data, but not stored data.  That's why I feel we should be precise in our terms. It really doesn't mater which term we use as long as we are both using the same unit of measure. The term "mb" can be either megabits or megabytes.  The term Mb is generally used for megabit and the term MB for megabyte.

---

### Post by Roasted on 2008-12-06
I provide customer support in a different way, I guess. I work at a school district, and I am assigned to 3 of the 8 schools in the district to manage front to back.

It just goes along with what you're speaking about in terms of topic. If I'm talking about a networking issue and I say "Yeah, I'm only gettin 11 meg" then you know what I mean. 

Anyway, let's roll back to the original question at hand.

I am transferring 7.7Mb (?) per second. What would that be considered? Average? Pretty good? Poor?

---

### Post by bab1 on 2008-12-06
> I am transferring 7.7Mb (?) per second. What would that be considered? Average? Pretty good? Poor?

Sounds good to me.  :-)

---

### Post by Roasted on 2008-12-06
> **bab1 said:**
> Sounds good to me.  :-)

Ha, sounds good. I just didn't know how to gauge that number. I wasn't sure if people were pullin 300Mb or .5Mb. I just didn't know how that stacked up.

---

### Post by rhcm123 on 2008-12-07
> **Roasted said:**
> Ha, sounds good. I just didn't know how to gauge that number. I wasn't sure if people were pullin 300Mb or .5Mb. I just didn't know how that stacked up.

I transefered 100 megabytes of video data in about 3 seconds over fast ethernet. On my wifi, that transfer took about 1 minute. I guess it's just your connection. (Mine mounts the share from /etc/fstab, which i have found makes it a twill bit faster.)

My smb file, cause you asked (anything in double parenthesis is somthing you have to personalize):

```
# Global parameters
[global]
	log file = /var/log/samba/log.%m
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	map to guest = Bad User
	wins support = true
	dns proxy = No
	netbios name = ((YOUR HOSTNAME))
	server string = ((WHATEVER YOU WANT TO CALL YOUR SERVER))
	default = Share
	local master = No
	workgroup = ((YOUR WINDOWS WORKGROUP))
	os level = 20
	security = user
	preferred master = no
	max log size = 50

# Share Folder (/share) configs
[share]
	path = ((DIRECTORY DO BE SHARED))
	valid users = ((USERS, ORGINIZED AS SUCH: nobody root user ))
	read only = No
	browseable = yes
	comment = SAMBA directory on ((HOSTNAME))
	create mask = 0700
	directory mask = 0700

```

---

### Post by Roasted on 2008-12-07
You transferred 100Mb in 1 minute wirelessly... which equates to 1.66Mb/second.

I transferred 650Mb in 5 minutes time wirelessly... which equates to about the same... 2Mb or so per second.

However, you also said you transferred 100Mb in 3 seconds on wired network... averaging 33Mb/second. On wired, I transfer 7Mb/second.

So, our wireless speeds are comparable, but wired... wow.

Are you on a gigabit network?

---

### Post by rhcm123 on 2008-12-08
> **Roasted said:**
> You transferred 100Mb in 1 minute wirelessly... which equates to 1.66Mb/second.

I transferred 650Mb in 5 minutes time wirelessly... which equates to about the same... 2Mb or so per second.

However, you also said you transferred 100Mb in 3 seconds on wired network... averaging 33Mb/second. On wired, I transfer 7Mb/second.

So, our wireless speeds are comparable, but wired... wow.

Are you on a gigabit network?

Nope, standard 100 mbps network. Hmmm.... is your samba server headed or headless? How is your network organized (how does the traffic get from your server to your machine?). Thats the only thing i can think of for mine being over 4 times faster than yours.

---

### Post by Roasted on 2008-12-08
Headed or Headless? What does this mean?

This is how everything is organized.

Linksys WRT54G Router 

- Family Computer
- Brother's Computer
- Other Brother's Computer
- Netgear 10/100 Fast Ethernet Switch
Running off of the Netgear switch...
- XBOX 360
- My Computer
- Spare Computer 
- Empty

I transfer 650mb ISO's between My Computer and Spare Computer I in order to see what kind of speeds I pull. I wait until the clock hits a new minute and I time it from there. After some basic math, I came up with the basic  Mb/sec I posted earlier.

XP Wireless - to - Ubuntu Samba Server = 2Mb/second
XP Wired - to - Ubuntu Samba Server = Upwards of 10Mb/second (spare computer)
Ubuntu Wired - to - Ubuntu Samba Server = Avgerage of 7.1Mb/second (spare computer)


Spare Computer = 512mb 1.3Ghz AMD Athlon with 10/100 PCI NIC.

EDIT - I've done some more reading, and it seems to be a general consensus that in a perfect world on a 54mbps router, you'd be looking at a max of 12MB/second. Are you sure you're pulling 30?? Everywhere I read suggests that.







EDIT AGAIN - I just did a test using 3 computers. All of them are plugged into a 10/100 Netgear switch, which the Netgear switch in question plugs into a WRT54G Linksys router.

Using a 650mb ISO file, I tested the connection between...

XP Pro Desktop - to - XP Pro Desktop = 7.8MB/second
XP Pro Desktop - to - Ubuntu Server = also, 7.8MB/second.

So, I can rest assured when I hear people say "omgawsh Samba is slow" that mine, indeed, isn't suffering... from what I can tell, at least! And I've just got a real basic setup, too... I wonder how in the world anybody else had trouble! *shrug*

---

### Post by rhcm123 on 2008-12-11
> **Roasted said:**
> Headed or Headless? What does this mean?

This is how everything is organized.

Linksys WRT54G Router 

- Family Computer
- Brother's Computer
- Other Brother's Computer
- Netgear 10/100 Fast Ethernet Switch
Running off of the Netgear switch...
- XBOX 360
- My Computer
- Spare Computer 
- Empty

I transfer 650mb ISO's between My Computer and Spare Computer I in order to see what kind of speeds I pull. I wait until the clock hits a new minute and I time it from there. After some basic math, I came up with the basic  Mb/sec I posted earlier.

XP Wireless - to - Ubuntu Samba Server = 2Mb/second
XP Wired - to - Ubuntu Samba Server = Upwards of 10Mb/second (spare computer)
Ubuntu Wired - to - Ubuntu Samba Server = Avgerage of 7.1Mb/second (spare computer)


Spare Computer = 512mb 1.3Ghz AMD Athlon with 10/100 PCI NIC.

EDIT - I've done some more reading, and it seems to be a general consensus that in a perfect world on a 54mbps router, you'd be looking at a max of 12MB/second. Are you sure you're pulling 30?? Everywhere I read suggests that.







EDIT AGAIN - I just did a test using 3 computers. All of them are plugged into a 10/100 Netgear switch, which the Netgear switch in question plugs into a WRT54G Linksys router.

Using a 650mb ISO file, I tested the connection between...

XP Pro Desktop - to - XP Pro Desktop = 7.8MB/second
XP Pro Desktop - to - Ubuntu Server = also, 7.8MB/second.

So, I can rest assured when I hear people say "omgawsh Samba is slow" that mine, indeed, isn't suffering... from what I can tell, at least! And I've just got a real basic setup, too... I wonder how in the world anybody else had trouble! *shrug*

Headed = Has a gui, such as GNOME or XFCE
Headless = Just a command shell

Well, our wifi rates are matched because my router is only 100 mbps, going into a gigabit switch. My laptop is plugged into said switch.
And it's not samba, it's SMB thats slow. But for data transfer, I can stream music over the wifi in a snap! (I installed jinzora2 onto my apache web server, and then just used my smb shared directories to hold the music, and even my command line only machine can play it with cplay.

---

### Post by Roasted on 2008-12-11
So wait, you're working off of a gigabit switch... 

The other computer you're transferring documents to in order to get that "MB/second" number you pulled earlier, is it also plugged into that gigabit switch?

If so, that may be why... cause if you're transferring locally on that switch @ gigabit speeds, the router shouldn't bottleneck it to 100... whereas my switch AND router are 10/100 so I'm stuck all the way around.

Plus I think I said this earlier but I transferred a  650MB ISO file as a test between two XP computers on my 10/100 switch and I also got 7.5 MB/second or so.. exactly the same I get in Samba. So I know Samba isn't "slow" in comparison to anything. It's right on up there!!

---

### Post by rhcm123 on 2008-12-11
> **Roasted said:**
> So wait, you're working off of a gigabit switch... 

The other computer you're transferring documents to in order to get that "MB/second" number you pulled earlier, is it also plugged into that gigabit switch?

If so, that may be why... cause if you're transferring locally on that switch @ gigabit speeds, the router shouldn't bottleneck it to 100... whereas my switch AND router are 10/100 so I'm stuck all the way around.

Plus I think I said this earlier but I transferred a  650MB ISO file as a test between two XP computers on my 10/100 switch and I also got 7.5 MB/second or so.. exactly the same I get in Samba. So I know Samba isn't "slow" in comparison to anything. It's right on up there!!

Yes, both my start point and endpoint are on the gigabit switch. When i wifi to the machine though, our speeds are relatively the same.

But your speeds are good enough for government work!

---

