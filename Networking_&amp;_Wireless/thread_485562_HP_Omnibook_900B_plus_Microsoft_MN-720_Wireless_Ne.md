---
title: "HP Omnibook 900B plus Microsoft MN-720 Wireless Network Card disable problem"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by guytrotter on 2007-06-27
Hi all,

I've got an HP Omnibook 900B that I've installed Ubuntu Feisty Fawn upon.  I'm trying to get a Microsoft MN-720 PCMCIA Cardbus wireless network adapter to work with it.  

Ubuntu seems to recognize it - it displays a "wireless connection" under the network settings dialog.  Furthermore, lshw shows the details on the wireless card, but shows "*-network DISABLED".  Thus, somehow, the card is disabled, although recognized.

Anyone have any ideas on getting it ENABLED?

Thanks!


Guy

---

### Post by spd106 on 2007-07-05
Could you please post the output of this command?
```
lspci
```

Chances are you will have to install ndiswrapper.
See [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

