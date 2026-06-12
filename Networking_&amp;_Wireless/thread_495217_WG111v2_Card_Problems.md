---
title: "WG111v2 Card Problems"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by Shyper on 2007-07-07
I've been having some problems with the WG111v2 USB Adapter I just bought for Ubuntu Internet access. I ndswrapper'd it, and it says the drivers are installed, but the light on the adapter doesn't come on. Furthermore, Ubuntu now recognizes my wireless network, but when I try to connect to the Internet, the icon just spins for a while before timing out. Can anyone help me at all?! I'm all out of ideas. Thanks a lot.

---

### Post by Jose Catre-Vandis on 2007-07-07
Please output the pertinent sections of your:

lsusb
lspci
ifconfig
dmesg

also which ubuntu? Fiesty/Edgy/Dapper?

FWIW  these adapters will either work out of the box (but no light working) or will need ndiswrapper and configuration

Also, user "phossal" has a good howto on these adapters

[http://ubuntuforums.org/showthread.php?t=329299&highlight=netgear](http://ubuntuforums.org/showthread.php?t=329299&highlight=netgear)

---

### Post by Shyper on 2007-07-07
A ha!

Thanks a lot, Jose. That phossal tutorial really helped. It seems I had a V1 version of the card after all. What kind of stupid company...

Anyway, I'm on Linux now. This is great.

---

