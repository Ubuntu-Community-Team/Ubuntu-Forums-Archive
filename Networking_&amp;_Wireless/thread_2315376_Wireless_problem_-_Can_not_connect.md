---
title: "Wireless problem - Can not connect"
date: 2016-02-28
forum: Networking &amp; Wireless
---

### Post by odik on 2016-02-28
[FONT=Helvetica Neue]I have a desktop computer with windows  10 and ubuntu 15.10 in dual boot
Windows connects to wireless networks without problem so the [/FONT][COLOR=#282828][FONT=helvetica]adapter TP LINK TL -WN8200ND   is working.[/FONT][/COLOR]
[FONT=Helvetica Neue]Ubuntu finds wireless networks but it can not connect.
Could you help me to find a solution?

Thanks..


sudo iwconfig
 
  [HTML] sudo iwconfig: 
wlxc04a002465d6  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          
enp3s0    no wireless extensions.
 
lo        no wireless extensions.
 [/HTML]
 

[/FONT][FONT=Helvetica Neue]
sudo lspci -v[/FONT]

[FONT=Helvetica Neue][HTML] sudo lspci -v
[spoiler]sudo lspci -v
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
Subsystem: Gigabyte Technology Co., Ltd Device 5000
Flags: bus master, fast devsel, latency 0
Capabilities: [e0] Vendor Specific Information: Len=0c
Kernel driver in use: hsw_uncore

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0, IRQ 24
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
I/O behind bridge: 0000e000-0000efff
Memory behind bridge: e0000000-f00fffff
Capabilities: [88] Subsystem: Gigabyte Technology Co., Ltd Device 5000
Capabilities: [80] Power Management version 3
Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
Capabilities: [a0] Express Root Port (Slot+), MSI 00
Capabilities: [100] Virtual Channel
Capabilities: [140] Root Complex Link
Kernel driver in use: pcieport

00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
Subsystem: Gigabyte Technology Co., Ltd Device d000
Flags: bus master, fast devsel, latency 0, IRQ 28
Memory at f0400000 (64-bit, non-prefetchable) [size=4M]
Memory at d0000000 (64-bit, prefetchable) [size=256M]
I/O ports at f000 [size=64]
Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
Capabilities: [d0] Power Management version 2
Capabilities: [a4] PCI Advanced Features
Kernel driver in use: i915

00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
Subsystem: Intel Corporation Device 2010
Flags: bus master, fast devsel, latency 0, IRQ 33
Memory at f0914000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [50] Power Management version 2
Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit-
Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
Kernel driver in use: snd_hda_intel

00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05) (prog-if 30 [XHCI])
Subsystem: Gigabyte Technology Co., Ltd Device 5007
Flags: bus master, medium devsel, latency 0, IRQ 25
Memory at f0900000 (64-bit, non-prefetchable) [size=64K]
Capabilities: [70] Power Management version 2
Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
Subsystem: Gigabyte Technology Co., Ltd Device 1c3a
Flags: bus master, fast devsel, latency 0, IRQ 30
Memory at f091e000 (64-bit, non-prefetchable) [size=16]
Capabilities: [50] Power Management version 3
Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
Kernel driver in use: mei_me

00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05) (prog-if 20 [EHCI])
Subsystem: Gigabyte Technology Co., Ltd Device 5006
Flags: bus master, medium devsel, latency 0, IRQ 16
Memory at f091c000 (32-bit, non-prefetchable) [size=1K]
Capabilities: [50] Power Management version 2
Capabilities: [58] Debug port: BAR=1 offset=00a0
Capabilities: [98] PCI Advanced Features
Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
Subsystem: Gigabyte Technology Co., Ltd Device a002
Flags: bus master, fast devsel, latency 0, IRQ 31
Memory at f0910000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [50] Power Management version 2
Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
Capabilities: [100] Virtual Channel
Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0, IRQ 16
Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
Capabilities: [40] Express Root Port (Slot+), MSI 00
Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
Capabilities: [90] Subsystem: Gigabyte Technology Co., Ltd Device 5001
Capabilities: [a0] Power Management version 3
Kernel driver in use: pcieport

00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0, IRQ 18
Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
I/O behind bridge: 0000d000-0000dfff
Memory behind bridge: f0800000-f08fffff
Capabilities: [40] Express Root Port (Slot+), MSI 00
Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
Capabilities: [90] Subsystem: Gigabyte Technology Co., Ltd Device 5001
Capabilities: [a0] Power Management version 3
Kernel driver in use: pcieport

