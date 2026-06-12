---
title: "Pathetically slow Internet"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by Linux_Man on 2009-07-29
Ok, so I recently bought a Toshiba L305-S5955, everything works fine except for the wireless internet, it has horrible latency and the same file that downloads at 200 Killobytes/sec on other computers in the network along with on the Vista partition. However, on Ubuntu the same file downloads at around 50 Killobytes/sec and has terrible latency. The networkcard is Realtek RTL8187B Wireless 802.11b/g 54Mbps USB 2.0 Network Adapter and is detected the same on Ubuntu (using Vista -shudder- for the time being because Vista is faster at browsing, never thought anyone would say that eh ;) ). I thought that perhaps IPv6 would be the problem, however in Ubuntu 9.04 which I'm using there is no easy way to disable it. I have tried three different routers all with the same results. I have also tried three different network connections and all gave the same speeds. Any advice on what I can do? Perhaps a different distro works better?

---

### Post by alphacrucis2 on 2009-07-29
> **Linux_Man said:**
> Ok, so I recently bought a Toshiba L305-S5955, everything works fine except for the wireless internet, it has horrible latency and the same file that downloads at 200 Killobytes/sec on other computers in the network along with on the Vista partition. However, on Ubuntu the same file downloads at around 50 Killobytes/sec and has terrible latency. The networkcard is Realtek RTL8187B Wireless 802.11b/g 54Mbps USB 2.0 Network Adapter and is detected the same on Ubuntu (using Vista -shudder- for the time being because Vista is faster at browsing, never thought anyone would say that eh ;) ). I thought that perhaps IPv6 would be the problem, however in Ubuntu 9.04 which I'm using there is no easy way to disable it. I have tried three different routers all with the same results. I have also tried three different network connections and all gave the same speeds. Any advice on what I can do? Perhaps a different distro works better?

I had a problem with wireless on a laptop running Vista giving pathetic performance. It turned out the problem was caused by the wireless driver defaulting to a setting that amounted to minimum power usage. Changing the setting to maximum performance fixed the problem. With wireless running on low power you are likely to get a lot of packet loss/retransmissions which makes the performance really bad. Maybe something similar with the Linux driver for your Realtek?

---

### Post by Linux_Man on 2009-07-29
Hm, perhaps. That would be something I would need to check out. Thanks for the lead.

---

### Post by mapes12 on 2009-07-30
The slow speed may be down to the native Linux driver running at "b" 11Mbps and not "g" 54Mbps. It's a recognised problem. Here'a a suggested fix:

[http://michael-peeters.blogspot.com/2008/12/getting-realtek-rtl8187b-wifi-stable.html](http://michael-peeters.blogspot.com/2008/12/getting-realtek-rtl8187b-wifi-stable.html)

And other results from Google:

[http://www.google.co.uk/search?hl=en&q=Realtek+RTL8187B+Wireless+ubuntu&btnG=Search&meta=](http://www.google.co.uk/search?hl=en&q=Realtek+RTL8187B+Wireless+ubuntu&btnG=Search&meta=)

---

