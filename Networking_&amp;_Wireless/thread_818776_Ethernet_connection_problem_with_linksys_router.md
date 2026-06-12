---
title: "Ethernet connection problem with linksys router"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by draginx on 2008-06-04
Hello,
I am having trouble getting my PC to connect to my linksys (BEFSR41) router. I have a windows xp machine that connects to this router just fine (using DHCP). When I try to connect the PC directly into the modem, I get the same problem.

My PC is running Ubuntu 8.04 64-bit, with no ndiswrapper. When I restart the network, it says that it has found a DHCP thing and that it's bound to an IP address. But, the assigned IP address, subnet, and gateway are WA different than what is being shown on my windows xp machine. I've also tried to set the gateway, ip, subnet, and DNS nameservers manually and I was still unable to connect. 

My network card info:
Realtek (RTL-8139/8139C/8139C+)
driver = 8139too

The windows xp machine has the same exact network card.

NOTE: The router/modem also gives me problems for my laptop, which is a MCP67 nVidia network card (driver is forcedeth).

I have tried looking through the forums and have tried numerous attempts, but have failed to find a solution. :(

---

### Post by jimv on 2008-06-04
Is the address that the Ubuntu machine is binding to a 169.x.x.x address?

---

### Post by draginx on 2008-06-04
No, it's binding to a 192.168.1.100 address

---

### Post by superprash2003 on 2008-06-04
are you able to ping your router? please post your ifconfig output from the terminal

---

### Post by Coollie on 2008-06-06
> **draginx said:**
> 

NOTE: The router/modem also gives me problems for my laptop, which is a MCP67 nVidia network card (driver is forcedeth).

:(

Try upgrading your BIOS. I didn't have these kind of problems but after a BIOS upgrade (latest release) my problem (incrementing EthX and changing MAC address) was solved. My mobo is a Asus M2N-VM DH. 

Maybe the following links can help you: 
 
[http://ubuntuforums.org/showthread.php?t=766361&highlight=forcedeth]("http://ubuntuforums.org/showthread.php?t=766361&highlight=forcedeth")
[http://ubuntuforums.org/showthread.php?t=745293&highlight=forcedeth]("http://ubuntuforums.org/showthread.php?t=745293&highlight=forcedeth")
[http://ubuntuforums.org/showthread.php?t=739163&highlight=forcedeth]("http://ubuntuforums.org/showthread.php?t=739163&highlight=forcedeth")
[http://ubuntuforums.org/showthread.php?t=779156&highlight=forcedeth]("http://ubuntuforums.org/showthread.php?t=779156&highlight=forcedeth")

Good luck!

---

### Post by J Brian Slinger on 2008-06-06
> **draginx said:**
> Hello,
I am having trouble getting my PC to connect to my linksys (BEFSR41) router. I have a windows xp machine that connects to this router just fine (using DHCP). When I try to connect the PC directly into the modem, I get the same problem.

My PC is running Ubuntu 8.04 64-bit, with no ndiswrapper. When I restart the network, it says that it has found a DHCP thing and that it's bound to an IP address. But, the assigned IP address, subnet, and gateway are WA different than what is being shown on my windows xp machine. I've also tried to set the gateway, ip, subnet, and DNS nameservers manually and I was still unable to connect. 

My network card info:
Realtek (RTL-8139/8139C/8139C+)
driver = 8139too

The windows xp machine has the same exact network card.

NOTE: The router/modem also gives me problems for my laptop, which is a MCP67 nVidia network card (driver is forcedeth).

I have tried looking through the forums and have tried numerous attempts, but have failed to find a solution. :(

This problem seems something like mine. I have a Linksys@home wireless router model HG200 v2 communicating with a Ralink RT2500 802.11g wireless card in a dual 64bit computer. Whilst I can link to the internet using Ubuntu 8.04 (ex a magazine DVD) the download speed is only) 0.15 to 0.35 Mbps whereas I can get 3 to 4 Mbps using Ubuntu 7.10 (64 bit version, downloaded from Ubuntu. This is irrespective of whether 8.04 is installed or is used as a live CD. Both give the same fast rate when connected with an ethernet cable between router and computer.

Funnily enough, I have the same problem with Mandriva 2008 and the later Mandriva One 2008 Spring. As with Ubuntu, this applies irrespective of whether the One version is installed or is being used as a Live CD.

Now how about this? With exception of Ubuntu 8.04 and Mandriva One 2008 Spring, All of the Linux Distros that I have tried give download speeds in the 3 to 4 Mbps range whilst Vista Home Premium gives nearer to 6 Mbps.
Oh Dear! 

Comments Welcome
Regards

---

