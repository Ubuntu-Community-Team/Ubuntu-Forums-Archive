---
title: "internet and network problem - strange random errors"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by 3SV on 2008-02-10
Hello,

I have an Desktop PC that connects wireless and/or with wire to an Linksys router. Al the other systems that connects to the Linksys seems to have no problems. The problems seems to appear only when i am connecting wireless. I am using an ASUS P5 wifi motherboard with onboard Realtek wireless card with the rtl8187 driver.

On the desktop the connection stays always on but on some random moments i can't do anything with the connection. I can't access the internet and can even ping the router. 
On such a moment with ifconfig and iwconfig everything seems to be fine.  When i open wireshark i can even see some packets coming from my router. It seems that the physical connection is still OK.

I have no idea what the problem can be. I have already blacklisted IPv6. I have also tried to not using the gnome network-manager without success. The problem stays the same. I have also installed the latest Hardy beta but the problem is the same there. Sometimes the problem occurs after 5 minutes, sometimes after 2 hours. 

In the attachment you find an Wireshark file from the moment i can't do anything with the network. My router has fixed ip address 10.0.0.1. DHCP range starts at 10.0.0.100.

Does anybody see what the problem can be?

Thanks in advance!

---

