---
title: "[Intrepid] Wireless working ... if I stop networking??? Help!"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by Roberto Rosselli on 2008-11-01
Hi all,
I just made a clean install with Ubuntu 8.10 and, like many other people, I'm having troubles with the wireless connection. It actually didn't work, or work sooooo slowly, until during my fiddling I typed
```
sudo /etc/init.d/networking stop
```
to see if stopping and restarting the network would produce some results. This produced an error message:
```
Ignoring unknown interface wlan0=wlan0.
```

After that, it mostly works: it sometimes stops, the wireless connections is lost, then picked up again, etc. Not perfect but bearable for the moment.

Anybody's got an idea why this happens??? And what happened to the old network-configuration software?

RR

---

### Post by Roberto Rosselli on 2008-11-02
Sigh ... can someone at least tell me how to disable wlan0?

---

### Post by glinsvad on 2008-11-06
I'm having the exact same problems. Well, it's even worse because since I'm on a WPA encrypted net and the authentication freezes for about 30 s every time.

I'm pretty sure this is confined to NM version 0.7 (Intrepid) since these problems weren't present in version 0.6.6-0ubuntu5 (Hardy). I'm also quite confident in saying that version 0.7 wasn't quite release-worthy as of last week, especially judging by the number of open high-priority bug reports related to NM v0.7 in Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/network-manager]("https://bugs.launchpad.net/ubuntu/+source/network-manager")

The good news is that these issues are getting a lot of attention by the developers, so hopefully bugfixes will trickle down in a matter of days/weeks...

---

### Post by MockY on 2008-11-06
> **Roberto Rosselli said:**
> Sigh ... can someone at least tell me how to disable wlan0?

```
sudo ifconfig wlan0 down
```

---

