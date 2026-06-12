---
title: "Network not working"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by sa3atsky on 2007-05-29
Hi, I just recently installed Xubuntu, network wasnt working and my video card (an old matrox) werent identified. I can only run at 800x600 resolution and no network is working whatsoever.
Tried hooking up different cables to the Router, replaced network cards. still, nothing..

Installed Ubuntu, still the exact same problems.. I remember I've installed Ubuntu once before on the same pc and both the videocard and network were working perfectly. Please help!

---

### Post by Blender on 2007-05-29
Hello!

Open a terminal (Applications->Accessories->Terminal) and type the following (without the $)
```

$ /sbin/ifconfig

```
and
```

$ lspci

```

Paste the output of the two commands here.

---

### Post by sa3atsky on 2007-05-29
Heres the /sbin/ifconfig
---------------------------------------------------------------------------------------------------
eth1      Link encap:Ethernet  HWaddr 00:50:FC:22:08:40  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0xa000 

eth1:avah Link encap:Ethernet  HWaddr 00:50:FC:22:08:40  
          inet addr:169.254.4.15  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:9 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2004 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2004 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123832 (120.9 KiB)  TX bytes:123832 (120.9 KiB)
---------------------------------------------------------------------------------------------------


..and the lspci
---------------------------------------------------------------------------------------------------
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0d.0 VGA compatible controller: Matrox Graphics, Inc. MGA 2064W [Millennium] (rev 01)
00:0f.0 Mass storage controller: Promise Technology, Inc. PDC40718 (SATA 300 TX4) (rev 02)
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
---------------------------------------------------------------------------------------------------

---

### Post by Bigdog60 on 2007-05-29
Dude something is most likely wrong with your config of your wireless internet go onto config and find wireless etc.

---

### Post by sa3atsky on 2007-05-29
Im on a wired connection to the router!

---

### Post by Blender on 2007-05-29
Hmm... there's a Realtek card that seems to be recognized.

Could you also post the output of **dmesg**, **/sbin/lsmod**, and the contents of the **/etc/network/interfaces** file?

Also, what are the IP addresses of your computer and the router?

---

### Post by ugm6hr on 2007-05-29
> **sa3atsky said:**
> 
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


This card chipset definitely works fine with Xubuntu7.04 - cos I have it on my laptop, and all that was required was to plug the ethernet cable into my router at booting.  Then edit Applications->System->Network with the correct settings (I use DHCP on my router).

---

### Post by handydan918 on 2007-05-30
Hope this isn't too basic, but did you try typing "sudo dhclient" in a terminal?

---

### Post by sa3atsky on 2007-05-30
> **handydan918 said:**
> Hope this isn't too basic, but did you try typing "sudo dhclient" in a terminal?

Tried that, searches and doesnt find any DHClient available..



Did /sbin/lsmod
What I noticed:
[B][   57.359960] Local APIC disabled by BIOS -- you can enable it with "lapic"
APIC not detected so using dummpy APIC emulation
ACPI: Interpretere disabled
[   58.434009] pnp: PnP ACPI: disabled
[  108.785792] ADDRCONF(NETDEV_UP): eth1: link is not ready[/B]

Dunno how this is relevant, please look at entier **/sbin/lsmod**:
[Link to text file (view with wordpad or other, sorry couldnt find better host)]("http://upload2.net/page/download/gegSYTDWHnUFaxP/Text.txt.html")



Interfaces file
--------------------------------------------------
[B][I]auto lo
iface lo inet loopback


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp
address 192.168.2.5
netmask 255.255.255.0

auto eth0

auto eth1[/I][/B]
--------------------------------------------------

---

### Post by Blender on 2007-05-30
You forgot the **lsmod**-thing, I guess.
Can you post the output of **/sbin/ifconfig -a**?

At least according to **dmesg**, your Realtek card at **eth0**.
```

  65.619931] 8139cp 0000:00:10.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   65.619944] 8139cp 0000:00:10.0: Try the "8139too" driver instead.
[   65.627307] 8139too Fast Ethernet driver 0.9.28
[   65.627422] PCI: Found IRQ 9 for device 0000:00:10.0
[   65.627441] PCI: Sharing IRQ 9 with 0000:00:07.2
[   65.627799] eth0: RealTek RTL8139 at 0xd482a000, 00:50:fc:22:08:40, IRQ 9
[   65.627807] eth0:  Identified 8139 chip type 'RTL-8139C'

```

