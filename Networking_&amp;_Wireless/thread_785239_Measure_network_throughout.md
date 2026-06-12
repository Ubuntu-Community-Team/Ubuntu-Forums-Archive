---
title: "Measure network throughout"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by chrislynch8 on 2008-05-07
Hi,

we have a Ubuntu server and we are setting up VPN using openVPN. I want to test the throughput over this secure channel by simulating real data uploads/downloads etc.

Does anyone know of a nice program that can take care of this. When searching google etc. it was all pricey software, I'm looking for a free application freely available.

Rgds

---

### Post by Monicker on 2008-05-07
You could give iperf a try.  I've used that in the past to test site to site vpn tunnels.  Its in the Ubuntu repos.

---

### Post by yogensha on 2008-05-07
iperf:

[http://dast.nlanr.net/Projects/Iperf/](http://dast.nlanr.net/Projects/Iperf/)

The default settings will run a TCP flow between 2 points and basically give you an idea of the maximum throughput.  It runs on windows too.

There are myriad others, but this is my favorite.

---

### Post by chrislynch8 on 2008-05-07
Thanks,

I will give it a try.

Rgds

---

