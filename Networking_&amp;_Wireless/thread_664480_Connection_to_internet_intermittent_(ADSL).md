---
title: "Connection to internet intermittent (ADSL)"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by Tapps on 2008-01-11
Hello everyone. I am still a newbe to the world of Linux so bear with me. 

I have been using the internet now for a couple of months on a Thomson Speedtouch 510 V6 ADSL modem. The system was working fine until late.

Now I am able to surf the net for about 30 mins to an hour and then the internet will shut off. I notice that when this happens both the Ethernet light on the modem and the back of the computer turn off. I have tried rebooting the modem, turning off the computer, unplugging the cables, and starting over a number of times but with no success. 

I have tried to look through the other forums but have not found anything that has helped. If I ping when the internet is down here is what I get: 

```
ryan@ryan-laptop:~$ ping -c 4 64.233.187.99 
PING 64.233.187.99 (64.233.187.99) 56(84) bytes of data. 
64 bytes from 64.233.187.99: icmp_seq=2 ttl=241 time=209 ms 
64 bytes from 64.233.187.99: icmp_seq=3 ttl=241 time=208 ms 
64 bytes from 64.233.187.99: icmp_seq=4 ttl=241 time=211 ms 

--- 64.233.187.99 ping statistics --- 
4 packets transmitted, 3 received, 25% packet loss, time 3009ms 
rtt min/avg/max/mdev = 208.101/209.692/211.256/1.288 ms 
ryan@ryan-laptop:~$ ping -c 4 google.com 
PING google.com (72.14.207.99) 56(84) bytes of data. 
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=1 ttl=242 time=210 ms 
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=2 ttl=242 time=213 ms 
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=3 ttl=242 time=211 ms 

--- google.com ping statistics --- 
4 packets transmitted, 3 received, 25% packet loss, time 3003ms 
rtt min/avg/max/mdev = 210.703/212.064/213.719/1.357 ms 
ryan@ryan-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03) 
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) 
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01) 
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) 
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1) 
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01) 
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02) 
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller 
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05) 
```
ryan@ryan-laptop:~$ lspci 
```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03) 
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) 
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01) 
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) 
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1) 
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01) 
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02) 
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller 
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05) 
ryan@ryan-laptop:~$  ping -c 4 xxx.xxx.1.1 
PING xxx.xxx.1.1 (xxx.xxx.1.1) 56(84) bytes of data. 

--- xxx.xxx.1.1 ping statistics --- 
4 packets transmitted, 0 received, 100% packet loss, time 6239ms 
```

Also in the system log right after the net has stopped working it states that the Serial link appears to be disconnected. 

Here is what I get from ifconfig:

```
ryan@ryan-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0F:1F:2B:08:64  
          inet6 addr: fe80::20f:1fff:fe2b:864/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:4234 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4021 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:4179295 (3.9 MiB)  TX bytes:654109 (638.7 KiB) 
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:79:80:E4  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:15337 errors:0 dropped:0 overruns:0 carrier:1 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:7 Memory:faffc000-faffcfff 

eth1:avah Link encap:Ethernet  HWaddr 00:0E:35:79:80:E4  
          inet addr:xxx.xxx.x.xx  Bcast:xxx.xxx.xxx.xxx  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:7 Memory:faffc000-faffcfff 

lo        Link encap:Local Loopback  
          inet addr:xxx.x.x.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2220 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2220 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:180096 (175.8 KiB)  TX bytes:180096 (175.8 KiB) 
```

And here is what I get when I do dmesg:

