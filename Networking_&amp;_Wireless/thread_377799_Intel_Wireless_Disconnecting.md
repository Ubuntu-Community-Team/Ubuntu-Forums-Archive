---
title: "Intel Wireless Disconnecting"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by falcons7 on 2007-03-06
hello i seem to be having trouble keeping a connection to my school network. I periodically get disconnected and have to log back in. 

I have tried  dmesg | grep 177
[17179571.168000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179571.220000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179574.556000] ide1: I/O resource 0x170-0x177 not free.
[17179575.104000] ACPI: PCI Interrupt 0000:07:06.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179575.152000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[de006000-de0067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
anthony@anthony-laptop:~$ 

and  lspci | grep Wireless
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


I am running Edgy with all the updates
this are the results.... any ideas?

---

