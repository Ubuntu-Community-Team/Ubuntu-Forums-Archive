---
title: "freezing on shut down"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by L2U2K2E on 2010-08-12
Lately, every time I shut down my laptop with lucid installed It freezes before the computer is totally shut down. The system appears to logg out of my account and Gnome in general, but gets stuck around the ubuntu screen just before shutdown. the screen slightly pixel-ates and just stays.

I am not sure if this is strictly an ubuntu problem as I recently updated my BIOS as well.

---

### Post by dfirsov on 2010-08-12
same here on my laptop inspiron 1545 with Ubuntu 10.04 :confused:

---

### Post by Bhavik_UK on 2010-08-12
I'm having this issue as well.

I've just installed Ubuntu onto a PC and for some reason when I click shutdown, it leaves the OS and goes to the Ubuntu screen with the 5 dots, two of the dots go red and then it just sits there.

Any ideas on how this can be resolved?

---

### Post by L2U2K2E on 2010-08-12
Confusing. perhaps this is a recent ubuntu bug? Has anyone started recently experiencing this or has it been happening for some time?

---

### Post by vagrale13 on 2010-08-12
Try to shutdown with command
```
sudo shutdown -P now
```

---

### Post by L2U2K2E on 2010-08-12
> **vagrale13 said:**
> Try to shutdown with command
```
sudo shutdown -P now
```
Tried that. Same problem. Ubuntu logo pops up, 3 dots turn red, then It just stops.

---

### Post by vagrale13 on 2010-08-12
Press **Ctrl+Alt+F2** to get out of graphic,
and then try again to shutdown with the command and see where freeze it
and post the last messages!

---

### Post by L2U2K2E on 2010-08-12
I tried the ctrl+alt+f2 command, then shut the computer down with the command line. Unfortunately, It scrolled quickly through a bunch of shutdown script, and then cut to the Ubuntu icon with the 5 dots under it, and the system would not let me go back to the command line interface. It got stuck again at 3 red dots

---

### Post by vagrale13 on 2010-08-13
Is clear install or upgrade from 9.10?
Can you give the output of commands
```
uname -a
``````
lspci -nn
```This problem when it was presented, after install or after you upgrade bios,
or after something else?

---

### Post by L2U2K2E on 2010-08-13
> **vagrale13 said:**
> Is clear install or upgrade from 9.10?
Can you give the output of commands
```
uname -a
```
```
Linux luke-laptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux
```

> **vagrale13 said:**
> ```
lspci -nn
```
```
00:00.0 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0754] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation Device [10de:075e] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP78S [GeForce 8200] SMBus [10de:0752] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP78S [GeForce 8200] Co-Processor [10de:0753] (rev a2)
00:01.4 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0568] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077b] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077c] (rev a1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077d] (rev a1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077e] (rev a1)
00:06.0 IDE interface [0101]: nVidia Corporation MCP78S [GeForce 8200] IDE [10de:0759] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio [10de:0774] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:075a] (rev a1)
00:09.0 SATA controller [0106]: nVidia Corporation Device [10de:0ad5] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP77 Ethernet [10de:0760] (rev a2)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:0778] (rev a1)
00:12.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:075b] (rev a1)
00:13.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:077a] (rev a1)
00:14.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:077a] (rev a1)
00:16.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:077a] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control [1022:1304]
02:00.0 VGA compatible controller [0300]: nVidia Corporation G96 [GeForce 9600M GT] [10de:0649] (rev a1)
03:00.0 Network controller [0280]: RaLink RT2860 [1814:0781]
08:00.0 FireWire (IEEE 1394) [0c00]: JMicron Technology Corp. IEEE 1394 Host Controller [197b:2380]
08:00.1 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
08:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
08:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
08:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]
```


The problem came after I updated my BIOS, but if I remember correctly, it did not happen the first few times I shut down after updating my BIOS.

---

### Post by vagrale13 on 2010-08-14
Try to boot with oldest kernel, of grub menu, e.g. *2.6.32.21-generic*
and test it if is ok there!

Another you can try is to logout first and then to try shutdown.

If the problem persists after these tests, post the output of
```
sudo dmidecode
```> **L2U2K2E said:**
> The problem came after I updated my BIOS, but if I  remember correctly, it did not happen the first few times I shut down  after updating my BIOS.
Why you upgrade *BIOS*? :confused:
I think if you hadn' t problems, you mustn' t upgrade your BIOS.

---

### Post by L2U2K2E on 2010-08-14
I ended up just reinstalling ubuntu to move my /home to a separate partition, and it fixed this freezing problem as well.

