---
title: "Wireless Phasing"
date: 2005-11-28
forum: Networking &amp; Wireless
---

### Post by Night on 2005-11-28
So my wireless internet is giving me a lot of headache. I set up ndiswrapper and it works fine right after boot up. It generally works fine for a while but then randomly stops connecting. After it goes down I look at gtkwifi and it tells me that their are no nearby wirless networks. Im not sure whats going on but this is the major thing stoping me from using linux. Also my windows boot works fine. Any help? If needed I can provide more details.

---

### Post by Lambert on 2005-11-28
What kind of wireless device are you using and what driver for it?

When the signal drops and you don't see anything in gtkwifi, open a terminal and type this command. 

iwlist <device> scan

where <device> = your device ath0, wlan0 ra0, etc0 etcc...

Also try it when you know you have a good signal and notice the difference. This is just to check if it's a gtkwifi problem or a device/driver problem.

---

### Post by Night on 2005-11-28
```
When Working:
Cell 01 - Address: 00:06:25:C6:26:22
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-66 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=3
          Cell 02 - Address: 00:09:5B:DC:FB:02
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-83 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1

Down:
wlan0     No scan results
```

Whats really odd is after it went down I did a "lsusb" and I get this:
Bus 004 Device 004: ID 13b1:000a (the usb wireless isnt showing up)
but it still showed up under gnome device manager.

---

