---
title: "Feisty not playing fair with a Windows share....."
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by Netfreak on 2007-07-02
OK, I'm new to Linux & Ubuntu, so go easy ;)

Installed Ubuntu Server, then, as it's on a home network, installed Kubuntu gui :p

Next, I went to install SwissCenter & ran across a problem with Windows shares. All of the media I want to share through SwissCenter is stored on network drives, for the most part on a Synology DS106e NAS drive.

The following is my /etc/fstab contents

 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=015c5176-8069-40ec-9d54-f1e63ef97bcf /               ext3    defaults,erro$
# /dev/hdb5
UUID=020d915a-d0e1-467a-8476-f44824b9efc1 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//192.168.1.99/video    /media/video/ cifs ro  0       0
//192.168.1.99/music    /media/music/ cifs ro  0       0
//192.168.1.99/photo    /media/photos/ cifs ro  0       0
//192.168.1.99/usbshare1    /media/TVOld/ cifs ro  0       0
//192.168.1.9/TVNew    /media/TVNew/ cifs ro  0       0

All of the shares of 192.168.1.99 (the Synology) "mount ?" and allow the SwissCenter to add the media.

However, the share on 192.169.1.9 appears to mount - the icon appears on the desktop as per the other shares - BUT - no files appear in the mounted drive :( If I manually run       

sudo mount -t cifs //192.168.1.9/TVNew /media/TVNew/ -ro -o

Files show up & SwissCenter can add the media  :o

The share is on a Windows XP machine, ntfs, full read/write with no password protection etc. If I use the network browser I can browse to the share, see, load, copy play files without any problems &, without the need to run the sudo mount command :o. All the created  mount folders in /media have the same full access to everyone rights.

Any ideas or help gratefully received as I'd like to be able to re-boot the server without having to manually run the sudo mount command.

TIA

---

### Post by PeterDB on 2007-10-10
Hei,

Okay, this might be a late answer, but here goes anyhow.

It should be as simple as adding guest to the line, this is how I solved my issues.

so //192.168.1.9/TVNew /media/TVNew/ cifs ro 0 0 would be //192.168.1.9/TVNew /media/TVNew/ cifs guest,ro 0 0 instead..

try and let me know.

---

