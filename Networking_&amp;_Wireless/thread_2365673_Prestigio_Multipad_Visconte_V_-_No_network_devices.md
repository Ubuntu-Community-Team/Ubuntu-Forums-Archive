---
title: "Prestigio Multipad Visconte V - No network devices available"
date: 2017-07-09
forum: Networking &amp; Wireless
---

### Post by andrew772 on 2017-07-09
Hello. I have installed Lubuntu on a netbook but it doesn't recognise the network device (displays "No network devices available" in the panel). Networking is enabled in the panel. It can only do WiFi, no LAN.

I have exported the output of lspci and lshw, Any suggestions would be much appreciated! Thanks.

```

**lubuntu@lubuntu:~$ sudo lspci**
00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 0f)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0f)
00:14.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI (rev 0f)
00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 0f)
00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 0f)

**lubuntu@lubuntu:~$ sudo lshw**
lubuntu                     
    description: Notebook
    product: Multipad Visconte V (MRD7)
    vendor: Prestigio
    version: Type1 - TBD by OEM
    serial: PMP250363210595
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    configuration: boot=normal chassis=notebook family=BayTrail-T CR sku=MRD7 uuid=78563412-3412-7856-90AB-CDDEEFAABBCC
  *-core
       description: Motherboard
       product: BYT-PF02
       vendor: Hampoo
       physical id: 0
       version: Type2 - Board Version
       serial: Type2 - Board Serial Number
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: INSYDE Corp.
          physical id: 0
          version: G1W_QI10X_PRESTIGIO_252
          date: 06/20/2016
          size: 64KiB
          capacity: 3008KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU  Z3735F @ 1.33GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Atom(TM) CPU  Z3735F @ 1.33GHz
          slot: CPU 1
          size: 1036MHz
          capacity: 1832MHz
          width: 64 bits
          clock: 83MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology tsc_reliable nonstop_tsc aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand lahf_lm 3dnowprefetch epb tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat cpufreq
          configuration: cores=4 enabledcores=4 threads=1
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: Unknown
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
     *-cache
          description: L1 cache
          physical id: 7
          slot: Unknown
          size: 24KiB
          capacity: 24KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: To be filled by O.E.M
             vendor: To be filled by O.E.M
             physical id: 0
             serial: To be filled by O.E.M
             slot: DIMM0
             size: 2GiB
             width: 32 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns) [empty]
             product: To be filled by O.E.M
             vendor: To be filled by O.E.M
             physical id: 1
             serial: To be filled by O.E.M
             slot: DIMM1
             width: 32 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0f
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:200 memory:90000000-903fffff memory:80000000-8fffffff ioport:1000(size=8) memory:c0000-dffff
        *-usb
             description: USB controller
             product: Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 0f
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:198 memory:90800000-9080ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.10.0-19-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.10
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: USB 2.0 Hub
                   vendor: Terminus Technology Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.11
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Mouse
                      product: Optical Wheel Mouse
                      vendor: Dell Computer Corp.
                      physical id: 1
                      bus info: usb@1:1.1
                      version: 2.20
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
                 *-usb:1
                      description: Keyboard
                      product: USB KEYBOARD
                      vendor: SINO WEALTH
                      physical id: 3
                      bus info: usb@1:1.3
                      version: 1.00
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
                 *-usb:2
                      description: Mass storage device
                      product: STORE N GO
                      vendor: Verbatim
                      physical id: 4
                      bus info: usb@1:1.4
                      logical name: scsi0
                      version: 1.00
                      serial: 07105743C9A21D51
                      capabilities: usb-2.00 scsi emulated scsi-host
                      configuration: driver=usb-storage maxpower=200mA speed=480Mbit/s
                    *-disk
                         description: SCSI Disk
                         product: STORE N GO
                         vendor: Verbatim
                         physical id: 0.0.0
                         bus info: scsi@0:0.0.0
                         logical name: /dev/sda
                         version: 5.00
                         serial: 017D15015070
                         size: 3700MiB (3880MB)
                         capabilities: removable
                         configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512
                       *-medium
                            physical id: 0
                            logical name: /dev/sda
                            size: 3700MiB (3880MB)
                            capabilities: partitioned partitioned:dos
                            configuration: signature=616f42f7
                          *-volume
                               description: Windows FAT volume
                               vendor: mkfs.fat
                               physical id: 1
                               logical name: /dev/sda1
                               logical name: /isodevice
                               version: FAT32
                               serial: 1485-835c
                               size: 3698MiB
                               capacity: 3699MiB
                               capabilities: primary bootable fat initialized
                               configuration: FATs=2 filesystem=fat label=MULTIBOOT mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.10.0-19-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.10
                capabilities: usb-3.00
                configuration: driver=hub slots=1 speed=5000Mbit/s
        *-generic
             description: Encryption controller
             product: Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:202 memory:90700000-907fffff memory:90600000-906fffff
        *-isa
             description: ISA bridge
             product: Atom Processor Z36xxx/Z37xxx Series Power Control Unit
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
  *-battery
       description: Lithium Ion Battery
       product: SR Real Battery
       vendor: Intel SR 1
       physical id: 1
       version: Date
       serial: 123456789
       slot: I2C2
       configuration: voltage=3.8V
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 2
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 42mWh

```

