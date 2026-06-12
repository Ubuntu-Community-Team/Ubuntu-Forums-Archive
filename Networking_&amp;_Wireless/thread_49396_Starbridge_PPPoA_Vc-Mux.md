---
title: "Starbridge PPPoA Vc-Mux"
date: 2005-07-16
forum: Networking &amp; Wireless
---

### Post by shmk on 2005-07-16
I have a Starbridge-EU plugged through an ethernet cable to my pc.

With pppoeconf ubuntu can found an ethernet device but can't found a connection to my provider.

The problem is that my provider use "pppoa vc-mux" instead of "pppoe" ?

Someone cna give me a hand ?

PS: i'm using a multi-boot system with ubuntu hoary and winxp; on winxp the router is function properly.

---

### Post by shmk on 2005-07-18
No one have this problem ?

"router connect through ethernet but protocol is pppoa"

---

### Post by shmk on 2005-07-18
[QUOTE=shmk]No one have this problem ?

"router connect through ethernet but protocol is pppoa"[/QUOTE]
 Found the solution:

"Simply have to lanch from console dhcp ( "dhclient3" on my system ) and then from the browser type 10.0.0.2 , the router configuration starts ^_^"

---

