---
title: "Can't find the wireless AP anymore"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by dev.urandom on 2008-11-01
Something strange is happening. Ubuntu can't find the wireless AP in the dorm. After it was shut down due to a fire alarm (which happens often), the wireless is not visible in the network manager list. However, I can see and connect to it if I boot into Vista.

Besides trying with network manager, I also tried using iwconfig to connect to it, like this:

iwconfig wlan0 essid "Foyer" # the Foyer essid hasn't changed, according to Vista
dhclient wlan0

The dhclient did not return an IP though.

iwlist wlan0 scan also didn't return my AP.

I also tried using an 8.10 live usb, which also couldn't list the networks. On both HH (my install) and 8.10 I can see all kinds of other networks, but not the one I'm supposed to connect to. And that was the only unsecured one out there as well.

If it matters, I have the intel 4965 wireless.

---

