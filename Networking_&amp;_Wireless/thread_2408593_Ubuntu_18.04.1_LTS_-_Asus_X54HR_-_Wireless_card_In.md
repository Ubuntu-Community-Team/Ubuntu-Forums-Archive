---
title: "Ubuntu 18.04.1 LTS - Asus X54HR - Wireless card Intel (changed)"
date: 2018-12-20
forum: Networking &amp; Wireless
---

### Post by caxetax on 2018-12-20
Hello,

I have installed Ubuntu 18.04.1 LTS on my Asus X54HR and Im having wireless network issues, In front of router have slow conection sometimes and one bar missing in wireless symbol.
Is like I have low signal in front of router. I think that can be driver issues, because I have windows 7 installed in this computer too and nothing of this happen.

Speed conection windows 7 - between 40-50Mbps Download and 20-30Mbps Updload.
Speed conection Ubuntu 18.04.1 LTS - with slow conection issue - between 0,1 - 0,5Mbps Download and can't do the upload test;
                                                          with "normal conection" - between 15 - 25Mbps Download and 5 - 15Mbps Upload;

Cant you help me fixing this?
I can provide more info if you need it.

Thank you.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
My card was changed and now I have one Intel Centrino:  
 ```

*-network
                descrição: Interface sem fio
                produto: Centrino Wireless-N 100
                fabricante: Intel Corporation
                ID físico: 0
                informações do barramento: pci@0000:03:00.0
                nome lógico: wlp3s0
                versão: 00
                serial: 78:92:9c:2e:ca:04
                largura: 64 bits
                clock: 33MHz
                capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuração: broadcast=yes driver=iwlwifi driverversion=4.15.0-42-generic firmware=39.31.5.1 build 32895 ip=192.168.1.66 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                recursos: irq:35 memória:dea00000-dea01fff
```


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
_**FULL HARDWARE INFO:**_

