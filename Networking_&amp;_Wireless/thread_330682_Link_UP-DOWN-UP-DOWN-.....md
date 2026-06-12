---
title: "Link UP-DOWN-UP-DOWN-...."
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by XeeleeUniversum on 2007-01-03
Hi,

I installed Ubuntu Edgy on a Nano-ITX board as an internet/vpn router with three RTL8100D onboard network cards. Everything runs perfectly but since I connected the GREEN (internal net) interface to an 1000/100/10 DLink Switch , I get this:
--- 8< ---
[  173.807551] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  174.012477] eth0: link down
[  174.359829] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  174.438481] eth0: link down
[  174.469862] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  174.525704] eth0: link down
[  174.842778] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  174.927044] eth0: link down
[  175.179733] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  175.294101] eth0: link down
[  175.767763] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  175.917012] eth0: link down
[  176.538187] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  176.591293] eth0: link down
[  176.807285] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  176.918113] eth0: link down
[  177.109461] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  177.129007] eth0: link down
[  177.149719] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  177.164181] eth0: link down
[  177.194154] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  177.220783] eth0: link down
[  177.246832] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  177.261378] eth0: link down
[  177.332567] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  177.354745] eth0: link down
[  177.379036] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  177.393422] eth0: link down
[  177.551066] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  177.639016] eth0: link down
[  177.998420] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  178.093869] eth0: link down
[  178.853288] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  178.902919] eth0: link down
[  179.010775] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  179.023980] eth0: link down
[  179.048395] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  179.064002] eth0: link down
[  179.087300] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  179.102623] eth0: link down
[  179.128515] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  179.140706] eth0: link down
[  179.342983] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  179.368200] eth0: link down
--- >8 ---

Connecting to an older 10/100 noname switch and connect to the mentioned dlink switch a link will etablishes. :)

I believe that the switch/net. card want to increase conn speed from 100 to 1000 and naturally failes.

Is there any LKM option to prevent that endless negation loop?

Thanks Alex

---

