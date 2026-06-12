---
title: "ssh not working"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by merlinus on 2007-05-09
I have set up ssh on one ubuntu machine, but cannot log into it from my other ubuntu box.

I have tried ssh user@merlin-desktop, but get a message that it does not exist.  This is the host name listed in Network Settings/General.

When I use IP address 192.168.0.1, the terminal does nothing but sit and blink.

The computers are connected to a router that uses DHCP.

Thanks for any assistance.

-merlin

---

### Post by blackened on 2007-05-09
Have you tried using a static address on the box that you're trying to connect to?

---

### Post by haricharan on 2007-05-09
try assigning static ip to both the systems...or atleast the system where ssh-server is running and try....btw 192.168.0.1 usually is the ip for router..you have to find out ur ip using ifconfig (guessing u didnt change ur router's default ip)

---

### Post by merlinus on 2007-05-09
OK!  This worked.  The IP address on the host is 192.168.1.100.  Will this change, or is it permanent?

If it will change, how can I make it a static address?

Many thanks!

-merlin

---

### Post by blackened on 2007-05-09
It'll change whenever you reboot if you're using dhcp.

To make the address static:
System -> Administration -> Networking
On the "Connections" tab select the device you're using to connect then hit the "Properties" button.
Change the dropdown list from "Automatic Configuration (DHCP)" to "Static IP Address" and hit ok.

---

### Post by merlinus on 2007-05-09
OK.  I see how this can be done.

But....  will this then kill my Internet connection, which is DHCP (comcast)?

And will I also need to put in a subnet mask and gateway address?

Thanks.

-merlin

---

### Post by blackened on 2007-05-09
It shouldn't hurt your internet connection. With DHCP, your modem will request its IP from the provider, then your router will request its IP from the modem, the computers with static addressing will already have an IP address, but those using DHCP will request and receive an IP from the router.

You shouldn't have lost your subnet mask or gateway, but if you did, then put in 255.255.255.0 for the subnet mask and 192.168.1.1 for the gateway.

---

### Post by merlinus on 2007-05-09
Great!  It is working fine at the moment, and hopefully will continue to do so after rebooting.

Thanks so much for your assistance and expertise.

-merlin

---

