---
title: "WIreshark - how do I turn my wireless card into monitor mode?"
date: 2014-10-17
forum: Networking &amp; Wireless
---

### Post by ascendingphoenix on 2014-10-17
Hiya, just recently got Ubuntu and I want to be able to monitor all traffic using Wireshark - I know that you need to turn the wireless card into monitor mode but I'm not sure how.

How do I make this work? I'm hoping that it's just as simple as turning monitor mode on and then scanning with Wireshark.

My wireless card is a Atheros AR928X.

I'm totally new to Linux (got Ubuntu a few days ago) but will learn whatever. =)

---

### Post by chili555 on 2014-10-17
I suggest you click the Network Manager icon and ask to disconnect from your current access point. Open a terminal and do:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
```To connect again:```
sudo iwconfig wlan0 mode managed
```And then ask Network Manager to connect to your access point.

Not every device and driver combination do monitor mode. I don't know about your Atheros.

---

### Post by ascendingphoenix on 2014-10-17
Thanks a lot.

I've read that this card can do monitor mode with the right drivers, but there's still more than turning on monitor mode to getting it right it seems...

Yay learning! =)

---

