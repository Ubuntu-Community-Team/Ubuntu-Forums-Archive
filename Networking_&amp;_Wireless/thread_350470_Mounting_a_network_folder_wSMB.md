---
title: "Mounting a network folder w/SMB"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by fusiachi on 2007-01-31
Hi,

I'm on a college network w/access to a shared network drive.  I can access it via Konqueror by entering **smb://fas\robertsw@files/students$** into the address bar (where it then prompts me for username and password).  No problems there.

My question is: how do I mount this drive such that it'll appear on my desktop/in my file browser rather than going through konqueror every time?  I've tried following a few sets of directions, but w/no luck.  Also, my pass has a "!" in it, so I don't know if that'll affect anything or not.  Basically, I don't have a clue.  Any help would be appreciated.

-wade

---

### Post by mayonaise15 on 2007-02-01
Check out [this article]("https://wiki.kubuntu.org/MountWindowsSharesPermanently?highlight=%28mount%29%7C%28smb%29") on the Kubuntu Wiki that may help you out.

Let us know how it works out for you. :D

---

### Post by fusiachi on 2007-02-03
Those directions didn't work for me.

As it stands, browsing the fileserver from Konqueror will cut it, I guess.  May not be the ideal solution, but it looks like it'll be the easiest.

Thanks for your time.

---

### Post by mayonaise15 on 2007-02-04
I'm sorry, I'm a bit confused.  Are you using the Gnome desktop or the KDE desktop version of Edgy?  Your profile says Ubuntu (which is gnome) but Konqueror is a KDE browser.  If you could clear that up for me, I may be able to help you get some results.

---

### Post by gradedcheese on 2007-02-04
The 'mount' command can accept 'smbfs' as a file system type, so you can actually mount the network share that way.  You can then add an entry for it in /etc/fstab to have it mounted automatically.  This will also be Gnome/KDE independent.

---

### Post by Johan! on 2007-02-04
[http://www.ubuntuforums.org/showthread.php?t=288534](http://www.ubuntuforums.org/showthread.php?t=288534)

---

### Post by fusiachi on 2007-02-04
> **mayonaise15 said:**
> I'm sorry, I'm a bit confused.  Are you using the Gnome desktop or the KDE desktop version of Edgy?  Your profile says Ubuntu (which is gnome) but Konqueror is a KDE browser.  If you could clear that up for me, I may be able to help you get some results.


I'm using Gnome.  It just so happens that Konqueror worked for accessing shared network folders, so I used it.  

I should mention that my problem was solved; since upgrading to 6.10 I've had no troubles mounting our fileserver.  Thanks for your time.

-Wade

---

