---
title: "Bluetooth USB Adapter not working Ubuntu 20.04 LTS"
date: 2020-08-05
forum: Networking &amp; Wireless
---

### Post by bl75 on 2020-08-05
I bought a Hommie BT-501 USB bluetooth adapter which works with Win 10 but not with Ubuntu 20.04. Bluetooth cannot be activated in the settings as the adapter is not found, apparently due to an address conflict (see below).

Does anyone have an idea how to solve that?



sudo systemctl status bluetooth gives the following result:[INDENT]
 bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor pre>
     Active: active (running) since Wed 2020-08-05 09:50:17 CEST; 1min 48s ago
       Docs: man:bluetoothd(8)
   Main PID: 868 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 18881)
     Memory: 2.0M
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;868 /usr/lib/bluetooth/bluetoothd

Aug 05 09:50:17 eO-116-PC1-Ubuntu systemd[1]: Starting Bluetooth service...
Aug 05 09:50:17 eO-116-PC1-Ubuntu bluetoothd[868]: Bluetooth daemon 5.53
Aug 05 09:50:17 eO-116-PC1-Ubuntu systemd[1]: Started Bluetooth service.
Aug 05 09:50:17 eO-116-PC1-Ubuntu bluetoothd[868]: Starting SDP server
Aug 05 09:50:17 eO-116-PC1-Ubuntu bluetoothd[868]: Bluetooth management interface
Aug 05 09:50:26 eO-116-PC1-Ubuntu bluetoothd[868]: [COLOR=#ff0000]No Bluetooth address for index 0[/COLOR]
[/INDENT]

So it seems due to an address problem... and Blueman-manager does not start because it doesn't find the device:[INDENT]sudo blueman-manager
[sudo] Passwort für bl: 
blueman-manager version 2.1.2 starting
Failed to enable bluetooth
blueman-manager 10.18.26 ERROR    Manager:118 on_dbus_name_appeared: Default adapter not found, trying first available.
blueman-manager 10.18.26 ERROR    Manager:122 on_dbus_name_appeared: No adapter(s) found, exiting

[/INDENT]

Bluetooth seems activated and not blocked:
[INDENT]                         bl@eO-116-PC1-Ubuntu:~$ dmesg | grep -i bluetooth
 [   12.633165] Bluetooth: hci0: RTL: download fw command failed (-110)
 [  405.995000] usb 1-9: Product: Bluetooth Radio
 [  405.999179] Bluetooth: hci0: RTL: examining hci_ver=0a hci_rev=000b lmp_ver=0a lmp_subver=8761
 [  406.000160] Bluetooth: hci0: RTL: rom_version status=0 version=1
 [  406.000165] Bluetooth: hci0: RTL: loading rtl_bt/rtl8761a_fw.bin
 [  406.000320] Bluetooth: hci0: RTL: loading rtl_bt/rtl8761a_config.bin
 [  406.000352] bluetooth hci0: Direct firmware load for rtl_bt/rtl8761a_config.bin failed with error -2
 [  406.000367] Bluetooth: hci0: RTL: cfg_sz -2, total sz 20204
 [  408.089180] Bluetooth: hci0: command 0xfc20 tx timeout
 [  416.089190] Bluetooth: hci0: RTL: download fw command failed (-110)
 bl@eO-116-PC1-Ubuntu:~$ 
 bl@eO-116-PC1-Ubuntu:~$ 
 bl@eO-116-PC1-Ubuntu:~$ hciconfig --all
 hci0:    Type: Primary  Bus: USB
     BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
     DOWN  
     RX bytes:581 acl:0 sco:0 events:82 errors:0
     TX bytes:20534 acl:0 sco:0 commands:83 errors:0
     Features: 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00
     Packet type: DM1 DH1 HV1  

     Link policy:  
     Link mode: SLAVE ACCEPT  

                       
 bl@eO-116-PC1-Ubuntu:~$ rfkill list all
 1: hci0: Bluetooth
     Soft blocked: no
     Hard blocked: no
  
  
[/INDENT]

---

### Post by mIk3_08 on 2020-08-05
something wrong with the firmware:[B]
[ 406.000352] bluetooth hci0: Direct firmware load for rtl_bt/rtl8761a_config.bin failed with error -2[/B]

---

### Post by bl75 on 2020-08-05
```
bl@eO-116-PC1-Ubuntu:~$ sudo lshw
eo-116-pc1-ubuntu           
    Beschreibung: Arbeitsplatzrechner
    Produkt: HP EliteDesk 800 G5 SFF (6BD64AV)
    Hersteller: HP
    Seriennummer: CZC0218Q61
    Breite: 64 bits
    Fähigkeiten: smbios-3.1.0 dmi-3.1.0 smp vsyscall32
    Konfiguration: administrator_password=disabled boot=normal chassis=desktop family=103C_53307F HP EliteDesk frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=6BD64AV uuid=F1A1BA76-F899-C1EC-9AD2-98CB625BE99A
  *-core
       Beschreibung: Hauptplatine
       Produkt: 8592
       Hersteller: HP
       Physische ID: 0
       Version: KBC Version 08.95.00
       Seriennummer: PHUQC0HE2DNF4W
     *-firmware
          Beschreibung: BIOS
          Hersteller: HP
          Physische ID: 1
          Version: R01 Ver. 02.04.02
          date: 12/27/2019
          Größe: 64KiB
          Kapazität: 32MiB
          Fähigkeiten: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot uefi
     *-memory
          Beschreibung: Systemspeicher
          Physische ID: 7
          Steckplatz: Systemplatine oder Hauptplatine
          Größe: 16GiB
        *-bank:0
             Beschreibung: DIMM DDR4 Synchron 2667 MHz (0,4 ns)
             Produkt: HMA81GU6CJR8N-VK
             Hersteller: Hynix/Hyundai
             Physische ID: 0
             Seriennummer: 539ACF90
             Steckplatz: DIMM1
             Größe: 8GiB
             Breite: 64 bits
             Takt: 2667MHz (0.4ns)
        *-bank:1
             Beschreibung: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-05-30 08:16+0000Last-Translator: Hendrik Knackstedt <Unknown>Language-Team: German <de@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2020-07-09 17:42+0000X-Generator: Launchpad (build 4809fcb62f445aaa3ae919f7f6c3cc7d156ea57a)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-05-30 08:16+0000Last-Translator: Hendrik Knackstedt <Unknown>Language-Team: German <de@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2020-07-09 17:42+0000X-Generator: Launchpad (build 4809fcb62f445aaa3ae919f7f6c3cc7d156ea57a) [leer]
             Physische ID: 1
             Steckplatz: DIMM2
        *-bank:2
             Beschreibung: DIMM DDR4 Synchron 2667 MHz (0,4 ns)
             Produkt: HMA81GU6CJR8N-VK
             Hersteller: Hynix/Hyundai
             Physische ID: 2
             Seriennummer: 539ACDF2
             Steckplatz: DIMM3
             Größe: 8GiB
             Breite: 64 bits
             Takt: 2667MHz (0.4ns)
        *-bank:3
             Beschreibung: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-05-30 08:16+0000Last-Translator: Hendrik Knackstedt <Unknown>Language-Team: German <de@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2020-07-09 17:42+0000X-Generator: Launchpad (build 4809fcb62f445aaa3ae919f7f6c3cc7d156ea57a)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-05-30 08:16+0000Last-Translator: Hendrik Knackstedt <Unknown>Language-Team: German <de@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2020-07-09 17:42+0000X-Generator: Launchpad (build 4809fcb62f445aaa3ae919f7f6c3cc7d156ea57a) [leer]
             Physische ID: 3
             Steckplatz: DIMM4
     *-cache:0
          Beschreibung: L1 Cache
          Physische ID: 15
          Steckplatz: L1 Cache
          Größe: 512KiB
          Kapazität: 512KiB
          Fähigkeiten: synchronous internal write-back unified
          Konfiguration: level=1
     *-cache:1
          Beschreibung: L2 Cache
          Physische ID: 16
          Steckplatz: L2 Cache
          Größe: 2MiB
          Kapazität: 2MiB
          Fähigkeiten: synchronous internal write-back unified
          Konfiguration: level=2
     *-cache:2
          Beschreibung: L3 Cache
          Physische ID: 17
          Steckplatz: L3 Cache
          Größe: 12MiB
          Kapazität: 12MiB
          Fähigkeiten: synchronous internal write-back unified
          Konfiguration: level=3
     *-cpu
          Beschreibung: CPU
          Produkt: Intel(R) Core(TM) i7-9700 CPU @ 3.00GHz
          Hersteller: Intel Corp.
          Physische ID: 18
          Bus-Informationen: cpu@0
          Version: Intel(R) Core(TM) i7-9700 CPU @ 3.00GHz
          Seriennummer: To Be Filled By O.E.M.
          Steckplatz: U3E1
          Größe: 1516MHz
          Kapazität: 4700MHz
          Breite: 64 bits
          Takt: 100MHz
          Fähigkeiten: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d arch_capabilities cpufreq
          Konfiguration: cores=8 enabledcores=8 threads=8
     *-pci
          Beschreibung: Host bridge
          Produkt: 8th Gen Core 8-core Desktop Processor Host Bridge/DRAM Registers [Coffee Lake S]
          Hersteller: Intel Corporation
          Physische ID: 100
          Bus-Informationen: pci@0000:00:00.0
          Version: 0d
          Breite: 32 bits
          Takt: 33MHz
          Konfiguration: driver=skl_uncore
          Ressourcen: irq:0
        *-display
             Beschreibung: VGA compatible controller
             Produkt: UHD Graphics 630 (Desktop 9 Series)
             Hersteller: Intel Corporation
             Physische ID: 2
             Bus-Informationen: pci@0000:00:02.0
             Version: 02
             Breite: 64 bits
             Takt: 33MHz
             Fähigkeiten: pciexpress msi pm vga_controller bus_master cap_list rom
             Konfiguration: driver=i915 latency=0
             Ressourcen: irq:136 memory:e0000000-e0ffffff memory:d0000000-dfffffff ioport:3000(Größe=64) memory:c0000-dffff
        *-generic
             Beschreibung: Signal processing controller
             Produkt: Cannon Lake PCH Thermal Controller
             Hersteller: Intel Corporation
             Physische ID: 12
             Bus-Informationen: pci@0000:00:12.0
             Logischer Name: /dev/fb0
             Version: 10
             Breite: 64 bits
             Takt: 33MHz
             Fähigkeiten: pm msi cap_list fb
             Konfiguration: depth=32 driver=intel_pch_thermal latency=0 mode=1920x1080 visual=truecolor xres=1920 yres=1080
             Ressourcen: iomemory:400-3ff irq:16 memory:4000107000-4000107fff
        *-usb
             Beschreibung: USB controller
             Produkt: Cannon Lake PCH USB 3.1 xHCI Host Controller
             Hersteller: Intel Corporation
             Physische ID: 14
             Bus-Informationen: pci@0000:00:14.0
             Version: 10
             Breite: 64 bits
             Takt: 33MHz
             Fähigkeiten: pm msi xhci bus_master cap_list
             Konfiguration: driver=xhci_hcd latency=0
             Ressourcen: irq:123 memory:e1120000-e112ffff
           *-usbhost:0
                Produkt: xHCI Host Controller
                Hersteller: Linux 5.4.0-42-generic xhci-hcd
                Physische ID: 0
                Bus-Informationen: usb@1
                Logischer Name: usb1
                Version: 5.04
                Fähigkeiten: usb-2.00
                Konfiguration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   Beschreibung: Tastatur
                   Produkt: HP Wireless Slim Keyboard - Skylab EU
                   Hersteller: Lite-On Technology Corp.
                   Physische ID: 4
                   Bus-Informationen: usb@1:4
                   Version: 0.66
                   Fähigkeiten: usb-2.00
                   Konfiguration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usb:1
                   Beschreibung: Bluetooth-Schnittstelle
                   Produkt: Bluetooth Radio
                   Hersteller: Realtek
                   Physische ID: 9
                   Bus-Informationen: usb@1:9
                   Version: 2.00
                   Seriennummer: 00E04C239987
                   Fähigkeiten: bluetooth usb-1.10
                   Konfiguration: driver=btusb maxpower=500mA speed=12Mbit/s
              *-usb:2
                   Beschreibung: Massenspeichergerät
                   Produkt: USB Flash Disk
                   Hersteller: General
                   Physische ID: a
                   Bus-Informationen: usb@1:a
                   Version: 1.00
                   Seriennummer: 0664000000004B1D
                   Fähigkeiten: usb-2.00 scsi
                   Konfiguration: driver=usb-storage maxpower=100mA speed=480Mbit/s
              *-usb:3
                   Beschreibung: Video
                   Produkt: USB PHY 2.0
                   Hersteller: Jieli Technology
                   Physische ID: d
                   Bus-Informationen: usb@1:d
                   Version: 1.00
                   Fähigkeiten: usb-2.00
                   Konfiguration: driver=snd-usb-audio maxpower=500mA speed=480Mbit/s
           *-usbhost:1
                Produkt: xHCI Host Controller
                Hersteller: Linux 5.4.0-42-generic xhci-hcd
                Physische ID: 1
                Bus-Informationen: usb@2
                Logischer Name: usb2
                Version: 5.04
                Fähigkeiten: usb-3.10
                Konfiguration: driver=hub slots=10 speed=10000Mbit/s
              *-usb:0
                   Beschreibung: Massenspeichergerät
                   Produkt: External USB 3.0
                   Hersteller: TOSHIBA
                   Physische ID: 5
                   Bus-Informationen: usb@2:5
                   Logischer Name: scsi6
                   Version: 0.00
                   Seriennummer: 20160208009747F
                   Fähigkeiten: usb-3.00 scsi emulated scsi-host
                   Konfiguration: driver=usb-storage maxpower=896mA speed=5000Mbit/s
                 *-disk
                      Beschreibung: SCSI Disk
                      Produkt: External USB 3.0
                      Hersteller: TOSHIBA
                      Physische ID: 0.0.0
                      Bus-Informationen: scsi@6:0.0.0
                      Logischer Name: /dev/sdc
                      Version: 0
                      Seriennummer: F74790080206102
                      Größe: 931GiB (1TB)
                      Fähigkeiten: partitioned partitioned:dos
                      Konfiguration: ansiversion=6 logicalsectorsize=512 sectorsize=512 signature=4ba609e6
                    *-volume
                         Beschreibung: Windows NTFS Laufwerk
                         Physische ID: 1
                         Bus-Informationen: scsi@6:0.0.0,1
                         Logischer Name: /dev/sdc1
                         Logischer Name: /media/bl/TOSHIBA EXT
                         Version: 3.1
                         Seriennummer: 047d272d-dcaf-6947-ab7c-70311aec3a66
                         Größe: 931GiB
                         Kapazität: 931GiB
                         Fähigkeiten: primary ntfs initialized
                         Konfiguration: clustersize=4096 created=2016-08-19 15:36:10 filesystem=ntfs label=TOSHIBA EXT mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-usb:1
                   Beschreibung: Massenspeichergerät
                   Produkt: Elements SE 2622
                   Hersteller: Western Digital
                   Physische ID: 6
                   Bus-Informationen: usb@2:6
                   Logischer Name: scsi5
                   Version: 10.18
                   Seriennummer: 57585031453739354A56534D
                   Fähigkeiten: usb-3.10 scsi emulated scsi-host
                   Konfiguration: driver=usb-storage maxpower=896mA speed=5000Mbit/s
                 *-disk
                      Beschreibung: SCSI Disk
                      Produkt: Elements SE 2622
                      Hersteller: WD
                      Physische ID: 0.0.0
                      Bus-Informationen: scsi@5:0.0.0
                      Logischer Name: /dev/sdb
                      Version: 1018
                      Seriennummer: WXP1E795JVSM
                      Größe: 3725GiB (4TB)
                      Fähigkeiten: gpt-1.00 partitioned partitioned:gpt
                      Konfiguration: ansiversion=6 guid=93f3de55-d7c1-4912-b325-e328739ecffd logicalsectorsize=512 sectorsize=4096
                    *-volume
                         Beschreibung: Windows NTFS Laufwerk
                         Hersteller: Windows
                         Physische ID: 1
                         Bus-Informationen: scsi@5:0.0.0,1
                         Logischer Name: /dev/sdb1
                         Logischer Name: /media/bl/Elements SE
                         Version: 3.1
                         Seriennummer: aa45be89-c76a-7443-8b45-44ba399d1eb9
                         Größe: 1677GiB
                         Kapazität: 3725GiB
                         Fähigkeiten: ntfs initialized
                         Konfiguration: clustersize=4096 created=2019-11-11 06:54:08 filesystem=ntfs label=Elements SE mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 name=Elements SE state=mounted
                 *-enclosure UNGEFORDERT
                      Beschreibung: SCSI Enclosure
                      Produkt: SES Device
                      Hersteller: WD
                      Physische ID: 0.0.1
                      Bus-Informationen: scsi@5:0.0.1
                      Version: 1018
                      Seriennummer: WXP1E795JVSM
                      Konfiguration: ansiversion=6
        *-memory UNGEFORDERT
             Beschreibung: RAM memory
             Produkt: Cannon Lake PCH Shared SRAM
             Hersteller: Intel Corporation
             Physische ID: 14.2
             Bus-Informationen: pci@0000:00:14.2
             Version: 10
             Breite: 64 bits
             Takt: 33MHz (30.3ns)
             Fähigkeiten: pm cap_list
             Konfiguration: latency=0
             Ressourcen: iomemory:400-3ff memory:e1132000-e1133fff memory:4000106000-4000106fff
        *-communication:0
             Beschreibung: Communication controller
             Produkt: Cannon Lake PCH HECI Controller
             Hersteller: Intel Corporation
             Physische ID: 16
             Bus-Informationen: pci@0000:00:16.0
             Version: 10
             Breite: 64 bits
             Takt: 33MHz
             Fähigkeiten: pm msi bus_master cap_list
             Konfiguration: driver=mei_me latency=0
             Ressourcen: iomemory:400-3ff irq:135 memory:4000105000-4000105fff
        *-communication:1
             Beschreibung: Serial controller
             Produkt: Cannon Lake PCH Active Management Technology - SOL
             Hersteller: Intel Corporation
             Physische ID: 16.3
             Bus-Informationen: pci@0000:00:16.3
             Version: 10
             Breite: 32 bits
             Takt: 66MHz
             Fähigkeiten: msi pm 16550 cap_list
             Konfiguration: driver=serial latency=0
             Ressourcen: irq:19 ioport:3088(Größe=8) memory:e1137000-e1137fff
        *-sata
             Beschreibung: SATA controller
             Produkt: Cannon Lake PCH SATA AHCI Controller
             Hersteller: Intel Corporation
             Physische ID: 17
             Bus-Informationen: pci@0000:00:17.0
             Logischer Name: scsi1
             Version: 10
             Breite: 32 bits
             Takt: 66MHz
             Fähigkeiten: sata msi pm ahci_1.0 bus_master cap_list emulated
             Konfiguration: driver=ahci latency=0
             Ressourcen: irq:124 memory:e1130000-e1131fff memory:e1136000-e11360ff ioport:3080(Größe=8) ioport:3090(Größe=4) ioport:3060(Größe=32) memory:e1135000-e11357ff
           *-cdrom
                Beschreibung: DVD-RAM writer
                Produkt: DVDRW  GUD1N
                Hersteller: hp HLDS
                Physische ID: 0.0.0
                Bus-Informationen: scsi@1:0.0.0
                Logischer Name: /dev/cdrom
                Logischer Name: /dev/cdrw
                Logischer Name: /dev/dvd
                Logischer Name: /dev/dvdrw
                Logischer Name: /dev/sr0
                Version: LD04
                Fähigkeiten: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                Konfiguration: ansiversion=5 status=nodisc
        *-pci
             Beschreibung: PCI bridge
             Produkt: Cannon Lake PCH PCI Express Root Port #21
             Hersteller: Intel Corporation
             Physische ID: 1b
             Bus-Informationen: pci@0000:00:1b.0
             Version: f0
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: pci pciexpress msi pm normal_decode bus_master cap_list
             Konfiguration: driver=pcieport
             Ressourcen: irq:122 memory:e1000000-e10fffff
           *-storage
                Beschreibung: Non-Volatile memory controller
                Produkt: SK hynix
                Hersteller: SK hynix
                Physische ID: 0
                Bus-Informationen: pci@0000:01:00.0
                Version: 00
                Breite: 64 bits
                Takt: 33MHz
                Fähigkeiten: storage pm msi msix pciexpress nvm_express bus_master cap_list
                Konfiguration: driver=nvme latency=0
                Ressourcen: irq:16 memory:e1000000-e1003fff memory:e1005000-e1005fff memory:e1004000-e1004fff
        *-isa
             Beschreibung: ISA bridge
             Produkt: Q370 Chipset LPC/eSPI Controller
             Hersteller: Intel Corporation
             Physische ID: 1f
             Bus-Informationen: pci@0000:00:1f.0
             Version: 10
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: isa bus_master
             Konfiguration: latency=0
        *-multimedia
             Beschreibung: Audio device
             Produkt: Cannon Lake PCH cAVS
             Hersteller: Intel Corporation
             Physische ID: 1f.3
             Bus-Informationen: pci@0000:00:1f.3
             Version: 10
             Breite: 64 bits
             Takt: 33MHz
             Fähigkeiten: pm msi bus_master cap_list
             Konfiguration: driver=snd_hda_intel latency=64
             Ressourcen: iomemory:400-3ff iomemory:400-3ff irq:137 memory:4000100000-4000103fff memory:4000000000-40000fffff
        *-serial:0
             Beschreibung: SMBus
             Produkt: Cannon Lake PCH SMBus Controller
             Hersteller: Intel Corporation
             Physische ID: 1f.4
             Bus-Informationen: pci@0000:00:1f.4
             Version: 10
             Breite: 64 bits
             Takt: 33MHz
             Konfiguration: driver=i801_smbus latency=0
             Ressourcen: iomemory:400-3ff irq:16 memory:4000104000-40001040ff ioport:efa0(Größe=32)
        *-serial:1 UNGEFORDERT
             Beschreibung: Serial bus controller
             Produkt: Cannon Lake PCH SPI Controller
             Hersteller: Intel Corporation
             Physische ID: 1f.5
             Bus-Informationen: pci@0000:00:1f.5
             Version: 10
             Breite: 32 bits
             Takt: 33MHz
             Konfiguration: latency=0
             Ressourcen: memory:fe010000-fe010fff
        *-network
             Beschreibung: Ethernet interface
             Produkt: Ethernet Connection (7) I219-LM
             Hersteller: Intel Corporation
             Physische ID: 1f.6
             Bus-Informationen: pci@0000:00:1f.6
             Logischer Name: eno1
             Version: 10
             Seriennummer: 80:e8:2c:c9:2d:0f
             Größe: 100Mbit/s
             Kapazität: 1Gbit/s
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             Konfiguration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.5-4 ip=141.78.16.13 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             Ressourcen: irq:126 memory:e1100000-e111ffff
     *-pnp00:00
          Produkt: PnP device PNP0c02
          Physische ID: 0
          Fähigkeiten: pnp
          Konfiguration: driver=system
     *-pnp00:01
          Produkt: PnP device PNP0c02
          Physische ID: 2
          Fähigkeiten: pnp
          Konfiguration: driver=system
     *-pnp00:02
          Produkt: PnP device PNP0c02
          Physische ID: 3
          Fähigkeiten: pnp
          Konfiguration: driver=system
     *-pnp00:03
          Produkt: PnP device PNP0c02
          Physische ID: 4
          Fähigkeiten: pnp
          Konfiguration: driver=system
     *-pnp00:04
          Produkt: PnP device PNP0b00
          Physische ID: 5
          Fähigkeiten: pnp
          Konfiguration: driver=rtc_cmos
     *-pnp00:05
          Produkt: PnP device INT3f0d
          Physische ID: 6
          Fähigkeiten: pnp
          Konfiguration: driver=system
     *-pnp00:06
          Produkt: PnP device HPQ8002
          Physische ID: 8
          Fähigkeiten: pnp
          Konfiguration: driver=i8042 kbd
     *-pnp00:07
          Produkt: PnP device PNP0f13
          Physische ID: 9
          Fähigkeiten: pnp
          Konfiguration: driver=i8042 aux
     *-pnp00:08
          Produkt: PnP device PNP0c02
          Physische ID: a
          Fähigkeiten: pnp
          Konfiguration: driver=system
     *-pnp00:09
          Produkt: PnP device PNP0c02
          Physische ID: b
          Fähigkeiten: pnp
          Konfiguration: driver=system
     *-pnp00:0a
          Produkt: PnP device PNP0c02
          Physische ID: c
          Fähigkeiten: pnp
          Konfiguration: driver=system
     *-pnp00:0b
          Produkt: PnP device PNP0c02
          Physische ID: d
          Fähigkeiten: pnp
          Konfiguration: driver=system
     *-scsi
          Physische ID: e
          Bus-Informationen: usb@1:10
          Logischer Name: scsi4
          Fähigkeiten: emulated scsi-host
          Konfiguration: driver=usb-storage
        *-disk
             Beschreibung: SCSI Disk
             Produkt: USB Flash Disk
             Hersteller: General
             Physische ID: 0.0.0
             Bus-Informationen: scsi@4:0.0.0
             Logischer Name: /dev/sda
             Version: 1.00
             Größe: 7651MiB (8022MB)
             Fähigkeiten: removable
             Konfiguration: ansiversion=2 logicalsectorsize=512 sectorsize=512
           *-medium
                Physische ID: 0
                Logischer Name: /dev/sda
                Größe: 7651MiB (8022MB)
                Fähigkeiten: partitioned partitioned:dos
                Konfiguration: signature=000ec20b
              *-volume
                   Beschreibung: Windows NTFS Laufwerk
                   Physische ID: 1
                   Logischer Name: /dev/sda1
                   Logischer Name: /media/bl/Jimal
                   Version: 3.1
                   Seriennummer: 17fc-8de8
                   Größe: 7648MiB
                   Kapazität: 7650MiB
                   Fähigkeiten: primary ntfs initialized
                   Konfiguration: clustersize=4096 created=2019-08-07 13:53:44 filesystem=ntfs label=Jimal mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
  *-power UNGEFORDERT
       Beschreibung: NULL
       Produkt: High Efficiency
       Hersteller: NULL
       Physische ID: 1
       Version: NULL
       Seriennummer: NULL
       Kapazität: 32768mWh

```

---

### Post by bl75 on 2020-08-05
many thanks for the quick reply. If it is a problem with the firmware, an update from the manufacturer is probably required?

I assume that is the info that matters from the above mentioned command:

```
 *-usb:1
                   Beschreibung: Bluetooth-Schnittstelle
                   Produkt: Bluetooth Radio
                   Hersteller: Realtek
                   Physische ID: 9
                   Bus-Informationen: usb@1:9
                   Version: 2.00
                   Seriennummer: 00E04C239987
                   Fähigkeiten: bluetooth usb-1.10
                   Konfiguration: driver=btusb maxpower=500mA speed=12Mbit/s
```

---

### Post by chili555 on 2020-08-05
I don't believe the error suggests that there is something wrong with the firmware at all. I think the error indicates that the firmware is missing from your system altogether. Please check:

```
ls /lib/firmware/rtl_bt
```Do you see rtl8761a_config.bin in there? I sure don't.

Let's try a very experimental process to load it. First, remove the device. Next, do:

```
wget https://mpow.s3-us-west-1.amazonaws.com/mpow_MPBH456AB_driver+for+Linux.tgz
tar -xvzf mpow_MPBH456AB_driver+for+Linux.tgz
sudo cp 20200610_LINUX_BT_DRIVER/rtkbt-firmware/lib/firmware/rtlbt/rtl8761a_config  /lib/firmware/rtl_bt
sudo mv /lib/firmware/rtl_bt/rtl8761a_config  /lib/firmware/rtl_bt/rtl8761a_config.bin

```
Reinsert the device and let us see:

```
dmesg | grep -i blue 
```

---

### Post by bl75 on 2020-08-06
Many thanks - I did as described.

Indeed, the rtl8761a_config.bin was missing. After executing the above mentioned steps, the device is still not working. Also a re-boot does not change that. Something seems still wrong:

```
bl@eO-116-PC1-Ubuntu:~$ dmesg | grep -i blue
[   12.633007] Bluetooth: hci0: RTL: HCI_OP_READ_LOCAL_VERSION failed (-110)
```


Repeating the first command described above, the firmware seems now installed:

```
bl@eO-116-PC1-Ubuntu:~$ ls /lib/firmware/rtl_bt
rtl8192ee_fw.bin               rtl8723d_fw.bin      rtl8822b_config.bin
rtl8192eu_fw.bin               rtl8761a_config.bin  rtl8822b_fw.bin
rtl8723a_fw.bin                rtl8761a_fw.bin      rtl8822cs_config.bin
rtl8723b_fw.bin                rtl8812ae_fw.bin     rtl8822cs_fw.bin
rtl8723bs_config-OBDA8723.bin  rtl8821a_fw.bin      rtl8822cu_config.bin
rtl8723bs_fw.bin               rtl8821c_config.bin  rtl8822cu_fw.bin
rtl8723d_config.bin            rtl8821c_fw.bin

```

The adapter is still not found, so I can't start blueman-manager:

```
bl@eO-116-PC1-Ubuntu:~$ sudo blueman-manager
[sudo] Passwort für bl: 
blueman-manager version 2.1.2 starting
blueman-manager 09.16.26 ERROR    Manager:118 on_dbus_name_appeared: Default adapter not found, trying first available.
blueman-manager 09.16.26 ERROR    Manager:122 on_dbus_name_appeared: No adapter(s) found, exiting

```

The device works with Win 10, though (installed in dual-boot), so it is definitely not a hardware problem.

---

### Post by chili555 on 2020-08-06
Did the device come with a Windows driver CD? Are there .bin (firmware) files on it?

---

### Post by bl75 on 2020-08-06
Many thanks - there was no CD, but possibility to download the driver: [http://images.agptek.us/Download/Hommie-BT-501%20Driver.zip](http://images.agptek.us/Download/Hommie-BT-501%20Driver.zip)

In the resulting file, there are various folders. But at BT_Driver and Win 10x64, there is no bin-file, just dll, sys, exe, cat, and inf. The main folder has only one bin-file (layout.bin), many ini, and some cab, hdr.

I just noticed that the above mentioned commands created a folder 20200610_Linux_BT_Driver on my harddisk. There is a readme with suggestions of commands that were not yet executed:

```
===============
  TITLE
===============

The document describes how to support Realtek Bluetooth UART and USB driver in Linux system.

===============
  REQUIREMENT
===============

The supported kernel version is 2.6.32 - 5.3.

=============================
  QUICKLY INSTALL AUTOMATICALLY
=============================

  $ sudo make install INTERFACE=all
or
  $ sudo make install INTERFACE=usb
or
  $ sudo make install INTERFACE=uart

===============
  FOR UART I/F
===============

-The default serial protocol of Realtek Bluetooth chip is Three-wire (H5) protocol.

-The default initial baud rate is 115200.

-Installation

  To support Three-wire (H5) protocol, you need to install Realtek hci_uart driver
  and rtk_hciattach tool.

  1. Make sure your UART setting is correct.
     host tx  - controller rx
     host rx  - controller tx
     host rts - controller cts
     host cts - ground
   ( host cts - controller rts ) // for RTL8822C and RTL8761B
          NC  - controller rts

  2. Install Bluetooth kernel driver and rtk_hciattach tool
   $ cd uart
   $ sudo make install

  3. Copy the right FW file and config file to the correct path.
   $ sudo mkdir -p /lib/firmware/rtlbt/
   $ sudo cp rtkbt-firmware/lib/firmware/rtlbt/rtl8xxxx_fw /lib/firmware/rtlbt/
   $ sudo cp rtkbt-firmware/lib/firmware/rtlbt/rtl8xxxx_config /lib/firmware/rtlbt/

   NOTE: PLEASE REFER THE FORWARD SECTION OF FILENAME LIST TO CORRESPONDE THE FW FILENAME AND THE CONFIG FILENAME WITH THE CHIP.

  3. Initialize Realtek Bluetooth chip by rtk_hciattach
   $ sudo rtk_hciattach -n -s 115200 ttyUSB0 rtk_h5

    Tips: ttyUSB0 is serial port name in your system, you should change it
    according to hardware such as ttyS0.

-Uninstallation
   $ sudo make uninstall

- If you want to change the parameter such as baud rate and pcm settings, you
should modify rtl8xxx_config file.

===============
  FOR USB I/F
===============

-Installation

  1. Build and install USB driver, change to the driver direcotory
   $ cd usb
   $ sudo make install

  2. Copy the right FW file and config file to the correct path.
   $ sudo cp rtkbt-firmware/lib/firmware/rtl8xxxxx_fw /lib/firmware/
   $ sudo cp rtkbt-firmware/lib/firmware/rtl8xxxxx_config /lib/firmware/

   NOTE: PLEASE REFER THE FORWARD SECTION OF FILENAME LIST TO CORRESPONDE THE FW FILENAME AND THE CONFIG FILENAME WITH THE CHIP.
       
  3. Insert Realtek Bluetooth dongle
    Check LMP subversion by the following command
    $ hciconfig -a

    Now RTK chip can be recognized by the system and bluetooth function can be used.

-Uninstallation
   $ sudo make uninstall

===============    
  FILENAME LIST
===============
    
Chip        I/F         FW/Config Path        FW Filename        Config Filename
        for
        BT driver
------------------------------------------------------------------------------------------------
RTL8761AUV    USB        /lib/firmware/        rtl8761au_fw        rtl8761a_config

RTL8761AW     USB        /lib/firmware/        rtl8761aw_fw        rtl8761aw_config
(RTL8761AW 
+RTL8192EU)    

RTL8761AUV      USB        /lib/firmware/        rtl8761au8192ee_fw    rtl8761a_config
+RTL8192EE
 
RTL8761AUV    USB        /lib/firmware/        rtl8761au8192ee_fw    rtl8761a_config
+RTL8812AE
 
RTL8761ATV    UART        /lib/firmware/rtlbt/    rtl8761a_fw        rtl8761a_config

RTL8761ATV
+RTL8192EE    UART        /lib/firmware/rtlbt/    rtl8761at8192ee_fw    rtl8761a_config
 
-----------------------------------------------------------------------------------------------

RTL8761BUV    USB        /lib/firmware/        rtl8761bu_fw        rtl8761bu_config

RTL8761BTV    UART        /lib/firmware/rtlbt/    rtl8761b_fw        rtl8761b_config

-----------------------------------------------------------------------------------------------

RTL8725AU    USB        /lib/firmware/        rtl8725au_fw        rtl8725au_config

RTL8725AS    UART        /lib/firmware/rtlbt/    rtl8725as_fw        rtl8725as_config

-----------------------------------------------------------------------------------------------

RTL8723BU    USB        /lib/firmware/        rtl8723b_fw        rtl8723b_config
RTL8723BE

RTL8723BS    UART        /lib/firmware/rtlbt/    rtl8723b_fw        rtl8723b_config

-----------------------------------------------------------------------------------------------

RTL8821AU    USB        /lib/firmware/        rtl8821a_fw        rtl8821a_config
RTL8821AE

RTL8821AS    UART        /lib/firmware/rtlbt/    rtl8821a_fw        rtl8821a_config

-----------------------------------------------------------------------------------------------

RTL8822BU    USB        /lib/firmware/        rtl8822bu_fw        rtl8822bu_config
RTL8822BE

RTL8822BS    UART        /lib/firmware/rtlbt/    rtl8822b_fw        rtl8822b_config

-----------------------------------------------------------------------------------------------

RTL8723DU    USB        /lib/firmware/        rtl8723du_fw        rtl8723du_config
RTL8723DE

RTL8723DS    UART        /lib/firmware/rtlbt/    rtl8723d_fw        rtl8723d_config

-----------------------------------------------------------------------------------------------

RTL8821CU    USB        /lib/firmware/        rtl8821cu_fw        rtl8821cu_config
RTL8821CE

RTL8821CS    UART        /lib/firmware/rtlbt/    rtl8821c_fw        rtl8821c_config

-----------------------------------------------------------------------------------------------

RTL8822CU    USB        /lib/firmware/        rtl8822cu_fw        rtl8822cu_config
RTL8822CE

RTL8822CS    UART        /lib/firmware/rtlbt/    rtl8822cs_fw        rtl8822cs_config

-----------------------------------------------------------------------------------------------
```

---

### Post by chili555 on 2020-08-06
> There is a readme with suggestions of commands that were not yet executed:Yes, indeed. I had hoped that the firmware alone might fix it but evidently not.

By all means, let's try. Assuming that the folder that was created is in your /home/bl directory, please do:

```
cd ~/20200610_LINUX_BT_DRIVER
sudo make install INTERFACE=usb
```Reboot.

---

### Post by bl75 on 2020-08-06
The driver was installed sucessfully.

```
                         bl@eO-116-PC1-Ubuntu:~/20200610_LINUX_BT_DRIVER$ sudo make install INTERFACE=usb
 mkdir -p /lib/modules/5.4.0-42-generic/kernel/drivers/bluetooth
 Start Realtek Bluetooth USB driver installation
 mkdir -p /lib/firmware
 Copy rtkbt-firmware/lib/firmware/rtl*_fw to /lib/firmware
 cp -a rtkbt-firmware/lib/firmware/rtl*_fw /lib/firmware
 Copy rtkbt-firmware/lib/firmware/rtl*_config /lib/firmware
 cp -a rtkbt-firmware/lib/firmware/rtl*_config /lib/firmware
 make -C usb install
 make[1]: Verzeichnis „/home/bl/20200610_LINUX_BT_DRIVER/usb“ wird betreten
 rmmod btusb
 rmmod: ERROR: Module btusb is not currently loaded
 make[1]: [Makefile:7: install] Fehler 1 (ignoriert)
 mv /lib/modules/5.4.0-42-generic/kernel/drivers/bluetooth/btusb.ko /lib/modules/5.4.0-42-generic/kernel/drivers/bluetooth/btusb_bak
 mv: Aufruf von stat für '/lib/modules/5.4.0-42-generic/kernel/drivers/bluetooth/btusb.ko' nicht möglich: Datei oder Verzeichnis nicht gefunden
 make[1]: [Makefile:8: install] Fehler 1 (ignoriert)
 rmmod rtk_btusb
 rmmod: ERROR: Module rtk_btusb is not currently loaded
 make[1]: [Makefile:9: install] Fehler 1 (ignoriert)
 make -C ./bluetooth_usb_driver
 make[2]: Verzeichnis „/home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver“ wird betreten
 make -C /lib/modules/5.4.0-42-generic/build M=/home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver modules
 make[3]: Verzeichnis „/usr/src/linux-headers-5.4.0-42-generic“ wird betreten
   CC [M]  /home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver/rtk_coex.o
   CC [M]  /home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver/rtk_misc.o
   CC [M]  /home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver/rtk_bt.o
   LD [M]  /home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver/rtk_btusb.o
   Building modules, stage 2.
   MODPOST 1 modules
   CC [M]  /home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver/rtk_btusb.mod.o
   LD [M]  /home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver/rtk_btusb.ko
 make[3]: Verzeichnis „/usr/src/linux-headers-5.4.0-42-generic“ wird verlassen
 make[2]: Verzeichnis „/home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver“ wird verlassen
 cp -f ./bluetooth_usb_driver/rtk_btusb.ko /lib/modules/5.4.0-42-generic/kernel/drivers/bluetooth/rtk_btusb.ko
 depmod -a 5.4.0-42-generic
 make -C ./bluetooth_usb_driver clean
 make[2]: Verzeichnis „/home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver“ wird betreten
 rm -rf *.o *.mod.c *.mod.o *.ko *.symvers *.order *.a
 make[2]: Verzeichnis „/home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver“ wird verlassen
 echo "install rtk_btusb success!"
 install rtk_btusb success!
 make[1]: Verzeichnis „/home/bl/20200610_LINUX_BT_DRIVER/usb“ wird verlassen
 bl@eO-116-PC1-Ubuntu:~/20200610_LINUX_BT_DRIVER$ 
 
 
  
```

However, the adapter is still not found :(

bl@eO-116-PC1-Ubuntu:~$ dmesg | grep -i blue

does not produce any message.

However, the Bluetooth service now seems correctly loaded:

```
bl@eO-116-PC1-Ubuntu:~$ sudo systemctl status bluetooth
[sudo] Passwort für bl: 
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor pre>
     Active: active (running) since Thu 2020-08-06 16:16:05 CEST; 4min 32s ago
       Docs: man:bluetoothd(8)
   Main PID: 1344 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 18881)
     Memory: 2.3M
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;1344 /usr/lib/bluetooth/bluetoothd

Aug 06 16:16:05 eO-116-PC1-Ubuntu systemd[1]: Starting Bluetooth service...
Aug 06 16:16:05 eO-116-PC1-Ubuntu bluetoothd[1344]: Bluetooth daemon 5.53
Aug 06 16:16:05 eO-116-PC1-Ubuntu systemd[1]: Started Bluetooth service.
Aug 06 16:16:05 eO-116-PC1-Ubuntu bluetoothd[1344]: Starting SDP server
Aug 06 16:16:05 eO-116-PC1-Ubuntu bluetoothd[1344]
```

But still no chance to start blueman:

```
bl@eO-116-PC1-Ubuntu:~$ sudo blueman-manager
blueman-manager version 2.1.2 starting
blueman-manager 16.21.40 ERROR    Manager:118 on_dbus_name_appeared: Default adapter not found, trying first available.
blueman-manager 16.21.40 ERROR    Manager:122 on_dbus_name_appeared: No adapter(s) found, exiting

```

As well, bluetoothctl does not help:

```
bluetoothctl
Agent registered
[bluetooth]# agent on
Agent is already registered
[bluetooth]# discoverable on
No default controller available
[bluetooth]# pairable on
No default controller available
[bluetooth]# 

```

Any ideas?

---

### Post by bl75 on 2020-08-06
I just see there was an error during the install:

stat für '/lib/modules/5.4.0-42-generic/kernel/drivers/bluetooth/btusb.ko

the file or directory was not found

and

rmmod: ERROR: Module rtk_btusb is not currently loaded

---

### Post by chili555 on 2020-08-06
> **bl75 said:**
> I just see there was an error during the install:

stat für '/lib/modules/5.4.0-42-generic/kernel/drivers/bluetooth/btusb.ko

the file or directory was not found

and

rmmod: ERROR: Module rtk_btusb is not currently loadedNot really. It was simply trying to remove conflicting modules, also known as drivers. None were loaded so none were unloaded.

What does this tell us?

```
lsusb
sudo modprobe rtk_btusb && dmesg | grep rtk

```

---

### Post by bl75 on 2020-08-06
OK thanks. Now:

```
bl@eO-116-PC1-Ubuntu:~$ lsusb
Bus 002 Device 002: ID 1058:2622 Western Digital Technologies, Inc. Elements SE 2622
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:8771 Realtek Semiconductor Corp. Bluetooth Radio
Bus 001 Device 002: ID 03f0:1a4a HP, Inc HP Wireless Slim Keyboard - Skylab EU
Bus 001 Device 004: ID 1224:2a25 Jieli Technology USB PHY 2.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bl@eO-116-PC1-Ubuntu:~$ sudo modprobe rtk_btusb && dmesg | grep rtk
[sudo] Passwort für bl: 
modprobe: ERROR: could not insert 'rtk_btusb': Operation not permitted

```

---

### Post by chili555 on 2020-08-06
> modprobe: ERROR: could not insert 'rtk_btusb': Operation not permittedStrange. It modprobes for me.

Is it already loaded?```
lsmod | grep bt
```I am quickly running low on useful ideas.

Is secure boot enabled or disabled in the BIOS/EFI? Try disabled.

---

### Post by bl75 on 2020-08-07
Secure boot was the problem.

Without disabling secure boot, lsmod | grep bt would just yield nothing. But now things work:

```
bl@eO-116-PC1-Ubuntu:~$ lsmod | grep bt
rtk_btusb              61440  0
bluetooth             581632  54 bnep,rtk_btusb,rfcomm
bl@eO-116-PC1-Ubuntu:~$ 


```

For those who might face a similar problem, here's how you disable secure boot:[COLOR=#ff6600]

$ sudo apt install mokutil[/COLOR][COLOR=#ff6600]
$ sudo mokutil –disable-validation

[/COLOR]You may not need the first command as it might already be installed on your system if secure boot is enabled. Reviewing the features of secure boot, which I installed without much inquiry when offered during install of Ubuntu 20, I do not think it is helpful. Ubuntu is imitating a Windows feature which I consider rather problematic and useless as Linux systems are far less affected by Viruses and other typical Windows issues. The main drawback of Linux is limited hardware compatibility, so why make things more complicated.

When rebooting after this command, I was prompted in a blue screen to enter selected characters of the password that I set during Ubuntu install, and could then disable secure boot. From now on, the Bluetooth adapter is found and works properly.

Many thanks for the support!


[INDENT][COLOR=#ff6600]
[/COLOR]

[/INDENT]

---

### Post by chili555 on 2020-08-07
> Ubuntu is imitating a Windows feature which I consider rather problematic and uselessIt isn't really Ubuntu's issue. I believe that Secure Boot is a feature (or a defect) in the BIOS/EFI of all modern computers. When you download Ubuntu and install it, it is already signed so that it installs without issue. It is only when you compile and install kernel modules from other sources that Secure Boot steps in to save you from yourself! 

I think it is a bit helpful to prevent some malware and spyware from being installed by users who are unaware of the methods to avoid  malware, etc.

```
depmod -a [COLOR="#FF0000"]5.4.0-42[/COLOR]-generic
```Please note that the driver is installed for your currently running kernel version *only.* Eventually, Update Manager will offer to install a newer kernel version, 5.4.0-43, for example. You will know this first, because you will be asked to reboot and, second, because, after the reboot, your bluetooth will no longer work! In that case, simple remove the device and do:

```
cd ~/20200610_LINUX_BT_DRIVER
sudo make install INTERFACE=usb

```Reinsert the device and you should be all set.

Thank you for posting the exact steps. I'm sure that the searchers will appreciate it.

I'm glad it's working. Have fun!

---

### Post by apetrelli on 2020-08-11
I managed to make it work in a different way, although probably it won't work with secure boot.
I added 5.8.0 kernel with this guide:
[https://www.how2shout.com/linux/install-linux-5-8-kernel-on-ubuntu-20-04-lts/](https://www.how2shout.com/linux/install-linux-5-8-kernel-on-ubuntu-20-04-lts/)
Then downloaded the package from MPOW:
[https://mpow.s3-us-west-1.amazonaws.com/mpow_MPBH456AB_driver+for+Linux.tgz](https://mpow.s3-us-west-1.amazonaws.com/mpow_MPBH456AB_driver+for+Linux.tgz)
Unpacked, copied and renamed the rtl8761b_fw and rtl8761b_config files inside /lib/firmware/rtl_bt, adding the ".bin" extension. Notice that these are the "b" version, supported in kernel 5.8.0 and used in BT 501. See the patch here:
[https://patchwork.kernel.org/patch/11483367/](https://patchwork.kernel.org/patch/11483367/)

And after a reboot it works! Hopefully Realtek publishes officially the firmware with the 5.8.0, although currently they did not answer the call from kernel developers. Hope for the best, but anyway this method works.

---

### Post by hong2 on 2021-04-21
Hi,

I've encountered similar problem with this particular adapter. 

Currently I've copied, and renamed the[COLOR=#000000] rtl8761a_config file following instructions in this thread, and also [/COLOR]rtk_btusb is loaded properly on my system. However, bluetooth is not working properly on my end.

The output of dmesg | tail :
```
dmesg | tail                                     
[ 2370.151683] usb 1-1: Manufacturer: Realtek
[ 2370.151685] usb 1-1: SerialNumber: A09F10C04B1A
[ 2370.153785] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 0
[ 2370.153788] rtk_btusb: btusb_probe can_wakeup 1, may wakeup 0
[ 2370.153789] rtk_btusb: patch_add
[ 2370.153791] rtk_btusb: auto suspend is disabled
[ 2370.153793] rtk_btusb: pid = 0x2550
[ 2370.153795] rtk_btusb: get_patch_entry =NULL, can not find device pid in patch_table
[ 2370.153805] rtk_btusb: probe of 1-1:1.0 failed with error -1
[ 2370.154081] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 1

```

Output of sudo modprobe rtk_btusb && dmesg | grep rtk:
```
sudo modprobe rtk_btusb && dmesg | grep rtk            
[  221.030926] rtk_btusb: Realtek Bluetooth USB driver ver 3.1.897f3bb.20201202-173003
[  221.030926] rtk_btcoex: rtk_btcoex_init: version: 1.2
[  221.030926] rtk_btcoex: create workqueue
[  221.030952] rtk_btcoex: alloc buffers 1792, 2432 for ev and l2
[  221.030965] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 0
[  221.030965] rtk_btusb: btusb_probe can_wakeup 1, may wakeup 0
[  221.030965] rtk_btusb: patch_add
[  221.030966] rtk_btusb: auto suspend is disabled
[  221.030966] rtk_btusb: pid = 0x2550
[  221.030966] rtk_btusb: get_patch_entry =NULL, can not find device pid in patch_table
[  221.030968] rtk_btusb: probe of 1-1:1.0 failed with error -1
[  221.030971] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 1
[  221.030981] usbcore: registered new interface driver rtk_btusb
[  289.057396] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 0
[  289.057399] rtk_btusb: btusb_probe can_wakeup 1, may wakeup 0
[  289.057400] rtk_btusb: patch_add
[  289.057402] rtk_btusb: auto suspend is disabled
[  289.057403] rtk_btusb: pid = 0x2550
[  289.057405] rtk_btusb: get_patch_entry =NULL, can not find device pid in patch_table
[  289.057415] rtk_btusb: probe of 1-1:1.0 failed with error -1
[  289.057726] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 1
[  748.193232] rtk_btusb: rtk_btusb: btusb_exit
[  748.193233] usbcore: deregistering interface driver rtk_btusb
[  748.193256] rtk_btcoex: rtk_btcoex_exit: destroy workqueue
[ 1121.977548] rtk_btusb: Realtek Bluetooth USB driver ver 3.1.897f3bb.20201202-173003
[ 1121.977549] rtk_btcoex: rtk_btcoex_init: version: 1.2
[ 1121.977550] rtk_btcoex: create workqueue
[ 1121.977579] rtk_btcoex: alloc buffers 1792, 2432 for ev and l2
[ 1121.977595] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 0
[ 1121.977595] rtk_btusb: btusb_probe can_wakeup 1, may wakeup 0
[ 1121.977595] rtk_btusb: patch_add
[ 1121.977596] rtk_btusb: auto suspend is disabled
[ 1121.977596] rtk_btusb: pid = 0x2550
[ 1121.977596] rtk_btusb: get_patch_entry =NULL, can not find device pid in patch_table
[ 1121.977599] rtk_btusb: probe of 1-1:1.0 failed with error -1
[ 1121.977602] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 1
[ 1121.977624] usbcore: registered new interface driver rtk_btusb
[ 1280.653855] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 0
[ 1280.653858] rtk_btusb: btusb_probe can_wakeup 1, may wakeup 0
[ 1280.653859] rtk_btusb: patch_add
[ 1280.653861] rtk_btusb: auto suspend is disabled
[ 1280.653862] rtk_btusb: pid = 0x2550
[ 1280.653864] rtk_btusb: get_patch_entry =NULL, can not find device pid in patch_table
[ 1280.653874] rtk_btusb: probe of 1-1:1.0 failed with error -1
[ 1280.654158] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 1
[ 1965.395564] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 0
[ 1965.395567] rtk_btusb: btusb_probe can_wakeup 1, may wakeup 0
[ 1965.395569] rtk_btusb: patch_add
[ 1965.395570] rtk_btusb: auto suspend is disabled
[ 1965.395572] rtk_btusb: pid = 0x2550
[ 1965.395574] rtk_btusb: get_patch_entry =NULL, can not find device pid in patch_table
[ 1965.395583] rtk_btusb: probe of 1-1:1.0 failed with error -1
[ 1965.395877] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 1



```

I have tried all the steps mentioned in this post, and I am running out of ideas. Any help is highly appreciated.

---

### Post by esperie on 2021-08-06
I have the same MPOW adaptor (BH519A) with Realtek chipset RTL8761BU. My  kernel version is 5.11 on ubuntu 20.04. Exhausted every solution I can  find on the internet and only the one posted by @meavydev ([link]("https://ubuntuforums.org/showthread.php?t=2460970&p=14052213#post14052213")) worked.

To be precise, 
1. Go to the downloaded linux driver folder (20201202_LINUX_BT_DRIVER/usb/bluetooth_usb_driver)
2. edit rtk_misc.c.
3. Look for the code block: static patch_info fw_patch_table[]
4. Add the line: {0x2550, 0x8761, "mp_rtl8761b_fw", "rtl8761bu_fw", "rtl8761b_config", NULL, 0},    /* RTL8761BU only */
5. Save and close the file.
6. Run sudo make install INTERFACE=usb from 20201202_LINUX_BT_DRIVER/usb.
7. hciconfig will now show the device and bluetooth works as intended after that.

---

### Post by bl75 on 2021-11-02
I tried to use the adapter on a different computer, with a fresh install of Ubuntu 20.04.03. LTS 64 bit

I copied the driver files and executed the steps as described above. However, this time I cannot execute the make install command. It claims "make" and "sudo" that commands are not found.

Have commands changed, do I need to unblock make or install, or is there something wrong with my saved driver file?

[INDENT]```
bl@bl-LDS-HP-EliteDesk-800-G2-SFF:~$ sudo cp 20200610_LINUX_BT_DRIVER/rtkbt-firmware/lib/firmware/rtlbt/rtl8761a_config  /lib/firmware/rtl_bt
[sudo] Passwort für bl: 
bl@bl-LDS-HP-EliteDesk-800-G2-SFF:~$ sudo mv /lib/firmware/rtl_bt/rtl8761a_config  /lib/firmware/rtl_bt/rtl8761a_config.bin
bl@bl-LDS-HP-EliteDesk-800-G2-SFF:~$ dmesg | grep -i blue
[    1.612061] usb 1-1: Product: Bluetooth Radio
[   13.620639] Bluetooth: Core ver 2.22
[   13.620654] Bluetooth: HCI device and connection manager initialized
[   13.620657] Bluetooth: HCI socket layer initialized
[   13.620659] Bluetooth: L2CAP socket layer initialized
[   13.620661] Bluetooth: SCO socket layer initialized
[   14.341190] Bluetooth: hci0: RTL: examining hci_ver=0a hci_rev=000b lmp_ver=0a lmp_subver=8761
[   14.342172] Bluetooth: hci0: RTL: rom_version status=0 version=1
[   14.342175] Bluetooth: hci0: RTL: loading rtl_bt/rtl8761b_fw.bin
[   14.659461] bluetooth hci0: Direct firmware load for rtl_bt/rtl8761b_fw.bin failed with error -2
[   14.659467] Bluetooth: hci0: RTL: firmware file rtl_bt/rtl8761b_fw.bin not found
[   27.235443] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.235448] Bluetooth: BNEP filters: protocol multicast
[   27.235452] Bluetooth: BNEP socket layer initialized
[  490.544292] usb 1-4: Product: Bluetooth Radio
[  490.548110] Bluetooth: hci0: RTL: examining hci_ver=0a hci_rev=000b lmp_ver=0a lmp_subver=8761
[  490.550810] Bluetooth: hci0: RTL: rom_version status=0 version=1
[  490.550815] Bluetooth: hci0: RTL: loading rtl_bt/rtl8761b_fw.bin
[  490.550832] bluetooth hci0: Direct firmware load for rtl_bt/rtl8761b_fw.bin failed with error -2
[  490.550836] Bluetooth: hci0: RTL: firmware file rtl_bt/rtl8761b_fw.bin not found
[  748.252269] usb 1-4: Product: Bluetooth Radio
[  748.256161] Bluetooth: hci0: RTL: examining hci_ver=0a hci_rev=000b lmp_ver=0a lmp_subver=8761
[  748.257160] Bluetooth: hci0: RTL: rom_version status=0 version=1
[  748.257166] Bluetooth: hci0: RTL: loading rtl_bt/rtl8761b_fw.bin
[  748.257198] bluetooth hci0: Direct firmware load for rtl_bt/rtl8761b_fw.bin failed with error -2
[  748.257203] Bluetooth: hci0: RTL: firmware file rtl_bt/rtl8761b_fw.bin not found
[ 1379.496098] usb 1-4: Product: Bluetooth Radio
[ 1379.499877] Bluetooth: hci0: RTL: examining hci_ver=0a hci_rev=000b lmp_ver=0a lmp_subver=8761
[ 1379.500678] Bluetooth: hci0: RTL: rom_version status=0 version=1
[ 1379.500685] Bluetooth: hci0: RTL: loading rtl_bt/rtl8761b_fw.bin
[ 1379.500723] bluetooth hci0: Direct firmware load for rtl_bt/rtl8761b_fw.bin failed with error -2
[ 1379.500729] Bluetooth: hci0: RTL: firmware file rtl_bt/rtl8761b_fw.bin not found

bl@bl-LDS-HP-EliteDesk-800-G2-SFF:~$ ls /lib/firmware/rtl_bt
rtl8192ee_fw.bin               rtl8761a_config.bin  rtl8822cs_config.bin
rtl8192eu_fw.bin               rtl8761a_fw.bin      rtl8822cs_fw.bin
rtl8723a_fw.bin                rtl8812ae_fw.bin     rtl8822cu_config.bin
rtl8723b_fw.bin                rtl8821a_fw.bin      rtl8822cu_fw.bin
rtl8723bs_config-OBDA8723.bin  rtl8821c_config.bin  rtl8852au_config.bin
rtl8723bs_fw.bin               rtl8821c_fw.bin      rtl8852au_fw.bin
rtl8723d_config.bin            rtl8822b_config.bin
rtl8723d_fw.bin                rtl8822b_fw.bin

bl@bl-LDS-HP-EliteDesk-800-G2-SFF:~$ sudo blueman-manager
blueman-manager version 2.1.2 starting
blueman-manager 17.11.20 ERROR    Manager:118 on_dbus_name_appeared: Default adapter not found, trying first available.
blueman-manager 17.11.20 ERROR    Manager:122 on_dbus_name_appeared: No adapter(s) found, exiting

bl@bl-LDS-HP-EliteDesk-800-G2-SFF:~$ cd ~/20200610_LINUX_BT_DRIVER
bl@bl-LDS-HP-EliteDesk-800-G2-SFF:~/20200610_LINUX_BT_DRIVER$ sudo make install INTERFACE=usb
sudo: make: Befehl nicht gefunden
bl@bl-LDS-HP-EliteDesk-800-G2-SFF:~/20200610_LINUX_BT_DRIVER$ 

```
[/INDENT]

---

### Post by chili555 on 2021-11-02
Rather than tack on to the end of a solved thread that is geeting a bit old, I suggest that you start your own new question. 

Have you installed the package build-essential?

---

### Post by bl75 on 2021-11-04
Many thanks for the reply - I thought adding to the same thread would be better than opening a new one.

Indeed, the build-essentials package was not installed. I did not expect that I had to install it myself; with the earlier installation of Ubuntu 20 it came automatically.

Now, with build essentials, I could execute the make-command and it was successful (see at bottom).

However, the bluetooth stick is still not found:

```
bl@bl-LDS-HP-EliteDesk-800-G2-SFF:~$ ls /lib/firmware/rtl_bt
rtl8192ee_fw.bin               rtl8761a_config.bin  rtl8822cs_config.bin
rtl8192eu_fw.bin               rtl8761a_fw.bin      rtl8822cs_fw.bin
rtl8723a_fw.bin                rtl8812ae_fw.bin     rtl8822cu_config.bin
rtl8723b_fw.bin                rtl8821a_fw.bin      rtl8822cu_fw.bin
rtl8723bs_config-OBDA8723.bin  rtl8821c_config.bin  rtl8852au_config.bin
rtl8723bs_fw.bin               rtl8821c_fw.bin      rtl8852au_fw.bin
rtl8723d_config.bin            rtl8822b_config.bin
rtl8723d_fw.bin                rtl8822b_fw.bin
bl@bl-LDS-HP-EliteDesk-800-G2-SFF:~$ dmesg | grep -i blue
[   80.483351] usb 1-4: Product: Bluetooth Radio
[   80.646346] Bluetooth: Core ver 2.22
[   80.646394] Bluetooth: HCI device and connection manager initialized
[   80.646398] Bluetooth: HCI socket layer initialized
[   80.646401] Bluetooth: L2CAP socket layer initialized
[   80.646405] Bluetooth: SCO socket layer initialized
[   97.965549] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   97.965552] Bluetooth: BNEP filters: protocol multicast
[   97.965555] Bluetooth: BNEP socket layer initialized
bl@bl-LDS-HP-EliteDesk-800-G2-SFF:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 0bda:8771 Realtek Semiconductor Corp. Bluetooth Radio
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bl@bl-LDS-HP-EliteDesk-800-G2-SFF:~$ sudo modprobe rtk_btusb && dmesg | grep rtk
[sudo] Passwort für bl: 
modprobe: ERROR: could not insert 'rtk_btusb': Operation not permitted
bl@bl-LDS-HP-EliteDesk-800-G2-SFF:~$ 

```

I am not sure whether the stick was inserted when I installed the firmware with these commands:

```

sudo cp 20200610_LINUX_BT_DRIVER/rtkbt-firmware/lib/firmware/rtlbt/rtl8761a_config  /lib/firmware/rtl_bt
sudo mv /lib/firmware/rtl_bt/rtl8761a_config  /lib/firmware/rtl_bt/rtl8761a_config.bin

```

There was some confusion when I started to re-install the drivers etc. In any case, I repeated the commands above with no adapter inserted before executing the make command for the driver.

Secure boot should, to the best of my knowledge, be disabled...


Here's the result of make:

```
   	 	 	 	   bl@bl-LDS-HP-EliteDesk-800-G2-SFF:~/20200610_LINUX_BT_DRIVER$ sudo make install INTERFACE=usb
 mkdir -p /lib/modules/5.11.0-38-generic/kernel/drivers/bluetooth
 Start Realtek Bluetooth USB driver installation
 mkdir -p /lib/firmware
 Copy rtkbt-firmware/lib/firmware/rtl*_fw to /lib/firmware
 cp -a rtkbt-firmware/lib/firmware/rtl*_fw /lib/firmware
 Copy rtkbt-firmware/lib/firmware/rtl*_config /lib/firmware
 cp -a rtkbt-firmware/lib/firmware/rtl*_config /lib/firmware
 make -C usb install
 make[1]: Verzeichnis „/home/bl/20200610_LINUX_BT_DRIVER/usb“ wird betreten
 rmmod btusb
 mv /lib/modules/5.11.0-38-generic/kernel/drivers/bluetooth/btusb.ko /lib/modules/5.11.0-38-generic/kernel/drivers/bluetooth/btusb_bak
 rmmod rtk_btusb
 rmmod: ERROR: Module rtk_btusb is not currently loaded
 make[1]: [Makefile:9: install] Fehler 1 (ignoriert)
 make -C ./bluetooth_usb_driver
 make[2]: Verzeichnis „/home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver“ wird betreten
 make -C /lib/modules/5.11.0-38-generic/build M=/home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver modules
 make[3]: Verzeichnis „/usr/src/linux-headers-5.11.0-38-generic“ wird betreten
   CC [M]  /home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver/rtk_coex.o
   CC [M]  /home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver/rtk_misc.o
   CC [M]  /home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver/rtk_bt.o
   LD [M]  /home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver/rtk_btusb.o
   MODPOST /home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver/Module.symvers
   CC [M]  /home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver/rtk_btusb.mod.o
   LD [M]  /home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver/rtk_btusb.ko
 make[3]: Verzeichnis „/usr/src/linux-headers-5.11.0-38-generic“ wird verlassen
 make[2]: Verzeichnis „/home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver“ wird verlassen
 cp -f ./bluetooth_usb_driver/rtk_btusb.ko /lib/modules/5.11.0-38-generic/kernel/drivers/bluetooth/rtk_btusb.ko
 depmod -a 5.11.0-38-generic
 make -C ./bluetooth_usb_driver clean
 make[2]: Verzeichnis „/home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver“ wird betreten
 rm -rf *.o *.mod.c *.mod.o *.ko *.symvers *.order *.a
 make[2]: Verzeichnis „/home/bl/20200610_LINUX_BT_DRIVER/usb/bluetooth_usb_driver“ wird verlassen
 echo "install rtk_btusb success!"
 install rtk_btusb success!
 make[1]: Verzeichnis „/home/bl/20200610_LINUX_BT_DRIVER/usb“ wird verlassen
 bl@bl-LDS-HP-EliteDesk-800-G2-SFF:~/20200610_LINUX_BT_DRIVER$ 
 
 
  
```

---

### Post by bl75 on 2021-11-04
Here's the result of the secure boot disabling command. Not sure whether it was executed correctly...:

```
bl@bl-LDS-HP-EliteDesk-800-G2-SFF:~$ sudo mokutil –disable-validation
Usage:
  mokutil OPTIONS [ARGS...]

Options:
  --help                Show help
  --list-enrolled            List the enrolled keys
  --list-new                List the keys to be enrolled
  --list-delete                List the keys to be deleted
  --import <der file...>        Import keys
  --delete <der file...>        Delete specific keys
  --revoke-import            Revoke the import request
  --revoke-delete            Revoke the delete request
  --export                Export keys to files
  --password                Set MOK password
  --clear-password            Clear MOK password
  --disable-validation            Disable signature validation
  --enable-validation            Enable signature validation
  --sb-state                Show SecureBoot State
  --test-key <der file>            Test if the key is enrolled or not
  --reset                Reset MOK list
  --generate-hash[=password]        Generate the password hash
  --ignore-db                Ignore DB for validation
  --use-db                Use DB for validation
  --import-hash <hash>            Import a hash into MOK or MOKX
  --delete-hash <hash>            Delete a hash in MOK or MOKX
  --set-verbosity <true/false>        Set the verbosity bit for shim
  --pk                    List the keys in PK
  --kek                    List the keys in KEK
  --db                    List the keys in db
  --dbx                    List the keys in dbx
  --timeout <-1,0..0x7fff>        Set the timeout for MOK prompt

Supplimentary Options:
  --hash-file <hash file>        Use the specific password hash
  --root-pw                Use the root password
  --simple-hash                Use the old password hash method
  --mokx                Manipulate the MOK blacklist

```

---

### Post by bl75 on 2021-11-10
I found out that it was indeed a secure boot problem.

This time, however, secure boot had to be deactivated in the BIOS. Finally I found out how to do that. Problem solved!

---

