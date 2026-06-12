---
title: "e1000e driver still not working in intrepid"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by drunken_sapo on 2008-11-05
Hello.
I was happily using my intel 82573L wired ethernet card in ubuntu hardy (after using the flag eeprpom_allow_bad_csum=1 flag to allow module to load).
After I've upgraded to intrepid with card was no longer detected due to the module being disabled.
As for this version of the kernel 
```
Linux laia 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux 
```
I understood that bug was corrected but I still had not net. So I've tried a live CD and fresh install without any luck.
At the moment of writing, I'm on the brand new installation (from official CD release on 30th October) witht his kernel
```
Linux laia 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686 GNU/Linux 
```

When I try to manually load the module, I get this:

```

modprobe -v e1000e
insmod /lib/modules/2.6.27-7-generic/kernel/drivers/net/e1000e/e1000e.ko

```

and the log shows this:

```

tail -f /var/log/messages
Nov  5 05:50:58 laia kernel: [ 1280.592458] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
Nov  5 05:50:58 laia kernel: [ 1280.592472] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Nov  5 05:50:58 laia kernel: [ 1280.593831] e1000e 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Nov  5 05:50:59 laia kernel: [ 1280.677190] e1000e 0000:05:00.0: PCI INT A disabled
Nov  5 05:50:59 laia kernel: [ 1280.677404] e1000e: probe of 0000:05:00.0 failed with error -5

```

Any suggestions about what to do next?
I'm just sick of this, I hope someone could help me.
Thanks.


BTW, here goes my hardware detection

```

lshw -C network
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:5c:12:64
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.100 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network UNCLAIMED
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fe:db:97:5b:32:be
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

