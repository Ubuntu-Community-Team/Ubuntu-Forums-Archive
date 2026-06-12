---
title: "Do I have USB 2.0?"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by suomalainen on 2010-04-21
Ubunteros?

I guess USB 2.o is the latest?

Amyway, how do I tell which version I have? Is there a terminal command?

Thank you!!!

---

### Post by Rex Bouwense on 2010-04-21
I am pretty sure that you can find out if you run lshw from the terminal.

---

### Post by suomalainen on 2010-04-21
This is the info I found.


Does this help???


 *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:30a0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:3080(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:e3226400-e32267ff

---

### Post by |Mitch| on 2010-04-21
version 02 means its 2.0, I believe

---

### Post by Rex Bouwense on 2010-04-21
You got it, you betcha.

---

### Post by quadproc on 2010-04-21
> **suomalainen said:**
> Ubunteros?

I guess USB 2.o is the latest?

Just within the last couple of months some vendors have started to offer products using USB 3.0 but it is certainly not much of a factor yet.

Your BIOS should have something to say about your USB port speeds.  Most BIOSes have the ability to enable or disable the 2.0 speed if they have 2.0 capability.

quadproc

---

