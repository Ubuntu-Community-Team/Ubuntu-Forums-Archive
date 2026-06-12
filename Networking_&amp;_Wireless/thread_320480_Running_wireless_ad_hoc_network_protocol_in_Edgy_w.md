---
title: "Running wireless ad hoc network protocol in Edgy with 2 network interfaces"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by arinto on 2006-12-17
Dear All

I want to run a routing protocol using Edgy Eft in my desktop that has 2 network interfaces. The first one is LAN interface, eth 0. The ip address for this interface is set dynamically using my school DHCP server. The 2nd interface is the USB Wireless Interface, wlan0. This wireless interface act as the gateway from my ad hoc network to the Internet. 

Here is the configuration for my ad hoc network

internet -->> desktop  <<-------->> laptop 1, laptop 2 (ad hoc network through wlan0)
(through eth0)

The protocol broadcasts packet to its neighboring nodes But, interestingly, it broadcast its packets
via the wired LAN interfaces (eth0) not the wireless interface (wlan0) as what I expected. Is there any way to set the default interface in ubuntu? Or is there any solution for this problem so that the protocol will send its packet through the wireless interface?

Thank you
arinto

---

### Post by compwiz18 on 2006-12-17
Good luck with this, it is difficult.

But it can be done.

First: Run **sudo iwconfig wlan0 mode ad-hoc** on the desktop
Second: Run **sudo iwconfig wlan0 essid [put-your-essid-here] channel [put-your-channel-number-here]** on the desktop
Third: Run **sudo ifconfig wlan0 192.168.1.1** (this will set the IP of wlan0 on the desktop to 192.168.1.1)
Fourth, I would suggest you install firestarter ( **sudo apt-get install firestarter** ) .  It will give you an easy way to setup internet connection sharing.
Fifth: During the Firestarter config screens, setup internet connection sharing.
Sixth: Give the two laptops static ips, like 192.168.1.2 and 192.168.1.3, and set the netmask to 255.0.0.0 and the gateway to 192.168.1.1 and set the DNS servers to the your ISP's DNS servers, or if you don't know what they are, use the OpenDNS DNS servers: 208.67.222.222 and 208.67.220.220
Seventh: Use the internet from your laptops!

Hope this helps.  If this doesn't solve the problem, ask, and I'll try and help you some more.

---

### Post by drim on 2007-01-26
great! it's workin'!
thank you very much, have a nice day.

Andrea
Italy.

---

