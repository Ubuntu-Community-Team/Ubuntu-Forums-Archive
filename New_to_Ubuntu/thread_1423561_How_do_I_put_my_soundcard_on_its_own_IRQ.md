---
title: "How do I put my soundcard on its own IRQ?"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by Monona on 2010-03-06
I'd like to move my soundcard to it's own interrupt to see if I can get some better audio performance.  How do I do that?  

My soundcard is:
Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)


I've got the output of cat /proc/interrupts below:

~$ cat /proc/interrupts
           CPU0       CPU1       
  0:        496          0   IO-APIC-edge      timer
  1:       3470          0   IO-APIC-edge      i8042
  7:          0          0   IO-APIC-edge      parport0
  8:          3          0   IO-APIC-edge      rtc
  9:          1          0   IO-APIC-fasteoi   acpi
 14:     174318          0   IO-APIC-edge      libata
 15:          0          0   IO-APIC-edge      libata
 16:     770225          0   IO-APIC-fasteoi   uhci_hcd:usb4, HDA Intel, ivtv0
 17:      50081          0   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb5
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb2
 19:     126505          0   IO-APIC-fasteoi   uhci_hcd:usb3
 20:      72110          0   IO-APIC-fasteoi   ohci1394, eth0
222:      44183          0   PCI-MSI-edge      ahci
NMI:          0          0   Non-maskable interrupts
LOC:   13938033   13905602   Local timer interrupts
RES:      52220     233872   Rescheduling interrupts
CAL:      20904      19295   function call interrupts
TLB:       4489       3943   TLB shootdowns
TRM:          0          0   Thermal event interrupts
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

---

### Post by MechaMechanism on 2010-03-19
I would not bother with putting your sound card on it's own IRQ.  In modern operating systems the IRQ has little effect.  What little effect it has is mostly to do with older OS like XP.  Vista or Windows 7 or Linux, they manage IRQ just fine.  For better audio performance you need a real time Linux kernel and a low latency motherboard.

---

### Post by ayenack on 2010-03-19
+1

Not likely to make any difference at all don't bother. Even on old systems this was a myth as far as I'm concerned and caused more problems than it solved.

---

