---
title: "e1000e: probe failed with error -2"
date: 2021-01-05
forum: Networking &amp; Wireless
---

### Post by Anquietas on 2021-01-05
Hello all,

I was wondering if someone could help me with an odd problem...

I have a Lenovo ThinkCentre M92P Desktop PC, which has an Intel Onboard LAN Card that doesn't want to initialize and I don't know what the hell is the problem with it...

I'll post some of my configs:

lspci:

```
infosky [~] # lspci |grep Etherne
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (Lewisville) (rev 04)
```

lshw:
```

infosky [~] # lshw -c network
  *-network UNCLAIMED
       description: Ethernet controller
       product: 82579LM Gigabit Network Connection (Lewisville)
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:f7e00000-f7e1ffff memory:f7e35000-f7e35fff ioport:f080(size=32)

```

dmesg:
```

infosky [~] # dmesg |grep e1000
[    0.678546] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    0.680549] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    0.688720] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.951961] e1000e: probe of 0000:00:19.0 failed with error -2

```

uname -a:
```

Linux infosky 5.4.0-59-generic #65-Ubuntu SMP Thu Dec 10 12:01:51 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```

Ubuntu version:
```

Ubuntu 20.04.1 LTS

```

In BIOS, the Oboard LAN is enabled and LAN Booting is Disabled.

All updates are already performed.
System up-to-date. LAN Card not recognized by driver, I assume.
Something has to do with that "probe of 0000:00:19.0 failed with error -2" which I don't know what it means.

I was thinking about installing Intel's drivers from their website but this seems a little too much to do.
The drivers should be naturally integrated in the kernel.
If I install manual drivers, then this means that everytime I get a kernel update I must manually reinstall drivers ? This sucks...

If anyone can lend a helping hand, it would be very appreciated... :-)

Thanks !

---

