---
title: "Do I need a full-fledged WAN router to run a home"
date: 2015-06-19
forum: Networking &amp; Wireless
---

### Post by papakota on 2015-06-19
Hello

I want to set-up a home web server. It won't be an issue to get a static  IP and to run a server (spoke about that with my ISP already).
The difficult part is the hardware. My budget is tight and I don't feel  like investing money into buying an additional hardware, unless I  absolutely have to. What I have right now is a DSL modem that has SOME  (keyword SOME!) router capabilities. It's basically 3 in 1. It's a DSL  modem, a Wi-FI AP and Ethernet switch. I don't need it as a modem, since  I don't have DSL here (the device is from another apartment and even  country -- long story and not relevant). Right now I use it as a switch  and AP. I really do NOT need this nice device to get online, it's just  it's more convenient to get rid of wires on the floor. Some fools think  that I have a Wi-Fi Internet at home or DSL. AGAIN -- it's NEITHER. It's  a RJ-45 Ethernet PPPoE connection to the ISP.
P.S. Frankly, it's not even a money issue -- I'm afraid to buy Chinese  crap that produces a high-pitched noise (kinda zzzzzzzzzzzzzz!) while  working and I can hear it and it drives me crazy (already returned  couple of devices to the store).

---

### Post by TheFu on 2015-06-19
You need a router capable of forwarding 1 port (80/tcp) from the WAN side to a static IP on the LAN side. That's all. A $15 el-cheapo-router made in the last 10 yrs can do that.

However, you should consider security more. If someone breaks into your web server, they will likely own your entire network in 2 minutes. Most people don't know when that happens - just look at all the phishing emails you get that point to web servers on the internet. ALL OF THOSE SERVERS have been pwned.  Think about that for a few minutes.

---

### Post by Bucky Ball on 2015-06-20
If your modem is plugged in to your router and the router is online then the machines plugged into the router should be online, including the server.

---

### Post by papakota on 2015-06-20
[COLOR=#000000]The device we're talking about is
HUAWEI hg-530 
This  device does have some router capabilities, but not all. It does have  port-forwarding. Now when you know exactly what we're talking about,  you'd know better IF that device can be used in a home web server  set-up. This device has a DSL WAN port (RJ-11), that I'm NOT using. So I  can't use this modem for automatic connection to the Internet. I have  to use a Windows dialer (so called "High Speed Connection) or ppoeconf  in Ubuntu.
My guess is that I probably CAN use this device in the context of HTTP server hardware, but it all comes down to **its correct configuration** for such purpose.[/COLOR]

---

### Post by TheFu on 2015-06-20
Sounds like you need a $20 router to make this easy and more secure. Fine one that runs openwrt, tomato, or dd-wrt.

The port forwarding are probably tied to the WAN port (i.e. the DSL connection). That is sorta the way these things work.

---

### Post by Bucky Ball on 2015-06-20
[Here's]("http://www.bestphone.com.ar/comercio46/html/385240HUAWEI_HG530_Home_Gateway_Product_Description%20%281%29.pdf") a link to the manual for that device, incidentally.

---

### Post by papakota on 2015-06-20
Thanks for your replies! Okay, I'm gonna check my router and see what I can do with it.

---

