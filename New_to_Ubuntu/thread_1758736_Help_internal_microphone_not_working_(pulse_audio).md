---
title: "Help internal microphone not working (pulse audio?)"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by xaegis on 2011-05-15
I am using Ubuntu 11.04 and I cannot get the internal mic to work. Can anyone help me troubleshoot this?

Thank you,

---

### Post by wildmanne39 on 2011-05-15
> **xaegis said:**
> I am using Ubuntu 11.04 and I cannot get the internal mic to work. Can anyone help me troubleshoot this?

Thank you,

Hi, first click on the speaker in the top right corner and go into preferences and check that your mic is not muted because mine is muted by default.:)

---

### Post by sectshun8 on 2011-05-15
> **wildmanne39 said:**
> Hi, first click on the speaker in the top right corner and go into preferences and check that your mic is not muted because mine is muted by default.:)

Thanks for that small tidbit... I just found mine was muted by default as well :)

---

### Post by wildmanne39 on 2011-05-15
> **sectshun8 said:**
> Thanks for that small tidbit... I just found mine was muted by default as well :)
Hi, your welcome if this fixed your problem please go to the top of the page and under forum tools mark the post solved. Thank you very much.):P

---

### Post by xaegis on 2011-05-15
Yup. Tried that and it still does not work. I already unchecked the "mute" button.

