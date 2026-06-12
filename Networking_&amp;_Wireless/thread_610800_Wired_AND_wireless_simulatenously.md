---
title: "Wired AND wireless simulatenously?"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by Isaacariah on 2007-11-12
Right

My workstation is connected to two networks, one wired, one wirelessly, as I need to RDP to machines on both networks. When I was using Windows, I simply plugged in my ethernet cable and configured the IP settings fine, and for the wireless I entered the SSID, passkey and IP settings, and it connected to both, enabling me to connect to machines on both networks fine.

From Ubuntu, I cant seem to connect to both at the same time, if I try and connect to the wireless, it disconnects the wired, and vice versa.

How can I obtain the same setup I had in Windows whereby both are connected and useable at the same time?

(Also, in the network manager, It gives me two wireless adapters, wlan0 and wmaster0, wmaster0 doesnt seem to do anything)

Thanks
Isaac

---

### Post by weblordpepe on 2007-11-13
Bump.

I would like to know this too.

Perhaps you could use the GUI to connect to the WIFI, and then use the command-line to bring up the wired network?
Mebbbee?

---

### Post by Isaacariah on 2007-11-13
I tried stopping the Network Manager and bringing both interfaces up with /etc/network/interfaces and ifconfig, but after doing this, although ifconfig showed both interfaces were connected, none of my internet programs worked.

Very confusing.

---

### Post by ImNeat on 2007-11-15
Perhaps try installing wireless_tools and dhcpcd, then:

```
dhcpcd -d [wired_interface] #dhcp request on wired connection

iwconfig [wireless_interface] essid [wireless_ssid] #configure wireless settings

dhcpcd -d [wireless_interface] #dhcp request on wireless connection

ifconfig #list status of wireless devices
```

---