00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5) (prog-if 01 [Subtractive decode])
Flags: bus master, fast devsel, latency 0, IRQ 3
Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
Capabilities: [40] Express Root Port (Slot+), MSI 00
Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
Capabilities: [90] Subsystem: Gigabyte Technology Co., Ltd Device 5001
Capabilities: [a0] Power Management version 3

00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05) (prog-if 20 [EHCI])
Subsystem: Gigabyte Technology Co., Ltd Device 5006
Flags: bus master, medium devsel, latency 0, IRQ 23
Memory at f091b000 (32-bit, non-prefetchable) [size=1K]
Capabilities: [50] Power Management version 2
Capabilities: [58] Debug port: BAR=1 offset=00a0
Capabilities: [98] PCI Advanced Features
Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation C220 Series Chipset Family H81 Express LPC Controller (rev 05)
Subsystem: Gigabyte Technology Co., Ltd Device 5001
Flags: bus master, medium devsel, latency 0
Capabilities: [e0] Vendor Specific Information: Len=0c
Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05) (prog-if 01 [AHCI 1.0])
Subsystem: Gigabyte Technology Co., Ltd Device b005
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
I/O ports at f0b0 [size=8]
I/O ports at f0a0 [size=4]
I/O ports at f090 [size=8]
I/O ports at f080 [size=4]
I/O ports at f060 [size=32]
Memory at f091a000 (32-bit, non-prefetchable) [size=2K]
Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
Capabilities: [70] Power Management version 3
Capabilities: [a8] SATA HBA v1.0
Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
Subsystem: Gigabyte Technology Co., Ltd Device 5001
Flags: medium devsel, IRQ 10
Memory at f0919000 (64-bit, non-prefetchable) [size=256]
I/O ports at f040 [size=32]

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM] (prog-if 00 [VGA controller])
Subsystem: PC Partner Limited / Sapphire Technology Device e199
Flags: bus master, fast devsel, latency 0, IRQ 29
Memory at e0000000 (64-bit, prefetchable) [size=256M]
Memory at f0020000 (64-bit, non-prefetchable) [size=128K]
I/O ports at e000 [size=256]
Expansion ROM at f0000000 [disabled] [size=128K]
Capabilities: [50] Power Management version 3
Capabilities: [58] Express Legacy Endpoint, MSI 00
Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010
Capabilities: [150] Advanced Error Reporting
Kernel driver in use: radeon

01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series]
Subsystem: PC Partner Limited / Sapphire Technology Radeon HD 6450 1GB DDR3
Flags: bus master, fast devsel, latency 0, IRQ 32
Memory at f0040000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [50] Power Management version 3
Capabilities: [58] Express Legacy Endpoint, MSI 00
Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010
Capabilities: [150] Advanced Error Reporting
Kernel driver in use: snd_hda_intel

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
Subsystem: Gigabyte Technology Co., Ltd Motherboard
Flags: bus master, fast devsel, latency 0, IRQ 26
I/O ports at d000 [size=256]
Memory at f0804000 (64-bit, non-prefetchable) [size=4K]
Memory at f0800000 (64-bit, prefetchable) [size=16K]
Capabilities: [40] Power Management version 3
Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
Capabilities: [70] Express Endpoint, MSI 01
Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
Capabilities: [d0] Vital Product Data
Capabilities: [100] Advanced Error Reporting
Capabilities: [140] Virtual Channel
Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
Kernel driver in use: r8169

04:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41) (prog-if 01 [Subtractive decode])
Flags: bus master, fast devsel, latency 0, IRQ 3
Bus: primary=04, secondary=05, subordinate=05, sec-latency=32
Capabilities: [90] Power Management version 2
Capabilities: [a0] Subsystem: Gigabyte Technology Co., Ltd Device 8892
 
[/HTML]
 
 sudo lshw -C network[/FONT]
[HTML]sudo lshw -C network
  *-network                      description: Ethernet interface       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller       vendor: Realtek Semiconductor Co., Ltd.       physical id: 0       bus info: pci@0000:03:00.0       logical name: enp3s0       version: 06       serial: 94:de:80:da:86:dc       size: 10Mbit/s       capacity: 1Gbit/s       width: 64 bits       clock: 33MHz       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s       resources: irq:26 ioport:d000(size=256) memory:f0804000-f0804fff memory:f0800000-f0803fff  *-network       description: Wireless interface       physical id: 1       bus info: usb@1:1       logical name: wlxc04a002465d6       serial: c0:4a:00:24:65:d6       capabilities: ethernet physical wireless       configuration: broadcast=yes driver=rtl8192cu driverversion=4.2.0-16-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgnodik@odik-H81M-S2PV:~$ [/HTML]

