---
title: "Network dropping out, Motherboard driver possibly?"
date: 2015-05-30
forum: Networking &amp; Wireless
---

### Post by casey-earnshaw on 2015-05-30
Hello

I'm a new user who has only been running Ubuntu for 3 days now but I have noticed a problem that wasn't present with my old operating system (Windows 7). 

For some reason I find that my network will disconnect for anywhere between 1 and 5 minutes at random intervals, sometimes they are as close as half an hour apart and other times they are several hours with no pattern that I can see. 

Searching online I found someone who had a similar issue and they were recommended to change their motherboard driver to an official one as I think Linux does its own thing, however I don't actually know which motherboard is in this computer as it was built for me a long time ago and sadly I have forgotten. Is there a way I can find out what motherboard I am using so I can try installing a different driver to see if that helps me too?

I connect to the internet through a cable rather than using wireless.

Many thanks

Casey

---

### Post by The Cog on 2015-05-30
Welcome to the forums. 
I hope they help you solve our problem.

The command ```
lspci -v
``` will list lots of useful info, listing everything on the PCI bus. If you post the output from that, it would be a good start.

---

### Post by casey-earnshaw on 2015-05-30
Thank you for a quick reply :)

This is what it output:
```
casey@Desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
    Subsystem: Intel Corporation Device 4f4a
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82Q35 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: e0000000-e2ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
    Subsystem: Intel Corporation Device 4f4a
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at e3226900 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei_me

00:03.2 IDE interface: Intel Corporation 82Q35 Express PT IDER Controller (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: Intel Corporation Device 4f4a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
    I/O ports at 3480 [size=8]
    I/O ports at 349c [size=4]
    I/O ports at 3478 [size=8]
    I/O ports at 3498 [size=4]
    I/O ports at 3440 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_generic

00:03.3 Serial controller: Intel Corporation 82Q35 Express Serial KT Controller (rev 02) (prog-if 02 [16550])
    Subsystem: Intel Corporation Device 4f4a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
    I/O ports at 3470 [size=8]
    Memory at e3225000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: serial

00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
    Subsystem: Intel Corporation Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at e3200000 (32-bit, non-prefetchable) [size=128K]
    Memory at e3224000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 30e0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e

00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Intel Corporation Device 4f4a
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 30c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Intel Corporation Device 4f4a
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 30a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Intel Corporation Device 4f4a
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 3080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Intel Corporation Device 4f4a
    Flags: bus master, medium devsel, latency 0, IRQ 17
    Memory at e3226400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
    Subsystem: Intel Corporation Device 0012
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at e3220000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f8000000-f81fffff
    Prefetchable memory behind bridge: 00000000f8200000-00000000f83fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: f8400000-f85fffff
    Prefetchable memory behind bridge: 00000000f8600000-00000000f87fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: e3100000-e31fffff
    Prefetchable memory behind bridge: 00000000f8800000-00000000f89fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: f8a00000-f8bfffff
    Prefetchable memory behind bridge: 00000000f8c00000-00000000f8dfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: f8e00000-f8ffffff
    Prefetchable memory behind bridge: 00000000f9000000-00000000f91fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Intel Corporation Device 4f4a
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 3060 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Intel Corporation Device 4f4a
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 3040 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Intel Corporation Device 4f4a
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 3020 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Intel Corporation Device 4f4a
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at e3226000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
    Memory behind bridge: e3000000-e30fffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
    Subsystem: Intel Corporation Device 4f4a
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich

00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Intel Corporation Device 4f4a
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
    I/O ports at 3468 [size=8]
    I/O ports at 3494 [size=4]
    I/O ports at 3460 [size=8]
    I/O ports at 3490 [size=4]
    I/O ports at 3430 [size=16]
    I/O ports at 3420 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
    Subsystem: Intel Corporation Device 4f4a
    Flags: medium devsel, IRQ 9
    Memory at e3226800 (64-bit, non-prefetchable) [size=256]
    I/O ports at 3000 [size=32]

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: Intel Corporation Device 4f4a
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
    I/O ports at 3458 [size=8]
    I/O ports at 348c [size=4]
    I/O ports at 3450 [size=8]
    I/O ports at 3488 [size=4]
    I/O ports at 3410 [size=16]
    I/O ports at 3400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: NVIDIA Corporation G94 [GeForce 9600 GT] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Foxconn International, Inc. Device 0f2f
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at e2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at e0000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at 2000 [size=128]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: nouveau

04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface (rev b2) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface
    Flags: bus master, fast devsel, latency 0, IRQ 18
    I/O ports at 1018 [size=8]
    I/O ports at 1024 [size=4]
    I/O ports at 1010 [size=8]
    I/O ports at 1020 [size=4]
    I/O ports at 1000 [size=16]
    Memory at e3100000 (32-bit, non-prefetchable) [size=512]
    Capabilities: <access denied>
    Kernel driver in use: pata_marvell

07:03.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 70) (prog-if 10 [OHCI])
    Subsystem: LSI Corporation FW322/323 [TrueFire] 1394a Controller
    Flags: bus master, fast Back2Back, medium devsel, latency 32, IRQ 19
    Memory at e3000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci

casey@Desktop:~$ 

```

