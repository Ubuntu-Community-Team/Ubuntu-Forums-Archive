---
title: "Why are all the interrupts from my ethernet device being serviced on CPU3?"
date: 2014-07-01
forum: Networking &amp; Wireless
---

### Post by loyhz2ayj-jeff on 2014-07-01
Here's an odd one.  Why are all the interrupts from my ethernet device (em1) being serviced on CPU3?  I'm trying to debug a "dropped rx packets" problem and have arrived here.

```
root@egret:~# more /proc/interrupts 
           CPU0       CPU1       CPU2       CPU3       
  0:         17          0          0          0   IO-APIC-edge      timer
  1:          2          0          1          0   IO-APIC-edge      i8042
  8:          1          0          0          0   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 12:          3          0          1          0   IO-APIC-edge      i8042
 16:         18          5          9          9   IO-APIC-fasteoi   ehci_hcd:usb1
 23:         18          2          7          2   IO-APIC-fasteoi   ehci_hcd:usb2
 40:        163          0        252   13288359   PCI-MSI-edge      em1
 41:      11732       2061    2978986       9448   PCI-MSI-edge      ahci
NMI:        455        476        452        446   Non-maskable interrupts
LOC:   21293115   23594907   22704593   26400802   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:        455        476        452        446   Performance monitoring interrupts
IWI:     817063     289711     147895     826539   IRQ work interrupts
RTR:          3          0          0          0   APIC ICR read retries
RES:     808949     593075    1083654    1258760   Rescheduling interrupts
CAL:    3071214    2030863     882720    3146478   Function call interrupts
TLB:      57941      58619      59652      57274   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:       7482       7482       7482       7482   Machine check polls
ERR:          0
MIS:          0
root@egret:~# 

```

---