```
ryan@ryan-laptop:~$ dmesg 
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Dec 18 05:45:12 UTC 2007 (Ubuntu 2.6.20-16.33-generic) 
[    0.000000] BIOS-provided physical RAM map: 
[    0.000000] sanitize start 
[    0.000000] sanitize end 
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1 
[    0.000000] copy_e820_map() type is E820_RAM 
[    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2 
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001feae000 end: 000000001ffae000 type: 1 
[    0.000000] copy_e820_map() type is E820_RAM 
[    0.000000] copy_e820_map() start: 000000001ffae000 size: 0000000000052000 end: 0000000020000000 type: 2 
[    0.000000] copy_e820_map() start: 00000000feda0000 size: 0000000000060000 end: 00000000fee00000 type: 2 
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2 
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable) 
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved) 
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffae000 (usable) 
[    0.000000]  BIOS-e820: 000000001ffae000 - 0000000020000000 (reserved) 
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved) 
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved) 
[    0.000000] 0MB HIGHMEM available. 
[    0.000000] 511MB LOWMEM available. 
[    0.000000] Entering add_active_range(0, 0, 130990) 0 entries of 256 used 
[    0.000000] Zone PFN ranges: 
[    0.000000]   DMA             0 ->     4096 
[    0.000000]   Normal       4096 ->   130990 
[    0.000000]   HighMem    130990 ->   130990 
[    0.000000] early_node_map[1] active PFN ranges 
[    0.000000]     0:        0 ->   130990 
[    0.000000] On node 0 totalpages: 130990 
[    0.000000]   DMA zone: 32 pages used for memmap 
[    0.000000]   DMA zone: 0 pages reserved 
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0 
[    0.000000]   Normal zone: 991 pages used for memmap 
[    0.000000]   Normal zone: 125903 pages, LIFO batch:31 
[    0.000000]   HighMem zone: 0 pages used for memmap 
[    0.000000] DMI 2.3 present. 
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fdf00 
[    0.000000] ACPI: RSDT (v001 DELL    CPi R   0x27d40a19 ASL  0x00000061) @ 0x1fff0000 
[    0.000000] ACPI: FADT (v001 DELL    CPi R   0x27d40a19 ASL  0x00000061) @ 0x1fff0400 
[    0.000000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000 
[    0.000000] ACPI: PM-Timer IO Port: 0x808 
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:deda0000) 
[    0.000000] Detected 1594.881 MHz processor. 
[    7.570892] Built 1 zonelists.  Total pages: 129967 
[    7.570897] Kernel command line: root=UUID=e1452ec3-a06b-49d3-9aa0-51a204d096d7 ro quiet splash 
[    7.571073] Local APIC disabled by BIOS -- you can enable it with "lapic" 
[    7.571084] mapped APIC to ffffd000 (0140b000) 
[    7.571088] Enabling fast FPU save and restore... done. 
[    7.571091] Enabling unmasked SIMD FPU exception support... done. 
[    7.571103] Initializing CPU#0 
[    7.571173] PID hash table entries: 2048 (order: 11, 8192 bytes) 
[    7.572920] Console: colour VGA+ 80x25 
[    7.573223] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes) 
[    7.573525] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes) 
[    7.587326] Memory: 508344k/523960k available (1993k kernel code, 14988k reserved, 900k data, 328k init, 0k highmem) 
[    7.587336] virtual kernel memory layout: 
[    7.587338]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB) 
[    7.587339]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
[    7.587340]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB) 
[    7.587342]     lowmem  : 0xc0000000 - 0xdffae000   ( 511 MB) 
[    7.587343]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB) 
[    7.587344]       .data : 0xc02f2429 - 0xc03d36d4   ( 900 kB) 
[    7.587346]       .text : 0xc0100000 - 0xc02f2429   (1993 kB) 
[    7.587349] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
[    7.667172] Calibrating delay using timer specific routine.. 3191.90 BogoMIPS (lpj=6383802) 
[    7.667214] Security Framework v1.0.0 initialized 
[    7.667224] SELinux:  Disabled at boot. 
[    7.667241] Mount-cache hash table entries: 512 
[    7.667384] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000 
[    7.667397] CPU: L1 I cache: 32K, L1 D cache: 32K 
[    7.667400] CPU: L2 cache: 2048K 
[    7.667403] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000 
[    7.667412] Compat vDSO mapped to ffffe000. 
[    7.667417] Remapping vsyscall page to ffffe000 
[    7.667428] Checking 'hlt' instruction... OK. 
[    7.683271] SMP alternatives: switching to UP code 
[    7.683474] Freeing SMP alternatives: 11k freed 
[    7.683657] Early unpacking initramfs... done 
[    8.031457] ACPI: Core revision 20060707 
[    8.038043] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT. 
[    8.039433] ACPI: setting ELCR to 0200 (from 0800) 
[    8.041656] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 06 
[    8.041662] SMP motherboard not detected. 
[    8.041665] Local APIC not detected. Using dummy APIC emulation. 
[    8.041698] Brought up 1 CPUs 
[    8.041947] Booting paravirtualized kernel on bare hardware 
[    8.042004] Time:  6:09:12  Date: 00/11/108 
[    8.042034] NET: Registered protocol family 16 
[    8.042113] EISA bus registered 
[    8.042118] ACPI: bus type pci registered 
[    8.075748] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2 
[    8.075750] PCI: Using configuration type 1 
[    8.075752] Setting up standard PCI resources 
[    8.086938] ACPI: Interpreter enabled 
[    8.086941] ACPI: Using PIC for interrupt routing 
[    8.088239] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[    8.088248] PCI: Probing PCI hardware (bus 00) 
[    8.088369] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0 
[    8.093673] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO 
[    8.093678] PCI quirk: region 0880-08bf claimed by ICH4 GPIO 
[    8.093879] Boot video device is 0000:01:00.0 
[    8.094129] PCI: Transparent bridge - 0000:00:1e.0 
[    8.094179] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses') 
[    8.094182] Please report the result to linux-kernel to fix this permanently 
[    8.094199] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[    8.114375] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11) 
[    8.114624] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11 
[    8.114873] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11) 
[    8.115122] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11) 
[    8.115363] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
[    8.115614] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
[    8.116877] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT] 
[    8.117622] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT] 
[    8.118550] Linux Plug and Play Support v0.97 (c) Adam Belay 
[    8.118562] pnp: PnP ACPI init 
[    8.134580] pnp: PnP ACPI: found 11 devices 
[    8.134586] PnPBIOS: Disabled by ACPI PNP 
[    8.134620] PCI: Using ACPI for IRQ routing 
[    8.134623] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
[    8.141270] NET: Registered protocol family 8 
[    8.141272] NET: Registered protocol family 20 
[    8.146376] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved 
[    8.146380] pnp: 00:02: ioport range 0x800-0x805 could not be reserved 
[    8.146383] pnp: 00:02: ioport range 0x808-0x80f could not be reserved 
[    8.146388] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved 
[    8.146391] pnp: 00:03: ioport range 0x806-0x807 has been reserved 
[    8.146394] pnp: 00:03: ioport range 0x810-0x85f could not be reserved 
[    8.146397] pnp: 00:03: ioport range 0x860-0x87f has been reserved 
[    8.146400] pnp: 00:03: ioport range 0x880-0x8bf has been reserved 
[    8.146402] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved 
[    8.146409] pnp: 00:08: ioport range 0x900-0x97f has been reserved 
[    8.146659] PCI: Bridge: 0000:00:01.0 
[    8.146662]   IO window: c000-cfff 
[    8.146665]   MEM window: fc000000-fdffffff 
[    8.146669]   PREFETCH window: d0000000-dfffffff 
[    8.146677] PCI: Bus 3, cardbus bridge: 0000:02:01.0 
[    8.146680]   IO window: 0000d000-0000d0ff 
[    8.146684]   IO window: 0000d400-0000d4ff 
[    8.146688]   PREFETCH window: 30000000-33ffffff 
[    8.146692]   MEM window: 38000000-3bffffff 
[    8.146696] PCI: Bridge: 0000:00:1e.0 
[    8.146699]   IO window: d000-efff 
[    8.146704]   MEM window: f6000000-fbffffff 
[    8.146708]   PREFETCH window: 30000000-33ffffff 
[    8.146723] PCI: Setting latency timer of device 0000:00:1e.0 to 64 
[    8.146735] PCI: Enabling device 0000:02:01.0 (0000 -> 0003) 
[    8.146914] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11 
[    8.146917] PCI: setting IRQ 11 as level-triggered 
[    8.146921] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11 
[    8.146944] NET: Registered protocol family 2 
[    8.179196] IP route cache hash table entries: 4096 (order: 2, 16384 bytes) 
[    8.179270] TCP established hash table entries: 16384 (order: 5, 131072 bytes) 
[    8.179378] TCP bind hash table entries: 8192 (order: 4, 65536 bytes) 
[    8.179437] TCP: Hash tables configured (established 16384 bind 8192) 
[    8.179440] TCP reno registered 
[    8.191246] checking if image is initramfs... it is 
[    8.881607] Freeing initrd memory: 6787k freed 
[    8.882060] audit: initializing netlink socket (disabled) 
[    8.882078] audit(1200031753.492:1): initialized 
[    8.882215] VFS: Disk quotas dquot_6.5.1 
[    8.882237] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[    8.882291] io scheduler noop registered 
[    8.882294] io scheduler anticipatory registered 
[    8.882296] io scheduler deadline registered 
[    8.882307] io scheduler cfq registered (default) 
[    8.882617] isapnp: Scanning for PnP cards... 
[    9.235467] isapnp: No Plug & Play device found 
[    9.260259] Real Time Clock Driver v1.12ac 
[    9.260323] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
[    9.261228] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7 
[    9.261232] PCI: setting IRQ 7 as level-triggered 
[    9.261236] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7 
[    9.261245] ACPI: PCI interrupt for device 0000:00:1f.6 disabled 
[    9.261327] mice: PS/2 mouse device common for all mice 
[    9.261898] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[    9.262115] input: Macintosh mouse button emulation as /class/input/input0 
[    9.262157] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
[    9.262162] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
[    9.262341] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[    9.268138] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    9.268143] serio: i8042 AUX port at 0x60,0x64 irq 12 
[    9.268315] EISA: Probing bus 0 at eisa.0 
[    9.268341] EISA: Detected 0 cards. 
[    9.298440] TCP cubic registered 
[    9.298451] NET: Registered protocol family 1 
[    9.298474] Using IPI No-Shortcut mode 
[    9.298537] ACPI: (supports S0 S1 S3 S4 S5) 
[    9.298582]   Magic number: 8:45:165 
[    9.298625]   hash matches device ttyq5 
[    9.298975] Freeing unused kernel memory: 328k freed 
[    9.299071] Time: tsc clocksource has been installed. 
[    9.300680] input: AT Translated Set 2 keyboard as /class/input/input1 
[   10.512396] Capability LSM initialized 
[   10.545130] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3]) 
[   10.545137] ACPI: Processor [CPU0] (supports 8 throttling states) 
[   10.548480] ACPI: Thermal Zone [THM] (25 C) 
[   10.854502] usbcore: registered new interface driver usbfs 
[   10.854525] usbcore: registered new interface driver hub 
[   10.854543] usbcore: registered new device driver usb 
[   10.868849] USB Universal Host Controller Interface driver v3.0 
[   10.869146] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11 
[   10.869150] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11 
[   10.869164] PCI: Setting latency timer of device 0000:00:1d.0 to 64 
[   10.869167] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[   10.869354] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1 
[   10.869378] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80 
[   10.869491] usb usb1: configuration #1 chosen from 1 choice 
[   10.869520] hub 1-0:1.0: USB hub found 
[   10.869525] hub 1-0:1.0: 2 ports detected 
[   10.910513] SCSI subsystem initialized 
[   10.932131] libata version 2.20 loaded. 
[   10.967302] ieee1394: Initialized config rom entry `ip1394' 
[   10.971106] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11 
[   10.971121] PCI: Setting latency timer of device 0000:00:1d.1 to 64 
[   10.971125] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[   10.971154] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2 
[   10.971178] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40 
[   10.971267] usb usb2: configuration #1 chosen from 1 choice 
[   10.971292] hub 2-0:1.0: USB hub found 
[   10.971298] hub 2-0:1.0: 2 ports detected 
[   11.075386] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11 
[   11.075392] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11 
[   11.075405] PCI: Setting latency timer of device 0000:00:1d.2 to 64 
[   11.075409] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[   11.075432] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3 
[   11.075456] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20 
[   11.075549] usb usb3: configuration #1 chosen from 1 choice 
[   11.075573] hub 3-0:1.0: USB hub found 
[   11.075578] hub 3-0:1.0: 2 ports detected 
[    3.440000] Time: acpi_pm clocksource has been installed. 
[    3.476000] ata_piix 0000:00:1f.1: version 2.10ac1 
[    3.476000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007) 
[    3.476000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11 
[    3.476000] PCI: Setting latency timer of device 0000:00:1f.1 to 64 
[    3.476000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14 
[    3.476000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15 
[    3.476000] scsi0 : ata_piix 
[    3.640000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240 
[    3.640000] ata1.00: ATA-5: TOSHIBA MK6021GAS, GA030D, max UDMA/100 
[    3.640000] ata1.00: 117210240 sectors, multi 8: LBA 
[    3.648000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240 
[    3.648000] ata1.00: configured for UDMA/100 
[    3.648000] scsi1 : ata_piix 
[    3.968000] ata2.00: ATAPI, max UDMA/33 
[    4.140000] ata2.00: configured for UDMA/33 
[    4.140000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6021GA GA03 PQ: 0 ANSI: 5 
[    4.152000] scsi 1:0:0:0: CD-ROM            SAMSUNG  CDRW/DVD SN-324S U303 PQ: 0 ANSI: 5 
[    4.152000] b44.c:v1.01 (Jun 16, 2006) 
[    4.152000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11 
[    4.156000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0f:1f:2b:08:64 
[    4.156000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11 
[    4.208000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11 
[    4.208000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11 
[    4.208000] PCI: Setting latency timer of device 0000:00:1d.7 to 64 
[    4.208000] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[    4.208000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4 
[    4.208000] ehci_hcd 0000:00:1d.7: debug port 1 
[    4.208000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7 
[    4.208000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00 
[    4.212000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[    4.212000] usb usb4: configuration #1 chosen from 1 choice 
[    4.212000] hub 4-0:1.0: USB hub found 
[    4.212000] hub 4-0:1.0: 6 ports detected 
[    4.212000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[faffd800-faffdfff]  Max Packet=[2048]  IR/IT contexts=[4/8] 
[    4.224000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB) 
[    4.224000] sda: Write Protect is off 
[    4.224000] sda: Mode Sense: 00 3a 00 00 
[    4.224000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    4.224000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB) 
[    4.224000] sda: Write Protect is off 
[    4.224000] sda: Mode Sense: 00 3a 00 00 
[    4.224000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    4.224000]  sda: sda1 sda2 < sda5 > 
[    4.332000] sd 0:0:0:0: Attached scsi disk sda 
[    4.336000] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[    4.336000] scsi 1:0:0:0: Attached scsi generic sg1 type 5 
[    4.400000] sr0: scsi3-mmc drive: 5x/24x writer cd/rw xa/form2 cdda tray 
[    4.400000] Uniform CD-ROM driver Revision: 3.20 
[    4.400000] sr 1:0:0:0: Attached scsi CD-ROM sr0 
[    4.556000] Attempting manual resume 
[    4.556000] swsusp: Resume From Partition 8:5 
[    4.556000] PM: Checking swsusp image. 
[    4.556000] PM: Resume from disk failed. 
[    4.608000] kjournald starting.  Commit interval 5 seconds 
[    4.608000] EXT3-fs: mounted filesystem with ordered data mode. 
[    5.484000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[364fc00018f2f8a1] 
[   21.984000] iTCO_vendor_support: vendor-support=0 
[   22.028000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006) 
[   22.028000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0860) 
[   22.028000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
[   22.140000] Linux agpgart interface v0.102 (c) Dave Jones 
[   22.172000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   22.176000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   22.320000] intel_rng: FWH not detected 
[   22.332000] agpgart: Detected an Intel 855PM Chipset. 
[   22.340000] agpgart: AGP aperture is 128M @ 0xe0000000 
[   22.876000] input: PS/2 Mouse as /class/input/input2 
[   22.896000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3 
[   23.188000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:0191] 
[   23.188000] Yenta: Using CSCINT to route CSC interrupts to PCI 
[   23.188000] Yenta: Routing CardBus interrupts to PCI 
[   23.188000] Yenta TI: socket 0000:02:01.0, mfunc 0x012c1202, devctl 0x64 
[   23.304000] ieee80211_crypt: registered algorithm 'NULL' 
[   23.304000] ieee80211: 802.11 data/management/control stack, git-1.1.13 
[   23.304000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com> 
[   23.424000] Yenta: ISA IRQ mask 0x0478, PCI irq 11 
[   23.424000] Socket status: 30000086 
[   23.424000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06 
[   23.424000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff 
[   23.424000] cs: IO port probe 0xd000-0xefff: clean. 
[   23.424000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff 
[   23.424000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff 
[   23.476000] input: PC Speaker as /class/input/input4 
[   23.504000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq 
[   23.504000] ipw2200: Copyright(c) 2003-2006 Intel Corporation 
[   23.504000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7 
[   23.504000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection 
[   23.584000] nvidia: module license 'NVIDIA' taints kernel. 
[   24.128000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels) 
[   24.128000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11 
[   24.128000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007 
[   24.424000] cs: IO port probe 0x100-0x3af: clean. 
[   24.424000] cs: IO port probe 0x3e0-0x4ff: clean. 
[   24.424000] cs: IO port probe 0x820-0x8ff: clean. 
[   24.424000] cs: IO port probe 0xc00-0xcf7: clean. 
[   24.424000] cs: IO port probe 0xa00-0xaff: clean. 
[   24.540000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7 
[   24.540000] PCI: Setting latency timer of device 0000:00:1f.5 to 64 
[   25.360000] intel8x0_measure_ac97_clock: measured 55485 usecs 
[   25.360000] intel8x0: clocking to 48000 
[   25.504000] NET: Registered protocol family 17 
[   25.608000] fuse init (API version 7.8) 
[   25.744000] lp: driver loaded but no devices found 
[   25.808000] Adding 1510068k swap on /dev/disk/by-uuid/4db6ba73-1475-486c-b8b1-6bb4786a89f5.  Priority:-1 extents:1 across:1510068k 
[   26.000000] EXT3 FS on sda1, internal journal 
[   30.568000] PPP generic driver version 2.4.2 
[   30.672000] NET: Registered protocol family 10 
[   30.672000] lo: Disabled Privacy Extensions 
[   30.672000] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   31.744000] input: Lid Switch as /class/input/input5 
[   31.748000] ACPI: Lid Switch [LID] 
[   31.792000] input: Power Button (CM) as /class/input/input6 
[   31.796000] ACPI: Power Button (CM) [PBTN] 
[   31.836000] input: Sleep Button (CM) as /class/input/input7 
[   31.840000] ACPI: Sleep Button (CM) [SBTN] 
[   31.984000] ibm_acpi: ec object not found 
[   32.012000] ACPI: AC Adapter [AC] (on-line) 
[   32.040000] ACPI: ACPI Dock Station Driver 
[   32.088000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no) 
[   32.388000] ACPI: Battery Slot [BAT0] (battery present) 
[   32.388000] ACPI: Battery Slot [BAT1] (battery absent) 
[   32.400000] Using specific hotkey driver 
[   32.440000] pcc_acpi: loading... 
[   37.684000] ppdev: user-space parallel port driver 
[   38.024000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0. 
[   38.024000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode 
[   38.024000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode 
[   39.944000] apm: BIOS not found. 
[   42.496000] Bluetooth: Core ver 2.11 
[   42.496000] NET: Registered protocol family 31 
[   42.496000] Bluetooth: HCI device and connection manager initialized 
[   42.496000] Bluetooth: HCI socket layer initialized 
[   43.244000] Bluetooth: L2CAP ver 2.8 
[   43.244000] Bluetooth: L2CAP socket layer initialized 
[   43.396000] Bluetooth: RFCOMM socket layer initialized 
[   43.396000] Bluetooth: RFCOMM TTY layer initialized 
[   43.396000] Bluetooth: RFCOMM ver 1.8 
[  987.672000] b44: eth0: Link is up at 100 Mbps, full duplex. 
[  987.672000] b44: eth0: Flow control is off for TX and off for RX. 
[  987.672000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
[  998.456000] eth0: no IPv6 routers present 
[ 1003.672000] b44: eth0: Link is down. 
[ 1006.672000] b44: eth0: Link is up at 100 Mbps, full duplex. 
[ 1006.672000] b44: eth0: Flow control is off for TX and off for RX. 
[ 1157.568000] NET: Registered protocol family 24 
[ 1187.288000] ip_tables: (C) 2000-2006 Netfilter Core Team 
[ 3094.672000] b44: eth0: Link is down. 
```

I have also noticed that when this happens my system slows down. If I go into the system monitor sometimes my CPU is running upwards of 90% and user memory is at about 50%. When I restart there is not usually any internet but when I go back to the system monitor the numbers are back to normal. I do not know if there is any connection there...? 

Again I am a newbe to this so if you have any suggestions please take me step by step as to what I need to do. I hope someone can help me with this it is really frustrating.

---

### Post by Tapps on 2008-01-12
I really need some help with this.....please help me out on this one.

---

### Post by Aximilli on 2008-01-12
I am also having trouble with my network after installing VMplayer. I also have the interrupt 7 code on my eth0, and would like to know what it means.

---

