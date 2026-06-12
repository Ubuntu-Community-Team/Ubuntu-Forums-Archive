---
title: "Cannot connect public hotspots with temporary key"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by bajun on 2008-11-10
Hello!

Public hotspots, called BlueSpots in Germany, in despite of the fact, that they have no encryption, want a temporary access key, that should ordered by SMS on demand.

Avtually, I have no problems by establishing a connection to encrypted wlan network on the standard ubuntu way.
If the network have no encryption and no key, I can simply leave key field in gnome-network-manager empty.
My wlan card works through ndiswrapper.

But I cannot connect BlueSpots.

In gnome-network-manager, if I set a key, there is no possibility to use "without encryption" mode.

If I use command line:
```
sudo iwconfig wlan0 essid "BlueSpot-kostenlos" key off mode auto
```
```
sudo iwconfig wlan0 key s:1761
```
```
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.

```

What's wrong with this?

---

