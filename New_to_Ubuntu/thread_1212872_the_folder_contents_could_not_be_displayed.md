---
title: "the folder contents could not be displayed"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by mosaabJ on 2009-07-14
**[SIZE="3"]Hello, I recently faced a problem with both my operating systems (Windows and Ubuntu) and I decided to format the Hard Disk and before doing that I wanted to back up my data and especially my book marks which contains useful sites. I cannot access any of my operating systems so I am currently using the Live CD to do that but the problem that I am facing right now is that I cannot access the Mozilla fire fox folder on my Ubuntu distro to get my bookmarks and is shown in the following screen shot.[/SIZE]**
[[IMG]http://img20.imageshack.us/img20/4421/screenshot1lwo.png[/IMG]](http://img20.imageshack.us/i/screenshot1lwo.png/)

---

### Post by wojox on 2009-07-14
You have to open a terminal:

```
gksudo nautilus
```

Or open firefox and export the bookmarks to your home folder.

---

### Post by mosaabJ on 2009-07-14
> **wojox said:**
> You have to open a terminal:

```
gksudo nautilus
```

Or open firefox and export the bookmarks to your home folder.

What exactly does the command do because I didn't experience any changes and please consider that I am currently booting from the Live CD and can't use the Ubuntu which is installed on my PC

---

### Post by rio2000 on 2010-10-10
i have same problem, using ubuntu 10.04 live cd i get "The folder contents could not be displayed" using "gksu nautilus" stil can't open my folder (only get 2 file)

they are:
1. Access-Your-Private-Data.Desktop 

(when i'm click, get this messages: 
Untrusted application launcher 
The application launcher "Access-Your-Private-Data.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe.)

2. Read Me.txt

(THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private)

can someone help me? i need the my document data :D

---

### Post by jnorthr on 2010-10-10
since you are running from the live cd, your original hard disk with bookmarks and documents may not be visible to ubuntu unless you mount your existing hard drive.

---

