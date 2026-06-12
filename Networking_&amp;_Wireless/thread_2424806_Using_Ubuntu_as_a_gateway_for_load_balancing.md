---
title: "Using Ubuntu as a gateway for load balancing"
date: 2019-08-14
forum: Networking &amp; Wireless
---

### Post by hikariws on 2019-08-14
Hello everybody. I'm considering building a gateway at home, to use some services and to load balance 2 ISPs. That's a lot of trouble, so I'd like suggestions if Ubuntu is an adequate distro for that and what tool to use for load balancing.


First, my background. I've used linux for over 15 years ago, good old Kurumin distro. But in all this time I never had real opportunity to use and learn linux, some times I installed it on a VM and used for some days and left. I have no will at all on stop using windows on my Main PC.


3 years ago I bought an Asustor NAS with Busybox, which gave me the opportunity I lacked. Thanks to long past learnings I got on Kurumin it wasn't as hard as I expected to get used to it. Now I have a QNAP NAS also with Busybox.


A few weeks ago then I bought a cheap PC and installed Ubuntu on it. The result has been overwhelming! Both in features and how easy it was to setup things. Currently I have Pihole + BIND, Tor bridge, Dante, Squid, 3 Transmission instances and still have some stuff to setup. I got xming configured on my Main PC and when needed I'm able to use scite to edit bigger configs.


Parallel to this server outstanding success, some stuff on my internet is bothering me, which made me consider having a full grown gateway:


1) When I got a second ISP, I bought Cisco RV340 router to make load balancing. It's a great router and load balancing works under heavy download demands, but for pings and trace routes it always uses WAN1.


2) There are also some websites that bind my authentication to my IP (Ubuntu forum is one of them) and logs me out in some seconds forcing me to drop WAN2 every time I need to use them. I've found no way to setup some IPs to be used only on 1 WAN. IDK how but suppose that I could do that on a gateway.


3) I need to monitor both ISPs availability! RV340 has no availability monitoring for each WAN, and ALAIK there's no way for a NATed devide to choose a route to use. There's no host on neither ISP that's only reachable from inside. In a gateway, I suppose I'd be able to force a ping to go by a unique WAN. Or setup routing so that some destiny IPs will always be routed to the same WAN.


4) As I started working on port forwarding for my services, I discovered that one of my IPSs is using CGNAT and I can't reach home from it using IPv4. But both ISPs are providing me a valid IPv6, which I don't mind using. But I can't get pihole to DHCP IPv6. My PCs have one and can ping each other, but can't ping RV340 and I don't have IPv6 for outside internet. I have to troubleshoot this, but I suppose it'd easier to do on a gateway that has all services instead of having NAT on RV340 and DHCP on another PC.

5) There should be better monitoring softwares, like traffic made by each device and by each WAN.

6) It'd be a greater opportunity to use linux and learn more.


Of course it'll also be harder and I'd have much more to learn. If I decide to proceed, 2019 will be for planning and testing on VMs, and I'd only do it on 2020 after I buy my future new PC and get it all working. And I'll do it so if needed I can just plug cabes back to RV340 and have my LAN back. Before the shift I'll also get the Gateway working with a laptop behind it before plugging it on my LAN.


Anyway, a few years ago I heard about IPFire and even installed it on a VM to see how it is. I first considered using it for my Gateway, as its setup is directly aimed at that and the distro is aimed for such use cases.


But I'm rly getting used to Ubuntu, and finding out that IPFire is a direct distro not built on any other made me flag an alarm, as I'd not be able even to use deb packages and maybe go back to config/make/make install. When I got to its support and saw it only has a small forum, I got scared. Not wanting to disrespect their huge effort, but Ubuntu makes me more comfortable as it has askubuntu, ubuntu forum, has lots of independent sites with lots of articles, and is very popular in general linux community. I started considering having a bigger trouble in beginning to setup networks and load balancing, but then once I learn how to and do it, I'd have more ease of mind.


So, what do you guys think and suggest? IPFire or Ubuntu? Which load balancing solution? Anything will be mostly appreciated.

---

