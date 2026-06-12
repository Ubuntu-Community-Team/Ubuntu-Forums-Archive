---
title: "Wireless NIC Settings and NDISWrapper Settings didn't &quot;take&quot;"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by Stervyatnik on 2008-08-03
Hello, all!

Yesterday, I proudly installed and configured two TrendNet TEW-423PI Wirelkess Adapters in two Ubuntu 7.04 computers, and installed drivers IAW NDISWrapper instructions. At the end of the day, I had two computers running wireless connections to my DSL, and I was supremely happy. At the end of the day, I shut down.

This morning, I fired up my computers, and no wireless networking. I did "ifconfig," and it doesn't see the Wireless NICs on either computer. I click the network icon, and there are no options for wireless networks. I installed WICD, and nothing. I tried to "sudo /etc/init.d/networking restart" but to no avail. I lloked at "System > Administration > Windows Wireless Drivers," and it looks like there is a driver in place, but it also looks like it isn't seeing any Wireless NIC.

It's as if all my hard work simply vanished.

Anybody know what went on? Is there a "save" option I need to do so it will save the configurations? Or do I need to re-do the NDISWrapper setup? If this is something I need to do each and every time, why? Is there a config file I should edit, so it will automagically reconnect to the wireless when I boot up?

Any help would be greatly appreciated. I can also supply additional details if needed. Thanks in advance!

Dan sends...

---

### Post by Stervyatnik on 2008-08-03
If I reboot, and then from the command line, do the following:

[INDENT]sudo depmod -a <ENTER>
sudo modprobe ndiswrapper <ENTER>[/INDENT]

This apparently "reinitializes" the wireless NIC, and then it automatically reconnects to my default wireless network, (my home DSL).

Still would like an automatic way to do this whenever it's booted up.

Thanks again for any help!

Dan sends...

---

### Post by caljohnsmith on 2008-08-04
I believe all you have to do to get ndiswrapper to load automatically is:
```
sudo ndiswrapper -m
```
What that actually does is load ndiswrapper (if it's not all ready loaded) whenever the interface wlan0 is used (i.e. your wireless connection). If for some reason that doesn't work, you can always add ndiswrapper to your /etc/modules file. Just add "ndiswrapper" to the end of that file.

---