:(

---

### Post by wildmanne39 on 2011-05-15
> **xaegis said:**
> Yup. Tried that and it still does not work. I already unchecked the "mute" button.

:(

Hi type lspci in a terminal and post it back here by clicking on new reply and click # and paste the information between the brackets.:D

---

### Post by xaegis on 2011-05-15
Thanks.

```

00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc Madison [Mobility Radeon HD 5000 Series]
02:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
05:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
09:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
09:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
09:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
09:00.3 FireWire (IEEE 1394): Ricoh Co Ltd FireWire Host Controller (rev 01)
0b:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
Me@TheComputer:~/Desktop$ 

```

---

### Post by wildmanne39 on 2011-05-16
> **xaegis said:**
> Thanks.

```

00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc Madison [Mobility Radeon HD 5000 Series]
02:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
05:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
09:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
09:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
09:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
09:00.3 FireWire (IEEE 1394): Ricoh Co Ltd FireWire Host Controller (rev 01)
0b:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
Me@TheComputer:~/Desktop$ 

```
HI, put this in a terminal and post it back here please.
sudo dmidecode | less

---

### Post by xaegis on 2011-05-16
this is really long. Need the Handles too?

```
BIOS Information
        Vendor: Dell Inc.
        Version: A11
        Release Date: 08/03/2010
        Address: 0xE2D50
        Runtime Size: 119472 bytes
        ROM Size: 2048 kB
        Characteristics:
                PCI is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                5.25"/360 KB floppy services are supported (int 13h)
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 KB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                LS-120 boot is supported
                Smart battery is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported
                Targeted content distribution is supported
Handle 0x0002, DMI type 1, 27 bytes
System Information
        Manufacturer: Dell Inc.
        Product Name: Studio XPS 1645
        Version: A11 
        Serial Number: 4FX7SN1
        UUID: 44454C4C-4600-1058-8037-B4C04F534E31
        Wake-up Type: Power Switch
        SKU Number: Not Specified
        Family: Not Specified

Handle 0x0003, DMI type 2, 15 bytes
Base Board Information
        Manufacturer: Dell Inc.
        Product Name: 0VV228
        Version: A11
        Serial Number: .4FX7SN1.CN486430AT0054.
        Asset Tag:           
        Features: None
        Location In Chassis: Not Specified
        Chassis Handle: 0xFFFF
        Type: Unknown
        Contained Object Handles: 0

Handle 0x0004, DMI type 3, 21 bytes
Chassis Information
        Manufacturer: Dell Inc.
        Type: Portable
        Lock: Not Present
        Version: A11        
        Serial Number: 4FX7SN1
        Asset Tag:           
        Boot-up State: Safe
        Power Supply State: Safe
        Thermal State: Safe
        Security Status: None
        OEM Information: 0x00000000
        Height: Unspecified
        Number Of Power Cords: Unspecified
        Contained Elements: 0
Handle 0x0005, DMI type 4, 42 bytes
Processor Information
        Socket Designation: U2E1
        Type: Central Processor
        Family: <OUT OF SPEC>
        Manufacturer: Intel
        ID: E5 06 01 00 FF FB EB BF
        Version: CPU Version
        Voltage: 3.3 V
        External Clock: 133 MHz
        Max Speed: 4096 MHz
        Current Speed: 1600 MHz
        Status: Populated, Enabled
        Upgrade: ZIF Socket
        L1 Cache Handle: 0x0006
        L2 Cache Handle: 0x0007
        L3 Cache Handle: 0x0008
        Serial Number: Not Specified
        Asset Tag: Not Specified
        Part Number: Not Specified
        Core Count: 4
        Core Enabled: 4
        Thread Count: 8
        Characteristics:
                64-bit capable

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L1 Cache
        Configuration: Enabled, Socketed, Level 1
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 128 KB
        Maximum Size: 128 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
                Asynchronous
        Installed SRAM Type: Asynchronous
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Data
        Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L2 Cache
        Configuration: Enabled, Socketed, Level 2
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 1024 KB
        Maximum Size: 1024 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
Handle 0x0005, DMI type 4, 42 bytes
Processor Information
        Socket Designation: U2E1
        Type: Central Processor
        Family: <OUT OF SPEC>
        Manufacturer: Intel
        ID: E5 06 01 00 FF FB EB BF
        Version: CPU Version
        Voltage: 3.3 V
        External Clock: 133 MHz
        Max Speed: 4096 MHz
        Current Speed: 1600 MHz
        Status: Populated, Enabled
        Upgrade: ZIF Socket
        L1 Cache Handle: 0x0006
        L2 Cache Handle: 0x0007
        L3 Cache Handle: 0x0008
        Serial Number: Not Specified
        Asset Tag: Not Specified
        Part Number: Not Specified
        Core Count: 4
        Core Enabled: 4
        Thread Count: 8
        Characteristics:
                64-bit capable

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L1 Cache
        Configuration: Enabled, Socketed, Level 1
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 128 KB
        Maximum Size: 128 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
                Asynchronous
        Installed SRAM Type: Asynchronous
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Data
        Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L2 Cache
        Configuration: Enabled, Socketed, Level 2
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 1024 KB
        Maximum Size: 1024 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
Handle 0x0005, DMI type 4, 42 bytes
Processor Information
        Socket Designation: U2E1
        Type: Central Processor
        Family: <OUT OF SPEC>
        Manufacturer: Intel
        ID: E5 06 01 00 FF FB EB BF
        Version: CPU Version
        Voltage: 3.3 V
        External Clock: 133 MHz
        Max Speed: 4096 MHz
        Current Speed: 1600 MHz
        Status: Populated, Enabled
        Upgrade: ZIF Socket
        L1 Cache Handle: 0x0006
        L2 Cache Handle: 0x0007
        L3 Cache Handle: 0x0008
        Serial Number: Not Specified
        Asset Tag: Not Specified
        Part Number: Not Specified
        Core Count: 4
        Core Enabled: 4
        Thread Count: 8
        Characteristics:
                64-bit capable

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L1 Cache
        Configuration: Enabled, Socketed, Level 1
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 128 KB
        Maximum Size: 128 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
                Asynchronous
        Installed SRAM Type: Asynchronous
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Data
        Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L2 Cache
        Configuration: Enabled, Socketed, Level 2
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 1024 KB
        Maximum Size: 1024 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
               Asynchronous
        Installed SRAM Type: Burst
        Speed: Unknown
        Error Correction Type: None
        System Type: Other
        Associativity: 4-way Set-associative

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: Not Specified
        Internal Connector Type: None
        External Reference Designator: CRT
        External Connector Type: DB-15 female
        Port Type: Video Port

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J1A1
        Internal Connector Type: None
        External Reference Designator: Keyboard
        External Connector Type: Circular DIN-8 male
        Port Type: Keyboard Port

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J1A1
        Internal Connector Type: None
        External Reference Designator: PS/2 Mouse
        External Connector Type: Circular DIN-8 male
        Port Type: Mouse Port

Handle 0x000C, DMI type 9, 17 bytes
System Slot Information
        Designation: PEG Slot J6B2
        Type: 32-bit PCI Express
        Current Usage: Available
        Length: Long
        ID: 6
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x000D, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot J6B1
        Type: 32-bit PCI Express
        Current Usage: Available
        Length: Long
        ID: 7
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x000E, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot J6D1
        Type: 32-bit PCI Express
        Current Usage: In Use
        Length: Long
        ID: 8
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x000F, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot J8B3
        Type: 32-bit PCI Express
        Current Usage: Available
        Length: Long
        ID: 9
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x0010, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot J8D1
        Type: 32-bit PCI Express
        Current Usage: Available
        Length: Long
        ID: 10
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x0011, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot J7B1
        Type: 32-bit PCI Express
        Current Usage: In Use
        Length: Long
        ID: 11
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x0012, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot 6
        Type: 32-bit PCI Express
        Current Usage: In Use
        Length: Long
        ID: 12
        Characteristics:
                5.0 V is provided
                3.3 V is provided
Handle 0x0013, DMI type 10, 8 bytes
On Board Device 1 Information
        Type: Video
        Status: Enabled
        Description: Intel Arrandale Graphics    
On Board Device 2 Information
        Type: Sound
        Status: Enabled
        Description: Sigmatel 9273

Handle 0x0014, DMI type 11, 5 bytes
OEM Strings
        String 1: Dell System
        String 2: 5
        String 3: 13

Handle 0x0015, DMI type 15, 29 bytes
System Event Log
        Area Length: 16 bytes
        Header Start Offset: 0x0000
        Header Length: 16 bytes
        Data Start Offset: 0x0010
        Access Method: General-purpose non-volatile data functions
        Access Address: 0x0000
        Status: Valid, Not Full
        Change Token: 0x00000048
        Header Format: Type 1
        Supported Log Type Descriptors: 3
        Descriptor 1: POST error
        Data Format 1: POST results bitmap
        Descriptor 2: Single-bit ECC memory error
        Data Format 2: Multiple-event
        Descriptor 3: Multi-bit ECC memory error
        Data Format 3: Multiple-event

Handle 0x0016, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 8 GB
        Error Information Handle: Not Provided
        Number Of Devices: 2

Handle 0x0017, DMI type 17, 28 bytes
Memory Device
        Array Handle: 0x0016
        Error Information Handle: No Error
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: SODIMM
        Set: 1
        Locator: DIMM_A
       Bank Locator: Not Specified
        Type: <OUT OF SPEC>
        Type Detail: Synchronous
        Speed: 1333 MHz (0.8 ns)
        Manufacturer: 830B            
        Serial Number: 26A2127C        
        Asset Tag: 1028
        Part Number: NT2GC64B8HC0NS-CG 

Handle 0x0018, DMI type 17, 28 bytes
Memory Device
        Array Handle: 0x0016
        Error Information Handle: No Error
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: SODIMM
        Set: 1
        Locator: DIMM_B
        Bank Locator: Not Specified
        Type: <OUT OF SPEC>
        Type Detail: Synchronous
        Speed: 1333 MHz (0.8 ns)
        Manufacturer: 830B            
        Serial Number: 16A1127D        
        Asset Tag: 1028
        Part Number: NT2GC64B8HC0NS-CG 

Handle 0x0019, DMI type 18, 23 bytes
32-bit Memory Error Information
        Type: OK
        Granularity: Unknown
        Operation: Unknown
        Vendor Syndrome: Unknown
        Memory Array Address: Unknown
        Device Address: Unknown
        Resolution: Unknown

Handle 0x001A, DMI type 18, 23 bytes
32-bit Memory Error Information
        Type: OK
        Granularity: Unknown
        Operation: Unknown
        Vendor Syndrome: Unknown
        Memory Array Address: Unknown
        Device Address: Unknown
        Resolution: Unknown

Handle 0x001B, DMI type 19, 15 bytes
Memory Array Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x000FFFFFFFF
        Range Size: 4 GB
        Physical Array Handle: 0x0016
        Partition Width: 0

Handle 0x001C, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x0007FFFFFFF
        Range Size: 2 GB
        Physical Device Handle: 0x0017
        Memory Array Mapped Address Handle: 0x001B
        Partition Row Position: 1
        Interleaved Data Depth: 1

Handle 0x001D, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00080000000
        Ending Address: 0x000FFFFFFFF
        Range Size: 2 GB
        Physical Device Handle: 0x0018
        Memory Array Mapped Address Handle: 0x001B
        Partition Row Position: 1
        Interleaved Data Depth: 1

Handle 0x001E, DMI type 21, 7 bytes
Built-in Pointing Device
        Type: Touch Pad
        Interface: Bus Mouse
        Buttons: 2

Handle 0x001F, DMI type 22, 26 bytes
Portable Battery
        Location: System Battery Bay
        Manufacturer: SDI                 
        Name: SDI                 
        Design Capacity: 78000 mWh
        Design Voltage: 11100 mV
        SBDS Version: Bat123
        Maximum Error: Unknown
        SBDS Serial Number: 466C
        SBDS Manufacture Date: 2010-08-23
        SBDS Chemistry: LION  
        OEM-specific Information: 0x00000001

Handle 0x0020, DMI type 23, 13 bytes
System Reset
        Status: Enabled
        Watchdog Timer: Present
        Boot Option: Do Not Reboot
        Boot Option On Limit: Do Not Reboot
        Reset Count: Unknown
        Reset Limit: Unknown
        Timer Interval: Unknown
        Timeout: Unknown

Handle 0x0021, DMI type 24, 5 bytes

Handle 0x0023, DMI type 26, 20 bytes
Voltage Probe
        Description: Voltage Probe
        Location: Processor
        Status: OK
        Maximum Value: Unknown
        Minimum Value: Unknown
        Resolution: Unknown
        Tolerance: Unknown
        Accuracy: Unknown
        OEM-specific Information: 0x00000000

Handle 0x0024, DMI type 27, 12 bytes
Cooling Device
        Temperature Probe Handle: 0x0025
        Type: Fan
        Status: OK
        OEM-specific Information: 0x00000000

Handle 0x0025, DMI type 28, 20 bytes
Temperature Probe
        Description: Temperature Probe
        Location: Processor
        Status: OK
        Maximum Value: Unknown
        Minimum Value Unknown
        Resolution: Unknown
        Tolerance: Unknown
        Accuracy: Unknown
        OEM-specific Information: 0x00000000

Handle 0x0026, DMI type 29, 20 bytes
Electrical Current Probe
        Description: Electrical Current Probe
        Location: Processor
        Status: OK
        Maximum Value: Unknown
        Minimum Value: Unknown


Handle 0xB000, DMI type 176, 5 bytes
OEM-specific Type
        Header and Data:
                B0 05 00 B0 00

Handle 0xB100, DMI type 177, 12 bytes
OEM-specific Type
        Header and Data:
                B1 0C 00 B1 1A 06 00 00 00 00 00 00

Handle 0xD000, DMI type 208, 12 bytes
OEM-specific Type
        Header and Data:
                D0 0C 00 D0 01 05 FE 00 FE 02 32 30
        Strings:
                09010120090101

Handle 0xD300, DMI type 211, 17 bytes
OEM-specific Type
        Header and Data:
                D3 11 00 D3 46 72 6F 6E 74 03 02 01 00 31 33 35
                04

Handle 0xD400, DMI type 212, 17 bytes
OEM-specific Type
        Header and Data:
                D4 11 00 D4 70 00 71 00 00 10 2D 2E FF FF 00 00
                00

Handle 0xD800, DMI type 216, 9 bytes
OEM-specific Type
        Header and Data:
                D8 09 00 D8 01 02 01 F0 03
        Strings:
                Intel
                012.020.000.035.035105

Handle 0xDC00, DMI type 220, 20 bytes
OEM-specific Type
        Header and Data:
                DC 14 00 DC 01 F0 00 00 02 F0 00 00 03 F0 04 F0
                00 00 00 00

Handle 0xDD00, DMI type 221, 19 bytes
OEM-specific Type
        Header and Data:
                DD 13 00 DD 00 00 00 00 00 00 00 00 00 00 00 00
                00 00 00

Handle 0xDE00, DMI type 222, 16 bytes
OEM-specific Type
        Header and Data:
                DE 10 00 DE 01 02 FF FF 00 00 00 00 00 00 00 00

Handle 0x0033, DMI type 127, 4 bytes
End Of Table




```

---

### Post by wildmanne39 on 2011-05-17
> **xaegis said:**
> this is really long. Need the Handles too?

```
BIOS Information
        Vendor: Dell Inc.
        Version: A11
        Release Date: 08/03/2010
        Address: 0xE2D50
        Runtime Size: 119472 bytes
        ROM Size: 2048 kB
        Characteristics:
                PCI is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                5.25"/360 KB floppy services are supported (int 13h)
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 KB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                LS-120 boot is supported
                Smart battery is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported
                Targeted content distribution is supported
Handle 0x0002, DMI type 1, 27 bytes
System Information
        Manufacturer: Dell Inc.
        Product Name: Studio XPS 1645
        Version: A11 
        Serial Number: 4FX7SN1
        UUID: 44454C4C-4600-1058-8037-B4C04F534E31
        Wake-up Type: Power Switch
        SKU Number: Not Specified
        Family: Not Specified

Handle 0x0003, DMI type 2, 15 bytes
Base Board Information
        Manufacturer: Dell Inc.
        Product Name: 0VV228
        Version: A11
        Serial Number: .4FX7SN1.CN486430AT0054.
        Asset Tag:           
        Features: None
        Location In Chassis: Not Specified
        Chassis Handle: 0xFFFF
        Type: Unknown
        Contained Object Handles: 0

Handle 0x0004, DMI type 3, 21 bytes
Chassis Information
        Manufacturer: Dell Inc.
        Type: Portable
        Lock: Not Present
        Version: A11        
        Serial Number: 4FX7SN1
        Asset Tag:           
        Boot-up State: Safe
        Power Supply State: Safe
        Thermal State: Safe
        Security Status: None
        OEM Information: 0x00000000
        Height: Unspecified
        Number Of Power Cords: Unspecified
        Contained Elements: 0
Handle 0x0005, DMI type 4, 42 bytes
Processor Information
        Socket Designation: U2E1
        Type: Central Processor
        Family: <OUT OF SPEC>
        Manufacturer: Intel
        ID: E5 06 01 00 FF FB EB BF
        Version: CPU Version
        Voltage: 3.3 V
        External Clock: 133 MHz
        Max Speed: 4096 MHz
        Current Speed: 1600 MHz
        Status: Populated, Enabled
        Upgrade: ZIF Socket
        L1 Cache Handle: 0x0006
        L2 Cache Handle: 0x0007
        L3 Cache Handle: 0x0008
        Serial Number: Not Specified
        Asset Tag: Not Specified
        Part Number: Not Specified
        Core Count: 4
        Core Enabled: 4
        Thread Count: 8
        Characteristics:
                64-bit capable

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L1 Cache
        Configuration: Enabled, Socketed, Level 1
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 128 KB
        Maximum Size: 128 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
                Asynchronous
        Installed SRAM Type: Asynchronous
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Data
        Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L2 Cache
        Configuration: Enabled, Socketed, Level 2
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 1024 KB
        Maximum Size: 1024 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
Handle 0x0005, DMI type 4, 42 bytes
Processor Information
        Socket Designation: U2E1
        Type: Central Processor
        Family: <OUT OF SPEC>
        Manufacturer: Intel
        ID: E5 06 01 00 FF FB EB BF
        Version: CPU Version
        Voltage: 3.3 V
        External Clock: 133 MHz
        Max Speed: 4096 MHz
        Current Speed: 1600 MHz
        Status: Populated, Enabled
        Upgrade: ZIF Socket
        L1 Cache Handle: 0x0006
        L2 Cache Handle: 0x0007
        L3 Cache Handle: 0x0008
        Serial Number: Not Specified
        Asset Tag: Not Specified
        Part Number: Not Specified
        Core Count: 4
        Core Enabled: 4
        Thread Count: 8
        Characteristics:
                64-bit capable

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L1 Cache
        Configuration: Enabled, Socketed, Level 1
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 128 KB
        Maximum Size: 128 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
                Asynchronous
        Installed SRAM Type: Asynchronous
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Data
        Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L2 Cache
        Configuration: Enabled, Socketed, Level 2
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 1024 KB
        Maximum Size: 1024 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
Handle 0x0005, DMI type 4, 42 bytes
Processor Information
        Socket Designation: U2E1
        Type: Central Processor
        Family: <OUT OF SPEC>
        Manufacturer: Intel
        ID: E5 06 01 00 FF FB EB BF
        Version: CPU Version
        Voltage: 3.3 V
        External Clock: 133 MHz
        Max Speed: 4096 MHz
        Current Speed: 1600 MHz
        Status: Populated, Enabled
        Upgrade: ZIF Socket
        L1 Cache Handle: 0x0006
        L2 Cache Handle: 0x0007
        L3 Cache Handle: 0x0008
        Serial Number: Not Specified
        Asset Tag: Not Specified
        Part Number: Not Specified
        Core Count: 4
        Core Enabled: 4
        Thread Count: 8
        Characteristics:
                64-bit capable

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L1 Cache
        Configuration: Enabled, Socketed, Level 1
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 128 KB
        Maximum Size: 128 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
                Asynchronous
        Installed SRAM Type: Asynchronous
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Data
        Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L2 Cache
        Configuration: Enabled, Socketed, Level 2
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 1024 KB
        Maximum Size: 1024 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
               Asynchronous
        Installed SRAM Type: Burst
        Speed: Unknown
        Error Correction Type: None
        System Type: Other
        Associativity: 4-way Set-associative

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: Not Specified
        Internal Connector Type: None
        External Reference Designator: CRT
        External Connector Type: DB-15 female
        Port Type: Video Port

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J1A1
        Internal Connector Type: None
        External Reference Designator: Keyboard
        External Connector Type: Circular DIN-8 male
        Port Type: Keyboard Port

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J1A1
        Internal Connector Type: None
        External Reference Designator: PS/2 Mouse
        External Connector Type: Circular DIN-8 male
        Port Type: Mouse Port

Handle 0x000C, DMI type 9, 17 bytes
System Slot Information
        Designation: PEG Slot J6B2
        Type: 32-bit PCI Express
        Current Usage: Available
        Length: Long
        ID: 6
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x000D, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot J6B1
        Type: 32-bit PCI Express
        Current Usage: Available
        Length: Long
        ID: 7
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x000E, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot J6D1
        Type: 32-bit PCI Express
        Current Usage: In Use
        Length: Long
        ID: 8
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x000F, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot J8B3
        Type: 32-bit PCI Express
        Current Usage: Available
        Length: Long
        ID: 9
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x0010, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot J8D1
        Type: 32-bit PCI Express
        Current Usage: Available
        Length: Long
        ID: 10
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x0011, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot J7B1
        Type: 32-bit PCI Express
        Current Usage: In Use
        Length: Long
        ID: 11
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x0012, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot 6
        Type: 32-bit PCI Express
        Current Usage: In Use
        Length: Long
        ID: 12
        Characteristics:
                5.0 V is provided
                3.3 V is provided
Handle 0x0013, DMI type 10, 8 bytes
On Board Device 1 Information
        Type: Video
        Status: Enabled
        Description: Intel Arrandale Graphics    
On Board Device 2 Information
        Type: Sound
        Status: Enabled
        Description: Sigmatel 9273

Handle 0x0014, DMI type 11, 5 bytes
OEM Strings
        String 1: Dell System
        String 2: 5
        String 3: 13

Handle 0x0015, DMI type 15, 29 bytes
System Event Log
        Area Length: 16 bytes
        Header Start Offset: 0x0000
        Header Length: 16 bytes
        Data Start Offset: 0x0010
        Access Method: General-purpose non-volatile data functions
        Access Address: 0x0000
        Status: Valid, Not Full
        Change Token: 0x00000048
        Header Format: Type 1
        Supported Log Type Descriptors: 3
        Descriptor 1: POST error
        Data Format 1: POST results bitmap
        Descriptor 2: Single-bit ECC memory error
        Data Format 2: Multiple-event
        Descriptor 3: Multi-bit ECC memory error
        Data Format 3: Multiple-event

Handle 0x0016, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 8 GB
        Error Information Handle: Not Provided
        Number Of Devices: 2

Handle 0x0017, DMI type 17, 28 bytes
Memory Device
        Array Handle: 0x0016
        Error Information Handle: No Error
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: SODIMM
        Set: 1
        Locator: DIMM_A
       Bank Locator: Not Specified
        Type: <OUT OF SPEC>
        Type Detail: Synchronous
        Speed: 1333 MHz (0.8 ns)
        Manufacturer: 830B            
        Serial Number: 26A2127C        
        Asset Tag: 1028
        Part Number: NT2GC64B8HC0NS-CG 

Handle 0x0018, DMI type 17, 28 bytes
Memory Device
        Array Handle: 0x0016
        Error Information Handle: No Error
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: SODIMM
        Set: 1
        Locator: DIMM_B
        Bank Locator: Not Specified
        Type: <OUT OF SPEC>
        Type Detail: Synchronous
        Speed: 1333 MHz (0.8 ns)
        Manufacturer: 830B            
        Serial Number: 16A1127D        
        Asset Tag: 1028
        Part Number: NT2GC64B8HC0NS-CG 

Handle 0x0019, DMI type 18, 23 bytes
32-bit Memory Error Information
        Type: OK
        Granularity: Unknown
        Operation: Unknown
        Vendor Syndrome: Unknown
        Memory Array Address: Unknown
        Device Address: Unknown
        Resolution: Unknown

Handle 0x001A, DMI type 18, 23 bytes
32-bit Memory Error Information
        Type: OK
        Granularity: Unknown
        Operation: Unknown
        Vendor Syndrome: Unknown
        Memory Array Address: Unknown
        Device Address: Unknown
        Resolution: Unknown

Handle 0x001B, DMI type 19, 15 bytes
Memory Array Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x000FFFFFFFF
        Range Size: 4 GB
        Physical Array Handle: 0x0016
        Partition Width: 0

Handle 0x001C, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x0007FFFFFFF
        Range Size: 2 GB
        Physical Device Handle: 0x0017
        Memory Array Mapped Address Handle: 0x001B
        Partition Row Position: 1
        Interleaved Data Depth: 1

Handle 0x001D, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00080000000
        Ending Address: 0x000FFFFFFFF
        Range Size: 2 GB
        Physical Device Handle: 0x0018
        Memory Array Mapped Address Handle: 0x001B
        Partition Row Position: 1
        Interleaved Data Depth: 1

Handle 0x001E, DMI type 21, 7 bytes
Built-in Pointing Device
        Type: Touch Pad
        Interface: Bus Mouse
        Buttons: 2

Handle 0x001F, DMI type 22, 26 bytes
Portable Battery
        Location: System Battery Bay
        Manufacturer: SDI                 
        Name: SDI                 
        Design Capacity: 78000 mWh
        Design Voltage: 11100 mV
        SBDS Version: Bat123
        Maximum Error: Unknown
        SBDS Serial Number: 466C
        SBDS Manufacture Date: 2010-08-23
        SBDS Chemistry: LION  
        OEM-specific Information: 0x00000001

Handle 0x0020, DMI type 23, 13 bytes
System Reset
        Status: Enabled
        Watchdog Timer: Present
        Boot Option: Do Not Reboot
        Boot Option On Limit: Do Not Reboot
        Reset Count: Unknown
        Reset Limit: Unknown
        Timer Interval: Unknown
        Timeout: Unknown

Handle 0x0021, DMI type 24, 5 bytes

Handle 0x0023, DMI type 26, 20 bytes
Voltage Probe
        Description: Voltage Probe
        Location: Processor
        Status: OK
        Maximum Value: Unknown
        Minimum Value: Unknown
        Resolution: Unknown
        Tolerance: Unknown
        Accuracy: Unknown
        OEM-specific Information: 0x00000000

Handle 0x0024, DMI type 27, 12 bytes
Cooling Device
        Temperature Probe Handle: 0x0025
        Type: Fan
        Status: OK
        OEM-specific Information: 0x00000000

Handle 0x0025, DMI type 28, 20 bytes
Temperature Probe
        Description: Temperature Probe
        Location: Processor
        Status: OK
        Maximum Value: Unknown
        Minimum Value Unknown
        Resolution: Unknown
        Tolerance: Unknown
        Accuracy: Unknown
        OEM-specific Information: 0x00000000

Handle 0x0026, DMI type 29, 20 bytes
Electrical Current Probe
        Description: Electrical Current Probe
        Location: Processor
        Status: OK
        Maximum Value: Unknown
        Minimum Value: Unknown


Handle 0xB000, DMI type 176, 5 bytes
OEM-specific Type
        Header and Data:
                B0 05 00 B0 00

Handle 0xB100, DMI type 177, 12 bytes
OEM-specific Type
        Header and Data:
                B1 0C 00 B1 1A 06 00 00 00 00 00 00

Handle 0xD000, DMI type 208, 12 bytes
OEM-specific Type
        Header and Data:
                D0 0C 00 D0 01 05 FE 00 FE 02 32 30
        Strings:
                09010120090101

Handle 0xD300, DMI type 211, 17 bytes
OEM-specific Type
        Header and Data:
                D3 11 00 D3 46 72 6F 6E 74 03 02 01 00 31 33 35
                04

Handle 0xD400, DMI type 212, 17 bytes
OEM-specific Type
        Header and Data:
                D4 11 00 D4 70 00 71 00 00 10 2D 2E FF FF 00 00
                00

Handle 0xD800, DMI type 216, 9 bytes
OEM-specific Type
        Header and Data:
                D8 09 00 D8 01 02 01 F0 03
        Strings:
                Intel
                012.020.000.035.035105

Handle 0xDC00, DMI type 220, 20 bytes
OEM-specific Type
        Header and Data:
                DC 14 00 DC 01 F0 00 00 02 F0 00 00 03 F0 04 F0
                00 00 00 00

Handle 0xDD00, DMI type 221, 19 bytes
OEM-specific Type
        Header and Data:
                DD 13 00 DD 00 00 00 00 00 00 00 00 00 00 00 00
                00 00 00

Handle 0xDE00, DMI type 222, 16 bytes
OEM-specific Type
        Header and Data:
                DE 10 00 DE 01 02 FF FF 00 00 00 00 00 00 00 00

Handle 0x0033, DMI type 127, 4 bytes
End Of Table




```

Hi, I did not see a mic listed any where so I am not sure how to proceed, maybe someone with more experience with mics can help.

---

### Post by wildmanne39 on 2011-05-17
> **xaegis said:**
> this is really long. Need the Handles too?

```
BIOS Information
        Vendor: Dell Inc.
        Version: A11
        Release Date: 08/03/2010
        Address: 0xE2D50
        Runtime Size: 119472 bytes
        ROM Size: 2048 kB
        Characteristics:
                PCI is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                5.25"/360 KB floppy services are supported (int 13h)
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 KB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                LS-120 boot is supported
                Smart battery is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported
                Targeted content distribution is supported
Handle 0x0002, DMI type 1, 27 bytes
System Information
        Manufacturer: Dell Inc.
        Product Name: Studio XPS 1645
        Version: A11 
        Serial Number: 4FX7SN1
        UUID: 44454C4C-4600-1058-8037-B4C04F534E31
        Wake-up Type: Power Switch
        SKU Number: Not Specified
        Family: Not Specified

Handle 0x0003, DMI type 2, 15 bytes
Base Board Information
        Manufacturer: Dell Inc.
        Product Name: 0VV228
        Version: A11
        Serial Number: .4FX7SN1.CN486430AT0054.
        Asset Tag:           
        Features: None
        Location In Chassis: Not Specified
        Chassis Handle: 0xFFFF
        Type: Unknown
        Contained Object Handles: 0

Handle 0x0004, DMI type 3, 21 bytes
Chassis Information
        Manufacturer: Dell Inc.
        Type: Portable
        Lock: Not Present
        Version: A11        
        Serial Number: 4FX7SN1
        Asset Tag:           
        Boot-up State: Safe
        Power Supply State: Safe
        Thermal State: Safe
        Security Status: None
        OEM Information: 0x00000000
        Height: Unspecified
        Number Of Power Cords: Unspecified
        Contained Elements: 0
Handle 0x0005, DMI type 4, 42 bytes
Processor Information
        Socket Designation: U2E1
        Type: Central Processor
        Family: <OUT OF SPEC>
        Manufacturer: Intel
        ID: E5 06 01 00 FF FB EB BF
        Version: CPU Version
        Voltage: 3.3 V
        External Clock: 133 MHz
        Max Speed: 4096 MHz
        Current Speed: 1600 MHz
        Status: Populated, Enabled
        Upgrade: ZIF Socket
        L1 Cache Handle: 0x0006
        L2 Cache Handle: 0x0007
        L3 Cache Handle: 0x0008
        Serial Number: Not Specified
        Asset Tag: Not Specified
        Part Number: Not Specified
        Core Count: 4
        Core Enabled: 4
        Thread Count: 8
        Characteristics:
                64-bit capable

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L1 Cache
        Configuration: Enabled, Socketed, Level 1
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 128 KB
        Maximum Size: 128 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
                Asynchronous
        Installed SRAM Type: Asynchronous
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Data
        Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L2 Cache
        Configuration: Enabled, Socketed, Level 2
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 1024 KB
        Maximum Size: 1024 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
Handle 0x0005, DMI type 4, 42 bytes
Processor Information
        Socket Designation: U2E1
        Type: Central Processor
        Family: <OUT OF SPEC>
        Manufacturer: Intel
        ID: E5 06 01 00 FF FB EB BF
        Version: CPU Version
        Voltage: 3.3 V
        External Clock: 133 MHz
        Max Speed: 4096 MHz
        Current Speed: 1600 MHz
        Status: Populated, Enabled
        Upgrade: ZIF Socket
        L1 Cache Handle: 0x0006
        L2 Cache Handle: 0x0007
        L3 Cache Handle: 0x0008
        Serial Number: Not Specified
        Asset Tag: Not Specified
        Part Number: Not Specified
        Core Count: 4
        Core Enabled: 4
        Thread Count: 8
        Characteristics:
                64-bit capable

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L1 Cache
        Configuration: Enabled, Socketed, Level 1
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 128 KB
        Maximum Size: 128 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
                Asynchronous
        Installed SRAM Type: Asynchronous
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Data
        Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L2 Cache
        Configuration: Enabled, Socketed, Level 2
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 1024 KB
        Maximum Size: 1024 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
Handle 0x0005, DMI type 4, 42 bytes
Processor Information
        Socket Designation: U2E1
        Type: Central Processor
        Family: <OUT OF SPEC>
        Manufacturer: Intel
        ID: E5 06 01 00 FF FB EB BF
        Version: CPU Version
        Voltage: 3.3 V
        External Clock: 133 MHz
        Max Speed: 4096 MHz
        Current Speed: 1600 MHz
        Status: Populated, Enabled
        Upgrade: ZIF Socket
        L1 Cache Handle: 0x0006
        L2 Cache Handle: 0x0007
        L3 Cache Handle: 0x0008
        Serial Number: Not Specified
        Asset Tag: Not Specified
        Part Number: Not Specified
        Core Count: 4
        Core Enabled: 4
        Thread Count: 8
        Characteristics:
                64-bit capable

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L1 Cache
        Configuration: Enabled, Socketed, Level 1
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 128 KB
        Maximum Size: 128 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
                Asynchronous
        Installed SRAM Type: Asynchronous
        Speed: Unknown
        Error Correction Type: Single-bit ECC
        System Type: Data
        Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L2 Cache
        Configuration: Enabled, Socketed, Level 2
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 1024 KB
        Maximum Size: 1024 KB
        Supported SRAM Types:
                Burst
                Pipeline Burst
               Asynchronous
        Installed SRAM Type: Burst
        Speed: Unknown
        Error Correction Type: None
        System Type: Other
        Associativity: 4-way Set-associative

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: Not Specified
        Internal Connector Type: None
        External Reference Designator: CRT
        External Connector Type: DB-15 female
        Port Type: Video Port

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J1A1
        Internal Connector Type: None
        External Reference Designator: Keyboard
        External Connector Type: Circular DIN-8 male
        Port Type: Keyboard Port

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J1A1
        Internal Connector Type: None
        External Reference Designator: PS/2 Mouse
        External Connector Type: Circular DIN-8 male
        Port Type: Mouse Port

Handle 0x000C, DMI type 9, 17 bytes
System Slot Information
        Designation: PEG Slot J6B2
        Type: 32-bit PCI Express
        Current Usage: Available
        Length: Long
        ID: 6
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x000D, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot J6B1
        Type: 32-bit PCI Express
        Current Usage: Available
        Length: Long
        ID: 7
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x000E, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot J6D1
        Type: 32-bit PCI Express
        Current Usage: In Use
        Length: Long
        ID: 8
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x000F, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot J8B3
        Type: 32-bit PCI Express
        Current Usage: Available
        Length: Long
        ID: 9
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x0010, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot J8D1
        Type: 32-bit PCI Express
        Current Usage: Available
        Length: Long
        ID: 10
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x0011, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot J7B1
        Type: 32-bit PCI Express
        Current Usage: In Use
        Length: Long
        ID: 11
        Characteristics:
                5.0 V is provided
                3.3 V is provided

Handle 0x0012, DMI type 9, 17 bytes
System Slot Information
        Designation: PCI Express Slot 6
        Type: 32-bit PCI Express
        Current Usage: In Use
        Length: Long
        ID: 12
        Characteristics:
                5.0 V is provided
                3.3 V is provided
Handle 0x0013, DMI type 10, 8 bytes
On Board Device 1 Information
        Type: Video
        Status: Enabled
        Description: Intel Arrandale Graphics    
On Board Device 2 Information
        Type: Sound
        Status: Enabled
        Description: Sigmatel 9273

Handle 0x0014, DMI type 11, 5 bytes
OEM Strings
        String 1: Dell System
        String 2: 5
        String 3: 13

Handle 0x0015, DMI type 15, 29 bytes
System Event Log
        Area Length: 16 bytes
        Header Start Offset: 0x0000
        Header Length: 16 bytes
        Data Start Offset: 0x0010
        Access Method: General-purpose non-volatile data functions
        Access Address: 0x0000
        Status: Valid, Not Full
        Change Token: 0x00000048
        Header Format: Type 1
        Supported Log Type Descriptors: 3
        Descriptor 1: POST error
        Data Format 1: POST results bitmap
        Descriptor 2: Single-bit ECC memory error
        Data Format 2: Multiple-event
        Descriptor 3: Multi-bit ECC memory error
        Data Format 3: Multiple-event

Handle 0x0016, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 8 GB
        Error Information Handle: Not Provided
        Number Of Devices: 2

Handle 0x0017, DMI type 17, 28 bytes
Memory Device
        Array Handle: 0x0016
        Error Information Handle: No Error
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: SODIMM
        Set: 1
        Locator: DIMM_A
       Bank Locator: Not Specified
        Type: <OUT OF SPEC>
        Type Detail: Synchronous
        Speed: 1333 MHz (0.8 ns)
        Manufacturer: 830B            
        Serial Number: 26A2127C        
        Asset Tag: 1028
        Part Number: NT2GC64B8HC0NS-CG 

Handle 0x0018, DMI type 17, 28 bytes
Memory Device
        Array Handle: 0x0016
        Error Information Handle: No Error
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: SODIMM
        Set: 1
        Locator: DIMM_B
        Bank Locator: Not Specified
        Type: <OUT OF SPEC>
        Type Detail: Synchronous
        Speed: 1333 MHz (0.8 ns)
        Manufacturer: 830B            
        Serial Number: 16A1127D        
        Asset Tag: 1028
        Part Number: NT2GC64B8HC0NS-CG 

Handle 0x0019, DMI type 18, 23 bytes
32-bit Memory Error Information
        Type: OK
        Granularity: Unknown
        Operation: Unknown
        Vendor Syndrome: Unknown
        Memory Array Address: Unknown
        Device Address: Unknown
        Resolution: Unknown

Handle 0x001A, DMI type 18, 23 bytes
32-bit Memory Error Information
        Type: OK
        Granularity: Unknown
        Operation: Unknown
        Vendor Syndrome: Unknown
        Memory Array Address: Unknown
        Device Address: Unknown
        Resolution: Unknown

Handle 0x001B, DMI type 19, 15 bytes
Memory Array Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x000FFFFFFFF
        Range Size: 4 GB
        Physical Array Handle: 0x0016
        Partition Width: 0

Handle 0x001C, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x0007FFFFFFF
        Range Size: 2 GB
        Physical Device Handle: 0x0017
        Memory Array Mapped Address Handle: 0x001B
        Partition Row Position: 1
        Interleaved Data Depth: 1

Handle 0x001D, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00080000000
        Ending Address: 0x000FFFFFFFF
        Range Size: 2 GB
        Physical Device Handle: 0x0018
        Memory Array Mapped Address Handle: 0x001B
        Partition Row Position: 1
        Interleaved Data Depth: 1

Handle 0x001E, DMI type 21, 7 bytes
Built-in Pointing Device
        Type: Touch Pad
        Interface: Bus Mouse
        Buttons: 2

Handle 0x001F, DMI type 22, 26 bytes
Portable Battery
        Location: System Battery Bay
        Manufacturer: SDI                 
        Name: SDI                 
        Design Capacity: 78000 mWh
        Design Voltage: 11100 mV
        SBDS Version: Bat123
        Maximum Error: Unknown
        SBDS Serial Number: 466C
        SBDS Manufacture Date: 2010-08-23
        SBDS Chemistry: LION  
        OEM-specific Information: 0x00000001

Handle 0x0020, DMI type 23, 13 bytes
System Reset
        Status: Enabled
        Watchdog Timer: Present
        Boot Option: Do Not Reboot
        Boot Option On Limit: Do Not Reboot
        Reset Count: Unknown
        Reset Limit: Unknown
        Timer Interval: Unknown
        Timeout: Unknown

Handle 0x0021, DMI type 24, 5 bytes

Handle 0x0023, DMI type 26, 20 bytes
Voltage Probe
        Description: Voltage Probe
        Location: Processor
        Status: OK
        Maximum Value: Unknown
        Minimum Value: Unknown
        Resolution: Unknown
        Tolerance: Unknown
        Accuracy: Unknown
        OEM-specific Information: 0x00000000

Handle 0x0024, DMI type 27, 12 bytes
Cooling Device
        Temperature Probe Handle: 0x0025
        Type: Fan
        Status: OK
        OEM-specific Information: 0x00000000

Handle 0x0025, DMI type 28, 20 bytes
Temperature Probe
        Description: Temperature Probe
        Location: Processor
        Status: OK
        Maximum Value: Unknown
        Minimum Value Unknown
        Resolution: Unknown
        Tolerance: Unknown
        Accuracy: Unknown
        OEM-specific Information: 0x00000000

Handle 0x0026, DMI type 29, 20 bytes
Electrical Current Probe
        Description: Electrical Current Probe
        Location: Processor
        Status: OK
        Maximum Value: Unknown
        Minimum Value: Unknown


Handle 0xB000, DMI type 176, 5 bytes
OEM-specific Type
        Header and Data:
                B0 05 00 B0 00

Handle 0xB100, DMI type 177, 12 bytes
OEM-specific Type
        Header and Data:
                B1 0C 00 B1 1A 06 00 00 00 00 00 00

Handle 0xD000, DMI type 208, 12 bytes
OEM-specific Type
        Header and Data:
                D0 0C 00 D0 01 05 FE 00 FE 02 32 30
        Strings:
                09010120090101

Handle 0xD300, DMI type 211, 17 bytes
OEM-specific Type
        Header and Data:
                D3 11 00 D3 46 72 6F 6E 74 03 02 01 00 31 33 35
                04

Handle 0xD400, DMI type 212, 17 bytes
OEM-specific Type
        Header and Data:
                D4 11 00 D4 70 00 71 00 00 10 2D 2E FF FF 00 00
                00

Handle 0xD800, DMI type 216, 9 bytes
OEM-specific Type
        Header and Data:
                D8 09 00 D8 01 02 01 F0 03
        Strings:
                Intel
                012.020.000.035.035105

Handle 0xDC00, DMI type 220, 20 bytes
OEM-specific Type
        Header and Data:
                DC 14 00 DC 01 F0 00 00 02 F0 00 00 03 F0 04 F0
                00 00 00 00

Handle 0xDD00, DMI type 221, 19 bytes
OEM-specific Type
        Header and Data:
                DD 13 00 DD 00 00 00 00 00 00 00 00 00 00 00 00
                00 00 00

Handle 0xDE00, DMI type 222, 16 bytes
OEM-specific Type
        Header and Data:
                DE 10 00 DE 01 02 FF FF 00 00 00 00 00 00 00 00

Handle 0x0033, DMI type 127, 4 bytes
End Of Table




```

Bump

---

### Post by retropdarb on 2011-07-27
I am having a similar problem.  Was this ever solved?  Thanks.

---

### Post by xaegis on 2011-07-27
oops, yes I solved this. :)

in terminal:
```
computer@TheComputer:~$ alsamixer
```

press "F4" for capture


There you can go in and un-mute your internal microphone and make sure it is selected as a capture source.

You might have to play with it a bit to get it right but this is what solved my problems on a a dell xps 16 and a dell Inspiron M5030

HTH

Cheers

-e

---

### Post by tlyman1141 on 2011-08-07
Hey guys, this is an issue that has bothered me since I switched to Ubuntu 11.04 32bit.... When it was a clean install, the internal mic on my HP Pavillion DV7 (only a year old) worked, and then it just stopped. I have tried a few things and am still an uber-noob when dealing with Linux. We all gotta start somewhere though right? I am going to post the "lspci" and hopefully someone can help me figure this out. I have already gone in and unmuted the mic through both sound settings and pavucontrol and alsamixer as well, and will keep working on it.


dragonwolf@DWL-HP-Pavilion-dv7-Notebook-PC:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc RV710/730
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
dragonwolf@DWL-HP-Pavilion-dv7-Notebook-PC:~$ 



Any help would be a lot of help, Thanks guys!!

---

