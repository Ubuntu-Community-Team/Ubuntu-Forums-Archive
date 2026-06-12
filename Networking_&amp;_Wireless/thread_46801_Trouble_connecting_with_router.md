---
title: "Trouble connecting with router"
date: 2005-07-06
forum: Networking &amp; Wireless
---

### Post by topoftheworld on 2005-07-06
my router has dhcp, it was working perfectly on my computer with windows XP, and currently works fine with other computers on the network running windows.

when I try to use DHCP under ubuntu, it dosn't work. I have tried using dhclient, most of the time there is no response from the router, and SOMETIMES theres a response, like this:

DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 16
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
.. (repeats that for like  7 times)
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67

etc.. etc..


when I am trying to ping the router (192.168.0.1) under DHCP, it says "connect: Network is unreachable"

now, when I declare a static IP, subnet, and gateway and DNS, I can ping the router, but the ping times are like in the thousands, and most of the time don't even respond. 

please help?! I posted before, but I think I wasn't descriptive enough or something...

---

### Post by intangible on 2005-07-06
I'm assuming this is a wireless problem, because a wired lan should never cause problems like this.

Try changing the SSID of the router back to the default and making it broadcast and see if your problems go away.  I had a problem once where my linksys router was using its default SSID instead of the configured one (but it was working fine on windows?)  I enabled broadcast and then I was able to make the configured SSID stick.  Also, try changing the wireless channel in the router to something else.

One last problem I've seen, if it's a certain linksys, you sometimes have to tell it to only use one antenae to get any decent ping times from it, only saw that once.

---

### Post by topoftheworld on 2005-07-06
it's wired :(


netgear router. i am connecting first to a switch, if that makes any difference.

---

### Post by intangible on 2005-07-07
Ouch, that's gonna be a bit harder to troubleshoot, because with wired we know it's not a bad connection to the router, because we are physically connected.

Perhaps try a new firmware update from Linksys?  I had a few problems solved by thier firmware updates before.

What model is the router?

---

### Post by topoftheworld on 2005-07-07
thanks for responding  :smile: 

router is a netgear wgt624
current firmware  :-x

---

### Post by intangible on 2005-07-07
Silly me, assuming it was a linksys, sry bout that :D

Anyway, it's trying to get an address for "lo" first?  lo shouldn't try to get a dhcp address.  Sounds like you may be getting a route or a bridged route setup through the loopback device.

Your **/etc/network/interfaces** should look like this (ignoring comments):
```
auto lo

iface lo inet loopback

mapping hotplug
        script grep
        map eth0

iface eth0 inet dhcp

auto eth0

```

Hope this gets you going.

---

### Post by topoftheworld on 2005-07-08
hmm, well, i installed mandrake 10.1 and it seems to work fine.

if i try out ubuntu again i'll make sure that that's what the file looks like.

thanks for replying

---