---

### Post by chili555 on 2017-07-09
May we also see:```
lsusb
iwconfig
```

---

### Post by andrew772 on 2017-07-09
Thanks for the quick reply! here's the results of lsusb and iwconfig -

```

**lubuntu@lubuntu:~$ sudo lsusb**
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 18a5:0302 Verbatim, Ltd Flash Drive
Bus 001 Device 004: ID 258a:6a88  
Bus 001 Device 003: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**lubuntu@lubuntu:~$ sudo iwconfig**
lo        no wireless extensions.

```

---

### Post by chili555 on 2017-07-09
Let's dig a bit deeper: ```
dmesg | grep -i sdio
```

---

### Post by andrew772 on 2017-07-09
Thanks for another quick reply, below is the output again.

```

**lubuntu@lubuntu:~$ dmesg | grep -i sdio**
[   16.578543] mmc0: new high speed SDIO card at address 0001

```

I've also seen mention of the dmidecode command, I didn't grep it in case I missed something important -

```

**lubuntu@lubuntu:~$ sudo dmidecode**
# dmidecode 3.0
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.
34 structures occupying 1990 bytes.
Table at 0x7BD24000.


Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: INSYDE Corp.
    Version: G1W_QI10X_PRESTIGIO_252
    Release Date: 06/20/2016
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 3072 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
    BIOS Revision: 0.121
    Firmware Revision: 0.0


Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Prestigio
    Product Name: Multipad Visconte V
    Version: Type1 - TBD by OEM
    Serial Number: PMP250363210595
    UUID: 12345678-1234-5678-90AB-CDDEEFAABBCC
    Wake-up Type: Power Switch
    SKU Number: MRD7
    Family: BayTrail-T CR


Handle 0x0002, DMI type 2, 17 bytes
Base Board Information
    Manufacturer: Hampoo
    Product Name: BYT-PF02
    Version: Type2 - Board Version
    Serial Number: Type2 - Board Serial Number
    Asset Tag: Type2 - Board Asset Tag
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: Type2 - Board Chassis Location
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0


Handle 0x0003, DMI type 3, 24 bytes
Chassis Information
    Manufacturer: Chassis Manufacturer
    Type: Notebook
    Lock: Not Present
    Version: Chassis Version
    Serial Number: Chassis Serial Number
    Asset Tag: Chassis Asset Tag
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0
    SKU Number: Not Specified


