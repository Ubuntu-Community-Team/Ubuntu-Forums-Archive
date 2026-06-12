---
title: "NIC found and have link, but no network"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by qualjyn on 2007-01-12
The problem appeared on both 6.10 and 6.06, installed on an old computer, with working nics.

Most of my debugging has been on 6.06 though, which is what the computer is running with now.

I have tried with a 3com 3C905C NIC and a Realtek 8139 NIC.

mii-tool reports eth0: negotiated 100baseTx-FD flow-control, link ok

I can set a static IP, and ping that, localhost and 127.0.0.1. There is no way I can ping anything outside the machine.

I have tested the cable (tried it with another machine, and all works perfectly. And the machine (windows laptop) can ping the desired machine.

I have been trawling the for post about this problem, and I have tried the following:
changed /etc/modprope.d/aliases, and set alias net-pf-10 off so ipv6 doesn't disturb.

Furthermore I have changed /boot/grub/menu.lst and added acpi=noirq since some people found that to help. It didn't here though.

I'm totally at a loss, since it seems that everything is properly configured, but something is preventing me from speaking with the network (btw, I have just installed this 6.06 out of the box, and I do not have any other firewalls involved here.

Yours

/QuaLjyn

---

### Post by qualjyn on 2007-01-12
I forgot to mention:

lspci reports me to have the NIC, and lsmod lists mii as being used by 8139cp and 8139too.

dmesg does output: 
PCI: Enabling device 0000:01:0d.0 (0004 -> 0007)
PCI: IRQ 0 for device 0000:01:0d.0 doesn't match PIRQ mask - try pci=usepirqmask
PCI: setting IRQ 10 as level-triggered
PCI: Assigning IRQ 10 for device 0000:01:0d.0 

And i see it under /proc/interrupts that eth0 is set to have IRQ 10.

What disturbs is, that you report a different output than mine, on your lsmod | grep 8139. I get:

lsmod|grep 8139 produces:

8139cp   22528 0
8139too  26880 0
mii         5888   2, 8139cp, 8139too

Do I have "double drivers" or something like that?

---