Guess you forgot the IP addresses, too?
How do you connect to your router? Do you use a static IP or DHCP?

---

### Post by sa3atsky on 2007-06-04
Here are the rest of the details:

```
root@Ravage:~# /sbin/ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:08:54:B3:7C:C3
          inet6 addr: fe80::208:54ff:feb3:7cc3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1078837 (1.0 MiB)  TX bytes:11887 (11.6 KiB)
          Interrupt:9 Base address:0x6000

eth0:avah Link encap:Ethernet  HWaddr 00:08:54:B3:7C:C3
          inet addr:169.254.8.137  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:9 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:991 errors:0 dropped:0 overruns:0 frame:0
          TX packets:991 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:78968 (77.1 KiB)  TX bytes:78968 (77.1 KiB)

root@Ravage:~# lsmod
Module                  Size  Used by
nls_iso8859_1           5120  1
nls_cp437               6784  1
vfat                   14208  1
fat                    53916  1 vfat
rfcomm                 40856  0
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
apm                    22752  2
ppdev                  10116  0
speedstep_lib           6148  0
cpufreq_stats           7360  0
cpufreq_userspace       5408  0
cpufreq_ondemand        9228  0
cpufreq_conservative     8200  0
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0
af_packet              23816  4
nls_utf8                3072  2
ntfs                  107764  2
lp                     12452  0
fuse                   46612  0
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
psmouse                38920  0
serio_raw               7940  0
intel_agp              25116  1
pcspkr                  4224  0
i2c_piix4               9740  0
i2c_core               22784  1 i2c_piix4
agpgart                35400  1 intel_agp
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
ipv6                  268704  8
tsdev                   8768  0
evdev                  11008  3
ext3                  133128  2
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0
sd_mod                 23428  10
usbhid                 26592  0
hid                    27392  1 usbhid
usb_storage            72256  1
libusual               17936  1 usb_storage
ide_cd                 32672  0
cdrom                  37664  1 ide_cd
ata_generic             9092  0
generic                 5124  0 [permanent]
floppy                 59524  0
r8169                  32392  0
sata_promise           13316  5
libata                125720  2 ata_generic,sata_promise
scsi_mod              142348  4 sg,sd_mod,usb_storage,libata
uhci_hcd               25360  0
usbcore               134280  5 usbhid,usb_storage,libusual,uhci_hcd
piix                   10756  0 [permanent]
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability
```

--------------------------------------------------------------------------------

My network is on DHCP but I assign static IP addresses to the computers on the network.. But I tried both static and DHCP on ubuntu, both didnt work...
Restarted the Router, installed Kubuntu for the Network Config tool. still nothing

My default gateway: 192.168.2.2
Whenever I try to input the Default Gateway IP address in the Network config GUI it changes back to 0.0.0.0.. I feel like any changes that I make make no difference.. My Subnet Mask is: 255.255.255.0 and it still inputs 255.255.0.0 ..

Somebody please help this problem is making me hate ubuntu!!

---

### Post by Blender on 2007-06-04
Hmmm...
Don't know...
Two things to try:
[list=1]
[*] Restart your computer, go to the network configuration tool and try setting up 
your networking. You said it changes back to 0.0.0.0. *After* it does so, open a 
terminal, get the output of **dmesg** and paste it here. I hope the driver will
print something as to why it does not work.

[*] I see your networking card is sharing an interrupt with the USB controller. Is it 
possible to, just temporarily, disable USB in BIOS?
[/list]

Do you have other computers in the network? Can you ping them?

I am sorry you're experiencing this problem. It's very odd, as this card works out of 
the box under GNU/Linux.

---

