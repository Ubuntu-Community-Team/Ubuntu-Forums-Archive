---
title: "dual boot windows/thin client"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by chrisblessing on 2007-04-18
Greetings. I have a new Edubuntu server serving a lab of 18 clients. The clients can boot either to the server or to Windows 98 on the hard drive. For those teachers/students booting to Edubuntu everything is sweet (faster, prettier, stable, etc...). For those who choose Windows for specific applications, it is not possible to access the Internet or school LAN. If I disable Edubuntu's DHCP, the Windows computers get an IP from the school LAN DHCP server and work normally, but if they retrieve an IP from Edubuntu they can ping eth1 (internal) but not eth0 (external).

Physically, both eth0 and eth1 are plugged into the switch so that users outside the lab can print to a networked printer in the lab.

I appears to me, as a network novice, that I must allow forwarding of requests from the Windows clients from eth1 to eth0  on Edubuntu. Either that, or something else on Edubuntu is not properly configured to allow Windows requests to pass to the LAN.

Any help on where to look would be greatly appreciated. Our teachers are nuts about Edubuntu, but we will continue to have some need to have the Windows 98 machines work as usual.

---

### Post by bloodniece on 2007-04-18
try setting the Windows gateway to the Windows DHCP server and vice-versa for Edubuntu pointing to Edubuntu DHCP server as gateway and DNS.

With 18 workstations you could use static IPs, which would be ideal.

---

### Post by chrisblessing on 2007-04-20
Thanks bloodniece for your reply. Let me tell you how I fixed this problem. First, I tried following your suggestion. However, because no requests from the Windows machines made it past eth1, no matter what gateway I gave them, they wouldn't work. That includes just assigning a static ip from the LAN. So the Windows computers would only receive an ip from Edubuntu. Clearly, the Windows computers were not communicating with eth0 at all.

Initially I thought that I might correct this by using port forwarding, but this would be a true adventure for me. Instead, I thought it better simply to have Edubuntu be the DHCP, DNS and cache server for all the Windows computers. So what I did was to link a 5 port switch to the school LAN, along with Edubuntu's eth0 and the printer, making the printer available on the external interface. The 24 port lab switch then connected to Edubuntu's eth1. I then installed bind and squid on Edubuntu. Edubuntu's DHCP now listens on eth1, as well as resolving http requests from the Windows clients. Now the lab computers can boot to Windows when necessary and access the school LAN as before. Of course, in time I suspect few teachers will wish to use Windows, as the Edubuntu clients are so much faster. And the students have already made up their minds...they love Edubuntu.

Thanks again for your help.

Chris

---

