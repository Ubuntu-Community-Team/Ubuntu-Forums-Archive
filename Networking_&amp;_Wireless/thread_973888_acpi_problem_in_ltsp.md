---
title: "acpi problem in ltsp"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by send2iwan on 2008-11-07
i am using ltsp 5 with ubuntu 8.04

trying to connect with hard drive and success with pentium 4 cpu.
with this help [http://www.ltsp.org/twiki/bin/view/Ltsp/BootingFromHarddrive](http://www.ltsp.org/twiki/bin/view/Ltsp/BootingFromHarddrive)

now the problem is when i am using pentium 3 cpu error comes.
after many dot and done. 
it say acpi bios year... assuming acpi capable...
computer hang about 3-4 minute, then can login to server.

i am trying add this to my dhcp.conf
option option-128 code 128 = string;
option option-129 code 129 = text;

option option-128 e4:45:74:68:00:00; 
option option-129 "acpi=off";

but seems it never read by client.

how to fix this situation please?  i have already search anywhere with no success.

---

