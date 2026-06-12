---
title: "Samba Write Permissions ??"
date: 2005-07-07
forum: Networking &amp; Wireless
---

### Post by Digitallysick on 2005-07-07
I can see my linux box from my powermac laptop, and vise versa, but when i try to drop files from my mac over to linux i get an error " you do not have suffecient privledges " here is my smb.conf (i am sure it is screwed up somehow)

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
log file = /var/log/samba/log.%m
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n
obey pam restrictions = yes
null passwords = yes
encrypt passwords = true
guest ok = yes
passdb backend = tdbsam guest
passwd program = /usr/bin/passwd %u
dns proxy = no
server string = Adams Computer
printing = cups
invalid users = root
workgroup = Mshome
printcap name = cups
syslog = 0
panic action = /usr/share/samba/panic-action %d
max log size = 1000
security = share


# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
; comment = Network Logon Service
; path = /home/samba/netlogon
; guest ok = yes
; writable = no
; share modes = no

[printers]
comment = All Printers
path = /var/spool/samba
read only = no
printable = Yes
use client driver = yes
disable spoolss = yes
browseable = no
print command = lpr -r -P %p %s -U %u -o raw
lprm command = /usr/bin/lprm -P %p %j




# Windows clients look for this share name as a source of downloadable
# printer drivers
;[print$]
; comment = Printer Drivers
; path = /var/lib/samba/printers
; browseable = yes
; read only = yes
; guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
; write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
; comment = Samba server's CD-ROM
; writable = no
; locking = no
; path = /cdrom
; public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
# cdrom share is accesed. For this to work /etc/fstab must contain
# an entry like this:
#
# /dev/scd0 /cdrom iso9660 defaults,noauto,ro,user 0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
# is mounted on /cdrom
#
; preexec = /bin/mount /cdrom
; postexec = /bin/umount /cdrom


[Adam]
comment = Adams Home
path = /home/adam/
read only = no
writable = yes
inherit permissions = yes
case sensitive = no
msdfs proxy = no
delete readonly = yes

---

### Post by Digitallysick on 2005-07-07
i finally got it fixed, thanks again, i went back to the "home" folder and went into the properties, there was a file in it that prevented me from making the changes , i finally went in as root and deleted the file and then corrected the permissions, thanks!

---

