---
title: "fresh install Lubuntu 16-04 LTS, No wire connection"
date: 2016-06-22
forum: Networking &amp; Wireless
---

### Post by tuut29 on 2016-06-22
Hello everybody ! 
I just started a new fresh install (format HDD...) of Lubuntu 16-04. and it appears my ETH port (and link) are not detected, however everything worked properly with the previous LTS ...
here is the output of ifconfig ;

```
lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          Packets reçus:667 erreurs:0 :0 overruns:0 frame:0
          TX packets:667 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1 
          Octets reçus:65177 (65.1 KB) Octets transmis:65177 (65.1 KB)

wlx14cc20104ef5 Link encap:Ethernet  HWaddr 14:cc:20:10:4e:f5  
          inet adr:192.168.1.6  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::b110:1ea5:5bfc:61e8/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:140574 erreurs:0 :48 overruns:0 frame:0
          TX packets:71335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:202153312 (202.1 MB) Octets transmis:6970961 (6.9 MB)

```
Any help will be dully appreciated !

---

### Post by jeremy31 on 2016-06-22
*Thread moved to **Networking & Wireless**.*

Welcome to the forums, please post the result of ```
lspci -nnk | grep -iA2 net
```

---

### Post by tuut29 on 2016-06-23
Hi, the result is empty !

The unfiltered output is :
```

lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 82Q35 Express DRAM Controller [8086:29b0] (rev 02)
    Subsystem: Hewlett-Packard Company 82Q35 Express DRAM Controller [103c:2818]
00:01.0 PCI bridge [0604]: Intel Corporation 82Q35 Express PCI Express Root Port [8086:29b1] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:03.0 Communication controller [0780]: Intel Corporation 82Q35 Express MEI Controller [8086:29b4] (rev 02)
    Subsystem: Hewlett-Packard Company 82Q35 Express MEI Controller [103c:2818]
    Kernel modules: mei_me
00:03.2 IDE interface [0101]: Intel Corporation 82Q35 Express PT IDER Controller [8086:29b6] (rev 02)
    Subsystem: Hewlett-Packard Company 82Q35 Express PT IDER Controller [103c:2818]
    Kernel driver in use: ata_generic
    Kernel modules: pata_acpi
00:03.3 Serial controller [0700]: Intel Corporation 82Q35 Express Serial KT Controller [8086:29b7] (rev 02)
    Subsystem: Hewlett-Packard Company 82Q35 Express Serial KT Controller [103c:2818]
    Kernel driver in use: serial
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 02)
    Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) USB UHCI Controller [103c:2818]
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 02)
    Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) USB UHCI Controller [103c:2818]
    Kernel driver in use: uhci_hcd
00:1a.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 02)
    Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) USB UHCI Controller [103c:2818]
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 02)
    Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) USB2 EHCI Controller [103c:2818]
    Kernel driver in use: ehci-pci
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 02)
    Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) USB UHCI Controller [103c:2818]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 02)
    Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) USB UHCI Controller [103c:2818]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 02)
    Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) USB2 EHCI Controller [103c:2818]
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller [8086:2914] (rev 02)
    Subsystem: Hewlett-Packard Company 82801IO (ICH9DO) LPC Interface Controller [103c:2818]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 IDE interface [0101]: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] [8086:2920] (rev 02)
    Subsystem: Hewlett-Packard Company 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] [103c:2818]
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi
00:1f.5 IDE interface [0101]: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] [8086:2926] (rev 02)
    Subsystem: Hewlett-Packard Company 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] [103c:2818]
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM] [1002:6779]
    Subsystem: PC Partner Limited / Sapphire Technology Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM] [174b:e206]
    Kernel driver in use: radeon
    Kernel modules: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series] [1002:aa98]
    Subsystem: PC Partner Limited / Sapphire Technology Radeon HD 6450 1GB DDR3 [174b:aa98]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

```

---

### Post by tuut29 on 2016-06-23
Oooops, the ETH port seems dead ...

How can I mark the thread as solved ?
Thanks for the helping !

---

### Post by jeremy31 on 2016-06-23
Use the "Thread tool" near the top of the page to mark as solved

---

