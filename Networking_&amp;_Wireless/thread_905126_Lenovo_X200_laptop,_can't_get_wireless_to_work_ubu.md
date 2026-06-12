---
title: "Lenovo X200 laptop, can't get wireless to work ubuntu 8.04 64bit"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by barlrol on 2008-08-30
Just got my new Lenovo x200 laptop and I threw ubuntu 8.04 AMD64 onto it.  I can't get my wireless to work on it.  I read some of the ubuntu documentation about wireless but didnt find a solution.  This might help:
 Host bridge: Intel Corporation Cantiga Memory Controller Hub (rev 07)
        Subsystem: Lenovo Unknown device 20e0
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Cantiga Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
        Subsystem: Lenovo Unknown device 20e4
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f2000000 (64-bit, non-prefetchable) [size=4M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Cantiga Integrated Graphics Controller (rev 07)
        Subsystem: Lenovo Unknown device 20e4
        Flags: bus master, fast devsel, latency 0
        Memory at f2400000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

00:03.0 Communication controller: Intel Corporation Cantiga MEI Controller (rev 07)
        Subsystem: Lenovo Unknown device 20e6
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at f2826800 (64-bit, non-prefetchable) [size=16]
        Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
        Subsystem: Lenovo Unknown device 20ee
        Flags: bus master, fast devsel, latency 0, IRQ 507
        Memory at f2600000 (32-bit, non-prefetchable) [size=128K]
        Memory at f2625000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 1840 [size=32]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 20f0
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1860 [size=32]
        Capabilities: <access denied>

USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 20f0
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1880 [size=32]
        Capabilities: <access denied>

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 20f0
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 18a0 [size=32]
        Capabilities: <access denied>

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Lenovo Unknown device 20f1
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at f2826c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Lenovo Unknown device 20f2
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f2620000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: f2500000-f25fffff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
        I/O behind bridge: 00002000-00002fff

 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: f0000000-f1ffffff
        Prefetchable memory behind bridge: 00000000f2900000-00000000f29fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 20f0
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 18c0 [size=32]
        Capabilities: <access denied>

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 20f0
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 18e0 [size=32]
        Capabilities: <access denied>

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 20f0
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1c00 [size=32]
        Capabilities: <access denied>

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Lenovo Unknown device 20f1
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at f2827000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=0
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
        Subsystem: Lenovo Unknown device 20f5
:

SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: Lenovo Unknown device 20f8
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 508
        I/O ports at 1c48 [size=8]
        I/O ports at 183c [size=4]
        I/O ports at 1c40 [size=8]
        I/O ports at 1838 [size=4]
        I/O ports at 1c20 [size=32]
        Memory at f2826000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
        Subsystem: Lenovo Unknown device 20f9
        Flags: medium devsel, IRQ 11
        Memory at f2827400 (64-bit, non-prefetchable) [size=256]
        I/O ports at 1c60 [size=32]

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Atheros Communications Inc. Unknown device 0035
        Flags: fast devsel, IRQ 17
        Memory at f2500000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>



I'm think i found the wireless ethernet controller but im not sure.  I think its the Atheros one.  How do I get ubuntu to recognize this.  Thanks in advance.

---

### Post by DemonBob on 2008-08-30
Connect the laptop to a wired connection first to download the nessecary packages.


System -> Administration -> Hardware Drivers, make sure everything is enabled. 

Next:

Open up a terminal: Applications -> Assecories -> Terminal. 

Run these commands. 

```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
tar -xvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801
sudo apt-get install build-essential linux-headers-$(uname -r)
sudo make
sudo make install
```

You can copy and past those commands one line at a time. 

Reboot, then disconnect your wired connection. 

Test.

I have the same card so it should work.

---

### Post by barlrol on 2008-08-30
thank you so much it worked!

---

### Post by DemonBob on 2008-08-30
No problem. GLad i could help. 

Keep in mind though, that if you recieve a kernel update from the update manager, you will have to do this again.

---

### Post by e_x_p on 2008-09-05
Hi,

I just got my x200 today and I wanted to use linux on it.
Since I am not using Ubuntu, could you let me know which kernel version you guys are using get a working ethernet connection?
Apparently mine is too old but I don't want to risk git kernels.
Thanks a lot!

-Tai

---

### Post by cprofitt on 2008-09-06
I thought the Atheros chipset was built in to the kernel; no?

---

### Post by justincwatt on 2008-09-11
Man DemonBob, where were you when I was trying to figure X200 wireless out 3 weeks ago? Well, I ended up posting about this on my blog, our instructions are remarkably similar: [Getting wireless to work in Ubuntu on a Lenovo ThinkPad X200]("http://justinsomnia.org/2008/09/getting-wireless-to-work-in-ubuntu-on-a-lenovo-thinkpad-x200/") (glad to know I'm not alone).

---

### Post by phrOzenX200 on 2008-09-12
Hey,

The instructions unfortunately dont work for me.

Instead of
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
I have
03:00.0 Network controller: Intel Corporation Unknown device 4237

Can somebody help me? Pleeaaaaase? ;)

Thanks!

---

