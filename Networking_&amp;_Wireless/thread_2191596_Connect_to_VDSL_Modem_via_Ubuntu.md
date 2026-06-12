---
title: "Connect to VDSL Modem via Ubuntu"
date: 2013-12-03
forum: Networking &amp; Wireless
---

### Post by chrislynch8 on 2013-12-03
Hi,

Our ISP are now offering VDSL with increased Bandwidth from 8Mbps/2Mbps to 70Mbps/20Mbps. I have upgraded a test line in work (which cannot be downgraded) to test if on our Ubuntu File Servers. Currently we have ADSL in all offices, the Phone Line is connected to an ADSL Modem that is in Bridge Mode and then using pppoconf we configure the Server to Connect to the ADSL and provide Internet to the Office, then server then acts are the Router, Firewalls, etc for that office among other things.

I now have our ISPs Router next to me and I am getting the speeds above which is great, when the router is in Route Mode. The Router has the ability to be used in Bridge Mode. When I enable Bridge Mode and connect it to my File Server, when I issue pppoeconf it will not work as it is unable to find PADO Packets. 

My question is should this work as before and Ubuntu should be able to connect to the VDSL and provide Internet access to an office, or is this a no go?

Rgds
Chris

---