Handle 0x0004, DMI type 4, 42 bytes
Processor Information
    Socket Designation: CPU 1
    Type: Central Processor
    Family: Atom
    Manufacturer: Intel(R) Corporation
    ID: 78 06 03 00 FF FB EB BF
    Signature: Type 0, Family 6, Model 55, Stepping 8
    Flags:
        FPU (Floating-point unit on-chip)
        VME (Virtual mode extension)
        DE (Debugging extension)
        PSE (Page size extension)
        TSC (Time stamp counter)
        MSR (Model specific registers)
        PAE (Physical address extension)
        MCE (Machine check exception)
        CX8 (CMPXCHG8 instruction supported)
        APIC (On-chip APIC hardware supported)
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        CLFSH (CLFLUSH instruction supported)
        DS (Debug store)
        ACPI (ACPI supported)
        MMX (MMX technology supported)
        FXSR (FXSAVE and FXSTOR instructions supported)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        SS (Self-snoop)
        HTT (Multi-threading)
        TM (Thermal monitor supported)
        PBE (Pending break enabled)
    Version: Intel(R) Atom(TM) CPU  Z3735F @ 1.33GHz
    Voltage: 0.7 V
    External Clock: 83 MHz
    Max Speed: 1826 MHz
    Current Speed: 1339 MHz
    Status: Populated, Enabled
    Upgrade: None
    L1 Cache Handle: 0x0008
    L2 Cache Handle: 0x0009
    L3 Cache Handle: Not Provided
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified
    Core Count: 4
    Core Enabled: 4
    Thread Count: 1
    Characteristics:
        64-bit capable
        Multi-Core
        Execute Protection
        Enhanced Virtualization
        Power/Performance Control


Handle 0x0005, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM0
    Bank Connections: 0 0
    Current Speed: Unknown
    Type: None
    Installed Size: 2048 MB (Single-bank Connection)
    Enabled Size: 2048 MB (Single-bank Connection)
    Error Status: OK


Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM1
    Bank Connections: 0 0
    Current Speed: Unknown
    Type: None
    Installed Size: Not Installed
    Enabled Size: Not Installed
    Error Status: OK


Handle 0x0007, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Unknown
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 24 kB
    Maximum Size: 24 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Data
    Associativity: Fully Associative


Handle 0x0008, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Unknown
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 32 kB
    Maximum Size: 32 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Instruction
    Associativity: 8-way Set-associative


Handle 0x0009, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Unknown
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 1024 kB
    Maximum Size: 1024 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 16-way Set-associative


Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J7A1
    Internal Connector Type: None
    External Reference Designator: Micro HDMI
    External Connector Type: Other
    Port Type: Video Port


Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J8A1
    Internal Connector Type: None
    External Reference Designator: Displat Port
    External Connector Type: Other
    Port Type: Video Port


Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J5A1
    Internal Connector Type: None
    External Reference Designator: USB3.0 AB
    External Connector Type: Access Bus (USB)
    Port Type: USB


Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J6A1
    Internal Connector Type: None
    External Reference Designator: USB3.0 Dock/USB2.0
    External Connector Type: Access Bus (USB)
    Port Type: USB


Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: CON9E1
    Internal Connector Type: None
    External Reference Designator: Micro SDCard
    External Connector Type: Other
    Port Type: Other


Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9A1
    Internal Connector Type: None
    External Reference Designator: SIM Card
    External Connector Type: Other
    Port Type: Other


Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9E1
    Internal Connector Type: None
    External Reference Designator: Audio Jack
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port


Handle 0x0011, DMI type 11, 5 bytes
OEM Strings
    String 1: ACME Corporation
    String 2: BF7yuKDKwEsd0
    String 3: sgkh6Gqr8+x+X
    String 4: rUMbNCclvVXrh


Handle 0x0012, DMI type 12, 5 bytes
System Configuration Options
    Option 1: SMI:00B2C002
    Option 2: DSN:      MP2C10X3G0Z3GB        
    Option 3: DSN:8HTF6464HDY-667B3 080EBAF3  
    Option 4: DSN:SANYOMAL42b500682006/03/01  


Handle 0x0013, DMI type 13, 22 bytes
BIOS Language Information
    Language Description Format: Long
    Installable Languages: 4
        en|US|iso8859-1
        fr|CA|iso8859-1
        zh|TW|unicode
        ja|JP|unicode
    Currently Installed Language: en|US|iso8859-1


Handle 0x0014, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 4 GB
    Error Information Handle: No Error
    Number Of Devices: 2


