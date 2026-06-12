---
title: "Internet Connection Slows after 24 hours"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by baloo56 on 2007-03-12
I have a High Speed Cable Internet connection at home (Speeds up to 10 Mbps....well.. advertised at that anyway)

I am using Ubuntu Dapper with all updates installed.

The modem I am using is Motorola SB5100  Cable modem and the ISP is Eastlink . I also use a LinkSys WRT54GS Wireless Router with it. My desktop is hardwired to the router while the kids laptops use the wireless. The speed of the connection goes from a very nice top speed and over a period of 24 to 36 hours gradually slows to a crawl. This happens with my desktop as well as the kids two laptops.

If I unplug & then reconnect the modem & router, it starts again from its top speed, but 24 to 36 hours later its slow down again.

Any ideas on how to isolate the cause of this slow down?

---

### Post by denver on 2007-03-12
It sounds more like a router/modem problem. In some cases ( poor grounding or otherwise ) some modems or routers get statically charged. A reset gets them back in working condition. I had the same problem with a switch once. After a day or so, it stopped working and I couldn't see anyone on the network. The problem persisted until i reset the switch.

This was in my case at least...i don't know if it applies in yours....however the fact that it works after a reset of the modem/router suggests that you have the sae problem. Solved this problem by adding grounding to my Power Sockets.


Hope this helps...good luck!

---

### Post by baloo56 on 2007-03-17
Thank you for your reply Denver. I checked the grounding on both my router & modem with my multimeter and they were fine. The problem seems to have dissappeared. The only change I made since my posting of the problem was to reduce the number of DNS server addresses for my Internet Service Provider from three to one in my network DNS setup. I also noted a faster login time  to my ISP's E-mail server since the change. It may be a coincidence but time will tell.

---

### Post by denver on 2007-03-18
It was not necesarily a coincidence. If you have a slow DNS server in youre list, slow queries to that server might mimic no connectivity to the internet on the count that we usualy tend to ping or access a server by its hostname rather then the IP address. 
Glad you managed to resolve youre problem :).

---

