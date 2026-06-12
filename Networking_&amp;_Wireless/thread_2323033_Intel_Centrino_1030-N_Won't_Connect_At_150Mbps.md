---
title: "Intel Centrino 1030-N Won't Connect At 150Mbps"
date: 2016-05-02
forum: Networking &amp; Wireless
---

### Post by Elliot_Berg on 2016-05-02
Hi,

I've got an intel centrino-N 1030, and can't seem to get it to connect to any wireless network at more than 72Mbps. Other devices on the same routers can connect at 130/144/150 on 2.4GHz without trouble, but this won't seem to. I've tried adding options iwlwifi 11n_disable=8 to /etc/modprobe.d/iwlwifi.conf, but it hasn't helped - with and without I get the same reported speed from iwconfig, and the same speed for transfers. It's a bit frustrating, as I've got 100Mbps internet, but can't get above about 30Mbps on this laptop - despite being able to get over 50Mbps on others attached to 2.4GHz, and local networking is suffering too.

Any and all help appreciated!

UPDATE: I've managed to find a spare hard disk and get Windows 10 installed and running on this laptop - it behaves the same, until I set the channel width to Auto (it defaults to 20MHz), at which point it connects at 144Mbps and gets ~95Mbps download speeds, which is what I want under Ubuntu! Does anyone know how I can do this under Ubuntu? The router only allows 20MHz or 20/40MHz, you can't force it to 40MHz.

---

### Post by Elliot_Berg on 2016-05-11
I eventually upgraded my kernel to 4.4.8, and now it's vastly improved. iwconfig doesn't report the correct speed, but I get the real throughput, so it doesn't really matter!

---

### Post by jeremy31 on 2016-05-11
What version of Ubuntu are you using?
Using an upstream kernel isn't advised here as Ubuntu kernel updates won't work in many cases

---

