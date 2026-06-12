---
title: "Lucid does not see onboard Ethernet Controller on Dell OptiPlex 7020"
date: 2014-12-08
forum: Networking &amp; Wireless
---

### Post by david.aldrich.ntml on 2014-12-08
Hi

I have a new Dell OptiPlex 7020 desktop and I have installed Ubuntu 10.04 LTS 32-bit (Lucid) on it.  I must use Lucid because our development project requires a particular version of gcc and associated libraries.  Lucid is not detected the onboard Ethernet controller properly. I have also installed a Intel Gigabit CT Desktop Adapter (PCIe) and that is detected and working.  I need two Ethernet ports so I want to get the onboard controller working.

Here is what I have done so far to try to resolve this (without success):

$ lspci -nn | grep Eth
00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:153a] (rev 04)
02:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]

The first entry is the onboard controller (not working) the second in the PCIe card (working).

I believe that the [8086:153a] entry requires the Intel e1000e driver so I downloaded  igb-5.2.15.tar.gz from [http://sourceforge.net/projects/e1000/files/?source=navbar](http://sourceforge.net/projects/e1000/files/?source=navbar) and installed it as follows:

tar xfz igb-5.2.15.tar.gz[FONT=Calibri]cd igb-5.2.15/src[/FONT]
[FONT=Calibri]sudo make install

but the device is still not detected:

sudo lshw -class network
  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: [EMAIL="pci@0000:00:19.0"]pci@0000:00:19.0[/EMAIL]
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:f7d00000-f7d1ffff memory:f7d3d000-f7d3dfff ioport:f080(size=32)
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0

Both Ethernet ports are connected by cables to working networks.

Please can anyone suggest how to fix this?

David
[/FONT]

---

### Post by lisati on 2014-12-08
If you are running the desktop version of 10.04, it is highly recommended that you upgrade to a newer version of Ubuntu, if possible.

For more information, see [http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

### Post by david.aldrich.ntml on 2014-12-08
I'm actually running the server version. Unfortunately, I really do need to stay with 10.04.

---

### Post by chili555 on 2014-12-08
> 00:19.0 Ethernet controller [0200]: Intel Corporation Device [[COLOR="#FF0000"]8086:153a[/COLOR]] (rev 04)In fact, the version of igb that you downloaded does *not* cover your device:```
chili@T410:~/Downloads/igb-5.2.15/src$ modinfo igb.ko | grep 153
alias:          pci:v00008086d00001539sv*sd*bc*sc*i*
alias:          pci:v00008086d00001538sv*sd*bc*sc*i*
alias:          pci:v00008086d00001537sv*sd*bc*sc*i*
alias:          pci:v00008086d00001536sv*sd*bc*sc*i*
alias:          pci:v00008086d00001533sv*sd*bc*sc*i*
```Notice that 153A is not listed.

The latest version of e1000e does cover it:```
$ modinfo e1000e | grep -i 153a
alias:          pci:v00008086d0000[COLOR="#FF0000"]153A[/COLOR]sv*sd*bc*sc*i*
```I believe that your other device also uses e1000e but maybe in 10.04, an earlier version doesn't yet cover it. Check:```
modinfo e1000e | grep -i 153a
modinfo e1000e | grep -i version
```Mine, in 14.10, is 2.3.2-k. 

You might try this: [http://sourceforge.net/projects/e1000/files/e1000e%20stable/2.3.2/](http://sourceforge.net/projects/e1000/files/e1000e%20stable/2.3.2/)

---

### Post by david.aldrich.ntml on 2014-12-08
Thanks for your reply. I don't quite understand what to do next. I tried your commands:

$ modinfo e1000e | grep -i 153a
alias:          pci:v00008086d0000153Asv*sd*bc*sc*I*
$ modinfo e1000e | grep -i version
version:        3.1.0.2-NAPI
srcversion:     BC98E0BD9BE9F1638D89AE9
vermagic:       2.6.32-38-generic SMP mod_unload modversions 586

Does this mean I should download and try the stable version you suggested?

David

---

### Post by chili555 on 2014-12-08
> **david.aldrich.ntml said:**
> Thanks for your reply. I don't quite understand what to do next. I tried your commands:

$ modinfo e1000e | grep -i 153a
alias:          pci:v00008086d0000153Asv*sd*bc*sc*I*
$ modinfo e1000e | grep -i version
version:        3.1.0.2-NAPI
srcversion:     BC98E0BD9BE9F1638D89AE9
vermagic:       2.6.32-38-generic SMP mod_unload modversions 586

Does this mean I should download and try the stable version you suggested?

DavidWhat to do next depended entirely on your results above. The version of e1000e you have installed, 3.1.0.2, does claim your device and yet it still appears as unclaimed. Something else is wrong, I suspect. Let's look in the log for any interesting clues. We'll grep for the driver and the bus number:```
dmesg | grep -e e100 -e 19.0
```

---

### Post by david.aldrich.ntml on 2014-12-08
Thanks, here's the output:

> ~$ dmesg | grep -e e100 -e 19.0
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000d219b000 (usable)
[    0.000000]  BIOS-e820: 00000000d219b000 - 00000000d21a2000 (ACPI NVS)
[    0.000000]  modified: 0000000000100000 - 00000000d219b000 (usable)
[    0.000000]  modified: 00000000d219b000 - 00000000d21a2000 (ACPI NVS)
[    0.529175] pci 0000:00:19.0: reg 10 32bit mmio: [0xf7e00000-0xf7e1ffff]
[    0.529180] pci 0000:00:19.0: reg 14 32bit mmio: [0xf7e3d000-0xf7e3dfff]
[    0.529185] pci 0000:00:19.0: reg 18 io port: [0xf080-0xf09f]
[    0.529216] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.529219] pci 0000:00:19.0: PME# disabled
[    0.549748] system 00:0c: iomem range 0xfed19000-0xfed19fff has been reserved
[    1.023786] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    1.023788] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    1.023878] e1000e 0000:01:00.0: Disabling L1 ASPM
[    1.023895] e1000e 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.023921] e1000e 0000:01:00.0: setting latency timer to 64
[    1.024172] e1000e 0000:01:00.0: irq 28 for MSI/MSI-X
[    1.024175] e1000e 0000:01:00.0: irq 29 for MSI/MSI-X
[    1.024178] e1000e 0000:01:00.0: irq 30 for MSI/MSI-X
[    1.138312] e1000e 0000:03:00.0: Disabling L1 ASPM
[    1.138336] e1000e 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.138386] e1000e 0000:03:00.0: setting latency timer to 64
[    1.138637] e1000e 0000:03:00.0: irq 31 for MSI/MSI-X
[    1.138640] e1000e 0000:03:00.0: irq 32 for MSI/MSI-X
[    1.138643] e1000e 0000:03:00.0: irq 33 for MSI/MSI-X
[   16.173853] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[11150.444505] e1000e: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX

---

### Post by chili555 on 2014-12-08
> e1000e: Intel(R) PRO/1000 Network Driver - [COLOR="#FF0000"]1.0.2-k2[/COLOR]However, your modinfo says:> $ modinfo e1000e | grep -i version
version: [COLOR="#FF0000"]3.1.0.2-NAPI[/COLOR]Did you recently compile 3.1.0.2 and didn't either reboot or unload 1.0.2-k2 with modprobe -r? Anything you'd care to tell the doctor under strict confidentiality??

This implies both are up, yes?> [ 16.173853] e1000e: [COLOR="#FF0000"]eth0[/COLOR] NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[11150.444505] e1000e: [COLOR="#FF0000"]eth1[/COLOR] NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX

---

### Post by david.aldrich.ntml on 2014-12-08
Erm, sorry it's a mess. I have to say I know nothing about installing Linux drivers. No idea what modprobe does etc. :confused:

Anyway, two things to confess:

1) I didn't uninstall the older driver. Please will you give me the modprobe -r command to do that?

2) The reason that eth0 and eth1 are shown as both up is that I fitted another Intel NIC to the PC to get me going. So the onboard controller still isn't working and I would still like to make it work.

David

---

### Post by chili555 on 2014-12-08
Please try:```
sudo modprobe -r e1000e
```'-r' for remove unloads the old driver; so then load the new one:```
sudo modprobe e1000e
```And check the end of the logs to see if there is some indication that the newer version is present:```
dmesg | tail -n10
```Then I'd check again to see if the card is working:```
sudo lshw -C network
```

---

### Post by david.aldrich.ntml on 2014-12-08
That worked, I now have eth0, eth1 and eth2 :p

Thanks very much for your help and patience.

David

---

### Post by chili555 on 2014-12-08
Awesome! Glad it's working. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

