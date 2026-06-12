---
title: "How to Mimic Windows Home Server with Ubuntu?"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by dmaxel on 2010-02-15
Hi everyone,

My family has been switching more and more computers over to Ubuntu, and now I want to see what all it can do.

Currently we still have a handful Windows machines, along with a Windows Home Server. We are using the server as a file server (which we will eventually switch to Ubuntu using SAMBA as long as my question gets answered), and as a backup system.

When I mean backup system, I mean the little program that you can install onto client Windows systems which will then backup the entire system (in order to enable the use of a FULL recovery, no matter if even a new HDD has to be used) to the Windows Home Server.

Since I know how to do file sharing with SAMBA, I would like to know what I could do/use (if possible) to backup entire Windows **and** (again if possible) Ubuntu systems and have them on the server (which would be Ubuntu if there are methods in doing this). What possibilities do I have? Please do not recommend using a Sync Program, as they are ideal for data/documents, not system files. Thank you.

---

### Post by jflaker on 2010-02-15
> **dmaxel said:**
> Hi everyone,

My family has been switching more and more computers over to Ubuntu, and now I want to see what all it can do.

Currently we still have a handful Windows machines, along with a Windows Home Server. We are using the server as a file server (which we will eventually switch to Ubuntu using SAMBA as long as my question gets answered), and as a backup system.

When I mean backup system, I mean the little program that you can install onto client Windows systems which will then backup the entire system (in order to enable the use of a FULL recovery, no matter if even a new HDD has to be used) to the Windows Home Server.

Since I know how to do file sharing with SAMBA, I would like to know what I could do/use (if possible) to backup entire Windows **and** (again if possible) Ubuntu systems and have them on the server (which would be Ubuntu if there are methods in doing this). What possibilities do I have? Please do not recommend using a Sync Program, as they are ideal for data/documents, not system files. Thank you.

For windows boxes, may I recommend Mozy.  You get 2gb per email address and you can pay for a pro account which I believe will allow you to back up multiple systems to one account.  For my 2 Win Boxes, I use 2 free accounts which gives me just enough room.  It has been set it and forget it for almost 2 years not with no issues.

---

### Post by dmaxel on 2010-02-15
> **jflaker said:**
> For windows boxes, may I recommend Mozy.  You get 2gb per email address and you can pay for a pro account which I believe will allow you to back up multiple systems to one account.  For my 2 Win Boxes, I use 2 free accounts which gives me just enough room.  It has been set it and forget it for almost 2 years not with no issues.
Thanks for the suggestion, but A) It wouldn't use my Ubuntu server, B) It's space limited, and C) As far as I know, Mozy is for documents, not everything, which would include system files.

---

### Post by ask21900 on 2010-02-16
If I understand you correctly, you are asking for a way to backup an entire windows system to an Ubuntu server?

As a certified tech, I always recommend Acronis TrueImage to my customers for windows systems.  TrueImage will allow you to backup over a network (local or internet), so you can backup the image to your Samba share.  It is not free, but IMHO, it is the best backup solution for Windows.

As far as backing up Ubuntu (Desktop) to an Ubuntu Server, rsync does the trick.  It has no problem syncing system, or any type of files.

---

### Post by anewguy on 2010-02-16
You may also want to check Macrium Reflect.  They (at least used to - haven't check in a year or so) have a free version for personal use.  It makes an image file of your drive (or a partition) and can store that file on a some sort of external USB devices or with network support to a network share.  I had Ubuntu server on a older PC to play with it a year or more ago, and had a Windows machine that I ran Macrium Reflect on and directed the output to a Samba share.  Macrium Reflect lets you build a recovery CD (you have to do a little extra to install network support, but it's EASY) so you can load that image file back to disk - including a hard disk larger than the 1 the image is from.  Makes it real handy to backup a bunch of Windows machines to a Samba server as each backup gets it's own file name (so you could have like "bedroom1PC" and "mediaPC" and "officePC", as an example).

I sure there are other products that do the same thing and probably just as easily - perhaps the one already posted by ask21900 (I've never used any other so I can't comment one way or the other on any other software).

Good luck!

Dave ;)

---

### Post by cariboo on 2010-02-16
Have a look at [DeltaCopy]("http:///www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp"), I'm testing it right now, and so far it does everything it says.

---

### Post by dmaxel on 2010-02-16
Macrium and especially DeltaCopy seem like excellent choices. I'll have to look at them once I've gotten a few winks of sleep. If anyone can suggest anything else, that would be great, but from what I'm seeing, I think I hit gold. :popcorn:

---

### Post by rgotten on 2010-04-12
> **cariboo907 said:**
> Have a look at [DeltaCopy]("http:///www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp"), I'm testing it right now, and so far it does everything it says.do you have an easy how to configure it to copy windows clients into ubuntu server with Deltacopy?

---

