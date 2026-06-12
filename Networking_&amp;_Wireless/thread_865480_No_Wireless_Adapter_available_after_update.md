---
title: "No Wireless Adapter available after update"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by fmontoy2 on 2008-07-20
After a recent system update wireless is missing from my networking options as an available connection. "lshw -C network" results in"

  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945

anyone know why there is no logical name listed/how to get it back. I'm by no means a Ubuntu expert but I'd assume this is part of the problem. If any other info is needed I'd be more than happy to provide it. Thank you all for your time and effort.

---

### Post by fmontoy2 on 2008-07-20
Never mind. I was able to fix it on my own.

Thanks Anyway.

---

