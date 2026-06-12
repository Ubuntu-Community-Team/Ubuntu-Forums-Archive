---
title: "Can I improve my routing speeds with dual gigabit?"
date: 2018-07-17
forum: Networking &amp; Wireless
---

### Post by jonathanese on 2018-07-17
I have an Ubuntu 18.04 server which is running as my router, and I'm using WebMin to configure things.

So I have an onboard gigabit port as well as a dual-gigabit card. My onboard port is used as my WAN connection while one of my NIC gigabit ports is used for LAN routing.

Anyway, I realized at work that I can use two gigabit ports on a NAS to get an effective total of 2Gb (though not to a single device) and both ports appear on the network as a single IP. I'm not sure how this works on a 1Gb switch.

I would think 1Gb would be the total bandwidth available across all devices combined. However my own 24-port Netgear switch reports a "48Gbps" total bandwidth, so clearly I didn't learn something right.

But otherwise, is there a way I can use my two gigabit ports on my server to potentially speed up my total routing capability? I hadn't looked much into this kind of load-balancing. Most of what I've used has been load balancing WAN connections, not LAN connections.

---

### Post by jonathanese on 2018-07-17
Never Mind. I'm not used to netplan, so I looked up bonding in netplan.

HOLY CRAP that was simple.

Just define your lan connections, then set up a bond as though it is a lan connection with 2 interfaces, and voila! Worked right away without hiccup.

---

### Post by 1clue on 2018-07-18
Realistically, it depends on:
[LIST=1]
[*]Your switch.
[*]Your computer.
[*]Your nics.
[/LIST]

The switch needs to not be a bargain-basement switch. High quality switches with X ports of Y bandwidth have a backplane which can support X*Y total bandwidth, or very close to it. Add routing and firewall to that and things often slow down. The best routers can still go very close to wire speed on all ports.

Your computer needs to have enough CPU to handle the traffic. I see people trying to make a switch out of a raspberry pi by adding one or more gigabit usb ethernet nics, it won't work in any stretch because the board will not handle that bandwidth, period. Some communications-specific atom processors could handle multiple gigabit networking, but not all of them.

Your nics. Here's the deal most people don't get. A really good NIC will implement all or almost all networking right in the card. It pulls data from your network and sticks it in RAM directly, leaving your CPU free to do whatever it wants.

A cheap NIC is sort of like a win modem from back in the 90s. Win modems had very minimal hardware and relied on special drivers to make them work. Linux couldn't use them because the drivers were Windows-specific. This approach happens when a company wants to make maximum profits. They put out crappy cheap hardware, then rely on the CPU to finish the job. So while a high-end system will probably still get wire speed or near wire speed from the crappy NIC, there will be a lot more interrupts to the CPU and the CPU load goes up much more than it should.

I hope you got Intel NICs, that use the igb driver. That's the best NIC I know of in the gigabit range. My example of a crappy gigabit nic is Realtek. I have hardware with Intel and other hardware with Realtek. The difference is so profound that I will not buy any new hardware with any realtek device on it.

If you do some searching in Google you'll find many people saying similar things. It's not just me.

---

### Post by The Cog on 2018-07-18
As I understand i, you also need to configure the switch for bonding its two ports. If you don't it won't use both ports to send you packets, but just sne packets to your PC over whichever one it last received a packet from your PC on, as though you keep moving the PC from one port to the other. It will probably also send broadcast/multicast packets to you on both ports leading to you receiving duplicated packets.

P.S. I see no point in having a 2GB bonded LAN connection if you only have a 1GB WAN connection.

---

### Post by jonathanese on 2018-07-18
"[COLOR=#000000]Your computer needs to have enough CPU to handle the traffic."
It's my previous desktop. Core i5 3570K with 16GB of DDR3.

Of course, it's also managing two ZFS pools, Plex, home automation through Home Assistant, network-wide adblocking and DNS, SQL server, and hell, I might throw a minecraft server on it as well. CPU usage stays pretty low. Rarely seeing it get over 50% and the CPU temp stays at 27C consistently. Though ZFS sees me using ~80% of my RAM which is fine by me.

"[/COLOR][COLOR=#000000]P.S. I see no point in having a 2GB bonded LAN connection if you only have a 1GB WAN connection."
Technically my WAN is 100Mbps internet coming from my modem. But the server is also my router, so all LAN traffic goes through it, as I understand. So it won't make my internet faster, but the point is to speed up my network between devices.

I'm not expecting 2Gbps transfers between two individual devices. That would be impossible as it's limited by the device's network interface. But I figure I could do things have one device doing 1Gb transfers without slowing down the other devices such as netflix streams or lighting control or whatever else.

