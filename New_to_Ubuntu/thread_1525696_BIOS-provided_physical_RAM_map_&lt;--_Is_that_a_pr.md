---
title: "BIOS-provided physical RAM map &lt;-- Is that a problem?"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by Bakmeel on 2010-07-07
Hello,

I am seeing some strange messages in my dmesg and kern.log logfiles. It appears there is something to do with the memory, but I can't tell whether there is actually a problem or not.

One of the first messages in the dmesg log file is this one:
```
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff80000 (usable)
[    0.000000]  BIOS-e820: 00000000bff8e000 - 00000000bff90000 (reserved)
[    0.000000]  BIOS-e820: 00000000bff90000 - 00000000bff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bff9e000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
```

The Motherboard is a SuperMicro X7SPA-HF (AMI BIOS) with 4GB RAM installed. The BIOS detects the memory correctly, and actually the system boots and operates correctly as well.

There should be 8MB reserved somewhere for the integrated graphics card. (Maybe it is included)

The installation is Ubuntu Server 10.04, but I have upgraded the kernel to Linux version 2.6.34-020634-generic.

Any suggestions whether I should be concerned or not? How much memory is actually affected?

Thanks a lot.

---

### Post by jtarin on 2010-07-07
I would say not really...maybe you would like to take a look at [[COLOR="Blue"]this[/COLOR]]("https://help.ubuntu.com/community/EnablingPAE") if memory allocation is of some importance to you. I've switched to this kernel and have not noticed any overt difference but memory allocation is made more usable.

---