> **vagrale13 said:**
> I think if you hadn' t problems, you mustn' t upgrade your BIOS.
I hoped that the new BIOS might have some sort of improved temperature control as the older one didn't have any (no such luck)

---

### Post by vagrale13 on 2010-08-14
> **L2U2K2E said:**
> I ended up just reinstalling ubuntu to move my /home to a separate partition, and it fixed this freezing problem as well.
Glad, but i though not a solution a reinstalling, we could fixed more easily believe! :popcorn:

> **L2U2K2E said:**
> I hoped that the new BIOS might have some sort of improved temperature control as the older one didn't have any (no such luck)
If you have problems with sensors, look here [http://forum.ubuntu-gr.org/viewtopic.php?f=9&t=10150](http://forum.ubuntu-gr.org/viewtopic.php?f=9&t=10150)
but it' s in *greek language*! :guitar:

---

### Post by L2U2K2E on 2010-08-14
FALSE ALARM! not solved   :(   The computer shut down fine a few times after reinstall, but then started the same problems again. I tried to log out and then shut down, which worked once, but after that the same freezing problems persisted.

> **vagrale13 said:**
> Try to boot with oldest kernel, of grub menu, e.g. *2.6.32.21-generic*
and test it if is ok there!
how do I do that?  :/

> **vagrale13 said:**
> If the problem persists after these tests, post the output of
```
sudo dmidecode
```
```
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
    Manufacturer: Micro-Star International
    Type: Notebook
    Lock: Not Present
    Version: Ver.001
    Serial Number: FFFFFFFF
    Asset Tag: To Be Filled By O.E.M.
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
    Socket Designation: CPU 1
    Type: Central Processor
    Family: Dual-Core Opteron
    Manufacturer: AMD Athlon(tm) X 
    ID: 31 0F 20 00 FF FB 8B 17
    Signature: Family 17, Model 3, Stepping 1
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
        MMX (MMX technology supported)
        FXSR (Fast floating-point save and restore)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        HTT (Hyper-threading technology)
    Version: AMD Athlon(tm) X2 Dual-Core QL-62              
    Voltage: 0.0 V
    External Clock: Unknown
    Max Speed: 12288 MHz
    Current Speed: 2000 MHz
    Status: Populated, Enabled
    Upgrade: Socket 940
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: Not Provided
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Part Number: To Be Filled By O.E.M.

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1-Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 64 KB
    Maximum Size: 64 KB
    Supported SRAM Types:
        Unknown
    Installed SRAM Type: Unknown
    Speed: Unknown
    Error Correction Type: None
    System Type: Unified
    Associativity: 2-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2-Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Varies With Memory Address
    Location: Internal
    Installed Size: 512 KB
    Maximum Size: 512 KB
    Supported SRAM Types:
        Unknown
    Installed SRAM Type: Unknown
    Speed: Unknown
    Error Correction Type: None
    System Type: Data
    Associativity: 8-way Set-associative

Handle 0x0007, DMI type 126, 19 bytes
Inactive

Handle 0x0008, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1A1
    Internal Connector Type: None
    External Reference Designator: PS2Mouse
    External Connector Type: PS/2
    Port Type: Mouse Port

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1A1
    Internal Connector Type: None
    External Reference Designator: Keyboard
    External Connector Type: PS/2
    Port Type: Keyboard Port

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2A1
    Internal Connector Type: None
    External Reference Designator: TV Out
    External Connector Type: Mini Centronics Type-14
    Port Type: Other

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2A2A
    Internal Connector Type: None
    External Reference Designator: COM A
    External Connector Type: DB-9 male
    Port Type: Serial Port 16550A Compatible

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2A2B
    Internal Connector Type: None
    External Reference Designator: Video
    External Connector Type: DB-15 female
    Port Type: Video Port

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3A1
    Internal Connector Type: None
    External Reference Designator: USB1
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3A1
    Internal Connector Type: None
    External Reference Designator: USB2
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3A1
    Internal Connector Type: None
    External Reference Designator: USB3
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9A1 - TPM HDR
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9C1 - PCIE DOCKING CONN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2B3 - CPU FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J6C2 - EXT HDMI
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3C1 - GMCH FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1D1 - ITP
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9E2 - MDC INTPSR
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9E4 - MDC INTPSR
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9E3 - LPC HOT DOCKING
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9E1 - SCAN MATRIX
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9G1 - LPC SIDE BAND
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J8F1 - UNIFIED
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J6F1 - LVDS
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2F1 - LAI FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2G1 - GFX VID
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1G6 - AC JACK
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0020, DMI type 9, 13 bytes
System Slot Information
    Designation: J6B2
    Type: x16 PCI Express
    Current Usage: In Use
    Length: Long
    ID: 0
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0021, DMI type 9, 13 bytes
System Slot Information
    Designation: J6B1
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 1
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0022, DMI type 9, 13 bytes
System Slot Information
    Designation: J6D1
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 2
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0023, DMI type 9, 13 bytes
System Slot Information
    Designation: J7B1
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 3
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0024, DMI type 9, 13 bytes
System Slot Information
    Designation: J8B4
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 4
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0025, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Enabled
    Description:    To Be Filled By O.E.M.

Handle 0x0026, DMI type 11, 5 bytes
OEM Strings
    String 1: 0010DC000150AEC0
    String 2: 002185E4A5E5

Handle 0x0027, DMI type 12, 5 bytes
System Configuration Options
    Option 1: To Be Filled By O.E.M.

Handle 0x0028, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

Handle 0x0029, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 2048 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x002A, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0013FFFFFFF
    Range Size: 5 GB
    Physical Array Handle: 0x0029
    Partition Width: 0

Handle 0x002B, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0029
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: A1_DIMM0
    Bank Locator: A1_BANK0
    Type: <OUT OF SPEC>
    Type Detail: Synchronous
    Speed: 333 MHz (3.0 ns)
    Manufacturer: A1_Manufacturer0
    Serial Number: A1_SerNum0
    Asset Tag: A1_AssetTagNum0
    Part Number: A1_PartNum0

Handle 0x002C, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x002B
    Memory Array Mapped Address Handle: 0x002A
    Partition Row Position: 1

Handle 0x002D, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0029
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: A1_DIMM1
    Bank Locator: A1_BANK1
    Type: <OUT OF SPEC>
    Type Detail: Synchronous
    Speed: 333 MHz (3.0 ns)
    Manufacturer: A1_Manufacturer1
    Serial Number: A1_SerNum1
    Asset Tag: A1_AssetTagNum1
    Part Number: A1_PartNum1

Handle 0x002E, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00080000000
    Ending Address: 0x000FFFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x002D
    Memory Array Mapped Address Handle: 0x002A
    Partition Row Position: 1

Handle 0x002F, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0029
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: 64 bits
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: A1_DIMM2
    Bank Locator: A1_BANK2
    Type: DDR2
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: A1_Manufacturer2
    Serial Number: A1_SerNum2
    Asset Tag: A1_AssetTagNum2
    Part Number: A1_PartNum2

Handle 0x0030, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000000003FF
    Range Size: 1 kB
    Physical Device Handle: 0x002F
    Memory Array Mapped Address Handle: 0x002A
    Partition Row Position: 1

Handle 0x0031, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0029
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: 64 bits
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: A1_DIMM3
    Bank Locator: A1_BANK3
    Type: DDR2
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: A1_Manufacturer3
    Serial Number: A1_SerNum3
    Asset Tag: A1_AssetTagNum3
    Part Number: A1_PartNum3

Handle 0x0032, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000000003FF
    Range Size: 1 kB
    Physical Device Handle: 0x0031
    Memory Array Mapped Address Handle: 0x002A
    Partition Row Position: 1

Handle 0x0033, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x0034, DMI type 127, 4 bytes
End Of Table

```

---

### Post by vagrale13 on 2010-08-15
> **L2U2K2E said:**
> FALSE ALARM! not solved   :(   The computer shut down fine a few times after reinstall, but then started the same problems again. I tried to log out and then shut down, which worked once, but after that the same freezing problems persisted.


how do I do that?  :/
Before the grub loading, hold down **Shift** and then from the boot options 
select an oldest kernel to continue.

Because is missed some info of the previous command,run
```
sudo dmidecode aux > info.txt
```and post the content of the file *info.txt* where create to your [I]home

[/I]Also, try to disable the closed drivers for your graphics card, 
(*system - **administration - hardware&drivers*)
if they have enabled, and tried to see if anything changed.

---

### Post by L2U2K2E on 2010-08-16
> **vagrale13 said:**
> Before the grub loading, hold down **Shift** and then from the boot options 
select an oldest kernel to continue.
with the slightly older kernel (2.6.31)
The system still freezes on shutdown, but also has some graphics problems.

> Because is missed some info of the previous command,run
```
sudo dmidecode aux > info.txt
```and post the content of the file *info.txt* where create to your *home*```
# dmidecode 2.9
SMBIOS 2.4 present.
53 structures occupying 2062 bytes.
Table at 0xBFB4F018.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: E1652NMS VER.10P
    Release Date: 12/02/2009
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 1024 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 4.6

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Micro-Star International
    Product Name: GX630/GX633
    Version: Ver.001
    Serial Number: FFFFFFFF
    UUID: 00000000-0000-0000-0000-002185E4A5E5
    Wake-up Type: Power Switch
    SKU Number: To be filled by O.E.M.
    Family: To be filled by O.E.M.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: Micro-Star International
    Product Name: GX630/GX633
    Version: Ver.001
    Serial Number: FFFFFFFF
    Asset Tag: To be filled by O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To be filled by O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
    Manufacturer: Micro-Star International
    Type: Notebook
    Lock: Not Present
    Version: Ver.001
    Serial Number: FFFFFFFF
    Asset Tag: To Be Filled By O.E.M.
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
    Socket Designation: CPU 1
    Type: Central Processor
    Family: Dual-Core Opteron
    Manufacturer: AMD Athlon(tm) X 
    ID: 31 0F 20 00 FF FB 8B 17
    Signature: Family 17, Model 3, Stepping 1
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
        MMX (MMX technology supported)
        FXSR (Fast floating-point save and restore)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        HTT (Hyper-threading technology)
    Version: AMD Athlon(tm) X2 Dual-Core QL-62              
    Voltage: 0.0 V
    External Clock: Unknown
    Max Speed: 12288 MHz
    Current Speed: 2000 MHz
    Status: Populated, Enabled
    Upgrade: Socket 940
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: Not Provided
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Part Number: To Be Filled By O.E.M.

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1-Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 64 KB
    Maximum Size: 64 KB
    Supported SRAM Types:
        Unknown
    Installed SRAM Type: Unknown
    Speed: Unknown
    Error Correction Type: None
    System Type: Unified
    Associativity: 2-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2-Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Varies With Memory Address
    Location: Internal
    Installed Size: 512 KB
    Maximum Size: 512 KB
    Supported SRAM Types:
        Unknown
    Installed SRAM Type: Unknown
    Speed: Unknown
    Error Correction Type: None
    System Type: Data
    Associativity: 8-way Set-associative

Handle 0x0007, DMI type 126, 19 bytes
Inactive

Handle 0x0008, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1A1
    Internal Connector Type: None
    External Reference Designator: PS2Mouse
    External Connector Type: PS/2
    Port Type: Mouse Port

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1A1
    Internal Connector Type: None
    External Reference Designator: Keyboard
    External Connector Type: PS/2
    Port Type: Keyboard Port

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2A1
    Internal Connector Type: None
    External Reference Designator: TV Out
    External Connector Type: Mini Centronics Type-14
    Port Type: Other

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2A2A
    Internal Connector Type: None
    External Reference Designator: COM A
    External Connector Type: DB-9 male
    Port Type: Serial Port 16550A Compatible

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2A2B
    Internal Connector Type: None
    External Reference Designator: Video
    External Connector Type: DB-15 female
    Port Type: Video Port

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3A1
    Internal Connector Type: None
    External Reference Designator: USB1
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3A1
    Internal Connector Type: None
    External Reference Designator: USB2
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3A1
    Internal Connector Type: None
    External Reference Designator: USB3
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9A1 - TPM HDR
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9C1 - PCIE DOCKING CONN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2B3 - CPU FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J6C2 - EXT HDMI
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3C1 - GMCH FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1D1 - ITP
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9E2 - MDC INTPSR
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9E4 - MDC INTPSR
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9E3 - LPC HOT DOCKING
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9E1 - SCAN MATRIX
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9G1 - LPC SIDE BAND
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J8F1 - UNIFIED
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J6F1 - LVDS
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2F1 - LAI FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2G1 - GFX VID
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1G6 - AC JACK
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0020, DMI type 9, 13 bytes
System Slot Information
    Designation: J6B2
    Type: x16 PCI Express
    Current Usage: In Use
    Length: Long
    ID: 0
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0021, DMI type 9, 13 bytes
System Slot Information
    Designation: J6B1
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 1
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0022, DMI type 9, 13 bytes
System Slot Information
    Designation: J6D1
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 2
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0023, DMI type 9, 13 bytes
System Slot Information
    Designation: J7B1
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 3
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0024, DMI type 9, 13 bytes
System Slot Information
    Designation: J8B4
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 4
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0025, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Enabled
    Description:    To Be Filled By O.E.M.

Handle 0x0026, DMI type 11, 5 bytes
OEM Strings
    String 1: 0010DC000150AEC0
    String 2: 002185E4A5E5

Handle 0x0027, DMI type 12, 5 bytes
System Configuration Options
    Option 1: To Be Filled By O.E.M.

Handle 0x0028, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

Handle 0x0029, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 2048 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x002A, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0013FFFFFFF
    Range Size: 5 GB
    Physical Array Handle: 0x0029
    Partition Width: 0

Handle 0x002B, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0029
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: A1_DIMM0
    Bank Locator: A1_BANK0
    Type: <OUT OF SPEC>
    Type Detail: Synchronous
    Speed: 333 MHz (3.0 ns)
    Manufacturer: A1_Manufacturer0
    Serial Number: A1_SerNum0
    Asset Tag: A1_AssetTagNum0
    Part Number: A1_PartNum0

Handle 0x002C, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x002B
    Memory Array Mapped Address Handle: 0x002A
    Partition Row Position: 1

Handle 0x002D, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0029
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: A1_DIMM1
    Bank Locator: A1_BANK1
    Type: <OUT OF SPEC>
    Type Detail: Synchronous
    Speed: 333 MHz (3.0 ns)
    Manufacturer: A1_Manufacturer1
    Serial Number: A1_SerNum1
    Asset Tag: A1_AssetTagNum1
    Part Number: A1_PartNum1

Handle 0x002E, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00080000000
    Ending Address: 0x000FFFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x002D
    Memory Array Mapped Address Handle: 0x002A
    Partition Row Position: 1

Handle 0x002F, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0029
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: 64 bits
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: A1_DIMM2
    Bank Locator: A1_BANK2
    Type: DDR2
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: A1_Manufacturer2
    Serial Number: A1_SerNum2
    Asset Tag: A1_AssetTagNum2
    Part Number: A1_PartNum2

Handle 0x0030, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000000003FF
    Range Size: 1 kB
    Physical Device Handle: 0x002F
    Memory Array Mapped Address Handle: 0x002A
    Partition Row Position: 1

Handle 0x0031, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0029
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: 64 bits
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: A1_DIMM3
    Bank Locator: A1_BANK3
    Type: DDR2
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: A1_Manufacturer3
    Serial Number: A1_SerNum3
    Asset Tag: A1_AssetTagNum3
    Part Number: A1_PartNum3

Handle 0x0032, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000000003FF
    Range Size: 1 kB
    Physical Device Handle: 0x0031
    Memory Array Mapped Address Handle: 0x002A
    Partition Row Position: 1

Handle 0x0033, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x0034, DMI type 127, 4 bytes
End Of Table
```

> Also, try to disable the closed drivers for your graphics card, 
(*system - **administration - hardware&drivers*)
if they have enabled, and tried to see if anything changed.
This did not make any change.



By the way, thank you for all the patience

---

### Post by vagrale13 on 2010-08-18
Try this
Press **Ctrl+Alt+F2** to get out of graphic,
login with user&pass  - and the type the commands
```
sudo /etc/init.d/gdm stop
sudo shutdown -P now
```and see if normaly shutdown!

---

### Post by L2U2K2E on 2010-08-19
> **vagrale13 said:**
> Try this
Press **Ctrl+Alt+F2** to get out of graphic,
login with user&pass  - and the type the commands
```
sudo /etc/init.d/gdm stop
sudo shutdown -P now
```and see if normaly shutdown!
I tried this, and It did not seem to work. the first command came back with an error. something about the command not existing.

Also, not sure if it is related, but before I could enter that in at all I kept receiving this line of code.
```

[###.######] ata5.00: exception Emask 0x0 SErr 0x0 action 0x6 frozen
[###.######] ata5.00: irq_stat 0x40000001
[###.######] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag0
[###.######]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[###.######] ata5.00: status {DRDY ERR}

```

This popped up multiple times, filling the entire screen, and the #'s would change each time... not sure if that is relevant or not.

---

### Post by vagrale13 on 2010-08-19
These messages are from the bios most likely problem,
where you have the problem you got!
Look here [URL="http://forums.opensuse.org/english/get-help-here/64-bit/422641-what-problem-ata1-00-status-drdy.html"]http://forums.opensuse.org/english/get-help-here/64-bit/422641-what-problem-ata1-00-status-drdy.html
[/URL] 
I think the best is to return to the previous version of bios, where you had no problem
and try to fix the problem with sensors with other way! :KS


If you want also you can try and a later kernel, e.g. *2.6.34*
look here [URL="http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/"]http://kernel.ubuntu.com/~kernel-ppa/mainline/
[/URL] and here [http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/](http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/) 
where perhaps there has corrected the problem!
But if you are not quite sure what you doing, don' t continue, because you may have a biggest problem after that.

Also, you can wait someone else give you some other solution!

---

