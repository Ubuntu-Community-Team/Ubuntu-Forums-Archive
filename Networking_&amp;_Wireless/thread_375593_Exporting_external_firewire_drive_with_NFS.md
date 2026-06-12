---
title: "Exporting external firewire drive with NFS"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by hawksworth on 2007-03-03
I've successfully exported, using NFS, my home folder from an Ubuntu Edgy PC to a Mac. I plugged a firewire drive into the Ubunutu, converted it to ext3, and can use write to and read from it with Ubuntu.  However, now I'm trying to export over NFS a couple of directories on the firewire drive (mounted as "lacie").  The mac is mounting the exported directories but I can't see any of the files on the lacie from the mac.  Also the Mac is telling me that only 17G are free on the lacie (which is true of my internal drive, but the lacie firewire drive has 200gigs free.)

I"m exporting as follows:

/home/samm cinderella.local(rw,async)
/media/lacie/backup cinderella.local(rw,async)
/media/lacie/torrent cinderella.local(rw,async)

(my wife named the Mac cinderella because, she claimed, I treated it like a princess)

All three are showing up as mounted on the mac and the /home/samm files shows up just fine.  But the mac shows nothing in either of the lacie folders (and there is something).  What am I doing wrong?

---

### Post by Mr. C. on 2007-03-04
Be sure the directories you are mounting have appropriate permissions and ownership for "nobody" access.

Be sure you are not mounting a symlink.

NFS clients have no idea about the hardware underlying the filesystem's storage.  Its just an NFS mount as far as its concerned.  So don't get focused on firewire or lacie - these are all red herrings.

MrC

---

### Post by hawksworth on 2007-03-04
Thanks - that worked.  Seems that it need the lacie folder to be owned by root, and the group 'users'.  Thanks.

---

