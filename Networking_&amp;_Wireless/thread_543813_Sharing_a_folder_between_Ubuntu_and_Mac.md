---
title: "Sharing a folder between Ubuntu and Mac ?"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by xadloki on 2007-09-05
I'm trying to share files between a Mac and Ubuntu, I have two ethernet cards on the Ubuntu
machine so one is to connect to the ethernet port of the mac and the second one goes to a router
and from there to the internet, I don't want to have access to the internet with my mac, just so it
connects to the other machine. I also have a spare wireless router that I could attach in between the
two and another iBook G4.
I've read that SAMBA is not very good and can mess up something, also I've never tried this sort
of thing in linux so I prefer something simple. Like some small application with GUI that just connects
the shared folders with read/write access.
Some suggestions that I've read are that you can make a ftp server in Ubuntu and it shows up in
Network in the Mac and mounts it, again I prefer something very simple.

---

### Post by reiki on 2007-09-05
First off you can't just string a plain ethernet cable between 2 machines like that. Now if you were to make it a crossover cable then you might be able to pull this off. Terminate 568A on one end and 568B on the other.

---

### Post by xadloki on 2007-09-05
Well I'll put a router in between the two then. What do I do from that point on then ?

---

### Post by xadloki on 2007-09-05
So i played around a little bit with these settings and I managed to connect to the Mac through FTP, and that was pretty simple, just had to turn on ftp sharing in the mac... 
However something so simple to do in Mac seems to be impossible to get working on
Ubuntu...

I've tried to add a folder to share in ubuntu and nothing shows up in the mac end...
please some help would be nice.

---

### Post by xadloki on 2007-09-06
actually you are wrong, I just tried to connect with a single ethernet cable a Windows and Mac and it connects perfectly.
So is this possible to do in linux ?

---

