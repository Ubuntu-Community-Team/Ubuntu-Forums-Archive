---
title: "WUBI windows file integration"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by 11010110 on 2008-12-13
I was told that there would be a way for me to access the document and other files that are located underneath my windows system while i was running ubuntu ibex thru a wubi setup. Under comuter i see the file system, cdrom, and "TOSHIBA SYSTEM VOLUME". I assume that that is what im looking for. however, once i click it, and enter my sudo password  it tells me that the system cannot mount the disk and then once i enter i get a fre useless files that when clicked run nothing and lead nowhere. 

I was wondering if anyone has any ideas on how i could gain access to my windows files. thank you very much in advace everyone any information would be appriciated.

---

### Post by Titan8990 on 2008-12-13
That error is common for users when Windows was not shut down properly. When it is not shut down properly, the drive stays flagged as being used.

Try logging in to Windows and gracefully shut down. Log back in to Ubuntu and try again.


The alternative is to force mount it which will require a little CLI.

---

### Post by abn91c on 2008-12-13
> **11010110 said:**
> I was told that there would be a way for me to access the document and other files that are located underneath my windows system while i was running ubuntu ibex thru a wubi setup. Under comuter i see the file system, cdrom, and "TOSHIBA SYSTEM VOLUME". I assume that that is what im looking for. however, once i click it, and enter my sudo password  it tells me that the system cannot mount the disk and then once i enter i get a fre useless files that when clicked run nothing and lead nowhere. 

I was wondering if anyone has any ideas on how i could gain access to my windows files. thank you very much in advace everyone any information would be appriciated.

 your windows drive is /host, or go to dolphin file manager click on the root folder then on the host folder to access windows files

---

### Post by vanadium on 2008-12-13
Pay attention to Titan8990's post: it is important.

In addition to that, you might prefer to mount your ntfs partition automatically during startup instead of "on demand". This will require adding the partition to /etc/fstab yourself.

Either way, you must make sure that your ntfs partition is properly closed before (attempting) to access it with Ubuntu. This is the case when you fully close Windows down, not when you hibernated.

---

### Post by Paqman on 2008-12-13
> **vanadium said:**
> Pay attention to Titan8990's post: it is important.


I don't think it is. I'm thinking the "Toshiba System Volume" is a recovery partition that shouldn't be mounted in either Windows or Ubuntu. 

> 
In addition to that, you might prefer to mount your ntfs partition automatically during startup instead of "on demand". This will require adding the partition to /etc/fstab yourself.


Wubi automatically sets the NTFS partition to mount at /host.

---

### Post by 11010110 on 2008-12-13
thank you guys very much! ill leave that toshiba volume alone lol. i found the files i was looking for and everything works like a charm! would there be a way i could link the /host directory to the wain computer explorer page (next to filesystem) in order to gain easier access? if so that would be great if not then no problem

---

### Post by abn91c on 2008-12-13
> **11010110 said:**
> thank you guys very much! ill leave that toshiba volume alone lol. i found the files i was looking for and everything works like a charm! would there be a way i could link the /host directory to the wain computer explorer page (next to filesystem) in order to gain easier access? if so that would be great if not then no problem

right click on the host folder then "add to places"

---

### Post by 11010110 on 2008-12-13
hmm... there is no right click option "add to places"

---

### Post by abn91c on 2008-12-13
> **11010110 said:**
> hmm... there is no right click option "add to places"

sorry I was using kubuntu earlier, if you install the dolphin file manager you get that option

---

### Post by abn91c on 2008-12-13
you can try copy/paste to desktop if its just a document folder

---

### Post by vanadium on 2008-12-14
You can just drag your folder to the "Places" panel, or use "Bookmarks", "Add bookmark". I recommend you only do this for your Windows "My Documents" folder. There is no need nor is it recommended to have easy access to Windows system files.

A (much) better way that will integrate your Windows "My Documents" into your Ubuntu installation, is to create a symbolic link. Press Ctrl+Shift and drag the Windows "My Documents" folder to your personal home directory (you best do that with two nautilus Windows side by side). That way, a symbolic link will be created in your home directory that acts and feels just like a real directory: it is as if you would have moved that folder right in your home.

@pacman

[quote=pacman]
Quote:
Originally Posted by vanadium View Post
Pay attention to Titan8990's post: it is important.
I don't think it is. I'm thinking the "Toshiba System Volume" is a recovery partition that shouldn't be mounted in either Windows or Ubuntu.[/quote]
It is. He was not referring to mounting the Toshiba System Volume, but to the necessity of having a properly closed ntfs volume in the first place. "host" will not be mounted if the Windows file system is not "clean".

---

### Post by Paqman on 2008-12-14
> **vanadium said:**
> 
It is. He was not referring to mounting the Toshiba System Volume, but to the necessity of having a properly closed ntfs volume in the first place. "host" will not be mounted if the Windows file system is not "clean".

Indeed, however nothing the OP described suggested that the problem was an unclean shutdown.

---

