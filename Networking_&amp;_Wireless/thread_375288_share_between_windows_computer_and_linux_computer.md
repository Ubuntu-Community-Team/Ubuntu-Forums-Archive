---
title: "share between windows computer and linux computer"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by zami on 2007-03-03
I need to create a directory (or partition, I don't care which) that can be read/writable from both
-my husbands Windows/NTFS computer, and
-my Linux (Ubuntu) Ext3 computer.

I  would need to put this shared directory or partion on my Linux machine.  (We are about  to wipe his machine and have 20 some gigs we need to backup).

Are there any walkthroughs available detailing how to do this?

I've been searching the forums, but most of what I've found involves sharing information between Windows and Linux on a dual boot machine - not what I'm  looking for at all.

I imagine this is a pretty common scenario so there must be a how-to out there.  I'd much appreciate anyone pointing me to it!

Thanks!

-zami

---

### Post by Mr. C. on 2007-03-03
You want Samba.

This allows you to share your linux system to create and use windows shared resources.

Configure your disk as an ext3 (or your favorite fs), mount it, install and configure samba.

Share your disk and you can have read/write access from any PC on your LAN.

Finding howtos' should be straightforward given this info.

MrC

---

### Post by zami on 2007-03-03
Awesome.  Thank you so much.

Just having the basics like that gives me a great starting point. As you said, I should be able to make use of the forums now.  I think my searches were too... vague.

(I'll still check on this thread incase anyone knows a how-to location right off the top of their head!)

Thanks again Mr. C!

-zami

---

### Post by Mr. C. on 2007-03-03
I've never looked through this howto, but here's one locally:

[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba)

I also recommend learning the app directly from the source.  Go to [www.samba.org](www.samba.org), select a nearby mirror, and then go to the HowTo on the left side midway down.

---

