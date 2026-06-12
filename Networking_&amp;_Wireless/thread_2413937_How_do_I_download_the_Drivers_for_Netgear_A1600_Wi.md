---
title: "How do I download the Drivers for Netgear A1600 WiFi Adapter?"
date: 2019-03-04
forum: Networking &amp; Wireless
---

### Post by jjm00ey on 2019-03-04
I’ve never used Ubuntu before, only windows. Is there a way for me to download the drivers for my WiFi adapter to a USB flash drive, & then to my computer? How would I do so? I’ve never used the terminal either..

---

### Post by kc1di on 2019-03-04
Hello jjm00ey and Welcome to Ubuntu Forums, 

That device may be hard to install on linux, here is [a page]("https://marcnu.github.io/2016-09-10/How-to-install-Netgear-A6100-USB-Wifi-adapter-on-Ubuntu-16.04/") that may help but it's quite involved.  You will have to build the driver for that stick,  My advise would be to find a  different usb dongle that is better supported by linux.  Some are listed[ here]("https://www.wirelesshack.org/top-linux-compatible-usb-wireless-adapters.html").

---

### Post by praseodym on 2019-03-04
Do you have the possibility to temporarily connect via cable? If yes, run
```

sudo apt-get install rtl8812au-dkms
```

---

