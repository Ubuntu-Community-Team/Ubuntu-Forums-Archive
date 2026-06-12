---
title: "Wireless card not listed in lshw (Broadcom)"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by MewRS on 2008-11-10
Hi you all..

I'm getting nervous with my wireless card...
It's been two weeks since I tried to discard Windows and use only Kubuntu Intrepid...

There is the problem: the wireless card was working fine until I updated some packages...

Then I formated the HD and got a fresh install again...
But now my Kubuntu just doesn't detect the wireless card...

This is my **lspci**.

```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)        
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) 
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) 
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)                                                                            
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)               
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)                
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)                          
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)                     
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)        
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)        
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)                    
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)  
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)                
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)   
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)           
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration                                                 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map                                                                             
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller                                                                         
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control                                                                   
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller          
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)                                                                      
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)     
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)                                                                           
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)     
rafajaques@deviant:~$ sudo lshw
deviant                        
    description: Notebook      
    product: HP Pavilion dv9000 (RU975UA#ABA)
    vendor: Hewlett-Packard                  
    version: Rev 1                           
    serial: CNF712071T                       
    width: 32 bits                           
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 uuid=434E4637-3132-3037-3154-001B2410FC65                                                          
  *-core                                                                        
       description: Motherboard                                                 
       product: 30B9                                                            
       vendor: Quanta                                                           
       physical id: 0                                                           
       version: 65.28                                                           
       serial: None                                                             
       slot: &#65533;&#65533;@                                                                
     *-firmware                                                                 
          description: BIOS                                                     
          vendor: Hewlett-Packard                                               
          physical id: 0                                                        
          version: F.3A (07/19/2007)                                            
          size: 101KiB                                                          
          capacity: 960KiB                                                      
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification                                                              
     *-cpu:0                                                                    
          description: CPU                                                      
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-52                 
          vendor: Advanced Micro Devices [AMD]                                  
          physical id: 4                                                        
          bus info: cpu@0                                                       
          version: 15.8.2                                                       
          slot: Socket S1                                                       
          size: 1600MHz                                                         
          capacity: 1600MHz                                                     
          width: 64 bits                                                        
          clock: 200MHz                                                         
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq                                                           
        *-cache:0                                                               
             description: L1 cache                                              
             physical id: 5                                                     
             slot: L1 Cache                                                     
             size: 128KiB                                                       
             capabilities: asynchronous internal write-back                     
        *-cache:1                                                               
             description: L2 cache                                              
             physical id: 6                                                     
             slot: L2 Cache                                                     
             size: 512KiB                                                       
             capacity: 1MiB                                                     
             capabilities: synchronous internal write-through unified           
     *-memory:0                                                                 
          description: System Memory                                            
          physical id: c                                                        
          slot: System board or motherboard                                     
          size: 2GiB                                                            
          capacity: 2GiB                                                        
        *-bank:0                                                                
             description: DIMM Synchronous 533 MHz (1.9 ns)                     
             vendor: F789000000000000                                           
             physical id: 0                                                     
             serial: 76B0E182                                                   
             slot: DIMM 1                                                       
             size: 1GiB                                                         
             width: 64 bits                                                     
             clock: 533MHz (1.9ns)                                              
        *-bank:1                                                                
             description: DIMM 533 MHz (1.9 ns)                                 
             vendor: F789000000000000                                           
             physical id: 1                                                     
             serial: 565329B1                                                   
             slot: DIMM 2                                                       
             size: 1GiB                                                         
             width: 64 bits                                                     
             clock: 533MHz (1.9ns)                                              
     *-cpu:1                                                                    
          physical id: 1                                                        
          bus info: cpu@1                                                       
          version: 15.8.2                                                       
          size: 1600MHz                                                         
          capacity: 1600MHz                                                     
          capabilities: cpufreq                                                 
        *-cache:0                                                               
             description: L1 cache                                              
             physical id: 0                                                     
             size: 128KiB                                                       
        *-cache:1                                                               
             description: L2 cache                                              
             physical id: 1                                                     
             size: 512KiB                                                       
     *-memory:1 UNCLAIMED                                                       
          description: RAM memory                                               
          product: C51 Host Bridge                                              
          vendor: nVidia Corporation                                            
          physical id: 6                                                        
          bus info: pci@0000:00:00.0                                            
          version: a2                                                           
          width: 32 bits                                                        
          clock: 66MHz (15.2ns)                                                 
          capabilities: ht bus_master cap_list                                  
          configuration: latency=0                                              
     *-memory:2 UNCLAIMED                                                       
          description: RAM memory                                               
          product: C51 Memory Controller 0                                      
          vendor: nVidia Corporation                                            
          physical id: 0.1                                                      
          bus info: pci@0000:00:00.1                                            
          version: a2                                                           
          width: 32 bits                                                        
          clock: 66MHz (15.2ns)                                                 
          configuration: latency=0                                              
     *-memory:3 UNCLAIMED                                                       
          description: RAM memory                                               
          product: C51 Memory Controller 1                                      
          vendor: nVidia Corporation                                            
          physical id: 0.2                                                      
          bus info: pci@0000:00:00.2                                            
          version: a2                                                           
          width: 32 bits                                                        
          clock: 66MHz (15.2ns)                                                 
          configuration: latency=0                                              
     *-memory:4 UNCLAIMED                                                       
          description: RAM memory                                               
          product: C51 Memory Controller 5                                      
          vendor: nVidia Corporation                                            
          physical id: 0.3                                                      
          bus info: pci@0000:00:00.3                                            
          version: a2                                                           
          width: 32 bits                                                        
          clock: 66MHz (15.2ns)                                                 
          configuration: latency=0                                              
     *-memory:5 UNCLAIMED                                                       
          description: RAM memory                                               
          product: C51 Memory Controller 4                                      
          vendor: nVidia Corporation                                            
          physical id: 0.4                                                      
          bus info: pci@0000:00:00.4                                            
          version: a2                                                           
          width: 32 bits                                                        
          clock: 66MHz (15.2ns)                                                 
          capabilities: bus_master                                              
          configuration: latency=0                                              
     *-memory:6 UNCLAIMED                                                       
          description: RAM memory                                               
          product: C51 Host Bridge                                              
          vendor: nVidia Corporation                                            
          physical id: 0.5                                                      
          bus info: pci@0000:00:00.5                                            
          version: a2                                                           
          width: 32 bits                                                        
          clock: 66MHz (15.2ns)                                                 
          capabilities: bus_master cap_list                                     
          configuration: latency=0                                              
     *-memory:7 UNCLAIMED                                                       
          description: RAM memory                                               
          product: C51 Memory Controller 3                                      
          vendor: nVidia Corporation                                            
          physical id: 0.6                                                      
          bus info: pci@0000:00:00.6                                            
          version: a2                                                           
          width: 32 bits                                                        
          clock: 66MHz (15.2ns)                                                 
          configuration: latency=0                                              
     *-memory:8 UNCLAIMED                                                       
          description: RAM memory                                               
          product: C51 Memory Controller 2                                      
          vendor: nVidia Corporation                                            
          physical id: 0.7                                                      
          bus info: pci@0000:00:00.7                                            
          version: a2                                                           
          width: 32 bits                                                        
          clock: 66MHz (15.2ns)                                                 
          configuration: latency=0                                              
     *-pci:0                                                                    
          description: PCI bridge                                               
          product: C51 PCI Express Bridge                                       
          vendor: nVidia Corporation                                            
          physical id: 2                                                        
          bus info: pci@0000:00:02.0                                            
          version: a1                                                           
          width: 32 bits                                                        
          clock: 33MHz                                                          
          capabilities: pci pm msi ht pciexpress bus_master cap_list            
          configuration: driver=pcieport-driver                                 
     *-pci:1                                                                    
          description: PCI bridge                                               
          product: C51 PCI Express Bridge                                       
          vendor: nVidia Corporation                                            
          physical id: 3                                                        
          bus info: pci@0000:00:03.0                                            
          version: a1                                                           
          width: 32 bits                                                        
          clock: 33MHz                                                          
          capabilities: pci pm msi ht pciexpress bus_master cap_list            
          configuration: driver=pcieport-driver                                 
     *-display                                                                  
          description: VGA compatible controller                                
          product: C51 [Geforce 6150 Go]                                        
          vendor: nVidia Corporation                                            
          physical id: 5                                                        
          bus info: pci@0000:00:05.0                                            
          version: a2                                                           
          width: 64 bits                                                        
          clock: 66MHz                                                          
          capabilities: pm msi bus_master cap_list                              
          configuration: driver=nvidia latency=0 module=nvidia                  
     *-memory:9 UNCLAIMED                                                       
          description: RAM memory                                               
          product: MCP51 Host Bridge                                            
          vendor: nVidia Corporation                                            
          physical id: 9                                                        
          bus info: pci@0000:00:09.0                                            
          version: a2                                                           
          width: 32 bits                                                        
          clock: 66MHz (15.2ns)                                                 
          capabilities: ht bus_master cap_list                                  
          configuration: latency=0                                              
     *-isa                                                                      
          description: ISA bridge                                               
          product: MCP51 LPC Bridge                                             
          vendor: nVidia Corporation                                            
          physical id: a                                                        
          bus info: pci@0000:00:0a.0                                            
          version: a3                                                           
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: isa bus_master                                          
          configuration: latency=0                                              
     *-serial                                                                   
          description: SMBus                                                    
          product: MCP51 SMBus                                                  
          vendor: nVidia Corporation                                            
          physical id: a.1                                                      
          bus info: pci@0000:00:0a.1                                            
          version: a3                                                           
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: pm cap_list                                             
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2      
     *-processor UNCLAIMED                                                      
          description: Co-processor                                             
          product: MCP51 PMU                                                    
          vendor: nVidia Corporation                                            
          physical id: a.3                                                      
          bus info: pci@0000:00:0a.3                                            
          version: a3                                                           
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: bus_master                                              
          configuration: latency=0 maxlatency=1 mingnt=3                        
     *-usb:0                                                                    
          description: USB Controller                                           
          product: MCP51 USB Controller                                         
          vendor: nVidia Corporation                                            
          physical id: b                                                        
          bus info: pci@0000:00:0b.0                                            
          version: a3                                                           
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: pm bus_master cap_list                                  
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd                                                                        
     *-usb:1                                                                    
          description: USB Controller                                           
          product: MCP51 USB Controller                                         
          vendor: nVidia Corporation                                            
          physical id: b.1                                                      
          bus info: pci@0000:00:0b.1                                            
          version: a3                                                           
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: debug pm bus_master cap_list                            
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd                                                                        
     *-ide:0                                                                    
          description: IDE interface                                            
          product: MCP51 IDE                                                    
          vendor: nVidia Corporation                                            
          physical id: d                                                        
          bus info: pci@0000:00:0d.0                                            
          logical name: scsi0                                                   
          version: f1                                                           
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: ide pm bus_master cap_list emulated                     
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd                                                                        
        *-cdrom                                                                 
             description: DVD-RAM writer                                        
             product: DVD-RAM UJ-851S                                           
             vendor: MATSHITA                                                   
             physical id: 0.0.0                                                 
             bus info: scsi@0:0.0.0                                             
             logical name: /dev/cdrom                                           
             logical name: /dev/cdrw                                            
             logical name: /dev/dvd                                             
             logical name: /dev/dvdrw                                           
             logical name: /dev/scd0                                            
             logical name: /dev/sr0                                             
             version: 1.50                                                      
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram         
             configuration: ansiversion=5 status=nodisc                         
     *-ide:1                                                                    
          description: IDE interface                                            
          product: MCP51 Serial ATA Controller                                  
          vendor: nVidia Corporation                                            
          physical id: e                                                        
          bus info: pci@0000:00:0e.0                                            
          logical name: scsi2                                                   
          version: f1                                                           
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: ide pm msi ht bus_master cap_list emulated              
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv                                                                          
        *-disk                                                                  
             description: ATA Disk                                              
             product: WDC WD1600BEVS-6                                          
             vendor: Western Digital                                            
             physical id: 0.0.0                                                 
             bus info: scsi@2:0.0.0                                             
             logical name: /dev/sda                                             
             version: 04.0                                                      
             serial: WD-WXC107100757                                            
             size: 149GiB (160GB)                                               
             capabilities: partitioned partitioned:dos                          
             configuration: ansiversion=5 signature=aab3dcbc                    
           *-volume:0                                                           
                description: EXT3 volume                                        
                vendor: Linux                                                   
                physical id: 1                                                  
                bus info: scsi@2:0.0.0,1                                        
                logical name: /dev/sda1                                         
                logical name: /                                                 
                logical name: /dev/.static/dev                                  
                version: 1.0                                                    
                serial: 63650065-40c7-4d30-9361-7cb84f4cd191                    
                size: 40GiB                                                     
                capacity: 40GiB                                                 
                capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized                               
                configuration: created=2008-11-08 01:34:26 filesystem=ext3 modified=2008-11-10 16:34:59 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2008-11-10 16:08:57 state=mounted                             
           *-volume:1                                                           
                description: Linux swap volume                                  
                physical id: 2                                                  
                bus info: scsi@2:0.0.0,2                                        
                logical name: /dev/sda2                                         
                version: 1                                                      
                serial: 1c5f0ac5-68c9-4a5c-a3cf-ee0db4372120                    
                size: 509MiB                                                    
                capacity: 509MiB                                                
                capabilities: primary nofs swap initialized                     
                configuration: filesystem=swap pagesize=4096                    
           *-volume:2                                                           
                description: Windows FAT volume                                 
                vendor: mkdosfs                                                 
                physical id: 3                                                  
                bus info: scsi@2:0.0.0,3                                        
                logical name: /dev/sda3                                         
                version: FAT32                                                  
                serial: 46de-1234                                               
                size: 108GiB                                                    
                capacity: 108GiB                                                
                capabilities: primary fat initialized                           
                configuration: FATs=2 filesystem=fat                            
     *-pci:2                                                                    
          description: PCI bridge                                               
          product: MCP51 PCI Bridge                                             
          vendor: nVidia Corporation                                            
          physical id: 10                                                       
          bus info: pci@0000:00:10.0                                            
          version: a2                                                           
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: pci ht bus_master cap_list                              
        *-firewire                                                              
             description: FireWire (IEEE 1394)                                  
             product: R5C832 IEEE 1394 Controller                               
             vendor: Ricoh Co Ltd                                               
             physical id: 5                                                     
             bus info: pci@0000:07:05.0                                         
             version: 00                                                        
             width: 32 bits                                                     
             clock: 33MHz                                                       
             capabilities: pm bus_master cap_list                               
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394                                                                    
        *-system:0                                                              
             description: SD Host controller                                    
             product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter                  
             vendor: Ricoh Co Ltd                                               
             physical id: 5.1                                                   
             bus info: pci@0000:07:05.1                                         
             version: 19                                                        
             width: 32 bits                                                     
             clock: 33MHz                                                       
             capabilities: pm bus_master cap_list                               
             configuration: driver=sdhci-pci latency=64 module=sdhci_pci        
        *-system:1                                                              
             description: System peripheral                                     
             product: R5C592 Memory Stick Bus Host Adapter                      
             vendor: Ricoh Co Ltd                                               
             physical id: 5.2                                                   
             bus info: pci@0000:07:05.2                                         
             version: 0a                                                        
             width: 32 bits                                                     
             clock: 33MHz                                                       
             capabilities: pm cap_list                                          
             configuration: driver=ricoh-mmc latency=0 module=ricoh_mmc         
        *-system:2 UNCLAIMED                                                    
             description: System peripheral                                     
             product: xD-Picture Card Controller                                
             vendor: Ricoh Co Ltd                                               
             physical id: 5.3                                                   
             bus info: pci@0000:07:05.3                                         
             version: 05                                                        
             width: 32 bits                                                     
             clock: 33MHz                                                       
             capabilities: pm cap_list                                          
             configuration: latency=0                                           
        *-generic UNCLAIMED                                                     
             product: Illegal Vendor ID                                         
             vendor: Illegal Vendor ID                                          
             physical id: 5.4                                                   
             bus info: pci@0000:07:05.4                                         
             version: ff                                                        
             width: 32 bits                                                     
             clock: 66MHz                                                       
             capabilities: bus_master vga_palette cap_list                      
             configuration: latency=255 maxlatency=255 mingnt=255               
     *-multimedia                                                               
          description: Audio device                                             
          product: MCP51 High Definition Audio                                  
          vendor: nVidia Corporation                                            
          physical id: 10.1                                                     
          bus info: pci@0000:00:10.1                                            
          version: a2                                                           
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: pm msi ht bus_master cap_list                           
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel                                                                  
     *-bridge                                                                   
          description: Ethernet interface                                       
          product: MCP51 Ethernet Controller                                    
          vendor: nVidia Corporation                                            
          physical id: 14                                                       
          bus info: pci@0000:00:14.0                                            
          logical name: eth0                                                    
          version: a3                                                           
          serial: 00:1b:24:10:fc:65                                             
          size: 100000000                                                       
          capacity: 100000000                                                   
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation                                         
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.5.11 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s                       
     *-pci:3                                                                    
          description: Host bridge                                              
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]                                  
          physical id: 100                                                      
          bus info: pci@0000:00:18.0                                            
          version: 00                                                           
          width: 32 bits                                                        
          clock: 33MHz                                                          
     *-pci:4                                                                    
          description: Host bridge                                              
          product: K8 [Athlon64/Opteron] Address Map                            
          vendor: Advanced Micro Devices [AMD]                                  
          physical id: 101                                                      
          bus info: pci@0000:00:18.1                                            
          version: 00                                                           
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c6:86:dc:9d:23:cb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

My machine is an HP Pavilion dv9000

Any ideas will be much appreciated!

Detail: Already tried madwifi, ndiswrapper, bcm43xx, bcfwcutter... Because it's a hardware problem... Not software

:(

---

### Post by MewRS on 2008-11-10
More stuff...

I removed "silent" from the boot line and then I found the following lines at the boot:

```
Starting basic network [failed]
Configuring network interfaces [failed]
```

My wireless card was earlier in wlan0, and then eth1...
But now it is in nowhere!

My **ifconfig**:

```
eth0      Link encap:Ethernet  Endereço de HW 00:1b:24:10:fc:65
          inet end.: 192.168.5.11  Bcast:192.168.5.255  Masc:255.255.255.0
          endereço inet6: fe80::21b:24ff:fe10:fc65/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:1073 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:851 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:1080230 (1.0 MB) TX bytes:129149 (129.1 KB)
          IRQ:20 Endereço de E/S:0xe000

lo        Link encap:Loopback Local
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:46 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:46 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0
          RX bytes:2548 (2.5 KB) TX bytes:2548 (2.5 KB)
```

My **iwconfig**:

```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```


How sad... :(

---

### Post by MewRS on 2008-11-11
Any idea? :(

---

### Post by superprash2003 on 2008-11-11
post output of lshw -C network

---

### Post by MewRS on 2008-11-11
```
rafajaques@deviant:~$ sudo lshw -C network
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 22:00:55:3d:8f:d8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

The device is not listed, I guess! :(

---

### Post by Ayuthia on 2008-11-12
You might check and see if your laptop falls under this:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01087277&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01087277&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)

---