```

descrição: Notebook
    produto: K54HR
    fabricante: ASUSTeK Computer Inc.
    versão: 1.0
    serial: C5N0AS56445121A
    largura: 64 bits
    capacidades: smbios-2.6 dmi-2.6 smp vsyscall32
    configuração: boot=normal chassis=notebook family=K uuid=807E8B06-BEA5-E181-25C5-10BF4826D3CC
  *-core
       descrição: Placa-mãe
       produto: K54HR
       fabricante: ASUSTeK Computer Inc.
       ID físico: 0
       versão: 1.0
       serial: BSN12345678901234567
       slot: MIDDLE
     *-firmware
          descrição: BIOS
          fabricante: American Megatrends Inc.
          ID físico: 0
          versão: K54HR.205
          date: 06/20/2012
          tamanho: 64KiB
          capacidade: 2496KiB
          capacidades: pci upgrade shadowing cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification
     *-cpu
          descrição: CPU
          produto: Intel(R) Pentium(R) CPU B960 @ 2.20GHz
          fabricante: Intel Corp.
          ID físico: 4
          informações do barramento: cpu@0
          versão: Intel(R) Pentium(R) CPU B960 @ 2.20GHz
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          tamanho: 1922MHz
          capacidade: 4GHz
          largura: 64 bits
          clock: 100MHz
          capacidades: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave lahf_lm epb pti ssbd ibrs ibpb stibp xsaveopt dtherm arat pln pts flush_l1d cpufreq
          configuração: cores=2 enabledcores=1
        *-cache
             descrição: L1 cache
             ID físico: 5
             slot: L1-Cache
             tamanho: 32KiB
             capacidade: 32KiB
             capacidades: internal write-back instruction
             configuração: level=1
     *-memory
          descrição: Memória do sistema
          ID físico: 3f
          slot: Placa do sistema ou placa-mãe
          tamanho: 4GiB
        *-bank:0
             descrição: SODIMM DDR3 Síncrono 1333 MHz (0,8 ns)
             produto: M471B5273DH0-CH9
             fabricante: Samsung
             ID físico: 0
             serial: 976B3C15
             slot: ChannelA-DIMM0
             tamanho: 4GiB
             largura: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             descrição: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-06-04 15:22+0000Last-Translator: Mykas0 <Mykas0@gmail.com>Language-Team: Portuguese <pt@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2018-07-12 13:19+0000X-Generator: Launchpad (build 18719) [vazio]
             produto: [Empty]
             fabricante: [Empty]
             ID físico: 1
             serial: [Empty]
             slot: ChannelB-DIMM0
     *-pci
          descrição: Host bridge
          produto: 2nd Generation Core Processor Family DRAM Controller
          fabricante: Intel Corporation
          ID físico: 100
          informações do barramento: pci@0000:00:00.0
          versão: 09
          largura: 32 bits
          clock: 33MHz
        *-pci:0
             descrição: PCI bridge
             produto: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             fabricante: Intel Corporation
             ID físico: 1
             informações do barramento: pci@0000:00:01.0
             versão: 09
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pm msi pciexpress normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:24 porta de E/S:d000(tamanho=4096) memória:dfe00000-dfefffff porta de E/S:c0000000(tamanho=268435456)
           *-display
                descrição: VGA compatible controller
                produto: Seymour [Radeon HD 6400M/7400M Series]
                fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
                ID físico: 0
                informações do barramento: pci@0000:01:00.0
                versão: 00
                largura: 64 bits
                clock: 33MHz
                capacidades: pm pciexpress msi vga_controller bus_master cap_list rom
                configuração: driver=radeon latency=0
                recursos: irq:33 memória:c0000000-cfffffff memória:dfe20000-dfe3ffff porta de E/S:d000(tamanho=256) memória:c0000-dffff
           *-multimedia
                descrição: Audio device
                produto: Caicos HDMI Audio [Radeon HD 6450 / 7450/8450/8490 OEM / R5 230/235/235X OEM]
                fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
                ID físico: 0.1
                informações do barramento: pci@0000:01:00.1
                versão: 00
                largura: 64 bits
                clock: 33MHz
                capacidades: pm pciexpress msi bus_master cap_list
                configuração: driver=snd_hda_intel latency=0
                recursos: irq:37 memória:dfe40000-dfe43fff
        *-communication
             descrição: Communication controller
             produto: 6 Series/C200 Series Chipset Family MEI Controller #1
             fabricante: Intel Corporation
             ID físico: 16
             informações do barramento: pci@0000:00:16.0
             versão: 04
             largura: 64 bits
             clock: 33MHz
             capacidades: pm msi bus_master cap_list
             configuração: driver=mei_me latency=0
             recursos: irq:34 memória:dff0b000-dff0b00f
        *-usb:0
             descrição: USB controller
             produto: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             fabricante: Intel Corporation
             ID físico: 1a
             informações do barramento: pci@0000:00:1a.0
             versão: 05
             largura: 32 bits
             clock: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuração: driver=ehci-pci latency=0
             recursos: irq:16 memória:dff08000-dff083ff
           *-usbhost
                produto: EHCI Host Controller
                fabricante: Linux 4.15.0-42-generic ehci_hcd
                ID físico: 1
                informações do barramento: usb@1
                nome lógico: usb1
                versão: 4.15
                capacidades: usb-2.00
                configuração: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   descrição: hub USB
                   produto: Integrated Rate Matching Hub
                   fabricante: Intel Corp.
                   ID físico: 1
                   informações do barramento: usb@1:1
                   versão: 0.00
                   capacidades: usb-2.00
                   configuração: driver=hub slots=6 speed=480Mbit/s
                 *-usb
                      descrição: Vídeo
                      produto: USB 2.0 UVC VGA WebCam
                      fabricante: Azurewave
                      ID físico: 2
                      informações do barramento: usb@1:1.2
                      versão: 11.30
                      serial: 0x0001
                      capacidades: usb-2.00
                      configuração: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-multimedia
             descrição: Audio device
             produto: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             fabricante: Intel Corporation
             ID físico: 1b
             informações do barramento: pci@0000:00:1b.0
             versão: 05
             largura: 64 bits
             clock: 33MHz
             capacidades: pm msi pciexpress bus_master cap_list
             configuração: driver=snd_hda_intel latency=0
             recursos: irq:36 memória:dff00000-dff03fff
        *-pci:1
             descrição: PCI bridge
             produto: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             fabricante: Intel Corporation
             ID físico: 1c
             informações do barramento: pci@0000:00:1c.0
             versão: b5
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:25 porta de E/S:c000(tamanho=4096) memória:df400000-dfdfffff porta de E/S:d2200000(tamanho=10485760)
        *-pci:2
             descrição: PCI bridge
             produto: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             fabricante: Intel Corporation
             ID físico: 1c.1
             informações do barramento: pci@0000:00:1c.1
             versão: b5
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:26 porta de E/S:b000(tamanho=4096) memória:dea00000-df3fffff porta de E/S:d1700000(tamanho=10485760)
           *-network
                descrição: Interface sem fio
                produto: Centrino Wireless-N 100
                fabricante: Intel Corporation
                ID físico: 0
                informações do barramento: pci@0000:03:00.0
                nome lógico: wlp3s0
                versão: 00
                serial: 78:92:9c:2e:ca:04
                largura: 64 bits
                clock: 33MHz
                capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuração: broadcast=yes driver=iwlwifi driverversion=4.15.0-42-generic firmware=39.31.5.1 build 32895 ip=192.168.1.66 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                recursos: irq:35 memória:dea00000-dea01fff
        *-pci:3
             descrição: PCI bridge
             produto: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             fabricante: Intel Corporation
             ID físico: 1c.3
             informações do barramento: pci@0000:00:1c.3
             versão: b5
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:27 porta de E/S:a000(tamanho=4096) memória:de000000-de9fffff porta de E/S:d0c00000(tamanho=10485760)
           *-usb
                descrição: USB controller
                produto: ASM1042 SuperSpeed USB Host Controller
                fabricante: ASMedia Technology Inc.
                ID físico: 0
                informações do barramento: pci@0000:04:00.0
                versão: 00
                largura: 64 bits
                clock: 33MHz
                capacidades: msi msix pm pciexpress xhci bus_master cap_list
                configuração: driver=xhci_hcd latency=0
                recursos: irq:19 memória:de000000-de007fff
              *-usbhost:0
                   produto: xHCI Host Controller
                   fabricante: Linux 4.15.0-42-generic xhci-hcd
                   ID físico: 0
                   informações do barramento: usb@3
                   nome lógico: usb3
                   versão: 4.15
                   capacidades: usb-2.00
                   configuração: driver=hub slots=2 speed=480Mbit/s
              *-usbhost:1
                   produto: xHCI Host Controller
                   fabricante: Linux 4.15.0-42-generic xhci-hcd
                   ID físico: 1
                   informações do barramento: usb@4
                   nome lógico: usb4
                   versão: 4.15
                   capacidades: usb-3.00
                   configuração: driver=hub slots=2 speed=5000Mbit/s
        *-pci:4
             descrição: PCI bridge
             produto: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             fabricante: Intel Corporation
             ID físico: 1c.5
             informações do barramento: pci@0000:00:1c.5
             versão: b5
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:28 porta de E/S:9000(tamanho=4096) memória:dd600000-ddffffff porta de E/S:d0100000(tamanho=10485760)
           *-network
                descrição: Ethernet interface
                produto: AR8151 v2.0 Gigabit Ethernet
                fabricante: Qualcomm Atheros
                ID físico: 0
                informações do barramento: pci@0000:05:00.0
                nome lógico: enp5s0
                versão: c0
                serial: 10:bf:48:26:d3:cc
                capacidade: 1Gbit/s
                largura: 64 bits
                clock: 33MHz
                capacidades: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuração: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
                recursos: irq:38 memória:dd600000-dd63ffff porta de E/S:9000(tamanho=128)
        *-usb:1
             descrição: USB controller
             produto: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             fabricante: Intel Corporation
             ID físico: 1d
             informações do barramento: pci@0000:00:1d.0
             versão: 05
             largura: 32 bits
             clock: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuração: driver=ehci-pci latency=0
             recursos: irq:23 memória:dff07000-dff073ff
           *-usbhost
                produto: EHCI Host Controller
                fabricante: Linux 4.15.0-42-generic ehci_hcd
                ID físico: 1
                informações do barramento: usb@2
                nome lógico: usb2
                versão: 4.15
                capacidades: usb-2.00
                configuração: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   descrição: hub USB
                   produto: Integrated Rate Matching Hub
                   fabricante: Intel Corp.
                   ID físico: 1
                   informações do barramento: usb@2:1
                   versão: 0.00
                   capacidades: usb-2.00
                   configuração: driver=hub slots=6 speed=480Mbit/s
        *-isa
             descrição: ISA bridge
             produto: HM65 Express Chipset Family LPC Controller
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
             produto: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             fabricante: Intel Corporation
             ID físico: 1f.2
             informações do barramento: pci@0000:00:1f.2
             versão: 05
             largura: 32 bits
             clock: 66MHz
             capacidades: storage msi pm ahci_1.0 bus_master cap_list
             configuração: driver=ahci latency=0
             recursos: irq:32 porta de E/S:e070(tamanho=8) porta de E/S:e060(tamanho=4) porta de E/S:e050(tamanho=8) porta de E/S:e040(tamanho=4) porta de E/S:e020(tamanho=32) memória:dff06000-dff067ff
        *-serial
             descrição: SMBus
             produto: 6 Series/C200 Series Chipset Family SMBus Controller
             fabricante: Intel Corporation
             ID físico: 1f.3
             informações do barramento: pci@0000:00:1f.3
             versão: 05
             largura: 64 bits
             clock: 33MHz
             configuração: driver=i801_smbus latency=0
             recursos: irq:18 memória:dff05000-dff050ff porta de E/S:e000(tamanho=32)
     *-scsi:0
          ID físico: 1
          nome lógico: scsi0
          capacidades: emulated
        *-disk
             descrição: ATA Disk
             produto: WDC WD2500BPVT-2
             fabricante: Western Digital
             ID físico: 0.0.0
             informações do barramento: scsi@0:0.0.0
             nome lógico: /dev/sda
             versão: 1A01
             serial: WD-WX31A6115285
             tamanho: 232GiB (250GB)
             capacidades: partitioned partitioned:dos
             configuração: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=000d70ee
           *-volume:0
                descrição: Windows NTFS volume
                ID físico: 1
                informações do barramento: scsi@0:0.0.0,1
                nome lógico: /dev/sda1
                versão: 3.1
                serial: 32b1-57cd
                tamanho: 98MiB
                capacidade: 100MiB
                capacidades: primary bootable ntfs initialized
                configuração: clustersize=4096 created=2018-12-09 09:22:23 filesystem=ntfs label=System Reserved state=clean
           *-volume:1
                descrição: Windows NTFS volume
                ID físico: 2
                informações do barramento: scsi@0:0.0.0,2
                nome lógico: /dev/sda2
                versão: 3.1
                serial: f428b922-c124-cd47-a3ad-2dd054db131b
                tamanho: 131GiB
                capacidade: 131GiB
                capacidades: primary ntfs initialized
                configuração: clustersize=4096 created=2018-12-09 09:22:37 filesystem=ntfs state=clean
           *-volume:2
                descrição: Extended partition
                ID físico: 3
                informações do barramento: scsi@0:0.0.0,3
                nome lógico: /dev/sda3
                tamanho: 101GiB
                capacidade: 101GiB
                capacidades: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   descrição: volume EXT4
                   fabricante: Linux
                   ID físico: 5
                   nome lógico: /dev/sda5
                   nome lógico: /boot
                   versão: 1.0
                   serial: 7dc3b898-1b42-41e1-a7ae-a69cef28684e
                   tamanho: 1000MiB
                   capacidade: 1000MiB
                   capacidades: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                   configuração: created=2018-12-09 19:56:14 filesystem=ext4 lastmountpoint=/boot modified=2018-01-28 15:58:40 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2018-01-28 15:58:40 state=mounted
              *-logicalvolume:1
                   descrição: volume EXT4
                   fabricante: Linux
                   ID físico: 6
                   nome lógico: /dev/sda6
                   nome lógico: /
                   versão: 1.0
                   serial: e691c7f6-23d5-40fe-8573-dfaf1c850f74
                   tamanho: 24GiB
                   capacidade: 24GiB
                   capacidades: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                   configuração: created=2018-12-09 19:56:14 filesystem=ext4 lastmountpoint=/ modified=2012-06-20 18:38:12 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2018-01-28 15:58:21 state=mounted
              *-logicalvolume:2
                   descrição: Linux swap volume
                   ID físico: 7
                   nome lógico: /dev/sda7
                   versão: 1
                   serial: 264cd85e-e76e-40fa-8acd-83bad86ec4b1
                   tamanho: 8535MiB
                   capacidade: 8535MiB
                   capacidades: nofs swap initialized
                   configuração: filesystem=swap pagesize=4096
              *-logicalvolume:3
                   descrição: volume EXT4
                   fabricante: Linux
                   ID físico: 8
                   nome lógico: /dev/sda8
                   nome lógico: /home
                   versão: 1.0
                   serial: b7839f1f-7d4d-4a13-8b82-c6762d5c2fae
                   tamanho: 67GiB
                   capacidade: 67GiB
                   capacidades: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                   configuração: created=2018-12-09 19:56:18 filesystem=ext4 lastmountpoint=/home modified=2018-01-28 15:58:42 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2018-01-28 15:58:42 state=mounted
     *-scsi:1
          ID físico: 2
          nome lógico: scsi1
          capacidades: emulated
        *-disk
             descrição: ATA Disk
             produto: Hitachi HTS54502
             fabricante: Hitachi
             ID físico: 0.0.0
             informações do barramento: scsi@1:0.0.0
             nome lógico: /dev/sdb
             versão: C60N
             serial: 091018PBY2061SC65Y1L
             tamanho: 232GiB (250GB)
             capacidades: partitioned partitioned:dos
             configuração: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=26952412
           *-volume
                descrição: Windows NTFS volume
                ID físico: 1
                informações do barramento: scsi@1:0.0.0,1
                nome lógico: /dev/sdb1
                nome lógico: /mnt/53C2D8A2122E7F22
                versão: 3.1
                serial: 40fdbc18-c101-234a-9008-2b6382f29cc7
                tamanho: 232GiB
                capacidade: 232GiB
                capacidades: primary ntfs initialized
                configuração: clustersize=4096 created=2018-12-09 23:56:02 filesystem=ntfs label=Share mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
```

---

