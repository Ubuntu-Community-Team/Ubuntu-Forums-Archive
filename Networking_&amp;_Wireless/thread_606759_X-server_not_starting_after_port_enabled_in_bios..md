---
title: "X-server not starting after port enabled in bios."
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by mikeescott on 2007-11-08
My motherboard has dual onboard gigabit ethernet ports. I have always had one enabled in bios for the crossover cable connected to my wifes computer and the second disabled in bios. I finally found a high speed ISP that services my house. I have no switch or router and would just like to plug the high speed into the second port on my mb. I went into bios and enabled the second port, but x-server will not start after 3 tries. I went back in and disabled it again and is starts up just fine. I unplugged the crossover and plugged the high speed in there and it works fine. Do I need to go into something and change something to get the second port to work before I enable it in bios?

---

### Post by Lambert on 2007-11-08
when you have the port enabled for the second nic, run dmesg or check out syslog file (/var/log/sys.log) for any errors.

---

### Post by mikeescott on 2007-11-08
> **Lambert said:**
> when you have the port enabled for the second nic, run dmesg or check out syslog file (/var/log/sys.log) for any errors.

While in recovery mode, how would I save the dmesg file to view later? Below is a copy of my syslog file. It's kinda long. I am having the same problem in Feisty 64 bit as well.


```


Nov  8 17:28:19 uue16 syslogd 1.4.1#21ubuntu3: restart.
Nov  8 17:28:19 uue16 anacron[8679]: Job `cron.daily' terminated
Nov  8 17:28:19 uue16 anacron[8679]: Normal exit (1 job run)
Nov  8 17:32:05 uue16 ntfs-3g[9116]: Unmounting /dev/sdk1 (My Documents) 
Nov  8 17:32:05 uue16 hald: unmounted /dev/sdk1 from '/media/My Documents' on behalf of uid 1000
Nov  8 17:32:05 uue16 hald: unmounted /dev/sdf1 from '/media/USB' on behalf of uid 1000
Nov  8 17:32:05 uue16 init: tty4 main process (6308) killed by TERM signal
Nov  8 17:32:05 uue16 init: tty5 main process (6309) killed by TERM signal
Nov  8 17:32:05 uue16 init: tty3 main process (6313) killed by TERM signal
Nov  8 17:32:05 uue16 init: tty1 main process (6315) killed by TERM signal
Nov  8 17:32:05 uue16 init: tty2 main process (6311) killed by TERM signal
Nov  8 17:32:05 uue16 init: tty6 main process (6316) killed by TERM signal
Nov  8 17:32:06 uue16 avahi-daemon[8246]: Got SIGTERM, quitting.
Nov  8 17:32:06 uue16 avahi-daemon[8246]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.20.253.
Nov  8 17:32:08 uue16 atieventsd[7564]: Closing acpid connection 
Nov  8 17:32:08 uue16 atieventsd[7564]: Closing control socket 
Nov  8 17:32:08 uue16 atieventsd[7564]: ATI External Events Daemon shutting down 
Nov  8 17:32:09 uue16 rpc.statd[6129]: Caught signal 15, un-registering and exiting.
Nov  8 17:32:14 uue16 kernel: [  673.182828] device eth0 left promiscuous mode
Nov  8 17:32:14 uue16 kernel: [  673.182841] audit(1194564734.491:7): dev=eth0 prom=0 old_prom=256 auid=4294967295
Nov  8 17:32:14 uue16 mysqld[7382]: 071108 17:32:14 [Note] /usr/sbin/mysqld: Normal shutdown
Nov  8 17:32:14 uue16 mysqld[7382]: 
Nov  8 17:32:14 uue16 mysqld[7382]: 071108 17:32:14  InnoDB: Starting shutdown...
Nov  8 17:32:17 uue16 mysqld[7382]: 071108 17:32:17  InnoDB: Shutdown completed; log sequence number 0 43655
Nov  8 17:32:17 uue16 mysqld[7382]: 071108 17:32:17 [Note] /usr/sbin/mysqld: Shutdown complete
Nov  8 17:32:17 uue16 mysqld[7382]: 
Nov  8 17:32:17 uue16 mysqld_safe[9954]: ended
Nov  8 17:32:20 uue16 mountd[7881]: Caught signal 15, un-registering and exiting.
Nov  8 17:32:20 uue16 kernel: [  679.326548] nfsd: last server has exited
Nov  8 17:32:20 uue16 kernel: [  679.326553] nfsd: unexporting all filesystems
Nov  8 17:32:20 uue16 exiting on signal 15
Nov  8 17:34:06 uue16 syslogd 1.4.1#21ubuntu3: restart.
Nov  8 17:34:06 uue16 kernel: Inspecting /boot/System.map-2.6.22-14-generic
Nov  8 17:34:07 uue16 kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Nov  8 17:34:07 uue16 kernel: Symbols match kernel version 2.6.22.
Nov  8 17:34:07 uue16 kernel: No module symbols loaded - kernel modules not enabled. 
Nov  8 17:34:07 uue16 kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Nov  8 17:34:07 uue16 kernel: [    0.000000] BIOS-provided physical RAM map:
Nov  8 17:34:07 uue16 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov  8 17:34:07 uue16 kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov  8 17:34:07 uue16 kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Nov  8 17:34:07 uue16 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff80000 (usable)
Nov  8 17:34:07 uue16 kernel: [    0.000000]  BIOS-e820: 00000000bff80000 - 00000000bff8e000 (ACPI data)
Nov  8 17:34:07 uue16 kernel: [    0.000000]  BIOS-e820: 00000000bff8e000 - 00000000bffe0000 (ACPI NVS)
Nov  8 17:34:07 uue16 kernel: [    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
Nov  8 17:34:07 uue16 kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Nov  8 17:34:07 uue16 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Nov  8 17:34:07 uue16 kernel: [    0.000000] Warning only 4GB will be used.
Nov  8 17:34:07 uue16 kernel: [    0.000000] Use a PAE enabled kernel.
Nov  8 17:34:07 uue16 kernel: [    0.000000] 3200MB HIGHMEM available.
Nov  8 17:34:07 uue16 kernel: [    0.000000] 896MB LOWMEM available.
Nov  8 17:34:07 uue16 kernel: [    0.000000] found SMP MP-table at 000ff780
Nov  8 17:34:07 uue16 kernel: [    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
Nov  8 17:34:07 uue16 kernel: [    0.000000] Zone PFN ranges:
Nov  8 17:34:07 uue16 kernel: [    0.000000]   DMA             0 ->     4096
Nov  8 17:34:07 uue16 kernel: [    0.000000]   Normal       4096 ->   229376
Nov  8 17:34:07 uue16 kernel: [    0.000000]   HighMem    229376 ->  1048576
Nov  8 17:34:07 uue16 kernel: [    0.000000] early_node_map[1] active PFN ranges
Nov  8 17:34:07 uue16 kernel: [    0.000000]     0:        0 ->  1048576
Nov  8 17:34:07 uue16 kernel: [    0.000000] On node 0 totalpages: 1048576
Nov  8 17:34:07 uue16 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov  8 17:34:07 uue16 kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov  8 17:34:07 uue16 kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Nov  8 17:34:07 uue16 kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Nov  8 17:34:07 uue16 kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Nov  8 17:34:07 uue16 kernel: [    0.000000]   HighMem zone: 6400 pages used for memmap
Nov  8 17:34:07 uue16 kernel: [    0.000000]   HighMem zone: 812800 pages, LIFO batch:31
Nov  8 17:34:07 uue16 kernel: [    0.000000] DMI 2.3 present.
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FA740 checksum 0
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: RSDP 000FA740, 0024 (r2 ACPIAM)
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: XSDT BFF80100, 0044 (r1 A M I  OEMXSDT   7000610 MSFT       97)
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: FACP BFF80290, 00F4 (r3 A M I  OEMFACP   7000610 MSFT       97)
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: DSDT BFF80410, 84CF (r1  A0411 A0411000        0 INTL  2002026)
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: FACS BFF8E000, 0040
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: APIC BFF80390, 0080 (r1 A M I  OEMAPIC   7000610 MSFT       97)
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: OEMB BFF8E040, 0066 (r1 A M I  AMI_OEM   7000610 MSFT       97)
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: MCFG BFF888E0, 003C (r1 A M I  OEMMCFG   7000610 MSFT       97)
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Nov  8 17:34:07 uue16 kernel: [    0.000000] Processor #0 15:6 APIC version 20
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Nov  8 17:34:07 uue16 kernel: [    0.000000] Processor #2 15:6 APIC version 20
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
Nov  8 17:34:07 uue16 kernel: [    0.000000] Processor #1 15:6 APIC version 20
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Nov  8 17:34:07 uue16 kernel: [    0.000000] Processor #3 15:6 APIC version 20
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Nov  8 17:34:07 uue16 kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov  8 17:34:07 uue16 kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov  8 17:34:07 uue16 kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov  8 17:34:07 uue16 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov  8 17:34:07 uue16 kernel: [    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3fb00000)
Nov  8 17:34:07 uue16 kernel: [    0.000000] Built 1 zonelists.  Total pages: 1040384
Nov  8 17:34:07 uue16 kernel: [    0.000000] Kernel command line: root=UUID=e8bee423-266f-49eb-8f99-a75d19ffa386 ro quiet splash
Nov  8 17:34:07 uue16 kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Nov  8 17:34:07 uue16 kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Nov  8 17:34:07 uue16 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov  8 17:34:07 uue16 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov  8 17:34:07 uue16 kernel: [    0.000000] Initializing CPU#0
Nov  8 17:34:07 uue16 kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov  8 17:34:07 uue16 kernel: [    0.000000] Detected 3472.833 MHz processor.
Nov  8 17:34:07 uue16 kernel: [   25.978912] Console: colour VGA+ 80x25
Nov  8 17:34:07 uue16 kernel: [   25.979120] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov  8 17:34:07 uue16 kernel: [   25.979380] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov  8 17:34:07 uue16 kernel: [   26.145087] Memory: 3099116k/4194304k available (2015k kernel code, 44952k reserved, 916k data, 364k init, 2227712k highmem)
Nov  8 17:34:07 uue16 kernel: [   26.145095] virtual kernel memory layout:
Nov  8 17:34:07 uue16 kernel: [   26.145096]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Nov  8 17:34:07 uue16 kernel: [   26.145097]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov  8 17:34:07 uue16 kernel: [   26.145098]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Nov  8 17:34:07 uue16 kernel: [   26.145099]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Nov  8 17:34:07 uue16 kernel: [   26.145100]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Nov  8 17:34:07 uue16 kernel: [   26.145101]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Nov  8 17:34:07 uue16 kernel: [   26.145101]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Nov  8 17:34:07 uue16 kernel: [   26.145104] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov  8 17:34:07 uue16 kernel: [   26.145135] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
Nov  8 17:34:07 uue16 kernel: [   26.224921] Calibrating delay using timer specific routine.. 6951.56 BogoMIPS (lpj=13903138)
Nov  8 17:34:07 uue16 kernel: [   26.224942] Security Framework v1.0.0 initialized
Nov  8 17:34:07 uue16 kernel: [   26.224946] SELinux:  Disabled at boot.
Nov  8 17:34:07 uue16 kernel: [   26.224957] Mount-cache hash table entries: 512
Nov  8 17:34:07 uue16 kernel: [   26.225058] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
Nov  8 17:34:07 uue16 kernel: [   26.225065] monitor/mwait feature present.
Nov  8 17:34:07 uue16 kernel: [   26.225067] using mwait in idle threads.
Nov  8 17:34:07 uue16 kernel: [   26.225073] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov  8 17:34:07 uue16 kernel: [   26.225075] CPU: L2 cache: 2048K
Nov  8 17:34:07 uue16 kernel: [   26.225077] CPU: Physical Processor ID: 0
Nov  8 17:34:07 uue16 kernel: [   26.225079] CPU: Processor Core ID: 0
Nov  8 17:34:07 uue16 kernel: [   26.225081] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e43d 00000000 00000001
Nov  8 17:34:07 uue16 kernel: [   26.225090] Compat vDSO mapped to ffffe000.
Nov  8 17:34:07 uue16 kernel: [   26.225102] Checking 'hlt' instruction... OK.
Nov  8 17:34:07 uue16 kernel: [   26.240951] SMP alternatives: switching to UP code
Nov  8 17:34:07 uue16 kernel: [   26.241304] Early unpacking initramfs... done
Nov  8 17:34:07 uue16 kernel: [   26.493261] ACPI: Core revision 20070126
Nov  8 17:34:07 uue16 kernel: [   26.493314] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov  8 17:34:07 uue16 kernel: [   26.497196] CPU0: Intel(R) Pentium(R) D CPU 3.46GHz stepping 02
Nov  8 17:34:07 uue16 kernel: [   26.497212] SMP alternatives: switching to SMP code
Nov  8 17:34:07 uue16 kernel: [   26.497282] Booting processor 1/1 eip 3000
Nov  8 17:34:07 uue16 kernel: [   26.507464] Initializing CPU#1
Nov  8 17:34:07 uue16 kernel: [   26.587855] Calibrating delay using timer specific routine.. 6945.74 BogoMIPS (lpj=13891499)
Nov  8 17:34:07 uue16 kernel: [   26.587863] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
Nov  8 17:34:07 uue16 kernel: [   26.587869] monitor/mwait feature present.
Nov  8 17:34:07 uue16 kernel: [   26.587875] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov  8 17:34:07 uue16 kernel: [   26.587877] CPU: L2 cache: 2048K
Nov  8 17:34:07 uue16 kernel: [   26.587880] CPU: Physical Processor ID: 0
Nov  8 17:34:07 uue16 kernel: [   26.587881] CPU: Processor Core ID: 0
Nov  8 17:34:07 uue16 kernel: [   26.587883] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e43d 00000000 00000001
Nov  8 17:34:07 uue16 kernel: [   26.588362] CPU1: Intel(R) Pentium(R) D CPU 3.46GHz stepping 02
Nov  8 17:34:07 uue16 kernel: [   26.588384] SMP alternatives: switching to SMP code
Nov  8 17:34:07 uue16 kernel: [   26.588454] Booting processor 2/2 eip 3000
Nov  8 17:34:07 uue16 kernel: [   26.598659] Initializing CPU#2
Nov  8 17:34:07 uue16 kernel: [   26.675597] Calibrating delay using timer specific routine.. 6945.77 BogoMIPS (lpj=13891554)
Nov  8 17:34:07 uue16 kernel: [   26.675604] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
Nov  8 17:34:07 uue16 kernel: [   26.675609] monitor/mwait feature present.
Nov  8 17:34:07 uue16 kernel: [   26.675614] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov  8 17:34:07 uue16 kernel: [   26.675616] CPU: L2 cache: 2048K
Nov  8 17:34:07 uue16 kernel: [   26.675617] CPU: Physical Processor ID: 0
Nov  8 17:34:07 uue16 kernel: [   26.675619] CPU: Processor Core ID: 1
Nov  8 17:34:07 uue16 kernel: [   26.675620] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e43d 00000000 00000001
Nov  8 17:34:07 uue16 kernel: [   26.676059] CPU2: Intel(R) Pentium(R) D CPU 3.46GHz stepping 02
Nov  8 17:34:07 uue16 kernel: [   26.676072] SMP alternatives: switching to SMP code
Nov  8 17:34:07 uue16 kernel: [   26.676088] Booting processor 3/3 eip 3000
Nov  8 17:34:07 uue16 kernel: [   26.686270] Initializing CPU#3
Nov  8 17:34:07 uue16 kernel: [   26.763340] Calibrating delay using timer specific routine.. 6945.75 BogoMIPS (lpj=13891512)
Nov  8 17:34:07 uue16 kernel: [   26.763348] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
Nov  8 17:34:07 uue16 kernel: [   26.763354] monitor/mwait feature present.
Nov  8 17:34:07 uue16 kernel: [   26.763359] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov  8 17:34:07 uue16 kernel: [   26.763362] CPU: L2 cache: 2048K
Nov  8 17:34:07 uue16 kernel: [   26.763364] CPU: Physical Processor ID: 0
Nov  8 17:34:07 uue16 kernel: [   26.763366] CPU: Processor Core ID: 1
Nov  8 17:34:07 uue16 kernel: [   26.763368] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e43d 00000000 00000001
Nov  8 17:34:07 uue16 kernel: [   26.763843] CPU3: Intel(R) Pentium(R) D CPU 3.46GHz stepping 02
Nov  8 17:34:07 uue16 kernel: [   26.763876] Total of 4 processors activated (27788.85 BogoMIPS).
Nov  8 17:34:07 uue16 kernel: [   26.764023] ENABLING IO-APIC IRQs
Nov  8 17:34:07 uue16 kernel: [   26.764198] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov  8 17:34:07 uue16 kernel: [   26.910997] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Nov  8 17:34:07 uue16 kernel: [   26.930980] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Nov  8 17:34:07 uue16 kernel: [   26.950969] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Nov  8 17:34:07 uue16 kernel: [   26.970929] Brought up 4 CPUs
Nov  8 17:34:07 uue16 kernel: [   27.215660] migration_cost=108,888
Nov  8 17:34:07 uue16 kernel: [   27.215825] Booting paravirtualized kernel on bare hardware
Nov  8 17:34:07 uue16 kernel: [   27.215885] Time: 23:33:49  Date: 10/08/107
Nov  8 17:34:07 uue16 kernel: [   27.215906] NET: Registered protocol family 16
Nov  8 17:34:07 uue16 kernel: [   27.215980] EISA bus registered
Nov  8 17:34:07 uue16 kernel: [   27.215985] ACPI: bus type pci registered
Nov  8 17:34:07 uue16 kernel: [   27.216066] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
Nov  8 17:34:07 uue16 kernel: [   27.216068] PCI: Using configuration type 1
Nov  8 17:34:07 uue16 kernel: [   27.216070] Setting up standard PCI resources
Nov  8 17:34:07 uue16 kernel: [   27.227890] ACPI: EC: Look up EC in DSDT
Nov  8 17:34:07 uue16 kernel: [   27.235648] ACPI: Interpreter enabled
Nov  8 17:34:07 uue16 kernel: [   27.235652] ACPI: (supports S0 S1 S3 S4 S5)
Nov  8 17:34:07 uue16 kernel: [   27.235673] ACPI: Using IOAPIC for interrupt routing
Nov  8 17:34:07 uue16 kernel: [   27.244022] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov  8 17:34:07 uue16 kernel: [   27.244035] PCI: Probing PCI hardware (bus 00)
Nov  8 17:34:07 uue16 kernel: [   27.244600] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Nov  8 17:34:07 uue16 kernel: [   27.244604] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
Nov  8 17:34:07 uue16 kernel: [   27.245776] PCI: Transparent bridge - 0000:00:1e.0
Nov  8 17:34:07 uue16 kernel: [   27.245852] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov  8 17:34:07 uue16 kernel: [   27.246003] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Nov  8 17:34:07 uue16 kernel: [   27.246089] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
Nov  8 17:34:07 uue16 kernel: [   27.246203] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
Nov  8 17:34:07 uue16 kernel: [   27.246282] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
Nov  8 17:34:07 uue16 kernel: [   27.246348] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
Nov  8 17:34:07 uue16 kernel: [   27.246414] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
Nov  8 17:34:07 uue16 kernel: [   27.249390] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Nov  8 17:34:07 uue16 kernel: [   27.249502] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Nov  8 17:34:07 uue16 kernel: [   27.249612] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
Nov  8 17:34:07 uue16 kernel: [   27.249721] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Nov  8 17:34:07 uue16 kernel: [   27.249830] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 *14 15)
Nov  8 17:34:07 uue16 kernel: [   27.249945] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Nov  8 17:34:07 uue16 kernel: [   27.250076] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Nov  8 17:34:07 uue16 kernel: [   27.250185] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Nov  8 17:34:07 uue16 kernel: [   27.250288] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov  8 17:34:07 uue16 kernel: [   27.250298] pnp: PnP ACPI init
Nov  8 17:34:07 uue16 kernel: [   27.250306] ACPI: bus type pnp registered
Nov  8 17:34:07 uue16 kernel: [   27.256039] pnp: PnP ACPI: found 19 devices
Nov  8 17:34:07 uue16 kernel: [   27.256041] ACPI: ACPI bus type pnp unregistered
Nov  8 17:34:07 uue16 kernel: [   27.256045] PnPBIOS: Disabled by ACPI PNP
Nov  8 17:34:07 uue16 kernel: [   27.256095] PCI: Using ACPI for IRQ routing
Nov  8 17:34:07 uue16 kernel: [   27.256099] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov  8 17:34:07 uue16 kernel: [   27.270624] NET: Registered protocol family 8
Nov  8 17:34:07 uue16 kernel: [   27.270626] NET: Registered protocol family 20
Nov  8 17:34:07 uue16 kernel: [   27.270682] pnp: 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
Nov  8 17:34:07 uue16 kernel: [   27.270692] pnp: 00:08: ioport range 0x290-0x297 has been reserved
Nov  8 17:34:07 uue16 kernel: [   27.270697] pnp: 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
Nov  8 17:34:07 uue16 kernel: [   27.270700] pnp: 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
Nov  8 17:34:07 uue16 kernel: [   27.270703] pnp: 00:09: iomem range 0xfed50000-0xfed8ffff has been reserved
Nov  8 17:34:07 uue16 kernel: [   27.270706] pnp: 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
Nov  8 17:34:07 uue16 kernel: [   27.270710] pnp: 00:0a: ioport range 0x3f6-0x3f6 has been reserved
Nov  8 17:34:07 uue16 kernel: [   27.270717] pnp: 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
Nov  8 17:34:07 uue16 kernel: [   27.270720] pnp: 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
Nov  8 17:34:07 uue16 kernel: [   27.270726] pnp: 00:11: iomem range 0xf0000000-0xf3ffffff has been reserved
Nov  8 17:34:07 uue16 kernel: [   27.270733] pnp: 00:12: iomem range 0x0-0x9ffff could not be reserved
Nov  8 17:34:07 uue16 kernel: [   27.270736] pnp: 00:12: iomem range 0xc0000-0xdffff could not be reserved
Nov  8 17:34:07 uue16 kernel: [   27.270738] pnp: 00:12: iomem range 0xe0000-0xfffff could not be reserved
Nov  8 17:34:07 uue16 kernel: [   27.270741] pnp: 00:12: iomem range 0x100000-0xbfffffff could not be reserved
Nov  8 17:34:07 uue16 kernel: [   27.273858] Time: tsc clocksource has been installed.
Nov  8 17:34:07 uue16 kernel: [   27.300983] PCI: Bridge: 0000:00:01.0
Nov  8 17:34:07 uue16 kernel: [   27.300986]   IO window: c000-cfff
Nov  8 17:34:07 uue16 kernel: [   27.300990]   MEM window: fea00000-feafffff
Nov  8 17:34:07 uue16 kernel: [   27.300993]   PREFETCH window: cff00000-efefffff
Nov  8 17:34:07 uue16 kernel: [   27.300996] PCI: Bridge: 0000:00:1c.0
Nov  8 17:34:07 uue16 kernel: [   27.300998]   IO window: disabled.
Nov  8 17:34:07 uue16 kernel: [   27.301002]   MEM window: disabled.
Nov  8 17:34:07 uue16 kernel: [   27.301006]   PREFETCH window: cfe00000-cfefffff
Nov  8 17:34:07 uue16 kernel: [   27.301010] PCI: Bridge: 0000:00:1c.3
Nov  8 17:34:07 uue16 kernel: [   27.301013]   IO window: b000-bfff
Nov  8 17:34:07 uue16 kernel: [   27.301018]   MEM window: fe900000-fe9fffff
Nov  8 17:34:07 uue16 kernel: [   27.301021]   PREFETCH window: disabled.
Nov  8 17:34:07 uue16 kernel: [   27.301026] PCI: Bridge: 0000:00:1c.4
Nov  8 17:34:07 uue16 kernel: [   27.301028]   IO window: a000-afff
Nov  8 17:34:07 uue16 kernel: [   27.301033]   MEM window: fe800000-fe8fffff
Nov  8 17:34:07 uue16 kernel: [   27.301036]   PREFETCH window: disabled.
Nov  8 17:34:07 uue16 kernel: [   27.301041] PCI: Bridge: 0000:00:1c.5
Nov  8 17:34:07 uue16 kernel: [   27.301043]   IO window: 9000-9fff
Nov  8 17:34:07 uue16 kernel: [   27.301048]   MEM window: fe700000-fe7fffff
Nov  8 17:34:07 uue16 kernel: [   27.301051]   PREFETCH window: disabled.
Nov  8 17:34:07 uue16 kernel: [   27.301056] PCI: Bridge: 0000:00:1e.0
Nov  8 17:34:07 uue16 kernel: [   27.301059]   IO window: 8000-8fff
Nov  8 17:34:07 uue16 kernel: [   27.301064]   MEM window: f6200000-fe6fffff
Nov  8 17:34:07 uue16 kernel: [   27.301067]   PREFETCH window: disabled.
Nov  8 17:34:07 uue16 kernel: [   27.301082] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov  8 17:34:07 uue16 kernel: [   27.301088] PCI: Setting latency timer of device 0000:00:01.0 to 64
Nov  8 17:34:07 uue16 kernel: [   27.301104] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov  8 17:34:07 uue16 kernel: [   27.301109] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Nov  8 17:34:07 uue16 kernel: [   27.301126] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Nov  8 17:34:07 uue16 kernel: [   27.301131] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Nov  8 17:34:07 uue16 kernel: [   27.301148] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
Nov  8 17:34:07 uue16 kernel: [   27.301153] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Nov  8 17:34:07 uue16 kernel: [   27.301170] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 18
Nov  8 17:34:07 uue16 kernel: [   27.301175] PCI: Setting latency timer of device 0000:00:1c.5 to 64
Nov  8 17:34:07 uue16 kernel: [   27.301185] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Nov  8 17:34:07 uue16 kernel: [   27.301194] NET: Registered protocol family 2
Nov  8 17:34:07 uue16 kernel: [   27.337692] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov  8 17:34:07 uue16 kernel: [   27.337740] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Nov  8 17:34:07 uue16 kernel: [   27.338482] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov  8 17:34:07 uue16 kernel: [   27.338730] TCP: Hash tables configured (established 131072 bind 65536)
Nov  8 17:34:07 uue16 kernel: [   27.338732] TCP reno registered
Nov  8 17:34:07 uue16 kernel: [   27.349775] checking if image is initramfs... it is
Nov  8 17:34:07 uue16 kernel: [   27.796419] Switched to high resolution mode on CPU 1
Nov  8 17:34:07 uue16 kernel: [   27.796449] Switched to high resolution mode on CPU 2
Nov  8 17:34:07 uue16 kernel: [   27.796493] Switched to high resolution mode on CPU 3
Nov  8 17:34:07 uue16 kernel: [   27.800311] Switched to high resolution mode on CPU 0
Nov  8 17:34:07 uue16 kernel: [   27.845656] Freeing initrd memory: 7343k freed
Nov  8 17:34:07 uue16 kernel: [   27.846349] audit: initializing netlink socket (disabled)
Nov  8 17:34:07 uue16 kernel: [   27.846361] audit(1194564829.480:1): initialized
Nov  8 17:34:07 uue16 kernel: [   27.846454] highmem bounce pool size: 64 pages
Nov  8 17:34:07 uue16 kernel: [   27.848514] VFS: Disk quotas dquot_6.5.1
Nov  8 17:34:07 uue16 kernel: [   27.848562] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov  8 17:34:07 uue16 kernel: [   27.848644] io scheduler noop registered
Nov  8 17:34:07 uue16 kernel: [   27.848646] io scheduler anticipatory registered
Nov  8 17:34:07 uue16 kernel: [   27.848648] io scheduler deadline registered
Nov  8 17:34:07 uue16 kernel: [   27.848663] io scheduler cfq registered (default)
Nov  8 17:34:07 uue16 kernel: [   27.876056] Boot video device is 0000:06:00.0
Nov  8 17:34:07 uue16 kernel: [   27.876193] PCI: Setting latency timer of device 0000:00:01.0 to 64
Nov  8 17:34:07 uue16 kernel: [   27.876229] assign_interrupt_mode Found MSI capability
Nov  8 17:34:07 uue16 kernel: [   27.876232] Allocate Port Service[0000:00:01.0:pcie00]
Nov  8 17:34:07 uue16 kernel: [   27.876306] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Nov  8 17:34:07 uue16 kernel: [   27.876347] assign_interrupt_mode Found MSI capability
Nov  8 17:34:07 uue16 kernel: [   27.876349] Allocate Port Service[0000:00:1c.0:pcie00]
Nov  8 17:34:07 uue16 kernel: [   27.876383] Allocate Port Service[0000:00:1c.0:pcie02]
Nov  8 17:34:07 uue16 kernel: [   27.876463] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Nov  8 17:34:07 uue16 kernel: [   27.876503] assign_interrupt_mode Found MSI capability
Nov  8 17:34:07 uue16 kernel: [   27.876506] Allocate Port Service[0000:00:1c.3:pcie00]
Nov  8 17:34:07 uue16 kernel: [   27.876585] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Nov  8 17:34:07 uue16 kernel: [   27.876625] assign_interrupt_mode Found MSI capability
Nov  8 17:34:07 uue16 kernel: [   27.876627] Allocate Port Service[0000:00:1c.4:pcie00]
Nov  8 17:34:07 uue16 kernel: [   27.876710] PCI: Setting latency timer of device 0000:00:1c.5 to 64
Nov  8 17:34:07 uue16 kernel: [   27.876750] assign_interrupt_mode Found MSI capability
Nov  8 17:34:07 uue16 kernel: [   27.876752] Allocate Port Service[0000:00:1c.5:pcie00]
Nov  8 17:34:07 uue16 kernel: [   27.876895] isapnp: Scanning for PnP cards...
Nov  8 17:34:07 uue16 kernel: [   28.227477] isapnp: No Plug & Play device found
Nov  8 17:34:07 uue16 kernel: [   28.250428] Real Time Clock Driver v1.12ac
Nov  8 17:34:07 uue16 kernel: [   28.250514] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov  8 17:34:07 uue16 kernel: [   28.250604] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov  8 17:34:07 uue16 kernel: [   28.251255] 00:10: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov  8 17:34:07 uue16 kernel: [   28.251892] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov  8 17:34:07 uue16 kernel: [   28.252006] input: Macintosh mouse button emulation as /class/input/input0
Nov  8 17:34:07 uue16 kernel: [   28.252091] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Nov  8 17:34:07 uue16 kernel: [   28.254742] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov  8 17:34:07 uue16 kernel: [   28.254749] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov  8 17:34:07 uue16 kernel: [   28.254930] mice: PS/2 mouse device common for all mice
Nov  8 17:34:07 uue16 kernel: [   28.255049] EISA: Probing bus 0 at eisa.0
Nov  8 17:34:07 uue16 kernel: [   28.255076] Cannot allocate resource for EISA slot 8
Nov  8 17:34:07 uue16 kernel: [   28.255078] EISA: Detected 0 cards.
Nov  8 17:34:07 uue16 kernel: [   28.255143] TCP cubic registered
Nov  8 17:34:07 uue16 kernel: [   28.255154] NET: Registered protocol family 1
Nov  8 17:34:07 uue16 kernel: [   28.255172] Using IPI No-Shortcut mode
Nov  8 17:34:07 uue16 kernel: [   28.255325]   Magic number: 15:102:605
Nov  8 17:34:07 uue16 kernel: [   28.255382]   hash matches device ptyd9
Nov  8 17:34:07 uue16 kernel: [   28.255393]   hash matches device ptyac
Nov  8 17:34:07 uue16 kernel: [   28.255603] Freeing unused kernel memory: 364k freed
Nov  8 17:34:07 uue16 kernel: [   28.273374] input: AT Translated Set 2 keyboard as /class/input/input1
Nov  8 17:34:07 uue16 kernel: [   29.448932] AppArmor: AppArmor initialized<5>audit(1194564830.980:2):  type=1505 info="AppArmor initialized" pid=1374
Nov  8 17:34:07 uue16 kernel: [   29.454572] fuse init (API version 7.8)
Nov  8 17:34:07 uue16 kernel: [   29.458795] Failure registering capabilities with primary security module.
Nov  8 17:34:07 uue16 kernel: [   29.579557] ACPI Warning (tbutils-0217): Incorrect checksum in table [  Qµ] -  00, should be 01 [20070126]
Nov  8 17:34:07 uue16 kernel: [   29.579576] ACPI Error (tbinstal-0134): Table has invalid signature [  Qµ], must be SSDT, PSDT or OEMx [20070126]
Nov  8 17:34:07 uue16 kernel: [   29.579601] ACPI Error (psparse-0551): Method parse/execution failed [\_PR_.CPU1._PDC] (Node df83a150), AE_BAD_SIGNATURE
Nov  8 17:34:07 uue16 kernel: [   29.579940] ACPI: Processor [CPU1] (supports 8 throttling states)
Nov  8 17:34:07 uue16 kernel: [   29.676600] ACPI Warning (tbutils-0217): Incorrect checksum in table [  Qµ] -  00, should be 01 [20070126]
Nov  8 17:34:07 uue16 kernel: [   29.676617] ACPI Error (tbinstal-0134): Table has invalid signature [  Qµ], must be SSDT, PSDT or OEMx [20070126]
Nov  8 17:34:07 uue16 kernel: [   29.676639] ACPI Error (psparse-0551): Method parse/execution failed [\_PR_.CPU2._PDC] (Node df83a1e0), AE_BAD_SIGNATURE
Nov  8 17:34:07 uue16 kernel: [   30.157373] usbcore: registered new interface driver usbfs
Nov  8 17:34:07 uue16 kernel: [   30.157403] usbcore: registered new interface driver hub
Nov  8 17:34:07 uue16 kernel: [   30.157821] usbcore: registered new device driver usb
Nov  8 17:34:07 uue16 kernel: [   30.190457] SCSI subsystem initialized
Nov  8 17:34:07 uue16 kernel: [   30.214011] USB Universal Host Controller Interface driver v3.0
Nov  8 17:34:07 uue16 kernel: [   30.214070] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
Nov  8 17:34:07 uue16 kernel: [   30.214084] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Nov  8 17:34:07 uue16 kernel: [   30.214089] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Nov  8 17:34:07 uue16 kernel: [   30.214187] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Nov  8 17:34:07 uue16 kernel: [   30.214217] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000e480
Nov  8 17:34:07 uue16 kernel: [   30.214358] usb usb1: configuration #1 chosen from 1 choice
Nov  8 17:34:07 uue16 kernel: [   30.214394] hub 1-0:1.0: USB hub found
Nov  8 17:34:07 uue16 kernel: [   30.214402] hub 1-0:1.0: 2 ports detected
Nov  8 17:34:07 uue16 kernel: [   30.214456] libata version 2.21 loaded.
Nov  8 17:34:07 uue16 kernel: [   30.232670] Floppy drive(s): fd0 is 1.44M
Nov  8 17:34:07 uue16 kernel: [   30.248616] FDC 0 is a post-1991 82077
Nov  8 17:34:07 uue16 kernel: [   30.316866] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
Nov  8 17:34:07 uue16 kernel: [   30.316877] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Nov  8 17:34:07 uue16 kernel: [   30.316881] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Nov  8 17:34:07 uue16 kernel: [   30.316904] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Nov  8 17:34:07 uue16 kernel: [   30.316932] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000e800
Nov  8 17:34:07 uue16 kernel: [   30.317021] usb usb2: configuration #1 chosen from 1 choice
Nov  8 17:34:07 uue16 kernel: [   30.317047] hub 2-0:1.0: USB hub found
Nov  8 17:34:07 uue16 kernel: [   30.317052] hub 2-0:1.0: 2 ports detected
Nov  8 17:34:07 uue16 kernel: [   30.420537] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
Nov  8 17:34:07 uue16 kernel: [   30.420546] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Nov  8 17:34:07 uue16 kernel: [   30.420550] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Nov  8 17:34:07 uue16 kernel: [   30.420572] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Nov  8 17:34:07 uue16 kernel: [   30.420597] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000e880
Nov  8 17:34:07 uue16 kernel: [   30.420683] usb usb3: configuration #1 chosen from 1 choice
Nov  8 17:34:07 uue16 kernel: [   30.420712] hub 3-0:1.0: USB hub found
Nov  8 17:34:07 uue16 kernel: [   30.420718] hub 3-0:1.0: 2 ports detected
Nov  8 17:34:07 uue16 kernel: [   30.524229] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17
Nov  8 17:34:07 uue16 kernel: [   30.524238] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Nov  8 17:34:07 uue16 kernel: [   30.524242] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Nov  8 17:34:07 uue16 kernel: [   30.524264] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Nov  8 17:34:07 uue16 kernel: [   30.524290] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000ec00
Nov  8 17:34:07 uue16 kernel: [   30.524384] usb usb4: configuration #1 chosen from 1 choice
Nov  8 17:34:07 uue16 kernel: [   30.524411] hub 4-0:1.0: USB hub found
Nov  8 17:34:07 uue16 kernel: [   30.524417] hub 4-0:1.0: 2 ports detected
Nov  8 17:34:07 uue16 kernel: [   30.556049] usb 1-1: new full speed USB device using uhci_hcd and address 2
Nov  8 17:34:07 uue16 kernel: [   30.627947] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 21 (level, low) -> IRQ 21
Nov  8 17:34:07 uue16 kernel: [   30.627956] uhci_hcd 0000:01:00.0: UHCI Host Controller
Nov  8 17:34:07 uue16 kernel: [   30.627978] uhci_hcd 0000:01:00.0: new USB bus registered, assigned bus number 5
Nov  8 17:34:07 uue16 kernel: [   30.628004] uhci_hcd 0000:01:00.0: irq 21, io base 0x00008880
Nov  8 17:34:07 uue16 kernel: [   30.628095] usb usb5: configuration #1 chosen from 1 choice
Nov  8 17:34:07 uue16 kernel: [   30.628122] hub 5-0:1.0: USB hub found
Nov  8 17:34:07 uue16 kernel: [   30.628128] hub 5-0:1.0: 2 ports detected
Nov  8 17:34:07 uue16 kernel: [   30.731608] ACPI: PCI Interrupt 0000:01:00.1[B] -> GSI 22 (level, low) -> IRQ 22
Nov  8 17:34:07 uue16 kernel: [   30.731618] uhci_hcd 0000:01:00.1: UHCI Host Controller
Nov  8 17:34:07 uue16 kernel: [   30.731641] uhci_hcd 0000:01:00.1: new USB bus registered, assigned bus number 6
Nov  8 17:34:07 uue16 kernel: [   30.731667] uhci_hcd 0000:01:00.1: irq 22, io base 0x00008c00
Nov  8 17:34:07 uue16 kernel: [   30.731758] usb usb6: configuration #1 chosen from 1 choice
Nov  8 17:34:07 uue16 kernel: [   30.731785] hub 6-0:1.0: USB hub found
Nov  8 17:34:07 uue16 kernel: [   30.731791] hub 6-0:1.0: 2 ports detected
Nov  8 17:34:07 uue16 kernel: [   30.734759] usb 1-1: configuration #1 chosen from 1 choice
Nov  8 17:34:07 uue16 kernel: [   30.835320] ata_piix 0000:00:1f.1: version 2.11
Nov  8 17:34:07 uue16 kernel: [   30.835339] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 22
Nov  8 17:34:07 uue16 kernel: [   30.835377] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Nov  8 17:34:07 uue16 kernel: [   30.835445] scsi0 : ata_piix
Nov  8 17:34:07 uue16 kernel: [   30.835499] scsi1 : ata_piix
Nov  8 17:34:07 uue16 kernel: [   30.835645] ata1: PATA max UDMA/133 cmd 0x0001d800 ctl 0x0001d482 bmdma 0x0001d000 irq 22
Nov  8 17:34:07 uue16 kernel: [   30.835650] ata2: PATA max UDMA/133 cmd 0x0001d400 ctl 0x0001d082 bmdma 0x0001d008 irq 22
Nov  8 17:34:07 uue16 kernel: [   30.982780] usb 1-2: new full speed USB device using uhci_hcd and address 3
Nov  8 17:34:07 uue16 kernel: [   31.008614] ata1.00: ATA-7: Maxtor 6B300R0, BAH41E00, max UDMA/133
Nov  8 17:34:07 uue16 kernel: [   31.008617] ata1.00: 586114704 sectors, multi 16: LBA48 
Nov  8 17:34:07 uue16 kernel: [   31.008781] ata1.01: ATA-6: ST340015ACE, 3.01, max UDMA/100
Nov  8 17:34:07 uue16 kernel: [   31.008784] ata1.01: 78165360 sectors, multi 16: LBA 
Nov  8 17:34:07 uue16 kernel: [   31.024570] ata1.00: configured for UDMA/133
Nov  8 17:34:07 uue16 kernel: [   31.039107] ata1.01: configured for UDMA/100
Nov  8 17:34:07 uue16 kernel: [   31.159516] usb 1-2: configuration #1 chosen from 1 choice
Nov  8 17:34:07 uue16 kernel: [   31.204347] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6B300R0   BAH4 PQ: 0 ANSI: 5
Nov  8 17:34:07 uue16 kernel: [   31.204484] scsi 0:0:1:0: Direct-Access     ATA      ST340015ACE      3.01 PQ: 0 ANSI: 5
Nov  8 17:34:07 uue16 kernel: [   31.204551] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Nov  8 17:34:07 uue16 kernel: [   31.204582] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 23
Nov  8 17:34:07 uue16 kernel: [   31.204616] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Nov  8 17:34:07 uue16 kernel: [   31.204660] scsi2 : ata_piix
Nov  8 17:34:07 uue16 kernel: [   31.204706] scsi3 : ata_piix
Nov  8 17:34:07 uue16 kernel: [   31.204741] ata3: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e082 bmdma 0x0001d880 irq 23
Nov  8 17:34:07 uue16 kernel: [   31.204746] ata4: SATA max UDMA/133 cmd 0x0001e000 ctl 0x0001dc02 bmdma 0x0001d888 irq 23
Nov  8 17:34:07 uue16 kernel: [   31.366874] ata3.00: ATA-6: WDC WD740GD-00FLC0, 33.08F33, max UDMA/133
Nov  8 17:34:07 uue16 kernel: [   31.366878] ata3.00: 145226112 sectors, multi 16: LBA48 
Nov  8 17:34:07 uue16 kernel: [   31.382878] ata3.00: configured for UDMA/133
Nov  8 17:34:07 uue16 kernel: [   31.409501] usb 3-1: new full speed USB device using uhci_hcd and address 2
Nov  8 17:34:07 uue16 kernel: [   31.590225] usb 3-1: configuration #1 chosen from 1 choice
Nov  8 17:34:07 uue16 kernel: [   31.736160] ata4.00: ATA-7: WDC WD3200KS-00PFB0, 21.00M21, max UDMA/133
Nov  8 17:34:07 uue16 kernel: [   31.736164] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/1)
Nov  8 17:34:07 uue16 kernel: [   31.736168] ata4.01: ATAPI: PLEXTOR DVDR   PX-755A, 1.06, max UDMA/66
Nov  8 17:34:07 uue16 kernel: [   31.748847] ata4.00: configured for UDMA/133
Nov  8 17:34:07 uue16 kernel: [   31.832244] usb 4-2: new full speed USB device using uhci_hcd and address 2
Nov  8 17:34:07 uue16 kernel: [   31.912191] ata4.01: configured for UDMA/66
Nov  8 17:34:07 uue16 kernel: [   31.912296] scsi 2:0:0:0: Direct-Access     ATA      WDC WD740GD-00FL 33.0 PQ: 0 ANSI: 5
Nov  8 17:34:07 uue16 kernel: [   31.912429] scsi 3:0:0:0: Direct-Access     ATA      WDC WD3200KS-00P 21.0 PQ: 0 ANSI: 5
Nov  8 17:34:07 uue16 kernel: [   31.913118] scsi 3:0:1:0: CD-ROM            PLEXTOR  DVDR   PX-755A   1.06 PQ: 0 ANSI: 5
Nov  8 17:34:07 uue16 kernel: [   31.913228] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
Nov  8 17:34:07 uue16 kernel: [   31.913243] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Nov  8 17:34:07 uue16 kernel: [   31.913246] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Nov  8 17:34:07 uue16 kernel: [   31.913279] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Nov  8 17:34:07 uue16 kernel: [   31.913310] ehci_hcd 0000:00:1d.7: debug port 1
Nov  8 17:34:07 uue16 kernel: [   31.913316] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
Nov  8 17:34:07 uue16 kernel: [   31.913322] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebfbc00
Nov  8 17:34:07 uue16 kernel: [   31.947906] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov  8 17:34:07 uue16 kernel: [   31.948000] usb usb7: configuration #1 chosen from 1 choice
Nov  8 17:34:07 uue16 kernel: [   31.948028] hub 7-0:1.0: USB hub found
Nov  8 17:34:07 uue16 kernel: [   31.948034] hub 7-0:1.0: 8 ports detected
Nov  8 17:34:07 uue16 kernel: [   32.051723] ACPI: PCI Interrupt 0000:01:00.2[C] -> GSI 23 (level, low) -> IRQ 23
Nov  8 17:34:07 uue16 kernel: [   32.051734] ehci_hcd 0000:01:00.2: EHCI Host Controller
Nov  8 17:34:07 uue16 kernel: [   32.051760] ehci_hcd 0000:01:00.2: new USB bus registered, assigned bus number 8
Nov  8 17:34:07 uue16 kernel: [   32.051793] ehci_hcd 0000:01:00.2: irq 23, io mem 0xfe6ffc00
Nov  8 17:34:07 uue16 kernel: [   32.051801] ehci_hcd 0000:01:00.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
Nov  8 17:34:07 uue16 kernel: [   32.051875] usb usb8: configuration #1 chosen from 1 choice
Nov  8 17:34:07 uue16 kernel: [   32.051903] hub 8-0:1.0: USB hub found
Nov  8 17:34:07 uue16 kernel: [   32.051909] hub 8-0:1.0: 4 ports detected
Nov  8 17:34:07 uue16 kernel: [   32.155384] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 21 (level, low) -> IRQ 21
Nov  8 17:34:07 uue16 kernel: [   32.205044] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fe6ff000-fe6ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov  8 17:34:07 uue16 kernel: [   32.209029] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
Nov  8 17:34:07 uue16 kernel: [   32.209052] sd 0:0:0:0: [sda] Write Protect is off
Nov  8 17:34:07 uue16 kernel: [   32.209057] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  8 17:34:07 uue16 kernel: [   32.209085] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 17:34:07 uue16 kernel: [   32.209167] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
Nov  8 17:34:07 uue16 kernel: [   32.209184] sd 0:0:0:0: [sda] Write Protect is off
Nov  8 17:34:07 uue16 kernel: [   32.209188] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  8 17:34:07 uue16 kernel: [   32.209215] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 17:34:07 uue16 kernel: [   32.209221]  sda: sda1 sda2
Nov  8 17:34:07 uue16 kernel: [   32.229981] sd 0:0:0:0: [sda] Attached SCSI disk
Nov  8 17:34:07 uue16 kernel: [   32.230053] sd 0:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
Nov  8 17:34:07 uue16 kernel: [   32.230069] sd 0:0:1:0: [sdb] Write Protect is off
Nov  8 17:34:07 uue16 kernel: [   32.230073] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Nov  8 17:34:07 uue16 kernel: [   32.230098] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 17:34:07 uue16 kernel: [   32.230150] sd 0:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
Nov  8 17:34:07 uue16 kernel: [   32.230166] sd 0:0:1:0: [sdb] Write Protect is off
Nov  8 17:34:07 uue16 kernel: [   32.230169] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Nov  8 17:34:07 uue16 kernel: [   32.230194] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 17:34:07 uue16 kernel: [   32.230199]  sdb: sdb1 sdb2 < sdb5 >
Nov  8 17:34:07 uue16 kernel: [   32.296559] sd 0:0:1:0: [sdb] Attached SCSI disk
Nov  8 17:34:07 uue16 kernel: [   32.296625] sd 2:0:0:0: [sdc] 145226112 512-byte hardware sectors (74356 MB)
Nov  8 17:34:07 uue16 kernel: [   32.296640] sd 2:0:0:0: [sdc] Write Protect is off
Nov  8 17:34:07 uue16 kernel: [   32.296644] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Nov  8 17:34:07 uue16 kernel: [   32.296667] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 17:34:07 uue16 kernel: [   32.296721] sd 2:0:0:0: [sdc] 145226112 512-byte hardware sectors (74356 MB)
Nov  8 17:34:07 uue16 kernel: [   32.296735] sd 2:0:0:0: [sdc] Write Protect is off
Nov  8 17:34:07 uue16 kernel: [   32.296738] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Nov  8 17:34:07 uue16 kernel: [   32.296762] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 17:34:07 uue16 kernel: [   32.296766]  sdc: sdc1
Nov  8 17:34:07 uue16 kernel: [   32.307765] sd 2:0:0:0: [sdc] Attached SCSI disk
Nov  8 17:34:07 uue16 kernel: [   32.307825] sd 3:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
Nov  8 17:34:07 uue16 kernel: [   32.307839] sd 3:0:0:0: [sdd] Write Protect is off
Nov  8 17:34:07 uue16 kernel: [   32.307843] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Nov  8 17:34:07 uue16 kernel: [   32.307865] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 17:34:07 uue16 kernel: [   32.307914] sd 3:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
Nov  8 17:34:07 uue16 kernel: [   32.307927] sd 3:0:0:0: [sdd] Write Protect is off
Nov  8 17:34:07 uue16 kernel: [   32.307931] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Nov  8 17:34:07 uue16 kernel: [   32.307955] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 17:34:07 uue16 kernel: [   32.307959]  sdd: sdd1 sdd2 < sdd5 >
Nov  8 17:34:07 uue16 kernel: [   32.332547] sd 3:0:0:0: [sdd] Attached SCSI disk
Nov  8 17:34:07 uue16 kernel: [   32.335284] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Nov  8 17:34:07 uue16 kernel: [   32.335289] Uniform CD-ROM driver Revision: 3.20
Nov  8 17:34:07 uue16 kernel: [   32.335347] sr 3:0:1:0: Attached scsi CD-ROM sr0
Nov  8 17:34:07 uue16 kernel: [   32.336998] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov  8 17:34:07 uue16 kernel: [   32.337027] sd 0:0:1:0: Attached scsi generic sg1 type 0
Nov  8 17:34:07 uue16 kernel: [   32.337057] sd 2:0:0:0: Attached scsi generic sg2 type 0
Nov  8 17:34:07 uue16 kernel: [   32.337084] sd 3:0:0:0: Attached scsi generic sg3 type 0
Nov  8 17:34:07 uue16 kernel: [   32.337110] sr 3:0:1:0: Attached scsi generic sg4 type 5
Nov  8 17:34:07 uue16 kernel: [   32.354689] usb 4-2: device not accepting address 2, error -71
Nov  8 17:34:07 uue16 kernel: [   32.569117] Attempting manual resume
Nov  8 17:34:07 uue16 kernel: [   32.569120] swsusp: Resume From Partition 8:53
Nov  8 17:34:07 uue16 kernel: [   32.569122] PM: Checking swsusp image.
Nov  8 17:34:07 uue16 kernel: [   32.569283] PM: Resume from disk failed.
Nov  8 17:34:07 uue16 kernel: [   32.611347] kjournald starting.  Commit interval 5 seconds
Nov  8 17:34:07 uue16 kernel: [   32.611357] EXT3-fs: mounted filesystem with ordered data mode.
Nov  8 17:34:07 uue16 kernel: [   32.921019] usb 3-1: USB disconnect, address 2
Nov  8 17:34:07 uue16 kernel: [   33.287909] usb 7-1: new high speed USB device using ehci_hcd and address 2
Nov  8 17:34:07 uue16 kernel: [   33.436123] usb 7-1: configuration #1 chosen from 1 choice
Nov  8 17:34:07 uue16 kernel: [   33.471452] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800008e4aa6]
Nov  8 17:34:07 uue16 kernel: [   33.918024] usb 7-5: new high speed USB device using ehci_hcd and address 4
Nov  8 17:34:07 uue16 kernel: [   34.067113] usb 7-5: configuration #1 chosen from 1 choice
Nov  8 17:34:07 uue16 kernel: [   34.304871] usb 7-8: new high speed USB device using ehci_hcd and address 5
Nov  8 17:34:07 uue16 kernel: [   34.438374] usb 7-8: configuration #1 chosen from 1 choice
Nov  8 17:34:07 uue16 kernel: [   34.438657] usb 1-1: USB disconnect, address 2
Nov  8 17:34:07 uue16 kernel: [   34.438694] usbcore: registered new interface driver libusual
Nov  8 17:34:07 uue16 kernel: [   34.564108] usb 1-2: USB disconnect, address 3
Nov  8 17:34:07 uue16 kernel: [   34.754189] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov  8 17:34:07 uue16 kernel: [   34.754242] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov  8 17:34:07 uue16 kernel: [   34.803380] usb 1-2: new full speed USB device using uhci_hcd and address 4
Nov  8 17:34:07 uue16 kernel: [   34.861421] Initializing USB Mass Storage driver...
Nov  8 17:34:07 uue16 kernel: [   34.980074] usb 1-2: configuration #1 chosen from 1 choice
Nov  8 17:34:07 uue16 kernel: [   35.222139] usb 8-3: new high speed USB device using ehci_hcd and address 2
Nov  8 17:34:07 uue16 kernel: [   35.354703] usb 8-3: configuration #1 chosen from 1 choice
Nov  8 17:34:07 uue16 kernel: [   35.355219] scsi4 : SCSI emulation for USB Mass Storage devices
Nov  8 17:34:07 uue16 kernel: [   35.355265] usb-storage: device found at 2
Nov  8 17:34:07 uue16 kernel: [   35.355268] usb-storage: waiting for device to settle before scanning
Nov  8 17:34:07 uue16 kernel: [   35.355306] scsi5 : SCSI emulation for USB Mass Storage devices
Nov  8 17:34:07 uue16 kernel: [   35.355343] usb-storage: device found at 4
Nov  8 17:34:07 uue16 kernel: [   35.355346] usb-storage: waiting for device to settle before scanning
Nov  8 17:34:07 uue16 kernel: [   35.355379] scsi6 : SCSI emulation for USB Mass Storage devices
Nov  8 17:34:07 uue16 kernel: [   35.355417] usb-storage: device found at 5
Nov  8 17:34:07 uue16 kernel: [   35.355419] usb-storage: waiting for device to settle before scanning
Nov  8 17:34:07 uue16 kernel: [   35.355464] scsi7 : SCSI emulation for USB Mass Storage devices
Nov  8 17:34:07 uue16 kernel: [   35.355519] usbcore: registered new interface driver usb-storage
Nov  8 17:34:07 uue16 kernel: [   35.355523] USB Mass Storage support registered.
Nov  8 17:34:07 uue16 kernel: [   35.355584] usb-storage: device found at 2
Nov  8 17:34:07 uue16 kernel: [   35.355587] usb-storage: waiting for device to settle before scanning
Nov  8 17:34:07 uue16 kernel: [   38.780022] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov  8 17:34:07 uue16 kernel: [   38.957245] intel_rng: FWH not detected
Nov  8 17:34:07 uue16 kernel: [   38.960708] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov  8 17:34:07 uue16 kernel: [   39.218300] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0xC202
Nov  8 17:34:07 uue16 kernel: [   39.218327] usbcore: registered new interface driver usblp
Nov  8 17:34:07 uue16 kernel: [   39.218334] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Nov  8 17:34:07 uue16 kernel: [   39.379108] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 19 (level, low) -> IRQ 17
Nov  8 17:34:07 uue16 kernel: [   39.379123] PCI: Setting latency timer of device 0000:04:00.0 to 64
Nov  8 17:34:07 uue16 kernel: [   39.379149] sky2 0000:04:00.0: v1.18 addr 0xfe9fc000 irq 17 Yukon-EC (0xb6) rev 2
Nov  8 17:34:07 uue16 kernel: [   39.379271] sky2 eth0: addr 00:15:f2:a0:f8:e6
Nov  8 17:34:07 uue16 kernel: [   39.379293] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov  8 17:34:07 uue16 kernel: [   39.379303] PCI: Setting latency timer of device 0000:03:00.0 to 64
Nov  8 17:34:07 uue16 kernel: [   39.379329] sky2 0000:03:00.0: v1.18 addr 0xfe8fc000 irq 16 Yukon-EC (0xb6) rev 2
Nov  8 17:34:07 uue16 kernel: [   39.379442] sky2 eth1: addr 00:15:f2:a0:f1:e7
Nov  8 17:34:07 uue16 kernel: [   39.387727] iTCO_vendor_support: vendor-support=0
Nov  8 17:34:07 uue16 kernel: [   39.392640] sky2 eth0: enabling interface
Nov  8 17:34:07 uue16 kernel: [   39.403271] Linux agpgart interface v0.102 (c) Dave Jones
Nov  8 17:34:07 uue16 kernel: [   39.462566] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Nov  8 17:34:07 uue16 kernel: [   39.493093] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
Nov  8 17:34:07 uue16 kernel: [   39.505459] parport_pc 00:07: reported by Plug and Play ACPI
Nov  8 17:34:07 uue16 kernel: [   39.505501] input: PC Speaker as /class/input/input3
Nov  8 17:34:07 uue16 kernel: [   39.505571] parport0: PC-style at 0x378 (0x778), irq 7<6>iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
Nov  8 17:34:07 uue16 kernel: [   39.505672] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Nov  8 17:34:07 uue16 kernel: [   39.506159] , dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Nov  8 17:34:07 uue16 kernel: [   39.716778] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov  8 17:34:07 uue16 kernel: [   39.744314] [fglrx] Maximum main memory to use for locked dma buffers: 2888 MBytes.
Nov  8 17:34:07 uue16 kernel: [   39.744362] [fglrx] ASYNCIO init succeed!
Nov  8 17:34:07 uue16 kernel: [   39.746074] [fglrx] PAT is enabled successfully!
Nov  8 17:34:07 uue16 kernel: [   39.746093] [fglrx] module loaded - fglrx 8.42.3 [Oct 19 2007] on minor 0
Nov  8 17:34:07 uue16 kernel: [   39.940351] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 17
Nov  8 17:34:07 uue16 kernel: [   39.940371] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Nov  8 17:34:07 uue16 kernel: [   40.339033] usb-storage: device scan complete
Nov  8 17:34:07 uue16 kernel: [   40.339041] usb-storage: device scan complete
Nov  8 17:34:07 uue16 kernel: [   40.339412] usb-storage: device scan complete
Nov  8 17:34:07 uue16 kernel: [   40.339537] scsi 7:0:0:0: Direct-Access     HP       Photosmart 8200  1.00 PQ: 0 ANSI: 2
Nov  8 17:34:07 uue16 kernel: [   40.340285] usb-storage: device scan complete
Nov  8 17:34:07 uue16 kernel: [   40.340664] scsi 5:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
Nov  8 17:34:07 uue16 kernel: [   40.340802] sd 7:0:0:0: [sde] Attached SCSI removable disk
Nov  8 17:34:07 uue16 kernel: [   40.340843] sd 7:0:0:0: Attached scsi generic sg5 type 0
Nov  8 17:34:07 uue16 kernel: [   40.341661] scsi 4:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100D PQ: 0 ANSI: 4
Nov  8 17:34:07 uue16 kernel: [   40.342034] scsi 5:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
Nov  8 17:34:07 uue16 kernel: [   40.343280] scsi 5:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
Nov  8 17:34:07 uue16 kernel: [   40.344526] scsi 5:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
Nov  8 17:34:07 uue16 kernel: [   40.374325] scsi 6:0:0:0: Direct-Access     IC25N030 ATCS04-0         CA3O PQ: 0 ANSI: 0
Nov  8 17:34:07 uue16 kernel: [   40.375424] sd 6:0:0:0: [sdf] 58605119 512-byte hardware sectors (30006 MB)
Nov  8 17:34:07 uue16 kernel: [   40.376296] sd 6:0:0:0: [sdf] Write Protect is off
Nov  8 17:34:07 uue16 kernel: [   40.376300] sd 6:0:0:0: [sdf] Mode Sense: 03 00 00 00
Nov  8 17:34:07 uue16 kernel: [   40.376303] sd 6:0:0:0: [sdf] Assuming drive cache: write through
Nov  8 17:34:07 uue16 kernel: [   40.377167] sd 6:0:0:0: [sdf] 58605119 512-byte hardware sectors (30006 MB)
Nov  8 17:34:07 uue16 kernel: [   40.378042] sd 6:0:0:0: [sdf] Write Protect is off
Nov  8 17:34:07 uue16 kernel: [   40.378045] sd 6:0:0:0: [sdf] Mode Sense: 03 00 00 00
Nov  8 17:34:07 uue16 kernel: [   40.378048] sd 6:0:0:0: [sdf] Assuming drive cache: write through
Nov  8 17:34:07 uue16 kernel: [   40.378052]  sdf:<6>lp0: using parport0 (interrupt-driven).
Nov  8 17:34:07 uue16 kernel: [   40.651247]  sdf1
Nov  8 17:34:07 uue16 kernel: [   40.651314] sd 6:0:0:0: [sdf] Attached SCSI disk
Nov  8 17:34:07 uue16 kernel: [   40.651357] sd 6:0:0:0: Attached scsi generic sg6 type 0
Nov  8 17:34:07 uue16 kernel: [   40.652523] sd 5:0:0:0: [sdg] Attached SCSI removable disk
Nov  8 17:34:07 uue16 kernel: [   40.652577] sd 5:0:0:0: Attached scsi generic sg7 type 0
Nov  8 17:34:07 uue16 kernel: [   40.653638] sd 5:0:0:1: [sdh] Attached SCSI removable disk
Nov  8 17:34:07 uue16 kernel: [   40.653689] sd 5:0:0:1: Attached scsi generic sg8 type 0
Nov  8 17:34:07 uue16 kernel: [   40.654877] sd 5:0:0:2: [sdi] Attached SCSI removable disk
Nov  8 17:34:07 uue16 kernel: [   40.654912] sd 5:0:0:2: Attached scsi generic sg9 type 0
Nov  8 17:34:07 uue16 kernel: [   40.657984] sd 5:0:0:3: [sdj] Attached SCSI removable disk
Nov  8 17:34:07 uue16 kernel: [   40.658035] sd 5:0:0:3: Attached scsi generic sg10 type 0
Nov  8 17:34:07 uue16 kernel: [   40.661922] sd 4:0:0:0: [sdk] 625142448 512-byte hardware sectors (320073 MB)
Nov  8 17:34:07 uue16 kernel: [   40.665927] sd 4:0:0:0: [sdk] Write Protect is off
Nov  8 17:34:07 uue16 kernel: [   40.665932] sd 4:0:0:0: [sdk] Mode Sense: 1c 00 00 00
Nov  8 17:34:07 uue16 kernel: [   40.665936] sd 4:0:0:0: [sdk] Assuming drive cache: write through
Nov  8 17:34:07 uue16 kernel: [   40.668839] sd 4:0:0:0: [sdk] 625142448 512-byte hardware sectors (320073 MB)
Nov  8 17:34:07 uue16 kernel: [   40.670288] sd 4:0:0:0: [sdk] Write Protect is off
Nov  8 17:34:07 uue16 kernel: [   40.670292] sd 4:0:0:0: [sdk] Mode Sense: 1c 00 00 00
Nov  8 17:34:07 uue16 kernel: [   40.670294] sd 4:0:0:0: [sdk] Assuming drive cache: write through
Nov  8 17:34:07 uue16 kernel: [   40.670296]  sdk: sdk1
Nov  8 17:34:07 uue16 kernel: [   40.675614] sd 4:0:0:0: [sdk] Attached SCSI disk
Nov  8 17:34:07 uue16 kernel: [   40.675668] sd 4:0:0:0: Attached scsi generic sg11 type 0
Nov  8 17:34:07 uue16 kernel: [   40.760678] Adding 9100780k swap on /dev/sdd5.  Priority:-1 extents:1 across:9100780k
Nov  8 17:34:07 uue16 kernel: [   40.897298] NET: Registered protocol family 17
Nov  8 17:34:07 uue16 kernel: [   41.110298] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Nov  8 17:34:07 uue16 kernel: [   41.145056] EXT3 FS on sdd1, internal journal
Nov  8 17:34:07 uue16 kernel: [   42.986317] NET: Registered protocol family 10
Nov  8 17:34:07 uue16 kernel: [   42.986443] lo: Disabled Privacy Extensions
Nov  8 17:34:07 uue16 kernel: [   43.939585] No dock devices found.
Nov  8 17:34:07 uue16 kernel: [   43.993317] input: Power Button (FF) as /class/input/input4
Nov  8 17:34:07 uue16 kernel: [   43.993340] ACPI: Power Button (FF) [PWRF]
Nov  8 17:34:07 uue16 kernel: [   43.993445] input: Power Button (CM) as /class/input/input5
Nov  8 17:34:07 uue16 kernel: [   43.993470] ACPI: Power Button (CM) [PWRB]
Nov  8 17:34:07 uue16 NetworkManager: <info>  starting... 
Nov  8 17:34:07 uue16 NetworkManager: <debug> [1194564847.560050] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_277c'). 
Nov  8 17:34:07 uue16 kernel: [   45.495120] ppdev: user-space parallel port driver
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.006889] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_277d'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.009968] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_7109'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.011294] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_7129'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.012639] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.013820] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.014382] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.014990] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_11ab_4362'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.015967] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27e0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.016562] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_11ab_4362_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.050731] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27e2'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.051168] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_11ab_6141'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.051576] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.052009] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.052447] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.052855] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_220d_noserial'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.053262] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_220d_noserial_if0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.053669] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.054073] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.054479] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.054889] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.055295] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.055700] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.056105] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.056520] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.056925] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.057330] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.057734] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.058139] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.058542] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.058947] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_if0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.059351] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_if0_scsi_host'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.059793] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_if0_scsi_host_scsi_device_lun0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.060215] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.060638] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.061072] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.061493] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.061899] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun1'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.062302] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun2'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.062706] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun3'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.063109] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.063511] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_if0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.063913] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_if0_scsi_host'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.064324] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_if0_scsi_host_scsi_device_lun0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.064724] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_244e'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.065126] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3038'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.065527] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.065927] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_0_if0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.066328] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3038_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.066727] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_1'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.067124] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_1_if0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.067524] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3104'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.067920] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_2'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.068329] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_2_if0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.068740] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.069163] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.069567] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if1'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.069987] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if2'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.070404] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if2_scsi_host'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.070808] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if2_scsi_host_scsi_device_lun0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.071209] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1102_5'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.071610] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_104c_8023'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.072012] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b8'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.072421] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.072818] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.073216] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.073611] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.074006] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.074403] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.074798] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_scsi_device_lun0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.075194] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.075590] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.075985] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.076473] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.076878] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.077329] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_floppy_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.077727] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.078142] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.078539] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.079004] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.079424] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.079818] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.080212] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a08'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.080692] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.081090] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.081535] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.081953] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.082422] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.082863] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0700'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.083297] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0401'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.083723] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.084148] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.084590] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_1'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.085019] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.085444] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f03'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.085871] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_2'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.086297] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNPb02f'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.086723] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNPb006'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.087148] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.087576] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_3'). 
Nov  8 17:34:08 uue16 kernel: [   45.792330] audit(1194564848.217:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=7050 profile="/usr/sbin/cupsd"
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.350689] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.351232] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.351674] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.352098] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.352538] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_f2_a0_f8_e6'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.360982] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_f2_a0_f1_e7'). 
Nov  8 17:34:08 uue16 kernel: [   45.866426] sky2 eth1: enabling interface
Nov  8 17:34:08 uue16 kernel: [   45.870358] ADDRCONF(NETDEV_UP): eth1: link is not ready
Nov  8 17:34:08 uue16 NetworkManager: <info>  eth1: Device is fully-supported using driver 'sky2'. 
Nov  8 17:34:08 uue16 NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov  8 17:34:08 uue16 NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov  8 17:34:08 uue16 NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth1'. 
Nov  8 17:34:08 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.447564] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 17:34:08 uue16 NetworkManager: <info>  Will activate wired connection 'eth1' because it now has a link. 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.448299] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0_0_scsi_generic'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.448929] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun3_scsi_generic'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.449442] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.450032] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.452801] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.453311] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0_0_scsi_generic'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.453823] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if2_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.454278] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.454722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.455210] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.455632] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun2_scsi_generic'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.456186] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_1'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.456760] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.457548] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.458023] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.458510] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.459083] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNPb006_oss_mixer__1'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.459561] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.460125] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.460700] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_1'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.463737] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_1'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.464245] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_2'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.464795] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.465215] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.465654] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.466162] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.466578] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.467012] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.467412] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.467805] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.468200] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.468602] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.468995] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_220d_noserial_usbraw'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.469386] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.469795] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.470200] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.470590] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_0_usbraw'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.470977] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_1_usbraw'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.471365] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.471754] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_usbraw'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.472196] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_usbraw'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.472598] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_usbraw'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.472985] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_2_usbraw'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.473371] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_usbraw'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.473759] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_floppy_0_storage'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.474146] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Maxtor_6B300R0_B620LRQH'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.474533] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_01C660C5D0074900'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.543795] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_36D04443D0440C15'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.548881] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST340015ACE_5LAEEQQH'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.557205] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_6c99eb8b_ecab_4126_bb00_453192aecfb6'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.562829] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.570553] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_e73ed621_c1d6_43e1_adc4_505d9a6360f9'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.575706] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD740GD_00FLC0_WD_WMAKE2361213'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.585332] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_4AA44F23A44F10BD'). 
Nov  8 17:34:08 uue16 ntpdate[5953]: adjust time server 91.189.94.4 offset -0.002855 sec
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.910206] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD3200KS_00PFB0_WD_WCAPD1030686'). 
Nov  8 17:34:08 uue16 NetworkManager: <debug> [1194564848.915904] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_e8bee423_266f_49eb_8f99_a75d19ffa386'). 
Nov  8 17:34:09 uue16 NetworkManager: <debug> [1194564849.043247] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024_0'). 
Nov  8 17:34:09 uue16 NetworkManager: <debug> [1194564849.048577] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_2d0e7fbd_476c_40ef_8e51_f20e13690ce1'). 
Nov  8 17:34:09 uue16 NetworkManager: <debug> [1194564849.113451] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_HP_Photosmart_8200_MY5AR3X0H504KK_0_0'). 
Nov  8 17:34:09 uue16 NetworkManager: <debug> [1194564849.118831] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_IC25N030_ATCS04_0_0_0_0'). 
Nov  8 17:34:09 uue16 NetworkManager: <debug> [1194564849.136026] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8CD0_6617'). 
Nov  8 17:34:09 uue16 NetworkManager: <debug> [1194564849.148506] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_STORAGE_DEVICE_0300836166_0_0'). 
Nov  8 17:34:09 uue16 NetworkManager: <debug> [1194564849.158432] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_STORAGE_DEVICE_0300836166_0_1'). 
Nov  8 17:34:09 uue16 NetworkManager: <debug> [1194564849.168788] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_STORAGE_DEVICE_0300836166_0_2'). 
Nov  8 17:34:09 uue16 NetworkManager: <debug> [1194564849.178998] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_STORAGE_DEVICE_0300836166_0_3'). 
Nov  8 17:34:09 uue16 NetworkManager: <debug> [1194564849.184587] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Seagate_FreeAgentDesktop_9QF3CG9K_0_0'). 
Nov  8 17:34:09 uue16 NetworkManager: <debug> [1194564849.225730] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_04F07BDEF07BD480'). 
Nov  8 17:34:09 uue16 NetworkManager: <debug> [1194564849.339980] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU4'). 
Nov  8 17:34:09 uue16 NetworkManager: <debug> [1194564849.346862] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU3'). 
Nov  8 17:34:09 uue16 NetworkManager: <debug> [1194564849.347736] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU2'). 
Nov  8 17:34:09 uue16 NetworkManager: <debug> [1194564849.348136] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Nov  8 17:34:09 uue16 NetworkManager: <debug> [1194564849.348544] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVDR___PX_755A'). 
Nov  8 17:34:10 uue16 kernel: [   47.510834] sky2 eth1: Link is up at 100 Mbps, full duplex, flow control rx
Nov  8 17:34:10 uue16 NetworkManager: <info>  Will activate wired connection 'eth1' because it now has a link. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:10 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:10 uue16 kernel: [   47.512924] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:10 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:10 uue16 hal_lpadmin: add
Nov  8 17:34:10 uue16 mysqld_safe[7280]: started
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:10 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:10 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:10 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:10 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:10 uue16 mysqld[7295]: 071108 17:34:10  InnoDB: Started; log sequence number 0 43655
Nov  8 17:34:10 uue16 mysqld[7295]: 071108 17:34:10 [Note] /usr/sbin/mysqld: ready for connections.
Nov  8 17:34:10 uue16 mysqld[7295]: Version: '5.0.45-Debian_1ubuntu3-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian etch distribution
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:10 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:10 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:10 uue16 /etc/mysql/debian-start[7426]: Upgrading MySQL tables if necessary.
Nov  8 17:34:11 uue16 kernel: [   48.509526] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Nov  8 17:34:11 uue16 kernel: [   48.509532] apm: disabled - APM is not SMP safe.
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:11 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:11 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:11 uue16 /etc/mysql/debian-start[7430]: Looking for 'mysql' in: /usr/bin/mysql
Nov  8 17:34:11 uue16 /etc/mysql/debian-start[7430]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck
Nov  8 17:34:11 uue16 /etc/mysql/debian-start[7430]: This installation of MySQL is already upgraded to 5.0.45, use --force if you still need to run mysql_upgrade
Nov  8 17:34:11 uue16 /etc/mysql/debian-start[7500]: Checking for insecure root accounts.
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:11 uue16 /etc/mysql/debian-start[7509]: WARNING: mysql.user contains 3 root accounts without password!
Nov  8 17:34:11 uue16 /etc/mysql/debian-start[7511]: Checking for crashed MySQL tables.
Nov  8 17:34:11 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:11 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:11 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:11 uue16 atieventsd[7532]: ATI External Events Daemon started... 
Nov  8 17:34:11 uue16 atieventsd[7532]: Event daemon control socket created 
Nov  8 17:34:11 uue16 atieventsd[7532]: acpid connection established 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:11 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:11 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:11 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:11 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:12 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:12 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:12 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:12 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:12 uue16 kernel: [   50.283221] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:12 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:12 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:12 uue16 kernel: [   50.386468] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Nov  8 17:34:12 uue16 kernel: [   50.403013] NFSD: starting 90-second grace period
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:13 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:13 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:13 uue16 hal_lpadmin: URIs: ['hp:/usb/Photosmart_8200_series?serial=MY5AR3X0H504KK', 'usb://HP/Photosmart%208200%20series?serial=MY5AR3X0H504KK', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if0_printer_MY5AR3X0H504KK']
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:13 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:13 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:13 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:13 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:13 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:13 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:13 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:14 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:14 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:14 uue16 snort[8093]: Var 'eth0_ADDRESS' defined, value len = 26 chars
Nov  8 17:34:14 uue16 snort[8093]: , value = 192.168.20.0/255.255.255.0 
Nov  8 17:34:14 uue16 snort[8093]: Var 'any_ADDRESS' defined, value len = 15 chars
Nov  8 17:34:14 uue16 snort[8093]: , value = 0.0.0.0/0.0.0.0 
Nov  8 17:34:14 uue16 snort[8093]: Var 'lo_ADDRESS' defined, value len = 19 chars
Nov  8 17:34:14 uue16 snort[8093]: , value = 127.0.0.0/255.0.0.0 
Nov  8 17:34:14 uue16 snort[8093]: Parsing Rules file /etc/snort/snort.conf 
Nov  8 17:34:14 uue16 snort[8093]: Var 'HOME_NET' redefined 
Nov  8 17:34:14 uue16 snort[8093]: Var 'EXTERNAL_NET' defined, value len = 3 chars
Nov  8 17:34:14 uue16 snort[8093]: , value = any 
Nov  8 17:34:14 uue16 snort[8093]: Var 'DNS_SERVERS' defined, value len = 16 chars
Nov  8 17:34:14 uue16 snort[8093]: , value = [192.168.0.0/16] 
Nov  8 17:34:14 uue16 snort[8093]: Var 'SMTP_SERVERS' defined, value len = 16 chars
Nov  8 17:34:14 uue16 snort[8093]: , value = [192.168.0.0/16] 
Nov  8 17:34:14 uue16 snort[8093]: Var 'HTTP_SERVERS' defined, value len = 16 chars
Nov  8 17:34:14 uue16 snort[8093]: , value = [192.168.0.0/16] 
Nov  8 17:34:14 uue16 snort[8093]: Var 'SQL_SERVERS' defined, value len = 16 chars
Nov  8 17:34:14 uue16 snort[8093]: , value = [192.168.0.0/16] 
Nov  8 17:34:14 uue16 snort[8093]: Var 'TELNET_SERVERS' defined, value len = 16 chars
Nov  8 17:34:14 uue16 snort[8093]: , value = [192.168.0.0/16] 
Nov  8 17:34:14 uue16 snort[8093]: Var 'SNMP_SERVERS' defined, value len = 16 chars
Nov  8 17:34:14 uue16 snort[8093]: , value = [192.168.0.0/16] 
Nov  8 17:34:14 uue16 snort[8093]: Var 'HTTP_PORTS' defined, value len = 2 chars
Nov  8 17:34:14 uue16 snort[8093]: , value = 80 
Nov  8 17:34:14 uue16 snort[8093]: Var 'SHELLCODE_PORTS' defined, value len = 3 chars
Nov  8 17:34:14 uue16 snort[8093]: , value = !80 
Nov  8 17:34:14 uue16 snort[8093]: Var 'ORACLE_PORTS' defined, value len = 4 chars
Nov  8 17:34:14 uue16 snort[8093]: , value = 1521 
Nov  8 17:34:14 uue16 snort[8093]: Var 'AIM_SERVERS' defined, value len = 185 chars
Nov  8 17:34:14 uue16 snort[8093]:  
Nov  8 17:34:14 uue16 snort[8093]:    [64.12.24.0/23,64.12.28.0/23,64.12.161.0/24,64.12.163.0/24,64.12.200.0/24,205.188.3.0/24,205.188.5.0/24,205.188.7.0/24,205.188.9 
Nov  8 17:34:14 uue16 snort[8093]:    .0/24,205.188.153.0/24,205.188.179.0/24,205.188.248.0/24] 
Nov  8 17:34:14 uue16 snort[8093]: Var 'RULE_PATH' defined, value len = 16 chars
Nov  8 17:34:14 uue16 snort[8093]: , value = /etc/snort/rules 
Nov  8 17:34:14 uue16 snort[8093]: ,-----------[Flow Config]---------------------- 
Nov  8 17:34:14 uue16 snort[8093]: | Stats Interval:  0 
Nov  8 17:34:14 uue16 snort[8093]: | Hash Method:     2 
Nov  8 17:34:14 uue16 snort[8093]: | Memcap:          10485760 
Nov  8 17:34:14 uue16 snort[8093]: | Rows  :          4099 
Nov  8 17:34:14 uue16 snort[8093]: | Overhead Bytes:  16400(%0.16) 
Nov  8 17:34:14 uue16 snort[8093]: `---------------------------------------------- 
Nov  8 17:34:14 uue16 snort[8093]: Frag3 global config: 
Nov  8 17:34:14 uue16 snort[8093]:     Max frags: 65536 
Nov  8 17:34:14 uue16 snort[8093]:     Fragment memory cap: 4194304 bytes 
Nov  8 17:34:14 uue16 snort[8093]: Frag3 engine config: 
Nov  8 17:34:14 uue16 snort[8093]:     Target-based policy: FIRST 
Nov  8 17:34:14 uue16 snort[8093]:     Fragment timeout: 60 seconds 
Nov  8 17:34:14 uue16 snort[8093]:     Fragment min_ttl:   1 
Nov  8 17:34:14 uue16 snort[8093]:     Fragment ttl_limit: 5 
Nov  8 17:34:14 uue16 snort[8093]:     Fragment Problems: 1 
Nov  8 17:34:14 uue16 snort[8093]:     Bound Addresses: 0.0.0.0/0.0.0.0 
Nov  8 17:34:14 uue16 snort[8093]: Stream5 global config: 
Nov  8 17:34:14 uue16 snort[8093]:     Track TCP sessions: ACTIVE 
Nov  8 17:34:14 uue16 snort[8093]:     Max TCP sessions: 8192 
Nov  8 17:34:14 uue16 snort[8093]:     Memcap (for reassembly packet storage): 8388608 
Nov  8 17:34:14 uue16 snort[8093]:     Track UDP sessions: INACTIVE 
Nov  8 17:34:14 uue16 snort[8093]:     Track ICMP sessions: INACTIVE 
Nov  8 17:34:14 uue16 snort[8093]: Stream5 TCP Policy config: 
Nov  8 17:34:14 uue16 snort[8093]:     Reassembly Policy: FIRST 
Nov  8 17:34:14 uue16 snort[8093]:     Timeout: 30 seconds 
Nov  8 17:34:14 uue16 snort[8093]:     Min ttl:  1 
Nov  8 17:34:14 uue16 snort[8093]:     Options: 
Nov  8 17:34:14 uue16 snort[8093]:         Static Flushpoint Sizes: YES 
Nov  8 17:34:14 uue16 snort[8093]:     Reassembly Ports: 
Nov  8 17:34:14 uue16 snort[8093]:       21 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:       23 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:       25 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:       42 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:       53 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:       80 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:       110 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:       111 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:       135 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:       136 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:       137 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:       139 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:       143 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:       445 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:       513 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:       1433 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:       1521 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:       3306 client (Footprint)  
Nov  8 17:34:14 uue16 snort[8093]:     Bound Addresses:0.0.0.0/0.0.0.0 
Nov  8 17:34:14 uue16 snort[8093]: HttpInspect Config: 
Nov  8 17:34:14 uue16 snort[8093]:     GLOBAL CONFIG 
Nov  8 17:34:14 uue16 snort[8093]:       Max Pipeline Requests:    0 
Nov  8 17:34:14 uue16 snort[8093]:       Inspection Type:          STATELESS 
Nov  8 17:34:14 uue16 snort[8093]:       Detect Proxy Usage:       NO 
Nov  8 17:34:14 uue16 snort[8093]:       IIS Unicode Map Filename: /etc/snort/unicode.map 
Nov  8 17:34:14 uue16 snort[8093]:       IIS Unicode Map Codepage: 1252 
Nov  8 17:34:14 uue16 snort[8093]:     DEFAULT SERVER CONFIG: 
Nov  8 17:34:14 uue16 snort[8093]:       Server profile: All 
Nov  8 17:34:14 uue16 snort[8093]:       Ports: 80 8080 8180  
Nov  8 17:34:14 uue16 snort[8093]:       Flow Depth: 300 
Nov  8 17:34:14 uue16 snort[8093]:       Max Chunk Length: 500000 
Nov  8 17:34:14 uue16 snort[8093]:       Inspect Pipeline Requests: YES 
Nov  8 17:34:14 uue16 snort[8093]:       URI Discovery Strict Mode: NO 
Nov  8 17:34:14 uue16 snort[8093]:       Allow Proxy Usage: NO 
Nov  8 17:34:14 uue16 snort[8093]:       Disable Alerting: NO 
Nov  8 17:34:14 uue16 snort[8093]:       Oversize Dir Length: 500 
Nov  8 17:34:14 uue16 snort[8093]:       Only inspect URI: NO 
Nov  8 17:34:14 uue16 snort[8093]:       Ascii: YES alert: NO 
Nov  8 17:34:14 uue16 snort[8093]:       Double Decoding: YES alert: YES 
Nov  8 17:34:14 uue16 snort[8093]:       %U Encoding: YES alert: YES 
Nov  8 17:34:14 uue16 snort[8093]:       Bare Byte: YES alert: YES 
Nov  8 17:34:14 uue16 snort[8093]:       Base36: OFF 
Nov  8 17:34:14 uue16 snort[8093]:       UTF 8: OFF 
Nov  8 17:34:14 uue16 snort[8093]:       IIS Unicode: YES alert: YES 
Nov  8 17:34:14 uue16 snort[8093]:       Multiple Slash: YES alert: NO 
Nov  8 17:34:14 uue16 snort[8093]:       IIS Backslash: YES alert: NO 
Nov  8 17:34:14 uue16 snort[8093]:       Directory Traversal: YES alert: NO 
Nov  8 17:34:14 uue16 snort[8093]:       Web Root Traversal: YES alert: YES 
Nov  8 17:34:14 uue16 snort[8093]:       Apache WhiteSpace: YES alert: NO 
Nov  8 17:34:14 uue16 snort[8093]:       IIS Delimiter: YES alert: NO 
Nov  8 17:34:14 uue16 snort[8093]:       IIS Unicode Map: GLOBAL IIS UNICODE MAP CONFIG 
Nov  8 17:34:14 uue16 snort[8093]:       Non-RFC Compliant Characters: NONE 
Nov  8 17:34:14 uue16 snort[8093]:       Whitespace Characters: 0x09 0x0b 0x0c 0x0d  
Nov  8 17:34:14 uue16 snort[8093]: rpc_decode arguments: 
Nov  8 17:34:14 uue16 snort[8093]:     Ports to decode RPC on: 111 32771  
Nov  8 17:34:14 uue16 snort[8093]:     alert_fragments: INACTIVE 
Nov  8 17:34:14 uue16 snort[8093]:     alert_large_fragments: ACTIVE 
Nov  8 17:34:14 uue16 snort[8093]:     alert_incomplete: ACTIVE 
Nov  8 17:34:14 uue16 snort[8093]:     alert_multiple_requests: ACTIVE 
Nov  8 17:34:14 uue16 snort[8093]: Portscan Detection Config: 
Nov  8 17:34:14 uue16 snort[8093]:     Detect Protocols:  TCP UDP ICMP IP 
Nov  8 17:34:14 uue16 snort[8093]:     Detect Scan Type:  portscan portsweep decoy_portscan distributed_portscan 
Nov  8 17:34:14 uue16 snort[8093]:     Sensitivity Level: Low 
Nov  8 17:34:14 uue16 snort[8093]:     Memcap (in bytes): 10000000 
Nov  8 17:34:14 uue16 snort[8093]:     Number of Nodes:   36900 
Nov  8 17:34:14 uue16 snort[8093]:  
Nov  8 17:34:14 uue16 python: hp-probe[8148]: warning: No devices found on the 'usb' bus. If this isn't the result you are expecting,
Nov  8 17:34:14 uue16 python: hp-probe[8148]: warning: check to make sure your devices are properly connected and powered on.
Nov  8 17:34:14 uue16 hal_lpadmin: HPLIP Fax URIs: None
Nov  8 17:34:14 uue16 hal_lpadmin: Not adding printer: Photosmart_8200_series already exists
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:14 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:14 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:14 uue16 snort[8093]: Tagged Packet Limit: 256 
Nov  8 17:34:14 uue16 snort[8093]:  
Nov  8 17:34:14 uue16 snort[8093]: +-----------------------[thresholding-config]---------------------------------- 
Nov  8 17:34:14 uue16 snort[8093]: | memory-cap : 1048576 bytes 
Nov  8 17:34:14 uue16 snort[8093]: +-----------------------[thresholding-global]---------------------------------- 
Nov  8 17:34:14 uue16 snort[8093]: | none 
Nov  8 17:34:14 uue16 snort[8093]: +-----------------------[thresholding-local]----------------------------------- 
Nov  8 17:34:14 uue16 snort[8093]: | none 
Nov  8 17:34:14 uue16 snort[8093]: +-----------------------[suppression]------------------------------------------ 
Nov  8 17:34:14 uue16 snort[8093]: | none 
Nov  8 17:34:14 uue16 snort[8093]: ------------------------------------------------------------------------------- 
Nov  8 17:34:14 uue16 snort[8093]: Rule application order: activation->dynamic->pass->drop->alert->log 
Nov  8 17:34:14 uue16 snort[8093]: Log directory = /var/log/snort 
Nov  8 17:34:14 uue16 snort[8093]: Loading dynamic engine /usr/lib/snort_dynamicengine/libsf_engine.so... 
Nov  8 17:34:14 uue16 snort[8093]: done 
Nov  8 17:34:14 uue16 snort[8093]: Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/... 
Nov  8 17:34:14 uue16 snort[8093]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ssh_preproc.so... 
Nov  8 17:34:14 uue16 snort[8093]: done 
Nov  8 17:34:14 uue16 snort[8093]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dns_preproc.so... 
Nov  8 17:34:14 uue16 snort[8093]: done 
Nov  8 17:34:14 uue16 snort[8093]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ftptelnet_preproc.so... 
Nov  8 17:34:14 uue16 snort[8093]: done 
Nov  8 17:34:14 uue16 snort[8093]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dcerpc_preproc.so... 
Nov  8 17:34:14 uue16 snort[8093]: done 
Nov  8 17:34:14 uue16 snort[8093]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_smtp_preproc.so... 
Nov  8 17:34:14 uue16 snort[8093]: done 
Nov  8 17:34:14 uue16 snort[8093]:   Finished Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/ 
Nov  8 17:34:14 uue16 snort[8093]: FTPTelnet Config: 
Nov  8 17:34:14 uue16 snort[8093]:     GLOBAL CONFIG 
Nov  8 17:34:14 uue16 snort[8093]:       Inspection Type: stateful 
Nov  8 17:34:14 uue16 snort[8093]:       Check for Encrypted Traffic: YES alert: YES 
Nov  8 17:34:14 uue16 snort[8093]:       Continue to check encrypted data: NO 
Nov  8 17:34:14 uue16 snort[8093]:     TELNET CONFIG: 
Nov  8 17:34:14 uue16 snort[8093]:       Ports: 23  
Nov  8 17:34:14 uue16 snort[8093]:       Are You There Threshold: 200 
Nov  8 17:34:14 uue16 snort[8093]:       Normalize: YES 
Nov  8 17:34:14 uue16 snort[8093]:       Detect Anomalies: NO 
Nov  8 17:34:14 uue16 snort[8093]:     FTP CONFIG: 
Nov  8 17:34:14 uue16 snort[8093]:       FTP Server: default 
Nov  8 17:34:14 uue16 snort[8093]:         Ports: 21  
Nov  8 17:34:14 uue16 snort[8093]:         Check for Telnet Cmds: YES alert: YES 
Nov  8 17:34:14 uue16 snort[8093]:         Identify open data channels: YES 
Nov  8 17:34:14 uue16 snort[8093]:       FTP Client: default 
Nov  8 17:34:14 uue16 snort[8093]:         Check for Bounce Attacks: YES alert: YES 
Nov  8 17:34:14 uue16 snort[8093]:         Check for Telnet Cmds: YES alert: YES 
Nov  8 17:34:14 uue16 snort[8093]:         Max Response Length: 256 
Nov  8 17:34:14 uue16 snort[8093]: SMTP Config: 
Nov  8 17:34:14 uue16 snort[8093]:       Ports: 
Nov  8 17:34:14 uue16 snort[8093]: 25 
Nov  8 17:34:14 uue16 snort[8093]:  
Nov  8 17:34:14 uue16 snort[8093]:       Inspection Type:            STATEFUL 
Nov  8 17:34:14 uue16 snort[8093]:       Normalize Spaces:           YES 
Nov  8 17:34:14 uue16 snort[8093]:       Ignore Data:                NO 
Nov  8 17:34:14 uue16 snort[8093]:       Ignore TLS Data:            NO 
Nov  8 17:34:14 uue16 snort[8093]:       Ignore Alerts:              NO 
Nov  8 17:34:14 uue16 snort[8093]:       Max Command Length:         0 
Nov  8 17:34:14 uue16 snort[8093]:       Max Header Line Length:     0 
Nov  8 17:34:14 uue16 snort[8093]:       Max Response Line Length:   0 
Nov  8 17:34:14 uue16 snort[8093]:       X-Link2State Alert:         YES 
Nov  8 17:34:14 uue16 snort[8093]:       Drop on X-Link2State Alert: NO 
Nov  8 17:34:14 uue16 snort[8093]:  DCE/RPC Decoder config: 
Nov  8 17:34:14 uue16 snort[8093]:     Autodetect ports ENABLED 
Nov  8 17:34:14 uue16 snort[8093]:     SMB fragmentation ENABLED 
Nov  8 17:34:14 uue16 snort[8093]:     DCE/RPC fragmentation ENABLED 
Nov  8 17:34:14 uue16 snort[8093]:     Max Frag Size: 3000 bytes 
Nov  8 17:34:14 uue16 snort[8093]:     Memcap: 100000 KB 
Nov  8 17:34:14 uue16 snort[8093]:     Alert if memcap exceeded DISABLED 
Nov  8 17:34:14 uue16 snort[8093]:  
Nov  8 17:34:14 uue16 snort[8093]: DNS config:  
Nov  8 17:34:14 uue16 snort[8093]:     DNS Client rdata txt Overflow Alert: ACTIVE 
Nov  8 17:34:14 uue16 snort[8093]:     Obsolete DNS RR Types Alert: INACTIVE 
Nov  8 17:34:14 uue16 snort[8093]:     Experimental DNS RR Types Alert: INACTIVE 
Nov  8 17:34:14 uue16 snort[8093]:     Ports:
Nov  8 17:34:14 uue16 snort[8093]:  53
Nov  8 17:34:14 uue16 snort[8093]:  
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:14 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:14 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:14 uue16 snort[8093]: Warning: flowbits key 'realplayer.playlist' is checked but not ever set. 
Nov  8 17:34:14 uue16 snort[8093]: Warning: flowbits key 'smb.tree.create.llsrpc' is set but not ever checked. 
Nov  8 17:34:14 uue16 snort[8093]: Warning: flowbits key 'community_uri.size.1050' is set but not ever checked. 
Nov  8 17:34:14 uue16 snort[8093]: Warning: flowbits key 'ms_sql_seen_dns' is checked but not ever set. 
Nov  8 17:34:14 uue16 snort[8093]: 37 out of 512 flowbits in use. 
Nov  8 17:34:14 uue16 kernel: [   52.194269] device eth0 entered promiscuous mode
Nov  8 17:34:14 uue16 kernel: [   52.194280] audit(1194564854.215:4): dev=eth0 prom=256 old_prom=0 auid=4294967295
Nov  8 17:34:14 uue16 snort[8093]: Initializing daemon mode 
Nov  8 17:34:14 uue16 kernel: [   52.226178] device eth0 left promiscuous mode
Nov  8 17:34:14 uue16 kernel: [   52.226186] audit(1194564854.714:5): dev=eth0 prom=0 old_prom=256 auid=4294967295
Nov  8 17:34:14 uue16 kernel: [   52.242139] device eth0 entered promiscuous mode
Nov  8 17:34:14 uue16 snort[8217]: PID path stat checked out ok, PID path set to /var/run/ 
Nov  8 17:34:14 uue16 snort[8217]: Writing PID "8217" to file "/var/run//snort_eth0.pid" 
Nov  8 17:34:14 uue16 snort[8093]: Daemon parent exiting 
Nov  8 17:34:14 uue16 kernel: [   52.242147] audit(1194564854.714:6): dev=eth0 prom=256 old_prom=0 auid=4294967295
Nov  8 17:34:14 uue16 snort[8217]: Daemon initialized, signaled parent pid: 8093 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:14 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:14 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 17:34:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:14 uue16 kernel: [   52.418511] Failure registering capabilities with primary security module.
Nov  8 17:34:14 uue16 avahi-daemon[8425]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Nov  8 17:34:14 uue16 avahi-daemon[8425]: Successfully dropped root privileges.
Nov  8 17:34:14 uue16 avahi-daemon[8425]: avahi-daemon 0.6.20 starting up.
Nov  8 17:34:14 uue16 avahi-daemon[8425]: Successfully called chroot().
Nov  8 17:34:14 uue16 avahi-daemon[8425]: Successfully dropped remaining capabilities.
Nov  8 17:34:14 uue16 avahi-daemon[8425]: No service file found in /etc/avahi/services.
Nov  8 17:34:14 uue16 avahi-daemon[8425]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.20.253.
Nov  8 17:34:14 uue16 avahi-daemon[8425]: New relevant interface eth0.IPv4 for mDNS.
Nov  8 17:34:14 uue16 avahi-daemon[8425]: Network interface enumeration completed.
Nov  8 17:34:14 uue16 avahi-daemon[8425]: Registering new address record for fe80::215:f2ff:fea0:f8e6 on eth0.*.
Nov  8 17:34:14 uue16 avahi-daemon[8425]: Registering new address record for 192.168.20.253 on eth0.IPv4.
Nov  8 17:34:14 uue16 avahi-daemon[8425]: Registering HINFO record with values 'I686'/'LINUX'.
Nov  8 17:34:15 uue16 dhcdbd: Started up.
Nov  8 17:34:15 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 17:34:15 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 17:34:15 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 17:34:15 uue16 python: hp-probe[8467]: warning: No devices found on the 'usb' bus. If this isn't the result you are expecting,
Nov  8 17:34:15 uue16 python: hp-probe[8467]: warning: check to make sure your devices are properly connected and powered on.
Nov  8 17:34:15 uue16 kernel: [   53.103992] eth0: no IPv6 routers present
Nov  8 17:34:15 uue16 avahi-daemon[8425]: Server startup complete. Host name is uue16.local. Local service cookie is 3706980048.
Nov  8 17:34:17 uue16 hcid[8593]: Bluetooth HCI daemon
Nov  8 17:34:17 uue16 kernel: [   54.571042] Bluetooth: Core ver 2.11
Nov  8 17:34:17 uue16 kernel: [   54.571298] NET: Registered protocol family 31
Nov  8 17:34:17 uue16 kernel: [   54.571302] Bluetooth: HCI device and connection manager initialized
Nov  8 17:34:17 uue16 kernel: [   54.571306] Bluetooth: HCI socket layer initialized
Nov  8 17:34:17 uue16 hcid[8593]: Starting SDP server
Nov  8 17:34:17 uue16 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Nov  8 17:34:17 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 17:34:17 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 17:34:17 uue16 NetworkManager: <debug> [1194564857.132927] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if0_printer_MY5AR3X0H504KK'). 
Nov  8 17:34:17 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 17:34:17 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 17:34:17 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 17:34:17 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 17:34:17 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 17:34:17 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 17:34:17 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 17:34:17 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 17:34:17 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 17:34:17 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 17:34:17 uue16 kernel: [   54.658092] Bluetooth: L2CAP ver 2.8
Nov  8 17:34:17 uue16 kernel: [   54.658096] Bluetooth: L2CAP socket layer initialized
Nov  8 17:34:17 uue16 hcid[8593]: Created local server at unix:abstract=/var/run/dbus-v2h0kflJSM,guid=9346720b7a7f48960461ba0047339cf9
Nov  8 17:34:17 uue16 audio[8640]: Bluetooth Audio daemon
Nov  8 17:34:17 uue16 audio[8640]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Nov  8 17:34:17 uue16 audio[8640]: Unix socket created: 5
Nov  8 17:34:17 uue16 kernel: [   54.748514] Bluetooth: RFCOMM socket layer initialized
Nov  8 17:34:17 uue16 kernel: [   54.748529] Bluetooth: RFCOMM TTY layer initialized
Nov  8 17:34:17 uue16 kernel: [   54.748532] Bluetooth: RFCOMM ver 1.8
Nov  8 17:34:17 uue16 input[8641]: Bluetooth Input daemon
Nov  8 17:34:17 uue16 input[8641]: Registered input manager path:/org/bluez/input
Nov  8 17:34:17 uue16 audio[8640]: add_service_record: got record id 0x10000
Nov  8 17:34:17 uue16 audio[8640]: add_service_record: got record id 0x10001
Nov  8 17:34:17 uue16 audio[8640]: Registered manager path:/org/bluez/audio
Nov  8 17:34:18 uue16 NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Nov  8 17:34:18 uue16 NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Nov  8 17:34:18 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 17:34:19 uue16 NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Nov  8 17:34:19 uue16 anacron[8883]: Anacron 2.3 started on 2007-11-08
Nov  8 17:34:19 uue16 anacron[8883]: Normal exit (0 jobs run)
Nov  8 17:34:19 uue16 /usr/sbin/cron[8910]: (CRON) INFO (pidfile fd = 3)
Nov  8 17:34:19 uue16 /usr/sbin/cron[8911]: (CRON) STARTUP (fork ok)
Nov  8 17:34:19 uue16 /usr/sbin/cron[8911]: (CRON) INFO (Running @reboot jobs)
Nov  8 17:34:20 uue16 gdm[8790]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov  8 17:34:20 uue16 snort[8217]: Preprocessor/Decoder Rule Count: 0 
Nov  8 17:34:20 uue16 snort[8217]: Snort initialization completed successfully (pid=8217) 
Nov  8 17:34:20 uue16 snort[8217]: Not Using PCAP_FRAMES 
Nov  8 17:34:23 uue16 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Nov  8 17:34:24 uue16 gdm[8958]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov  8 17:34:26 uue16 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Nov  8 17:34:28 uue16 gdm[9166]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov  8 17:34:28 uue16 gdm[8779]: CRITICAL: gdm_config_value_get_bool: assertion `value->type == GDM_CONFIG_VALUE_BOOL' failed 
Nov  8 17:34:32 uue16 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Nov  8 17:34:44 uue16 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Nov  8 17:34:46 uue16 gdm[8779]: CRITICAL: gdm_config_value_get_bool: assertion `value->type == GDM_CONFIG_VALUE_BOOL' failed 
Nov  8 17:34:54 uue16 dhclient: No DHCPOFFERS received.
Nov  8 17:34:54 uue16 avahi-autoipd(eth1)[9383]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Nov  8 17:34:54 uue16 avahi-autoipd(eth1)[9383]: Successfully called chroot().
Nov  8 17:34:54 uue16 avahi-autoipd(eth1)[9383]: Successfully dropped root privileges.
Nov  8 17:34:54 uue16 avahi-autoipd(eth1)[9383]: Starting with address 169.254.12.33
Nov  8 17:34:59 uue16 avahi-autoipd(eth1)[9383]: Callout BIND, address 169.254.12.33 on interface eth1
Nov  8 17:34:59 uue16 avahi-daemon[8425]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.12.33.
Nov  8 17:34:59 uue16 avahi-daemon[8425]: New relevant interface eth1.IPv4 for mDNS.
Nov  8 17:34:59 uue16 avahi-daemon[8425]: Registering new address record for 169.254.12.33 on eth1.IPv4.
Nov  8 17:35:03 uue16 avahi-autoipd(eth1)[9383]: Successfully claimed IP address 169.254.12.33
Nov  8 17:35:03 uue16 NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface eth1 
Nov  8 17:35:03 uue16 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Nov  8 17:35:03 uue16 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Nov  8 17:35:03 uue16 NetworkManager: <info>  No DHCP reply received.  Automatically obtaining IP via Zeroconf. 
Nov  8 17:35:03 uue16 NetworkManager: <info>  avahi-autoipd running on eth1, assuming IPv4LL address 
Nov  8 17:35:03 uue16 NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov  8 17:35:03 uue16 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Nov  8 17:35:03 uue16 NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Nov  8 17:35:03 uue16 NetworkManager: <info>  not touching eth1 configuration, was configured externally 
Nov  8 17:35:03 uue16 NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Nov  8 17:35:03 uue16 NetworkManager: <info>  Activation (eth1) successful, device activated. 
Nov  8 17:35:03 uue16 NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Nov  8 17:35:03 uue16 dhcdbd: Unrequested down ?:3
Nov  8 17:35:03 uue16 NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Nov  8 17:35:06 uue16 ntpdate[9423]: adjust time server 91.189.94.4 offset 0.226763 sec
Nov  8 17:35:11 uue16 gdm[8779]: WARNING: Failed to start X server several times in a short time period; disabling display :0 
Nov  8 17:38:52 uue16 init: tty4 main process (6196) killed by TERM signal
Nov  8 17:38:52 uue16 init: tty5 main process (6197) killed by TERM signal
Nov  8 17:38:52 uue16 init: tty1 main process (6203) killed by TERM signal
Nov  8 17:38:52 uue16 init: tty3 main process (6201) killed by TERM signal
Nov  8 17:38:52 uue16 init: tty2 main process (6199) killed by TERM signal
Nov  8 17:38:52 uue16 init: tty6 main process (6204) killed by TERM signal
Nov  8 17:38:53 uue16 avahi-daemon[8425]: Got SIGTERM, quitting.
Nov  8 17:38:53 uue16 avahi-daemon[8425]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.12.33.
Nov  8 17:38:53 uue16 avahi-daemon[8425]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.20.253.
Nov  8 17:38:55 uue16 atieventsd[7532]: Closing acpid connection 
Nov  8 17:38:55 uue16 atieventsd[7532]: Closing control socket 
Nov  8 17:38:55 uue16 atieventsd[7532]: ATI External Events Daemon shutting down 
Nov  8 17:38:56 uue16 rpc.statd[6006]: Caught signal 15, un-registering and exiting.
Nov  8 17:38:56 uue16 snort[8217]: *** Caught Term-Signal 
Nov  8 17:38:56 uue16 snort[8217]: Frag3 statistics: 
Nov  8 17:38:56 uue16 snort[8217]:         Total Fragments: 0 
Nov  8 17:38:56 uue16 snort[8217]:       Frags Reassembled: 0 
Nov  8 17:38:56 uue16 snort[8217]:                Discards: 0 
Nov  8 17:38:56 uue16 snort[8217]:           Memory Faults: 0 
Nov  8 17:38:56 uue16 snort[8217]:                Timeouts: 0 
Nov  8 17:38:56 uue16 snort[8217]:                Overlaps: 0 
Nov  8 17:38:56 uue16 snort[8217]:               Anomalies: 0 
Nov  8 17:38:56 uue16 snort[8217]:                  Alerts: 0 
Nov  8 17:38:56 uue16 snort[8217]:      FragTrackers Added: 0 
Nov  8 17:38:56 uue16 snort[8217]:     FragTrackers Dumped: 0 
Nov  8 17:38:56 uue16 snort[8217]: FragTrackers Auto Freed: 0 
Nov  8 17:38:56 uue16 snort[8217]:     Frag Nodes Inserted: 0 
Nov  8 17:38:56 uue16 snort[8217]:      Frag Nodes Deleted: 0 
Nov  8 17:38:56 uue16 snort[8217]: =============================================================================== 
Nov  8 17:38:56 uue16 snort[8217]: Stream5 statistics: 
Nov  8 17:38:56 uue16 snort[8217]:             Total sessions: 0 
Nov  8 17:38:56 uue16 snort[8217]:               TCP sessions: 0 
Nov  8 17:38:56 uue16 snort[8217]:               UDP sessions: 0 
Nov  8 17:38:56 uue16 snort[8217]:              ICMP sessions: 0 
Nov  8 17:38:56 uue16 snort[8217]:                 TCP Prunes: 0 
Nov  8 17:38:56 uue16 snort[8217]:                 UDP Prunes: 0 
Nov  8 17:38:56 uue16 snort[8217]:                ICMP Prunes: 0 
Nov  8 17:38:56 uue16 snort[8217]: TCP StreamTrackers Created: 0 
Nov  8 17:38:56 uue16 snort[8217]: TCP StreamTrackers Deleted: 0 
Nov  8 17:38:56 uue16 snort[8217]:               TCP Timeouts: 0 
Nov  8 17:38:56 uue16 snort[8217]:               TCP Overlaps: 0 
Nov  8 17:38:56 uue16 snort[8217]:        TCP Segments Queued: 0 
Nov  8 17:38:56 uue16 snort[8217]:      TCP Segments Released: 0 
Nov  8 17:38:56 uue16 snort[8217]:        TCP Rebuilt Packets: 0 
Nov  8 17:38:56 uue16 snort[8217]:          TCP Segments Used: 0 
Nov  8 17:38:56 uue16 snort[8217]:               TCP Discards: 0 
Nov  8 17:38:56 uue16 snort[8217]:       UDP Sessions Created: 0 
Nov  8 17:38:56 uue16 snort[8217]:       UDP Sessions Deleted: 0 
Nov  8 17:38:56 uue16 snort[8217]:               UDP Timeouts: 0 
Nov  8 17:38:56 uue16 snort[8217]:               UDP Discards: 0 
Nov  8 17:38:56 uue16 snort[8217]:                     Events: 0 
Nov  8 17:38:56 uue16 snort[8217]: =============================================================================== 
Nov  8 17:38:56 uue16 snort[8217]: Final Flow Statistics 
Nov  8 17:38:56 uue16 snort[8217]: ,----[ FLOWCACHE STATS ]---------- 
Nov  8 17:38:56 uue16 snort[8217]: Memcap: 10485760 Overhead Bytes 16400 used(%0.163231)/blocks (17116/5) Overhead blocks: 1 Could Hold: (58579) 
Nov  8 17:38:56 uue16 snort[8217]: IPV4 count: 4 frees: 0 low_time: 1194564903, high_time: 1194565133, diff: 0h:03:50s 
Nov  8 17:38:56 uue16 snort[8217]:     finds: 13 reversed: 0(%0.000000)      find_success: 9 find_fail: 4 percent_success: (%69.230769) new_flows: 4 
Nov  8 17:38:56 uue16 snort[8217]:  Protocol: 2 (%23.076923)    finds: 3    reversed: 0(%0.000000)    find_success: 2    find_fail: 1    percent_success: (%66.666667)    new_flows: 1 
Nov  8 17:38:56 uue16 snort[8217]:  Protocol: 17 (%76.923077)    finds: 10    reversed: 0(%0.000000)    find_success: 7    find_fail: 3    percent_success: (%70.000000)    new_flows: 3 
Nov  8 17:38:56 uue16 snort[8217]: Snort received 57 packets 
Nov  8 17:38:56 uue16 snort[8217]:     Analyzed: 56(98.246%) 
Nov  8 17:38:56 uue16 snort[8217]:     Dropped: 0(0.000%) 
Nov  8 17:38:56 uue16 snort[8217]:     Outstanding: 1(1.754%) 
Nov  8 17:38:56 uue16 snort[8217]: =============================================================================== 
Nov  8 17:38:56 uue16 snort[8217]: Breakdown by protocol: 
Nov  8 17:38:56 uue16 snort[8217]:       TCP: 0          (0.000%)           
Nov  8 17:38:57 uue16 snort[8217]:       UDP: 46         (82.143%)          
Nov  8 17:38:57 uue16 snort[8217]:      ICMP: 0          (0.000%)           
Nov  8 17:38:57 uue16 snort[8217]:       ARP: 2          (3.571%) 
Nov  8 17:38:57 uue16 snort[8217]:     EAPOL: 0          (0.000%) 
Nov  8 17:38:57 uue16 snort[8217]:      IPv6: 0          (0.000%) 
Nov  8 17:38:57 uue16 snort[8217]:   ETHLOOP: 0          (0.000%) 
Nov  8 17:38:57 uue16 snort[8217]:       IPX: 0          (0.000%) 
Nov  8 17:38:57 uue16 snort[8217]:      FRAG: 0          (0.000%)          
Nov  8 17:38:57 uue16 snort[8217]:     OTHER: 8          (14.286%) 
Nov  8 17:38:57 uue16 snort[8217]:   DISCARD: 0          (0.000%) 
Nov  8 17:38:57 uue16 snort[8217]: InvChkSum: 36         (64.286%) 
Nov  8 17:38:57 uue16 snort[8217]: =============================================================================== 
Nov  8 17:38:57 uue16 snort[8217]: Action Stats: 
Nov  8 17:38:57 uue16 snort[8217]: ALERTS: 0 
Nov  8 17:38:57 uue16 snort[8217]: LOGGED: 0 
Nov  8 17:38:57 uue16 snort[8217]: PASSED: 0 
Nov  8 17:38:57 uue16 snort[8217]: =============================================================================== 
Nov  8 17:38:57 uue16 snort[8217]: Snort exiting 
Nov  8 17:38:57 uue16 snort[8217]: Could not remove pid file /var/run//snort_eth0.pid: Permission denied 
Nov  8 17:38:57 uue16 kernel: [  333.549265] device eth0 left promiscuous mode
Nov  8 17:38:57 uue16 kernel: [  333.549275] audit(1194565136.844:7): dev=eth0 prom=0 old_prom=256 auid=4294967295
Nov  8 17:38:57 uue16 mysqld[7295]: 071108 17:38:57 [Note] /usr/sbin/mysqld: Normal shutdown
Nov  8 17:38:57 uue16 mysqld[7295]: 
Nov  8 17:38:57 uue16 mysqld[7295]: 071108 17:38:57  InnoDB: Starting shutdown...
Nov  8 17:38:58 uue16 mysqld[7295]: 071108 17:38:58  InnoDB: Shutdown completed; log sequence number 0 43655
Nov  8 17:38:58 uue16 mysqld[7295]: 071108 17:38:58 [Note] /usr/sbin/mysqld: Shutdown complete
Nov  8 17:38:58 uue16 mysqld[7295]: 
Nov  8 17:38:58 uue16 mysqld_safe[9850]: ended
Nov  8 17:39:01 uue16 /USR/SBIN/CRON[9906]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov  8 17:39:02 uue16 mountd[7942]: Caught signal 15, un-registering and exiting.
Nov  8 17:39:02 uue16 kernel: [  339.176225] nfsd: last server has exited
Nov  8 17:39:02 uue16 kernel: [  339.176231] nfsd: unexporting all filesystems
Nov  8 17:39:02 uue16 kernel: [  339.177657] RPC: failed to contact local rpcbind server (errno 5).
Nov  8 17:39:02 uue16 exiting on signal 15
Nov  8 17:40:27 uue16 syslogd 1.4.1#21ubuntu3: restart.
Nov  8 17:40:27 uue16 kernel: Inspecting /boot/System.map-2.6.22-14-generic
Nov  8 17:40:27 uue16 kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Nov  8 17:40:27 uue16 kernel: Symbols match kernel version 2.6.22.
Nov  8 17:40:27 uue16 kernel: No module symbols loaded - kernel modules not enabled. 
Nov  8 17:40:27 uue16 kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Nov  8 17:40:27 uue16 kernel: [    0.000000] BIOS-provided physical RAM map:
Nov  8 17:40:27 uue16 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov  8 17:40:27 uue16 kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov  8 17:40:27 uue16 kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Nov  8 17:40:27 uue16 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff80000 (usable)
Nov  8 17:40:27 uue16 kernel: [    0.000000]  BIOS-e820: 00000000bff80000 - 00000000bff8e000 (ACPI data)
Nov  8 17:40:27 uue16 kernel: [    0.000000]  BIOS-e820: 00000000bff8e000 - 00000000bffe0000 (ACPI NVS)
Nov  8 17:40:27 uue16 kernel: [    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
Nov  8 17:40:27 uue16 kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Nov  8 17:40:27 uue16 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Nov  8 17:40:27 uue16 kernel: [    0.000000] Warning only 4GB will be used.
Nov  8 17:40:27 uue16 kernel: [    0.000000] Use a PAE enabled kernel.
Nov  8 17:40:27 uue16 kernel: [    0.000000] 3200MB HIGHMEM available.
Nov  8 17:40:27 uue16 kernel: [    0.000000] 896MB LOWMEM available.
Nov  8 17:40:27 uue16 kernel: [    0.000000] found SMP MP-table at 000ff780
Nov  8 17:40:27 uue16 kernel: [    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
Nov  8 17:40:27 uue16 kernel: [    0.000000] Zone PFN ranges:
Nov  8 17:40:27 uue16 kernel: [    0.000000]   DMA             0 ->     4096
Nov  8 17:40:27 uue16 kernel: [    0.000000]   Normal       4096 ->   229376
Nov  8 17:40:27 uue16 kernel: [    0.000000]   HighMem    229376 ->  1048576
Nov  8 17:40:27 uue16 kernel: [    0.000000] early_node_map[1] active PFN ranges
Nov  8 17:40:27 uue16 kernel: [    0.000000]     0:        0 ->  1048576
Nov  8 17:40:27 uue16 kernel: [    0.000000] On node 0 totalpages: 1048576
Nov  8 17:40:27 uue16 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov  8 17:40:27 uue16 kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov  8 17:40:27 uue16 kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Nov  8 17:40:27 uue16 kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Nov  8 17:40:27 uue16 kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Nov  8 17:40:27 uue16 kernel: [    0.000000]   HighMem zone: 6400 pages used for memmap
Nov  8 17:40:27 uue16 kernel: [    0.000000]   HighMem zone: 812800 pages, LIFO batch:31
Nov  8 17:40:27 uue16 kernel: [    0.000000] DMI 2.3 present.
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FA740 checksum 0
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: RSDP 000FA740, 0024 (r2 ACPIAM)
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: XSDT BFF80100, 0044 (r1 A M I  OEMXSDT   7000610 MSFT       97)
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: FACP BFF80290, 00F4 (r3 A M I  OEMFACP   7000610 MSFT       97)
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: DSDT BFF80410, 84CF (r1  A0411 A0411000        0 INTL  2002026)
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: FACS BFF8E000, 0040
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: APIC BFF80390, 0080 (r1 A M I  OEMAPIC   7000610 MSFT       97)
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: OEMB BFF8E040, 0066 (r1 A M I  AMI_OEM   7000610 MSFT       97)
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: MCFG BFF888E0, 003C (r1 A M I  OEMMCFG   7000610 MSFT       97)
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Nov  8 17:40:27 uue16 kernel: [    0.000000] Processor #0 15:6 APIC version 20
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Nov  8 17:40:27 uue16 kernel: [    0.000000] Processor #2 15:6 APIC version 20
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
Nov  8 17:40:27 uue16 kernel: [    0.000000] Processor #1 15:6 APIC version 20
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Nov  8 17:40:27 uue16 kernel: [    0.000000] Processor #3 15:6 APIC version 20
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Nov  8 17:40:27 uue16 kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov  8 17:40:27 uue16 kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov  8 17:40:27 uue16 kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov  8 17:40:27 uue16 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov  8 17:40:27 uue16 kernel: [    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3fb00000)
Nov  8 17:40:27 uue16 kernel: [    0.000000] Built 1 zonelists.  Total pages: 1040384
Nov  8 17:40:27 uue16 kernel: [    0.000000] Kernel command line: root=UUID=e8bee423-266f-49eb-8f99-a75d19ffa386 ro quiet splash
Nov  8 17:40:27 uue16 kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Nov  8 17:40:27 uue16 kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Nov  8 17:40:27 uue16 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov  8 17:40:27 uue16 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov  8 17:40:27 uue16 kernel: [    0.000000] Initializing CPU#0
Nov  8 17:40:27 uue16 kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov  8 17:40:27 uue16 kernel: [    0.000000] Detected 3472.827 MHz processor.
Nov  8 17:40:27 uue16 kernel: [   25.527316] Console: colour VGA+ 80x25
Nov  8 17:40:27 uue16 kernel: [   25.527525] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov  8 17:40:27 uue16 kernel: [   25.527785] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov  8 17:40:27 uue16 kernel: [   25.693540] Memory: 3099116k/4194304k available (2015k kernel code, 44952k reserved, 916k data, 364k init, 2227712k highmem)
Nov  8 17:40:27 uue16 kernel: [   25.693549] virtual kernel memory layout:
Nov  8 17:40:27 uue16 kernel: [   25.693550]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Nov  8 17:40:27 uue16 kernel: [   25.693551]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov  8 17:40:27 uue16 kernel: [   25.693552]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Nov  8 17:40:27 uue16 kernel: [   25.693553]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Nov  8 17:40:27 uue16 kernel: [   25.693554]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Nov  8 17:40:27 uue16 kernel: [   25.693555]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Nov  8 17:40:27 uue16 kernel: [   25.693556]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Nov  8 17:40:27 uue16 kernel: [   25.693558] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov  8 17:40:27 uue16 kernel: [   25.693589] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
Nov  8 17:40:27 uue16 kernel: [   25.773375] Calibrating delay using timer specific routine.. 6951.54 BogoMIPS (lpj=13903081)
Nov  8 17:40:27 uue16 kernel: [   25.773396] Security Framework v1.0.0 initialized
Nov  8 17:40:27 uue16 kernel: [   25.773400] SELinux:  Disabled at boot.
Nov  8 17:40:27 uue16 kernel: [   25.773411] Mount-cache hash table entries: 512
Nov  8 17:40:27 uue16 kernel: [   25.773512] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
Nov  8 17:40:27 uue16 kernel: [   25.773519] monitor/mwait feature present.
Nov  8 17:40:27 uue16 kernel: [   25.773521] using mwait in idle threads.
Nov  8 17:40:27 uue16 kernel: [   25.773527] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov  8 17:40:27 uue16 kernel: [   25.773529] CPU: L2 cache: 2048K
Nov  8 17:40:27 uue16 kernel: [   25.773531] CPU: Physical Processor ID: 0
Nov  8 17:40:27 uue16 kernel: [   25.773533] CPU: Processor Core ID: 0
Nov  8 17:40:27 uue16 kernel: [   25.773535] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e43d 00000000 00000001
Nov  8 17:40:27 uue16 kernel: [   25.773544] Compat vDSO mapped to ffffe000.
Nov  8 17:40:27 uue16 kernel: [   25.773556] Checking 'hlt' instruction... OK.
Nov  8 17:40:27 uue16 kernel: [   25.789405] SMP alternatives: switching to UP code
Nov  8 17:40:27 uue16 kernel: [   25.789756] Early unpacking initramfs... done
Nov  8 17:40:27 uue16 kernel: [   26.041715] ACPI: Core revision 20070126
Nov  8 17:40:27 uue16 kernel: [   26.041768] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov  8 17:40:27 uue16 kernel: [   26.045760] CPU0: Intel(R) Pentium(R) D CPU 3.46GHz stepping 02
Nov  8 17:40:27 uue16 kernel: [   26.045776] SMP alternatives: switching to SMP code
Nov  8 17:40:27 uue16 kernel: [   26.045846] Booting processor 1/1 eip 3000
Nov  8 17:40:27 uue16 kernel: [   26.056033] Initializing CPU#1
Nov  8 17:40:27 uue16 kernel: [   26.136308] Calibrating delay using timer specific routine.. 6945.73 BogoMIPS (lpj=13891469)
Nov  8 17:40:27 uue16 kernel: [   26.136317] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
Nov  8 17:40:27 uue16 kernel: [   26.136323] monitor/mwait feature present.
Nov  8 17:40:27 uue16 kernel: [   26.136329] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov  8 17:40:27 uue16 kernel: [   26.136331] CPU: L2 cache: 2048K
Nov  8 17:40:27 uue16 kernel: [   26.136334] CPU: Physical Processor ID: 0
Nov  8 17:40:27 uue16 kernel: [   26.136335] CPU: Processor Core ID: 0
Nov  8 17:40:27 uue16 kernel: [   26.136337] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e43d 00000000 00000001
Nov  8 17:40:27 uue16 kernel: [   26.136816] CPU1: Intel(R) Pentium(R) D CPU 3.46GHz stepping 02
Nov  8 17:40:27 uue16 kernel: [   26.136838] SMP alternatives: switching to SMP code
Nov  8 17:40:27 uue16 kernel: [   26.136909] Booting processor 2/2 eip 3000
Nov  8 17:40:27 uue16 kernel: [   26.147118] Initializing CPU#2
Nov  8 17:40:27 uue16 kernel: [   26.224051] Calibrating delay using timer specific routine.. 6945.78 BogoMIPS (lpj=13891564)
Nov  8 17:40:27 uue16 kernel: [   26.224058] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
Nov  8 17:40:27 uue16 kernel: [   26.224063] monitor/mwait feature present.
Nov  8 17:40:27 uue16 kernel: [   26.224068] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov  8 17:40:27 uue16 kernel: [   26.224070] CPU: L2 cache: 2048K
Nov  8 17:40:27 uue16 kernel: [   26.224072] CPU: Physical Processor ID: 0
Nov  8 17:40:27 uue16 kernel: [   26.224073] CPU: Processor Core ID: 1
Nov  8 17:40:27 uue16 kernel: [   26.224074] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e43d 00000000 00000001
Nov  8 17:40:27 uue16 kernel: [   26.224514] CPU2: Intel(R) Pentium(R) D CPU 3.46GHz stepping 02
Nov  8 17:40:27 uue16 kernel: [   26.224527] SMP alternatives: switching to SMP code
Nov  8 17:40:27 uue16 kernel: [   26.224543] Booting processor 3/3 eip 3000
Nov  8 17:40:27 uue16 kernel: [   26.234737] Initializing CPU#3
Nov  8 17:40:27 uue16 kernel: [   26.311794] Calibrating delay using timer specific routine.. 6945.83 BogoMIPS (lpj=13891664)
Nov  8 17:40:27 uue16 kernel: [   26.311802] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
Nov  8 17:40:27 uue16 kernel: [   26.311808] monitor/mwait feature present.
Nov  8 17:40:27 uue16 kernel: [   26.311813] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov  8 17:40:27 uue16 kernel: [   26.311816] CPU: L2 cache: 2048K
Nov  8 17:40:27 uue16 kernel: [   26.311818] CPU: Physical Processor ID: 0
Nov  8 17:40:27 uue16 kernel: [   26.311819] CPU: Processor Core ID: 1
Nov  8 17:40:27 uue16 kernel: [   26.311821] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e43d 00000000 00000001
Nov  8 17:40:27 uue16 kernel: [   26.312283] CPU3: Intel(R) Pentium(R) D CPU 3.46GHz stepping 02
Nov  8 17:40:27 uue16 kernel: [   26.312316] Total of 4 processors activated (27788.88 BogoMIPS).
Nov  8 17:40:27 uue16 kernel: [   26.312463] ENABLING IO-APIC IRQs
Nov  8 17:40:27 uue16 kernel: [   26.312639] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov  8 17:40:27 uue16 kernel: [   26.459451] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Nov  8 17:40:27 uue16 kernel: [   26.479433] checking TSC synchronization [CPU#0 -> CPU#2]:
Nov  8 17:40:27 uue16 kernel: [   26.499382] Measured 52 cycles TSC warp between CPUs, turning off TSC clock.
Nov  8 17:40:27 uue16 kernel: [    0.668000] Marking TSC unstable due to: check_tsc_sync_source failed.
Nov  8 17:40:27 uue16 kernel: [    0.672000] Brought up 4 CPUs
Nov  8 17:40:27 uue16 kernel: [    0.824000] migration_cost=4000,4000
Nov  8 17:40:27 uue16 kernel: [    0.824000] Booting paravirtualized kernel on bare hardware
Nov  8 17:40:27 uue16 kernel: [    0.824000] Time: 23:40:10  Date: 10/08/107
Nov  8 17:40:27 uue16 kernel: [    0.824000] NET: Registered protocol family 16
Nov  8 17:40:27 uue16 kernel: [    0.824000] EISA bus registered
Nov  8 17:40:27 uue16 kernel: [    0.824000] ACPI: bus type pci registered
Nov  8 17:40:27 uue16 kernel: [    0.824000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
Nov  8 17:40:27 uue16 kernel: [    0.824000] PCI: Using configuration type 1
Nov  8 17:40:27 uue16 kernel: [    0.824000] Setting up standard PCI resources
Nov  8 17:40:27 uue16 kernel: [    0.836000] ACPI: EC: Look up EC in DSDT
Nov  8 17:40:27 uue16 kernel: [    0.844000] ACPI: Interpreter enabled
Nov  8 17:40:27 uue16 kernel: [    0.844000] ACPI: (supports S0 S1 S3 S4 S5)
Nov  8 17:40:27 uue16 kernel: [    0.844000] ACPI: Using IOAPIC for interrupt routing
Nov  8 17:40:27 uue16 kernel: [    0.852000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov  8 17:40:27 uue16 kernel: [    0.852000] PCI: Probing PCI hardware (bus 00)
Nov  8 17:40:27 uue16 kernel: [    0.856000] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Nov  8 17:40:27 uue16 kernel: [    0.856000] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
Nov  8 17:40:27 uue16 kernel: [    0.856000] PCI: Transparent bridge - 0000:00:1e.0
Nov  8 17:40:27 uue16 kernel: [    0.856000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov  8 17:40:27 uue16 kernel: [    0.856000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Nov  8 17:40:27 uue16 kernel: [    0.856000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
Nov  8 17:40:27 uue16 kernel: [    0.856000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
Nov  8 17:40:27 uue16 kernel: [    0.856000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
Nov  8 17:40:27 uue16 kernel: [    0.856000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
Nov  8 17:40:27 uue16 kernel: [    0.860000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Nov  8 17:40:27 uue16 kernel: [    0.860000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Nov  8 17:40:27 uue16 kernel: [    0.860000] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
Nov  8 17:40:27 uue16 kernel: [    0.860000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Nov  8 17:40:27 uue16 kernel: [    0.860000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 *14 15)
Nov  8 17:40:27 uue16 kernel: [    0.860000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Nov  8 17:40:27 uue16 kernel: [    0.860000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Nov  8 17:40:27 uue16 kernel: [    0.860000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Nov  8 17:40:27 uue16 kernel: [    0.860000] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov  8 17:40:27 uue16 kernel: [    0.860000] pnp: PnP ACPI init
Nov  8 17:40:27 uue16 kernel: [    0.860000] ACPI: bus type pnp registered
Nov  8 17:40:27 uue16 kernel: [    0.864000] pnp: PnP ACPI: found 19 devices
Nov  8 17:40:27 uue16 kernel: [    0.864000] ACPI: ACPI bus type pnp unregistered
Nov  8 17:40:27 uue16 kernel: [    0.864000] PnPBIOS: Disabled by ACPI PNP
Nov  8 17:40:27 uue16 kernel: [    0.864000] PCI: Using ACPI for IRQ routing
Nov  8 17:40:27 uue16 kernel: [    0.864000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov  8 17:40:27 uue16 kernel: [    0.876000] NET: Registered protocol family 8
Nov  8 17:40:27 uue16 kernel: [    0.876000] NET: Registered protocol family 20
Nov  8 17:40:27 uue16 kernel: [    0.876000] pnp: 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
Nov  8 17:40:27 uue16 kernel: [    0.876000] pnp: 00:08: ioport range 0x290-0x297 has been reserved
Nov  8 17:40:27 uue16 kernel: [    0.876000] pnp: 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
Nov  8 17:40:27 uue16 kernel: [    0.876000] pnp: 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
Nov  8 17:40:27 uue16 kernel: [    0.876000] pnp: 00:09: iomem range 0xfed50000-0xfed8ffff has been reserved
Nov  8 17:40:27 uue16 kernel: [    0.876000] pnp: 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
Nov  8 17:40:27 uue16 kernel: [    0.876000] pnp: 00:0a: ioport range 0x3f6-0x3f6 has been reserved
Nov  8 17:40:27 uue16 kernel: [    0.876000] pnp: 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
Nov  8 17:40:27 uue16 kernel: [    0.876000] pnp: 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
Nov  8 17:40:27 uue16 kernel: [    0.876000] pnp: 00:11: iomem range 0xf0000000-0xf3ffffff has been reserved
Nov  8 17:40:27 uue16 kernel: [    0.876000] pnp: 00:12: iomem range 0x0-0x9ffff could not be reserved
Nov  8 17:40:27 uue16 kernel: [    0.876000] pnp: 00:12: iomem range 0xc0000-0xdffff could not be reserved
Nov  8 17:40:27 uue16 kernel: [    0.876000] pnp: 00:12: iomem range 0xe0000-0xfffff could not be reserved
Nov  8 17:40:27 uue16 kernel: [    0.876000] pnp: 00:12: iomem range 0x100000-0xbfffffff could not be reserved
Nov  8 17:40:27 uue16 kernel: [    0.908000] PCI: Bridge: 0000:00:01.0
Nov  8 17:40:27 uue16 kernel: [    0.908000]   IO window: c000-cfff
Nov  8 17:40:27 uue16 kernel: [    0.908000]   MEM window: fea00000-feafffff
Nov  8 17:40:27 uue16 kernel: [    0.908000]   PREFETCH window: cff00000-efefffff
Nov  8 17:40:27 uue16 kernel: [    0.908000] PCI: Bridge: 0000:00:1c.0
Nov  8 17:40:27 uue16 kernel: [    0.908000]   IO window: disabled.
Nov  8 17:40:27 uue16 kernel: [    0.908000]   MEM window: disabled.
Nov  8 17:40:27 uue16 kernel: [    0.908000]   PREFETCH window: cfe00000-cfefffff
Nov  8 17:40:27 uue16 kernel: [    0.908000] PCI: Bridge: 0000:00:1c.3
Nov  8 17:40:27 uue16 kernel: [    0.908000]   IO window: b000-bfff
Nov  8 17:40:27 uue16 kernel: [    0.908000]   MEM window: fe900000-fe9fffff
Nov  8 17:40:27 uue16 kernel: [    0.908000]   PREFETCH window: disabled.
Nov  8 17:40:27 uue16 kernel: [    0.908000] PCI: Bridge: 0000:00:1c.5
Nov  8 17:40:27 uue16 kernel: [    0.908000]   IO window: a000-afff
Nov  8 17:40:27 uue16 kernel: [    0.908000]   MEM window: fe800000-fe8fffff
Nov  8 17:40:27 uue16 kernel: [    0.908000]   PREFETCH window: disabled.
Nov  8 17:40:27 uue16 kernel: [    0.908000] PCI: Bridge: 0000:00:1e.0
Nov  8 17:40:27 uue16 kernel: [    0.908000]   IO window: 9000-9fff
Nov  8 17:40:27 uue16 kernel: [    0.908000]   MEM window: f6300000-fe7fffff
Nov  8 17:40:27 uue16 kernel: [    0.908000]   PREFETCH window: disabled.
Nov  8 17:40:27 uue16 kernel: [    0.908000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov  8 17:40:27 uue16 kernel: [    0.908000] PCI: Setting latency timer of device 0000:00:01.0 to 64
Nov  8 17:40:27 uue16 kernel: [    0.908000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov  8 17:40:27 uue16 kernel: [    0.908000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Nov  8 17:40:27 uue16 kernel: [    0.908000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Nov  8 17:40:27 uue16 kernel: [    0.908000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Nov  8 17:40:27 uue16 kernel: [    0.908000] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 18
Nov  8 17:40:27 uue16 kernel: [    0.908000] PCI: Setting latency timer of device 0000:00:1c.5 to 64
Nov  8 17:40:27 uue16 kernel: [    0.908000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Nov  8 17:40:27 uue16 kernel: [    0.908000] NET: Registered protocol family 2
Nov  8 17:40:27 uue16 kernel: [    0.912000] Time: acpi_pm clocksource has been installed.
Nov  8 17:40:27 uue16 kernel: [    0.912000] Switched to high resolution mode on CPU 0
Nov  8 17:40:27 uue16 kernel: [    0.912000] Switched to high resolution mode on CPU 1
Nov  8 17:40:27 uue16 kernel: [    0.912000] Switched to high resolution mode on CPU 2
Nov  8 17:40:27 uue16 kernel: [    0.912000] Switched to high resolution mode on CPU 3
Nov  8 17:40:27 uue16 kernel: [    0.956000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov  8 17:40:27 uue16 kernel: [    0.956000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Nov  8 17:40:27 uue16 kernel: [    0.956000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov  8 17:40:27 uue16 kernel: [    0.956000] TCP: Hash tables configured (established 131072 bind 65536)
Nov  8 17:40:27 uue16 kernel: [    0.956000] TCP reno registered
Nov  8 17:40:27 uue16 kernel: [    0.972000] checking if image is initramfs... it is
Nov  8 17:40:27 uue16 kernel: [    1.468000] Freeing initrd memory: 7343k freed
Nov  8 17:40:27 uue16 kernel: [    1.468000] audit: initializing netlink socket (disabled)
Nov  8 17:40:27 uue16 kernel: [    1.468000] audit(1194565210.412:1): initialized
Nov  8 17:40:27 uue16 kernel: [    1.468000] highmem bounce pool size: 64 pages
Nov  8 17:40:27 uue16 kernel: [    1.472000] VFS: Disk quotas dquot_6.5.1
Nov  8 17:40:27 uue16 kernel: [    1.472000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov  8 17:40:27 uue16 kernel: [    1.472000] io scheduler noop registered
Nov  8 17:40:27 uue16 kernel: [    1.472000] io scheduler anticipatory registered
Nov  8 17:40:27 uue16 kernel: [    1.472000] io scheduler deadline registered
Nov  8 17:40:27 uue16 kernel: [    1.472000] io scheduler cfq registered (default)
Nov  8 17:40:27 uue16 kernel: [    1.500000] Boot video device is 0000:05:00.0
Nov  8 17:40:27 uue16 kernel: [    1.500000] PCI: Setting latency timer of device 0000:00:01.0 to 64
Nov  8 17:40:27 uue16 kernel: [    1.500000] assign_interrupt_mode Found MSI capability
Nov  8 17:40:27 uue16 kernel: [    1.500000] Allocate Port Service[0000:00:01.0:pcie00]
Nov  8 17:40:27 uue16 kernel: [    1.500000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Nov  8 17:40:27 uue16 kernel: [    1.500000] assign_interrupt_mode Found MSI capability
Nov  8 17:40:27 uue16 kernel: [    1.500000] Allocate Port Service[0000:00:1c.0:pcie00]
Nov  8 17:40:27 uue16 kernel: [    1.500000] Allocate Port Service[0000:00:1c.0:pcie02]
Nov  8 17:40:27 uue16 kernel: [    1.500000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Nov  8 17:40:27 uue16 kernel: [    1.500000] assign_interrupt_mode Found MSI capability
Nov  8 17:40:27 uue16 kernel: [    1.500000] Allocate Port Service[0000:00:1c.3:pcie00]
Nov  8 17:40:27 uue16 kernel: [    1.500000] PCI: Setting latency timer of device 0000:00:1c.5 to 64
Nov  8 17:40:27 uue16 kernel: [    1.500000] assign_interrupt_mode Found MSI capability
Nov  8 17:40:27 uue16 kernel: [    1.500000] Allocate Port Service[0000:00:1c.5:pcie00]
Nov  8 17:40:27 uue16 kernel: [    1.500000] isapnp: Scanning for PnP cards...
Nov  8 17:40:27 uue16 kernel: [    1.852000] isapnp: No Plug & Play device found
Nov  8 17:40:27 uue16 kernel: [    1.876000] Real Time Clock Driver v1.12ac
Nov  8 17:40:27 uue16 kernel: [    1.876000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov  8 17:40:27 uue16 kernel: [    1.876000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov  8 17:40:27 uue16 kernel: [    1.876000] 00:10: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov  8 17:40:27 uue16 kernel: [    1.876000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov  8 17:40:27 uue16 kernel: [    1.876000] input: Macintosh mouse button emulation as /class/input/input0
Nov  8 17:40:27 uue16 kernel: [    1.876000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Nov  8 17:40:27 uue16 kernel: [    1.880000] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov  8 17:40:27 uue16 kernel: [    1.880000] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov  8 17:40:27 uue16 kernel: [    1.880000] mice: PS/2 mouse device common for all mice
Nov  8 17:40:27 uue16 kernel: [    1.880000] EISA: Probing bus 0 at eisa.0
Nov  8 17:40:27 uue16 kernel: [    1.880000] EISA: Detected 0 cards.
Nov  8 17:40:27 uue16 kernel: [    1.880000] TCP cubic registered
Nov  8 17:40:27 uue16 kernel: [    1.880000] NET: Registered protocol family 1
Nov  8 17:40:27 uue16 kernel: [    1.880000] Using IPI No-Shortcut mode
Nov  8 17:40:27 uue16 kernel: [    1.880000]   Magic number: 15:205:706
Nov  8 17:40:27 uue16 kernel: [    1.880000] Freeing unused kernel memory: 364k freed
Nov  8 17:40:27 uue16 kernel: [    1.896000] input: AT Translated Set 2 keyboard as /class/input/input1
Nov  8 17:40:27 uue16 kernel: [    3.076000] AppArmor: AppArmor initialized<5>audit(1194565211.912:2):  type=1505 info="AppArmor initialized" pid=1374
Nov  8 17:40:27 uue16 kernel: [    3.084000] fuse init (API version 7.8)
Nov  8 17:40:27 uue16 kernel: [    3.088000] Failure registering capabilities with primary security module.
Nov  8 17:40:27 uue16 kernel: [    3.212000] ACPI Warning (tbutils-0217): Incorrect checksum in table [  Qµ] -  00, should be 01 [20070126]
Nov  8 17:40:27 uue16 kernel: [    3.212000] ACPI Error (tbinstal-0134): Table has invalid signature [  Qµ], must be SSDT, PSDT or OEMx [20070126]
Nov  8 17:40:27 uue16 kernel: [    3.212000] ACPI Error (psparse-0551): Method parse/execution failed [\_PR_.CPU1._PDC] (Node df83b150), AE_BAD_SIGNATURE
Nov  8 17:40:27 uue16 kernel: [    3.212000] ACPI: Processor [CPU1] (supports 8 throttling states)
Nov  8 17:40:27 uue16 kernel: [    3.308000] ACPI Warning (tbutils-0217): Incorrect checksum in table [  Qµ] -  00, should be 01 [20070126]
Nov  8 17:40:27 uue16 kernel: [    3.308000] ACPI Error (tbinstal-0134): Table has invalid signature [  Qµ], must be SSDT, PSDT or OEMx [20070126]
Nov  8 17:40:27 uue16 kernel: [    3.308000] ACPI Error (psparse-0551): Method parse/execution failed [\_PR_.CPU2._PDC] (Node df83b1e0), AE_BAD_SIGNATURE
Nov  8 17:40:27 uue16 kernel: [    3.752000] usbcore: registered new interface driver usbfs
Nov  8 17:40:27 uue16 kernel: [    3.752000] usbcore: registered new interface driver hub
Nov  8 17:40:27 uue16 kernel: [    3.752000] usbcore: registered new device driver usb
Nov  8 17:40:27 uue16 kernel: [    3.752000] USB Universal Host Controller Interface driver v3.0
Nov  8 17:40:27 uue16 kernel: [    3.752000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
Nov  8 17:40:27 uue16 kernel: [    3.752000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Nov  8 17:40:27 uue16 kernel: [    3.752000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Nov  8 17:40:27 uue16 kernel: [    3.752000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Nov  8 17:40:27 uue16 kernel: [    3.752000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000e480
Nov  8 17:40:27 uue16 kernel: [    3.752000] usb usb1: configuration #1 chosen from 1 choice
Nov  8 17:40:27 uue16 kernel: [    3.752000] hub 1-0:1.0: USB hub found
Nov  8 17:40:27 uue16 kernel: [    3.752000] hub 1-0:1.0: 2 ports detected
Nov  8 17:40:27 uue16 kernel: [    3.780000] Floppy drive(s): fd0 is 1.44M
Nov  8 17:40:27 uue16 kernel: [    3.832000] SCSI subsystem initialized
Nov  8 17:40:27 uue16 kernel: [    3.848000] FDC 0 is a post-1991 82077
Nov  8 17:40:27 uue16 kernel: [    3.852000] libata version 2.21 loaded.
Nov  8 17:40:27 uue16 kernel: [    3.856000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
Nov  8 17:40:27 uue16 kernel: [    3.856000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Nov  8 17:40:27 uue16 kernel: [    3.856000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Nov  8 17:40:27 uue16 kernel: [    3.856000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Nov  8 17:40:27 uue16 kernel: [    3.856000] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000e800
Nov  8 17:40:27 uue16 kernel: [    3.856000] usb usb2: configuration #1 chosen from 1 choice
Nov  8 17:40:27 uue16 kernel: [    3.856000] hub 2-0:1.0: USB hub found
Nov  8 17:40:27 uue16 kernel: [    3.856000] hub 2-0:1.0: 2 ports detected
Nov  8 17:40:27 uue16 kernel: [    3.960000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
Nov  8 17:40:27 uue16 kernel: [    3.960000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Nov  8 17:40:27 uue16 kernel: [    3.960000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Nov  8 17:40:27 uue16 kernel: [    3.960000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Nov  8 17:40:27 uue16 kernel: [    3.960000] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000e880
Nov  8 17:40:27 uue16 kernel: [    3.960000] usb usb3: configuration #1 chosen from 1 choice
Nov  8 17:40:27 uue16 kernel: [    3.960000] hub 3-0:1.0: USB hub found
Nov  8 17:40:27 uue16 kernel: [    3.960000] hub 3-0:1.0: 2 ports detected
Nov  8 17:40:27 uue16 kernel: [    4.064000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17
Nov  8 17:40:27 uue16 kernel: [    4.064000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Nov  8 17:40:27 uue16 kernel: [    4.064000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Nov  8 17:40:27 uue16 kernel: [    4.064000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Nov  8 17:40:27 uue16 kernel: [    4.064000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000ec00
Nov  8 17:40:27 uue16 kernel: [    4.064000] usb usb4: configuration #1 chosen from 1 choice
Nov  8 17:40:27 uue16 kernel: [    4.064000] hub 4-0:1.0: USB hub found
Nov  8 17:40:27 uue16 kernel: [    4.064000] hub 4-0:1.0: 2 ports detected
Nov  8 17:40:27 uue16 kernel: [    4.096000] usb 1-1: new full speed USB device using uhci_hcd and address 2
Nov  8 17:40:27 uue16 kernel: [    4.168000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 21 (level, low) -> IRQ 21
Nov  8 17:40:27 uue16 kernel: [    4.168000] uhci_hcd 0000:01:00.0: UHCI Host Controller
Nov  8 17:40:27 uue16 kernel: [    4.168000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
Nov  8 17:40:27 uue16 kernel: [    4.168000] uhci_hcd 0000:01:00.0: new USB bus registered, assigned bus number 5
Nov  8 17:40:27 uue16 kernel: [    4.168000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Nov  8 17:40:27 uue16 kernel: [    4.168000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Nov  8 17:40:27 uue16 kernel: [    4.168000] uhci_hcd 0000:01:00.0: irq 21, io base 0x00009880
Nov  8 17:40:27 uue16 kernel: [    4.168000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 6
Nov  8 17:40:27 uue16 kernel: [    4.168000] ehci_hcd 0000:00:1d.7: debug port 1
Nov  8 17:40:27 uue16 kernel: [    4.168000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
Nov  8 17:40:27 uue16 kernel: [    4.168000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebfbc00
Nov  8 17:40:27 uue16 kernel: [    4.168000] usb usb5: configuration #1 chosen from 1 choice
Nov  8 17:40:27 uue16 kernel: [    4.168000] hub 5-0:1.0: USB hub found
Nov  8 17:40:27 uue16 kernel: [    4.168000] hub 5-0:1.0: 2 ports detected
Nov  8 17:40:27 uue16 kernel: [    4.216000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov  8 17:40:27 uue16 kernel: [    4.272000] ACPI: PCI Interrupt 0000:01:00.1[B] -> GSI 22 (level, low) -> IRQ 22
Nov  8 17:40:27 uue16 kernel: [    4.272000] uhci_hcd 0000:01:00.1: UHCI Host Controller
Nov  8 17:40:27 uue16 kernel: [    4.272000] usb usb6: configuration #1 chosen from 1 choice
Nov  8 17:40:27 uue16 kernel: [    4.272000] hub 6-0:1.0: USB hub found
Nov  8 17:40:27 uue16 kernel: [    4.272000] hub 6-0:1.0: 8 ports detected
Nov  8 17:40:27 uue16 kernel: [    4.376000] uhci_hcd 0000:01:00.1: new USB bus registered, assigned bus number 7
Nov  8 17:40:27 uue16 kernel: [    4.376000] uhci_hcd 0000:01:00.1: irq 22, io base 0x00009c00
Nov  8 17:40:27 uue16 kernel: [    4.376000] usb usb7: configuration #1 chosen from 1 choice
Nov  8 17:40:27 uue16 kernel: [    4.376000] hub 7-0:1.0: USB hub found
Nov  8 17:40:27 uue16 kernel: [    4.376000] hub 7-0:1.0: 2 ports detected
Nov  8 17:40:27 uue16 kernel: [    4.480000] ata_piix 0000:00:1f.1: version 2.11
Nov  8 17:40:27 uue16 kernel: [    4.480000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 22
Nov  8 17:40:27 uue16 kernel: [    4.480000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Nov  8 17:40:27 uue16 kernel: [    4.480000] scsi0 : ata_piix
Nov  8 17:40:27 uue16 kernel: [    4.480000] scsi1 : ata_piix
Nov  8 17:40:27 uue16 kernel: [    4.480000] ata1: PATA max UDMA/133 cmd 0x0001d800 ctl 0x0001d482 bmdma 0x0001d000 irq 22
Nov  8 17:40:27 uue16 kernel: [    4.480000] ata2: PATA max UDMA/133 cmd 0x0001d400 ctl 0x0001d082 bmdma 0x0001d008 irq 22
Nov  8 17:40:27 uue16 kernel: [    4.624000] usb 1-1: device not accepting address 2, error -71
Nov  8 17:40:27 uue16 kernel: [    4.656000] ata1.00: ATA-7: Maxtor 6B300R0, BAH41E00, max UDMA/133
Nov  8 17:40:27 uue16 kernel: [    4.656000] ata1.00: 586114704 sectors, multi 16: LBA48 
Nov  8 17:40:27 uue16 kernel: [    4.656000] ata1.01: ATA-6: ST340015ACE, 3.01, max UDMA/100
Nov  8 17:40:27 uue16 kernel: [    4.656000] ata1.01: 78165360 sectors, multi 16: LBA 
Nov  8 17:40:27 uue16 kernel: [    4.672000] ata1.00: configured for UDMA/133
Nov  8 17:40:27 uue16 kernel: [    4.688000] ata1.01: configured for UDMA/100
Nov  8 17:40:27 uue16 kernel: [    4.856000] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6B300R0   BAH4 PQ: 0 ANSI: 5
Nov  8 17:40:27 uue16 kernel: [    4.856000] scsi 0:0:1:0: Direct-Access     ATA      ST340015ACE      3.01 PQ: 0 ANSI: 5
Nov  8 17:40:27 uue16 kernel: [    4.856000] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Nov  8 17:40:27 uue16 kernel: [    4.856000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 23
Nov  8 17:40:27 uue16 kernel: [    4.856000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Nov  8 17:40:27 uue16 kernel: [    4.856000] scsi2 : ata_piix
Nov  8 17:40:27 uue16 kernel: [    4.856000] scsi3 : ata_piix
Nov  8 17:40:27 uue16 kernel: [    4.856000] ata3: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e082 bmdma 0x0001d880 irq 23
Nov  8 17:40:27 uue16 kernel: [    4.856000] ata4: SATA max UDMA/133 cmd 0x0001e000 ctl 0x0001dc02 bmdma 0x0001d888 irq 23
Nov  8 17:40:27 uue16 kernel: [    5.020000] ata3.00: ATA-6: WDC WD740GD-00FLC0, 33.08F33, max UDMA/133
Nov  8 17:40:27 uue16 kernel: [    5.020000] ata3.00: 145226112 sectors, multi 16: LBA48 
Nov  8 17:40:27 uue16 kernel: [    5.036000] ata3.00: configured for UDMA/133
Nov  8 17:40:27 uue16 kernel: [    5.388000] ata4.00: ATA-7: WDC WD3200KS-00PFB0, 21.00M21, max UDMA/133
Nov  8 17:40:27 uue16 kernel: [    5.388000] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/1)
Nov  8 17:40:27 uue16 kernel: [    5.388000] ata4.01: ATAPI: PLEXTOR DVDR   PX-755A, 1.06, max UDMA/66
Nov  8 17:40:27 uue16 kernel: [    5.404000] ata4.00: configured for UDMA/133
Nov  8 17:40:27 uue16 kernel: [    5.564000] usb 6-1: new high speed USB device using ehci_hcd and address 2
Nov  8 17:40:27 uue16 kernel: [    5.568000] ata4.01: configured for UDMA/66
Nov  8 17:40:27 uue16 kernel: [    5.568000] scsi 2:0:0:0: Direct-Access     ATA      WDC WD740GD-00FL 33.0 PQ: 0 ANSI: 5
Nov  8 17:40:27 uue16 kernel: [    5.568000] scsi 3:0:0:0: Direct-Access     ATA      WDC WD3200KS-00P 21.0 PQ: 0 ANSI: 5
Nov  8 17:40:27 uue16 kernel: [    5.568000] scsi 3:0:1:0: CD-ROM            PLEXTOR  DVDR   PX-755A   1.06 PQ: 0 ANSI: 5
Nov  8 17:40:27 uue16 kernel: [    5.568000] ACPI: PCI Interrupt 0000:01:00.2[C] -> GSI 23 (level, low) -> IRQ 23
Nov  8 17:40:27 uue16 kernel: [    5.568000] ehci_hcd 0000:01:00.2: EHCI Host Controller
Nov  8 17:40:27 uue16 kernel: [    5.568000] ehci_hcd 0000:01:00.2: new USB bus registered, assigned bus number 8
Nov  8 17:40:27 uue16 kernel: [    5.568000] ehci_hcd 0000:01:00.2: irq 23, io mem 0xfe6ffc00
Nov  8 17:40:27 uue16 kernel: [    5.680000] ehci_hcd 0000:01:00.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
Nov  8 17:40:27 uue16 kernel: [    5.680000] usb usb8: configuration #1 chosen from 1 choice
Nov  8 17:40:27 uue16 kernel: [    5.680000] hub 8-0:1.0: USB hub found
Nov  8 17:40:27 uue16 kernel: [    5.680000] hub 8-0:1.0: 4 ports detected
Nov  8 17:40:27 uue16 kernel: [    5.712000] usb 6-1: configuration #1 chosen from 1 choice
Nov  8 17:40:27 uue16 kernel: [    5.784000] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 21 (level, low) -> IRQ 21
Nov  8 17:40:27 uue16 kernel: [    5.832000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fe6ff000-fe6ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov  8 17:40:27 uue16 kernel: [    5.844000] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
Nov  8 17:40:27 uue16 kernel: [    5.844000] sd 0:0:0:0: [sda] Write Protect is off
Nov  8 17:40:27 uue16 kernel: [    5.844000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  8 17:40:27 uue16 kernel: [    5.844000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 17:40:27 uue16 kernel: [    5.844000] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
Nov  8 17:40:27 uue16 kernel: [    5.844000] sd 0:0:0:0: [sda] Write Protect is off
Nov  8 17:40:27 uue16 kernel: [    5.844000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  8 17:40:27 uue16 kernel: [    5.844000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 17:40:27 uue16 kernel: [    5.844000]  sda: sda1 sda2
Nov  8 17:40:27 uue16 kernel: [    5.864000] sd 0:0:0:0: [sda] Attached SCSI disk
Nov  8 17:40:27 uue16 kernel: [    5.864000] sd 0:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
Nov  8 17:40:27 uue16 kernel: [    5.864000] sd 0:0:1:0: [sdb] Write Protect is off
Nov  8 17:40:27 uue16 kernel: [    5.864000] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Nov  8 17:40:27 uue16 kernel: [    5.864000] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 17:40:27 uue16 kernel: [    5.864000] sd 0:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
Nov  8 17:40:27 uue16 kernel: [    5.864000] sd 0:0:1:0: [sdb] Write Protect is off
Nov  8 17:40:27 uue16 kernel: [    5.864000] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Nov  8 17:40:27 uue16 kernel: [    5.864000] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 17:40:27 uue16 kernel: [    5.864000]  sdb: sdb1 sdb2 < sdb5 >
Nov  8 17:40:27 uue16 kernel: [    5.916000] sd 0:0:1:0: [sdb] Attached SCSI disk
Nov  8 17:40:27 uue16 kernel: [    5.916000] sd 2:0:0:0: [sdc] 145226112 512-byte hardware sectors (74356 MB)
Nov  8 17:40:27 uue16 kernel: [    5.916000] sd 2:0:0:0: [sdc] Write Protect is off
Nov  8 17:40:27 uue16 kernel: [    5.916000] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Nov  8 17:40:27 uue16 kernel: [    5.916000] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 17:40:27 uue16 kernel: [    5.916000] sd 2:0:0:0: [sdc] 145226112 512-byte hardware sectors (74356 MB)
Nov  8 17:40:27 uue16 kernel: [    5.916000] sd 2:0:0:0: [sdc] Write Protect is off
Nov  8 17:40:27 uue16 kernel: [    5.916000] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Nov  8 17:40:27 uue16 kernel: [    5.916000] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 17:40:27 uue16 kernel: [    5.916000]  sdc: sdc1
Nov  8 17:40:27 uue16 kernel: [    5.924000] sd 2:0:0:0: [sdc] Attached SCSI disk
Nov  8 17:40:27 uue16 kernel: [    5.924000] sd 3:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
Nov  8 17:40:27 uue16 kernel: [    5.924000] sd 3:0:0:0: [sdd] Write Protect is off
Nov  8 17:40:27 uue16 kernel: [    5.924000] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Nov  8 17:40:27 uue16 kernel: [    5.924000] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 17:40:27 uue16 kernel: [    5.924000] sd 3:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
Nov  8 17:40:27 uue16 kernel: [    5.924000] sd 3:0:0:0: [sdd] Write Protect is off
Nov  8 17:40:27 uue16 kernel: [    5.924000] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Nov  8 17:40:27 uue16 kernel: [    5.924000] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 17:40:27 uue16 kernel: [    5.924000]  sdd: sdd1 sdd2 < sdd5 >
Nov  8 17:40:27 uue16 kernel: [    5.952000] sd 3:0:0:0: [sdd] Attached SCSI disk
Nov  8 17:40:27 uue16 kernel: [    5.956000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov  8 17:40:27 uue16 kernel: [    5.956000] sd 0:0:1:0: Attached scsi generic sg1 type 0
Nov  8 17:40:27 uue16 kernel: [    5.956000] sd 2:0:0:0: Attached scsi generic sg2 type 0
Nov  8 17:40:27 uue16 kernel: [    5.956000] sd 3:0:0:0: Attached scsi generic sg3 type 0
Nov  8 17:40:27 uue16 kernel: [    5.956000] sr 3:0:1:0: Attached scsi generic sg4 type 5
Nov  8 17:40:27 uue16 kernel: [    5.972000] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Nov  8 17:40:27 uue16 kernel: [    5.972000] Uniform CD-ROM driver Revision: 3.20
Nov  8 17:40:27 uue16 kernel: [    5.972000] sr 3:0:1:0: Attached scsi CD-ROM sr0
Nov  8 17:40:27 uue16 kernel: [    6.192000] Attempting manual resume
Nov  8 17:40:27 uue16 kernel: [    6.192000] swsusp: Resume From Partition 8:53
Nov  8 17:40:27 uue16 kernel: [    6.192000] PM: Checking swsusp image.
Nov  8 17:40:27 uue16 kernel: [    6.192000] PM: Resume from disk failed.
Nov  8 17:40:27 uue16 kernel: [    6.220000] usb 6-5: new high speed USB device using ehci_hcd and address 4
Nov  8 17:40:27 uue16 kernel: [    6.232000] kjournald starting.  Commit interval 5 seconds
Nov  8 17:40:27 uue16 kernel: [    6.232000] EXT3-fs: mounted filesystem with ordered data mode.
Nov  8 17:40:27 uue16 kernel: [    6.368000] usb 6-5: configuration #1 chosen from 1 choice
Nov  8 17:40:27 uue16 kernel: [    6.608000] usb 6-8: new high speed USB device using ehci_hcd and address 5
Nov  8 17:40:27 uue16 kernel: [    6.740000] usb 6-8: configuration #1 chosen from 1 choice
Nov  8 17:40:27 uue16 kernel: [    7.116000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800008e4aa6]
Nov  8 17:40:27 uue16 kernel: [    7.240000] usb 8-3: new high speed USB device using ehci_hcd and address 2
Nov  8 17:40:27 uue16 kernel: [    7.376000] usb 8-3: configuration #1 chosen from 1 choice
Nov  8 17:40:27 uue16 kernel: [    7.376000] usbcore: registered new interface driver libusual
Nov  8 17:40:27 uue16 kernel: [    7.616000] usb 1-2: new full speed USB device using uhci_hcd and address 4
Nov  8 17:40:27 uue16 kernel: [    7.792000] usb 1-2: configuration #1 chosen from 1 choice
Nov  8 17:40:27 uue16 kernel: [    8.488000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov  8 17:40:27 uue16 kernel: [    8.488000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov  8 17:40:27 uue16 kernel: [    8.556000] Initializing USB Mass Storage driver...
Nov  8 17:40:27 uue16 kernel: [    8.556000] scsi4 : SCSI emulation for USB Mass Storage devices
Nov  8 17:40:27 uue16 kernel: [    8.556000] usb-storage: device found at 2
Nov  8 17:40:27 uue16 kernel: [    8.556000] usb-storage: waiting for device to settle before scanning
Nov  8 17:40:27 uue16 kernel: [    8.556000] scsi5 : SCSI emulation for USB Mass Storage devices
Nov  8 17:40:27 uue16 kernel: [    8.556000] usb-storage: device found at 4
Nov  8 17:40:27 uue16 kernel: [    8.556000] usb-storage: waiting for device to settle before scanning
Nov  8 17:40:27 uue16 kernel: [    8.556000] scsi6 : SCSI emulation for USB Mass Storage devices
Nov  8 17:40:27 uue16 kernel: [    8.556000] usb-storage: device found at 5
Nov  8 17:40:27 uue16 kernel: [    8.556000] usb-storage: waiting for device to settle before scanning
Nov  8 17:40:27 uue16 kernel: [    8.556000] scsi7 : SCSI emulation for USB Mass Storage devices
Nov  8 17:40:27 uue16 kernel: [    8.556000] usb-storage: device found at 2
Nov  8 17:40:27 uue16 kernel: [    8.556000] usb-storage: waiting for device to settle before scanning
Nov  8 17:40:27 uue16 kernel: [    8.556000] usbcore: registered new interface driver usb-storage
Nov  8 17:40:27 uue16 kernel: [    8.556000] USB Mass Storage support registered.
Nov  8 17:40:27 uue16 kernel: [   12.488000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov  8 17:40:27 uue16 kernel: [   12.488000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov  8 17:40:27 uue16 kernel: [   12.628000] parport_pc 00:07: reported by Plug and Play ACPI
Nov  8 17:40:27 uue16 kernel: [   12.628000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Nov  8 17:40:27 uue16 kernel: [   12.776000] input: PC Speaker as /class/input/input2
Nov  8 17:40:27 uue16 kernel: [   13.000000] intel_rng: FWH not detected
Nov  8 17:40:27 uue16 kernel: [   13.000000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 17
Nov  8 17:40:27 uue16 kernel: [   13.000000] PCI: Setting latency timer of device 0000:03:00.0 to 64
Nov  8 17:40:27 uue16 kernel: [   13.000000] sky2 0000:03:00.0: v1.18 addr 0xfe9fc000 irq 17 Yukon-EC (0xb6) rev 2
Nov  8 17:40:27 uue16 kernel: [   13.000000] sky2 eth0: addr 00:15:f2:a0:f8:e6
Nov  8 17:40:27 uue16 kernel: [   13.144000] iTCO_vendor_support: vendor-support=0
Nov  8 17:40:27 uue16 kernel: [   13.144000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Nov  8 17:40:27 uue16 kernel: [   13.148000] sky2 eth0: enabling interface
Nov  8 17:40:27 uue16 kernel: [   13.220000] Linux agpgart interface v0.102 (c) Dave Jones
Nov  8 17:40:27 uue16 kernel: [   13.384000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0xC202
Nov  8 17:40:27 uue16 kernel: [   13.384000] usbcore: registered new interface driver usblp
Nov  8 17:40:27 uue16 kernel: [   13.384000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Nov  8 17:40:27 uue16 kernel: [   13.480000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
Nov  8 17:40:27 uue16 kernel: [   13.484000] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
Nov  8 17:40:27 uue16 kernel: [   13.484000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Nov  8 17:40:27 uue16 kernel: [   13.508000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov  8 17:40:27 uue16 kernel: [   13.536000] [fglrx] Maximum main memory to use for locked dma buffers: 2888 MBytes.
Nov  8 17:40:27 uue16 kernel: [   13.536000] [fglrx] ASYNCIO init succeed!
Nov  8 17:40:27 uue16 kernel: [   13.536000] [fglrx] PAT is enabled successfully!
Nov  8 17:40:27 uue16 kernel: [   13.536000] [fglrx] module loaded - fglrx 8.42.3 [Oct 19 2007] on minor 0
Nov  8 17:40:27 uue16 kernel: [   13.556000] usb-storage: device scan complete
Nov  8 17:40:27 uue16 last message repeated 2 times
Nov  8 17:40:27 uue16 kernel: [   13.556000] scsi 7:0:0:0: Direct-Access     HP       Photosmart 8200  1.00 PQ: 0 ANSI: 2
Nov  8 17:40:27 uue16 kernel: [   13.556000] usb-storage: device scan complete
Nov  8 17:40:27 uue16 kernel: [   13.556000] sd 7:0:0:0: [sde] Attached SCSI removable disk
Nov  8 17:40:27 uue16 kernel: [   13.556000] sd 7:0:0:0: Attached scsi generic sg5 type 0
Nov  8 17:40:27 uue16 kernel: [   13.556000] scsi 4:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100D PQ: 0 ANSI: 4
Nov  8 17:40:27 uue16 kernel: [   13.560000] scsi 5:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
Nov  8 17:40:27 uue16 kernel: [   13.560000] scsi 5:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
Nov  8 17:40:27 uue16 kernel: [   13.564000] scsi 5:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
Nov  8 17:40:27 uue16 kernel: [   13.568000] scsi 5:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
Nov  8 17:40:27 uue16 kernel: [   13.588000] scsi 6:0:0:0: Direct-Access     IC25N030 ATCS04-0         CA3O PQ: 0 ANSI: 0
Nov  8 17:40:27 uue16 kernel: [   13.592000] sd 6:0:0:0: [sdf] 58605119 512-byte hardware sectors (30006 MB)
Nov  8 17:40:27 uue16 kernel: [   13.592000] sd 6:0:0:0: [sdf] Write Protect is off
Nov  8 17:40:27 uue16 kernel: [   13.592000] sd 6:0:0:0: [sdf] Mode Sense: 03 00 00 00
Nov  8 17:40:27 uue16 kernel: [   13.592000] sd 6:0:0:0: [sdf] Assuming drive cache: write through
Nov  8 17:40:27 uue16 kernel: [   13.592000] sd 6:0:0:0: [sdf] 58605119 512-byte hardware sectors (30006 MB)
Nov  8 17:40:27 uue16 kernel: [   13.592000] sd 6:0:0:0: [sdf] Write Protect is off
Nov  8 17:40:27 uue16 kernel: [   13.592000] sd 6:0:0:0: [sdf] Mode Sense: 03 00 00 00
Nov  8 17:40:27 uue16 kernel: [   13.592000] sd 6:0:0:0: [sdf] Assuming drive cache: write through
Nov  8 17:40:27 uue16 kernel: [   13.592000]  sdf:<6>ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 17
Nov  8 17:40:27 uue16 kernel: [   13.724000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Nov  8 17:40:27 uue16 kernel: [   13.868000]  sdf1
Nov  8 17:40:27 uue16 kernel: [   13.868000] sd 6:0:0:0: [sdf] Attached SCSI disk
Nov  8 17:40:27 uue16 kernel: [   13.868000] sd 6:0:0:0: Attached scsi generic sg6 type 0
Nov  8 17:40:27 uue16 kernel: [   13.868000] sd 5:0:0:0: [sdg] Attached SCSI removable disk
Nov  8 17:40:27 uue16 kernel: [   13.868000] sd 5:0:0:0: Attached scsi generic sg7 type 0
Nov  8 17:40:27 uue16 kernel: [   13.872000] sd 5:0:0:1: [sdh] Attached SCSI removable disk
Nov  8 17:40:27 uue16 kernel: [   13.872000] sd 5:0:0:1: Attached scsi generic sg8 type 0
Nov  8 17:40:27 uue16 kernel: [   13.872000] sd 5:0:0:2: [sdi] Attached SCSI removable disk
Nov  8 17:40:27 uue16 kernel: [   13.872000] sd 5:0:0:2: Attached scsi generic sg9 type 0
Nov  8 17:40:27 uue16 kernel: [   13.872000] sd 5:0:0:3: [sdj] Attached SCSI removable disk
Nov  8 17:40:27 uue16 kernel: [   13.872000] sd 5:0:0:3: Attached scsi generic sg10 type 0
Nov  8 17:40:27 uue16 kernel: [   13.876000] sd 4:0:0:0: [sdk] 625142448 512-byte hardware sectors (320073 MB)
Nov  8 17:40:27 uue16 kernel: [   13.876000] sd 4:0:0:0: [sdk] Write Protect is off
Nov  8 17:40:27 uue16 kernel: [   13.876000] sd 4:0:0:0: [sdk] Mode Sense: 1c 00 00 00
Nov  8 17:40:27 uue16 kernel: [   13.876000] sd 4:0:0:0: [sdk] Assuming drive cache: write through
Nov  8 17:40:27 uue16 kernel: [   13.880000] sd 4:0:0:0: [sdk] 625142448 512-byte hardware sectors (320073 MB)
Nov  8 17:40:27 uue16 kernel: [   13.880000] sd 4:0:0:0: [sdk] Write Protect is off
Nov  8 17:40:27 uue16 kernel: [   13.880000] sd 4:0:0:0: [sdk] Mode Sense: 1c 00 00 00
Nov  8 17:40:27 uue16 kernel: [   13.880000] sd 4:0:0:0: [sdk] Assuming drive cache: write through
Nov  8 17:40:27 uue16 kernel: [   13.880000]  sdk: sdk1
Nov  8 17:40:27 uue16 kernel: [   13.884000] sd 4:0:0:0: [sdk] Attached SCSI disk
Nov  8 17:40:27 uue16 kernel: [   13.884000] sd 4:0:0:0: Attached scsi generic sg11 type 0
Nov  8 17:40:27 uue16 kernel: [   14.388000] lp0: using parport0 (interrupt-driven).
Nov  8 17:40:27 uue16 kernel: [   14.440000] Adding 9100780k swap on /dev/sdd5.  Priority:-1 extents:1 across:9100780k
Nov  8 17:40:27 uue16 kernel: [   14.576000] NET: Registered protocol family 17
Nov  8 17:40:27 uue16 kernel: [   14.816000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Nov  8 17:40:27 uue16 kernel: [   14.832000] EXT3 FS on sdd1, internal journal
Nov  8 17:40:27 uue16 kernel: [   17.388000] No dock devices found.
Nov  8 17:40:27 uue16 kernel: [   17.432000] input: Power Button (FF) as /class/input/input4
Nov  8 17:40:27 uue16 kernel: [   17.432000] ACPI: Power Button (FF) [PWRF]
Nov  8 17:40:27 uue16 kernel: [   17.432000] input: Power Button (CM) as /class/input/input5
Nov  8 17:40:27 uue16 kernel: [   17.432000] ACPI: Power Button (CM) [PWRB]
Nov  8 17:40:27 uue16 NetworkManager: <info>  starting... 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.259942] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_277c'). 
Nov  8 17:40:28 uue16 kernel: [   18.796000] NET: Registered protocol family 10
Nov  8 17:40:28 uue16 kernel: [   18.796000] lo: Disabled Privacy Extensions
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.756973] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_277d'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.759855] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_7109'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.761424] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_7129'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.762631] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.763681] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.764201] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.765054] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_11ab_4362'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.765557] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27e2'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.766063] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_11ab_6141'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.766608] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.799846] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.800446] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.800887] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_220d_noserial'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.801301] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_220d_noserial_if0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.801715] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.802139] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.802577] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.803010] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.803424] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.803838] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.804251] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.804661] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.805071] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.805482] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.805893] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.806305] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.806741] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.807146] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_if0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.807582] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_if0_scsi_host'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.808123] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_if0_scsi_host_scsi_device_lun0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.808612] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.809133] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.809637] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.810045] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.810476] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun1'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.810888] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun2'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.811300] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun3'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.811709] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.812137] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_if0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.812547] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_if0_scsi_host'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.813028] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_if0_scsi_host_scsi_device_lun0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.813438] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_244e'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.813845] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3038'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.814252] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.814685] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_0_if0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.815085] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3038_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.815482] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_1'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.815882] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_1_if0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.816283] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3104'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.816683] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_2'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.817082] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_2_if0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.817479] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.817883] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.818282] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if1'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.818703] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if2'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.819100] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if2_scsi_host'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.819509] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if2_scsi_host_scsi_device_lun0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.819907] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1102_5'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.820304] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_104c_8023'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.820699] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b8'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.821095] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.821592] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.822016] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.822430] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.822835] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.823240] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.823641] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_scsi_device_lun0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.824044] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.824448] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.824851] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.825252] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.825652] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.826053] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_floppy_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.826479] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.826899] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.827303] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.827705] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.828105] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.828507] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.828922] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a08'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.829325] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.829724] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.830125] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.830548] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.830967] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.831368] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0700'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.831767] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0401'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.832164] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.832562] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.833016] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_1'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.833418] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.833815] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f03'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.834214] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_2'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.834646] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNPb02f'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.835055] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNPb006'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.835464] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.835871] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_3'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.836278] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.836686] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.837111] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.837520] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.837929] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_f2_a0_f8_e6'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.846634] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.847159] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0_0_scsi_generic'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.847562] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun3_scsi_generic'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.847961] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.848361] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.848776] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.849173] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0_0_scsi_generic'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.849569] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if2_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.849965] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.850363] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.850781] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.851179] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun2_scsi_generic'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.851575] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_1'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.851971] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.852367] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.852763] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.853158] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.853571] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNPb006_oss_mixer__1'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.853964] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.854358] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.854786] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_1'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.855211] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_1'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.855621] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_2'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.856029] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.856438] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.856847] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.857270] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.857677] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.858086] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.858513] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.858924] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.859334] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.954118] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.990703] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_220d_noserial_usbraw'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.991241] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.991717] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.992117] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.992511] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_0_usbraw'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.992905] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.993354] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_usbraw'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.993750] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_usbraw'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.994144] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_usbraw'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.994566] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_1_usbraw'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.994958] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_2_usbraw'). 
Nov  8 17:40:28 uue16 NetworkManager: <debug> [1194565228.995368] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_usbraw'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.056563] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_floppy_0_storage'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.090019] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Maxtor_6B300R0_B620LRQH'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.099642] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_01C660C5D0074900'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.174103] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_36D04443D0440C15'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.179225] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST340015ACE_5LAEEQQH'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.187459] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_6c99eb8b_ecab_4126_bb00_453192aecfb6'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.193060] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.210518] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_e73ed621_c1d6_43e1_adc4_505d9a6360f9'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.215754] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD740GD_00FLC0_WD_WMAKE2361213'). 
Nov  8 17:40:29 uue16 kernel: [   19.504000] ppdev: user-space parallel port driver
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.228119] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_4AA44F23A44F10BD'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.368094] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD3200KS_00PFB0_WD_WCAPD1030686'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.373645] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_e8bee423_266f_49eb_8f99_a75d19ffa386'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.659522] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024_0'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.664863] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_2d0e7fbd_476c_40ef_8e51_f20e13690ce1'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.745422] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_HP_Photosmart_8200_MY5AR3X0H504KK_0_0'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.751376] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_IC25N030_ATCS04_0_0_0_0'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.768659] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8CD0_6617'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.782055] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_STORAGE_DEVICE_0300836166_0_0'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.792073] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_STORAGE_DEVICE_0300836166_0_1'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.802627] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_STORAGE_DEVICE_0300836166_0_2'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.811884] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_STORAGE_DEVICE_0300836166_0_3'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.816753] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Seagate_FreeAgentDesktop_9QF3CG9K_0_0'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.856126] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_04F07BDEF07BD480'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.928211] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU4'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.935605] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU3'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.936318] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU2'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.936700] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Nov  8 17:40:29 uue16 NetworkManager: <debug> [1194565229.937055] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVDR___PX_755A'). 
Nov  8 17:40:30 uue16 dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  8 17:40:30 uue16 dhclient: DHCPACK from 192.168.20.1
Nov  8 17:40:30 uue16 kernel: [   20.436000] audit(1194565230.131:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=7033 profile="/usr/sbin/cupsd"
Nov  8 17:40:30 uue16 dhclient: bound to 192.168.20.253 -- renewal in 113666 seconds.
Nov  8 17:40:31 uue16 hal_lpadmin: add
Nov  8 17:40:31 uue16 mysqld_safe[7265]: started
Nov  8 17:40:31 uue16 mysqld[7268]: 071108 17:40:31  InnoDB: Started; log sequence number 0 43655
Nov  8 17:40:32 uue16 mysqld[7268]: 071108 17:40:32 [Note] /usr/sbin/mysqld: ready for connections.
Nov  8 17:40:32 uue16 mysqld[7268]: Version: '5.0.45-Debian_1ubuntu3-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian etch distribution
Nov  8 17:40:32 uue16 /etc/mysql/debian-start[7365]: Upgrading MySQL tables if necessary.
Nov  8 17:40:32 uue16 kernel: [   23.044000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Nov  8 17:40:32 uue16 kernel: [   23.044000] apm: disabled - APM is not SMP safe.
Nov  8 17:40:32 uue16 atieventsd[7429]: ATI External Events Daemon started... 
Nov  8 17:40:32 uue16 atieventsd[7429]: Event daemon control socket created 
Nov  8 17:40:32 uue16 atieventsd[7429]: acpid connection established 
Nov  8 17:40:32 uue16 /etc/mysql/debian-start[7369]: Looking for 'mysql' in: /usr/bin/mysql
Nov  8 17:40:32 uue16 /etc/mysql/debian-start[7369]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck
Nov  8 17:40:32 uue16 /etc/mysql/debian-start[7369]: This installation of MySQL is already upgraded to 5.0.45, use --force if you still need to run mysql_upgrade
Nov  8 17:40:32 uue16 /etc/mysql/debian-start[7435]: Checking for insecure root accounts.
Nov  8 17:40:32 uue16 /etc/mysql/debian-start[7439]: WARNING: mysql.user contains 3 root accounts without password!
Nov  8 17:40:32 uue16 /etc/mysql/debian-start[7440]: Checking for crashed MySQL tables.
Nov  8 17:40:33 uue16 ntpdate[7129]: adjust time server 91.189.94.4 offset 0.026081 sec
Nov  8 17:40:33 uue16 hal_lpadmin: URIs: ['hp:/usb/Photosmart_8200_series?serial=MY5AR3X0H504KK', 'usb://HP/Photosmart%208200%20series?serial=MY5AR3X0H504KK', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if0_printer_MY5AR3X0H504KK']
Nov  8 17:40:34 uue16 kernel: [   24.408000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Nov  8 17:40:34 uue16 kernel: [   24.520000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Nov  8 17:40:34 uue16 kernel: [   24.536000] NFSD: starting 90-second grace period
Nov  8 17:40:35 uue16 python: hp-probe[7837]: warning: No devices found on the 'usb' bus. If this isn't the result you are expecting,
Nov  8 17:40:35 uue16 python: hp-probe[7837]: warning: check to make sure your devices are properly connected and powered on.
Nov  8 17:40:35 uue16 hal_lpadmin: HPLIP Fax URIs: None
Nov  8 17:40:35 uue16 hal_lpadmin: Not adding printer: Photosmart_8200_series already exists
Nov  8 17:40:35 uue16 snort[7856]: Var 'eth0_ADDRESS' defined, value len = 26 chars
Nov  8 17:40:35 uue16 snort[7856]: , value = 192.168.20.0/255.255.255.0 
Nov  8 17:40:35 uue16 snort[7856]: Var 'any_ADDRESS' defined, value len = 15 chars
Nov  8 17:40:35 uue16 snort[7856]: , value = 0.0.0.0/0.0.0.0 
Nov  8 17:40:35 uue16 snort[7856]: Var 'lo_ADDRESS' defined, value len = 19 chars
Nov  8 17:40:35 uue16 snort[7856]: , value = 127.0.0.0/255.0.0.0 
Nov  8 17:40:35 uue16 snort[7856]: Parsing Rules file /etc/snort/snort.conf 
Nov  8 17:40:35 uue16 snort[7856]: Var 'HOME_NET' redefined 
Nov  8 17:40:35 uue16 snort[7856]: Var 'EXTERNAL_NET' defined, value len = 3 chars
Nov  8 17:40:35 uue16 snort[7856]: , value = any 
Nov  8 17:40:35 uue16 snort[7856]: Var 'DNS_SERVERS' defined, value len = 16 chars
Nov  8 17:40:35 uue16 snort[7856]: , value = [192.168.0.0/16] 
Nov  8 17:40:35 uue16 snort[7856]: Var 'SMTP_SERVERS' defined, value len = 16 chars
Nov  8 17:40:35 uue16 snort[7856]: , value = [192.168.0.0/16] 
Nov  8 17:40:35 uue16 snort[7856]: Var 'HTTP_SERVERS' defined, value len = 16 chars
Nov  8 17:40:35 uue16 snort[7856]: , value = [192.168.0.0/16] 
Nov  8 17:40:35 uue16 snort[7856]: Var 'SQL_SERVERS' defined, value len = 16 chars
Nov  8 17:40:35 uue16 snort[7856]: , value = [192.168.0.0/16] 
Nov  8 17:40:35 uue16 snort[7856]: Var 'TELNET_SERVERS' defined, value len = 16 chars
Nov  8 17:40:35 uue16 snort[7856]: , value = [192.168.0.0/16] 
Nov  8 17:40:35 uue16 snort[7856]: Var 'SNMP_SERVERS' defined, value len = 16 chars
Nov  8 17:40:35 uue16 snort[7856]: , value = [192.168.0.0/16] 
Nov  8 17:40:35 uue16 snort[7856]: Var 'HTTP_PORTS' defined, value len = 2 chars
Nov  8 17:40:35 uue16 snort[7856]: , value = 80 
Nov  8 17:40:35 uue16 snort[7856]: Var 'SHELLCODE_PORTS' defined, value len = 3 chars
Nov  8 17:40:35 uue16 snort[7856]: , value = !80 
Nov  8 17:40:35 uue16 snort[7856]: Var 'ORACLE_PORTS' defined, value len = 4 chars
Nov  8 17:40:35 uue16 snort[7856]: , value = 1521 
Nov  8 17:40:35 uue16 snort[7856]: Var 'AIM_SERVERS' defined, value len = 185 chars
Nov  8 17:40:35 uue16 snort[7856]:  
Nov  8 17:40:35 uue16 snort[7856]:    [64.12.24.0/23,64.12.28.0/23,64.12.161.0/24,64.12.163.0/24,64.12.200.0/24,205.188.3.0/24,205.188.5.0/24,205.188.7.0/24,205.188.9 
Nov  8 17:40:35 uue16 snort[7856]:    .0/24,205.188.153.0/24,205.188.179.0/24,205.188.248.0/24] 
Nov  8 17:40:35 uue16 snort[7856]: Var 'RULE_PATH' defined, value len = 16 chars
Nov  8 17:40:35 uue16 snort[7856]: , value = /etc/snort/rules 
Nov  8 17:40:35 uue16 snort[7856]: ,-----------[Flow Config]---------------------- 
Nov  8 17:40:35 uue16 snort[7856]: | Stats Interval:  0 
Nov  8 17:40:35 uue16 snort[7856]: | Hash Method:     2 
Nov  8 17:40:35 uue16 snort[7856]: | Memcap:          10485760 
Nov  8 17:40:35 uue16 snort[7856]: | Rows  :          4099 
Nov  8 17:40:35 uue16 snort[7856]: | Overhead Bytes:  16400(%0.16) 
Nov  8 17:40:35 uue16 snort[7856]: `---------------------------------------------- 
Nov  8 17:40:35 uue16 snort[7856]: Frag3 global config: 
Nov  8 17:40:35 uue16 snort[7856]:     Max frags: 65536 
Nov  8 17:40:35 uue16 snort[7856]:     Fragment memory cap: 4194304 bytes 
Nov  8 17:40:35 uue16 snort[7856]: Frag3 engine config: 
Nov  8 17:40:35 uue16 snort[7856]:     Target-based policy: FIRST 
Nov  8 17:40:35 uue16 snort[7856]:     Fragment timeout: 60 seconds 
Nov  8 17:40:35 uue16 snort[7856]:     Fragment min_ttl:   1 
Nov  8 17:40:35 uue16 snort[7856]:     Fragment ttl_limit: 5 
Nov  8 17:40:35 uue16 snort[7856]:     Fragment Problems: 1 
Nov  8 17:40:35 uue16 snort[7856]:     Bound Addresses: 0.0.0.0/0.0.0.0 
Nov  8 17:40:35 uue16 snort[7856]: Stream5 global config: 
Nov  8 17:40:35 uue16 snort[7856]:     Track TCP sessions: ACTIVE 
Nov  8 17:40:35 uue16 snort[7856]:     Max TCP sessions: 8192 
Nov  8 17:40:35 uue16 snort[7856]:     Memcap (for reassembly packet storage): 8388608 
Nov  8 17:40:35 uue16 snort[7856]:     Track UDP sessions: INACTIVE 
Nov  8 17:40:35 uue16 snort[7856]:     Track ICMP sessions: INACTIVE 
Nov  8 17:40:35 uue16 snort[7856]: Stream5 TCP Policy config: 
Nov  8 17:40:35 uue16 snort[7856]:     Reassembly Policy: FIRST 
Nov  8 17:40:35 uue16 snort[7856]:     Timeout: 30 seconds 
Nov  8 17:40:35 uue16 snort[7856]:     Min ttl:  1 
Nov  8 17:40:35 uue16 snort[7856]:     Options: 
Nov  8 17:40:35 uue16 snort[7856]:         Static Flushpoint Sizes: YES 
Nov  8 17:40:35 uue16 snort[7856]:     Reassembly Ports: 
Nov  8 17:40:35 uue16 snort[7856]:       21 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:       23 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:       25 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:       42 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:       53 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:       80 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:       110 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:       111 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:       135 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:       136 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:       137 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:       139 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:       143 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:       445 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:       513 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:       1433 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:       1521 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:       3306 client (Footprint)  
Nov  8 17:40:35 uue16 snort[7856]:     Bound Addresses:0.0.0.0/0.0.0.0 
Nov  8 17:40:35 uue16 snort[7856]: HttpInspect Config: 
Nov  8 17:40:35 uue16 snort[7856]:     GLOBAL CONFIG 
Nov  8 17:40:35 uue16 snort[7856]:       Max Pipeline Requests:    0 
Nov  8 17:40:35 uue16 snort[7856]:       Inspection Type:          STATELESS 
Nov  8 17:40:35 uue16 snort[7856]:       Detect Proxy Usage:       NO 
Nov  8 17:40:35 uue16 snort[7856]:       IIS Unicode Map Filename: /etc/snort/unicode.map 
Nov  8 17:40:35 uue16 snort[7856]:       IIS Unicode Map Codepage: 1252 
Nov  8 17:40:35 uue16 snort[7856]:     DEFAULT SERVER CONFIG: 
Nov  8 17:40:35 uue16 snort[7856]:       Server profile: All 
Nov  8 17:40:35 uue16 snort[7856]:       Ports: 80 8080 8180  
Nov  8 17:40:35 uue16 snort[7856]:       Flow Depth: 300 
Nov  8 17:40:35 uue16 snort[7856]:       Max Chunk Length: 500000 
Nov  8 17:40:35 uue16 snort[7856]:       Inspect Pipeline Requests: YES 
Nov  8 17:40:35 uue16 snort[7856]:       URI Discovery Strict Mode: NO 
Nov  8 17:40:35 uue16 snort[7856]:       Allow Proxy Usage: NO 
Nov  8 17:40:35 uue16 snort[7856]:       Disable Alerting: NO 
Nov  8 17:40:35 uue16 snort[7856]:       Oversize Dir Length: 500 
Nov  8 17:40:35 uue16 snort[7856]:       Only inspect URI: NO 
Nov  8 17:40:35 uue16 snort[7856]:       Ascii: YES alert: NO 
Nov  8 17:40:35 uue16 snort[7856]:       Double Decoding: YES alert: YES 
Nov  8 17:40:35 uue16 snort[7856]:       %U Encoding: YES alert: YES 
Nov  8 17:40:35 uue16 snort[7856]:       Bare Byte: YES alert: YES 
Nov  8 17:40:35 uue16 snort[7856]:       Base36: OFF 
Nov  8 17:40:35 uue16 snort[7856]:       UTF 8: OFF 
Nov  8 17:40:35 uue16 snort[7856]:       IIS Unicode: YES alert: YES 
Nov  8 17:40:35 uue16 snort[7856]:       Multiple Slash: YES alert: NO 
Nov  8 17:40:35 uue16 snort[7856]:       IIS Backslash: YES alert: NO 
Nov  8 17:40:35 uue16 snort[7856]:       Directory Traversal: YES alert: NO 
Nov  8 17:40:35 uue16 snort[7856]:       Web Root Traversal: YES alert: YES 
Nov  8 17:40:35 uue16 snort[7856]:       Apache WhiteSpace: YES alert: NO 
Nov  8 17:40:35 uue16 snort[7856]:       IIS Delimiter: YES alert: NO 
Nov  8 17:40:35 uue16 snort[7856]:       IIS Unicode Map: GLOBAL IIS UNICODE MAP CONFIG 
Nov  8 17:40:35 uue16 snort[7856]:       Non-RFC Compliant Characters: NONE 
Nov  8 17:40:35 uue16 snort[7856]:       Whitespace Characters: 0x09 0x0b 0x0c 0x0d  
Nov  8 17:40:35 uue16 snort[7856]: rpc_decode arguments: 
Nov  8 17:40:35 uue16 snort[7856]:     Ports to decode RPC on: 111 32771  
Nov  8 17:40:35 uue16 snort[7856]:     alert_fragments: INACTIVE 
Nov  8 17:40:35 uue16 snort[7856]:     alert_large_fragments: ACTIVE 
Nov  8 17:40:35 uue16 snort[7856]:     alert_incomplete: ACTIVE 
Nov  8 17:40:35 uue16 snort[7856]:     alert_multiple_requests: ACTIVE 
Nov  8 17:40:35 uue16 snort[7856]: Portscan Detection Config: 
Nov  8 17:40:35 uue16 snort[7856]:     Detect Protocols:  TCP UDP ICMP IP 
Nov  8 17:40:35 uue16 snort[7856]:     Detect Scan Type:  portscan portsweep decoy_portscan distributed_portscan 
Nov  8 17:40:35 uue16 snort[7856]:     Sensitivity Level: Low 
Nov  8 17:40:35 uue16 snort[7856]:     Memcap (in bytes): 10000000 
Nov  8 17:40:35 uue16 snort[7856]:     Number of Nodes:   36900 
Nov  8 17:40:35 uue16 snort[7856]:  
Nov  8 17:40:35 uue16 snort[7856]: Tagged Packet Limit: 256 
Nov  8 17:40:35 uue16 snort[7856]:  
Nov  8 17:40:35 uue16 snort[7856]: +-----------------------[thresholding-config]---------------------------------- 
Nov  8 17:40:35 uue16 snort[7856]: | memory-cap : 1048576 bytes 
Nov  8 17:40:35 uue16 snort[7856]: +-----------------------[thresholding-global]---------------------------------- 
Nov  8 17:40:35 uue16 snort[7856]: | none 
Nov  8 17:40:35 uue16 snort[7856]: +-----------------------[thresholding-local]----------------------------------- 
Nov  8 17:40:35 uue16 snort[7856]: | none 
Nov  8 17:40:35 uue16 snort[7856]: +-----------------------[suppression]------------------------------------------ 
Nov  8 17:40:35 uue16 snort[7856]: | none 
Nov  8 17:40:35 uue16 snort[7856]: ------------------------------------------------------------------------------- 
Nov  8 17:40:35 uue16 snort[7856]: Rule application order: activation->dynamic->pass->drop->alert->log 
Nov  8 17:40:35 uue16 snort[7856]: Log directory = /var/log/snort 
Nov  8 17:40:35 uue16 snort[7856]: Loading dynamic engine /usr/lib/snort_dynamicengine/libsf_engine.so... 
Nov  8 17:40:35 uue16 snort[7856]: done 
Nov  8 17:40:35 uue16 snort[7856]: Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/... 
Nov  8 17:40:35 uue16 snort[7856]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ssh_preproc.so... 
Nov  8 17:40:35 uue16 snort[7856]: done 
Nov  8 17:40:35 uue16 snort[7856]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dns_preproc.so... 
Nov  8 17:40:35 uue16 snort[7856]: done 
Nov  8 17:40:35 uue16 snort[7856]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ftptelnet_preproc.so... 
Nov  8 17:40:35 uue16 snort[7856]: done 
Nov  8 17:40:35 uue16 snort[7856]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dcerpc_preproc.so... 
Nov  8 17:40:35 uue16 snort[7856]: done 
Nov  8 17:40:35 uue16 snort[7856]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_smtp_preproc.so... 
Nov  8 17:40:35 uue16 snort[7856]: done 
Nov  8 17:40:35 uue16 snort[7856]:   Finished Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/ 
Nov  8 17:40:35 uue16 snort[7856]: FTPTelnet Config: 
Nov  8 17:40:35 uue16 snort[7856]:     GLOBAL CONFIG 
Nov  8 17:40:35 uue16 snort[7856]:       Inspection Type: stateful 
Nov  8 17:40:35 uue16 snort[7856]:       Check for Encrypted Traffic: YES alert: YES 
Nov  8 17:40:35 uue16 snort[7856]:       Continue to check encrypted data: NO 
Nov  8 17:40:35 uue16 snort[7856]:     TELNET CONFIG: 
Nov  8 17:40:35 uue16 snort[7856]:       Ports: 23  
Nov  8 17:40:35 uue16 snort[7856]:       Are You There Threshold: 200 
Nov  8 17:40:35 uue16 snort[7856]:       Normalize: YES 
Nov  8 17:40:35 uue16 snort[7856]:       Detect Anomalies: NO 
Nov  8 17:40:35 uue16 snort[7856]:     FTP CONFIG: 
Nov  8 17:40:35 uue16 snort[7856]:       FTP Server: default 
Nov  8 17:40:35 uue16 snort[7856]:         Ports: 21  
Nov  8 17:40:35 uue16 snort[7856]:         Check for Telnet Cmds: YES alert: YES 
Nov  8 17:40:35 uue16 snort[7856]:         Identify open data channels: YES 
Nov  8 17:40:35 uue16 snort[7856]:       FTP Client: default 
Nov  8 17:40:35 uue16 snort[7856]:         Check for Bounce Attacks: YES alert: YES 
Nov  8 17:40:35 uue16 snort[7856]:         Check for Telnet Cmds: YES alert: YES 
Nov  8 17:40:35 uue16 snort[7856]:         Max Response Length: 256 
Nov  8 17:40:35 uue16 snort[7856]: SMTP Config: 
Nov  8 17:40:35 uue16 snort[7856]:       Ports: 
Nov  8 17:40:35 uue16 snort[7856]: 25 
Nov  8 17:40:35 uue16 snort[7856]:  
Nov  8 17:40:35 uue16 snort[7856]:       Inspection Type:            STATEFUL 
Nov  8 17:40:35 uue16 snort[7856]:       Normalize Spaces:           YES 
Nov  8 17:40:35 uue16 snort[7856]:       Ignore Data:                NO 
Nov  8 17:40:35 uue16 snort[7856]:       Ignore TLS Data:            NO 
Nov  8 17:40:35 uue16 snort[7856]:       Ignore Alerts:              NO 
Nov  8 17:40:35 uue16 snort[7856]:       Max Command Length:         0 
Nov  8 17:40:35 uue16 snort[7856]:       Max Header Line Length:     0 
Nov  8 17:40:35 uue16 snort[7856]:       Max Response Line Length:   0 
Nov  8 17:40:35 uue16 snort[7856]:       X-Link2State Alert:         YES 
Nov  8 17:40:35 uue16 snort[7856]:       Drop on X-Link2State Alert: NO 
Nov  8 17:40:35 uue16 snort[7856]:  DCE/RPC Decoder config: 
Nov  8 17:40:35 uue16 snort[7856]:     Autodetect ports ENABLED 
Nov  8 17:40:35 uue16 snort[7856]:     SMB fragmentation ENABLED 
Nov  8 17:40:35 uue16 snort[7856]:     DCE/RPC fragmentation ENABLED 
Nov  8 17:40:35 uue16 snort[7856]:     Max Frag Size: 3000 bytes 
Nov  8 17:40:35 uue16 snort[7856]:     Memcap: 100000 KB 
Nov  8 17:40:35 uue16 snort[7856]:     Alert if memcap exceeded DISABLED 
Nov  8 17:40:35 uue16 snort[7856]:  
Nov  8 17:40:35 uue16 snort[7856]: DNS config:  
Nov  8 17:40:35 uue16 snort[7856]:     DNS Client rdata txt Overflow Alert: ACTIVE 
Nov  8 17:40:35 uue16 snort[7856]:     Obsolete DNS RR Types Alert: INACTIVE 
Nov  8 17:40:35 uue16 snort[7856]:     Experimental DNS RR Types Alert: INACTIVE 
Nov  8 17:40:35 uue16 snort[7856]:     Ports:
Nov  8 17:40:35 uue16 snort[7856]:  53
Nov  8 17:40:35 uue16 snort[7856]:  
Nov  8 17:40:35 uue16 snort[7856]: Warning: flowbits key 'realplayer.playlist' is checked but not ever set. 
Nov  8 17:40:35 uue16 snort[7856]: Warning: flowbits key 'community_uri.size.1050' is set but not ever checked. 
Nov  8 17:40:35 uue16 snort[7856]: Warning: flowbits key 'smb.tree.create.llsrpc' is set but not ever checked. 
Nov  8 17:40:35 uue16 snort[7856]: Warning: flowbits key 'ms_sql_seen_dns' is checked but not ever set. 
Nov  8 17:40:35 uue16 snort[7856]: 37 out of 512 flowbits in use. 
Nov  8 17:40:35 uue16 kernel: [   26.212000] device eth0 entered promiscuous mode
Nov  8 17:40:35 uue16 kernel: [   26.212000] audit(1194565235.632:4): dev=eth0 prom=256 old_prom=0 auid=4294967295
Nov  8 17:40:35 uue16 kernel: [   26.224000] device eth0 left promiscuous mode
Nov  8 17:40:35 uue16 snort[7856]: Initializing daemon mode 
Nov  8 17:40:35 uue16 kernel: [   26.224000] audit(1194565235.632:5): dev=eth0 prom=0 old_prom=256 auid=4294967295
Nov  8 17:40:35 uue16 kernel: [   26.244000] device eth0 entered promiscuous mode
Nov  8 17:40:35 uue16 kernel: [   26.244000] audit(1194565235.632:6): dev=eth0 prom=256 old_prom=0 auid=4294967295
Nov  8 17:40:35 uue16 snort[7906]: PID path stat checked out ok, PID path set to /var/run/ 
Nov  8 17:40:35 uue16 snort[7906]: Writing PID "7906" to file "/var/run//snort_eth0.pid" 
Nov  8 17:40:35 uue16 snort[7856]: Daemon parent exiting 
Nov  8 17:40:35 uue16 snort[7906]: Daemon initialized, signaled parent pid: 7856 
Nov  8 17:40:36 uue16 kernel: [   26.492000] Failure registering capabilities with primary security module.
Nov  8 17:40:36 uue16 python: hp-probe[8086]: warning: No devices found on the 'usb' bus. If this isn't the result you are expecting,
Nov  8 17:40:36 uue16 python: hp-probe[8086]: warning: check to make sure your devices are properly connected and powered on.
Nov  8 17:40:36 uue16 avahi-daemon[8104]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Nov  8 17:40:36 uue16 avahi-daemon[8104]: Successfully dropped root privileges.
Nov  8 17:40:36 uue16 avahi-daemon[8104]: avahi-daemon 0.6.20 starting up.
Nov  8 17:40:36 uue16 avahi-daemon[8104]: Successfully called chroot().
Nov  8 17:40:36 uue16 avahi-daemon[8104]: Successfully dropped remaining capabilities.
Nov  8 17:40:36 uue16 NetworkManager: <debug> [1194565236.260928] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if0_printer_MY5AR3X0H504KK'). 
Nov  8 17:40:36 uue16 avahi-daemon[8104]: No service file found in /etc/avahi/services.
Nov  8 17:40:36 uue16 avahi-daemon[8104]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.20.253.
Nov  8 17:40:36 uue16 avahi-daemon[8104]: New relevant interface eth0.IPv4 for mDNS.
Nov  8 17:40:36 uue16 avahi-daemon[8104]: Network interface enumeration completed.
Nov  8 17:40:36 uue16 avahi-daemon[8104]: Registering new address record for fe80::215:f2ff:fea0:f8e6 on eth0.*.
Nov  8 17:40:36 uue16 avahi-daemon[8104]: Registering new address record for 192.168.20.253 on eth0.IPv4.
Nov  8 17:40:36 uue16 avahi-daemon[8104]: Registering HINFO record with values 'I686'/'LINUX'.
Nov  8 17:40:36 uue16 dhcdbd: Started up.
Nov  8 17:40:37 uue16 avahi-daemon[8104]: Server startup complete. Host name is uue16.local. Local service cookie is 97342489.
Nov  8 17:40:38 uue16 hcid[8276]: Bluetooth HCI daemon
Nov  8 17:40:38 uue16 kernel: [   28.708000] Bluetooth: Core ver 2.11
Nov  8 17:40:38 uue16 kernel: [   28.708000] NET: Registered protocol family 31
Nov  8 17:40:38 uue16 kernel: [   28.708000] Bluetooth: HCI device and connection manager initialized
Nov  8 17:40:38 uue16 kernel: [   28.708000] Bluetooth: HCI socket layer initialized
Nov  8 17:40:38 uue16 hcid[8276]: Starting SDP server
Nov  8 17:40:38 uue16 kernel: [   28.836000] Bluetooth: L2CAP ver 2.8
Nov  8 17:40:38 uue16 kernel: [   28.836000] Bluetooth: L2CAP socket layer initialized
Nov  8 17:40:38 uue16 hcid[8276]: Created local server at unix:abstract=/var/run/dbus-vqievd1x5q,guid=66be12e6c1ebb56471f92e0047339e76
Nov  8 17:40:38 uue16 audio[8304]: Bluetooth Audio daemon
Nov  8 17:40:38 uue16 audio[8304]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Nov  8 17:40:38 uue16 audio[8304]: Unix socket created: 5
Nov  8 17:40:38 uue16 kernel: [   28.920000] Bluetooth: RFCOMM socket layer initialized
Nov  8 17:40:38 uue16 kernel: [   28.920000] Bluetooth: RFCOMM TTY layer initialized
Nov  8 17:40:38 uue16 kernel: [   28.920000] Bluetooth: RFCOMM ver 1.8
Nov  8 17:40:38 uue16 input[8305]: Bluetooth Input daemon
Nov  8 17:40:38 uue16 input[8305]: Registered input manager path:/org/bluez/input
Nov  8 17:40:38 uue16 audio[8304]: add_service_record: got record id 0x10000
Nov  8 17:40:38 uue16 audio[8304]: add_service_record: got record id 0x10001
Nov  8 17:40:38 uue16 audio[8304]: Registered manager path:/org/bluez/audio
Nov  8 17:40:39 uue16 kernel: [   29.316000] eth0: no IPv6 routers present
Nov  8 17:40:40 uue16 kernel: [   31.244000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov  8 17:40:41 uue16 anacron[8534]: Anacron 2.3 started on 2007-11-08
Nov  8 17:40:41 uue16 anacron[8534]: Normal exit (0 jobs run)
Nov  8 17:40:41 uue16 /usr/sbin/cron[8570]: (CRON) INFO (pidfile fd = 3)
Nov  8 17:40:41 uue16 /usr/sbin/cron[8571]: (CRON) STARTUP (fork ok)
Nov  8 17:40:41 uue16 /usr/sbin/cron[8571]: (CRON) INFO (Running @reboot jobs)
Nov  8 17:40:41 uue16 snort[7906]: Preprocessor/Decoder Rule Count: 0 
Nov  8 17:40:41 uue16 snort[7906]: Snort initialization completed successfully (pid=7906) 
Nov  8 17:40:41 uue16 snort[7906]: Not Using PCAP_FRAMES 
Nov  8 17:40:43 uue16 kernel: [   33.672000] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
Nov  8 17:40:43 uue16 kernel: [   33.672000] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
Nov  8 17:40:43 uue16 kernel: [   33.672000] [fglrx] Reserve Block - 2 offset =  0Xffff000 length = 0X1000
Nov  8 17:40:43 uue16 kernel: [   33.672000] [fglrx] Reserve Block - 3 offset =  0Xffbf000 length = 0X40000
Nov  8 17:40:57 uue16 hcid[8276]: Default passkey agent (:1.22, /org/bluez/passkey) registered
Nov  8 17:40:57 uue16 hcid[8276]: Default authorization agent (:1.22, /org/bluez/auth) registered
Nov  8 17:40:57 uue16 ntfs-3g[8959]: Version 1.913 
Nov  8 17:40:57 uue16 ntfs-3g[8959]: Mounted /dev/sdk1 (Read-Write, label "My Documents", NTFS 3.1) 
Nov  8 17:40:57 uue16 ntfs-3g[8959]: Cmdline options: rw,nosuid,nodev,locale=en_US.UTF-8 
Nov  8 17:40:57 uue16 ntfs-3g[8959]: Mount options: noatime,rw,nosuid,nodev,silent,allow_other,nonempty,fsname=/dev/sdk1,blkdev,blksize=4096 
Nov  8 17:40:57 uue16 hald: mounted /dev/sdk1 on behalf of uid 1000
Nov  8 17:40:57 uue16 hald: mounted /dev/sdf1 on behalf of uid 1000
Nov  8 17:40:59 uue16 NetworkManager: <info>  Updating allowed wireless network lists. 
Nov  8 17:40:59 uue16 NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov  8 17:49:30 uue16 kernel: [  560.376000] sky2 eth0: Link is down.
Nov  8 17:49:41 uue16 kernel: [  571.604000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Nov  8 17:50:19 uue16 kernel: [  609.988000] sky2 eth0: Link is down.
Nov  8 17:50:21 uue16 kernel: [  612.148000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Nov  8 17:53:50 uue16 NetworkManager: <info>  Disconnected. 
Nov  8 17:53:53 uue16 NetworkManager: <info>  Enabling networking. 
Nov  8 18:09:01 uue16 /USR/SBIN/CRON[9592]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov  8 18:17:01 uue16 /USR/SBIN/CRON[9635]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  8 18:33:58 uue16 NetworkManager: <info>  Disconnected. 
Nov  8 18:34:00 uue16 NetworkManager: <info>  Enabling networking. 
Nov  8 18:39:01 uue16 /USR/SBIN/CRON[9812]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov  8 19:00:27 uue16 -- MARK --
Nov  8 19:01:15 uue16 NetworkManager: <info>  Disconnected. 
Nov  8 19:01:17 uue16 NetworkManager: <info>  Enabling networking. 
Nov  8 19:06:11 uue16 NetworkManager: <info>  Disconnected. 
Nov  8 19:06:14 uue16 NetworkManager: <info>  Enabling networking. 
Nov  8 19:06:56 uue16 kernel: [ 5206.752000] sky2 eth0: Link is down.
Nov  8 19:07:12 uue16 kernel: [ 5223.136000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Nov  8 19:07:49 uue16 kernel: [ 5259.532000] sky2 eth0: Link is down.
Nov  8 19:07:51 uue16 kernel: [ 5261.492000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Nov  8 19:07:55 uue16 NetworkManager: <info>  Disconnected. 
Nov  8 19:07:59 uue16 NetworkManager: <info>  Enabling networking. 
Nov  8 19:09:01 uue16 /USR/SBIN/CRON[10058]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov  8 19:09:47 uue16 kernel: [ 5377.572000] sky2 eth0: Link is down.
Nov  8 19:09:52 uue16 kernel: [ 5382.404000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Nov  8 19:10:12 uue16 NetworkManager: <info>  Disconnected. 
Nov  8 19:10:21 uue16 NetworkManager: <info>  Enabling networking. 
Nov  8 19:10:26 uue16 kernel: [ 5417.244000] sky2 eth0: Link is down.
Nov  8 19:10:28 uue16 kernel: [ 5418.984000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Nov  8 19:12:00 uue16 kernel: [ 5511.056000] sky2 eth0: Link is down.
Nov  8 19:12:17 uue16 kernel: [ 5527.912000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Nov  8 19:12:55 uue16 kernel: [ 5565.472000] sky2 eth0: Link is down.
Nov  8 19:12:57 uue16 kernel: [ 5567.408000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Nov  8 19:13:02 uue16 NetworkManager: <info>  Disconnected. 
Nov  8 19:13:15 uue16 kernel: [ 5585.664000] sky2 eth0: Link is down.
Nov  8 19:13:21 uue16 kernel: [ 5591.736000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Nov  8 19:13:34 uue16 NetworkManager: <info>  Enabling networking. 
Nov  8 19:17:01 uue16 /USR/SBIN/CRON[10166]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  8 19:39:01 uue16 /USR/SBIN/CRON[10258]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov  8 20:00:27 uue16 -- MARK --
Nov  8 20:08:42 uue16 NetworkManager: <info>  Disconnected. 
Nov  8 20:08:48 uue16 kernel: [ 8919.196000] sky2 eth0: Link is down.
Nov  8 20:08:52 uue16 kernel: [ 8922.908000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Nov  8 20:09:01 uue16 /USR/SBIN/CRON[10386]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov  8 20:09:06 uue16 NetworkManager: <info>  Enabling networking. 
Nov  8 20:09:51 uue16 kernel: [ 8982.200000] sky2 eth0: Link is down.
Nov  8 20:10:13 uue16 kernel: [ 9003.524000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Nov  8 20:10:21 uue16 NetworkManager: <info>  Disconnected. 
Nov  8 20:10:44 uue16 NetworkManager: <info>  Enabling networking. 
Nov  8 20:10:49 uue16 kernel: [ 9040.192000] sky2 eth0: Link is down.
Nov  8 20:10:51 uue16 kernel: [ 9042.244000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Nov  8 20:11:27 uue16 NetworkManager: <info>  Disconnected. 
Nov  8 20:11:34 uue16 NetworkManager: <info>  Enabling networking. 
Nov  8 20:11:38 uue16 kernel: [ 9089.148000] sky2 eth0: Link is down.
Nov  8 20:11:42 uue16 kernel: [ 9092.336000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Nov  8 20:12:19 uue16 NetworkManager: <info>  Disconnected. 
Nov  8 20:12:25 uue16 kernel: [ 9135.568000] sky2 eth0: Link is down.
Nov  8 20:13:04 uue16 kernel: [ 9174.844000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Nov  8 20:13:18 uue16 NetworkManager: <info>  Enabling networking. 
Nov  8 20:13:32 uue16 kernel: [ 9202.440000] sky2 eth0: Link is down.
Nov  8 20:13:34 uue16 kernel: [ 9204.376000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Nov  8 20:13:42 uue16 kernel: [ 9212.860000] etherape uses obsolete (PF_INET,SOCK_PACKET)
Nov  8 20:13:56 uue16 NetworkManager: <info>  Disconnected. 
Nov  8 20:14:24 uue16 NetworkManager: <info>  Enabling networking. 
Nov  8 20:16:10 uue16 kernel: [ 9361.116000] sky2 eth0: Link is down.
Nov  8 20:16:20 uue16 kernel: [ 9371.264000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Nov  8 20:16:58 uue16 kernel: [ 9408.304000] sky2 eth0: Link is down.
Nov  8 20:16:59 uue16 kernel: [ 9410.152000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Nov  8 20:17:01 uue16 /USR/SBIN/CRON[12330]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  8 20:17:11 uue16 NetworkManager: <info>  Going to sleep. 
Nov  8 20:17:11 uue16 NetworkManager: <info>  Waking up from sleep. 
Nov  8 20:39:01 uue16 /USR/SBIN/CRON[12869]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov  8 21:00:27 uue16 -- MARK --
Nov  8 21:09:01 uue16 /USR/SBIN/CRON[13131]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov  8 21:14:31 uue16 ntfs-3g[8959]: Unmounting /dev/sdk1 (My Documents) 
Nov  8 21:14:31 uue16 hald: unmounted /dev/sdk1 from '/media/My Documents' on behalf of uid 1000
Nov  8 21:14:32 uue16 hald: unmounted /dev/sdf1 from '/media/USB' on behalf of uid 1000
Nov  8 21:14:32 uue16 init: tty5 main process (6077) killed by TERM signal
Nov  8 21:14:32 uue16 init: tty1 main process (6083) killed by TERM signal
Nov  8 21:14:32 uue16 init: tty2 main process (6079) killed by TERM signal
Nov  8 21:14:32 uue16 init: tty6 main process (6084) killed by TERM signal
Nov  8 21:14:32 uue16 init: tty4 main process (6076) killed by TERM signal
Nov  8 21:14:32 uue16 init: tty3 main process (6081) killed by TERM signal
Nov  8 21:14:32 uue16 avahi-daemon[8104]: Got SIGTERM, quitting.
Nov  8 21:14:32 uue16 avahi-daemon[8104]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.20.253.
Nov  8 21:14:34 uue16 atieventsd[7429]: Closing acpid connection 
Nov  8 21:14:34 uue16 atieventsd[7429]: Closing control socket 
Nov  8 21:14:34 uue16 atieventsd[7429]: ATI External Events Daemon shutting down 
Nov  8 21:14:36 uue16 rpc.statd[5893]: Caught signal 15, un-registering and exiting.
Nov  8 21:14:39 uue16 snort[7906]: *** Caught Term-Signal 
Nov  8 21:14:39 uue16 snort[7906]: Frag3 statistics: 
Nov  8 21:14:39 uue16 snort[7906]:         Total Fragments: 0 
Nov  8 21:14:39 uue16 snort[7906]:       Frags Reassembled: 0 
Nov  8 21:14:39 uue16 snort[7906]:                Discards: 0 
Nov  8 21:14:39 uue16 snort[7906]:           Memory Faults: 0 
Nov  8 21:14:39 uue16 snort[7906]:                Timeouts: 0 
Nov  8 21:14:39 uue16 snort[7906]:                Overlaps: 0 
Nov  8 21:14:39 uue16 snort[7906]:               Anomalies: 0 
Nov  8 21:14:39 uue16 snort[7906]:                  Alerts: 0 
Nov  8 21:14:39 uue16 snort[7906]:      FragTrackers Added: 0 
Nov  8 21:14:39 uue16 snort[7906]:     FragTrackers Dumped: 0 
Nov  8 21:14:39 uue16 snort[7906]: FragTrackers Auto Freed: 0 
Nov  8 21:14:39 uue16 snort[7906]:     Frag Nodes Inserted: 0 
Nov  8 21:14:39 uue16 snort[7906]:      Frag Nodes Deleted: 0 
Nov  8 21:14:39 uue16 snort[7906]: =============================================================================== 
Nov  8 21:14:39 uue16 snort[7906]: Stream5 statistics: 
Nov  8 21:14:39 uue16 snort[7906]:             Total sessions: 449 
Nov  8 21:14:39 uue16 snort[7906]:               TCP sessions: 449 
Nov  8 21:14:39 uue16 snort[7906]:               UDP sessions: 0 
Nov  8 21:14:39 uue16 snort[7906]:              ICMP sessions: 0 
Nov  8 21:14:39 uue16 snort[7906]:                 TCP Prunes: 0 
Nov  8 21:14:39 uue16 snort[7906]:                 UDP Prunes: 0 
Nov  8 21:14:39 uue16 snort[7906]:                ICMP Prunes: 0 
Nov  8 21:14:39 uue16 snort[7906]: TCP StreamTrackers Created: 517 
Nov  8 21:14:39 uue16 snort[7906]: TCP StreamTrackers Deleted: 517 
Nov  8 21:14:39 uue16 snort[7906]:               TCP Timeouts: 91 
Nov  8 21:14:39 uue16 snort[7906]:               TCP Overlaps: 0 
Nov  8 21:14:39 uue16 snort[7906]:        TCP Segments Queued: 0 
Nov  8 21:14:39 uue16 snort[7906]:      TCP Segments Released: 0 
Nov  8 21:14:39 uue16 snort[7906]:        TCP Rebuilt Packets: 0 
Nov  8 21:14:39 uue16 snort[7906]:          TCP Segments Used: 0 
Nov  8 21:14:39 uue16 snort[7906]:               TCP Discards: 370696 
Nov  8 21:14:39 uue16 snort[7906]:       UDP Sessions Created: 0 
Nov  8 21:14:39 uue16 snort[7906]:       UDP Sessions Deleted: 0 
Nov  8 21:14:39 uue16 snort[7906]:               UDP Timeouts: 0 
Nov  8 21:14:39 uue16 snort[7906]:               UDP Discards: 0 
Nov  8 21:14:39 uue16 snort[7906]:                     Events: 0 
Nov  8 21:14:39 uue16 snort[7906]: =============================================================================== 
Nov  8 21:14:39 uue16 snort[7906]: Final Flow Statistics 
Nov  8 21:14:39 uue16 snort[7906]: ,----[ FLOWCACHE STATS ]---------- 
Nov  8 21:14:39 uue16 snort[7906]: Memcap: 10485760 Overhead Bytes 16400 used(%1.633024)/blocks (171235/866) Overhead blocks: 1 Could Hold: (58579) 
Nov  8 21:14:39 uue16 snort[7906]: IPV4 count: 865 frees: 0 low_time: 1194565241, high_time: 1194578074, diff: 3h:33:53s 
Nov  8 21:14:39 uue16 snort[7906]:     finds: 499804 reversed: 319031(%63.831222)      find_success: 498939 find_fail: 865 percent_success: (%99.826932) new_flows: 865 
Nov  8 21:14:39 uue16 snort[7906]:  Protocol: 1 (%0.070828)    finds: 354    reversed: 273(%77.118644)    find_success: 335    find_fail: 19    percent_success: (%94.632768)    new_flows: 19 
Nov  8 21:14:39 uue16 snort[7906]:  Protocol: 2 (%0.001601)    finds: 8    reversed: 0(%0.000000)    find_success: 7    find_fail: 1    percent_success: (%87.500000)    new_flows: 1 
Nov  8 21:14:39 uue16 snort[7906]:  Protocol: 6 (%99.750902)    finds: 498559    reversed: 318758(%63.935863)    find_success: 498110    find_fail: 449    percent_success: (%99.909940)    new_flows: 449 
Nov  8 21:14:39 uue16 snort[7906]:  Protocol: 17 (%0.176669)    finds: 883    reversed: 0(%0.000000)    find_success: 487    find_fail: 396    percent_success: (%55.152888)    new_flows: 396 
Nov  8 21:14:39 uue16 snort[7906]: Snort received 504165 packets 
Nov  8 21:14:39 uue16 snort[7906]:     Analyzed: 504164(100.000%) 
Nov  8 21:14:39 uue16 snort[7906]:     Dropped: 0(0.000%) 
Nov  8 21:14:39 uue16 snort[7906]:     Outstanding: 1(0.000%) 
Nov  8 21:14:39 uue16 snort[7906]: =============================================================================== 
Nov  8 21:14:39 uue16 snort[7906]: Breakdown by protocol: 
Nov  8 21:14:39 uue16 snort[7906]:       TCP: 500149     (99.204%)          
Nov  8 21:14:39 uue16 snort[7906]:       UDP: 2507       (0.497%)           
Nov  8 21:14:39 uue16 snort[7906]:      ICMP: 354        (0.070%)           
Nov  8 21:14:39 uue16 snort[7906]:       ARP: 647        (0.128%) 
Nov  8 21:14:39 uue16 snort[7906]:     EAPOL: 0          (0.000%) 
Nov  8 21:14:39 uue16 snort[7906]:      IPv6: 1          (0.000%) 
Nov  8 21:14:39 uue16 snort[7906]:   ETHLOOP: 0          (0.000%) 
Nov  8 21:14:39 uue16 snort[7906]:       IPX: 0          (0.000%) 
Nov  8 21:14:39 uue16 snort[7906]:      FRAG: 0          (0.000%)           
Nov  8 21:14:39 uue16 snort[7906]:     OTHER: 211        (0.042%) 
Nov  8 21:14:39 uue16 snort[7906]:   DISCARD: 295        (0.059%) 
Nov  8 21:14:39 uue16 snort[7906]: InvChkSum: 3214       (0.637%) 
Nov  8 21:14:39 uue16 snort[7906]: =============================================================================== 
Nov  8 21:14:39 uue16 snort[7906]: Action Stats: 
Nov  8 21:14:39 uue16 snort[7906]: ALERTS: 9 
Nov  8 21:14:39 uue16 snort[7906]: LOGGED: 9 
Nov  8 21:14:39 uue16 snort[7906]: PASSED: 0 
Nov  8 21:14:39 uue16 snort[7906]: =============================================================================== 
Nov  8 21:14:39 uue16 snort[7906]: HTTP Inspect - encodings (Note: stream-reassembled packets included): 
Nov  8 21:14:39 uue16 snort[7906]:     POST methods:                   0          
Nov  8 21:14:39 uue16 snort[7906]:     GET methods:                    0          
Nov  8 21:14:39 uue16 snort[7906]:     Post parameters extracted:      0          
Nov  8 21:14:39 uue16 snort[7906]:     Unicode:                        0          
Nov  8 21:14:39 uue16 snort[7906]:     Double unicode:                 0          
Nov  8 21:14:39 uue16 snort[7906]:     Non-ASCII representable:        0          
Nov  8 21:14:39 uue16 snort[7906]:     Base 36:                        0          
Nov  8 21:14:39 uue16 snort[7906]:     Directory traversals:           0          
Nov  8 21:14:39 uue16 snort[7906]:     Extra slashes ("//"):           0          
Nov  8 21:14:39 uue16 snort[7906]:     Self-referencing paths ("./"):  0          
Nov  8 21:14:39 uue16 snort[7906]:     Total packets processed:        316213     
Nov  8 21:14:39 uue16 snort[7906]: =============================================================================== 
Nov  8 21:14:39 uue16 snort[7906]: Snort exiting 
Nov  8 21:14:39 uue16 snort[7906]: Could not remove pid file /var/run//snort_eth0.pid: Permission denied 
Nov  8 21:14:39 uue16 kernel: [12870.132000] device eth0 left promiscuous mode
Nov  8 21:14:39 uue16 kernel: [12870.132000] audit(1194578079.402:7): dev=eth0 prom=0 old_prom=256 auid=4294967295
Nov  8 21:14:39 uue16 mysqld[7268]: 071108 21:14:39 [Note] /usr/sbin/mysqld: Normal shutdown
Nov  8 21:14:39 uue16 mysqld[7268]: 
Nov  8 21:14:40 uue16 mysqld[7268]: 071108 21:14:40  InnoDB: Starting shutdown...
Nov  8 21:14:42 uue16 mysqld[7268]: 071108 21:14:42  InnoDB: Shutdown completed; log sequence number 0 43655
Nov  8 21:14:42 uue16 mysqld[7268]: 071108 21:14:42 [Note] /usr/sbin/mysqld: Shutdown complete
Nov  8 21:14:42 uue16 mysqld[7268]: 
Nov  8 21:14:42 uue16 mysqld_safe[13581]: ended
Nov  8 21:14:46 uue16 mountd[7751]: Caught signal 15, un-registering and exiting.
Nov  8 21:14:46 uue16 kernel: [12876.968000] nfsd: last server has exited
Nov  8 21:14:46 uue16 kernel: [12876.968000] nfsd: unexporting all filesystems
Nov  8 21:14:46 uue16 exiting on signal 15
Nov  8 21:20:05 uue16 syslogd 1.4.1#21ubuntu3: restart.
Nov  8 21:20:06 uue16 kernel: Inspecting /boot/System.map-2.6.22-14-generic
Nov  8 21:20:06 uue16 kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Nov  8 21:20:06 uue16 kernel: Symbols match kernel version 2.6.22.
Nov  8 21:20:06 uue16 kernel: No module symbols loaded - kernel modules not enabled. 
Nov  8 21:20:06 uue16 kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Nov  8 21:20:06 uue16 kernel: [    0.000000] BIOS-provided physical RAM map:
Nov  8 21:20:06 uue16 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov  8 21:20:06 uue16 kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov  8 21:20:06 uue16 kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Nov  8 21:20:06 uue16 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff80000 (usable)
Nov  8 21:20:06 uue16 kernel: [    0.000000]  BIOS-e820: 00000000bff80000 - 00000000bff8e000 (ACPI data)
Nov  8 21:20:06 uue16 kernel: [    0.000000]  BIOS-e820: 00000000bff8e000 - 00000000bffe0000 (ACPI NVS)
Nov  8 21:20:06 uue16 kernel: [    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
Nov  8 21:20:06 uue16 kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Nov  8 21:20:06 uue16 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Nov  8 21:20:06 uue16 kernel: [    0.000000] Warning only 4GB will be used.
Nov  8 21:20:06 uue16 kernel: [    0.000000] Use a PAE enabled kernel.
Nov  8 21:20:06 uue16 kernel: [    0.000000] 3200MB HIGHMEM available.
Nov  8 21:20:06 uue16 kernel: [    0.000000] 896MB LOWMEM available.
Nov  8 21:20:06 uue16 kernel: [    0.000000] found SMP MP-table at 000ff780
Nov  8 21:20:06 uue16 kernel: [    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
Nov  8 21:20:06 uue16 kernel: [    0.000000] Zone PFN ranges:
Nov  8 21:20:06 uue16 kernel: [    0.000000]   DMA             0 ->     4096
Nov  8 21:20:06 uue16 kernel: [    0.000000]   Normal       4096 ->   229376
Nov  8 21:20:06 uue16 kernel: [    0.000000]   HighMem    229376 ->  1048576
Nov  8 21:20:06 uue16 kernel: [    0.000000] early_node_map[1] active PFN ranges
Nov  8 21:20:06 uue16 kernel: [    0.000000]     0:        0 ->  1048576
Nov  8 21:20:06 uue16 kernel: [    0.000000] On node 0 totalpages: 1048576
Nov  8 21:20:06 uue16 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov  8 21:20:06 uue16 kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov  8 21:20:06 uue16 kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Nov  8 21:20:06 uue16 kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Nov  8 21:20:06 uue16 kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Nov  8 21:20:06 uue16 kernel: [    0.000000]   HighMem zone: 6400 pages used for memmap
Nov  8 21:20:06 uue16 kernel: [    0.000000]   HighMem zone: 812800 pages, LIFO batch:31
Nov  8 21:20:06 uue16 kernel: [    0.000000] DMI 2.3 present.
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FA740 checksum 0
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: RSDP 000FA740, 0024 (r2 ACPIAM)
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: XSDT BFF80100, 0044 (r1 A M I  OEMXSDT   7000610 MSFT       97)
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: FACP BFF80290, 00F4 (r3 A M I  OEMFACP   7000610 MSFT       97)
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: DSDT BFF80410, 84CF (r1  A0411 A0411000        0 INTL  2002026)
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: FACS BFF8E000, 0040
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: APIC BFF80390, 0080 (r1 A M I  OEMAPIC   7000610 MSFT       97)
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: OEMB BFF8E040, 0066 (r1 A M I  AMI_OEM   7000610 MSFT       97)
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: MCFG BFF888E0, 003C (r1 A M I  OEMMCFG   7000610 MSFT       97)
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Nov  8 21:20:06 uue16 kernel: [    0.000000] Processor #0 15:6 APIC version 20
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Nov  8 21:20:06 uue16 kernel: [    0.000000] Processor #2 15:6 APIC version 20
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
Nov  8 21:20:06 uue16 kernel: [    0.000000] Processor #1 15:6 APIC version 20
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Nov  8 21:20:06 uue16 kernel: [    0.000000] Processor #3 15:6 APIC version 20
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Nov  8 21:20:06 uue16 kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov  8 21:20:06 uue16 kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov  8 21:20:06 uue16 kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov  8 21:20:06 uue16 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov  8 21:20:06 uue16 kernel: [    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3fb00000)
Nov  8 21:20:06 uue16 kernel: [    0.000000] Built 1 zonelists.  Total pages: 1040384
Nov  8 21:20:06 uue16 kernel: [    0.000000] Kernel command line: root=UUID=e8bee423-266f-49eb-8f99-a75d19ffa386 ro quiet splash
Nov  8 21:20:06 uue16 kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Nov  8 21:20:06 uue16 kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Nov  8 21:20:06 uue16 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov  8 21:20:06 uue16 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov  8 21:20:06 uue16 kernel: [    0.000000] Initializing CPU#0
Nov  8 21:20:06 uue16 kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov  8 21:20:06 uue16 kernel: [    0.000000] Detected 3472.847 MHz processor.
Nov  8 21:20:06 uue16 kernel: [   28.945365] Console: colour VGA+ 80x25
Nov  8 21:20:06 uue16 kernel: [   28.945576] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov  8 21:20:06 uue16 kernel: [   28.945836] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov  8 21:20:06 uue16 kernel: [   29.112667] Memory: 3099116k/4194304k available (2015k kernel code, 44952k reserved, 916k data, 364k init, 2227712k highmem)
Nov  8 21:20:06 uue16 kernel: [   29.112676] virtual kernel memory layout:
Nov  8 21:20:06 uue16 kernel: [   29.112677]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Nov  8 21:20:06 uue16 kernel: [   29.112678]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov  8 21:20:06 uue16 kernel: [   29.112679]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Nov  8 21:20:06 uue16 kernel: [   29.112680]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Nov  8 21:20:06 uue16 kernel: [   29.112681]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Nov  8 21:20:06 uue16 kernel: [   29.112682]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Nov  8 21:20:06 uue16 kernel: [   29.112683]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Nov  8 21:20:06 uue16 kernel: [   29.112685] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov  8 21:20:06 uue16 kernel: [   29.112717] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
Nov  8 21:20:06 uue16 kernel: [   29.192503] Calibrating delay using timer specific routine.. 6951.62 BogoMIPS (lpj=13903247)
Nov  8 21:20:06 uue16 kernel: [   29.192524] Security Framework v1.0.0 initialized
Nov  8 21:20:06 uue16 kernel: [   29.192528] SELinux:  Disabled at boot.
Nov  8 21:20:06 uue16 kernel: [   29.192539] Mount-cache hash table entries: 512
Nov  8 21:20:06 uue16 kernel: [   29.192639] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
Nov  8 21:20:06 uue16 kernel: [   29.192647] monitor/mwait feature present.
Nov  8 21:20:06 uue16 kernel: [   29.192649] using mwait in idle threads.
Nov  8 21:20:06 uue16 kernel: [   29.192654] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov  8 21:20:06 uue16 kernel: [   29.192656] CPU: L2 cache: 2048K
Nov  8 21:20:06 uue16 kernel: [   29.192659] CPU: Physical Processor ID: 0
Nov  8 21:20:06 uue16 kernel: [   29.192660] CPU: Processor Core ID: 0
Nov  8 21:20:06 uue16 kernel: [   29.192662] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e43d 00000000 00000001
Nov  8 21:20:06 uue16 kernel: [   29.192671] Compat vDSO mapped to ffffe000.
Nov  8 21:20:06 uue16 kernel: [   29.192683] Checking 'hlt' instruction... OK.
Nov  8 21:20:06 uue16 kernel: [   29.208534] SMP alternatives: switching to UP code
Nov  8 21:20:06 uue16 kernel: [   29.208887] Early unpacking initramfs... done
Nov  8 21:20:06 uue16 kernel: [   29.460975] ACPI: Core revision 20070126
Nov  8 21:20:06 uue16 kernel: [   29.461028] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov  8 21:20:06 uue16 kernel: [   29.464926] CPU0: Intel(R) Pentium(R) D CPU 3.46GHz stepping 02
Nov  8 21:20:06 uue16 kernel: [   29.464942] SMP alternatives: switching to SMP code
Nov  8 21:20:06 uue16 kernel: [   29.465011] Booting processor 1/1 eip 3000
Nov  8 21:20:06 uue16 kernel: [   29.475193] Initializing CPU#1
Nov  8 21:20:06 uue16 kernel: [   29.555437] Calibrating delay using timer specific routine.. 6945.74 BogoMIPS (lpj=13891489)
Nov  8 21:20:06 uue16 kernel: [   29.555446] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
Nov  8 21:20:06 uue16 kernel: [   29.555452] monitor/mwait feature present.
Nov  8 21:20:06 uue16 kernel: [   29.555457] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov  8 21:20:06 uue16 kernel: [   29.555460] CPU: L2 cache: 2048K
Nov  8 21:20:06 uue16 kernel: [   29.555462] CPU: Physical Processor ID: 0
Nov  8 21:20:06 uue16 kernel: [   29.555464] CPU: Processor Core ID: 0
Nov  8 21:20:06 uue16 kernel: [   29.555466] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e43d 00000000 00000001
Nov  8 21:20:06 uue16 kernel: [   29.555945] CPU1: Intel(R) Pentium(R) D CPU 3.46GHz stepping 02
Nov  8 21:20:06 uue16 kernel: [   29.555967] SMP alternatives: switching to SMP code
Nov  8 21:20:06 uue16 kernel: [   29.556038] Booting processor 2/2 eip 3000
Nov  8 21:20:06 uue16 kernel: [   29.566222] Initializing CPU#2
Nov  8 21:20:06 uue16 kernel: [   29.643179] Calibrating delay using timer specific routine.. 6945.78 BogoMIPS (lpj=13891564)
Nov  8 21:20:06 uue16 kernel: [   29.643187] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
Nov  8 21:20:06 uue16 kernel: [   29.643191] monitor/mwait feature present.
Nov  8 21:20:06 uue16 kernel: [   29.643196] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov  8 21:20:06 uue16 kernel: [   29.643198] CPU: L2 cache: 2048K
Nov  8 21:20:06 uue16 kernel: [   29.643200] CPU: Physical Processor ID: 0
Nov  8 21:20:06 uue16 kernel: [   29.643201] CPU: Processor Core ID: 1
Nov  8 21:20:06 uue16 kernel: [   29.643202] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e43d 00000000 00000001
Nov  8 21:20:06 uue16 kernel: [   29.643643] CPU2: Intel(R) Pentium(R) D CPU 3.46GHz stepping 02
Nov  8 21:20:06 uue16 kernel: [   29.643656] SMP alternatives: switching to SMP code
Nov  8 21:20:06 uue16 kernel: [   29.643672] Booting processor 3/3 eip 3000
Nov  8 21:20:06 uue16 kernel: [   29.653854] Initializing CPU#3
Nov  8 21:20:06 uue16 kernel: [   29.730922] Calibrating delay using timer specific routine.. 6945.79 BogoMIPS (lpj=13891582)
Nov  8 21:20:06 uue16 kernel: [   29.730930] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
Nov  8 21:20:06 uue16 kernel: [   29.730936] monitor/mwait feature present.
Nov  8 21:20:06 uue16 kernel: [   29.730941] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov  8 21:20:06 uue16 kernel: [   29.730944] CPU: L2 cache: 2048K
Nov  8 21:20:06 uue16 kernel: [   29.730946] CPU: Physical Processor ID: 0
Nov  8 21:20:06 uue16 kernel: [   29.730948] CPU: Processor Core ID: 1
Nov  8 21:20:06 uue16 kernel: [   29.730949] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e43d 00000000 00000001
Nov  8 21:20:06 uue16 kernel: [   29.731380] CPU3: Intel(R) Pentium(R) D CPU 3.46GHz stepping 02
Nov  8 21:20:06 uue16 kernel: [   29.731413] Total of 4 processors activated (27788.94 BogoMIPS).
Nov  8 21:20:06 uue16 kernel: [   29.731559] ENABLING IO-APIC IRQs
Nov  8 21:20:06 uue16 kernel: [   29.731735] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov  8 21:20:06 uue16 kernel: [   29.878578] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Nov  8 21:20:06 uue16 kernel: [   29.898562] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Nov  8 21:20:06 uue16 kernel: [   29.918550] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Nov  8 21:20:06 uue16 kernel: [   29.938510] Brought up 4 CPUs
Nov  8 21:20:06 uue16 kernel: [   30.183170] migration_cost=95,863
Nov  8 21:20:06 uue16 kernel: [   30.183335] Booting paravirtualized kernel on bare hardware
Nov  8 21:20:06 uue16 kernel: [   30.183395] Time:  3:16:10  Date: 10/09/107
Nov  8 21:20:06 uue16 kernel: [   30.183415] NET: Registered protocol family 16
Nov  8 21:20:06 uue16 kernel: [   30.183488] EISA bus registered
Nov  8 21:20:06 uue16 kernel: [   30.183493] ACPI: bus type pci registered
Nov  8 21:20:06 uue16 kernel: [   30.183575] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
Nov  8 21:20:06 uue16 kernel: [   30.183577] PCI: Using configuration type 1
Nov  8 21:20:06 uue16 kernel: [   30.183579] Setting up standard PCI resources
Nov  8 21:20:06 uue16 kernel: [   30.195406] ACPI: EC: Look up EC in DSDT
Nov  8 21:20:06 uue16 kernel: [   30.203187] ACPI: Interpreter enabled
Nov  8 21:20:06 uue16 kernel: [   30.203190] ACPI: (supports S0 S1 S3 S4 S5)
Nov  8 21:20:06 uue16 kernel: [   30.203211] ACPI: Using IOAPIC for interrupt routing
Nov  8 21:20:06 uue16 kernel: [   30.211551] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov  8 21:20:06 uue16 kernel: [   30.211565] PCI: Probing PCI hardware (bus 00)
Nov  8 21:20:06 uue16 kernel: [   30.212130] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Nov  8 21:20:06 uue16 kernel: [   30.212134] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
Nov  8 21:20:06 uue16 kernel: [   30.213309] PCI: Transparent bridge - 0000:00:1e.0
Nov  8 21:20:06 uue16 kernel: [   30.213385] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov  8 21:20:06 uue16 kernel: [   30.213534] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Nov  8 21:20:06 uue16 kernel: [   30.213618] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
Nov  8 21:20:06 uue16 kernel: [   30.213733] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
Nov  8 21:20:06 uue16 kernel: [   30.213812] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
Nov  8 21:20:06 uue16 kernel: [   30.213879] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
Nov  8 21:20:06 uue16 kernel: [   30.213944] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
Nov  8 21:20:06 uue16 kernel: [   30.216911] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Nov  8 21:20:06 uue16 kernel: [   30.217023] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Nov  8 21:20:06 uue16 kernel: [   30.217132] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
Nov  8 21:20:06 uue16 kernel: [   30.217241] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Nov  8 21:20:06 uue16 kernel: [   30.217349] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 *14 15)
Nov  8 21:20:06 uue16 kernel: [   30.217459] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Nov  8 21:20:06 uue16 kernel: [   30.217594] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Nov  8 21:20:06 uue16 kernel: [   30.217706] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Nov  8 21:20:06 uue16 kernel: [   30.217810] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov  8 21:20:06 uue16 kernel: [   30.217820] pnp: PnP ACPI init
Nov  8 21:20:06 uue16 kernel: [   30.217829] ACPI: bus type pnp registered
Nov  8 21:20:06 uue16 kernel: [   30.223009] pnp: PnP ACPI: found 19 devices
Nov  8 21:20:06 uue16 kernel: [   30.223011] ACPI: ACPI bus type pnp unregistered
Nov  8 21:20:06 uue16 kernel: [   30.223015] PnPBIOS: Disabled by ACPI PNP
Nov  8 21:20:06 uue16 kernel: [   30.223068] PCI: Using ACPI for IRQ routing
Nov  8 21:20:06 uue16 kernel: [   30.223071] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov  8 21:20:06 uue16 kernel: [   30.237607] NET: Registered protocol family 8
Nov  8 21:20:06 uue16 kernel: [   30.237609] NET: Registered protocol family 20
Nov  8 21:20:06 uue16 kernel: [   30.237664] pnp: 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
Nov  8 21:20:06 uue16 kernel: [   30.237674] pnp: 00:08: ioport range 0x290-0x297 has been reserved
Nov  8 21:20:06 uue16 kernel: [   30.237679] pnp: 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
Nov  8 21:20:06 uue16 kernel: [   30.237682] pnp: 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
Nov  8 21:20:06 uue16 kernel: [   30.237685] pnp: 00:09: iomem range 0xfed50000-0xfed8ffff has been reserved
Nov  8 21:20:06 uue16 kernel: [   30.237688] pnp: 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
Nov  8 21:20:06 uue16 kernel: [   30.237692] pnp: 00:0a: ioport range 0x3f6-0x3f6 has been reserved
Nov  8 21:20:06 uue16 kernel: [   30.237698] pnp: 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
Nov  8 21:20:06 uue16 kernel: [   30.237701] pnp: 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
Nov  8 21:20:06 uue16 kernel: [   30.237708] pnp: 00:11: iomem range 0xf0000000-0xf3ffffff has been reserved
Nov  8 21:20:06 uue16 kernel: [   30.237714] pnp: 00:12: iomem range 0x0-0x9ffff could not be reserved
Nov  8 21:20:06 uue16 kernel: [   30.237717] pnp: 00:12: iomem range 0xc0000-0xdffff could not be reserved
Nov  8 21:20:06 uue16 kernel: [   30.237719] pnp: 00:12: iomem range 0xe0000-0xfffff could not be reserved
Nov  8 21:20:06 uue16 kernel: [   30.237722] pnp: 00:12: iomem range 0x100000-0xbfffffff could not be reserved
Nov  8 21:20:06 uue16 kernel: [   30.241441] Time: tsc clocksource has been installed.
Nov  8 21:20:06 uue16 kernel: [   30.267964] PCI: Bridge: 0000:00:01.0
Nov  8 21:20:06 uue16 kernel: [   30.267967]   IO window: c000-cfff
Nov  8 21:20:06 uue16 kernel: [   30.267971]   MEM window: fea00000-feafffff
Nov  8 21:20:06 uue16 kernel: [   30.267974]   PREFETCH window: cff00000-efefffff
Nov  8 21:20:06 uue16 kernel: [   30.267978] PCI: Bridge: 0000:00:1c.0
Nov  8 21:20:06 uue16 kernel: [   30.267979]   IO window: disabled.
Nov  8 21:20:06 uue16 kernel: [   30.267983]   MEM window: disabled.
Nov  8 21:20:06 uue16 kernel: [   30.267987]   PREFETCH window: cfe00000-cfefffff
Nov  8 21:20:06 uue16 kernel: [   30.267992] PCI: Bridge: 0000:00:1c.3
Nov  8 21:20:06 uue16 kernel: [   30.267994]   IO window: b000-bfff
Nov  8 21:20:06 uue16 kernel: [   30.267999]   MEM window: fe900000-fe9fffff
Nov  8 21:20:06 uue16 kernel: [   30.268002]   PREFETCH window: disabled.
Nov  8 21:20:06 uue16 kernel: [   30.268007] PCI: Bridge: 0000:00:1c.4
Nov  8 21:20:06 uue16 kernel: [   30.268010]   IO window: a000-afff
Nov  8 21:20:06 uue16 kernel: [   30.268014]   MEM window: fe800000-fe8fffff
Nov  8 21:20:06 uue16 kernel: [   30.268018]   PREFETCH window: disabled.
Nov  8 21:20:06 uue16 kernel: [   30.268022] PCI: Bridge: 0000:00:1c.5
Nov  8 21:20:06 uue16 kernel: [   30.268025]   IO window: 9000-9fff
Nov  8 21:20:06 uue16 kernel: [   30.268029]   MEM window: fe700000-fe7fffff
Nov  8 21:20:06 uue16 kernel: [   30.268033]   PREFETCH window: disabled.
Nov  8 21:20:06 uue16 kernel: [   30.268038] PCI: Bridge: 0000:00:1e.0
Nov  8 21:20:06 uue16 kernel: [   30.268040]   IO window: 8000-8fff
Nov  8 21:20:06 uue16 kernel: [   30.268045]   MEM window: f6200000-fe6fffff
Nov  8 21:20:06 uue16 kernel: [   30.268048]   PREFETCH window: disabled.
Nov  8 21:20:06 uue16 kernel: [   30.268063] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov  8 21:20:06 uue16 kernel: [   30.268068] PCI: Setting latency timer of device 0000:00:01.0 to 64
Nov  8 21:20:06 uue16 kernel: [   30.268085] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov  8 21:20:06 uue16 kernel: [   30.268090] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Nov  8 21:20:06 uue16 kernel: [   30.268107] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Nov  8 21:20:06 uue16 kernel: [   30.268112] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Nov  8 21:20:06 uue16 kernel: [   30.268129] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
Nov  8 21:20:06 uue16 kernel: [   30.268134] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Nov  8 21:20:06 uue16 kernel: [   30.268151] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 18
Nov  8 21:20:06 uue16 kernel: [   30.268156] PCI: Setting latency timer of device 0000:00:1c.5 to 64
Nov  8 21:20:06 uue16 kernel: [   30.268166] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Nov  8 21:20:06 uue16 kernel: [   30.268175] NET: Registered protocol family 2
Nov  8 21:20:06 uue16 kernel: [   30.305274] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov  8 21:20:06 uue16 kernel: [   30.305322] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Nov  8 21:20:06 uue16 kernel: [   30.306067] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov  8 21:20:06 uue16 kernel: [   30.306315] TCP: Hash tables configured (established 131072 bind 65536)
Nov  8 21:20:06 uue16 kernel: [   30.306317] TCP reno registered
Nov  8 21:20:06 uue16 kernel: [   30.317921] checking if image is initramfs... it is
Nov  8 21:20:06 uue16 kernel: [   30.764001] Switched to high resolution mode on CPU 1
Nov  8 21:20:06 uue16 kernel: [   30.764030] Switched to high resolution mode on CPU 2
Nov  8 21:20:06 uue16 kernel: [   30.764075] Switched to high resolution mode on CPU 3
Nov  8 21:20:06 uue16 kernel: [   30.767893] Switched to high resolution mode on CPU 0
Nov  8 21:20:06 uue16 kernel: [   30.813795] Freeing initrd memory: 7343k freed
Nov  8 21:20:06 uue16 kernel: [   30.814496] audit: initializing netlink socket (disabled)
Nov  8 21:20:06 uue16 kernel: [   30.814507] audit(1194578170.480:1): initialized
Nov  8 21:20:06 uue16 kernel: [   30.814601] highmem bounce pool size: 64 pages
Nov  8 21:20:06 uue16 kernel: [   30.816635] VFS: Disk quotas dquot_6.5.1
Nov  8 21:20:06 uue16 kernel: [   30.816684] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov  8 21:20:06 uue16 kernel: [   30.816765] io scheduler noop registered
Nov  8 21:20:06 uue16 kernel: [   30.816767] io scheduler anticipatory registered
Nov  8 21:20:06 uue16 kernel: [   30.816769] io scheduler deadline registered
Nov  8 21:20:06 uue16 kernel: [   30.816784] io scheduler cfq registered (default)
Nov  8 21:20:06 uue16 kernel: [   30.831676] Boot video device is 0000:06:00.0
Nov  8 21:20:06 uue16 kernel: [   30.831796] PCI: Setting latency timer of device 0000:00:01.0 to 64
Nov  8 21:20:06 uue16 kernel: [   30.831832] assign_interrupt_mode Found MSI capability
Nov  8 21:20:06 uue16 kernel: [   30.831835] Allocate Port Service[0000:00:01.0:pcie00]
Nov  8 21:20:06 uue16 kernel: [   30.831910] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Nov  8 21:20:06 uue16 kernel: [   30.831951] assign_interrupt_mode Found MSI capability
Nov  8 21:20:06 uue16 kernel: [   30.831953] Allocate Port Service[0000:00:1c.0:pcie00]
Nov  8 21:20:06 uue16 kernel: [   30.831987] Allocate Port Service[0000:00:1c.0:pcie02]
Nov  8 21:20:06 uue16 kernel: [   30.832067] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Nov  8 21:20:06 uue16 kernel: [   30.832107] assign_interrupt_mode Found MSI capability
Nov  8 21:20:06 uue16 kernel: [   30.832109] Allocate Port Service[0000:00:1c.3:pcie00]
Nov  8 21:20:06 uue16 kernel: [   30.832190] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Nov  8 21:20:06 uue16 kernel: [   30.832229] assign_interrupt_mode Found MSI capability
Nov  8 21:20:06 uue16 kernel: [   30.832232] Allocate Port Service[0000:00:1c.4:pcie00]
Nov  8 21:20:06 uue16 kernel: [   30.832314] PCI: Setting latency timer of device 0000:00:1c.5 to 64
Nov  8 21:20:06 uue16 kernel: [   30.832354] assign_interrupt_mode Found MSI capability
Nov  8 21:20:06 uue16 kernel: [   30.832356] Allocate Port Service[0000:00:1c.5:pcie00]
Nov  8 21:20:06 uue16 kernel: [   30.832499] isapnp: Scanning for PnP cards...
Nov  8 21:20:06 uue16 kernel: [   31.183076] isapnp: No Plug & Play device found
Nov  8 21:20:06 uue16 kernel: [   31.206089] Real Time Clock Driver v1.12ac
Nov  8 21:20:06 uue16 kernel: [   31.206174] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov  8 21:20:06 uue16 kernel: [   31.206263] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov  8 21:20:06 uue16 kernel: [   31.206948] 00:10: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov  8 21:20:06 uue16 kernel: [   31.207588] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov  8 21:20:06 uue16 kernel: [   31.207703] input: Macintosh mouse button emulation as /class/input/input0
Nov  8 21:20:06 uue16 kernel: [   31.207787] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Nov  8 21:20:06 uue16 kernel: [   31.210378] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov  8 21:20:06 uue16 kernel: [   31.210382] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov  8 21:20:06 uue16 kernel: [   31.210518] mice: PS/2 mouse device common for all mice
Nov  8 21:20:06 uue16 kernel: [   31.210633] EISA: Probing bus 0 at eisa.0
Nov  8 21:20:06 uue16 kernel: [   31.210659] Cannot allocate resource for EISA slot 8
Nov  8 21:20:06 uue16 kernel: [   31.210660] EISA: Detected 0 cards.
Nov  8 21:20:06 uue16 kernel: [   31.210720] TCP cubic registered
Nov  8 21:20:06 uue16 kernel: [   31.210730] NET: Registered protocol family 1
Nov  8 21:20:06 uue16 kernel: [   31.210747] Using IPI No-Shortcut mode
Nov  8 21:20:06 uue16 kernel: [   31.210894]   Magic number: 15:739:259
Nov  8 21:20:06 uue16 kernel: [   31.210905]   hash matches device ttyx1
Nov  8 21:20:06 uue16 kernel: [   31.210960]   hash matches device 0000:00:1d.7
Nov  8 21:20:06 uue16 kernel: [   31.211101] Freeing unused kernel memory: 364k freed
Nov  8 21:20:06 uue16 kernel: [   31.228869] input: AT Translated Set 2 keyboard as /class/input/input1
Nov  8 21:20:06 uue16 kernel: [   32.403098] AppArmor: AppArmor initialized<5>audit(1194578171.980:2):  type=1505 info="AppArmor initialized" pid=1378
Nov  8 21:20:06 uue16 kernel: [   32.408810] fuse init (API version 7.8)
Nov  8 21:20:06 uue16 kernel: [   32.413037] Failure registering capabilities with primary security module.
Nov  8 21:20:06 uue16 kernel: [   32.535162] ACPI Warning (tbutils-0217): Incorrect checksum in table [  Qµ] -  00, should be 01 [20070126]
Nov  8 21:20:06 uue16 kernel: [   32.535181] ACPI Error (tbinstal-0134): Table has invalid signature [  Qµ], must be SSDT, PSDT or OEMx [20070126]
Nov  8 21:20:06 uue16 kernel: [   32.535204] ACPI Error (psparse-0551): Method parse/execution failed [\_PR_.CPU1._PDC] (Node df83b150), AE_BAD_SIGNATURE
Nov  8 21:20:06 uue16 kernel: [   32.535528] ACPI: Processor [CPU1] (supports 8 throttling states)
Nov  8 21:20:06 uue16 kernel: [   32.632115] ACPI Warning (tbutils-0217): Incorrect checksum in table [  Qµ] -  00, should be 01 [20070126]
Nov  8 21:20:06 uue16 kernel: [   32.632132] ACPI Error (tbinstal-0134): Table has invalid signature [  Qµ], must be SSDT, PSDT or OEMx [20070126]
Nov  8 21:20:06 uue16 kernel: [   32.632153] ACPI Error (psparse-0551): Method parse/execution failed [\_PR_.CPU2._PDC] (Node df83b1e0), AE_BAD_SIGNATURE
Nov  8 21:20:06 uue16 kernel: [   33.138874] usbcore: registered new interface driver usbfs
Nov  8 21:20:06 uue16 kernel: [   33.138902] usbcore: registered new interface driver hub
Nov  8 21:20:06 uue16 kernel: [   33.138932] usbcore: registered new device driver usb
Nov  8 21:20:06 uue16 kernel: [   33.139920] USB Universal Host Controller Interface driver v3.0
Nov  8 21:20:06 uue16 kernel: [   33.139973] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
Nov  8 21:20:06 uue16 kernel: [   33.139985] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Nov  8 21:20:06 uue16 kernel: [   33.139990] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Nov  8 21:20:06 uue16 kernel: [   33.140090] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Nov  8 21:20:06 uue16 kernel: [   33.140119] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000e480
Nov  8 21:20:06 uue16 kernel: [   33.140250] usb usb1: configuration #1 chosen from 1 choice
Nov  8 21:20:06 uue16 kernel: [   33.140284] hub 1-0:1.0: USB hub found
Nov  8 21:20:06 uue16 kernel: [   33.140292] hub 1-0:1.0: 2 ports detected
Nov  8 21:20:06 uue16 kernel: [   33.144659] Floppy drive(s): fd0 is 1.44M
Nov  8 21:20:06 uue16 kernel: [   33.173353] FDC 0 is a post-1991 82077
Nov  8 21:20:06 uue16 kernel: [   33.175435] SCSI subsystem initialized
Nov  8 21:20:06 uue16 kernel: [   33.182245] libata version 2.21 loaded.
Nov  8 21:20:06 uue16 kernel: [   33.240587] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
Nov  8 21:20:06 uue16 kernel: [   33.240598] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Nov  8 21:20:06 uue16 kernel: [   33.240602] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Nov  8 21:20:06 uue16 kernel: [   33.240624] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Nov  8 21:20:06 uue16 kernel: [   33.240652] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000e800
Nov  8 21:20:06 uue16 kernel: [   33.240743] usb usb2: configuration #1 chosen from 1 choice
Nov  8 21:20:06 uue16 kernel: [   33.240771] hub 2-0:1.0: USB hub found
Nov  8 21:20:06 uue16 kernel: [   33.240777] hub 2-0:1.0: 2 ports detected
Nov  8 21:20:06 uue16 kernel: [   33.344256] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
Nov  8 21:20:06 uue16 kernel: [   33.344265] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Nov  8 21:20:06 uue16 kernel: [   33.344268] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Nov  8 21:20:06 uue16 kernel: [   33.344292] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Nov  8 21:20:06 uue16 kernel: [   33.344318] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000e880
Nov  8 21:20:06 uue16 kernel: [   33.344406] usb usb3: configuration #1 chosen from 1 choice
Nov  8 21:20:06 uue16 kernel: [   33.344430] hub 3-0:1.0: USB hub found
Nov  8 21:20:06 uue16 kernel: [   33.344436] hub 3-0:1.0: 2 ports detected
Nov  8 21:20:06 uue16 kernel: [   33.447948] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17
Nov  8 21:20:06 uue16 kernel: [   33.447957] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Nov  8 21:20:06 uue16 kernel: [   33.447960] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Nov  8 21:20:06 uue16 kernel: [   33.447985] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Nov  8 21:20:06 uue16 kernel: [   33.448012] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000ec00
Nov  8 21:20:06 uue16 kernel: [   33.448104] usb usb4: configuration #1 chosen from 1 choice
Nov  8 21:20:06 uue16 kernel: [   33.448129] hub 4-0:1.0: USB hub found
Nov  8 21:20:06 uue16 kernel: [   33.448135] hub 4-0:1.0: 2 ports detected
Nov  8 21:20:06 uue16 kernel: [   33.479774] usb 1-1: new full speed USB device using uhci_hcd and address 2
Nov  8 21:20:06 uue16 kernel: [   33.551675] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 21 (level, low) -> IRQ 21
Nov  8 21:20:06 uue16 kernel: [   33.551688] uhci_hcd 0000:01:00.0: UHCI Host Controller
Nov  8 21:20:06 uue16 kernel: [   33.551704] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
Nov  8 21:20:06 uue16 kernel: [   33.551718] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Nov  8 21:20:06 uue16 kernel: [   33.551722] uhci_hcd 0000:01:00.0: new USB bus registered, assigned bus number 5
Nov  8 21:20:06 uue16 kernel: [   33.551731] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Nov  8 21:20:06 uue16 kernel: [   33.551753] uhci_hcd 0000:01:00.0: irq 21, io base 0x00008880
Nov  8 21:20:06 uue16 kernel: [   33.551761] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 6
Nov  8 21:20:06 uue16 kernel: [   33.551793] ehci_hcd 0000:00:1d.7: debug port 1
Nov  8 21:20:06 uue16 kernel: [   33.551800] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
Nov  8 21:20:06 uue16 kernel: [   33.551807] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebfbc00
Nov  8 21:20:06 uue16 kernel: [   33.551863] usb usb5: configuration #1 chosen from 1 choice
Nov  8 21:20:06 uue16 kernel: [   33.551896] hub 5-0:1.0: USB hub found
Nov  8 21:20:06 uue16 kernel: [   33.551902] hub 5-0:1.0: 2 ports detected
Nov  8 21:20:06 uue16 kernel: [   33.599426] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov  8 21:20:06 uue16 kernel: [   33.655344] ACPI: PCI Interrupt 0000:01:00.1[B] -> GSI 22 (level, low) -> IRQ 22
Nov  8 21:20:06 uue16 kernel: [   33.655356] uhci_hcd 0000:01:00.1: UHCI Host Controller
Nov  8 21:20:06 uue16 kernel: [   33.655407] usb usb6: configuration #1 chosen from 1 choice
Nov  8 21:20:06 uue16 kernel: [   33.655433] hub 6-0:1.0: USB hub found
Nov  8 21:20:06 uue16 kernel: [   33.655440] hub 6-0:1.0: 8 ports detected
Nov  8 21:20:06 uue16 kernel: [   33.759031] uhci_hcd 0000:01:00.1: new USB bus registered, assigned bus number 7
Nov  8 21:20:06 uue16 kernel: [   33.759059] uhci_hcd 0000:01:00.1: irq 22, io base 0x00008c00
Nov  8 21:20:06 uue16 kernel: [   33.759148] usb usb7: configuration #1 chosen from 1 choice
Nov  8 21:20:06 uue16 kernel: [   33.759175] hub 7-0:1.0: USB hub found
Nov  8 21:20:06 uue16 kernel: [   33.759181] hub 7-0:1.0: 2 ports detected
Nov  8 21:20:06 uue16 kernel: [   33.862744] ACPI: PCI Interrupt 0000:01:00.2[C] -> GSI 23 (level, low) -> IRQ 23
Nov  8 21:20:06 uue16 kernel: [   33.862759] ehci_hcd 0000:01:00.2: EHCI Host Controller
Nov  8 21:20:06 uue16 kernel: [   33.862800] ehci_hcd 0000:01:00.2: new USB bus registered, assigned bus number 8
Nov  8 21:20:06 uue16 kernel: [   33.862845] ehci_hcd 0000:01:00.2: irq 23, io mem 0xfe6ffc00
Nov  8 21:20:06 uue16 kernel: [   33.862855] ehci_hcd 0000:01:00.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
Nov  8 21:20:06 uue16 kernel: [   33.862961] usb usb8: configuration #1 chosen from 1 choice
Nov  8 21:20:06 uue16 kernel: [   33.862999] hub 8-0:1.0: USB hub found
Nov  8 21:20:06 uue16 kernel: [   33.863007] hub 8-0:1.0: 4 ports detected
Nov  8 21:20:06 uue16 kernel: [   33.966431] ata_piix 0000:00:1f.1: version 2.11
Nov  8 21:20:06 uue16 kernel: [   33.966458] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 22
Nov  8 21:20:06 uue16 kernel: [   33.966464] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 21 (level, low) -> IRQ 21
Nov  8 21:20:06 uue16 kernel: [   33.966511] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Nov  8 21:20:06 uue16 kernel: [   33.966686] scsi0 : ata_piix
Nov  8 21:20:06 uue16 kernel: [   33.966733] scsi1 : ata_piix
Nov  8 21:20:06 uue16 kernel: [   33.966839] ata1: PATA max UDMA/133 cmd 0x0001d800 ctl 0x0001d482 bmdma 0x0001d000 irq 22
Nov  8 21:20:06 uue16 kernel: [   33.966843] ata2: PATA max UDMA/133 cmd 0x0001d400 ctl 0x0001d082 bmdma 0x0001d008 irq 22
Nov  8 21:20:06 uue16 kernel: [   34.006205] usb 1-1: device not accepting address 2, error -71
Nov  8 21:20:06 uue16 kernel: [   34.016132] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fe6ff000-fe6ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov  8 21:20:06 uue16 kernel: [   34.139884] ata1.00: ATA-7: Maxtor 6B300R0, BAH41E00, max UDMA/133
Nov  8 21:20:06 uue16 kernel: [   34.139889] ata1.00: 586114704 sectors, multi 16: LBA48 
Nov  8 21:20:06 uue16 kernel: [   34.140065] ata1.01: ATA-6: ST340015ACE, 3.01, max UDMA/100
Nov  8 21:20:06 uue16 kernel: [   34.140069] ata1.01: 78165360 sectors, multi 16: LBA 
Nov  8 21:20:06 uue16 kernel: [   34.155676] ata1.00: configured for UDMA/133
Nov  8 21:20:06 uue16 kernel: [   34.170204] ata1.01: configured for UDMA/100
Nov  8 21:20:06 uue16 kernel: [   34.335456] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6B300R0   BAH4 PQ: 0 ANSI: 5
Nov  8 21:20:06 uue16 kernel: [   34.335594] scsi 0:0:1:0: Direct-Access     ATA      ST340015ACE      3.01 PQ: 0 ANSI: 5
Nov  8 21:20:06 uue16 kernel: [   34.335657] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Nov  8 21:20:06 uue16 kernel: [   34.335685] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 23
Nov  8 21:20:06 uue16 kernel: [   34.335718] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Nov  8 21:20:06 uue16 kernel: [   34.335757] scsi2 : ata_piix
Nov  8 21:20:06 uue16 kernel: [   34.335830] scsi3 : ata_piix
Nov  8 21:20:06 uue16 kernel: [   34.335866] ata3: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e082 bmdma 0x0001d880 irq 23
Nov  8 21:20:06 uue16 kernel: [   34.335870] ata4: SATA max UDMA/133 cmd 0x0001e000 ctl 0x0001dc02 bmdma 0x0001d888 irq 23
Nov  8 21:20:06 uue16 kernel: [   34.498026] ata3.00: ATA-6: WDC WD740GD-00FLC0, 33.08F33, max UDMA/133
Nov  8 21:20:06 uue16 kernel: [   34.498030] ata3.00: 145226112 sectors, multi 16: LBA48 
Nov  8 21:20:06 uue16 kernel: [   34.513975] ata3.00: configured for UDMA/133
Nov  8 21:20:06 uue16 kernel: [   34.867938] ata4.00: ATA-7: WDC WD3200KS-00PFB0, 21.00M21, max UDMA/133
Nov  8 21:20:06 uue16 kernel: [   34.867942] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/1)
Nov  8 21:20:06 uue16 kernel: [   34.867947] ata4.01: ATAPI: PLEXTOR DVDR   PX-755A, 1.06, max UDMA/66
Nov  8 21:20:06 uue16 kernel: [   34.875952] ata4.00: configured for UDMA/133
Nov  8 21:20:06 uue16 kernel: [   34.939433] usb 6-1: new high speed USB device using ehci_hcd and address 2
Nov  8 21:20:06 uue16 kernel: [   35.039323] ata4.01: configured for UDMA/66
Nov  8 21:20:06 uue16 kernel: [   35.039430] scsi 2:0:0:0: Direct-Access     ATA      WDC WD740GD-00FL 33.0 PQ: 0 ANSI: 5
Nov  8 21:20:06 uue16 kernel: [   35.039561] scsi 3:0:0:0: Direct-Access     ATA      WDC WD3200KS-00P 21.0 PQ: 0 ANSI: 5
Nov  8 21:20:06 uue16 kernel: [   35.040254] scsi 3:0:1:0: CD-ROM            PLEXTOR  DVDR   PX-755A   1.06 PQ: 0 ANSI: 5
Nov  8 21:20:06 uue16 kernel: [   35.053749] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
Nov  8 21:20:06 uue16 kernel: [   35.053780] sd 0:0:0:0: [sda] Write Protect is off
Nov  8 21:20:06 uue16 kernel: [   35.053785] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  8 21:20:06 uue16 kernel: [   35.053876] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 21:20:06 uue16 kernel: [   35.053944] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
Nov  8 21:20:06 uue16 kernel: [   35.053959] sd 0:0:0:0: [sda] Write Protect is off
Nov  8 21:20:06 uue16 kernel: [   35.053963] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  8 21:20:06 uue16 kernel: [   35.053991] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 21:20:06 uue16 kernel: [   35.053996]  sda: sda1 sda2
Nov  8 21:20:06 uue16 kernel: [   35.071083] sd 0:0:0:0: [sda] Attached SCSI disk
Nov  8 21:20:06 uue16 kernel: [   35.071153] sd 0:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
Nov  8 21:20:06 uue16 kernel: [   35.071169] sd 0:0:1:0: [sdb] Write Protect is off
Nov  8 21:20:06 uue16 kernel: [   35.071173] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Nov  8 21:20:06 uue16 kernel: [   35.071198] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 21:20:06 uue16 kernel: [   35.071255] sd 0:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
Nov  8 21:20:06 uue16 kernel: [   35.071271] sd 0:0:1:0: [sdb] Write Protect is off
Nov  8 21:20:06 uue16 kernel: [   35.071274] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Nov  8 21:20:06 uue16 kernel: [   35.071300] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 21:20:06 uue16 kernel: [   35.071304]  sdb:<6>usb 6-1: configuration #1 chosen from 1 choice
Nov  8 21:20:06 uue16 kernel: [   35.097992]  sdb1 sdb2 < sdb5 >
Nov  8 21:20:06 uue16 kernel: [   35.125505] sd 0:0:1:0: [sdb] Attached SCSI disk
Nov  8 21:20:06 uue16 kernel: [   35.125571] sd 2:0:0:0: [sdc] 145226112 512-byte hardware sectors (74356 MB)
Nov  8 21:20:06 uue16 kernel: [   35.125586] sd 2:0:0:0: [sdc] Write Protect is off
Nov  8 21:20:06 uue16 kernel: [   35.125590] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Nov  8 21:20:06 uue16 kernel: [   35.125614] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 21:20:06 uue16 kernel: [   35.125664] sd 2:0:0:0: [sdc] 145226112 512-byte hardware sectors (74356 MB)
Nov  8 21:20:06 uue16 kernel: [   35.125680] sd 2:0:0:0: [sdc] Write Protect is off
Nov  8 21:20:06 uue16 kernel: [   35.125683] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Nov  8 21:20:06 uue16 kernel: [   35.125708] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 21:20:06 uue16 kernel: [   35.125712]  sdc: sdc1
Nov  8 21:20:06 uue16 kernel: [   35.136534] sd 2:0:0:0: [sdc] Attached SCSI disk
Nov  8 21:20:06 uue16 kernel: [   35.136592] sd 3:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
Nov  8 21:20:06 uue16 kernel: [   35.136607] sd 3:0:0:0: [sdd] Write Protect is off
Nov  8 21:20:06 uue16 kernel: [   35.136610] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Nov  8 21:20:06 uue16 kernel: [   35.136633] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 21:20:06 uue16 kernel: [   35.136680] sd 3:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
Nov  8 21:20:06 uue16 kernel: [   35.136694] sd 3:0:0:0: [sdd] Write Protect is off
Nov  8 21:20:06 uue16 kernel: [   35.136697] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Nov  8 21:20:06 uue16 kernel: [   35.136721] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 21:20:06 uue16 kernel: [   35.136725]  sdd: sdd1 sdd2 < sdd5 >
Nov  8 21:20:06 uue16 kernel: [   35.165410] sd 3:0:0:0: [sdd] Attached SCSI disk
Nov  8 21:20:06 uue16 kernel: [   35.168182] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Nov  8 21:20:06 uue16 kernel: [   35.168188] Uniform CD-ROM driver Revision: 3.20
Nov  8 21:20:06 uue16 kernel: [   35.168491] sr 3:0:1:0: Attached scsi CD-ROM sr0
Nov  8 21:20:06 uue16 kernel: [   35.171074] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov  8 21:20:06 uue16 kernel: [   35.171305] sd 0:0:1:0: Attached scsi generic sg1 type 0
Nov  8 21:20:06 uue16 kernel: [   35.171547] sd 2:0:0:0: Attached scsi generic sg2 type 0
Nov  8 21:20:06 uue16 kernel: [   35.171793] sd 3:0:0:0: Attached scsi generic sg3 type 0
Nov  8 21:20:06 uue16 kernel: [   35.172046] sr 3:0:1:0: Attached scsi generic sg4 type 5
Nov  8 21:20:06 uue16 kernel: [   35.282525] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800008e4aa6]
Nov  8 21:20:06 uue16 kernel: [   35.343759] Attempting manual resume
Nov  8 21:20:06 uue16 kernel: [   35.343762] swsusp: Resume From Partition 8:53
Nov  8 21:20:06 uue16 kernel: [   35.343764] PM: Checking swsusp image.
Nov  8 21:20:06 uue16 kernel: [   35.343914] PM: Resume from disk failed.
Nov  8 21:20:06 uue16 kernel: [   35.386078] kjournald starting.  Commit interval 5 seconds
Nov  8 21:20:06 uue16 kernel: [   35.386099] EXT3-fs: mounted filesystem with ordered data mode.
Nov  8 21:20:06 uue16 kernel: [   35.573542] usb 6-5: new high speed USB device using ehci_hcd and address 4
Nov  8 21:20:06 uue16 kernel: [   35.722438] usb 6-5: configuration #1 chosen from 1 choice
Nov  8 21:20:06 uue16 kernel: [   35.960392] usb 6-8: new high speed USB device using ehci_hcd and address 5
Nov  8 21:20:06 uue16 kernel: [   36.093952] usb 6-8: configuration #1 chosen from 1 choice
Nov  8 21:20:06 uue16 kernel: [   36.586522] usb 8-3: new high speed USB device using ehci_hcd and address 2
Nov  8 21:20:06 uue16 kernel: [   36.719035] usb 8-3: configuration #1 chosen from 1 choice
Nov  8 21:20:06 uue16 kernel: [   36.719551] usbcore: registered new interface driver libusual
Nov  8 21:20:06 uue16 kernel: [   36.957420] usb 1-2: new full speed USB device using uhci_hcd and address 4
Nov  8 21:20:06 uue16 kernel: [   37.134234] usb 1-2: configuration #1 chosen from 1 choice
Nov  8 21:20:06 uue16 kernel: [   37.504040] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov  8 21:20:06 uue16 kernel: [   37.504047] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov  8 21:20:06 uue16 kernel: [   37.619657] Initializing USB Mass Storage driver...
Nov  8 21:20:06 uue16 kernel: [   37.619737] scsi4 : SCSI emulation for USB Mass Storage devices
Nov  8 21:20:06 uue16 kernel: [   37.619785] usb-storage: device found at 2
Nov  8 21:20:06 uue16 kernel: [   37.619788] usb-storage: waiting for device to settle before scanning
Nov  8 21:20:06 uue16 kernel: [   37.619826] scsi5 : SCSI emulation for USB Mass Storage devices
Nov  8 21:20:06 uue16 kernel: [   37.619867] usb-storage: device found at 4
Nov  8 21:20:06 uue16 kernel: [   37.619869] usb-storage: waiting for device to settle before scanning
Nov  8 21:20:06 uue16 kernel: [   37.619903] scsi6 : SCSI emulation for USB Mass Storage devices
Nov  8 21:20:06 uue16 kernel: [   37.619942] usb-storage: device found at 5
Nov  8 21:20:06 uue16 kernel: [   37.619945] usb-storage: waiting for device to settle before scanning
Nov  8 21:20:06 uue16 kernel: [   37.619989] scsi7 : SCSI emulation for USB Mass Storage devices
Nov  8 21:20:06 uue16 kernel: [   37.620032] usb-storage: device found at 2
Nov  8 21:20:06 uue16 kernel: [   37.620035] usb-storage: waiting for device to settle before scanning
Nov  8 21:20:06 uue16 kernel: [   37.620044] usbcore: registered new interface driver usb-storage
Nov  8 21:20:06 uue16 kernel: [   37.620047] USB Mass Storage support registered.
Nov  8 21:20:06 uue16 kernel: [   41.927499] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov  8 21:20:06 uue16 kernel: [   41.990025] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov  8 21:20:06 uue16 kernel: [   41.994159] intel_rng: FWH not detected
Nov  8 21:20:06 uue16 kernel: [   42.015411] input: PC Speaker as /class/input/input2
Nov  8 21:20:06 uue16 kernel: [   42.154140] iTCO_vendor_support: vendor-support=0
Nov  8 21:20:06 uue16 kernel: [   42.155487] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Nov  8 21:20:06 uue16 kernel: [   42.447297] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 19 (level, low) -> IRQ 17
Nov  8 21:20:06 uue16 kernel: [   42.447312] PCI: Setting latency timer of device 0000:04:00.0 to 64
Nov  8 21:20:06 uue16 kernel: [   42.447338] sky2 0000:04:00.0: v1.18 addr 0xfe9fc000 irq 17 Yukon-EC (0xb6) rev 2
Nov  8 21:20:06 uue16 kernel: [   42.447459] sky2 eth0: addr 00:15:f2:a0:f8:e6
Nov  8 21:20:06 uue16 kernel: [   42.447482] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov  8 21:20:06 uue16 kernel: [   42.447492] PCI: Setting latency timer of device 0000:03:00.0 to 64
Nov  8 21:20:06 uue16 kernel: [   42.447517] sky2 0000:03:00.0: v1.18 addr 0xfe8fc000 irq 16 Yukon-EC (0xb6) rev 2
Nov  8 21:20:06 uue16 kernel: [   42.447626] sky2 eth1: addr 00:15:f2:a0:f1:e7
Nov  8 21:20:06 uue16 kernel: [   42.460023] sky2 eth0: enabling interface
Nov  8 21:20:06 uue16 kernel: [   42.574044] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
Nov  8 21:20:06 uue16 kernel: [   42.577300] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
Nov  8 21:20:06 uue16 kernel: [   42.577354] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Nov  8 21:20:06 uue16 kernel: [   42.577431] parport_pc 00:07: reported by Plug and Play ACPI
Nov  8 21:20:06 uue16 kernel: [   42.577539] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Nov  8 21:20:06 uue16 kernel: [   42.604804] usb-storage: device scan complete
Nov  8 21:20:06 uue16 kernel: [   42.604816] usb-storage: device scan complete
Nov  8 21:20:06 uue16 kernel: [   42.605057] usb-storage: device scan complete
Nov  8 21:20:06 uue16 kernel: [   42.605187] scsi 7:0:0:0: Direct-Access     HP       Photosmart 8200  1.00 PQ: 0 ANSI: 2
Nov  8 21:20:06 uue16 kernel: [   42.606172] usb-storage: device scan complete
Nov  8 21:20:06 uue16 kernel: [   42.606308] scsi 5:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
Nov  8 21:20:06 uue16 kernel: [   42.606460] sd 7:0:0:0: [sde] Attached SCSI removable disk
Nov  8 21:20:06 uue16 kernel: [   42.606510] sd 7:0:0:0: Attached scsi generic sg5 type 0
Nov  8 21:20:06 uue16 kernel: [   42.607545] scsi 4:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100D PQ: 0 ANSI: 4
Nov  8 21:20:06 uue16 kernel: [   42.607550] scsi 5:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
Nov  8 21:20:06 uue16 kernel: [   42.608786] scsi 5:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
Nov  8 21:20:06 uue16 kernel: [   42.610031] scsi 5:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
Nov  8 21:20:06 uue16 kernel: [   42.626834] Linux agpgart interface v0.102 (c) Dave Jones
Nov  8 21:20:06 uue16 kernel: [   42.640079] scsi 6:0:0:0: Direct-Access     IC25N030 ATCS04-0         CA3O PQ: 0 ANSI: 0
Nov  8 21:20:06 uue16 kernel: [   42.641179] sd 6:0:0:0: [sdf] 58605119 512-byte hardware sectors (30006 MB)
Nov  8 21:20:06 uue16 kernel: [   42.642175] sd 6:0:0:0: [sdf] Write Protect is off
Nov  8 21:20:06 uue16 kernel: [   42.642179] sd 6:0:0:0: [sdf] Mode Sense: 03 00 00 00
Nov  8 21:20:06 uue16 kernel: [   42.642182] sd 6:0:0:0: [sdf] Assuming drive cache: write through
Nov  8 21:20:06 uue16 kernel: [   42.643045] sd 6:0:0:0: [sdf] 58605119 512-byte hardware sectors (30006 MB)
Nov  8 21:20:06 uue16 kernel: [   42.643919] sd 6:0:0:0: [sdf] Write Protect is off
Nov  8 21:20:06 uue16 kernel: [   42.643923] sd 6:0:0:0: [sdf] Mode Sense: 03 00 00 00
Nov  8 21:20:06 uue16 kernel: [   42.643925] sd 6:0:0:0: [sdf] Assuming drive cache: write through
Nov  8 21:20:06 uue16 kernel: [   42.643929]  sdf:<6>/build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0xC202
Nov  8 21:20:06 uue16 kernel: [   42.673999] usbcore: registered new interface driver usblp
Nov  8 21:20:06 uue16 kernel: [   42.674002] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Nov  8 21:20:06 uue16 kernel: [   42.840286] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov  8 21:20:06 uue16 kernel: [   42.866985] [fglrx] Maximum main memory to use for locked dma buffers: 2888 MBytes.
Nov  8 21:20:06 uue16 kernel: [   42.867032] [fglrx] ASYNCIO init succeed!
Nov  8 21:20:06 uue16 kernel: [   42.868752] [fglrx] PAT is enabled successfully!
Nov  8 21:20:06 uue16 kernel: [   42.868772] [fglrx] module loaded - fglrx 8.42.3 [Oct 19 2007] on minor 0
Nov  8 21:20:06 uue16 kernel: [   42.916627]  sdf1
Nov  8 21:20:06 uue16 kernel: [   42.916708] sd 6:0:0:0: [sdf] Attached SCSI disk
Nov  8 21:20:06 uue16 kernel: [   42.916770] sd 6:0:0:0: Attached scsi generic sg6 type 0
Nov  8 21:20:06 uue16 kernel: [   42.917896] sd 5:0:0:0: [sdg] Attached SCSI removable disk
Nov  8 21:20:06 uue16 kernel: [   42.917954] sd 5:0:0:0: Attached scsi generic sg7 type 0
Nov  8 21:20:06 uue16 kernel: [   42.919006] sd 5:0:0:1: [sdh] Attached SCSI removable disk
Nov  8 21:20:06 uue16 kernel: [   42.919061] sd 5:0:0:1: Attached scsi generic sg8 type 0
Nov  8 21:20:06 uue16 kernel: [   42.920129] sd 5:0:0:2: [sdi] Attached SCSI removable disk
Nov  8 21:20:06 uue16 kernel: [   42.920183] sd 5:0:0:2: Attached scsi generic sg9 type 0
Nov  8 21:20:06 uue16 kernel: [   42.921250] sd 5:0:0:3: [sdj] Attached SCSI removable disk
Nov  8 21:20:06 uue16 kernel: [   42.921311] sd 5:0:0:3: Attached scsi generic sg10 type 0
Nov  8 21:20:06 uue16 kernel: [   42.926641] sd 4:0:0:0: [sdk] 625142448 512-byte hardware sectors (320073 MB)
Nov  8 21:20:06 uue16 kernel: [   42.928196] sd 4:0:0:0: [sdk] Write Protect is off
Nov  8 21:20:06 uue16 kernel: [   42.928201] sd 4:0:0:0: [sdk] Mode Sense: 1c 00 00 00
Nov  8 21:20:06 uue16 kernel: [   42.928204] sd 4:0:0:0: [sdk] Assuming drive cache: write through
Nov  8 21:20:06 uue16 kernel: [   42.930315] sd 4:0:0:0: [sdk] 625142448 512-byte hardware sectors (320073 MB)
Nov  8 21:20:06 uue16 kernel: [   42.931631] sd 4:0:0:0: [sdk] Write Protect is off
Nov  8 21:20:06 uue16 kernel: [   42.931635] sd 4:0:0:0: [sdk] Mode Sense: 1c 00 00 00
Nov  8 21:20:06 uue16 kernel: [   42.931638] sd 4:0:0:0: [sdk] Assuming drive cache: write through
Nov  8 21:20:06 uue16 kernel: [   42.931643]  sdk: sdk1
Nov  8 21:20:06 uue16 kernel: [   42.936500] sd 4:0:0:0: [sdk] Attached SCSI disk
Nov  8 21:20:06 uue16 kernel: [   42.936562] sd 4:0:0:0: Attached scsi generic sg11 type 0
Nov  8 21:20:06 uue16 kernel: [   43.106240] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 17
Nov  8 21:20:06 uue16 kernel: [   43.106261] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Nov  8 21:20:06 uue16 kernel: [   43.559212] lp0: using parport0 (interrupt-driven).
Nov  8 21:20:06 uue16 kernel: [   43.603047] Adding 9100780k swap on /dev/sdd5.  Priority:-1 extents:1 across:9100780k
Nov  8 21:20:06 uue16 kernel: [   43.970869] NET: Registered protocol family 17
Nov  8 21:20:06 uue16 kernel: [   44.177683] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Nov  8 21:20:06 uue16 kernel: [  261.837082] EXT3 FS on sdd1, internal journal
Nov  8 21:20:06 uue16 kernel: [  262.489921] NET: Registered protocol family 10
Nov  8 21:20:06 uue16 kernel: [  262.489996] lo: Disabled Privacy Extensions
Nov  8 21:20:06 uue16 kernel: [  264.366058] No dock devices found.
Nov  8 21:20:06 uue16 kernel: [  264.412237] input: Power Button (FF) as /class/input/input4
Nov  8 21:20:06 uue16 kernel: [  264.412256] ACPI: Power Button (FF) [PWRF]
Nov  8 21:20:06 uue16 kernel: [  264.412340] input: Power Button (CM) as /class/input/input5
Nov  8 21:20:06 uue16 kernel: [  264.412355] ACPI: Power Button (CM) [PWRB]
Nov  8 21:20:06 uue16 NetworkManager: <info>  starting... 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.469237] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_277c'). 
Nov  8 21:20:05 uue16 ntpdate[20863]: step time server 91.189.94.4 offset -0.682169 sec
Nov  8 21:20:05 uue16 NetworkManager: <debug> [1194578405.954168] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_277d'). 
Nov  8 21:20:06 uue16 kernel: [  265.606088] ppdev: user-space parallel port driver
Nov  8 21:20:06 uue16 kernel: [  265.672818] audit(1194578406.052:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=22102 profile="/usr/sbin/cupsd"
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.195984] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_7109'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.196866] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_7129'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.199253] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.200861] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.202215] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.202767] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_11ab_4362'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.203204] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27e0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.203710] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_11ab_4362_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.236884] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27e2'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.237380] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_11ab_6141'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.237875] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.238342] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.238771] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.239701] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_220d_noserial'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.240120] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_220d_noserial_if0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.240528] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.240932] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.241336] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.241741] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.242147] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.242550] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.242967] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.243370] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.243771] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.244216] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.244620] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.245040] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.245444] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.245847] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_if0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.246250] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_if0_scsi_host'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.246663] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_if0_scsi_host_scsi_device_lun0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.247070] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.247474] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.247878] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.248280] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.248683] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun1'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.249088] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun2'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.249493] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun3'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.249897] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.250299] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_if0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.250714] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_if0_scsi_host'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.251116] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_if0_scsi_host_scsi_device_lun0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.251517] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_244e'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.251918] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3038'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.252321] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.252737] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_0_if0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.253151] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3038_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.253566] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_1'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.253966] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_1_if0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.254365] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3104'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.254773] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_2'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.255173] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_2_if0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.255572] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.255970] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.256369] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if1'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.256766] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if2'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.257164] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if2_scsi_host'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.257563] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if2_scsi_host_scsi_device_lun0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.257962] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1102_5'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.258360] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_104c_8023'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.258767] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b8'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.259164] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.259561] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.259959] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.260359] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.260758] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.261155] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.261552] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_scsi_device_lun0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.261979] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.262375] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.262796] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.263194] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.263778] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.264179] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_floppy_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.264574] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.264969] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.265365] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.265760] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.266154] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.266549] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.266956] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a08'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.267350] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.267747] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.268142] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.268537] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.268930] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.269325] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0700'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.269719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0401'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.270113] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.270505] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.270910] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_1'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.271330] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.271796] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f03'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.272194] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_2'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.272603] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNPb02f'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.272995] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNPb006'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.273387] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.273779] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_3'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.274170] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.274561] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.274966] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.275357] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.275748] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_f2_a0_f8_e6'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.284170] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_f2_a0_f1_e7'). 
Nov  8 21:20:06 uue16 kernel: [  265.788448] sky2 eth1: enabling interface
Nov  8 21:20:06 uue16 kernel: [  265.792397] ADDRCONF(NETDEV_UP): eth1: link is not ready
Nov  8 21:20:06 uue16 NetworkManager: <info>  eth1: Device is fully-supported using driver 'sky2'. 
Nov  8 21:20:06 uue16 NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov  8 21:20:06 uue16 NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov  8 21:20:06 uue16 NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth1'. 
Nov  8 21:20:06 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.381414] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 21:20:06 uue16 NetworkManager: <info>  Will activate wired connection 'eth1' because it now has a link. 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.568576] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0_0_scsi_generic'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.569058] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun3_scsi_generic'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.569551] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.570016] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.570418] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.570847] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0_0_scsi_generic'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.571247] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if2_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.571658] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.572051] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.572464] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.572862] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun2_scsi_generic'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.573257] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_1'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.573649] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.574042] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.574530] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.574934] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.575326] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.575717] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.576107] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_1'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.576497] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_1'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.576887] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_2'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.577278] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.577667] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.578057] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.578445] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.578854] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.579261] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.579653] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.580048] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.580457] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.580847] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.581305] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_220d_noserial_usbraw'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.581751] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.582143] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.582533] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.582929] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_0_usbraw'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.583318] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.583706] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_usbraw'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.584095] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_usbraw'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.584481] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_usbraw'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.584868] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_1_usbraw'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.585254] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_2_usbraw'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.585641] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_usbraw'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.632945] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_floppy_0_storage'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.661015] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Maxtor_6B300R0_B620LRQH'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.689368] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_01C660C5D0074900'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.753407] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_36D04443D0440C15'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.789872] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST340015ACE_5LAEEQQH'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.849341] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_6c99eb8b_ecab_4126_bb00_453192aecfb6'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.854797] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.896806] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_e73ed621_c1d6_43e1_adc4_505d9a6360f9'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.905498] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD740GD_00FLC0_WD_WMAKE2361213'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.915103] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_4AA44F23A44F10BD'). 
Nov  8 21:20:06 uue16 NetworkManager: <debug> [1194578406.979456] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD3200KS_00PFB0_WD_WCAPD1030686'). 
Nov  8 21:20:07 uue16 NetworkManager: <debug> [1194578407.042798] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_e8bee423_266f_49eb_8f99_a75d19ffa386'). 
Nov  8 21:20:07 uue16 NetworkManager: <debug> [1194578407.097752] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024_0'). 
Nov  8 21:20:07 uue16 NetworkManager: <debug> [1194578407.278851] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_2d0e7fbd_476c_40ef_8e51_f20e13690ce1'). 
Nov  8 21:20:07 uue16 NetworkManager: <debug> [1194578407.340952] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_HP_Photosmart_8200_MY5AR3X0H504KK_0_0'). 
Nov  8 21:20:07 uue16 NetworkManager: <debug> [1194578407.348464] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_IC25N030_ATCS04_0_0_0_0'). 
Nov  8 21:20:07 uue16 NetworkManager: <debug> [1194578407.365915] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8CD0_6617'). 
Nov  8 21:20:07 uue16 NetworkManager: <debug> [1194578407.378489] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_STORAGE_DEVICE_0300836166_0_0'). 
Nov  8 21:20:07 uue16 NetworkManager: <debug> [1194578407.388554] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_STORAGE_DEVICE_0300836166_0_1'). 
Nov  8 21:20:07 uue16 mysqld_safe[22278]: started
Nov  8 21:20:07 uue16 NetworkManager: <debug> [1194578407.402602] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_STORAGE_DEVICE_0300836166_0_2'). 
Nov  8 21:20:07 uue16 NetworkManager: <debug> [1194578407.411569] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_STORAGE_DEVICE_0300836166_0_3'). 
Nov  8 21:20:07 uue16 NetworkManager: <debug> [1194578407.436571] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Seagate_FreeAgentDesktop_9QF3CG9K_0_0'). 
Nov  8 21:20:07 uue16 NetworkManager: <debug> [1194578407.549498] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_04F07BDEF07BD480'). 
Nov  8 21:20:07 uue16 NetworkManager: <debug> [1194578407.623141] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU4'). 
Nov  8 21:20:07 uue16 NetworkManager: <debug> [1194578407.630357] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU3'). 
Nov  8 21:20:07 uue16 NetworkManager: <debug> [1194578407.631287] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU2'). 
Nov  8 21:20:07 uue16 NetworkManager: <debug> [1194578407.631713] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Nov  8 21:20:07 uue16 NetworkManager: <debug> [1194578407.632110] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVDR___PX_755A'). 
Nov  8 21:20:07 uue16 hal_lpadmin: add
Nov  8 21:20:07 uue16 mysqld[22293]: 071108 21:20:07  InnoDB: Started; log sequence number 0 43655
Nov  8 21:20:07 uue16 kernel: [  267.469445] sky2 eth1: Link is up at 100 Mbps, full duplex, flow control rx
Nov  8 21:20:07 uue16 NetworkManager: <info>  Will activate wired connection 'eth1' because it now has a link. 
Nov  8 21:20:07 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:07 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 21:20:07 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:07 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:07 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:07 uue16 kernel: [  267.471666] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Nov  8 21:20:07 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:07 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:07 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:07 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:07 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:07 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:07 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:07 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:07 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:07 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 21:20:07 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 21:20:07 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:08 uue16 mysqld[22293]: 071108 21:20:08 [Note] /usr/sbin/mysqld: ready for connections.
Nov  8 21:20:08 uue16 mysqld[22293]: Version: '5.0.45-Debian_1ubuntu3-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian etch distribution
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:08 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:08 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:08 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:08 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:08 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:08 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:08 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:08 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:09 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:09 uue16 /etc/mysql/debian-start[22512]: Upgrading MySQL tables if necessary.
Nov  8 21:20:09 uue16 kernel: [  268.702461] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Nov  8 21:20:09 uue16 kernel: [  268.702468] apm: disabled - APM is not SMP safe.
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:09 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:09 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:09 uue16 atieventsd[22584]: ATI External Events Daemon started... 
Nov  8 21:20:09 uue16 atieventsd[22584]: Event daemon control socket created 
Nov  8 21:20:09 uue16 atieventsd[22584]: acpid connection established 
Nov  8 21:20:09 uue16 /etc/mysql/debian-start[22516]: Looking for 'mysql' in: /usr/bin/mysql
Nov  8 21:20:09 uue16 /etc/mysql/debian-start[22516]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck
Nov  8 21:20:09 uue16 /etc/mysql/debian-start[22516]: This installation of MySQL is already upgraded to 5.0.45, use --force if you still need to run mysql_upgrade
Nov  8 21:20:09 uue16 /etc/mysql/debian-start[22602]: Checking for insecure root accounts.
Nov  8 21:20:09 uue16 /etc/mysql/debian-start[22606]: WARNING: mysql.user contains 3 root accounts without password!
Nov  8 21:20:09 uue16 /etc/mysql/debian-start[22607]: Checking for crashed MySQL tables.
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:09 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:09 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:09 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:09 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 21:20:09 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:10 uue16 hal_lpadmin: URIs: ['hp:/usb/Photosmart_8200_series?serial=MY5AR3X0H504KK', 'usb://HP/Photosmart%208200%20series?serial=MY5AR3X0H504KK', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if0_printer_MY5AR3X0H504KK']
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:10 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:10 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:10 uue16 kernel: [  269.695010] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:10 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:10 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:10 uue16 kernel: [  269.785023] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Nov  8 21:20:10 uue16 kernel: [  269.785055] NFSD: starting 90-second grace period
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:10 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:10 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:10 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:10 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 21:20:10 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:11 uue16 python: hp-probe[23058]: warning: No devices found on the 'usb' bus. If this isn't the result you are expecting,
Nov  8 21:20:11 uue16 python: hp-probe[23058]: warning: check to make sure your devices are properly connected and powered on.
Nov  8 21:20:11 uue16 hal_lpadmin: HPLIP Fax URIs: None
Nov  8 21:20:11 uue16 hal_lpadmin: Not adding printer: Photosmart_8200_series already exists
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:11 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:11 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:11 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:11 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:11 uue16 snort[23081]: Var 'eth0_ADDRESS' defined, value len = 26 chars
Nov  8 21:20:11 uue16 snort[23081]: , value = 192.168.20.0/255.255.255.0 
Nov  8 21:20:11 uue16 snort[23081]: Var 'any_ADDRESS' defined, value len = 15 chars
Nov  8 21:20:11 uue16 snort[23081]: , value = 0.0.0.0/0.0.0.0 
Nov  8 21:20:11 uue16 snort[23081]: Var 'lo_ADDRESS' defined, value len = 19 chars
Nov  8 21:20:11 uue16 snort[23081]: , value = 127.0.0.0/255.0.0.0 
Nov  8 21:20:11 uue16 snort[23081]: Parsing Rules file /etc/snort/snort.conf 
Nov  8 21:20:11 uue16 snort[23081]: Var 'HOME_NET' redefined 
Nov  8 21:20:11 uue16 snort[23081]: Var 'EXTERNAL_NET' defined, value len = 3 chars
Nov  8 21:20:11 uue16 snort[23081]: , value = any 
Nov  8 21:20:11 uue16 snort[23081]: Var 'DNS_SERVERS' defined, value len = 16 chars
Nov  8 21:20:11 uue16 snort[23081]: , value = [192.168.0.0/16] 
Nov  8 21:20:11 uue16 snort[23081]: Var 'SMTP_SERVERS' defined, value len = 16 chars
Nov  8 21:20:11 uue16 snort[23081]: , value = [192.168.0.0/16] 
Nov  8 21:20:11 uue16 snort[23081]: Var 'HTTP_SERVERS' defined, value len = 16 chars
Nov  8 21:20:11 uue16 snort[23081]: , value = [192.168.0.0/16] 
Nov  8 21:20:11 uue16 snort[23081]: Var 'SQL_SERVERS' defined, value len = 16 chars
Nov  8 21:20:11 uue16 snort[23081]: , value = [192.168.0.0/16] 
Nov  8 21:20:11 uue16 snort[23081]: Var 'TELNET_SERVERS' defined, value len = 16 chars
Nov  8 21:20:11 uue16 snort[23081]: , value = [192.168.0.0/16] 
Nov  8 21:20:11 uue16 snort[23081]: Var 'SNMP_SERVERS' defined, value len = 16 chars
Nov  8 21:20:11 uue16 snort[23081]: , value = [192.168.0.0/16] 
Nov  8 21:20:11 uue16 snort[23081]: Var 'HTTP_PORTS' defined, value len = 2 chars
Nov  8 21:20:11 uue16 snort[23081]: , value = 80 
Nov  8 21:20:11 uue16 snort[23081]: Var 'SHELLCODE_PORTS' defined, value len = 3 chars
Nov  8 21:20:11 uue16 snort[23081]: , value = !80 
Nov  8 21:20:11 uue16 snort[23081]: Var 'ORACLE_PORTS' defined, value len = 4 chars
Nov  8 21:20:11 uue16 snort[23081]: , value = 1521 
Nov  8 21:20:11 uue16 snort[23081]: Var 'AIM_SERVERS' defined, value len = 185 chars
Nov  8 21:20:11 uue16 snort[23081]:  
Nov  8 21:20:11 uue16 snort[23081]:    [64.12.24.0/23,64.12.28.0/23,64.12.161.0/24,64.12.163.0/24,64.12.200.0/24,205.188.3.0/24,205.188.5.0/24,205.188.7.0/24,205.188.9 
Nov  8 21:20:11 uue16 snort[23081]:    .0/24,205.188.153.0/24,205.188.179.0/24,205.188.248.0/24] 
Nov  8 21:20:11 uue16 snort[23081]: Var 'RULE_PATH' defined, value len = 16 chars
Nov  8 21:20:11 uue16 snort[23081]: , value = /etc/snort/rules 
Nov  8 21:20:11 uue16 snort[23081]: ,-----------[Flow Config]---------------------- 
Nov  8 21:20:11 uue16 snort[23081]: | Stats Interval:  0 
Nov  8 21:20:11 uue16 snort[23081]: | Hash Method:     2 
Nov  8 21:20:11 uue16 snort[23081]: | Memcap:          10485760 
Nov  8 21:20:11 uue16 snort[23081]: | Rows  :          4099 
Nov  8 21:20:11 uue16 snort[23081]: | Overhead Bytes:  16400(%0.16) 
Nov  8 21:20:11 uue16 snort[23081]: `---------------------------------------------- 
Nov  8 21:20:11 uue16 snort[23081]: Frag3 global config: 
Nov  8 21:20:11 uue16 snort[23081]:     Max frags: 65536 
Nov  8 21:20:11 uue16 snort[23081]:     Fragment memory cap: 4194304 bytes 
Nov  8 21:20:11 uue16 snort[23081]: Frag3 engine config: 
Nov  8 21:20:11 uue16 snort[23081]:     Target-based policy: FIRST 
Nov  8 21:20:11 uue16 snort[23081]:     Fragment timeout: 60 seconds 
Nov  8 21:20:11 uue16 snort[23081]:     Fragment min_ttl:   1 
Nov  8 21:20:11 uue16 snort[23081]:     Fragment ttl_limit: 5 
Nov  8 21:20:11 uue16 snort[23081]:     Fragment Problems: 1 
Nov  8 21:20:11 uue16 snort[23081]:     Bound Addresses: 0.0.0.0/0.0.0.0 
Nov  8 21:20:11 uue16 snort[23081]: Stream5 global config: 
Nov  8 21:20:11 uue16 snort[23081]:     Track TCP sessions: ACTIVE 
Nov  8 21:20:11 uue16 snort[23081]:     Max TCP sessions: 8192 
Nov  8 21:20:11 uue16 snort[23081]:     Memcap (for reassembly packet storage): 8388608 
Nov  8 21:20:11 uue16 snort[23081]:     Track UDP sessions: INACTIVE 
Nov  8 21:20:11 uue16 snort[23081]:     Track ICMP sessions: INACTIVE 
Nov  8 21:20:11 uue16 snort[23081]: Stream5 TCP Policy config: 
Nov  8 21:20:11 uue16 snort[23081]:     Reassembly Policy: FIRST 
Nov  8 21:20:11 uue16 snort[23081]:     Timeout: 30 seconds 
Nov  8 21:20:11 uue16 snort[23081]:     Min ttl:  1 
Nov  8 21:20:11 uue16 snort[23081]:     Options: 
Nov  8 21:20:11 uue16 snort[23081]:         Static Flushpoint Sizes: YES 
Nov  8 21:20:11 uue16 snort[23081]:     Reassembly Ports: 
Nov  8 21:20:11 uue16 snort[23081]:       21 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:       23 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:       25 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:       42 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:       53 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:       80 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:       110 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:       111 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:       135 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:       136 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:       137 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:       139 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:       143 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:       445 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:       513 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:       1433 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:       1521 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:       3306 client (Footprint)  
Nov  8 21:20:11 uue16 snort[23081]:     Bound Addresses:0.0.0.0/0.0.0.0 
Nov  8 21:20:11 uue16 snort[23081]: HttpInspect Config: 
Nov  8 21:20:11 uue16 snort[23081]:     GLOBAL CONFIG 
Nov  8 21:20:11 uue16 snort[23081]:       Max Pipeline Requests:    0 
Nov  8 21:20:11 uue16 snort[23081]:       Inspection Type:          STATELESS 
Nov  8 21:20:11 uue16 snort[23081]:       Detect Proxy Usage:       NO 
Nov  8 21:20:11 uue16 snort[23081]:       IIS Unicode Map Filename: /etc/snort/unicode.map 
Nov  8 21:20:11 uue16 snort[23081]:       IIS Unicode Map Codepage: 1252 
Nov  8 21:20:11 uue16 snort[23081]:     DEFAULT SERVER CONFIG: 
Nov  8 21:20:11 uue16 snort[23081]:       Server profile: All 
Nov  8 21:20:11 uue16 snort[23081]:       Ports: 80 8080 8180  
Nov  8 21:20:11 uue16 snort[23081]:       Flow Depth: 300 
Nov  8 21:20:11 uue16 snort[23081]:       Max Chunk Length: 500000 
Nov  8 21:20:11 uue16 snort[23081]:       Inspect Pipeline Requests: YES 
Nov  8 21:20:11 uue16 snort[23081]:       URI Discovery Strict Mode: NO 
Nov  8 21:20:11 uue16 snort[23081]:       Allow Proxy Usage: NO 
Nov  8 21:20:11 uue16 snort[23081]:       Disable Alerting: NO 
Nov  8 21:20:11 uue16 snort[23081]:       Oversize Dir Length: 500 
Nov  8 21:20:11 uue16 snort[23081]:       Only inspect URI: NO 
Nov  8 21:20:11 uue16 snort[23081]:       Ascii: YES alert: NO 
Nov  8 21:20:11 uue16 snort[23081]:       Double Decoding: YES alert: YES 
Nov  8 21:20:11 uue16 snort[23081]:       %U Encoding: YES alert: YES 
Nov  8 21:20:11 uue16 snort[23081]:       Bare Byte: YES alert: YES 
Nov  8 21:20:11 uue16 snort[23081]:       Base36: OFF 
Nov  8 21:20:11 uue16 snort[23081]:       UTF 8: OFF 
Nov  8 21:20:11 uue16 snort[23081]:       IIS Unicode: YES alert: YES 
Nov  8 21:20:11 uue16 snort[23081]:       Multiple Slash: YES alert: NO 
Nov  8 21:20:11 uue16 snort[23081]:       IIS Backslash: YES alert: NO 
Nov  8 21:20:11 uue16 snort[23081]:       Directory Traversal: YES alert: NO 
Nov  8 21:20:11 uue16 snort[23081]:       Web Root Traversal: YES alert: YES 
Nov  8 21:20:11 uue16 snort[23081]:       Apache WhiteSpace: YES alert: NO 
Nov  8 21:20:11 uue16 snort[23081]:       IIS Delimiter: YES alert: NO 
Nov  8 21:20:11 uue16 snort[23081]:       IIS Unicode Map: GLOBAL IIS UNICODE MAP CONFIG 
Nov  8 21:20:11 uue16 snort[23081]:       Non-RFC Compliant Characters: NONE 
Nov  8 21:20:11 uue16 snort[23081]:       Whitespace Characters: 0x09 0x0b 0x0c 0x0d  
Nov  8 21:20:11 uue16 snort[23081]: rpc_decode arguments: 
Nov  8 21:20:11 uue16 snort[23081]:     Ports to decode RPC on: 111 32771  
Nov  8 21:20:11 uue16 snort[23081]:     alert_fragments: INACTIVE 
Nov  8 21:20:11 uue16 snort[23081]:     alert_large_fragments: ACTIVE 
Nov  8 21:20:11 uue16 snort[23081]:     alert_incomplete: ACTIVE 
Nov  8 21:20:11 uue16 snort[23081]:     alert_multiple_requests: ACTIVE 
Nov  8 21:20:11 uue16 snort[23081]: Portscan Detection Config: 
Nov  8 21:20:11 uue16 snort[23081]:     Detect Protocols:  TCP UDP ICMP IP 
Nov  8 21:20:11 uue16 snort[23081]:     Detect Scan Type:  portscan portsweep decoy_portscan distributed_portscan 
Nov  8 21:20:11 uue16 snort[23081]:     Sensitivity Level: Low 
Nov  8 21:20:11 uue16 snort[23081]:     Memcap (in bytes): 10000000 
Nov  8 21:20:11 uue16 snort[23081]:     Number of Nodes:   36900 
Nov  8 21:20:11 uue16 snort[23081]:  
Nov  8 21:20:11 uue16 snort[23081]: Tagged Packet Limit: 256 
Nov  8 21:20:11 uue16 snort[23081]:  
Nov  8 21:20:11 uue16 snort[23081]: +-----------------------[thresholding-config]---------------------------------- 
Nov  8 21:20:11 uue16 snort[23081]: | memory-cap : 1048576 bytes 
Nov  8 21:20:11 uue16 snort[23081]: +-----------------------[thresholding-global]---------------------------------- 
Nov  8 21:20:11 uue16 snort[23081]: | none 
Nov  8 21:20:11 uue16 snort[23081]: +-----------------------[thresholding-local]----------------------------------- 
Nov  8 21:20:11 uue16 snort[23081]: | none 
Nov  8 21:20:11 uue16 snort[23081]: +-----------------------[suppression]------------------------------------------ 
Nov  8 21:20:11 uue16 snort[23081]: | none 
Nov  8 21:20:11 uue16 snort[23081]: ------------------------------------------------------------------------------- 
Nov  8 21:20:11 uue16 snort[23081]: Rule application order: activation->dynamic->pass->drop->alert->log 
Nov  8 21:20:11 uue16 snort[23081]: Log directory = /var/log/snort 
Nov  8 21:20:11 uue16 snort[23081]: Loading dynamic engine /usr/lib/snort_dynamicengine/libsf_engine.so... 
Nov  8 21:20:11 uue16 snort[23081]: done 
Nov  8 21:20:11 uue16 snort[23081]: Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/... 
Nov  8 21:20:11 uue16 snort[23081]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ssh_preproc.so... 
Nov  8 21:20:11 uue16 snort[23081]: done 
Nov  8 21:20:11 uue16 snort[23081]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dns_preproc.so... 
Nov  8 21:20:11 uue16 snort[23081]: done 
Nov  8 21:20:11 uue16 snort[23081]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ftptelnet_preproc.so... 
Nov  8 21:20:11 uue16 snort[23081]: done 
Nov  8 21:20:11 uue16 snort[23081]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dcerpc_preproc.so... 
Nov  8 21:20:11 uue16 snort[23081]: done 
Nov  8 21:20:11 uue16 snort[23081]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_smtp_preproc.so... 
Nov  8 21:20:11 uue16 snort[23081]: done 
Nov  8 21:20:11 uue16 snort[23081]:   Finished Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/ 
Nov  8 21:20:11 uue16 snort[23081]: FTPTelnet Config: 
Nov  8 21:20:11 uue16 snort[23081]:     GLOBAL CONFIG 
Nov  8 21:20:11 uue16 snort[23081]:       Inspection Type: stateful 
Nov  8 21:20:11 uue16 snort[23081]:       Check for Encrypted Traffic: YES alert: YES 
Nov  8 21:20:11 uue16 snort[23081]:       Continue to check encrypted data: NO 
Nov  8 21:20:11 uue16 snort[23081]:     TELNET CONFIG: 
Nov  8 21:20:11 uue16 snort[23081]:       Ports: 23  
Nov  8 21:20:11 uue16 snort[23081]:       Are You There Threshold: 200 
Nov  8 21:20:11 uue16 snort[23081]:       Normalize: YES 
Nov  8 21:20:11 uue16 snort[23081]:       Detect Anomalies: NO 
Nov  8 21:20:11 uue16 snort[23081]:     FTP CONFIG: 
Nov  8 21:20:11 uue16 snort[23081]:       FTP Server: default 
Nov  8 21:20:11 uue16 snort[23081]:         Ports: 21  
Nov  8 21:20:11 uue16 snort[23081]:         Check for Telnet Cmds: YES alert: YES 
Nov  8 21:20:11 uue16 snort[23081]:         Identify open data channels: YES 
Nov  8 21:20:11 uue16 snort[23081]:       FTP Client: default 
Nov  8 21:20:11 uue16 snort[23081]:         Check for Bounce Attacks: YES alert: YES 
Nov  8 21:20:11 uue16 snort[23081]:         Check for Telnet Cmds: YES alert: YES 
Nov  8 21:20:11 uue16 snort[23081]:         Max Response Length: 256 
Nov  8 21:20:11 uue16 snort[23081]: SMTP Config: 
Nov  8 21:20:11 uue16 snort[23081]:       Ports: 
Nov  8 21:20:11 uue16 snort[23081]: 25 
Nov  8 21:20:11 uue16 snort[23081]:  
Nov  8 21:20:11 uue16 snort[23081]:       Inspection Type:            STATEFUL 
Nov  8 21:20:11 uue16 snort[23081]:       Normalize Spaces:           YES 
Nov  8 21:20:11 uue16 snort[23081]:       Ignore Data:                NO 
Nov  8 21:20:11 uue16 snort[23081]:       Ignore TLS Data:            NO 
Nov  8 21:20:11 uue16 snort[23081]:       Ignore Alerts:              NO 
Nov  8 21:20:11 uue16 snort[23081]:       Max Command Length:         0 
Nov  8 21:20:11 uue16 snort[23081]:       Max Header Line Length:     0 
Nov  8 21:20:11 uue16 snort[23081]:       Max Response Line Length:   0 
Nov  8 21:20:11 uue16 snort[23081]:       X-Link2State Alert:         YES 
Nov  8 21:20:11 uue16 snort[23081]:       Drop on X-Link2State Alert: NO 
Nov  8 21:20:11 uue16 snort[23081]:  DCE/RPC Decoder config: 
Nov  8 21:20:11 uue16 snort[23081]:     Autodetect ports ENABLED 
Nov  8 21:20:11 uue16 snort[23081]:     SMB fragmentation ENABLED 
Nov  8 21:20:11 uue16 snort[23081]:     DCE/RPC fragmentation ENABLED 
Nov  8 21:20:11 uue16 snort[23081]:     Max Frag Size: 3000 bytes 
Nov  8 21:20:11 uue16 snort[23081]:     Memcap: 100000 KB 
Nov  8 21:20:11 uue16 snort[23081]:     Alert if memcap exceeded DISABLED 
Nov  8 21:20:11 uue16 snort[23081]:  
Nov  8 21:20:11 uue16 snort[23081]: DNS config:  
Nov  8 21:20:11 uue16 snort[23081]:     DNS Client rdata txt Overflow Alert: ACTIVE 
Nov  8 21:20:11 uue16 snort[23081]:     Obsolete DNS RR Types Alert: INACTIVE 
Nov  8 21:20:11 uue16 snort[23081]:     Experimental DNS RR Types Alert: INACTIVE 
Nov  8 21:20:11 uue16 snort[23081]:     Ports:
Nov  8 21:20:11 uue16 snort[23081]:  53
Nov  8 21:20:11 uue16 snort[23081]:  
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:11 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:11 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:11 uue16 snort[23081]: Warning: flowbits key 'smb.tree.create.llsrpc' is set but not ever checked. 
Nov  8 21:20:11 uue16 snort[23081]: Warning: flowbits key 'realplayer.playlist' is checked but not ever set. 
Nov  8 21:20:11 uue16 snort[23081]: Warning: flowbits key 'community_uri.size.1050' is set but not ever checked. 
Nov  8 21:20:11 uue16 snort[23081]: Warning: flowbits key 'ms_sql_seen_dns' is checked but not ever set. 
Nov  8 21:20:11 uue16 snort[23081]: 37 out of 512 flowbits in use. 
Nov  8 21:20:11 uue16 kernel: [  271.359253] device eth0 entered promiscuous mode
Nov  8 21:20:11 uue16 kernel: [  271.359263] audit(1194578411.552:4): dev=eth0 prom=256 old_prom=0 auid=4294967295
Nov  8 21:20:11 uue16 snort[23081]: Initializing daemon mode 
Nov  8 21:20:11 uue16 kernel: [  271.375196] device eth0 left promiscuous mode
Nov  8 21:20:11 uue16 kernel: [  271.375203] audit(1194578411.552:5): dev=eth0 prom=0 old_prom=256 auid=4294967295
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:11 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:11 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 21:20:11 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:11 uue16 snort[23181]: PID path stat checked out ok, PID path set to /var/run/ 
Nov  8 21:20:11 uue16 kernel: [  271.391166] device eth0 entered promiscuous mode
Nov  8 21:20:11 uue16 snort[23181]: Writing PID "23181" to file "/var/run//snort_eth0.pid" 
Nov  8 21:20:11 uue16 snort[23081]: Daemon parent exiting 
Nov  8 21:20:11 uue16 kernel: [  271.391176] audit(1194578411.552:6): dev=eth0 prom=256 old_prom=0 auid=4294967295
Nov  8 21:20:11 uue16 snort[23181]: Daemon initialized, signaled parent pid: 23081 
Nov  8 21:20:12 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 21:20:12 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:12 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:12 uue16 NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Nov  8 21:20:12 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:12 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:12 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:12 uue16 NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Nov  8 21:20:12 uue16 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Nov  8 21:20:12 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:12 uue16 python: hp-probe[23273]: warning: No devices found on the 'usb' bus. If this isn't the result you are expecting,
Nov  8 21:20:12 uue16 python: hp-probe[23273]: warning: check to make sure your devices are properly connected and powered on.
Nov  8 21:20:12 uue16 NetworkManager: <debug> [1194578412.175543] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if0_printer_MY5AR3X0H504KK'). 
Nov  8 21:20:12 uue16 kernel: [  271.747982] Failure registering capabilities with primary security module.
Nov  8 21:20:12 uue16 avahi-daemon[23419]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Nov  8 21:20:12 uue16 avahi-daemon[23419]: Successfully dropped root privileges.
Nov  8 21:20:12 uue16 avahi-daemon[23419]: avahi-daemon 0.6.20 starting up.
Nov  8 21:20:12 uue16 avahi-daemon[23419]: Successfully called chroot().
Nov  8 21:20:12 uue16 avahi-daemon[23419]: Successfully dropped remaining capabilities.
Nov  8 21:20:12 uue16 avahi-daemon[23419]: No service file found in /etc/avahi/services.
Nov  8 21:20:12 uue16 avahi-daemon[23419]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.20.253.
Nov  8 21:20:12 uue16 avahi-daemon[23419]: New relevant interface eth0.IPv4 for mDNS.
Nov  8 21:20:12 uue16 avahi-daemon[23419]: Network interface enumeration completed.
Nov  8 21:20:12 uue16 avahi-daemon[23419]: Registering new address record for fe80::215:f2ff:fea0:f8e6 on eth0.*.
Nov  8 21:20:12 uue16 avahi-daemon[23419]: Registering new address record for 192.168.20.253 on eth0.IPv4.
Nov  8 21:20:12 uue16 avahi-daemon[23419]: Registering HINFO record with values 'I686'/'LINUX'.
Nov  8 21:20:12 uue16 dhcdbd: Started up.
Nov  8 21:20:12 uue16 NetworkManager: <info>  Activation (eth1) failed. 
Nov  8 21:20:12 uue16 NetworkManager: <info>  Deactivating device eth1. 
Nov  8 21:20:12 uue16 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Nov  8 21:20:13 uue16 avahi-daemon[23419]: Server startup complete. Host name is uue16.local. Local service cookie is 3435919472.
Nov  8 21:20:13 uue16 kernel: [  272.723175] eth0: no IPv6 routers present
Nov  8 21:20:14 uue16 hcid[23577]: Bluetooth HCI daemon
Nov  8 21:20:14 uue16 kernel: [  273.741871] Bluetooth: Core ver 2.11
Nov  8 21:20:14 uue16 kernel: [  273.741923] NET: Registered protocol family 31
Nov  8 21:20:14 uue16 kernel: [  273.741926] Bluetooth: HCI device and connection manager initialized
Nov  8 21:20:14 uue16 kernel: [  273.741930] Bluetooth: HCI socket layer initialized
Nov  8 21:20:14 uue16 hcid[23577]: Starting SDP server
Nov  8 21:20:14 uue16 kernel: [  273.841248] Bluetooth: L2CAP ver 2.8
Nov  8 21:20:14 uue16 kernel: [  273.841254] Bluetooth: L2CAP socket layer initialized
Nov  8 21:20:14 uue16 hcid[23577]: Created local server at unix:abstract=/var/run/dbus-k6FWOztQo0,guid=dfd77d727f3e947a369de7004733d1ee
Nov  8 21:20:14 uue16 audio[23601]: Bluetooth Audio daemon
Nov  8 21:20:14 uue16 audio[23601]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Nov  8 21:20:14 uue16 audio[23601]: Unix socket created: 5
Nov  8 21:20:14 uue16 input[23606]: Bluetooth Input daemon
Nov  8 21:20:14 uue16 input[23606]: Registered input manager path:/org/bluez/input
Nov  8 21:20:14 uue16 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Nov  8 21:20:14 uue16 NetworkManager: <info>  Will activate connection 'eth1'. 
Nov  8 21:20:14 uue16 NetworkManager: <info>  Device eth1 activation scheduled... 
Nov  8 21:20:14 uue16 NetworkManager: <info>  Activation (eth1) started... 
Nov  8 21:20:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 21:20:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 21:20:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 21:20:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 21:20:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 21:20:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Nov  8 21:20:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 21:20:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 21:20:14 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 21:20:14 uue16 kernel: [  273.927348] Bluetooth: RFCOMM socket layer initialized
Nov  8 21:20:14 uue16 kernel: [  273.927428] Bluetooth: RFCOMM TTY layer initialized
Nov  8 21:20:14 uue16 kernel: [  273.927431] Bluetooth: RFCOMM ver 1.8
Nov  8 21:20:14 uue16 audio[23601]: add_service_record: got record id 0x10000
Nov  8 21:20:14 uue16 audio[23601]: add_service_record: got record id 0x10001
Nov  8 21:20:14 uue16 audio[23601]: Registered manager path:/org/bluez/audio
Nov  8 21:20:14 uue16 anacron[23708]: Anacron 2.3 started on 2007-11-08
Nov  8 21:20:14 uue16 anacron[23708]: Normal exit (0 jobs run)
Nov  8 21:20:14 uue16 /usr/sbin/cron[23743]: (CRON) INFO (pidfile fd = 3)
Nov  8 21:20:14 uue16 /usr/sbin/cron[23748]: (CRON) STARTUP (fork ok)
Nov  8 21:20:14 uue16 /usr/sbin/cron[23748]: (CRON) INFO (Running @reboot jobs)
Nov  8 21:20:15 uue16 NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Nov  8 21:20:15 uue16 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 21:20:15 uue16 NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Nov  8 21:20:16 uue16 gdm[23671]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov  8 21:20:16 uue16 NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Nov  8 21:20:17 uue16 snort[23181]: Preprocessor/Decoder Rule Count: 0 
Nov  8 21:20:17 uue16 snort[23181]: Snort initialization completed successfully (pid=23181) 
Nov  8 21:20:17 uue16 snort[23181]: Not Using PCAP_FRAMES 
Nov  8 21:20:19 uue16 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Nov  8 21:20:20 uue16 gdm[23880]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov  8 21:20:24 uue16 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Nov  8 21:20:25 uue16 gdm[24016]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov  8 21:20:25 uue16 gdm[23670]: CRITICAL: gdm_config_value_get_bool: assertion `value->type == GDM_CONFIG_VALUE_BOOL' failed 
Nov  8 21:20:34 uue16 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Nov  8 21:20:41 uue16 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Nov  8 21:20:50 uue16 dhclient: No DHCPOFFERS received.
Nov  8 21:20:50 uue16 avahi-autoipd(eth1)[24129]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Nov  8 21:20:50 uue16 avahi-autoipd(eth1)[24129]: Successfully called chroot().
Nov  8 21:20:50 uue16 avahi-autoipd(eth1)[24129]: Successfully dropped root privileges.
Nov  8 21:20:50 uue16 avahi-autoipd(eth1)[24129]: Starting with address 169.254.12.33
Nov  8 21:20:55 uue16 avahi-autoipd(eth1)[24129]: Callout BIND, address 169.254.12.33 on interface eth1
Nov  8 21:20:55 uue16 avahi-daemon[23419]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.12.33.
Nov  8 21:20:55 uue16 avahi-daemon[23419]: New relevant interface eth1.IPv4 for mDNS.
Nov  8 21:20:55 uue16 avahi-daemon[23419]: Registering new address record for 169.254.12.33 on eth1.IPv4.
Nov  8 21:20:59 uue16 avahi-autoipd(eth1)[24129]: Successfully claimed IP address 169.254.12.33
Nov  8 21:20:59 uue16 NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface eth1 
Nov  8 21:20:59 uue16 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Nov  8 21:20:59 uue16 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Nov  8 21:20:59 uue16 NetworkManager: <info>  No DHCP reply received.  Automatically obtaining IP via Zeroconf. 
Nov  8 21:20:59 uue16 NetworkManager: <info>  avahi-autoipd running on eth1, assuming IPv4LL address 
Nov  8 21:20:59 uue16 NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov  8 21:20:59 uue16 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Nov  8 21:20:59 uue16 NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Nov  8 21:20:59 uue16 NetworkManager: <info>  not touching eth1 configuration, was configured externally 
Nov  8 21:20:59 uue16 NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Nov  8 21:20:59 uue16 NetworkManager: <info>  Activation (eth1) successful, device activated. 
Nov  8 21:20:59 uue16 NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Nov  8 21:20:59 uue16 dhcdbd: Unrequested down ?:3
Nov  8 21:20:59 uue16 NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Nov  8 21:21:01 uue16 ntpdate[24169]: adjust time server 91.189.94.4 offset 0.018284 sec
Nov  8 21:39:02 uue16 /USR/SBIN/CRON[24210]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov  8 21:44:38 uue16 init: tty4 main process (21279) killed by TERM signal
Nov  8 21:44:38 uue16 init: tty5 main process (21280) killed by TERM signal
Nov  8 21:44:38 uue16 init: tty3 main process (21284) killed by TERM signal
Nov  8 21:44:38 uue16 init: tty1 main process (21286) killed by TERM signal
Nov  8 21:44:38 uue16 init: tty6 main process (21287) killed by TERM signal
Nov  8 21:44:38 uue16 init: tty2 main process (21282) killed by TERM signal
Nov  8 21:44:49 uue16 avahi-daemon[23419]: Got SIGTERM, quitting.
Nov  8 21:44:49 uue16 avahi-daemon[23419]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.12.33.
Nov  8 21:44:49 uue16 avahi-daemon[23419]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.20.253.
Nov  8 21:44:51 uue16 atieventsd[22584]: Closing acpid connection 
Nov  8 21:44:51 uue16 atieventsd[22584]: Closing control socket 
Nov  8 21:44:51 uue16 atieventsd[22584]: ATI External Events Daemon shutting down 
Nov  8 21:44:52 uue16 rpc.statd[21104]: Caught signal 15, un-registering and exiting.
Nov  8 21:44:57 uue16 kernel: [ 1752.424420] device eth0 left promiscuous mode
Nov  8 21:44:57 uue16 kernel: [ 1752.424434] audit(1194579897.164:7): dev=eth0 prom=0 old_prom=256 auid=4294967295
Nov  8 21:44:57 uue16 mysqld[22293]: 071108 21:44:57 [Note] /usr/sbin/mysqld: Normal shutdown
Nov  8 21:44:57 uue16 mysqld[22293]: 
Nov  8 21:44:57 uue16 mysqld[22293]: 071108 21:44:57  InnoDB: Starting shutdown...
Nov  8 21:45:00 uue16 mysqld[22293]: 071108 21:45:00  InnoDB: Shutdown completed; log sequence number 0 43655
Nov  8 21:45:00 uue16 mysqld[22293]: 071108 21:45:00 [Note] /usr/sbin/mysqld: Shutdown complete
Nov  8 21:45:00 uue16 mysqld[22293]: 
Nov  8 21:45:00 uue16 mysqld_safe[24608]: ended
Nov  8 21:45:03 uue16 mountd[22954]: Caught signal 15, un-registering and exiting.
Nov  8 21:45:03 uue16 kernel: [ 1758.687467] nfsd: last server has exited
Nov  8 21:45:03 uue16 kernel: [ 1758.687473] nfsd: unexporting all filesystems
Nov  8 21:45:03 uue16 kernel: [ 1758.687990] RPC: failed to contact local rpcbind server (errno 5).
Nov  8 21:45:03 uue16 exiting on signal 15
Nov  8 22:01:13 uue16 syslogd 1.4.1#21ubuntu3: restart.
Nov  8 22:01:13 uue16 kernel: Inspecting /boot/System.map-2.6.22-14-generic
Nov  8 22:01:13 uue16 kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Nov  8 22:01:13 uue16 kernel: Symbols match kernel version 2.6.22.
Nov  8 22:01:13 uue16 kernel: No module symbols loaded - kernel modules not enabled. 
Nov  8 22:01:13 uue16 kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Nov  8 22:01:13 uue16 kernel: [    0.000000] BIOS-provided physical RAM map:
Nov  8 22:01:13 uue16 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov  8 22:01:13 uue16 kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov  8 22:01:13 uue16 kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Nov  8 22:01:13 uue16 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff80000 (usable)
Nov  8 22:01:13 uue16 kernel: [    0.000000]  BIOS-e820: 00000000bff80000 - 00000000bff8e000 (ACPI data)
Nov  8 22:01:13 uue16 kernel: [    0.000000]  BIOS-e820: 00000000bff8e000 - 00000000bffe0000 (ACPI NVS)
Nov  8 22:01:13 uue16 kernel: [    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
Nov  8 22:01:13 uue16 kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Nov  8 22:01:13 uue16 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Nov  8 22:01:13 uue16 kernel: [    0.000000] Warning only 4GB will be used.
Nov  8 22:01:13 uue16 kernel: [    0.000000] Use a PAE enabled kernel.
Nov  8 22:01:13 uue16 kernel: [    0.000000] 3200MB HIGHMEM available.
Nov  8 22:01:13 uue16 kernel: [    0.000000] 896MB LOWMEM available.
Nov  8 22:01:13 uue16 kernel: [    0.000000] found SMP MP-table at 000ff780
Nov  8 22:01:13 uue16 kernel: [    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
Nov  8 22:01:13 uue16 kernel: [    0.000000] Zone PFN ranges:
Nov  8 22:01:13 uue16 kernel: [    0.000000]   DMA             0 ->     4096
Nov  8 22:01:13 uue16 kernel: [    0.000000]   Normal       4096 ->   229376
Nov  8 22:01:13 uue16 kernel: [    0.000000]   HighMem    229376 ->  1048576
Nov  8 22:01:13 uue16 kernel: [    0.000000] early_node_map[1] active PFN ranges
Nov  8 22:01:13 uue16 kernel: [    0.000000]     0:        0 ->  1048576
Nov  8 22:01:13 uue16 kernel: [    0.000000] On node 0 totalpages: 1048576
Nov  8 22:01:13 uue16 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov  8 22:01:13 uue16 kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov  8 22:01:13 uue16 kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Nov  8 22:01:13 uue16 kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Nov  8 22:01:13 uue16 kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Nov  8 22:01:13 uue16 kernel: [    0.000000]   HighMem zone: 6400 pages used for memmap
Nov  8 22:01:13 uue16 kernel: [    0.000000]   HighMem zone: 812800 pages, LIFO batch:31
Nov  8 22:01:13 uue16 kernel: [    0.000000] DMI 2.3 present.
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FA740 checksum 0
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: RSDP 000FA740, 0024 (r2 ACPIAM)
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: XSDT BFF80100, 0044 (r1 A M I  OEMXSDT   7000610 MSFT       97)
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: FACP BFF80290, 00F4 (r3 A M I  OEMFACP   7000610 MSFT       97)
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: DSDT BFF80410, 84CF (r1  A0411 A0411000        0 INTL  2002026)
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: FACS BFF8E000, 0040
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: APIC BFF80390, 0080 (r1 A M I  OEMAPIC   7000610 MSFT       97)
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: OEMB BFF8E040, 0066 (r1 A M I  AMI_OEM   7000610 MSFT       97)
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: MCFG BFF888E0, 003C (r1 A M I  OEMMCFG   7000610 MSFT       97)
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Nov  8 22:01:13 uue16 kernel: [    0.000000] Processor #0 15:6 APIC version 20
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Nov  8 22:01:13 uue16 kernel: [    0.000000] Processor #2 15:6 APIC version 20
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
Nov  8 22:01:13 uue16 kernel: [    0.000000] Processor #1 15:6 APIC version 20
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Nov  8 22:01:13 uue16 kernel: [    0.000000] Processor #3 15:6 APIC version 20
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Nov  8 22:01:13 uue16 kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov  8 22:01:13 uue16 kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov  8 22:01:13 uue16 kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov  8 22:01:13 uue16 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov  8 22:01:13 uue16 kernel: [    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3fb00000)
Nov  8 22:01:13 uue16 kernel: [    0.000000] Built 1 zonelists.  Total pages: 1040384
Nov  8 22:01:13 uue16 kernel: [    0.000000] Kernel command line: root=UUID=e8bee423-266f-49eb-8f99-a75d19ffa386 ro quiet splash
Nov  8 22:01:13 uue16 kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Nov  8 22:01:13 uue16 kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Nov  8 22:01:13 uue16 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov  8 22:01:13 uue16 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov  8 22:01:13 uue16 kernel: [    0.000000] Initializing CPU#0
Nov  8 22:01:13 uue16 kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov  8 22:01:13 uue16 kernel: [    0.000000] Detected 3472.948 MHz processor.
Nov  8 22:01:13 uue16 kernel: [   25.583714] Console: colour VGA+ 80x25
Nov  8 22:01:13 uue16 kernel: [   25.583926] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov  8 22:01:13 uue16 kernel: [   25.584184] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov  8 22:01:13 uue16 kernel: [   25.750103] Memory: 3099116k/4194304k available (2015k kernel code, 44952k reserved, 916k data, 364k init, 2227712k highmem)
Nov  8 22:01:13 uue16 kernel: [   25.750112] virtual kernel memory layout:
Nov  8 22:01:13 uue16 kernel: [   25.750113]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Nov  8 22:01:13 uue16 kernel: [   25.750114]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov  8 22:01:13 uue16 kernel: [   25.750115]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Nov  8 22:01:13 uue16 kernel: [   25.750116]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Nov  8 22:01:13 uue16 kernel: [   25.750117]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Nov  8 22:01:13 uue16 kernel: [   25.750118]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Nov  8 22:01:13 uue16 kernel: [   25.750119]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Nov  8 22:01:13 uue16 kernel: [   25.750121] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov  8 22:01:13 uue16 kernel: [   25.750153] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
Nov  8 22:01:13 uue16 kernel: [   25.829939] Calibrating delay using timer specific routine.. 6951.52 BogoMIPS (lpj=13903044)
Nov  8 22:01:13 uue16 kernel: [   25.829960] Security Framework v1.0.0 initialized
Nov  8 22:01:13 uue16 kernel: [   25.829964] SELinux:  Disabled at boot.
Nov  8 22:01:13 uue16 kernel: [   25.829975] Mount-cache hash table entries: 512
Nov  8 22:01:13 uue16 kernel: [   25.830076] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
Nov  8 22:01:13 uue16 kernel: [   25.830083] monitor/mwait feature present.
Nov  8 22:01:13 uue16 kernel: [   25.830085] using mwait in idle threads.
Nov  8 22:01:13 uue16 kernel: [   25.830091] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov  8 22:01:13 uue16 kernel: [   25.830093] CPU: L2 cache: 2048K
Nov  8 22:01:13 uue16 kernel: [   25.830095] CPU: Physical Processor ID: 0
Nov  8 22:01:13 uue16 kernel: [   25.830097] CPU: Processor Core ID: 0
Nov  8 22:01:13 uue16 kernel: [   25.830099] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e43d 00000000 00000001
Nov  8 22:01:13 uue16 kernel: [   25.830108] Compat vDSO mapped to ffffe000.
Nov  8 22:01:13 uue16 kernel: [   25.830120] Checking 'hlt' instruction... OK.
Nov  8 22:01:13 uue16 kernel: [   25.845970] SMP alternatives: switching to UP code
Nov  8 22:01:13 uue16 kernel: [   25.846322] Early unpacking initramfs... done
Nov  8 22:01:13 uue16 kernel: [   26.098275] ACPI: Core revision 20070126
Nov  8 22:01:13 uue16 kernel: [   26.098328] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov  8 22:01:13 uue16 kernel: [   26.102300] CPU0: Intel(R) Pentium(R) D CPU 3.46GHz stepping 02
Nov  8 22:01:13 uue16 kernel: [   26.102316] SMP alternatives: switching to SMP code
Nov  8 22:01:13 uue16 kernel: [   26.102386] Booting processor 1/1 eip 3000
Nov  8 22:01:13 uue16 kernel: [   26.112596] Initializing CPU#1
Nov  8 22:01:13 uue16 kernel: [   26.192873] Calibrating delay using timer specific routine.. 6945.73 BogoMIPS (lpj=13891464)
Nov  8 22:01:13 uue16 kernel: [   26.192881] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
Nov  8 22:01:13 uue16 kernel: [   26.192887] monitor/mwait feature present.
Nov  8 22:01:13 uue16 kernel: [   26.192893] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov  8 22:01:13 uue16 kernel: [   26.192895] CPU: L2 cache: 2048K
Nov  8 22:01:13 uue16 kernel: [   26.192897] CPU: Physical Processor ID: 0
Nov  8 22:01:13 uue16 kernel: [   26.192899] CPU: Processor Core ID: 0
Nov  8 22:01:13 uue16 kernel: [   26.192901] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e43d 00000000 00000001
Nov  8 22:01:13 uue16 kernel: [   26.193380] CPU1: Intel(R) Pentium(R) D CPU 3.46GHz stepping 02
Nov  8 22:01:13 uue16 kernel: [   26.193402] SMP alternatives: switching to SMP code
Nov  8 22:01:13 uue16 kernel: [   26.193472] Booting processor 2/2 eip 3000
Nov  8 22:01:13 uue16 kernel: [   26.203655] Initializing CPU#2
Nov  8 22:01:13 uue16 kernel: [   26.280615] Calibrating delay using timer specific routine.. 6945.75 BogoMIPS (lpj=13891516)
Nov  8 22:01:13 uue16 kernel: [   26.280622] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
Nov  8 22:01:13 uue16 kernel: [   26.280627] monitor/mwait feature present.
Nov  8 22:01:13 uue16 kernel: [   26.280632] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov  8 22:01:13 uue16 kernel: [   26.280634] CPU: L2 cache: 2048K
Nov  8 22:01:13 uue16 kernel: [   26.280635] CPU: Physical Processor ID: 0
Nov  8 22:01:13 uue16 kernel: [   26.280637] CPU: Processor Core ID: 1
Nov  8 22:01:13 uue16 kernel: [   26.280638] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e43d 00000000 00000001
Nov  8 22:01:13 uue16 kernel: [   26.281089] CPU2: Intel(R) Pentium(R) D CPU 3.46GHz stepping 02
Nov  8 22:01:13 uue16 kernel: [   26.281103] SMP alternatives: switching to SMP code
Nov  8 22:01:13 uue16 kernel: [   26.281119] Booting processor 3/3 eip 3000
Nov  8 22:01:13 uue16 kernel: [   26.291305] Initializing CPU#3
Nov  8 22:01:13 uue16 kernel: [   26.368358] Calibrating delay using timer specific routine.. 6945.81 BogoMIPS (lpj=13891630)
Nov  8 22:01:13 uue16 kernel: [   26.368366] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e43d 00000000 00000001
Nov  8 22:01:13 uue16 kernel: [   26.368372] monitor/mwait feature present.
Nov  8 22:01:13 uue16 kernel: [   26.368377] CPU: Trace cache: 12K uops, L1 D cache: 16K
Nov  8 22:01:13 uue16 kernel: [   26.368380] CPU: L2 cache: 2048K
Nov  8 22:01:13 uue16 kernel: [   26.368382] CPU: Physical Processor ID: 0
Nov  8 22:01:13 uue16 kernel: [   26.368384] CPU: Processor Core ID: 1
Nov  8 22:01:13 uue16 kernel: [   26.368386] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e43d 00000000 00000001
Nov  8 22:01:13 uue16 kernel: [   26.368823] CPU3: Intel(R) Pentium(R) D CPU 3.46GHz stepping 02
Nov  8 22:01:13 uue16 kernel: [   26.368855] Total of 4 processors activated (27788.82 BogoMIPS).
Nov  8 22:01:13 uue16 kernel: [   26.369002] ENABLING IO-APIC IRQs
Nov  8 22:01:13 uue16 kernel: [   26.369178] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov  8 22:01:13 uue16 kernel: [   26.516014] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Nov  8 22:01:13 uue16 kernel: [   26.535999] checking TSC synchronization [CPU#0 -> CPU#2]:
Nov  8 22:01:13 uue16 kernel: [   26.555946] Measured 221 cycles TSC warp between CPUs, turning off TSC clock.
Nov  8 22:01:13 uue16 kernel: [    0.668000] Marking TSC unstable due to: check_tsc_sync_source failed.
Nov  8 22:01:13 uue16 kernel: [    0.672000] Brought up 4 CPUs
Nov  8 22:01:13 uue16 kernel: [    0.780000] migration_cost=4000,4000
Nov  8 22:01:13 uue16 kernel: [    0.780000] Booting paravirtualized kernel on bare hardware
Nov  8 22:01:13 uue16 kernel: [    0.780000] Time:  4:00:55  Date: 10/09/107
Nov  8 22:01:13 uue16 kernel: [    0.780000] NET: Registered protocol family 16
Nov  8 22:01:13 uue16 kernel: [    0.780000] EISA bus registered
Nov  8 22:01:13 uue16 kernel: [    0.780000] ACPI: bus type pci registered
Nov  8 22:01:13 uue16 kernel: [    0.780000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
Nov  8 22:01:13 uue16 kernel: [    0.780000] PCI: Using configuration type 1
Nov  8 22:01:13 uue16 kernel: [    0.780000] Setting up standard PCI resources
Nov  8 22:01:13 uue16 kernel: [    0.792000] ACPI: EC: Look up EC in DSDT
Nov  8 22:01:13 uue16 kernel: [    0.800000] ACPI: Interpreter enabled
Nov  8 22:01:13 uue16 kernel: [    0.800000] ACPI: (supports S0 S1 S3 S4 S5)
Nov  8 22:01:13 uue16 kernel: [    0.800000] ACPI: Using IOAPIC for interrupt routing
Nov  8 22:01:13 uue16 kernel: [    0.808000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov  8 22:01:13 uue16 kernel: [    0.808000] PCI: Probing PCI hardware (bus 00)
Nov  8 22:01:13 uue16 kernel: [    0.808000] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Nov  8 22:01:13 uue16 kernel: [    0.808000] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
Nov  8 22:01:13 uue16 kernel: [    0.812000] PCI: Transparent bridge - 0000:00:1e.0
Nov  8 22:01:13 uue16 kernel: [    0.812000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov  8 22:01:13 uue16 kernel: [    0.812000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Nov  8 22:01:13 uue16 kernel: [    0.812000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
Nov  8 22:01:13 uue16 kernel: [    0.812000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
Nov  8 22:01:13 uue16 kernel: [    0.812000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
Nov  8 22:01:13 uue16 kernel: [    0.812000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
Nov  8 22:01:13 uue16 kernel: [    0.812000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Nov  8 22:01:13 uue16 kernel: [    0.812000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Nov  8 22:01:13 uue16 kernel: [    0.812000] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
Nov  8 22:01:13 uue16 kernel: [    0.812000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Nov  8 22:01:13 uue16 kernel: [    0.816000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 *14 15)
Nov  8 22:01:13 uue16 kernel: [    0.816000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Nov  8 22:01:13 uue16 kernel: [    0.816000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Nov  8 22:01:13 uue16 kernel: [    0.816000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Nov  8 22:01:13 uue16 kernel: [    0.816000] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov  8 22:01:13 uue16 kernel: [    0.816000] pnp: PnP ACPI init
Nov  8 22:01:13 uue16 kernel: [    0.816000] ACPI: bus type pnp registered
Nov  8 22:01:13 uue16 kernel: [    0.820000] pnp: PnP ACPI: found 19 devices
Nov  8 22:01:13 uue16 kernel: [    0.820000] ACPI: ACPI bus type pnp unregistered
Nov  8 22:01:13 uue16 kernel: [    0.820000] PnPBIOS: Disabled by ACPI PNP
Nov  8 22:01:13 uue16 kernel: [    0.820000] PCI: Using ACPI for IRQ routing
Nov  8 22:01:13 uue16 kernel: [    0.820000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov  8 22:01:13 uue16 kernel: [    0.832000] NET: Registered protocol family 8
Nov  8 22:01:13 uue16 kernel: [    0.832000] NET: Registered protocol family 20
Nov  8 22:01:13 uue16 kernel: [    0.832000] pnp: 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
Nov  8 22:01:13 uue16 kernel: [    0.832000] pnp: 00:08: ioport range 0x290-0x297 has been reserved
Nov  8 22:01:13 uue16 kernel: [    0.832000] pnp: 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
Nov  8 22:01:13 uue16 kernel: [    0.832000] pnp: 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
Nov  8 22:01:13 uue16 kernel: [    0.832000] pnp: 00:09: iomem range 0xfed50000-0xfed8ffff has been reserved
Nov  8 22:01:13 uue16 kernel: [    0.832000] pnp: 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
Nov  8 22:01:13 uue16 kernel: [    0.832000] pnp: 00:0a: ioport range 0x3f6-0x3f6 has been reserved
Nov  8 22:01:13 uue16 kernel: [    0.832000] pnp: 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
Nov  8 22:01:13 uue16 kernel: [    0.832000] pnp: 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
Nov  8 22:01:13 uue16 kernel: [    0.832000] pnp: 00:11: iomem range 0xf0000000-0xf3ffffff has been reserved
Nov  8 22:01:13 uue16 kernel: [    0.832000] pnp: 00:12: iomem range 0x0-0x9ffff could not be reserved
Nov  8 22:01:13 uue16 kernel: [    0.832000] pnp: 00:12: iomem range 0xc0000-0xdffff could not be reserved
Nov  8 22:01:13 uue16 kernel: [    0.832000] pnp: 00:12: iomem range 0xe0000-0xfffff could not be reserved
Nov  8 22:01:13 uue16 kernel: [    0.832000] pnp: 00:12: iomem range 0x100000-0xbfffffff could not be reserved
Nov  8 22:01:13 uue16 kernel: [    0.864000] PCI: Bridge: 0000:00:01.0
Nov  8 22:01:13 uue16 kernel: [    0.864000]   IO window: c000-cfff
Nov  8 22:01:13 uue16 kernel: [    0.864000]   MEM window: fea00000-feafffff
Nov  8 22:01:13 uue16 kernel: [    0.864000]   PREFETCH window: cff00000-efefffff
Nov  8 22:01:13 uue16 kernel: [    0.864000] PCI: Bridge: 0000:00:1c.0
Nov  8 22:01:13 uue16 kernel: [    0.864000]   IO window: disabled.
Nov  8 22:01:13 uue16 kernel: [    0.864000]   MEM window: disabled.
Nov  8 22:01:13 uue16 kernel: [    0.864000]   PREFETCH window: cfe00000-cfefffff
Nov  8 22:01:13 uue16 kernel: [    0.864000] PCI: Bridge: 0000:00:1c.3
Nov  8 22:01:13 uue16 kernel: [    0.864000]   IO window: b000-bfff
Nov  8 22:01:13 uue16 kernel: [    0.864000]   MEM window: fe900000-fe9fffff
Nov  8 22:01:13 uue16 kernel: [    0.864000]   PREFETCH window: disabled.
Nov  8 22:01:13 uue16 kernel: [    0.864000] PCI: Bridge: 0000:00:1c.5
Nov  8 22:01:13 uue16 kernel: [    0.864000]   IO window: a000-afff
Nov  8 22:01:13 uue16 kernel: [    0.864000]   MEM window: fe800000-fe8fffff
Nov  8 22:01:13 uue16 kernel: [    0.864000]   PREFETCH window: disabled.
Nov  8 22:01:13 uue16 kernel: [    0.864000] PCI: Bridge: 0000:00:1e.0
Nov  8 22:01:13 uue16 kernel: [    0.864000]   IO window: 9000-9fff
Nov  8 22:01:13 uue16 kernel: [    0.864000]   MEM window: f6300000-fe7fffff
Nov  8 22:01:13 uue16 kernel: [    0.864000]   PREFETCH window: disabled.
Nov  8 22:01:13 uue16 kernel: [    0.864000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov  8 22:01:13 uue16 kernel: [    0.864000] PCI: Setting latency timer of device 0000:00:01.0 to 64
Nov  8 22:01:13 uue16 kernel: [    0.864000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov  8 22:01:13 uue16 kernel: [    0.864000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Nov  8 22:01:13 uue16 kernel: [    0.864000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Nov  8 22:01:13 uue16 kernel: [    0.864000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Nov  8 22:01:13 uue16 kernel: [    0.864000] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 18
Nov  8 22:01:13 uue16 kernel: [    0.864000] PCI: Setting latency timer of device 0000:00:1c.5 to 64
Nov  8 22:01:13 uue16 kernel: [    0.864000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Nov  8 22:01:13 uue16 kernel: [    0.864000] NET: Registered protocol family 2
Nov  8 22:01:13 uue16 kernel: [    0.868000] Time: acpi_pm clocksource has been installed.
Nov  8 22:01:13 uue16 kernel: [    0.868000] Switched to high resolution mode on CPU 0
Nov  8 22:01:13 uue16 kernel: [    0.868000] Switched to high resolution mode on CPU 1
Nov  8 22:01:13 uue16 kernel: [    0.868000] Switched to high resolution mode on CPU 2
Nov  8 22:01:13 uue16 kernel: [    0.868000] Switched to high resolution mode on CPU 3
Nov  8 22:01:13 uue16 kernel: [    0.908000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov  8 22:01:13 uue16 kernel: [    0.908000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Nov  8 22:01:13 uue16 kernel: [    0.908000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov  8 22:01:13 uue16 kernel: [    0.908000] TCP: Hash tables configured (established 131072 bind 65536)
Nov  8 22:01:13 uue16 kernel: [    0.908000] TCP reno registered
Nov  8 22:01:13 uue16 kernel: [    0.924000] checking if image is initramfs... it is
Nov  8 22:01:13 uue16 kernel: [    1.420000] Freeing initrd memory: 7343k freed
Nov  8 22:01:13 uue16 kernel: [    1.420000] audit: initializing netlink socket (disabled)
Nov  8 22:01:13 uue16 kernel: [    1.420000] audit(1194580855.368:1): initialized
Nov  8 22:01:13 uue16 kernel: [    1.420000] highmem bounce pool size: 64 pages
Nov  8 22:01:13 uue16 kernel: [    1.424000] VFS: Disk quotas dquot_6.5.1
Nov  8 22:01:13 uue16 kernel: [    1.424000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov  8 22:01:13 uue16 kernel: [    1.424000] io scheduler noop registered
Nov  8 22:01:13 uue16 kernel: [    1.424000] io scheduler anticipatory registered
Nov  8 22:01:13 uue16 kernel: [    1.424000] io scheduler deadline registered
Nov  8 22:01:13 uue16 kernel: [    1.424000] io scheduler cfq registered (default)
Nov  8 22:01:13 uue16 kernel: [    1.452000] Boot video device is 0000:05:00.0
Nov  8 22:01:13 uue16 NetworkManager: <info>  starting... 
Nov  8 22:01:13 uue16 kernel: [    1.452000] PCI: Setting latency timer of device 0000:00:01.0 to 64
Nov  8 22:01:13 uue16 kernel: [    1.452000] assign_interrupt_mode Found MSI capability
Nov  8 22:01:13 uue16 kernel: [    1.452000] Allocate Port Service[0000:00:01.0:pcie00]
Nov  8 22:01:13 uue16 kernel: [    1.452000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Nov  8 22:01:13 uue16 kernel: [    1.452000] assign_interrupt_mode Found MSI capability
Nov  8 22:01:13 uue16 kernel: [    1.452000] Allocate Port Service[0000:00:1c.0:pcie00]
Nov  8 22:01:13 uue16 kernel: [    1.452000] Allocate Port Service[0000:00:1c.0:pcie02]
Nov  8 22:01:13 uue16 kernel: [    1.452000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Nov  8 22:01:13 uue16 kernel: [    1.452000] assign_interrupt_mode Found MSI capability
Nov  8 22:01:13 uue16 kernel: [    1.452000] Allocate Port Service[0000:00:1c.3:pcie00]
Nov  8 22:01:13 uue16 kernel: [    1.452000] PCI: Setting latency timer of device 0000:00:1c.5 to 64
Nov  8 22:01:13 uue16 kernel: [    1.452000] assign_interrupt_mode Found MSI capability
Nov  8 22:01:13 uue16 kernel: [    1.452000] Allocate Port Service[0000:00:1c.5:pcie00]
Nov  8 22:01:13 uue16 kernel: [    1.452000] isapnp: Scanning for PnP cards...
Nov  8 22:01:13 uue16 kernel: [    1.804000] isapnp: No Plug & Play device found
Nov  8 22:01:13 uue16 kernel: [    1.828000] Real Time Clock Driver v1.12ac
Nov  8 22:01:13 uue16 kernel: [    1.828000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov  8 22:01:13 uue16 kernel: [    1.828000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov  8 22:01:13 uue16 kernel: [    1.828000] 00:10: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov  8 22:01:13 uue16 kernel: [    1.828000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov  8 22:01:13 uue16 kernel: [    1.828000] input: Macintosh mouse button emulation as /class/input/input0
Nov  8 22:01:13 uue16 kernel: [    1.828000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Nov  8 22:01:13 uue16 kernel: [    1.832000] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov  8 22:01:13 uue16 kernel: [    1.832000] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov  8 22:01:13 uue16 kernel: [    1.832000] mice: PS/2 mouse device common for all mice
Nov  8 22:01:13 uue16 kernel: [    1.832000] EISA: Probing bus 0 at eisa.0
Nov  8 22:01:13 uue16 kernel: [    1.832000] EISA: Detected 0 cards.
Nov  8 22:01:13 uue16 kernel: [    1.832000] TCP cubic registered
Nov  8 22:01:13 uue16 kernel: [    1.832000] NET: Registered protocol family 1
Nov  8 22:01:13 uue16 kernel: [    1.832000] Using IPI No-Shortcut mode
Nov  8 22:01:13 uue16 kernel: [    1.832000]   Magic number: 15:89:9
Nov  8 22:01:13 uue16 kernel: [    1.832000] Freeing unused kernel memory: 364k freed
Nov  8 22:01:13 uue16 kernel: [    1.848000] input: AT Translated Set 2 keyboard as /class/input/input1
Nov  8 22:01:13 uue16 kernel: [    3.028000] AppArmor: AppArmor initialized<5>audit(1194580856.868:2):  type=1505 info="AppArmor initialized" pid=1374
Nov  8 22:01:13 uue16 kernel: [    3.036000] fuse init (API version 7.8)
Nov  8 22:01:13 uue16 kernel: [    3.040000] Failure registering capabilities with primary security module.
Nov  8 22:01:13 uue16 kernel: [    3.164000] ACPI Warning (tbutils-0217): Incorrect checksum in table [  Qµ] -  00, should be 01 [20070126]
Nov  8 22:01:13 uue16 kernel: [    3.164000] ACPI Error (tbinstal-0134): Table has invalid signature [  Qµ], must be SSDT, PSDT or OEMx [20070126]
Nov  8 22:01:13 uue16 kernel: [    3.164000] ACPI Error (psparse-0551): Method parse/execution failed [\_PR_.CPU1._PDC] (Node df83b150), AE_BAD_SIGNATURE
Nov  8 22:01:13 uue16 kernel: [    3.164000] ACPI: Processor [CPU1] (supports 8 throttling states)
Nov  8 22:01:13 uue16 kernel: [    3.260000] ACPI Warning (tbutils-0217): Incorrect checksum in table [  Qµ] -  00, should be 01 [20070126]
Nov  8 22:01:13 uue16 kernel: [    3.260000] ACPI Error (tbinstal-0134): Table has invalid signature [  Qµ], must be SSDT, PSDT or OEMx [20070126]
Nov  8 22:01:13 uue16 kernel: [    3.260000] ACPI Error (psparse-0551): Method parse/execution failed [\_PR_.CPU2._PDC] (Node df83b1e0), AE_BAD_SIGNATURE
Nov  8 22:01:13 uue16 kernel: [    3.700000] usbcore: registered new interface driver usbfs
Nov  8 22:01:13 uue16 kernel: [    3.700000] usbcore: registered new interface driver hub
Nov  8 22:01:13 uue16 kernel: [    3.700000] usbcore: registered new device driver usb
Nov  8 22:01:13 uue16 kernel: [    3.700000] USB Universal Host Controller Interface driver v3.0
Nov  8 22:01:13 uue16 kernel: [    3.700000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
Nov  8 22:01:13 uue16 kernel: [    3.700000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Nov  8 22:01:13 uue16 kernel: [    3.700000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Nov  8 22:01:13 uue16 kernel: [    3.700000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Nov  8 22:01:13 uue16 kernel: [    3.700000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000e480
Nov  8 22:01:13 uue16 kernel: [    3.700000] usb usb1: configuration #1 chosen from 1 choice
Nov  8 22:01:13 uue16 kernel: [    3.700000] hub 1-0:1.0: USB hub found
Nov  8 22:01:13 uue16 kernel: [    3.700000] hub 1-0:1.0: 2 ports detected
Nov  8 22:01:13 uue16 kernel: [    3.748000] SCSI subsystem initialized
Nov  8 22:01:13 uue16 kernel: [    3.776000] libata version 2.21 loaded.
Nov  8 22:01:13 uue16 kernel: [    3.796000] Floppy drive(s): fd0 is 1.44M
Nov  8 22:01:13 uue16 kernel: [    3.804000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
Nov  8 22:01:13 uue16 kernel: [    3.804000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Nov  8 22:01:13 uue16 kernel: [    3.804000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Nov  8 22:01:13 uue16 kernel: [    3.804000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Nov  8 22:01:13 uue16 kernel: [    3.804000] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000e800
Nov  8 22:01:13 uue16 kernel: [    3.804000] usb usb2: configuration #1 chosen from 1 choice
Nov  8 22:01:13 uue16 kernel: [    3.804000] hub 2-0:1.0: USB hub found
Nov  8 22:01:14 uue16 kernel: [    3.804000] hub 2-0:1.0: 2 ports detected
Nov  8 22:01:14 uue16 kernel: [    3.836000] FDC 0 is a post-1991 82077
Nov  8 22:01:14 uue16 kernel: [    3.912000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
Nov  8 22:01:14 uue16 kernel: [    3.912000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Nov  8 22:01:14 uue16 kernel: [    3.912000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Nov  8 22:01:14 uue16 kernel: [    3.912000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Nov  8 22:01:14 uue16 kernel: [    3.912000] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000e880
Nov  8 22:01:14 uue16 kernel: [    3.912000] usb usb3: configuration #1 chosen from 1 choice
Nov  8 22:01:14 uue16 kernel: [    3.912000] hub 3-0:1.0: USB hub found
Nov  8 22:01:14 uue16 kernel: [    3.912000] hub 3-0:1.0: 2 ports detected
Nov  8 22:01:14 uue16 kernel: [    4.020000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17
Nov  8 22:01:14 uue16 kernel: [    4.020000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Nov  8 22:01:14 uue16 kernel: [    4.020000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Nov  8 22:01:14 uue16 kernel: [    4.020000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Nov  8 22:01:14 uue16 kernel: [    4.020000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000ec00
Nov  8 22:01:14 uue16 kernel: [    4.020000] usb usb4: configuration #1 chosen from 1 choice
Nov  8 22:01:14 uue16 kernel: [    4.020000] hub 4-0:1.0: USB hub found
Nov  8 22:01:14 uue16 kernel: [    4.020000] hub 4-0:1.0: 2 ports detected
Nov  8 22:01:14 uue16 kernel: [    4.044000] usb 1-1: new full speed USB device using uhci_hcd and address 2
Nov  8 22:01:14 uue16 kernel: [    4.124000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 21 (level, low) -> IRQ 21
Nov  8 22:01:14 uue16 kernel: [    4.124000] uhci_hcd 0000:01:00.0: UHCI Host Controller
Nov  8 22:01:14 uue16 kernel: [    4.124000] uhci_hcd 0000:01:00.0: new USB bus registered, assigned bus number 5
Nov  8 22:01:14 uue16 kernel: [    4.124000] uhci_hcd 0000:01:00.0: irq 21, io base 0x00009880
Nov  8 22:01:14 uue16 kernel: [    4.124000] usb usb5: configuration #1 chosen from 1 choice
Nov  8 22:01:14 uue16 kernel: [    4.124000] hub 5-0:1.0: USB hub found
Nov  8 22:01:14 uue16 kernel: [    4.124000] hub 5-0:1.0: 2 ports detected
Nov  8 22:01:14 uue16 kernel: [    4.220000] usb 1-1: configuration #1 chosen from 1 choice
Nov  8 22:01:14 uue16 kernel: [    4.228000] ACPI: PCI Interrupt 0000:01:00.1[B] -> GSI 22 (level, low) -> IRQ 22
Nov  8 22:01:14 uue16 kernel: [    4.228000] uhci_hcd 0000:01:00.1: UHCI Host Controller
Nov  8 22:01:14 uue16 kernel: [    4.228000] uhci_hcd 0000:01:00.1: new USB bus registered, assigned bus number 6
Nov  8 22:01:14 uue16 kernel: [    4.228000] uhci_hcd 0000:01:00.1: irq 22, io base 0x00009c00
Nov  8 22:01:14 uue16 kernel: [    4.228000] usb usb6: configuration #1 chosen from 1 choice
Nov  8 22:01:14 uue16 kernel: [    4.228000] hub 6-0:1.0: USB hub found
Nov  8 22:01:14 uue16 kernel: [    4.228000] hub 6-0:1.0: 2 ports detected
Nov  8 22:01:14 uue16 kernel: [    4.332000] ata_piix 0000:00:1f.1: version 2.11
Nov  8 22:01:14 uue16 kernel: [    4.332000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 22
Nov  8 22:01:14 uue16 kernel: [    4.332000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Nov  8 22:01:14 uue16 kernel: [    4.332000] scsi0 : ata_piix
Nov  8 22:01:14 uue16 kernel: [    4.332000] scsi1 : ata_piix
Nov  8 22:01:14 uue16 kernel: [    4.332000] ata1: PATA max UDMA/133 cmd 0x0001d800 ctl 0x0001d482 bmdma 0x0001d000 irq 22
Nov  8 22:01:14 uue16 kernel: [    4.332000] ata2: PATA max UDMA/133 cmd 0x0001d400 ctl 0x0001d082 bmdma 0x0001d008 irq 22
Nov  8 22:01:14 uue16 kernel: [    4.476000] usb 1-2: new full speed USB device using uhci_hcd and address 3
Nov  8 22:01:14 uue16 kernel: [    4.504000] ata1.00: ATA-7: Maxtor 6B300R0, BAH41E00, max UDMA/133
Nov  8 22:01:14 uue16 kernel: [    4.504000] ata1.00: 586114704 sectors, multi 16: LBA48 
Nov  8 22:01:14 uue16 kernel: [    4.504000] ata1.01: ATA-6: ST340015ACE, 3.01, max UDMA/100
Nov  8 22:01:14 uue16 kernel: [    4.504000] ata1.01: 78165360 sectors, multi 16: LBA 
Nov  8 22:01:14 uue16 kernel: [    4.520000] ata1.00: configured for UDMA/133
Nov  8 22:01:14 uue16 kernel: [    4.536000] ata1.01: configured for UDMA/100
Nov  8 22:01:14 uue16 kernel: [    4.652000] usb 1-2: configuration #1 chosen from 1 choice
Nov  8 22:01:14 uue16 kernel: [    4.700000] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6B300R0   BAH4 PQ: 0 ANSI: 5
Nov  8 22:01:14 uue16 kernel: [    4.700000] scsi 0:0:1:0: Direct-Access     ATA      ST340015ACE      3.01 PQ: 0 ANSI: 5
Nov  8 22:01:14 uue16 kernel: [    4.700000] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Nov  8 22:01:14 uue16 kernel: [    4.700000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 23
Nov  8 22:01:14 uue16 kernel: [    4.700000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Nov  8 22:01:14 uue16 kernel: [    4.700000] scsi2 : ata_piix
Nov  8 22:01:14 uue16 kernel: [    4.700000] scsi3 : ata_piix
Nov  8 22:01:14 uue16 kernel: [    4.700000] ata3: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e082 bmdma 0x0001d880 irq 23
Nov  8 22:01:14 uue16 kernel: [    4.700000] ata4: SATA max UDMA/133 cmd 0x0001e000 ctl 0x0001dc02 bmdma 0x0001d888 irq 23
Nov  8 22:01:14 uue16 kernel: [    4.864000] ata3.00: ATA-6: WDC WD740GD-00FLC0, 33.08F33, max UDMA/133
Nov  8 22:01:14 uue16 kernel: [    4.864000] ata3.00: 145226112 sectors, multi 16: LBA48 
Nov  8 22:01:14 uue16 kernel: [    4.880000] ata3.00: configured for UDMA/133
Nov  8 22:01:14 uue16 kernel: [    4.896000] usb 3-1: new full speed USB device using uhci_hcd and address 2
Nov  8 22:01:14 uue16 kernel: [    5.076000] usb 3-1: configuration #1 chosen from 1 choice
Nov  8 22:01:14 uue16 kernel: [    5.228000] ata4.00: ATA-7: WDC WD3200KS-00PFB0, 21.00M21, max UDMA/133
Nov  8 22:01:14 uue16 kernel: [    5.228000] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/1)
Nov  8 22:01:14 uue16 kernel: [    5.228000] ata4.01: ATAPI: PLEXTOR DVDR   PX-755A, 1.06, max UDMA/66
Nov  8 22:01:14 uue16 kernel: [    5.244000] ata4.00: configured for UDMA/133
Nov  8 22:01:14 uue16 kernel: [    5.320000] usb 4-2: new full speed USB device using uhci_hcd and address 2
Nov  8 22:01:14 uue16 kernel: [    5.408000] ata4.01: configured for UDMA/66
Nov  8 22:01:14 uue16 kernel: [    5.408000] scsi 2:0:0:0: Direct-Access     ATA      WDC WD740GD-00FL 33.0 PQ: 0 ANSI: 5
Nov  8 22:01:14 uue16 kernel: [    5.408000] scsi 3:0:0:0: Direct-Access     ATA      WDC WD3200KS-00P 21.0 PQ: 0 ANSI: 5
Nov  8 22:01:14 uue16 kernel: [    5.408000] scsi 3:0:1:0: CD-ROM            PLEXTOR  DVDR   PX-755A   1.06 PQ: 0 ANSI: 5
Nov  8 22:01:14 uue16 kernel: [    5.408000] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 21 (level, low) -> IRQ 21
Nov  8 22:01:14 uue16 kernel: [    5.408000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
Nov  8 22:01:14 uue16 kernel: [    5.408000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Nov  8 22:01:14 uue16 kernel: [    5.408000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Nov  8 22:01:14 uue16 kernel: [    5.408000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Nov  8 22:01:14 uue16 kernel: [    5.408000] ehci_hcd 0000:00:1d.7: debug port 1
Nov  8 22:01:14 uue16 kernel: [    5.408000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
Nov  8 22:01:14 uue16 kernel: [    5.408000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebfbc00
Nov  8 22:01:14 uue16 kernel: [    5.456000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov  8 22:01:14 uue16 kernel: [    5.456000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fe6ff000-fe6ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov  8 22:01:14 uue16 kernel: [    5.456000] usb usb7: configuration #1 chosen from 1 choice
Nov  8 22:01:14 uue16 kernel: [    5.456000] hub 7-0:1.0: USB hub found
Nov  8 22:01:14 uue16 kernel: [    5.456000] hub 7-0:1.0: 8 ports detected
Nov  8 22:01:14 uue16 kernel: [    5.560000] ACPI: PCI Interrupt 0000:01:00.2[C] -> GSI 23 (level, low) -> IRQ 23
Nov  8 22:01:14 uue16 kernel: [    5.560000] ehci_hcd 0000:01:00.2: EHCI Host Controller
Nov  8 22:01:14 uue16 kernel: [    5.560000] ehci_hcd 0000:01:00.2: new USB bus registered, assigned bus number 8
Nov  8 22:01:14 uue16 kernel: [    5.560000] ehci_hcd 0000:01:00.2: irq 23, io mem 0xfe6ffc00
Nov  8 22:01:14 uue16 kernel: [    5.560000] ehci_hcd 0000:01:00.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
Nov  8 22:01:14 uue16 kernel: [    5.560000] usb usb8: configuration #1 chosen from 1 choice
Nov  8 22:01:14 uue16 kernel: [    5.560000] hub 8-0:1.0: USB hub found
Nov  8 22:01:14 uue16 kernel: [    5.560000] hub 8-0:1.0: 4 ports detected
Nov  8 22:01:14 uue16 kernel: [    5.676000] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
Nov  8 22:01:14 uue16 kernel: [    5.676000] sd 0:0:0:0: [sda] Write Protect is off
Nov  8 22:01:14 uue16 kernel: [    5.676000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  8 22:01:14 uue16 kernel: [    5.676000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 22:01:14 uue16 kernel: [    5.676000] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
Nov  8 22:01:14 uue16 kernel: [    5.676000] sd 0:0:0:0: [sda] Write Protect is off
Nov  8 22:01:14 uue16 kernel: [    5.676000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  8 22:01:14 uue16 kernel: [    5.676000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 22:01:14 uue16 kernel: [    5.676000]  sda: sda1 sda2
Nov  8 22:01:14 uue16 kernel: [    5.696000] sd 0:0:0:0: [sda] Attached SCSI disk
Nov  8 22:01:14 uue16 kernel: [    5.696000] sd 0:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
Nov  8 22:01:14 uue16 kernel: [    5.696000] sd 0:0:1:0: [sdb] Write Protect is off
Nov  8 22:01:14 uue16 kernel: [    5.696000] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Nov  8 22:01:14 uue16 kernel: [    5.696000] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 22:01:14 uue16 kernel: [    5.696000] sd 0:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
Nov  8 22:01:14 uue16 kernel: [    5.696000] sd 0:0:1:0: [sdb] Write Protect is off
Nov  8 22:01:14 uue16 kernel: [    5.696000] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Nov  8 22:01:14 uue16 kernel: [    5.696000] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 22:01:14 uue16 kernel: [    5.696000]  sdb: sdb1 sdb2 < sdb5 >
Nov  8 22:01:14 uue16 kernel: [    5.756000] sd 0:0:1:0: [sdb] Attached SCSI disk
Nov  8 22:01:14 uue16 kernel: [    5.756000] sd 2:0:0:0: [sdc] 145226112 512-byte hardware sectors (74356 MB)
Nov  8 22:01:14 uue16 kernel: [    5.756000] sd 2:0:0:0: [sdc] Write Protect is off
Nov  8 22:01:14 uue16 kernel: [    5.756000] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Nov  8 22:01:14 uue16 kernel: [    5.756000] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 22:01:14 uue16 kernel: [    5.756000] sd 2:0:0:0: [sdc] 145226112 512-byte hardware sectors (74356 MB)
Nov  8 22:01:14 uue16 kernel: [    5.756000] sd 2:0:0:0: [sdc] Write Protect is off
Nov  8 22:01:14 uue16 kernel: [    5.756000] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Nov  8 22:01:14 uue16 kernel: [    5.756000] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 22:01:14 uue16 kernel: [    5.756000]  sdc: sdc1
Nov  8 22:01:14 uue16 kernel: [    5.764000] sd 2:0:0:0: [sdc] Attached SCSI disk
Nov  8 22:01:14 uue16 kernel: [    5.764000] sd 3:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
Nov  8 22:01:14 uue16 kernel: [    5.764000] sd 3:0:0:0: [sdd] Write Protect is off
Nov  8 22:01:14 uue16 kernel: [    5.764000] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Nov  8 22:01:14 uue16 kernel: [    5.764000] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 22:01:14 uue16 kernel: [    5.764000] sd 3:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
Nov  8 22:01:14 uue16 kernel: [    5.764000] sd 3:0:0:0: [sdd] Write Protect is off
Nov  8 22:01:14 uue16 kernel: [    5.764000] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Nov  8 22:01:14 uue16 kernel: [    5.764000] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 22:01:14 uue16 kernel: [    5.764000]  sdd: sdd1 sdd2 < sdd5 >
Nov  8 22:01:14 uue16 kernel: [    5.792000] sd 3:0:0:0: [sdd] Attached SCSI disk
Nov  8 22:01:14 uue16 kernel: [    5.796000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov  8 22:01:14 uue16 kernel: [    5.796000] sd 0:0:1:0: Attached scsi generic sg1 type 0
Nov  8 22:01:14 uue16 kernel: [    5.796000] sd 2:0:0:0: Attached scsi generic sg2 type 0
Nov  8 22:01:14 uue16 kernel: [    5.796000] sd 3:0:0:0: Attached scsi generic sg3 type 0
Nov  8 22:01:14 uue16 kernel: [    5.796000] sr 3:0:1:0: Attached scsi generic sg4 type 5
Nov  8 22:01:14 uue16 kernel: [    5.796000] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Nov  8 22:01:14 uue16 kernel: [    5.796000] Uniform CD-ROM driver Revision: 3.20
Nov  8 22:01:14 uue16 kernel: [    5.796000] sr 3:0:1:0: Attached scsi CD-ROM sr0
Nov  8 22:01:14 uue16 kernel: [    5.868000] usb 4-2: device not accepting address 2, error -71
Nov  8 22:01:14 uue16 kernel: [    5.988000] Attempting manual resume
Nov  8 22:01:14 uue16 kernel: [    5.988000] swsusp: Resume From Partition 8:53
Nov  8 22:01:14 uue16 kernel: [    5.988000] PM: Checking swsusp image.
Nov  8 22:01:14 uue16 kernel: [    5.988000] PM: Resume from disk failed.
Nov  8 22:01:14 uue16 kernel: [    6.032000] kjournald starting.  Commit interval 5 seconds
Nov  8 22:01:14 uue16 kernel: [    6.032000] EXT3-fs: mounted filesystem with ordered data mode.
Nov  8 22:01:14 uue16 kernel: [    6.436000] usb 3-1: USB disconnect, address 2
Nov  8 22:01:14 uue16 kernel: [    6.728000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800008e4aa6]
Nov  8 22:01:14 uue16 kernel: [    6.808000] usb 7-1: new high speed USB device using ehci_hcd and address 2
Nov  8 22:01:14 uue16 kernel: [    6.960000] usb 7-1: configuration #1 chosen from 1 choice
Nov  8 22:01:14 uue16 kernel: [    7.444000] usb 7-5: new high speed USB device using ehci_hcd and address 4
Nov  8 22:01:14 uue16 kernel: [    7.592000] usb 7-5: configuration #1 chosen from 1 choice
Nov  8 22:01:14 uue16 kernel: [    7.832000] usb 7-8: new high speed USB device using ehci_hcd and address 5
Nov  8 22:01:14 uue16 kernel: [    7.964000] usb 7-8: configuration #1 chosen from 1 choice
Nov  8 22:01:14 uue16 kernel: [    7.964000] usb 1-1: USB disconnect, address 2
Nov  8 22:01:14 uue16 kernel: [    7.964000] usbcore: registered new interface driver libusual
Nov  8 22:01:14 uue16 kernel: [    8.092000] usb 1-2: USB disconnect, address 3
Nov  8 22:01:14 uue16 kernel: [    8.188000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov  8 22:01:14 uue16 kernel: [    8.188000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov  8 22:01:14 uue16 kernel: [    8.272000] Initializing USB Mass Storage driver...
Nov  8 22:01:14 uue16 kernel: [    8.332000] usb 1-2: new full speed USB device using uhci_hcd and address 4
Nov  8 22:01:14 uue16 kernel: [    8.508000] usb 1-2: configuration #1 chosen from 1 choice
Nov  8 22:01:14 uue16 kernel: [    8.752000] usb 8-3: new high speed USB device using ehci_hcd and address 2
Nov  8 22:01:14 uue16 kernel: [    8.884000] usb 8-3: configuration #1 chosen from 1 choice
Nov  8 22:01:14 uue16 kernel: [    8.884000] scsi4 : SCSI emulation for USB Mass Storage devices
Nov  8 22:01:14 uue16 kernel: [    8.884000] usb-storage: device found at 2
Nov  8 22:01:14 uue16 kernel: [    8.884000] usb-storage: waiting for device to settle before scanning
Nov  8 22:01:14 uue16 kernel: [    8.884000] scsi5 : SCSI emulation for USB Mass Storage devices
Nov  8 22:01:14 uue16 kernel: [    8.884000] usb-storage: device found at 4
Nov  8 22:01:14 uue16 kernel: [    8.884000] usb-storage: waiting for device to settle before scanning
Nov  8 22:01:14 uue16 kernel: [    8.884000] scsi6 : SCSI emulation for USB Mass Storage devices
Nov  8 22:01:14 uue16 kernel: [    8.884000] usb-storage: device found at 5
Nov  8 22:01:14 uue16 kernel: [    8.884000] usb-storage: waiting for device to settle before scanning
Nov  8 22:01:14 uue16 kernel: [    8.884000] scsi7 : SCSI emulation for USB Mass Storage devices
Nov  8 22:01:14 uue16 kernel: [    8.884000] usb-storage: device found at 2
Nov  8 22:01:14 uue16 kernel: [    8.884000] usb-storage: waiting for device to settle before scanning
Nov  8 22:01:14 uue16 kernel: [    8.884000] usbcore: registered new interface driver usb-storage
Nov  8 22:01:14 uue16 kernel: [    8.884000] USB Mass Storage support registered.
Nov  8 22:01:14 uue16 kernel: [   12.512000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov  8 22:01:14 uue16 kernel: [   12.512000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov  8 22:01:14 uue16 kernel: [   12.904000] parport_pc 00:07: reported by Plug and Play ACPI
Nov  8 22:01:14 uue16 kernel: [   12.904000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Nov  8 22:01:14 uue16 kernel: [   12.916000] input: PC Speaker as /class/input/input2
Nov  8 22:01:14 uue16 kernel: [   13.032000] intel_rng: FWH not detected
Nov  8 22:01:14 uue16 kernel: [   13.156000] iTCO_vendor_support: vendor-support=0
Nov  8 22:01:14 uue16 kernel: [   13.156000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Nov  8 22:01:14 uue16 kernel: [   13.228000] Linux agpgart interface v0.102 (c) Dave Jones
Nov  8 22:01:14 uue16 kernel: [   13.364000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov  8 22:01:14 uue16 kernel: [   13.392000] [fglrx] Maximum main memory to use for locked dma buffers: 2888 MBytes.
Nov  8 22:01:14 uue16 kernel: [   13.392000] [fglrx] ASYNCIO init succeed!
Nov  8 22:01:14 uue16 kernel: [   13.396000] [fglrx] PAT is enabled successfully!
Nov  8 22:01:14 uue16 kernel: [   13.396000] [fglrx] module loaded - fglrx 8.42.3 [Oct 19 2007] on minor 0
Nov  8 22:01:14 uue16 kernel: [   13.400000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 17
Nov  8 22:01:14 uue16 kernel: [   13.400000] PCI: Setting latency timer of device 0000:03:00.0 to 64
Nov  8 22:01:14 uue16 kernel: [   13.400000] sky2 0000:03:00.0: v1.18 addr 0xfe9fc000 irq 17 Yukon-EC (0xb6) rev 2
Nov  8 22:01:14 uue16 kernel: [   13.404000] sky2 eth0: addr 00:15:f2:a0:f8:e6
Nov  8 22:01:14 uue16 kernel: [   13.412000] sky2 eth0: enabling interface
Nov  8 22:01:14 uue16 kernel: [   13.424000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0xC202
Nov  8 22:01:14 uue16 kernel: [   13.424000] usbcore: registered new interface driver usblp
Nov  8 22:01:14 uue16 kernel: [   13.424000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Nov  8 22:01:14 uue16 kernel: [   13.648000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 17
Nov  8 22:01:14 uue16 kernel: [   13.648000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Nov  8 22:01:14 uue16 kernel: [   13.720000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
Nov  8 22:01:14 uue16 kernel: [   13.724000] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
Nov  8 22:01:14 uue16 kernel: [   13.724000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Nov  8 22:01:14 uue16 kernel: [   13.884000] usb-storage: device scan complete
Nov  8 22:01:14 uue16 last message repeated 2 times
Nov  8 22:01:14 uue16 kernel: [   13.884000] scsi 7:0:0:0: Direct-Access     HP       Photosmart 8200  1.00 PQ: 0 ANSI: 2
Nov  8 22:01:14 uue16 kernel: [   13.884000] usb-storage: device scan complete
Nov  8 22:01:14 uue16 kernel: [   13.884000] scsi 5:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
Nov  8 22:01:14 uue16 kernel: [   13.884000] sd 7:0:0:0: [sde] Attached SCSI removable disk
Nov  8 22:01:14 uue16 kernel: [   13.884000] sd 7:0:0:0: Attached scsi generic sg5 type 0
Nov  8 22:01:14 uue16 kernel: [   13.884000] scsi 4:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100D PQ: 0 ANSI: 4
Nov  8 22:01:14 uue16 kernel: [   13.884000] scsi 5:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
Nov  8 22:01:14 uue16 kernel: [   13.888000] scsi 5:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
Nov  8 22:01:14 uue16 kernel: [   13.888000] scsi 5:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
Nov  8 22:01:14 uue16 kernel: [   13.916000] scsi 6:0:0:0: Direct-Access     IC25N030 ATCS04-0         CA3O PQ: 0 ANSI: 0
Nov  8 22:01:14 uue16 kernel: [   13.920000] sd 6:0:0:0: [sdf] 58605119 512-byte hardware sectors (30006 MB)
Nov  8 22:01:14 uue16 kernel: [   13.920000] sd 6:0:0:0: [sdf] Write Protect is off
Nov  8 22:01:14 uue16 kernel: [   13.920000] sd 6:0:0:0: [sdf] Mode Sense: 03 00 00 00
Nov  8 22:01:14 uue16 kernel: [   13.920000] sd 6:0:0:0: [sdf] Assuming drive cache: write through
Nov  8 22:01:14 uue16 kernel: [   13.920000] sd 6:0:0:0: [sdf] 58605119 512-byte hardware sectors (30006 MB)
Nov  8 22:01:14 uue16 kernel: [   13.920000] sd 6:0:0:0: [sdf] Write Protect is off
Nov  8 22:01:14 uue16 kernel: [   13.920000] sd 6:0:0:0: [sdf] Mode Sense: 03 00 00 00
Nov  8 22:01:14 uue16 kernel: [   13.920000] sd 6:0:0:0: [sdf] Assuming drive cache: write through
Nov  8 22:01:14 uue16 kernel: [   13.920000]  sdf: sdf1
Nov  8 22:01:14 uue16 kernel: [   14.192000] sd 6:0:0:0: [sdf] Attached SCSI disk
Nov  8 22:01:14 uue16 kernel: [   14.192000] sd 6:0:0:0: Attached scsi generic sg6 type 0
Nov  8 22:01:14 uue16 kernel: [   14.192000] sd 5:0:0:0: [sdg] Attached SCSI removable disk
Nov  8 22:01:14 uue16 kernel: [   14.192000] sd 5:0:0:0: Attached scsi generic sg7 type 0
Nov  8 22:01:14 uue16 kernel: [   14.196000] sd 5:0:0:1: [sdh] Attached SCSI removable disk
Nov  8 22:01:14 uue16 kernel: [   14.196000] sd 5:0:0:1: Attached scsi generic sg8 type 0
Nov  8 22:01:14 uue16 kernel: [   14.196000] sd 5:0:0:2: [sdi] Attached SCSI removable disk
Nov  8 22:01:14 uue16 kernel: [   14.196000] sd 5:0:0:2: Attached scsi generic sg9 type 0
Nov  8 22:01:14 uue16 kernel: [   14.196000] sd 5:0:0:3: [sdj] Attached SCSI removable disk
Nov  8 22:01:14 uue16 kernel: [   14.196000] sd 5:0:0:3: Attached scsi generic sg10 type 0
Nov  8 22:01:14 uue16 kernel: [   14.200000] sd 4:0:0:0: [sdk] 625142448 512-byte hardware sectors (320073 MB)
Nov  8 22:01:14 uue16 kernel: [   14.200000] sd 4:0:0:0: [sdk] Write Protect is off
Nov  8 22:01:14 uue16 kernel: [   14.200000] sd 4:0:0:0: [sdk] Mode Sense: 1c 00 00 00
Nov  8 22:01:14 uue16 kernel: [   14.200000] sd 4:0:0:0: [sdk] Assuming drive cache: write through
Nov  8 22:01:14 uue16 kernel: [   14.204000] sd 4:0:0:0: [sdk] 625142448 512-byte hardware sectors (320073 MB)
Nov  8 22:01:14 uue16 kernel: [   14.204000] sd 4:0:0:0: [sdk] Write Protect is off
Nov  8 22:01:14 uue16 kernel: [   14.204000] sd 4:0:0:0: [sdk] Mode Sense: 1c 00 00 00
Nov  8 22:01:14 uue16 kernel: [   14.204000] sd 4:0:0:0: [sdk] Assuming drive cache: write through
Nov  8 22:01:14 uue16 kernel: [   14.204000]  sdk: sdk1
Nov  8 22:01:14 uue16 kernel: [   14.212000] sd 4:0:0:0: [sdk] Attached SCSI disk
Nov  8 22:01:14 uue16 kernel: [   14.212000] sd 4:0:0:0: Attached scsi generic sg11 type 0
Nov  8 22:01:14 uue16 kernel: [   14.760000] NET: Registered protocol family 17
Nov  8 22:01:14 uue16 kernel: [   15.132000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Nov  8 22:01:14 uue16 kernel: [   15.360000] lp0: using parport0 (interrupt-driven).
Nov  8 22:01:14 uue16 kernel: [   15.404000] Adding 9100780k swap on /dev/sdd5.  Priority:-1 extents:1 across:9100780k
Nov  8 22:01:14 uue16 kernel: [   15.752000] EXT3 FS on sdd1, internal journal
Nov  8 22:01:14 uue16 kernel: [   16.752000] NET: Registered protocol family 10
Nov  8 22:01:14 uue16 kernel: [   16.752000] lo: Disabled Privacy Extensions
Nov  8 22:01:14 uue16 kernel: [   18.384000] No dock devices found.
Nov  8 22:01:14 uue16 kernel: [   18.440000] input: Power Button (FF) as /class/input/input4
Nov  8 22:01:14 uue16 kernel: [   18.440000] ACPI: Power Button (FF) [PWRF]
Nov  8 22:01:14 uue16 kernel: [   18.440000] input: Power Button (CM) as /class/input/input5
Nov  8 22:01:14 uue16 kernel: [   18.440000] ACPI: Power Button (CM) [PWRB]
Nov  8 22:01:14 uue16 ntpdate[5937]: adjust time server 91.189.94.4 offset 0.063688 sec
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.321694] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_277c'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.673952] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_277d'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.676233] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_7109'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.677023] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_7129'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.678158] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.678936] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.679372] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.679953] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_11ab_4362'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.680666] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27e2'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.681040] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_11ab_6141'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.681434] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.681853] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.682266] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.714711] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_220d_noserial'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.715152] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_220d_noserial_if0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.716022] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.716614] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.718171] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.718677] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.720511] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.721058] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.721957] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.722513] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.723086] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.723741] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.724259] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.725551] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.726161] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.726930] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_if0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.727495] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_if0_scsi_host'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.898599] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_if0_scsi_host_scsi_device_lun0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.899017] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.899398] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.899786] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.900152] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.900562] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun1'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.900945] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun2'). 
Nov  8 22:01:14 uue16 kernel: [   20.180000] ppdev: user-space parallel port driver
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.902465] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun3'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.902886] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.903267] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_if0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.903706] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_if0_scsi_host'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.904266] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_if0_scsi_host_scsi_device_lun0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.904770] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_244e'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.905134] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3038'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.905495] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.905856] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_0_if0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.906214] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3038_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.906573] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_1'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.906932] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_1_if0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.907292] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3104'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.907648] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_2'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.908005] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_2_if0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.908362] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.908746] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.909106] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if1'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.909462] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if2'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.909819] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if2_scsi_host'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.910176] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if2_scsi_host_scsi_device_lun0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.910532] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1102_5'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.910888] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_104c_8023'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.911243] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b8'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.911599] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.911954] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.912311] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.912693] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.913050] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.913405] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.913760] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_scsi_device_lun0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.914115] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.914471] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.914826] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.915181] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.915536] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.915890] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_floppy_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.916243] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.916624] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.916980] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.917335] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.917706] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.918064] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.918418] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a08'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.918774] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.919127] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.919479] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.919831] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.920184] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.920565] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0700'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.920924] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0401'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.921278] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.921630] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.921982] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_1'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.922333] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.922686] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f03'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.923038] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_2'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.923389] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNPb02f'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.923739] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNPb006'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.924091] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.924442] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_3'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.924824] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.925176] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.925528] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.925878] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.926230] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_f2_a0_f8_e6'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.934614] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.936738] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27df_scsi_host_scsi_device_lun0_0_scsi_generic'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.937197] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun3_scsi_generic'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.937558] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.937914] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.938312] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.938677] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0_0_scsi_generic'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.939027] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if2_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.939378] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.939727] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.940078] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.940426] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_if0_scsi_host_scsi_device_lun2_scsi_generic'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.940814] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_1'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.941164] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.941598] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.941948] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.942296] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.942645] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.942993] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.943341] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_1'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.943688] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_1'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.944034] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_2'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.944381] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.944782] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.945189] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.945601] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.945984] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.946368] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.946772] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.947130] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.947481] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.947865] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.948237] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_220d_noserial_usbraw'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.948613] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.948960] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.949306] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.949652] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_0_usbraw'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.949998] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_1_usbraw'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.950342] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.950685] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3CG9K_usbraw'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.951029] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_8989_0300836166_usbraw'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.951374] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2507_0_usbraw'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.951719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_01_00_2_usbraw'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.952063] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_usbraw'). 
Nov  8 22:01:14 uue16 NetworkManager: <debug> [1194580874.966631] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_floppy_0_storage'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580874.999973] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_Maxtor_6B300R0_B620LRQH'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.009376] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_01C660C5D0074900'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.044184] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_36D04443D0440C15'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.082922] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST340015ACE_5LAEEQQH'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.123488] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_6c99eb8b_ecab_4126_bb00_453192aecfb6'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.129481] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.158996] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_e73ed621_c1d6_43e1_adc4_505d9a6360f9'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.163645] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD740GD_00FLC0_WD_WMAKE2361213'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.172821] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_4AA44F23A44F10BD'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.327642] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD3200KS_00PFB0_WD_WCAPD1030686'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.333001] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_e8bee423_266f_49eb_8f99_a75d19ffa386'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.485874] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024_0'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.490895] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_2d0e7fbd_476c_40ef_8e51_f20e13690ce1'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.556113] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_HP_Photosmart_8200_MY5AR3X0H504KK_0_0'). 
Nov  8 22:01:15 uue16 kernel: [   20.912000] audit(1194580875.590:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=7116 profile="/usr/sbin/cupsd"
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.835437] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_IC25N030_ATCS04_0_0_0_0'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.853875] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8CD0_6617'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.866558] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_STORAGE_DEVICE_0300836166_0_0'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.877031] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_STORAGE_DEVICE_0300836166_0_1'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.886175] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_STORAGE_DEVICE_0300836166_0_2'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.897068] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_STORAGE_DEVICE_0300836166_0_3'). 
Nov  8 22:01:15 uue16 NetworkManager: <debug> [1194580875.902882] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Seagate_FreeAgentDesktop_9QF3CG9K_0_0'). 
Nov  8 22:01:16 uue16 NetworkManager: <debug> [1194580876.012467] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_04F07BDEF07BD480'). 
Nov  8 22:01:16 uue16 NetworkManager: <debug> [1194580876.052428] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU4'). 
Nov  8 22:01:16 uue16 NetworkManager: <debug> [1194580876.059401] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU3'). 
Nov  8 22:01:16 uue16 NetworkManager: <debug> [1194580876.059839] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU2'). 
Nov  8 22:01:16 uue16 NetworkManager: <debug> [1194580876.060371] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Nov  8 22:01:16 uue16 NetworkManager: <debug> [1194580876.060864] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVDR___PX_755A'). 
Nov  8 22:01:16 uue16 hal_lpadmin: add
Nov  8 22:01:16 uue16 mysqld_safe[7291]: started
Nov  8 22:01:17 uue16 mysqld[7294]: 071108 22:01:17  InnoDB: Started; log sequence number 0 43655
Nov  8 22:01:17 uue16 mysqld[7294]: 071108 22:01:17 [Note] /usr/sbin/mysqld: ready for connections.
Nov  8 22:01:17 uue16 mysqld[7294]: Version: '5.0.45-Debian_1ubuntu3-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian etch distribution
Nov  8 22:01:17 uue16 /etc/mysql/debian-start[7377]: Upgrading MySQL tables if necessary.
Nov  8 22:01:17 uue16 kernel: [   23.080000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Nov  8 22:01:17 uue16 kernel: [   23.080000] apm: disabled - APM is not SMP safe.
Nov  8 22:01:17 uue16 /etc/mysql/debian-start[7382]: Looking for 'mysql' in: /usr/bin/mysql
Nov  8 22:01:17 uue16 /etc/mysql/debian-start[7382]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck
Nov  8 22:01:17 uue16 /etc/mysql/debian-start[7382]: This installation of MySQL is already upgraded to 5.0.45, use --force if you still need to run mysql_upgrade
Nov  8 22:01:17 uue16 /etc/mysql/debian-start[7439]: Checking for insecure root accounts.
Nov  8 22:01:18 uue16 /etc/mysql/debian-start[7445]: WARNING: mysql.user contains 3 root accounts without password!
Nov  8 22:01:18 uue16 /etc/mysql/debian-start[7446]: Checking for crashed MySQL tables.
Nov  8 22:01:18 uue16 atieventsd[7464]: ATI External Events Daemon started... 
Nov  8 22:01:18 uue16 atieventsd[7464]: Event daemon control socket created 
Nov  8 22:01:18 uue16 atieventsd[7464]: acpid connection established 
Nov  8 22:01:19 uue16 kernel: [   24.860000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Nov  8 22:01:19 uue16 hal_lpadmin: URIs: ['hp:/usb/Photosmart_8200_series?serial=MY5AR3X0H504KK', 'usb://HP/Photosmart%208200%20series?serial=MY5AR3X0H504KK', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if0_printer_MY5AR3X0H504KK']
Nov  8 22:01:19 uue16 kernel: [   25.104000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Nov  8 22:01:19 uue16 kernel: [   25.120000] NFSD: starting 90-second grace period
Nov  8 22:01:20 uue16 python: hp-probe[7902]: warning: No devices found on the 'usb' bus. If this isn't the result you are expecting,
Nov  8 22:01:21 uue16 python: hp-probe[7902]: warning: check to make sure your devices are properly connected and powered on.
Nov  8 22:01:21 uue16 hal_lpadmin: HPLIP Fax URIs: None
Nov  8 22:01:21 uue16 hal_lpadmin: Not adding printer: Photosmart_8200_series already exists
Nov  8 22:01:21 uue16 snort[7896]: Var 'eth0_ADDRESS' defined, value len = 26 chars
Nov  8 22:01:21 uue16 snort[7896]: , value = 192.168.20.0/255.255.255.0 
Nov  8 22:01:21 uue16 snort[7896]: Var 'any_ADDRESS' defined, value len = 15 chars
Nov  8 22:01:21 uue16 snort[7896]: , value = 0.0.0.0/0.0.0.0 
Nov  8 22:01:21 uue16 snort[7896]: Var 'lo_ADDRESS' defined, value len = 19 chars
Nov  8 22:01:21 uue16 snort[7896]: , value = 127.0.0.0/255.0.0.0 
Nov  8 22:01:21 uue16 snort[7896]: Parsing Rules file /etc/snort/snort.conf 
Nov  8 22:01:21 uue16 snort[7896]: Var 'HOME_NET' redefined 
Nov  8 22:01:21 uue16 snort[7896]: Var 'EXTERNAL_NET' defined, value len = 3 chars
Nov  8 22:01:21 uue16 snort[7896]: , value = any 
Nov  8 22:01:21 uue16 snort[7896]: Var 'DNS_SERVERS' defined, value len = 16 chars
Nov  8 22:01:21 uue16 snort[7896]: , value = [192.168.0.0/16] 
Nov  8 22:01:21 uue16 snort[7896]: Var 'SMTP_SERVERS' defined, value len = 16 chars
Nov  8 22:01:21 uue16 snort[7896]: , value = [192.168.0.0/16] 
Nov  8 22:01:21 uue16 snort[7896]: Var 'HTTP_SERVERS' defined, value len = 16 chars
Nov  8 22:01:21 uue16 snort[7896]: , value = [192.168.0.0/16] 
Nov  8 22:01:21 uue16 snort[7896]: Var 'SQL_SERVERS' defined, value len = 16 chars
Nov  8 22:01:21 uue16 snort[7896]: , value = [192.168.0.0/16] 
Nov  8 22:01:21 uue16 snort[7896]: Var 'TELNET_SERVERS' defined, value len = 16 chars
Nov  8 22:01:21 uue16 snort[7896]: , value = [192.168.0.0/16] 
Nov  8 22:01:21 uue16 snort[7896]: Var 'SNMP_SERVERS' defined, value len = 16 chars
Nov  8 22:01:21 uue16 snort[7896]: , value = [192.168.0.0/16] 
Nov  8 22:01:21 uue16 snort[7896]: Var 'HTTP_PORTS' defined, value len = 2 chars
Nov  8 22:01:21 uue16 snort[7896]: , value = 80 
Nov  8 22:01:21 uue16 snort[7896]: Var 'SHELLCODE_PORTS' defined, value len = 3 chars
Nov  8 22:01:21 uue16 snort[7896]: , value = !80 
Nov  8 22:01:21 uue16 snort[7896]: Var 'ORACLE_PORTS' defined, value len = 4 chars
Nov  8 22:01:21 uue16 snort[7896]: , value = 1521 
Nov  8 22:01:21 uue16 snort[7896]: Var 'AIM_SERVERS' defined, value len = 185 chars
Nov  8 22:01:21 uue16 snort[7896]:  
Nov  8 22:01:21 uue16 snort[7896]:    [64.12.24.0/23,64.12.28.0/23,64.12.161.0/24,64.12.163.0/24,64.12.200.0/24,205.188.3.0/24,205.188.5.0/24,205.188.7.0/24,205.188.9 
Nov  8 22:01:21 uue16 snort[7896]:    .0/24,205.188.153.0/24,205.188.179.0/24,205.188.248.0/24] 
Nov  8 22:01:21 uue16 snort[7896]: Var 'RULE_PATH' defined, value len = 16 chars
Nov  8 22:01:21 uue16 snort[7896]: , value = /etc/snort/rules 
Nov  8 22:01:21 uue16 snort[7896]: ,-----------[Flow Config]---------------------- 
Nov  8 22:01:21 uue16 snort[7896]: | Stats Interval:  0 
Nov  8 22:01:21 uue16 snort[7896]: | Hash Method:     2 
Nov  8 22:01:21 uue16 snort[7896]: | Memcap:          10485760 
Nov  8 22:01:21 uue16 snort[7896]: | Rows  :          4099 
Nov  8 22:01:21 uue16 snort[7896]: | Overhead Bytes:  16400(%0.16) 
Nov  8 22:01:21 uue16 snort[7896]: `---------------------------------------------- 
Nov  8 22:01:21 uue16 snort[7896]: Frag3 global config: 
Nov  8 22:01:21 uue16 snort[7896]:     Max frags: 65536 
Nov  8 22:01:21 uue16 snort[7896]:     Fragment memory cap: 4194304 bytes 
Nov  8 22:01:21 uue16 snort[7896]: Frag3 engine config: 
Nov  8 22:01:21 uue16 snort[7896]:     Target-based policy: FIRST 
Nov  8 22:01:21 uue16 snort[7896]:     Fragment timeout: 60 seconds 
Nov  8 22:01:21 uue16 snort[7896]:     Fragment min_ttl:   1 
Nov  8 22:01:21 uue16 snort[7896]:     Fragment ttl_limit: 5 
Nov  8 22:01:21 uue16 snort[7896]:     Fragment Problems: 1 
Nov  8 22:01:21 uue16 snort[7896]:     Bound Addresses: 0.0.0.0/0.0.0.0 
Nov  8 22:01:21 uue16 snort[7896]: Stream5 global config: 
Nov  8 22:01:21 uue16 snort[7896]:     Track TCP sessions: ACTIVE 
Nov  8 22:01:21 uue16 snort[7896]:     Max TCP sessions: 8192 
Nov  8 22:01:21 uue16 snort[7896]:     Memcap (for reassembly packet storage): 8388608 
Nov  8 22:01:21 uue16 snort[7896]:     Track UDP sessions: INACTIVE 
Nov  8 22:01:21 uue16 snort[7896]:     Track ICMP sessions: INACTIVE 
Nov  8 22:01:21 uue16 snort[7896]: Stream5 TCP Policy config: 
Nov  8 22:01:21 uue16 snort[7896]:     Reassembly Policy: FIRST 
Nov  8 22:01:21 uue16 snort[7896]:     Timeout: 30 seconds 
Nov  8 22:01:21 uue16 snort[7896]:     Min ttl:  1 
Nov  8 22:01:21 uue16 snort[7896]:     Options: 
Nov  8 22:01:21 uue16 snort[7896]:         Static Flushpoint Sizes: YES 
Nov  8 22:01:21 uue16 snort[7896]:     Reassembly Ports: 
Nov  8 22:01:21 uue16 snort[7896]:       21 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:       23 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:       25 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:       42 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:       53 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:       80 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:       110 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:       111 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:       135 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:       136 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:       137 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:       139 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:       143 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:       445 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:       513 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:       1433 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:       1521 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:       3306 client (Footprint)  
Nov  8 22:01:21 uue16 snort[7896]:     Bound Addresses:0.0.0.0/0.0.0.0 
Nov  8 22:01:21 uue16 snort[7896]: HttpInspect Config: 
Nov  8 22:01:21 uue16 snort[7896]:     GLOBAL CONFIG 
Nov  8 22:01:21 uue16 snort[7896]:       Max Pipeline Requests:    0 
Nov  8 22:01:21 uue16 snort[7896]:       Inspection Type:          STATELESS 
Nov  8 22:01:21 uue16 snort[7896]:       Detect Proxy Usage:       NO 
Nov  8 22:01:21 uue16 snort[7896]:       IIS Unicode Map Filename: /etc/snort/unicode.map 
Nov  8 22:01:21 uue16 snort[7896]:       IIS Unicode Map Codepage: 1252 
Nov  8 22:01:21 uue16 snort[7896]:     DEFAULT SERVER CONFIG: 
Nov  8 22:01:21 uue16 snort[7896]:       Server profile: All 
Nov  8 22:01:21 uue16 snort[7896]:       Ports: 80 8080 8180  
Nov  8 22:01:21 uue16 snort[7896]:       Flow Depth: 300 
Nov  8 22:01:21 uue16 snort[7896]:       Max Chunk Length: 500000 
Nov  8 22:01:21 uue16 snort[7896]:       Inspect Pipeline Requests: YES 
Nov  8 22:01:21 uue16 snort[7896]:       URI Discovery Strict Mode: NO 
Nov  8 22:01:21 uue16 snort[7896]:       Allow Proxy Usage: NO 
Nov  8 22:01:21 uue16 snort[7896]:       Disable Alerting: NO 
Nov  8 22:01:21 uue16 snort[7896]:       Oversize Dir Length: 500 
Nov  8 22:01:21 uue16 snort[7896]:       Only inspect URI: NO 
Nov  8 22:01:21 uue16 snort[7896]:       Ascii: YES alert: NO 
Nov  8 22:01:21 uue16 snort[7896]:       Double Decoding: YES alert: YES 
Nov  8 22:01:21 uue16 snort[7896]:       %U Encoding: YES alert: YES 
Nov  8 22:01:21 uue16 snort[7896]:       Bare Byte: YES alert: YES 
Nov  8 22:01:21 uue16 snort[7896]:       Base36: OFF 
Nov  8 22:01:21 uue16 snort[7896]:       UTF 8: OFF 
Nov  8 22:01:21 uue16 snort[7896]:       IIS Unicode: YES alert: YES 
Nov  8 22:01:21 uue16 snort[7896]:       Multiple Slash: YES alert: NO 
Nov  8 22:01:21 uue16 snort[7896]:       IIS Backslash: YES alert: NO 
Nov  8 22:01:21 uue16 snort[7896]:       Directory Traversal: YES alert: NO 
Nov  8 22:01:21 uue16 snort[7896]:       Web Root Traversal: YES alert: YES 
Nov  8 22:01:21 uue16 snort[7896]:       Apache WhiteSpace: YES alert: NO 
Nov  8 22:01:21 uue16 snort[7896]:       IIS Delimiter: YES alert: NO 
Nov  8 22:01:21 uue16 snort[7896]:       IIS Unicode Map: GLOBAL IIS UNICODE MAP CONFIG 
Nov  8 22:01:21 uue16 snort[7896]:       Non-RFC Compliant Characters: NONE 
Nov  8 22:01:21 uue16 snort[7896]:       Whitespace Characters: 0x09 0x0b 0x0c 0x0d  
Nov  8 22:01:21 uue16 snort[7896]: rpc_decode arguments: 
Nov  8 22:01:21 uue16 snort[7896]:     Ports to decode RPC on: 111 32771  
Nov  8 22:01:21 uue16 snort[7896]:     alert_fragments: INACTIVE 
Nov  8 22:01:21 uue16 snort[7896]:     alert_large_fragments: ACTIVE 
Nov  8 22:01:21 uue16 snort[7896]:     alert_incomplete: ACTIVE 
Nov  8 22:01:21 uue16 snort[7896]:     alert_multiple_requests: ACTIVE 
Nov  8 22:01:21 uue16 snort[7896]: Portscan Detection Config: 
Nov  8 22:01:21 uue16 snort[7896]:     Detect Protocols:  TCP UDP ICMP IP 
Nov  8 22:01:21 uue16 snort[7896]:     Detect Scan Type:  portscan portsweep decoy_portscan distributed_portscan 
Nov  8 22:01:21 uue16 snort[7896]:     Sensitivity Level: Low 
Nov  8 22:01:21 uue16 snort[7896]:     Memcap (in bytes): 10000000 
Nov  8 22:01:21 uue16 snort[7896]:     Number of Nodes:   36900 
Nov  8 22:01:21 uue16 snort[7896]:  
Nov  8 22:01:21 uue16 snort[7896]: Tagged Packet Limit: 256 
Nov  8 22:01:21 uue16 snort[7896]:  
Nov  8 22:01:21 uue16 snort[7896]: +-----------------------[thresholding-config]---------------------------------- 
Nov  8 22:01:21 uue16 snort[7896]: | memory-cap : 1048576 bytes 
Nov  8 22:01:21 uue16 snort[7896]: +-----------------------[thresholding-global]---------------------------------- 
Nov  8 22:01:21 uue16 snort[7896]: | none 
Nov  8 22:01:21 uue16 snort[7896]: +-----------------------[thresholding-local]----------------------------------- 
Nov  8 22:01:21 uue16 snort[7896]: | none 
Nov  8 22:01:21 uue16 snort[7896]: +-----------------------[suppression]------------------------------------------ 
Nov  8 22:01:21 uue16 snort[7896]: | none 
Nov  8 22:01:21 uue16 snort[7896]: ------------------------------------------------------------------------------- 
Nov  8 22:01:21 uue16 snort[7896]: Rule application order: activation->dynamic->pass->drop->alert->log 
Nov  8 22:01:21 uue16 snort[7896]: Log directory = /var/log/snort 
Nov  8 22:01:21 uue16 snort[7896]: Loading dynamic engine /usr/lib/snort_dynamicengine/libsf_engine.so... 
Nov  8 22:01:21 uue16 snort[7896]: done 
Nov  8 22:01:21 uue16 snort[7896]: Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/... 
Nov  8 22:01:21 uue16 snort[7896]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ssh_preproc.so... 
Nov  8 22:01:21 uue16 snort[7896]: done 
Nov  8 22:01:21 uue16 snort[7896]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dns_preproc.so... 
Nov  8 22:01:21 uue16 snort[7896]: done 
Nov  8 22:01:21 uue16 snort[7896]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ftptelnet_preproc.so... 
Nov  8 22:01:21 uue16 snort[7896]: done 
Nov  8 22:01:21 uue16 snort[7896]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dcerpc_preproc.so... 
Nov  8 22:01:21 uue16 snort[7896]: done 
Nov  8 22:01:21 uue16 snort[7896]:   Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_smtp_preproc.so... 
Nov  8 22:01:21 uue16 snort[7896]: done 
Nov  8 22:01:21 uue16 snort[7896]:   Finished Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/ 
Nov  8 22:01:21 uue16 snort[7896]: FTPTelnet Config: 
Nov  8 22:01:21 uue16 snort[7896]:     GLOBAL CONFIG 
Nov  8 22:01:21 uue16 snort[7896]:       Inspection Type: stateful 
Nov  8 22:01:21 uue16 snort[7896]:       Check for Encrypted Traffic: YES alert: YES 
Nov  8 22:01:21 uue16 snort[7896]:       Continue to check encrypted data: NO 
Nov  8 22:01:21 uue16 snort[7896]:     TELNET CONFIG: 
Nov  8 22:01:21 uue16 snort[7896]:       Ports: 23  
Nov  8 22:01:21 uue16 snort[7896]:       Are You There Threshold: 200 
Nov  8 22:01:21 uue16 snort[7896]:       Normalize: YES 
Nov  8 22:01:21 uue16 snort[7896]:       Detect Anomalies: NO 
Nov  8 22:01:21 uue16 snort[7896]:     FTP CONFIG: 
Nov  8 22:01:21 uue16 snort[7896]:       FTP Server: default 
Nov  8 22:01:21 uue16 snort[7896]:         Ports: 21  
Nov  8 22:01:21 uue16 snort[7896]:         Check for Telnet Cmds: YES alert: YES 
Nov  8 22:01:21 uue16 snort[7896]:         Identify open data channels: YES 
Nov  8 22:01:21 uue16 snort[7896]:       FTP Client: default 
Nov  8 22:01:21 uue16 snort[7896]:         Check for Bounce Attacks: YES alert: YES 
Nov  8 22:01:21 uue16 snort[7896]:         Check for Telnet Cmds: YES alert: YES 
Nov  8 22:01:21 uue16 snort[7896]:         Max Response Length: 256 
Nov  8 22:01:21 uue16 snort[7896]: SMTP Config: 
Nov  8 22:01:21 uue16 snort[7896]:       Ports: 
Nov  8 22:01:21 uue16 snort[7896]: 25 
Nov  8 22:01:21 uue16 snort[7896]:  
Nov  8 22:01:21 uue16 snort[7896]:       Inspection Type:            STATEFUL 
Nov  8 22:01:21 uue16 snort[7896]:       Normalize Spaces:           YES 
Nov  8 22:01:21 uue16 snort[7896]:       Ignore Data:                NO 
Nov  8 22:01:21 uue16 snort[7896]:       Ignore TLS Data:            NO 
Nov  8 22:01:21 uue16 snort[7896]:       Ignore Alerts:              NO 
Nov  8 22:01:21 uue16 snort[7896]:       Max Command Length:         0 
Nov  8 22:01:21 uue16 snort[7896]:       Max Header Line Length:     0 
Nov  8 22:01:21 uue16 snort[7896]:       Max Response Line Length:   0 
Nov  8 22:01:21 uue16 snort[7896]:       X-Link2State Alert:         YES 
Nov  8 22:01:21 uue16 snort[7896]:       Drop on X-Link2State Alert: NO 
Nov  8 22:01:21 uue16 snort[7896]:  DCE/RPC Decoder config: 
Nov  8 22:01:21 uue16 snort[7896]:     Autodetect ports ENABLED 
Nov  8 22:01:21 uue16 snort[7896]:     SMB fragmentation ENABLED 
Nov  8 22:01:21 uue16 snort[7896]:     DCE/RPC fragmentation ENABLED 
Nov  8 22:01:21 uue16 snort[7896]:     Max Frag Size: 3000 bytes 
Nov  8 22:01:21 uue16 snort[7896]:     Memcap: 100000 KB 
Nov  8 22:01:21 uue16 snort[7896]:     Alert if memcap exceeded DISABLED 
Nov  8 22:01:21 uue16 snort[7896]:  
Nov  8 22:01:21 uue16 snort[7896]: DNS config:  
Nov  8 22:01:21 uue16 snort[7896]:     DNS Client rdata txt Overflow Alert: ACTIVE 
Nov  8 22:01:21 uue16 snort[7896]:     Obsolete DNS RR Types Alert: INACTIVE 
Nov  8 22:01:21 uue16 snort[7896]:     Experimental DNS RR Types Alert: INACTIVE 
Nov  8 22:01:21 uue16 snort[7896]:     Ports:
Nov  8 22:01:21 uue16 snort[7896]:  53
Nov  8 22:01:21 uue16 snort[7896]:  
Nov  8 22:01:21 uue16 snort[7896]: Warning: flowbits key 'ms_sql_seen_dns' is checked but not ever set. 
Nov  8 22:01:21 uue16 snort[7896]: Warning: flowbits key 'realplayer.playlist' is checked but not ever set. 
Nov  8 22:01:21 uue16 snort[7896]: Warning: flowbits key 'smb.tree.create.llsrpc' is set but not ever checked. 
Nov  8 22:01:21 uue16 snort[7896]: Warning: flowbits key 'community_uri.size.1050' is set but not ever checked. 
Nov  8 22:01:21 uue16 snort[7896]: 37 out of 512 flowbits in use. 
Nov  8 22:01:21 uue16 kernel: [   26.856000] device eth0 entered promiscuous mode
Nov  8 22:01:21 uue16 kernel: [   26.856000] audit(1194580881.093:4): dev=eth0 prom=256 old_prom=0 auid=4294967295
Nov  8 22:01:21 uue16 snort[7896]: Initializing daemon mode 
Nov  8 22:01:21 uue16 kernel: [   26.872000] device eth0 left promiscuous mode
Nov  8 22:01:21 uue16 kernel: [   26.872000] audit(1194580881.093:5): dev=eth0 prom=0 old_prom=256 auid=4294967295
Nov  8 22:01:21 uue16 kernel: [   26.892000] device eth0 entered promiscuous mode
Nov  8 22:01:21 uue16 snort[7952]: PID path stat checked out ok, PID path set to /var/run/ 
Nov  8 22:01:21 uue16 kernel: [   26.892000] audit(1194580881.593:6): dev=eth0 prom=256 old_prom=0 auid=4294967295
Nov  8 22:01:21 uue16 snort[7952]: Writing PID "7952" to file "/var/run//snort_eth0.pid" 
Nov  8 22:01:21 uue16 snort[7896]: Daemon parent exiting 
Nov  8 22:01:21 uue16 snort[7952]: Daemon initialized, signaled parent pid: 7896 
Nov  8 22:01:21 uue16 kernel: [   27.060000] Failure registering capabilities with primary security module.
Nov  8 22:01:21 uue16 avahi-daemon[8148]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Nov  8 22:01:21 uue16 avahi-daemon[8148]: Successfully dropped root privileges.
Nov  8 22:01:21 uue16 avahi-daemon[8148]: avahi-daemon 0.6.20 starting up.
Nov  8 22:01:21 uue16 avahi-daemon[8148]: Successfully called chroot().
Nov  8 22:01:21 uue16 avahi-daemon[8148]: Successfully dropped remaining capabilities.
Nov  8 22:01:21 uue16 kernel: [   27.108000] eth0: no IPv6 routers present
Nov  8 22:01:21 uue16 avahi-daemon[8148]: No service file found in /etc/avahi/services.
Nov  8 22:01:21 uue16 avahi-daemon[8148]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.20.253.
Nov  8 22:01:21 uue16 avahi-daemon[8148]: New relevant interface eth0.IPv4 for mDNS.
Nov  8 22:01:21 uue16 avahi-daemon[8148]: Network interface enumeration completed.
Nov  8 22:01:21 uue16 avahi-daemon[8148]: Registering new address record for fe80::215:f2ff:fea0:f8e6 on eth0.*.
Nov  8 22:01:21 uue16 avahi-daemon[8148]: Registering new address record for 192.168.20.253 on eth0.IPv4.
Nov  8 22:01:21 uue16 avahi-daemon[8148]: Registering HINFO record with values 'I686'/'LINUX'.
Nov  8 22:01:21 uue16 dhcdbd: Started up.
Nov  8 22:01:22 uue16 python: hp-probe[8180]: warning: No devices found on the 'usb' bus. If this isn't the result you are expecting,
Nov  8 22:01:22 uue16 python: hp-probe[8180]: warning: check to make sure your devices are properly connected and powered on.
Nov  8 22:01:22 uue16 NetworkManager: <debug> [1194580882.099296] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_c202_MY5AR3X0H504KK_if0_printer_MY5AR3X0H504KK'). 
Nov  8 22:01:22 uue16 avahi-daemon[8148]: Server startup complete. Host name is uue16.local. Local service cookie is 1731285922.
Nov  8 22:01:23 uue16 hcid[8322]: Bluetooth HCI daemon
Nov  8 22:01:24 uue16 kernel: [   29.328000] Bluetooth: Core ver 2.11
Nov  8 22:01:24 uue16 kernel: [   29.328000] NET: Registered protocol family 31
Nov  8 22:01:24 uue16 kernel: [   29.328000] Bluetooth: HCI device and connection manager initialized
Nov  8 22:01:24 uue16 kernel: [   29.328000] Bluetooth: HCI socket layer initialized
Nov  8 22:01:24 uue16 hcid[8322]: Starting SDP server
Nov  8 22:01:24 uue16 kernel: [   29.416000] Bluetooth: L2CAP ver 2.8
Nov  8 22:01:24 uue16 kernel: [   29.416000] Bluetooth: L2CAP socket layer initialized
Nov  8 22:01:24 uue16 hcid[8322]: Created local server at unix:abstract=/var/run/dbus-elqXTHqRF1,guid=626781d5b081740be258a8004733db94
Nov  8 22:01:24 uue16 audio[8347]: Bluetooth Audio daemon
Nov  8 22:01:24 uue16 audio[8347]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Nov  8 22:01:24 uue16 audio[8347]: Unix socket created: 5
Nov  8 22:01:24 uue16 kernel: [   29.508000] Bluetooth: RFCOMM socket layer initialized
Nov  8 22:01:24 uue16 kernel: [   29.508000] Bluetooth: RFCOMM TTY layer initialized
Nov  8 22:01:24 uue16 kernel: [   29.508000] Bluetooth: RFCOMM ver 1.8
Nov  8 22:01:24 uue16 input[8356]: Bluetooth Input daemon
Nov  8 22:01:24 uue16 input[8356]: Registered input manager path:/org/bluez/input
Nov  8 22:01:24 uue16 audio[8347]: add_service_record: got record id 0x10000
Nov  8 22:01:24 uue16 audio[8347]: add_service_record: got record id 0x10001
Nov  8 22:01:24 uue16 audio[8347]: Registered manager path:/org/bluez/audio
Nov  8 22:01:26 uue16 kernel: [   31.860000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov  8 22:01:26 uue16 anacron[8579]: Anacron 2.3 started on 2007-11-08
Nov  8 22:01:26 uue16 anacron[8579]: Normal exit (0 jobs run)
Nov  8 22:01:26 uue16 /usr/sbin/cron[8615]: (CRON) INFO (pidfile fd = 3)
Nov  8 22:01:26 uue16 /usr/sbin/cron[8619]: (CRON) STARTUP (fork ok)
Nov  8 22:01:27 uue16 /usr/sbin/cron[8619]: (CRON) INFO (Running @reboot jobs)
Nov  8 22:01:27 uue16 snort[7952]: Preprocessor/Decoder Rule Count: 0 
Nov  8 22:01:27 uue16 snort[7952]: Snort initialization completed successfully (pid=7952) 
Nov  8 22:01:27 uue16 snort[7952]: Not Using PCAP_FRAMES 
Nov  8 22:01:29 uue16 kernel: [   34.352000] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
Nov  8 22:01:29 uue16 kernel: [   34.352000] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
Nov  8 22:01:29 uue16 kernel: [   34.352000] [fglrx] Reserve Block - 2 offset =  0Xffff000 length = 0X1000
Nov  8 22:01:29 uue16 kernel: [   34.352000] [fglrx] Reserve Block - 3 offset =  0Xffbf000 length = 0X40000
Nov  8 22:01:43 uue16 hcid[8322]: Default passkey agent (:1.22, /org/bluez/passkey) registered
Nov  8 22:01:43 uue16 hcid[8322]: Default authorization agent (:1.22, /org/bluez/auth) registered
Nov  8 22:01:43 uue16 hald: mounted /dev/sdf1 on behalf of uid 1000
Nov  8 22:01:45 uue16 ntfs-3g[9046]: Version 1.913 
Nov  8 22:01:45 uue16 ntfs-3g[9046]: Mounted /dev/sdk1 (Read-Write, label "My Documents", NTFS 3.1) 
Nov  8 22:01:45 uue16 ntfs-3g[9046]: Cmdline options: rw,nosuid,nodev,locale=en_US.UTF-8 
Nov  8 22:01:46 uue16 ntfs-3g[9046]: Mount options: noatime,rw,nosuid,nodev,silent,allow_other,nonempty,fsname=/dev/sdk1,blkdev,blksize=4096 
Nov  8 22:01:46 uue16 hald: mounted /dev/sdk1 on behalf of uid 1000
Nov  8 22:01:51 uue16 NetworkManager: <info>  Updating allowed wireless network lists. 
Nov  8 22:01:51 uue16 NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

```

---

### Post by mikeescott on 2007-11-10
I installed Gutsy64 over Feisty64 with both ports enabled and the both work fine. Is there a way to correct this problem without reinstalling all over again?

---

