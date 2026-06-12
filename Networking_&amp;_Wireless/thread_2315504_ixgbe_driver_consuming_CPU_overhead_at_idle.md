---
title: "ixgbe driver consuming CPU overhead at idle"
date: 2016-02-29
forum: Networking &amp; Wireless
---

### Post by mike265 on 2016-02-29
I am running Ubuntu 14.04.4 LTS on a supermicro server X10DRW-iT with an intel x540 NIC and was doing some Performance analysis with perf and I noticed when the system is idle the ixgbe_read_reg is responsible for about 25% CPU overhead. Why is this. On my other servers running 12.04.4 LTS I do not have this. I am running an older motherboard on my other servers with an intel x520 NIC. Driver version for the x520 is 4.1.2 and for the x540 is 4.3.13.
```

# Overhead       Samples  Command        Shared Object      Symbol
#
    29.05%            84  swapper          [kernel.kallsyms]  [k] ixgbe_read_reg
     6.88%            16  kworker/u96:0    [kernel.kallsyms]  [k] ixgbe_read_reg





```

---

