---
title: "Problems having a network interface without ip assigned"
date: 2016-07-10
forum: Networking &amp; Wireless
---

### Post by marcus-dahlberg on 2016-07-10
At reboot, the network adapter in not active.
I can fix this with "ifconfig enp3s0 up"

It  comes up with an ip address assigned. I think this has something to  with that I remove the ip address and ubuntu doesn't want to bring up an  adapter without ip?

This is a vpn adapter working in promiscuous mode and shout not have an IP assigned.

Is there a way to ensure the adapter comes up at reboot without an ip address?

Thanks

---

### Post by marcus-dahlberg on 2016-07-18
I had to remove the card from the GUI configurator then added this lines to /etc/network/interfaces

auto enp3s0
iface enp3s0 inet manual
up ifconfig enp3s0 up

replace enp3s0 with your interface.

Solved

---

