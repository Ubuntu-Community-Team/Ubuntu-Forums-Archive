---
title: "Losing the will with Ubuntu, please help!"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Shmeegs2001 on 2009-01-29
Hi everyone!

I'm really losing the will with Ubuntu and I am getting seriously tempted to take my laptop to the shop and get Windows installed.  My friend is convinced that Ubuntu is better than Windows for countless reasons, but I am having so many problems with it and I have no idea how to fix them, so I'm just not sure!  If anyone can help, please do!

Problem 1 - After installing Ubuntu 8.10 my wireless stopped working.  The box for 'Enable Wireless' is there, but it is greyed out and I can't get it to work!!!

Problem 2 - I cannot stream anything at all on the internet.  I need to use Youtube, and Myspace for my work but all I get is a black box with nothing going on in it!

I have a pretty basic grasp of all of this!  hopefully someone can help!

Cheers

Sam

---

### Post by UbuntuNerd on 2009-01-29
type this command in a terminal by going to system > accessories > terminal, one at a time and you should be able to watch anything
```
sudo apt-get install flashplugin-nonfree flashplayer-nonfree
```
```
sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin
```
also install all the plugins in this guide:
[http://my.opera.com/ubuntunerd1/blog/how-to-play-quicktime-videos-and-other-media-with-totem]("http://my.opera.com/ubuntunerd1/blog/how-to-play-quicktime-videos-and-other-media-with-totem")
im sorry I guess you need to resolve the wireless problem before you can do all this post your hardware.

---

### Post by Lostin60's on 2009-01-29
> **Shmeegs2001 said:**
> Hi everyone!

I'm really losing the will with Ubuntu and I am getting seriously tempted to take my laptop to the shop and get Windows installed.  My friend is convinced that Ubuntu is better than Windows for countless reasons, but I am having so many problems with it and I have no idea how to fix them, so I'm just not sure!  If anyone can help, please do!

Problem 1 - After installing Ubuntu 8.10 my wireless stopped working.  The box for 'Enable Wireless' is there, but it is greyed out and I can't get it to work!!!

Problem 2 - I cannot stream anything at all on the internet.  I need to use Youtube, and Myspace for my work but all I get is a black box with nothing going on in it!

I have a pretty basic grasp of all of this!  hopefully someone can help!

Cheers

Sam

These should fix you right up
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
this is a great wireless tutorial, it will get your wireless going.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
follow all of this tut, and all your issues with video, both off and on line should go away.
are you dual booting windows?, If so use the file browser to find your wireless cards .sys and .inf files and copy them to your desktop, as you will need them. 
These tuts saved my but when I started.  Don't give up. also, what ubuntunoob said will prolly work, but the tuts are far more in depth, and get you better results..no offence noob
[COLOR="White"]aa[/COLOR]

---

### Post by smothpocket on 2009-01-29
You have to install flash in order to view the streaming video as stated above. As for the wireless, you probably have to install the driver... there are plenty of guides on how to do this.

Even if you do switch back to Windows, I wouldn't recommend taking it to a "shop"... they'll charge way to much for something you can do yourself.

Ultimately, if you want a successful and happy user experience with Ubuntu, you'll have to be willing to do a bit of research. Well worth it in my opinion though. :D

---

### Post by xfacta on 2009-01-29
My recommendation is use wicd for networking and uninstall network manager.
Definitely use the wireless tutorial mentioned, it may cover wicd already.

If your Flash doesn't get sorted out using the previous posts here then: 
[LIST]
[*]uninstall the non-free plugins and gnash
[*]go to [www.adobe.com](www.adobe.com) and download the .deb there for Flash player
[*]double click on it to install
[*]close and reopen FireFox
[/LIST]
That should sort out your Flash problems

The only down-side is you'll have to revisit the adobe site and get a new .deb if you ever have a problem/bug with the flash player, and it won't be included in the Ubuntu update process.

---

### Post by GepettoBR on 2009-01-29
> **smothpocket said:**
> You have to install flash in order to view the streaming video as stated above. As for the wireless, you probably have to install the driver... there are plenty of guides on how to do this.

Even if you do switch back to Windows, I wouldn't recommend taking it to a "shop"... they'll charge way to much for something you can do yourself.

Ultimately, if you want a successful and happy user experience with Ubuntu, you'll have to be willing to do a bit of research. Well worth it in my opinion though. :D

Seconded.

As a person who still uses both Ubuntu and Windows a lot, this is my advice to you: Windows is a lot easier to setup and get working, but it will break often. Ubuntu is hard to set up, but once you're done, you won't ever have to mess withthe configurations again if you don't want to. If it gets frustrating, just think that on the long run, you'd spend more time configuring Windows than Ubuntu, but in Ubuntu you kind of have to do it all at once while Windows splits it up.

Each OS has its strengths and weaknesses. If you choose to go back to Windows or stay with Ubuntu, make sure that your choice takes that into account.

---

### Post by egalvan on 2009-01-29
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by sydbat on 2009-01-29
> **Shmeegs2001 said:**
> I need to use Youtube, and Myspace for my workHow can I find a job like yours!!:-k

Follow the above tutorials and you should be fine.

---

### Post by Cosimix on 2009-01-29
OK First your friend is absolutely right about choosing Ubuntu. The more you use it the earlier you will understand why. 

**By the way, is the online support for Win as good as Ubuntu's??   **

About video streaming on Firefox I use the non-free FlashPlayer plugin and it works. It does noticeably consume CPU horses (that's another issue).

The deb package from **[Adobe.com]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb")** also should work.


To install** non-free** do the following:

Application >> Accessories >> Terminal

**sudo apt-get install flashplugin-nonfree**

Restart your browser

**[COLOR=Red]YOU ARE DONE[/COLOR]**


**Wireless Issue**
 [COLOR=Black]Run this command and send all the output to me, then I will give you the solution:

**lspci > ~/Desktop/log **
**dmesg >> ~/Desktop/log **
**sudo lshw -C network >> ~/Desktop/log **
**sudo lsmod >> ~/Desktop/log **

[COLOR=DarkGreen]
[COLOR=DarkRed]*****Note** The above commands create one text file named **log** on your Desktop, please attach it to this thread and I will give you the solution[/COLOR][/COLOR][/COLOR][COLOR=Black][COLOR=DarkGreen][COLOR=DarkRed]*** 

**[COLOR=Black]Ciao[/COLOR]**
[/COLOR][/COLOR][/COLOR][COLOR=Black][COLOR=DarkGreen] [/COLOR]
[/COLOR]

---

### Post by Shmeegs2001 on 2009-01-29
Hi!

Thanks everyone for the awesome support!  I've just got the sound back on (did what Xfacta said).  And I am working my way through the tutorials on Wireless at the moment!

Thanks a lot for the help, and advise on Windows to!  I'm sure I'll be back here for help again, but until then!

Cheers

Sam

---

### Post by Shmeegs2001 on 2009-01-29
Oops, sorry, didnt see that message from Cosimix!  How do I run a command?  Like i said, I really don't no anything about working this stuff!

Cheers

Sam

---

### Post by Shmeegs2001 on 2009-01-29
[U][B]dmesg.log 
[/B][/U]
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Wed Jan 28 00:02:01 UTC 2009 (Ubuntu 2.6.27-11.26-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f66d800 (usable)
[    0.000000]  BIOS-e820: 000000007f66d800 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x7f66d max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3781d000 - 37fefc9b
[    0.000000] ACPI: RSDP 000FBC60, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 7F66F200, 0064 (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: FACP 7F66F09C, 00F4 (r4 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: DSDT 7F66F800, 5495 (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 7F67E000, 0040
[    0.000000] ACPI: HPET 7F66F300, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC 7F66F400, 0068 (r1 DELL    M08     27D8030A ASL        47)
[    0.000000] ACPI: MCFG 7F66F3C0, 003E (r16 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: SLIC 7F66F49C, 0024 (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: OSFR 7F66EA00, 002C (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: BOOT 7F66EFC0, 0028 (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: SSDT 7F66DA44, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003781d000 - 0037fefc9b]          RAMDISK ==> [003781d000 - 0037fefc9b]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007f66d
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f66d
[    0.000000] On node 0 totalpages: 521740
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 289890 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:78000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517153
[    0.000000] Kernel command line: root=UUID=300afdd1-2cd1-4e19-9934-50c8265e411a ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1828.720 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2053868k/2087348k available (2576k kernel code, 32208k reserved, 1165k data, 424k init, 1169844k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3657.44 BogoMIPS (lpj=7314880)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017985] ACPI: Core revision 20080609
[    0.019900] ACPI: Checking initramfs for custom DSDT
[    0.388270] ENABLING IO-APIC IRQs
[    0.388465] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.428296] CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.432027] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3657.42 BogoMIPS (lpj=7314853)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.516499] CPU1: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.516517] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.520049] Brought up 2 CPUs
[    0.520052] Total of 2 processors activated (7314.86 BogoMIPS).
[    0.520074] CPU0 attaching sched-domain:
[    0.520077]  domain 0: span 0-1 level MC
[    0.520080]   groups: 0 1
[    0.520087] CPU1 attaching sched-domain:
[    0.520089]  domain 0: span 0-1 level MC
[    0.520092]   groups: 1 0
[    0.520171] net_namespace: 840 bytes
[    0.520171] Booting paravirtualized kernel on bare hardware
[    0.520319] Time: 18:54:17  Date: 01/29/09
[    0.520346] NET: Registered protocol family 16
[    0.520365] EISA bus registered
[    0.520365] ACPI: bus type pci registered
[    0.520365] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.520365] PCI: MCFG area at f8000000 reserved in E820
[    0.520365] PCI: Using MMCONFIG for extended config space
[    0.520365] PCI: Using configuration type 1 for base access
[    0.521057] ACPI: EC: Look up EC in DSDT
[    0.521291] ACPI: BIOS _OSI(Linux) query ignored
[    0.521293] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
[    0.553424] ACPI: Interpreter enabled
[    0.553429] ACPI: (supports S0 S3 S4 S5)
[    0.553444] ACPI: Using IOAPIC for interrupt routing
[    0.604179] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.604179] PCI: 0000:00:02.0 reg 10 64bit mmio: [fea00000, feafffff]
[    0.604179] PCI: 0000:00:02.0 reg 18 64bit mmio: [e0000000, efffffff]
[    0.604179] PCI: 0000:00:02.0 reg 20 io port: [eff8, efff]
[    0.604179] PCI: 0000:00:02.1 reg 10 64bit mmio: [feb00000, febfffff]
[    0.604287] PCI: 0000:00:1a.0 reg 20 io port: [6f20, 6f3f]
[    0.604358] PCI: 0000:00:1a.1 reg 20 io port: [6f00, 6f1f]
[    0.604436] PCI: 0000:00:1a.7 reg 10 32bit mmio: [fed1c400, fed1c7ff]
[    0.604500] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.604507] pci 0000:00:1a.7: PME# disabled
[    0.604560] PCI: 0000:00:1b.0 reg 10 64bit mmio: [fe9fc000, fe9fffff]
[    0.604619] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.604625] pci 0000:00:1b.0: PME# disabled
[    0.604704] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.604709] pci 0000:00:1c.0: PME# disabled
[    0.604790] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.604796] pci 0000:00:1c.1: PME# disabled
[    0.604879] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.604885] pci 0000:00:1c.4: PME# disabled
[    0.604940] PCI: 0000:00:1d.0 reg 20 io port: [6f80, 6f9f]
[    0.605010] PCI: 0000:00:1d.1 reg 20 io port: [6f60, 6f7f]
[    0.605081] PCI: 0000:00:1d.2 reg 20 io port: [6f40, 6f5f]
[    0.605158] PCI: 0000:00:1d.7 reg 10 32bit mmio: [fed1c000, fed1c3ff]
[    0.605221] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.605228] pci 0000:00:1d.7: PME# disabled
[    0.605403] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.605408] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.605441] PCI: 0000:00:1f.1 reg 10 io port: [1f0, 1f7]
[    0.605450] PCI: 0000:00:1f.1 reg 14 io port: [3f4, 3f7]
[    0.605459] PCI: 0000:00:1f.1 reg 18 io port: [170, 177]
[    0.605468] PCI: 0000:00:1f.1 reg 1c io port: [374, 377]
[    0.605477] PCI: 0000:00:1f.1 reg 20 io port: [6fa0, 6faf]
[    0.605559] PCI: 0000:00:1f.2 reg 10 io port: [6eb0, 6eb7]
[    0.605568] PCI: 0000:00:1f.2 reg 14 io port: [6eb8, 6ebb]
[    0.605577] PCI: 0000:00:1f.2 reg 18 io port: [6ec0, 6ec7]
[    0.605586] PCI: 0000:00:1f.2 reg 1c io port: [6ec8, 6ecb]
[    0.605595] PCI: 0000:00:1f.2 reg 20 io port: [6ee0, 6eff]
[    0.605604] PCI: 0000:00:1f.2 reg 24 32bit mmio: [fe9fb800, fe9fbfff]
[    0.605641] pci 0000:00:1f.2: PME# supported from D3hot
[    0.605646] pci 0000:00:1f.2: PME# disabled
[    0.605669] PCI: 0000:00:1f.3 reg 10 32bit mmio: [fe9fb700, fe9fb7ff]
[    0.605699] PCI: 0000:00:1f.3 reg 20 io port: [10c0, 10df]
[    0.605811] PCI: 0000:09:00.0 reg 10 64bit mmio: [fe8fc000, fe8fffff]
[    0.605823] PCI: 0000:09:00.0 reg 18 io port: [de00, deff]
[    0.605902] pci 0000:09:00.0: supports D1
[    0.605904] pci 0000:09:00.0: supports D2
[    0.605906] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.605914] pci 0000:09:00.0: PME# disabled
[    0.605973] PCI: bridge 0000:00:1c.0 io port: [d000, dfff]
[    0.605979] PCI: bridge 0000:00:1c.0 32bit mmio: [fe800000, fe8fffff]
[    0.606175] PCI: 0000:0b:00.0 reg 10 32bit mmio: [fe7ff000, fe7fffff]
[    0.606390] pci 0000:0b:00.0: PME# supported from D0 D3hot D3cold
[    0.606404] pci 0000:0b:00.0: PME# disabled
[    0.606466] PCI: bridge 0000:00:1c.1 32bit mmio: [fe700000, fe7fffff]
[    0.606541] PCI: bridge 0000:00:1c.4 io port: [c000, cfff]
[    0.606547] PCI: bridge 0000:00:1c.4 32bit mmio: [fe400000, fe6fffff]
[    0.606556] PCI: bridge 0000:00:1c.4 64bit mmio pref: [f0000000, f01fffff]
[    0.606624] PCI: 0000:02:09.0 reg 10 32bit mmio: [fe3ff800, fe3fffff]
[    0.606686] pci 0000:02:09.0: supports D1
[    0.606688] pci 0000:02:09.0: supports D2
[    0.606690] pci 0000:02:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.606695] pci 0000:02:09.0: PME# disabled
[    0.606737] PCI: 0000:02:09.1 reg 10 32bit mmio: [fe3ff500, fe3ff5ff]
[    0.606798] pci 0000:02:09.1: supports D1
[    0.606799] pci 0000:02:09.1: supports D2
[    0.606802] pci 0000:02:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.606807] pci 0000:02:09.1: PME# disabled
[    0.606850] PCI: 0000:02:09.2 reg 10 32bit mmio: [fe3ff600, fe3ff6ff]
[    0.606912] pci 0000:02:09.2: supports D1
[    0.606914] pci 0000:02:09.2: supports D2
[    0.606916] pci 0000:02:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.606922] pci 0000:02:09.2: PME# disabled
[    0.606964] PCI: 0000:02:09.3 reg 10 32bit mmio: [fe3ff700, fe3ff7ff]
[    0.607027] pci 0000:02:09.3: supports D1
[    0.607028] pci 0000:02:09.3: supports D2
[    0.607031] pci 0000:02:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.607036] pci 0000:02:09.3: PME# disabled
[    0.607093] pci 0000:00:1e.0: transparent bridge
[    0.607102] PCI: bridge 0000:00:1e.0 32bit mmio: [fe300000, fe3fffff]
[    0.607140] bus 00 -> node 0
[    0.607147] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.608290] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.608493] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.608661] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.608824] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.624187] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.624350] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.624511] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
[    0.624656] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
[    0.624821] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.624985] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.625149] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.625299] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.625388] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.625388] pnp: PnP ACPI init
[    0.625388] ACPI: bus type pnp registered
[    0.649919] pnp 00:0a: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.649919] pnp 00:0a: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.649919] pnp 00:0b: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.649919] pnp 00:0b: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.649919] pnp 00:0b: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.649919] pnp 00:0b: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.679522] pnp: PnP ACPI: found 13 devices
[    0.679522] ACPI: ACPI bus type pnp unregistered
[    0.679522] PnPBIOS: Disabled by ACPI PNP
[    0.680055] PCI: Using ACPI for IRQ routing
[    0.684041] NET: Registered protocol family 8
[    0.684044] NET: Registered protocol family 20
[    0.684061] NetLabel: Initializing
[    0.684061] NetLabel:  domain hash size = 128
[    0.684061] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.684068] NetLabel:  unlabeled traffic allowed by default
[    0.684077] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.684082] hpet0: 3 64-bit timers, 14318180 Hz
[    0.685604] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.685607]    actual entries 65620
[    0.685701] AppArmor: AppArmor Filesystem Enabled
[    0.685729] ACPI: RTC can wake from S4
[    0.688039] Switched to high resolution mode on CPU 0
[    0.688536] Switched to high resolution mode on CPU 1
[    0.692023] system 00:01: iomem range 0xff800000-0xff8fffff has been reserved
[    0.692027] system 00:01: iomem range 0xffc00000-0xffcfffff has been reserved
[    0.692037] system 00:06: ioport range 0xc80-0xcff could not be reserved
[    0.692046] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.692052] system 00:0a: ioport range 0x900-0x97f has been reserved
[    0.692055] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.692069] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
[    0.692072] system 00:0b: ioport range 0x1080-0x10bf has been reserved
[    0.692076] system 00:0b: ioport range 0x10c0-0x10df has been reserved
[    0.692079] system 00:0b: ioport range 0x809-0x809 has been reserved
[    0.692086] system 00:0c: iomem range 0x0-0x9efff could not be reserved
[    0.692089] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
[    0.692092] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.692096] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.692099] system 00:0c: iomem range 0x100000-0x7f66d7ff could not be reserved
[    0.692102] system 00:0c: iomem range 0x7f66d800-0x7f6fffff could not be reserved
[    0.692106] system 00:0c: iomem range 0x7f700000-0x7f7fffff could not be reserved
[    0.692109] system 00:0c: iomem range 0x7f700000-0x7fefffff could not be reserved
[    0.692113] system 00:0c: iomem range 0xffe00000-0xffffffff could not be reserved
[    0.692116] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.692119] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.692123] system 00:0c: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    0.692126] system 00:0c: iomem range 0xfed20000-0xfed8ffff could not be reserved
[    0.692130] system 00:0c: iomem range 0xfeda0000-0xfeda3fff could not be reserved
[    0.692133] system 00:0c: iomem range 0xfeda4000-0xfeda4fff could not be reserved
[    0.692136] system 00:0c: iomem range 0xfeda5000-0xfeda5fff could not be reserved
[    0.692140] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.692143] system 00:0c: iomem range 0xfed18000-0xfed1bfff could not be reserved
[    0.692147] system 00:0c: iomem range 0xf8000000-0xfbffffff could not be reserved
[    0.727258] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:09
[    0.727263] pci 0000:00:1c.0:   IO window: 0xd000-0xdfff
[    0.727270] pci 0000:00:1c.0:   MEM window: 0xfe800000-0xfe8fffff
[    0.727276] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.727285] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0b
[    0.727287] pci 0000:00:1c.1:   IO window: disabled
[    0.727294] pci 0000:00:1c.1:   MEM window: 0xfe700000-0xfe7fffff