### Post by sa3atsky on 2007-06-04
```
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009d000 end: 000000000009d000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009d000 size: 0000000000003000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e6c00 size: 0000000000019400 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000003ffd800 end: 00000000040fd800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000040fd800 size: 0000000000002000 end: 00000000040ff800 type: 3
[    0.000000] copy_e820_map() start: 00000000040ff800 size: 0000000000000400 end: 00000000040ffc00 type: 4
[    0.000000] copy_e820_map() start: 00000000040ffc00 size: 000000000ff00400 end: 0000000014000000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000fffe6c00 size: 0000000000019400 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d000 (usable)
[    0.000000]  BIOS-e820: 000000000009d000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6c00 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000040fd800 (usable)
[    0.000000]  BIOS-e820: 00000000040fd800 - 00000000040ff800 (ACPI data)
[    0.000000]  BIOS-e820: 00000000040ff800 - 00000000040ffc00 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000040ffc00 - 0000000014000000 (usable)
[    0.000000]  BIOS-e820: 00000000fffe6c00 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 320MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 81920) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    81920
[    0.000000]   HighMem     81920 ->    81920
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    81920
[    0.000000] On node 0 totalpages: 81920
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 608 pages used for memmap
[    0.000000]   Normal zone: 77216 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.1 present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6a90
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x00000001 PTL  0x01000000) @ 0x040fda8b
[    0.000000] ACPI: FADT (v001 INTEL  MP440BX  0x19991130 PTL  0x000f4240) @ 0x040ff78c
[    0.000000] ACPI: DSDT (v001  Intel   MP44BX 0x00000001 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 14000000:ebfe6c00)
[    0.000000] Detected 697.016 MHz processor.
[   57.114548] Built 1 zonelists.  Total pages: 81280
[   57.114558] Kernel command line: root=UUID=457a5d24-9478-4632-a694-571d5b8cecbd ro quiet splash
[   57.115123] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   57.115143] mapped APIC to ffffd000 (0128b000)
[   57.115153] Enabling fast FPU save and restore... done.
[   57.115161] Enabling unmasked SIMD FPU exception support... done.
[   57.115184] Initializing CPU#0
[   57.115287] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   57.117442] Console: colour VGA+ 80x25
[   57.118614] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   57.120103] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   57.162119] Memory: 313400k/327680k available (1992k kernel code, 13664k reserved, 893k data, 328k init, 0k highmem)
[   57.162151] virtual kernel memory layout:
[   57.162154]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   57.162159]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   57.162163]     vmalloc : 0xd4800000 - 0xff7fe000   ( 687 MB)
[   57.162167]     lowmem  : 0xc0000000 - 0xd4000000   ( 320 MB)
[   57.162171]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   57.162175]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   57.162180]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   57.162190] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   57.239279] Calibrating delay using timer specific routine.. 1395.16 BogoMIPS (lpj=2790326)
[   57.239397] Security Framework v1.0.0 initialized
[   57.239416] SELinux:  Disabled at boot.
[   57.239465] Mount-cache hash table entries: 512
[   57.239815] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   57.239846] CPU: L1 I cache: 16K, L1 D cache: 16K
[   57.239854] CPU: L2 cache: 256K
[   57.239863] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   57.239891] Compat vDSO mapped to ffffe000.
[   57.239912] Remapping vsyscall page to ffffe000
[   57.239938] Checking 'hlt' instruction... OK.
[   57.255510] SMP alternatives: switching to UP code
[   57.255933] Freeing SMP alternatives: 11k freed
[   57.256444] Early unpacking initramfs... done
[   58.178073] CPU0: Intel Pentium III (Coppermine) stepping 01
[   58.178091] SMP motherboard not detected.
[   58.178098] Local APIC not detected. Using dummy APIC emulation.
[   58.178228] Brought up 1 CPUs
[   58.178946] Booting paravirtualized kernel on bare hardware
[   58.179117] Time:  0:08:11  Date: 05/05/107
[   58.179262] NET: Registered protocol family 16
[   58.179554] EISA bus registered
[   58.180083] PCI: PCI BIOS revision 2.10 entry at 0xfd993, last bus=1
[   58.180091] PCI: Using configuration type 1
[   58.180097] Setting up standard PCI resources
[   58.182557] ACPI: Interpreter disabled.
[   58.182570] Linux Plug and Play Support v0.97 (c) Adam Belay
[   58.182593] pnp: PnP ACPI: disabled
[   58.182603] PnPBIOS: Scanning system for PnP BIOS support...
[   58.182656] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6b10
[   58.182666] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9e95, dseg 0x400
[   58.188167] PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
[   58.188314] PCI: Probing PCI hardware
[   58.188328] PCI: Probing PCI hardware (bus 00)
[   58.188691] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   58.188697] * this clock source is slow. Consider trying other clock sources
[   58.188752] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[   58.188762] PCI quirk: region 7000-700f claimed by PIIX4 SMB
[   58.188835] Boot video device is 0000:00:0d.0
[   58.190245] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   58.191832] NET: Registered protocol family 8
[   58.191839] NET: Registered protocol family 20
[   58.192015] pnp: 00:00: ioport range 0x370-0x371 has been reserved
[   58.192055] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   58.192065] pnp: 00:0a: ioport range 0x8000-0x803f has been reserved
[   58.192073] pnp: 00:0a: ioport range 0x7000-0x700f has been reserved
[   58.192962] PCI: Bridge: 0000:00:01.0
[   58.192970]   IO window: disabled.
[   58.192979]   MEM window: disabled.
[   58.192986]   PREFETCH window: disabled.
[   58.193070] NET: Registered protocol family 2
[   58.219403] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   58.219641] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   58.220065] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   58.220322] TCP: Hash tables configured (established 16384 bind 8192)
[   58.220331] TCP reno registered
[   58.231588] checking if image is initramfs... it is
[   59.986820] Freeing initrd memory: 7006k freed
[   59.987959] audit: initializing netlink socket (disabled)
[   59.987998] audit(1181002093.056:1): initialized
[   59.988377] VFS: Disk quotas dquot_6.5.1
[   59.988439] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   59.988595] io scheduler noop registered
[   59.988604] io scheduler anticipatory registered
[   59.988611] io scheduler deadline registered
[   59.988645] io scheduler cfq registered (default)
[   59.988666] Limiting direct PCI/PCI transfers.
[   59.989174] isapnp: Scanning for PnP cards...
[   60.343644] isapnp: No Plug & Play device found
[   60.428861] Real Time Clock Driver v1.12ac
[   60.429050] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   60.429266] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   60.431307] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   60.431987] mice: PS/2 mouse device common for all mice
[   60.433614] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   60.434312] input: Macintosh mouse button emulation as /class/input/input0
[   60.434413] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   60.434426] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   60.434892] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   60.438564] serio: i8042 KBD port at 0x60,0x64 irq 1
[   60.438583] serio: i8042 AUX port at 0x60,0x64 irq 12
[   60.438983] EISA: Probing bus 0 at eisa.0
[   60.439028] Cannot allocate resource for EISA slot 1
[   60.439062] Cannot allocate resource for EISA slot 7
[   60.439069] Cannot allocate resource for EISA slot 8
[   60.439075] EISA: Detected 0 cards.
[   60.439298] TCP cubic registered
[   60.439320] NET: Registered protocol family 1
[   60.439374] Using IPI No-Shortcut mode
[   60.439445]   Magic number: 11:434:101
[   60.440794] Freeing unused kernel memory: 328k freed
[   60.443004] Time: tsc clocksource has been installed.
[   60.460501] input: AT Translated Set 2 keyboard as /class/input/input1
[   62.099210] Capability LSM initialized
[   62.245427] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   63.655272] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   63.655306] PIIX4: chipset revision 1
[   63.655313] PIIX4: not 100% native mode: will probe irqs later
[   63.655331]     ide1: BM-DMA at 0x1008-0x100f, BIOS settings: hdc:DMA, hdd:pio
[   63.655355] Probing IDE interface ide1...
[   63.794168] SCSI subsystem initialized
[   63.820270] libata version 2.20 loaded.
[   63.959014] usbcore: registered new interface driver usbfs
[   63.959078] usbcore: registered new interface driver hub
[   63.959147] usbcore: registered new device driver usb
[   63.963434] USB Universal Host Controller Interface driver v3.0
[   64.289228] Floppy drive(s): fd0 is 1.44M
[   64.335321] FDC 0 is a post-1991 82077
[   64.434777] hdc: HL-DT-ST GCE-8526B, ATAPI CD/DVD-ROM drive
[   65.106807] ide1 at 0x170-0x177,0x376 on irq 15
[   65.124566] sata_promise 0000:00:0f.0: version 2.01
[   65.124611] PCI: setting IRQ 5 as level-triggered
[   65.124619] PCI: Found IRQ 5 for device 0000:00:0f.0
[   65.124839] ata1: SATA max UDMA/133 cmd 0xd482a200 ctl 0xd482a238 bmdma 0x00000000 irq 5
[   65.124921] ata2: SATA max UDMA/133 cmd 0xd482a280 ctl 0xd482a2b8 bmdma 0x00000000 irq 5
[   65.125005] ata3: SATA max UDMA/133 cmd 0xd482a300 ctl 0xd482a338 bmdma 0x00000000 irq 5
[   65.125087] ata4: SATA max UDMA/133 cmd 0xd482a380 ctl 0xd482a3b8 bmdma 0x00000000 irq 5
[   65.125114] scsi0 : sata_promise
[   65.162106] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   65.162132] Uniform CD-ROM driver Revision: 3.20
[   65.434591] ata1: SATA link down (SStatus 0 SControl 300)
[   65.434631] scsi1 : sata_promise
[   65.902547] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   65.946936] ata2.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[   65.946955] ata2.00: ATA-7: ST3320620AS, 3.AAE, max UDMA/133
[   65.946964] ata2.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   66.013566] ata2.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[   66.013589] ata2.00: configured for UDMA/133
[   66.013616] scsi2 : sata_promise
[   66.478495] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   66.527997] ata3.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[   66.528021] ata3.00: ATA-7: ST3320620AS, 3.AAE, max UDMA/133
[   66.528030] ata3.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   66.586273] ata3.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[   66.586286] ata3.00: configured for UDMA/133
[   66.586312] scsi3 : sata_promise
[   67.054469] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   72.384248] ata4.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[   72.384273] ata4.00: ATA-7: ST3320620AS, 3.AAE, max UDMA/133
[   72.384282] ata4.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   72.442524] ata4.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[   72.442538] ata4.00: configured for UDMA/133
[   72.442873] scsi 1:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[   72.443939] scsi 2:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[   72.444814] scsi 3:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[   72.445754] r8169 Gigabit Ethernet driver 2.2LK loaded
[   72.445791] PCI: Enabling device 0000:00:10.0 (0114 -> 0117)
[   72.445806] PCI: setting IRQ 9 as level-triggered
[   72.445813] PCI: Found IRQ 9 for device 0000:00:10.0
[   72.445830] PCI: Sharing IRQ 9 with 0000:00:07.2
[   72.446464] eth0: RTL8169s/8110s at 0xd482c000, 00:08:54:b3:7c:c3, IRQ 9
[   72.449967] PCI: Found IRQ 9 for device 0000:00:07.2
[   72.449989] PCI: Sharing IRQ 9 with 0000:00:10.0
[   72.450007] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   72.450618] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   72.450668] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001020
[   72.453471] usb usb1: configuration #1 chosen from 1 choice
[   72.454021] hub 1-0:1.0: USB hub found
[   72.454053] hub 1-0:1.0: 2 ports detected
[   72.493862] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[   72.493981] sda: Write Protect is off
[   72.493989] sda: Mode Sense: 00 3a 00 00
[   72.494039] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   72.494188] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[   72.494218] sda: Write Protect is off
[   72.494225] sda: Mode Sense: 00 3a 00 00
[   72.494272] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   72.494282]  sda:<3>ldm_parse_privhead(): Cannot find PRIVHEAD structure. LDM database is corrupt. Aborting.
[   72.508137] ldm_validate_privheads(): Cannot find PRIVHEAD 1.
[   72.508153]  sda1
[   72.508992] sd 1:0:0:0: Attached scsi disk sda
[   72.509452] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[   72.509488] sdb: Write Protect is off
[   72.509496] sdb: Mode Sense: 00 3a 00 00
[   72.509545] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   72.509684] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[   72.509714] sdb: Write Protect is off
[   72.509721] sdb: Mode Sense: 00 3a 00 00
[   72.509768] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   72.509778]  sdb: sdb1 sdb2 sdb3
[   72.547038] sd 2:0:0:0: Attached scsi disk sdb
[   72.547485] SCSI device sdc: 625142448 512-byte hdwr sectors (320073 MB)
[   72.547518] sdc: Write Protect is off
[   72.547526] sdc: Mode Sense: 00 3a 00 00
[   72.547574] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   72.547720] SCSI device sdc: 625142448 512-byte hdwr sectors (320073 MB)
[   72.547749] sdc: Write Protect is off
[   72.547757] sdc: Mode Sense: 00 3a 00 00
[   72.547803] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   72.547814]  sdc: sdc1
[   72.599761] sd 3:0:0:0: Attached scsi disk sdc
[   72.615734] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   72.616134] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   72.616483] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   72.798002] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   72.975836] usb 1-2: configuration #1 chosen from 1 choice
[   73.019558] usbcore: registered new interface driver hiddev
[   73.054026] Attempting manual resume
[   73.054038] swsusp: Resume From Partition 8:19
[   73.054043] PM: Checking swsusp image.
[   73.059423] input: Logitech USB Receiver as /class/input/input2
[   73.059468] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:07.2-2
[   73.078740] PM: Resume from disk failed.
[   73.089561] input: Logitech USB Receiver as /class/input/input3
[   73.090018] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:07.2-2
[   73.090061] usbcore: registered new interface driver usbhid
[   73.090071] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   73.210994] kjournald starting.  Commit interval 5 seconds
[   73.211027] EXT3-fs: mounted filesystem with ordered data mode.
[   81.555972] r8169: eth0: link up
[   82.976280] NET: Registered protocol family 17
[   86.559251] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   86.609931] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   86.729225] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   87.105911] Linux agpgart interface v0.102 (c) Dave Jones
[   87.112400] agpgart: Detected an Intel 440BX Chipset.
[   87.117093] agpgart: AGP aperture is 64M @ 0xf8000000
[   87.432088] input: PC Speaker as /class/input/input4
[   87.845165] parport: PnPBIOS parport detected.
[   87.845240] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   88.300257] fuse init (API version 7.8)
[   88.352585] lp0: using parport0 (interrupt-driven).
[   88.433349] Adding 658656k swap on /dev/disk/by-uuid/1eb862e3-b717-41da-a21e-1167ac233158.  Priority:-1 extents:1 across:658656k
[   88.635551] EXT3 FS on sdb1, internal journal
[   89.278421] kjournald starting.  Commit interval 5 seconds
[   89.279165] EXT3 FS on sdb2, internal journal
[   89.279180] EXT3-fs: mounted filesystem with ordered data mode.
[   89.334504] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   89.407164] NTFS volume version 3.1.
[   89.433280] NTFS volume version 3.1.
[   96.876820] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   96.877002] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   96.877539] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   96.877782] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[  103.397223] ppdev: user-space parallel port driver
[  104.564513] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  105.905791] Bluetooth: Core ver 2.11
[  105.905944] NET: Registered protocol family 31
[  105.905951] Bluetooth: HCI device and connection manager initialized
[  105.905960] Bluetooth: HCI socket layer initialized
[  105.993292] Bluetooth: L2CAP ver 2.8
[  105.993304] Bluetooth: L2CAP socket layer initialized
[  106.012880] Bluetooth: RFCOMM socket layer initialized
[  106.012914] Bluetooth: RFCOMM TTY layer initialized
[  106.012920] Bluetooth: RFCOMM ver 1.8
[  125.259776] NET: Registered protocol family 10
[  125.260033] lo: Disabled Privacy Extensions
[  135.576275] eth0: no IPv6 routers present
```

