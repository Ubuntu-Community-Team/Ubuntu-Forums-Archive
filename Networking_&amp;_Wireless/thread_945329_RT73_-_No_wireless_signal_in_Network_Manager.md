---
title: "RT73 - No wireless signal in Network Manager"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by sh_son on 2008-10-12
Hi,

I have replaced DWL-G122(C1) with DWA-110(A1) as my wireless router on third floor did not reach (signal) my DWL-G122 on first floor. Though, they are all manufactured by D-Link and both use G band, same chipset RT2571WF, DWA-110 catches 40% more signal than DWL-G122, I don't know why, especially since I updated to latest driver. (XP, I'm talking about)

Now back to Ubuntu; I re-installed Ubuntu 8.04/Hardy on 16GB memory stick rather than 40GB 1.8" HDD, and it works great!

Btw, I got my DWA-110 working with this '**rt73.k2wrlz-3.0.1.tar.bz2**' driver module to use with aireplay-ng, however I can see wireless networks (in managed mode) but without signal strength. - When I click on them and it asks for WPA-PSK and I type my key and does not connect. It does same for WEP key.

Can anyone help me solve this problem? Thanks. :)

---

### Post by Sava8420 on 2008-10-12
Open terminal and run:
```
sudo iwlist wlan0 scan
```
Post results and can help you get connected.

---

