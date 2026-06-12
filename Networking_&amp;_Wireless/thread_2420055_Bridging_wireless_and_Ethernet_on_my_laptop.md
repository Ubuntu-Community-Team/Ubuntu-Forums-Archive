---
title: "Bridging wireless and Ethernet on my laptop"
date: 2019-05-29
forum: Networking &amp; Wireless
---

### Post by Gvarelov on 2019-05-29
Hi good people,
I have an old laptop lying around with CentOS 6 32-bit installed on it already (upgraded it from Windows XP) and am trying to bridge that laptop's wireless network connection with its Ethernet network connection. I thought it would be a breeze but apparently it isn't, so I am thinking of pulling the trick of switching distros and am considering a 32-bit Ubintu flavor.
[B]How would I bridge wireless and Ethernet in ubuntu-12.04.5, provided it is at all possible?

Scenario:[/B]
Laptop has a wireless adapter that connects it to the Internet, address is in the range of 10.0.0.0/24, it is assigned dynamically from a router two houses away, to which I don't have access (it's somebody else's house, we are all in a gated community). Laptop also has an Ethernet adapter which will connect to a home wireless router- that wireless router will provide internet connection around my house and also keep my network devices from being accessed by my neighbors by accident (we're all on the same network as it is now and I'd be happy to separate but keep the internet connection). That wireless router will also assign network address to the Ethernet adapter of my laptop.
I need to share the internet connection from the wireless card to the Ethernet adapter. So the now- CentOS 6 and in the future Ubuntu 12.04 laptop will serve as a pasthrough of sorts.

---

### Post by wildmanne39 on 2019-05-29
First of all 12.04 is way out dated and presents a security risk if it is connected to the internet so I recommend 18.04.

I park my rv trailer in rv parks often and I do not have access to the wireless router but they give me the password to access the internet, is that not the case here that you can simply get the password to access the internet by wireless means?

---

### Post by TheFu on 2019-05-29
Linux networking as you've described is about the same on all distros. 

I don't know how to accomplish this without using double-NAT.  That will be ugly and can break some protocols.  My networking isn't strong enough to solve this without double-NAT.
 
I'd buy a WAP (probably from Ubiquiti), connect that to the WAN link on the router, then keep everything simple. It will make things much easier within the network, though you'd still need double-NAT.  The router gets to be a router.  The computers and your internal devices are protected behind that router.

I use a router as a bridge here. Just don't connect anything to the WAN port and that is what it is. Because it is a consumer wifi-router, I don't trust it or the wifi it provides.  It is connected outside my real router and I treat all traffic on it just like raw internet traffic. Consumer wifi routers aren't usually updated often enough and the firmware updates usually end in about 3 yrs. For me, it is just easier never to trust those devices.

Being familiar with OS support periods is very important:
* Ubuntu [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) - check out the "standard support" dates.
* [https://wiki.centos.org/About/Product](https://wiki.centos.org/About/Product)
I wouldn't deploy any of the OSes you've listed above.

---

### Post by QIII on 2019-05-30
Have you asked for help from the neighbor with the router?

---

### Post by Gvarelov on 2019-05-30
Even on a 32-bit machine that was made in early 2000's? Do you think it'd work?

---

### Post by Gvarelov on 2019-05-30
Neighbor is not at home very often and even if he was, he is a lost cause when it comes to networking and computers...

---

### Post by Gvarelov on 2019-05-30
> **TheFu said:**
> Linux networking as you've described is about the same on all distros. 

 
I'd buy a WAP (probably from Ubiquiti), connect that to the WAN link on the router, then keep everything simple. It will make things much easier within the network, though you'd still need double-NAT.  The router gets to be a router.  The computers and your internal devices are protected behind that router.

I use a router as a bridge here. Just don't connect anything to the WAN port and that is what it is. Because it is a consumer wifi-router, I don't trust it or the wifi it provides.  It is connected outside my real router and I treat all traffic on it just like raw internet traffic. Consumer wifi routers aren't usually updated often enough and the firmware updates usually end in about 3 yrs. For me, it is just easier never to trust those devices.

Being familiar with OS support periods is very important:
* Ubuntu [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) - check out the "standard support" dates.
* [https://wiki.centos.org/About/Product](https://wiki.centos.org/About/Product)
I wouldn't deploy any of the OSes you've listed above.
Thank you, all wonderful points there.
I am a fan of recycling and have this ancient laptop sitting around still in working condition, and also a situation with the shared internet access that I wanted to solve for quite a time. Surely, solution you presented is optimal given the problem at hand, I wanted to see this old laptop got used instead of filling up the landfill.

---

### Post by Gvarelov on 2019-05-30
I am marking this thread as solved, documentation on network/internet connection sharing helped solve the problem. Particularly the section "GUI method with Network Manager".
It is important to have dnsmasq-base package installed and uninstall dnsmasq. That alone I think opened the gates.
[https://help.ubuntu.com/community/Internet/ConnectionSharing#Wireless_Ad-Hoc_connection_sharing_scenario](https://help.ubuntu.com/community/Internet/ConnectionSharing#Wireless_Ad-Hoc_connection_sharing_scenario)

---

### Post by TheFu on 2019-05-30
> **Gvarelov said:**
> Thank you, all wonderful points there.
I am a fan of recycling and have this ancient laptop sitting around still in working condition, and also a situation with the shared internet access that I wanted to solve for quite a time. Surely, solution you presented is optimal given the problem at hand, I wanted to see this old laptop got used instead of filling up the landfill.

Old computers will use more electricity in 2-3 yrs than a WAP costs.  Just something to consider.
The world of computer efficiency has changed in the last 20 yrs drastically.

Just throwing out options.

I've been replacing computers from 2010 with more efficient models.  Saving about $15/month in electricity now just by replacing two 2009-era computers with a single 2018 model that is more than 2x faster. The CPU uses about 50% less power than one of the older machines alone.  65W vs 125W. For me, it will payback the cost of the new system in a little over 2 yrs with that savings alone.  

Your numbers will be different, but I would encourage you to look at the cost of electricity, unless you happen to get it for free/fixed price every month.  There definitely are situations where re-purposing older systems makes perfect sense.

When it comes to 18.04 - don't attempt the heavy desktop distros.  If you need more detailed guidance, post **sudo inxi -bz** output, using *code tags*, of course. That provides an overview of the hardware. A likely safe bet would be Lubuntu or Xubuntu 18.04. Whichever has a 32-bit version should work well enough as a router.

---

