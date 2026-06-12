---
title: "Mounting automatically a network shared folder with fstab"
date: 2015-01-01
forum: Networking &amp; Wireless
---

### Post by balubeto on 2015-01-01
Hi

I have a computer on my network that has Lubuntu 14.04 32 bit with many accounts and a NAS that shares, via Login, its folders with the Samba protocol.

 I wish that a network shared folder was mounted automatically when the computer is started so that all users could access it, without Login, in reading, writing and running.

 So, what was the proper procedure to do this by configuring appropriately also the file /etc/fstab?

Thanks

Bye

---

### Post by blitzit on 2015-01-01
Hi,

You will need to know 2 things about your NAS before this can be done.
1) The IP address of the NAS share
2) The Share Name (or the folder) being shared by the NAS

After you are sure about these two, open a terminal window and type the following command to create a mount-point for your NAS:
sudo mkdir /media/NAS

Install the cifs-utils package install using apt-get:
sudo apt-get install cifs-utils

Create a Samba Credentials File (/root/.smbcredentials) inside root so that your NAS username and password is not written in an exposed way. The following command uses the nano editor. You could use any editor of your choice.
sudo nano /root/.smbcredentials

The .smbcredentials file should look something like this:
username=your_username
password=your_password

Save the file and close the editor.

Then edit your /etc/fstab to add this line at the very end of the file that will mount the NAS
//NASIP1.NASIP2.NASIP3.NASIP4/ShareName /media/NAS cifs credentials=/root/.smbcredentials,rw,file_mode=0777,dir_mode=0777,uid=1000,gid=1000,iocharset=utf8,sec=ntlm 0 0

An example for this would be:
//10.10.64.255/ShareVolume /media/NAS cifs credentials=/root/.smbcredentials,rw,file_mode=0777,dir_mode=0777,uid=1000,gid=1000,iocharset=utf8,sec=ntlm 0 0

Save the file and close the editor.

From the terminal window issue the following command to mount immediately.
sudo mount -a

Your NAS should now be mounted on /media/NAS and shall remount automatically on reboot as long as the IP is reachable through the network. Hope that helps.

---

### Post by SeijiSensei on 2015-01-01
Is this an all-Linux environment, or are the users running Windows?  If everyone is running Linux, you should use [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") rather than Samba to share files.  Then you can add a line to /etc/fstab like
```
servername:/path/to/share    /media/share   nfs    defaults 0 0 
```
and the remote share will be mounted to /media/share at boot.

---

### Post by balubeto on 2015-01-02
> **blitzit said:**
> Hi,

You will need to know 2 things about your NAS before this can be done.
1) The IP address of the NAS share
2) The Share Name (or the folder) being shared by the NAS

After you are sure about these two, open a terminal window and type the following command to create a mount-point for your NAS:
sudo mkdir /media/NAS

Install the cifs-utils package install using apt-get:
sudo apt-get install cifs-utils

Create a Samba Credentials File (/root/.smbcredentials) inside root so that your NAS username and password is not written in an exposed way. The following command uses the nano editor. You could use any editor of your choice.
sudo nano /root/.smbcredentials

The .smbcredentials file should look something like this:
username=your_username
password=your_password

Save the file and close the editor.

Then edit your /etc/fstab to add this line at the very end of the file that will mount the NAS
//NASIP1.NASIP2.NASIP3.NASIP4/ShareName /media/NAS cifs credentials=/root/.smbcredentials,rw,file_mode=0777,dir_mode=0777,uid=1000,gid=1000,iocharset=utf8,sec=ntlm 0 0

An example for this would be:
//10.10.64.255/ShareVolume /media/NAS cifs credentials=/root/.smbcredentials,rw,file_mode=0777,dir_mode=0777,uid=1000,gid=1000,iocharset=utf8,sec=ntlm 0 0

Save the file and close the editor.

From the terminal window issue the following command to mount immediately.
sudo mount -a

Your NAS should now be mounted on /media/NAS and shall remount automatically on reboot as long as the IP is reachable through the network. Hope that helps.

I performed your procedure, but when I access this network directory with PCManFM, I get this error message: "mount: only root can mount //<Server_name>/<Share_directory> on /media/<Point_mount>". How come?

Thanks

Bye

---

