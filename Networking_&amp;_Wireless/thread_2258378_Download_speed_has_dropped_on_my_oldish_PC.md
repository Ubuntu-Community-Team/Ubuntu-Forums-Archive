---
title: "Download speed has dropped on my oldish PC"
date: 2014-12-27
forum: Networking &amp; Wireless
---

### Post by shantiq on 2014-12-27
....    seems to be capped at 1.1MB/s these days on my ubuntu setup on a PC and also "paralizes" use of browsers if at that speed

now with a macbook using the mac partition i have no such cap   it goes up to 3.84MB/s **with same internet connection** and i can still surf the net while doing this

I am pretty certain this was the case with ubuntu too going back a couple of years

Was something changed?

Is there a way to override those changes and get it all back to what that Mac can do?

---

### Post by sudodus on 2014-12-27
I use Transmission in Ubuntu 12.04.5 LTS, and if I do not limit the download speed, it can be very high, 7-9 MB/s using up to 60 connected peers.

At Transmission Preferences -- Speed, I do not tick the speed limit for Download -- If you want to decrease the footprint, you can set a suitable limit.

But maybe you have some other problem.

---

### Post by Bucky Ball on 2014-12-27
Yes, cut down the number of connections/peers/leechers and limit the upload speed to leechers.

PS: As far as I know, Linux isn't Latin for anything. Linux = [Linus Torvalds]("https://en.wikipedia.org/wiki/Linus_Torvalds") (the father of Linux) + [Unix]("https://en.wikipedia.org/wiki/Unix"). It's made up by Linus himself. I'm ready to be enlightened, though, as I don't speak Latin (why learn a dead language when I have enough problems with a living one!). ;)

---

### Post by shantiq on 2014-12-27
thanx guys will look deeper into it 
I too use Transmission with no check on download just upload this cap might be from elsewhere as you mention Sudodus
Ps    Bucky my Latin quote is facetious humour it is a joke not serious i know where Linux comes from / and babies   ...      love and worship Linus like we all do :)



**EDIT:** ok tested transmission on the 14.04 Ubuntu   boot part of Macbook and got speed of 3.60MB    so the issue is **not** with Ubuntu but with
the pc I mentioned is now 9 years old     could it be old age ?   i am positive i remember 2 years ago it went to 4MB speed so    what could be amiss?    anyone any thoughts? any settings could have shifted **as i very much doubt it is a hardware issue **must be some system-wide setting one of you learned chaps might know about ?

---

### Post by flaymond on 2014-12-27
I also got the same problem, my Transmission download an ISO file far more longer than usual  downloading without using any client.

---

### Post by sudodus on 2014-12-27
> **shantiq said:**
> ... **EDIT:** ok tested transmission on the 14.04 Ubuntu   boot part of Macbook and got speed of 3.60MB    so the issue is **not** with Ubuntu but with
the pc I mentioned is now 9 years old     could it be old age ?   i am positive i remember 2 years ago it went to 4MB speed so    what could be amiss?    anyone any thoughts? any settings could have shifted **as i very much doubt it is a hardware issue **must be some system-wide setting one of you learned chaps might know about ?

You could test with a live system in that old computer. If still slow, we should be able to rule out software, except maybe the network connection, where there must be a driver for the hardware (wired or wireless network chip).

Maybe some hardware component is slow or not quite reliable, for example that the hard disk drive comes to bad or almost bad sectors and has the re-try. Or that the drive is almost full (which causes fragmentation also with linux file systems).

---

### Post by hojat2 on 2014-12-27
You can use Vuze Program , It Is very Fast Than Other Program !

---

### Post by shantiq on 2014-12-27
> **sudodus said:**
> You could test with a live system in that old computer. If still slow, we should be able to rule out software, except maybe the network connection, where there must be a driver for the hardware (wired or wireless network chip).

Maybe some hardware component is slow or not quite reliable, for example that the hard disk drive comes to bad or almost bad sectors and has the re-try. Or that the drive is almost full (which causes fragmentation also with linux file systems).

well it is a one-week old install of 14.04 Sudodus so we have 450GB of space left at this stage
so a live usb should not show too much here maybe ///   something has shifted somewhere and it "caps" downloads   actually not just torrents but even DD from a potential   3 to 4 MB/s   i have a 30MB connection    to a paltry   1.1MB/s    which is quite a drop  REALLY   i have no idea where to look    how can you check those sectors you mention Sudodus to see if any unhealthy?

---

### Post by sudodus on 2014-12-27
When booted from another drive (for example an Ubuntu install drive), unmount the partition you want to check, and run e2fsck

```
sudo umount /dev/sdxy

sudo e2fsck -cf /dev/sdxy
```

where x is the drive letter and y is the partition number.

If you store the torrented data in an ntfs partition, that might be slow in linux (and if you want to check it, do it from Windows).

---

### Post by Bucky Ball on 2014-12-28
> **shantiq said:**
> 
Ps    Bucky my Latin quote is facetious humour it is a joke not serious i know where Linux comes from / and babies   ...      love and worship Linus like we all do :)


Sometimes I take things too literally. ;)

---

### Post by shantiq on 2014-12-28
> **sudodus said:**
> When booted from another drive (for example an Ubuntu install drive), unmount the partition you want to check, and run e2fsck

```
sudo umount /dev/sdxy

sudo e2fsck -cf /dev/sdxy
```

where x is the drive letter and y is the partition number.

If you store the torrented data in an ntfs partition, that might be slow in linux (and if you want to check it, do it from Windows).



sorry Sudodus.   first thanx for input   but I need more explanations please
booted from another drive     do you mean like a live USB?

I have no knowledge of the whole partition business
do you mean to enter   this   sudo umount /dev/sdxy    in terminal  when on usb Try Ubuntu non-install from live usb?  where will i see x and y?    and what will i look out for in results ?

I need more blow by blow here if you have the time   as no real understanding/experience of this side of things


thanx    shan

---

### Post by sudodus on 2014-12-28
Yes, boot from a live USB or live CD (for example made from an Ubuntu desktop iso file, but most linux live drives would be OK).

If the internal drive is the only drive except the live drive, x is probably a. If only Ubuntu, y is probably 1. If dual boot y can be 5.

so the partition to be checked could be **/dev/sda1** or **/dev/sda5**

Check that you get the partition correctly with

```
sudo parted -l
```

Please post the output of the command, if you want help with it :-)

---

### Post by shantiq on 2014-12-28
ok Sudodus

i ran sudo parted -l

in my current install and found

>  sudo parted -l
[sudo] password for shantiq: 
Model: ATA ST3500630AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  497GB  497GB   primary   ext4            boot
 2      497GB   500GB  2681MB  extended
 5      497GB   500GB  2681MB  logical   linux-swap(v1)




now systems monitor shows this   /dev/sda1  ext4  total 489.5GB  available 444GB  used 20GB   as the only partition


so i am going to load live usb

go to terminal and enter

```
sudo umount   /dev/sda1

```and 

```
sudo e2fsck -cf /dev/sda1
```


and will post findings

---

### Post by sudodus on 2014-12-28
```
sudo e2fsck -cf [COLOR=#ff0000]/dev/[/COLOR]sda1
```

---

### Post by shantiq on 2014-12-28
obtained under live usb  on the terminal

> ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST3500630AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  497GB  497GB   primary   ext4            boot
 2      497GB   500GB  2681MB  extended
 5      497GB   500GB  2681MB  logical   linux-swap(v1)


Model:  USB Flash Memory (scsi)
Disk /dev/sdb: 8022MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  8022MB  8022MB  primary  fat32        boot, lba


ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo e2fsck -cf /dev/sda1
e2fsck 1.42.9 (4-Feb-2014)
Checking for bad blocks (read-only test): done                                                 
/dev/sda1: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 283423/30367744 files (0.2% non-contiguous), 6956056/121441280 blocks
ubuntu@ubuntu:~$ 




is   (0.2% non-contiguous)   the kink here?

---

### Post by sudodus on 2014-12-28
No [kink], I think it is OK now. Did you notice if some bad blocks were found?

Does it work better? If not, the problem is somewhere else. Could there be a problem between the driver and the network chip/card?

Are you using wired network (ethernet) or wireless network? Or maybe home-plug (via the power grid)?

---

### Post by shantiq on 2014-12-28
ethernet is my current weapon Sudodus
     0   errors were found i think   when it was scanning

PS and still "caps"

5.6% of 588.87MiB at  **1.12MiB/s** ETA 08:17

---

