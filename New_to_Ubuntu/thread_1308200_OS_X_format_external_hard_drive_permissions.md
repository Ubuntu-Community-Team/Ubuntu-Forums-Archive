---
title: "OS X format external hard drive permissions"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by catraeth on 2009-10-31
I have pretty much everything working as it should now (touch wood I guess) but I have one 'final' ;) problem that I need some help with.  I have a 350 gig external hard drive which is formatted for Mac OS X but my Imac G5 is defunct (on its 3rd power supply unit!).  So I need to access the drive and to be able to make changes/copy files etc in Ubuntu.  The drive mounts without any trouble but the folders in it vary.  Most of them I can access to read files but some I can't access at all.  I have so far been unable to delete any files.  Can I make a 'global' change to the permissions on the external drive so that I'll be able to read and write files easily?

Thanks again.

---

### Post by catraeth on 2009-10-31
I've had a go, but nothing I do seems to work.  I get a message that I am not the 'owner' of the disk and therefore don't have access.  Any help with this would be much appreciated.

---

### Post by jrrader on 2009-10-31
Linux can read HFS+ but I've heard you need to turn off "journaling" via disk utility to get into an HFS+ disk.  That's a good thing - most of the time anyway.  I'd log in as root and attempt to mount it that way.  If that doesn't work, maybe find a similar mac you can borrow to put your HDD in to get OSX working long enough to take the files off.

---

