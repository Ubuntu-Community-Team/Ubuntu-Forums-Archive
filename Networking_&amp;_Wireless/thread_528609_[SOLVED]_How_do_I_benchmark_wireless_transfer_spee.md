---
title: "[SOLVED] How do I benchmark wireless transfer speeds?"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by Jamie Jackson on 2007-08-18
How do I test the throughput of my wireless connection? I hear people claim things like "I'm getting 20 Mbps ..."

How are they likely to be getting those numbers?

Thanks,
Jamie

---

### Post by spd106 on 2007-08-18
There are two ways.

Artificial - The data rate reported by the driver. These are discreet values used to describe the "wire" rate rather than the flow of useful data such as files or data streams. For example it might be useful to know that the version of bcm43xx driver in Feisty is limited to 22Mbps, whereas if you use ndiswrapper you can reach 54Mbps, depending on interference etc. The nm-applet displays this as the speed in the connection information box.

Real data - Transfer a known amount of data and time how long it takes. As this is a statistical approach the larger the data the more accurate the calculated rate will be. This measures sustained rate rather than peak or burst rate.

There is a tool for testing called iperf, that's available in the Ubuntu universe repo. You install it on two systems, one runs as a server and the other as a client. It will give you a more realistic view of what your network is capable of.

---

### Post by Jamie Jackson on 2007-08-18
The iperf package couldn't be any easier. I'm all set, thanks!

Jamie

---

