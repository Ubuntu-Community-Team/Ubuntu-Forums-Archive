---
title: "Network desktop and laptop, both ubuntu"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by xboxbman on 2007-02-16
I've got Edgy Eft running on both my desktop and my laptop.  Thanks to the ridiculously high speed connections I can find at the university, my laptop's tiny 160 gig HDD fills up pretty fast.  I want to connect my laptop to my desktop to ftp the files over.  Right now, I'm using my PSP with a 2 gig mem stick in it as a usb stick.  When I've got 30-40 gigs of files to move over, it takes a while, and attention.  I have a wireless router, which i have no problem plugging into with a network cable if that makes it easier.  My desktop also has two network cards, so if it's simpler to plug directly into the pc with crossover cable, i can do that too.  All i know is that i need to use NFS, but really i have no idea how to set it up while keeping my desktop secure.  Help me ubunto forums, you're my only hope.

---

### Post by pebo on 2007-02-16
NFS: [https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")
You can also use Samba: [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
or SSH: [https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")
edit: or you could use ftp - gftp is very good and easy to use

---

### Post by xboxbman on 2007-02-16
> **pebo said:**
> NFS: [https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")
You can also use Samba: [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
or SSH: [https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")
edit: or you could use ftp - gftp is very good and easy to use

i tried using gftp.  I use it all the time between both my computers and my xbox, but my computers don't seem to want to talk to each other.i'll try NFS, see how that goes.  I'm school now, i'll post back my results after i set it up tonite.  Thanks for the help

---

### Post by chili555 on 2007-02-16
Are you connecting these computers through a network, or with an ethernet cable, a crossover cable, I hope?

---

