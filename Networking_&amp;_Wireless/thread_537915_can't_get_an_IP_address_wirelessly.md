---
title: "can't get an IP address wirelessly"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by tyggna1 on 2007-08-29
I'm using an Actiontec card.  It reads as a Intersil Corporation Prism 2.5 Wavelan chipset in 

```
lspci
```

which is strange, because it's supposed to be based off the orinoco drivers.  I have the orinoco_pci installed with modprobe, and after doing that was able to see wireless access points with network manager and with WiCD.

Even though I can see them, I can't connect to any of them.

any ideas?

---

### Post by fdrake on 2007-08-29
what's the output of your 
$iwconfig

can you connect using the following command:

$sudo iwconfig <adapter's name: example my is eth1>  essid <name of you wifi  network name> 

do you use a password?

---

