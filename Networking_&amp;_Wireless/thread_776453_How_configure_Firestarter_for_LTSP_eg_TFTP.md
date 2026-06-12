---
title: "How configure Firestarter for LTSP eg: TFTP?"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by haz2a on 2008-04-30
I can only boot LTSP clients when the firewall is disabled via Firestarter.
I have allowed the following inbound services: DHCP(67-68), NFS(111+2049), SSH(22), UDP(2070), UDP(69), plus others.
LTSP tutorials say to allow TFTP and RPC but these are not listed in Firestarter's list of services to allow under Policy > Inbound.
Syslog messages while the client is trying to do TFTP are UDP on SPT2070 and DPT69. I have added rules for UDP on ports 2070 and 69 but they made no difference. ICMP and ToS Filtering are both disabled. If the firewall is enabled in Firestarter then clients hang at "TFTP open timeout".

Anyone know what ports or protocols need to be allowed for TFTP, and how they can be setup in Firestarter?

PS: I have eth0 with a static IP for the LTSP clients, and eth1 with a static IP for the internet.
Ubuntu 8.04 LTSP Server install, with Firestarter 1.0.3.

Thanks

---

### Post by jnwry on 2008-07-29
actually i'm having the same problem. I hope you get an answer. Otherwise if i find something i'll post it here.

---

### Post by haz2a on 2008-07-29
Yes I eventually solved it via [https://help.ubuntu.com/community/UbuntuLTSP/LTSPFirewall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPFirewall)

HTH
Haz

---

