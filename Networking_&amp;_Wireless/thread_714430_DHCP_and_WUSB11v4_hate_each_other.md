---
title: "DHCP and WUSB11v4 hate each other"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by SZF2001 on 2008-03-03
Here's the thing - the card will send out signal and see other networks, but won't connect to any of them with Network Manager's roaming mode, or whatever.

Wifi-radar doesn't seem to help. It sees them, tries to connect and can never grab an IP if it has to do with DCHP.

So now if I ever boot up I have to run these terminal commands:

```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo ifconfig wlan0 essid frankzappa key ****-****-** mode Managed rate auto
sudo dhclient wlan0
```

The asterisks (*) being my code, mind you.

It always seems to work after running the dhclient. Perhaps there is a script I can use or something? Ugh. Network Manager seems to be crap and the 'if' commands... I don't remember them much.

---

