---
title: "Not able to access Ubuntu on Virtualbox from another machine in the network"
date: 2013-11-09
forum: Networking &amp; Wireless
---

### Post by rony.kris on 2013-11-09
Hi,

I have Ubuntu (12.04) running as a guest OS on VirtualBox. I have a network port configured as NAT and another one is bridged. Through the bridged port i am able to ssh into the VM form the host. I am able to access the internet via the NAT configured port. 

What i want is; access to the VM on the NAT configured port from other machines on the network. I mayhave a webserver running on that port eventually and want to access it from outside the Host machine. Can someone help please?

Thanks,
Krish

---

### Post by SeijiSensei on 2013-11-09
If you want to access the VM from outside the host, you should use a bridged adapter.  It's possible to use NAT, but you'll need to write iptables rules to forward the outside traffic to the VM guest.  Bridging is by far the simpler method.

---

### Post by rony.kris on 2013-11-09
I have another port configured as "bridged". Using this i was able to sssh into the VM from the host. But the outside network cannot access the VM through it. I'm guessing it requires some changes to the configuration, but not sure exactly what.

Also, if one of you can tell me what rules should be created in the iptables to use the NAT configured port for outside traffic i'll be very eager to try it.

---

