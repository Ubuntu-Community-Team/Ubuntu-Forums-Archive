---
title: "HDD only works when Trackpad or Keyboard used"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by david.pagan on 2009-10-28
This is truly the group for me. And a very exciting group to begin with. I have installed Xubuntu 9.04 on my Acer Travelmate 280. Everything so far works fine apart from the hard drive only functions when I either move my finger on the trackpad or type something in the keyboard. 

Any ideas?

 I am only running 256MB ram at the moment until more comes in the post. Would that anything to do with it?

Also I put a new/old 80GB harddrive into the machine before installing everything. This problem of the harddrive happened during installation although it did manage to move on a little by itself.

I have resorted to leaving the adaptor-transformer resting on the Space bar!! I hope this won't always be necessary?

Any help is gratefully accepted

 David

---

### Post by kerry_s on 2009-10-28
i don't understand.
how can it not be working if your using the os?

---

### Post by CharlesA on 2009-10-28
> **kerry_s said:**
> i don't understand.
how can it not be working if your using the os?

This.

Needs more infos.

---

### Post by ukripper on 2009-10-28
Can you run the following and post the output as needed:

```
sudo apt-get install smartmontools
```

and then post output of the below command:
```
sudo smartctl -a /dev/sda
```
*assuming it is sda device if it is something else like sdb then replace it with sdb.

---

### Post by david.pagan on 2009-10-28
Thanks guys for the super quick replies.

Everything is working fine but if I don't keep moving the mouse cursor around or touching the keyboard after about a second the computer just pauses. It doesn't crash it just stops doing what it has been doing.

In the system monitor the lines move along for a second after I have let go and then they stop.

Is that any clearer?

Thanks

David

---

### Post by ukripper on 2009-10-28
> **david.pagan said:**
> Thanks guys for the super quick replies.

Everything is working fine but if I don't keep moving the mouse cursor around or touching the keyboard after about a second the computer just pauses. It doesn't crash it just stops doing what it has been doing.

In the system monitor the lines move along for a second after I have let go and then they stop.

Is that any clearer?

Thanks

David

Can you do as my above post and post the output here?

---

### Post by kerry_s on 2009-10-28
> **david.pagan said:**
> Thanks guys for the super quick replies.

Everything is working fine but if I don't keep moving the mouse cursor around or touching the keyboard after about a second the computer just pauses. It doesn't crash it just stops doing what it has been doing.

In the system monitor the lines move along for a second after I have let go and then they stop.

Is that any clearer?

Thanks

David

i bet you have intel graphics, turn off the effects in appearance.

---

### Post by david.pagan on 2009-10-28
Here you go ukripper,

I hope this is what you meant! like I said I very new to all this.

Thanks:D



