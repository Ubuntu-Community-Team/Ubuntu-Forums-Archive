---
title: "How to &quot;map&quot; 7.04 to a drive on a networked Windows XP machine?"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by TheTaylorEffect on 2007-07-15
Hello All,

I'm still relativley new to Linux, but I have a great background in general networking. I'm not sure if the term "Drive Mapping" has any meaning in the world of Linux... but for those of you that aren't familiar with the terminology, a mapped drive is a pathway to a drive on a network that makes it appear as a local path for local applications.

We've got a fairly large Windows sever on our network (750gb drive), and my roommates and I compile all of our collectively downloaded Torrent booty there. 

We do this by simply 'maping' our local machine  to the drive on the server. Than we use the 'mapped' path in the local bit torrent client as the download folder (so the downloads would get dumped directly into the hard drive on the the headless server machine, rather then storing them on my local hard drive).

I was wondering if there is anyway to "map" a drive on a Windows computer into Fiesty, for the same purpose.

Its important that this "mapped" pathway reconnects automatically with every reboot. Is this possible?

Thanks in advance!

-MT

---

### Post by spd106 on 2007-07-16
You probably want to add a line in your /etc/fstab file. 

Read this guide in the wiki for instructions.
[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

Nevermind, a solution appears to have been found.
[http://ubuntuforums.org/showthread.php?t=501575](http://ubuntuforums.org/showthread.php?t=501575)

---