continued....

---

### Post by Shmeegs2001 on 2009-01-29
...


[    0.727300] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.727309] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0c
[    0.727313] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
[    0.727320] pci 0000:00:1c.4:   MEM window: 0xfe400000-0xfe6fffff
[    0.727326] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.727335] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.727338] pci 0000:00:1e.0:   IO window: disabled
[    0.727345] pci 0000:00:1e.0:   MEM window: 0xfe300000-0xfe3fffff
[    0.727350] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.727370] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.727377] pci 0000:00:1c.0: setting latency timer to 64
[    0.727388] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.727394] pci 0000:00:1c.1: setting latency timer to 64
[    0.727404] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.727410] pci 0000:00:1c.4: setting latency timer to 64
[    0.727419] pci 0000:00:1e.0: setting latency timer to 64
[    0.727424] bus: 00 index 0 io port: [0, ffff]
[    0.727426] bus: 00 index 1 mmio: [0, ffffffff]
[    0.727429] bus: 09 index 0 io port: [d000, dfff]
[    0.727431] bus: 09 index 1 mmio: [fe800000, fe8fffff]
[    0.727434] bus: 09 index 2 mmio: [0, 0]
[    0.727436] bus: 09 index 3 mmio: [0, 0]
[    0.727438] bus: 0b index 0 mmio: [0, 0]
[    0.727440] bus: 0b index 1 mmio: [fe700000, fe7fffff]
[    0.727442] bus: 0b index 2 mmio: [0, 0]
[    0.727444] bus: 0b index 3 mmio: [0, 0]
[    0.727446] bus: 0c index 0 io port: [c000, cfff]
[    0.727449] bus: 0c index 1 mmio: [fe400000, fe6fffff]
[    0.727451] bus: 0c index 2 mmio: [f0000000, f01fffff]
[    0.727453] bus: 0c index 3 mmio: [0, 0]
[    0.727455] bus: 02 index 0 mmio: [0, 0]
[    0.727457] bus: 02 index 1 mmio: [fe300000, fe3fffff]
[    0.727460] bus: 02 index 2 mmio: [0, 0]
[    0.727462] bus: 02 index 3 io port: [0, ffff]
[    0.727464] bus: 02 index 4 mmio: [0, ffffffff]
[    0.727472] NET: Registered protocol family 2
[    0.740052] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.740299] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.740671] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.740870] TCP: Hash tables configured (established 131072 bind 65536)
[    0.740874] TCP reno registered
[    0.744077] NET: Registered protocol family 1
[    0.744192] checking if image is initramfs... it is
[    1.491769] Freeing initrd memory: 8011k freed
[    1.492133] Simple Boot Flag at 0x79 set to 0x1
[    1.492949] audit: initializing netlink socket (disabled)
[    1.492974] type=2000 audit(1233255257.492:1): initialized
[    1.499422] highmem bounce pool size: 64 pages
[    1.499428] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.501767] VFS: Disk quotas dquot_6.5.1
[    1.501853] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.501959] msgmni has been set to 1743
[    1.502083] io scheduler noop registered
[    1.502086] io scheduler anticipatory registered

