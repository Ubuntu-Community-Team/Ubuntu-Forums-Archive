---
title: "Assign TUN to physical NIC"
date: 2020-04-29
forum: Networking &amp; Wireless
---

### Post by finnjaeger on 2020-04-29
Hey everyone, 

so due to the bad internet situation in Germany, i am forced to run 2 seperate ISPs, 2 seperate routers , 2 seperate NICs on my workstation. 

Now I also have 2 seperate VPN connections to 2 different endpoints.  

So naturally I want to split them to have "double" the bandwidth, and Isp 1 has better routing to location A and ISP 2 better routing to Location B, so it makes sense to split. 


The easy way out would be using 2 seperate machines and synergy, but thats not cool, and thats what ive been doing so far.   Thats why I am thinking if its possible to assign the virtual tun interface to run via NIC 1 or NIC2. 

eno1  192.168.178.0/24
en6f0 192.168.169.0/24

Now the first problem I found is that network manager creates the TUN virtual Nics on the fly.  

Maybe, as the endpoint IPs are static I could do something with static routes.? 

Destination IP X --> en0
Destination IP Y --> en6f0


I am using high res remote Desktop (HP RGS) to both locations at the same time and I am streaming video, so I really seeing the bandwidth being a bottleneck.  
Virtual machines are not a option 
I tried to bond the 2 WANs in a cisco router but performance was really bad. 
Running Ubunu 18.04 
OpenVPN 
Both WAN connections are arount 75Mbit/s Down  35Mbit/s Up

Thank you!

---

