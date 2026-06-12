---
title: "Wireshark"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by fly_boy on 2010-04-04
Hi, everyone, is anyone on here a whizz on wireshark???

Thanks

Alan

---

### Post by HermanAB on 2010-04-04
just google for a howto - easy.

---

### Post by fly_boy on 2010-04-04
Part of the problem is trying to find the right question if you know what I mean????


I can capture TCP and HTTP traffic between the wireshark host and the router, but not between any other machine and  the router...

I can ping these boxes and get a response, but strangely I cannot traceroute to them...

I want to trap traffic between these other machines and the router, any ideas????

---

### Post by stderr on 2010-04-04
Are you in promiscuous mode? (edit: set it in Capture Options)

---

### Post by fly_boy on 2010-04-04
Sure am!!! I seem to see all the LLC packets, and all the Ethernet packets. But no TCP HTTP Packets...

Even though I am generating traffic using a laptop connected to the same network...

---

