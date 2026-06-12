---
title: "New York City IP address, AOL Time Warner"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by Shim7 on 2010-06-13
Hi, Just decided to dump windows and try linux. i loaded xubuntu on a toshiba satellite 1909 with 256 ram. I didn't have the internet when i did. Anyways, internet isn't working when i plug in the cord. I did blank out the mac address (probably a mistake)
it knows the internet is there. Heres a bunch of stuff i copied for the gurus to look at!
I can't get either the ethernet cord to work, i have a wireless card but thats not working.
 
I am plugged in through the ethernet cord wired to a router with cable internet, time warner cable in NYC.
 
xubuntu 10.04
 
 ```

 
[FONT=Times New Roman][SIZE=3]$ lspci[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 05)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]02:00.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]02:00.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]matthew@matthew-laptop:~$ lsusb[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Bus 001 Device 002: ID 0d7d:1900 Phison Electronics Corp. USB Thumb Drive[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]$ lshw[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]WARNING: you should run this program as super-user.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]matthew-laptop [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: Computer[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-core[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: Motherboard[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-memory[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: System memory[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]size: 244MiB[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-cpu[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]product: Intel(R) Pentium(R) 4 CPU 1.60GHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]vendor: Intel Corp.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: cpu@0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]version: 15.1.2[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]size: 1600MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]configuration: id=0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-cache:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: L1 cache[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]size: 8KiB[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-cache:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: L2 cache[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]size: 256KiB[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-pci[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: Host bridge[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]product: 82845 845 [Brookdale] Chipset Host Bridge[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]vendor: Intel Corporation[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 100[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:00:00.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]version: 04[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]configuration: driver=agpgart-intel[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]resources: irq:0 memory:ec000000-efffffff(prefetchable)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-pci:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: PCI bridge[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]product: 82845 845 [Brookdale] Chipset AGP Bridge[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]vendor: Intel Corporation[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:00:01.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]version: 04[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]clock: 66MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]capabilities: pci bus_master[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]resources: ioport:3000(size=4096) memory:e8000000-e80fffff memory:f0000000-f7ffffff(prefetchable)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-display[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: VGA compatible controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]product: Radeon Mobility M6 LY[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]vendor: ATI Technologies Inc[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:01:00.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]version: 00[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]clock: 66MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]capabilities: bus_master cap_list rom[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]configuration: driver=radeon latency=64 mingnt=8[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]resources: irq:5 memory:f0000000-f7ffffff(prefetchable) ioport:3000(size=256) memory:e8000000-e800ffff memory:e8020000-e803ffff(prefetchable)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-pci:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: PCI bridge[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]product: 82801 PCI Bridge[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]vendor: Intel Corporation[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 1e[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:00:1e.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]version: 05[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]capabilities: pci bus_master[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]resources: ioport:4000(size=4096) memory:e8100000-e81fffff memory:10000000-17ffffff(prefetchable)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-pcmcia:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: CardBus bridge[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]product: PCI1420 PC card Cardbus Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]vendor: Texas Instruments[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:02:00.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]version: 00[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]capabilities: pcmcia bus_master cap_list[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]resources: irq:5 memory:e8101000-e8101fff ioport:4400(size=256) ioport:4800(size=256) memory:10000000-13ffffff(prefetchable) memory:18000000-1bffffff[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-pcmcia:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: CardBus bridge[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]product: PCI1420 PC card Cardbus Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]vendor: Texas Instruments[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 0.1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:02:00.1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]version: 00[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]capabilities: pcmcia bus_master cap_list[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]resources: irq:11 memory:e8102000-e8102fff ioport:4c00(size=256) ioport:1400(size=256) memory:14000000-17ffffff(prefetchable) memory:1c000000-1fffffff[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-network DISABLED[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: Ethernet interface[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]product: 82801BA/BAM/CA/CAM Ethernet Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]vendor: Intel Corporation[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 8[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:02:08.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]logical name: eth0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]version: 03[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]serial: 00:02:3f:74:6c:be[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]capabilities: bus_master cap_list ethernet physical[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 multicast=yes[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]resources: irq:11 memory:e8100000-e8100fff ioport:4000(size=64)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-isa[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: ISA bridge[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]product: 82801BA ISA Bridge (LPC)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]vendor: Intel Corporation[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 1f[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:00:1f.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]version: 05[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]capabilities: isa bus_master[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]configuration: latency=0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-ide[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: IDE interface[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]product: 82801BA IDE U100 Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]vendor: Intel Corporation[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 1f.1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:00:1f.1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]version: 05[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]capabilities: ide bus_master[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]configuration: driver=ata_piix latency=0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1800(size=16)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-usb:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: USB Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]product: 82801BA/BAM USB Controller #1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]vendor: Intel Corporation[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 1f.2[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:00:1f.2[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]version: 05[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]capabilities: bus_master[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]configuration: driver=uhci_hcd latency=0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]resources: irq:5 ioport:1820(size=32)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-serial UNCLAIMED[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: SMBus[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]product: 82801BA/BAM SMBus Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]vendor: Intel Corporation[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 1f.3[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:00:1f.3[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]version: 05[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]configuration: latency=0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]resources: ioport:1810(size=16)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-usb:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: USB Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]product: 82801BA/BAM USB Controller #1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]vendor: Intel Corporation[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 1f.4[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:00:1f.4[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]version: 05[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]capabilities: bus_master[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]configuration: driver=uhci_hcd latency=0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]resources: irq:5 ioport:1840(size=32)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-multimedia[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: Multimedia audio controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]product: 82801BA/BAM AC'97 Audio Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]vendor: Intel Corporation[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 1f.5[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:00:1f.5[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]version: 05[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]capabilities: bus_master[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]configuration: driver=Intel ICH latency=0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]resources: irq:11 ioport:1c00(size=256) ioport:1880(size=64)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-communication UNCLAIMED[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: Modem[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]product: 82801BA/BAM AC'97 Modem Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]vendor: Intel Corporation[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 1f.6[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:00:1f.6[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]version: 05[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]configuration: latency=0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]resources: ioport:2400(size=256) ioport:2000(size=128)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-scsi[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: scsi@2[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]logical name: scsi2[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]capabilities: scsi-host[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]configuration: driver=usb-storage[/FONT][/SIZE]

[FONT=Times New Roman][SIZE=3]$ uname -a[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Linux matthew-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]matthew@matthew-laptop:~$ lsb_release -a[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]No LSB modules are available.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Distributor ID: Ubuntu[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Description: Ubuntu 10.04 LTS[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Release: 10.04[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Codename: lucid[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]$ ifconfig[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]lo Link encap:Local Loopback [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]inet addr:127.0.0.1 Mask:255.0.0.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]UP LOOPBACK RUNNING MTU:16436 Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]RX packets:72 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]TX packets:72 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]collisions:0 txqueuelen:0 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]RX bytes:5600 (5.6 KB) TX bytes:5600 (5.6 KB)[/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]$ iwconfig[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]lo no wireless extensions.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]eth0 no wireless extensions.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]$ route -n[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Kernel IP routing table[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Destination Gateway Genmask Flags Metric Ref Use Iface[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]matthew@matthew-laptop:~$ ping -c 3 208.67.219.101[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]connect: Network is unreachable[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]a)[/SIZE] [/FONT]
[FONT=Times New Roman][SIZE=3]$ ping -c [www.opendns.com]("http://www.opendns.com")[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ping: bad number of packets to transmit.[/SIZE][/FONT]
 
```
[FONT=Times New Roman][SIZE=3]Can anybody help me????[/SIZE][/FONT]

