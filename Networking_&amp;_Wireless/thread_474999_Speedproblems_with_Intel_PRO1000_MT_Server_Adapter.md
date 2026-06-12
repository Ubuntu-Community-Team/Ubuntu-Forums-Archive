---
title: "Speedproblems with Intel PRO/1000 MT Server Adapter on 6.06 lts"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by majkey on 2007-06-15
Hello, i have problems with my new NIC in my fileserver. Before this i had an onboard realtek gigabitnic that i decided to change to a real server nic. The motherboard is an nf3 msi something something. Ubuntu 6.06 LTS AMD64. The NIC is an 82545EM PCI-X card. Kernel: 2.6.15-28-amd64-server

I use iperf to measure speeds and i only get 140Mbit to the server and 530Mbit from the server. With my onboard realtek i had around 650/650Mbit.
Jumbo frames doesnt really do any difference in speed.
Ive updated to latest e1000 drivers i think (not sure how i check the version on the current loaded drivers though so cant be sure).

lspci:
0000:00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
0000:00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
0000:00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
0000:00:09.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:02:06.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo Banshee (rev 03)
0000:02:08.0 Ethernet controller: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) (rev 01)
0000:02:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
0000:02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

Help would be very appreciated.
/Majkey

---

### Post by majkey on 2007-06-17
Anyone?

---

