---
title: "Network not working (eth0 is disabled)"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by wslyhbb on 2008-04-25
Hi I have Kubuntu 7.10, and the network was working fine for a long time but recently it stopped working.  I have rebooted numerous times but that does not help.
When I go to Manual Configuration... I can see eth0 but it says, "Disabled Ethernet Network Device", I try enabling it but it doesn't enable.
```
$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0f.0 VGA compatible controller: VMware Inc [VMware SVGA II] PCI Display Adapter
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
00:11.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
00:12.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)

```
```
$ sudo lshw -C network
  *-network
       description: Ethernet controller
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 11
       bus info: pci@0000:00:11.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=vmxnet latency=64 maxlatency=255 mingnt=6 module=vmxnet

```
```
$ sudo ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Please help me get my network back up and running.  If you need anymore information, let me know.

---

### Post by wslyhbb on 2008-04-25
Nevermind, I figured it out :-).  Somehow my wired connection got the "Enable roaming mode" checked.  Unchecked that, set it to DHCP and I was all good.

---