---

### Post by Shim7 on 2010-06-13
Am hearing rumors that AOL time warner does funky stuff with the DHCP and IP Addresses? Anybody have experience with NYC?

---

### Post by Shim7 on 2010-06-13
Does anybody have knowledge about configuring access for AOL Time Warner in New York City?  Am hearing that it might be different... ideas?

---

### Post by Autodave on 2010-06-13
> **Shim7 said:**
> Does anybody have knowledge about configuring access for AOL Time Warner in New York City?  Am hearing that it might be different... ideas?

Can you give more info.......I really don't know what you are asking or trying to do.

---

### Post by anewguy on 2010-06-13
You don't need to create a new post every time you want an answer, this is just a dup of what you are asking in your  [original post]("http://ubuntuforums.org/showthread.php?t=1508739").  

Please keep the following in mind:

- this is a volunteer forum, and as much as we always seem to need our answers NOW (believe me, we've all been there!), you will probably have to wait a while for a solution.

- duplicate posts, or as in this case, a post which in theory is a dup (you don't state everything like in the first post, but the question is the same) aren't allowed

- the most common way of bringing your thread back to the top of the list, instead of making a new thread, is to add a post with the word "bump" in it.  This adds a new post, which puts your thread back at the top of the list - the word "bump" is a way of indicating you are still looking for help so you created the post to "bump" your thread to the top of the list.  Please note that forum rules dictate that you don't bump your post until 24 hours have elapsed since your last post.

I will try to have a moderator combine your posts here, and now you know how things work as well.  I know you are new to the forums (and perhaps Ubuntu?) so I just wanted to try to explain how some of the things work here - not complaining, just explaining.

I don't know the answer to your questions, but in reviewing your original post it appears that you don't have a wireless adapter (unless I missed it) so wireless would be out anyway.

Best of luck, and welcome to Ubuntu!

Dave ;)

---

### Post by cariboo on 2010-06-13
Please don't create multiple post on the same subject, I have merged your to threads.

---

### Post by nemilar on 2010-06-13
Your ifconfig output shows that no ethernet device is configured (except the loopback device).

Post the output of ```
ifconfig -a
```

---