### Post by balubeto on 2015-01-02
> **SeijiSensei said:**
> Is this an all-Linux environment, or are the users running Windows?  If everyone is running Linux, you should use [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") rather than Samba to share files.  Then you can add a line to /etc/fstab like
```
servername:/path/to/share    /media/share   nfs    defaults 0 0 
```
and the remote share will be mounted to /media/share at boot.

Unfortunately, I also users who use Windows to access the NAS.

Thanks

Bye

---

### Post by SeijiSensei on 2015-01-02
> **balubeto said:**
> I performed your procedure, but when I access this network directory with PCManFM, I get this error message: "mount: only root can mount //<Server_name>/<Share_directory> on /media/<Point_mount>". How come?

As always, the best answers come from the "man" pages.  "man mount" reports:
> 
The non-superuser mounts.
Normally,  only the superuser can mount filesystems.  However, when fstab contains the user option on a line, anybody can mount the corresponding system.

Thus, given a line

              /dev/cdrom  /cd  iso9660  ro,user,noauto,unhide

any user can mount the iso9660 filesystem found on his CDROM using the command
              mount /dev/cdrom
              or
               mount /cd

For more details, see fstab(5).  Only the user that mounted a filesystem can unmount it again.  If any user should be able to unmount,  then use users instead of user in the fstab line.  The owner option is similar to the user option, with the restriction that the user must be the owner of the special file. This may be useful e.g. for /dev/fd if a login script makes the console user owner of this device.  The group option  is  similar, with the restriction that the user must be member of the group of the special file.


---

### Post by balubeto on 2015-01-03
> **SeijiSensei said:**
> As always, the best answers come from the "man" pages.  "man mount" reports:

If I use the users parameter to the users group in the /etc/fstab and I insert each user in the Linux users group how do I create the special file so that all users, belonging to the Linux users group, can mount and unmount a network directory that has its mount point in /media/<mount_point>?

Thanks

Bye

---

### Post by SeijiSensei on 2015-01-04
Add the "file_mode" and "dir_mode" items to the options list of the entry in /etc/fstab as described here: [http://unix.stackexchange.com/questions/106596/granting-all-users-access-to-mounted-cifs-shares](http://unix.stackexchange.com/questions/106596/granting-all-users-access-to-mounted-cifs-shares).

---

### Post by balubeto on 2015-01-05
> **SeijiSensei said:**
> Add the "file_mode" and "dir_mode" items to the options list of the entry in /etc/fstab as described here: [http://unix.stackexchange.com/questions/106596/granting-all-users-access-to-mounted-cifs-shares](http://unix.stackexchange.com/questions/106596/granting-all-users-access-to-mounted-cifs-shares).

So, should I create a new group, insert all users who will be using the network directory, get the GID of the new group (how?) and insert in the file /etc/fstab the gid=<New_group_Number>,file_mode=0770,dir_mode=0770 options. Right?

Thanks

Bye

---

### Post by bab1 on 2015-01-05
> **balubeto said:**
> So, should I create a new group, insert all users who will be using the network directory, get the GID of the new group (how?) and insert in the file /etc/fstab the gid=<New_group_Number>,file_mode=0770,dir_mode=0770 options. Right?

Thanks

Bye
This would allow **access**.  But what about a file or directory that is ***created** * in that directory?  By default, a file would have the ownership of <user1:user1>.  To overcome that you need to use *force group = <New_group>* in the share definition.

---

### Post by SeijiSensei on 2015-01-06
Quickest way to identify the GID:
```
grep group_name /etc/group
```

---

### Post by balubeto on 2015-01-06
> **bab1 said:**
> This would allow **access**.  But what about a file or directory that is ***created** * in that directory?  By default, a file would have the ownership of <user1:user1>.  To overcome that you need to use *force group = <New_group>* in the share definition.

So, to be able to also create files and directories in the shared directory (and subdirectories), I should put the forcegroup=<New_group_name> or forcegid,rw options. Correct?

 Since I have a lot of confusion in the head, someone could write all the parameters that I should insert in the file /etc/fstab in order to reach my goal?

Thanks

Bye

---

### Post by bab1 on 2015-01-06
> **balubeto said:**
> So, to be able to also create files and directories in the shared directory (and subdirectories), I should put the forcegroup=<New_group_name> or forcegid,rw options. Correct?

 Since I have a lot of confusion in the head, someone could write all the parameters that I should insert in the file /etc/fstab in order to reach my goal?

Thanks

Bye
You should always be able to create files and directories.  The suggestion is to have these created object have the group ownership you expect.

You add force group = <New_group_name> in the /etc/samba/smb.conf file in the share definition section that you are then going to mount remotly.  It is not a /etc/fstab parameter at all.

---

### Post by bab1 on 2015-01-06
> **SeijiSensei said:**
> Quickest way to identify the GID:
```
grep group_name /etc/group
```

A safer way for a newbie is to use this```
getent group <group_name>
```

---

### Post by balubeto on 2015-01-07
> **bab1 said:**
> You should always be able to create files and directories.  The suggestion is to have these created object have the group ownership you expect.

You add force group = <New_group_name> in the /etc/samba/smb.conf file in the share definition section that you are then going to mount remotly.  It is not a /etc/fstab parameter at all.

In conclusion, what are the parameters that I should insert in the /etc/fstab file?

Thanks

Bye

---

### Post by balubeto on 2015-01-08
I inserted, in the sambashare group, the accounts that will use the network directory. Then, I added, in the /etc/fstab, this line:

```

//<Server_name>/<Share_directory> /media/<Point_mount> cifs credentials=/root/.smbcredentials,file_mode=0775,dir_mode=0775,gid=118,forcegid,iocharset=utf8 0 0

```

Later, I put the force group = sambashare directive in /etc/samba/smb.conf and I restarted the system.

Now, if I write:

```

[EMAIL="xxxxxxx@Pluto:~$"]xxxxxxx@Pluto:~$[/EMAIL] sudo mount -a

```

I get:

```

mount error: could not resolve address for <Server_name>: Unknown error

```

Instead, if I access directly to this resource by PCManFM, I get this error:

```

mount: only root can mount //<Server_name>/<Share_directory> on /media/<Point_mount>

```

This network resource can I use it normally if I access it via the menu Go ---> Network of PCManFM.

How come?

Thanks

Bye

---

### Post by bab1 on 2015-01-08
> **balubeto said:**
> I inserted, in the sambashare group, the accounts that will use the network directory. Then, I added, in the /etc/fstab, this line:

//<Server_name>/<Share_directory> /media/<Point_mount> cifs credentials=/root/.smbcredentials,file_mode=0775,dir_mode=0775,gid=118,forcegid,iocharset=utf8 0 0

Later, I put the force group = sambashare directive in /etc/samba/smb.conf and I restarted the system.

Now, if I write:

[EMAIL="xxxxxxx@Pluto:~$"]xxxxxxx@Pluto:~$[/EMAIL] sudo mount -a

I get:

mount error: could not resolve address for <Server_name>: Unknown error

Instead, if I access directly to this resource by PCManFM, I get this error:

mount: only root can mount //<Server_name>/<Share_directory> on /media/<Point_mount>

This network resource can I use it normally if I access it via the menu Go ---> Network of PCManFM.

How come?

Thanks

Bye
You are missunderstanding the forcegid parameter for fstab.  In any event I was not referring to this entry in the fstab anyway. 

Directly answering your question.  It seems that the mount routine can't resolve the Server Name you have supplied in the fstab.  The second probem is most likely to also involve the fstab cofiguration.  Under normal circumstances only the user *root* has the right to mount a partition.  You can configure non-root users to have this ability using the fstab file.

I think I would start over with the original fstab file settings.  Did you make a backup /etc/fstab file before started modifying it?

If I was attempting this I would revert to settings mount the partition successfully and then later add UID and GID  and mode settings.  Check eac step along the way.  It is important that you read and understand the man pages for both fstab and smbconf rather than just guessing what to do.

You **do not need** *forcegroup* in the fstab file.  You **do need  ***force group* in the smb.conf file.  These are 2 completely different things that just happen simalar names.  The term *_forcegroup_* is not the same as *_force group _*.

Post the output of these commands when you have reverted back to the original settings```

# for the client mounting the share
cat /etc/fstab

# The server hosting Samba
cat /etc/samba/smb.conf

```

---

### Post by balubeto on 2015-01-09
> **bab1 said:**
> You are missunderstanding the forcegid parameter for fstab.  In any event I was not referring to this entry in the fstab anyway. 

Directly answering your question.  It seems that the mount routine can't resolve the Server Name you have supplied in the fstab.  The second probem is most likely to also involve the fstab cofiguration.  Under normal circumstances only the user *root* has the right to mount a partition.  You can configure non-root users to have this ability using the fstab file.

I think I would start over with the original fstab file settings.  Did you ake a backup /etc/fstab file before started modifying it?

If I was attempting this I would revert to settings mount the partition successfully and then latter add UID and GID  and mode settings.  Check eac step along the way.  It is important that you read and understand the man pages for both fstab and smbconf rather than just guessing what to do.

You **do not need** *forcegroup* in the fstab file.  You **do need  ***force group* in the smb.conf file.  These are 2 completely different things that just happen simalar names.  The term *_forcegroup_* is not the same as *_force group _*.

Post the output of these commands when you have reverted back to the original settings```

# for the client mounting the share
cat /etc/fstab

# The server hosting Samba
cat /etc/samba/smb.conf

```

The original files of /etc/fstab and /etc/samba/smb.conf are:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=d07497b2-0392-412f-a0b4-574a39bfda83 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=10a97ab0-809e-41eb-ba3a-bc81388f9bd4 /boot           ext4    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=898259f2-4530-4d23-862f-f0560ed67e39 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=5ee76451-f283-4767-8706-399885e5c653 none            swap    sw              0       0

```

and

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
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#======================= Global Settings =======================
[global]
## Browsing/Identification ###
# Change this to the workgroup/NT-domain name your Samba server will part of
 workgroup = ufficio
# server string is the equivalent of the NT Description field
 server string = %h server (Samba, Ubuntu)
# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no
# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z
# This will prevent nmbd to search for NetBIOS names through DNS.
 dns proxy = no
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
;   bind interfaces only = yes
 
#### Debugging/Accounting ####
# This tells Samba to use a separate log file for each machine
# that connects
 log file = /var/log/samba/log.%m
# Cap the size of the individual log files (in KiB).
 max log size = 1000
# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no
# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
 syslog = 0
# Do something sensible when Samba crashes: mail the admin a backtrace
 panic action = /usr/share/samba/panic-action %d

####### Authentication #######
# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
 server role = standalone server
# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
; passdb backend = tdbsam
 obey pam restrictions = yes
# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
 unix password sync = yes
# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<[EMAIL="kahan@informatik.tu-muenchen.de"]kahan@informatik.tu-muenchen.de[/EMAIL]> for
# sending the correct chat script for the passwd program in Debian Sarge).
 passwd program = /usr/bin/passwd %u
 passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
 pam password change = yes
# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
 map to guest = bad user
########## Domains ###########
#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#
# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = [\\%N\profiles\%U]("file://\\%N\profiles\%U")
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = [\\%N\%U\profile]("file://\\%N\%U\profile")
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = [\\%N\%U]("file://\\%N\%U")
# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd
# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g
############ Misc ############
# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m
# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
# Setup usershare options to enable non-root users to share folders
# with the net usershare command.
# Maximum number of usershare. 0 (default) means that usershare is disabled.
; usershare max shares = 100
# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
 usershare allow guests = yes
 username map = /etc/samba/smbusers
 security = user
; encrypt passwords = yes
; guest ok = no
; guest account = nobody
#======================= Share Definitions =======================
# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as [\\server\username]("file://\\server\username")
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
# By default, [\\server\username]("file://\\server\username") shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to [\\server\username]("file://\\server\username")
# This might need tweaking when using external authentication schemes
;   valid users = %S
# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
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
; guest ok = no
; read only = yes
 create mask = 0700
# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
 comment = Printer Drivers
 path = /var/lib/samba/printers
; browseable = yes
; read only = yes
; guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin
[Documenti_pubblici]
 path = /home/account_comune/Documenti
 writeable = yes
; browseable = yes
 valid users = account_comune

```

So, what I should add these files to achieve my goal?

Thanks

Bye

---

### Post by SeijiSensei on 2015-01-09
> **bab1 said:**
> A safer way for a newbie is to use this```
getent group <group_name>
```

Off topic, but what in the world is wrong with grepping the /etc/group file?  It's not like that changes the content of the file at all.  Are you suggesting new users shouldn't be informed about things like /etc/passwd and /etc/group?  The very openness of *nix authentication was one of the most striking aspect of the OS when I came to Linux from Netware.

---

### Post by bab1 on 2015-01-09
> If I was attempting this I would revert to settings mount the partition successfully and then latter add UID and GID and mode settings. Check each step along the way. 

Did you try the above?

---

### Post by balubeto on 2015-01-10
I noticed that if in /etc/fstab I substitute the name of the server with its IP address, I can fully access to this network resource. How come? How should I do to make sure that DNS service is working correctly also during the startup of Linux?

Thanks

Bye

---

### Post by bab1 on 2015-01-10
> **balubeto said:**
> I noticed that if in /etc/fstab I substitute the name of the server with its IP address, I can fully access to this network resource. How come? How should I do to make sure that DNS service is working correctly also during the startup of Linux?

Thanks 
Bye
I would add this to the [global] section of the smb.conf file```
netbios name = <SERVER_NAME>
```...  Most people use the hostname as the <SERVER_NAME>.

Then you need to add this line to the same [global] section ```
name resolve order = bcast 
```

Now you need to restart samba with this command```

suod service smbd restart

```
You shuld be able to see the server and its shares with this command```
smbtree
```...and you should be able to browse to the server share by name.

---

