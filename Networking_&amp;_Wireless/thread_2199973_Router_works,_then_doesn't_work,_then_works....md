---
title: "Router works, then doesn't work, then works..."
date: 2014-01-16
forum: Networking &amp; Wireless
---

### Post by Old Newville on 2014-01-16
Hello,

We have five devices on our home network. A Dell desktop (Ubuntu 12.04 LTS) is connected to a router by wire, and three laptops (Windows 7, 8 and Ubuntu 12.04 LTS) and a wireless Sony Bluray player. The router is a Cisco Linksys E900.

Our internet connection for the Dell is solid and reliable and we never have any problems with it. 

However, the connection for the wireless devices seems to come and go as it pleases. Some days there are no problems and other days it takes hours to connect. I just spent about two hours fiddling with the Ubuntu laptop before it just decided to connect. In every case, the radio indicator on the panels show a strong signal, but there is no internet, even while I'm using the Dell to surf. Then it shows up for maybe a minute, then goes, and comes back.

I plugged the Ubuntu laptop into the router by wire, and the connection popped on instantly, and I was able to browse in Firefox. When I unplugged it, the laptop went back to on off, on off.

I bought the E900 because it had a higher bandwidth capacity than our previous router, and it worked for the past year with no problems, until a few weeks ago. I honestly don't know what happened to change this.

I need to fix this once and for all, and would appreciate any suggestions about what to look for.

I checked the IP addresses of all the devices, and they are all different.

---

### Post by tgalati4 on 2014-01-16
Open up the router and put your finger on the wireless chip.  If you can't keep your finger on it for 30 seconds then you have found your problem.  Also check the capacitors. Look for leaking or bulging capacitors.  If the wireless chip is a card in a slot, then reseat the card.

It could also be wireless interference.  Do you think your neighbors got tablets for Christmas?

---

### Post by Zhivargo on 2014-01-20
why do you think the router is faulty tgalati4? OP said it was working fine!

no your problem is def your wlan settings. Start with the Ubuntu laptop. 

```

ifconfig -a
iwconfig
lsmod
lspci
iwlist wlan0 scan

```

---

### Post by Iowan on 2014-01-20
@Zhivargo
> **Old Newville said:**
> 
However, the connection for the wireless devices seems to come and go as it pleases.
All 5 devices have the same config issue?

---

### Post by Old Newville on 2014-02-16
I ended up giving two devices -- the printer and the desktop -- fixed IP addresses, and the problem has improved.

I'm not marking this as solved until I've seen consistent performance over a longer period of time.

We have a neighboring house about 100 feet away, but their router signal is pretty weak at my house. 

I also don't think its the router overheating, but the replies here have given me something to think about, though. We live in the country and an electric fence comes to within about 30 feet of our house. With two feet of snow on the ground, the lower wires are submerged, so the whole system is probably shorting. I can hear it humming at one of the corner posts. 

This has given our digitial TV reception some fits at times in the past, but I never thought about the possibility of interference with the router signal. 

The fence also shorts when it rains, especially when the grass has grown tall. So its probably subject to shorting most of the time. Sometimes at night you can see the arcs!

Thanks everyone for your replies.

---

### Post by Old Newville on 2014-02-16
Iowan,

The desktop is connected by wire and works nonstop, even when the wireless isn't working. I was thinking about running a wire to my bluray player to keep it connected more consistently.

Thanks!

---

### Post by Easy Limits on 2014-02-16
The first thing I would do is change the channel for the WiFi in the router.

---

