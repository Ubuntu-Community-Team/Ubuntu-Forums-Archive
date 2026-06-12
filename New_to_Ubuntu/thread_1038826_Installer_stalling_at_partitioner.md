---
title: "Installer stalling at partitioner"
date: 2009-01-13
forum: New to Ubuntu
---

### Post by DestructionPreventer on 2009-01-13
Trying to install 7.04, the install stalls when running the partitioner. My friend who suggested I try Ubuntu says this error happened with his computer (Also HP, like mine) and was fixed by tinkering with some boot commands that he's long since forgotten. Lucky me. Anyone have any insight into this? I wish I knew more, I'm very new to it.

---

### Post by steve8track on 2009-01-14
Try downloading the live gparted cd:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

That is the same program Ubuntu uses to partition the drive.

The problem with the live CD is that it loads the whole OS into RAM and claims it leaves your hard drive alone, but I'm inclined to believe it may be accessing the hard drive, perhaps just while scanning hardware or to store anything that doesn't fit into RAM.  Either way, it is like the live Ubuntu CD sometimes steps on it's own toes.  Try Opening the file browser (nautilus) under the places menu, right click the hard drive in the left hand column, and tell it to unmount.  If that doesn't work, try the gparted CD.

Alernatively, you could fix the problem by trying a different Ubuntu CD with a different version.  (You could upgrade after installing if you choose that route.)

I hope this helps,

Steve

---

