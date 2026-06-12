---
title: "Intel NIC - need recommendation please"
date: 2014-02-18
forum: Networking &amp; Wireless
---

### Post by incurablegeek on 2014-02-18
I need a recommendation for both a single port and multi-port PCI-e NIC for use in a Network Appliance (firewall).

Presently using CAT-7 cable, Cisco 2911 router and Cisco SG-300 switch.

Note: **Must be Intel NIC**

Currently prepping for Cisco CCENT test but baffled by wide range of pricing and features in NIC's. Briefly, this network appliance with run **pfSense on Ubuntu 12.04.4 LTS** and function as a firewall, then Cisco 2911 router and on to Cisco SG-300 switch with 5 computers, server and other hosts.

Point of confusion: I see that most Intel NICs are rated as CAT-5, which I would assume to be a minimum and not a maximum?

[B]Questions:

1) Why the wide range of pricing in NIC's?

2) Would two PCI-e single port NICs work better than a multi-port NIC?

3) Your recommendations?
[/B]
Thanks guys! :)

---

### Post by lukeiamyourfather on 2014-02-18
> **incurablegeek said:**
> 
Presently using CAT-7 cable, Cisco 2911 router and Cisco SG-300 switch.


Those devices are for 1GbE so you don't need Cat 7 cable, only Cat 5e or Cat 6 is necessary.

> **incurablegeek said:**
> 
Note: **Must be Intel NIC**


Why? That shouldn't matter from a technical standpoint.

> **incurablegeek said:**
> 
...baffled by wide range of pricing and features in NIC's.


The number of ports, speed of the ports, and type of ports can greatly affect the cost. Also some adapters have support for iSCSI, VLAN, and other functionality.

> **incurablegeek said:**
> 
Point of confusion: I see that most Intel NICs are rated as CAT-5, which I would assume to be a minimum and not a maximum?


Use cabling appropriate for the speed of the network. If the network is 1GbE then you don't need cabling meant for 10GbE or 40GbE.

[http://en.wikipedia.org/wiki/ISO/IEC_11801](http://en.wikipedia.org/wiki/ISO/IEC_11801)

> **incurablegeek said:**
> 
Would two PCI-e single port NICs work better than a multi-port NIC?


Define "work better" because that could mean a lot of things. If you only have one open expansion slot and you need two interfaces then obviously an adapter with two interfaces works better. Though having two adapters with a single interface on each gives more flexibility down the road because you can put them into different machines and they're not stuck together. It all depends on what you want to do with them and what the circumstances are.

> **incurablegeek said:**
> 
Your recommendations?


That depends on what features you're looking for. Intel has a document that might help you narrow down the features that you need.

[http://www.intel.com/content/www/us/en/network-adapters/gigabit-network-adapters/gbe-server-selection-guide.html](http://www.intel.com/content/www/us/en/network-adapters/gigabit-network-adapters/gbe-server-selection-guide.html)

---

### Post by incurablegeek on 2014-02-18
1) "Those devices are for 1GbE so you don't need Cat 7 cable, only Cat 5e or Cat 6 is necessary."  The operative word here would be "necessary". I always opt for ideal. And CAT-7 offers significant improvement over 5e and 6.

2) Intel Nic only: "Why? That shouldn't matter from a technical standpoint." Most everyone deeply involved in networking would take issue with that. Drivers, compatibility, etc.

3) "Define "work better" because that could mean a lot of things."  Just that. Better throughput due to separate BUS

4) [http://www.intel.com/content/www/us/...ion-guide.html](http://www.intel.com/content/www/us/...ion-guide.html)  I of course know of this guide and have visited it several times.

Was kinda hoping for some tangible info and suggestions here. Thanks anyway.

---

### Post by lukeiamyourfather on 2014-02-19
> **incurablegeek said:**
> 1) "Those devices are for 1GbE so you don't need Cat 7 cable, only Cat 5e or Cat 6 is necessary."  The operative word here would be "necessary". I always opt for ideal. And CAT-7 offers significant improvement over 5e and 6.

2) Intel Nic only: "Why? That shouldn't matter from a technical standpoint." Most everyone deeply involved in networking would take issue with that. Drivers, compatibility, etc.

3) "Define "work better" because that could mean a lot of things."  Just that. Better throughput due to separate BUS

4) [http://www.intel.com/content/www/us/...ion-guide.html](http://www.intel.com/content/www/us/...ion-guide.html)  I of course know of this guide and have visited it several times.

Was kinda hoping for some tangible info and suggestions here. Thanks anyway.

The differences in Cat 5e/6/7 are a moot point if you're using 1GbE. Literally no difference at all in performance but if you want to waste money on cabling nobody is going to stop you. Intel does make reliable and widely supported network adapters, however so do a lot of other companies. If you want an Intel adapter by all means buy one. Modern busses like PCI Express have more than an order of magnitude more bandwidth than a 1GbE adapter could need so you don't have to worry about that. I would give tangible suggestions if you would give tangible requirements. If the only requirements are it has to be 1GbE and Intel then go for the a no frills adapter like the I210-T1.

---

