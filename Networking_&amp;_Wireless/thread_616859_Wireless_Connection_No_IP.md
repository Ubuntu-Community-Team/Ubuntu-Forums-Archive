---
title: "Wireless Connection No IP"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by dalezjc on 2007-11-18
I'm using the latest LIVE CD and I can connect to my wireless AP without problem, but I don't get an IP address from it.  I can use other Live distros and they get IPs  just fine so what's the issue with Ubuntu?  I assume I have to use some sort of command line trick to get an IP?

Thanks,
Dale

---

### Post by moe_syzlak on 2007-11-18
Is the wireless network encrypted?

---

### Post by dalezjc on 2007-11-20
I'm using WEP.

Dale

---

### Post by elctb on 2007-11-20
Try configuring the key with the "iwconfig" command:

iwconfig eth0 key <your-key>

You need to issue the above command from a terminal.

---

