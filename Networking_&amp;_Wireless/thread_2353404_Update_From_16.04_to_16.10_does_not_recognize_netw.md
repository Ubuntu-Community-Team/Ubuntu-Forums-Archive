---
title: "Update From 16.04 to 16.10 does not recognize network adapter"
date: 2017-02-21
forum: Networking &amp; Wireless
---

### Post by saladriel on 2017-02-21
Hi there, I upgraded today one of my PCs from 16.04 to 16.10, now Ubuntu seems not to recognize my network adapter anymore!
Network icon on the top right of the screen tells "Device not handled" (It's roughly translated from Italian, so the correspondent message in English could not be the same, sorry)
If I go into "System Configuration -> Network" it says "Cable  Not handled"

The adapter is the Asus M2N-XE onboard ethernet adapter. Does anyone experienced the same problem or has any idea to solve it?

Any answer is much appreciated...

---

### Post by saladriel on 2017-02-22
Bump

Uh, ok. Thanx a lot. I'm new to this forums.

Ok, I'm running some tests and the command ```
sudlo lshw -C network
``` outputs nothing. 


The command ```
sudo lshw
``` outputs lots of things and amongst them an interesting part:

```

-bridge DISABLED
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1e:8c:7b:a1:36
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:23 memory:dfefd000-dfefdfff ioport:d480(size=8)


```

As I can understand the ethernet bridge seems to be detected as disabled by the system, but if I go into the board BIOS and look into Southbridge configuration, the ethernet adapter is enabled and operative... 

Another tip: trying to recreate the ethernet connection with the GUI Ubuntu clearly detects a MAC Address, but seems not to be able to handle the adapter...

---

### Post by wildmanne39 on 2017-02-22
*Thread moved to **Networking & Wireless**.*

---

### Post by wildmanne39 on 2017-02-22
I do not know much about this ethernet card except it use to have one issue that required a parameter to be set, this card is almost never seen.

Please do:
```
echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
```
Reboot

---

### Post by saladriel on 2017-02-22
Done, but it does not seem to change a thing, both in system behaviour and in lshw outputs

---

### Post by wildmanne39 on 2017-02-22
Please post the output of:
```
rfkill list all
ifconfig
```
Thanks

---

### Post by saladriel on 2017-02-22
Ok, here it is:

```
rfkill list all
``` does not give any output


```
ifconfig
``` gives this output:

```
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Loopback locale)
        RX packets 4262  bytes 262604 (262.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4262  bytes 262604 (262.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



```

---

### Post by wildmanne39 on 2017-02-22
Please post the output of:
```
lsmod
```
it says bridge network, did you set it up as a bridge network?

---

### Post by saladriel on 2017-02-22
Well, no. Not that I'm aware of...


Btw, here it is the output 

```
Module                  Size  Used by
nls_iso8859_1          16384  0
uas                    24576  0
usb_storage            73728  1 uas
binfmt_misc            20480  1
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     45056  1
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           86016  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               110592  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
kvm_amd                73728  0
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
kvm                   598016  1 kvm_amd
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    86016  21 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
irqbypass              16384  1 kvm
soundcore              16384  1 snd
input_leds             16384  0
serio_raw              16384  0
shpchp                 36864  0
k8temp                 16384  0
asus_atk0110           20480  0
i2c_nforce2            16384  0
mac_hid                16384  0
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  0
x_tables               36864  1 ip_tables
autofs4                40960  2
amdkfd                139264  1
amd_iommu_v2           20480  1 amdkfd
radeon               1515520  3
i2c_algo_bit           16384  1 radeon
ttm                   102400  1 radeon
pata_acpi              16384  0
drm_kms_helper        167936  1 radeon
syscopyarea            16384  1 drm_kms_helper
psmouse               139264  0
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   368640  6 radeon,ttm,drm_kms_helper
forcedeth              69632  0
sata_nv                32768  2
pata_amd               20480  1
floppy                 73728  0
fjes                   28672  0

```

Uh, now I see what you mean... now that I think of it is possible that posting just a sub part of the ***sudo lshw ***command I could have misguided both you and myself.
Here it is the full output, you're obviously more expert than me, maybe you can pick the correct interesting part
```
description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=60C69A7B-8DFE-D511-BBD9-001E8C7BA136
  *-core
       description: Motherboard
       product: M2N-XE
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev x.xx
       serial: MS1C7CBA5305073
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0103
          date: 10/24/2007
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          serial: To Be Filled By O.E.M.
          slot: AM2
          size: 1800MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp 3dnowext 3dnow rep_good nopl extd_apicid eagerfpu pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch vmmcall cpufreq
          configuration: cores=2 enabledcores=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
             configuration: level=2
     *-memory:0
          description: System Memory
          physical id: 2f
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1,2 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:900(size=256)
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:e00(size=64) ioport:600(size=64) ioport:700(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP61 USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:dfeff000-dfefffff
        *-usbhost
             product: OHCI PCI host controller
             vendor: Linux 4.8.0-38-generic ohci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 4.08
             capabilities: usb-1.10
             configuration: driver=hub slots=10 speed=12Mbit/s
     *-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:dfefec00-dfefecff
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 4.8.0-38-generic ehci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 4.08
             capabilities: usb-2.00
             configuration: driver=hub slots=10 speed=480Mbit/s
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:dfef8000-dfefbfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
     *-bridge DISABLED
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1e:8c:7b:a1:36
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:23 memory:dfefd000-dfefdfff ioport:d480(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:d400(size=8) ioport:d080(size=4) ioport:d000(size=8) ioport:cc00(size=4) ioport:c880(size=16) memory:dfefc000-dfefcfff
     *-ide:2
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8.1
          bus info: pci@0000:00:08.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:20 ioport:c800(size=8) ioport:c480(size=4) ioport:c400(size=8) ioport:c080(size=4) ioport:c000(size=16) memory:dfeef000-dfeeffff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24 ioport:e000(size=4096) memory:dff00000-dfffffff ioport:c0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: RV670 [Radeon HD 3870]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 0
             bus info: pci@0000:02:00.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:27 memory:c0000000-cfffffff memory:dfff0000-dfffffff ioport:e800(size=256) memory:c0000-dffff
        *-multimedia
             description: Audio device
             product: RV670/680 HDMI Audio [Radeon HD 3690/3800 Series]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:28 memory:dffec000-dffeffff
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:26
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: a
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Maxtor 6L200P0
             vendor: Maxtor
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1G10
             serial: L41B5FSH
             size: 189GiB (203GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=a2c6a2c6
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /usr/local
                version: 1.0
                serial: cdd8d3c8-f7e9-4b15-afbc-a429f145bcf0
                size: 189GiB
                capacity: 189GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-04-30 12:50:41 filesystem=ext4 modified=2017-02-22 22:21:29 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2017-02-22 22:21:29 state=mounted
     *-scsi:1
          physical id: d
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG HD501LJ
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 0-12
             serial: S0MUJDWQ139574
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=3fe93fe8
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /
                version: 1.0
                serial: e6a9c35d-f16d-4882-8447-ddaf792ac2d6
                size: 456GiB
                capacity: 456GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2015-04-30 12:50:48 filesystem=ext4 lastmountpoint=/ modified=2017-02-22 23:21:14 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-02-22 18:37:58 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sdb2
                size: 9535MiB
                capacity: 9535MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap volume
                   physical id: 5
                   logical name: /dev/sdb5
                   version: 1
                   serial: 29ed3478-89db-4565-9f8e-f9023af096ce
                   size: 9535MiB
                   capacity: 9535MiB
                   capabilities: nofs swap initialized
                   configuration: filesystem=swap pagesize=4096

```
Hope it hepls

---

### Post by wildmanne39 on 2017-02-22
My connection says this:
```
-network               
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 05
       serial: b8:97:5a:22:19:9d
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:25 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff

```
I do not have it plugged in but you notice it does not say bridged?

Do you have network manager installed and running or is this a server?

If not sure please post the output of:
```
ps aux | egrep 'Network|wicd'
```
Thanks

---

### Post by saladriel on 2017-02-22
No, I do not have installed any network manager that I am aware of and no... it is not a server.

here it is your output:
```
luca      3001  0.0  0.0  14256   924 pts/4    S+   23:16   0:00 grep -E --color=auto network|wicd



```

The words **network **and **wicd** at the end are written in red.


Btw, the first two reboots Nautilus gave me some problems related with Dropbox, asking me to restart it. The message window was locked and did not get any click on its buttons, so I rebooted. After a couple of times the message stopped to pop up. In any case, the network was non functional since the first boot with 16.10


EDIT:
My bad, I wrote **network **instead of **Network**.

Here it is the correct output:
```
root       760  0.0  0.8 468288 16932 ?        Ssl  22:21   0:00 /usr/sbin/NetworkManager --no-daemon
luca      3080  0.0  0.0  14256  1020 pts/4    S+   23:24   0:00 grep -E --color=auto Network|wicd



```

---

### Post by wildmanne39 on 2017-02-22
```
sudo ifconfig enp2s0 up
```
does it come on?

---

### Post by saladriel on 2017-02-22
Nope, it gives this error (Translated from Italian the best I can)

```
enp2s0: ERROR reading interface flags: no corresponding device
```

---

### Post by wildmanne39 on 2017-02-22
Do you have two lines in the top right corner of the screen if so that is network manager, click on it and make sure networking is enabled.

---

### Post by saladriel on 2017-02-22
Networking is enabled in the drop down menu I have in the top right part of the screen (opened clicking the "radio waves" icon that right now is empty. It used to be "filled up" when the network connection worked)

EDIT:

The firts line of the menu is grayed out and tells "Ethernet Network" 
The second line of the menu is also grayed out and tells "Device not handled"

---

### Post by wildmanne39 on 2017-02-22
Does this command make a difference:
```
sudo systemctl start NetworkManager.service
sudo systemctl enable NetworkManager.service

```

---

### Post by saladriel on 2017-02-22
No, nothing seems to change

---

### Post by jeremy31 on 2017-02-22
Please post results for ```
cat /etc/network/interfaces
```

---

### Post by saladriel on 2017-02-22
Here it is: ```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback



```

---

### Post by wildmanne39 on 2017-02-22
I am also pretty sure it is not being managed, just looking to see how to do that by command line it has been years since I have done that.

---

### Post by saladriel on 2017-02-22
Thanx, your effort is very appreciated

---

### Post by saladriel on 2017-02-25
Bump

EDIT:

I see somebody else is having a very similar problem (if not the same) with Lubuntu 16.10
Maybe exchanging informations can help solving the problem

Here is the link:
[https://ubuntuforums.org/showthread.php?t=2353634&p=13612627#post13612627](https://ubuntuforums.org/showthread.php?t=2353634&p=13612627#post13612627)

---

### Post by jeremy31 on 2017-02-25
Lets try a variation of wildmanne39's command ```
sudo ifconfig eth0 up
```
And let's see if there is anything from ```
ls /etc/netctl/
```

---

### Post by saladriel on 2017-02-26
First commnand seems to bring no change to the system, /etc/netctl/ does not exists

---

### Post by jeremy31 on 2017-02-26
Is there any result for ```
ls /etc/network/interfaces.d/
```

---

### Post by saladriel on 2017-02-26
Directory existing, yet empty

---

### Post by saladriel on 2017-03-03
Bump

---

### Post by saladriel on 2017-03-19
Reading other posts on this very forum gave me the solution. 
Here it is:

/etc/NetworkManager$ ifconfig   gave this result:
```

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.4  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::21e:8cff:fe7b:a136  prefixlen 64  scopeid 0x20<link>
        ether 00:1e:8c:7b:a1:36  txqueuelen 1000  (Ethernet)
        RX packets 133359  bytes 196354831 (196.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 68506  bytes 5096767 (5.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Loopback locale)
        RX packets 7572  bytes 461351 (461.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7572  bytes 461351 (461.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```


EDIT:
the command /etc/NetworkManager$ nmcli device show  gave this result:

```
GENERAL.DEVICE:                         eth0
GENERAL.TIPO:                           ethernet
GENERAL.HWADDR:                         00:1E:8C:7B:A1:36
GENERAL.MTU:                            1500
GENERAL.STATO:                          10 (non gestito)
GENERAL.CONNESSIONE:                    --
GENERAL.PERCORSO-CON:                   --
WIRED-PROPERTIES.PORTANTE:              on
IP4.INDIRIZZO[1]:                       192.168.1.4/24
IP4.GATEWAY:                            192.168.1.1
IP4.INSTRADAMENTO[1]:                   dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.INDIRIZZO[1]:                       fe80::21e:8cff:fe7b:a136/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         lo
GENERAL.TIPO:                           loopback
GENERAL.HWADDR:                         00:00:00:00:00:00
GENERAL.MTU:                            65536
GENERAL.STATO:                          10 (non gestito)
GENERAL.CONNESSIONE:                    --
GENERAL.PERCORSO-CON:                   --
IP4.INDIRIZZO[1]:                       127.0.0.1/8
IP4.GATEWAY:                            
IP6.INDIRIZZO[1]:                       ::1/128
IP6.GATEWAY:   

```
END OF EDIT

and my /etc/network/interfaces file contained:
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

EDIT:
as you can see only one of the two is handled in /etc/network/interfaces
END OF EDIT


The issue has been solved by editing /etc/network/interface with:

```
sudo nano /etc/network/interfaces
```

adding this part below the one already existing:
```


auto eth0
iface eth0 inet dhcp

```

saving and rebooting the system.

---

### Post by donbastiano on 2017-03-19
Same problem here, I think is a bug and I don't think is right to change /etc/network/interfaces when NetworkManager is used. I have also 16.04 in another partition and no problem with the connection and as in 16.10 and 17.04, just lo is present. Maybe there is some conflict with systemd and especially with the network service?

---

### Post by saladriel on 2017-03-19
Honestly I don't know... I'm pretty new to Linux and I don't know it's inner way of working. 
Maybe some expert can comment this solution and give us some insight, it would be very appreciate, I love to learn new things.

---

### Post by jeremy31 on 2017-03-19
donbastiano, you are correct to a degree as we normally won't add any interface to that interfaces file if we want Network Manager to manage the interface

saladriel, if you click on the networking icon near the clock and choose edit connections, what is listed?  I just booted 16.10 on USB with ethernet working

---

### Post by saladriel on 2017-03-20
It lists "Ethernet Connection 1"  and under the column "last usage" it says "Never".

My understanding of Ubuntu are rather limited, but seems like Network Manager can't for some reason recognize the adapter while setting it manually works.

EDIT:

I can confirm Network Manager is not handling my ethernet connection right now, as I'm writing this addition to the post with "Network Functionality" disabled from Network Manager.

---

### Post by donbastiano on 2017-03-20
saladriel: thank you and sorry, maybe I have to write another post but it was the same problem and I want just to clarify that the problem is not really solved :)

jeremy31: thank you, I switched back to 16.04 for this problem, I updated just to have a more recent kernel and Mesa. As said, I tried also to upgrade to the 17.04 beta but the problem persists. I don't know but maybe depends on something missing in the upgrade procedure, a symbolic link or something like that, I think that the live works regularly.
I'm on a laptop and with the work-around suggested, NM doesn't appear to work properly, It shows always the connected icons on the app indicator also if I disconnect the cable, furthermore in this scenario, the wireless doesn't connect on my test.

---

### Post by saladriel on 2017-03-20
No need to be sorry, donbastiano. In fact it is a good thing what you have pointed out. 
Right now my connection is up and running, very stable. But now I know it is more a hack than a solution.

---

### Post by jeremy31 on 2017-03-20
donbastiano, thanks as I might just install it as I have plenty of room on the hard drive

I still am not sure why the lshw results showed bridge disabled instead of network disabled

---

### Post by saladriel on 2017-03-21
Wondering the same thing... If you have some tests for me to run, I'll do. Just ask

---