But yeah, My speeds are actually a few percent slower after making the change, so [/COLOR][COLOR=#000000]I may have to reconfigure routing because I don't think it's listening for traffic on the other port. [/COLOR][COLOR=#000000]I think it keeps trying the other interface, failing, and then reverting to the original. Of course, WebMin is now giving me a "PERL execution failed" error on the IPTables page, so I'll have to resolve that before I can go much further. As much as I try to stick with command line, I still have to ease into it to understand the ins and outs well enough to command-line it all.[/COLOR]

---

### Post by 1clue on 2018-07-18
Bonding 2 ethernet devices must be configured on both ends of the cables. The switch and the PC must both understand that the nics are bonded.

CPU: It's not so much about having a fast system but low latency. Intel is making atom processors specifically for communications tasks. A fast system with a lot of other junk going on is not going to get wire speed because of latency.

LAN vs WAN: If every system in the building is simply using the Internet then it makes no sense to have LAN ports any faster than the WAN port. If you have 3 people gaming on the local network, or you have a LAN backup of really big drives, or whatever else might cause hosts on the LAN to talk quickly then it may make sense to bond ethernet together.

And for that matter if you have 2 hosts which are bonded to the switch (2 hosts, 4 cables) and you have a process talking through multiple sockets between them, then they can benefit from the bonded channels.

---

### Post by 1clue on 2018-07-18
While this example doesn't exactly fit into the scope of the OP's question, it may shed light on possible faster communication using multiple nics.

It's not that uncommon to run a separate point-to-point network connection from, say, a database server and an application server. Or any other two hosts that have a large amount of traffic specifically between them. No switch, just cables. That too can be bonded if necessary.

You would add a static point-to-point route on each host directing traffic to the other host to go through the special-purpose NIC. Then they use the IP address and have no reference to any outside system through that connection. Meaning that "network" has no routing in or out of the network. It's even possible to get rid of TCP/IP altogether and use pure ethernet communications. The goal is to (a) free up traffic on the LAN and (b) reduce traffic on the high-speed pipe to only that which is necessary in that situation. Packet header size is smaller, no DNS, nothing that takes extra traffic.

---

### Post by The Cog on 2018-07-20
If all the LAN devices are in the same IP subnet (e.g. all 192.168.0.*) then they don't need to talk via the server/router at all - they will talk directly to each other via the LAN/switch. In which case bonding two cables between switch and router is not going to make any difference. 

And even if they are on different subnets, the router should issue a redirect message that effectively says that "For IP address X don't send packets via me in future, but send them directly to Y instead". The router should still have minimal involvement in relaying traffic.

---

### Post by jonathanese on 2018-07-20
Ohh. OK thanks.

So that is actually related to an issue I had at work. We had debated whether or not adding a gigabit switch on a 100Mbps router would give us gigabit speeds between devices, or if we would be limited to 100Mbps.

Sounds like we would be getting gigabit speeds, just with possible slowdowns on things like DHCP.

---

### Post by The Cog on 2018-07-21
> **jonathanese said:**
> Ohh. OK thanks.

So that is actually related to an issue I had at work. We had debated whether or not adding a gigabit switch on a 100Mbps router would give us gigabit speeds between devices, or if we would be limited to 100Mbps.

Sounds like we would be getting gigabit speeds, just with possible slowdowns on things like DHCP.

Go for it. You should see a big improvement, and I don't think the switch will add any significant delay to DHCP processing. For traffic that traverses the WAN, the delay in the switch will be insignificant relative to the WAN latency so no worries there either.

---

### Post by caberry9 on 2018-07-21
[COLOR=#000000][FONT=&quot]If you want top speeds in your home, you'll want to save room in your remodeling budget for running gigabit Ethernet network cables (CAT5e -- or better yet, CAT6) to every room in your home. Ethernet is the only connection standard where the real-world speeds are very close to, or even match, the lofty theoretical speeds.[/FONT][/COLOR]

---

### Post by TheFu on 2018-07-22
> **The Cog said:**
>  
P.S. I see no point in having a 2GB bonded LAN connection if you only have a 1GB WAN connection.

Internal transfers. If you deal with videos and video editing,  it makes a huge difference.  And for backups.  Why spend 30min on a backup when it can finish in 15min?

Even if you are on dial-up internet, your LAN doesn't need to be slow.

I can confirm that on the same subnet, systems connected to GIgE switches with just local ethernet connections don't care what the   router speed might be. Systems within the same netmask "find" each other to talk directly at switch speed.

BTW, bonded connections require a switch/router that supports that protocol.  Unmanaged switched do not. I think the cheapest managed switch that supports bonding is around $150, so not too bad, but still 10x than a cheap, unmanaged, switch.

Netflix streams are tiny compared to GigE bandwidth. Bonding or not, it won't matter unless the interface  is already flooded,which is doubtful.   Perhaps if you had multiple enterprise SSDs in a RAID0, you could, in theory, but probably not. Spinning disks won't. Consumer SSDs won't, in the real world.

---

