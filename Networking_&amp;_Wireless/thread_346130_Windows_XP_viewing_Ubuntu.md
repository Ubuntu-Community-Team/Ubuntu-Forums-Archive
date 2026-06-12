---
title: "Windows XP viewing Ubuntu"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by Gorlist on 2007-01-25
Hi, right when I first installed Ubuntu many moons ago I setup a shared directory which appeared fine on the MSHOME network and worked fine - I noticed about a month ago it disappeared completely for some reason. 

I just installed Xubuntu on another old office machine, setup a shared directory and again the shared folder does not appear on the MSHOME network for some reason?

If I "View workgroup Computers" from Windows XP I do see both linux machines listed, though if I double click on them out of interest it promts for a username & password...

Now ive also tested from a second Windows XP system, and that also fails to displayer the shared folders.

Anyideas?

Regards!

---

### Post by rmartz on 2007-01-25
Just read a post that might shead some light into your dilema.

[http://ubuntuforums.org/showthread.php?t=346130](http://ubuntuforums.org/showthread.php?t=346130)

The username and password request means you need to set up individual accounts one the linux machines unless you modify the smb.conf file. You should be able to search the posts to find the exact commands needed to allow guests to view the shared folders.

Hope that helps.

---

### Post by Gorlist on 2007-01-26
Thanks, will take a look at the link shortly - so why did it work fine first time round for a couple of months??

Regards,

****The link brings me back to this thread :) heh**

---

### Post by rmartz on 2007-01-26
Sorry about the incorrect link. It was late and I must have copied and pasted from the wrong page. 

There are continual updates available that are not supposed to make things wacky, but seems to do so from time to time. I had to redo my network card settings a few days ago ... right after an update. I noticed that several others seemed to have the same issue.

You should be able to search the forums for Samba and edit smb.conf to get you the info you are looking for. You could search for "guest ok = yes" and it will tell you how to make your Ubuntu shares available without having to set up individual accounts.

Hope that helps a bit.

---

