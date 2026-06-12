---
title: "Help connecting two computers using Ethernet, to a third using Wi-Fi"
date: 2017-02-16
forum: Networking &amp; Wireless
---

### Post by epsilonjon on 2017-02-16
Hi.

I am working on a robotics project where I am running two single board computers with Ubuntu 14.04.5 on the robot, which communicate over Ethernet. However, I also need to send data back to a desktop (also Ubuntu 14.04.5) over Wi-Fi:


---------------------------- Robot ----------------------------
Computer A -------- ethernet --------- Computer B -------- wifi ------- Computer C (Desktop)
                     

I am able to set Computer B up as access point, and  can then connect it to Computer C. However, this means that Computer B has one IP address from the perspective of Computer A, and a different IP address from the perspective of Computer C. Unfortunately, due to the nature of the  underlying robotics software (Robot Operating System), this is not acceptable.

I believe that the way around this is to bridge the Ethernet and Wi-Fi interfaces of Computer B? Unfortunately I'm not very experienced with networking and i've been unable to understand how to implement this. Would anybody be able to give me some assistance please?

I would very much appreciate any help.

Many thanks.

---

### Post by TheFu on 2017-02-17
Welcome to the forums.  

Unfortunately, I can't understand the issue, so I cannot help.
A networking primer:
[https://www.cisco.com/en/US/docs/security/vpn5000/manager/reference/guide/appA.html](https://www.cisco.com/en/US/docs/security/vpn5000/manager/reference/guide/appA.html)
Ignore all the non-IP stuff.  IPX/Appletalk don't apply.

I don't think you want a bridge. I think you need a router if the devices are on separate networks.  Seems it would be easier to put them all on the same subnet and manually make any routes to each device as required.  That means 
* A would have 2 routes to B and C
* B would have 2 routes to A and C
* C would have 2 routes to A and B

This is what switches and routers do for us. IF you can't or won't have those devices, you'll need to manually tell each system how to find the others.

If you posted the subnets and IPs for each device, perhaps someone could be more help?  An **arp** table might help too.

Or I could be completely wrong and missing the point.

---

### Post by SeijiSensei on 2017-02-17
Can computer B not also act as a router?  If A and B are running some form of Linux, can you turn on packet forwarding in /etc/sysctl.conf on B?  Then A and C should be able to communicate via B.

---

