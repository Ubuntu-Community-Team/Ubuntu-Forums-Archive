---
title: "Ndiswrapper + feisty = trouble?"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by piccia on 2007-03-10
Hello everyone.
Up to few hours ago I had a perfectly working Edgy with a DLink D520+ wireless card configured with ndiswrapper for WPA access. This afternoon I updated my ubuntu to Feisty (I like living on the edge :)) but the wireless connection doesn't work anymore, since no wlan0 interface is detected. 

Facts:

* under edgy everything worked fine

* after switching to feisty I initially had a problem since the acx driver was loaded instead of ndiswrapper. I solved the problem blacklisting acx in /etc/modprobes.d/blacklist

* the firmware is correctly installed:
```

Installed drivers:
gplus           driver installed, hardware present 

```
* aliases are properly defined (with ndiswrapper -m)

* interface configuration is ok (it works under Edgy):
```

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid XXXXXXXX
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-psk XXXXXXXX

```
* ndiswrapper module loads, but doesn't detect the wireless card
```

[   43.000470] ndiswrapper version 1.30 loaded (preempt=no,smp=yes)
[   43.027043] usbcore: registered new interface driver ndiswrapper

```
(ifconfig / iwconfig don't show any wlan0 card)

* I tried with the last version of ndiswrapper, 1.38, without success

* If I boot feisty with the old edgy 2.6.17 kernel the network WORKS fine! (but I want to use the new kernel)


Anyone has the same problem? (seems not, after a quick search on the forum).
Should I report it as a bug?

Thanks for any hint :)

---

### Post by teaker1s on 2007-03-10
install "ndiswrapper-utils-1.8"

---

### Post by piccia on 2007-03-11
> **teaker1s said:**
> install "ndiswrapper-utils-1.8"

actually it was already installed.
But I needed ndiswrapper-utils-1.9 :)
Now everything works fine! Thanks a lot.

---

