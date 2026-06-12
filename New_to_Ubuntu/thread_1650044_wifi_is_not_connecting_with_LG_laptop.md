---
title: "wifi is not connecting with LG laptop"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by navaneethan on 2010-12-21
i have upgraded my system to ubuntu lucid ,then i tried to connect my system with wi-fi it does't connected

here i am giving my configuration details which i ran the command

lspci without sudo::

"
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5110 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, fast devsel, latency 0
	Memory at 93500000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 50e0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 50c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at 96705c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 96700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: 95600000-966fffff
	Prefetchable memory behind bridge: 0000000090400000-00000000913fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 94600000-955fffff
	Prefetchable memory behind bridge: 0000000091400000-00000000923fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00001000-00002fff
	Memory behind bridge: 93600000-945fffff
	Prefetchable memory behind bridge: 0000000092400000-00000000934fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 50a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 5080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 5060 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 5040 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at 96705800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
	I/O ports at 5108 [size=8]
	I/O ports at 511c [size=4]
	I/O ports at 5100 [size=8]
	I/O ports at 5118 [size=4]
	I/O ports at 5020 [size=32]
	Memory at 96705000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: medium devsel, IRQ 11
	Memory at 96706000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 5000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: fast devsel, IRQ 11
	Memory at 96704000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

01:00.0 **Network controller**: RaLink RT2860
	Subsystem: Device 1a32:0302
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 95600000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rt2860
	Kernel modules: rt2860sta

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, fast devsel, latency 0, IRQ 28
	I/O ports at 1000 [size=256]
	Memory at 92410000 (64-bit, prefetchable) [size=4K]
	Memory at 92400000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at 92420000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169


[B][U]lspci with sudo::
[/U][/B]


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5110 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [d0] Power Management version 3
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, fast devsel, latency 0
	Memory at 93500000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 50e0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 50c0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at 96705c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 96700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: 95600000-966fffff
	Prefetchable memory behind bridge: 0000000090400000-00000000913fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: LG Electronics, Inc. Device 1780
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 94600000-955fffff
	Prefetchable memory behind bridge: 0000000091400000-00000000923fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: LG Electronics, Inc. Device 1780
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00001000-00002fff
	Memory behind bridge: 93600000-945fffff
	Prefetchable memory behind bridge: 0000000092400000-00000000934fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: LG Electronics, Inc. Device 1780
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 50a0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 5080 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 5060 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 5040 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at 96705800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Capabilities: [50] Subsystem: LG Electronics, Inc. Device 1780

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
	I/O ports at 5108 [size=8]
	I/O ports at 511c [size=4]
	I/O ports at 5100 [size=8]
	I/O ports at 5118 [size=4]
	I/O ports at 5020 [size=32]
	Memory at 96705000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/4 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA <?>
	Capabilities: [b0] PCIe advanced features <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: medium devsel, IRQ 11
	Memory at 96706000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 5000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: fast devsel, IRQ 11
	Memory at 96704000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: [50] Power Management version 3

01:00.0 **Network controller: RaLink RT2860**
	Subsystem: Device 1a32:0302
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 95600000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/5 Enable-
	Capabilities: [70] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Kernel driver in use: rt2860
	Kernel modules: rt2860sta

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: LG Electronics, Inc. Device 1780
	Flags: bus master, fast devsel, latency 0, IRQ 28
	I/O ports at 1000 [size=256]
	Memory at 92410000 (64-bit, prefetchable) [size=4K]
	Memory at 92400000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at 92420000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [d0] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
	Kernel driver in use: r8169
	Kernel modules: r8169
please suggest me what i have to do?? to connect wi-fi?
""

---

### Post by karthick87 on 2010-12-21
What it says,when you type,

```
sudo iwlist wlan0 scan
```

---

### Post by navaneethan on 2010-12-21
> **karthick87 said:**
> What it says,when you type,

```
sudo iwlist wlan0 scan
```


"
wlan0     Scan completed :
          Cell 01 - Address: 00:25:9C:0C:94:3E
                    Protocol:802.11b/g/n
                    ESSID:""
                    Mode:Managed
                    Channel:6
                    Quality:81/100  Signal level:-58 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 02 - Address: 00:1E:40:14:DB:E8
                    Protocol:802.11b/g
                    ESSID:"Anitha"
                    Mode:Managed
                    Channel:11
                    Quality:39/100  Signal level:-74 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:22 Mb/s

"

---

### Post by karthick87 on 2010-12-21
Have a look at this..

[http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)

---

### Post by navaneethan on 2010-12-21
> **karthick87 said:**
> Have a look at this..

[http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)


> nava@nava-laptop:~$ ndiswrapper -l
nava@nava-laptop:~$ sudo ndiswrapper -i driver.inf
couldn't open driver.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
nava@nava-laptop:~$


even it doesn't help in my lucid

---

### Post by navaneethan on 2010-12-21
Finally It has helped for me ;-)

"> sudo apt-get install linux-backports-modules-wireless-lucid-generic
sudo apt-get install linux-backports-modules-wireless-lucid-generic-pae
sudo apt-get install linux-backports-modules-wireless-lucid-preempt
sudo apt-get install linux-backports-modules-wireless-lucid-server




[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

---

### Post by karthick87 on 2010-12-21
Glad it worked :) Mark this thread as [COLOR=Red][SOLVED][/COLOR]

---

### Post by navaneethan on 2010-12-23
again which is not connecting,i am gonna try to install that again

---

### Post by TBABill on 2010-12-23
You may want to also look in /etc/modules and see if other drivers are trying to load that conflict (such as the rt2800, rt 2800usb, etc). If they are you may need to blacklist them.

---

