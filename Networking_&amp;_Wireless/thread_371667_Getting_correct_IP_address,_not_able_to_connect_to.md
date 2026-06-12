---
title: "Getting correct IP address, not able to connect to hosts outside the network."
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by bhtooefr on 2007-02-27
System configuration is in my sig. Tried using wired (Broadcom BCM5751F) and wireless (Atheros AR5004G), same effect.

Everything works correctly in Windows.

I can connect to the network, and the network configuration (that I view by right-clicking on the NetworkManager applet (which I installed to allow me to use WPA) and clicking Connection Information is correct - that is, everything is what the DHCP server should be sending.

Also, I can ping and connect to hosts within the subnet. However, I cannot ping them by host name. (That's likely a DNS issue with the server, however, as I've seen it happen on some other machines running Windows.)

However, I cannot ping or connect to anything beyond the firewall, a SonicWall DMZ with largely default settings. I can't see why it would block a Linux host for whatever reason, unless it didn't like the MAC being the same.

Any suggestions for troubleshooting? Thanks!

---

### Post by bhtooefr on 2007-03-01
Bump?

---

### Post by bhtooefr on 2007-06-05
Bit of an update here, I've gotten it working with a set of commands.

In this network, the IP addresses issued are in the 10.42.0.50-200 range. Subnet mask is 255.255.0.0. Gateway is 10.40.0.1, however, traceroutes on Windows machines show traffic going through 10.4**1**.0.1.

I fixed this by running the following commands:

```
sudo ifconfig ath0 netmask 255.0.0.0
sudo route add default gw 10.41.0.1
```

That got it to connect, but it's mildly annoying to have to do that EVERY SINGLE TIME I connect. And, the Windows hosts don't have a problem with the default gateway or netmask (although they also don't have a problem with how I corrected the default gateway - I attempted to correct the netmask, but Windows DHCP doesn't allow you do do that when you specify your IP pool within a certain range narrower than, say, 10.x.x.x.

---

