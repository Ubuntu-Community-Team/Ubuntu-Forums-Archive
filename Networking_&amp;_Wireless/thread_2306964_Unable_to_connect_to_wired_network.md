---
title: "Unable to connect to wired network"
date: 2015-12-20
forum: Networking &amp; Wireless
---

### Post by mitchell21 on 2015-12-20
Hello,
I am running a fresh installation of Ubuntu 14.04 LTS on my custom built computer, and I am having some issues with connecting to the internet. My computer will try to connect, but it will display a popup that says "network disconnected. You are now offline" few seconds later. My specs are:

AMD FX 8350 processor
Gigabyte 990-FXA-UD3 ATX motherboard
NVIDIA GeForce GTX 960 graphics card
Samsung 850 evo 500 gb ssd
16gb Ballistix sport RAM (Frequency: 1866)
Rosewill Blackhawk case

---

### Post by praseodym on 2015-12-21
Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsmod
cat /etc/resolv.conf
route -n
cat /etc/network/interfaces
```
Does wireless work?

---

