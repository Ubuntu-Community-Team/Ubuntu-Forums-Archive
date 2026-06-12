---
title: "Wireless networking NOK after upgrade"
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by Reginald Overdose on 2006-10-05
Linux newby, installed ubuntu 6.06 LTS from a live CD, set up wireless network OK and intalled all available upgrades. Running the 2.6.15-27-386 kernel networking now does not appear to work anymore. I cannot ping my router, although Network settings says that wlan0 is active ; re-entered SSID and WEP key for my LAN but to no avail.

Things are still OK when running the 2.6.15-25-386 kernel as originally installed.

I have an Intel PII mobile (Dell Inspiron 7000) and connect to LAN with a Mercury Wireless-G PCMCIA card.

Any ideas ?

---

### Post by Reginald Overdose on 2006-10-09
OK I fixed this as follows :
1. Remove cloth from between ears.
2. Apply determination as detailed below.

I found out my network card is based on a Texas Instruments ACX 111 54Mbps Wireless Interface.

```
lspci
```

then stumbled across the following link :

[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/45162/](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/45162/)

not understanding the half of it (cloth very tenacious) I decide to go for :

```
sudo
cp /lib/firmware/$(uname -r)/acx/1.2.1.34/* /lib/firmware/$(uname -r)/acx/default
```

Although I have a nagging feeling that this might not be the _proper_ way of fixing it. But it works, what the heck.

---

