---
title: "Can't connect SSH trough wireless"
date: 2014-10-15
forum: Networking &amp; Wireless
---

### Post by mario42 on 2014-10-15
I am having troubles connecting to ubunt via ssh/smb trough wireless. When I try to connect trough Eth it works just fine, but wireless de nada. I thought it was something with the router, I saw no options there; (although its a IPS T-Home Huawei router). Then I did another test, enabled SSH Server on one machine (laptop) and connected from another laptop it worked just fine... So I guess the router is not blocking anything related to SSH.

any clues?

---

### Post by Lars Noodén on 2014-10-15
Are the wireless devices and the ethernet on the same LAN?  Some set ups have them on separate subnets.

---

### Post by mario42 on 2014-10-15
> **Lars Noodén said:**
> Are the wireless devices and the ethernet on the same LAN?  Some set ups have them on separate subnets.

Thanks for your reply. I have my eth interface disabled. At the end its not possible to have same subnet on 2 interfaces on 1 machine.

---

### Post by davit2 on 2014-10-15
when your ethernet is disabled, can you do ping to remote machine?

---

