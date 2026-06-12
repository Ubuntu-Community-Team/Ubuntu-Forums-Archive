---
title: "wireless in an unfriendly world -hidden ssid's and too many ap's"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by awry on 2007-01-24
I have a ThinkPad T60p with the Intel ipw3945 wireless chipset.

It works fine for me at home, connecting to my neighbor's g network using WPA2.  There aren't many other networks around, so there's no real interference or anything in this environment.

My university, on the other hand, is a completely different story.  They are evidently clueless about wireless network design.

They have three networks going at once.  The first is a "legacy" network being phased out.  It is a b-only network with a hidden SSID and secured with WEP.  The next is an "Info" only network, which takes you to a page with instructions to get on the actual network.  Finally, the production network uses basic WEP with a hidden SSID, like the legacy network.  The two new networks are both abg.

With all of these networks, I've seen over 70 cells listed with iwlist scan in one room, distributed across every conceivable frequency.  The driver has a terrible time getting and staying associated with any of them, though the legacy b-only network seems to be the most reliable (but it's being phased out!).  

Sometimes NetworkManager works, other times I have to use my script around wireless-tools.  Usually neither works.  Often unloading and reloading the ipw and ieee drivers a couple times helps.

Is there anything I can do to improve this situation?  I've tried various versions of ipw and ieee to no avail.  Any good diagnostic tools people recommend?  I know the environment is horrible, but Windows and Mac people do seem to manage better and I'm taking flack from a couple windoze users in particular... "you're *still* not on the network? oh yeah, linucks, har har"

---

### Post by corax on 2007-01-24
Hi !

I'm not sure if this helps but when you get the list of APs you see the MAC addresses with ifwonfig you can give not just an ESSID but a MAC address too ... It is important because AFAIK your system tries to get the best connection for you and if you have many APs with the same ESSID the jumping begins :-) to get the best and it is hopeless because the parameters are changing all the time ...

so I think maybe this helps:

```
sudo iwconfig eth1 essid "networkessid" channel 11 key "WEPKEY" ap 00:11:22:33:44:55
```

of course replace with the correct parameters ;-)

good luck

---

### Post by awry on 2007-01-24
Yeah, I have a script that I use, where I attempt to keep track of the strongest ap in each room, and then uses the wireless-tools as you described.  This works with about a 35% success rate.

---

### Post by nalmeth on 2007-01-24
Tell them to F-OFF! :D
Being dorky about linux is one thing, being dorky about Windows is really lame.

Have you tried wifi-radar? I wonder what kind of results it would bring up for you.

I usually open wifi-radar, see what networks are available, and enter the information in System-Administration-Networking
For some reason, wifi-radar will never actually connect to the network (maybe it will for you), and network-manager doesn't work at all with wireless.

---

