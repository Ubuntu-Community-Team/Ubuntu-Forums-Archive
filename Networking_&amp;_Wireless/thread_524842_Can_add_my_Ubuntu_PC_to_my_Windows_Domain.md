---
title: "Can add my Ubuntu PC to my Windows Domain?"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by Jay_Rock on 2007-08-13
Is there a program or tool I could run in order to get my Ubuntu PC added to my domain?
Or a way to just share files with on my Win03 server and other Win PC's? 

Their has got to be an easy way to accomplish of this task.

---

### Post by gashcrumb on 2007-08-13
The easiest way is to go into System/Administration/Shared folders in the gnome menu, from there you have a choice between using samba or NFS to share a folder, you want samba.  You should be prompted to install samba if it isn't installed already.

You can do a lot more with samba as well, go to System/Help and Support and type samba in the search text field and hit enter, the man page for samba is a good starting point.

---

