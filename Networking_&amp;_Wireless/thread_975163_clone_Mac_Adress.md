---
title: "clone Mac Adress"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by realthor on 2008-11-08
Hi guys,

I am using ubuntu 8.10 and I want to connect to a pppoe ISP ocasionally but although the connection is set up identically as on the Windows PC that is permanently connected to the ISP when I plug in the cable the connection isn't ,ade.

I suspect the ISP filters by MAC but i wasn't able to get the MAC cloned on my linux laptop.

ipconfig shows for windows an ip like 00-1B-FC-F7-71-F7

but when I try in linux:

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00-1B-FC-F7-71-F7

i get:

00-1B-FC-F7-71-F7: Invalid ether address.



Thanks.

---

### Post by helgman on 2008-11-08
If you just use ifconfig eth0 you'll see your current MAC and the format used in Linux.

Regards,
Helgman

---

### Post by realthor on 2008-11-10
Solved, my bad...

I should have used ":" instead of "-" for the MAC format.

regards.

---

