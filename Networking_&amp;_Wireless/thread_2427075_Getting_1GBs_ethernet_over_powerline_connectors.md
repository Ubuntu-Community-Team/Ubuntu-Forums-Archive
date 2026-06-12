---
title: "Getting 1GB/s ethernet over powerline connectors"
date: 2019-09-17
forum: Networking &amp; Wireless
---

### Post by tornadof3 on 2019-09-17
My router and motherboard support 1gb/s connections and I've just checked I'm using CAT5e cables out of my computer and into a TP link powerline adapter (like this: [https://www.tp-link.com/uk/home-networking/powerline/tl-pa4010-kit/](https://www.tp-link.com/uk/home-networking/powerline/tl-pa4010-kit/) ), and from the adapter the other end into the router. This connection is running at 100Mb/s.
I note from the text of the hyperlink that it says 100MBps on the manufacturer's website, but then the photo of the box clearly says 600MBps and the model number is AV600. When I changed the connection speed manually by editing the network settings for "Wired Connection 1" to 1Gbps it wouldn't connect, so my quest is to discover the reason *why* it wouldn't connect as I don't know much about these powerline adapters; my two queries:

1. Is 600Mbps even a possible connection speed - i.e. does it have to be the discrete 10/100/1000MBps rather than the obscure 600Mbps? 
2. If 1) is "yes, it is possible", has anyone achieved 1Gbps or anything > 100Mbps with these powerline adapters?
3. If 1 and 2 are "yes", does anyone know if this particular model will do 600Mbps?

Any help or guidance appreciated.

---

### Post by Dennis N on 2019-09-17
1 Gb (gigabit) ethernet (= 1000 Mb) max theoretical transfer speed = about 125 MB/sec. So you can't get 600 MB/sec; must be a misprint on that box. 

Depending on the physical layout (distance traveled and electrical circuits traversed), you only get a fraction of the rated speed with powerline network. I'm using a rather old  D-link unit rated at 100 Mbps, but the actual real speed on download is around 50 Mbps or 5 to 6 MBps. But it's very reliable (never has disconnected on me) and consistent speed. Beats wi-fi.

---

### Post by chili555 on 2019-09-17
It appears that the devices are sold in several versions, AV600, AV1000, AV2000 and more. I assume that each carries better tecnology and, of course, higher cost. For some consumers, I suppose 600 Mb/s is quite enough. I suspect that to get gigabit speed, you'll need to get the AV1000 or better.

I recommend that you select auto-negotiation and take what speeds you get.

[https://www.tp-link.com/us/home-networking/powerline/](https://www.tp-link.com/us/home-networking/powerline/)

---

### Post by sisco311 on 2019-09-17
Don't know much about networking, but I think 600Mb/s is the peak data rate.

AV600 refers to the HomePlug AV2 technology. 

See:
[https://en.wikipedia.org/wiki/HomePlug](https://en.wikipedia.org/wiki/HomePlug)
[https://en.wikipedia.org/wiki/Bit_rate](https://en.wikipedia.org/wiki/Bit_rate)

Devices which offer gigabit speed I think are also using the ground wire.

---

### Post by TheFu on 2019-09-17
I have a different brand of 600 Mbps Powerline ethernet extenders.  My networking is all GigE and the powerline adaptors all show "GigE" connections on the switch ports.  This is required for any powerline with over 100 Mbps on the box. When I first got the powerline equipment, I ran some tests.  [https://blog.jdpfu.com/2015/08/27/powerline-ethernet-adapters](https://blog.jdpfu.com/2015/08/27/powerline-ethernet-adapters)  You can do the same.

Basically, on opposite sides of a wall, it got 220 Mbps.  Between floors, it only provided 60 Mbps, so only 10% of the bandwidth claimed on the box.  House wiring will matter.  My home was built in the early 1990s following the electrical code at the time.

The reason for powerline over wifi, is that the 60 Mbps is stable, solid, unwavering, reliable.  Wifi bandwidth jumps all over the place and we don't have any real control over the true throughput achieved. Other devices, even non-wifi devices, weather conditions, atmospheric conditions inside the house, wall thickness and materials, all impact the real throughput for wifi.  Never believe the wifi "connection speed" - those are all lies.  

**NOBODY gets the speed on the box for any networking devices.  ** It is just the size of the lie told which changes.

Wired ethernet comes closest to the truth and is by far the most consistent of all home networking setups. Pretty much anywhere in a house, with CAT5e, you should be able to get 920 Mbps, even going through multiple GigE switches. There are distance limits, but if you aren't living on a huge estate like JR Ewing, then you don't need to worry about those distances.  CAT5e has double the require capacity to handle GigE networking.  There is little need to get CAT6 or CAT7 wiring unless you plan to deploy short-range 10 GigE inside 1 room. If you are going there, best to use fiber which easily will handle JR Ewing's estate distances.

---

