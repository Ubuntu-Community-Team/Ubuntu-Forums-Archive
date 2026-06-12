---
title: "Intel PRO/Wireless 2200/2915"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by onurguzel on 2006-07-26
```

[17179588.528000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17179588.528000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179588.528000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[17179588.600000] Yenta: ISA IRQ mask 0x04b8, PCI irq 169
[17179588.600000] Socket status: 30000006
[17179588.600000] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
[17179588.600000] pcmcia: parent PCI bridge Memory window: 0xdfd00000 - 0xdfdfffff
[17179588.600000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
[17179588.628000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179588.628000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179588.936000] ipw2200: Radio Frequency Kill Switch is On:
[17179588.936000] Kill switch must be turned off for wireless networking to work.
[17179588.936000] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)

```

have do i turn radio frequency swtich off?

---

### Post by it.henrik on 2006-07-26
> **onurguzel said:**
> 
have do i turn radio frequency swtich off?

I guess that you can find it on your computer. I believe it is refering to the hardware switch most laptops have nowadays.

---

### Post by onurguzel on 2006-07-26
There's a switch on my computer and it's turned on. [Fn]+[F2] (Dell Inspiron 6000) But after turning it on, the indicator does not change

---

### Post by philippe_carlo on 2006-07-26
Check the BIOS and try also:
```
sudo iwconfig <interface> power on
```

---

