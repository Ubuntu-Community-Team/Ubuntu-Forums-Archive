---
title: "ok here is what i have done"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2009-07-07
i have hooked my ipd nano 3g to my computer  still not mountin    i opened the terminal and typed in dmesg

and i got this


[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800         
[    0.000000] Initializing cgroup subsys cpuset              
[    0.000000] Initializing cgroup subsys cpu                 
[    0.000000] Linux version 2.6.28-13-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 (Ubuntu 2.6.28-13.44-generic)
[    0.000000] KERNEL supported cpus:                                                                                                                                               
[    0.000000]   Intel GenuineIntel                                                                                                                                                 
[    0.000000]   AMD AuthenticAMD                                                                                                                                                   
[    0.000000]   NSC Geode by NSC                                                                                                                                                   
[    0.000000]   Cyrix CyrixInstead                                                                                                                                                 
[    0.000000]   Centaur CentaurHauls                                                                                                                                               
[    0.000000]   Transmeta GenuineTMx86                                                                                                                                             
[    0.000000]   Transmeta TransmetaCPU                                                                                                                                             
[    0.000000]   UMC UMC UMC UMC                                                                                                                                                    
[    0.000000] BIOS-provided physical RAM map:                                                                                                                                      
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)                                                                                                             
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)                                                                                                           
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)                                                                                                           
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f770000 (usable)                                                                                                             
[    0.000000]  BIOS-e820: 000000001f770000 - 000000001f77a000 (ACPI data)                                                                                                          
[    0.000000]  BIOS-e820: 000000001f77a000 - 000000001f780000 (ACPI NVS)                                                                                                           
[    0.000000]  BIOS-e820: 000000001f780000 - 0000000020000000 (reserved)                                                                                                           
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)                                                                                                           
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)                                                                                                           
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)                                                                                                           
[    0.000000] DMI present.                                                                                                                                                         
[    0.000000] last_pfn = 0x1f770 max_arch_pfn = 0x100000                                                                                                                           
[    0.000000] Scanning 2 areas for low memory corruption                                                                                                                           
[    0.000000] modified physical RAM map:                                                                                                                                           
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)                                                                                                              
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)                                                                                                            
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)                                                                                                              
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)                                                                                                            
[    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)                                                                                                              
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)                                                                                                            
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)                                                                                                            
[    0.000000]  modified: 0000000000100000 - 000000001f770000 (usable)                                                                                                              
[    0.000000]  modified: 000000001f770000 - 000000001f77a000 (ACPI data)                                                                                                           
[    0.000000]  modified: 000000001f77a000 - 000000001f780000 (ACPI NVS)                                                                                                            
[    0.000000]  modified: 000000001f780000 - 0000000020000000 (reserved)                                                                                                            
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)                                                                                                            
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)                                                                                                            
[    0.000000]  modified: 00000000ff800000 - 0000000100000000 (reserved)                                                                                                            
[    0.000000] kernel direct mapping tables up to 1f770000 @ 10000-16000                                                                                                            
[    0.000000] RAMDISK: 1f02b000 - 1f75f2ac                                                                                                                                         
[    0.000000] ACPI: RSDP 000F64A0, 0014 (r0 PTLTD )                                                                                                                                
[    0.000000] ACPI: RSDT 1F77509C, 0038 (r1 PTLTD    RSDT    60400D0  LTP        0)                                                                                                
[    0.000000] ACPI: FACP 1F779E93, 0074 (r1 IBM    THINKCEN  60400D0 PTL         1)                                                                                                
[    0.000000] ACPI: DSDT 1F7750D4, 4DBF (r1    IBM THINKCEN  60400D0 MSFT  100000E)                                                                                                
[    0.000000] ACPI: FACS 1F77AFC0, 0040                                                                                                                                            
[    0.000000] ACPI: TCPA 1F779F07, 0032 (r1 IBM    THINKCEN  60400D0 PTL         1)                                                                                                
[    0.000000] ACPI: APIC 1F779F39, 0068 (r1 PTLTD       APIC    60400D0  LTP        0)                                                                                             
[    0.000000] ACPI: BOOT 1F779FA1, 0028 (r1 PTLTD  $SBFTBL$  60400D0  LTP        1)                                                                                                
[    0.000000] ACPI: SSDT 1F779FC9, 0037 (r1 PTLTD  ACPIHT    60400D0  LTP        1)                                                                                                
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                                                                                  
[    0.000000] 0MB HIGHMEM available.                                                                                                                                               
[    0.000000] 503MB LOWMEM available.                                                                                                                                              
[    0.000000]   mapped low ram: 0 - 1f770000                                                                                                                                       
[    0.000000]   low ram: 00000000 - 1f770000                                                                                                                                       
[    0.000000]   bootmap 00012000 - 00015ef0                                                                                                                                        
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001f770000]                                                                                                         
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                                                                                        
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]                                                                                        
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]                                                                                        
[    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac]                                                                                        
[    0.000000]   #4 [001f02b000 - 001f75f2ac]          RAMDISK ==> [001f02b000 - 001f75f2ac]                                                                                        
[    0.000000]   #5 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000]                                                                                        
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]                                                                                        
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]                                                                                        
[    0.000000]   #8 [0000012000 - 0000016000]          BOOTMAP ==> [0000012000 - 0000016000]                                                                                        
[    0.000000] found SMP MP-table at [c00f63f0] 000f63f0                                                                                                                            
[    0.000000] Zone PFN ranges:                                                                                                                                                     
[    0.000000]   DMA      0x00000000 -> 0x00001000                                                                                                                                  
[    0.000000]   Normal   0x00001000 -> 0x0001f770                                                                                                                                  
[    0.000000]   HighMem  0x0001f770 -> 0x0001f770                                                                                                                                  
[    0.000000] Movable zone start PFN for each node                                                                                                                                 
[    0.000000] early_node_map[4] active PFN ranges                                                                                                                                  
[    0.000000]     0: 0x00000000 -> 0x00000002                                                                                                                                      
[    0.000000]     0: 0x00000006 -> 0x00000007                                                                                                                                      
[    0.000000]     0: 0x00000010 -> 0x00000092                                                                                                                                      
[    0.000000]     0: 0x00000100 -> 0x0001f770                                                                                                                                      
[    0.000000] On node 0 totalpages: 128757                                                                                                                                         
[    0.000000] free_area_init_node: node 0, pgdat c06c9500, node_mem_map c1000000                                                                                                   
[    0.000000]   DMA zone: 32 pages used for memmap                                                                                                                                 
[    0.000000]   DMA zone: 0 pages reserved                                                                                                                                         
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0                                                                                                                                 
[    0.000000]   Normal zone: 975 pages used for memmap                                                                                                                             
[    0.000000]   Normal zone: 123809 pages, LIFO batch:31                                                                                                                           
[    0.000000]   HighMem zone: 0 pages used for memmap                                                                                                                              
[    0.000000]   Movable zone: 0 pages used for memmap                                                                                                                              
[    0.000000] ACPI: PM-Timer IO Port: 0x1008                                                                                                                                       
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                                                                                  
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)                                                                                                                   
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)                                                                                                                   
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])                                                                                                                  
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])                                                                                                                  
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])                                                                                                              
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23                                                                                                       
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)                                                                                                           
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)                                                                                                          
[    0.000000] ACPI: IRQ0 used by override.                                                                                                                                         
[    0.000000] ACPI: IRQ2 used by override.                                                                                                                                         
[    0.000000] ACPI: IRQ9 used by override.                                                                                                                                         
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs                                                                                                                        
[    0.000000] Using ACPI (MADT) for SMP configuration information                                                                                                                  
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs                                                                                                                                 
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000                                                                                                    
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000                                                                                                    
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000                                                                                                    
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000                                                                                                    
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000                                                                                                    
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)                                                                                               
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data                                                                                                                       
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1                                                                                                                            
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127750                                                                                          
[    0.000000] Kernel command line: root=UUID=00fa0420-aa93-4a4c-84d1-1eb7ebedb2a8 ro quiet splash                                                                                  
[    0.000000] Enabling fast FPU save and restore... done.                                                                                                                          
[    0.000000] Enabling unmasked SIMD FPU exception support... done.                                                                                                                
[    0.000000] Initializing CPU#0                                                                                                                                                   
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)                                                                                                                 
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops                                                                                                                        
[    0.000000] Detected 2792.959 MHz processor.                                                                                                                                     
[    0.004000] Console: colour VGA+ 80x25                                                                                                                                           
[    0.004000] console [tty0] enabled                                                                                                                                               
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)                                                                                                      
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)                                                                                                       
[    0.004000] allocated 2577600 bytes of page_cgroup                                                                                                                               
[    0.004000] please try cgroup_disable=memory option if you don't want                                                                                                            
[    0.004000] Scanning for low memory corruption every 60 seconds                                                                                                                  
[    0.004000] Memory: 492672k/515520k available (4110k kernel code, 22128k reserved, 2197k data, 532k init, 0k highmem)                                                            
[    0.004000] virtual kernel memory layout:                                                                                                                                        
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)                                                                                                                    
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)                                                                                                                    
[    0.004000]     vmalloc : 0xdff70000 - 0xff3fe000   ( 500 MB)                                                                                                                    
[    0.004000]     lowmem  : 0xc0000000 - 0xdf770000   ( 503 MB)                                                                                                                    
[    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)                                                                                                                    
[    0.004000]       .data : 0xc05039df - 0xc0728e60   (2197 kB)                                                                                                                    
[    0.004000]       .text : 0xc0100000 - 0xc05039df   (4110 kB)                                                                                                                    
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.                                                                                          
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1                                                                                             
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 5585.91 BogoMIPS (lpj=11171836)                                                           
[    0.004031] Security Framework initialized                                                                                                                                       
[    0.004039] SELinux:  Disabled at boot.                                                                                                                                          
[    0.004058] AppArmor: AppArmor initialized                                                                                                                                       
[    0.004071] Mount-cache hash table entries: 512                                                                                                                                  
[    0.004230] Initializing cgroup subsys ns                                                                                                                                        
[    0.004235] Initializing cgroup subsys cpuacct                                                                                                                                   
[    0.004239] Initializing cgroup subsys memory                                                                                                                                    
[    0.004244] Initializing cgroup subsys freezer                                                                                                                                   
[    0.004262] CPU: Trace cache: 12K uops, L1 D cache: 8K                                                                                                                           
[    0.004266] CPU: L2 cache: 512K                                                                                                                                                  
[    0.004270] CPU: Physical Processor ID: 0                                                                                                                                        
[    0.004273] CPU: Processor Core ID: 0                                                                                                                                            
[    0.004288] Checking 'hlt' instruction... OK.                                                                                                                                    
[    0.023001] ACPI: Core revision 20080926                                                                                                                                         
[    0.026078] ACPI: Checking initramfs for custom DSDT                                                                                                                             
[    0.333912] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1                                                                                                                 
[    0.373770] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09                                                                                                                  
[    0.376001] Booting processor 1 APIC 0x1 ip 0x6000                                                                                                                               
[    0.004000] Initializing CPU#1                                                                                                                                                   
[    0.004000] Calibrating delay using timer specific routine.. 5586.48 BogoMIPS (lpj=11172961)                                                                                     
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 8K                                                                                                                           
[    0.004000] CPU: L2 cache: 512K                                                                                                                                                  
[    0.004000] CPU: Physical Processor ID: 0                                                                                                                                        
[    0.004000] CPU: Processor Core ID: 0                                                                                                                                            
[    0.460217] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09                                                                                                                  
[    0.460242] checking TSC synchronization [CPU#0 -> CPU#1]: passed.                                                                                                               
[    0.464072] Brought up 2 CPUs                                                                                                                                                    
[    0.464078] Total of 2 processors activated (11172.39 BogoMIPS).                                                                                                                 
[    0.464130] CPU0 attaching sched-domain:                                                                                                                                         
[    0.464135]  domain 0: span 0-1 level SIBLING                                                                                                                                    
[    0.464138]   groups: 0 1                                                                                                                                                        
[    0.464147] CPU1 attaching sched-domain:                                                                                                                                         
[    0.464151]  domain 0: span 0-1 level SIBLING                                                                                                                                    
[    0.464154]   groups: 1 0                                                                                                                                                        
[    0.464256] net_namespace: 776 bytes                                                                                                                                             
[    0.464266] Booting paravirtualized kernel on bare hardware                                                                                                                      
[    0.464518] Time: 16:26:28  Date: 07/04/09                                                                                                                                       
[    0.464518] regulator: core version 0.5                                                                                                                                          
[    0.464518] NET: Registered protocol family 16                                                                                                                                   
[    0.464518] EISA bus registered                                                                                                                                                  
[    0.464518] ACPI: bus type pci registered                                                                                                                                        
[    0.464717] PCI: PCI BIOS revision 2.10 entry at 0xfd98d, last bus=3                                                                                                             
[    0.464721] PCI: Using configuration type 1 for base access                                                                                                                      
[    0.468306] ACPI: EC: Look up EC in DSDT                                                                                                                                         
[    0.489037] ACPI: Interpreter enabled                                                                                                                                            
[    0.489044] ACPI: (supports S0 S1 S3 S4 S5)                                                                                                                                      
[    0.489074] ACPI: Using IOAPIC for interrupt routing                                                                                                                             
[    0.522350] ACPI: No dock devices found.                                                                                                                                         
[    0.522367] ACPI: PCI Root Bridge [PCI0] (0000:00)                                                                                                                               
[    0.522427] pci 0000:00:00.0: reg 10 32bit mmio: [0xec000000-0xefffffff]                                                                                                         
[    0.522489] pci 0000:00:02.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]                                                                                                         
[    0.522497] pci 0000:00:02.0: reg 14 32bit mmio: [0xe8000000-0xe807ffff]                                                                                                         
[    0.522503] pci 0000:00:02.0: reg 18 io port: [0x1800-0x1807]                                                                                                                    
[    0.522600] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]                                                                                                                    
[    0.522655] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]                                                                                                                    
[    0.522709] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]                                                                                                                    
[    0.522763] pci 0000:00:1d.3: reg 20 io port: [0x1880-0x189f]                                                                                                                    
[    0.522826] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe8080000-0xe80803ff]                                                                                                         
[    0.522873] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold                                                                                                                
[    0.522879] pci 0000:00:1d.7: PME# disabled                                                                                                                                      
[    0.522969] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000                                                                                                                   
[    0.522976] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO                                                                                              
[    0.522981] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO                                                                                                       
[    0.523003] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]                                                                                                                        
[    0.523011] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]                                                                                                                        
[    0.523018] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]                                                                                                                        
[    0.523026] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]                                                                                                                        
[    0.523034] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]                                                                                                                    
[    0.523042] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]                                                                                                             
[    0.523094] pci 0000:00:1f.3: reg 20 io port: [0x18a0-0x18bf]                                                                                                                    
[    0.523138] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]                                                                                                                    
[    0.523145] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]                                                                                                                    
[    0.523153] pci 0000:00:1f.5: reg 18 32bit mmio: [0xe8080c00-0xe8080dff]                                                                                                         
[    0.523160] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xe8080800-0xe80808ff]                                                                                                         
[    0.523184] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold                                                                                                                
[    0.523189] pci 0000:00:1f.5: PME# disabled                                                                                                                                      
[    0.524027] pci 0000:03:08.0: reg 10 32bit mmio: [0xe8100000-0xe8100fff]                                                                                                         
[    0.524035] pci 0000:03:08.0: reg 14 io port: [0x2000-0x203f]                                                                                                                    
[    0.524067] pci 0000:03:08.0: supports D1 D2                                                                                                                                     
[    0.524070] pci 0000:03:08.0: PME# supported from D0 D1 D2 D3hot D3cold                                                                                                          
[    0.524075] pci 0000:03:08.0: PME# disabled                                                                                                                                      
[    0.524110] pci 0000:03:0a.0: reg 10 32bit mmio: [0xe8400000-0xe87fffff]                                                                                                         
[    0.524150] pci 0000:03:0a.0: supports D2                                                                                                                                        
[    0.524152] pci 0000:03:0a.0: PME# supported from D2 D3hot D3cold                                                                                                                
[    0.524157] pci 0000:03:0a.0: PME# disabled                                                                                                                                      
[    0.524190] pci 0000:00:1e.0: transparent bridge                                                                                                                                 
[    0.524195] pci 0000:00:1e.0: bridge io port: [0x2000-0x2fff]                                                                                                                    
[    0.524201] pci 0000:00:1e.0: bridge 32bit mmio: [0xe8100000-0xe87fffff]                                                                                                         
[    0.524213] bus 00 -> node 0                                                                                                                                                     
[    0.524221] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]                                                                                                                  
[    0.524492] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SLOT._PRT]                                                                                                             
[    0.622009] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)                                                                                                     
[    0.622162] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)                                                                                                     
[    0.622312] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)                                                                                                     
[    0.622461] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)                                                                                                     
[    0.622620] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 12 14 15)                                                                                                     
[    0.622777] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.                                                                                        
[    0.622938] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12 14 15)                                                                                                     
[    0.623097] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 9 10 11 12 14 15)                                                                                                     
[    0.623312] ACPI: WMI: Mapper loaded                                                                                                                                             
[    0.623411] SCSI subsystem initialized                                                                                                                                           
[    0.623411] libata version 3.00 loaded.                                                                                                                                          
[    0.623411] usbcore: registered new interface driver usbfs                                                                                                                       
[    0.623411] usbcore: registered new interface driver hub                                                                                                                         
[    0.623411] usbcore: registered new device driver usb                                                                                                                            
[    0.624029] PCI: Using ACPI for IRQ routing                                                                                                                                      
[    0.628015] Bluetooth: Core ver 2.13                                                                                                                                             
[    0.628043] NET: Registered protocol family 31                                                                                                                                   
[    0.628043] Bluetooth: HCI device and connection manager initialized                                                                                                             
[    0.628043] Bluetooth: HCI socket layer initialized                                                                                                                              
[    0.628043] NET: Registered protocol family 8                                                                                                                                    
[    0.628043] NET: Registered protocol family 20                                                                                                                                   
[    0.628054] NetLabel: Initializing                                                                                                                                               
[    0.628057] NetLabel:  domain hash size = 128                                                                                                                                    
[    0.628060] NetLabel:  protocols = UNLABELED CIPSOv4                                                                                                                             
[    0.628077] NetLabel:  unlabeled traffic allowed by default                                                                                                                      
[    0.628185] hpet clockevent registered                                                                                                                                           
[    0.628190] HPET: 3 timers in total, 0 timers will be used for per-cpu timer                                                                                                     
[    0.628196] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0                                                                                                                              
[    0.628203] hpet0: 3 comparators, 64-bit 14.318180 MHz counter                                                                                                                   
[    0.632106] AppArmor: AppArmor Filesystem Enabled                                                                                                                                
[    0.640014] pnp: PnP ACPI init                                                                                                                                                   
[    0.640031] ACPI: bus type pnp registered                                                                                                                                        
[    0.676491] pnp: PnP ACPI: found 14 devices                                                                                                                                      
[    0.676497] ACPI: ACPI bus type pnp unregistered                                                                                                                                 
[    0.676502] PnPBIOS: Disabled by ACPI PNP                                                                                                                                        
[    0.676528] system 00:01: ioport range 0x4d0-0x4d1 has been reserved                                                                                                             
[    0.676532] system 00:01: ioport range 0x800-0x87f has been reserved                                                                                                             
[    0.676535] system 00:01: ioport range 0x1000-0x107f has been reserved                                                                                                           
[    0.676539] system 00:01: ioport range 0x1100-0x111f has been reserved                                                                                                           
[    0.676542] system 00:01: ioport range 0x1180-0x11bf has been reserved                                                                                                           
[    0.676547] system 00:01: ioport range 0xe000-0xe00f has been reserved                                                                                                           
[    0.676550] system 00:01: ioport range 0xfe00-0xfe00 has been reserved                                                                                                           
[    0.676554] system 00:01: ioport range 0xfe10-0xfe11 has been reserved                                                                                                           
[    0.676559] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved                                                                                                    
[    0.676563] system 00:01: iomem range 0xfed90000-0xfed903ff has been reserved                                                                                                    
[    0.711362] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03                                                                                                                  
[    0.711367] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff                                                                                                                         
[    0.711373] pci 0000:00:1e.0:   MEM window: 0xe8100000-0xe87fffff                                                                                                                
[    0.711378] pci 0000:00:1e.0:   PREFETCH window: disabled                                                                                                                        
[    0.711394] pci 0000:00:1e.0: setting latency timer to 64                                                                                                                        
[    0.711400] bus: 00 index 0 io port: [0x00-0xffff]                                                                                                                               
[    0.711403] bus: 00 index 1 mmio: [0x000000-0xffffffff]                                                                                                                          
[    0.711406] bus: 03 index 0 io port: [0x2000-0x2fff]                                                                                                                             
[    0.711409] bus: 03 index 1 mmio: [0xe8100000-0xe87fffff]                                                                                                                        
[    0.711411] bus: 03 index 2 mmio: [0x0-0x0]                                                                                                                                      
[    0.711414] bus: 03 index 3 io port: [0x00-0xffff]                                                                                                                               
[    0.711417] bus: 03 index 4 mmio: [0x000000-0xffffffff]                                                                                                                          
[    0.711429] NET: Registered protocol family 2                                                                                                                                    
[    0.724085] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)                                                                                                      
[    0.724396] TCP established hash table entries: 16384 (order: 5, 131072 bytes)                                                                                                   
[    0.724451] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)                                                                                                          
[    0.724508] TCP: Hash tables configured (established 16384 bind 16384)                                                                                                           
[    0.724511] TCP reno registered                                                                                                                                                  
[    0.732100] NET: Registered protocol family 1                                                                                                                                    
[    0.732257] checking if image is initramfs... it is                                                                                                                              
[    1.128361] Switched to high resolution mode on CPU 1                                                                                                                            
[    1.132044] Switched to high resolution mode on CPU 0                                                                                                                            
[    1.360465] Freeing initrd memory: 7376k freed                                                                                                                                   
[    1.360516] Simple Boot Flag at 0x35 set to 0x1                                                                                                                                  
[    1.360553] cpufreq: No nForce2 chipset.                                                                                                                                         
[    1.360746] audit: initializing netlink socket (disabled)                                                                                                                        
[    1.360769] type=2000 audit(1246724788.357:1): initialized                                                                                                                       
[    1.367442] HugeTLB registered 4 MB page size, pre-allocated 0 pages                                                                                                             
[    1.369124] VFS: Disk quotas dquot_6.5.1                                                                                                                                         
[    1.369212] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)                                                                                                           
[    1.370049] fuse init (API version 7.10)                                                                                                                                         
[    1.370159] msgmni has been set to 977                                                                                                                                           
[    1.370635] alg: No test for stdrng (krng)                                                                                                                                       
[    1.370659] io scheduler noop registered                                                                                                                                         
[    1.370664] io scheduler anticipatory registered                                                                                                                                 
[    1.370668] io scheduler deadline registered                                                                                                                                     
[    1.370699] io scheduler cfq registered (default)                                                                                                                                
[    1.370717] pci 0000:00:02.0: Boot video device                                                                                                                                  
[    1.370931] pci 0000:03:08.0: Firmware left e100 interrupts enabled; disabling                                                                                                   
[    1.393506] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                                                                                                                      
[    1.393519] pciehp: PCI Express Hot Plug Controller Driver version: 0.4                                                                                                          
[    1.393698] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0                                                                                            
[    1.393702] ACPI: Power Button (FF) [PWRF]                                                                                                                                       
[    1.393778] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0C:00/input/input1                                                                        
[    1.393782] ACPI: Power Button (CM) [PWRB]                                                                                                                                       
[    1.394027] processor ACPI_CPU:00: registered as cooling_device0                                                                                                                 
[    1.394033] ACPI: Processor [CPU0] (supports 8 throttling states)                                                                                                                
[    1.394160] processor ACPI_CPU:01: registered as cooling_device1                                                                                                                 
[    1.394166] ACPI: Processor [CPU1] (supports 8 throttling states)                                                                                                                
[    1.415548] thermal LNXTHERM:01: registered as thermal_zone0                                                                                                                     
[    1.416438] ACPI: Thermal Zone [THM0] (62 C)                                                                                                                                     
[    1.416540] isapnp: Scanning for PnP cards...                                                                                                                                    
[    1.770321] isapnp: No Plug & Play device found                                                                                                                                  
[    1.777187] Serial: 8250/16550 driver4 ports, IRQ sharing enabled                                                                                                                
[    1.777286] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                                                                                 
[    1.777750] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                                                                                      
[    1.778770] brd: module loaded                                                                                                                                                   
[    1.779220] loop: module loaded                                                                                                                                                  
[    1.779323] Fixed MDIO Bus: probed                                                                                                                                               
[    1.779331] PPP generic driver version 2.4.2                                                                                                                                     
[    1.779414] input: Macintosh mouse button emulation as /devices/virtual/input/input2                                                                                             
[    1.779459] Driver 'sd' needs updating - please use bus_type methods                                                                                                             
[    1.779473] Driver 'sr' needs updating - please use bus_type methods                                                                                                             
[    1.779573] ata_piix 0000:00:1f.1: version 2.12                                                                                                                                  
[    1.779586] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)                                                                                                                
[    1.779599] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18                                                                                                    
[    1.779655] ata_piix 0000:00:1f.1: setting latency timer to 64                                                                                                                   
[    1.779809] scsi0 : ata_piix                                                                                                                                                     
[    1.779953] scsi1 : ata_piix                                                                                                                                                     
[    1.781405] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14                                                                                                      
[    1.781409] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15                                                                                                      
[    1.968273] ata1.00: HPA unlocked: 151440515 -> 156312576, native 156312576                                                                                                      
[    1.968279] ata1.00: ATA-6: IC35L090AVV207-0, V23OA66A, max UDMA/100                                                                                                             
[    1.968282] ata1.00: 156312576 sectors, multi 16: LBA48                                                                                                                          
[    1.992437] ata1.00: configured for UDMA/100                                                                                                                                     
[    2.268653] ata2.00: ATAPI: LTN486S, YUS6, max UDMA/33, CDB intr                                                                                                                 
[    2.268690] ata2.01: ATAPI: LITE-ON DVDRW SOHW-1693S, KS06, max UDMA/66                                                                                                          
[    2.276375] ata2.00: configured for UDMA/33                                                                                                                                      
[    2.292234] ata2.01: configured for UDMA/66                                                                                                                                      
[    2.293043] scsi 0:0:0:0: Direct-Access     ATA      IC35L090AVV207-0 V23O PQ: 0 ANSI: 5                                                                                         
[    2.293188] sd 0:0:0:0: [sda] 156312576 512-byte hardware sectors: (80.0 GB/74.5 GiB)                                                                                            
[    2.293211] sd 0:0:0:0: [sda] Write Protect is off                                                                                                                               
[    2.293215] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                                                                                            
[    2.293252] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                              
[    2.293349] sd 0:0:0:0: [sda] 156312576 512-byte hardware sectors: (80.0 GB/74.5 GiB)                                                                                            
[    2.293370] sd 0:0:0:0: [sda] Write Protect is off                                                                                                                               
[    2.293374] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                                                                                            
[    2.293410] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                              
[    2.293415]  sda: sda1 sda2 < sda5 >                                                                                                                                             
[    2.330721] sd 0:0:0:0: [sda] Attached SCSI disk                                                                                                                                 
[    2.330797] sd 0:0:0:0: Attached scsi generic sg0 type 0                                                                                                                         
[    2.331111] scsi 1:0:0:0: CD-ROM            LITEON   CD-ROM LTN486S   YUS6 PQ: 0 ANSI: 5                                                                                         
[    2.333901] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray                                                                                                               
[    2.333905] Uniform CD-ROM driver Revision: 3.20                                                                                                                                 
[    2.334051] sr 1:0:0:0: Attached scsi CD-ROM sr0                                                                                                                                 
[    2.334115] sr 1:0:0:0: Attached scsi generic sg1 type 5                                                                                                                         
[    2.334901] scsi 1:0:1:0: CD-ROM            LITE-ON  DVDRW SOHW-1693S KS06 PQ: 0 ANSI: 5                                                                                         
[    2.338567] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray                                                                                                        
[    2.338656] sr 1:0:1:0: Attached scsi CD-ROM sr1                                                                                                                                 
[    2.338712] sr 1:0:1:0: Attached scsi generic sg2 type 5                                                                                                                         
[    2.339579] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                                                                                                           
[    2.339614] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23                                                                                                    
[    2.339650] ehci_hcd 0000:00:1d.7: setting latency timer to 64                                                                                                                   
[    2.339655] ehci_hcd 0000:00:1d.7: EHCI Host Controller                                                                                                                          
[    2.339749] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1                                                                                                 
[    2.343668] ehci_hcd 0000:00:1d.7: debug port 1                                                                                                                                  
[    2.343677] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported                                                                                                       
[    2.343701] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe8080000                                                                                                                     
[    2.356044] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00                                                                                                                    
[    2.356182] usb usb1: configuration #1 chosen from 1 choice                                                                                                                      
[    2.356221] hub 1-0:1.0: USB hub found                                                                                                                                           
[    2.356237] hub 1-0:1.0: 8 ports detected                                                                                                                                        
[    2.356422] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                                                                                                               
[    2.356455] uhci_hcd: USB Universal Host Controller Interface driver                                                                                                             
[    2.356512] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                                                                    
[    2.356522] uhci_hcd 0000:00:1d.0: setting latency timer to 64                                                                                                                   
[    2.356526] uhci_hcd 0000:00:1d.0: UHCI Host Controller                                                                                                                          
[    2.356592] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2                                                                                                 
[    2.356627] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001820                                                                                                                    
[    2.356723] usb usb2: configuration #1 chosen from 1 choice                                                                                                                      
[    2.356761] hub 2-0:1.0: USB hub found                                                                                                                                           
[    2.356771] hub 2-0:1.0: 2 ports detected                                                                                                                                        
[    2.356884] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19                                                                                                    
[    2.356891] uhci_hcd 0000:00:1d.1: setting latency timer to 64                                                                                                                   
[    2.356896] uhci_hcd 0000:00:1d.1: UHCI Host Controller                                                                                                                          
[    2.356954] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3                                                                                                 
[    2.356984] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840                                                                                                                    
[    2.357089] usb usb3: configuration #1 chosen from 1 choice                                                                                                                      
[    2.357123] hub 3-0:1.0: USB hub found                                                                                                                                           
[    2.357132] hub 3-0:1.0: 2 ports detected                                                                                                                                        
[    2.357244] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18                                                                                                    
[    2.357252] uhci_hcd 0000:00:1d.2: setting latency timer to 64                                                                                                                   
[    2.357256] uhci_hcd 0000:00:1d.2: UHCI Host Controller                                                                                                                          
[    2.357317] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4                                                                                                 
[    2.357347] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860                                                                                                                    
[    2.357441] usb usb4: configuration #1 chosen from 1 choice                                                                                                                      
[    2.357475] hub 4-0:1.0: USB hub found                                                                                                                                           
[    2.357485] hub 4-0:1.0: 2 ports detected                                                                                                                                        
[    2.357595] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                                                                    
[    2.357602] uhci_hcd 0000:00:1d.3: setting latency timer to 64                                                                                                                   
[    2.357606] uhci_hcd 0000:00:1d.3: UHCI Host Controller                                                                                                                          
[    2.357672] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5                                                                                                 
[    2.357693] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880                                                                                                                    
[    2.357790] usb usb5: configuration #1 chosen from 1 choice                                                                                                                      
[    2.357830] hub 5-0:1.0: USB hub found                                                                                                                                           
[    2.357840] hub 5-0:1.0: 2 ports detected                                                                                                                                        
[    2.358023] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PSM] at 0x60,0x64 irq 1,12                                                                                                 
[    2.359532] serio: i8042 KBD port at 0x60,0x64 irq 1                                                                                                                             
[    2.359542] serio: i8042 AUX port at 0x60,0x64 irq 12                                                                                                                            
[    2.360063] mice: PS/2 mouse device common for all mice                                                                                                                          
[    2.372083] rtc_cmos 00:04: RTC can wake from S4                                                                                                                                 
[    2.372140] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0                                                                                                                
[    2.372165] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs                                                                                                        
[    2.372266] device-mapper: uevent: version 1.0.3                                                                                                                                 
[    2.372411] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]                                                                                     
[    2.372531] device-mapper: multipath: version 1.0.5 loaded                                                                                                                       
[    2.372537] device-mapper: multipath round-robin: version 1.0.0 loaded                                                                                                           
[    2.372658] EISA: Probing bus 0 at eisa.0                                                                                                                                        
[    2.372668] Cannot allocate resource for EISA slot 1                                                                                                                             
[    2.372672] Cannot allocate resource for EISA slot 2                                                                                                                             
[    2.372701] EISA: Detected 0 cards.                                                                                                                                              
[    2.372781] cpuidle: using governor ladder                                                                                                                                       
[    2.372786] cpuidle: using governor menu                                                                                                                                         
[    2.373556] TCP cubic registered                                                                                                                                                 
[    2.373645] NET: Registered protocol family 10                                                                                                                                   
[    2.374273] lo: Disabled Privacy Extensions                                                                                                                                      
[    2.374770] NET: Registered protocol family 17                                                                                                                                   
[    2.374799] Bluetooth: L2CAP ver 2.11                                                                                                                                            
[    2.374802] Bluetooth: L2CAP socket layer initialized                                                                                                                            
[    2.374806] Bluetooth: SCO (Voice Link) ver 0.6                                                                                                                                  
[    2.374809] Bluetooth: SCO socket layer initialized                                                                                                                              
[    2.374874] Bluetooth: RFCOMM socket layer initialized                                                                                                                           
[    2.374891] Bluetooth: RFCOMM TTY layer initialized                                                                                                                              
[    2.374896] Bluetooth: RFCOMM ver 1.10                                                                                                                                           
[    2.374973] Using IPI No-Shortcut mode                                                                                                                                           
[    2.375098] registered taskstats version 1                                                                                                                                       
[    2.375239]   Magic number: 1:377:438                                                                                                                                            
[    2.375336] rtc_cmos 00:04: setting system clock to 2009-07-04 16:26:30 UTC (1246724790)                                                                                         
[    2.375341] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found                                                                                                                 
[    2.375344] EDD information not available.                                                                                                                                       
[    2.375895] Freeing unused kernel memory: 532k freed                                                                                                                             
[    2.376114] Write protecting the kernel text: 4112k                                                                                                                              
[    2.376187] Write protecting the kernel read-only data: 1524k                                                                                                                    
[    2.397547] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3                                                                                   
[    2.669065] usb 1-7: new high speed USB device using ehci_hcd and address 2                                                                                                      
[    2.748755] Floppy drive(s): fd0 is 1.44M                                                                                                                                        
[    2.768161] FDC 0 is a post-1991 82077                                                                                                                                           
[    2.805779] usb 1-7: configuration #1 chosen from 1 choice                                                                                                                       
[    2.904991] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI                                                                                                                
[    2.904996] e100: Copyright(c) 1999-2006 Intel Corporation                                                                                                                       
[    2.905086] e100 0000:03:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20                                                                                                        
[    2.933918] e100 0000:03:08.0: PME# disabled                                                                                                                                     
[    2.947273] e100: eth0: e100_probe: addr 0xe8100000, irq 20, MAC addr 00:09:6b:d9:28:5a                                                                                          
[    3.362106] Initializing USB Mass Storage driver...                                                                                                                              
[    3.362417] scsi2 : SCSI emulation for USB Mass Storage devices                                                                                                                  
[    3.362959] usbcore: registered new interface driver usb-storage                                                                                                                 
[    3.362969] USB Mass Storage support registered.                                                                                                                                 
[    3.363351] usb-storage: device found at 2                                                                                                                                       
[    3.363360] usb-storage: waiting for device to settle before scanning                                                                                                            
[    3.445453] PM: Starting manual resume from disk                                                                                                                                 
[    3.445458] PM: Resume from partition 8:5                                                                                                                                        
[    3.445461] PM: Checking hibernation image.                                                                                                                                      
[    3.445644] PM: Resume from disk failed.                                                                                                                                         
[    3.479594] kjournald starting.  Commit interval 5 seconds                                                                                                                       
[    3.479613] EXT3-fs: mounted filesystem with ordered data mode.                                                                                                                  
[    8.360170] usb-storage: device scan complete                                                                                                                                    
[    8.476027] usb 1-7: reset high speed USB device using ehci_hcd and address 2                                                                                                    
[    8.609345] scsi 2:0:0:0: Direct-Access     Maxtor   OneTouch         0125 PQ: 0 ANSI: 4                                                                                         
[    8.610574] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)                                                                                              
[    8.724107] usb 1-7: reset high speed USB device using ehci_hcd and address 2                                                                                                    
[    8.857147] usb 1-7: device firmware changed                                                                                                                                     
[    8.857242] usb 1-7: USB disconnect, address 2                                                                                                                                   
[    8.857246] sd 2:0:0:0: [sdb] Write Protect is off                                                                                                                               
[    8.857250] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00                                                                                                                            
[    8.857254] sd 2:0:0:0: [sdb] Assuming drive cache: write through                                                                                                                
[    8.857684] sd 2:0:0:0: [sdb] READ CAPACITY failed                                                                                                                               
[    8.857688] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                                                                                    
[    8.857693] sd 2:0:0:0: [sdb] Sense not available.                                                                                                                               
[    8.857712] sd 2:0:0:0: [sdb] Write Protect is off                                                                                                                               
[    8.857715] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00                                                                                                                            
[    8.857718] sd 2:0:0:0: [sdb] Assuming drive cache: write through                                                                                                                
[    8.857724] sdb: detected capacity change from 500107862016 to 0                                                                                                                 
[    8.857809] sd 2:0:0:0: [sdb] Attached SCSI disk                                                                                                                                 
[    8.857881] sd 2:0:0:0: Attached scsi generic sg3 type 0                                                                                                                         
[    8.968026] usb 1-7: new high speed USB device using ehci_hcd and address 3                                                                                                      
[    9.101591] usb 1-7: configuration #1 chosen from 1 choice                                                                                                                       
[    9.101903] scsi3 : SCSI emulation for USB Mass Storage devices                                                                                                                  
[    9.102027] usb-storage: device found at 3                                                                                                                                       
[    9.102031] usb-storage: waiting for device to settle before scanning                                                                                                            
[    9.175454] udev: starting version 141                                                                                                                                           
[    9.369095] parport_pc 00:0d: reported by Plug and Play ACPI                                                                                                                     
[    9.369165] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]                                                                                    
[    9.452759] Linux agpgart interface v0.103                                                                                                                                       
[    9.602898] agpgart-intel 0000:00:00.0: Intel 865 Chipset                                                                                                                        
[    9.603191] agpgart-intel 0000:00:00.0: detected 8060K stolen memory                                                                                                             
[    9.605307] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000                                                                                                        
[    9.664259] intel_rng: Firmware space is locked read-only. If you can't or                                                                                                       
[    9.664263] intel_rng: don't want to disable this in firmware setup, and if                                                                                                      
[    9.664266] intel_rng: you are certain that your system has a functional                                                                                                         
[    9.664269] intel_rng: RNG, try using the 'no_fwh_detect' option.                                                                                                                
[    9.702465] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4                                                                                                         
[    9.912728] input: PC Speaker as /devices/platform/pcspkr/input/input4                                                                                                           
[   10.016548] ppdev: user-space parallel port driver                                                                                                                               
[   10.023851] iTCO_vendor_support: vendor-support=0                                                                                                                                
[   10.027147] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05                                                                                                                      
[   10.027410] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x1060)                                                                                               
[   10.027516] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)                                                                                                                 
[   10.108819] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume                                                                              
[   10.219848] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17                                                                                                   
[   10.219989] Intel ICH 0000:00:1f.5: setting latency timer to 64                                                                                                                  
[   10.633407] psmouse serio1: ID: 10 00 64<6>intel8x0_measure_ac97_clock: measured 54755 usecs                                                                                     
[   10.640017] intel8x0: clocking to 48000                                                                                                                                          
[   10.806127] lp0: using parport0 (interrupt-driven).                                                                                                                              
[   10.957117] Adding 1477940k swap on /dev/sda5.  Priority:-1 extents:1 across:1477940k                                                                                            
[   11.338984] input: ImExPS/2 Logitech MX Mouse as /devices/platform/i8042/serio1/input/input5                                                                                     
[   11.515784] EXT3 FS on sda1, internal journal                                                                                                                                    
[   12.738110] type=1505 audit(1246724800.861:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1956                                                    
[   12.738316] type=1505 audit(1246724800.861:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1956                                                          
[   12.738376] type=1505 audit(1246724800.861:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1956                            
[   12.738431] type=1505 audit(1246724800.861:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1956                                 
[   12.891617] type=1505 audit(1246724801.013:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1961                                           
[   12.891882] type=1505 audit(1246724801.013:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1961                                                          
[   12.928035] type=1505 audit(1246724801.049:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1965                                                        
[   14.101182] usb-storage: device scan complete                                                                                                                                    
[   14.217039] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   14.468036] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   14.597188] scsi 3:0:0:0: Direct-Access     Maxtor   OneTouch         0125 PQ: 0 ANSI: 4                                                                                         
[   14.599181] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)                                                                                              
[   14.599935] sd 3:0:0:0: [sdb] Write Protect is off                                                                                                                               
[   14.599945] sd 3:0:0:0: [sdb] Mode Sense: 2d 08 00 00                                                                                                                            
[   14.599949] sd 3:0:0:0: [sdb] Assuming drive cache: write through                                                                                                                
[   14.600804] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)                                                                                              
[   14.601586] sd 3:0:0:0: [sdb] Write Protect is off                                                                                                                               
[   14.601593] sd 3:0:0:0: [sdb] Mode Sense: 2d 08 00 00                                                                                                                            
[   14.601597] sd 3:0:0:0: [sdb] Assuming drive cache: write through                                                                                                                
[   14.601606]  sdb:<6>usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                            
[   14.964073] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   15.212027] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   15.460030] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   15.717039] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   15.911026] Bluetooth: BNEP (Ethernet Emulation) ver 1.3                                                                                                                         
[   15.911031] Bluetooth: BNEP filters: protocol multicast                                                                                                                          
[   15.932566] Bridge firewalling registered                                                                                                                                        
[   15.964029] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   16.096995] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK                                                                                         
[   16.097003] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[   16.097011] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[   16.212023] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   16.464030] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   16.712028] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   16.960022] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   17.208031] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   17.456040] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   17.588834] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK                                                                                         
[   17.588842] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[   17.588849] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[   17.704064] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   17.964033] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   18.208942] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   18.456734] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   18.732377] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   18.984037] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   19.116851] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK                                                                                         
[   19.116860] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[   19.116867] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[   19.236028] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   19.484063] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   19.732032] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   19.980032] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   20.228044] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   20.476025] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   20.608876] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK                                                                                         
[   20.608885] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[   20.608892] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[   20.724043] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   20.892973] ADDRCONF(NETDEV_UP): eth0: link is not ready                                                                                                                         
[   20.897129] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex                                                                                                             
[   20.897381] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready                                                                                                                    
[   20.972031] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   21.220031] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   21.468031] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   21.720032] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   21.968035] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   22.100775] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK                                                                                         
[   22.100784] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[   22.100791] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[   22.100812] ldm_validate_partition_table(): Disk read failed.                                                                                                                    
[   22.216034] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   22.464030] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   22.716031] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   22.964027] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   23.216034] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   23.464031] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   23.596795] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK                                                                                         
[   23.596805] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[   23.596811] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[   23.712038] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   23.960050] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   24.212084] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   24.464032] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   24.712222] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   24.960037] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   25.092951] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK                                                                                         
[   25.092960] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[   25.092969] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[   25.208070] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   25.456040] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   25.704047] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   25.952020] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   26.200020] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   26.448019] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   26.580845] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK                                                                                         
[   26.580854] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[   26.580862] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[   26.696019] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   26.948018] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   27.196020] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   27.329483] Dev sdb: unable to read RDB block 0                                                                                                                                  
[   27.444019] usb 1-7: reset high speed USB device using ehci_hcd and address 3                                                                                                    
[   27.577451]  unable to read partition table
[   27.577668] sd 3:0:0:0: [sdb] Attached SCSI disk
[   27.577856] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   27.716023] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[   27.964019] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[   28.212019] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[   28.460018] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[   28.708020] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[   28.956018] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[   29.088838] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[   29.088846] end_request: I/O error, dev sdb, sector 0
[   29.088854] Buffer I/O error on device sdb, logical block 0
[   29.088866] Buffer I/O error on device sdb, logical block 1
[   29.088873] Buffer I/O error on device sdb, logical block 2
[   29.088881] Buffer I/O error on device sdb, logical block 3
[   29.204019] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[   29.452017] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[   29.700021] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[   29.948019] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[   30.196020] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[   30.444020] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[   30.576860] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[   30.576869] end_request: I/O error, dev sdb, sector 0
[   30.576876] Buffer I/O error on device sdb, logical block 0
[   31.376013] eth0: no IPv6 routers present
[ 1486.124145] usb 1-7: USB disconnect, address 3
[ 1790.796058] usb 1-7: new high speed USB device using ehci_hcd and address 4
[ 1790.929597] usb 1-7: configuration #1 chosen from 1 choice
[ 1790.932912] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1790.933460] usb-storage: device found at 4
[ 1790.933467] usb-storage: waiting for device to settle before scanning
[ 1795.932251] usb-storage: device scan complete
[ 1795.934381] scsi 4:0:0:0: Direct-Access     Maxtor   OneTouch         0125 PQ: 0 ANSI: 4
[ 1795.935867] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 1795.936998] sd 4:0:0:0: [sdb] Write Protect is off
[ 1795.937064] sd 4:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[ 1795.937068] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1795.938614] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 1795.939520] sd 4:0:0:0: [sdb] Write Protect is off
[ 1795.939530] sd 4:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[ 1795.939535] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1795.939550]  sdb: sdb1
[ 1795.965352] sd 4:0:0:0: [sdb] Attached SCSI disk
[ 1795.965524] sd 4:0:0:0: Attached scsi generic sg3 type 0
[42880.988305] e100: eth0: e100_watchdog: link down
[48004.989153] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[116330.738747] usb 1-7: USB disconnect, address 4
[131967.953642] type=1505 audit(1246856764.298:9): operation="profile_replace" name="/sbin/dhclient-script" name2="default" pid=9240
[131967.954053] type=1505 audit(1246856764.298:10): operation="profile_replace" name="/sbin/dhclient3" name2="default" pid=9240
[131967.954126] type=1505 audit(1246856764.298:11): operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=9240
[131967.954188] type=1505 audit(1246856764.298:12): operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=9240
[131968.218280] type=1505 audit(1246856764.562:13): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=9245
[131968.218769] type=1505 audit(1246856764.562:14): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=9245
[131968.276343] type=1505 audit(1246856764.622:15): operation="profile_replace" name="/usr/sbin/tcpdump" name2="default" pid=9249
hawk@ltittletech:~$


