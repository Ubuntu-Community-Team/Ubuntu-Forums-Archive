---
title: "Cant Connect to Secure Network  (10.10)"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by amfavs on 2011-03-10
So I updated to 10.10 and can no longer connect to WPA or WEP. I can connect wirelessly to an unsecured network. 

Any thoughts? 

Thanks in advance.

---

### Post by amfavs on 2011-03-11
So, waiving really doesn't help me... I tried turning green as well, still cant connect. 


Thanks again.

---

### Post by silkworm2.5 on 2011-03-11
Try connecting to the internet, either through an unsecured wireless, or wired connection, then update your system. Then have a look in System> Administration> Hardware Drivers. try again after. Does this help at all?

---

### Post by amfavs on 2011-03-11
Thanks for the advice, I did this last night and it still will not connect. It finds the network, knows its WPA, I enter the password and it pops out after 2 mins wanting me to reenter the password. I am 100% sure the password is correct. 

Thanks again.

---

### Post by Hippytaff on 2011-03-11
The waving guy is spam I think.
 
Did you set up a keyring for the WEP?

---

### Post by amfavs on 2011-03-11
It is a WPA connection.

---

### Post by silkworm2.5 on 2011-03-11
Ok, I did some research... Use this command in a terminal and post the output here for us.

lspci -v

---

### Post by Hippytaff on 2011-03-11
> **amfavs said:**
> It is a WEP connection.
 
Amended from WPA to WEP ;-)

---

### Post by Hippytaff on 2011-03-11
As well as post #7 the output of```
sudo lshw -C Network
``` and ```
iwconfig
``` might be useful

---

### Post by amfavs on 2011-03-11
So I am at work as of now - where the network is unsecured, will this effect the results?

---

### Post by Hippytaff on 2011-03-11
Not for the lspci -v, but the netwrok details will be different from the commands I posted

---

### Post by silkworm2.5 on 2011-03-11
I remember a while ago on 10.04 I couldn't connect to my home network normally, and had to manually put in the IP address, subnet mask, gateway and DNS server. They are all different for different router brands.

Do you know which brand of router you have? If not and we can't help you now, when will you be able to find out?

---

### Post by amfavs on 2011-03-11
lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: ASUSTeK Computer Inc. Device 1f77
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fd000000-fe9fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000fbffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 1af2
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at fcc00000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at cc00 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1f77
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at c880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1f77
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at c800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1f77
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at c480 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1f77
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at fcbfbc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 13a3
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at fcbf4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: fea00000-feafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: 00000000bde00000-00000000bdffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1f77
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at c400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1f77
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at c080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1f77
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at c000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1f77
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fcbfb800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1f77
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 1f77
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
    I/O ports at bc00 [size=8]
    I/O ports at b880 [size=4]
    I/O ports at b800 [size=8]
    I/O ports at b480 [size=4]
    I/O ports at b400 [size=32]
    Memory at fcbfb000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce G210M] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 1af2
    Physical Slot: 16
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at fa000000 (64-bit, prefetchable) [size=32M]
    I/O ports at dc00 [size=128]
    Expansion ROM at fe980000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb

01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 1af2
    Physical Slot: 16
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fe97c000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at feafe000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

04:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device 1820
    Physical Slot: 0
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at febc0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

---

### Post by Hippytaff on 2011-03-11
> 03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000

This is your wireless chipset. Try searching using that info...I'm at work at the moment but found [this]("http://ubuntuforums.org/showthread.php?t=1592846")

---

