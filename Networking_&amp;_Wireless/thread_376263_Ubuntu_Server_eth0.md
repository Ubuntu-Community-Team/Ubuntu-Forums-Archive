---
title: "Ubuntu Server eth0"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by Smokeymcpawt on 2007-03-04
I have an old PC that I couldn't get ubuntu server to install on, so I removed the hard drive, and placed it in my newer machine, and then installed ubuntu server. Once the install was done, I put the hard drive back into the old pc, and it booted up just fine. 

However, It is configured to use my normal computers network device, not the old ones. How can I set it up so that it uses the correct Device?

ifconfig returns:
```
Link encap:Local Lopback
inet addr:127.0.0.1 Mask 255.0.0.0
Up Loopback Running MTU:16436 Metric :1

```

sudo ifup eth0 returns: 
```
SIOCSIFADDR: No such device
eth0: Error while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0
```

lspci shows the card is there..:
0000:01:0b.0 Ethernet controller: D-Link System Inc DL10050 undance Ethernet (Rev 14)

---

### Post by PilotJLR on 2007-03-04
Debian / Ubuntu ties and interface to a mac address. If you do a "ifconfig -a", I would expect to see an eth1 interface for the new machine.

You can change this value by modifying /etc/iftab

---

### Post by Smokeymcpawt on 2007-03-05
Thanks alot, PilotJLR.


It worked :)

---

