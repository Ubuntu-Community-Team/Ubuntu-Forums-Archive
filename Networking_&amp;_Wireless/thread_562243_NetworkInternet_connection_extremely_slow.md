---
title: "Network/Internet connection extremely slow"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by Mithrilhall on 2007-09-28
I just purchased a  Shuttle XPC SN27P2 barebones and put everything together. When I try to browse the internet my speeds are extremely slow (it's an on-board NIC - Marvell). I've tried disabling the NIC and put in a Intel NIC with the same results.

Something I found interesting...PCLinuxOS out of the ones listed below is the only one that worked for me (normal network speeds).  I noticed it's the only one that has IO-APIC-level rather than IO-APIC-fasteoi. Could that be my problem and if so how do I fix that?

> 
> PCLinuxOS:
> [root@localhost root]# cat /proc/interrupts CPU0 CPU1
> 0: 39309 2494 IO-APIC-edge timer
> 6: 1 1 IO-APIC-edge floppy
> 8: 3 2 IO-APIC-edge rtc
> 9: 0 0 IO-APIC-level acpi
> 14: 4486 1 IO-APIC-edge ide0
> 16: 1146 1 IO-APIC-level libata, HDA Intel
> 17: 555 1 IO-APIC-level libata
> 18: 682 1 IO-APIC-level ohci_hcd:usb1
> 19: 2 1 IO-APIC-level ehci_hcd:usb2
> 20: 2 1 IO-APIC-level ohci1394
> 21: 29 1 IO-APIC-level eth0
> 22: 61 1 IO-APIC-level eth1
> NMI: 0 0
> LOC: 41779 41767
> ERR: 1
> MIS: 0
> [root@localhost root]#
>


> > Ubuntu 7.01:
> ubuntu@ubuntu:~$ cat /proc/interrupts
> CPU0 CPU1
> 0: 53890 2253 IO-APIC-edge timer
> 1: 0 2 IO-APIC-edge i8042
> 6: 1 1 IO-APIC-edge floppy
> 8: 28 2 IO-APIC-edge rtc
> 9: 0 0 IO-APIC-fasteoi acpi
> 12: 2 2 IO-APIC-edge i8042
> 14: 6506 1 IO-APIC-edge ide0
> 16: 5839 1 IO-APIC-fasteoi ohci_hcd:usb1, HDA Intel
> 17: 2 1 IO-APIC-fasteoi ehci_hcd:usb2
> 18: 1 1 IO-APIC-fasteoi ohci1394
> 19: 331 1 IO-APIC-fasteoi eth0
> 20: 87 1 IO-APIC-fasteoi eth1
> 21: 0 0 IO-APIC-fasteoi libata
> 22: 302 1 IO-APIC-fasteoi libata
> NMI: 0 0
> LOC: 56035 56045
> ERR: 1
> MIS: 0
> ubuntu@ubuntu:~$


> 
> Debian:
> eric@localhost:~$ cat /proc/interrupts CPU0 CPU1
> 0: 84 1 IO-APIC-edge timer
> 1: 0 2 IO-APIC-edge i8042
> 6: 0 2 IO-APIC-edge floppy
> 8: 0 0 IO-APIC-edge rtc
> 9: 0 0 IO-APIC-fasteoi acpi
> 12: 0 4 IO-APIC-edge i8042
> 14: 0 764 IO-APIC-edge ide0
> 16: 0 257 IO-APIC-fasteoi ehci_hcd:usb1, HDA Intel
> 17: 2 1401 IO-APIC-fasteoi ohci_hcd:usb2
> 18: 0 36 IO-APIC-fasteoi eth1
> 19: 0 63 IO-APIC-fasteoi eth2
> 20: 0 2 IO-APIC-fasteoi ohci1394
> 21: 0 0 IO-APIC-fasteoi libata
> 22: 2 5733 IO-APIC-fasteoi libata
> NMI: 0 0
> LOC: 5171 8933
> ERR: 1
> MIS: 0
> eric@localhost:~$
>


> 
> Knoppix:
> knoppix@Knoppix:~$ cat /proc/interrupts CPU0 CPU1
> 0: 92 109261 IO-APIC-edge timer
> 1: 0 2 IO-APIC-edge i8042
> 6: 0 2 IO-APIC-edge floppy
> 8: 0 1 IO-APIC-edge rtc
> 9: 0 0 IO-APIC-fasteoi acpi
> 12: 0 4 IO-APIC-edge i8042
> 14: 1 2175 IO-APIC-edge ide0
> 16: 0 237 IO-APIC-fasteoi libata, HDA Intel
> 17: 1 242 IO-APIC-fasteoi libata
> 18: 0 3 IO-APIC-fasteoi ehci_hcd:usb1
> 19: 1 3640 IO-APIC-fasteoi ohci_hcd:usb2
> 20: 0 3 IO-APIC-fasteoi ohci1394
> 21: 15 8061 IO-APIC-fasteoi eth1
> NMI: 0 0
> LOC: 109311 109296
> ERR: 1
> MIS: 0
> knoppix@Knoppix:~$
>


> 
> SabayonLinux:
> sabayonuser@sabayonx86 ~ $ cat /proc/interrupts CPU0 CPU1
> 0: 250 0 IO-APIC-edge timer
> 1: 3 3 IO-APIC-edge i8042
> 6: 0 2 IO-APIC-edge floppy
> 8: 48 2 IO-APIC-edge rtc
> 9: 0 0 IO-APIC-fasteoi acpi
> 12: 0 4 IO-APIC-edge i8042
> 14: 6853 6 IO-APIC-edge libata
> 15: 0 0 IO-APIC-edge libata
> 16: 9568 4 IO-APIC-fasteoi ohci1394, nvidia
> 17: 1693 1 IO-APIC-fasteoi sata_nv, ohci_hcd:usb2
> 18: 164 5 IO-APIC-fasteoi sata_nv
> 19: 2 1 IO-APIC-fasteoi ehci_hcd:usb1
> 20: 6067 1 IO-APIC-fasteoi HDA Intel
> 21: 133 1 IO-APIC-fasteoi eth0
> 22: 77 1 IO-APIC-fasteoi eth1
> NMI: 0 0
> LOC: 292338 292302
> ERR: 1
> MIS: 0
> sabayonuser@sabayonx86 ~ $
>


---

### Post by ddrichardson on 2007-09-28
Have you tried disabling IPv6?

---

### Post by Mithrilhall on 2007-10-01
Yep, I added it to my modules blacklist and I'm still having problems.

---

### Post by billgoldberg on 2007-10-01
I had an extremely slow internet connection, after I changed my dns nameservers to that of my isp, everything was fine.

---

