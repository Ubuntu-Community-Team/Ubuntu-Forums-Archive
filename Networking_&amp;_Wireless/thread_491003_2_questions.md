---
title: "2 questions"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by Bert Mariën on 2007-07-03
I have a D-Link AirPlus G+ DWL-G520+ Wireless PCI Adapter which works fine on Ubuntu 7.04.

1ste question: Does anyone know where to find that driver in Ubuntu and where it is at? And how can I intall that driver in other distro's?

2nd question: where can I find a list of supported wireless cards supported on almost any Linux distro, so I can buy a card that is globbaly recognized.

Thanks.

Bert.

---

### Post by spd106 on 2007-07-03
With this command you can see the driver being used.
```
sudo lshw -class network
```

It's likely that you have the [acx100]("https://help.ubuntu.com/community/WifiDocs/Driver/acx100") or [acx111]("https://help.ubuntu.com/community/WifiDocs/Driver/acx111"). I believe this driver's homepage is located at [http://acx100.sourceforge.net/wiki/Main_Page](http://acx100.sourceforge.net/wiki/Main_Page)

---

### Post by Bert Mariën on 2007-07-03
Thank you spd106

---

