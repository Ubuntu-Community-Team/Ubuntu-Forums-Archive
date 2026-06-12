---
title: "PXE-booting a diskless client over WLAN (solution)"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by blumi00GT on 2006-10-27
Hi,

I am writing this because it caused me some headache and I couldn't find any reliable solution for this problem in the net. It doesn't rely on Ubuntu especially - it works on all systems.


_**THE SITUATION**_

(1) A PC without harddrive and on-board ethernet card (namely: a VIA EPIA system), intented to act as a livingroom-PC with as less noise as possible.

(2) A file server (with harddrives 8) ), connected over ethernet, which acts as DHCP- and DNS-server also. WLAN is availible at a DSL-router in the network.

The PC was set up until everything worked fine. When switched on, it sends a PXE-Broadcast over ethernet, which got answered by the DHCP-server with the IP-address and the kernel-image(*). The rest is the usual system setup (Ubuntu, in this case).

*) This is not exactly correct in a technical way, but enough here to describe the problem. Interested persons may read [this]("http://dev.brantleyonline.com/wiki/index.php/General_Network_%28PXE%29_Booting") as a starting point.


_**THE PROBLEM**_

I was not allowed to pull an ethernet cable through the living room (women [-( ). Since WLAN was availible, this was the way to go. Unfortunately WLAN adapters don't support the PXE-broadcast mentioned above. So this couldn't be solved with a simple USB-WLAN-adapter.


_**THE SOLUTION**_

After doing some research I found out that there is no "priceless" software solution (i.e. by hacking some kernel parameters or drivers and such). So I browsed the product pages of the common hardware manufacturers and found one device, which did the trick:

The [DLink DWL-G810]("http://www.dlink.co.uk/?go=gNTyP9CgrdFOIC4AStFCF834mptYKO9ZTdvhLPG3yV3oUYl9j6ltbNlwaaFp6DQoHDrqyCJA+okKBts=")
[IMG]http://www.dlink.co.uk/archivos/2333-638-Imagen/dwl-g810_2.jpg[/IMG]

It is designed to work as a WLAN-Adapter for gaming consoles like XBOX, but it turns out that it is a good WLAN-bridge which also transports the PXE-broadcasts. During configuration of this device it's important to select "infrastructure mode", not the defaulted "ad-hoc mode" (this cost me an hour of trying).

By writing this I discovered that the DWL-G810 is marked as "discontinued" on the DLink homepage, but its successor, the [DWL-G820]("http://www.dlink.com/products/?pid=333") should work also, reading the specs.

The network transfer rate is not as good as before with ethernet, of course. But the ~2MB/s this device delivers are enough for the purpose of the living room PC.


I hope, this information helps someone, sometime.

Blumi

---

