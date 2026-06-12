---
title: "Navigating to connected share"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by jpbeard on 2007-04-13
Hello all, my first post.

Question about Fiesty. I am able to connect to network shares via the Places->Connect to Server menu and it puts a convenient icon on my desktop. How do I access that through the console or through other applications (i.e. like trying to install office from a network share via CrossOver). I know it's possible to mount the share via the console but I was looking for an easy solution.

---

### Post by dbott67 on 2007-04-13
You could mount the shares in your fstab file and then they will automatically mount during boot (or by running 'sudo mount -a').

Complete instructions here:

[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

-Dave

---

