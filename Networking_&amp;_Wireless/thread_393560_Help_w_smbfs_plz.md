---
title: "Help w/ smbfs plz"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by notwen on 2007-03-25
I have a 4 computer network here at home.  1 Windows PC, 1 Linux PC, and 2 Macs.  I have the majority of my media(mp3s/videos) on my windows pc.  I'm wanting to use smbfs to mount my shared folders from my windows pc on my linux and mac boxes.  I've been using the guide [here]("https://help.ubuntu.com/community/MountWindowsSharesPermanently#head-35cfd84dee9a392fa28c8795f37b6660a8786c35"), but am having little luck mounting the drives.  Any help or other how-tos out there for getting my shared folder mounted on my linux box?  The macs I'll hafta figure out elsewhere =]

---

### Post by notwen on 2007-03-26
-bump-

---

### Post by love2learn on 2008-04-05
i would like to bump this too. I have 1 linux client and a media server. I am also following the same guide but cant get it to mount in ubuntu. I can give all sorts of information such as.

**this is the error message i am getting:**

[I]lucana@laptop:~$ sudo mount -a
Could not resolve mount point /home/lucana/desktop/mount
lucana@laptop:~$ [/I]

**this is my fstab config:**
[I]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=eafe81a0-359c-4f9e-8289-a2bdc8d1b196 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ff38c1b7-89b0-4066-84d4-687e910a18e7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
//media/e: /home/lucana/desktop/mount smbfs /home/lucana/.smbcredentials,uid=1000 0 0[/I]

**this is my etc/nsswitch.conf:**

[I]# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns wins mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis[/I]

**this is my .smbcreditials file:**

[I]lucana=lucana
password=password

# OR:
# username=MyUsername@MyDomain
# password=MyPassword[/I]


I have been working on this for about a week. I also tried samba following another guide and figured this would be better. This is a deal breaker for me though, if i cant get these shares working for my media server I will have to go back to windows and I really want to be able to enjoy linux and learn. I am three weeks in with no windows ( besides configuring a user account for samba on my xp file server ) 

thanks in advance

---

### Post by Eiríkr on 2008-04-05
**@love2learn -- **

A number of things:
***** There should be no colons in any share paths.  So instead of **//media/e:** you should only have **//media/e**.  
***** The _smbfs_ filesystem type has been deprecated for some time, and appears to finally be broken as of Samba version 3.024 or 3.026 (possibly even earlier).  Version 3.026 is currently the default package for Ubuntu Gutsy 7.10.  You'll have to use the _cifs_ filesystem type instead.  

----------

**@notwen -- **

Macs can also make use of Samba sharing.  I've got Tiger on my iBook, and I see my Samba shares by clicking the Network icon in Finder.  Also, check the parameters I mention above for love2learn.

----------

HTH,

Eiríkr

---

### Post by dmizer on 2008-04-06
i wrote a howto for mounting with cifs.  it is linked in my sig.

---