anybody tell what this means

---

### Post by cariboo on 2009-07-07
It looks like you may have a problem with your external MAxtor One Touch, I don't see anything about an ipod in the listing.

Please use [noparse]```

```[/noparse] tags to make the output of long listings easier to read.

---

### Post by llamabr on 2009-07-07
Yes, here's the relevant bit:

```
[ 1795.934381] scsi 4:0:0:0: Direct-Access Maxtor OneTouch 0125 PQ: 0 ANSI: 4
[ 1795.935867] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 1795.936998] sd 4:0:0:0: [sdb] Write Protect is off
[ 1795.937064] sd 4:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[ 1795.937068] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1795.938614] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 1795.939520] sd 4:0:0:0: [sdb] Write Protect is off
[ 1795.939530] sd 4:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[ 1795.939535] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1795.939550] sdb: sdb1
[ 1795.965352] sd 4:0:0:0: [sdb] Attached SCSI disk
[ 1795.965524] sd 4:0:0:0: Attached scsi generic sg3 type 0
[42880.988305] e100: eth0: e100_watchdog: link down
[48004.989153] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[116330.738747] usb 1-7: USB disconnect, address 4
```

Unplug your ipod, wait a minute, plug it back in, and then post the last 15 or so lines of dmesg.  What model and generation are you using?

