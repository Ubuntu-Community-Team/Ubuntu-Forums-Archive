---
title: "e100 EEPROM corrupted problem"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by closer9 on 2006-10-25
Ubuntu 6.10

Im getting the same error after doing an update. Restarted my computer and now the network applet says "No such device". 

Booting into the 2.6.17-10-386 recovery mode kernel i see this:
```
ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 201
e100: 0000:02:02.0: e100_eeprom_load: EEPROM corrupted
ACPI: PCI interrupt for device 0000:02:02.0 disabled
e100: probe of 0000:02:02.0 failed with error -11
```

lspci shows my network card:
Ethernet Controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 05)

But whenever I try to bring up eth0 with ifup it says:
```
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.
```

"ifconfig -a" shows only lo and sit0(i assume a ipv6 -> ipv4 converter)

"modprobe -l | grep e100" shows:
/lib/modules/2.6.17-10-386/kernel/drivers/net/e1000/e1000.ko
/lib/modules/2.6.17-10-386/kernel/drivers/net/e100.ko

"lsmod | grep e100" shows:
```
e100   36484 0
mii       6016 1 e100
```

Thanks for any help,
Scott

---

### Post by closer9 on 2006-10-25
Bump just this once...

I have faith that someone knows whats going on :-P

---

### Post by closer9 on 2006-10-26
Okay, I just replaced the card with a 3com and it seems to be working fine now. I tested the Intel card in another box and the card doesnt work. So, problem solved.

-Scott

---

