---
title: "HDA Sound card not recognized. Help!!"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by SebSmith on 2011-02-27
level of exp: newbie

i have a beats envy 14, and the sound card is not being recognized by ubuntu, it works fine in windows but when i look at audio output on ubuntu it says dummy output.

it worked at one point, but i have no idea what happened. ive run alsa scripts, tried downloading every alsa package i can find, even upgraded from 10.04 lts to 10.10. nothing is working. please help

lspci : Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)

ive looked at every forum thread for my problem.

thanks in advance

---

### Post by SebSmith on 2011-02-27
bumpity

---

### Post by SebSmith on 2011-02-27
is nobody able to help? ive been going crazy compiling drivers and everything. what do i do??

---

### Post by robert shearer on 2011-02-27
well, first, bumping **once** in 24 hrs is considered polite.
Anything more often is likely to get you ignored by many who could otherwise help. Just something to remember.

secondly, try putting this in your favourite search engine...

> site:ubuntuforums.org beats envy 14

and you will find about 1410 instances all from Ubuntu forums posts.
One of those might just be what you are looking for.


> it worked at one point, but i have no idea what happened. ive run alsa scripts, tried downloading every alsa package i can find, even upgraded from 10.04 lts to 10.10. nothing is working. please help

did you open sound preferences and select it as the default card...??

---

### Post by SebSmith on 2011-02-27
> **robert shearer said:**
> well, first, bumping **once** in 24 hrs is considered polite.
Anything more often is likely to get you ignored by many who could otherwise help. Just something to remember.

secondly, try putting this in your favourite search engine...



and you will find about 1410 instances all from Ubuntu forums posts.
One of those might just be what you are looking for.




did you open sound preferences and select it as the default card...??


no sound card detected, it says dummy stereo

---

### Post by Hedgehog1 on 2011-02-27
That leaves you with the search option:

```
site:ubuntuforums.org beats envy 14
```

When you find the solution, please be sure to post it on your thread for the next person who needs it.

---

### Post by SebSmith on 2011-02-27
> **Hedgehog1 said:**
> That leaves you with the search option:

```
site:ubuntuforums.org beats envy 14
```When you find the solution, please be sure to post it on your thread for the next person who needs it.