---

### Post by The Cog on 2015-05-30
I hope that helps those who understand these things. 

While we wait for somepne more knowlegable about this stuff, can I suggest you run the command **ifconfig** while the adapter is working and again when it drops out, to see if there's a difference in output.
Also, this command might contain some kind of error message if you run it just after the dropout (basically looking at the last few log messages):```
dmesg | tail
```

---

### Post by casey-earnshaw on 2015-05-30
ifconfig when working:
```

casey@Desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:89:89:e6  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe89:89e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:199235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132620 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:250765284 (250.7 MB)  TX bytes:14673604 (14.6 MB)
          Interrupt:20 Memory:e3200000-e3220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1067466 (1.0 MB)  TX bytes:1067466 (1.0 MB)

wlan0     Link encap:Ethernet  HWaddr 60:02:b4:79:71:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

casey@Desktop:~$ 

```

ifconfig when offline:
```
casey@Desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:89:89:e6  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe89:89e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:588757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:366611 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:767119257 (767.1 MB)  TX bytes:38542293 (38.5 MB)
          Interrupt:20 Memory:e3200000-e3220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:18276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1922478 (1.9 MB)  TX bytes:1922478 (1.9 MB)

wlan0     Link encap:Ethernet  HWaddr 60:02:b4:79:71:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

dmesg tail when offline:
```
casey@Desktop:~$ dmesg | tail
[   47.966957] audit_printk_skb: 168 callbacks suppressed
[   47.966961] audit: type=1400 audit(1432986367.303:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1856 comm="apparmor_parser"
[   47.966972] audit: type=1400 audit(1432986367.303:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1856 comm="apparmor_parser"
[   47.967425] audit: type=1400 audit(1432986367.303:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1856 comm="apparmor_parser"
[  653.374371] perf interrupt took too long (2513 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 1418.738982] audit: type=1400 audit(1432987738.075:71): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3191 comm="apparmor_parser"
[ 1418.738999] audit: type=1400 audit(1432987738.075:72): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3191 comm="apparmor_parser"
[ 1418.739546] audit: type=1400 audit(1432987738.075:73): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3191 comm="apparmor_parser"
[ 3025.381120] systemd-hostnamed[3513]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 4462.662479] perf interrupt took too long (5039 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
casey@Desktop:~$ 


```

---

### Post by The Cog on 2015-05-30
I don't see anything odd there. Nothing relevant in dmesg, and no change in ifconfig status.
You say your network "disconnects". Can you still ping the router (probably 192.168.1.1)?
Can you still ping 8.8.8.8? 
I am wondering if it's a name resolution problem or a router problem.
Can you try these commands when  it's down and post the result?
```

route -n
ping -c 3 192.168.1.1
ping -c 3 91.189.94.12
ping -c 3 ubuntuforums.org

```

---

### Post by casey-earnshaw on 2015-05-30
I'll probably have to try that tomorrow, I don't think I'll be using my  computer too much longer tonight. I found a command that lets me detect  my motherboard model which is: cat /sys/devices/virtual/dmi/id/board_{vendor,name,version}

Which outputs:

```
Intel Corporation
DQ35JO
AAE41927-803
```

I suppose I could search for a driver for that but is there an easy way to roll the driver back if it makes things worse? Generally is it better to look for official drivers or is it normally better to allow Linux to handle these things itself?

---

### Post by The Cog on 2015-05-30
If you want really good info on the computer, use the command
```
sudo lshw
```

I don't think you need motherboard specific drivers - with Linux we generally use drivers for whatever chipset is fitted to the motherboard. As yet I don't see anything to indicate it's a driver issue and not some other networking issue. But I'm an expert in these things, far from it.

---

