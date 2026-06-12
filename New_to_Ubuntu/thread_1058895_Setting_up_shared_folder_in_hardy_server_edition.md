---
title: "Setting up shared folder in hardy server edition"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by zulasmum on 2009-02-03
Hi
I am a linux newbie and am trying to set up a pc as a home server for music, pictures etc. I have installed hardy server edition and can access it headless via ssh and putty.
My problem is trying to set up a shared folder called data that is at /home/data that a group of users can access from our home network using samba.
I have created a group of users on the hardy server and I think I have created samba users and added them to the smbusers file. Am i right in assuming the samba usernames have to be the same as the windows usernames?
Currently I have altered the smb.conf file to be able to see the server from the windows network but I don't think that I have shared the folder as all see is the server name and not the shared folder.
Not sure if I am making myself clear.
What should my next steps be?
Thanks

---

### Post by lykwydchykyn on 2009-02-03
> **zulasmum said:**
> Hi
I am a linux newbie and am trying to set up a pc as a home server for music, pictures etc. I have installed hardy server edition and can access it headless via ssh and putty.
My problem is trying to set up a shared folder called data that is at /home/data that a group of users can access from our home network using samba.
I have created a group of users on the hardy server and I think I have created samba users and added them to the smbusers file. Am i right in assuming the samba usernames have to be the same as the windows usernames?

You don't have to, but it makes things a bit smoother.
> 
Currently I have altered the smb.conf file to be able to see the server from the windows network but I don't think that I have shared the folder as all see is the server name and not the shared folder.
Not sure if I am making myself clear.
What should my next steps be?
Thanks
Can you post the smb.conf file here?  It might help to see what you've done there.

Also, post the output of:
```

ls -l /home/data

```

---

### Post by Coreigh on 2009-02-03
I have always struggled creating non-public shared folders with Samba for a Windows network, it never goes smoothly for me. So when I am on a secure network (where all users are allowed access to the share and I am behind a firewall) I create a public share. If you are allowed on the network you are allowed access to the folder. 

Here is a link.
[http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_183.html](http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_183.html)

---

### Post by HermanAB on 2009-02-03
Here is a debug guide:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by zulasmum on 2009-02-03
Thanks for the reply
I can now see the share on the network but cannot access it.

The smb.conf file is as follows:


#======================= Global Settings =======================

[global]

workgroup = Home

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


###### Authentication #######

security = user  username map = /etc/samba/smbusers

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



#======================= Share Definitions =======================


[data]
comment = shared data
browseable = yes
path = /home/data
writeable = yes

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


The output from ls -l /home/data is:

total 16
drwxr-xr-x 2 root root 4096 2009-02-03 15:39 documents
-rw-r--r-- 1 root root    0 2009-02-03 13:33 example.txt
drwxr-xr-x 2 root root 4096 2009-02-03 15:39 music
drwxr-xr-x 2 root root 4096 2009-02-03 15:39 photos
drwxr-xr-x 2 root root 4096 2009-02-03 15:39 videos

---

### Post by lykwydchykyn on 2009-02-03
Try:
```

chmod -R 777 /home/data

```
That will give read/write/execute permissions on the whole folder to all users on the system.

Also, change this line:
```

security = user username map = /etc/samba/smbusers

```
To this:
```

security = user 
username map = /etc/samba/smbusers

```

(in other words, make a new line after "security = user")

Then restart samba.

---

### Post by zulasmum on 2009-02-03
That has worked a treat. I can now access the folder and all users can write to it etc.
Thanks very much lykwydchykyn

---

