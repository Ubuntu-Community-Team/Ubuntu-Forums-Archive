---
title: "Samba - Mask to allow everyone read write access"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by powel212 on 2009-04-13
Hi

I've been trying to correct an problem I've been having with file sharing. I have an Ubuntu share folder on server in my office. I have tried to give it read write permissions to everyone so anyone in the office can access and modify community based files but sometimes the files end up read only if viewed from other Ubuntu computers within the network. Even though I have added those other users to smbpassd and the folder is set to "Share-with everyone" 

Any help is appreciated.

Powel

```


#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = workgroup

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)


#   wins support = no


;   wins server = w.x.y.z


	dns proxy = no


;   name resolve order = lmhosts host wins bcast

#### Networking ####


;   interfaces = 127.0.0.0/8 eth0


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

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
	passdb backend = tdbsam

	obey pam restrictions = yes

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

# This option controls how unsuccessful authentication attempts are mapped 
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
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

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

  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########


#   load printers = yes


;   printing = bsd
;   printcap name = /etc/printcap


;	printing = cups
;   printcap name = cups

############ Misc ############


;   include = /home/samba/etc/smb.conf.%m




;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

#   domain master = auto


;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


;   winbind enum groups = yes
;   winbind enum users = yes


;	usershare max shares = 100


	usershare allow guests = yes
	security = share
	guest ok = yes
	guest account = drock

#======================= Share Definitions =======================


;[homes]
;   comment = Home Directories
;   browseable = no


;   read only = yes


;   create mask = 0700


;   directory mask = 0700


;   valid users = %S


;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no


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


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no

;   write list = root, @lpadmin


;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes


;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[Public]
	path = /home/share/Public
	writeable = yes
;	browseable = yes
	guest ok = yes
```

---

### Post by HalPomeranz on 2009-04-13
This should work:

```

[Public]
	path = /home/share/Public
	writeable = yes
;	browseable = yes
	guest ok = yes
       create mask = 777
       directory mask = 777

```

The above settings will make sure that when new files and directories are created the permissions are set wide-open.  However, this also means that users are free to trample on each other's files at will, so there are some significant security risks to this setting.

---

### Post by powel212 on 2009-04-14
Thank you. I'll give it a try.

I have a pretty good backup system to protect us from ourselves. The trouble is there are many different users accessing the same files and they are all using different operating systems in different locations around the building. And, none of the operators are tech savy so i have to make it really easy for them or they get frustrated very quickly.

Thanks again

Powel

---

### Post by powel212 on 2009-04-14
I am afraid that did not work. Is it possible there is something other than the smb.conf that is influencing the share? For example I have /home/bob/share shared within smb.conf but the folder icon does not have show the share icon so I can still right click the folder and share it out that way. And when I do so with any folder on the computer it does not afterward show up in smb.conf as I assume it should.

Thanks

Powel

---

### Post by HalPomeranz on 2009-04-14
Hmmm.  You know I'm actually not sure what happens when you share a directory via the right-click mechanism. I normally just add new shares directly to my smb.conf file by hand with a text editor.  

You could do the same, using the example in my original response as a template.  Each new share would have to have a different name in "[...]" at the start of the entry, and obviously would have a different value for "path = ...", but the rest of the settings should be the same for each new share.  You'll need to reload or HUP the samba daemons after each smb.conf update.

---

### Post by NullHead on 2009-04-14
What HalPomeranz suggested should work. 

Try un-sharing all the directories you shared via the right click menu, and share them manually through the smb.conf file. 

As HalPomeranz also said, do that with the bit of code he gave earlier. 

```
[Your Share name goes here]
	path = /your/folder/goes/here
	writeable = yes
;	browseable = yes
	guest ok = yes
       create mask = 777
       directory mask = 777
```

I run a similar setup as you do and I manually setup all the shares through the smb.conf file. I don't have any problems. 

This is how somebody would make a share through SSH.

---

### Post by Iowan on 2009-04-14
There is another file that (sometimes) gets used for Samba configuration - check */var/lib/samba/usershares*.

---

### Post by powel212 on 2009-04-15
Thanks for the help. I've done as has been mentioned above and it is working quite well. Just one lingering problem. 

If I access files in the share folder from another Ubuntu machine on the network I have read and write access but I can still not modify files created by other users. I can delete them but when I open them in Oo-Writer, make a modification, and then try to save, it tells me I have insufficient rights to do so. This problem does not occur if I access the share from Windows or Mac.

Any ideas?

P.

---

### Post by aytacd on 2009-09-13
Hi,

I've been trying to give read/write access to all users for a certain folder via terminal. Is there a function or a script that I can use?

Thank you for your help...

---

