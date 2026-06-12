---
title: "AT&amp;T 6700G wireless help"
date: 2005-11-07
forum: Networking &amp; Wireless
---

### Post by jakewiz247 on 2005-11-07
I just installed the new version of ubuntu on my thinkpad 600e.  Everything is working fine on it except for my wireless card.  I have an AT&T Plug and Share 6700G PCMCIA card.  I have loaded the drivers from the network card CD and installed them using ndiswrapper.  Drivers show as installed and hardware installed with ndiswrapper -l.  Try to connect to my access point but still get nothing.  I have configured the wireless key, change, and mode.  The only other thing i could think it might be is the drivers I'm using.  I noticed on the compatibility list that the driver that is being used is ar5212 and I have been using ar5211.  Others have used the ar5211 and have worked so I'm not sure.  Someone please give me something to work with.

---

### Post by mips on 2005-11-07
Have a look at these threads:
[http://ubuntuforums.org/showthread.php?t=17940&highlight=6700G](http://ubuntuforums.org/showthread.php?t=17940&highlight=6700G)
[http://ubuntuforums.org/showthread.php?t=13977&highlight=6700G](http://ubuntuforums.org/showthread.php?t=13977&highlight=6700G)
[http://ubuntuforums.org/showthread.php?t=8490&highlight=6700G](http://ubuntuforums.org/showthread.php?t=8490&highlight=6700G)
[http://ubuntuforums.org/showthread.php?t=12696&highlight=6700G](http://ubuntuforums.org/showthread.php?t=12696&highlight=6700G)

Try adding **acpi=off** to the linux boot line in GRUB

---

### Post by jakewiz247 on 2005-11-09
Alright i checked out all of these links and all they are telling me is that their cards worked right out the box.  This is not the case for me.  Ubuntu recognized my card but does not connect to my AP.  When it does actually act like it is connect, i do an ifconfig and instead of an ip addr:  i get an inet6 addr:.  Any idea why that is?

---

