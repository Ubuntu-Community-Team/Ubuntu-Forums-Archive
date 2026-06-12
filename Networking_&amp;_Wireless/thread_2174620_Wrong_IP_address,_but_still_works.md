---
title: "Wrong IP address, but still works"
date: 2013-09-15
forum: Networking &amp; Wireless
---

### Post by raac on 2013-09-15
I have a question about networking. To be honest I don't why my virtual box OS (lubuntu) has internet. I did a ifconfig and according to the OS my internal IP is 10.0.2.15. But my subnet starts with 192.168...

The reason I bothered to check this was because I went to my router configuration page because I wanted to open port 22, but my virtual computer didn't show up in the list. I went ahead and check the ip of it and realize it is that weird IP, could that be the reason of it not showing up in the list?. I'm afraid if I change the IP the internet would stop working since I would have to change the subnet.

Any advice would be appreciated.

Thanks

---

### Post by steve_clark2 on 2013-09-15
Check routes on the host.  It could be that the host is routing to a private network using NAT.

---

### Post by coffeecat on 2013-09-15
The reason your virtualbox Lubuntu has an IP of 10.0.2.15, is that there is a virtualbox NAT engine. From the VirtualBox manual:

> The virtual machine receives its network address and configuration on the private network
from a DHCP server integrated into VirtualBox. The IP address thus assigned to the virtual
machine is usually on a completely different network than the host. As more than one card of
a virtual machine can be set up to use NAT, the first card is connected to the private network
10.0.2.0, the second card to the network 10.0.3.0 and so on. If you need to change the guestassigned
IP range for some reason, please refer to chapter 9.10, Fine-tuning the VirtualBox NAT
engine, page 145.

There's more in the VB manual, including setting up port forwarding.

---

### Post by Shrek01 on 2013-09-15
If you want your virtual machine to be in the same subnet:
Open your VirtualBox Manager and click on 
Settings (for that VM) -> Network -> and change the "Attached to" from NAT to Bridged Adapter

---

### Post by raac on 2013-09-15
Yep, that was the problem. I changed the network interface in virtual box to be "Bridged Adapter" instead of "NAT".

Thank for your help!!.

---

