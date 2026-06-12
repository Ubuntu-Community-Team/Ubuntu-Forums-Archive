---
title: "Re-mount home folder to different location"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by MyD0j0 on 2011-02-08
Sorry if this has already been discussed, but the search for "mount home folder" brought back a lot of results and none I saw seemed relevant.  That said...

My 10.10 is installed on an external usb hdd.  It has 100Gb for ubuntu and the remaining is for an ntfs partition that i am using for swap space between ubuntu and various windows machines I use.  In fact, for the windows vista machines, all my profile folders are mapped to folders on the external drive and I'd like to do the same for my ubuntu home folder.  I'm just not sure how I go about linking my home folder in ubuntu to this other partition -- won't there be problems moving the home folder while I am logged in?  and if so...how do I log in as root since there was never a root password specified when the system was installed?

Anyway, thanks for the assistance!

---

### Post by P4man on 2011-02-08
You dont want your homefolder on an NTFS partition. If that would even work, its a guarantee for trouble. I would just change the shortcuts to "documents" "Pictures" etc and point them to the NTFS partition. Just open nautilus, in the menu "bookmarks" choose "change bookmarks" and edit them. Make sure the NTFS partition is mounted on startup though, so it may have to be in your fstab.

---

### Post by [Snc] on 2011-02-08
Well, you can edit fstab to move your home

Take a look [here]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

---

### Post by vanadium on 2011-02-08
The problem remains: you should probably not move your /home to an ntfs partition, which does not support linux permissions.

---

