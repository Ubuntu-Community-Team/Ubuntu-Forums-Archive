---
title: "Network topology questions"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by asmith3006 on 2008-07-30
I have a question that's not OS related at all but I don't know of a more helpful forum than this so thought I'd try my luck.

On our company network we have a large internet connnection which we get charged for the highest speed we use. So, I want to throttle general users but allow certain servers unrestricted access (web servers etc).

The best way I can think of doing this is to have a router on the network which has the ability to have maximum upload and download rates set and then use this as a default gateway which would have the WAN port pointing at the main router. This default gateway would be assigned by DHCP. I could then hard-code the important machines with the master default gateway:

```

Web Server------------------------------Master Gateway - Internet
Web Server2---------------------------/     /
                                           /
Desktop PC1 -----------------Additional Gateway
Desktop PC2------------------/     /
Laptop1 --------------------------/

```

IP details:
Master Gatewat: LAN IP: 172.18.0.254/255.255.0.0
Additional Gateway:
LAN IP: 172.18.0.252/255.255.0.0
WAN IP: 172.18.0.253/255.255.0.0
WAN Gateway: 172.18.0.253

Web Server (Static IP): 
IP: 172.18.0.(1,2,3,4)/255.255.0.0
Default Gateway: 172.18.0.254

Desktops/Laptops (DHCP):
IP: 172.18.0.(101,102,103,104)/255.255.0.0
Default Gateway: 172.18.0.253


Is this possible? I'm not sure about the additional router having the same subnet for WAN and LAN. I want to thrttle all traffic which is why I'm avoiding Squid as that's difficult/impossible to throttle everything (note i want to throttle not block).

Any and all advice welcome.

Thanks in advance.

Andrew

---

### Post by randomnote1 on 2008-07-30
It appears you're looking for a QOS (quality of service) type of device.  Traditional home routers (ie. Linksys) have these type of controls built in, but larger business class routers are strictly for routing.  You can definitely find QOS devices, but I cannot for the life of me think of any right now.

Anyway, long story short, you're looking for QOS.

---

### Post by asmith3006 on 2008-08-03
Thought you'd say that :( Thanks for the advice :)

---

### Post by casevh on 2008-08-03
What you are looking is called "policing". It is typically used along with QOS. It is supported on most Cisco routers and some Cisco switches. Search for "cisco qos policing". (I assume most other business-class routers support policing; I'm just familiar with Cisco.)

casevh

---

