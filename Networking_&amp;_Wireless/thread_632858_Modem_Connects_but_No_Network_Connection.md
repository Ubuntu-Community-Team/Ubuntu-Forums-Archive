---
title: "Modem Connects but No Network Connection"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by wedge_769 on 2007-12-05
Hi Everyone,

I'm a newbie to Ubuntu 7.10 and am having trouble with my modem connection.

Using scanmodem I found my modem, downloaded the driver from linuxant. Purchased the Linuxant license key and successfully registered for full version of driver.

When I dial out it works however I still get "No Network Connection" reported in the network symbol top right of screen.

Firefox does access the net but slowly, way slower than windows.

Evolution "Send & Recieve" is greyed out so I cant use it.

My routing is as follows,

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
203.173.60.88   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

Any suggestions would be greatly appreciated,

---

### Post by Bartender on 2007-12-06
Who's your ISP?
And what Linux dialer are you using to connect?
Can you attach a log file from wvdial?

---

### Post by wedge_769 on 2007-12-07
Hi Bartender, thanks for your interest.

My ISP here in Australia is iinet.

I dont use wvdial, should I? When i tried it it was not setup.

I use the modem connection found by clicking on network connection symbol top right of ubuntu 7.10 screen. Then as follows,
Manual Configuration,
Network Settings,
Modem Connection, (Highlight)
Click properties to fill in modem dialing details.

Then to activate,
Click on network connection,
dialup connections,
connect to ppp0 via modem. (It then dials and connects.)

However internet access via firefox is slow.
Evolution email send & recieve is greyed out.

Best Regards, Wedge_769

---

