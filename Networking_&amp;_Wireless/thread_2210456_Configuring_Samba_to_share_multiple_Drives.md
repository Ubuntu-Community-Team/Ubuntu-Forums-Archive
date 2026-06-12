---
title: "Configuring Samba to share multiple Drives"
date: 2014-03-10
forum: Networking &amp; Wireless
---

### Post by Enforcer83 on 2014-03-10
I have several hard drives connected to my computer mounted at the following mount points.  These drives are configured to auto mount on boot.  How to I configure Samba so when someone browses my network they see mappable drives with the names of MDrive, EDrive, etc?

/media/EDrive
/media/GDrive
/media/HDrive
/media/IDrive
/media/JDrive
/media/MDrive

---

### Post by tfrue on 2014-03-11
I would say that the the person browsing your shares from Windows would have to manually map them from the "Map network drive" option in the left click menu.

---

### Post by Enforcer83 on 2014-03-11
That is what I I am trying to do, but How do I configure samba so it allows me to do that?

---

### Post by bab1 on 2014-03-11
> **Enforcer83 said:**
> I have several hard drives connected to my computer mounted at the following mount points.  These drives are configured to auto mount on boot.  How to I configure Samba so when someone browses my network they see mappable drives with the names of MDrive, EDrive, etc?

/media/EDrive
/media/GDrive
/media/HDrive
/media/IDrive
/media/JDrive
/media/MDrive

The terms "Mappable drives" and things like E: drive etc. are Windows naming conventions.  What you need to do is create a shared directory (the mappable drive) so it can be remotely mounted (the actual mapping of the drive).

Follow [this guide]("http://www.jonathanmoeller.com/screed/?p=4169").  You can use something like this for your shares (the mapped drives)```


[EDrive]
path = /media/EDrive

```...The first line is the name of the share (this is what you see when browsing)  The second line is the path for Samba to find the shared directory to be mounted (mapped).

---

### Post by Enforcer83 on 2014-03-13
I shall try it tonight.

---

### Post by Enforcer83 on 2014-03-13
That was it.  Thank you for the help.

---