---

### Post by chili555 on 2016-02-28
May we also see:```
lsusb
sudo iwlist scan
```In the scan results, just show us your own network and disguise the MAC address like this:> Cell 01 - Address:[COLOR="#FF0000"] XX:2B:B0:DC:45:XX[/COLOR]
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000012029f132a
                    Extra: Last beacon: 100ms ago
                    IE: Unknown: 000447425231
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSKThanks.

---

### Post by odik on 2016-02-28
```
lsusb
```
> Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 004: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 001 Device 003: ID 045e:07b9 Microsoft Corp. 
Bus 001 Device 002: ID 2357:0100  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
sudo iwlist scan
```

>           Cell 03 - Address: xx:60:80:82:xx:xx
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-26 dBm  
Encryption key:on
                    ESSID:"house"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000047bcf1153
                    Extra: Last beacon: 348ms ago
                    IE: Unknown: 0005686F757365
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606050700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500030A7A12
                    IE: Unknown: DD1E00904C336E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406050700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000



---

### Post by odik on 2016-02-28
should i hide the address? i put xx on it

---

### Post by chili555 on 2016-02-28
> **odik said:**
> should i hide the address? i put xx on itYou did fine. I just don't want to expose your real MAC address to spoofers who launch DDOS, viruses, etc. upon the world.

I see two problems here. First, a great many Linux drivers are sensitive to the access point and, most especially, do not work well with TKIP. Check the settings in your router.

WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

The second problem I see is that your device uses the infamous rtl8192cu. Please get a temporary internet connection by ethernet, tethered or whatever means possible and open a terminal and do:```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/lwfinger/rtl8192cu.git
sudo dkms add ./rtl8192cu
sudo dkms install rtl8192cu/0.1
```Reboot and tell us if it is working.

---

### Post by odik on 2016-02-29
ok it works, thanks..

---

### Post by odik on 2016-02-29
i get a  temporary  internet connection with an ethernet,  update ubuntu as you say and it works.

---

### Post by pellegrino-e on 2016-08-04
[COLOR=#000000]@chili555 , I did those things and it's still not working. The lights on the device do not turn on. It shows/detects the wifi networks around the area but it just won't to connect to them.[/COLOR]
[COLOR=#000000]I'd say this was the closest thing to get it working I've been because: [/COLOR]
[COLOR=#000000]-it's a recent thread, all of the rest are years old[/COLOR]
[COLOR=#000000]-it's the only method that allowed me to successfully install the drivers.[/COLOR]
[COLOR=#000000]In the other methods/drivers it fails to install/compile at the end.[/COLOR]

[COLOR=#000000]Any ideas?[/COLOR]

[COLOR=#000000]I'll attach some info about my pc and the other errors I got while trying to install any other drivers. I believe everything is up to date. I'm using the latest release of xubuntu.

[/COLOR][ATTACH]270580[/ATTACH]

Or here:
[http://pastebin.com/tEatVcsn](http://pastebin.com/tEatVcsn) (wireless-info)
[http://pastebin.com/B5atfyAg](http://pastebin.com/B5atfyAg) (problems)

Thanks in advance.

---

### Post by chili555 on 2016-08-05
> **pellegrino-e said:**
> [COLOR=#000000]@chili555 , I did those things and it's still not working. The lights on the device do not turn on. It shows/detects the wifi networks around the area but it just won't to connect to them.[/COLOR]
[COLOR=#000000]I'd say this was the closest thing to get it working I've been because: [/COLOR]
[COLOR=#000000]-it's a recent thread, all of the rest are years old[/COLOR]
[COLOR=#000000]-it's the only method that allowed me to successfully install the drivers.[/COLOR]
[COLOR=#000000]In the other methods/drivers it fails to install/compile at the end.[/COLOR]

[COLOR=#000000]Any ideas?[/COLOR]

[COLOR=#000000]I'll attach some info about my pc and the other errors I got while trying to install any other drivers. I believe everything is up to date. I'm using the latest release of xubuntu.

[/COLOR][ATTACH]270580[/ATTACH]

Or here:
[http://pastebin.com/tEatVcsn](http://pastebin.com/tEatVcsn) (wireless-info)
[http://pastebin.com/B5atfyAg](http://pastebin.com/B5atfyAg) (problems)

Thanks in advance.Just. Wow. Where do I start??

First, you do not even have an rtl8192cu device, the original subject of this thread, at all. You have:> Atheros Communications, Inc. AR9271 802.11nI suggest you start a new thread and I'll help you there. First of all, we'll remove the drivers you installed which are not relevant.

---

