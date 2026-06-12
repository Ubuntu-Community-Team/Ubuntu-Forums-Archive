---
title: "Ubuntu 17.04 does not found WIFI if I use some 4.10.x-xx kernel"
date: 2017-09-14
forum: Networking &amp; Wireless
---

### Post by jordanmoises on 2017-09-14
This is my first post, I apologize in advance if my English is not good enough, I hope I did it correctly and in the corresponding section; I have been using this notebook for a few years now, it came with Ubuntu 12 installed.

After many reboots without WiFi, I realized that the problem was if I used a version 4.10 kernel. I was researching with "journalctl" and checking the lines that there was difference between a start with WiFi and another without.

I base my hypothesis that the problem is related to the kernel version, since if I choose to use 4.8.xx or 4.6.xx at boot time and I always have WiFi enabled.



What caught my attention is that when I do not have WIFI I do not see the following line when I run "**journalctl -b**":

```
rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/ieee80211/phy0/rfkill0) (ath9k driver)
```


It is actually the first of many lines that are not from this one. Another thing I see happening is that I have no audio and no bluetooth. But I'm sure if they help me with the WiFi, the rest will be similar or I hope so.


Thank you very much and please help me to find the solution.





**My distro information**
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.04
DISTRIB_CODENAME=zesty
DISTRIB_DESCRIPTION="Ubuntu 17.04"
NAME="Ubuntu"
VERSION="17.04 (Zesty Zapus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 17.04"
VERSION_ID="17.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=zesty
UBUNTU_CODENAME=zesty
```


**Part of journalctl -b output with WiFI**
Kenel mentions and NetworkManager unit lines

Look at [https://pastebin.com/urhQJaKn](https://pastebin.com/urhQJaKn)


**Part of **[B]journalctl -b output without WiFI
[/B]
Kenel mentions and NetworkManager unit lines

Look at [https://pastebin.com/jg3wqzwV](https://pastebin.com/jg3wqzwV)
[B]
hwinfo output[/B]Look at [https://pastebin.com/KzM3JgMK](https://pastebin.com/KzM3JgMK)

**lspci output**
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
```




**lspci -t output**
```
-[0000:00]-+-00.0
           +-02.0
           +-14.0
           +-16.0
           +-1a.0
           +-1b.0
           +-1c.0-[01]----00.0
           +-1c.1-[02]----00.0
           +-1d.0
           +-1f.0
           +-1f.2
           \-1f.3
```


**lspci -v output**
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
    Subsystem: COMPAL Electronics Inc 3rd Gen Core processor DRAM Controller
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: ivb_uncore


00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: COMPAL Electronics Inc 3rd Gen Core processor Graphics Controller
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=64]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915


00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: COMPAL Electronics Inc 7 Series/C210 Series Chipset Family USB xHCI Host Controller
    Flags: bus master, medium devsel, latency 0, IRQ 24
    Memory at c0600000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: xhci_hcd


00:16.0 Communication controller: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 (rev 04)
    Subsystem: COMPAL Electronics Inc 7 Series/C216 Chipset Family MEI Controller
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at c0614000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei_me
    Kernel modules: mei_me


00:1a.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: COMPAL Electronics Inc 7 Series/C216 Chipset Family USB Enhanced Host Controller
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at c0619000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci


00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: COMPAL Electronics Inc 7 Series/C216 Chipset Family High Definition Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at c0610000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


00:1c.0 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Prefetchable memory behind bridge: 00000000c0400000-00000000c04fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: COMPAL Electronics Inc 7 Series/C216 Chipset Family PCI Express Root Port 1
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: c0500000-c05fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: COMPAL Electronics Inc 7 Series/C210 Series Chipset Family PCI Express Root Port 2
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1d.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: COMPAL Electronics Inc 7 Series/C216 Chipset Family USB Enhanced Host Controller
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at c0618000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci


00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
    Subsystem: COMPAL Electronics Inc HM76 Express Chipset LPC Controller
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich


00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: COMPAL Electronics Inc 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 25
    I/O ports at 3088 [size=8]
    I/O ports at 3094 [size=4]
    I/O ports at 3080 [size=8]
    I/O ports at 3090 [size=4]
    I/O ports at 3060 [size=32]
    Memory at c0617000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci


00:1f.3 SMBus: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller (rev 04)
    Subsystem: COMPAL Electronics Inc 7 Series/C216 Chipset Family SMBus Controller
    Flags: medium devsel, IRQ 10
    Memory at c0615000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 3040 [size=32]
    Kernel modules: i2c_i801


