---
title: "Ubuntu installation backup?"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by Tombgeek on 2010-08-10
Hey there.

I tried searching Google for a way to backup my system should something go wrong.
I want to create a Ubuntu backup .iso or disk that contains all my drivers, updates, configurations, and installed applications. I have all my other data like music and files all on a separate hard drive.
I found there is a thing called Remastersys, but I'm not too sure if it does exactly what I want, and I can not find it in the Ubuntu Software Centre (well, I did, but it is something called "Remaster a CD with additional oem-config functionality").

So what applications can I download which would enable me to do this?

---

### Post by Ron Carson on 2010-08-10
I've been using Lucky Backup for some time.  I recently began messing around with "Back in Time".  I don't think either will burn to CD, but they will backup to an external hard drive.  What I'm looking for is  a backup program that will keep different versions of a backup and automatically delete the older versions.

---

### Post by tea for one on 2010-08-10
> **Tombgeek said:**
> Hey there.

I tried searching Google for a way to backup my system should something go wrong.
I want to create a Ubuntu backup .iso or disk that contains all my drivers, updates, configurations, and installed applications. I have all my other data like music and files all on a separate hard drive.
I found there is a thing called Remastersys, but I'm not too sure if it does exactly what I want, and I can not find it in the Ubuntu Software Centre (well, I did, but it is something called "Remaster a CD with additional oem-config functionality").

So what applications can I download which would enable me to do this?

I can confirm that Remastersys will provide you with an ISO image of your own Ubuntu installation complete with other software that you have added.

It will also automatically include the Ubuntu installation software in case you want to reinstall.

Secondly, have a quick look at Grsync to back up your home directory and media files.

Good luck

---

### Post by inameiname on 2010-08-10
I prefer Remastersys. Grsync works just fine though. Great for incremental backups. Remastersys just is much easier when all you want is a simple tool to have full system backups.

---

### Post by stlsaint on 2010-08-10
I use the Backup/Restore Suite to do my backups. It allows you to select which dir's to backup and to where. It also handles incremental backups as needed.

---

