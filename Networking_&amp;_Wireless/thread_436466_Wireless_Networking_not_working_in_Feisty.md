---
title: "Wireless Networking not working in Feisty"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by HerbalDoc on 2007-05-07
Hey all of you, hope you can help me!

I just got done installing everything into my laptop (Dell Latitude CPi-A 400xt) from the Ubuntu Dvd-Rom. I also loaded Kismet. From what I can tell, my networking card (D-Link DWL-650+) should be supported. Its just the ACX100 driver. And when I look at hardware, it shows up, Kismet works (kinda), and I can "see" networks. But when I try to connect to them, the computer shows its trying to connect for about 30 sec, then stops and goes back to no-connection. I've tried it with Roaming mode, and with manual configuration. The closest I've come to getting connected so far was at a Subway wireless hotspot, which showed that I was connected, but didn't assign me an IP, and of course I couldn't connect to the internet.

Please help! I have a passing understanding of linux, but this is beyond me. Thank you all very much in advance, and let me know if there's anything else I can provide that might help you help me!

---

### Post by Floppyjoe on 2007-05-07
Issue a lspci command from the terminal window. Then find your wireless adapters chipset(under network controller) and search the forum for information on how to get that chipset to work.

Hope this helps,
Floppyjoe

---