...

---

### Post by Shmeegs2001 on 2009-01-29
It keeps giving me this message... You have included 11 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

Can I message you/ email you with the codes?

Thanks

Sam

---

### Post by HittingSmoke on 2009-01-29
> **Shmeegs2001 said:**
> It keeps giving me this message... You have included 11 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

Can I message you/ email you with the codes?

Thanks

Sam

There is a CODE tag box in the text controls at the top of the window (the one that has a # on it)

Highlight any file output and click this button

```
to make it show up in a nice easy to read box like this all in one post
```

Don't get discouraged. I was new to Ubuntu fresh from Windows a few months ago. Stick around here and learn how to search for Ubuntu problems on Google (which will usually point you back here also) and you will be running your dream system in no time.

---

### Post by bodhi.zazen on 2009-01-29
> **Shmeegs2001 said:**
> It keeps giving me this message... You have included 11 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

Can I message you/ email you with the codes?

Thanks

Sam

Dude ...  Attach the output on a text (.txt) file

---

### Post by Shmeegs2001 on 2009-01-29
Think that's attached them all!

Cheers

Sam

---

### Post by Shmeegs2001 on 2009-01-29
dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Wed Jan 28 00:02:01 UTC 2009 (Ubuntu 2.6.27-11.26-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f66d800 (usable)
[    0.000000]  BIOS-e820: 000000007f66d800 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x7f66d max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3781d000 - 37fefc9b
[    0.000000] ACPI: RSDP 000FBC60, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 7F66F200, 0064 (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: FACP 7F66F09C, 00F4 (r4 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: DSDT 7F66F800, 5495 (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 7F67E000, 0040
[    0.000000] ACPI: HPET 7F66F300, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC 7F66F400, 0068 (r1 DELL    M08     27D8030A ASL        47)
[    0.000000] ACPI: MCFG 7F66F3C0, 003E (r16 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: SLIC 7F66F49C, 0024 (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: OSFR 7F66EA00, 002C (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: BOOT 7F66EFC0, 0028 (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: SSDT 7F66DA44, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003781d000 - 0037fefc9b]          RAMDISK ==> [003781d000 - 0037fefc9b]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007f66d
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f66d
[    0.000000] On node 0 totalpages: 521740
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 289890 pages, LIFO batch:31

[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:78000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517153
[    0.000000] Kernel command line: root=UUID=300afdd1-2cd1-4e19-9934-50c8265e411a ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1828.720 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2053868k/2087348k available (2576k kernel code, 32208k reserved, 1165k data, 424k init, 1169844k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3657.44 BogoMIPS (lpj=7314880)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017985] ACPI: Core revision 20080609
[    0.019900] ACPI: Checking initramfs for custom DSDT
[    0.388270] ENABLING IO-APIC IRQs
[    0.388465] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.428296] CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.432027] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3657.42 BogoMIPS (lpj=7314853)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.516499] CPU1: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.516517] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.520049] Brought up 2 CPUs
[    0.520052] Total of 2 processors activated (7314.86 BogoMIPS).
[    0.520074] CPU0 attaching sched-domain:
[    0.520077]  domain 0: span 0-1 level MC
[    0.520080]   groups: 0 1
[    0.520087] CPU1 attaching sched-domain:
[    0.520089]  domain 0: span 0-1 level MC
[    0.520092]   groups: 1 0
[    0.520171] net_namespace: 840 bytes
[    0.520171] Booting paravirtualized kernel on bare hardware
[    0.520319] Time: 18:54:17  Date: 01/29/09
[    0.520346] NET: Registered protocol family 16
[    0.520365] EISA bus registered
[    0.520365] ACPI: bus type pci registered
[    0.520365] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.520365] PCI: MCFG area at f8000000 reserved in E820
[    0.520365] PCI: Using MMCONFIG for extended config space
[    0.520365] PCI: Using configuration type 1 for base access
[    0.521057] ACPI: EC: Look up EC in DSDT
[    0.521291] ACPI: BIOS _OSI(Linux) query ignored
[    0.521293] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
[    0.553424] ACPI: Interpreter enabled
[    0.553429] ACPI: (supports S0 S3 S4 S5)
[    0.553444] ACPI: Using IOAPIC for interrupt routing
[    0.604179] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.604179] PCI: 0000:00:02.0 reg 10 64bit mmio: [fea00000, feafffff]
[    0.604179] PCI: 0000:00:02.0 reg 18 64bit mmio: [e0000000, efffffff]
[    0.604179] PCI: 0000:00:02.0 reg 20 io port: [eff8, efff]
[    0.604179] PCI: 0000:00:02.1 reg 10 64bit mmio: [feb00000, febfffff]
[    0.604287] PCI: 0000:00:1a.0 reg 20 io port: [6f20, 6f3f]
[    0.604358] PCI: 0000:00:1a.1 reg 20 io port: [6f00, 6f1f]
[    0.604436] PCI: 0000:00:1a.7 reg 10 32bit mmio: [fed1c400, fed1c7ff]
[    0.604500] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.604507] pci 0000:00:1a.7: PME# disabled
[    0.604560] PCI: 0000:00:1b.0 reg 10 64bit mmio: [fe9fc000, fe9fffff]
[    0.604619] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.604625] pci 0000:00:1b.0: PME# disabled
[    0.604704] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.604709] pci 0000:00:1c.0: PME# disabled
[    0.604790] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.604796] pci 0000:00:1c.1: PME# disabled
[    0.604879] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.604885] pci 0000:00:1c.4: PME# disabled
[    0.604940] PCI: 0000:00:1d.0 reg 20 io port: [6f80, 6f9f]
[    0.605010] PCI: 0000:00:1d.1 reg 20 io port: [6f60, 6f7f]
[    0.605081] PCI: 0000:00:1d.2 reg 20 io port: [6f40, 6f5f]
[    0.605158] PCI: 0000:00:1d.7 reg 10 32bit mmio: [fed1c000, fed1c3ff]
[    0.605221] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.605228] pci 0000:00:1d.7: PME# disabled
[    0.605403] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.605408] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.605441] PCI: 0000:00:1f.1 reg 10 io port: [1f0, 1f7]
[    0.605450] PCI: 0000:00:1f.1 reg 14 io port: [3f4, 3f7]
[    0.605459] PCI: 0000:00:1f.1 reg 18 io port: [170, 177]
[    0.605468] PCI: 0000:00:1f.1 reg 1c io port: [374, 377]
[    0.605477] PCI: 0000:00:1f.1 reg 20 io port: [6fa0, 6faf]
[    0.605559] PCI: 0000:00:1f.2 reg 10 io port: [6eb0, 6eb7]
[    0.605568] PCI: 0000:00:1f.2 reg 14 io port: [6eb8, 6ebb]
[    0.605577] PCI: 0000:00:1f.2 reg 18 io port: [6ec0, 6ec7]
[    0.605586] PCI: 0000:00:1f.2 reg 1c io port: [6ec8, 6ecb]
[    0.605595] PCI: 0000:00:1f.2 reg 20 io port: [6ee0, 6eff]
[    0.605604] PCI: 0000:00:1f.2 reg 24 32bit mmio: [fe9fb800, fe9fbfff]
[    0.605641] pci 0000:00:1f.2: PME# supported from D3hot
[    0.605646] pci 0000:00:1f.2: PME# disabled
[    0.605669] PCI: 0000:00:1f.3 reg 10 32bit mmio: [fe9fb700, fe9fb7ff]
[    0.605699] PCI: 0000:00:1f.3 reg 20 io port: [10c0, 10df]
[    0.605811] PCI: 0000:09:00.0 reg 10 64bit mmio: [fe8fc000, fe8fffff]
[    0.605823] PCI: 0000:09:00.0 reg 18 io port: [de00, deff]
[    0.605902] pci 0000:09:00.0: supports D1
[    0.605904] pci 0000:09:00.0: supports D2
[    0.605906] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.605914] pci 0000:09:00.0: PME# disabled
[    0.605973] PCI: bridge 0000:00:1c.0 io port: [d000, dfff]
[    0.605979] PCI: bridge 0000:00:1c.0 32bit mmio: [fe800000, fe8fffff]
[    0.606175] PCI: 0000:0b:00.0 reg 10 32bit mmio: [fe7ff000, fe7fffff]
[    0.606390] pci 0000:0b:00.0: PME# supported from D0 D3hot D3cold
[    0.606404] pci 0000:0b:00.0: PME# disabled
[    0.606466] PCI: bridge 0000:00:1c.1 32bit mmio: [fe700000, fe7fffff]
[    0.606541] PCI: bridge 0000:00:1c.4 io port: [c000, cfff]
[    0.606547] PCI: bridge 0000:00:1c.4 32bit mmio: [fe400000, fe6fffff]
[    0.606556] PCI: bridge 0000:00:1c.4 64bit mmio pref: [f0000000, f01fffff]
[    0.606624] PCI: 0000:02:09.0 reg 10 32bit mmio: [fe3ff800, fe3fffff]
[    0.606686] pci 0000:02:09.0: supports D1
[    0.606688] pci 0000:02:09.0: supports D2
[    0.606690] pci 0000:02:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.606695] pci 0000:02:09.0: PME# disabled
[    0.606737] PCI: 0000:02:09.1 reg 10 32bit mmio: [fe3ff500, fe3ff5ff]
[    0.606798] pci 0000:02:09.1: supports D1
[    0.606799] pci 0000:02:09.1: supports D2
[    0.606802] pci 0000:02:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.606807] pci 0000:02:09.1: PME# disabled
[    0.606850] PCI: 0000:02:09.2 reg 10 32bit mmio: [fe3ff600, fe3ff6ff]
[    0.606912] pci 0000:02:09.2: supports D1
[    0.606914] pci 0000:02:09.2: supports D2
[    0.606916] pci 0000:02:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.606922] pci 0000:02:09.2: PME# disabled
[    0.606964] PCI: 0000:02:09.3 reg 10 32bit mmio: [fe3ff700, fe3ff7ff]
[    0.607027] pci 0000:02:09.3: supports D1
[    0.607028] pci 0000:02:09.3: supports D2
[    0.607031] pci 0000:02:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.607036] pci 0000:02:09.3: PME# disabled
[    0.607093] pci 0000:00:1e.0: transparent bridge
[    0.607102] PCI: bridge 0000:00:1e.0 32bit mmio: [fe300000, fe3fffff]
[    0.607140] bus 00 -> node 0
[    0.607147] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.608290] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.608493] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.608661] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.608824] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.624187] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.624350] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.624511] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
[    0.624656] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
[    0.624821] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.624985] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.625149] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.625299] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.625388] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.625388] pnp: PnP ACPI init
[    0.625388] ACPI: bus type pnp registered
[    0.649919] pnp 00:0a: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.649919] pnp 00:0a: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.649919] pnp 00:0b: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.649919] pnp 00:0b: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.649919] pnp 00:0b: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.649919] pnp 00:0b: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.679522] pnp: PnP ACPI: found 13 devices
[    0.679522] ACPI: ACPI bus type pnp unregistered
[    0.679522] PnPBIOS: Disabled by ACPI PNP
[    0.680055] PCI: Using ACPI for IRQ routing
[    0.684041] NET: Registered protocol family 8
[    0.684044] NET: Registered protocol family 20
[    0.684061] NetLabel: Initializing
[    0.684061] NetLabel:  domain hash size = 128
[    0.684061] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.684068] NetLabel:  unlabeled traffic allowed by default
[    0.684077] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.684082] hpet0: 3 64-bit timers, 14318180 Hz
[    0.685604] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.685607]    actual entries 65620
[    0.685701] AppArmor: AppArmor Filesystem Enabled
[    0.685729] ACPI: RTC can wake from S4
[    0.688039] Switched to high resolution mode on CPU 0
[    0.688536] Switched to high resolution mode on CPU 1
[    0.692023] system 00:01: iomem range 0xff800000-0xff8fffff has been reserved
[    0.692027] system 00:01: iomem range 0xffc00000-0xffcfffff has been reserved
[    0.692037] system 00:06: ioport range 0xc80-0xcff could not be reserved
[    0.692046] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.692052] system 00:0a: ioport range 0x900-0x97f has been reserved
[    0.692055] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.692069] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
[    0.692072] system 00:0b: ioport range 0x1080-0x10bf has been reserved
[    0.692076] system 00:0b: ioport range 0x10c0-0x10df has been reserved
[    0.692079] system 00:0b: ioport range 0x809-0x809 has been reserved
[    0.692086] system 00:0c: iomem range 0x0-0x9efff could not be reserved
[    0.692089] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
[    0.692092] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.692096] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.692099] system 00:0c: iomem range 0x100000-0x7f66d7ff could not be reserved
[    0.692102] system 00:0c: iomem range 0x7f66d800-0x7f6fffff could not be reserved
[    0.692106] system 00:0c: iomem range 0x7f700000-0x7f7fffff could not be reserved
[    0.692109] system 00:0c: iomem range 0x7f700000-0x7fefffff could not be reserved
[    0.692113] system 00:0c: iomem range 0xffe00000-0xffffffff could not be reserved
[    0.692116] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.692119] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.692123] system 00:0c: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    0.692126] system 00:0c: iomem range 0xfed20000-0xfed8ffff could not be reserved
[    0.692130] system 00:0c: iomem range 0xfeda0000-0xfeda3fff could not be reserved
[    0.692133] system 00:0c: iomem range 0xfeda4000-0xfeda4fff could not be reserved
[    0.692136] system 00:0c: iomem range 0xfeda5000-0xfeda5fff could not be reserved
[    0.692140] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.692143] system 00:0c: iomem range 0xfed18000-0xfed1bfff could not be reserved
[    0.692147] system 00:0c: iomem range 0xf8000000-0xfbffffff could not be reserved
[    0.727258] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:09
[    0.727263] pci 0000:00:1c.0:   IO window: 0xd000-0xdfff
[    0.727270] pci 0000:00:1c.0:   MEM window: 0xfe800000-0xfe8fffff
[    0.727276] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.727285] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0b
[    0.727287] pci 0000:00:1c.1:   IO window: disabled
[    0.727294] pci 0000:00:1c.1:   MEM window: 0xfe700000-0xfe7fffff
[    0.727300] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.727309] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0c
[    0.727313] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
[    0.727320] pci 0000:00:1c.4:   MEM window: 0xfe400000-0xfe6fffff
[    0.727326] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.727335] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.727338] pci 0000:00:1e.0:   IO window: disabled
[    0.727345] pci 0000:00:1e.0:   MEM window: 0xfe300000-0xfe3fffff
[    0.727350] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.727370] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.727377] pci 0000:00:1c.0: setting latency timer to 64
[    0.727388] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.727394] pci 0000:00:1c.1: setting latency timer to 64
[    0.727404] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.727410] pci 0000:00:1c.4: setting latency timer to 64
[    0.727419] pci 0000:00:1e.0: setting latency timer to 64
[    0.727424] bus: 00 index 0 io port: [0, ffff]
[    0.727426] bus: 00 index 1 mmio: [0, ffffffff]
[    0.727429] bus: 09 index 0 io port: [d000, dfff]
[    0.727431] bus: 09 index 1 mmio: [fe800000, fe8fffff]
[    0.727434] bus: 09 index 2 mmio: [0, 0]
[    0.727436] bus: 09 index 3 mmio: [0, 0]
[    0.727438] bus: 0b index 0 mmio: [0, 0]
[    0.727440] bus: 0b index 1 mmio: [fe700000, fe7fffff]
[    0.727442] bus: 0b index 2 mmio: [0, 0]
[    0.727444] bus: 0b index 3 mmio: [0, 0]
[    0.727446] bus: 0c index 0 io port: [c000, cfff]
[    0.727449] bus: 0c index 1 mmio: [fe400000, fe6fffff]
[    0.727451] bus: 0c index 2 mmio: [f0000000, f01fffff]
[    0.727453] bus: 0c index 3 mmio: [0, 0]
[    0.727455] bus: 02 index 0 mmio: [0, 0]
[    0.727457] bus: 02 index 1 mmio: [fe300000, fe3fffff]
[    0.727460] bus: 02 index 2 mmio: [0, 0]
[    0.727462] bus: 02 index 3 io port: [0, ffff]
[    0.727464] bus: 02 index 4 mmio: [0, ffffffff]
[    0.727472] NET: Registered protocol family 2
[    0.740052] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.740299] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.740671] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.740870] TCP: Hash tables configured (established 131072 bind 65536)
[    0.740874] TCP reno registered
[    0.744077] NET: Registered protocol family 1
[    0.744192] checking if image is initramfs... it is
[    1.491769] Freeing initrd memory: 8011k freed
[    1.492133] Simple Boot Flag at 0x79 set to 0x1
[    1.492949] audit: initializing netlink socket (disabled)
[    1.492974] type=2000 audit(1233255257.492:1): initialized
[    1.499422] highmem bounce pool size: 64 pages
[    1.499428] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.501767] VFS: Disk quotas dquot_6.5.1
[    1.501853] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.501959] msgmni has been set to 1743
[    1.502083] io scheduler noop registered
[    1.502086] io scheduler anticipatory registered
[    1.502089] io scheduler deadline registered
[    1.502102] io scheduler cfq registered (default)
[    1.502116] pci 0000:00:02.0: Boot video device
[    1.502394] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.502451] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.502507] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.502551] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.502592] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.502712] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.502767] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.502820] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.502862] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.502905] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.503024] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.503079] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.503132] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.503174] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.503214] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.503575] isapnp: Scanning for PnP cards...
[    1.857596] isapnp: No Plug & Play device found
[    1.891091] hpet_resources: 0xfed00000 is busy
[    1.891201] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.893437] brd: module loaded
[    1.893509] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.893640] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.909966] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.922317] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.922322] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.922325] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.922328] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.922331] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.924110] mice: PS/2 mouse device common for all mice
[    1.924235] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.924268] rtc0: alarms up to one month, y3k, hpet irqs
[    1.924399] EISA: Probing bus 0 at eisa.0
[    1.924407] Cannot allocate resource for EISA slot 1
[    1.924441] EISA: Detected 0 cards.
[    1.924444] cpuidle: using governor ladder
[    1.924447] cpuidle: using governor menu
[    1.924988] TCP cubic registered
[    1.925015] Using IPI No-Shortcut mode
[    1.925188] registered taskstats version 1
[    1.925328]   Magic number: 9:947:949
[    1.925340] tty ttya4: hash matches
[    1.925396] tty tty6: hash matches
[    1.925448] rtc_cmos 00:04: setting system clock to 2009-01-29 18:54:18 UTC (1233255258)
[    1.925452] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.925454] EDD information not available.
[    1.925697] Freeing unused kernel memory: 424k freed
[    1.925737] Write protecting the kernel text: 2580k
[    1.925765] Write protecting the kernel read-only data: 940k
[    1.948017] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.161071] fuse init (API version 7.9)
[    2.200525] ACPI: SSDT 7F66E57A, 0202 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    2.200942] ACPI: SSDT 7F66DF10, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    2.201381] Monitor-Mwait will be used to enter C-1 state
[    2.201384] Monitor-Mwait will be used to enter C-2 state
[    2.201387] Monitor-Mwait will be used to enter C-3 state
[    2.201575] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.201633] processor ACPI0007:00: registered as cooling_device0
[    2.201637] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.201997] ACPI: SSDT 7F66E77C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    2.202369] ACPI: SSDT 7F66E4F5, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    2.205224] Marking TSC unstable due to TSC halts in idle
[    2.205397] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.205446] processor ACPI0007:01: registered as cooling_device1
[    2.205450] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.208270] thermal LNXTHERM:01: registered as thermal_zone0
[    2.208528] ACPI: Thermal Zone [THM] (54 C)
[    2.344630] usbcore: registered new interface driver usbfs
[    2.344655] usbcore: registered new interface driver hub
[    2.352898] usbcore: registered new device driver usb
[    2.360112] USB Universal Host Controller Interface driver v3.0
[    2.360164] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.360174] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.360179] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.360227] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.360268] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    2.360417] usb usb1: configuration #1 chosen from 1 choice
[    2.360446] hub 1-0:1.0: USB hub found
[    2.360454] hub 1-0:1.0: 2 ports detected
[    2.464308] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.464324] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.464331] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.464359] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.464416] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    2.464522] usb usb2: configuration #1 chosen from 1 choice
[    2.464550] hub 2-0:1.0: USB hub found
[    2.464558] hub 2-0:1.0: 2 ports detected
[    2.568259] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.568275] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.568283] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.568308] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    2.568354] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    2.568461] usb usb3: configuration #1 chosen from 1 choice
[    2.568490] hub 3-0:1.0: USB hub found
[    2.568497] hub 3-0:1.0: 2 ports detected
[    2.568620] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.648913] No dock devices found.
[    2.672253] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.672264] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.672269] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.672296] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    2.672329] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    2.672432] usb usb4: configuration #1 chosen from 1 choice
[    2.672462] hub 4-0:1.0: USB hub found
[    2.672468] hub 4-0:1.0: 2 ports detected
[    2.674955] SCSI subsystem initialized
[    2.692927] libata version 3.00 loaded.
[    2.776364] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.776376] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.776381] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.776410] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    2.776450] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    2.776547] usb usb5: configuration #1 chosen from 1 choice
[    2.776578] hub 5-0:1.0: USB hub found
[    2.776585] hub 5-0:1.0: 2 ports detected
[    2.880394] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.880415] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.880419] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.880449] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    2.884362] ehci_hcd 0000:00:1a.7: debug port 1
[    2.884371] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.884379] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    2.900023] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.900168] usb usb6: configuration #1 chosen from 1 choice
[    2.900198] hub 6-0:1.0: USB hub found
[    2.900207] hub 6-0:1.0: 4 ports detected
[    3.004883] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.004900] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.004905] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.004938] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    3.008831] ehci_hcd 0000:00:1d.7: debug port 1
[    3.008839] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.008848] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    3.025024] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.025187] usb usb7: configuration #1 chosen from 1 choice
[    3.025218] hub 7-0:1.0: USB hub found
[    3.025225] hub 7-0:1.0: 6 ports detected
[    3.128622] sky2 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.128637] sky2 0000:09:00.0: setting latency timer to 64
[    3.128667] sky2 0000:09:00.0: v1.22 addr 0xfe8fc000 irq 16 Yukon-2 FE+ rev 0
[    3.128851] ahci 0000:00:1f.2: version 3.0
[    3.128864] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.128972] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    3.128975] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    3.128982] ahci 0000:00:1f.2: setting latency timer to 64
[    3.129171] scsi0 : ahci
[    3.129487] sky2 eth0: addr 00:21:9b:ce:19:86
[    3.130211] scsi1 : ahci
[    3.130300] scsi2 : ahci
[    3.130634] ata1: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fb900 irq 219
[    3.130637] ata2: DUMMY
[    3.130640] ata3: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fba00 irq 219
[    3.448257] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.493877] ata1.00: ATA-8: WDC WD1600BEVT-75ZCT0, 11.01A11, max UDMA/133
[    3.493883] ata1.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    3.494874] ata1.00: configured for UDMA/133
[    3.500061] Clocksource tsc unstable (delta = -310558670 ns)
[    3.828274] ata3: SATA link down (SStatus 0 SControl 300)
[    3.845424] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-7 11.0 PQ: 0 ANSI: 5
[    3.848704] ohci1394 0000:02:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.901436] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fe3ff800-fe3fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.907178] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.907217] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    3.907232] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    3.913908] ata_piix 0000:00:1f.1: version 2.12
[    3.913924] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.913975] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.915725] scsi3 : ata_piix
[    3.917509] scsi4 : ata_piix
[    3.918374] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    3.918378] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    3.919077] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    3.931173] Driver 'sd' needs updating - please use bus_type methods
[    3.931277] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    3.931295] sd 0:0:0:0: [sda] Write Protect is off
[    3.931298] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.931326] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.931396] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    3.931412] sd 0:0:0:0: [sda] Write Protect is off
[    3.931415] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.931443] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.931446]  sda: sda1 sda2 < sda5 >
[    4.008948] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.080816] ata4.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T21N, A102, max UDMA/33
[    4.096683] ata4.00: configured for UDMA/33
[    4.096762] ata5: port disabled. ignoring.
[    4.100552] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T21N A102 PQ: 0 ANSI: 5
[    4.100764] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[    4.117356] Driver 'sr' needs updating - please use bus_type methods
[    4.128459] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.128467] Uniform CD-ROM driver Revision: 3.20
[    4.128627] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    4.265916] PM: Starting manual resume from disk
[    4.265920] PM: Resume from partition 8:5
[    4.265921] PM: Checking hibernation image.
[    4.266108] PM: Resume from disk failed.
[    4.340512] kjournald starting.  Commit interval 5 seconds
[    4.340557] EXT3-fs: mounted filesystem with ordered data mode.
[    5.176516] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[354fc000128be070]
[   10.193988] udevd version 124 started
[   10.470554] Linux agpgart interface v0.103
[   10.557184] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   10.557721] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   10.570725] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   10.631660] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   10.673179] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.786479] ACPI: Battery Slot [BAT0] (battery present)
[   10.829979] ACPI: AC Adapter [AC] (on-line)
[   10.870248] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[   10.870982] ACPI: Lid Switch [LID]
[   10.871037] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   10.888050] ACPI: Power Button (CM) [PBTN]
[   10.888133] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   10.920023] ACPI: Sleep Button (CM) [SBTN]
[   10.936765] ACPI: WMI: Mapper loaded
[   11.161153] acpi device:31: registered as cooling_device2
[   11.161591] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/input/input5
[   11.184043] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   11.184244] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:33/input/input6
[   11.215549] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   11.616079] iTCO_vendor_support: vendor-support=0
[   11.789176] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   11.836097] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.836125] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.836784] sdhci: Secure Digital Host Controller Interface driver
[   11.836788] sdhci: Copyright(c) Pierre Ossman
[   11.864209] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   12.099236] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   12.099240] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   12.281135] sdhci-pci 0000:02:09.1: SDHCI controller found [1180:0822] (rev 22)
[   12.281211] iwl3945 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.281215] sdhci-pci 0000:02:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   12.281231] iwl3945 0000:0b:00.0: setting latency timer to 64
[   12.281251] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   12.284282] mmc0: SDHCI controller on PCI [0000:02:09.1] using DMA
[   12.346113] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   12.346634] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   12.358426] input: PS/2 Mouse as /devices/platform/i8042/serio2/input/input8
[   12.433170] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input9
[   12.455797] iwl3945 0000:0b:00.0: PCI INT A disabled
[   12.473108] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   12.473197] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.535336] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   14.190194] lp: driver loaded but no devices found
[   14.361973] Adding 6040400k swap on /dev/sda5.  Priority:-1 extents:1 across:6040400k
[   14.903637] EXT3 FS on sda1, internal journal
[   15.931190] type=1505 audit(1233255272.916:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4211
[   16.108834] type=1505 audit(1233255273.096:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4216
[   16.109067] type=1505 audit(1233255273.096:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4216
[   16.255041] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.960074] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   18.009866] apm: BIOS not found.
[   18.175444] ppdev: user-space parallel port driver
[   19.829974] Bluetooth: Core ver 2.13
[   19.830241] NET: Registered protocol family 31
[   19.830248] Bluetooth: HCI device and connection manager initialized
[   19.830253] Bluetooth: HCI socket layer initialized
[   19.850047] Bluetooth: L2CAP ver 2.11
[   19.850057] Bluetooth: L2CAP socket layer initialized
[   19.867059] Bluetooth: SCO (Voice Link) ver 0.6
[   19.867071] Bluetooth: SCO socket layer initialized
[   19.880667] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.880678] Bluetooth: BNEP filters: protocol multicast
[   19.911219] Bridge firewalling registered
[   20.051022] Bluetooth: RFCOMM socket layer initialized
[   20.051041] Bluetooth: RFCOMM TTY layer initialized
[   20.051045] Bluetooth: RFCOMM ver 1.10
[   24.192355] sky2 eth0: enabling interface
[   24.225310] iwl3945 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.225466] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   24.233167] firmware: requesting iwlwifi-3945-1.ucode
[   24.301990] iwl3945: Radio disabled by HW RF Kill switch
[   24.302213] iwl3945 0000:0b:00.0: PCI INT A disabled
[   24.897178] [drm] Initialized drm 1.1.0 20060810
[   24.915442] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   24.915456] pci 0000:00:02.0: setting latency timer to 64
[   24.916809] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   25.765560] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   25.845895] NET: Registered protocol family 17
[   34.453132] NET: Registered protocol family 10
[   34.454688] lo: Disabled Privacy Extensions
[   45.440316] eth0: no IPv6 routers present
[  221.558463] CPU0 attaching NULL sched-domain.
[  221.558484] CPU1 attaching NULL sched-domain.
[  221.559070] CPU0 attaching sched-domain:
[  221.559078]  domain 0: span 0-1 level MC
[  221.559083]   groups: 0 1
[  221.559095] CPU1 attaching sched-domain:
[  221.559099]  domain 0: span 0-1 level MC
[  221.559104]   groups: 1 0
[ 1895.141039] CE: hpet increasing min_delta_ns to 15000 nsec
```


lspci
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

lshw
```
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:ce:19:86
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.64 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:8d:15:86
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3a:ea:5c:15:53:b8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by stchman on 2009-01-29
> **Shmeegs2001 said:**
> Hi everyone!

