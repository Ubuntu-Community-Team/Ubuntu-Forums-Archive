---
title: "Disc catalog"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by A_M_S on 2009-08-14
Hi.

I'm trying to organize my CD/DVD colection (Data, Pictures, Music).

What are the best applications to do this task?


Tnx

---

### Post by LowSky on 2009-08-14
what do you mean by organize?
Are you uploading the media to a hard drive, or you looking to create a filing system, or a book loan type application to track objects use?

---

### Post by Col-1023 on 2009-10-03
I use Gwhere to catalog my external hard drives.

It's good for searching files, but I'm interested to know if there is something better.

Gwhere is in the repositories.

Hope this helps.

---

### Post by Francewhoa on 2010-06-07
I tried many. My favorite is Hyper's CdCatalog (aka Cdcat). Stable with lots of features.

Official site [http://cdcat.sourceforge.net](http://cdcat.sourceforge.net)

Installer or aptitude link for Ubuntu 8.04 LTS desktop 32bit [http://packages.ubuntu.com/hardy/i386/cdcat/download](http://packages.ubuntu.com/hardy/i386/cdcat/download)

Other Ubuntu versions at [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by deadcabbit on 2010-08-14
I had been using CdCat for quite a time (and Whereisit in wine before that), knowing that it stores the file lists in XML files, so I can easily convert it in case I decide to use something else: wrong.

Unfortunately CdCat's XML format is pretty messed up so I ended up using [JDvdKat]("http://code.google.com/p/jdvdkat/"): very barebones and simple but it works for me and it is **much** more stable than Hyper's CdCat.

It's a java jar file, so it may not be as beautiful as a Qt app and its crawler part is command line only, but be sure to read the [wiki ]("http://code.google.com/p/jdvdkat/w/list")on google code :)

---

### Post by expatCM on 2010-08-15
You may find Griffith interesting.  
[http://www.griffith.cc/](http://www.griffith.cc/)

---

### Post by omelette on 2013-01-23
Linux software often makes me wanna scream.  I've just installed two of the applications recommended here, 'GWhere' & 'Hyper's CD Catalog'.  GWhere unfathomably has no obvious way of refreshing what's in the drive, meaning that you must close & open the program to read each new CD - that an unbelievable omission.  Whereas while CdCat provides a 'rescan drive' button specifically for that, for some reason it is diabolically slow at scanning disks - Gwhere will usually scan a disk in less than 5secs, whereas CdCat easily takes over 60secs to do the same disk. Another annoying quirk about CdCat is that you cannot sort your scanned disks alphabetically - ie. if your physical disks are named "Disk 1" to "Disk 25" and if using this naming scheme with CdCat, the disks are scanned out-of-order, they are displayed permanently in this out-of-order scheme in the database.  Ok, it not a major problem but it sure looks sloppy when lots of disks are involved, and it should have been relatively simple to have made them sortable.

Edit:  I've just realised that Gwhere also suffers from the database-sorting problem as well.  Sad...

---

### Post by deadcabbit on 2013-01-25
CdCat uses a lossy (!!) xml structure, I absolutely don't recommend using it (check the file sizes in the gzipped xml) - I haven't used gWhere for ages, that may be better.

While I'm the developer of jDvdKat, I must admit, jDvdKat is not user friendly at all either (I just wrote the software to myself and nowdays I don't have the energy to add bells and whistles) - I'm not sure if a proper alternative to WhereIsIt exists on Linux.

---

### Post by Merrattic on 2013-01-25
Used Gwhere which was fine, but have now moved over to CDCat which does the job just fine.

---

