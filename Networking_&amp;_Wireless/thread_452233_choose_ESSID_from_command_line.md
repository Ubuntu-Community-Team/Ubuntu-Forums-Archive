---
title: "choose ESSID from command line"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by Zed on 2007-05-23
Following the WPA Howto in this forum, I quickly got my laptop with ipw3945-driven wifi talking to my hidden-ESSID WPA2-PSK wifi router, and I was very happy.

Then I realized I'd just locked myself into one set of settings, and that it wouldn't work with my employer's network, in public hotspots, or anywhere else.

When I'm not telling the laptop to connect to a specific known ESSID, I want to see a list of ESSIDs, and then be able to tell it to connect to one of those. I don't want it to ever connect on its own just because it found something. (I realize there might be times when I'm knocked off the net that could have been avoided if I'd let it reconnect on its own. I can live with that.)

I don't have ubuntu-desktop or the other -desktop packages installed, so I don't have a GUI front end for NetworkManager. I'd like to keep it this way.

How could I do this? Can it be done with wpa_supplicant alone? Can it be done with NetworkManager driven from the command line?

---

### Post by tturrisi on 2007-05-23
iwlist eth0 (eth1, ath0, wlan0, etc) scan

---

### Post by Zed on 2007-05-24
That gets me the list, but is there a way to configure everything about my WPA-PSK home system somewhere such that I can tell my interface to use that info when connecting to that one, and not to use it when connecting to something else?

---

### Post by jfinkels on 2007-05-24
> **Zed said:**
> That gets me the list, but is there a way to configure everything about my WPA-PSK home system somewhere such that I can tell my interface to use that info when connecting to that one, and not to use it when connecting to something else?

You can read a little bit about ifconfig with 
```
man ifconfig
```
and also
```
man iwconfig
```
They will each let you set several configuration options at once. Then I suppose you could write a script to connect to a specific network using a specific set of options (although I'm not sure if these have exactly what you need). Good luck!

---

