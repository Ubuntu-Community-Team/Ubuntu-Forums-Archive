---
title: "Ethernet dies after suspend"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by tylerious on 2007-10-24
When I start (or reboot) my computer, my NIC is correctly setup. It is an onboard Nvidia NIC (actually, a Broadcom AC131?). Anyways, after I try to resume, my ethernet device, eth0, is gone! I've been looking for answers to this all over the internet and have heard several answers: that it is a forcedeth module bug, a BIOS bug (although it worked fine in Windows), or something else.

One guy suggested (to another guy) doing "ifconfig eth0 down && rmmod forcedeth" before suspend and the reverse after resume. After "modprobe forcedeth", dmesg displays this:
> [ 4900.636000] forcedeth: using HIGHDMA
[ 4900.636000] 0000:00:14.0: Invalid Mac address detected: b5:83:48:58:15:00
[ 4900.636000] Please complain to your hardware vendor. Switching to a random MAC.
[ 4901.156000] eth0: forcedeth.c: subsystem: 0105b:0ca8 bound to 0000:00:14.0
naturally, "ifconfig eth0 up" responds: 
> eth0: ERROR while getting interface flags: No such device

My NIC's real MAC address is 00:15:58:48:83:B5 - the opposite of the once forcedeth detects. This seems to be a common problem.

"dmesg | grep 0000:00:14.0" results in more info relating to my NIC:
> [    8.604000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 20 (level, low) -> IRQ 20
[    8.604000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[    9.124000] eth0: forcedeth.c: subsystem: 0105b:0ca8 bound to 0000:00:14.0
[ 4561.936000] ACPI: PCI interrupt for device 0000:00:14.0 disabled
[ 4900.636000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 20 (level, low) -> IRQ 20
[ 4900.636000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[ 4900.636000] 0000:00:14.0: Invalid Mac address detected: b5:83:48:58:15:00
[ 4901.156000] eth0: forcedeth.c: subsystem: 0105b:0ca8 bound to 0000:00:14.0
I'm guessing the first three lines are from startup, the next line is when suspending, and the remaining four lines are from resume.

Has anybody else had problems similar to this?

NOTE: Oh, one last thing. I removed the network-manager package. While it's "roaming mode" may have maintained a network connection after suspending, it's method of doing so (creating virtual ethernet devices with made-up MAC addresses) was not good for my network. I am required to register every MAC address I connect with, so all these made-up MAC addresses would require me to re-register with the network after every resume!

---

