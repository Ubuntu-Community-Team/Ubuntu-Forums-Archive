---
title: "Can no longer connect"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by adzik on 2007-03-19
Maybe someone has dealt with this before.
My motherboard decided to stop working, so I had to get it replaced by ASUS.
I had Edgy installed on that system though, with everything working great.
The replacement motherboard came in,  I plugged it all back together and, everything works as if nothing happened, except for the NIC.  I didn't expect it to work at all with the motherboard being replaced actually.
It was identified as eth0 before, and now it is eth1. I only ever had 1 nic.
So the problem is that it won't pick up an IP address from my router.  It is able to see all the other information (DNS, address range, subnet etc.) but won't actually capture an address.
***ifup eth1*** gives me:

 [I][B]No DHCPOFFERS received.
No working leases in persistent database - sleeping[/B].[/I]

Since I'm not familiar with this stuff, this is where need help.
Thanks.

---

### Post by DrOlaf on 2007-03-19
This doesn't usually apply to wired connections, but did you turn on MAC address filtering on your router? If you did, and you have a new mobo with a new NIC, it will have a different MAC address and your router will refuse to give it an IP.

---

### Post by Mr. C. on 2007-03-19
Plug back into eth0, and do:

```
sudo ifdown eth1
sudo ifdown eth0
sudo rm -f /etc/iftab
sudo reboot

```
see if that helps.
MrC

---

### Post by adzik on 2007-03-19
The second suggestion worked. 
After reboot, it connected without a hitch. I guess that means I need to keep learning more about linux.
Thanks MrC.
That was the fastest help I think I've ever gotten anywhere!  :)

---

### Post by Mr. C. on 2007-03-19
Great!

The learning... is a life long process.

Cheers,
MrC

---

