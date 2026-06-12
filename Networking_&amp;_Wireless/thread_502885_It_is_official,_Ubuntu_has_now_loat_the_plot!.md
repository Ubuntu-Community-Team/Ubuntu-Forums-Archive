---
title: "It is official, Ubuntu has now loat the plot!"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by carriecomputers on 2007-07-17
I've had networking issues recently but have been too busy to really worry about it, but now they seem to be getting worse!

Every machine on the network is either new or recently re-installed. The two machines I'm looking at right now are both running Ubuntu feisty. A samba share is set up and they can see each other, I can see the fules but only half of them load, the xls file I want to load appears with the correct icon but when I click on it I get this:

> The filename "debts.xls" indicates that this file is of type "Excel spreadsheet". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

and the icon changes to a text one. All JPEGS load correctly, HTML files seem to be ok but documents are stuffed. I tried copying them to the local drive which worked last night but now:

> Error "Invalid parameters" while copying "smb://garet...l/debts.xls".

and when I tried to copy the files back after editing it just tells me that I don't have write privileges on that drive, which I do.

Any suggestions?

---

### Post by dmizer on 2007-07-17
is the windows computer you're attempting to access the excel files from, running in vmware?

if so, see this thread: [http://www.vmware.com/community/message.jspa?messageID=671438](http://www.vmware.com/community/message.jspa?messageID=671438)

if not, please post your /etc/samba/smb.conf file on the samba server.

---

### Post by carriecomputers on 2007-07-19
I am not using a windows machine, this is Ubuntu feisty to feisty. my smb.conf is as follows

> # Un-comment the following and create the profiles directory to store
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



[gareth]
path = /home/gareth
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by dmizer on 2007-07-24
for feisty to fiesty, use nfs instead of samba.  it's a file transfer protocol intended for linux instead of a transfer protocol developed for windows.  it's quick and painless to set up nfs.  just check the 4th link in my sig.

if you're set on using samba for some reason, set up your server using the first link in my sig, and set up your client with the second link in my sig.

---

