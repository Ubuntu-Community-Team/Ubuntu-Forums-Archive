---
title: "Detect USB Stick?"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by persofi on 2009-01-20
I'm running Ubuntu 8.10 with all recent updates. I just bought a new USB stick, plugged it in and it worked perfectly, I even copied some files on it. 
Than I plugged it in under Windows, it didnt seem to recognize it. Now when I want to use it under Ubuntu, it does not recognize it any more???

Here is my lsusb:
Bus 005 Device 004: ID 058f:1234 Alcor Micro Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 057c:3d00 AVM GmbH Fritz!Box
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 046d:c025 Logitech, Inc. MX500 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


And dmesg:
[  219.624064] usb 5-1: new high speed USB device using ehci_hcd and address 4
[  219.870726] usb 5-1: configuration #1 chosen from 1 choice
[  220.582836] usbcore: registered new interface driver libusual
[  220.653130] Initializing USB Mass Storage driver...
[  220.656766] scsi2 : SCSI emulation for USB Mass Storage devices
[  220.657570] usbcore: registered new interface driver usb-storage
[  220.657578] USB Mass Storage support registered.
[  220.660104] usb-storage: device found at 4
[  220.660115] usb-storage: waiting for device to settle before scanning
[  225.656428] usb-storage: device scan complete
[  225.657177] scsi 2:0:0:0: Direct-Access     Generic  USB Flash Disk   7.76 PQ: 0 ANSI: 2
[  225.661492] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  225.662175] sd 2:0:0:0: Attached scsi generic sg2 type 0

---

### Post by icanfly0307 on 2009-01-20
Hi there, I ran into this same problem when I used Ubuntu. Plug in your flash drive. Type [FONT="Courier New"]*sudo /sbin/fdisk -l*[/FONT] in a terminal and post the output. That way, I can help you access your flash drive. 

Good Luck! :)

PS: That's a lowercase "l", not a one (1)...

---

### Post by persofi on 2009-01-20
Hi,
My system language isnt english, but I hope you can get the necessary information nevertheless:

Platte /dev/sda: 80.0 GByte, 80026361856 Byte
255 Köpfe, 63 Sektoren/Spuren, 9729 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xba7ea4f6

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1         152     1220908+  82  Linux Swap / Solaris
/dev/sda2   *         510        5087    36772785    7  HPFS/NTFS
/dev/sda3            5088        6607    12209400   83  Linux
/dev/sda4            6608        9729    25077465   83  Linux


My Ubuntu is split into a Boot and a Home Partition + Swap. I also have a Windows system on another partition.

---

### Post by timcredible on 2009-01-20
did you unplug it without unmounting it first?  if so, that causes corruption of the filesystem and you might want to re-format it as fat16 or fat32.

---

### Post by icanfly0307 on 2009-01-20
I'm guessing that your usb drive is /dev/sdb1. Try this:

1. Open up a terminal.

2. Type *sudo mkdir /media/flash*

3. Type *mount /dev/sdb1 /media/flash*
4. Browse to /media/flash and you should see the contents of you flash drive in that directory. Good Luck! :D

---

### Post by persofi on 2009-01-20
I opened gparted and realized, that none of sda1,2,3,4 can be my USB stick.

What now? It is possible that I removed it in Windows without unmounting it. But how can I reformat it, if it doesnt get recognized?

---

### Post by pdtpatrick on 2009-01-20
plug in the flash drive then run sudo fdisk -l 

within there you should see something like /dev/sdb1 and if so then you take note of the name.. then using fdisk you can format the drive. 

after which, you can then mount the flash drive.

---

### Post by persofi on 2009-01-20
sudo fdisk -l only gives me:
/dev/sda1               1         152     1220908+  82  Linux Swap / Solaris
/dev/sda2   *         510        5087    36772785    7  HPFS/NTFS
/dev/sda3            5088        6607    12209400   83  Linux
/dev/sda4            6608        9729    25077465   83  Linux

None of which is my flash drive. 
Does this mean it doesnt work anymore?

---

### Post by pdtpatrick on 2009-01-20
restart and see if your computer auto detects it .. also repost your /var/log/messages and then fdisk -l after the reboot.

---

### Post by icanfly0307 on 2009-01-20
Okay. If you remove the Flash Drive without unmounting it in Windows, it won't work in Ubuntu. Plug in the flash drive in Windows, unmount it cleanly, and then try to mount it in Ubuntu. It's happened to me before.

---

### Post by persofi on 2009-01-21
Damn! Windows kinda recognizes it (It shows up as E-Drive, and I can safely remove it), but I cant access files or reformat it???

