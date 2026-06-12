---
title: "Viewing Ubuntu Files From Within Windows"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by goodvikings on 2009-08-03
Hey everybody!
 
I currently have my laptop dual booted with Ubuntu 9.04 and WinXP, and although I can view files from windows while in Ubuntu, I can't do the reverse, ie, when I'm in XP, i can't see any of my files from Ubuntu. The Ubuntu file system just shows up as one 17gig block on my HDD.
 
Are there any apps or the like that will allow me to see these files?
 
Cheers
 
\m/

---

### Post by desperado665 on 2009-08-03
I believe that depends on whether you formatted with ext3 or ext4. The short answer is no. There are downloadable utilities to view ext3 partitions out there, but I cannot vouch for their  reliability.

You might start here: [http://freedownloads.rbytes.net/search/ext3-viewer/](http://freedownloads.rbytes.net/search/ext3-viewer/)

---

### Post by goodvikings on 2009-08-03
ok cool - how do I find that out?

---

### Post by goodvikings on 2009-08-03
cancel that - it's ext3

---

### Post by credobyte on 2009-08-03
[http://e2fsprogs.sourceforge.net/](http://e2fsprogs.sourceforge.net/) ;)

---

### Post by pebo on 2009-08-03
The [ext2ifs]("http://www.fs-driver.org/") driver for windows works perfectly for my ext3 partitions.

---

### Post by Paddy Landau on 2009-08-03
You can also try [Ext2fsd]("https://sourceforge.net/projects/ext2fsd/"), which handles a wider range of implementations than Ext2ifs, and explicitly handles ext3 journalling, which Ext2ifs doesn't.

Bear in mind that they both don't handle ext4.

---

### Post by goodvikings on 2009-08-03
Hey thanks for the ideas guys - however these aren't really options that are helping. I think it's to do with the fact that I'm not running a seperate partition that is ext3 for the ubuntu install, rather on my windows C: there is a ubuntu installation, similar to a normal program.
 
The "filesystem file" is "C:\ubuntu\disks\root.disk". The only reason I know that this is the file is because of the size of it (17gig.)

---

### Post by Paddy Landau on 2009-08-03
> **goodvikings said:**
> The "filesystem file" is "C:\ubuntu\disks\root.disk". The only reason I know that this is the file is because of the size of it (17gig.)
Ah, you've installed using Wubi. That's an entirely different matter.

AFAIK, you can't see your Ubuntu files from Windows in this case. Sorry.

You'd be advised to create a separate partition and dual-boot; that way you will be able to.

---

### Post by Mark Phelps on 2009-08-03
The link below is to the Wubi Guide where it shows you how to migrate your Wubi installation to its own partition so you don't lose what you've already installed:

[https://wiki.ubuntu.com/WubiGuide%C2%A0#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?]("https://wiki.ubuntu.com/WubiGuide%C2%A0#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?")

---

### Post by goodvikings on 2009-08-05
cheers for that!

\m/

---

