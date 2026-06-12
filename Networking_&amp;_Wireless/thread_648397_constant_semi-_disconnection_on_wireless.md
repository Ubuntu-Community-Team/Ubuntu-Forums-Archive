---
title: "constant semi- disconnection on wireless"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by tiachopvutru on 2007-12-23
I'm having trouble with wireless on my desktop with Ubuntu Gutsy Gibbon on. At times, the Internet connection would randomly drops off and the only way to solve it was (at least, the only way I know, which doesn't cover a lot after all) a reboot. My wireless adapter is an USB Dongle, Netgear WG111T. I run it through ndiswrapper, uninstalled network-manager and network-manager-gnome since I had the same problems using them as well, and connected through the manual way.

Anyway, here's my */etc/network/interfaces* file:
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
wireless-essid Essid
wireless-key 26_keys open
wireless-mode managed
address 192.168.0.102
netmask 255.255.255.0
gateway 192.168.0.1
```

It connects fine, but after a while, the connection drops off, kinda at least. What happen is that, when I get disconnect, I notice ***iwlist scan*** returns me with *No Scan Results*, but iwconfig still show itself connected to the essid. So then, if I try ***sudo /etc/init.d/networking restart***, I'd get this:

```
 * Reconfiguring network interfaces...                                          
RTNETLINK answers: No such process
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
                                                                         [ OK ]
```

I don't remember if the RTNETLINK line still appear anymore, so it may or may not be best to ignore that line. In any case, this happens often to the point of annoyance. I hope someone could help :)

When I restart, it automatically works without me having to do ***sudo dhclient wlan0*** (although I still have to do that sometime). So I suspect i tmay have more to do with the device or something like that, but I'm pretty much a noob so I don't know. :)

---

### Post by johnnywellas on 2008-01-12
Man, I'm having exactly the same issue, point by point: fixed ip, unistalled the network managers (thought that they could be the origin of this issue), manually wrote down the interface's configuration on the /etc/network/interfaces file.
It ALWAYS disconnects, sooner or later!! :confused: I'm using a SMC usb adapter with ndiswrapper, it has the conexant cohiba chipset.
From the symptoms, I suppose that it's the system that loses the hang of the driver or something. I get exactly the same error message as you do, the "Set failed..." thing.
Then i reboot and everything is ok again. So, no p2p for me, I'm really thinking about buying a few feet of UTP cable and wiring the connection to the router downstairs... :mad:

Can anybody help us out on this? I'm literally growing slightly mad.

Thanks!

(EDIT: typos)

---

### Post by johnnywellas on 2008-01-24
Anyone?

---

### Post by thantos on 2008-01-25
Try this and see if it works:

make a script that looks like this (not sure about first line, but everything else is good)
```

#! /bin/bash

# This is to keep a connection going constantly with the router
# -s is the size (1 = 9 bytes)
# -i is the interval (in seconds), anything less than 300 should work
# insert your gateway ip address at [COLOR="Red"][gateway ip][/COLOR]
ping -s 1 -i 290 [COLOR="Red"][gateway ip][/COLOR]

```

then save it.

Now go to System -> Preferences -> Sessions
Go to the "Startup Programs" tab and click "Add"

Name it whatever you want (I use "Wireless Network workaround")
and have it point to the script you just made.

This may solve your problem.  If you want to test that this is your problem,
do not surf the internet and open a terminal and type:
```

ping -s 1 -i 1000 google.com

```

and wait to see if the second ping comes back with the "Destination Host Unreachable".

I think this is a problem with how WPA and WPA2 work, but not sure.

I hope this works:).

---

