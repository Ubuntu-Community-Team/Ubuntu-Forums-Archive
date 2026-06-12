---
title: "cant get b44 module to load under XEN"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by puccaso on 2007-03-04
hi
seeing as i cant get beryl to work
i thought i'd work on something else

im trying to get VISTA or XP installed under XEN

however
i cant even access the network via XEN

this is my current problem


when i type modprobe b44
this is what i get


```
==> /var/log/syslog <==
Mar  4 06:22:38 jt-laptop kernel: [  362.631177] b44.c:v1.01 (Jun 16, 2006)
Mar  4 06:22:38 jt-laptop kernel: [  362.631200] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Mar  4 06:22:38 jt-laptop kernel: [  362.632249] b44 0000:03:00.0: No usable DMA configuration, aborting.
Mar  4 06:22:38 jt-laptop kernel: [  362.632267] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Mar  4 06:22:38 jt-laptop kernel: [  362.632270] b44: probe of 0000:03:00.0 failed with error -5
Mar  4 06:22:38 jt-laptop kernel: [  362.635407] 4gb seg fixup, process init (pid 1), cs:ip 73:0805565e
Mar  4 06:22:38 jt-laptop kernel: [  362.635417] 4gb seg fixup, process init (pid 1), cs:ip 73:b7f35ee0
```

how do i fix this??

---

