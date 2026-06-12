---
title: "Possible to get two (virtual) interfaces from one NIC?"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by Bradl3yJ on 2008-07-10
I have seen guides on how to set up tap interfaces and a bridge so that a VM guest can use bridged network to get it's own IP. I am in a similar scenarion where i am installing and running a simulator for NetApp. The simulator software will use a second ethernet interface if present to connect to the network.

Here is what I have done:

```
sudo tunctl -t tap1 -u brad
sudo brctl addbr br0
sudo ifconfig eth0 0.0.0.0 promisc
sudo brctl addof br0 eth0
sudo dhclient br0
```

At this point, br0 has an IP and I can connect to the network using it.

So then I try to add tap1 to the bridge:

```
sudo brctl addif br0 tap1
sudo ifconfig tap1 up
sudo dhclient tap1
```

tap1 fails to get an IP address from DHCP. I obviously do not have a good understanding of bridging and tap interfaces. Is what I am trying to achieve possible?

---

