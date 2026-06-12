---
title: "DHCP fails to receive DHCPOFFER"
date: 2014-06-27
forum: Networking &amp; Wireless
---

### Post by jmoellers on 2014-06-27
I have a small board (Fujitsu D3221-B1) with an Intel I217-V gigabit ethernet chip driven by e1000e.
I started with 13.10 but in early may I installed 14.04.
The network is managed by nm and eth0 is set up for DHCP, a 12.04 system dealing out the addresses.
The system is used as a DVB-S recorder, so it regularly boots without the DHCP server being up, the client then gets an address 169.254.3.xxx.
When the system is up, WOL is configured (if-up.d/wol: /sbin/ethtool -s ${IFACE} wol g).
The first thing I notice is that when the system is down again, I cannot boot it using WOL!
When I then switch it on using the frontpanel button (with the DHCP server up), dhclient fails to get the client's address.
Using wireshark on both sides, I see that
1) the client sends a DHCPDISCOVER
2) the server responds with a DHCPOFFER carrying the client's IP address (172.16.0.37)
3) the client does not see the DHCPOFFER
4) the dhcp process fails, obviously.
I tried to put the client onto another port of my network switch, no improvement.
I tried disabling network-manager and entered eth0 into /etc/network/interfaces, no improvement.
Sometimes rebooting the client helps, but occasionally even this doesn't help.
Sometimes waiting long enoiugh helps ...

Any hints?

---

