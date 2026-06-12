---
title: "Routing through IPSEC endpoints"
date: 2018-11-26
forum: Networking &amp; Wireless
---

### Post by teledyn on 2018-11-26
A very novice question: how do I bridge two LANs using ipsec?

I think I have the tunnel itself figured out. I have two LANs that I need to bridge using OpenSWAN ipsec, and I can ping the LAN address of the opposite endpoint from either side, but I'm stuck at how to get the two machines to relay traffic to and from their respective LANs -- I'd hoped this was a common and easy problem, but so far haven't found any recipes online; if there is a good reference page, please point me at it!

Because of dynamic IPs on both sides (our ISP charges $200/month for fixed ip!!) I'm using OpenSWAN and LibreSWAN, on the office side using a raspbian pi2, on the other an AWS EC2 instance in the VPC; necessary UDP and ESP ports are open and I have /proc/sys/net/ipv4/ip_forward = 1 on both sides, and the remote LAN net shows up in the netstat -nr on each gw machine.  On the office side, on a third machine, I added a route giving the pi2 as the gw for the remote LAN subnet, but this other machine on the office side cannot ping the remote endpoint, although the pi2 gw machine itself can, and none can ping any machines beyond the remote endpoint.

What have I missed?

---

### Post by mitesh.agrwl on 2018-11-27
> A very novice question: how do I bridge two LANs using ipsec?

I think I have the tunnel itself figured out. I have two LANs that I  need to bridge using OpenSWAN ipsec, and I can ping the LAN address of  the opposite endpoint from either side, but I'm stuck at how to get the  two machines to relay traffic to and from their respective LANs -- I'd  hoped this was a common and easy problem, but so far haven't found any  recipes online; if there is a good reference page, please point me at  it!

Because of dynamic IPs on both sides (our ISP charges $200/month for  fixed ip!!) I'm using OpenSWAN and LibreSWAN, on the office side using a  raspbian pi2, on the other an AWS EC2 instance in the VPC; necessary  UDP and ESP ports are open and I have /proc/sys/net/ipv4/ip_forward = 1  on both sides, and the remote LAN net shows up in the netstat -nr on  each gw machine.  On the office side, on a third machine, I added a  route giving the pi2 as the gw for the remote LAN subnet, but this other  machine on the office side cannot ping the remote endpoint, although  the pi2 gw machine itself can, and none can ping any machines beyond the  remote endpoint.

What have I missed?

Though it has been tried best but the description is still confusing. Have tried to create a network diagram (check attachment) based on information provided, Check that, if it is correct, add info to that diagram, or you can create a simple one using Libre-Ofiice-Draw or Giffy-Diagrams. It will be easier to troubleshoot with a diagram! 

*Everybody is novice for something. And this is IPsec, needs a lot of practice and patience!

---

### Post by SeijiSensei on 2018-11-27
You need to have a pair of static routes, one on each machine.  My guess is that the remote machine doesn't have a route back to your local network.

---

