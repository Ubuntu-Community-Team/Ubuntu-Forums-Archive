---
title: "Ethernet is not working properly!"
date: 2013-10-26
forum: Networking &amp; Wireless
---

### Post by artis.davidenis on 2013-10-26
Hello! I just joined the ubuntu community and just installed ubuntu on my computer. When i plug in my ethernet cord a notification pops out after about a minute and says "Wired network Disconnected - You are now offline". And the internet isnt working. I dont know how to fix it. It is a desktop computer. It doesnt have a wireless adapter. It is an IBM computer. It is running linux ubuntu 12.04 LTS. 32-bit

---

### Post by seanwilson684 on 2013-10-26
try getting drivers from IBM or Lenovo,  IBM/LENOVO release linux drivers.

---

### Post by artis.davidenis on 2013-10-26
> **seanwilson684 said:**
> try getting drivers from IBM or Lenovo,  IBM/LENOVO release linux drivers.
I searched for drivers but i cant find any. Or maybe im stupid at finding them.

---

### Post by The Cog on 2013-10-26
Can you post the output of the commands
```
ifconfig
ip link
```
and also find and post the section on the ethernet interface from the output of this command:
```
lspci -v
```
Hopefully this will give us some clues.

---

### Post by artis.davidenis on 2013-10-27
> **The Cog said:**
> Can you post the output of the commands
```
ifconfig
ip link
```
and also find and post the section on the ethernet interface from the output of this command:
```
lspci -v
```
Hopefully this will give us some clues.
Now internet is working i dont know what was with it. I think it was MAGIC :) .
Btw here is the results from the terminal. 

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:6c:83:67:32  
          inet addr:84.237.196.234  Bcast:84.237.199.255  Mask:255.255.252.0
          inet6 addr: fe80::201:6cff:fe83:6732/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16962 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24662383 (24.6 MB)  TX bytes:898287 (898.2 KB)
          Interrupt:16 Memory:d0080000-d00a0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24500 (24.5 KB)  TX bytes:24500 (24.5 KB)
```
```
ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:01:6c:83:67:32 brd ff:ff:ff:ff:ff:ff

```
```

 lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
    Subsystem: IBM Device 030e
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: IBM Device 030e
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d0100000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 30c0 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at d0180000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
    Subsystem: IBM Device 030e
    Flags: fast devsel
    Memory at 40600000 (32-bit, non-prefetchable) [disabled] [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: IBM Device 030e
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at d01c0000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d0000000-d00fffff
    Prefetchable memory behind bridge: 0000000040000000-00000000401fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 40200000-403fffff
    Prefetchable memory behind bridge: 0000000040400000-00000000405fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
    Subsystem: IBM Device 030e
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 3000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
    Subsystem: IBM Device 030e
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 3020 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
    Subsystem: IBM Device 030e
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 3040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
    Subsystem: IBM Device 030e
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 3060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: IBM Device 030e
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d03c4000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
    I/O behind bridge: 00005000-00005fff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: IBM Device 030e
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: leds-ss4200, lpc_ich, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: IBM Device 030e
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 30a0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: IBM Device 030e
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 30f0 [size=8]
    I/O ports at 30e4 [size=4]
    I/O ports at 30e8 [size=8]
    I/O ports at 30e0 [size=4]
    I/O ports at 30b0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
    Subsystem: IBM Device 030e
    Flags: medium devsel, IRQ 9
    I/O ports at 3080 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller: Intel Corporation 82573E Gigabit Ethernet Controller (Copper) (rev 03)
    Subsystem: IBM Device 030e
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at d0080000 (32-bit, non-prefetchable) [size=128K]
    Memory at d0000000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 4000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

0a:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
    Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
    Flags: bus master, medium devsel, latency 32, IRQ 22
    I/O ports at 5000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: snd_cmipci
    Kernel modules: snd-cmipci

```

---

### Post by The Cog on 2013-10-27
That's odd. Poor cable connection perhaps? Still, it's good that it's working now.
You may want to edit your post and remove your public IP address - some folk get paranoid about letting others know it.

The bits I was looking for was "RUNNING" and the error counters from ifconfig, "LOWER_UP" from ip link. Of course, they look as they should now it's working.

---

