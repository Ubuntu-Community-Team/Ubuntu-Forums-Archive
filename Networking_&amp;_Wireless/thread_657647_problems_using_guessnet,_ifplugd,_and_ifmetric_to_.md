---
title: "problems using guessnet, ifplugd, and ifmetric to automatically configure the network"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by rrwo on 2008-01-03
I've managed to get ifupdown mostly working with guessnet, wpa_supplicant, and ifplugd so that when my network devices automatically configure themselves when they are plugged in, unplugged or turned on/off (in the case of wifi). [I'm using Gutsy by the way.] Sweet, except:

1. When I resume, the wireless network is not up. If I restart ifplugd or toggle the physical switch (my ThinkPad has a switch to turn wireless off/on), it comes on. (I could just remember to wake the ocmputer up with the switch off and manually turn it on, but this seems silly.)

2. ifmetric doesn't work when called on an up or post-up command in the /etc/network/interfaces.  When I check the ip route list, the metrics are unaffected.  I can manually run it, and it's changed.  I can also add it after the ifup line to /etc/ifupd/actiond.d/ifupdown, but I'd rather put it in the appropriate scripts.  Has anyone gotten this working? (I don't mean just putting it in the script, but actually looked at the metrics values!)

CAVEAT: I don't return to work until next week, so I could find new problems.... ;)

---

### Post by rrwo on 2008-01-08
I fixed the problem with ifmetric by not using it.

Instead, I use the "metric" keyword in my interfaces file, e.g.
```
iface lan-home inet dhcp
  test peer address  192.168.0.1  mac 01:23:45:67:89:AB
  metric 1
  post-up /etc/network/guessnet-scripts/home

iface wpa-home inet dhcp
  test wireless mac 01:23:45:67:89:AB essid HomeNetSSID
  metric 10
  post-up /etc/network/guessnet-scripts/home

```

---

### Post by rrwo on 2008-01-11
For the first problem, I now have the opposite: the network is ok when I resume, but when I boot, the wireless needs to be started manually using ipup.

---

