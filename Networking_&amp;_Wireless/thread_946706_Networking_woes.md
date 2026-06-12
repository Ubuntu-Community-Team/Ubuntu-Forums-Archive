---
title: "Networking woes"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by Florida Cracker on 2008-10-13
I've set-up ubuntu hardy on 3 computers and I've been unable to browse windows shares on any of them. I've installed samba and followed many tutorials/articles/forum posts, yet none of them have worked for me on any of the three computers. I can get windows to see ubuntu shares very easily. I can see and click on the workgroup, I can actually see and click on the workgroup computers, but it sits there with a wait cursor for about a minute then brings up nothing. No access to the shares. My p2p network consists of several windows computers running 98, xp, and vista. they all see each other and the linux boxes, but the linux boxes cannot connect to windows boxes or each other.
Anyone else run into this problem or know how to get it to work?
Thanks

---

### Post by Florida Cracker on 2008-10-14
Can someone please help me out. I don't want to go back to windows.

---

### Post by Florida Cracker on 2009-02-18
I finally solved my problem.
I did a sudo gedit on my nsswitch.conf file and added wins in front of dns in the hosts:files line. Now all windows shares show up and are easily accessed. Hope this helps others with same problem.

---

