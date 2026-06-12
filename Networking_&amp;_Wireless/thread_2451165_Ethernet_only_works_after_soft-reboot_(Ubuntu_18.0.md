---
title: "Ethernet only works after soft-reboot (Ubuntu 18.04.5 Server)"
date: 2020-09-28
forum: Networking &amp; Wireless
---

### Post by 5-john on 2020-09-28
I'm trying out an engineering sample of a Rock Pi X ([https://wiki.radxa.com/RockpiX](https://wiki.radxa.com/RockpiX)) and am having problems with the Ethernet connection.  On a cold boot (from power disconnected to power on), the Ethernet connection fails to obtain an DHCP address and when its configured for static, it still cannot reach the connected router... arp shows nothing.  If I do a simple reboot (sudo shutdown now), Ethernet works with no problem and all is good.  I've reinstalled Ubuntu 18.04.5 and had the same problem.  I then installed 20.04 and it works without an issue, so I suspect its something specific to 18.04.  I don't know where to look to try to troubleshoot this.

---

### Post by TheFu on 2020-09-28
> engineering sample
This is preproduction and you'll need to get wireshark capturing packets to figure out what might be happening.
Use the OS that the vendor suggests. 

It could easily be a driver incompatibility with new hardware that just isn't supported by older versions of the kernel.

---

### Post by 5-john on 2020-09-29
Thanks for the reply.  Using wireshark to figure this out is beyond my technical skills.  It was an engineering sample that they graciously provided me for a mid-life crisis project I'm working on (building a robot).  They thought there would be no problem using 18.04 so they sent me one.  It uses a RTL811F ethernet controller and I was hoping the problem would be something relatively simple so I could include it in their wiki so if someone else tries to install 18.04, they have a solution.  I'll try to see if there is an updated driver for it, but its weird that it if it is a driver issue, why would it work after a soft reboot and not a cold boot?

---

