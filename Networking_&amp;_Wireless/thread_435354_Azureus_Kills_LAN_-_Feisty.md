---
title: "Azureus Kills LAN - Feisty"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by craized on 2007-05-06
Hello everyone,

I'm new to the forum and I hope this is the right place to post this. So far Azureus has been the only torrent client I've found that does RSS downloading well, so I'm pretty attached to it. The problem is that after it runs for ~15 minutes my torrent speeds all drop to 0 and my internet connection locks up for 5-10 minutes. I've tried lowering my max connections/speeds based on a calculator I was linked to from this forum (I don't remember the URL). Any help would be greatly appreciated and I'm happy to post any info that would help.

Thank you,
-Craized

EDIT:
Ubuntu 7.04 Feisty AMD64

---

### Post by Bagster on 2007-05-08
I had the same problem - kinda....

After Azureus was runing for about 10 minutes, download and upload speeds would drop to zero. In my case the network was still working, it was only azureus that was stopping. It turns out that this was due to it using the gcj version of java instead of the sun version. If you have not done so, try installing  Sun's java 6.0 from the repositories. If you hve done this, try running

sudo update-alternatives --config java

and make sure that you are using sun java version 6.

This solved my problem - hope it does the same for you :)

---

### Post by craized on 2007-05-08
Thanks for the response. Azureus is crashing every time I try to open a torrent now so I'm giving up on it. I found KTorrent which offers RSS downloading as well as everything else I want except silent torrent adding.

---

