---
title: "BCM43142 can't see networks above channel 11"
date: 2016-02-17
forum: Networking &amp; Wireless
---

### Post by afccarl1994 on 2016-02-17
Hi guys,

Today I came home to find the router in my student house has been upgraded. Everything seemed great, until I tried to connect to the network on my laptop, which couldn't see the network at all. I have since found out that the network is currently broadcasting on channel 13, which is what is causing the problem.

To begin with, the country code was set to 00, and dmesg was reporting that it was being set every few seconds. I have since managed to get this set to the correct country code (GB). The output of a few commands can be seen below.

```
iw reg get
country GB: DFS-ETSI
... (everything else matches the laptop I am using to type this, which is able to connect)
```

```
sudo cat /sys/module/cfg80211/parameters/ieee80211_regdom
GB
```

```
crda
COUNTRY environment variable not set
```

I've also attached the output of the wireless info script. I'm using the iw driver, which I believe is the only one that works with this card. Windows is able to connect, so the card is capable of using this channel.

Despite making the changes to the region code above, it is still unable to see the access point. Any ideas?

---

### Post by jeremy31 on 2016-02-17
post ```
cat /etc/default/crda
```

You should not need ```
iw reg set GB
``` in /etc/rc.local[/code]

---

### Post by afccarl1994 on 2016-02-17
> **jeremy31 said:**
> 
You should not need ```
iw reg set GB
``` in /etc/rc.local[/code]

I no longer have that in rc.local, I just hadn't removed it when I ran the script. I've re-ran the script and uploaded an up to date log.

```
cat /etc/default/crda
REGDOMAIN=GB
```

---

### Post by afccarl1994 on 2016-02-28
I've since purchased an Atheros AR9382 card as a replacement. Not only does this support channels above 11, but it also has a 5GHz band. Best of all, it works out of the box (Ubuntu 15.10).

---

