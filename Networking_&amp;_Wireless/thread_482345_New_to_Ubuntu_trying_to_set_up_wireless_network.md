---
title: "New to Ubuntu trying to set up wireless network"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by digitaldixon on 2007-06-23
Hello,

I have an x86 that I just lodaed Ubuntu 6.06 onto.  Everything went quite smoothly except for my wireless access to the internet.  In the Networking Administration area I can see my card, everything appears to be enabled, but I cannot get out to the internet.  I have read some of the threads telling me I ned linux-restricted-modules, but I cannot figure out how to get these or use them.

My wireless adapter is a Trendnet TEW-443pi.  Can someone please help me get this thing up ad running?

Thank you,

John Dixon

---

### Post by spd106 on 2007-06-24
If your card uses the Atheros chipset (ar5212), then yes you do need the linux-restricted-modules package, though it should be installed by default. To check open up System -> Admin -> Synaptic Package Manager and search for it. If you can see wireless networks then this is probably already installed and working.

You might want to try installing Network Manager, though in my experience it didn't work well on Ubuntu 6.06. If you are trying to use WPA encryption, then I recommend that you read the Wireless Security howto sticky on page 1.

---

