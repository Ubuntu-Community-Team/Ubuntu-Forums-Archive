---
title: "ACX111 and problems with IRQ 0"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by metalelf0 on 2007-04-18
Hi everybody. I'm trying to make a wireless card D-Link G520+ work on my Ubuntu. At the moment I'm using Ubuntu 7.04, kernel 2.6.20.15-386, but this problem existed also on Edgy and with other kernels. I followed the instructions from acx100.sourceforge.net, firstly out-of the kernel, then when this failed I tried to recompile the module in the kernel, but with the same results.
When I boot the system the output from dmesg is:
```
dmesg | grep acx
[   49.357335] acx: Loaded combined PCI/USB driver, firmware_ver=1.2.1.34
[   49.357339] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   49.357404] acx: found ACX111-based wireless network card at 0000:01:08.0, irq:0, phymem1:0xEC020000, phymem2:0xEC000000, mem1:0xf8ad8000, mem1_size:8192, mem2:0xf8bc0000, mem2_size:131072
[   49.357408] acx: can't use IRQ 0
[   49.366479] acx_pci: probe of 0000:01:08.0 failed with error -5
```
So of course the interface cannot be seen in iwconfig.
This is the output from lspci:
```
01:08.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
```
The output from lsmod | grep acx is:
```
acx                    97540  0
usbcore               131480  7 acx,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
```
I don't know what to do at this point! Does anybody have any idea?
Bye, thank you in advance!

---

### Post by dmizer on 2007-04-18
i have been fighting this one for a while myself.  i moved to ndiswrapper because it doesn't have the same problem.

try blacklisting ohci_hcd
```
gksudo gedit /etc/modprobe.d/bladklist
```
at the end of the file, add this line:
```
blacklist ohci_hcd
```
save the file, reboot, and see if that fixes your problem.

if not, try changing ohci_hcd to ehci_hcd

---

### Post by metalelf0 on 2007-04-18
No, I still get the same error. Should I move to ndiswrapper too?

---

### Post by dmizer on 2007-04-18
humm ... i have another idea but i'm having trouble locating it.  there's a boot parameter you can add.  you might try going to system > services ... and turn of acpi

i'll keep hunting for the other option.

---

