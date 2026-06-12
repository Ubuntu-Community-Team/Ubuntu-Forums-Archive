---
title: "extract data from .iso to a folder"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by redshift88 on 2009-08-02
My ultimate goal is to mount my Sims3.iso and install it to see how playonlinux works.  However, this .iso will not mount due to an incorrect filesystem.

I am trying to extract data from the .iso file into a folder.  This .iso works fine on windows computers using virtual clone drive.  I stumbled across this when searching....

 [http://ubuntuforums.org/showthread.php?t=180668](http://ubuntuforums.org/showthread.php?t=180668)

I used the 'file' command to see what kind of file system my .iso is, and it says 'data'. So, I used the command presented on this website to a directory instead of a usb drive. The process completes, but there is nothing inside my destination folder. My target directory is /home/andrew/Desktop/Rename


andrew@awesome-hp:~/Desktop$ sudo dd if=Sims3.iso of=/Rename
11658112+0 records in
11658112+0 records out
5968953344 bytes (6.0 GB) copied, 380.84 s, 15.7 MB/s
andrew@awesome-hp:~/Desktop$                                                                                                                   

(nothing inside 'Rename')

Here's a link to an older thread that I have been posting in with no response.  It just shows a few of the different fs commands I tried.

Any ideas?

(acetone won't install on my 64bit version of ubuntu)

---

### Post by jacklinux on 2009-08-02
i don't think Sims3 runs under linux, Sims 2 ran very poorly on it.

---

### Post by Dark Aspect on 2009-08-02
> **jacklinux said:**
> i don't think Sims3 runs under linux, Sims 2 ran very poorly on it.

[Don't underestimate wine]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664")

---

### Post by HotShotDJ on 2009-08-02
You might give gmount-iso a try (Applications ..> Add/Remove).

---

### Post by redshift88 on 2009-08-02
> **HotShotDJ said:**
> You might give gmount-iso a try (Applications ..> Add/Remove).

Gmount-iso, the scripts, and manually mounting doesn't work because it's not really an iso.  They all just throw up filesystem errors.

---

### Post by jacklinux on 2009-08-02
> **Dark Aspect said:**
> [Don't underestimate wine]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664")
Haha, i guess not. Lets hope EA belive in Opensource ;)

---

### Post by jerome1232 on 2009-08-02
Well on my system I can just right click an iso and chose extract here.

Does that not work?

---

### Post by Revolutionary101 on 2009-08-02
You should be able to double click the .iso and it will open up in archive manager. Then you can extract your files from there.

---

### Post by redshift88 on 2009-08-02
> **jerome1232 said:**
> Well on my system I can just right click an iso and chose extract here.

Does that not work?

This is the error that it displays when choosing extract here.

[B]7-Zip  4.58 beta  Copyright (c) 1999-2008 Igor Pavlov  2008-05-05
p7zip Version 4.58 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Error: /home/andrew/Desktop/Sims3.iso is not supported archive

Errors: 1
[/B] 
With Gmount-iso

[B]An error occured
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]

dmesg:

**[ 3768.143596] ISOFS: Unable to identify CD-ROM format.**

sudo mount -o loop -t iso9660 ~/Desktop/sims3/Sims3.iso ~/Desktop/mount

[B]mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]


I've even reinstalled ubuntu.

edit:  After day three of this, I'm going to go work on my much simpler car.

---

### Post by niteshifter on 2009-08-02
> **redshift88 said:**
> .... The process completes, but there is nothing inside my destination folder. My target directory is /home/andrew/Desktop/Rename


andrew@awesome-hp:~/Desktop$ sudo dd if=Sims3.iso of=/Rename
11658112+0 records in
11658112+0 records out
5968953344 bytes (6.0 GB) copied, 380.84 s, 15.7 MB/s
andrew@awesome-hp:~/Desktop$                                                                                                                   

(nothing inside 'Rename')

Er, no. Your dd target directory was not /home/andrew/Desktop/Rename. It was /Rename. That's folder Rename, right at the root of the file system. Look there.

---

### Post by redshift88 on 2009-08-03
> **niteshifter said:**
> Er, no. Your dd target directory was not /home/andrew/Desktop/Rename. It was /Rename. That's folder Rename, right at the root of the file system. Look there.


You're right.  I found the data, used Brasero to create a proper .iso, and then I used playonlinux and it kept saying "Error: Unable to find the CD-ROM !"  no matter where I mount it.

BUT...this is another issue not related to the title of the topic.  


Thank you very much, everyone, for all your help

---

