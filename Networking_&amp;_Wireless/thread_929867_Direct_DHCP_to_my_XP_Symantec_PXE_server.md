---
title: "Direct DHCP to my XP Symantec PXE server?"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by bumthology on 2008-09-25
Hi!
I'm wanting to boot into my Windows XP machine which is running Symantec Ghost Cast server. In the services of this machine i also see it running PXE which i've already setup and it runs its own TFTP. The IP for this server is 210.8.69.121

My DHCP server is linux with these current configurations. None of my clients network boots work, they just load into windows when i want them to load from the network. What am i doing wrong?

subnet 210.8.69.0 netmask 255.255.255.128 {
        range 210.8.69.117 210.8.69.119;
	next-server 210.8.69.121;	
	option subnet-mask 255.255.255.128;
	option routers 210.8.69.1;
	option domain-name-servers 203.25.185.2, 203.25.185.3;

---

