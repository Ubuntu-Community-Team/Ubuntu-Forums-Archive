---
title: "Transparent Bridge - Packet loss"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by forbjok on 2008-11-17
After installing Ubuntu 8.10 server on a Compaq Proliant (can't remember the exact model number) rack server, I set up the two Ethernet interfaces, both using the Intel Ethernet Pro 100 chipset, as a bridge. (by specifying bridge_ports in the interfaces file)

However, when I connect the network through the bridge, it results in considerable packet loss (at least 11% in the relatively short time i tested it).
When I have the main internet connection connected directly to the Cisco switch outside the Ubuntu server, there is no packet loss.
Also, when I connected a laptop to the same Ethernet port on the server and tried pinging stuff on the other side, there was no packet loss.

This is a relatively heavily loaded network (a small ISP network actually), so there will be a lot of traffic on it.

Therefore I was wondering if maybe there is some sort of network buffer somewhere that will cause packets to be dropped if it runs out of space.

Is there such a buffer, and if so, how can I increase it to avoid packet loss under heavy load?

(Of course, any other suggestions as to what might cause the packet loss, or how to fix it, are welcome :) )

Thanks in advance.

---

