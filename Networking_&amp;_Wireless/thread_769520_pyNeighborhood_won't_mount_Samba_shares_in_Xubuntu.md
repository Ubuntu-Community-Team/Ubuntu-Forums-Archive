---
title: "pyNeighborhood won't mount Samba shares in Xubuntu"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by tvphil on 2008-04-26
I have already read some forum info. on this subject, without any success. I am using pyNeighborhood to look at Samba shares on my network, since Xubuntu doesn't have a default client that does this, like Ubuntu does (something that still makes no sense, but that's another thread for another day).PyNeighborhood is working in all other respects, I can find other computers on the network, I can even see the names of the folders after scanning. I took the advice of another thread and use PyNeighborhood as root, using gksudo, but I still can't mount any of the other computers on my network. None of my other computers running Ubuntu have this problem, so I'm assuming it has something to do with pyNeighborhood. I already made my home folder read and write shared, using Shared Folders, so I know it shouldn't have anything to do with permissions. Any ideas on what might help? I've run out of any right now.

---

### Post by tvphil on 2008-04-27
I love answering myself. Apparently, checking the box in preferences to capture the i.p. address is what it needs to mount a share. Why doesn't it do this by default? After doing this, then you have to type in "Thunar" to a new file manager box and add it. Too bad they stopped development on this 2 years ago, it needs it. Right now, it seems to be the only way to see other Windows computers on a network, while using Xubuntu.

---

