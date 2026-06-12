---
title: "portable ubuntu startup"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by bdws1975 on 2009-12-09
Hi all

I'm very new to Linux and decided to try the portable Ubuntu and run it from a thumbdrive.
I downloaded, extracted to my drive and then double flied on the application.  It then just shows a box that says portable Ubuntu remix and that's it.
am I doing something wrong?
I use windows for my job and really want to get into Linux.  I appreciate your help.
thanks
brett

---

### Post by ukripper on 2009-12-09
Best way for you to try linux without changing anything is using wubi - [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

> Wubi is an officially supported Ubuntu installer for Windows users that can install and uninstall Ubuntu as any other Windows application, in a simple and safe way

.

---

### Post by lotharmat on 2009-12-09
Another way is to download unetbootin in windows and create a bootable thumb-drive with ubuntu on.

Boot from the aforementioned thumb-drive and Bob's yer uncle!

---

### Post by bdws1975 on 2009-12-09
hi all,
 
thanks for the replies.
 
I've downloaded unetbootin.  Is there a particular version of ubuntu I should download?
 
 
 
Thanks,
Brett

---

### Post by bdws1975 on 2009-12-09
also, should I just choose the download from the 'distribution' at the top of the unetbootin box?
 
I'm sorry, but I'm VERY new to any alternative stuff on computers, but I'm wanting to expand my horizons.
 
thanks,
brett

---

### Post by bdws1975 on 2009-12-09
> **ukripper said:**
> Best way for you to try linux without changing anything is using wubi - [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
 
 
 
.
 
hi.  I went to the guide but where to I download it?  I can't find any link or location from which to download.
 
Thanks,
brett

---

### Post by ukripper on 2009-12-09
> **bdws1975 said:**
> hi.  I went to the guide but where to I download it?  I can't find any link or location from which to download.
 
Thanks,
brett


There was a link -
[http://wubi-installer.org/](http://wubi-installer.org/)

> How do I install on a machine with no internet connection?

Wubi works with a physical Ubuntu Desktop 9.10 Live CD. Wubi.exe is available on the CD itself.

If you do not have a CD, try to find a computer with internet access, and download both Wubi and the required ISO:

    *

      [http://wubi-installer.org/latest.php](http://wubi-installer.org/latest.php)
    *

      [http://releases.ubuntu.com/9.10](http://releases.ubuntu.com/9.10) 

Then copy both files within the same folder on the machine with no internet acces. Then run the Wubi executable. If you have internet access on the machine where you plan to install Ubuntu, you only need Wubi (the first link), Wubi will automatically download the other file as required. 

---

### Post by lotharmat on 2009-12-09
> **bdws1975 said:**
> hi all,
 
thanks for the replies.
 
I've downloaded unetbootin.  Is there a particular version of ubuntu I should download?
 
 
 
Thanks,
Brett

Personally, I'd download the 9.10 version (Karmic Koala) 

Download the iso and then use option 2 in unetbootin (choose an iso file)

make sure, before you hit 'create' that it has correctly picked up your USB drive and not on the hard drives in your PC (Look at windows explorer to see if the drive letter is correct!)

---