Handle 0x0015, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0014
    Error Information Handle: No Error
    Total Width: 32 bits
    Data Width: 32 bits
    Size: 2048 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK 0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MHz
    Manufacturer: To be filled by O.E.M
    Serial Number: To be filled by O.E.M
    Asset Tag: To be filled by O.E.M
    Part Number: To be filled by O.E.M
    Rank: Unknown
    Configured Clock Speed: 1333 MHz


Handle 0x0016, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0014
    Error Information Handle: No Error
    Total Width: 32 bits
    Data Width: 32 bits
    Size: No Module Installed
    Form Factor: SODIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK 1
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MHz
    Manufacturer: To be filled by O.E.M
    Serial Number: To be filled by O.E.M
    Asset Tag: To be filled by O.E.M
    Part Number: To be filled by O.E.M
    Rank: Unknown
    Configured Clock Speed: 1333 MHz


Handle 0x0017, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Array Handle: 0x0014
    Partition Width: 2


Handle 0x0018, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x0015
    Memory Array Mapped Address Handle: 0x0017
    Partition Row Position: Unknown


Handle 0x0019, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00080000000
    Ending Address: 0x0007FFFFFFF
    Range Size: Invalid
    Physical Device Handle: 0x0016
    Memory Array Mapped Address Handle: 0x0017
    Partition Row Position: Unknown


Handle 0x001A, DMI type 22, 26 bytes
Portable Battery
    Location: I2C2
    Manufacturer: Intel SR 1
    Manufacture Date: Date
    Serial Number: 123456789
    Name: SR Real Battery
    Chemistry: Lithium Ion
    Design Capacity: 0 mWh
    Design Voltage: 3750 mV
    SBDS Version: CRB Battery 0
    Maximum Error: Unknown
    OEM-specific Information: 0x00000000


Handle 0x001B, DMI type 26, 22 bytes
Voltage Probe
    Description: Voltage Probe Description.
    Location: Unknown
    Status: Unknown
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown


Handle 0x001C, DMI type 28, 22 bytes
Temperature Probe
    Description: Temperature Probe Description.
    Location: Unknown
    Status: Unknown
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown


Handle 0x001D, DMI type 32, 11 bytes
System Boot Information
    Status: No errors detected


Handle 0x001E, DMI type 39, 22 bytes
System Power Supply
    Location: OEM_Define0
    Name: OEM_Define1
    Manufacturer: OEM_Define2
    Serial Number: OEM_Define3
    Asset Tag: OEM_Define4
    Model Part Number: OEM_Define5
    Revision: OEM_Define6
    Max Power Capacity: 42 W
    Status: Present, OK
    Type: Regulator
    Input Voltage Range Switching: Auto-switch
    Plugged: No
    Hot Replaceable: No
    Input Voltage Probe Handle: 0x001B


Handle 0x001F, DMI type 41, 11 bytes
Onboard Device
    Reference Designation: IGD
    Type: Video
    Status: Disabled
    Type Instance: 1
    Bus Address: 0000:00:02.0


Handle 0x0020, DMI type 148, 26 bytes
OEM-specific Type
    Header and Data:
        94 1A 20 00 01 02 03 04 05 06 07 08 09 0A 0B 0C
        0D 0E 0F 10 11 12 13 14 15 16
    Strings:
        7.2.1003
        82B
        1.02
        1.1.1.1120
        Non ULPMC!!
        0x4_43
        0x22
        0F (C0 Stepping)
        BAY LAKE CR (6)
        0
        VLV-QC Tablet (1)
        G1W_QI10X_PRESTIGIO_252_KD101N55
        41.01
        NA
        0
        0
        1
        1
        3
        1
        1
        1


Handle 0xFEFF, DMI type 127, 4 bytes
End Of Table

