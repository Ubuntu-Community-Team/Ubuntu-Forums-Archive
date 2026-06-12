---
title: "Accessing samba share from windows"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by Naddiseo on 2006-10-09
I had this working the other day then I dist-upgraded to edgy and can't remember how I got my partition shared.

Anyway, I have two HDDs on my machine and would like to share a 100GB partition on my first HDD (/dev/hdc2) under /media/100GBBackup and allow my dad's WinXP to have read/write access without that annoying password prompt.

I've searched around this forum the last 3 hours trying every thread the searches came up with and I still have trouble accessing it. I think my problem lays in the permissions of fstab because I can see the drive on the network but don't have permission to read it.

Here's my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1 -- converted during upgrade to edgy
UUID=6000851c-92e3-41db-b398-4aa73e257912 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdc1 -- converted during upgrade to edgy
UUID=de6edff7-a133-45e9-aa06-161f4c2ca728 /hdd ext3 defaults 0 2
# /dev/hdd2 -- converted during upgrade to edgy
UUID=e02e1400-9b25-4bc3-83e2-f0ff4cd9fb2b none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/hdc2 /media/100GBBackup ntfs   defaults,auto,user,dmask=777,fmask=777   0       0

```
The permissions of /media once I've run mount -a
```
richard@richard-desktop:/media$ ls -la
total 16
drwxr-xr-x  4 root root 4096 2006-10-08 18:20 .
drwxr-xr-x 22 root root 4096 2006-10-09 11:36 ..
d---------  1 root root 4096 2006-09-30 13:17 100GBBackup
lrwxrwxrwx  1 root root    6 2006-10-05 15:48 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2006-10-05 15:48 cdrom0

```

My samba config
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

   workgroup = MSHOME
   server string = %h server
   dns proxy = no
   null passwords = true
   guest ok = yes
   security = SHARE
   preferred master = No
   local master = No
   domain master = No

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

   
   ;encrypt passwords = true 
   ;passdb backend = tdbsam
   ;obey pam restrictions = yes
   guest account = yes
   invalid users = root

   ;passwd program = /usr/bin/passwd %u
   ;passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

   ;wins support = no

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /tmp
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

[100GBBackup]
path = /media/100GBBackup
available = yes
browsable = yes
public = yes
writable = yes
create mask = 0644
directory mask = 0775 
```

I'm obviously missing something...

---

### Post by wirelessmonkey on 2006-10-09
Have you created the guest user on your Ubuntu box?  I'm not absolutely sure but you may have to create an empty password too....  smbpasswd <enter>


Let us know what you find out.

---

### Post by Naddiseo on 2006-10-09
Do I need a guest user? Because I don't want my dad to have to put in a password each time he tries to access the network drive.

Anyway, I tried that:

```
richard@richard-desktop:~$ smbpasswd
Old SMB password:
New SMB password:
Retype new SMB password:
Error connecting to 127.0.0.1 (Connection refused)
unable to connect to SMB server on machine 127.0.0.1. Error was : SUCCESS - 0.
Failed to change password for richard
```
Passwords were blank each time.

I also ran sudo /etc/init.d/samba restart but that didn't help too much.

Thanks for your reply.

---