### Post by sudodus on 2014-12-28
Can you test your internet connection? Try some website near you - maybe you can try [http://www.broadbandspeedchecker.co.uk](http://www.broadbandspeedchecker.co.uk)

[COLOR=#696969](I'm in Sweden, so I get the best performance at a Swedish site.)[/COLOR]

---

### Post by shantiq on 2014-12-29
ok you may have found the problem here sudodus
on my PC which has the problem the reading is this


[ATTACH=CONFIG]258850[/ATTACH]


if i run it on the Macbook 2 minutes later it shows

[ATTACH=CONFIG]258849[/ATTACH]


so the PC  ** is not allowing the full flow  **&#8203;as mentioned it is now 9 years old  you mentioned a chip before   somethng might be faulty at this point
you offered    > [COLOR=#000000] Could there be a problem between the driver and the network chip/card?[/COLOR]

is there a way to test that that you know of?


some info here

```
sudo lspci -v[sudo] password for shantiq: 
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS480/RS482/RS485 Host Bridge (rev 10)
    Subsystem: Packard Bell B.V. Device d008
    Flags: bus master, 66MHz, medium devsel, latency 0


00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS4xx PCI Express Port [ext gfx] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: fc600000-fe7fffff
    Prefetchable memory behind bridge: 00000000bbf00000-00000000dfefffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device 5950
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Kernel driver in use: pcieport


00:11.0 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB400 Serial ATA Controller (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Packard Bell B.V. Device d008
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 23
    I/O ports at bc00 [size=8]
    I/O ports at b800 [size=4]
    I/O ports at b400 [size=8]
    I/O ports at b000 [size=4]
    I/O ports at ac00 [size=16]
    Memory at febffc00 (32-bit, non-prefetchable) [size=512]
    Expansion ROM at feb00000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 2
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: sata_sil


00:12.0 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 Serial ATA Controller (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Packard Bell B.V. Device d008
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at a800 [size=8]
    I/O ports at a400 [size=4]
    I/O ports at a000 [size=8]
    I/O ports at 9c00 [size=4]
    I/O ports at 9800 [size=16]
    Memory at febff800 (32-bit, non-prefetchable) [size=512]
    Expansion ROM at fea80000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 2
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: sata_sil


00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (prog-if 10 [OHCI])
    Subsystem: Packard Bell B.V. Device d008
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: ohci-pci


00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (prog-if 10 [OHCI])
    Subsystem: Packard Bell B.V. Device d008
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at febfd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: ohci-pci


00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller (prog-if 20 [EHCI])
    Subsystem: Packard Bell B.V. Device d008
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at febfc000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [dc] Power Management version 2
    Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: ehci-pci


00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller (rev 10)
    Subsystem: Packard Bell B.V. Device d008
    Flags: 66MHz, medium devsel
    I/O ports at 0b00 [size=16]
    Memory at a0000000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
    Kernel driver in use: piix4_smbus


00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: Packard Bell B.V. Device d008
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4
    I/O ports at 0170 [size=8]
    I/O ports at 0374
    I/O ports at ff00 [size=16]
    Capabilities: [70] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: pata_atiixp


00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0


00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
    I/O behind bridge: 00008000-00008fff
    Memory behind bridge: fe800000-fe8fffff


00:14.5 Multimedia audio controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB400 AC'97 Audio Controller (rev 01)
    Subsystem: Packard Bell B.V. Device d008
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at febff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [40] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: snd_atiixp


00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface


00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel


00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel
    Kernel driver in use: amd64_edac


00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Kernel driver in use: k8temp


01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 8400 GS Rev. 3] (rev a2) (prog-if 00 [VGA controller])
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at dc000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 7c00 [size=128]
    [virtual] Expansion ROM at fe780000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia


01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fe77c000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel


02:00.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04) (prog-if 00 [Generic])
    Subsystem: Aztech System Ltd Device 3052
    Flags: bus master, stepping, medium devsel, latency 64, IRQ 20
    Memory at fe8ff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 8800 [size=256]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: serial


02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
    Subsystem: Packard Bell B.V. Device d008
    Flags: bus master, medium devsel, latency 64, IRQ 20
    I/O ports at 8400 [size=256]
    Memory at fe8fec00 (32-bit, non-prefetchable) [size=256]
    Expansion ROM at fe8e0000 [disabled] [size=64K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: 8139too


02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80) (prog-if 10 [OHCI])
    Subsystem: Packard Bell B.V. Device d008
    Flags: bus master, medium devsel, latency 64, IRQ 9
    Memory at fe8fe000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at 8c00 [size=128]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: firewire_ohci



```


[COLOR=#808080]Ps ha sweden. youngest daughter currently studies at uppsala uni  nice :][/COLOR]

---

### Post by sudodus on 2014-12-29
[COLOR=#696969][/COLOR]I don't know that much about network chips, network drivers and settings. [COLOR=#ff0000]Let us hope someone else will chip in and help you :-)[/COLOR]
[COLOR=#696969]

ps/ Uppsala is a nice town :-)/ ds[/COLOR]

---

### Post by sudodus on 2014-12-29
By the way, this thread is in the multimedia forum, but we think now, that the problem is not connected to multimedia or the torrent software, but rather connected to networking. ***Do you want me to move the thread to the networking forum***, where it may be found by people who know more about what we think is the problem?

---

### Post by shantiq on 2014-12-29
Yes please sudodus   it is about networking now  no longer a torrent question and thanx for isolating the real problem here...   many thanx    shan PS  hope they chip in :)

---

### Post by sudodus on 2014-12-29
Moved to the [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") forum. Let us hope someone can help you here :-)

---

### Post by shantiq on 2014-12-30
hi there     **so possible chip issue about download speed having dropped** on a 9 year old machine   ,,,    any of you know anything about this type of problem please

thanx   shan

---

### Post by shantiq on 2014-12-31
my Ethernet internet connection 30MB used to give me 3.8MB/s download rate on my PC and still does on my laptop
but in recent times [say a year] it has dropped to 1.1MB/s on PC as if "capped"    i know of no reason for this   so what could be the problem here?

Speedtest shows 33MB on the laptop and only 10MB on the PC     puzzling!

PS   i am on a clean install from 10 days ago/ situation was the same on previous 14.04 install

here is dmesg if it helps see possible kink

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-43-generic (buildd@tipua) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 (Ubuntu 3.13.0-43.72-generic 3.13.11.11)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-43-generic root=UUID=739e22d6-04f7-42f0-89e9-7e99603d63b3 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000009ffcffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009ffd0000-0x000000009ffddfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000009ffde000-0x000000009fffffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ff780000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.3 present.
[    0.000000] DMI: Packard Bell NEC 00000000000000000000000/MS-7168, BIOS 080012  09/06/2005
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x9ffd0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFE0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x9fc00000-0x9fdfffff]
[    0.000000]  [mem 0x9fc00000-0x9fdfffff] page 2M
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x9c000000-0x9fbfffff]
[    0.000000]  [mem 0x9c000000-0x9fbfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x80000000-0x9bffffff]
[    0.000000]  [mem 0x80000000-0x9bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x7fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x7fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x9fe00000-0x9ffcffff]
[    0.000000]  [mem 0x9fe00000-0x9ffcffff] page 4k
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35b4a000-0x36d9cfff]
[    0.000000] ACPI: RSDP 00000000000f9210 000014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 000000009ffd0000 000038 (v01 A M I  OEMRSDT  09000506 MSFT 00000097)
[    0.000000] ACPI: FACP 000000009ffd0200 000084 (v02 A M I  OEMFACP  09000506 MSFT 00000097)
[    0.000000] ACPI: DSDT 000000009ffd0430 00397A (v01  0AAAA 0AAAA000 00000000 INTL 02002026)
[    0.000000] ACPI: FACS 000000009ffde000 000040
[    0.000000] ACPI: APIC 000000009ffd0390 00005C (v01 A M I  OEMAPIC  09000506 MSFT 00000097)
[    0.000000] ACPI: MCFG 000000009ffd03f0 00003C (v01 A M I  OEMMCFG  09000506 MSFT 00000097)
[    0.000000] ACPI: SSDT 000000009ffd3db0 000D6E (v01    ATI ATIPATCH 00000001 INTL 02002026)
[    0.000000] ACPI: OEMB 000000009ffde040 000056 (v01 A M I  AMI_OEM  09000506 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000009ffcffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x9ffcffff]
[    0.000000]   NODE_DATA [mem 0x9ffcb000-0x9ffcffff]
[    0.000000]  [ffffea0000000000-ffffea00027fffff] PMD -> [ffff88009cc00000-ffff88009f3fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x9ffcffff]
[    0.000000] On node 0 totalpages: 655214
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10176 pages used for memmap
[    0.000000]   DMA32 zone: 651216 pages, LIFO batch:31
[    0.000000] SB4X0 revision 0x10
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] smpboot: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e4000-0x000fffff]
[    0.000000] e820: [mem 0xa0000000-0xff77ffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88009fa00000 s82304 r8192 d24192 u1048576
[    0.000000] pcpu-alloc: s82304 r8192 d24192 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 644953
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-43-generic root=UUID=739e22d6-04f7-42f0-89e9-7e99603d63b3 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 76fe000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Memory: 2544272K/2620856K available (7383K kernel code, 1144K rwdata, 3408K rodata, 1336K init, 1444K bss, 76584K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-1.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 10485760 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2188.779 MHz processor
[    0.000000] tsc: Marking TSC unstable due to TSCs unsynchronized
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 4377.55 BogoMIPS (lpj=8755116)
[    0.004013] pid_max: default: 32768 minimum: 301
[    0.004076] Security Framework initialized
[    0.004121] AppArmor: AppArmor initialized
[    0.004122] Yama: becoming mindful.
[    0.004686] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.013320] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.016044] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.016060] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.016659] Initializing cgroup subsys memory
[    0.016679] Initializing cgroup subsys devices
[    0.016682] Initializing cgroup subsys freezer
[    0.016686] Initializing cgroup subsys blkio
[    0.016689] Initializing cgroup subsys perf_event
[    0.016692] Initializing cgroup subsys hugetlb
[    0.016725] tseg: 0000000000
[    0.016738] mce: CPU supports 5 MCE banks
[    0.016752] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.016752] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.016752] tlb_flushall_shift: 4
[    0.025894] ACPI: Core revision 20131115
[    0.028150] ACPI: All ACPI Tables successfully acquired
[    0.028473] ftrace: allocating 28552 entries in 112 pages
[    0.040664] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.081438] smpboot: CPU0: AMD Athlon(tm) 64 Processor 3400+ (fam: 0f, model: 2f, stepping: 02)
[    0.084000] Performance Events: AMD PMU driver.
[    0.084000] ... version:                0
[    0.084000] ... bit width:              48
[    0.084000] ... generic registers:      4
[    0.084000] ... value mask:             0000ffffffffffff
[    0.084000] ... max period:             00007fffffffffff
[    0.084000] ... fixed-purpose events:   0
[    0.084000] ... event mask:             000000000000000f
[    0.084000] x86: Booted up 1 node, 1 CPUs
[    0.084000] smpboot: Total of 1 processors activated (4377.55 BogoMIPS)
[    0.084000] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.084000] devtmpfs: initialized
[    0.087623] EVM: security.selinux
[    0.087625] EVM: security.SMACK64
[    0.087626] EVM: security.ima
[    0.087627] EVM: security.capability
[    0.087715] PM: Registering ACPI NVS region [mem 0x9ffde000-0x9fffffff] (139264 bytes)
[    0.089246] pinctrl core: initialized pinctrl subsystem
[    0.089366] regulator-dummy: no parameters
[    0.089408] RTC time:  7:48:55, date: 12/31/14
[    0.089472] NET: Registered protocol family 16
[    0.089674] cpuidle: using governor ladder
[    0.089676] cpuidle: using governor menu
[    0.089684] node 0 link 0: io port [1000, ffffff]
[    0.089688] TOM: 00000000a0000000 aka 2560M
[    0.089691] node 0 link 0: mmio [e0000000, efffffff]
[    0.089694] node 0 link 0: mmio [a0000000, dfffffff]
[    0.089696] node 0 link 0: mmio [a0000, bffff]
[    0.089698] node 0 link 0: mmio [f0000000, ffffffff]
[    0.089702] bus: [bus 00-ff] on node 0 link 0
[    0.089704] bus: 00 [io  0x0000-0xffff]
[    0.089706] bus: 00 [mem 0xa0000000-0xfcffffffff]
[    0.089707] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.089757] ACPI: bus type PCI registered
[    0.089760] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.089848] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.089851] PCI: not using MMCONFIG
[    0.089853] PCI: Using configuration type 1 for base access
[    0.091054] bio: create slab <bio-0> at 0
[    0.091270] ACPI: Added _OSI(Module Device)
[    0.091272] ACPI: Added _OSI(Processor Device)
[    0.091274] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.091275] ACPI: Added _OSI(Processor Aggregator Device)
[    0.092761] ACPI: Executed 3 blocks of module-level executable AML code
[    0.094365] ACPI: Interpreter enabled
[    0.094374] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.094379] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.094394] ACPI: (supports S0 S3 S4 S5)
[    0.094396] ACPI: Using IOAPIC for interrupt routing
[    0.094478] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.095501] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.105112] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.105252] ACPI: No dock devices found.
[    0.110881] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.110891] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.110898] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.111007] acpi PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.111009] acpi PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.111012] acpi PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.111014] acpi PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.111017] acpi PNP0A03:00: host bridge window [mem 0xa0000000-0xffffffff] (ignored)
[    0.111020] PCI: root bus 00: hardware-probed resources
[    0.111210] PCI host bridge to bus 0000:00
[    0.111213] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.111216] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.111218] pci_bus 0000:00: root bus resource [mem 0xa0000000-0xfcffffffff]
[    0.111221] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.111230] pci 0000:00:00.0: [1002:5950] type 00 class 0x060000
[    0.111329] pci 0000:00:02.0: [1002:5a34] type 01 class 0x060400
[    0.111366] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.111410] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.111483] pci 0000:00:11.0: [1002:437a] type 00 class 0x01018f
[    0.111510] pci 0000:00:11.0: reg 0x10: [io  0xbc00-0xbc07]
[    0.111523] pci 0000:00:11.0: reg 0x14: [io  0xb800-0xb803]
[    0.111536] pci 0000:00:11.0: reg 0x18: [io  0xb400-0xb407]
[    0.111549] pci 0000:00:11.0: reg 0x1c: [io  0xb000-0xb003]
[    0.111562] pci 0000:00:11.0: reg 0x20: [io  0xac00-0xac0f]
[    0.111575] pci 0000:00:11.0: reg 0x24: [mem 0xfebffc00-0xfebffdff]
[    0.111589] pci 0000:00:11.0: reg 0x30: [mem 0xfeb00000-0xfeb7ffff pref]
[    0.111642] pci 0000:00:11.0: supports D1 D2
[    0.111727] pci 0000:00:12.0: [1002:4379] type 00 class 0x01018f
[    0.111753] pci 0000:00:12.0: reg 0x10: [io  0xa800-0xa807]
[    0.111766] pci 0000:00:12.0: reg 0x14: [io  0xa400-0xa403]
[    0.111779] pci 0000:00:12.0: reg 0x18: [io  0xa000-0xa007]
[    0.111792] pci 0000:00:12.0: reg 0x1c: [io  0x9c00-0x9c03]
[    0.111805] pci 0000:00:12.0: reg 0x20: [io  0x9800-0x980f]
[    0.111818] pci 0000:00:12.0: reg 0x24: [mem 0xfebff800-0xfebff9ff]
[    0.111831] pci 0000:00:12.0: reg 0x30: [mem 0xfea80000-0xfeafffff pref]
[    0.111884] pci 0000:00:12.0: supports D1 D2
[    0.111966] pci 0000:00:13.0: [1002:4374] type 00 class 0x0c0310
[    0.111990] pci 0000:00:13.0: reg 0x10: [mem 0xfebfe000-0xfebfefff]
[    0.112149] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.112197] pci 0000:00:13.1: [1002:4375] type 00 class 0x0c0310
[    0.112220] pci 0000:00:13.1: reg 0x10: [mem 0xfebfd000-0xfebfdfff]
[    0.112363] pci 0000:00:13.1: System wakeup disabled by ACPI
[    0.112416] pci 0000:00:13.2: [1002:4373] type 00 class 0x0c0320
[    0.112442] pci 0000:00:13.2: reg 0x10: [mem 0xfebfc000-0xfebfcfff]
[    0.112559] pci 0000:00:13.2: supports D1 D2
[    0.112561] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.112608] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.112662] pci 0000:00:14.0: [1002:4372] type 00 class 0x0c0500
[    0.112683] pci 0000:00:14.0: reg 0x10: [io  0x0b00-0x0b0f]
[    0.112696] pci 0000:00:14.0: reg 0x14: [mem 0x00000000-0x000003ff]
[    0.112754] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.112866] pci 0000:00:14.1: [1002:4376] type 00 class 0x01018a
[    0.112889] pci 0000:00:14.1: reg 0x10: [io  0x01f0-0x01f7]
[    0.112903] pci 0000:00:14.1: reg 0x14: [io  0x03f4-0x03f7]
[    0.112915] pci 0000:00:14.1: reg 0x18: [io  0x0170-0x0177]
[    0.112928] pci 0000:00:14.1: reg 0x1c: [io  0x0374-0x0377]
[    0.112941] pci 0000:00:14.1: reg 0x20: [io  0xff00-0xff0f]
[    0.113079] pci 0000:00:14.3: [1002:4377] type 00 class 0x060100
[    0.113239] pci 0000:00:14.4: [1002:4371] type 01 class 0x060401
[    0.113331] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.113384] pci 0000:00:14.5: [1002:4370] type 00 class 0x040100
[    0.113407] pci 0000:00:14.5: reg 0x10: [mem 0xfebff400-0xfebff4ff]
[    0.113548] pci 0000:00:14.5: System wakeup disabled by ACPI
[    0.113594] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
[    0.113669] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
[    0.113743] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
[    0.113815] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
[    0.113956] pci 0000:01:00.0: [10de:10c3] type 00 class 0x030000
[    0.113968] pci 0000:01:00.0: reg 0x10: [mem 0xfd000000-0xfdffffff]
[    0.113979] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.113990] pci 0000:01:00.0: reg 0x1c: [mem 0xdc000000-0xddffffff 64bit pref]
[    0.113998] pci 0000:01:00.0: reg 0x24: [io  0x7c00-0x7c7f]
[    0.114006] pci 0000:01:00.0: reg 0x30: [mem 0xfe780000-0xfe7fffff pref]
[    0.114091] pci 0000:01:00.1: [10de:0be3] type 00 class 0x040300
[    0.114102] pci 0000:01:00.1: reg 0x10: [mem 0xfe77c000-0xfe77ffff]
[    0.120024] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.120029] pci 0000:00:02.0:   bridge window [io  0x7000-0x7fff]
[    0.120032] pci 0000:00:02.0:   bridge window [mem 0xfc600000-0xfe7fffff]
[    0.120036] pci 0000:00:02.0:   bridge window [mem 0xbbf00000-0xdfefffff 64bit pref]
[    0.120082] pci 0000:02:00.0: [163c:3052] type 00 class 0x070300
[    0.120111] pci 0000:02:00.0: reg 0x10: [mem 0xfe8ff000-0xfe8fffff]
[    0.120127] pci 0000:02:00.0: reg 0x14: [io  0x8800-0x88ff]
[    0.120245] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.120315] pci 0000:02:03.0: [10ec:8139] type 00 class 0x020000
[    0.120344] pci 0000:02:03.0: reg 0x10: [io  0x8400-0x84ff]
[    0.120359] pci 0000:02:03.0: reg 0x14: [mem 0xfe8fec00-0xfe8fecff]
[    0.120428] pci 0000:02:03.0: reg 0x30: [mem 0xfe8e0000-0xfe8effff pref]
[    0.120476] pci 0000:02:03.0: supports D1 D2
[    0.120478] pci 0000:02:03.0: PME# supported from D1 D2 D3hot D3cold
[    0.120540] pci 0000:02:04.0: [1106:3044] type 00 class 0x0c0010
[    0.120570] pci 0000:02:04.0: reg 0x10: [mem 0xfe8fe000-0xfe8fe7ff]
[    0.120586] pci 0000:02:04.0: reg 0x14: [io  0x8c00-0x8c7f]
[    0.120704] pci 0000:02:04.0: supports D2
[    0.120706] pci 0000:02:04.0: PME# supported from D2 D3hot D3cold
[    0.120806] pci 0000:00:14.4: PCI bridge to [bus 02] (subtractive decode)
[    0.120815] pci 0000:00:14.4:   bridge window [io  0x8000-0x8fff]
[    0.120821] pci 0000:00:14.4:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.120826] pci 0000:00:14.4:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.120829] pci 0000:00:14.4:   bridge window [mem 0xa0000000-0xfcffffffff] (subtractive decode)
[    0.120831] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.121425] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.121481] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.121534] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.121586] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.121638] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.121690] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[    0.121741] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.121793] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.121888] ACPI: \_SB_.PCI0: notify handler is installed
[    0.121918] Found 1 acpi root devices
[    0.122112] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.122115] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.122117] vgaarb: loaded
[    0.122119] vgaarb: bridge control possible 0000:01:00.0
[    0.122386] SCSI subsystem initialized
[    0.122486] libata version 3.00 loaded.
[    0.122509] ACPI: bus type USB registered
[    0.122540] usbcore: registered new interface driver usbfs
[    0.122550] usbcore: registered new interface driver hub
[    0.122581] usbcore: registered new device driver usb
[    0.122715] PCI: Using ACPI for IRQ routing
[    0.134615] PCI: pci_cache_line_size set to 64 bytes
[    0.134695] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.134698] e820: reserve RAM buffer [mem 0x9ffd0000-0x9fffffff]
[    0.134837] NetLabel: Initializing
[    0.134839] NetLabel:  domain hash size = 128
[    0.134840] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.134860] NetLabel:  unlabeled traffic allowed by default
[    0.135000] Switched to clocksource refined-jiffies
[    0.145228] AppArmor: AppArmor Filesystem Enabled
[    0.145317] pnp: PnP ACPI init
[    0.145343] ACPI: bus type PNP registered
[    0.145446] pnp 00:00: [dma 4]
[    0.145482] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.145535] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.145568] pnp 00:02: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.145603] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.145880] pnp 00:04: [dma 0 disabled]
[    0.145944] pnp 00:04: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.146172] pnp 00:05: [dma 0]
[    0.146258] pnp 00:05: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.146515] pnp 00:06: [dma 2]
[    0.146566] pnp 00:06: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.146833] pnp 00:07: [dma 0 disabled]
[    0.146934] pnp 00:07: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.147133] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.147136] system 00:08: [io  0x040b] has been reserved
[    0.147139] system 00:08: [io  0x04d6] has been reserved
[    0.147142] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.147151] system 00:08: [io  0x0c14] has been reserved
[    0.147153] system 00:08: [io  0x0c50-0x0c51] has been reserved
[    0.147156] system 00:08: [io  0x0c52] has been reserved
[    0.147159] system 00:08: [io  0x0c6c] has been reserved
[    0.147161] system 00:08: [io  0x0c6f] has been reserved
[    0.147164] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.147167] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.147169] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.147173] system 00:08: [io  0x0800-0x089f] could not be reserved
[    0.147175] system 00:08: [io  0x0900-0x090f] has been reserved
[    0.147178] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.147182] system 00:08: [mem 0xfff80000-0xffffffff] has been reserved
[    0.147186] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.147307] system 00:09: [io  0x0e00-0x0e7f] has been reserved
[    0.147310] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.147390] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.147393] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.147396] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.147454] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.147457] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.147614] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.147617] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.147620] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.147623] system 00:0c: [mem 0x00100000-0x9fffffff] could not be reserved
[    0.147626] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.147742] pnp: PnP ACPI: found 13 devices
[    0.147744] ACPI: bus type PNP unregistered
[    0.154063] Switched to clocksource acpi_pm
[    0.154118] pci 0000:00:14.0: BAR 1: assigned [mem 0xa0000000-0xa00003ff]
[    0.154129] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.154132] pci 0000:00:02.0:   bridge window [io  0x7000-0x7fff]
[    0.154135] pci 0000:00:02.0:   bridge window [mem 0xfc600000-0xfe7fffff]
[    0.154139] pci 0000:00:02.0:   bridge window [mem 0xbbf00000-0xdfefffff 64bit pref]
[    0.154144] pci 0000:00:14.4: PCI bridge to [bus 02]
[    0.154148] pci 0000:00:14.4:   bridge window [io  0x8000-0x8fff]
[    0.154154] pci 0000:00:14.4:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.154167] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.154169] pci_bus 0000:00: resource 5 [mem 0xa0000000-0xfcffffffff]
[    0.154172] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.154175] pci_bus 0000:01: resource 0 [io  0x7000-0x7fff]
[    0.154177] pci_bus 0000:01: resource 1 [mem 0xfc600000-0xfe7fffff]
[    0.154180] pci_bus 0000:01: resource 2 [mem 0xbbf00000-0xdfefffff 64bit pref]
[    0.154183] pci_bus 0000:02: resource 0 [io  0x8000-0x8fff]
[    0.154185] pci_bus 0000:02: resource 1 [mem 0xfe800000-0xfe8fffff]
[    0.154188] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.154190] pci_bus 0000:02: resource 5 [mem 0xa0000000-0xfcffffffff]
[    0.154193] pci_bus 0000:02: resource 6 [mem 0x000a0000-0x000bffff]
[    0.154266] NET: Registered protocol family 2
[    0.154650] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.155016] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.155593] TCP: Hash tables configured (established 32768 bind 32768)
[    0.155795] TCP: reno registered
[    0.155806] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.155925] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.155925] NET: Registered protocol family 1
[    0.155925] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.316158] pci 0000:01:00.0: Video device with shadowed ROM
[    0.316175] PCI: CLS 64 bytes, default 64
[    0.316292] Trying to unpack rootfs image as initramfs...
[    0.782623] Freeing initrd memory: 18764K (ffff880035b4a000 - ffff880036d9d000)
[    0.783132] microcode: AMD CPU family 0xf not supported
[    0.783135] Scanning for low memory corruption every 60 seconds
[    0.783518] Initialise system trusted keyring
[    0.783589] audit: initializing netlink socket (disabled)
[    0.783612] type=2000 audit(1420012135.779:1): initialized
[    0.815874] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.817678] zbud: loaded
[    0.817861] VFS: Disk quotas dquot_6.5.2
[    0.817930] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.818667] fuse init (API version 7.22)
[    0.818774] msgmni has been set to 5005
[    0.818867] Key type big_key registered
[    0.819273] Key type asymmetric registered
[    0.819275] Asymmetric key parser 'x509' registered
[    0.819329] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.819367] io scheduler noop registered
[    0.819369] io scheduler deadline registered (default)
[    0.819407] io scheduler cfq registered
[    0.819607] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.819627] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.819695] ipmi message handler version 39.2
[    0.819794] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.819802] ACPI: Power Button [PWRB]
[    0.819851] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.819854] ACPI: Power Button [PWRF]
[    0.819894] ACPI: duty_cycle spans bit 4
[    0.819960] GHES: HEST is not enabled!
[    0.820174] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.840843] 00:04: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.861557] 00:05: ttyS1 at I/O 0x2f8 (irq = 3, base_baud = 115200) is a 16550A
[    0.863219] 0000:02:00.0: ttyS5 at I/O 0x8808 (irq = 20, base_baud = 115200) is a 16450
[    0.863335] 0000:02:00.0: ttyS6 at I/O 0x8810 (irq = 20, base_baud = 115200) is a 8250
[    0.863456] 0000:02:00.0: ttyS7 at I/O 0x8818 (irq = 20, base_baud = 115200) is a 16450
[    0.863566] 0000:02:00.0: ttyS8 at I/O 0x8820 (irq = 20, base_baud = 115200) is a 8250
[    0.863677] 0000:02:00.0: ttyS9 at I/O 0x8828 (irq = 20, base_baud = 115200) is a 8250
[    0.865846] Linux agpgart interface v0.103
[    0.867523] brd: module loaded
[    0.868483] loop: module loaded
[    0.869085] libphy: Fixed MDIO Bus: probed
[    0.869209] tun: Universal TUN/TAP device driver, 1.6
[    0.869210] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.869262] PPP generic driver version 2.4.2
[    0.869316] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.869322] ehci-pci: EHCI PCI platform driver
[    0.869476] ehci-pci 0000:00:13.2: EHCI Host Controller
[    0.869485] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.869577] ehci-pci 0000:00:13.2: irq 19, io mem 0xfebfc000
[    0.880021] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.880119] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.880122] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.880124] usb usb1: Product: EHCI Host Controller
[    0.880126] usb usb1: Manufacturer: Linux 3.13.0-43-generic ehci_hcd
[    0.880128] usb usb1: SerialNumber: 0000:00:13.2
[    0.880259] hub 1-0:1.0: USB hub found
[    0.880269] hub 1-0:1.0: 8 ports detected
[    0.880516] ehci-platform: EHCI generic platform driver
[    0.880532] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.880534] ohci-pci: OHCI PCI platform driver
[    0.880615] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    0.880624] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.880645] ohci-pci 0000:00:13.0: irq 19, io mem 0xfebfe000
[    0.940064] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.940066] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.940069] usb usb2: Product: OHCI PCI host controller
[    0.940071] usb usb2: Manufacturer: Linux 3.13.0-43-generic ohci_hcd
[    0.940073] usb usb2: SerialNumber: 0000:00:13.0
[    0.940183] hub 2-0:1.0: USB hub found
[    0.940195] hub 2-0:1.0: 4 ports detected
[    0.940365] ohci-pci 0000:00:13.1: OHCI PCI host controller
[    0.940372] ohci-pci 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.940391] ohci-pci 0000:00:13.1: irq 19, io mem 0xfebfd000
[    1.000062] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.000064] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.000067] usb usb3: Product: OHCI PCI host controller
[    1.000069] usb usb3: Manufacturer: Linux 3.13.0-43-generic ohci_hcd
[    1.000071] usb usb3: SerialNumber: 0000:00:13.1
[    1.000176] hub 3-0:1.0: USB hub found
[    1.000187] hub 3-0:1.0: 4 ports detected
[    1.000311] ohci-platform: OHCI generic platform driver
[    1.000324] uhci_hcd: USB Universal Host Controller Interface driver
[    1.000409] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.003628] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.003634] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.003767] mousedev: PS/2 mouse device common for all mice
[    1.003906] rtc_cmos 00:01: RTC can wake from S4
[    1.004100] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.004132] rtc_cmos 00:01: alarms up to one month, 114 bytes nvram
[    1.004234] device-mapper: uevent: version 1.0.3
[    1.004320] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.004330] ledtrig-cpu: registered to indicate activity on CPUs
[    1.004468] TCP: cubic registered
[    1.004601] NET: Registered protocol family 10
[    1.004871] NET: Registered protocol family 17
[    1.004888] Key type dns_resolver registered
[    1.005134] Loading compiled-in X.509 certificates
[    1.006406] Loaded X.509 cert 'Magrathea: Glacier signing key: 55ab2fe28ed5c60df9587150d1734c920ea7b818'
[    1.006427] registered taskstats version 1
[    1.009824] Key type trusted registered
[    1.012724] Key type encrypted registered
[    1.015617] AppArmor: AppArmor sha1 policy hashing enabled
[    1.015625] IMA: No TPM chip found, activating TPM-bypass!
[    1.015949] regulator-dummy: disabling
[    1.016106]   Magic number: 10:894:825
[    1.016263] rtc_cmos 00:01: setting system clock to 2014-12-31 07:48:56 UTC (1420012136)
[    1.016435] powernow-k8: fid 0xe (2200 MHz), vid 0x6
[    1.016437] powernow-k8: fid 0xc (2000 MHz), vid 0x8
[    1.016438] powernow-k8: fid 0xa (1800 MHz), vid 0xa
[    1.016440] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    1.016478] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3400+ (1 cpu cores) (version 2.20.00)
[    1.016487] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.016489] EDD information not available.
[    1.016527] PM: Hibernation image not present or could not be loaded.
[    1.019441] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    1.019448] Write protecting the kernel read-only data: 12288k
[    1.023274] Freeing unused kernel memory: 796K (ffff880001739000 - ffff880001800000)
[    1.026699] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
[    1.049222] systemd-udevd[92]: starting version 204
[    1.103138] Floppy drive(s): fd0 is 1.44M
[    1.109675] sata_sil 0000:00:11.0: version 2.4
[    1.113218] scsi0 : sata_sil
[    1.116847] scsi1 : sata_sil
[    1.116924] ata1: SATA max UDMA/100 mmio m512@0xfebffc00 tf 0xfebffc80 irq 23
[    1.116929] ata2: SATA max UDMA/100 mmio m512@0xfebffc00 tf 0xfebffcc0 irq 23
[    1.119979] scsi2 : sata_sil
[    1.122633] FDC 0 is a post-1991 82077
[    1.122650] scsi3 : sata_sil
[    1.122717] ata3: SATA max UDMA/100 mmio m512@0xfebff800 tf 0xfebff880 irq 22
[    1.122721] ata4: SATA max UDMA/100 mmio m512@0xfebff800 tf 0xfebff8c0 irq 22
[    1.124202] scsi4 : pata_atiixp
[    1.126264] scsi5 : pata_atiixp
[    1.126333] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.126336] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.134456] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.134493] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.156943] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.158256] 8139too 0000:02:03.0 eth0: RealTek RTL8139 at 0x0000000000018400, 00:13:d3:b6:0d:bb, IRQ 20
[    1.224091] firewire_ohci 0000:02:04.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x11
[    1.300615] ata6.00: ATAPI: _NEC DVD_RW ND-3550A, 1.52, max UDMA/33
[    1.316566] ata6.00: configured for UDMA/33
[    1.436055] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.444043] ata3: SATA link down (SStatus 0 SControl 300)
[    1.452034] usb 1-4: new high-speed USB device number 3 using ehci-pci
[    1.485149] ata1.00: ATA-7: ST3500630AS, 3.AAK, max UDMA/133
[    1.485151] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.551773] ata1.00: configured for UDMA/100
[    1.551925] scsi 0:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
[    1.552245] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.552314] sd 0:0:0:0: [sda] Write Protect is off
[    1.552318] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.552347] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.552686] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.611109]  sda: sda1 sda2 < sda5 >
[    1.611635] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.693601] usb 1-4: New USB device found, idVendor=046d, idProduct=09a4
[    1.693604] usb 1-4: New USB device strings: Mfr=0, Product=0, SerialNumber=2
[    1.693606] usb 1-4: SerialNumber: 85A3B057
[    1.724094] firewire_core 0000:02:04.0: created device fw0: GUID 0010dc0000d1167c, S400
[    1.804029] usb 1-6: new high-speed USB device number 4 using ehci-pci
[    1.872047] ata2: SATA link down (SStatus 0 SControl 300)
[    1.937504] usb 1-6: New USB device found, idVendor=05e3, idProduct=0608
[    1.937507] usb 1-6: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.937509] usb 1-6: Product: USB2.0 Hub
[    1.937919] hub 1-6:1.0: USB hub found
[    1.938255] hub 1-6:1.0: 4 ports detected
[    2.192043] ata4: SATA link down (SStatus 0 SControl 300)
[    2.193418] scsi 5:0:0:0: CD-ROM            _NEC     DVD_RW ND-3550A  1.52 PQ: 0 ANSI: 5
[    2.195442] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    2.195445] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.195582] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    2.195717] sr 5:0:0:0: Attached scsi generic sg1 type 5
[    2.616852] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.616859] EXT4-fs (sda1): write access will be enabled during recovery
[    2.632067] usb 2-2: new full-speed USB device number 2 using ohci-pci
[    2.843095] usb 2-2: config 1 has an invalid interface number: 4 but max is 3
[    2.843103] usb 2-2: config 1 has no interface number 3
[    2.851087] usb 2-2: New USB device found, idVendor=1210, idProduct=000a
[    2.851090] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.851093] usb 2-2: Product: Lexicon Alpha
[    2.851095] usb 2-2: Manufacturer: Lexicon
[    3.168034] usb 2-4: new full-speed USB device number 3 using ohci-pci
[    3.377086] usb 2-4: New USB device found, idVendor=058f, idProduct=9360
[    3.377089] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.377091] usb 2-4: Product: USB Reader
[    3.377094] usb 2-4: Manufacturer:  
[    3.377096] usb 2-4: SerialNumber: 2004888
[    3.383594] usb-storage 2-4:1.0: USB Mass Storage device detected
[    3.383712] scsi6 : usb-storage 2-4:1.0
[    3.384063] usbcore: registered new interface driver usb-storage
[    3.452344] usb 1-6.2: new full-speed USB device number 6 using ehci-pci
[    3.549464] usb 1-6.2: New USB device found, idVendor=04ca, idProduct=0064
[    3.549467] usb 1-6.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.549469] usb 1-6.2: Product: Wireless Device
[    3.549472] usb 1-6.2: Manufacturer: Lite-On Technology Corp.
[    3.557523] hidraw: raw HID events driver (C) Jiri Kosina
[    3.573734] usbcore: registered new interface driver usbhid
[    3.573740] usbhid: USB HID core driver
[    3.580514] input: Lite-On Technology Corp. Wireless Device as /devices/pci0000:00/0000:00:13.2/usb1/1-6/1-6.2/1-6.2:1.0/input/input5
[    3.581108] hid-generic 0003:04CA:0064.0001: input,hidraw0: USB HID v1.11 Keyboard [Lite-On Technology Corp. Wireless Device] on usb-0000:00:13.2-6.2/input0
[    3.585136] input: Lite-On Technology Corp. Wireless Device as /devices/pci0000:00/0000:00:13.2/usb1/1-6/1-6.2/1-6.2:1.1/input/input6
[    3.586134] hid-generic 0003:04CA:0064.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Lite-On Technology Corp. Wireless Device] on usb-0000:00:13.2-6.2/input1
[    3.586998] input: Lite-On Technology Corp. Wireless Device as /devices/pci0000:00/0000:00:13.2/usb1/1-6/1-6.2/1-6.2:1.2/input/input7
[    3.587883] hid-generic 0003:04CA:0064.0003: input,hidraw2: USB HID v1.11 Mouse [Lite-On Technology Corp. Wireless Device] on usb-0000:00:13.2-6.2/input2
[    3.624374] usb 1-6.3: new high-speed USB device number 7 using ehci-pci
[    3.716371] usb 1-6.3: New USB device found, idVendor=058f, idProduct=6254
[    3.716374] usb 1-6.3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.716653] hub 1-6.3:1.0: USB hub found
[    3.716741] hub 1-6.3:1.0: 4 ports detected
[    3.788383] usb 1-6.4: new low-speed USB device number 8 using ehci-pci
[    3.886262] usb 1-6.4: New USB device found, idVendor=09da, idProduct=024f
[    3.886265] usb 1-6.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.886267] usb 1-6.4: Product: RF USB Receiver
[    3.886269] usb 1-6.4: Manufacturer: A4Tech
[    3.889861] input: A4Tech RF USB Receiver as /devices/pci0000:00/0000:00:13.2/usb1/1-6/1-6.4/1-6.4:1.0/input/input8
[    3.889981] hid-generic 0003:09DA:024F.0004: input,hidraw3: USB HID v1.11 Keyboard [A4Tech RF USB Receiver] on usb-0000:00:13.2-6.4/input0
[    3.895989] input: A4Tech RF USB Receiver as /devices/pci0000:00/0000:00:13.2/usb1/1-6/1-6.4/1-6.4:1.1/input/input9
[    3.896148] hid-generic 0003:09DA:024F.0005: input,hidraw4: USB HID v1.11 Mouse [A4Tech RF USB Receiver] on usb-0000:00:13.2-6.4/input1
[    3.998057] EXT4-fs (sda1): orphan cleanup on readonly fs
[    4.004189] usb 1-6.3.4: new low-speed USB device number 9 using ehci-pci
[    4.131674] usb 1-6.3.4: New USB device found, idVendor=04d9, idProduct=1503
[    4.131679] usb 1-6.3.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.131682] usb 1-6.3.4: Product: USB Keyboard
[    4.131684] usb 1-6.3.4: Manufacturer:  
[    4.143050] input:   USB Keyboard as /devices/pci0000:00/0000:00:13.2/usb1/1-6/1-6.3/1-6.3.4/1-6.3.4:1.0/input/input10
[    4.143302] hid-generic 0003:04D9:1503.0006: input,hidraw5: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:13.2-6.3.4/input0
[    4.152080] EXT4-fs (sda1): 12 orphan inodes deleted
[    4.152083] EXT4-fs (sda1): recovery complete
[    4.161654] input:   USB Keyboard as /devices/pci0000:00/0000:00:13.2/usb1/1-6/1-6.3/1-6.3.4/1-6.3.4:1.1/input/input11
[    4.161833] hid-generic 0003:04D9:1503.0007: input,hidraw6: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:13.2-6.3.4/input1
[    4.235577] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.387165] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    4.393116] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    4.399099] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    4.405110] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    4.405435] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    4.405586] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    4.405740] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    4.405886] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    4.495096] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    4.505096] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    4.515096] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[    4.525100] sd 6:0:0:3: [sde] Attached SCSI removable disk
[    5.019040] random: nonblocking pool is initialized
[    7.463492] Adding 2618364k swap on /dev/sda5.  Priority:-1 extents:1 across:2618364k FS
[    8.628353] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.049497] systemd-udevd[274]: starting version 204
[   10.387084] lp: driver loaded but no devices found
[   10.466639] ppdev: user-space parallel port driver
[   10.508162] parport_pc 00:07: reported by Plug and Play ACPI
[   10.508208] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   10.604288] lp0: using parport0 (interrupt-driven).
[   11.286847] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   12.096305] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   12.552024] [drm] Initialized drm 1.1.0 20060810
[   14.191662] hda_intel: Disabling MSI
[   14.191673] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   14.191723] hda-intel 0000:01:00.1: Disabling 64bit DMA
[   14.197443] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[   14.332795] set volume quirk for QuickCam E3500
[   14.348091] 2:1:1: cannot get freq at ep 0x1
[   14.358087] 2:1:2: cannot get freq at ep 0x1
[   14.370083] 2:2:1: cannot get freq at ep 0x82
[   14.379082] 2:2:2: cannot get freq at ep 0x82
[   14.381551] usbcore: registered new interface driver snd-usb-audio
[   14.477956] Linux video capture interface: v2.00
[   14.823375] MCE: In-kernel MCE decoding enabled.
[   14.870883] EDAC MC: Ver: 3.0.0
[   14.935288] AMD64 EDAC driver v3.4.0
[   14.935338] EDAC amd64: DRAM ECC enabled.
[   14.935344] EDAC amd64: K8 revE or earlier detected (node 0).
[   14.935394] EDAC amd64: CS0: Double data rate SDRAM
[   14.935395] EDAC amd64: CS1: Double data rate SDRAM
[   14.935397] EDAC amd64: CS2: Double data rate SDRAM
[   14.935398] EDAC amd64: CS3: Double data rate SDRAM
[   14.935399] EDAC amd64: CS4: Double data rate SDRAM
[   14.935401] EDAC amd64: CS5: Double data rate SDRAM
[   14.935931] EDAC MC0: Giving out device to module amd64_edac controller K8: DEV 0000:00:18.2 (INTERRUPT)
[   14.935990] EDAC PCI0: Giving out device to module amd64_edac controller EDAC PCI controller: DEV 0000:00:18.2 (POLLED)
[   14.970908] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a4)
[   14.999385] input: UVC Camera (046d:09a4) as /devices/pci0000:00/0000:00:13.2/usb1/1-4/1-4:1.0/input/input12
[   14.999542] usbcore: registered new interface driver uvcvideo
[   14.999544] USB Video Class driver (1.1.1)
[   15.076326] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input16
[   15.076489] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input15
[   15.076601] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
[   15.076714] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input13
[   17.135385] type=1400 audit(1420012152.613:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=456 comm="apparmor_parser"
[   17.135398] type=1400 audit(1420012152.613:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=456 comm="apparmor_parser"
[   17.135403] type=1400 audit(1420012152.613:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=456 comm="apparmor_parser"
[   17.136748] type=1400 audit(1420012152.617:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=426 comm="apparmor_parser"
[   17.136759] type=1400 audit(1420012152.617:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=426 comm="apparmor_parser"
[   17.136765] type=1400 audit(1420012152.617:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=426 comm="apparmor_parser"
[   17.137386] type=1400 audit(1420012152.617:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=426 comm="apparmor_parser"
[   17.137391] type=1400 audit(1420012152.617:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=426 comm="apparmor_parser"
[   17.137721] type=1400 audit(1420012152.617:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=426 comm="apparmor_parser"
[   17.138311] type=1400 audit(1420012152.617:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=456 comm="apparmor_parser"
[   17.507778] nvidia: module license 'NVIDIA' taints kernel.
[   17.507786] Disabling lock debugging due to kernel taint
[   17.593116] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   17.637225] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   17.648585] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   17.648604] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  331.113  Mon Dec  1 21:08:13 PST 2014
[   18.502060] init: failsafe main process (539) killed by TERM signal
[   22.055945] init: cups main process (798) killed by HUP signal
[   22.055966] init: cups main process ended, respawning
[   22.458040] Bluetooth: Core ver 2.17
[   22.458117] NET: Registered protocol family 31
[   22.458119] Bluetooth: HCI device and connection manager initialized
[   22.459804] Bluetooth: HCI socket layer initialized
[   22.459813] Bluetooth: L2CAP socket layer initialized
[   22.459830] Bluetooth: SCO socket layer initialized
[   22.556851] Bluetooth: RFCOMM TTY layer initialized
[   22.556874] Bluetooth: RFCOMM socket layer initialized
[   22.556890] Bluetooth: RFCOMM ver 1.11
[   22.877225] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.877233] Bluetooth: BNEP filters: protocol multicast
[   22.877252] Bluetooth: BNEP socket layer initialized
[   23.597462] audit_printk_skb: 42 callbacks suppressed
[   23.597469] type=1400 audit(1420012159.077:26): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=797 comm="apparmor_parser"
[   23.597480] type=1400 audit(1420012159.077:27): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=797 comm="apparmor_parser"
[   23.597486] type=1400 audit(1420012159.077:28): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=797 comm="apparmor_parser"
[   23.597491] type=1400 audit(1420012159.077:29): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=797 comm="apparmor_parser"
[   23.597496] type=1400 audit(1420012159.077:30): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-thumbnailer" pid=797 comm="apparmor_parser"
[   23.597501] type=1400 audit(1420012159.077:31): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=797 comm="apparmor_parser"
[   23.603693] type=1400 audit(1420012159.081:32): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="sanitized_helper" pid=797 comm="apparmor_parser"
[   23.603726] type=1400 audit(1420012159.081:33): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/bin/evince-previewer" pid=797 comm="apparmor_parser"
[   23.604002] type=1400 audit(1420012159.081:34): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="sanitized_helper" pid=797 comm="apparmor_parser"
[   23.604042] type=1400 audit(1420012159.085:35): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/bin/evince-thumbnailer" pid=797 comm="apparmor_parser"
[   30.761076] 8139too 0000:02:03.0 eth0: link up, 10Mbps, full-duplex, lpa 0x4061
[   30.768663] serial8250: too much work for irq20
[   30.784417] serial8250: too much work for irq20
[   30.806664] serial8250: too much work for irq20
[   30.834268] serial8250: too much work for irq20
[   30.869165] serial8250: too much work for irq20
[   30.917118] serial8250: too much work for irq20
[   30.951853] serial8250: too much work for irq20
[   31.074990] serial8250: too much work for irq20
[   31.114902] serial8250: too much work for irq20
[   31.243377] serial8250: too much work for irq20
[   35.830501] serial8250_interrupt: 114 callbacks suppressed
[   35.830501] serial8250: too much work for irq20
[   35.864737] serial8250: too much work for irq20
[   35.883439] serial8250: too much work for irq20
[   35.925757] serial8250: too much work for irq20
[   35.957778] serial8250: too much work for irq20
[   35.974446] serial8250: too much work for irq20
[   36.053705] serial8250: too much work for irq20
[   36.094669] serial8250: too much work for irq20
[   36.113409] serial8250: too much work for irq20
[   36.153774] serial8250: too much work for irq20
[   37.348849] init: samba-ad-dc main process (1014) terminated with status 1
[   37.588137] init: nvidia-persistenced main process (1163) terminated with status 1
[   40.932289] serial8250_interrupt: 109 callbacks suppressed
[   40.932289] serial8250: too much work for irq20
[   40.948169] serial8250: too much work for irq20
[   40.972926] serial8250: too much work for irq20
[   40.992414] serial8250: too much work for irq20
[   41.014459] serial8250: too much work for irq20
[   41.050895] serial8250: too much work for irq20
[   41.077032] serial8250: too much work for irq20
[   41.155417] serial8250: too much work for irq20
[   41.186613] serial8250: too much work for irq20
[   41.234176] serial8250: too much work for irq20
[   46.056019] serial8250_interrupt: 114 callbacks suppressed
[   46.056019] serial8250: too much work for irq20
[   46.076018] serial8250: too much work for irq20
[   46.086850] serial8250: too much work for irq20
[   46.104018] serial8250: too much work for irq20
[   51.304585] NVRM: failed to enable MSI, 
[   51.304585] using PCIe virtual-wire interrupts.
[   52.468884] audit_printk_skb: 96 callbacks suppressed
[   52.468890] type=1400 audit(1420012210.797:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1374 comm="apparmor_parser"
[   52.468901] type=1400 audit(1420012210.797:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1374 comm="apparmor_parser"
[   52.469531] type=1400 audit(1420012210.797:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1374 comm="apparmor_parser"
[   53.310701] init: plymouth-upstart-bridge main process ended, respawning
[   53.328806] init: plymouth-upstart-bridge main process (1380) terminated with status 1
[   53.328829] init: plymouth-upstart-bridge main process ended, respawning
[   64.030097] 2:2:1: cannot get freq at ep 0x82
[   64.034094] 2:2:1: cannot get freq at ep 0x82
[   64.049096] 2:2:1: cannot get freq at ep 0x82
[   64.053098] 2:2:1: cannot get freq at ep 0x82
[   64.061092] 2:1:1: cannot get freq at ep 0x1
[   64.065098] 2:1:1: cannot get freq at ep 0x1
[   64.073091] 2:2:1: cannot get freq at ep 0x82
[   64.077094] 2:2:1: cannot get freq at ep 0x82
[   64.085098] 2:2:1: cannot get freq at ep 0x82
[   64.089096] 2:2:1: cannot get freq at ep 0x82
[   64.108095] 2:1:1: cannot get freq at ep 0x1
[   64.112240] 2:1:1: cannot get freq at ep 0x1
[   64.119091] 2:2:1: cannot get freq at ep 0x82
[   64.123094] 2:2:1: cannot get freq at ep 0x82
[   64.131091] 2:2:1: cannot get freq at ep 0x82
[   64.135093] 2:2:1: cannot get freq at ep 0x82
[   64.147094] 2:1:1: cannot get freq at ep 0x1
[   64.151093] 2:1:1: cannot get freq at ep 0x1
[   64.165093] 2:2:1: cannot get freq at ep 0x82
[   64.169093] 2:2:1: cannot get freq at ep 0x82
[   81.675139] 2:2:1: cannot get freq at ep 0x82
[   81.679113] 2:2:1: cannot get freq at ep 0x82
[   81.695140] 2:2:1: cannot get freq at ep 0x82
[   81.699146] 2:2:1: cannot get freq at ep 0x82
[   81.708132] 2:1:1: cannot get freq at ep 0x1
[   81.712237] 2:1:1: cannot get freq at ep 0x1
[   81.720098] 2:2:1: cannot get freq at ep 0x82
[   81.724279] 2:2:1: cannot get freq at ep 0x82
[   81.732097] 2:2:1: cannot get freq at ep 0x82
[   81.736252] 2:2:1: cannot get freq at ep 0x82
[   81.765100] 2:1:1: cannot get freq at ep 0x1
[   81.769097] 2:1:1: cannot get freq at ep 0x1
[   81.775093] 2:2:1: cannot get freq at ep 0x82
[   81.779101] 2:2:1: cannot get freq at ep 0x82
[   81.792100] 2:2:1: cannot get freq at ep 0x82
[   81.796263] 2:2:1: cannot get freq at ep 0x82
[   81.814098] 2:1:1: cannot get freq at ep 0x1
[   81.818093] 2:1:1: cannot get freq at ep 0x1
[   81.833097] 2:2:1: cannot get freq at ep 0x82
[   81.837099] 2:2:1: cannot get freq at ep 0x82
[  168.067156] 2:1:1: cannot get freq at ep 0x1
[  168.071136] 2:1:1: cannot get freq at ep 0x1



```

---

### Post by TheFu on 2014-12-31
First - don't confuse MB/s and Mb/s. There is an 8x difference and network speeds are always advertised in Mb/s ... 30 Mb/s is .... 30/8 = 3.75MB/s

Download performance is usually limited by the router, not the PC connection, unless you are using wifi. Then all sorts of interference can get in the way. Start by using only wired connections to troubleshoot, not wifi until the router-to-ISP connection has been removed from consideration. Call your ISP to see if they can figure anything out. Be certain the bill is paid. 

There is a network troubleshooting script somewhere in these forums that captures most of the network data about a system. Find that, post the output please.  It will have ifconfig, route, lshw and a few other commands.

---

### Post by shantiq on 2014-12-31
hi Fu thanx for input  [apart from remark on bill ::]]  


```
** ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:13:d3:b6:0d:bb  
          inet addr:82.22.72.183  Bcast:82.22.79.255  Mask:255.255.248.0
          inet6 addr: fe80::213:d3ff:feb6:dbb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:915504 errors:0 dropped:0 overruns:0 frame:0
          TX packets:734480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:855700665 (855.7 MB)  TX bytes:525844318 (525.8 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:14936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1407722 (1.4 MB)  TX bytes:1407722 (1.4 MB)


```


```
**route**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         cpc65345-nrwh11 0.0.0.0         UG    0      0        0 eth0
82.22.72.0      *               255.255.248.0   U     1      0        0 eth0
```






```
**sudo lshw **
[sudo] password for shantiq: 
shantiq-00000000000000000000000
    description: Desktop Computer
    product: 00000000000000000000000 (To Be Filled By O.E.M.)
    vendor: Packard Bell NEC
    version: PB34225301
    serial: 049652320227
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=549D0B9A-BE69-DA11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: MS-7168
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 1.0
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012
          date: 09/06/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 3400+
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1800MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 2560MiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM SDRAM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS480/RS482/RS485 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS4xx PCI Express Port [ext gfx]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:7000(size=4096) memory:fc600000-fe7fffff ioport:bbf00000(size=603979776)
           *-display
                description: VGA compatible controller
                product: GT218 [GeForce 8400 GS Rev. 3]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:7c00(size=128) memory:fe780000-fe7fffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:18 memory:fe77c000-fe77ffff
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:23 ioport:bc00(size=8) ioport:b800(size=4) ioport:b400(size=8) ioport:b000(size=4) ioport:ac00(size=16) memory:febffc00-febffdff memory:feb00000-feb7ffff
        *-ide:1
             description: IDE interface
             product: IXP SB4x0 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:22 ioport:a800(size=8) ioport:a400(size=4) ioport:a000(size=8) ioport:9c00(size=4) ioport:9800(size=16) memory:febff800-febff9ff memory:fea80000-feafffff
        *-usb:0
             description: USB controller
             product: IXP SB4x0 USB Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:febfe000-febfefff
        *-usb:1
             description: USB controller
             product: IXP SB4x0 USB Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:febfd000-febfdfff
        *-usb:2
             description: USB controller
             product: IXP SB4x0 USB2 Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:19 memory:febfc000-febfcfff
        *-serial
             description: SMBus
             product: IXP SB4x0 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:b00(size=16) memory:a0000000-a00003ff
        *-ide:2
             description: IDE interface
             product: IXP SB4x0 IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-isa
             description: ISA bridge
             product: IXP SB4x0 PCI-ISA Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB4x0 PCI-PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:8000(size=4096) memory:fe800000-fe8fffff
           *-communication
                description: Modem
                product: SmartLink SmartPCI562 56K Modem
                vendor: Smart Link Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm generic bus_master cap_list
                configuration: driver=serial latency=64 maxlatency=62 mingnt=1
                resources: irq:20 memory:fe8ff000-fe8fffff ioport:8800(size=256)
           *-network
                description: Ethernet interface
                product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth0
                version: 10
                serial: 00:13:d3:b6:0d:bb
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=82.22.72.183 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 ioport:8400(size=256) memory:fe8fec00-fe8fecff memory:fe8e0000-fe8effff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=32
                resources: irq:9 memory:fe8fe000-fe8fe7ff ioport:8c00(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=snd_atiixp latency=64 mingnt=2
             resources: irq:17 memory:febff400-febff4ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=amd64_edac
          resources: irq:0
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3500630AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: 5QG10JMC
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00021cfa
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 739e22d6-04f7-42f0-89e9-7e99603d63b3
                size: 463GiB
                capacity: 463GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-12-20 10:25:55 filesystem=ext4 lastmountpoint=/ modified=2014-12-31 07:49:06 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-12-31 07:49:06 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2557MiB
                capacity: 2557MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2557MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD_RW ND-3550A
             vendor: _NEC
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.52
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@2:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
             configuration: sectorsize=512
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde
             configuration: sectorsize=512
```

---

### Post by praseodym on 2014-12-31
Please show the outputs of
```

lsmod
ifconfig -a
cat /etc/resolv.conf
route -n
sudo apt-get install ethtool
sudo ethtool eth0
```

---

### Post by shantiq on 2014-12-31
thanx Praseodym



```
shantiq@shantiq-00000000000000000000000:~$ lsmod

Module                  Size  Used by
snd_hrtimer            12744  1 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391136  10 bnep,rfcomm
nvidia              10744943  39 
uvcvideo               80885  0 
amd64_edac_mod         32291  0 
k8temp                 12978  0 
serio_raw              13462  0 
edac_core              62291  2 amd64_edac_mod
edac_mce_amd           22617  1 amd64_edac_mod
snd_hda_codec_hdmi     46368  4 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
joydev                 17381  0 
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_usb_audio         153993  5 
snd_usbmidi_lib        29215  1 snd_usb_audio
snd_hda_intel          56451  2 
snd_hda_codec         192906  2 snd_hda_codec_hdmi,snd_hda_intel
snd_atiixp             19961  0 
snd_ac97_codec        130285  1 snd_atiixp
ac97_bus               12730  1 snd_ac97_codec
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm               102099  7 snd_usb_audio,snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_atiixp
snd_page_alloc         18710  3 snd_pcm,snd_hda_intel,snd_atiixp
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
binfmt_misc            17468  1 
snd_rawmidi            30144  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                61560  3 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  3 snd_hrtimer,snd_pcm,snd_seq
snd                    69322  29 snd_hrtimer,snd_usb_audio,snd_ac97_codec,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_atiixp,snd_seq_midi
soundcore              12680  1 snd
drm                   303102  2 nvidia
i2c_piix4              22155  0 
mac_hid                13205  0 
parport_pc             32701  1 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
usb_storage            62209  0 
8139too                33544  0 
firewire_ohci          40409  0 
psmouse               106714  0 
firewire_core          68769  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
8139cp                 27953  0 
pata_acpi              13038  0 
mii                    13934  2 8139cp,8139too
pata_atiixp            13271  0 
sata_sil               13512  2 
floppy                 69418  0 


ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:d3:b6:0d:bb  
          inet addr:82.22.72.183  Bcast:82.22.79.255  Mask:255.255.248.0
          inet6 addr: fe80::213:d3ff:feb6:dbb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1003983 errors:0 dropped:0 overruns:0 frame:0
          TX packets:857120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:870170944 (870.1 MB)  TX bytes:682292116 (682.2 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:16037 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16037 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1511156 (1.5 MB)  TX bytes:1511156 (1.5 MB)


cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search cable.virginmedia.net




route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         82.22.72.1      0.0.0.0         UG    0      0        0 eth0
82.22.72.0      0.0.0.0         255.255.248.0   U     1      0        0 eth0


sudo ethtool eth0
[sudo] password for shantiq: 
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 32
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: yes


























 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d3:b6:0d:bb  
          inet addr:82.22.72.183  Bcast:82.22.79.255  Mask:255.255.248.0
          inet6 addr: fe80::213:d3ff:feb6:dbb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:915504 errors:0 dropped:0 overruns:0 frame:0
          TX packets:734480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:855700665 (855.7 MB)  TX bytes:525844318 (525.8 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:14936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1407722 (1.4 MB)  TX bytes:1407722 (1.4 MB)










sudo lshw 
[sudo] password for shantiq: 
shantiq-00000000000000000000000
    description: Desktop Computer
    product: 00000000000000000000000 (To Be Filled By O.E.M.)
    vendor: Packard Bell NEC
    version: PB34225301
    serial: 049652320227
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=549D0B9A-BE69-DA11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: MS-7168
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 1.0
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012
          date: 09/06/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 3400+
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1800MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 2560MiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM SDRAM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS480/RS482/RS485 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS4xx PCI Express Port [ext gfx]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:7000(size=4096) memory:fc600000-fe7fffff ioport:bbf00000(size=603979776)
           *-display
                description: VGA compatible controller
                product: GT218 [GeForce 8400 GS Rev. 3]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:7c00(size=128) memory:fe780000-fe7fffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:18 memory:fe77c000-fe77ffff
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:23 ioport:bc00(size=8) ioport:b800(size=4) ioport:b400(size=8) ioport:b000(size=4) ioport:ac00(size=16) memory:febffc00-febffdff memory:feb00000-feb7ffff
        *-ide:1
             description: IDE interface
             product: IXP SB4x0 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:22 ioport:a800(size=8) ioport:a400(size=4) ioport:a000(size=8) ioport:9c00(size=4) ioport:9800(size=16) memory:febff800-febff9ff memory:fea80000-feafffff
        *-usb:0
             description: USB controller
             product: IXP SB4x0 USB Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:febfe000-febfefff
        *-usb:1
             description: USB controller
             product: IXP SB4x0 USB Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:febfd000-febfdfff
        *-usb:2
             description: USB controller
             product: IXP SB4x0 USB2 Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:19 memory:febfc000-febfcfff
        *-serial
             description: SMBus
             product: IXP SB4x0 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:b00(size=16) memory:a0000000-a00003ff
        *-ide:2
             description: IDE interface
             product: IXP SB4x0 IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-isa
             description: ISA bridge
             product: IXP SB4x0 PCI-ISA Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB4x0 PCI-PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:8000(size=4096) memory:fe800000-fe8fffff
           *-communication
                description: Modem
                product: SmartLink SmartPCI562 56K Modem
                vendor: Smart Link Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm generic bus_master cap_list
                configuration: driver=serial latency=64 maxlatency=62 mingnt=1
                resources: irq:20 memory:fe8ff000-fe8fffff ioport:8800(size=256)
           *-network
                description: Ethernet interface
                product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth0
                version: 10
                serial: 00:13:d3:b6:0d:bb
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=82.22.72.183 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 ioport:8400(size=256) memory:fe8fec00-fe8fecff memory:fe8e0000-fe8effff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=32
                resources: irq:9 memory:fe8fe000-fe8fe7ff ioport:8c00(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=snd_atiixp latency=64 mingnt=2
             resources: irq:17 memory:febff400-febff4ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=amd64_edac
          resources: irq:0
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3500630AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: 5QG10JMC
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00021cfa
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 739e22d6-04f7-42f0-89e9-7e99603d63b3
                size: 463GiB
                capacity: 463GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-12-20 10:25:55 filesystem=ext4 lastmountpoint=/ modified=2014-12-31 07:49:06 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-12-31 07:49:06 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2557MiB
                capacity: 2557MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2557MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD_RW ND-3550A
             vendor: _NEC
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.52
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@2:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
             configuration: sectorsize=512
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde
             configuration: sectorsize=512









```

---

### Post by praseodym on 2014-12-31
There are 2 drivers loaded:
```

sudo modprobe -rfv 8139cp 8139too
sudo modprobe -v 8139too
echo "blacklist 8139cp" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo depmod -a
sudo update-initramfs -u
```
Only 10MB/s?!

Try
```

sudo ethtool -s eth0 speed 100 duplex full
sudo ethtool eth0
```
If the connection is gone, revert it via

```

sudo ethtool -s eth0 speed 10 duplex full
sudo ethtool eth0
```and try
```

sudo ethtool -s eth0 speed 10 autoneg off
```

---

### Post by shantiq on 2014-12-31
ok and  thanx for your time and effort

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo ethtool -s eth0 speed 100 duplex full
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo ethtool eth0[/FONT][/COLOR]
```


curtailed speed further


then ran

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo ethtool -s eth0 speed 10 duplex full[/FONT][/COLOR][COLOR=#000000]sudo ethtool eth0[/COLOR]
[COLOR=#000000]and try[/COLOR]
[COLOR=#000000]Code:
[/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]sudo ethtool -s eth0 speed 10 autoneg off[/FONT][/COLOR]
```



and got me back to where i was before but no increase in speed   ...    any other ideas ...    thanx




> [download] Destination: Innovate Africa - Science Africa-SQ_xv8KfRdc.mp4
[download]   5.0% of 390.71MiB at  **1.09MiB/s** ETA 05:39




The problem i seem to have is that the laptop receives 33MB   and the PC only 10!     how can that be?     what is blocking the flow here?

---

### Post by verymadpip on 2014-12-31
Hi there.
Really stupid question: have you restarted your router?
I'm with BT & my download speed dropped into the Kb range at one point, so I phoned 'em to have a rant.  They suggested I restart my router - problem solved.  Did I feel ever like a dufus....

---

### Post by TheFu on 2014-12-31
Thanks for posting the info.  Would be nicer to read with "code" tags so things line up.
a) do you have a router or not?
b) your NIC is set to 10 base-tx according to the lshw output. That should only happen when the other side of the connection can only talk at that speed. 100base-tx has been the min for over a decade.  
c) definitely try rebooting the router, like V-B-Pip says.

If none of the other things fixes it - try a different cable in a different port on the router that is known to work faster with a different device.
If all the same equipment worked faster, previously, do you have any idea what might have changed?  Any new software, drivers, thunderstorms ..... ?

---

### Post by shantiq on 2014-12-31
hi again Fu  as i was getting no reply here for a couple of days i started a more focussed thread elsewhere and the 100 vs 10 thing came up and [this]("http://ubuntuforums.org/showthread.php?t=2258378&p=13197765#post13197765") is what happened

so not good to me

as regards rebooting i do this everyday surely when i take my internet lead from router to laptop then back to PC

I unplug all and replug   that is rebooting ?    and again none of this slowdown happens on the Macbook with Ubuntu 14.04     there  is a reset button too on the modem   but i have never tried that    do not even know what it does


as regards drivers

using this currently   and pretty sure this was not the one before as 
i have an nvidia graphics card and did not before   cannot remember if drop of speed from the same time or not as 
only realized recently when started to use Macbook with Ubuntu side by side with PC

[ATTACH=CONFIG]258904[/ATTACH]

---

### Post by overdrank on 2014-12-31
Threads merged.

---

### Post by shantiq on 2015-01-01
thanx Overdrank

---

### Post by shantiq on 2015-01-01
and now tested it by removing nvidia driver and using xserver-xorg-video-nouveau

but as you see same result

[download] Destination: Innovate Africa - Science Africa-SQ_xv8KfRdc.mp4
[download]   9.0% of 390.71MiB at  **1.11MiB/s **ETA 05:21



the "block"/"cap"   does two things:

**1.   **it makes 1.11MiB/s the highest download speed on any download
**2.**   when it is on 1.11MiB/s none of the browsers will work
none of these restrictions apply when i take my very same wired internet connection to a Macbook with same 14.04 distro  **and never was there either on my PC** going back a year or two

so my question remains :  what else could be placing this **brake **on downloading speed ...    this is puzzling   ::]]    thanx for all help so far  but any other thoughts please

---

### Post by TheFu on 2015-01-01
To reboot is to remove all power then add power back usually with 30 seconds of complete ZERO power between. If there is a battery, the battery must not be used.  For a router, rebooting is usually pulling the power cord, waiting 30 seconds, reconnecting the power.

Plugging and unplugging ethernet cables does not reboot anything.

Ethernet devices wear out all the time, but I've never seen one slow down. I have seen them stop working completely.  When that happens, it is usually a mechanical issue - bad cable, bad port connector, or a bad port in the router/switch.  Just because 1 port on a switch has failed doesn't mean the others are impacted at all.

So .... if the macbook uses the exact same port to the router/switch and the exact same cable and everything performs well, then that leave the Ubuntu PC as the issue.  Inside the Ubuntu PC there is hardware and software which could be failing.  To test the hardware, boot off a liveCD or liveUSB flash version of any Linux, then test the speeds. If they are fast again, it is a software issue with your specific installation. Otherwise, if it is slow I'd call it a hardware issue and spend $25 to get a new NIC - I'm partial to the Intel PRO/1000 cards, but I like gigabit networking and only have that in my house. For most people any $5 linux compatible NIC will be fine to get 10/100 base-tx.  Of course, people with very high speed internet connections can use the faster cards - google fibre, people in South Korea with 400+Mbps connections and a few other places.  

After you test, we'd like to know the results so this thread can be marked "solved" - you've gotten a bunch of help here from some smart volunteers. We'd like closure. ;)

---

### Post by shantiq on 2015-01-01
ok Fu    so live usb test was done on sudodus 's advice and all was good it [seems]("http://ubuntuforums.org/showthread.php?t=2258378&p=13195689#post13195689")
so hardware as you suggest might be the way   since machine is 9 years old and has been used a LOT!

so [NIC]("http://en.wikipedia.org/wiki/Network_interface_controller") replacement time    could be knackered 
  never even heard of NIC until you mentioned   this is how much i know about the tech side

now what is a reasonable buy for a guy who wants to use this machine for say one more year tops/?

these are the specs of my machine so nothing too expensive but nothing k-r-a-p either  [ is this what you mean and suitable?]("http://www.amazon.co.uk/Intel-PRO-1000-Desktop-Adapter/dp/B00030DEOQ/ref=sr_1_1?ie=UTF8&qid=1420114239&sr=8-1&keywords=nic+Intel+PRO%2F1000")

PS   i too clearly want this sorted :]


```
  description: Desktop Computer    product: 00000000000000000000000 (To Be Filled By O.E.M.)
    vendor: Packard Bell NEC
    version: PB34225301
    serial: 049652320227
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=549D0B9A-BE69-DA11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: MS-7168
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 1.0
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012
          date: 09/06/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 3400+
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1GHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 2560MiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM SDRAM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS480/RS482/RS485 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS4xx PCI Express Port [ext gfx]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:7000(size=4096) memory:fc600000-fe7fffff ioport:bbf00000(size=603979776)
           *-display
                description: VGA compatible controller
                product: GT218 [GeForce 8400 GS Rev. 3]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:7c00(size=128) memory:fe780000-fe7fffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:18 memory:fe77c000-fe77ffff
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:23 ioport:bc00(size=8) ioport:b800(size=4) ioport:b400(size=8) ioport:b000(size=4) ioport:ac00(size=16) memory:febffc00-febffdff memory:feb00000-feb7ffff
        *-ide:1
             description: IDE interface
             product: IXP SB4x0 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:22 ioport:a800(size=8) ioport:a400(size=4) ioport:a000(size=8) ioport:9c00(size=4) ioport:9800(size=16) memory:febff800-febff9ff memory:fea80000-feafffff
        *-usb:0
             description: USB controller
             product: IXP SB4x0 USB Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:febfe000-febfefff
        *-usb:1
             description: USB controller
             product: IXP SB4x0 USB Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:febfd000-febfdfff
        *-usb:2
             description: USB controller
             product: IXP SB4x0 USB2 Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:19 memory:febfc000-febfcfff
        *-serial
             description: SMBus
             product: IXP SB4x0 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:b00(size=16) memory:a0000000-a00003ff
        *-ide:2
             description: IDE interface
             product: IXP SB4x0 IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-isa
             description: ISA bridge
             product: IXP SB4x0 PCI-ISA Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB4x0 PCI-PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:8000(size=4096) memory:fe800000-fe8fffff
           *-communication
                description: Modem
                product: SmartLink SmartPCI562 56K Modem
                vendor: Smart Link Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm generic bus_master cap_list
                configuration: driver=serial latency=64 maxlatency=62 mingnt=1
                resources: irq:20 memory:fe8ff000-fe8fffff ioport:8800(size=256)
           *-network
                description: Ethernet interface
                product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth0
                version: 10
                serial: 00:13:d3:b6:0d:bb
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=82.22.72.183 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 ioport:8400(size=256) memory:fe8fec00-fe8fecff memory:fe8e0000-fe8effff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=32
                resources: irq:9 memory:fe8fe000-fe8fe7ff ioport:8c00(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=snd_atiixp latency=64 mingnt=2
             resources: irq:17 memory:febff400-febff4ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=amd64_edac
          resources: irq:0
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3500630AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: 5QG10JMC
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00021cfa
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 739e22d6-04f7-42f0-89e9-7e99603d63b3
                size: 463GiB
                capacity: 463GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-12-20 10:25:55 filesystem=ext4 lastmountpoint=/ modified=2015-01-01 08:51:18 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-01-01 08:51:19 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2557MiB
                capacity: 2557MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2557MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD_RW ND-3550A
             vendor: _NEC
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.52
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@2:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
             configuration: sectorsize=512
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde
             configuration: sectorsize=512
     *-scsi:3
          physical id: 5
          bus info: usb@1:5
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: DVD-RAM writer
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sr1
             capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: status=nodisc



```

---

### Post by TheFu on 2015-01-01
If the speed was back to nromal using a liveboot, then changing the NIC isn't needed.  Using the liveboot, see what driver is used and the settings used by it, then put those into your installed OS.

Mainly, you want the same driver to be used so that 100 base-tx is automatically enabled.

---

### Post by shantiq on 2015-01-01
oh sorry Fu you clearly know this stuff like the back of your hand.   i do not :]
you mean    back to live  usb and run     sudo lshw     ?

sorry this takes time but this is territory i am not familiar with    so will do a live usb boot     do lshw    and post here

then if you do not mind    please say what needs to be modified on current install    thanx   shan

---

### Post by TheFu on 2015-01-01
We don't need/or want to see the complete output. Just the network stuff.
# lshw -C network
```
  *-network
       description: Ethernet interface
       physical id: 1
       bus info: usb@3:1.1
       logical name: eth0
       serial: 00:23:55:3c:23:37
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ax88179_178a duplex=full ip=172.22.22.13 link=yes multicast=yes port=MII speed=1Gbit/s

```
is mine. The driver is ax88179_178a - see that?  You want to see that in the working liveboot - and make certain your installed Ubuntu uses the same driver.

---

### Post by shantiq on 2015-01-01
ok so ran it in both driver the same   but see highlighted in red surely that is where the limitation is    how to correct that?

LIVE USB


```
sudo  lshw -C network   LIVE USB
  *-network               
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:b6:0d:bb
       [B][COLOR=#b22222]size: 10Mbit/s
       capacity: 100Mbit/s[/COLOR][/B]
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=8139too** driverversion=0.9.28 duplex=full ip=82.22.72.183 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII **[COLOR=#800000]speed=10Mbit/s[/COLOR]**
       resources: irq:20 ioport:8400(size=256) memory:fe8fec00-fe8fecff memory:fe8e0000-fe8effff

``` 



PC


```
sudo  lshw -C network 
[sudo] password for shantiq: 
  *-network               
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:b6:0d:bb
       [COLOR=#800000][B]size: 10Mbit/s
       capacity: 100Mbit/s[/B][/COLOR]
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=8139too** driverversion=0.9.28 duplex=full ip=82.22.72.183 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII [COLOR=#800000]**speed=10Mbit/s**[/COLOR]
       resources: irq:20 ioport:8400(size=256) memory:fe8fec00-fe8fecff memory:fe8e0000-fe8effff
```


**edit   **


so i ran the same command on the Macbook and no discrepancy between size and capacity   Why is it there on the PC???

> shantiq@shantiq-MacBook:~$ sudo lshw -C network[sudo] password for shantiq: 
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 22
       serial: 00:17:f2:dc:e1:70
       [COLOR=#800000][B]size: 1Gbit/s
       capacity: 1Gbit/s[/B][/COLOR]
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=82.21.135.241 latency=0 link=yes multicast=yes port=twisted pair **[COLOR=#800000]speed=1Gbit/s[/COLOR]**
       resources: irq:42 memory:90200000-90203fff ioport:1000(size=256) memory:90500000-9051ffff




---

### Post by TheFu on 2015-01-01
Previously, you said that everything was faster under the liveboot - that is not the case.  

You need someone with driver expertise to help determine why this 100base-tx card is stuck at 10base-tx speeds
or
you need a new NIC.

That is not me. Sorry.  All I can suggest is that you search these forums and the internet for 8139too driver tweaks.  You've already tried everything I know by using ethtool and that didn't help.  If you truly have used the exact same cable for the macbook as for this PC, then simple cable and router port changes won't help.

---

### Post by shantiq on 2015-01-01
ok thanx fu   never said faster live just faster Ubuntu **Macbook **   thanx for your help genuinely thanx 

[COLOR=#000000]so i ran the same command on the Macbook and no discrepancy between size and capacity Why is it there on the PC??? [ see]("http://ubuntuforums.org/showthread.php?t=2258378&p=13198455#post13198455")[/COLOR]

---

### Post by praseodym on 2015-01-01
Was it the same cable?

---

### Post by shantiq on 2015-01-01
yes the exact same  pull it out of the PC   and to the Macbook   one does

[B]```
size: 1Gbit/s
capacity: 1Gbit/s
```  [/B]

 other does 

```
[B]size: 10Mbit/s
[/B]**capacity: 100Mbit/s**
```

there is the puzzle

---

### Post by sudodus on 2015-01-01
Your ethernet card might be bad (although not very common, that might be the case, usually it works or does not work at all).

But before deciding to get a new ethernet card, ***did you check with a live system***, not only lshw, but ***also the internet connection speed***)?

---

### Post by shantiq on 2015-01-01
hi sudodus   did internet speedtest on Macbook   and 33Mb    on PC   10Mb   which tallies with  > **size: 10Mbit/s**
   not done speedtest with live usb    **edit**   done it now   and reached 9Mb  so same as installed 14.04 on PC

---

### Post by sudodus on 2015-01-01
> **shantiq said:**
> hi sudodus   did internet speedtest on Macbook   and 33Mb    on PC   10Mb   which tallies with     not done speedtest with live usb    **edit**   done it now   and reached 9Mb  so same as installed 14.04 on PC

Then it seems to me, that the ethernet card might be bad. I suggest that you look for a new card corresponding to *TheFu*'s advice earlier in this merged thread.

---

### Post by shantiq on 2015-01-02
that does make a lot of sense Sudodus considering the age of the machine and the number of hours it has been used   the ethernet card is the same as NIC right?    ok will take a look see how to do this   hopefully the problem is that 
    makes the most sense     thanx again

---

### Post by shantiq on 2015-01-04
ok so i had a look inside the machine and it looks as if to change the ethernet card on this Packard Bell PC model **specs at bottom of page **is not easy or even possible as it is embedded with other equipment it seems part of a block?

see here


[ATTACH=CONFIG]258989[/ATTACH][ATTACH=CONFIG]258988[/ATTACH]



and i still do not understand why it says that a hundred is available and only accepts 10   when it accepted  higher before

shantiq@shantiq-00000000000000000000000:~$ sudo ethtool -s eth0 speed 1000 autoneg off
Cannot set new settings: Invalid argument
  not setting speed
  not setting autoneg
shantiq@shantiq-00000000000000000000000:~$ sudo ethtool -s eth0 speed 100 autoneg off   **<==  this cuts the flow**
shantiq@shantiq-00000000000000000000000:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 3642
shantiq@shantiq-00000000000000000000000:~$ sudo ethtool -s eth0 speed 10 autoneg off   **<==   and here comes back on**
shantiq@shantiq-00000000000000000000000:~$ sudo ethtool -s eth0 speed 100  **<==  this cuts the flow**
shantiq@shantiq-00000000000000000000000:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 3853
shantiq@shantiq-00000000000000000000000:~$ sudo ethtool -s eth0 speed 10 autoneg off  [B]<==   and here comes back on



although

[/B]```
shantiq@shantiq-00000000000000000000000:~$ sudo lshw -class network
[sudo] password for shantiq: 
  *-network               
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:b6:0d:bb
[COLOR=#b22222][SIZE=3]**       size: 10Mbit/s**[/SIZE][/COLOR]
[COLOR=#b22222][SIZE=3]**       capacity: 100Mbit/s         so it is there in the system!**[/SIZE][/COLOR]
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=82.22.72.183 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 ioport:8400(size=256) memory:fe8fec00-fe8fecff memory:fe8e0000-fe8effff
shantiq@shantiq-00000000000000000000000:~$ ethtool -i eth0
driver: 8139too
version: 0.9.28
firmware-version: 
bus-info: 0000:02:03.0
supports-statistics: yes
supports-test: no
supports-eeprom-access: no
supports-register-dump: no
supports-priv-flags: no
shantiq@shantiq-00000000000000000000000:~$ ls /sys/class/net
eth0  lo
shantiq@shantiq-00000000000000000000000:~$ dmesg | grep -e 8139 -e eth
[    0.120316] pci 0000:02:03.0: [10ec:8139] type 00 class 0x020000
[    1.138917] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.138961] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.155993] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.158742] 8139too 0000:02:03.0 eth0: RealTek RTL8139 at 0x0000000000018400, 00:13:d3:b6:0d:bb, IRQ 20
[   14.252139] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.279709] 8139too 0000:02:03.0 eth0: link up, 10Mbps, full-duplex, lpa 0x4061










```


got

```
# interfaces(5) file used by ifup(8) and ifdown(8)auto lo
iface lo inet loopback



```    in   gksudo gedit /etc/network/interfaces




I am so puzzled here ...    any further suggestions before I actually give up on this one ...    the card change looks like a nightmare seeing the inside of the machine  so any last-ditch code ideas from anyone knowledgeable enough     thanx    PS   otherwise i shall leave it alone for


full specs

```
 sudo lshw[sudo] password for shantiq: 
shantiq-00000000000000000000000
    description: Desktop Computer
    product: 00000000000000000000000 (To Be Filled By O.E.M.)
    vendor: Packard Bell NEC
    version: PB34225301
    serial: 049652320227
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=549D0B9A-BE69-DA11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: MS-7168
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 1.0
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012
          date: 09/06/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 3400+
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1GHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 2560MiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM SDRAM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS480/RS482/RS485 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS4xx PCI Express Port [ext gfx]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:7000(size=4096) memory:fc600000-fe7fffff ioport:bbf00000(size=603979776)
           *-display
                description: VGA compatible controller
                product: GT218 [GeForce 8400 GS Rev. 3]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:7c00(size=128) memory:fe780000-fe7fffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:18 memory:fe77c000-fe77ffff
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:23 ioport:bc00(size=8) ioport:b800(size=4) ioport:b400(size=8) ioport:b000(size=4) ioport:ac00(size=16) memory:febffc00-febffdff memory:feb00000-feb7ffff
        *-ide:1
             description: IDE interface
             product: IXP SB4x0 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:22 ioport:a800(size=8) ioport:a400(size=4) ioport:a000(size=8) ioport:9c00(size=4) ioport:9800(size=16) memory:febff800-febff9ff memory:fea80000-feafffff
        *-usb:0
             description: USB controller
             product: IXP SB4x0 USB Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:febfe000-febfefff
        *-usb:1
             description: USB controller
             product: IXP SB4x0 USB Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:febfd000-febfdfff
        *-usb:2
             description: USB controller
             product: IXP SB4x0 USB2 Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:19 memory:febfc000-febfcfff
        *-serial
             description: SMBus
             product: IXP SB4x0 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:b00(size=16) memory:a0000000-a00003ff
        *-ide:2
             description: IDE interface
             product: IXP SB4x0 IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-isa
             description: ISA bridge
             product: IXP SB4x0 PCI-ISA Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB4x0 PCI-PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:8000(size=4096) memory:fe800000-fe8fffff
           *-communication
                description: Modem
                product: SmartLink SmartPCI562 56K Modem
                vendor: Smart Link Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm generic bus_master cap_list
                configuration: driver=serial latency=64 maxlatency=62 mingnt=1
                resources: irq:20 memory:fe8ff000-fe8fffff ioport:8800(size=256)
           *-network
                description: Ethernet interface
                product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth0
                version: 10
                serial: 00:13:d3:b6:0d:bb
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=off broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=82.22.72.183 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 ioport:8400(size=256) memory:fe8fec00-fe8fecff memory:fe8e0000-fe8effff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=32
                resources: irq:9 memory:fe8fe000-fe8fe7ff ioport:8c00(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=snd_atiixp latency=64 mingnt=2
             resources: irq:17 memory:febff400-febff4ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=amd64_edac
          resources: irq:0
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3500630AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: 5QG10JMC
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00021cfa
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 739e22d6-04f7-42f0-89e9-7e99603d63b3
                size: 463GiB
                capacity: 463GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-12-20 10:25:55 filesystem=ext4 lastmountpoint=/ modified=2015-01-04 09:08:42 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-01-04 09:08:42 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2557MiB
                capacity: 2557MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2557MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD_RW ND-3550A
             vendor: _NEC
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.52
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@2:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
             configuration: sectorsize=512
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde
             configuration: sectorsize=512



```

---

### Post by TheFu on 2015-01-04
Dude.  Disable the onboard ethernet inside the BIOS and drop in a $5 new NIC. Do not try to do anything physically to the old NIC.
When you're done added the new card, just move the cable over to the new port.

Why - sometimes electronic components fail. See all that dust, that didn't help though I've seen worse.  Old stuff just breaks, espectally on computers.  This is a $5-$25 fix - worse case. No big deal.  The $25 fix is for an Intel PRO/1000 NIC which is the industry standard for networking and extremely well supported on every platform.

---

### Post by shantiq on 2015-01-04
Thanx Fu .  Of course i would be happy to shell $20 to fix things here
You may  have to be a bit more specific here please


[COLOR=#000000]Disable the onboard ethernet inside the BIOS and drop in a $5 new NIC     what do you mean by drop in    **do you mean an external card **   sorry   i really know nowt about all this
Like you are sprinting  and i am crawling here :]

Could you explain steps in a bit more detailed fashion if you have the time thanx   shan[/COLOR]

---

### Post by TheFu on 2015-01-04
[https://www.youtube.com/watch?v=BZS1Lvb23VA](https://www.youtube.com/watch?v=BZS1Lvb23VA) - only changes to that are - if the card isn't automatically recognized by Linux - take it back and get a different one.  For many questions, youtube has examples, you doin't have to limit yourself to just these forums.

---

### Post by shantiq on 2015-01-04
ok Fu taken good note and got the idea .   will report when hardware arrives.   Thanx for info and time

---

### Post by shantiq on 2015-01-07
Ok guys it was the NIC and i probably used my PC for over a year at a third of the speed;    that is a dork for you :]
Thanx to all you guys who gave good advice especially TheFu for the last hurdle
I am not great at fiddling inside a machine but this was fairly easy


Turns out this card is seen by Linux as comments show on the Amazon page

[URL="http://www.amazon.co.uk/product-reviews/B0000TO0BQ/ref=cm_cr_dp_see_all_btm?ie=UTF8&showViewpoints=1&sortBy=bySubmissionDateDescending"]StarTech.com 1 Port PCI 10/100/1000 32 Bit Gigabit Ethernet Network Adapter Card
[/URL] 


```
[download]   2.6% of 1.39GiB at  3.68MiB/s ETA 06:16

``` 



 ```
sudo lshw -class network
[sudo] password for shantiq: 
  *-network:0             
       description: Ethernet interface
       product: RTL8169 PCI Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth1
       version: 10
       serial: 00:0a:cd:26:64:71
       [B]size: 1Gbit/s
       capacity: 1Gbit/s[/B]
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=82.20.25.138 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1Gbit/s
       resources: irq:9 ioport:8400(size=256) memory:fe8fec00-fe8fecff memory:fe8c0000-fe8dffff
  *-network:1
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:b6:0d:bb
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 ioport:8000(size=256) memory:fe8fe800-fe8fe8ff memory:fe8e0000-fe8effff
```

---

