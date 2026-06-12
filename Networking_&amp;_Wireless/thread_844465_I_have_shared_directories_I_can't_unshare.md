---
title: "I have shared directories I can't unshare"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by Hooya on 2008-06-29
I have two directories shared that I can't figure out how they are shared on the network.  One is my home directory the other is on an auto mounted other partition.  My smb.conf file contains no information about the two directories at all, but they are still shared.  Also, when I check in Gnome on the sharing properties of the directories they do not appear shared.


What other computers see:
The /home/* directory is visible but not accessible in any way.
the /media/Documents directory is visible, mountable and writable with no username or password.

The thing is I can't figure out how these directories are shared.  Is there something else that might be sharing them?  I do have pyNeighborhood installed, but I didn't think that was capable of sharing, just mounting shares.

Any ideas?

---

### Post by Hooya on 2008-06-30
God I hate to be that guy, but; bump.

---

### Post by pmlxuser on 2008-06-30
just do
$sudo chown yourusername:yourusername /directory

the comand changes ownership of the stated folders which will also change the sharing properties.when u share a folder the last part of the properties  yourusername:yourusergroup.. something

say if it works/ its supposed to work though.

---

### Post by Hooya on 2008-06-30
No, the phantom folders are still there after I do that.

I was wrong above by the way, neither of them are accessible at all from remote machines, but the fact that they're showing up in the list is annoying.  Is there something somewhere that maintains a list of the folders to announce to the network?  I feel it's probably just being announced incorrectly not actually shared incorrectly.

---

