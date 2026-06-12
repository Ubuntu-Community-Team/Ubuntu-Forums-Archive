---
title: "router (shorewall/dhcp) - no connection between lan and wan"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by viggeh on 2008-11-18
I'm currently configuring a router/server box running ubuntu-server. As of now I've spent about 8 hours trying to enable connections between the lan and wan, however with no success.
I believe I'm missing something, but what?

**NIC configuration:**
eth0 = lan (connected to a switch, static ip)
eth1 = wan (connected to the dsl modem)

The router is accessable from outside, and from within the network (I can ssh to it), but the computers within the network does not have any access to the wan.

**Shorewall configuration:**
*/etc/shorewall/interfaces*```
#ZONE	INTERFACE	BROADCAST	OPTIONS
net		eth1		detect		dhcp,norfc1918,tcpflags
loc		eth0		detect		dhcp
```
*/etc/shorewall/policy*```
#SRC	DEST	POLICY		LOG LEVEL	LIMIT:BURST
all    all    ACCEPT
```
*/etc/shorewall/rules*```
#ACTION		SOURCE	DEST		PROTO	PORTS
```
*/etc/shorewall/zones*```
#ZONE	TYPE		OPTIONS			IN				OUT
fw		firewall	
net		ipv4		
loc		ipv4
```
*/etc/shorewall/masq*```
#INTERFACE	SUBNET		ADDRESS
eth1		eth0
```

Thanks in advance!

---

