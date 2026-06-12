---
title: "I am wanting to build a rack-mounted NAS server with hot-swap RAID..."
date: 2010-03-05
forum: New to Ubuntu
---

### Post by diablo75 on 2010-03-05
Actually, someone is asking me if I can build one for them.

They'd like to have four 1TB drives with a 5th to spare in case any of the first 4 crash on them.  I've never messed with RAID first hand but I understand there's such a thing as a "hot-swappable" system where you can pull a dead drive from a system while it is running and a fresh one will automatically be rebuilt upon insertion.  How might I go about building something like this with Ubuntu?

EDIT:  One other question.  Once built, what's the best way to share out this NAS to a network of Windows PCs?

---

### Post by Jordanwb on 2010-03-05
I don't know much about RAID 5 (which is what you want) but if you can talk your client into a sixth drive, that one can be used as a hot spare. AFAIK you can't simply yank out the bad drive, you have to remove it from the array first then physically remove the drive. If you have the hot spare the rebuilding will occur automatically.

There is a program for Windows machines to access NFS shares (crazy thing is >500MB IIRC), if that's not an option Samba will work.

---

### Post by diablo75 on 2010-03-05
Anyone know what kind of hardware is requires to put something like this together?

They are wanting to use a case like this one:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3655174&Sku=I202-1074](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3655174&Sku=I202-1074)

---

### Post by stegouin on 2010-03-06
Have you looked at the Drobo? [http://www.drobo.com/products/index.php](http://www.drobo.com/products/index.php)

I've been wanting one for awhile... some drawbacks... Linux support is beta and I believe ext3 filesystem only... 

It's not network ready either, a separate appliance needs to be purchased, called the DroboShare.

I'm monitoring their product releases... once full Linux support ext4 is available, I'm getting one.

---

