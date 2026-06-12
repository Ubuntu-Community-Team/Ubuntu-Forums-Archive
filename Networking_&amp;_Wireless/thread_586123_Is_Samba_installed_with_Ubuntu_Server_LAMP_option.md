---
title: "Is Samba installed with Ubuntu Server LAMP option?"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by petersfreeman on 2007-10-22
I have installed Ubuntu Server (Feisty Fawn) with the LAMP option.  Is Samba installed automatically or do I need to install it automatically?  How do I go about installing Samba?   I want to file share a 80GB hard drive that is beside the 20GB one on which I instaled Ubuntu Server.

Thank you,

Peter Freeman

---

### Post by petersfreeman on 2007-10-23
Got it!  Found out how to do it with some trial and error and a late night.  I am now serving my big second drive.  Thanks for your help.

Peter

---

### Post by kevdog on 2007-10-23
Posting your solution would be very helpful!!

---

### Post by petersfreeman on 2007-10-26
Sorry,  here is what I did.  

I searched for "second hard drive" and I found a post that described how to do it.  

My method was a bit unorthodox in that I luckily have another partition on my smaller hard drive and I am running Ubuntu desktop.  I rebooted my box into Desktop Ubuntu, mounted the big 80Gb drive, got its properties which described the mount points.  Armed with that info, I rebooted into Ubuntu server and set up the mount with this information.  I had to mkdir a directory on my small hard drive to act as a surrogate for the mount and then it worked fine.  I needed to chmod to make it read and write.

Let me know if this is not enough info and I'll try to find the post again.  (It was about 4:00am at the time :-)

Cheers,

Peter

---

