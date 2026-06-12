---
title: "Server routing: Masq not returning packets"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by richbayliss on 2008-04-30
Hey guys,

**Intro:**
I have an unusual problem with my ubuntu router. Google has yielded no results on it, so I thought I would check here.

The router is providing 2 "LAN" interfaces, both on the same physical NIC just with seperate VLANs (vlan38 & vlan101), and 1 "WAN" interface.

On VLAN38 I have a PPPoE server setup, which accepts connections flawlessly, and on VLAN101 I have a DHCP server configured. Both networks send out packets on their LAN without problem.

What I want is that the DHCP and PPP sessions have internet access, via the WAN interface on the system. This is just a NIC with DHCP client on it. The system has WAN access and pings work to google etc.

**Problem:**
I setup (or tried to setup) IP Masquerade with IPTables and I have some unusual results. They are as follows:

After enabling IP_Forwarding in the kernel (via sysctl) if I ping from either the PPP or DHCP clients on either VLAN, the packets are routed to the WAN network. No masquerading takes place. Since the pings goto IP's that dont know how to return data, no response is expected.

When I enable masquerading:
```

iptables -A POSTROUTING -t nat -o eth1 -j MASQUERADE

```

The packets ARE altered to come from the server's IP, and a repsonse is made from the WAN network, but the server doesn't return the packets to the LAN client.

**Question:**
Does anyone know why this is? My IPtables ruleset is blank to start, only the above line is used.

**System Info:**
Ubuntu JeOS 7.10

---

### Post by SpaceTeddy on 2008-04-30
mhm... i have never heard or seen any setup like that.. but ok. 

When the pakets come back, what chain does the kernel file them into ? do they go into INPUT or FORWARD ? Also, a returning paket has it's source altered in PREROUTING, which means a tcpdump should show what destination the replies are trying to go to. Is the reply address correct ?

otherwise, i cannot think of any idea what might be causing this besides your server not being able to find the client... whyever that is. Can the server ping the clients ?

---

### Post by richbayliss on 2008-05-06
I checked packets and all was correct. It just wasnt working.

For some reason IP_Forward kept being disabled after reboot (even though I told it to be set to 1 in a boot script)

Anyway, once ip_forwarding was (re)enabled, the packets went both ways.

Very strange...:confused:

---

### Post by SpaceTeddy on 2008-05-06
i've read/heard that multiple times, that the ipforwarding (despite being explicitly enabled in the sysctl.conf) just got ignored and ip_forwarding was still off...

i don't have the time to go to the bottom of this - but if someone could give me a hint where to start searching i could look around a little what is causing the problem.

good you got it working :)
cheers

---

