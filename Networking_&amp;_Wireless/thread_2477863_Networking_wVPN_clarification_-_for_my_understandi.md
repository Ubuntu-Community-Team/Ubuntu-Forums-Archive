---
title: "Networking w/VPN clarification - for my understanding"
date: 2022-08-09
forum: Networking &amp; Wireless
---

### Post by uacnt83982803 on 2022-08-09
So on my Ubuntu laptop, I am running a paid VPN.  On my local network, I have another Ubuntu laptop (ip 192.168.1.something).  Now, often I Remmina from the 1st laptop into the 2nd laptop.

So is my router recognizing that the 2nd laptop is on my same network and routing the Remmina packets directly to that 2nd machine, or are the packets traveling through the VPN tunnel and back to the 2nd laptop?  I expect that it's the latter, but wanted to verify.  Thanks.

---

### Post by TheFu on 2022-08-09
Use **traceroute** to see.  It is all about the routing.  Most cheap VPNs allow local LAN access without going through the VPN at all.  

Enterprise VPNs are usually (and should be) configured to no allow "split tunnels", so all traffic from the VPN client always goes to the business VPN - all of it.  With this 2nd type of setup, printing to a network printer in your home isn't possible - and it is by far the largest complaint from people at work.  Enterprise security is smart to prevent split tunnels, since it provides a back door into the enterprise LAN by hackers. Not a good idea, especially with typical users having all their IoT/IoSh stuff on the same LAN with their work computer when they work from home.

---

### Post by SeijiSensei on 2022-08-10
Open a terminal on each laptop and enter the command "ip route". If on each side you see an entry like this:
```
192.168.1.0/24 dev eno1 proto kernel scope link src 192.168.1.X metric 100
```
then the traffic isn't leaving your network. 

dev eno1 is my system's Ethernet adapter. If I was connecting with wifi there would be a different entry for dev, but the general structure of the result will be the same. A route exists for the 192.168.1.0/24 network. This connection uses the default of simply broadcasting packets over the wire with a source address of 192.168.1.X. It does not use a router to handle this traffic. Packets intended for other machines on the 192.168.1.0/24 network will see this traffic, and, if a packet has a destination address matching that machine's IP address, it will be accepted.

Ethernet is a remarkable protocol. Basically all the machines on the network just scream at each other and rely on their targets being able to "hear" them.

---