01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
    Subsystem: COMPAL Electronics Inc RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 26
    I/O ports at 2000 [size=256]
    Memory at c0404000 (64-bit, prefetchable) [size=4K]
    Memory at c0400000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
    Kernel driver in use: r8169
    Kernel modules: r8169


**02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)**
**    Subsystem: Qualcomm Atheros AR9485 Wireless Network Adapter**
**    Flags: bus master, fast devsel, latency 0, IRQ 17**
**    Memory at c0500000 (64-bit, non-prefetchable) [size=512K]**
**    Expansion ROM at c0580000 [disabled] [size=64K]**
**    Capabilities: [40] Power Management version 2**
**    Capabilities: [50] MSI: Enable- Count=1/4 Maskable+ 64bit+**
**    Capabilities: [70] Express Endpoint, MSI 00**
**    Capabilities: [100] Advanced Error Reporting**
**    Capabilities: [140] Virtual Channel**
**    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00**
**    Kernel driver in use: ath9k**
**    Kernel modules: ath9k**
```


**lscpu output**
```
Arquitectura:          **x86_64**
modo(s) de operación de las CPUs:32-bit, 64-bit
Orden de bytes:        Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Hilo(s) de procesamiento por núcleo:2
Núcleo(s) por «socket»:4
Socket(s):             1
Modo(s) NUMA:          1
ID de fabricante:      GenuineIntel
Familia de CPU:        6
Modelo:                58
Model name:            Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz
Revisión:             9
CPU MHz:               1301.660
CPU max MHz:           3400,0000
CPU min MHz:           1200,0000
BogoMIPS:              4789.20
Virtualización:       VT-x
Caché L1d:            32K
Caché L1i:            32K
Caché L2:             256K
Caché L3:             6144K
NUMA node0 CPU(s):     0-7
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts

```



[B]demicode output
[/B]
Look at [https://pastebin.com/iyZr7WXq](https://pastebin.com/iyZr7WXq)

Regards
Jordán

---

### Post by wildmanne39 on 2017-09-15
This is an issue with 17.04 and several adapters, this fix works for certain wifi issues, that have been reported here to bugzilla.
[https://bugzilla.gnome.org/show_bug.cgi?id=780119](https://bugzilla.gnome.org/show_bug.cgi?id=780119)

Open the file with your text editor, if you need more directions just ask:
```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
```
add lines
```
[device]
wifi.scan-rand-mac-address=0
```
Save and close file then reboot.

---

### Post by jordanmoises on 2017-09-17
> **wildmanne39 said:**
> This is an issue with 17.04 and several adapters, this fix works for certain wifi issues, that have been reported here to bugzilla.
[https://bugzilla.gnome.org/show_bug.cgi?id=780119](https://bugzilla.gnome.org/show_bug.cgi?id=780119)

Open the file with your text editor, if you need more directions just ask:
```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
```
add lines
```
[device]
wifi.scan-rand-mac-address=0
```
Save and close file then reboot.


Thanks for the information but unfortunately only the next boot worked.

I started with kernel 4.8.0-46, I saw your message and corrected the file according to what you specified.
Then  I rebooted and used the option with kernel 4.10.0-32 and that time it  worked, wifi, bluetooth and audio included, but I rebooted to try  another kernel version.
With the kernel 4.10.0-33.37 it did not work. So I decided to shut down not restart.
I started with  the kernel 4.10.0-32 also did not work.
I  rebooted with 4.8.0-46, the version with, which I had no problems, it did not  work either, I commented the lines, maybe it was a problem for that  older version and I turned it off.
I switched on 4.8.0-46 and it did not work either so this time I deleted the lines and turned off
Now I started with an older version 4.4.0-72 and I went back to have wifi, I take the opportunity to answer the message.

Anyway thank you very much, I will try, this and other methods.

What do you think if I try with kernel 4.12.xx? It has any sense? Or downgrade NetWorkManager?

Regards
Jordan

---

### Post by wildmanne39 on 2017-09-17
Did you add that file to each 4.10 version of the kernel you were trying to use? Why not just use the latest 4.10 kernel update and stay with it, there is no reason to try all of them, use the one that works.

---

### Post by jeremy31 on 2017-09-17
I would check ```
dpkg -l | grep linux-image
```
It wouldn't surprise me if the linux-image-extra files aren't missing from some kernels

---

### Post by jordanmoises on 2017-10-03
Sorry I've been very busy with my work and I almost did not use my notebook these days.

[B]
To wildmanne39[/B]
I only have one file "/etc/NetworkManager/NetworkManager.conf". I don't understar your question

**For jeremy31**
dpkg -l | grep linux-image
rc  linux-image-3.11.0-23-generic                               3.11.0-23.40                                  amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-29-generic                               3.13.0-29.53                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-55-generic                               3.13.0-55.94                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-61-generic                               3.13.0-61.100                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-19-generic                                3.8.0-19.30                                   amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-19-generic                               4.10.0-19.21                                  amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-20-generic                               4.10.0-20.22                                  amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-21-generic                               4.10.0-21.23                                  amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-22-generic                               4.10.0-22.24                                  amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-24-generic                               4.10.0-24.28                                  amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-26-generic                               4.10.0-26.30                                  amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-28-generic                               4.10.0-28.32                                  amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-32-generic                               4.10.0-32.36                                  amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-33-generic                               4.10.0-33.37                                  amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-35-generic                               4.10.0-35.39                                  amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-62-generic                                4.4.0-62.83                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-66-generic                                4.4.0-66.87                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-71-generic                                4.4.0-71.92                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-72-generic                                4.4.0-72.93                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-46-generic                                4.8.0-46.49                                   amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-23-generic                         3.11.0-23.40                                  amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-29-generic                         3.13.0-29.53                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-55-generic                         3.13.0-55.94                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-61-generic                         3.13.0-61.100                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-19-generic                          3.8.0-19.30                                   amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-19-generic                         4.10.0-19.21                                  amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-20-generic                         4.10.0-20.22                                  amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-21-generic                         4.10.0-21.23                                  amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-22-generic                         4.10.0-22.24                                  amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-24-generic                         4.10.0-24.28                                  amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-26-generic                         4.10.0-26.30                                  amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-28-generic                         4.10.0-28.32                                  amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-32-generic                         4.10.0-32.36                                  amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-33-generic                         4.10.0-33.37                                  amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-35-generic                         4.10.0-35.39                                  amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-62-generic                          4.4.0-62.83                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-66-generic                          4.4.0-66.87                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-71-generic                          4.4.0-71.92                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-72-generic                          4.4.0-72.93                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-46-generic                          4.8.0-46.49                                   amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-generic   

Today my first 3 starts  were with a version of the **4.8.XX** kernel and my wifi did not work, the  4th attempt I started using a new version of the kernel that was  updated, the "**4.10.0-35-generic**" and my wifi works correctly, with which I understand less what the real problem is. Which makes me believe that it is a random or hardware problem.

I leave in pastebin the output of the script wireless-info
[https://pastebin.com/0Ugt7JL6](https://pastebin.com/0Ugt7JL6)

regards
Jordan

---

### Post by Hadaka on 2017-10-04
Hi, Thank you for providing detailed information.
The following items were noted in your wireless report and may be causing you errors and wifi failure.
```
#area51_1   WPA1 WPA2  yes     * 
#area51_1   TKIP
#area51_1   [ipv6] method=auto
#ISO code   country 00: DFS-UNSET
```

*To correct please edit your area51_1 IPv4,IPv6 and Security settings/configuration. and Change to..
```
#Security -> wpa2 only NO Tkip
#IPv4 -> Automatic DHCP
#IPv6 -> Ignore
```
*ISO Country code..*IF correct timezone = America/Argentina/Buenos_Aires  ..Then do..
 ```
sudo iw reg set AR
sudo sed -i 's/=.*/=AR/' /etc/default/crda
```
~Disconnect wired connection,boot and test wireless

*Kernel Issues..
**Ubuntu 17.04 ~only~ Copy and Paste.
```
printf "[device]\nwifi.scan-rand-mac-address=0\n"| sudo tee -a /etc/NetworkManager/*.conf
```
The wifi card is -> Atheros AR9485 Wireless Network Adapter [168c:0032] 
The driver is ath9k and the *PCI-ID is 168c:0032 ...This PCI-ID must be in the kernel for wifi to function.
**To verify the PCI-ID is in the kernel after the kernel is loaded/changed . Copy and Paste the following command.
```
modinfo ath9k | grep $(lspci -n | awk '/0280/{print toupper($3)}'| cut -c 6-)
```
**IF PCI-ID is present for that kernel ... "0032" will be output in red.  [COLOR=#ff0000]**0032**[/COLOR]
Hope this helps.

---

### Post by wildmanne39 on 2017-10-04
You are missing the extra image files from several of the kernels that is causing your issue, I am about to walk out the door I believe the following command will pull them in as well as reinstall the kernel and dkms package:
```
sudo apt install --reinstall linux-headers-$(uname -r) build-essential dkms
```
You may need to boot each kernel and run that command then reboot. If that does not install the extra image file you will have to install just the image file one at time in each kernel, but you really do not need that many kernels they are just taking up space, it is best to remove all but the two newest ones.

---