Here it is..

How come I'm assigned this IP: 169.254.8.137 when my router is set up only to assign IP's in the 192.168.2.X range? Maybe thats the problem, how can I change that?

---

### Post by Blender on 2007-06-05
This second eth0 entry has something to do with [avahi]("http://en.wikipedia.org/wiki/Avahi_%28software%29"), I don't know. I don't use it.

Backup your *interfaces* files:
```

$ sudo cp /etc/network/interfaces /etc/network/interfaces-`date +%Y%m%d`

```
The above line creates a backup copy, appending the current date to it.

Now open the *interfaces* file:
```

$ sudo nano /etc/network/interfaces

```

and change it to
```

auto lo
iface lo inet loopback


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet static
address 192.168.2.**X**
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.**Y**

auto eth0

auto eth1

```
**X** is where you should put your computer's IP suffix (the last number) and 
**Y** is that of the router, you said 2, I think.

You could restart networking now, but it's probably better to restart your computer.

Now, what happens after the restart? Can you ping your router? Can you ping
google's IP (72.14.207.99, for example) ?

---

### Post by sa3atsky on 2007-06-05
Hi, thanks for going with me this far
I did exactly what you told me, saved the /network/interfaces/ file and rebooted.. When I checked the file after I rebooted it went back to the old faulty original settings.. Its like Kubuntus Network Manager is automatically changing it... is there a chance that the network settings within system settings and the setup screen in knetwork manager are conflicting? Should I uninstall Knetwork manager?

---

### Post by Blender on 2007-06-05
Yes, try uninstalling it. You can always install it later, if you want to.

---

### Post by sa3atsky on 2007-06-06
Uninstalled, rewrote the code.. restarted, restarted, restarted..... nothing.... :(

Although when I "sudo dhclient" on the terminal it searches on 255.255.255.255 instead of 255.255.255.0

---

