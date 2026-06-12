---
title: "How to connect to wireless network"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by Questioneer on 2007-05-24
Hello. I have Ubuntu 7, and a Linksys wireless G adapter. I installed the correct driver under ndiswrapper, and everything seems to have worked(it says device and driver are present). Now however, how do I connect to my wireless network, which has WPA password protection, and is hosted on windows?? Remember that I'm almost completely new to Linux, and I don't know shorthand commands and basically need it all spelled out.
thanks

---

### Post by benanzo on 2007-05-24
Which wireless adapter is it?  It's likely a Broadcom adapter if it's made by Linksys.
Is it a USB or PCI adapter?
While connected to the internet (via ethernet or otherwise)
Open a terminal **Applications -> Accessories -> Terminal** and type:
```
sudo update-pciids
```
then do:
```
lspci | grep Broadcom
```
(if it's PCI)

Post that info back here.  It will tell which specific chip you are using.

---

### Post by Questioneer on 2007-05-24
Sorry. I should have clarified that I don't have internet access at all. (Except with Windows, which uses my Adapter).
OK here was the update pciids output:
```

--17:50:21--  http://pciids.sourceforge.net/v2.2/pci.ids.bz2
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... failed: Name or service not known.
update-pciids: download failed

```
I assume this is because I'm not connected to the internet.

and here was the output of lspci:
```

05:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```
So what should I do now?

---

### Post by Questioneer on 2007-05-25
Does ndiswrapper need special add ins for WPA?

---

