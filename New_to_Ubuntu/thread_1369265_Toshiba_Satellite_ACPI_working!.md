---
title: "Toshiba Satellite ACPI working!"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Andy_Dempster on 2009-12-31
Hello all and Happy New Year. I have a Satellite A30-303 which is now solely running Jaunty. I've got the ACPI working via the buggy DSDT route but am now seeing the following error which although I think looks okay would just like someone to double check please? From syslog:

```
Dec 31 22:28:14 darktosh kernel: [    0.392718] ACPI: DSDT override uses original SSDTs unless "acpi_no_auto_ssdt"
Dec 31 22:28:14 darktosh kernel: [    0.396587] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
Dec 31 22:28:14 darktosh kernel: [    0.400001] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
Dec 31 22:28:14 darktosh kernel: [    0.400001] ...trying to set up timer (IRQ0) through the 8259A ...
Dec 31 22:28:14 darktosh kernel: [    0.400001] ..... (found apic 0 pin 0) ...
Dec 31 22:28:14 darktosh kernel: [    0.443210] ....... works.
```

Many thanks in advance!

Andy_D

---