I'm really losing the will with Ubuntu and I am getting seriously tempted to take my laptop to the shop and get Windows installed.  My friend is convinced that Ubuntu is better than Windows for countless reasons, but I am having so many problems with it and I have no idea how to fix them, so I'm just not sure!  If anyone can help, please do!

Problem 1 - After installing Ubuntu 8.10 my wireless stopped working.  The box for 'Enable Wireless' is there, but it is greyed out and I can't get it to work!!!

Problem 2 - I cannot stream anything at all on the internet.  I need to use Youtube, and Myspace for my work but all I get is a black box with nothing going on in it!

I have a pretty basic grasp of all of this!  hopefully someone can help!

Cheers

Sam

More detail like make/model of laptop would be nice.  Also post an lspci output in this thread.

---

### Post by Shmeegs2001 on 2009-01-29
Hi

It's a Dell inspiron 1525.

Here is the lspci code




```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

---

### Post by Lostin60's on 2009-01-30
> **Cosimix said:**
> OK First your friend is absolutely right about choosing Ubuntu. The more you use it the earlier you will understand why. 

**[COLOR="Red"]By the way, is the online support for Win as good as Ubuntu's??[/COLOR]   **


[SIZE="4"]HYSTERICALLY ROFL..GASP...LOL..WHEEZE..OH, IT HURTS..GRABS CHEST..[/SIZE]

Geeze, Cosimix, be careful what you post..you might hurt someone..lol.
[COLOR="White"][/COLOR]

---

### Post by wadeo on 2009-01-31
> **Shmeegs2001 said:**
> I'm sure I'll be back here for help again

lol, I'm on here daily for help and I've been running Ubuntu for over a year. Don't expect to learn everything there is to know about linux in a day ;)

good luck with any issues you may have and think of it as a puzzle for which you have the pieces, but have to figure out how they go together! That's what keeps me truckin along!

---

### Post by Cosimix on 2009-02-01
Hi guys,
I got someone who can understand me somewhere in the world[COLOR="DarkGreen"]*** Lostin60's***[/COLOR] 

Ive been a little bit busy... Thanks for sending info requested. 

[COLOR=Black][B]Let's solve the problem now... Now it comes the best part...
:)[/B][/COLOR]

_Good News_ your card is properly installed and functional and it's got a name **wlan0**...
_Bad News_ We need to check if its been configured properly and whether you [B]TURNED IT ON

[/B]In the meantime I have noticed you have become more familiar with the bash shell.

**1.** Turning on the card

On your laptop depending on the model there might be a wireless button or some special keystroke Fn+Fx to toggle wireless. The wireless radio also needs enabling from the BIOS. These are the first things to check. What's the wireless LED status??

Use these commands  in order to create an automatic configuration for your wireless card.

**2.** You need to edit the file /etc/network/interfaces

[B]sudo nano /etc/network/interfaces
[/B]**----------------------------**
[B]### make sure contains the following lines

[/B][I]auto lo
iface lo inet loopback

[/I]****[I]auto eth0 
iface eth0 inet dhcp
[/I][B][I]
auto wlan0
iface wlan0 inet dhcp

-----------------------------


3. [/I][/B]Now use the command **sudo /etc/init.d/networking restart **in order to let the system reload the configuration of the interfaces 

Use this command to turn on the wireless interface:

**sudo ifconfig wlan0 mtu 2200 up**

Use this command to scan for wireless access points:
[B]iwlist wlan0 scan

[/B]Use this command to connect to an ssid manually
**sudo iwconfig wlan0 essid **SSIDname **channel** <1-13> **power off** **rate** 54M

---

### Post by sanemanmad on 2009-02-01
It seems your wireless card is simply disabled... Do you have a hardware switch on this laptop.... or maybe a button combination to activate it? On my Dell I use ```
*fn + f2*
```

---

### Post by Stefanie on 2009-02-01
> **Cosimix said:**
> Use this command to connect to an ssid manually
**sudo iwconfig wlan0 essid **SSIDname **channel** <1-13> **power off** **rate** 54M

this last step shouldn't be necessary. after enabling your wireless card the "enable wireless" option shouldn't be greyed out anymore and you should be able to connect via the GUI.

---

### Post by minsf on 2009-02-01
> **Cosimix said:**
> 
**sudo ifconfig wlan0 mtu 2200 up**
**iwlist wlan0 scan**
**sudo iwconfig wlan0 essid **SSIDname **channel** <1-13> **power off** **rate** 54M
Thanks! This helped clarify some things about wireless connection from the command line.
in the last command, where does the wpa password go? how do i know the channel and the correct rate for my system?

---

### Post by Oliverkat on 2009-02-02
Many thanks Lostin60s. Followed your link to the great tutorial and now have a Flash player that works :D

---

### Post by Lostin60's on 2009-02-02
> **Oliverkat said:**
> Many thanks Lostin60s. Followed your link to the great tutorial and now have a Flash player that works :D

I'm glad I could help. I am a noob myself, and those 2 tuts really helped. It was nice to post an answer instead of a question...lol.
[COLOR="White"]aa[/COLOR]

---

