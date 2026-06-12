---
title: "My intelnetwork adapter connects,but eventually becomes idle after afround 10-15 mins"
date: 2020-04-21
forum: Networking &amp; Wireless
---

### Post by Vignesh_S on 2020-04-21
These are details of my adapter
*-network
       description: Wireless interface
       product: Wireless 3165
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:16:00.0
       logical name: wlp22s0
       version: 79
       serial: 98:3b:8f:a5:be:5a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.3.0-46-generic firmware=29.1044073957.0 ip=192.168.43.16 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:45 memory:fe900000-fe901fff

whenever i turn on my laptop, it autoconnects the saved network as usual routine in any ubuntu computer. 
But after around 15-20 mins , network gets disconnected but shows connected and idle, no response. When i turn off wifi, the wifi adapter is as if it got removed from my pc, there r no traces of it, it dissapears from gui asif no wifi adapter connected.

i tried installing drivers but i am confused what to do, i am using dell inspiron 3565,
description: Notebook
    product: Inspiron 15-3565 (078E)
    vendor: Dell Inc.
    version: 1.10.1
    serial: 4TFQ4P2
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 smp vsyscall32
    configuration: boot=normal chassis=notebook family=Inspiron sku=078E uuid=44454C4C-5400-1046-8051-B4C04F345032
  *-core
       description: Motherboard
       product: Inspiron 15-3565
       vendor: Dell Inc.
       physical id: 0
       version: A00
       serial: .4TFQ4P2.CNWSC008CS00Q7.
       slot: Default string
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: 1.10.1
          date: 09/03/2018
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int14serial int17printer acpi usb biosbootspecification netboot uefi
     *-cache:0
          description: L1 cache
          physical id: 17
          slot: L1 CACHE
          size: 160KiB
          capacity: 160KiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 18
          slot: L2 CACHE
          size: 1MiB
          capacity: 1MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=2
     *-memory
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR4 [empty]
             product: A1_PartNum0
             vendor: 000000000000
             physical id: 0
             serial: A1_SerialNum0
             slot: DIMM 0
             width: 64 bits
        *-bank:1
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
             product: HMA851S6CJR6N-UH
             vendor: 009C360B0000
             physical id: 1
             serial: 2D3861E9
             slot: DIMM 1
             size: 4GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
     *-cpu
          description: CPU
          product: AMD A6-9225 RADEON R4, 5 COMPUTE CORES 2C+3G
          vendor: Advanced Micro Devices [AMD]
          physical id: 2c
          bus info: cpu@0
          version: AMD A6-9225 RADEON R4, 5 COMPUTE CORES 2C+3G
          slot: P0
          size: 1761MHz
          capacity: 2600MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good acc_power nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm perfctr_core perfctr_nb bpext ptsc mwaitx cpb hw_pstate ssbd vmmcall fsgsbase bmi1 avx2 smep bmi2 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif overflow_recov cpufreq
          configuration: cores=2 enabledcores=2 threads=2
     *-pci:0
          description: Host bridge
          product: Family 15h (Models 60h-6fh) Processor Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-generic:0 UNCLAIMED
             description: IOMMU
             product: Family 15h (Models 60h-6fh) I/O Memory Management Unit
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi ht cap_list
             configuration: latency=0
        *-display
             description: VGA compatible controller
             product: Stoney [Radeon R2/R3/R4/R5 Graphics]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: ea
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=amdgpu latency=0
             resources: irq:43 memory:e8000000-efffffff memory:f0000000-f07fffff ioport:f000(size=256) memory:feb00000-feb3ffff memory:c0000-dffff

Intel 3165 network adapter used[ATTACH=CONFIG]285573[/ATTACH]

---

### Post by chili555 on 2020-04-21
You might try turning off pwer saving:```

sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*

```Is your router set to autoselect the channel or even the band; that is 2.4 vs. 5 gHz? There are several things you might do to improve stability.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

Any improvement?

---

