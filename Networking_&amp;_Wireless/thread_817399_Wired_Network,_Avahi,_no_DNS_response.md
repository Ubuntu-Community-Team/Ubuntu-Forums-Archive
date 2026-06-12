---
title: "Wired Network, Avahi, no DNS response"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by niiiick on 2008-06-03
Hi guys,

So i recently moved into a dorm for summer and am on the university network.  My roommate can connect his windows laptop with an ethernet cable with no problem, but I am having difficulty with my gutsy ubuntu install.

I plug the ethernet cable in and it takes a while to connect.  When it does, I am unable to connect to the internet.  An ifconfig yields eth0 and eth1 without ip addresses, but an eth0:avahi with an ip address.

I've tried setting my DNS servers to OpenDNS addresses to no avail, and I can't even ping those addresses by IP number.  I've tried killing the avahi daemon, getting rid of avahi-autoip and avahi-daemon, but when those don't exist, I don't get a connection.  It just stays "attempting to connect to the wireless network".

I think I understand that avahi shows up when there's no DHCP response from the router, but why would that be when my roommate's wired laptop works fine?  I can rule out a hardware issue; it's not the cord, the driver (as it works wired elsewhere) or the port.

Why can I not get a DHCP response and how can I fix that if I don't have administrative access to the router?

A pre-emptive thanks to whoever helps!

---

### Post by vexingmodstwo on 2008-06-03
> **niiiick said:**
> Hi guys,

So i recently moved into a dorm for summer and am on the university network.  My roommate can connect his windows laptop with an ethernet cable with no problem, but I am having difficulty with my gutsy ubuntu install.

I plug the ethernet cable in and it takes a while to connect.  When it does, I am unable to connect to the internet.  An ifconfig yields eth0 and eth1 without ip addresses, but an eth0:avahi with an ip address.

I've tried setting my DNS servers to OpenDNS addresses to no avail, and I can't even ping those addresses by IP number.  I've tried killing the avahi daemon, getting rid of avahi-autoip and avahi-daemon, but when those don't exist, I don't get a connection.  It just stays "attempting to connect to the wireless network".

I think I understand that avahi shows up when there's no DHCP response from the router, but why would that be when my roommate's wired laptop works fine?  I can rule out a hardware issue; it's not the cord, the driver (as it works wired elsewhere) or the port.

Why can I not get a DHCP response and how can I fix that if I don't have administrative access to the router?

A pre-emptive thanks to whoever helps!

If you can find out the default gateway IP address, you should be able to manually configure the connection.  You'll need the IP address that shows up under that "avahi" thing and the default gateway IP address from the router.  You should be able to get that from your buddy's windows machine when you run ipconfig in the command prompt window.

---

### Post by superprash2003 on 2008-06-03
have you gone to system->administration->network->eth0 or eth1 properties and set it to DHCP .. To setup opendns servers permanently on the laptop [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