davidpagan@davidpagan-laptop:~$ sudo smartctl -a /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD series (80 GB and above)
Device Model:     TOSHIBA MK8026GAX
Serial Number:    Z4Q30515S
Firmware Version: PA005B
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Oct 28 13:25:53 2009 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          ( 303) seconds.
Offline data collection
capabilities:              (0x1b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    No Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    No General Purpose Logging support.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  60) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1322
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       8772
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       5
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   071   071   000    Old_age   Always       -       11642
 10 Spin_Retry_Count        0x0033   253   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       5870
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       61
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       1033980
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       48 (Lifetime Min/Max 1/52)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       5
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       154
222 Loaded_Hours            0x0032   084   084   000    Old_age   Always       -       6730
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       243
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 2595 (device log contains only the most recent five errors)
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 2595 occurred at disk power-on lifetime: 10514 hours (438 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 18 28 9e 16 40  Error: UNC 24 sectors at LBA = 0x00169e28 = 1482280

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 40 00 9e 16 40 00      02:23:33.364  READ DMA EXT
  25 00 40 00 9e 16 40 00      02:23:26.544  READ DMA EXT
  25 00 40 00 9e 16 40 00      02:23:19.755  READ DMA EXT
  25 00 40 00 9e 16 40 00      02:23:12.955  READ DMA EXT
  25 00 40 00 9e 16 40 00      02:23:06.160  READ DMA EXT

Error 2594 occurred at disk power-on lifetime: 10514 hours (438 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 18 28 9e 16 40  Error: UNC 24 sectors at LBA = 0x00169e28 = 1482280

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 40 00 9e 16 40 00      02:23:26.544  READ DMA EXT
  25 00 40 00 9e 16 40 00      02:23:19.755  READ DMA EXT
  25 00 40 00 9e 16 40 00      02:23:12.955  READ DMA EXT
  25 00 40 00 9e 16 40 00      02:23:06.160  READ DMA EXT
  25 00 40 40 8d 07 40 00      02:23:06.160  READ DMA EXT

Error 2593 occurred at disk power-on lifetime: 10514 hours (438 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 18 28 9e 16 40  Error: UNC 24 sectors at LBA = 0x00169e28 = 1482280

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 40 00 9e 16 40 00      02:23:19.755  READ DMA EXT
  25 00 40 00 9e 16 40 00      02:23:12.955  READ DMA EXT
  25 00 40 00 9e 16 40 00      02:23:06.160  READ DMA EXT
  25 00 40 40 8d 07 40 00      02:23:06.160  READ DMA EXT
  25 00 40 40 8c 07 40 00      02:23:06.159  READ DMA EXT

Error 2592 occurred at disk power-on lifetime: 10514 hours (438 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 18 28 9e 16 40  Error: UNC 24 sectors at LBA = 0x00169e28 = 1482280

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 40 00 9e 16 40 00      02:23:12.955  READ DMA EXT
  25 00 40 00 9e 16 40 00      02:23:06.160  READ DMA EXT
  25 00 40 40 8d 07 40 00      02:23:06.160  READ DMA EXT
  25 00 40 40 8c 07 40 00      02:23:06.159  READ DMA EXT
  25 00 40 c0 8d 07 40 00      02:23:06.158  READ DMA EXT

Error 2591 occurred at disk power-on lifetime: 10514 hours (438 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 18 28 9e 16 40  Error: UNC 24 sectors at LBA = 0x00169e28 = 1482280

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 40 00 9e 16 40 00      02:23:06.160  READ DMA EXT
  25 00 40 40 8d 07 40 00      02:23:06.160  READ DMA EXT
  25 00 40 40 8c 07 40 00      02:23:06.159  READ DMA EXT
  25 00 40 c0 8d 07 40 00      02:23:06.158  READ DMA EXT
  25 00 40 00 8c 07 40 00      02:23:06.157  READ DMA EXT

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Device does not support Selective Self Tests/Logging
davidpagan@davidpagan-laptop:~$

---

### Post by ukripper on 2009-10-28
Thats great! can you run the following now and post output, just want to make sure your HDD is sane:
```
smartctl -l selftest /dev/sda
```

---

### Post by david.pagan on 2009-10-28
davidpagan@davidpagan-laptop:~$ smartctl -l selftest /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl open device: /dev/sda failed: Permission denied
davidpagan@davidpagan-laptop:~$ 



Is that any help? this is what happened

---

### Post by philinux on 2009-10-28
```
sudo smartctl -l selftest /dev/sda
```

---

### Post by david.pagan on 2009-10-28
davidpagan@davidpagan-laptop:~$ sudo smartctl -l selftest /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


davidpagan@davidpagan-laptop:~$ 

how is that?!

---

### Post by ukripper on 2009-10-28
> **david.pagan said:**
> davidpagan@davidpagan-laptop:~$ sudo smartctl -l selftest /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


davidpagan@davidpagan-laptop:~$ 

how is that?!

Looks it didn't work. Can you run this instead:
```
sudo smartctl -H /dev/sda
```

---

### Post by david.pagan on 2009-10-28
davidpagan@davidpagan-laptop:~$ sudo smartctl -H /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

davidpagan@davidpagan-laptop:~$ 


That seems positive!:D

---

### Post by ukripper on 2009-10-28
> **david.pagan said:**
> davidpagan@davidpagan-laptop:~$ sudo smartctl -H /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

davidpagan@davidpagan-laptop:~$ 


That seems positive!:D

Can you post output of the following command so that we can see what is you system spec and how much memory it has:
```
sudo dmidecode
```

and this to check how much memory is being used:
```
free -m
```

---

### Post by david.pagan on 2009-10-28
davidpagan@davidpagan-laptop:~$ sudo dmidecode
# dmidecode 2.9
SMBIOS 2.31 present.
36 structures occupying 1221 bytes.
Table at 0x000E9000.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
    Vendor: Phoenix Technologies LTD
    Version: R01-A0R        
    Release Date: 01/29/2003
    Address: 0xE2970
    Runtime Size: 120464 bytes
    ROM Size: 512 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PC Card (PCMCIA) is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        ACPI is supported
        USB legacy is supported
        AGP is supported
        Smart battery is supported
        BIOS boot specification is supported

Handle 0x0001, DMI type 1, 25 bytes
System Information
    Manufacturer: Acer           
    Product Name: TravelMate 280 
    Version: -1             
    Serial Number: LXT2206016314C1B61M000        
    UUID: 89B14CC0-662D-11D7-98A6-AD2FA9F175B2
    Wake-up Type: Power Switch

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: WISTRON        
    Product Name: GENERIC        
    Version: Rev.A          
    Serial Number: LXT2206016314C1B61M000        

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
    Manufacturer: Acer           
    Type: Other
    Lock: Not Present
    Version: N/A            
    Serial Number: None           
    Asset Tag:                                 
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00001234

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
    Socket Designation: WMT478/NWD
    Type: Central Processor
    Family: Pentium 4
    Manufacturer: Intel
    ID: 27 0F 00 00 FF FB EB BF
    Signature: Type 0, Family 15, Model 2, Stepping 7
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
        FXSR (Fast floating-point save and restore)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        SS (Self-snoop)
        HTT (Hyper-threading technology)
        TM (Thermal monitor supported)
        PBE (Pending break enabled)
    Version: A0
    Voltage: 1.8 V
    External Clock: Unknown
    Max Speed: 1500 MHz
    Current Speed: 1200 MHz
    Status: Populated, Enabled
    Upgrade: Slot 1
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: Not Provided
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1 Cache
    Configuration: Enabled, Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 20 KB
    Maximum Size: 20 KB
    Supported SRAM Types:
        Burst
        Pipeline Burst
        Asynchronous
    Installed SRAM Type: Asynchronous
    Speed: Unknown
    Error Correction Type: Unknown
    System Type: Unknown
    Associativity: Unknown

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2 Cache
    Configuration: Enabled, Socketed, Level 2
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 512 KB
    Maximum Size: 512 KB
    Supported SRAM Types:
        Burst
        Pipeline Burst
        Asynchronous
    Installed SRAM Type: Burst
    Speed: Unknown
    Error Correction Type: Unknown
    System Type: Unknown
    Associativity: Unknown

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L3 Cache
    Configuration: Enabled, Socketed, Level 3
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 512 KB
    Maximum Size: 512 KB
    Supported SRAM Types:
        Burst
        Pipeline Burst
        Asynchronous
    Installed SRAM Type: Burst
    Speed: Unknown
    Error Correction Type: Unknown
    System Type: Unknown
    Associativity: Unknown

Handle 0x0008, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2A1
    Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
    External Reference Designator: COM 1
    External Connector Type: DB-9 male
    Port Type: Serial Port 16550A Compatible

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3A1
    Internal Connector Type: 25 Pin Dual Inline (pin 26 cut)
    External Reference Designator: Parallel
    External Connector Type: DB-25 female
    Port Type: Parallel Port ECP/EPP

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
    Port Type: Keyboard Port

Handle 0x000C, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI Slot #1 - J6B3
    Type: 32-bit PCI
    Current Usage: Unknown
    Length: Long
    ID: 0
    Characteristics:
        5.0 V is provided
        3.3 V is provided

Handle 0x000D, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI Slot #2 - J6B2
    Type: 32-bit PCI
    Current Usage: Unknown
    Length: Long
    ID: 0
    Characteristics:
        5.0 V is provided
        3.3 V is provided

Handle 0x000E, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI Slot #3 - J7B1
    Type: 32-bit PCI
    Current Usage: Unknown
    Length: Long
    ID: 0
    Characteristics:
        5.0 V is provided
        3.3 V is provided

Handle 0x000F, DMI type 10, 6 bytes
On Board Device Information
    Type: Sound
    Status: Disabled
    Description: ADI1886

Handle 0x0010, DMI type 11, 5 bytes
OEM Strings
    String 1: This is the Intel NBVV-G
    String 2: System Validation Platform

Handle 0x0011, DMI type 12, 5 bytes
System Configuration Options
    Option 1: Jumper settings can be described here.

Handle 0x0012, DMI type 15, 29 bytes
System Event Log
    Area Length: 32 bytes
    Header Start Offset: 0x0000
    Header Length: 16 bytes
    Data Start Offset: 0x0010
    Access Method: General-purpose non-volatile data functions
    Access Address: 0x0000
    Status: Invalid, Not Full
    Change Token: 0x00000000
    Header Format: Type 1
    Supported Log Type Descriptors: 3
    Descriptor 1: POST error
    Data Format 1: POST results bitmap
    Descriptor 2: Single-bit ECC memory error
    Data Format 2: Multiple-event
    Descriptor 3: Multi-bit ECC memory error
    Data Format 3: Multiple-event

Handle 0x0013, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 512 MB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x0014, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0013
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 256 MB
    Form Factor: DIMM
    Set: 1
    Locator: J5G3
    Bank Locator: DIMM 0
    Type: DDR
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

Handle 0x0015, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0013
    Error Information Handle: No Error
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: 1
    Locator: J5G2
    Bank Locator: DIMM 1
    Type: DDR
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

Handle 0x0016, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0000FFFFFFF
    Range Size: 256 MB
    Physical Array Handle: 0x0013
    Partition Width: 0

Handle 0x0017, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0000FFFFFFF
    Range Size: 256 MB
    Physical Device Handle: 0x0014
    Memory Array Mapped Address Handle: 0x0016
    Partition Row Position: 1

Handle 0x0018, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x0000FFFFC00
    Ending Address: 0x0000FFFFFFF
    Range Size: 1 kB
    Physical Device Handle: 0x0015
    Memory Array Mapped Address Handle: 0x0016
    Partition Row Position: 1

Handle 0x0019, DMI type 23, 13 bytes
System Reset
    Status: Enabled
    Watchdog Timer: Present
    Boot Option: Do Not Reboot
    Boot Option On Limit: Do Not Reboot
    Reset Count: Unknown
    Reset Limit: Unknown
    Timer Interval: Unknown
    Timeout: Unknown

Handle 0x001A, DMI type 24, 5 bytes
Hardware Security
    Power-On Password Status: Enabled
    Keyboard Password Status: Unknown
    Administrator Password Status: Enabled
    Front Panel Reset Status: Unknown

Handle 0x001B, DMI type 25, 9 bytes
    System Power Controls
    Next Scheduled Power-on: 12-31 23:59:59

Handle 0x001C, DMI type 26, 20 bytes
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

Handle 0x001D, DMI type 27, 12 bytes
Cooling Device
    Temperature Probe Handle: 0x001E
    Type: Fan
    Status: OK
    OEM-specific Information: 0x00000000

Handle 0x001E, DMI type 28, 20 bytes
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

Handle 0x001F, DMI type 29, 20 bytes
Electrical Current Probe
    Description: Electrical Current Probe
    Location: Processor
    Status: OK
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000

Handle 0x0020, DMI type 30, 6 bytes
Out-of-band Remote Access
    Manufacturer Name: Intel
    Inbound Connection: Enabled
    Outbound Connection: Disabled

Handle 0x0021, DMI type 32, 20 bytes
System Boot Information
    Status: <OUT OF SPEC>

Handle 0x0022, DMI type 126, 4 bytes
Inactive

Handle 0x0023, DMI type 127, 4 bytes
End Of Table

davidpagan@davidpagan-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           243        214         29          0          4         72
-/+ buffers/cache:        137        106
Swap:          721        172        549
davidpagan@davidpagan-laptop:~$

---

### Post by ukripper on 2009-10-28
Can you reboot and boot into XUBUNTU live cd and see if you get the same problem?

---

### Post by david.pagan on 2009-10-28
Unfortunately, it still does. Does it matter that it was the version before of Xubuntu.

---

### Post by ukripper on 2009-10-28
> **david.pagan said:**
> Unfortunately, it still does. Does it matter that it was the version before of Xubuntu.

ok lets try this. Boot normally and install LXDE, it is a light weight desktop environment. after it is installed you need to logout and select LXDE from session at login screen.Let us know how it goes. Install it by following this link:
[http://navaspot.wordpress.com/2009/03/06/install-lxde-on-ubuntu/](http://navaspot.wordpress.com/2009/03/06/install-lxde-on-ubuntu/)

If it works for you that would mean xubuntu was too heavy for your system.

EDIT: As you'r using Hardy(8.04) i have updated the link above so follow that.

---

### Post by kerry_s on 2009-10-28
i'm telling you it's compiz, since your in xfce4, just go into synaptic & uninstall it.

i'm pretty sure i've seen exactly what he's talking about, progress bars look like they froze, things just stop like a snapshot of that moment, then when you move the mouse the screen catches up, till it stops again after a couple of seconds.

---

### Post by sydbat on 2009-10-28
> **kerry_s said:**
> i'm telling you it's compiz, since your in xfce4, just go into synaptic & uninstall it.

i'm pretty sure i've seen exactly what he's talking about, progress bars look like they froze, things just stop like a snapshot of that moment, then when you move the mouse the screen catches up, till it stops again after a couple of seconds.This.

---

### Post by ukripper on 2009-10-29
> **kerry_s said:**
> i'm telling you it's compiz, since your in xfce4, just go into synaptic & uninstall it.

i'm pretty sure i've seen exactly what he's talking about, progress bars look like they froze, things just stop like a snapshot of that moment, then when you move the mouse the screen catches up, till it stops again after a couple of seconds.

I think OP should give this a try! i thought he did before?

---

