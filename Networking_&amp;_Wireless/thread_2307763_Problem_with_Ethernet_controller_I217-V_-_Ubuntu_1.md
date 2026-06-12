---
title: "Problem with Ethernet controller I217-V - Ubuntu 15.10"
date: 2015-12-28
forum: Networking &amp; Wireless
---

### Post by Diogo Falcomer on 2015-12-28
Hello, 


I've installed ubuntu 15.10 on my laptop, wifi works fine but the ethernet doesn't work, searching on internet tried to modprobe the e1000e module, or install intel driver but when i try to make install on intel driver gives a error.

When reboot, dmesg shows that error:

dmesg | grep e100
```
 
[ 2668.476764] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.5-k[ 2668.476766] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[ 2668.476860] e1000e 0000:00:19.0: PCI INT A: failed to register GSI
[ 2668.476864] e1000e: probe of 0000:00:19.0 failed with error -16
[ 7581.964113] Modules linked in: e1000e ptp pps_core e1000 rfcomm ctr ccm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) binfmt_misc bnep vboxdrv(OE) arc4 rtl8723be btcoexist rtl8723_common rtl_pci rtlwifi snd_hda_codec_hdmi mac80211 snd_hda_codec_via rtsx_pci_ms memstick snd_hda_codec_generic cfg80211 nls_iso8859_1 drbg ansi_cprng dm_crypt uvcvideo intel_rapl btusb iosf_mbi btrtl btbcm videobuf2_vmalloc btintel videobuf2_memops bluetooth videobuf2_core v4l2_common videodev x86_pkg_temp_thermal media intel_powerclamp coretemp snd_hda_intel kvm_intel snd_hda_codec kvm snd_hda_core snd_hwdep crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul snd_pcm glue_helper snd_seq_midi ablk_helper cryptd snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer joydev input_leds serio_raw
[ 8676.934825] Modules linked in: e1000e ptp pps_core e1000 rfcomm ctr ccm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) binfmt_misc bnep vboxdrv(OE) arc4 rtl8723be btcoexist rtl8723_common rtl_pci rtlwifi snd_hda_codec_hdmi mac80211 snd_hda_codec_via rtsx_pci_ms memstick snd_hda_codec_generic cfg80211 nls_iso8859_1 drbg ansi_cprng dm_crypt uvcvideo intel_rapl btusb iosf_mbi btrtl btbcm videobuf2_vmalloc btintel videobuf2_memops bluetooth videobuf2_core v4l2_common videodev x86_pkg_temp_thermal media intel_powerclamp coretemp snd_hda_intel kvm_intel snd_hda_codec kvm snd_hda_core snd_hwdep crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul snd_pcm glue_helper snd_seq_midi ablk_helper cryptd snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer joydev input_leds serio_raw

```

lspci
```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 05)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.5 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #6 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)

```

