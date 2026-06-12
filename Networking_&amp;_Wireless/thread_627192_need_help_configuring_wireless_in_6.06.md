---
title: "need help configuring wireless in 6.06"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by nolis615 on 2007-11-29
when i go to the network preferences to configure my wireless card, all it shows is a connection called "lo"

i don't think my wireless card is supported by ubuntu

please help!

---

### Post by erfahren on 2007-11-29
I may not be able to help you completely, but hopefully can get you started

what kind of wireless card? one of these should tell you
```

lspci -nn | grep Ethernet
lspci -nn | grep Network

```

---

### Post by erfahren on 2007-11-29
oh, I forgot to include these. guides that may be helpful:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

