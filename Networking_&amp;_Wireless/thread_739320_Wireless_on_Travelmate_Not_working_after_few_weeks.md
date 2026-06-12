---
title: "Wireless on Travelmate Not working after few weeks"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by Riama on 2008-03-29
I have a Travelmate 4601 with ubuntu 7.10 installed. For a few weeks my wireless connection worked fine. I am using wireless with the onboard intell 2200BG. The connection is secured with WPA encryption. 

Now suddenly ubuntu can't connect any longer. It sees the network, but when it connects it stops after a few moments. A few months ago i had exactly the same problem. Everything the same setup, then it stopt working. But then it automatically was back on in a few days. This isn't the case at the moment.

**What i have done already**

I already updated the drivers of IPW2200

        *-network:0 DISABLED
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@0000:06:03.0
                logical name: eth1
                version: 05
                serial: 00:12:f0:6c:0f:a8
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wirelesst
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2 firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 mod

I think the problem is that this show a disabled status, but i can't find anything to enable this. And i don't see a switch on my notebook to do this. If anyone got any suggestions it would be greatly appreciated!

---

