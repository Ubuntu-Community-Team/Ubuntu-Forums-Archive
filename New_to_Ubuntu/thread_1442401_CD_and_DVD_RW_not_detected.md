---
title: "CD and DVD RW not detected"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by D.Bon on 2010-03-29
I have 2 devices that are working properly (functioning on windows and read CD's) but they are not detected on Kubuntu 9.1 AMD 64 bit
they are :1- ASUS CD-S520/A5 (CD ROM)
2- LG CD RW>>>HL-DT-ST DVDRAM GSA-H42N

how can I get them to work and fix this?
Thanks in Advance

---

### Post by undecim on 2010-03-30
Open a terminal, paste this command, and press enter
```
sudo lshw
```
(You will be prompted for your password. You won't see any characters being typed, but you are typing it in, trust me)

Post the output of that command here.

---

### Post by Chame_Wizard on 2010-03-30
```
dmesg|tail
```
What is the outcome?

---

### Post by D.Bon on 2010-03-30
> **undecim said:**
> Open a terminal, paste this command, and press enter
```
sudo lshw
```(You will be prompted for your password. You won't see any characters being typed, but you are typing it in, trust me)

Post the output of that command here.

    description: Desktop Computer
    width: 64 bits               
    capabilities: smbios-2.2 dmi-2.2 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00000000-0000-0000-0000-00508DDB1E8E                                                                        
  *-core                                                                        
       description: Motherboard                                                 
       product: KN8 SLI(NF-CK804)                                               
       vendor: [http://www.abit.com.tw/](http://www.abit.com.tw/)                                          
       physical id: 0                                                           
       version: 1.x                                                             
     *-firmware                                                                 
          description: BIOS                                                     
          vendor: Phoenix Technologies, LTD                                     
          physical id: 0                                                        
          version: 6.00 PG (11/11/2005)                                         
          size: 128KiB                                                          
          capacity: 448KiB                                                      
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot                                                                           
     *-cpu                                                                      
          description: CPU                                                      
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+               
          vendor: Advanced Micro Devices [AMD]                                  
          physical id: 4                                                        
          bus info: cpu@0                                                       
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+               
          slot: Socket 939                                                      
          size: 2200MHz                                                         
          capacity: 3GHz                                                        
          width: 64 bits                                                        
          clock: 200MHz                                                         
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good pni lahf_lm cmp_legacy cpufreq          
        *-cache:0                                                               
             description: L1 cache                                              
             physical id: a                                                     
             slot: Internal Cache                                               
             size: 128KiB                                                       
             capacity: 128KiB                                                   
             capabilities: synchronous internal write-back                      
        *-cache:1                                                               
             description: L2 cache                                              
             physical id: b                                                     
             slot: External Cache                                               
             size: 512KiB                                                       
             capacity: 512KiB                                                   
             capabilities: synchronous internal write-back                      
     *-memory:0                                                                 
          description: System Memory                                            
          physical id: 1b                                                       
          slot: System board or motherboard                                     
          size: 3GiB                                                            
        *-bank:0                                                                
             description: DIMM                                                  
             physical id: 0                                                     
             slot: A0                                                           
             size: 1GiB                                                         
             width: 64 bits                                                     
        *-bank:1                                                                
             description: DIMM                                                  
             physical id: 1                                                     
             slot: A1                                                           
             size: 1GiB                                                         
             width: 64 bits                                                     
        *-bank:2                                                                
             description: DIMM                                                  
             physical id: 2                                                     
             slot: A2                                                           
             size: 512MiB                                                       
             width: 64 bits                                                     
        *-bank:3                                                                
             description: DIMM                                                  
             physical id: 3                                                     
             slot: A3                                                           
             size: 512MiB                                                       
             width: 64 bits                                                     
     *-memory:1 UNCLAIMED                                                       
          description: Memory controller                                        
          product: CK804 Memory Controller                                      
          vendor: nVidia Corporation                                            
          physical id: 3                                                        
          bus info: pci@0000:00:00.0                                            
          version: a3                                                           
          width: 32 bits                                                        
          clock: 66MHz (15.2ns)                                                 
          capabilities: ht bus_master cap_list                                  
          configuration: latency=0                                              
     *-isa                                                                      
          description: ISA bridge                                               
          product: CK804 ISA Bridge                                             
          vendor: nVidia Corporation                                            
          physical id: 1                                                        
          bus info: pci@0000:00:01.0                                            
          version: a3                                                           
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: isa bus_master                                          
          configuration: latency=0                                              
     *-serial                                                                   
          description: SMBus                                                    
          product: CK804 SMBus                                                  
          vendor: nVidia Corporation                                            
          physical id: 1.1                                                      
          bus info: pci@0000:00:01.1                                            
          version: a2                                                           
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: pm cap_list                                             
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3   
          resources: irq:5 ioport:c400(size=32) ioport:1c00(size=64) ioport:1c40(size=64)                                                                       
     *-usb:0                                                                    
          description: USB Controller                                           
          product: CK804 USB Controller                                         
          vendor: nVidia Corporation                                            
          physical id: 2                                                        
          bus info: pci@0000:00:02.0                                            
          version: a2                                                           
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: pm bus_master cap_list                                  
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3        
          resources: irq:20 memory:fe02b000-fe02bfff                            
     *-usb:1                                                                    
          description: USB Controller                                           
          product: CK804 USB Controller                                         
          vendor: nVidia Corporation                                            
          physical id: 2.1                                                      
          bus info: pci@0000:00:02.1                                            
          version: a3                                                           
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: debug pm bus_master cap_list                            
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3        
          resources: irq:21 memory:feb00000-feb000ff                            
     *-ide:0                                                                    
          description: IDE interface                                            
          product: CK804 IDE                                                    
          vendor: nVidia Corporation                                            
          physical id: 6                                                        
          bus info: pci@0000:00:06.0                                            
          version: f2                                                           
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: ide pm bus_master cap_list                              
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3        
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:d000(size=16)                                                     
     *-ide:1                                                                    
          description: IDE interface                                            
          product: CK804 Serial ATA Controller                                  
          vendor: nVidia Corporation                                            
          physical id: 7                                                        
          bus info: pci@0000:00:07.0                                            
          logical name: scsi0                                                   
          version: f3                                                           
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: ide pm bus_master cap_list emulated                     
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3         
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d400(size=16) memory:fe02d000-fe02dfff           
        *-disk                                                                  
             description: ATA Disk                                              
             product: Maxtor 6V250F0                                            
             vendor: Maxtor                                                     
             physical id: 0.0.0                                                 
             bus info: scsi@0:0.0.0                                             
             logical name: /dev/sda                                             
             version: VA11                                                      
             serial: V50BM2NG                                                   
             size: 233GiB (251GB)                                               
             capabilities: partitioned partitioned:dos                          
             configuration: ansiversion=5 signature=2bd28d09                    
           *-volume:0                                                           
                description: Windows NTFS volume                                
                physical id: 1                                                  
                bus info: scsi@0:0.0.0,1                                        
                logical name: /dev/sda1                                         
                version: 3.1                                                    
                serial: 90b76d9b-fdc8-2244-97fb-e7523fec63da                    
                size: 48GiB                                                     
                capacity: 48GiB                                                 
                capabilities: primary bootable ntfs initialized                 
                configuration: clustersize=4096 created=2005-01-01 02:53:55 filesystem=ntfs state=clean                                                         
           *-volume:1                                                           
                description: Extended partition                                 
                physical id: 2                                                  
                bus info: scsi@0:0.0.0,2                                        
                logical name: /dev/sda2                                         
                size: 184GiB                                                    
                capacity: 184GiB                                                
                capabilities: primary extended partitioned partitioned:extended 
              *-logicalvolume:0                                                 
                   description: Linux filesystem partition                      
                   physical id: 5                                               
                   logical name: /dev/sda5                                      
                   logical name: /                                              
                   capacity: 28GiB                                              
                   configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=writeback state=mounted                                    
              *-logicalvolume:1                                                 
                   description: HPFS/NTFS partition                             
                   physical id: 6                                               
                   logical name: /dev/sda6                                      
                   capacity: 155GiB                                             
              *-logicalvolume:2                                                 
                   description: Linux swap / Solaris partition                  
                   physical id: 7                                               
                   logical name: /dev/sda7                                      
                   capacity: 541MiB                                             
                   capabilities: nofs                                           
     *-ide:2                                                                    
          description: IDE interface                                            
          product: CK804 Serial ATA Controller                                  
          vendor: nVidia Corporation                                            
          physical id: 8                                                        
          bus info: pci@0000:00:08.0                                            
          version: f3                                                           
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: ide pm bus_master cap_list                              
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3         
          resources: irq:22 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:e800(size=16) memory:fe02e000-fe02efff           
     *-pci:0                                                                    
          description: PCI bridge                                               
          product: CK804 PCI Bridge                                             
          vendor: nVidia Corporation                                            
          physical id: 9                                                        
          bus info: pci@0000:00:09.0                                            
          version: a2                                                           
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: pci bus_master                                          
          resources: ioport:7000(size=4096) memory:fdd00000-fddfffff memory:fdc00000-fdcfffff(prefetchable)                                                     
        *-firewire:0                                                            
             description: FireWire (IEEE 1394)                                  
             product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)         
             vendor: Texas Instruments                                          
             physical id: 6                                                     
             bus info: pci@0000:05:06.0                                         
             version: 00                                                        
             width: 32 bits                                                     
             clock: 33MHz                                                       
             capabilities: pm bus_master cap_list                               
             configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2    
             resources: irq:18 memory:fddff000-fddff7ff memory:fddf8000-fddfbfff
        *-multimedia                                                            
             description: Multimedia audio controller                           
             product: SB Audigy                                                 
             vendor: Creative Labs                                              
             physical id: a                                                     
             bus info: pci@0000:05:0a.0                                         
             version: 04                                                        
             width: 32 bits                                                     
             clock: 33MHz                                                       
             capabilities: pm bus_master cap_list                               
             configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2                                                                             
             resources: irq:18 ioport:7c00(size=64)                             
        *-input                                                                 
             description: Input device controller                               
             product: SB Audigy Game Port                                       
             vendor: Creative Labs                                              
             physical id: a.1                                                   
             bus info: pci@0000:05:0a.1                                         
             version: 04                                                        
             width: 32 bits                                                     
             clock: 33MHz                                                       
             capabilities: pm bus_master cap_list                               
             configuration: driver=Emu10k1_gameport latency=32                  
             resources: irq:0 ioport:7800(size=8)                               
        *-firewire:1                                                            
             description: FireWire (IEEE 1394)                                  
             product: SB Audigy FireWire Port                                   
             vendor: Creative Labs                                              
             physical id: a.2                                                   
             bus info: pci@0000:05:0a.2                                         
             version: 04                                                        
             width: 32 bits                                                     
             clock: 33MHz                                                       
             capabilities: pm bus_master cap_list                               
             configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2    
             resources: irq:19 memory:fddfe000-fddfe7ff memory:fddf4000-fddf7fff
     *-bridge                                                                   
          description: Ethernet interface                                       
          product: CK804 Ethernet Controller                                    
          vendor: nVidia Corporation                                            
          physical id: a                                                        
          bus info: pci@0000:00:0a.0                                            
          logical name: eth0                                                    
          version: a3                                                           
          serial: 00:50:8d:db:1e:8e                                             
          size: 100000000                                                       
          capacity: 1000000000                                                  
          width: 32 bits                                                        
          clock: 66MHz                                                          
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation                               
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.10 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s                                        
          resources: irq:23 memory:fe02f000-fe02ffff ioport:fc00(size=8)        
     *-pci:1                                                                    
          description: PCI bridge                                               
          product: CK804 PCIE Bridge                                            
          vendor: nVidia Corporation                                            
          physical id: b                                                        
          bus info: pci@0000:00:0b.0                                            
          version: a3                                                           
          width: 32 bits                                                        
          clock: 33MHz                                                          
          capabilities: pci pm msi ht pciexpress bus_master cap_list            
          configuration: driver=pcieport-driver                                 
          resources: irq:24 ioport:9000(size=4096) memory:fd700000-fd7fffff ioport:fdf00000(size=1048576)                                                       
     *-pci:2                                                                    
          description: PCI bridge                                               
          product: CK804 PCIE Bridge                                            
          vendor: nVidia Corporation                                            
          physical id: c                                                        
          bus info: pci@0000:00:0c.0                                            
          version: a3                                                           
          width: 32 bits                                                        
          clock: 33MHz                                                          
          capabilities: pci pm msi ht pciexpress bus_master cap_list            
          configuration: driver=pcieport-driver                                 
          resources: irq:25 ioport:a000(size=4096) memory:fd900000-fd9fffff ioport:fd800000(size=1048576)                                                       
     *-pci:3                                                                    
          description: PCI bridge                                               
          product: CK804 PCIE Bridge                                            
          vendor: nVidia Corporation                                            
          physical id: d                                                        
          bus info: pci@0000:00:0d.0                                            
          version: a3                                                           
          width: 32 bits                                                        
          clock: 33MHz                                                          
          capabilities: pci pm msi ht pciexpress bus_master cap_list            
          configuration: driver=pcieport-driver                                 
          resources: irq:26 ioport:6000(size=4096) memory:fdb00000-fdbfffff ioport:fda00000(size=1048576)                                                       
     *-pci:4                                                                    
          description: PCI bridge                                               
          product: CK804 PCIE Bridge                                            
          vendor: nVidia Corporation                                            
          physical id: e                                                        
          bus info: pci@0000:00:0e.0                                            
          version: a3                                                           
          width: 32 bits                                                        
          clock: 33MHz                                                          
          capabilities: pci pm msi ht pciexpress bus_master cap_list            
          configuration: driver=pcieport-driver                                 
          resources: irq:27 ioport:8000(size=4096) memory:fde00000-fdefffff ioport:d0000000(size=268435456)                                                     
        *-display:0 UNCLAIMED                                                   
             description: VGA compatible controller                             
             product: RV530 [Radeon X1600]                                      
             vendor: ATI Technologies Inc                                       
             physical id: 0                                                     
             bus info: pci@0000:01:00.0                                         
             version: 00                                                        
             width: 64 bits                                                     
             clock: 33MHz                                                       
             capabilities: pm pciexpress msi bus_master cap_list                
             configuration: latency=0                                           
             resources: memory:d0000000-dfffffff(prefetchable) memory:fdef0000-fdefffff ioport:8c00(size=256) memory:fde00000-fde1ffff(prefetchable)            
        *-display:1 UNCLAIMED                                                   
             description: Display controller                                    
             product: RV530 [Radeon X1600] (Secondary)                          
             vendor: ATI Technologies Inc                                       
             physical id: 0.1                                                   
             bus info: pci@0000:01:00.1                                         
             version: 00                                                        
             width: 64 bits                                                     
             clock: 33MHz                                                       
             capabilities: pm pciexpress cap_list                               
             configuration: latency=0                                           
             resources: memory:fdee0000-fdeeffff                                
     *-pci:5                                                                    
          description: Host bridge                                              
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0

---

### Post by D.Bon on 2010-03-30
> **Chame_Wizard said:**
> ```
dmesg|tail
```What is the outcome?

[   20.855016] [drm] Num pipes: 1
[   20.855023] [drm] writeback test succeeded in 1 usecs
[   24.030038] Clocksource tsc unstable (delta = -67271659 ns)
[   27.643537] eth0: no IPv6 routers present
[  459.414818] [drm] Num pipes: 1
[  459.474272] mtrr: MTRR 3 not used
[  459.628493] [drm] Setting GART location based on new memory map
[  459.628923] [drm] Loading R500 Microcode
[  459.628946] [drm] Num pipes: 1
[  459.628955] [drm] writeback test succeeded in 1 usecs

---

### Post by bclarky12 on 2010-04-02
i can't write anything to a cd either, when i put in the suggested command dmesg|tail, I get the following

[ 4642.586938] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[ 4642.586944] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 4642.586955] end_request: I/O error, dev sr0, sector 0
[ 4642.590013] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4642.590020] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 4642.590028] Info fld=0x0
[ 4642.590031] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[ 4642.590039] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 4642.590054] end_request: I/O error, dev sr0, sector 0
[ 4643.559258] cdrom: This disc doesn't have any tracks I recognize!
any help would be greatly appreciated, thank you all so much!

---

### Post by anewguy on 2010-04-02
I originally had written here to check master/slave on the IDE channel, but then noticed you said they worked in Windows, just not Ubuntu.   So, removed my original text.

Sorry for the interruption.

Dave 


it might have something to do with which device is first on the IDE interface though.  I would try swapping who is master and who is slave on the devices.  I had a problem once where I stupidly left a CDROM as a slave device and it was the only device on the interface.  Windows was okay with it, I could boot and install using the LiveCD, but when I booted the installed Ubuntu it didn't see the drive.  Changing to master solved the problem.  Perhaps you have something similar (a master/slave problem).

---