---

### Post by Mulenmar on 2009-07-07
I'm not entirely sure, but if you mean 3rd generation by "3g", that might be the generation when Apple started encrypting the iPod operating system, so only iTunes could access it. :mad:

Don't you just love proprietary technologies? ;)

---

### Post by abhiroopb on 2009-07-07
I have written a guide on how to connect the iPod Classic and (hopefully!) get it to work. Have a look: [http://ubuntuextreme.blogspot.com/2008/12/how-to-ipod-classic-6g-with-amarok-14_18.html](http://ubuntuextreme.blogspot.com/2008/12/how-to-ipod-classic-6g-with-amarok-14_18.html)

Also in the future please use a more descriptive title. Something like: iPod not connecting.

---

### Post by lisati on 2009-07-07
Whew! long post!

Suggestion for the OP: wrap what you "cut and paste" with [noparse]```
 
```[/noparse] tags e.g. 
```
[ 0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[ 0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.28-13-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 (Ubuntu 2.6.28-13.44-generic)
[ 0.000000] KERNEL supported cpus:
[ 0.000000] Intel GenuineIntel
[ 0.000000] AMD AuthenticAMD
[ 0.000000] NSC Geode by NSC
[ 0.000000] Cyrix CyrixInstead
[ 0.000000] Centaur CentaurHauls
[ 0.000000] Transmeta GenuineTMx86
[ 0.000000] Transmeta TransmetaCPU
[ 0.000000] UMC UMC UMC UMC
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[ 0.000000] BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000001f770000 (usable)
[ 0.000000] BIOS-e820: 000000001f770000 - 000000001f77a000 (ACPI data)
[ 0.000000] BIOS-e820: 000000001f77a000 - 000000001f780000 (ACPI NVS)
[ 0.000000] BIOS-e820: 000000001f780000 - 0000000020000000 (reserved)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[ 0.000000] DMI present.
[ 0.000000] last_pfn = 0x1f770 max_arch_pfn = 0x100000
[ 0.000000] Scanning 2 areas for low memory corruption
[ 0.000000] modified physical RAM map:
[ 0.000000] modified: 0000000000000000 - 0000000000002000 (usable)
[ 0.000000] modified: 0000000000002000 - 0000000000006000 (reserved)
[ 0.000000] modified: 0000000000006000 - 0000000000007000 (usable)
[ 0.000000] modified: 0000000000007000 - 0000000000010000 (reserved)
[ 0.000000] modified: 0000000000010000 - 0000000000092800 (usable)
[ 0.000000] modified: 000000000009f800 - 00000000000a0000 (reserved)
[ 0.000000] modified: 00000000000e0000 - 0000000000100000 (reserved)
[ 0.000000] modified: 0000000000100000 - 000000001f770000 (usable)
[ 0.000000] modified: 000000001f770000 - 000000001f77a000 (ACPI data)
[ 0.000000] modified: 000000001f77a000 - 000000001f780000 (ACPI NVS)
[ 0.000000] modified: 000000001f780000 - 0000000020000000 (reserved)
[ 0.000000] modified: 00000000fec00000 - 00000000fec10000 (reserved)
[ 0.000000] modified: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] modified: 00000000ff800000 - 0000000100000000 (reserved)
[ 0.000000] kernel direct mapping tables up to 1f770000 @ 10000-16000
[ 0.000000] RAMDISK: 1f02b000 - 1f75f2ac
[ 0.000000] ACPI: RSDP 000F64A0, 0014 (r0 PTLTD )
[ 0.000000] ACPI: RSDT 1F77509C, 0038 (r1 PTLTD RSDT 60400D0 LTP 0)
[ 0.000000] ACPI: FACP 1F779E93, 0074 (r1 IBM THINKCEN 60400D0 PTL 1)
[ 0.000000] ACPI: DSDT 1F7750D4, 4DBF (r1 IBM THINKCEN 60400D0 MSFT 100000E)
[ 0.000000] ACPI: FACS 1F77AFC0, 0040
[ 0.000000] ACPI: TCPA 1F779F07, 0032 (r1 IBM THINKCEN 60400D0 PTL 1)
[ 0.000000] ACPI: APIC 1F779F39, 0068 (r1 PTLTD APIC 60400D0 LTP 0)
[ 0.000000] ACPI: BOOT 1F779FA1, 0028 (r1 PTLTD $SBFTBL$ 60400D0 LTP 1)
[ 0.000000] ACPI: SSDT 1F779FC9, 0037 (r1 PTLTD ACPIHT 60400D0 LTP 1)
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] 0MB HIGHMEM available.
[ 0.000000] 503MB LOWMEM available.
[ 0.000000] mapped low ram: 0 - 1f770000
[ 0.000000] low ram: 00000000 - 1f770000
[ 0.000000] bootmap 00012000 - 00015ef0
[ 0.000000] (9 early reservations) ==> bootmem [0000000000 - 001f770000]
[ 0.000000] #0 [0000000000 - 0000001000] BIOS data page ==> [0000000000 - 0000001000]
[ 0.000000] #1 [0000001000 - 0000002000] EX TRAMPOLINE ==> [0000001000 - 0000002000]
[ 0.000000] #2 [0000006000 - 0000007000] TRAMPOLINE ==> [0000006000 - 0000007000]
[ 0.000000] #3 [0000100000 - 00008760ac] TEXT DATA BSS ==> [0000100000 - 00008760ac]
[ 0.000000] #4 [001f02b000 - 001f75f2ac] RAMDISK ==> [001f02b000 - 001f75f2ac]
[ 0.000000] #5 [0000877000 - 000087b000] INIT_PG_TABLE ==> [0000877000 - 000087b000]
[ 0.000000] #6 [000009f800 - 0000100000] BIOS reserved ==> [000009f800 - 0000100000]
[ 0.000000] #7 [0000010000 - 0000012000] PGTABLE ==> [0000010000 - 0000012000]
[ 0.000000] #8 [0000012000 - 0000016000] BOOTMAP ==> [0000012000 - 0000016000]
[ 0.000000] found SMP MP-table at [c00f63f0] 000f63f0
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0x00000000 -> 0x00001000
[ 0.000000] Normal 0x00001000 -> 0x0001f770
[ 0.000000] HighMem 0x0001f770 -> 0x0001f770
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[4] active PFN ranges
[ 0.000000] 0: 0x00000000 -> 0x00000002
[ 0.000000] 0: 0x00000006 -> 0x00000007
[ 0.000000] 0: 0x00000010 -> 0x00000092
[ 0.000000] 0: 0x00000100 -> 0x0001f770
[ 0.000000] On node 0 totalpages: 128757
[ 0.000000] free_area_init_node: node 0, pgdat c06c9500, node_mem_map c1000000
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 3941 pages, LIFO batch:0
[ 0.000000] Normal zone: 975 pages used for memmap
[ 0.000000] Normal zone: 123809 pages, LIFO batch:31
[ 0.000000] HighMem zone: 0 pages used for memmap
[ 0.000000] Movable zone: 0 pages used for memmap
[ 0.000000] ACPI: PM-Timer IO Port: 0x1008
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[ 0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[ 0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[ 0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[ 0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[ 0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[ 0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[ 0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[ 0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 127750
[ 0.000000] Kernel command line: root=UUID=00fa0420-aa93-4a4c-84d1-1eb7ebedb2a8 ro quiet splash
[ 0.000000] Enabling fast FPU save and restore... done.
[ 0.000000] Enabling unmasked SIMD FPU exception support... done.
[ 0.000000] Initializing CPU#0
[ 0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[ 0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[ 0.000000] Detected 2792.959 MHz processor.
[ 0.004000] Console: colour VGA+ 80x25
[ 0.004000] console [tty0] enabled
[ 0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.004000] allocated 2577600 bytes of page_cgroup
[ 0.004000] please try cgroup_disable=memory option if you don't want
[ 0.004000] Scanning for low memory corruption every 60 seconds
[ 0.004000] Memory: 492672k/515520k available (4110k kernel code, 22128k reserved, 2197k data, 532k init, 0k highmem)
[ 0.004000] virtual kernel memory layout:
[ 0.004000] fixmap : 0xffc77000 - 0xfffff000 (3616 kB)
[ 0.004000] pkmap : 0xff400000 - 0xff800000 (4096 kB)
[ 0.004000] vmalloc : 0xdff70000 - 0xff3fe000 ( 500 MB)
[ 0.004000] lowmem : 0xc0000000 - 0xdf770000 ( 503 MB)
[ 0.004000] .init : 0xc0731000 - 0xc07b6000 ( 532 kB)
[ 0.004000] .data : 0xc05039df - 0xc0728e60 (2197 kB)
[ 0.004000] .text : 0xc0100000 - 0xc05039df (4110 kB)
[ 0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[ 0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[ 0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 5585.91 BogoMIPS (lpj=11171836)
[ 0.004031] Security Framework initialized
[ 0.004039] SELinux: Disabled at boot.
[ 0.004058] AppArmor: AppArmor initialized
[ 0.004071] Mount-cache hash table entries: 512
[ 0.004230] Initializing cgroup subsys ns
[ 0.004235] Initializing cgroup subsys cpuacct
[ 0.004239] Initializing cgroup subsys memory
[ 0.004244] Initializing cgroup subsys freezer
[ 0.004262] CPU: Trace cache: 12K uops, L1 D cache: 8K
[ 0.004266] CPU: L2 cache: 512K
[ 0.004270] CPU: Physical Processor ID: 0
[ 0.004273] CPU: Processor Core ID: 0
[ 0.004288] Checking 'hlt' instruction... OK.
[ 0.023001] ACPI: Core revision 20080926
[ 0.026078] ACPI: Checking initramfs for custom DSDT
[ 0.333912] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 0.373770] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[ 0.376001] Booting processor 1 APIC 0x1 ip 0x6000
[ 0.004000] Initializing CPU#1
[ 0.004000] Calibrating delay using timer specific routine.. 5586.48 BogoMIPS (lpj=11172961)
[ 0.004000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[ 0.004000] CPU: L2 cache: 512K
[ 0.004000] CPU: Physical Processor ID: 0
[ 0.004000] CPU: Processor Core ID: 0
[ 0.460217] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[ 0.460242] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[ 0.464072] Brought up 2 CPUs
[ 0.464078] Total of 2 processors activated (11172.39 BogoMIPS).
[ 0.464130] CPU0 attaching sched-domain:
[ 0.464135] domain 0: span 0-1 level SIBLING
[ 0.464138] groups: 0 1
[ 0.464147] CPU1 attaching sched-domain:
[ 0.464151] domain 0: span 0-1 level SIBLING
[ 0.464154] groups: 1 0
[ 0.464256] net_namespace: 776 bytes
[ 0.464266] Booting paravirtualized kernel on bare hardware
[ 0.464518] Time: 16:26:28 Date: 07/04/09
[ 0.464518] regulator: core version 0.5
[ 0.464518] NET: Registered protocol family 16
[ 0.464518] EISA bus registered
[ 0.464518] ACPI: bus type pci registered
[ 0.464717] PCI: PCI BIOS revision 2.10 entry at 0xfd98d, last bus=3
[ 0.464721] PCI: Using configuration type 1 for base access
[ 0.468306] ACPI: EC: Look up EC in DSDT
[ 0.489037] ACPI: Interpreter enabled
[ 0.489044] ACPI: (supports S0 S1 S3 S4 S5)
[ 0.489074] ACPI: Using IOAPIC for interrupt routing
[ 0.522350] ACPI: No dock devices found.
[ 0.522367] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 0.522427] pci 0000:00:00.0: reg 10 32bit mmio: [0xec000000-0xefffffff]
[ 0.522489] pci 0000:00:02.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[ 0.522497] pci 0000:00:02.0: reg 14 32bit mmio: [0xe8000000-0xe807ffff]
[ 0.522503] pci 0000:00:02.0: reg 18 io port: [0x1800-0x1807]
[ 0.522600] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[ 0.522655] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[ 0.522709] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[ 0.522763] pci 0000:00:1d.3: reg 20 io port: [0x1880-0x189f]
[ 0.522826] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe8080000-0xe80803ff]
[ 0.522873] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[ 0.522879] pci 0000:00:1d.7: PME# disabled
[ 0.522969] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[ 0.522976] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[ 0.522981] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[ 0.523003] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[ 0.523011] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[ 0.523018] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[ 0.523026] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[ 0.523034] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[ 0.523042] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[ 0.523094] pci 0000:00:1f.3: reg 20 io port: [0x18a0-0x18bf]
[ 0.523138] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[ 0.523145] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
[ 0.523153] pci 0000:00:1f.5: reg 18 32bit mmio: [0xe8080c00-0xe8080dff]
[ 0.523160] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xe8080800-0xe80808ff]
[ 0.523184] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[ 0.523189] pci 0000:00:1f.5: PME# disabled
[ 0.524027] pci 0000:03:08.0: reg 10 32bit mmio: [0xe8100000-0xe8100fff]
[ 0.524035] pci 0000:03:08.0: reg 14 io port: [0x2000-0x203f]
[ 0.524067] pci 0000:03:08.0: supports D1 D2
[ 0.524070] pci 0000:03:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.524075] pci 0000:03:08.0: PME# disabled
[ 0.524110] pci 0000:03:0a.0: reg 10 32bit mmio: [0xe8400000-0xe87fffff]
[ 0.524150] pci 0000:03:0a.0: supports D2
[ 0.524152] pci 0000:03:0a.0: PME# supported from D2 D3hot D3cold
[ 0.524157] pci 0000:03:0a.0: PME# disabled
[ 0.524190] pci 0000:00:1e.0: transparent bridge
[ 0.524195] pci 0000:00:1e.0: bridge io port: [0x2000-0x2fff]
[ 0.524201] pci 0000:00:1e.0: bridge 32bit mmio: [0xe8100000-0xe87fffff]
[ 0.524213] bus 00 -> node 0
[ 0.524221] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 0.524492] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SLOT._PRT]
[ 0.622009] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[ 0.622162] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[ 0.622312] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[ 0.622461] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[ 0.622620] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[ 0.622777] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[ 0.622938] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[ 0.623097] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 9 10 11 12 14 15)
[ 0.623312] ACPI: WMI: Mapper loaded
[ 0.623411] SCSI subsystem initialized
[ 0.623411] libata version 3.00 loaded.
[ 0.623411] usbcore: registered new interface driver usbfs
[ 0.623411] usbcore: registered new interface driver hub
[ 0.623411] usbcore: registered new device driver usb
[ 0.624029] PCI: Using ACPI for IRQ routing
[ 0.628015] Bluetooth: Core ver 2.13
[ 0.628043] NET: Registered protocol family 31
[ 0.628043] Bluetooth: HCI device and connection manager initialized
[ 0.628043] Bluetooth: HCI socket layer initialized
[ 0.628043] NET: Registered protocol family 8
[ 0.628043] NET: Registered protocol family 20
[ 0.628054] NetLabel: Initializing
[ 0.628057] NetLabel: domain hash size = 128
[ 0.628060] NetLabel: protocols = UNLABELED CIPSOv4
[ 0.628077] NetLabel: unlabeled traffic allowed by default
[ 0.628185] hpet clockevent registered
[ 0.628190] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[ 0.628196] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[ 0.628203] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[ 0.632106] AppArmor: AppArmor Filesystem Enabled
[ 0.640014] pnp: PnP ACPI init
[ 0.640031] ACPI: bus type pnp registered
[ 0.676491] pnp: PnP ACPI: found 14 devices
[ 0.676497] ACPI: ACPI bus type pnp unregistered
[ 0.676502] PnPBIOS: Disabled by ACPI PNP
[ 0.676528] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[ 0.676532] system 00:01: ioport range 0x800-0x87f has been reserved
[ 0.676535] system 00:01: ioport range 0x1000-0x107f has been reserved
[ 0.676539] system 00:01: ioport range 0x1100-0x111f has been reserved
[ 0.676542] system 00:01: ioport range 0x1180-0x11bf has been reserved
[ 0.676547] system 00:01: ioport range 0xe000-0xe00f has been reserved
[ 0.676550] system 00:01: ioport range 0xfe00-0xfe00 has been reserved
[ 0.676554] system 00:01: ioport range 0xfe10-0xfe11 has been reserved
[ 0.676559] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[ 0.676563] system 00:01: iomem range 0xfed90000-0xfed903ff has been reserved
[ 0.711362] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[ 0.711367] pci 0000:00:1e.0: IO window: 0x2000-0x2fff
[ 0.711373] pci 0000:00:1e.0: MEM window: 0xe8100000-0xe87fffff
[ 0.711378] pci 0000:00:1e.0: PREFETCH window: disabled
[ 0.711394] pci 0000:00:1e.0: setting latency timer to 64
[ 0.711400] bus: 00 index 0 io port: [0x00-0xffff]
[ 0.711403] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[ 0.711406] bus: 03 index 0 io port: [0x2000-0x2fff]
[ 0.711409] bus: 03 index 1 mmio: [0xe8100000-0xe87fffff]
[ 0.711411] bus: 03 index 2 mmio: [0x0-0x0]
[ 0.711414] bus: 03 index 3 io port: [0x00-0xffff]
[ 0.711417] bus: 03 index 4 mmio: [0x000000-0xffffffff]
[ 0.711429] NET: Registered protocol family 2
[ 0.724085] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[ 0.724396] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[ 0.724451] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[ 0.724508] TCP: Hash tables configured (established 16384 bind 16384)
[ 0.724511] TCP reno registered
[ 0.732100] NET: Registered protocol family 1
[ 0.732257] checking if image is initramfs... it is
[ 1.128361] Switched to high resolution mode on CPU 1
[ 1.132044] Switched to high resolution mode on CPU 0
[ 1.360465] Freeing initrd memory: 7376k freed
[ 1.360516] Simple Boot Flag at 0x35 set to 0x1
[ 1.360553] cpufreq: No nForce2 chipset.
[ 1.360746] audit: initializing netlink socket (disabled)
[ 1.360769] type=2000 audit(1246724788.357:1): initialized
[ 1.367442] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[ 1.369124] VFS: Disk quotas dquot_6.5.1
[ 1.369212] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 1.370049] fuse init (API version 7.10)
[ 1.370159] msgmni has been set to 977
[ 1.370635] alg: No test for stdrng (krng)
[ 1.370659] io scheduler noop registered
[ 1.370664] io scheduler anticipatory registered
[ 1.370668] io scheduler deadline registered
[ 1.370699] io scheduler cfq registered (default)
[ 1.370717] pci 0000:00:02.0: Boot video device
[ 1.370931] pci 0000:03:08.0: Firmware left e100 interrupts enabled; disabling
[ 1.393506] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 1.393519] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 1.393698] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[ 1.393702] ACPI: Power Button (FF) [PWRF]
[ 1.393778] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0C:00/input/input1
[ 1.393782] ACPI: Power Button (CM) [PWRB]
[ 1.394027] processor ACPI_CPU:00: registered as cooling_device0
[ 1.394033] ACPI: Processor [CPU0] (supports 8 throttling states)
[ 1.394160] processor ACPI_CPU:01: registered as cooling_device1
[ 1.394166] ACPI: Processor [CPU1] (supports 8 throttling states)
[ 1.415548] thermal LNXTHERM:01: registered as thermal_zone0
[ 1.416438] ACPI: Thermal Zone [THM0] (62 C)
[ 1.416540] isapnp: Scanning for PnP cards...
[ 1.770321] isapnp: No Plug & Play device found
[ 1.777187] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[ 1.777286] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1.777750] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1.778770] brd: module loaded
[ 1.779220] loop: module loaded
[ 1.779323] Fixed MDIO Bus: probed
[ 1.779331] PPP generic driver version 2.4.2
[ 1.779414] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[ 1.779459] Driver 'sd' needs updating - please use bus_type methods
[ 1.779473] Driver 'sr' needs updating - please use bus_type methods
[ 1.779573] ata_piix 0000:00:1f.1: version 2.12
[ 1.779586] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[ 1.779599] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1.779655] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 1.779809] scsi0 : ata_piix
[ 1.779953] scsi1 : ata_piix
[ 1.781405] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[ 1.781409] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[ 1.968273] ata1.00: HPA unlocked: 151440515 -> 156312576, native 156312576
[ 1.968279] ata1.00: ATA-6: IC35L090AVV207-0, V23OA66A, max UDMA/100
[ 1.968282] ata1.00: 156312576 sectors, multi 16: LBA48
[ 1.992437] ata1.00: configured for UDMA/100
[ 2.268653] ata2.00: ATAPI: LTN486S, YUS6, max UDMA/33, CDB intr
[ 2.268690] ata2.01: ATAPI: LITE-ON DVDRW SOHW-1693S, KS06, max UDMA/66
[ 2.276375] ata2.00: configured for UDMA/33
[ 2.292234] ata2.01: configured for UDMA/66
[ 2.293043] scsi 0:0:0:0: Direct-Access ATA IC35L090AVV207-0 V23O PQ: 0 ANSI: 5
[ 2.293188] sd 0:0:0:0: [sda] 156312576 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2.293211] sd 0:0:0:0: [sda] Write Protect is off
[ 2.293215] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2.293252] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2.293349] sd 0:0:0:0: [sda] 156312576 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2.293370] sd 0:0:0:0: [sda] Write Protect is off
[ 2.293374] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2.293410] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2.293415] sda: sda1 sda2 < sda5 >
[ 2.330721] sd 0:0:0:0: [sda] Attached SCSI disk
[ 2.330797] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 2.331111] scsi 1:0:0:0: CD-ROM LITEON CD-ROM LTN486S YUS6 PQ: 0 ANSI: 5
[ 2.333901] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[ 2.333905] Uniform CD-ROM driver Revision: 3.20
[ 2.334051] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 2.334115] sr 1:0:0:0: Attached scsi generic sg1 type 5
[ 2.334901] scsi 1:0:1:0: CD-ROM LITE-ON DVDRW SOHW-1693S KS06 PQ: 0 ANSI: 5
[ 2.338567] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[ 2.338656] sr 1:0:1:0: Attached scsi CD-ROM sr1
[ 2.338712] sr 1:0:1:0: Attached scsi generic sg2 type 5
[ 2.339579] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 2.339614] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[ 2.339650] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 2.339655] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 2.339749] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[ 2.343668] ehci_hcd 0000:00:1d.7: debug port 1
[ 2.343677] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[ 2.343701] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe8080000
[ 2.356044] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[ 2.356182] usb usb1: configuration #1 chosen from 1 choice
[ 2.356221] hub 1-0:1.0: USB hub found
[ 2.356237] hub 1-0:1.0: 8 ports detected
[ 2.356422] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 2.356455] uhci_hcd: USB Universal Host Controller Interface driver
[ 2.356512] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2.356522] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 2.356526] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 2.356592] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[ 2.356627] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001820
[ 2.356723] usb usb2: configuration #1 chosen from 1 choice
[ 2.356761] hub 2-0:1.0: USB hub found
[ 2.356771] hub 2-0:1.0: 2 ports detected
[ 2.356884] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 2.356891] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 2.356896] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 2.356954] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[ 2.356984] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[ 2.357089] usb usb3: configuration #1 chosen from 1 choice
[ 2.357123] hub 3-0:1.0: USB hub found
[ 2.357132] hub 3-0:1.0: 2 ports detected
[ 2.357244] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 2.357252] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 2.357256] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 2.357317] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[ 2.357347] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[ 2.357441] usb usb4: configuration #1 chosen from 1 choice
[ 2.357475] hub 4-0:1.0: USB hub found
[ 2.357485] hub 4-0:1.0: 2 ports detected
[ 2.357595] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2.357602] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 2.357606] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[ 2.357672] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[ 2.357693] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[ 2.357790] usb usb5: configuration #1 chosen from 1 choice
[ 2.357830] hub 5-0:1.0: USB hub found
[ 2.357840] hub 5-0:1.0: 2 ports detected
[ 2.358023] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13SM] at 0x60,0x64 irq 1,12
[ 2.359532] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 2.359542] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 2.360063] mice: PS/2 mouse device common for all mice
[ 2.372083] rtc_cmos 00:04: RTC can wake from S4
[ 2.372140] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[ 2.372165] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[ 2.372266] device-mapper: uevent: version 1.0.3
[ 2.372411] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[ 2.372531] device-mapper: multipath: version 1.0.5 loaded
[ 2.372537] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 2.372658] EISA: Probing bus 0 at eisa.0
[ 2.372668] Cannot allocate resource for EISA slot 1
[ 2.372672] Cannot allocate resource for EISA slot 2
[ 2.372701] EISA: Detected 0 cards.
[ 2.372781] cpuidle: using governor ladder
[ 2.372786] cpuidle: using governor menu
[ 2.373556] TCP cubic registered
[ 2.373645] NET: Registered protocol family 10
[ 2.374273] lo: Disabled Privacy Extensions
[ 2.374770] NET: Registered protocol family 17
[ 2.374799] Bluetooth: L2CAP ver 2.11
[ 2.374802] Bluetooth: L2CAP socket layer initialized
[ 2.374806] Bluetooth: SCO (Voice Link) ver 0.6
[ 2.374809] Bluetooth: SCO socket layer initialized
[ 2.374874] Bluetooth: RFCOMM socket layer initialized
[ 2.374891] Bluetooth: RFCOMM TTY layer initialized
[ 2.374896] Bluetooth: RFCOMM ver 1.10
[ 2.374973] Using IPI No-Shortcut mode
[ 2.375098] registered taskstats version 1
[ 2.375239] Magic number: 1:377:438
[ 2.375336] rtc_cmos 00:04: setting system clock to 2009-07-04 16:26:30 UTC (1246724790)
[ 2.375341] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 2.375344] EDD information not available.
[ 2.375895] Freeing unused kernel memory: 532k freed
[ 2.376114] Write protecting the kernel text: 4112k
[ 2.376187] Write protecting the kernel read-only data: 1524k
[ 2.397547] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[ 2.669065] usb 1-7: new high speed USB device using ehci_hcd and address 2
[ 2.748755] Floppy drive(s): fd0 is 1.44M
[ 2.768161] FDC 0 is a post-1991 82077
[ 2.805779] usb 1-7: configuration #1 chosen from 1 choice
[ 2.904991] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[ 2.904996] e100: Copyright(c) 1999-2006 Intel Corporation
[ 2.905086] e100 0000:03:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 2.933918] e100 0000:03:08.0: PME# disabled
[ 2.947273] e100: eth0: e100_probe: addr 0xe8100000, irq 20, MAC addr 00:09:6b:d9:28:5a
[ 3.362106] Initializing USB Mass Storage driver...
[ 3.362417] scsi2 : SCSI emulation for USB Mass Storage devices
[ 3.362959] usbcore: registered new interface driver usb-storage
[ 3.362969] USB Mass Storage support registered.
[ 3.363351] usb-storage: device found at 2
[ 3.363360] usb-storage: waiting for device to settle before scanning
[ 3.445453] PM: Starting manual resume from disk
[ 3.445458] PM: Resume from partition 8:5
[ 3.445461] PM: Checking hibernation image.
[ 3.445644] PM: Resume from disk failed.
[ 3.479594] kjournald starting. Commit interval 5 seconds
[ 3.479613] EXT3-fs: mounted filesystem with ordered data mode.
[ 8.360170] usb-storage: device scan complete
[ 8.476027] usb 1-7: reset high speed USB device using ehci_hcd and address 2
[ 8.609345] scsi 2:0:0:0: Direct-Access Maxtor OneTouch 0125 PQ: 0 ANSI: 4
[ 8.610574] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 8.724107] usb 1-7: reset high speed USB device using ehci_hcd and address 2
[ 8.857147] usb 1-7: device firmware changed
[ 8.857242] usb 1-7: USB disconnect, address 2
[ 8.857246] sd 2:0:0:0: [sdb] Write Protect is off
[ 8.857250] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 8.857254] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 8.857684] sd 2:0:0:0: [sdb] READ CAPACITY failed
[ 8.857688] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 8.857693] sd 2:0:0:0: [sdb] Sense not available.
[ 8.857712] sd 2:0:0:0: [sdb] Write Protect is off
[ 8.857715] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 8.857718] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 8.857724] sdb: detected capacity change from 500107862016 to 0
[ 8.857809] sd 2:0:0:0: [sdb] Attached SCSI disk
[ 8.857881] sd 2:0:0:0: Attached scsi generic sg3 type 0
[ 8.968026] usb 1-7: new high speed USB device using ehci_hcd and address 3
[ 9.101591] usb 1-7: configuration #1 chosen from 1 choice
[ 9.101903] scsi3 : SCSI emulation for USB Mass Storage devices
[ 9.102027] usb-storage: device found at 3
[ 9.102031] usb-storage: waiting for device to settle before scanning
[ 9.175454] udev: starting version 141
[ 9.369095] parport_pc 00:0d: reported by Plug and Play ACPI
[ 9.369165] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[ 9.452759] Linux agpgart interface v0.103
[ 9.602898] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[ 9.603191] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[ 9.605307] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[ 9.664259] intel_rng: Firmware space is locked read-only. If you can't or
[ 9.664263] intel_rng: don't want to disable this in firmware setup, and if
[ 9.664266] intel_rng: you are certain that your system has a functional
[ 9.664269] intel_rng: RNG, try using the 'no_fwh_detect' option.
[ 9.702465] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 9.912728] input: PC Speaker as /devices/platform/pcspkr/input/input4
[ 10.016548] ppdev: user-space parallel port driver
[ 10.023851] iTCO_vendor_support: vendor-support=0
[ 10.027147] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[ 10.027410] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x1060)
[ 10.027516] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[ 10.108819] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[ 10.219848] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 10.219989] Intel ICH 0000:00:1f.5: setting latency timer to 64
[ 10.633407] psmouse serio1: ID: 10 00 64<6>intel8x0_measure_ac97_clock: measured 54755 usecs
[ 10.640017] intel8x0: clocking to 48000
[ 10.806127] lp0: using parport0 (interrupt-driven).
[ 10.957117] Adding 1477940k swap on /dev/sda5. Priority:-1 extents:1 across:1477940k
[ 11.338984] input: ImExPS/2 Logitech MX Mouse as /devices/platform/i8042/serio1/input/input5
[ 11.515784] EXT3 FS on sda1, internal journal
[ 12.738110] type=1505 audit(1246724800.861:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1956
[ 12.738316] type=1505 audit(1246724800.861:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1956
[ 12.738376] type=1505 audit(1246724800.861:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1956
[ 12.738431] type=1505 audit(1246724800.861:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1956
[ 12.891617] type=1505 audit(1246724801.013:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1961
[ 12.891882] type=1505 audit(1246724801.013:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1961
[ 12.928035] type=1505 audit(1246724801.049:: operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1965
[ 14.101182] usb-storage: device scan complete
[ 14.217039] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 14.468036] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 14.597188] scsi 3:0:0:0: Direct-Access Maxtor OneTouch 0125 PQ: 0 ANSI: 4
[ 14.599181] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 14.599935] sd 3:0:0:0: [sdb] Write Protect is off
[ 14.599945] sd 3:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[ 14.599949] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 14.600804] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 14.601586] sd 3:0:0:0: [sdb] Write Protect is off
[ 14.601593] sd 3:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[ 14.601597] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 14.601606] sdb:<6>usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 14.964073] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 15.212027] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 15.460030] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 15.717039] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 15.911026] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 15.911031] Bluetooth: BNEP filters: protocol multicast
[ 15.932566] Bridge firewalling registered
[ 15.964029] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 16.096995] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 16.097003] end_request: I/O error, dev sdb, sector 0
[ 16.097011] Buffer I/O error on device sdb, logical block 0
[ 16.212023] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 16.464030] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 16.712028] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 16.960022] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 17.208031] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 17.456040] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 17.588834] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 17.588842] end_request: I/O error, dev sdb, sector 0
[ 17.588849] Buffer I/O error on device sdb, logical block 0
[ 17.704064] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 17.964033] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 18.208942] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 18.456734] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 18.732377] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 18.984037] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 19.116851] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 19.116860] end_request: I/O error, dev sdb, sector 0
[ 19.116867] Buffer I/O error on device sdb, logical block 0
[ 19.236028] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 19.484063] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 19.732032] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 19.980032] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 20.228044] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 20.476025] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 20.608876] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 20.608885] end_request: I/O error, dev sdb, sector 0
[ 20.608892] Buffer I/O error on device sdb, logical block 0
[ 20.724043] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 20.892973] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 20.897129] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 20.897381] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 20.972031] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 21.220031] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 21.468031] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 21.720032] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 21.968035] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 22.100775] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 22.100784] end_request: I/O error, dev sdb, sector 0
[ 22.100791] Buffer I/O error on device sdb, logical block 0
[ 22.100812] ldm_validate_partition_table(): Disk read failed.
[ 22.216034] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 22.464030] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 22.716031] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 22.964027] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 23.216034] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 23.464031] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 23.596795] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 23.596805] end_request: I/O error, dev sdb, sector 0
[ 23.596811] Buffer I/O error on device sdb, logical block 0
[ 23.712038] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 23.960050] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 24.212084] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 24.464032] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 24.712222] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 24.960037] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 25.092951] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 25.092960] end_request: I/O error, dev sdb, sector 0
[ 25.092969] Buffer I/O error on device sdb, logical block 0
[ 25.208070] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 25.456040] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 25.704047] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 25.952020] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 26.200020] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 26.448019] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 26.580845] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 26.580854] end_request: I/O error, dev sdb, sector 0
[ 26.580862] Buffer I/O error on device sdb, logical block 0
[ 26.696019] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 26.948018] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 27.196020] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 27.329483] Dev sdb: unable to read RDB block 0
[ 27.444019] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 27.577451] unable to read partition table
[ 27.577668] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 27.577856] sd 3:0:0:0: Attached scsi generic sg3 type 0
[ 27.716023] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 27.964019] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 28.212019] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 28.460018] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 28.708020] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 28.956018] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 29.088838] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 29.088846] end_request: I/O error, dev sdb, sector 0
[ 29.088854] Buffer I/O error on device sdb, logical block 0
[ 29.088866] Buffer I/O error on device sdb, logical block 1
[ 29.088873] Buffer I/O error on device sdb, logical block 2
[ 29.088881] Buffer I/O error on device sdb, logical block 3
[ 29.204019] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 29.452017] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 29.700021] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 29.948019] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 30.196020] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 30.444020] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 30.576860] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 30.576869] end_request: I/O error, dev sdb, sector 0
[ 30.576876] Buffer I/O error on device sdb, logical block 0
[ 31.376013] eth0: no IPv6 routers present
[ 1486.124145] usb 1-7: USB disconnect, address 3
[ 1790.796058] usb 1-7: new high speed USB device using ehci_hcd and address 4
[ 1790.929597] usb 1-7: configuration #1 chosen from 1 choice
[ 1790.932912] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1790.933460] usb-storage: device found at 4
[ 1790.933467] usb-storage: waiting for device to settle before scanning
[ 1795.932251] usb-storage: device scan complete
[ 1795.934381] scsi 4:0:0:0: Direct-Access Maxtor OneTouch 0125 PQ: 0 ANSI: 4
[ 1795.935867] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 1795.936998] sd 4:0:0:0: [sdb] Write Protect is off
[ 1795.937064] sd 4:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[ 1795.937068] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1795.938614] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 1795.939520] sd 4:0:0:0: [sdb] Write Protect is off
[ 1795.939530] sd 4:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[ 1795.939535] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1795.939550] sdb: sdb1
[ 1795.965352] sd 4:0:0:0: [sdb] Attached SCSI disk
[ 1795.965524] sd 4:0:0:0: Attached scsi generic sg3 type 0
[42880.988305] e100: eth0: e100_watchdog: link down
[48004.989153] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[116330.738747] usb 1-7: USB disconnect, address 4
[131967.953642] type=1505 audit(1246856764.298:9): operation="profile_replace" name="/sbin/dhclient-script" name2="default" pid=9240
[131967.954053] type=1505 audit(1246856764.298:10): operation="profile_replace" name="/sbin/dhclient3" name2="default" pid=9240
[131967.954126] type=1505 audit(1246856764.298:11): operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=9240
[131967.954188] type=1505 audit(1246856764.298:12): operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=9240
[131968.218280] type=1505 audit(1246856764.562:13): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=9245
[131968.218769] type=1505 audit(1246856764.562:14): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=9245
[131968.276343] type=1505 audit(1246856764.622:15): operation="profile_replace" name="/usr/sbin/tcpdump" name2="default" pid=9249

```

---

