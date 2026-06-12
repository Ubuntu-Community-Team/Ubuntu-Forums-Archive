---
title: "PCI Wireless card CWP-854 on Ubuntu 7.10"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by arnaudus on 2007-11-19
Hi all, 

Sorry for this post, "my wireless card does not work" thing is probably boring...

So, here we are, my wireless card does not work. It's a CNet CWP-854 (chipset RaLink, PCI). According to the Ubuntu Wiki: Works out of the box. Too bad, not for me. 
```

> lsmod |grep RaLink
07:09.0 Network Controller: RaLink RT2561/RT61 802.11g PCI 
```

(sorry for the potential typos, since I write from another computer, no copy and paste...)

Three constraints: 1) wireless in my only way to connect the Internet (otherwise, I have to download things on another computer and transfer them with a memory stick). 2) I don't have any access to the router (WPA Enterprise identification, with ID + password) 3) the PC is Linux-only, and I have no way to pick up the Windows drivers for ndiswrapper.

First install: Ubuntu 7.4 (AMD64). The card is detected, but only WEP available from the gnome-network applet.
Second install: Ubuntu 7.10 (AMD64). The card is detected, WEP + WAP personal available, but the gnome-network applet is VERY unstable (crashes after the first click). System -> Administration -> Network -> Wireless connection works perfectly, but unfortunately, no "WPA Enterprise" thing (and thus: no login/password). Seems like I have to fix that by hand.

```
> less /etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-essid "uio"
wpa-ssid "arnaudl"
wpa-psk 6479...
```

I know everythink is not OK (there are "wpa-proto" etc. things to set up, but that's not what worries me for the moment)

```
> sudo /etc/init.d/networking restart
[I copy only error messages]
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
[...]
ioctl[SIOCSIWAUTH]: Operation not supported
[...]
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
[...]
No DHCPOFFERS recieved
```

Here I'm more worried: this wmaster0 errors don't look nice, do they?

According to lsmod, the driver seems to be rt2x00pci. 

And here are the features of the network:

```
> iwlist wlan0 scan
Cell 01 - Address: 00:15:C7:28:12:B0
              ESSID:"uio"
              Mode:Master
              Channel:5
              Frequency:2.432 GHz
              Signal level=-76 dBm
              Encryption key:on
              IE: WPA Version 1
                    Group Cipher: none TKIP
                    Pairwise Ciphers (1) : WEP-40
                    Authentification Suites (1) : 802.1x
              Bit Rates: 1Mb/s [...]
              Extra:tsf=000001963 [...]
```

Any idea? Are these "wmaster0" things very bad? My concern is that I don't know if WPA enterprise is supported by this new rt2x00 driver, so I don't want to spend days in fixing a problem I can't fix. Should I order another card? Thanks for sharing your experience. 

Arnaud.

---

### Post by arnaudus on 2007-11-20
OK, I reply to myself.

I fixed the issue in a dirty way: the wireless card is very well supported with the regular 32bit Ubuntu 7.10; so I had to install it. If someone has some experience in bug reporting to Ubuntu, it might be useful to let the devs know this issue --does it come directly from the driver? Is it compiled properly under 64 bits architectures?

A.

---

