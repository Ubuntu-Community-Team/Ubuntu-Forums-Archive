---
title: "ICS from Ubuntu through Vista not working"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by CreepinJesus on 2007-11-16
I have a laptop running Windows Vista which I'm trying to use as a throughput for internet connection sharing to an Ubuntu laptop.  Its all acting a bit strange: the Windows laptop is connected to my wireless network for internet access (which works - I'm on it now), with ICS enabled on the LAN device (*does it need to be on the wireless device?*).  The LAN is connected to the Ubuntu laptop (which has no wireless capabilities).

The Vista LAN card is set as static IP as:
- IP: 192.168.0.1
- Mask: 255.255.255.0
- Gateway: 192.168.0.1
- DNS Servers are the ones provided by my ISP (*may be the problem ?*)

The Ubuntu laptop is manually configured to a wired connection as:
- IP: 192.168.0.2
- Mask: 255.255.255.0
- Gateway: 192.168.0.1 (the Vista machine)
- DNS servers are also set to the ISP-supplies ones

There's some strange stuff happening though.  From the Ubuntu laptop, I can't ping the Vista machine @ 192.168.0.1, but I can ping the Ubuntu computer from Vista cmd @ 192.168.0.2.  nslookup does not resolve anything and there is no internet access on the Ubuntu computer.  However, I'm currently using Synergy to share the mouse and keyboard of the Vista machine with the Ubuntu machine, and that is working with no problems at all (the Vista machine is the Synergy server @ 192.168.0.1) so the two computers must be seeing each other.

Thanks in advance for any help...

---

### Post by ElijahLynn on 2008-06-21
I am not even showing a gateway with my vista laptop. Do I need this to enter into Ubuntu? I am basically having this same problem.

When I connect the ubuntu tower to the internet enabled laptop and select roaming mode it just shows all 0's for everything.

---

