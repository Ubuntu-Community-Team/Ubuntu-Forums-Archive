---
title: "Intel e1000 driver troubles."
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by Fed on 2008-01-05
Hi,

Well, I've had quite an adventure so far with my Intel gbit NIC (82566) on my Supermicro C2SBA motherboard. Basically, the e1000 in the kernel of my OS did not have support for the 82566. For example, modprobe e1000 would show this in dmesg:
Intel(R) PRO/1000 Network Driver - version 7.1.9-k4-NAPI
Copyright (c) 1999-2006 Intel Corporation.
And only that. So it didn't find any compatible NICs.

Many many hours later, after getting all kinds of errors with the e1000 drivers, I thought I had finally managed to sort it out but it appears not quite. The make install of the e1000 would end with:
install -D -m 644 e1000.7.gz /usr/share/man/man7/e1000.7.gz
man -c -P'cat > /dev/null' e1000 || true
man:
cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode
e1000.
After much googling and searching, it seems many people were seeing this but most replies were basically "it just failed installing the manual but the driver should be fine". OK fine, if you say so. However, modprobe e1000 still shows:
Intel(R) PRO/1000 Network Driver - version 7.1.9-k4-NAPI
Copyright (c) 1999-2006 Intel Corporation.

And not version 7.6.12 as it should. So eventually I thought hey, why don't I try that insmod command with the full path the make install of the drivers showed. And yay, dmesg shows:
Intel(R) PRO/1000 Network Driver - version 7.6.12-NAPI
Copyright (c) 1999-2007 Intel Corporation.
PCI: Enabling device 0000:00:19.0 (0100 -> 0103)
ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 16 (level, low) -> IRQ 169
PCI: Setting latency timer of device 0000:00:19.0 to 64
e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:30:48:92:8f:d1
e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection

So yes, now it's up. However, why is modprobe still loading the old driver (which the e1000 driver make install even said it removed)? Is there any way to get modprobe to load the right one? And perhaps most importantly, how do I get the right driver loaded on boot?

Thanks a lot for bearing with me if you've read thus far. I look forward to hearing some tips!

---

