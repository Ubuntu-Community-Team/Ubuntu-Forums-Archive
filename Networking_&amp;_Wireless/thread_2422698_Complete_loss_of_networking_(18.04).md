---
title: "Complete loss of networking (18.04)"
date: 2019-07-11
forum: Networking &amp; Wireless
---

### Post by jzjr on 2019-07-11
This morning, my box lost its LAN connection over Ethernet.  There have been no changes that I am aware of (the only access is mine) and I have tried numerous cables and ports.

My switch is showing just one packet every few seconds received and the box cannot interact with the network at all, using DHCP or static IP. 

I have checked the interface is shown in lspci and ifconfig and I have checked the netplan yaml file and I'm not sure where to look next.  It is a bit difficult as I have no other method of connecting to the box other than locally, I don't have a WiFi dongle I can try. 

If anyone can suggest which logs I can look at/share with you to help diagnose the problem I'd be grateful. This box is my main DNS server and home automation server so I'm hoping I can get it going again soon. 

Thanks
Fred

---

### Post by jzjr on 2019-07-11
On boot I get the following messages (not correctly formatted due to them being hand typed).

[FAILED] Failed to start Load Kernel Modules.

Three times - from what I can tell the missing modules are 'dahdi', 'dahdi_dummy' and 'dahdi_decode'.  This leads me to believe these failed modules are not the cause as I am experiencing an Ethernet issue and do not use this server for telephony.

Thanks
Fred.

---