sudo lshw
```
ak-bsb-2839
    descrição: Computer
    largura: 64 bits
    capacidades: smbios-2.8 vsyscall32
  *-core
       descrição: Motherboard
       ID físico: 0
     *-memory
          descrição: Memória do sistema
          ID físico: 0
          tamanho: 7873MiB
     *-cpu
          produto: Intel(R) Core(TM) i5-4200M CPU @ 2.50GHz
          fabricante: Intel Corp.
          ID físico: 1
          informações do barramento: cpu@0
          tamanho: 2599MHz
          capacidade: 3100MHz
          largura: 64 bits
          capacidades: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt cpufreq
     *-pci
          descrição: Host bridge
          produto: Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller
          fabricante: Intel Corporation
          ID físico: 100
          informações do barramento: pci@0000:00:00.0
          versão: 06
          largura: 32 bits
          clock: 33MHz
        *-display
             descrição: VGA compatible controller
             produto: 4th Gen Core Processor Integrated Graphics Controller
             fabricante: Intel Corporation
             ID físico: 2
             informações do barramento: pci@0000:00:02.0
             versão: 06
             largura: 64 bits
             clock: 33MHz
             capacidades: msi pm vga_controller bus_master cap_list rom
             configuração: driver=i915 latency=0
             recursos: irq:27 memória:f6c00000-f6ffffff memória:e0000000-efffffff porta de E/S:f000(tamanho=64)
        *-multimedia:0
             descrição: Audio device
             produto: Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
             fabricante: Intel Corporation
             ID físico: 3
             informações do barramento: pci@0000:00:03.0
             versão: 06
             largura: 64 bits
             clock: 33MHz
             capacidades: pm msi pciexpress bus_master cap_list
             configuração: driver=snd_hda_intel latency=0
             recursos: irq:29 memória:f7c34000-f7c37fff
        *-usb:0
             descrição: USB controller
             produto: 8 Series/C220 Series Chipset Family USB xHCI
             fabricante: Intel Corporation
             ID físico: 14
             informações do barramento: pci@0000:00:14.0
             versão: 05
             largura: 64 bits
             clock: 33MHz
             capacidades: pm msi xhci bus_master cap_list
             configuração: driver=xhci_hcd latency=0
             recursos: irq:24 memória:f7c20000-f7c2ffff
           *-usbhost:0
                produto: xHCI Host Controller
                fabricante: Linux 4.2.0-22-lowlatency xhci-hcd
                ID físico: 0
                informações do barramento: usb@2
                nome lógico: usb2
                versão: 4.02
                capacidades: usb-3.00
                configuração: driver=hub slots=6 speed=5000Mbit/s
           *-usbhost:1
                produto: xHCI Host Controller
                fabricante: Linux 4.2.0-22-lowlatency xhci-hcd
                ID físico: 1
                informações do barramento: usb@1
                nome lógico: usb1
                versão: 4.02
                capacidades: usb-2.00
                configuração: driver=hub slots=14 speed=480Mbit/s
              *-usb:0
                   descrição: Teclado
                   produto: Dell USB Keyboard
                   fabricante: Dell
                   ID físico: 1
                   informações do barramento: usb@1:1
                   versão: 3.06
                   capacidades: usb-1.10
                   configuração: driver=usbhid maxpower=70mA speed=1Mbit/s
              *-usb:1 DISPONÍVEL
                   descrição: Dispositivo USB genérico
                   produto: EgisTec_ES603
                   fabricante: EgisTec
                   ID físico: 5
                   informações do barramento: usb@1:5
                   versão: 2.00
                   capacidades: usb-1.10
                   configuração: maxpower=100mA speed=12Mbit/s
              *-usb:2
                   descrição: Mouse
                   produto: USB OPTICAL MOUSE
                   fabricante: Trust International B.V.
                   ID físico: 6
                   informações do barramento: usb@1:6
                   versão: 1.00
                   capacidades: usb-1.10
                   configuração: driver=usbhid maxpower=100mA speed=1Mbit/s
              *-usb:3
                   descrição: Interface sem fio bluetooth
                   produto: Bluetooth Radio
                   fabricante: Realtek
                   ID físico: 7
                   informações do barramento: usb@1:7
                   versão: 2.00
                   serial: 00e04c000001
                   capacidades: bluetooth usb-2.10
                   configuração: driver=btusb maxpower=500mA speed=12Mbit/s
              *-usb:4
                   descrição: Vídeo
                   produto: BisonCam, NB Pro
                   fabricante: Generic
                   ID físico: 8
                   informações do barramento: usb@1:8
                   versão: 6.05
                   serial: 200901010001
                   capacidades: usb-2.00
                   configuração: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:5 DISPONÍVEL
                   descrição: Leitor de Smart Card
                   produto: EMV Smartcard Reader
                   fabricante: Generic
                   ID físico: 9
                   informações do barramento: usb@1:9
                   versão: 1.20
                   capacidades: usb-2.01
                   configuração: maxpower=50mA speed=12Mbit/s
        *-communication DISPONÍVEL
             descrição: Communication controller
             produto: 8 Series/C220 Series Chipset Family MEI Controller #1
             fabricante: Intel Corporation
             ID físico: 16
             informações do barramento: pci@0000:00:16.0
             versão: 04
             largura: 64 bits
             clock: 33MHz
             capacidades: pm msi cap_list
             configuração: latency=0
             recursos: memória:f7c3e000-f7c3e00f
        *-network DISPONÍVEL
             descrição: Ethernet controller
             produto: Ethernet Connection I217-V
             fabricante: Intel Corporation
             ID físico: 19
             informações do barramento: pci@0000:00:19.0
             versão: 05
             largura: 32 bits
             clock: 33MHz
             capacidades: pm msi bus_master cap_list
             configuração: latency=0
             recursos: memória:f7c00000-f7c1ffff memória:f7c3d000-f7c3dfff porta de E/S:f080(tamanho=32)
        *-usb:1
             descrição: USB controller
             produto: 8 Series/C220 Series Chipset Family USB EHCI #2
             fabricante: Intel Corporation
             ID físico: 1a
             informações do barramento: pci@0000:00:1a.0
             versão: 05
             largura: 32 bits
             clock: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuração: driver=ehci-pci latency=0
             recursos: irq:16 memória:f7c3c000-f7c3c3ff
           *-usbhost
                produto: EHCI Host Controller
                fabricante: Linux 4.2.0-22-lowlatency ehci_hcd
                ID físico: 1
                informações do barramento: usb@3
                nome lógico: usb3
                versão: 4.02
                capacidades: usb-2.00
                configuração: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   descrição: hub USB
                   fabricante: Intel Corp.
                   ID físico: 1
                   informações do barramento: usb@3:1
                   versão: 0.05
                   capacidades: usb-2.00
                   configuração: driver=hub slots=6 speed=480Mbit/s
        *-multimedia:1
             descrição: Audio device
             produto: 8 Series/C220 Series Chipset High Definition Audio Controller
             fabricante: Intel Corporation
             ID físico: 1b
             informações do barramento: pci@0000:00:1b.0
             versão: 05
             largura: 64 bits
             clock: 33MHz
             capacidades: pm msi pciexpress bus_master cap_list
             configuração: driver=snd_hda_intel latency=0
             recursos: irq:28 memória:f7c30000-f7c33fff
        *-pci:0
             descrição: PCI bridge
             produto: 8 Series/C220 Series Chipset Family PCI Express Root Port #1
             fabricante: Intel Corporation
             ID físico: 1c
             informações do barramento: pci@0000:00:1c.0
             versão: d5
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:16 porta de E/S:2000(tamanho=4096) memória:df200000-df3fffff porta de E/S:df400000(tamanho=2097152)
        *-pci:1
             descrição: PCI bridge
             produto: 8 Series/C220 Series Chipset Family PCI Express Root Port #3
             fabricante: Intel Corporation
             ID físico: 1c.2
             informações do barramento: pci@0000:00:1c.2
             versão: d5
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:18 porta de E/S:e000(tamanho=4096) memória:f7b00000-f7bfffff
           *-network
                descrição: Interface sem fio
                produto: RTL8723BE PCIe Wireless Network Adapter
                fabricante: Realtek Semiconductor Co., Ltd.
                ID físico: 0
                informações do barramento: pci@0000:02:00.0
                nome lógico: wlp2s0
                versão: 00
                serial: 18:cf:5e:8f:52:52
                largura: 64 bits
                clock: 33MHz
                capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuração: broadcast=yes driver=rtl8723be driverversion=4.2.0-22-lowlatency firmware=N/A ip=10.10.1.154 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                recursos: irq:18 porta de E/S:e000(tamanho=256) memória:f7b00000-f7b03fff
        *-pci:2
             descrição: PCI bridge
             produto: 8 Series/C220 Series Chipset Family PCI Express Root Port #4
             fabricante: Intel Corporation
             ID físico: 1c.3
             informações do barramento: pci@0000:00:1c.3
             versão: d5
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:19 memória:f7a00000-f7afffff
           *-generic
                descrição: Unassigned class
                produto: RTS5229 PCI Express Card Reader
                fabricante: Realtek Semiconductor Co., Ltd.
                ID físico: 0
                informações do barramento: pci@0000:03:00.0
                versão: 01
                largura: 32 bits
                clock: 33MHz
                capacidades: pm msi pciexpress bus_master cap_list
                configuração: driver=rtsx_pci latency=0
                recursos: irq:25 memória:f7a00000-f7a00fff
        *-pci:3
             descrição: PCI bridge
             produto: 8 Series/C220 Series Chipset Family PCI Express Root Port #6
             fabricante: Intel Corporation
             ID físico: 1c.5
             informações do barramento: pci@0000:00:1c.5
             versão: d5
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:17 porta de E/S:d000(tamanho=4096) memória:f7000000-f79fffff porta de E/S:f0000000(tamanho=10485760)
        *-usb:2
             descrição: USB controller
             produto: 8 Series/C220 Series Chipset Family USB EHCI #1
             fabricante: Intel Corporation
             ID físico: 1d
             informações do barramento: pci@0000:00:1d.0
             versão: 05
             largura: 32 bits
             clock: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuração: driver=ehci-pci latency=0
             recursos: irq:23 memória:f7c3b000-f7c3b3ff
           *-usbhost
                produto: EHCI Host Controller
                fabricante: Linux 4.2.0-22-lowlatency ehci_hcd
                ID físico: 1
                informações do barramento: usb@4
                nome lógico: usb4
                versão: 4.02
                capacidades: usb-2.00
                configuração: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   descrição: hub USB
                   fabricante: Intel Corp.
                   ID físico: 1
                   informações do barramento: usb@4:1
                   versão: 0.05
                   capacidades: usb-2.00
                   configuração: driver=hub slots=8 speed=480Mbit/s
        *-isa
             descrição: ISA bridge
             produto: HM87 Express LPC Controller
             fabricante: Intel Corporation
             ID físico: 1f
             informações do barramento: pci@0000:00:1f.0
             versão: 05
             largura: 32 bits
             clock: 33MHz
             capacidades: isa bus_master cap_list
             configuração: driver=lpc_ich latency=0
             recursos: irq:0
        *-storage
             descrição: SATA controller
             produto: 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
             fabricante: Intel Corporation
             ID físico: 1f.2
             informações do barramento: pci@0000:00:1f.2
             versão: 05
             largura: 32 bits
             clock: 66MHz
             capacidades: storage msi pm ahci_1.0 bus_master cap_list
             configuração: driver=ahci latency=0
             recursos: irq:26 porta de E/S:f0d0(tamanho=8) porta de E/S:f0c0(tamanho=4) porta de E/S:f0b0(tamanho=8) porta de E/S:f0a0(tamanho=4) porta de E/S:f060(tamanho=32) memória:f7c3a000-f7c3a7ff
        *-serial DISPONÍVEL
             descrição: SMBus
             produto: 8 Series/C220 Series Chipset Family SMBus Controller
             fabricante: Intel Corporation
             ID físico: 1f.3
             informações do barramento: pci@0000:00:1f.3
             versão: 05
             largura: 64 bits
             clock: 33MHz
             configuração: latency=0
             recursos: memória:f7c39000-f7c390ff porta de E/S:f040(tamanho=32)
     *-scsi:0
          ID físico: 2
          nome lógico: scsi0
          capacidades: emulated
        *-cdrom
             descrição: DVD-RAM writer
             produto: DVDRAM GU90N
             fabricante: HL-DT-ST
             ID físico: 0.0.0
             informações do barramento: scsi@0:0.0.0
             nome lógico: /dev/cdrom
             nome lógico: /dev/cdrw
             nome lógico: /dev/dvd
             nome lógico: /dev/dvdrw
             nome lógico: /dev/sr0
             versão: 1.00
             capacidades: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuração: ansiversion=5 status=nodisc
     *-scsi:1
          ID físico: 3
          nome lógico: scsi5
          capacidades: emulated
        *-disk
             descrição: ATA Disk
             produto: WDC WD7500LPCX-6
             fabricante: Western Digital
             ID físico: 0.0.0
             informações do barramento: scsi@5:0.0.0
             nome lógico: /dev/sda
             versão: 1A01
             serial: WD-WX41A849L2Z6
             tamanho: 698GiB (750GB)
             capacidades: gpt-1.00 partitioned partitioned:gpt
             configuração: ansiversion=5 guid=1b305fee-dc07-4dc4-a978-f4f0294d419a logicalsectorsize=512 sectorsize=4096
           *-volume:0 DISPONÍVEL
                descrição: Windows FAT volume
                fabricante: mkfs.fat
                ID físico: 1
                informações do barramento: scsi@5:0.0.0,1
                versão: FAT32
                serial: 0e3d-f73f
                tamanho: 146MiB
                capacidade: 147MiB
                capacidades: boot fat initialized
                configuração: FATs=2 filesystem=fat
           *-volume:1
                descrição: volume EXT4
                fabricante: Linux
                ID físico: 2
                informações do barramento: scsi@5:0.0.0,2
                nome lógico: /dev/sda2
                nome lógico: /
                versão: 1.0
                serial: 51ab166a-a2a9-4ae8-bbc3-ce89f0dfc7f3
                tamanho: 42GiB
                capacidades: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuração: created=2015-12-26 13:27:24 filesystem=ext4 lastmountpoint=/ modified=2015-12-28 08:51:07 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-12-28 08:51:12 state=mounted
           *-volume:2
                descrição: Linux swap volume
                fabricante: Linux
                ID físico: 3
                informações do barramento: scsi@5:0.0.0,3
                nome lógico: /dev/sda3
                versão: 1
                serial: 025ca6a8-dcfe-4d09-a274-8f8546d29bc9
                tamanho: 3814MiB
                capacidade: 3814MiB
                capacidades: nofs precious readonly hidden nomount swap initialized
                configuração: filesystem=swap pagesize=4095
           *-volume:3
                descrição: volume EXT4
                fabricante: Linux
                ID físico: 4
                informações do barramento: scsi@5:0.0.0,4
                nome lógico: /dev/sda4
                nome lógico: /home
                versão: 1.0
                serial: d9dc2496-fb55-4b56-81e4-2dd9bce7ee9e
                tamanho: 651GiB
                capacidades: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuração: created=2015-12-26 13:27:26 filesystem=ext4 lastmountpoint=/home modified=2015-12-28 08:51:17 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2015-12-28 08:51:17 state=mounted
```

---

