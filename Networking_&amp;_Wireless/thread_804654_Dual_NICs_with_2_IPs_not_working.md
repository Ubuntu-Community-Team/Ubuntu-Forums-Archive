---
title: "Dual NICs with 2 IPs not working"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by Rob K on 2008-05-23
Hi
I have 2 NIC's in a IBM server and running VMWare Server on Ubuntu.
The plan is to have one NIC on my LAN with a private IP and the other NIC connected to the Internet.
Then I will map my VMs onto the WAN NIC as they will be webservers.

I am currently testing with both NIC's on my LAN and set to use DHCP but only on card gets an IP, the other doesn't.
I have eth0 & eth1, eth0 has an IP, eth1 doesn't - why not?

When I boot the server it seems to default to the card with no IP so I cannot get to the box via the LAN - again - why?

Any help much appreciated...

---

### Post by EoRaptor013 on 2008-05-28
I'm having a similar problem; hope you get an answer. 

I've got an integrated gigabit card on my Asus P5K mobo as eth0, and I threw a Linsys 10/100 card into a pci slot as eth1, then installed Hardy. A fresh install on clean new disks in a newly completed custom-built. Both were configured with static, behind the Belkin router, IPs. (Oh, and just to throw another wrench in, the mobo has an integrated RTL8187 wifi adapter.) 

Using Network Tools, both adapters show their correct static IP addresses. However, I was not able to get OpenVPN to work. Somewhere along the way, I noticed that eth1 had become the default system interface -- I can only get to the web, email, etc. through that adapter. Using ping -I eth0 [www.ubuntu.com](www.ubuntu.com), and observing interface activity with gkrellm, I see that while eth0 is transmitting, eth1 is both receiving and transmitting. This suggests that eth0 is, somehow being routed to eth1, even though there are no explicit routes for it. 

Any help would be greatly appreciated. 

Randy

---

### Post by Iowan on 2008-05-28
> **Rob K said:**
> 
I have eth0 & eth1, eth0 has an IP, eth1 doesn't - why not?

When I boot the server it seems to default to the card with no IP so I cannot get to the box via the LAN - again - why?

Any help much appreciated...I've been wrong before (and have no background with VMWare server)...  dunno if the system will tolerate two NIC's in the same subnet especially via DHCP.  Assigning one via static address (or via static lease) *might* work.

[Similar thread]("http://ubuntuforums.org/showthread.php?t=810423")

---