i really dont think you guys realize ive been searching for about 3 days now to no avail. ive upgraded to 10.10 from 10.04lts and compiled alsa about a million times, alsamixer doesnt work, card is not detected and eveything thing ive searched for (including my sound card and other hp models' issues and mine is still not going away. is there some information i can provide in order for you guys to better see the issue im dealing with?

---

### Post by robert shearer on 2011-02-27
> **SebSmith said:**
> i really dont think you guys realize ive been searching for about 3 days now to no avail. ive upgraded to 10.10 from 10.04lts and compiled alsa about a million times, alsamixer doesnt work, card is not detected and eveything thing ive searched for (including my sound card and other hp models' issues and mine is still not going away. is there some information i can provide in order for you guys to better see the issue im dealing with?

Well, if the card did work once then you have altered something in a config file and no amount of upgrading or recompiling will alter that.
All you get is an upgraded o/s with the same problem config file....Think about it.

If the card worked ootb initially and you have good backups of all your data then the quickest fix might just be a re-install that will start with all config files as they were(**if** it worked ootb first install)
A hammer to crack a nut but might save a lot of footling.

Otherwise, what is the output from...
```
aplay -l
```

and what happens if you disable the onboard audio in bios leaving only the pci card to be detected...?

and you can always target your research from the output you get from the o/s...
eg..
> site:ubuntuforums.org dummy stereo

note the common pattern..?

---

### Post by SebSmith on 2011-02-27
aplay: device_list:235: no soundcards found...

---

### Post by robert shearer on 2011-02-27
try..
```
sudo dmidecode 
```

to see if the card is recognised in bios.
If not, **and** it has worked previously, then you might want to check the card is seated correctly.

---

### Post by SebSmith on 2011-02-27
well my sound card works fine in windows 7 so bios should naturally think its there. i dont think i see my sound card in this though.. what could this mean?

# dmidecode 2.9
SMBIOS 2.6 present.
30 structures occupying 1425 bytes.
Table at 0x000E9000.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Hewlett-Packard
    Version: F.23
    Release Date: 11/11/2010
    ROM Size: 2048 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
        Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        8042 keyboard services are supported (int 9h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 15.23
    Firmware Revision: 89.35

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Hewlett-Packard
    Product Name: HP ENVY 14 Notebook PC          
    Version: 057D120011243E10001620100
    Serial Number: CNU1062YVJ
    UUID: 2260A85E-25EF-A3B0-20C0-9E6F185B965B
    Wake-up Type: Power Switch
    SKU Number: XQ104AV     
    Family: 103C_5335KV G=N L=CON B=HP S=ENV        

Handle 0x0002, DMI type 2, 16 bytes
Base Board Information
    Manufacturer: Hewlett-Packard
    Product Name: 1437
    Version: 59.23
    Serial Number: PBULT00QE0B01H
    Asset Tag: Base Board Asset Tag
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: Base Board Chassis Location
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0003, DMI type 3, 22 bytes
Chassis Information
    Manufacturer: Hewlett-Packard
    Type: Notebook
    Lock: Not Present
    Version: Chassis Version
    Serial Number: Chassis Serial Number
    Asset Tag: CNU1062YVJ
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x0002013E
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0

Handle 0x0004, DMI type 9, 17 bytes
System Slot Information
    Designation: J5C1
    Type: x16 <OUT OF SPEC>
    Current Usage: Available
    Length: Other
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported

Handle 0x0005, DMI type 9, 17 bytes
System Slot Information
    Designation: J6C1
    Type: x1 <OUT OF SPEC>
    Current Usage: Available
    Length: Other
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported

Handle 0x0006, DMI type 9, 17 bytes
System Slot Information
    Designation: J6C2
    Type: x1 <OUT OF SPEC>
    Current Usage: Available
    Length: Other
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported

Handle 0x0007, DMI type 9, 17 bytes
System Slot Information
    Designation: J6D2
    Type: x1 <OUT OF SPEC>
    Current Usage: Available
    Length: Other
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported

Handle 0x0008, DMI type 9, 17 bytes
System Slot Information
    Designation: J7C1
    Type: x1 <OUT OF SPEC>
    Current Usage: Available
    Length: Other
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported

Handle 0x0009, DMI type 9, 17 bytes
System Slot Information
    Designation: J7D2
    Type: x1 <OUT OF SPEC>
    Current Usage: Available
    Length: Other
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported

Handle 0x000A, DMI type 9, 17 bytes
System Slot Information
    Designation: J8C2
    Type: x16 <OUT OF SPEC>
    Current Usage: Available
    Length: Other
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported

Handle 0x000B, DMI type 9, 17 bytes
System Slot Information
    Designation: J8C1
    Type: x1 <OUT OF SPEC>
    Current Usage: Available
    Length: Other
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported

Handle 0x000C, DMI type 11, 5 bytes
OEM Strings
    String 1: $HP$
    String 2: LOC#ABA
    String 3: ABS 70/71 78 79 7A 7B
    String 4: CNB1 057D120011243E10001620100
    String 5: 120
    String 6: 20110221
    String 7: HP_Mute_LED_1_0

Handle 0x000D, DMI type 22, 26 bytes
Portable Battery
    Location: Primary
    Manufacturer: Dynapack
    Name: LU06062
    Design Capacity: 59200 mWh
    Design Voltage: 14800 mV
    SBDS Version: Not Specified
    Maximum Error: 1%
    SBDS Serial Number: 00B8
    SBDS Manufacture Date: 2010-12-04
    SBDS Chemistry: LION
    OEM-specific Information: 0x0000FFFF

Handle 0x000E, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x000F, DMI type 41, 11 bytes
Unknown Type
    Header and Data:
        29 0B 0F 00 01 85 01 00 00 00 01
    Strings:
        Hanksville Gbe Lan Connection

Handle 0x0010, DMI type 129, 8 bytes
OEM-specific Type
    Header and Data:
        81 08 10 00 01 01 02 01
    Strings:
        Intel_ASF
        Intel_ASF_001

Handle 0x0011, DMI type 130, 20 bytes
OEM-specific Type
    Header and Data:
        82 14 11 00 24 41 4D 54 01 01 01 01 01 A5 1F 02
        00 00 00 00

Handle 0x0012, DMI type 131, 64 bytes
OEM-specific Type
    Header and Data:
        83 40 12 00 17 00 00 00 00 00 32 D1 06 00 00 00
        F8 00 09 3B 00 00 00 00 01 20 00 00 01 00 06 00
        15 04 01 00 00 00 00 00 C8 00 FF FF 00 00 00 FF
        00 00 00 00 5E 00 00 00 76 50 72 6F 00 00 00 00

Handle 0x0013, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 8 GB
    Error Information Handle: No Error
    Number Of Devices: 2

Handle 0x0014, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0013
    Error Information Handle: Not Provided
    Total Width: 8 bits
    Data Width: 8 bits
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: Bottom - Slot 1 (top)
    Bank Locator: BANK 0
    Type: <OUT OF SPEC>
    Type Detail: Synchronous
    Speed: 1333 MHz (0.8 ns)
    Manufacturer: Not Specified
    Serial Number: 00000000
    Asset Tag: Unknown
    Part Number: Not Specified

Handle 0x0015, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0013
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: SODIMM
    Set: None
    Locator: Bottom - Slot 2 (under)
    Bank Locator: BANK 2
    Type: <OUT OF SPEC>
    Type Detail: Synchronous
    Speed: 1333 MHz (0.8 ns)
    Manufacturer: Samsung
    Serial Number: 875976B1
    Asset Tag: Unknown
    Part Number: M471B5273CH0-CH9  

Handle 0x0016, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000FFFFFFFF
    Range Size: 4 GB
    Physical Device Handle: 0x0015
    Memory Array Mapped Address Handle: 0x0017
    Partition Row Position: 1
    Interleave Position: 2
    Interleaved Data Depth: 1

Handle 0x0017, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000FFFFFFFF
    Range Size: 4 GB
    Physical Array Handle: 0x0013
    Partition Width: 0

Handle 0x0018, DMI type 4, 42 bytes
Processor Information
    Socket Designation: CPU
    Type: Central Processor
    Family: <OUT OF SPEC>
    Manufacturer: Intel(R) Corporation
    ID: E5 06 01 00 FF FB EB BF
    Version: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz
    Voltage: 1.2 V
    External Clock: 1066 MHz
    Max Speed: 1733 MHz
    Current Speed: 1724 MHz
    Status: Populated, Enabled
    Upgrade: ZIF Socket
    L1 Cache Handle: 0x001C
    L2 Cache Handle: 0x001B
    L3 Cache Handle: 0x0019
    Serial Number: Not Specified
    Asset Tag: FFFF
    Part Number: Not Specified
    Core Count: 4
    Core Enabled: 4
    Thread Count: 8
    Characteristics:
        64-bit capable

Handle 0x0019, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L3 Cache
    Configuration: Enabled, Not Socketed, Level 3
    Operational Mode: Write Through
    Location: Internal
    Installed Size: 6144 KB
    Maximum Size: 6144 KB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: Other

Handle 0x001A, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1 Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Through
    Location: Internal
    Installed Size: 32 KB
    Maximum Size: 32 KB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Data
    Associativity: 8-way Set-associative

Handle 0x001B, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2 Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Through
    Location: Internal
    Installed Size: 256 KB
    Maximum Size: 256 KB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x001C, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1 Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Through
    Location: Internal
    Installed Size: 32 KB
    Maximum Size: 32 KB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Instruction
    Associativity: 4-way Set-associative

Handle 0x001D, DMI type 127, 4 bytes
End Of Table

---

### Post by lidex on 2011-03-01
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**
No joy? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by SebSmith on 2011-03-02
> **lidex said:**
> Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```**Logout/in.**
No joy? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.


thank you, but nothing worked. i just reinstalled. but now this time around i didnt make a swap space and now after grub it hangs for a good 6 seconds. im not having very good luck lol

---

### Post by lidex on 2011-03-02
Does it boot to desktop? Do you have audio?

---

### Post by SebSmith on 2011-03-02
> **lidex said:**
> Does it boot to desktop? Do you have audio?


yeah my sound is fine now. i have no idea what happened before. but it boots right, it just hangs at blank screen for like 5-10 seconds.

---

### Post by lidex on 2011-03-02
> **SebSmith said:**
> yeah my sound is fine now. i have no idea what happened before. but it boots right, it just hangs at blank screen for like 5-10 seconds.

Yeah, mine too.

---

### Post by ForrestB on 2011-05-10
Hey Having Similar problem to Sam Smith:    
Here is the link to my ALSA info....
[http://www.alsa-project.org/db/?f=cd98fb4a537bd3d25dcaf1a5bdaf0b7a9936de0b](http://www.alsa-project.org/db/?f=cd98fb4a537bd3d25dcaf1a5bdaf0b7a9936de0b)

any advice would be appreciated

---

### Post by lidex on 2011-05-10
> **ForrestB said:**
> Hey Having Similar problem to Sam Smith:    
Here is the link to my ALSA info....
[http://www.alsa-project.org/db/?f=cd98fb4a537bd3d25dcaf1a5bdaf0b7a9936de0b](http://www.alsa-project.org/db/?f=cd98fb4a537bd3d25dcaf1a5bdaf0b7a9936de0b)

any advice would be appreciated
Try upgrading alsa using the script linked to in my sig.

---

### Post by logichype on 2011-11-30
I have had this problem, and when I do I can just restart the pulseaudio process (I can do that from the System Monitor by killing it and it comes back).   I am not sure but I think perhaps when I run VirtualBoxOSE it messes up the system audio when it installs the virtual alsa devices it needs.

I hope that info helps others.:)

---