Thats the product btw (8 GB): [http://tinyurl.com/2g5zkj](http://tinyurl.com/2g5zkj)

Ubuntu doesnt autodetect it after reboot:

fdisk-l after reboot:

Platte /dev/sda: 80.0 GByte, 80026361856 Byte
255 Köpfe, 63 Sektoren/Spuren, 9729 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xba7ea4f6

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1         152     1220908+  82  Linux Swap / Solaris
/dev/sda2   *         510        5087    36772785    7  HPFS/NTFS
/dev/sda3            5088        6607    12209400   83  Linux
/dev/sda4            6608        9729    25077465   83  Linux

> 
My /var/log/messages:
Jan 21 18:44:52 toby-laptop syslogd 1.5.0#2ubuntu6: restart.
Jan 21 18:44:52 toby-laptop kernel: Inspecting /boot/System.map-2.6.27-9-generic
Jan 21 18:44:52 toby-laptop kernel: Cannot find map file.
Jan 21 18:44:52 toby-laptop kernel: Loaded 51045 symbols from 96 modules.
Jan 21 18:44:52 toby-laptop kernel:     0.000000 Initializing cgroup subsys cpuset
Jan 21 18:44:52 toby-laptop kernel:     0.000000 Initializing cgroup subsys cpu
Jan 21 18:44:52 toby-laptop kernel:     0.000000 Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 BIOS-provided physical RAM map:
Jan 21 18:44:52 toby-laptop kernel:     0.000000  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jan 21 18:44:52 toby-laptop kernel:     0.000000  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jan 21 18:44:52 toby-laptop kernel:     0.000000  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jan 21 18:44:52 toby-laptop kernel:     0.000000  BIOS-e820: 0000000000100000 - 000000001f680000 (usable)
Jan 21 18:44:52 toby-laptop kernel:     0.000000  BIOS-e820: 000000001f680000 - 000000001f700000 (ACPI NVS)
Jan 21 18:44:52 toby-laptop kernel:     0.000000  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
Jan 21 18:44:52 toby-laptop kernel:     0.000000  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jan 21 18:44:52 toby-laptop kernel:     0.000000  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jan 21 18:44:52 toby-laptop kernel:     0.000000  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Jan 21 18:44:52 toby-laptop kernel:     0.000000  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Jan 21 18:44:52 toby-laptop kernel:     0.000000  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Jan 21 18:44:52 toby-laptop kernel:     0.000000  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jan 21 18:44:52 toby-laptop kernel:     0.000000  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 last_pfn = 0x1f680 max_arch_pfn = 0x100000
Jan 21 18:44:52 toby-laptop kernel:     0.000000 RAMDISK: 1ee9e000 - 1f66f837
Jan 21 18:44:52 toby-laptop kernel:     0.000000 DMI present.
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: RSDP 000F6290, 0014 (r0 ACRSYS)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: RSDT 1F685EBD, 0050 (r1 ACRSYS ACRPRDCT  6040000  LTP        0)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: FACP 1F68CC76, 0074 (r1 Acer   Grape     6040000 LOHR       5A)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: DSDT 1F686EE3, 5D93 (r1 Acer   CALISTGA  6040000 INTL 20050228)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: FACS 1F68DFC0, 0040
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: APIC 1F68CCEA, 0068 (r1 Acer   Grape     6040000 LOHR       5A)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: HPET 1F68CD52, 0038 (r1 Acer   Grape     6040000 LOHR       5A)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: MCFG 1F68CD8A, 003C (r1 Acer   Grape     6040000 LOHR       5A)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: SLIC 1F68CDC6, 0176 (r1 ACRSYS ACRPRDCT  6040000 LOHR        0)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: DBGP 1F68CF3C, 0034 (r1 Acer   Grape     6040000 LOHR        0)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: APIC 1F68CF70, 0068 (r1 PTLTD  ^I APIC    6040000  LTP        0)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: BOOT 1F68CFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: SSDT 1F68647F, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050228)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: SSDT 1F6863D9, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050228)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: SSDT 1F685F0D, 04CC (r1  PmRef    CpuPm     3000 INTL 20050228)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: BIOS bug: multiple APIC/MADT found, using 0
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: If "acpi_apic_instance=2" works better, notify [EMAIL="emaillinux-acpi@vger.kernel.org"]emaillinux-acpi@vger.kernel.org[/EMAIL]/email
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: DMI detected: Acer
Jan 21 18:44:52 toby-laptop kernel:     0.000000 0MB HIGHMEM available.
Jan 21 18:44:52 toby-laptop kernel:     0.000000 502MB LOWMEM available.
Jan 21 18:44:52 toby-laptop kernel:     0.000000   mapped low ram: 0 - 1f680000
Jan 21 18:44:52 toby-laptop kernel:     0.000000   low ram: 00000000 - 1f680000
Jan 21 18:44:52 toby-laptop kernel:     0.000000   bootmap 00002000 - 00005ed0
Jan 21 18:44:52 toby-laptop kernel:     0.000000 (9 early reservations) == bootmem 0000000000 - 001f680000
Jan 21 18:44:52 toby-laptop kernel:     0.000000   #0 0000000000 - 0000001000   BIOS data page == 0000000000 - 0000001000
Jan 21 18:44:52 toby-laptop kernel:     0.000000   #1 0000001000 - 0000002000    EX TRAMPOLINE == 0000001000 - 0000002000
Jan 21 18:44:52 toby-laptop kernel:     0.000000   #2 0000006000 - 0000007000       TRAMPOLINE == 0000006000 - 0000007000
Jan 21 18:44:52 toby-laptop kernel:     0.000000   #3 0000100000 - 00005c0a20    TEXT DATA BSS == 0000100000 - 00005c0a20
Jan 21 18:44:52 toby-laptop kernel:     0.000000   #4 001ee9e000 - 001f66f837          RAMDISK == 001ee9e000 - 001f66f837
Jan 21 18:44:52 toby-laptop kernel:     0.000000   #5 00005c1000 - 00005c4000    INIT_PG_TABLE == 00005c1000 - 00005c4000
Jan 21 18:44:52 toby-laptop kernel:     0.000000   #6 000009f800 - 0000100000    BIOS reserved == 000009f800 - 0000100000
Jan 21 18:44:52 toby-laptop kernel:     0.000000   #7 0000007000 - 0000009000          PGTABLE == 0000007000 - 0000009000
Jan 21 18:44:52 toby-laptop kernel:     0.000000   #8 0000002000 - 0000006000          BOOTMAP == 0000002000 - 0000006000
Jan 21 18:44:52 toby-laptop kernel:     0.000000 found SMP MP-table at c00f6340 000f6340
Jan 21 18:44:52 toby-laptop kernel:     0.000000 Zone PFN ranges:
Jan 21 18:44:52 toby-laptop kernel:     0.000000   DMA      0x00000000 - 0x00001000
Jan 21 18:44:52 toby-laptop kernel:     0.000000   Normal   0x00001000 - 0x0001f680
Jan 21 18:44:52 toby-laptop kernel:     0.000000   HighMem  0x0001f680 - 0x0001f680
Jan 21 18:44:52 toby-laptop kernel:     0.000000 Movable zone start PFN for each node
Jan 21 18:44:52 toby-laptop kernel:     0.000000 early_node_map2 active PFN ranges
Jan 21 18:44:52 toby-laptop kernel:     0.000000     0: 0x00000000 - 0x0000009f
Jan 21 18:44:52 toby-laptop kernel:     0.000000     0: 0x00000100 - 0x0001f680
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: PM-Timer IO Port: 0x1008
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: LAPIC (acpi_id0x00 lapic_id0x00 enabled)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: LAPIC (acpi_id0x01 lapic_id0x01 enabled)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: LAPIC_NMI (acpi_id0x00 high edge lint0x1)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: LAPIC_NMI (acpi_id0x01 high edge lint0x1)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: IOAPIC (id0x01 address0xfec00000 gsi_base0)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 IOAPIC0: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan 21 18:44:52 toby-laptop kernel:     0.000000 ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jan 21 18:44:52 toby-laptop kernel:     0.000000 Using ACPI (MADT) for SMP configuration information
Jan 21 18:44:52 toby-laptop kernel:     0.000000 SMP: Allowing 2 CPUs, 0 hotplug CPUs
Jan 21 18:44:52 toby-laptop kernel:     0.000000 PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 21 18:44:52 toby-laptop kernel:     0.000000 PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 21 18:44:52 toby-laptop kernel:     0.000000 PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 21 18:44:52 toby-laptop kernel:     0.000000 Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 PERCPU: Allocating 41628 bytes of per cpu data
Jan 21 18:44:52 toby-laptop kernel:     0.000000 Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127412
Jan 21 18:44:52 toby-laptop kernel:     0.000000 Kernel command line: root=UUID=ec053eea-d1ca-4d91-a0ea-0ede95959ba2 ro quiet splash 
Jan 21 18:44:52 toby-laptop kernel:     0.000000 Enabling fast FPU save and restore... done.
Jan 21 18:44:52 toby-laptop kernel:     0.000000 Enabling unmasked SIMD FPU exception support... done.
Jan 21 18:44:52 toby-laptop kernel:     0.000000 Initializing CPU#0
Jan 21 18:44:52 toby-laptop kernel:     0.000000 PID hash table entries: 2048 (order: 11, 8192 bytes)
Jan 21 18:44:52 toby-laptop kernel:     0.000000 TSC: PIT calibration confirmed by PMTIMER.
Jan 21 18:44:52 toby-laptop kernel:     0.000000 TSC: using PIT calibration value
Jan 21 18:44:52 toby-laptop kernel:     0.000000 Detected 1662.485 MHz processor.
Jan 21 18:44:52 toby-laptop kernel:     0.004000 Console: colour VGA+ 80x25
Jan 21 18:44:52 toby-laptop kernel:     0.004000 console tty0 enabled
Jan 21 18:44:52 toby-laptop kernel:     0.004000 Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan 21 18:44:52 toby-laptop kernel:     0.004000 Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan 21 18:44:52 toby-laptop kernel:     0.004000 Memory: 495940k/514560k available (2572k kernel code, 17956k reserved, 1160k data, 424k init, 0k highmem)
Jan 21 18:44:52 toby-laptop kernel:     0.004000 virtual kernel memory layout:
Jan 21 18:44:52 toby-laptop kernel:     0.004000     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Jan 21 18:44:52 toby-laptop kernel:     0.004000     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Jan 21 18:44:52 toby-laptop kernel:     0.004000     vmalloc : 0xe0000000 - 0xff3fe000   ( 499 MB)
Jan 21 18:44:52 toby-laptop kernel:     0.004000     lowmem  : 0xc0000000 - 0xdf680000   ( 502 MB)
Jan 21 18:44:52 toby-laptop kernel:     0.004000       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
Jan 21 18:44:52 toby-laptop kernel:     0.004000       .data : 0xc038335a - 0xc04a5680   (1160 kB)
Jan 21 18:44:52 toby-laptop kernel:     0.004000       .text : 0xc0100000 - 0xc038335a   (2572 kB)
Jan 21 18:44:52 toby-laptop kernel:     0.004000 Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan 21 18:44:52 toby-laptop kernel:     0.004000 SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jan 21 18:44:52 toby-laptop kernel:     0.004000 Calibrating delay loop (skipped), value calculated using timer frequency.. 3324.97 BogoMIPS (lpj=6649940)
Jan 21 18:44:52 toby-laptop kernel:     0.004000 Security Framework initialized
Jan 21 18:44:52 toby-laptop kernel:     0.004000 SELinux:  Disabled at boot.
Jan 21 18:44:52 toby-laptop kernel:     0.004000 AppArmor: AppArmor initialized
Jan 21 18:44:52 toby-laptop kernel:     0.004000 Mount-cache hash table entries: 512
Jan 21 18:44:52 toby-laptop kernel:     0.004000 Initializing cgroup subsys ns
Jan 21 18:44:52 toby-laptop kernel:     0.004000 Initializing cgroup subsys cpuacct
Jan 21 18:44:52 toby-laptop kernel:     0.004000 Initializing cgroup subsys memory
Jan 21 18:44:52 toby-laptop kernel:     0.004000 CPU: L1 I cache: 32K, L1 D cache: 32K
Jan 21 18:44:52 toby-laptop kernel:     0.004000 CPU: L2 cache: 2048K
Jan 21 18:44:52 toby-laptop kernel:     0.004000 CPU: Physical Processor ID: 0
Jan 21 18:44:52 toby-laptop kernel:     0.004000 CPU: Processor Core ID: 0
Jan 21 18:44:52 toby-laptop kernel:     0.004000 using mwait in idle threads.
Jan 21 18:44:52 toby-laptop kernel:     0.004000 Checking 'hlt' instruction... OK.
Jan 21 18:44:52 toby-laptop kernel:     0.020007 ACPI: Core revision 20080609
Jan 21 18:44:52 toby-laptop kernel:     0.023096 ACPI: Checking initramfs for custom DSDT
Jan 21 18:44:52 toby-laptop kernel:     0.716311 ENABLING IO-APIC IRQs
Jan 21 18:44:52 toby-laptop kernel:     0.716537 ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 21 18:44:52 toby-laptop kernel:     0.757647 CPU0: Intel Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08
Jan 21 18:44:52 toby-laptop kernel:     0.760031 Booting processor 1/1 ip 6000
Jan 21 18:44:52 toby-laptop kernel:     0.004000 Initializing CPU#1
Jan 21 18:44:52 toby-laptop kernel:     0.004000 Calibrating delay using timer specific routine.. 3325.12 BogoMIPS (lpj=6650256)
Jan 21 18:44:52 toby-laptop kernel:     0.004000 CPU: L1 I cache: 32K, L1 D cache: 32K
Jan 21 18:44:52 toby-laptop kernel:     0.004000 CPU: L2 cache: 2048K
Jan 21 18:44:52 toby-laptop kernel:     0.004000 CPU: Physical Processor ID: 0
Jan 21 18:44:52 toby-laptop kernel:     0.004000 CPU: Processor Core ID: 1
Jan 21 18:44:52 toby-laptop kernel:     0.844822 CPU1: Intel Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08
Jan 21 18:44:52 toby-laptop kernel:     0.844858 checking TSC synchronization CPU#0 - CPU#1: passed.
Jan 21 18:44:52 toby-laptop kernel:     0.848061 Brought up 2 CPUs
Jan 21 18:44:52 toby-laptop kernel:     0.848068 Total of 2 processors activated (6650.09 BogoMIPS).
Jan 21 18:44:52 toby-laptop kernel:     0.848281 net_namespace: 840 bytes
Jan 21 18:44:52 toby-laptop kernel:     0.848281 Booting paravirtualized kernel on bare hardware
Jan 21 18:44:52 toby-laptop kernel:     0.848539 Time: 18:44:29  Date: 01/21/09
Jan 21 18:44:52 toby-laptop kernel:     0.848590 NET: Registered protocol family 16
Jan 21 18:44:52 toby-laptop kernel:     0.848627 EISA bus registered
Jan 21 18:44:52 toby-laptop kernel:     0.848627 ACPI: bus type pci registered
Jan 21 18:44:52 toby-laptop kernel:     0.848627 PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jan 21 18:44:52 toby-laptop kernel:     0.848627 PCI: MCFG area at e0000000 reserved in E820
Jan 21 18:44:52 toby-laptop kernel:     0.848627 PCI: Using MMCONFIG for extended config space
Jan 21 18:44:52 toby-laptop kernel:     0.848627 PCI: Using configuration type 1 for base access
Jan 21 18:44:52 toby-laptop kernel:     0.863565 ACPI: BIOS _OSI(Linux) query ignored via DMI
Jan 21 18:44:52 toby-laptop kernel:     0.864984 ACPI: Interpreter enabled
Jan 21 18:44:52 toby-laptop kernel:     0.864990 ACPI: (supports S0 S3 S4 S5)
Jan 21 18:44:52 toby-laptop kernel:     0.865021 ACPI: Using IOAPIC for interrupt routing
Jan 21 18:44:52 toby-laptop kernel:     0.872314 ACPI: EC: non-query interrupt received, switching to interrupt mode
Jan 21 18:44:52 toby-laptop kernel:     0.932693 ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
Jan 21 18:44:52 toby-laptop kernel:     0.932693 ACPI: EC: driver started in interrupt mode
Jan 21 18:44:52 toby-laptop kernel:     0.932693 ACPI: PCI Root Bridge PCI0 (0000:00)
Jan 21 18:44:52 toby-laptop kernel:     0.936339 pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jan 21 18:44:52 toby-laptop kernel:     0.936348 pci 0000:00:1b.0: PME# disabled
Jan 21 18:44:52 toby-laptop kernel:     0.936437 pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jan 21 18:44:52 toby-laptop kernel:     0.936446 pci 0000:00:1c.0: PME# disabled
Jan 21 18:44:52 toby-laptop kernel:     0.936535 pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jan 21 18:44:52 toby-laptop kernel:     0.936543 pci 0000:00:1c.1: PME# disabled
Jan 21 18:44:52 toby-laptop kernel:     0.936632 pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jan 21 18:44:52 toby-laptop kernel:     0.936640 pci 0000:00:1c.2: PME# disabled
Jan 21 18:44:52 toby-laptop kernel:     0.936729 pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jan 21 18:44:52 toby-laptop kernel:     0.936737 pci 0000:00:1c.3: PME# disabled
Jan 21 18:44:52 toby-laptop kernel:     0.937200 pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jan 21 18:44:52 toby-laptop kernel:     0.937209 pci 0000:00:1d.7: PME# disabled
Jan 21 18:44:52 toby-laptop kernel:     0.937402 pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Jan 21 18:44:52 toby-laptop kernel:     0.937410 pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
Jan 21 18:44:52 toby-laptop kernel:     0.938269 pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
Jan 21 18:44:52 toby-laptop kernel:     0.938286 pci 0000:05:00.0: PME# disabled
Jan 21 18:44:52 toby-laptop kernel:     0.938495 pci 0000:06:01.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 21 18:44:52 toby-laptop kernel:     0.938504 pci 0000:06:01.0: PME# disabled
Jan 21 18:44:52 toby-laptop kernel:     0.938598 pci 0000:06:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 21 18:44:52 toby-laptop kernel:     0.938608 pci 0000:06:04.0: PME# disabled
Jan 21 18:44:52 toby-laptop kernel:     0.938664 pci 0000:00:1e.0: transparent bridge
Jan 21 18:44:52 toby-laptop kernel:     0.948259 ACPI: PCI Interrupt Link LNKA (IRQs 1 5 *6 10 12 14 15)
Jan 21 18:44:52 toby-laptop kernel:     0.948514 ACPI: PCI Interrupt Link LNKB (IRQs 1 5 6 *11 12 14 15)
Jan 21 18:44:52 toby-laptop kernel:     0.948766 ACPI: PCI Interrupt Link LNKC (IRQs 1 5 6 10 12 14 15) *11
Jan 21 18:44:52 toby-laptop kernel:     0.949027 ACPI: PCI Interrupt Link LNKD (IRQs 1 5 6 11 12 14 15) *10
Jan 21 18:44:52 toby-laptop kernel:     0.949281 ACPI: PCI Interrupt Link LNKE (IRQs 1 5 6 10 12 14 15) *0, disabled.
Jan 21 18:44:52 toby-laptop kernel:     0.949535 ACPI: PCI Interrupt Link LNKF (IRQs 1 5 6 11 12 14 15) *10
Jan 21 18:44:52 toby-laptop kernel:     0.949787 ACPI: PCI Interrupt Link LNKG (IRQs 1 5 6 *10 12 14 15)
Jan 21 18:44:52 toby-laptop kernel:     0.950040 ACPI: PCI Interrupt Link LNKH (IRQs 1 *5 6 11 12 14 15)
Jan 21 18:44:52 toby-laptop kernel:     0.950190 Linux Plug and Play Support v0.97 (c) Adam Belay
Jan 21 18:44:52 toby-laptop kernel:     0.950190 pnp: PnP ACPI init
Jan 21 18:44:52 toby-laptop kernel:     0.950190 ACPI: bus type pnp registered
Jan 21 18:44:52 toby-laptop kernel:     0.976457 pnp 00:06: io resource (0x2e-0x2f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 18:44:52 toby-laptop kernel:     0.976457 pnp 00:06: io resource (0x4e-0x4f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 18:44:52 toby-laptop kernel:     0.976457 pnp 00:06: io resource (0x61-0x61) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 18:44:52 toby-laptop kernel:     0.976457 pnp 00:06: io resource (0x63-0x63) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 18:44:52 toby-laptop kernel:     0.976457 pnp 00:06: io resource (0x65-0x65) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 18:44:52 toby-laptop kernel:     0.976457 pnp 00:06: io resource (0x67-0x67) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 18:44:52 toby-laptop kernel:     0.976457 pnp 00:06: io resource (0x70-0x70) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 18:44:52 toby-laptop kernel:     0.976457 pnp 00:06: io resource (0x80-0x80) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 18:44:52 toby-laptop kernel:     0.976457 pnp 00:06: io resource (0x92-0x92) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 18:44:52 toby-laptop kernel:     0.976457 pnp 00:06: io resource (0xb2-0xb3) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 18:44:52 toby-laptop kernel:     0.976457 pnp 00:06: io resource (0x800-0x80f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 18:44:52 toby-laptop kernel:     0.976457 pnp: PnP ACPI: found 10 devices
Jan 21 18:44:52 toby-laptop kernel:     0.976457 ACPI: ACPI bus type pnp unregistered
Jan 21 18:44:52 toby-laptop kernel:     0.976457 PnPBIOS: Disabled by ACPI PNP
Jan 21 18:44:52 toby-laptop kernel:     0.976457 PCI: Using ACPI for IRQ routing
Jan 21 18:44:52 toby-laptop kernel:     0.976457 pci 0000:00:1c.0: BAR 7: can't allocate resource
Jan 21 18:44:52 toby-laptop kernel:     0.976457 pci 0000:00:1c.0: BAR 8: can't allocate resource
Jan 21 18:44:52 toby-laptop kernel:     0.984050 NET: Registered protocol family 8
Jan 21 18:44:52 toby-laptop kernel:     0.984055 NET: Registered protocol family 20
Jan 21 18:44:52 toby-laptop kernel:     0.984087 NetLabel: Initializing
Jan 21 18:44:52 toby-laptop kernel:     0.984087 NetLabel:  domain hash size = 128
Jan 21 18:44:52 toby-laptop kernel:     0.984087 NetLabel:  protocols = UNLABELED CIPSOv4
Jan 21 18:44:52 toby-laptop kernel:     0.984104 NetLabel:  unlabeled traffic allowed by default
Jan 21 18:44:52 toby-laptop kernel:     0.984116 hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jan 21 18:44:52 toby-laptop kernel:     0.984126 hpet0: 3 64-bit timers, 14318180 Hz
Jan 21 18:44:52 toby-laptop kernel:     0.986198 tracer: 772 pages allocated for 65536 entries of 48 bytes
Jan 21 18:44:52 toby-laptop kernel:     0.986204    actual entries 65620
Jan 21 18:44:52 toby-laptop kernel:     0.986346 AppArmor: AppArmor Filesystem Enabled
Jan 21 18:44:52 toby-laptop kernel:     0.986382 ACPI: RTC can wake from S4
Jan 21 18:44:52 toby-laptop kernel:     0.992046 system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
Jan 21 18:44:52 toby-laptop kernel:     0.992053 system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
Jan 21 18:44:52 toby-laptop kernel:     0.992060 system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
Jan 21 18:44:52 toby-laptop kernel:     0.992067 system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
Jan 21 18:44:52 toby-laptop kernel:     0.992073 system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
Jan 21 18:44:52 toby-laptop kernel:     0.992080 system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
Jan 21 18:44:52 toby-laptop kernel:     0.992097 system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
Jan 21 18:44:52 toby-laptop kernel:     0.992112 system 00:06: ioport range 0x1000-0x107f has been reserved
Jan 21 18:44:52 toby-laptop kernel:     0.992118 system 00:06: ioport range 0x1180-0x11bf has been reserved
Jan 21 18:44:52 toby-laptop kernel:     0.992124 system 00:06: ioport range 0x1640-0x164f has been reserved
Jan 21 18:44:52 toby-laptop kernel:     0.992131 system 00:06: ioport range 0xfe00-0xfefe has been reserved
Jan 21 18:44:52 toby-laptop kernel:     0.992137 system 00:06: ioport range 0xff2c-0xff2f has been reserved
Jan 21 18:44:52 toby-laptop kernel:     1.028010 pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Jan 21 18:44:52 toby-laptop kernel:     1.028016 pci 0000:00:1c.0:   IO window: disabled
Jan 21 18:44:52 toby-laptop kernel:     1.028025 pci 0000:00:1c.0:   MEM window: disabled
Jan 21 18:44:52 toby-laptop kernel:     1.028033 pci 0000:00:1c.0:   PREFETCH window: disabled
Jan 21 18:44:52 toby-laptop kernel:     1.028045 pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
Jan 21 18:44:52 toby-laptop kernel:     1.028050 pci 0000:00:1c.1:   IO window: disabled
Jan 21 18:44:52 toby-laptop kernel:     1.028059 pci 0000:00:1c.1:   MEM window: disabled
Jan 21 18:44:52 toby-laptop kernel:     1.028067 pci 0000:00:1c.1:   PREFETCH window: disabled
Jan 21 18:44:52 toby-laptop kernel:     1.028079 pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
Jan 21 18:44:52 toby-laptop kernel:     1.028084 pci 0000:00:1c.2:   IO window: disabled
Jan 21 18:44:52 toby-laptop kernel:     1.028093 pci 0000:00:1c.2:   MEM window: disabled
Jan 21 18:44:52 toby-laptop kernel:     1.028101 pci 0000:00:1c.2:   PREFETCH window: disabled
Jan 21 18:44:52 toby-laptop kernel:     1.028113 pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
Jan 21 18:44:52 toby-laptop kernel:     1.028118 pci 0000:00:1c.3:   IO window: disabled
Jan 21 18:44:52 toby-laptop kernel:     1.028128 pci 0000:00:1c.3:   MEM window: 0xd0100000-0xd01fffff
Jan 21 18:44:52 toby-laptop kernel:     1.028136 pci 0000:00:1c.3:   PREFETCH window: disabled
Jan 21 18:44:52 toby-laptop kernel:     1.028158 pci 0000:06:04.0: CardBus bridge, secondary bus 0000:07
Jan 21 18:44:52 toby-laptop kernel:     1.028163 pci 0000:06:04.0:   IO window: 0x002000-0x0020ff
Jan 21 18:44:52 toby-laptop kernel:     1.028173 pci 0000:06:04.0:   IO window: 0x002400-0x0024ff
Jan 21 18:44:52 toby-laptop kernel:     1.028182 pci 0000:06:04.0:   PREFETCH window: 0x30000000-0x33ffffff
Jan 21 18:44:52 toby-laptop kernel:     1.028192 pci 0000:06:04.0:   MEM window: 0x34000000-0x37ffffff
Jan 21 18:44:52 toby-laptop kernel:     1.028201 pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
Jan 21 18:44:52 toby-laptop kernel:     1.028208 pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
Jan 21 18:44:52 toby-laptop kernel:     1.028218 pci 0000:00:1e.0:   MEM window: 0xd0000000-0xd00fffff
Jan 21 18:44:52 toby-laptop kernel:     1.028227 pci 0000:00:1e.0:   PREFETCH window: 0x00000030000000-0x00000033ffffff
Jan 21 18:44:52 toby-laptop kernel:     1.028256 pci 0000:00:1c.0: PCI INT A - GSI 17 (level, low) - IRQ 17
Jan 21 18:44:52 toby-laptop kernel:     1.028284 pci 0000:00:1c.1: PCI INT B - GSI 16 (level, low) - IRQ 16
Jan 21 18:44:52 toby-laptop kernel:     1.028307 pci 0000:00:1c.2: PCI INT C - GSI 18 (level, low) - IRQ 18
Jan 21 18:44:52 toby-laptop kernel:     1.028331 pci 0000:00:1c.3: PCI INT D - GSI 19 (level, low) - IRQ 19
Jan 21 18:44:52 toby-laptop kernel:     1.028350 pci 0000:00:1e.0: enabling device (0004 - 0007)
Jan 21 18:44:52 toby-laptop kernel:     1.028375 pci 0000:06:04.0: PCI INT A - GSI 16 (level, low) - IRQ 16
Jan 21 18:44:52 toby-laptop kernel:     1.028386 bus: 00 index 0 io port: 0, ffff
Jan 21 18:44:52 toby-laptop kernel:     1.028391 bus: 00 index 1 mmio: 0, ffffffff
Jan 21 18:44:52 toby-laptop kernel:     1.028396 bus: 02 index 0 mmio: 0, fff
Jan 21 18:44:52 toby-laptop kernel:     1.028400 bus: 02 index 1 mmio: 0, fffff
Jan 21 18:44:52 toby-laptop kernel:     1.028405 bus: 02 index 2 mmio: 0, 0
Jan 21 18:44:52 toby-laptop kernel:     1.028409 bus: 02 index 3 mmio: 0, 0
Jan 21 18:44:52 toby-laptop kernel:     1.028413 bus: 03 index 0 mmio: 0, 0
Jan 21 18:44:52 toby-laptop kernel:     1.028417 bus: 03 index 1 mmio: 0, 0
Jan 21 18:44:52 toby-laptop kernel:     1.028421 bus: 03 index 2 mmio: 0, 0
Jan 21 18:44:52 toby-laptop kernel:     1.028425 bus: 03 index 3 mmio: 0, 0
Jan 21 18:44:52 toby-laptop kernel:     1.028429 bus: 04 index 0 mmio: 0, 0
Jan 21 18:44:52 toby-laptop kernel:     1.028434 bus: 04 index 1 mmio: 0, 0
Jan 21 18:44:52 toby-laptop kernel:     1.028438 bus: 04 index 2 mmio: 0, 0
Jan 21 18:44:52 toby-laptop kernel:     1.028442 bus: 04 index 3 mmio: 0, 0
Jan 21 18:44:52 toby-laptop kernel:     1.028446 bus: 05 index 0 mmio: 0, 0
Jan 21 18:44:52 toby-laptop kernel:     1.028450 bus: 05 index 1 mmio: d0100000, d01fffff
Jan 21 18:44:52 toby-laptop kernel:     1.028455 bus: 05 index 2 mmio: 0, 0
Jan 21 18:44:52 toby-laptop kernel:     1.028459 bus: 05 index 3 mmio: 0, 0
Jan 21 18:44:52 toby-laptop kernel:     1.028464 bus: 06 index 0 io port: 2000, 2fff
Jan 21 18:44:52 toby-laptop kernel:     1.028468 bus: 06 index 1 mmio: d0000000, d00fffff
Jan 21 18:44:52 toby-laptop kernel:     1.028473 bus: 06 index 2 mmio: 30000000, 33ffffff
Jan 21 18:44:52 toby-laptop kernel:     1.028478 bus: 06 index 3 io port: 0, ffff
Jan 21 18:44:52 toby-laptop kernel:     1.028483 bus: 06 index 4 mmio: 0, ffffffff
Jan 21 18:44:52 toby-laptop kernel:     1.028487 bus: 07 index 0 io port: 2000, 20ff
Jan 21 18:44:52 toby-laptop kernel:     1.028492 bus: 07 index 1 io port: 2400, 24ff
Jan 21 18:44:52 toby-laptop kernel:     1.028497 bus: 07 index 2 mmio: 30000000, 33ffffff
Jan 21 18:44:52 toby-laptop kernel:     1.028501 bus: 07 index 3 mmio: 34000000, 37ffffff
Jan 21 18:44:52 toby-laptop kernel:     1.028518 NET: Registered protocol family 2
Jan 21 18:44:52 toby-laptop kernel:     1.040097 IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Jan 21 18:44:52 toby-laptop kernel:     1.040495 TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Jan 21 18:44:52 toby-laptop kernel:     1.040596 TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Jan 21 18:44:52 toby-laptop kernel:     1.040695 TCP: Hash tables configured (established 16384 bind 16384)
Jan 21 18:44:52 toby-laptop kernel:     1.040701 TCP reno registered
Jan 21 18:44:52 toby-laptop kernel:     1.044114 NET: Registered protocol family 1
Jan 21 18:44:52 toby-laptop kernel:     1.044314 checking if image is initramfs... it is
Jan 21 18:44:52 toby-laptop kernel:     2.443829 Freeing initrd memory: 8006k freed
Jan 21 18:44:52 toby-laptop kernel:     2.444398 Simple Boot Flag at 0x36 set to 0x1
Jan 21 18:44:52 toby-laptop kernel:     2.446188 audit: initializing netlink socket (disabled)
Jan 21 18:44:52 toby-laptop kernel:     2.446227 type=2000 audit(1232563469.444:1): initialized
Jan 21 18:44:52 toby-laptop kernel:     2.458589 HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jan 21 18:44:52 toby-laptop kernel:     2.463672 VFS: Disk quotas dquot_6.5.1
Jan 21 18:44:52 toby-laptop kernel:     2.463865 Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan 21 18:44:52 toby-laptop kernel:     2.464076 msgmni has been set to 984
Jan 21 18:44:52 toby-laptop kernel:     2.464331 io scheduler noop registered
Jan 21 18:44:52 toby-laptop kernel:     2.464337 io scheduler anticipatory registered
Jan 21 18:44:52 toby-laptop kernel:     2.464343 io scheduler deadline registered
Jan 21 18:44:52 toby-laptop kernel:     2.464367 io scheduler cfq registered (default)
Jan 21 18:44:52 toby-laptop kernel:     2.464806 pcieport-driver 0000:00:1c.0: found MSI capability
Jan 21 18:44:52 toby-laptop kernel:     2.465355 pcieport-driver 0000:00:1c.1: found MSI capability
Jan 21 18:44:52 toby-laptop kernel:     2.465838 pcieport-driver 0000:00:1c.2: found MSI capability
Jan 21 18:44:52 toby-laptop kernel:     2.466322 pcieport-driver 0000:00:1c.3: found MSI capability
Jan 21 18:44:52 toby-laptop kernel:     2.467260 isapnp: Scanning for PnP cards...
Jan 21 18:44:52 toby-laptop kernel:     2.821598 isapnp: No Plug & Play device found
Jan 21 18:44:52 toby-laptop kernel:     2.895908 Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Jan 21 18:44:52 toby-laptop kernel:     2.900494 brd: module loaded
Jan 21 18:44:52 toby-laptop kernel:     2.900644 input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jan 21 18:44:52 toby-laptop kernel:     2.900950 PNP: PS/2 Controller PNP0303:PS2K,PNP0f13:MSS0 at 0x60,0x64 irq 1,12
Jan 21 18:44:52 toby-laptop kernel:     2.901455 i8042.c: Detected active multiplexing controller, rev 1.1.
Jan 21 18:44:52 toby-laptop kernel:     2.901548 serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 21 18:44:52 toby-laptop kernel:     2.901559 serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jan 21 18:44:52 toby-laptop kernel:     2.901566 serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jan 21 18:44:52 toby-laptop kernel:     2.901571 serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jan 21 18:44:52 toby-laptop kernel:     2.901577 serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jan 21 18:44:52 toby-laptop kernel:     2.904252 mice: PS/2 mouse device common for all mice
Jan 21 18:44:52 toby-laptop kernel:     2.904542 rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Jan 21 18:44:52 toby-laptop kernel:     2.904583 rtc0: alarms up to one month, y3k, hpet irqs
Jan 21 18:44:52 toby-laptop kernel:     2.904858 EISA: Probing bus 0 at eisa.0
Jan 21 18:44:52 toby-laptop kernel:     2.904870 Cannot allocate resource for EISA slot 1
Jan 21 18:44:52 toby-laptop kernel:     2.904876 Cannot allocate resource for EISA slot 2
Jan 21 18:44:52 toby-laptop kernel:     2.904902 Cannot allocate resource for EISA slot 5
Jan 21 18:44:52 toby-laptop kernel:     2.904923 EISA: Detected 0 cards.
Jan 21 18:44:52 toby-laptop kernel:     2.904928 cpuidle: using governor ladder
Jan 21 18:44:52 toby-laptop kernel:     2.904933 cpuidle: using governor menu
Jan 21 18:44:52 toby-laptop kernel:     2.905997 TCP cubic registered
Jan 21 18:44:52 toby-laptop kernel:     2.906042 Using IPI No-Shortcut mode
Jan 21 18:44:52 toby-laptop kernel:     2.906429 registered taskstats version 1
Jan 21 18:44:52 toby-laptop kernel:     2.906632   Magic number: 9:141:747
Jan 21 18:44:52 toby-laptop kernel:     2.906781 rtc_cmos 00:07: setting system clock to 2009-01-21 18:44:31 UTC (1232563471)
Jan 21 18:44:52 toby-laptop kernel:     2.906788 BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 21 18:44:52 toby-laptop kernel:     2.906793 EDD information not available.
Jan 21 18:44:52 toby-laptop kernel:     2.907096 input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jan 21 18:44:52 toby-laptop kernel:     2.907217 Freeing unused kernel memory: 424k freed
Jan 21 18:44:52 toby-laptop kernel:     2.907312 Write protecting the kernel text: 2576k
Jan 21 18:44:52 toby-laptop kernel:     2.907369 Write protecting the kernel read-only data: 936k
Jan 21 18:44:52 toby-laptop kernel:     3.203830 fuse init (API version 7.9)
Jan 21 18:44:52 toby-laptop kernel:     3.315386 ACPI: SSDT 1F686C25, 01F6 (r1  PmRef  Cpu0Ist     3000 INTL 20050228)
Jan 21 18:44:52 toby-laptop kernel:     3.316265 ACPI: SSDT 1F6866DE, 04C2 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
Jan 21 18:44:52 toby-laptop kernel:     3.328338 ACPI: CPU0 (power states: C1C1 C2C2 C3C3)
Jan 21 18:44:52 toby-laptop kernel:     3.328456 processor ACPI0007:00: registered as cooling_device0
Jan 21 18:44:52 toby-laptop kernel:     3.328465 ACPI: Processor CPU0 (supports 8 throttling states)
Jan 21 18:44:52 toby-laptop kernel:     3.329142 ACPI: SSDT 1F686E1B, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050228)
Jan 21 18:44:52 toby-laptop kernel:     3.329927 ACPI: SSDT 1F686BA0, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050228)
Jan 21 18:44:52 toby-laptop kernel:     3.331770 Marking TSC unstable due to TSC halts in idle
Jan 21 18:44:52 toby-laptop kernel:     3.340118 ACPI: CPU1 (power states: C1C1 C2C2 C3C3)
Jan 21 18:44:52 toby-laptop kernel:     3.340257 processor ACPI0007:01: registered as cooling_device1
Jan 21 18:44:52 toby-laptop kernel:     3.340266 ACPI: Processor CPU1 (supports 8 throttling states)
Jan 21 18:44:52 toby-laptop kernel:     3.348626 thermal LNXTHERM:01: registered as thermal_zone0
Jan 21 18:44:52 toby-laptop kernel:     3.358563 ACPI: Thermal Zone TZ00 (24 C)
Jan 21 18:44:52 toby-laptop kernel:     3.365782 thermal LNXTHERM:02: registered as thermal_zone1
Jan 21 18:44:52 toby-laptop kernel:     3.375302 ACPI: Thermal Zone TZ01 (24 C)
Jan 21 18:44:52 toby-laptop kernel:     4.063173 usbcore: registered new interface driver usbfs
Jan 21 18:44:52 toby-laptop kernel:     4.063216 usbcore: registered new interface driver hub
Jan 21 18:44:52 toby-laptop kernel:     4.063319 usbcore: registered new device driver usb
Jan 21 18:44:52 toby-laptop kernel:     4.070187 ehci_hcd 0000:00:1d.7: PCI INT A - GSI 23 (level, low) - IRQ 23
Jan 21 18:44:52 toby-laptop kernel:     4.070215 ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan 21 18:44:52 toby-laptop kernel:     4.070289 ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jan 21 18:44:52 toby-laptop kernel:     4.074206 ehci_hcd 0000:00:1d.7: debug port 1
Jan 21 18:44:52 toby-laptop kernel:     4.074240 ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0544000
Jan 21 18:44:52 toby-laptop kernel:     4.082313 USB Universal Host Controller Interface driver v3.0
Jan 21 18:44:52 toby-laptop kernel:     4.088038 ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan 21 18:44:52 toby-laptop kernel:     4.088313 usb usb1: configuration #1 chosen from 1 choice
Jan 21 18:44:52 toby-laptop kernel:     4.088371 hub 1-0:1.0: USB hub found
Jan 21 18:44:52 toby-laptop kernel:     4.088385 hub 1-0:1.0: 8 ports detected
Jan 21 18:44:52 toby-laptop kernel:     4.189366 No dock devices found.
Jan 21 18:44:52 toby-laptop kernel:     4.230403 SCSI subsystem initialized
Jan 21 18:44:52 toby-laptop kernel:     4.321103 uhci_hcd 0000:00:1d.0: PCI INT A - GSI 23 (level, low) - IRQ 23
Jan 21 18:44:52 toby-laptop kernel:     4.321126 uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan 21 18:44:52 toby-laptop kernel:     4.321177 uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jan 21 18:44:52 toby-laptop kernel:     4.321217 uhci_hcd 0000:00:1d.0: irq 23, io base 0x000050a0
Jan 21 18:44:52 toby-laptop kernel:     4.321400 usb usb2: configuration #1 chosen from 1 choice
Jan 21 18:44:52 toby-laptop kernel:     4.321456 hub 2-0:1.0: USB hub found
Jan 21 18:44:52 toby-laptop kernel:     4.321470 hub 2-0:1.0: 2 ports detected
Jan 21 18:44:52 toby-laptop kernel:     4.528473 uhci_hcd 0000:00:1d.1: PCI INT B - GSI 19 (level, low) - IRQ 19
Jan 21 18:44:52 toby-laptop kernel:     4.528498 uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan 21 18:44:52 toby-laptop kernel:     4.528552 uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jan 21 18:44:52 toby-laptop kernel:     4.528604 uhci_hcd 0000:00:1d.1: irq 19, io base 0x000050c0
Jan 21 18:44:52 toby-laptop kernel:     4.528811 usb usb3: configuration #1 chosen from 1 choice
Jan 21 18:44:52 toby-laptop kernel:     4.528866 hub 3-0:1.0: USB hub found
Jan 21 18:44:52 toby-laptop kernel:     4.528879 hub 3-0:1.0: 2 ports detected
Jan 21 18:44:52 toby-laptop kernel:     4.632470 uhci_hcd 0000:00:1d.2: PCI INT C - GSI 18 (level, low) - IRQ 18
Jan 21 18:44:52 toby-laptop kernel:     4.632495 uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan 21 18:44:52 toby-laptop kernel:     4.632545 uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jan 21 18:44:52 toby-laptop kernel:     4.632598 uhci_hcd 0000:00:1d.2: irq 18, io base 0x000050e0
Jan 21 18:44:52 toby-laptop kernel:     4.632775 usb usb4: configuration #1 chosen from 1 choice
Jan 21 18:44:52 toby-laptop kernel:     4.632829 hub 4-0:1.0: USB hub found
Jan 21 18:44:52 toby-laptop kernel:     4.632842 hub 4-0:1.0: 2 ports detected
Jan 21 18:44:52 toby-laptop kernel:     4.641040 usb 2-1: new low speed USB device using uhci_hcd and address 2
Jan 21 18:44:52 toby-laptop kernel:     4.816586 usb 2-1: configuration #1 chosen from 1 choice
Jan 21 18:44:52 toby-laptop kernel:     4.840626 uhci_hcd 0000:00:1d.3: PCI INT D - GSI 16 (level, low) - IRQ 16
Jan 21 18:44:52 toby-laptop kernel:     4.840650 uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jan 21 18:44:52 toby-laptop kernel:     4.840706 uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Jan 21 18:44:52 toby-laptop kernel:     4.840759 uhci_hcd 0000:00:1d.3: irq 16, io base 0x00005400
Jan 21 18:44:52 toby-laptop kernel:     4.840955 usb usb5: configuration #1 chosen from 1 choice
Jan 21 18:44:52 toby-laptop kernel:     4.841023 hub 5-0:1.0: USB hub found
Jan 21 18:44:52 toby-laptop kernel:     4.841038 hub 5-0:1.0: 2 ports detected
Jan 21 18:44:52 toby-laptop kernel:     4.944757 pata_acpi 0000:00:1f.1: PCI INT B - GSI 19 (level, low) - IRQ 19
Jan 21 18:44:52 toby-laptop kernel:     4.944833 pata_acpi 0000:00:1f.1: PCI INT B disabled
Jan 21 18:44:52 toby-laptop kernel:     4.952045 usb 4-1: new full speed USB device using uhci_hcd and address 2
Jan 21 18:44:52 toby-laptop kernel:     4.972133 ata_piix 0000:00:1f.1: PCI INT B - GSI 19 (level, low) - IRQ 19
Jan 21 18:44:52 toby-laptop kernel:     4.972408 scsi0 : ata_piix
Jan 21 18:44:52 toby-laptop kernel:     4.978477 scsi1 : ata_piix
Jan 21 18:44:52 toby-laptop kernel:     4.979893 ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x5090 irq 14
Jan 21 18:44:52 toby-laptop kernel:     4.979899 ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x5098 irq 15
Jan 21 18:44:52 toby-laptop kernel:     5.000033 Clocksource tsc unstable (delta = -142928040 ns)
Jan 21 18:44:52 toby-laptop kernel:     5.122968 usb 4-1: configuration #1 chosen from 1 choice
Jan 21 18:44:52 toby-laptop kernel:     5.125131 usbcore: registered new interface driver hiddev
Jan 21 18:44:52 toby-laptop kernel:     5.138868 input: B16_b_02 USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2
Jan 21 18:44:52 toby-laptop kernel:     5.148335 input,hidraw0: USB HID v1.10 Mouse B16_b_02 USB-PS/2 Optical Mouse on usb-0000:00:1d.0-1
Jan 21 18:44:52 toby-laptop kernel:     5.148381 usbcore: registered new interface driver usbhid
Jan 21 18:44:52 toby-laptop kernel:     5.148388 usbhid: v2.6:USB HID core driver
Jan 21 18:44:52 toby-laptop kernel:     5.152866 ata1.00: ATA-6: HTS541080G9AT00, MB4OA60A, max UDMA/100
Jan 21 18:44:52 toby-laptop kernel:     5.152873 ata1.00: 156301488 sectors, multi 16: LBA48 
Jan 21 18:44:52 toby-laptop kernel:     5.152915 ata1.01: ATAPI: HL-DT-ST DVDRAM GSA-4082N, HR02, max UDMA/33
Jan 21 18:44:52 toby-laptop kernel:     5.168829 ata1.00: configured for UDMA/100
Jan 21 18:44:52 toby-laptop kernel:     5.184619 ata1.01: configured for UDMA/33
Jan 21 18:44:52 toby-laptop kernel:     5.184938 scsi 0:0:0:0: Direct-Access     ATA      HTS541080G9AT00  MB4O PQ: 0 ANSI: 5
Jan 21 18:44:52 toby-laptop kernel:     5.188828 scsi 0:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-4082N HR02 PQ: 0 ANSI: 5
Jan 21 18:44:52 toby-laptop kernel:     5.189122 b44 0000:06:01.0: enabling device (0000 - 0002)
Jan 21 18:44:52 toby-laptop kernel:     5.189140 b44 0000:06:01.0: PCI INT A - GSI 21 (level, low) - IRQ 21
Jan 21 18:44:52 toby-laptop kernel:     5.249221 ssb: Sonics Silicon Backplane found on PCI device 0000:06:01.0
Jan 21 18:44:52 toby-laptop kernel:     5.249311 b44.c:v2.0
Jan 21 18:44:52 toby-laptop kernel:     5.268821 eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0f:b0:f0:5a:de
Jan 21 18:44:52 toby-laptop kernel:     5.300499 scsi 0:0:0:0: Attached scsi generic sg0 type 0
Jan 21 18:44:52 toby-laptop kernel:     5.300578 scsi 0:0:1:0: Attached scsi generic sg1 type 5
Jan 21 18:44:52 toby-laptop kernel:     5.326270 Driver 'sd' needs updating - please use bus_type methods
Jan 21 18:44:52 toby-laptop kernel:     5.326461 sd 0:0:0:0: sda 156301488 512-byte hardware sectors (80026 MB)
Jan 21 18:44:52 toby-laptop kernel:     5.326504 sd 0:0:0:0: sda Write Protect is off
Jan 21 18:44:52 toby-laptop kernel:     5.326579 sd 0:0:0:0: sda Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 21 18:44:52 toby-laptop kernel:     5.326716 sd 0:0:0:0: sda 156301488 512-byte hardware sectors (80026 MB)
Jan 21 18:44:52 toby-laptop kernel:     5.326755 sd 0:0:0:0: sda Write Protect is off
Jan 21 18:44:52 toby-laptop kernel:     5.326831 sd 0:0:0:0: sda Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 21 18:44:52 toby-laptop kernel:     5.326839  sda:4Driver 'sr' needs updating - please use bus_type methods
Jan 21 18:44:52 toby-laptop kernel:     5.350328  sda1 sda2 sda3 sda4
Jan 21 18:44:52 toby-laptop kernel:     5.351448 sd 0:0:0:0: sda Attached SCSI disk
Jan 21 18:44:52 toby-laptop kernel:     5.366061 sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jan 21 18:44:52 toby-laptop kernel:     5.366071 Uniform CD-ROM driver Revision: 3.20
Jan 21 18:44:52 toby-laptop kernel:     5.758155 PM: Starting manual resume from disk
Jan 21 18:44:52 toby-laptop kernel:     5.825725 kjournald starting.  Commit interval 5 seconds
Jan 21 18:44:52 toby-laptop kernel:     5.825763 EXT3-fs: mounted filesystem with ordered data mode.
Jan 21 18:44:52 toby-laptop kernel:    12.903222 udevd version 124 started
Jan 21 18:44:52 toby-laptop kernel:    13.715956 pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 21 18:44:52 toby-laptop kernel:    13.841873 shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 21 18:44:52 toby-laptop kernel:    13.963125 Linux agpgart interface v0.103
Jan 21 18:44:52 toby-laptop kernel:    14.084013 agpgart-intel 0000:00:00.0: Intel 945GM Chipset
Jan 21 18:44:52 toby-laptop kernel:    14.084985 agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Jan 21 18:44:52 toby-laptop kernel:    14.105797 agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
Jan 21 18:44:52 toby-laptop kernel:    14.624905 input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jan 21 18:44:52 toby-laptop kernel:    14.635242 ACPI: Power Button (FF) PWRF
Jan 21 18:44:52 toby-laptop kernel:    14.635418 input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
Jan 21 18:44:52 toby-laptop kernel:    14.635548 ACPI: Lid Switch LID
Jan 21 18:44:52 toby-laptop kernel:    14.635697 input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
Jan 21 18:44:52 toby-laptop kernel:    14.657040 ACPI: Sleep Button (CM) SLPB
Jan 21 18:44:52 toby-laptop kernel:    14.657234 input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
Jan 21 18:44:52 toby-laptop kernel:    14.681027 ACPI: Power Button (CM) PWRB
Jan 21 18:44:52 toby-laptop kernel:    14.681672 ACPI: WMI: Mapper loaded
Jan 21 18:44:52 toby-laptop kernel:    14.789621 intel_rng: FWH not detected
Jan 21 18:44:52 toby-laptop kernel:    15.109979 ACPI: AC Adapter ACAD (on-line)
Jan 21 18:44:52 toby-laptop kernel:    15.240588 input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input7
Jan 21 18:44:52 toby-laptop kernel:    15.261037 ACPI: Video Device VGA (multi-head: yes  rom: no  post: no)
Jan 21 18:44:52 toby-laptop kernel:    15.261490 input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/input/input8
Jan 21 18:44:52 toby-laptop kernel:    15.277026 ACPI: Video Device GFX0 (multi-head: yes  rom: no  post: no)
Jan 21 18:44:52 toby-laptop kernel:    15.390155 iTCO_vendor_support: vendor-support=0
Jan 21 18:44:52 toby-laptop kernel:    15.450296 iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Jan 21 18:44:52 toby-laptop kernel:    15.472707 iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Jan 21 18:44:52 toby-laptop kernel:    15.472878 iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jan 21 18:44:52 toby-laptop kernel:    15.616143 ACPI: Battery Slot BAT1 (battery absent)
Jan 21 18:44:52 toby-laptop kernel:    16.183470 Yenta: CardBus bridge found at 0000:06:04.0 1025:0090
Jan 21 18:44:52 toby-laptop kernel:    16.183506 Yenta: Using CSCINT to route CSC interrupts to PCI
Jan 21 18:44:52 toby-laptop kernel:    16.183511 Yenta: Routing CardBus interrupts to PCI
Jan 21 18:44:52 toby-laptop kernel:    16.183521 Yenta TI: socket 0000:06:04.0, mfunc 0x00111c12, devctl 0x44
Jan 21 18:44:52 toby-laptop kernel:    16.360737 iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Jan 21 18:44:52 toby-laptop kernel:    16.360746 iwl3945: Copyright(c) 2003-2008 Intel Corporation
Jan 21 18:44:52 toby-laptop kernel:    16.420911 Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
Jan 21 18:44:52 toby-laptop kernel:    16.420919 Socket status: 30000006
Jan 21 18:44:52 toby-laptop kernel:    16.420926 Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
Jan 21 18:44:52 toby-laptop kernel:    16.420938 pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
Jan 21 18:44:52 toby-laptop kernel:    16.420944 cs: IO port probe 0x2000-0x2fff: clean.
Jan 21 18:44:52 toby-laptop kernel:    16.421363 pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd00fffff
Jan 21 18:44:52 toby-laptop kernel:    16.421369 pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
Jan 21 18:44:52 toby-laptop kernel:    16.459143 iwl3945 0000:05:00.0: PCI INT A - GSI 19 (level, low) - IRQ 19
Jan 21 18:44:52 toby-laptop kernel:    16.459199 iwl3945: Detected Intel Wireless WiFi Link 3945ABG
Jan 21 18:44:52 toby-laptop kernel:    16.573223 eth1: register 'cdc_ether' at usb-0000:00:1d.2-1, CDC Ethernet Device, 00:04:0e:7b:7b:34
Jan 21 18:44:52 toby-laptop kernel:    16.573272 usbcore: registered new interface driver cdc_ether
Jan 21 18:44:52 toby-laptop kernel:    16.653333 iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
Jan 21 18:44:52 toby-laptop kernel:    16.686272 input: PC Speaker as /devices/platform/pcspkr/input/input9
Jan 21 18:44:52 toby-laptop kernel:    17.186276 iwl3945 0000:05:00.0: PCI INT A disabled
Jan 21 18:44:52 toby-laptop kernel:    17.324116 Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
Jan 21 18:44:52 toby-laptop kernel:    17.354632 input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
Jan 21 18:44:52 toby-laptop kernel:    17.457816 HDA Intel 0000:00:1b.0: PCI INT A - GSI 22 (level, low) - IRQ 22
Jan 21 18:44:52 toby-laptop kernel:    17.491009 acer-wmi: Acer Laptop ACPI-WMI Extras
Jan 21 18:44:52 toby-laptop kernel:    17.502221 Registered led device: acer-wmi::mail
Jan 21 18:44:52 toby-laptop kernel:    18.659274 cs: IO port probe 0x100-0x3af: clean.
Jan 21 18:44:52 toby-laptop kernel:    18.661566 cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Jan 21 18:44:52 toby-laptop kernel:    18.662511 cs: IO port probe 0x820-0x8ff: clean.
Jan 21 18:44:52 toby-laptop kernel:    18.663297 cs: IO port probe 0xc00-0xcf7: clean.
Jan 21 18:44:52 toby-laptop kernel:    18.664394 cs: IO port probe 0xa00-0xaff: clean.
Jan 21 18:44:52 toby-laptop kernel:    19.955313 lp: driver loaded but no devices found
Jan 21 18:44:52 toby-laptop kernel:    20.219959 Adding 1220900k swap on /dev/sda1.  Priority:-1 extents:1 across:1220900k
Jan 21 18:44:52 toby-laptop kernel:    20.805271 EXT3 FS on sda3, internal journal
Jan 21 18:44:52 toby-laptop kernel:    21.745763 kjournald starting.  Commit interval 5 seconds
Jan 21 18:44:52 toby-laptop kernel:    21.746148 EXT3 FS on sda4, internal journal
Jan 21 18:44:52 toby-laptop kernel:    21.746159 EXT3-fs: mounted filesystem with ordered data mode.
Jan 21 18:44:52 toby-laptop kernel:    22.102841 type=1505 audit(1232559890.369:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4209
Jan 21 18:44:52 toby-laptop kernel:    22.469371 type=1505 audit(1232559890.737:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4214
Jan 21 18:44:52 toby-laptop kernel:    22.469716 type=1505 audit(1232559890.737:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4214
Jan 21 18:44:52 toby-laptop kernel:    22.673465 ip_tables: (C) 2000-2006 Netfilter Core Team
Jan 21 18:44:52 toby-laptop kernel:    24.687601 warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Jan 21 18:44:53 toby-laptop kernel:    24.765374 apm: BIOS not found.
Jan 21 18:44:53 toby-laptop kernel:    24.938444 ppdev: user-space parallel port driver
Jan 21 18:44:59 toby-laptop kernel:    30.813449 iwl3945 0000:05:00.0: PCI INT A - GSI 19 (level, low) - IRQ 19
Jan 21 18:44:59 toby-laptop kernel:    30.816742 firmware: requesting iwlwifi-3945-1.ucode
Jan 21 18:44:59 toby-laptop kernel:    30.832554 drm Initialized drm 1.1.0 20060810
Jan 21 18:44:59 toby-laptop kernel:    30.863723 pci 0000:00:02.0: PCI INT A - GSI 16 (level, low) - IRQ 16
Jan 21 18:44:59 toby-laptop kernel:    30.863967 drm Initialized i915 1.6.0 20060119 on minor 0
Jan 21 18:44:59 toby-laptop kernel:    30.963114 Registered led device: iwl-phy0:radio
Jan 21 18:44:59 toby-laptop kernel:    30.963188 Registered led device: iwl-phy0:assoc
Jan 21 18:44:59 toby-laptop kernel:    30.963218 Registered led device: iwl-phy0:RX
Jan 21 18:44:59 toby-laptop kernel:    30.963245 Registered led device: iwl-phy0:TX
Jan 21 18:44:59 toby-laptop kernel:    31.253193 NET: Registered protocol family 17
Jan 21 18:45:05 toby-laptop kernel:    37.178113 NET: Registered protocol family 10
Jan 21 18:45:05 toby-laptop kernel:    37.179170 lo: Disabled Privacy Extensions
Jan 21 18:45:05 toby-laptop kernel:    37.181298 ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 21 18:45:05 toby-laptop kernel:    37.185484 ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 21 18:45:11 toby-laptop pulseaudio5512: ltdl-bind-now.c: Failed to find original dlopen loader.
Jan 21 18:45:11 toby-laptop pulseaudio5514: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jan 21 18:45:11 toby-laptop pulseaudio5514: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jan 21 18:51:56 toby-laptop kernel:   449.253488 apm: BIOS not found.
Jan 21 18:51:58 toby-laptop kernel:   451.196989 ip6_tables: (C) 2000-2006 Netfilter Core Team
Jan 21 18:52:00 toby-laptop kernel:   453.020103 Bluetooth: Core ver 2.13
Jan 21 18:52:00 toby-laptop kernel:   453.020283 NET: Registered protocol family 31
Jan 21 18:52:00 toby-laptop kernel:   453.020291 Bluetooth: HCI device and connection manager initialized
Jan 21 18:52:00 toby-laptop kernel:   453.020302 Bluetooth: HCI socket layer initialized
Jan 21 18:52:00 toby-laptop kernel:   453.039129 Bluetooth: L2CAP ver 2.11
Jan 21 18:52:00 toby-laptop kernel:   453.039139 Bluetooth: L2CAP socket layer initialized
Jan 21 18:52:00 toby-laptop kernel:   453.051615 Bluetooth: RFCOMM socket layer initialized
Jan 21 18:52:00 toby-laptop kernel:   453.051643 Bluetooth: RFCOMM TTY layer initialized
Jan 21 18:52:00 toby-laptop kernel:   453.051647 Bluetooth: RFCOMM ver 1.10
Jan 21 18:52:01 toby-laptop exiting on signal 15
Jan 21 19:13:41 toby-laptop syslogd 1.5.0#2ubuntu6: restart.
Jan 21 19:13:41 toby-laptop kernel: Inspecting /boot/System.map-2.6.27-9-generic
Jan 21 19:13:41 toby-laptop kernel: Cannot find map file.
Jan 21 19:13:41 toby-laptop kernel: Loaded 51702 symbols from 98 modules.
Jan 21 19:13:41 toby-laptop kernel:     0.000000 Initializing cgroup subsys cpuset
Jan 21 19:13:41 toby-laptop kernel:     0.000000 Initializing cgroup subsys cpu
Jan 21 19:13:41 toby-laptop kernel:     0.000000 Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 BIOS-provided physical RAM map:
Jan 21 19:13:41 toby-laptop kernel:     0.000000  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jan 21 19:13:41 toby-laptop kernel:     0.000000  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jan 21 19:13:41 toby-laptop kernel:     0.000000  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jan 21 19:13:41 toby-laptop kernel:     0.000000  BIOS-e820: 0000000000100000 - 000000001f680000 (usable)
Jan 21 19:13:41 toby-laptop kernel:     0.000000  BIOS-e820: 000000001f680000 - 000000001f700000 (ACPI NVS)
Jan 21 19:13:41 toby-laptop kernel:     0.000000  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
Jan 21 19:13:41 toby-laptop kernel:     0.000000  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jan 21 19:13:41 toby-laptop kernel:     0.000000  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jan 21 19:13:41 toby-laptop kernel:     0.000000  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Jan 21 19:13:41 toby-laptop kernel:     0.000000  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Jan 21 19:13:41 toby-laptop kernel:     0.000000  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Jan 21 19:13:41 toby-laptop kernel:     0.000000  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jan 21 19:13:41 toby-laptop kernel:     0.000000  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 last_pfn = 0x1f680 max_arch_pfn = 0x100000
Jan 21 19:13:41 toby-laptop kernel:     0.000000 RAMDISK: 1ee9e000 - 1f66f837
Jan 21 19:13:41 toby-laptop kernel:     0.000000 DMI present.
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: RSDP 000F6290, 0014 (r0 ACRSYS)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: RSDT 1F685EBD, 0050 (r1 ACRSYS ACRPRDCT  6040000  LTP        0)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: FACP 1F68CC76, 0074 (r1 Acer   Grape     6040000 LOHR       5A)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: DSDT 1F686EE3, 5D93 (r1 Acer   CALISTGA  6040000 INTL 20050228)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: FACS 1F68DFC0, 0040
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: APIC 1F68CCEA, 0068 (r1 Acer   Grape     6040000 LOHR       5A)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: HPET 1F68CD52, 0038 (r1 Acer   Grape     6040000 LOHR       5A)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: MCFG 1F68CD8A, 003C (r1 Acer   Grape     6040000 LOHR       5A)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: SLIC 1F68CDC6, 0176 (r1 ACRSYS ACRPRDCT  6040000 LOHR        0)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: DBGP 1F68CF3C, 0034 (r1 Acer   Grape     6040000 LOHR        0)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: APIC 1F68CF70, 0068 (r1 PTLTD  ^I APIC    6040000  LTP        0)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: BOOT 1F68CFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: SSDT 1F68647F, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050228)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: SSDT 1F6863D9, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050228)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: SSDT 1F685F0D, 04CC (r1  PmRef    CpuPm     3000 INTL 20050228)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: BIOS bug: multiple APIC/MADT found, using 0
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: If "acpi_apic_instance=2" works better, notify [EMAIL="emaillinux-acpi@vger.kernel.org"]emaillinux-acpi@vger.kernel.org[/EMAIL]/email
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: DMI detected: Acer
Jan 21 19:13:41 toby-laptop kernel:     0.000000 0MB HIGHMEM available.
Jan 21 19:13:41 toby-laptop kernel:     0.000000 502MB LOWMEM available.
Jan 21 19:13:41 toby-laptop kernel:     0.000000   mapped low ram: 0 - 1f680000
Jan 21 19:13:41 toby-laptop kernel:     0.000000   low ram: 00000000 - 1f680000
Jan 21 19:13:41 toby-laptop kernel:     0.000000   bootmap 00002000 - 00005ed0
Jan 21 19:13:41 toby-laptop kernel:     0.000000 (9 early reservations) == bootmem 0000000000 - 001f680000
Jan 21 19:13:41 toby-laptop kernel:     0.000000   #0 0000000000 - 0000001000   BIOS data page == 0000000000 - 0000001000
Jan 21 19:13:41 toby-laptop kernel:     0.000000   #1 0000001000 - 0000002000    EX TRAMPOLINE == 0000001000 - 0000002000
Jan 21 19:13:41 toby-laptop kernel:     0.000000   #2 0000006000 - 0000007000       TRAMPOLINE == 0000006000 - 0000007000
Jan 21 19:13:41 toby-laptop kernel:     0.000000   #3 0000100000 - 00005c0a20    TEXT DATA BSS == 0000100000 - 00005c0a20
Jan 21 19:13:41 toby-laptop kernel:     0.000000   #4 001ee9e000 - 001f66f837          RAMDISK == 001ee9e000 - 001f66f837
Jan 21 19:13:41 toby-laptop kernel:     0.000000   #5 00005c1000 - 00005c4000    INIT_PG_TABLE == 00005c1000 - 00005c4000
Jan 21 19:13:41 toby-laptop kernel:     0.000000   #6 000009f800 - 0000100000    BIOS reserved == 000009f800 - 0000100000
Jan 21 19:13:41 toby-laptop kernel:     0.000000   #7 0000007000 - 0000009000          PGTABLE == 0000007000 - 0000009000
Jan 21 19:13:41 toby-laptop kernel:     0.000000   #8 0000002000 - 0000006000          BOOTMAP == 0000002000 - 0000006000
Jan 21 19:13:41 toby-laptop kernel:     0.000000 found SMP MP-table at c00f6340 000f6340
Jan 21 19:13:41 toby-laptop kernel:     0.000000 Zone PFN ranges:
Jan 21 19:13:41 toby-laptop kernel:     0.000000   DMA      0x00000000 - 0x00001000
Jan 21 19:13:41 toby-laptop kernel:     0.000000   Normal   0x00001000 - 0x0001f680
Jan 21 19:13:41 toby-laptop kernel:     0.000000   HighMem  0x0001f680 - 0x0001f680
Jan 21 19:13:41 toby-laptop kernel:     0.000000 Movable zone start PFN for each node
Jan 21 19:13:41 toby-laptop kernel:     0.000000 early_node_map2 active PFN ranges
Jan 21 19:13:41 toby-laptop kernel:     0.000000     0: 0x00000000 - 0x0000009f
Jan 21 19:13:41 toby-laptop kernel:     0.000000     0: 0x00000100 - 0x0001f680
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: PM-Timer IO Port: 0x1008
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: LAPIC (acpi_id0x00 lapic_id0x00 enabled)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: LAPIC (acpi_id0x01 lapic_id0x01 enabled)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: LAPIC_NMI (acpi_id0x00 high edge lint0x1)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: LAPIC_NMI (acpi_id0x01 high edge lint0x1)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: IOAPIC (id0x01 address0xfec00000 gsi_base0)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 IOAPIC0: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan 21 19:13:41 toby-laptop kernel:     0.000000 ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jan 21 19:13:41 toby-laptop kernel:     0.000000 Using ACPI (MADT) for SMP configuration information
Jan 21 19:13:41 toby-laptop kernel:     0.000000 SMP: Allowing 2 CPUs, 0 hotplug CPUs
Jan 21 19:13:41 toby-laptop kernel:     0.000000 PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 21 19:13:41 toby-laptop kernel:     0.000000 PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 21 19:13:41 toby-laptop kernel:     0.000000 PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 21 19:13:41 toby-laptop kernel:     0.000000 Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 PERCPU: Allocating 41628 bytes of per cpu data
Jan 21 19:13:41 toby-laptop kernel:     0.000000 Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127412
Jan 21 19:13:41 toby-laptop kernel:     0.000000 Kernel command line: root=UUID=ec053eea-d1ca-4d91-a0ea-0ede95959ba2 ro quiet splash 
Jan 21 19:13:41 toby-laptop kernel:     0.000000 Enabling fast FPU save and restore... done.
Jan 21 19:13:41 toby-laptop kernel:     0.000000 Enabling unmasked SIMD FPU exception support... done.
Jan 21 19:13:41 toby-laptop kernel:     0.000000 Initializing CPU#0
Jan 21 19:13:41 toby-laptop kernel:     0.000000 PID hash table entries: 2048 (order: 11, 8192 bytes)
Jan 21 19:13:41 toby-laptop kernel:     0.000000 TSC: PIT calibration confirmed by PMTIMER.
Jan 21 19:13:41 toby-laptop kernel:     0.000000 TSC: using PIT calibration value
Jan 21 19:13:41 toby-laptop kernel:     0.000000 Detected 1662.467 MHz processor.
Jan 21 19:13:41 toby-laptop kernel:     0.004000 Console: colour VGA+ 80x25
Jan 21 19:13:41 toby-laptop kernel:     0.004000 console tty0 enabled
Jan 21 19:13:41 toby-laptop kernel:     0.004000 Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan 21 19:13:41 toby-laptop kernel:     0.004000 Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan 21 19:13:41 toby-laptop kernel:     0.004000 Memory: 495940k/514560k available (2572k kernel code, 17956k reserved, 1160k data, 424k init, 0k highmem)
Jan 21 19:13:41 toby-laptop kernel:     0.004000 virtual kernel memory layout:
Jan 21 19:13:41 toby-laptop kernel:     0.004000     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Jan 21 19:13:41 toby-laptop kernel:     0.004000     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Jan 21 19:13:41 toby-laptop kernel:     0.004000     vmalloc : 0xe0000000 - 0xff3fe000   ( 499 MB)
Jan 21 19:13:41 toby-laptop kernel:     0.004000     lowmem  : 0xc0000000 - 0xdf680000   ( 502 MB)
Jan 21 19:13:41 toby-laptop kernel:     0.004000       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
Jan 21 19:13:41 toby-laptop kernel:     0.004000       .data : 0xc038335a - 0xc04a5680   (1160 kB)
Jan 21 19:13:41 toby-laptop kernel:     0.004000       .text : 0xc0100000 - 0xc038335a   (2572 kB)
Jan 21 19:13:41 toby-laptop kernel:     0.004000 Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan 21 19:13:41 toby-laptop kernel:     0.004000 SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jan 21 19:13:41 toby-laptop kernel:     0.004000 Calibrating delay loop (skipped), value calculated using timer frequency.. 3324.93 BogoMIPS (lpj=6649868)
Jan 21 19:13:41 toby-laptop kernel:     0.004000 Security Framework initialized
Jan 21 19:13:41 toby-laptop kernel:     0.004000 SELinux:  Disabled at boot.
Jan 21 19:13:41 toby-laptop kernel:     0.004000 AppArmor: AppArmor initialized
Jan 21 19:13:41 toby-laptop kernel:     0.004000 Mount-cache hash table entries: 512
Jan 21 19:13:41 toby-laptop kernel:     0.004000 Initializing cgroup subsys ns
Jan 21 19:13:41 toby-laptop kernel:     0.004000 Initializing cgroup subsys cpuacct
Jan 21 19:13:41 toby-laptop kernel:     0.004000 Initializing cgroup subsys memory
Jan 21 19:13:41 toby-laptop kernel:     0.004000 CPU: L1 I cache: 32K, L1 D cache: 32K
Jan 21 19:13:41 toby-laptop kernel:     0.004000 CPU: L2 cache: 2048K
Jan 21 19:13:41 toby-laptop kernel:     0.004000 CPU: Physical Processor ID: 0
Jan 21 19:13:41 toby-laptop kernel:     0.004000 CPU: Processor Core ID: 0
Jan 21 19:13:41 toby-laptop kernel:     0.004000 using mwait in idle threads.
Jan 21 19:13:41 toby-laptop kernel:     0.004000 Checking 'hlt' instruction... OK.
Jan 21 19:13:41 toby-laptop kernel:     0.020007 ACPI: Core revision 20080609
Jan 21 19:13:41 toby-laptop kernel:     0.023096 ACPI: Checking initramfs for custom DSDT
Jan 21 19:13:41 toby-laptop kernel:     0.716318 ENABLING IO-APIC IRQs
Jan 21 19:13:41 toby-laptop kernel:     0.716547 ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 21 19:13:41 toby-laptop kernel:     0.757229 CPU0: Intel Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08
Jan 21 19:13:41 toby-laptop kernel:     0.760031 Booting processor 1/1 ip 6000
Jan 21 19:13:41 toby-laptop kernel:     0.004000 Initializing CPU#1
Jan 21 19:13:41 toby-laptop kernel:     0.004000 Calibrating delay using timer specific routine.. 3127.72 BogoMIPS (lpj=6255458)
Jan 21 19:13:41 toby-laptop kernel:     0.004000 CPU: L1 I cache: 32K, L1 D cache: 32K
Jan 21 19:13:41 toby-laptop kernel:     0.004000 CPU: L2 cache: 2048K
Jan 21 19:13:41 toby-laptop kernel:     0.004000 CPU: Physical Processor ID: 0
Jan 21 19:13:41 toby-laptop kernel:     0.004000 CPU: Processor Core ID: 1
Jan 21 19:13:41 toby-laptop kernel:     0.844792 CPU1: Intel Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08
Jan 21 19:13:41 toby-laptop kernel:     0.844829 checking TSC synchronization CPU#0 - CPU#1: passed.
Jan 21 19:13:41 toby-laptop kernel:     0.848062 Brought up 2 CPUs
Jan 21 19:13:41 toby-laptop kernel:     0.848068 Total of 2 processors activated (6452.66 BogoMIPS).
Jan 21 19:13:41 toby-laptop kernel:     0.848330 net_namespace: 840 bytes
Jan 21 19:13:41 toby-laptop kernel:     0.848330 Booting paravirtualized kernel on bare hardware
Jan 21 19:13:41 toby-laptop kernel:     0.848540 Time: 19:13:17  Date: 01/21/09
Jan 21 19:13:41 toby-laptop kernel:     0.848591 NET: Registered protocol family 16
Jan 21 19:13:41 toby-laptop kernel:     0.848629 EISA bus registered
Jan 21 19:13:41 toby-laptop kernel:     0.848629 ACPI: bus type pci registered
Jan 21 19:13:41 toby-laptop kernel:     0.848629 PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jan 21 19:13:41 toby-laptop kernel:     0.848629 PCI: MCFG area at e0000000 reserved in E820
Jan 21 19:13:41 toby-laptop kernel:     0.848629 PCI: Using MMCONFIG for extended config space
Jan 21 19:13:41 toby-laptop kernel:     0.848629 PCI: Using configuration type 1 for base access
Jan 21 19:13:41 toby-laptop kernel:     0.863530 ACPI: BIOS _OSI(Linux) query ignored via DMI
Jan 21 19:13:41 toby-laptop kernel:     0.864958 ACPI: Interpreter enabled
Jan 21 19:13:41 toby-laptop kernel:     0.864963 ACPI: (supports S0 S3 S4 S5)
Jan 21 19:13:41 toby-laptop kernel:     0.864994 ACPI: Using IOAPIC for interrupt routing
Jan 21 19:13:41 toby-laptop kernel:     0.872314 ACPI: EC: non-query interrupt received, switching to interrupt mode
Jan 21 19:13:41 toby-laptop kernel:     0.928691 ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
Jan 21 19:13:41 toby-laptop kernel:     0.928691 ACPI: EC: driver started in interrupt mode
Jan 21 19:13:41 toby-laptop kernel:     0.928691 ACPI: PCI Root Bridge PCI0 (0000:00)
Jan 21 19:13:41 toby-laptop kernel:     0.932342 pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jan 21 19:13:41 toby-laptop kernel:     0.932351 pci 0000:00:1b.0: PME# disabled
Jan 21 19:13:41 toby-laptop kernel:     0.932443 pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jan 21 19:13:41 toby-laptop kernel:     0.932451 pci 0000:00:1c.0: PME# disabled
Jan 21 19:13:41 toby-laptop kernel:     0.932542 pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jan 21 19:13:41 toby-laptop kernel:     0.932551 pci 0000:00:1c.1: PME# disabled
Jan 21 19:13:41 toby-laptop kernel:     0.932642 pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jan 21 19:13:41 toby-laptop kernel:     0.932651 pci 0000:00:1c.2: PME# disabled
Jan 21 19:13:41 toby-laptop kernel:     0.932742 pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jan 21 19:13:41 toby-laptop kernel:     0.932751 pci 0000:00:1c.3: PME# disabled
Jan 21 19:13:41 toby-laptop kernel:     0.933223 pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jan 21 19:13:41 toby-laptop kernel:     0.933232 pci 0000:00:1d.7: PME# disabled
Jan 21 19:13:41 toby-laptop kernel:     0.933429 pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Jan 21 19:13:41 toby-laptop kernel:     0.933438 pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
Jan 21 19:13:41 toby-laptop kernel:     0.934314 pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
Jan 21 19:13:41 toby-laptop kernel:     0.934330 pci 0000:05:00.0: PME# disabled
Jan 21 19:13:41 toby-laptop kernel:     0.934545 pci 0000:06:01.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 21 19:13:41 toby-laptop kernel:     0.934553 pci 0000:06:01.0: PME# disabled
Jan 21 19:13:41 toby-laptop kernel:     0.934645 pci 0000:06:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 21 19:13:41 toby-laptop kernel:     0.934654 pci 0000:06:04.0: PME# disabled
Jan 21 19:13:41 toby-laptop kernel:     0.934714 pci 0000:00:1e.0: transparent bridge
Jan 21 19:13:41 toby-laptop kernel:     0.944261 ACPI: PCI Interrupt Link LNKA (IRQs 1 5 *6 10 12 14 15)
Jan 21 19:13:41 toby-laptop kernel:     0.944518 ACPI: PCI Interrupt Link LNKB (IRQs 1 5 6 *11 12 14 15)
Jan 21 19:13:41 toby-laptop kernel:     0.944769 ACPI: PCI Interrupt Link LNKC (IRQs 1 5 6 10 12 14 15) *11
Jan 21 19:13:41 toby-laptop kernel:     0.945030 ACPI: PCI Interrupt Link LNKD (IRQs 1 5 6 11 12 14 15) *10
Jan 21 19:13:41 toby-laptop kernel:     0.945283 ACPI: PCI Interrupt Link LNKE (IRQs 1 5 6 10 12 14 15) *0, disabled.
Jan 21 19:13:41 toby-laptop kernel:     0.945538 ACPI: PCI Interrupt Link LNKF (IRQs 1 5 6 11 12 14 15) *10
Jan 21 19:13:41 toby-laptop kernel:     0.945789 ACPI: PCI Interrupt Link LNKG (IRQs 1 5 6 *10 12 14 15)
Jan 21 19:13:41 toby-laptop kernel:     0.946040 ACPI: PCI Interrupt Link LNKH (IRQs 1 *5 6 11 12 14 15)
Jan 21 19:13:41 toby-laptop kernel:     0.946193 Linux Plug and Play Support v0.97 (c) Adam Belay
Jan 21 19:13:41 toby-laptop kernel:     0.946193 pnp: PnP ACPI init
Jan 21 19:13:41 toby-laptop kernel:     0.946193 ACPI: bus type pnp registered
Jan 21 19:13:41 toby-laptop kernel:     0.972459 pnp 00:06: io resource (0x2e-0x2f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 19:13:41 toby-laptop kernel:     0.972459 pnp 00:06: io resource (0x4e-0x4f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 19:13:41 toby-laptop kernel:     0.972459 pnp 00:06: io resource (0x61-0x61) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 19:13:41 toby-laptop kernel:     0.972459 pnp 00:06: io resource (0x63-0x63) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 19:13:41 toby-laptop kernel:     0.972459 pnp 00:06: io resource (0x65-0x65) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 19:13:41 toby-laptop kernel:     0.972459 pnp 00:06: io resource (0x67-0x67) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 19:13:41 toby-laptop kernel:     0.972459 pnp 00:06: io resource (0x70-0x70) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 19:13:41 toby-laptop kernel:     0.972459 pnp 00:06: io resource (0x80-0x80) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 19:13:41 toby-laptop kernel:     0.972459 pnp 00:06: io resource (0x92-0x92) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 19:13:41 toby-laptop kernel:     0.972459 pnp 00:06: io resource (0xb2-0xb3) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 19:13:41 toby-laptop kernel:     0.972459 pnp 00:06: io resource (0x800-0x80f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
Jan 21 19:13:41 toby-laptop kernel:     0.972459 pnp: PnP ACPI: found 10 devices
Jan 21 19:13:41 toby-laptop kernel:     0.972459 ACPI: ACPI bus type pnp unregistered
Jan 21 19:13:41 toby-laptop kernel:     0.972459 PnPBIOS: Disabled by ACPI PNP
Jan 21 19:13:41 toby-laptop kernel:     0.972459 PCI: Using ACPI for IRQ routing
Jan 21 19:13:41 toby-laptop kernel:     0.972459 pci 0000:00:1c.0: BAR 7: can't allocate resource
Jan 21 19:13:41 toby-laptop kernel:     0.972459 pci 0000:00:1c.0: BAR 8: can't allocate resource
Jan 21 19:13:41 toby-laptop kernel:     0.980048 NET: Registered protocol family 8
Jan 21 19:13:41 toby-laptop kernel:     0.980053 NET: Registered protocol family 20
Jan 21 19:13:41 toby-laptop kernel:     0.980085 NetLabel: Initializing
Jan 21 19:13:41 toby-laptop kernel:     0.980085 NetLabel:  domain hash size = 128
Jan 21 19:13:41 toby-laptop kernel:     0.980085 NetLabel:  protocols = UNLABELED CIPSOv4
Jan 21 19:13:41 toby-laptop kernel:     0.980104 NetLabel:  unlabeled traffic allowed by default
Jan 21 19:13:41 toby-laptop kernel:     0.980117 hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jan 21 19:13:41 toby-laptop kernel:     0.980127 hpet0: 3 64-bit timers, 14318180 Hz
Jan 21 19:13:41 toby-laptop kernel:     0.982196 tracer: 772 pages allocated for 65536 entries of 48 bytes
Jan 21 19:13:41 toby-laptop kernel:     0.982201    actual entries 65620
Jan 21 19:13:41 toby-laptop kernel:     0.982342 AppArmor: AppArmor Filesystem Enabled
Jan 21 19:13:41 toby-laptop kernel:     0.982378 ACPI: RTC can wake from S4
Jan 21 19:13:41 toby-laptop kernel:     0.988044 system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
Jan 21 19:13:41 toby-laptop kernel:     0.988052 system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
Jan 21 19:13:41 toby-laptop kernel:     0.988058 system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
Jan 21 19:13:41 toby-laptop kernel:     0.988065 system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
Jan 21 19:13:41 toby-laptop kernel:     0.988072 system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
Jan 21 19:13:41 toby-laptop kernel:     0.988079 system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
Jan 21 19:13:41 toby-laptop kernel:     0.988095 system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
Jan 21 19:13:41 toby-laptop kernel:     0.988110 system 00:06: ioport range 0x1000-0x107f has been reserved
Jan 21 19:13:41 toby-laptop kernel:     0.988117 system 00:06: ioport range 0x1180-0x11bf has been reserved
Jan 21 19:13:41 toby-laptop kernel:     0.988123 system 00:06: ioport range 0x1640-0x164f has been reserved
Jan 21 19:13:41 toby-laptop kernel:     0.988129 system 00:06: ioport range 0xfe00-0xfefe has been reserved
Jan 21 19:13:41 toby-laptop kernel:     0.988135 system 00:06: ioport range 0xff2c-0xff2f has been reserved
Jan 21 19:13:41 toby-laptop kernel:     1.023989 pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Jan 21 19:13:41 toby-laptop kernel:     1.024007 pci 0000:00:1c.0:   IO window: disabled
Jan 21 19:13:41 toby-laptop kernel:     1.024017 pci 0000:00:1c.0:   MEM window: disabled
Jan 21 19:13:41 toby-laptop kernel:     1.024025 pci 0000:00:1c.0:   PREFETCH window: disabled
Jan 21 19:13:41 toby-laptop kernel:     1.024037 pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
Jan 21 19:13:41 toby-laptop kernel:     1.024042 pci 0000:00:1c.1:   IO window: disabled
Jan 21 19:13:41 toby-laptop kernel:     1.024052 pci 0000:00:1c.1:   MEM window: disabled
Jan 21 19:13:41 toby-laptop kernel:     1.024059 pci 0000:00:1c.1:   PREFETCH window: disabled
Jan 21 19:13:41 toby-laptop kernel:     1.024072 pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
Jan 21 19:13:41 toby-laptop kernel:     1.024076 pci 0000:00:1c.2:   IO window: disabled
Jan 21 19:13:41 toby-laptop kernel:     1.024086 pci 0000:00:1c.2:   MEM window: disabled
Jan 21 19:13:41 toby-laptop kernel:     1.024094 pci 0000:00:1c.2:   PREFETCH window: disabled
Jan 21 19:13:41 toby-laptop kernel:     1.024106 pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
Jan 21 19:13:41 toby-laptop kernel:     1.024111 pci 0000:00:1c.3:   IO window: disabled
Jan 21 19:13:41 toby-laptop kernel:     1.024121 pci 0000:00:1c.3:   MEM window: 0xd0100000-0xd01fffff
Jan 21 19:13:41 toby-laptop kernel:     1.024130 pci 0000:00:1c.3:   PREFETCH window: disabled
Jan 21 19:13:41 toby-laptop kernel:     1.024150 pci 0000:06:04.0: CardBus bridge, secondary bus 0000:07
Jan 21 19:13:41 toby-laptop kernel:     1.024156 pci 0000:06:04.0:   IO window: 0x002000-0x0020ff
Jan 21 19:13:41 toby-laptop kernel:     1.024165 pci 0000:06:04.0:   IO window: 0x002400-0x0024ff
Jan 21 19:13:41 toby-laptop kernel:     1.024175 pci 0000:06:04.0:   PREFETCH window: 0x30000000-0x33ffffff
Jan 21 19:13:41 toby-laptop kernel:     1.024184 pci 0000:06:04.0:   MEM window: 0x34000000-0x37ffffff
Jan 21 19:13:41 toby-laptop kernel:     1.024194 pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
Jan 21 19:13:41 toby-laptop kernel:     1.024201 pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
Jan 21 19:13:41 toby-laptop kernel:     1.024211 pci 0000:00:1e.0:   MEM window: 0xd0000000-0xd00fffff
Jan 21 19:13:41 toby-laptop kernel:     1.024220 pci 0000:00:1e.0:   PREFETCH window: 0x00000030000000-0x00000033ffffff
Jan 21 19:13:41 toby-laptop kernel:     1.024248 pci 0000:00:1c.0: PCI INT A - GSI 17 (level, low) - IRQ 17
Jan 21 19:13:41 toby-laptop kernel:     1.024275 pci 0000:00:1c.1: PCI INT B - GSI 16 (level, low) - IRQ 16
Jan 21 19:13:41 toby-laptop kernel:     1.024300 pci 0000:00:1c.2: PCI INT C - GSI 18 (level, low) - IRQ 18
Jan 21 19:13:41 toby-laptop kernel:     1.024324 pci 0000:00:1c.3: PCI INT D - GSI 19 (level, low) - IRQ 19
Jan 21 19:13:41 toby-laptop kernel:     1.024343 pci 0000:00:1e.0: enabling device (0004 - 0007)
Jan 21 19:13:41 toby-laptop kernel:     1.024369 pci 0000:06:04.0: PCI INT A - GSI 16 (level, low) - IRQ 16
Jan 21 19:13:41 toby-laptop kernel:     1.024379 bus: 00 index 0 io port: 0, ffff
Jan 21 19:13:41 toby-laptop kernel:     1.024384 bus: 00 index 1 mmio: 0, ffffffff
Jan 21 19:13:41 toby-laptop kernel:     1.024389 bus: 02 index 0 mmio: 0, fff
Jan 21 19:13:41 toby-laptop kernel:     1.024393 bus: 02 index 1 mmio: 0, fffff
Jan 21 19:13:41 toby-laptop kernel:     1.024398 bus: 02 index 2 mmio: 0, 0
Jan 21 19:13:41 toby-laptop kernel:     1.024402 bus: 02 index 3 mmio: 0, 0
Jan 21 19:13:41 toby-laptop kernel:     1.024406 bus: 03 index 0 mmio: 0, 0
Jan 21 19:13:41 toby-laptop kernel:     1.024410 bus: 03 index 1 mmio: 0, 0
Jan 21 19:13:41 toby-laptop kernel:     1.024414 bus: 03 index 2 mmio: 0, 0
Jan 21 19:13:41 toby-laptop kernel:     1.024418 bus: 03 index 3 mmio: 0, 0
Jan 21 19:13:41 toby-laptop kernel:     1.024422 bus: 04 index 0 mmio: 0, 0
Jan 21 19:13:41 toby-laptop kernel:     1.024427 bus: 04 index 1 mmio: 0, 0
Jan 21 19:13:41 toby-laptop kernel:     1.024431 bus: 04 index 2 mmio: 0, 0
Jan 21 19:13:41 toby-laptop kernel:     1.024435 bus: 04 index 3 mmio: 0, 0
Jan 21 19:13:41 toby-laptop kernel:     1.024439 bus: 05 index 0 mmio: 0, 0
Jan 21 19:13:41 toby-laptop kernel:     1.024443 bus: 05 index 1 mmio: d0100000, d01fffff
Jan 21 19:13:41 toby-laptop kernel:     1.024448 bus: 05 index 2 mmio: 0, 0
Jan 21 19:13:41 toby-laptop kernel:     1.024452 bus: 05 index 3 mmio: 0, 0
Jan 21 19:13:41 toby-laptop kernel:     1.024457 bus: 06 index 0 io port: 2000, 2fff
Jan 21 19:13:41 toby-laptop kernel:     1.024461 bus: 06 index 1 mmio: d0000000, d00fffff
Jan 21 19:13:41 toby-laptop kernel:     1.024466 bus: 06 index 2 mmio: 30000000, 33ffffff
Jan 21 19:13:41 toby-laptop kernel:     1.024471 bus: 06 index 3 io port: 0, ffff
Jan 21 19:13:41 toby-laptop kernel:     1.024476 bus: 06 index 4 mmio: 0, ffffffff
Jan 21 19:13:41 toby-laptop kernel:     1.024480 bus: 07 index 0 io port: 2000, 20ff
Jan 21 19:13:41 toby-laptop kernel:     1.024485 bus: 07 index 1 io port: 2400, 24ff
Jan 21 19:13:41 toby-laptop kernel:     1.024490 bus: 07 index 2 mmio: 30000000, 33ffffff
Jan 21 19:13:41 toby-laptop kernel:     1.024494 bus: 07 index 3 mmio: 34000000, 37ffffff
Jan 21 19:13:41 toby-laptop kernel:     1.024511 NET: Registered protocol family 2
Jan 21 19:13:41 toby-laptop kernel:     1.036097 IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Jan 21 19:13:41 toby-laptop kernel:     1.036497 TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Jan 21 19:13:41 toby-laptop kernel:     1.036598 TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Jan 21 19:13:41 toby-laptop kernel:     1.036696 TCP: Hash tables configured (established 16384 bind 16384)
Jan 21 19:13:41 toby-laptop kernel:     1.036702 TCP reno registered
Jan 21 19:13:41 toby-laptop kernel:     1.037707 NET: Registered protocol family 1
Jan 21 19:13:41 toby-laptop kernel:     1.037907 checking if image is initramfs... it is
Jan 21 19:13:41 toby-laptop kernel:     2.437460 Freeing initrd memory: 8006k freed
Jan 21 19:13:41 toby-laptop kernel:     2.438018 Simple Boot Flag at 0x36 set to 0x1
Jan 21 19:13:41 toby-laptop kernel:     2.439711 audit: initializing netlink socket (disabled)
Jan 21 19:13:41 toby-laptop kernel:     2.439749 type=2000 audit(1232565198.437:1): initialized
Jan 21 19:13:41 toby-laptop kernel:     2.452142 HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jan 21 19:13:41 toby-laptop kernel:     2.457299 VFS: Disk quotas dquot_6.5.1
Jan 21 19:13:41 toby-laptop kernel:     2.457481 Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan 21 19:13:41 toby-laptop kernel:     2.457692 msgmni has been set to 984
Jan 21 19:13:41 toby-laptop kernel:     2.457940 io scheduler noop registered
Jan 21 19:13:41 toby-laptop kernel:     2.457946 io scheduler anticipatory registered
Jan 21 19:13:41 toby-laptop kernel:     2.457951 io scheduler deadline registered
Jan 21 19:13:41 toby-laptop kernel:     2.457975 io scheduler cfq registered (default)
Jan 21 19:13:41 toby-laptop kernel:     2.458414 pcieport-driver 0000:00:1c.0: found MSI capability
Jan 21 19:13:41 toby-laptop kernel:     2.458918 pcieport-driver 0000:00:1c.1: found MSI capability
Jan 21 19:13:41 toby-laptop kernel:     2.459409 pcieport-driver 0000:00:1c.2: found MSI capability
Jan 21 19:13:41 toby-laptop kernel:     2.459904 pcieport-driver 0000:00:1c.3: found MSI capability
Jan 21 19:13:41 toby-laptop kernel:     2.460847 isapnp: Scanning for PnP cards...
Jan 21 19:13:41 toby-laptop kernel:     2.794128 isapnp: No Plug & Play device found
Jan 21 19:13:41 toby-laptop kernel:     2.868499 Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Jan 21 19:13:41 toby-laptop kernel:     2.873197 brd: module loaded
Jan 21 19:13:41 toby-laptop kernel:     2.873346 input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jan 21 19:13:41 toby-laptop kernel:     2.873590 PNP: PS/2 Controller PNP0303:PS2K,PNP0f13:MSS0 at 0x60,0x64 irq 1,12
Jan 21 19:13:41 toby-laptop kernel:     2.874081 i8042.c: Detected active multiplexing controller, rev 1.1.
Jan 21 19:13:41 toby-laptop kernel:     2.874176 serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 21 19:13:41 toby-laptop kernel:     2.874187 serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jan 21 19:13:41 toby-laptop kernel:     2.874194 serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jan 21 19:13:41 toby-laptop kernel:     2.874200 serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jan 21 19:13:41 toby-laptop kernel:     2.874205 serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jan 21 19:13:41 toby-laptop kernel:     2.874907 mice: PS/2 mouse device common for all mice
Jan 21 19:13:41 toby-laptop kernel:     2.875198 rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Jan 21 19:13:41 toby-laptop kernel:     2.875239 rtc0: alarms up to one month, y3k, hpet irqs
Jan 21 19:13:41 toby-laptop kernel:     2.875515 EISA: Probing bus 0 at eisa.0
Jan 21 19:13:41 toby-laptop kernel:     2.875526 Cannot allocate resource for EISA slot 1
Jan 21 19:13:41 toby-laptop kernel:     2.875532 Cannot allocate resource for EISA slot 2
Jan 21 19:13:41 toby-laptop kernel:     2.875558 Cannot allocate resource for EISA slot 5
Jan 21 19:13:41 toby-laptop kernel:     2.875578 EISA: Detected 0 cards.
Jan 21 19:13:41 toby-laptop kernel:     2.875584 cpuidle: using governor ladder
Jan 21 19:13:41 toby-laptop kernel:     2.875589 cpuidle: using governor menu
Jan 21 19:13:41 toby-laptop kernel:     2.876655 TCP cubic registered
Jan 21 19:13:41 toby-laptop kernel:     2.876703 Using IPI No-Shortcut mode
Jan 21 19:13:41 toby-laptop kernel:     2.877083 registered taskstats version 1
Jan 21 19:13:41 toby-laptop kernel:     2.877284   Magic number: 9:729:243
Jan 21 19:13:41 toby-laptop kernel:     2.877438 rtc_cmos 00:07: setting system clock to 2009-01-21 19:13:19 UTC (1232565199)
Jan 21 19:13:41 toby-laptop kernel:     2.877445 BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 21 19:13:41 toby-laptop kernel:     2.877450 EDD information not available.
Jan 21 19:13:41 toby-laptop kernel:     2.877747 input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jan 21 19:13:41 toby-laptop kernel:     2.877891 Freeing unused kernel memory: 424k freed
Jan 21 19:13:41 toby-laptop kernel:     2.877986 Write protecting the kernel text: 2576k
Jan 21 19:13:41 toby-laptop kernel:     2.878043 Write protecting the kernel read-only data: 936k
Jan 21 19:13:41 toby-laptop kernel:     3.159726 fuse init (API version 7.9)
Jan 21 19:13:41 toby-laptop kernel:     3.272896 ACPI: SSDT 1F686C25, 01F6 (r1  PmRef  Cpu0Ist     3000 INTL 20050228)
Jan 21 19:13:41 toby-laptop kernel:     3.273763 ACPI: SSDT 1F6866DE, 04C2 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
Jan 21 19:13:41 toby-laptop kernel:     3.284358 ACPI: CPU0 (power states: C1C1 C2C2 C3C3)
Jan 21 19:13:41 toby-laptop kernel:     3.284477 processor ACPI0007:00: registered as cooling_device0
Jan 21 19:13:41 toby-laptop kernel:     3.284486 ACPI: Processor CPU0 (supports 8 throttling states)
Jan 21 19:13:41 toby-laptop kernel:     3.285161 ACPI: SSDT 1F686E1B, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050228)
Jan 21 19:13:41 toby-laptop kernel:     3.285947 ACPI: SSDT 1F686BA0, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050228)
Jan 21 19:13:41 toby-laptop kernel:     3.288017 Marking TSC unstable due to TSC halts in idle
Jan 21 19:13:41 toby-laptop kernel:     3.292417 ACPI: CPU1 (power states: C1C1 C2C2 C3C3)
Jan 21 19:13:41 toby-laptop kernel:     3.292525 processor ACPI0007:01: registered as cooling_device1
Jan 21 19:13:41 toby-laptop kernel:     3.292534 ACPI: Processor CPU1 (supports 8 throttling states)
Jan 21 19:13:41 toby-laptop kernel:     3.303397 thermal LNXTHERM:01: registered as thermal_zone0
Jan 21 19:13:41 toby-laptop kernel:     3.313398 ACPI: Thermal Zone TZ00 (48 C)
Jan 21 19:13:41 toby-laptop kernel:     3.318264 thermal LNXTHERM:02: registered as thermal_zone1
Jan 21 19:13:41 toby-laptop kernel:     3.327450 ACPI: Thermal Zone TZ01 (48 C)
Jan 21 19:13:41 toby-laptop kernel:     4.023530 usbcore: registered new interface driver usbfs
Jan 21 19:13:41 toby-laptop kernel:     4.023572 usbcore: registered new interface driver hub
Jan 21 19:13:41 toby-laptop kernel:     4.023660 usbcore: registered new device driver usb
Jan 21 19:13:41 toby-laptop kernel:     4.028845 USB Universal Host Controller Interface driver v3.0
Jan 21 19:13:41 toby-laptop kernel:     4.028928 uhci_hcd 0000:00:1d.0: PCI INT A - GSI 23 (level, low) - IRQ 23
Jan 21 19:13:41 toby-laptop kernel:     4.028950 uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan 21 19:13:41 toby-laptop kernel:     4.029024 uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jan 21 19:13:41 toby-laptop kernel:     4.029073 uhci_hcd 0000:00:1d.0: irq 23, io base 0x000050a0
Jan 21 19:13:41 toby-laptop kernel:     4.029339 usb usb1: configuration #1 chosen from 1 choice
Jan 21 19:13:41 toby-laptop kernel:     4.029394 hub 1-0:1.0: USB hub found
Jan 21 19:13:41 toby-laptop kernel:     4.029407 hub 1-0:1.0: 2 ports detected
Jan 21 19:13:41 toby-laptop kernel:     4.120146 No dock devices found.
Jan 21 19:13:41 toby-laptop kernel:     4.170443 SCSI subsystem initialized
Jan 21 19:13:41 toby-laptop kernel:     4.236498 uhci_hcd 0000:00:1d.1: PCI INT B - GSI 19 (level, low) - IRQ 19
Jan 21 19:13:41 toby-laptop kernel:     4.236523 uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan 21 19:13:41 toby-laptop kernel:     4.236570 uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jan 21 19:13:41 toby-laptop kernel:     4.236619 uhci_hcd 0000:00:1d.1: irq 19, io base 0x000050c0
Jan 21 19:13:41 toby-laptop kernel:     4.236799 usb usb2: configuration #1 chosen from 1 choice
Jan 21 19:13:41 toby-laptop kernel:     4.236861 hub 2-0:1.0: USB hub found
Jan 21 19:13:41 toby-laptop kernel:     4.236875 hub 2-0:1.0: 2 ports detected
Jan 21 19:13:41 toby-laptop kernel:     4.348080 usb 1-1: new low speed USB device using uhci_hcd and address 2
Jan 21 19:13:41 toby-laptop kernel:     4.444486 uhci_hcd 0000:00:1d.2: PCI INT C - GSI 18 (level, low) - IRQ 18
Jan 21 19:13:41 toby-laptop kernel:     4.444512 uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan 21 19:13:41 toby-laptop kernel:     4.444567 uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jan 21 19:13:41 toby-laptop kernel:     4.444619 uhci_hcd 0000:00:1d.2: irq 18, io base 0x000050e0
Jan 21 19:13:41 toby-laptop kernel:     4.444821 usb usb3: configuration #1 chosen from 1 choice
Jan 21 19:13:41 toby-laptop kernel:     4.444877 hub 3-0:1.0: USB hub found
Jan 21 19:13:41 toby-laptop kernel:     4.444892 hub 3-0:1.0: 2 ports detected
Jan 21 19:13:41 toby-laptop kernel:     4.524369 usb 1-1: configuration #1 chosen from 1 choice
Jan 21 19:13:41 toby-laptop kernel:     4.636045 usb 2-1: new full speed USB device using uhci_hcd and address 2
Jan 21 19:13:41 toby-laptop kernel:     4.653466 uhci_hcd 0000:00:1d.3: PCI INT D - GSI 16 (level, low) - IRQ 16
Jan 21 19:13:41 toby-laptop kernel:     4.653492 uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jan 21 19:13:41 toby-laptop kernel:     4.653546 uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Jan 21 19:13:41 toby-laptop kernel:     4.653599 uhci_hcd 0000:00:1d.3: irq 16, io base 0x00005400
Jan 21 19:13:41 toby-laptop kernel:     4.653780 usb usb4: configuration #1 chosen from 1 choice
Jan 21 19:13:41 toby-laptop kernel:     4.653840 hub 4-0:1.0: USB hub found
Jan 21 19:13:41 toby-laptop kernel:     4.653854 hub 4-0:1.0: 2 ports detected
Jan 21 19:13:41 toby-laptop kernel:     4.757323 ehci_hcd 0000:00:1d.7: PCI INT A - GSI 23 (level, low) - IRQ 23
Jan 21 19:13:41 toby-laptop kernel:     4.757355 ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan 21 19:13:41 toby-laptop kernel:     4.757410 ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Jan 21 19:13:41 toby-laptop kernel:     4.761323 ehci_hcd 0000:00:1d.7: debug port 1
Jan 21 19:13:41 toby-laptop kernel:     4.761349 ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0544000
Jan 21 19:13:41 toby-laptop kernel:     4.780071 ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan 21 19:13:41 toby-laptop kernel:     4.780352 usb usb5: configuration #1 chosen from 1 choice
Jan 21 19:13:41 toby-laptop kernel:     4.780411 hub 5-0:1.0: USB hub found
Jan 21 19:13:41 toby-laptop kernel:     4.780426 hub 5-0:1.0: 8 ports detected
Jan 21 19:13:41 toby-laptop kernel:     4.960170 usb 1-1: USB disconnect, address 2
Jan 21 19:13:41 toby-laptop kernel:     4.960239 usbcore: registered new interface driver hiddev
Jan 21 19:13:41 toby-laptop kernel:     4.984516 pata_acpi 0000:00:1f.1: PCI INT B - GSI 19 (level, low) - IRQ 19
Jan 21 19:13:41 toby-laptop kernel:     4.984597 pata_acpi 0000:00:1f.1: PCI INT B disabled
Jan 21 19:13:41 toby-laptop kernel:     4.999244 b44 0000:06:01.0: enabling device (0000 - 0002)
Jan 21 19:13:41 toby-laptop kernel:     4.999260 b44 0000:06:01.0: PCI INT A - GSI 21 (level, low) - IRQ 21
Jan 21 19:13:41 toby-laptop kernel:     5.000044 Clocksource tsc unstable (delta = -147904216 ns)
Jan 21 19:13:41 toby-laptop kernel:     5.056239 ssb: Sonics Silicon Backplane found on PCI device 0000:06:01.0
Jan 21 19:13:41 toby-laptop kernel:     5.056299 ata_piix 0000:00:1f.1: PCI INT B - GSI 19 (level, low) - IRQ 19
Jan 21 19:13:41 toby-laptop kernel:     5.056537 scsi0 : ata_piix
Jan 21 19:13:41 toby-laptop kernel:     5.056722 b44.c:v2.0
Jan 21 19:13:41 toby-laptop kernel:     5.056787 scsi1 : ata_piix
Jan 21 19:13:41 toby-laptop kernel:     5.058200 ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x5090 irq 14
Jan 21 19:13:41 toby-laptop kernel:     5.058207 ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x5098 irq 15
Jan 21 19:13:41 toby-laptop kernel:     5.076797 eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0f:b0:f0:5a:de
Jan 21 19:13:41 toby-laptop kernel:     5.229036 ata1.00: ATA-6: HTS541080G9AT00, MB4OA60A, max UDMA/100
Jan 21 19:13:41 toby-laptop kernel:     5.229044 ata1.00: 156301488 sectors, multi 16: LBA48 
Jan 21 19:13:41 toby-laptop kernel:     5.229085 ata1.01: ATAPI: HL-DT-ST DVDRAM GSA-4082N, HR02, max UDMA/33
Jan 21 19:13:41 toby-laptop kernel:     5.244936 ata1.00: configured for UDMA/100
Jan 21 19:13:41 toby-laptop kernel:     5.256161 usb 5-3: new high speed USB device using ehci_hcd and address 3
Jan 21 19:13:41 toby-laptop kernel:     5.260527 ata1.01: configured for UDMA/33
Jan 21 19:13:41 toby-laptop kernel:     5.260865 scsi 0:0:0:0: Direct-Access     ATA      HTS541080G9AT00  MB4O PQ: 0 ANSI: 5
Jan 21 19:13:41 toby-laptop kernel:     5.264654 scsi 0:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-4082N HR02 PQ: 0 ANSI: 5
Jan 21 19:13:41 toby-laptop kernel:     5.290041 scsi 0:0:0:0: Attached scsi generic sg0 type 0
Jan 21 19:13:41 toby-laptop kernel:     5.290119 scsi 0:0:1:0: Attached scsi generic sg1 type 5
Jan 21 19:13:41 toby-laptop kernel:     5.325680 Driver 'sd' needs updating - please use bus_type methods
Jan 21 19:13:41 toby-laptop kernel:     5.326684 sd 0:0:0:0: sda 156301488 512-byte hardware sectors (80026 MB)
Jan 21 19:13:41 toby-laptop kernel:     5.326734 sd 0:0:0:0: sda Write Protect is off
Jan 21 19:13:41 toby-laptop kernel:     5.326810 sd 0:0:0:0: sda Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 21 19:13:41 toby-laptop kernel:     5.326952 sd 0:0:0:0: sda 156301488 512-byte hardware sectors (80026 MB)
Jan 21 19:13:41 toby-laptop kernel:     5.326991 sd 0:0:0:0: sda Write Protect is off
Jan 21 19:13:41 toby-laptop kernel:     5.327066 sd 0:0:0:0: sda Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 21 19:13:41 toby-laptop kernel:     5.327074  sda:4Driver 'sr' needs updating - please use bus_type methods
Jan 21 19:13:41 toby-laptop kernel:     5.343592  sda1 sda2 sda3 sda4
Jan 21 19:13:41 toby-laptop kernel:     5.344677 sd 0:0:0:0: sda Attached SCSI disk
Jan 21 19:13:41 toby-laptop kernel:     5.360675 sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jan 21 19:13:41 toby-laptop kernel:     5.360684 Uniform CD-ROM driver Revision: 3.20
Jan 21 19:13:41 toby-laptop kernel:     5.634638 usb 5-3: configuration #1 chosen from 1 choice
Jan 21 19:13:41 toby-laptop kernel:     5.744343 usbcore: registered new interface driver usbhid
Jan 21 19:13:41 toby-laptop kernel:     5.744352 usbhid: v2.6:USB HID core driver
Jan 21 19:13:41 toby-laptop kernel:     5.745391 usbcore: registered new interface driver libusual
Jan 21 19:13:41 toby-laptop kernel:     5.758248 Initializing USB Mass Storage driver...
Jan 21 19:13:41 toby-laptop kernel:     5.805377 PM: Starting manual resume from disk
Jan 21 19:13:41 toby-laptop kernel:     5.874095 kjournald starting.  Commit interval 5 seconds
Jan 21 19:13:41 toby-laptop kernel:     5.874143 EXT3-fs: mounted filesystem with ordered data mode.
Jan 21 19:13:41 toby-laptop kernel:     5.984058 usb 1-1: new low speed USB device using uhci_hcd and address 3
Jan 21 19:13:41 toby-laptop kernel:     6.160497 usb 1-1: configuration #1 chosen from 1 choice
Jan 21 19:13:41 toby-laptop kernel:     6.177880 input: B16_b_02 USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input2
Jan 21 19:13:41 toby-laptop kernel:     6.178378 input,hidraw0: USB HID v1.10 Mouse B16_b_02 USB-PS/2 Optical Mouse on usb-0000:00:1d.0-1
Jan 21 19:13:41 toby-laptop kernel:     6.416117 usb 3-1: new full speed USB device using uhci_hcd and address 2
Jan 21 19:13:41 toby-laptop kernel:     6.586985 usb 3-1: configuration #1 chosen from 1 choice
Jan 21 19:13:41 toby-laptop kernel:     6.589525 scsi2 : SCSI emulation for USB Mass Storage devices
Jan 21 19:13:41 toby-laptop kernel:     6.589917 usbcore: registered new interface driver usb-storage
Jan 21 19:13:41 toby-laptop kernel:     6.589924 USB Mass Storage support registered.
Jan 21 19:13:41 toby-laptop kernel:    11.589034 scsi 2:0:0:0: Direct-Access     Generic  USB Flash Disk   7.76 PQ: 0 ANSI: 2
Jan 21 19:13:41 toby-laptop kernel:    11.590761 sd 2:0:0:0: sdb Attached SCSI removable disk
Jan 21 19:13:41 toby-laptop kernel:    11.590951 sd 2:0:0:0: Attached scsi generic sg2 type 0
Jan 21 19:13:41 toby-laptop kernel:    13.258945 udevd version 124 started
Jan 21 19:13:41 toby-laptop kernel:    14.124300 pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 21 19:13:41 toby-laptop kernel:    14.223416 shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 21 19:13:41 toby-laptop kernel:    14.259297 Linux agpgart interface v0.103
Jan 21 19:13:41 toby-laptop kernel:    14.397162 agpgart-intel 0000:00:00.0: Intel 945GM Chipset
Jan 21 19:13:41 toby-laptop kernel:    14.398134 agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Jan 21 19:13:41 toby-laptop kernel:    14.416941 agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
Jan 21 19:13:41 toby-laptop kernel:    14.587489 input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jan 21 19:13:41 toby-laptop kernel:    14.612135 ACPI: Power Button (FF) PWRF
Jan 21 19:13:41 toby-laptop kernel:    14.612299 input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
Jan 21 19:13:41 toby-laptop kernel:    14.612436 ACPI: Lid Switch LID
Jan 21 19:13:41 toby-laptop kernel:    14.612539 input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
Jan 21 19:13:41 toby-laptop kernel:    14.644048 ACPI: Sleep Button (CM) SLPB
Jan 21 19:13:41 toby-laptop kernel:    14.644185 input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
Jan 21 19:13:41 toby-laptop kernel:    14.676041 ACPI: Power Button (CM) PWRB
Jan 21 19:13:41 toby-laptop kernel:    14.731572 intel_rng: FWH not detected
Jan 21 19:13:41 toby-laptop kernel:    14.932216 iTCO_vendor_support: vendor-support=0
Jan 21 19:13:41 toby-laptop kernel:    15.063406 iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Jan 21 19:13:41 toby-laptop kernel:    15.063642 iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Jan 21 19:13:41 toby-laptop kernel:    15.063855 iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jan 21 19:13:41 toby-laptop kernel:    15.085762 ACPI: WMI: Mapper loaded
Jan 21 19:13:41 toby-laptop kernel:    15.663918 input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input7
Jan 21 19:13:41 toby-laptop kernel:    15.672044 ACPI: Video Device VGA (multi-head: yes  rom: no  post: no)
Jan 21 19:13:41 toby-laptop kernel:    15.672532 input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/input/input8
Jan 21 19:13:41 toby-laptop kernel:    15.696033 ACPI: Video Device GFX0 (multi-head: yes  rom: no  post: no)
Jan 21 19:13:41 toby-laptop kernel:    15.791508 ACPI: AC Adapter ACAD (on-line)
Jan 21 19:13:41 toby-laptop kernel:    15.900150 ACPI: Battery Slot BAT1 (battery absent)
Jan 21 19:13:41 toby-laptop kernel:    16.349573 HDA Intel 0000:00:1b.0: PCI INT A - GSI 22 (level, low) - IRQ 22
Jan 21 19:13:41 toby-laptop kernel:    16.615624 Yenta: CardBus bridge found at 0000:06:04.0 1025:0090
Jan 21 19:13:41 toby-laptop kernel:    16.615663 Yenta: Using CSCINT to route CSC interrupts to PCI
Jan 21 19:13:41 toby-laptop kernel:    16.615668 Yenta: Routing CardBus interrupts to PCI
Jan 21 19:13:41 toby-laptop kernel:    16.615678 Yenta TI: socket 0000:06:04.0, mfunc 0x00111c12, devctl 0x44
Jan 21 19:13:41 toby-laptop kernel:    16.849842 Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
Jan 21 19:13:41 toby-laptop kernel:    16.849850 Socket status: 30000006
Jan 21 19:13:41 toby-laptop kernel:    16.849857 Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
Jan 21 19:13:41 toby-laptop kernel:    16.849869 pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
Jan 21 19:13:41 toby-laptop kernel:    16.849875 cs: IO port probe 0x2000-0x2fff: clean.
Jan 21 19:13:41 toby-laptop kernel:    16.850294 pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd00fffff
Jan 21 19:13:41 toby-laptop kernel:    16.850300 pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
Jan 21 19:13:41 toby-laptop kernel:    17.007299 input: PC Speaker as /devices/platform/pcspkr/input/input9
Jan 21 19:13:41 toby-laptop kernel:    17.130000 iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Jan 21 19:13:41 toby-laptop kernel:    17.130008 iwl3945: Copyright(c) 2003-2008 Intel Corporation
Jan 21 19:13:41 toby-laptop kernel:    17.130109 iwl3945 0000:05:00.0: PCI INT A - GSI 19 (level, low) - IRQ 19
Jan 21 19:13:41 toby-laptop kernel:    17.130157 iwl3945: Detected Intel Wireless WiFi Link 3945ABG
Jan 21 19:13:41 toby-laptop kernel:    17.263249 eth1: register 'cdc_ether' at usb-0000:00:1d.2-1, CDC Ethernet Device, 00:04:0e:7b:7b:34
Jan 21 19:13:41 toby-laptop kernel:    17.263291 usbcore: registered new interface driver cdc_ether
Jan 21 19:13:41 toby-laptop kernel:    17.359644 iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
Jan 21 19:13:41 toby-laptop kernel:    17.821784 acer-wmi: Acer Laptop ACPI-WMI Extras
Jan 21 19:13:41 toby-laptop kernel:    17.871482 iwl3945 0000:05:00.0: PCI INT A disabled
Jan 21 19:13:41 toby-laptop kernel:    17.952775 Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
Jan 21 19:13:41 toby-laptop kernel:    17.982236 input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
Jan 21 19:13:41 toby-laptop kernel:    18.026700 Registered led device: acer-wmi::mail
Jan 21 19:13:41 toby-laptop kernel:    19.245404 cs: IO port probe 0x100-0x3af: clean.
Jan 21 19:13:41 toby-laptop kernel:    19.247677 cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Jan 21 19:13:41 toby-laptop kernel:    19.248711 cs: IO port probe 0x820-0x8ff: clean.
Jan 21 19:13:41 toby-laptop kernel:    19.249524 cs: IO port probe 0xc00-0xcf7: clean.
Jan 21 19:13:41 toby-laptop kernel:    19.250610 cs: IO port probe 0xa00-0xaff: clean.
Jan 21 19:13:41 toby-laptop kernel:    20.309323 lp: driver loaded but no devices found
Jan 21 19:13:41 toby-laptop kernel:    20.628990 Adding 1220900k swap on /dev/sda1.  Priority:-1 extents:1 across:1220900k
Jan 21 19:13:41 toby-laptop kernel:    21.214238 EXT3 FS on sda3, internal journal
Jan 21 19:13:41 toby-laptop kernel:    22.198690 kjournald starting.  Commit interval 5 seconds
Jan 21 19:13:41 toby-laptop kernel:    22.199109 EXT3 FS on sda4, internal journal
Jan 21 19:13:41 toby-laptop kernel:    22.199120 EXT3-fs: mounted filesystem with ordered data mode.
Jan 21 19:13:41 toby-laptop kernel:    22.577843 type=1505 audit(1232561619.489:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4286
Jan 21 19:13:41 toby-laptop kernel:    22.945210 type=1505 audit(1232561619.858:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4291
Jan 21 19:13:41 toby-laptop kernel:    22.945549 type=1505 audit(1232561619.858:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4291
Jan 21 19:13:41 toby-laptop kernel:    23.137075 ip_tables: (C) 2000-2006 Netfilter Core Team
Jan 21 19:13:42 toby-laptop kernel:    25.139989 warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Jan 21 19:13:42 toby-laptop kernel:    25.217133 apm: BIOS not found.
Jan 21 19:13:42 toby-laptop kernel:    25.391114 ppdev: user-space parallel port driver
Jan 21 19:13:47 toby-laptop kernel:    30.756065 ACPI: EC: missing confirmations, switch off interrupt mode.
Jan 21 19:13:48 toby-laptop kernel:    31.268360 iwl3945 0000:05:00.0: PCI INT A - GSI 19 (level, low) - IRQ 19
Jan 21 19:13:48 toby-laptop kernel:    31.268859 firmware: requesting iwlwifi-3945-1.ucode
Jan 21 19:13:48 toby-laptop kernel:    31.280045 ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for EmbeddedControl 20080609
Jan 21 19:13:48 toby-laptop kernel:    31.280074 ACPI Error (psparse-0530): Method parse/execution failed \_SB_.PCI0.LPCB.ACAD._PSR (Node de819ee8), AE_TIME
Jan 21 19:13:48 toby-laptop kernel:    31.280173 ACPI Exception (ac-0136): AE_TIME, Error reading AC Adapter state 20080609
Jan 21 19:13:48 toby-laptop kernel:    31.287224 drm Initialized drm 1.1.0 20060810
Jan 21 19:13:48 toby-laptop kernel:    31.316232 pci 0000:00:02.0: PCI INT A - GSI 16 (level, low) - IRQ 16
Jan 21 19:13:48 toby-laptop kernel:    31.319770 drm Initialized i915 1.6.0 20060119 on minor 0
Jan 21 19:13:48 toby-laptop kernel:    31.447414 Registered led device: iwl-phy0:radio
Jan 21 19:13:48 toby-laptop kernel:    31.448326 Registered led device: iwl-phy0:assoc
Jan 21 19:13:48 toby-laptop kernel:    31.449132 Registered led device: iwl-phy0:RX
Jan 21 19:13:48 toby-laptop kernel:    31.449887 Registered led device: iwl-phy0:TX
Jan 21 19:13:48 toby-laptop kernel:    31.639185 NET: Registered protocol family 17
Jan 21 19:13:51 toby-laptop kernel:    34.337638 NET: Registered protocol family 10
Jan 21 19:13:51 toby-laptop kernel:    34.338692 lo: Disabled Privacy Extensions
Jan 21 19:13:51 toby-laptop kernel:    34.340900 ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 21 19:13:51 toby-laptop kernel:    34.342949 ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 21 19:14:03 toby-laptop pulseaudio5601: ltdl-bind-now.c: Failed to find original dlopen loader.
Jan 21 19:14:03 toby-laptop pulseaudio5603: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jan 21 19:14:03 toby-laptop pulseaudio5603: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jan 21 19:15:28 toby-laptop kernel:   131.109064 CE: hpet increasing min_delta_ns to 15000 nsec

---

### Post by icanfly0307 on 2009-01-21
Hmmm. Would backing up the files and reformatting the flash drive be an option? This time, make sure that you format it as FAT32. NTFS isn't really that reliable in Ubuntu seeing that it's a Windows filesystem.

---

### Post by persofi on 2009-01-21
Yes it would, it is brand new and has no important files on it.

But how can I reformat it if neither Ubuntu nor Windows seems to recognize it?

---

### Post by icanfly0307 on 2009-01-21
Okay, first, if you have another computer in your house, try using it to detect your flash drive. Then, boot into Windows, and plug in your flash drive and when it comes up as E:\ or whatever the letter is, right click on it in My Computer. Select Format and follow on from there. Remember, format it as FAT32 and not NTFS as you have a greater chance of getting it to work as FAT32. Good Luck! :)

---

### Post by persofi on 2009-01-25
Hi,

thx for your help. Actually it seems to work on only 1 of 4 of my usb ports running Windows. I reformatted it in FAT32, but under Ubuntu it still doesnt get recognized. How can that be?

The strange thing is, that the stick must have worked flawlessly once under Ubuntu, since when I opened it in Windows, the files I copied onto in in Ubuntu where there and working...

---

