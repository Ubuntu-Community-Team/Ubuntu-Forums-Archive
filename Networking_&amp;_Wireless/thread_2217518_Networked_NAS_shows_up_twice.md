---
title: "Networked NAS shows up twice"
date: 2014-04-17
forum: Networking &amp; Wireless
---

### Post by Rocket J Squirrel on 2014-04-17
Ubuntu 12.04, Synology NAS, windows network

We have a Synology NAS here that shows up twice in both PCManFM and Thunar File Manager. They are both under "Network," and in both file viewers one shows a path of smb://diskstation/ , and the second as afp://diskstation.local/

The smb: path is correct, and the NAS can be accessed via it. The afp: path is not correct, and attempting to view files results in "Failed to open directory "AFP volumes on diskstation", "Error sending data: Broken pipe."

The afp: path is probably an old path. Even when the NAS was taken out of the network for repair, it continued to show up in the file managers. 

Viewing the NAS from Windows machines doesn't result in two paths. 

How can I get Ubuntu to let go, forget, stop pestering me with this dead path?

---

### Post by houstonbofh on 2014-04-17
You have an Apple file share running.  Linux is smart enough to see it, but Windows does not beleiev anything other than it actually exists.  If you do not want to see it, and you do not have a lot of MACs, just turn off Apply files sharing in the Synology.

---

### Post by Rocket J Squirrel on 2014-04-17
Okay, that's weird. There are two iPhones and one iPad in the entire building, on wireless. Does that make sense?

EDIT: Sorry, of course it makes sense. I'll take a look at the Synology this weekend.

---

### Post by Rocket J Squirrel on 2014-04-19
Yes, turning off Mac File Service on the Synology NAS (Control Panel > Win/Mac/NFS) did the trick. And it greatly sped up browsing the Windows network from the Ubuntu file managers. Many thanks.

---

