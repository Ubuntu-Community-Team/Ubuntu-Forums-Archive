---
title: "Ubuntu 17.10 Ethernet Adapter Loses IPV4 Address"
date: 2018-05-02
forum: Networking &amp; Wireless
---

### Post by 7-webmaster on 2018-05-02
The following is something mysterious that was resolved by rebooting the Ubuntu 17.10 system.  I would just like to understand why it happened.

I sat down at my desktop computer and discovered that it had lost network connectivity.  As a desktop its only connection is by cable to my home router.  When I looked at the network interface under settings it showed no IPV4 address, just an IPV6 address.  Everything else looked fine.  The light on the router for the Ethernet port was on.  The obvious explanation is that somehow an IPV4 address had not been obtained from DHCP in the router, but I had been using the computer an hour before without difficulty.  The IPV6 address does not require DHCP.  So the question is how Ubuntu "lost" the IP address and why when it lost the IPV4 address it didn't ask the DHCP to restore it?

---

### Post by 1clue on 2018-05-03
Do you by chance have a cisco/linksys router?

I had this same experience, only for me most of the devices in my house lost connectivity except to sites with ipv6 addresses.

For awhile there I was rebooting my router at least once a day, then the ipv4 addresses would come back. Sometimes I had to either reboot the device or reset the network connection before the individual device came back. I still have to do this occasionally.

---

### Post by 7-webmaster on 2018-05-03
I did not reboot the brand-new Smart/RG router, which was working fine for all of the other devices.  I rebooted my Ubuntu desktop.

---

### Post by 1clue on 2018-05-03
Sounds like you may have a different problem related to the same thing.

My router was brand new when this happened.

---