```

---

### Post by chili555 on 2017-07-09
I'm getting low on ideas. May I see all of:```
dmesg
```...after a clean boot. As it is quite lengthy, post it here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by andrew772 on 2017-07-09
Thanks for looking, at least it's confirming I'm not missing anything obvious!

[http://paste.ubuntu.com/25054602/](http://paste.ubuntu.com/25054602/)

EDIT: Whoops I just noticed I pasted it twice, just as well it was at pastebin!

I should probably have mentioned I'm running it from a live usb pendrive, I want to make sure we can get the WiFi to work before installing it.

I've also seen a tutorial on updating the Iso with an updated linux kernel (currently running 4.10.0-19-generic), do you think this would make any difference?

Thanks.

---

### Post by chili555 on 2017-07-09
> I've also seen a tutorial on updating the Iso with an updated linux kernel (currently running 4.10.0-19-generic), do you think this would make any difference?It's doubtful. If the driver/problem/solution isn't in -19, then it probably isn't in -26, the latest. Of course, a better solution might be in kernel version 4.11.xx but that is not mainstream Ubuntu yet.

We see a ton of these:> [   40.771698] ACPI Error: No handler for Region [BMOP] (ffff9619bb4cb678) [UserDefinedRegion] (20160930/evregion-166)
[   40.771714] ACPI Error: Region UserDefinedRegion (ID=158) has no handler (20160930/exfldio-299)
[   40.771724] ACPI Error: Method parse/execution failed [\_SB.I2C5.BMBT._BST] (Node ffff9619bb4ce208), AE_NOT_EXIST (20160930/psparse-543)
[   40.771742] ACPI Exception: AE_NOT_EXIST, Evaluating _BST (20160930/battery-530)
[   40.798382] ACPI Error: No handler for Region [BMOP] (ffff9619bb4cb678) [UserDefinedRegion] (20160930/evregion-166)
[   40.798398] ACPI Error: Region UserDefinedRegion (ID=158) has no handler (20160930/exfldio-299)
[   40.798408] ACPI Error: Method parse/execution failed [\_SB.I2C5.BMBT._BST] (Node ffff9619bb4ce208), AE_NOT_EXIST (20160930/psparse-543)
[   40.798425] ACPI Exception: AE_NOT_EXIST, Evaluating _BST (20160930/battery-530)
[   40.826363] ACPI Error: No handler for Region [BMOP] (ffff9619bb4cb678) [UserDefinedRegion] (20160930/evregion-166)
[   40.826378] ACPI Error: Region UserDefinedRegion (ID=158) has no handler (20160930/exfldio-299)
[   40.826388] ACPI Error: Method parse/execution failed [\_SB.I2C5.BMBT._BST] (Node ffff9619bb4ce208), AE_NOT_EXIST (20160930/psparse-543)It is unclear, after a Google search, whether this is significant or not. ACPI is a bit out of my limited expertise.

We also see a ton of:> [   51.068632]  Baytrail Audio Port: ASoC: no backend DAIs enabled for Baytrail Audio Port
[   51.070619]  Baytrail Audio Port: ASoC: no backend DAIs enabled for Baytrail Audio Port
[   51.071089]  Baytrail Audio Port: ASoC: no backend DAIs enabled for Baytrail Audio Port
[   51.072684]  Baytrail Audio Port: ASoC: no backend DAIs enabled for Baytrail Audio Port
[   51.087213]  Baytrail Audio Port: ASoC: no backend DAIs enabled for Baytrail Audio PortAnd that's also outside my expertise. Does audio work?

Is there a BIOS or EFI on this device? Is there any improvement with Secure Boot disabled?

This suggests that there may be an available boot parameter: [https://wiki.archlinux.org/index.php/DSDT](https://wiki.archlinux.org/index.php/DSDT) I haven't any suggestion as to which to try.

So far, I'm skeptical that Ubuntu will work.

---

### Post by andrew772 on 2017-07-09
I will look at trying some different boot parameters, it makes sense the BIOS might not talk to Linux, I didn't even know you could spoof another OS until now.

I have just tested the audio, it doesn't give an error and thinks it's playing it, but no sound, maybe the above parameter will fix this too.

If no success with this I might try updating the kernel as a last resort. I'll update this thread with any further progress.

Thanks a lot for your help! at the very least I learnt some new bash commands! \\:D/

---

