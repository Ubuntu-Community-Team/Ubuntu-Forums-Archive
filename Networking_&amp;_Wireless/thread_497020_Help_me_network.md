---
title: "Help me network"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by Dwiman89 on 2007-07-09
Hi
             Im new to linux and know little about networking. I have to computers. one laptop and one desktop that im trying to network. My laptop runs Ubuntu 7.04 fiesty fawn.  My desktop runs Windows XP service pack 2. I have two ethernet cords.  I have an HP 10 Base T hub.
     Im trying to get the two networked where i can share files between the two. and get internet on my desktop, and possibly get synergy working. My laptop gets the internet through a wifi card.  I havent set up the network between the two computers partly cause i dont know how and i dont want to loose my internet on my laptop. Is there a way i can get two networks running(my wifi network, and my LAN network) at the same time so i can share the internet via wifi. and share files and possibly use synergy all at the same time. I know this is possible with windows but i have no idea what to do with Ubuntu. Please help me.

---

### Post by Mr. C. on 2007-07-10
Sure, its not difficult.  You didn't say, but I presume your laptop also has an ethernet card?

The first step will be to get that card enabled and configured.  Have you been successful in getting packets flowing through the wired ethernet?

Once your laptop's wired network is functional, you need to configure your system to act as a router.  Before we spend too much time on this, let's see some output from the following commands run on the laptop in a command window:

```
ifconfig -a
netstat -rn
```

MrC

---

### Post by Dwiman89 on 2007-07-11
root@derrick-laptop:/home/derrick# iwconfig -a
-a        No such device

root@derrick-laptop:/home/derrick# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 eth0
umm, this is what i got.

---

### Post by Mr. C. on 2007-07-11
The command I wanted output from was **ifconfig**, not iwconfig (the latter is for wireless).

Your eth0 is configured with an automatic address - this is fine, but you have to make sure the other side is also so configured.

Have you connected your eth0 to the hub, and your desktop to the hub as well?

Does your desktop have an IP address yet?  If so, what is it.  In a  Windows command window, run
```

ipconfig /all
```

Once you have them connected, lets try:

```
ping *other_system's_ip_address*
```

---

### Post by Dwiman89 on 2007-07-14
this is what i got from ''ifconfig -a''
eth0      Link encap:Ethernet  HWaddr 08:00:46:02:5C:20  
          UP BROADCAST RUNNING MULTICAST  MTU:1514  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:516 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:126830 (123.8 KiB)

eth0:avah Link encap:Ethernet  HWaddr 08:00:46:02:5C:20  
          inet addr:169.254.2.163  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1514  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:789 errors:0 dropped:0 overruns:0 frame:0
          TX packets:789 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97953 (95.6 KiB)  TX bytes:97953 (95.6 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0D:88:E9:DE:F5  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:88ff:fee9:def5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45005 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35685802 (34.0 MiB)  TX bytes:5130454 (4.8 MiB)
          Interrupt:9 Memory:14010000-14020000 

This is what i got from ''ipconfig /all'' on the desktop(i had to type this so i hop i got it right)

Windows IP Configuration

              Host Name. . . . . . . . . . . . : DESKTOP
              Primary Dns Suffix . . . . . : 
              Node Type . . . . . . . . . . . . : Unknown
              IP Routing Enabled . . . . .: No
              WINS Proxy Enabled . . .  : No

Ethernet adapter Local Area Connection 6

              Connection-specific DNS suffix . :
              Description . . . . . . . . . . . . . . . . . . .: Asound 10/100M Based Fast Ethernet Card
ard
              Physical Address . . . . . . . . . . . . .  : 00-02-2A-B0-1A-F7
              Dhcp  Enabled . . . . . . . . . . . . . . . . : No
              IP Address . . . . . . . . . . . . . . . . . . . . :192.168.0.1
              Subnet Mask . . . . . . . . . . . . . . . . . . :255.255.255.0
              Default Gateway . . . . . . . . . . . . . .  :192.168.0.2
this is what i got when i pinged that address 
ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
213 packets transmitted, 0 received, 100% packet loss, time 212273ms

    I played a little with it in the GUI. i went to network under places and my desktop doesnt show up. only ''Saucy'' Which i think is my brothers computer name  who picks up internet from our wifi router too. Im not really interested in accessing my Brothers computer. i dont see my laptop under network places on my desktop ether. What do you think i should do now?

---

### Post by fneto on 2007-07-14
Hello;

    Would you please elaborate a little further how is your WIFI?
   I suggest you getting a router/firewall for your "internet gateway" so the rest of your network does not depend on your laptop for internet access.
   Then your network also would be simpler and cleaner to setup... Just a preference!

---

### Post by Mr. C. on 2007-07-14
Your wired Ethernet on your lapotop (eth0) has been automatically configured and is using IP 169.254.2.163, an IP address which is in the automatic range (meaning, you didn't specify an IP, and there is no DHCP server on that subnet to provide an address).

However, your desktop has an IP address 192.168.0.1, which is in the private range.  

Your laptop and desktop are incorrectly configured, as they are on different networks.

Configure your eth0 device on your laptop to be in the 192.168.0.0/24 range, as in:

```

$ cat /etc/network/interfaces
...
auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
...

```

Restart the interface with:
```

ifdown eth0
ifup eth0
```

Once this is done, both machines should be able to ping each other by IP address.  When you have this done, we'll go to the next step.

MrC

---

### Post by Dwiman89 on 2007-07-17
I tried the commands above, but they didnt work. ''bash command not found''. i tried setting it up from GUI under network settings.i set the IP to 192.168.0.2. i set the subnet to 255.255.255.0. and left the gateway blank. I tried to ping the other computers adress from boath, but nothing went through (0 packets recieved). Im lost as to what to do now.

---

### Post by Mr. C. on 2007-07-17
Are the lights on the hub and back of the ethernet card on?  Do they turn off when you unplug the cable ?

MrC

---

### Post by Dwiman89 on 2007-07-17
Yes, all the light are on. the back of boath ethernet cards. and where they plug into the hub. there are 16 ports on my hub. i have the two pluged into  port 10 and 12, just becaues it was the easest reach.

---

### Post by Mr. C. on 2007-07-17
Wait...you have both Ethernet plugs from that single computer plugged into the same hub ?

MrC

---

### Post by Dwiman89 on 2007-07-17
My hub has 16 ports.  It is a HP 10 base T (J2611B). It seems to be that the ports are in sections of 4 (1,2,3,4/5,6,7,8/9,10,11,12/13,14,15,16) Ive got an ethernet cord going from my laptop into port 10, and my desktop going into port 12.  All other ports are empty.There is a swich for port 16 called MDI/MDI-X. but i dont think that has anything to do with it.

---

### Post by Mr. C. on 2007-07-17
Ok, I had misunderstood your earlier post.

Since you are using a hub, it is possible that the card is not auto-negotiating to 10 Mbit, half duplex.

Please look for messages in your /var/log/messages or /var/log/dmesg for any eth0-related messages, and those in the immediate vicinity.

Also, run as root, the following command:

```
ethtool -i eth0
```

You can also try forcing 10 Mbit, half-duplex:
```

ethtool eth0 -s speed 10 duplex half autoneg off
```

MrC

---

### Post by Dwiman89 on 2007-07-17
I tried those commands and this is what i got for ehtool -i eth0:
driver: kaweth
version: 
firmware-version: 
bus-info: 

This is what i got for   ethtool eth0 -s speed 10 duplex half autoneg off
ethtool: bad command line argument(s)
For more information run ethtool -h

This is what i got for dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000ea400 size: 0000000000015c00 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000007ef0000 end: 0000000007ff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000007ff0000 size: 000000000000fc00 end: 0000000007fffc00 type: 3
[    0.000000] copy_e820_map() start: 0000000007fffc00 size: 0000000000000400 end: 0000000008000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fffea400 size: 0000000000015c00 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ea400 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000007ff0000 (usable)
[    0.000000]  BIOS-e820: 0000000007ff0000 - 0000000007fffc00 (ACPI data)
[    0.000000]  BIOS-e820: 0000000007fffc00 - 0000000008000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffea400 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 127MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 32752) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    32752
[    0.000000]   HighMem     32752 ->    32752
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    32752
[    0.000000] On node 0 totalpages: 32752
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 223 pages used for memmap
[    0.000000]   Normal zone: 28433 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI not present or invalid.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6d80
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x00000000  LTP 0x00000000) @ 0x07ffcffa
[    0.000000] ACPI: FADT (v001 SONY            0x00000000 PTL  0x000f4240) @ 0x07fffb8c
[    0.000000] ACPI: DSDT (v001   SONY          0x00000000 MSFT 0x01000007) @ 0x00000000
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 08000000:f7fea400)
[    0.000000] Detected 331.607 MHz processor.
[   32.055365] Built 1 zonelists.  Total pages: 32497
[   32.055384] Kernel command line: root=UUID=8127c5ec-ff74-4884-adae-d628601d8691 ro quiet splash
[   32.056526] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   32.056572] mapped APIC to ffffd000 (01109000)
[   32.056590] Enabling fast FPU save and restore... done.
[   32.056636] Initializing CPU#0
[   32.056814] PID hash table entries: 512 (order: 9, 2048 bytes)
[   32.058963] Console: colour VGA+ 80x25
[   32.059566] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[   32.060373] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[   32.083385] Memory: 118648k/131008k available (1992k kernel code, 11832k reserved, 893k data, 328k init, 0k highmem)
[   32.083450] virtual kernel memory layout:
[   32.083458]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   32.083467]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   32.083475]     vmalloc : 0xc8800000 - 0xff7fe000   ( 879 MB)
[   32.083484]     lowmem  : 0xc0000000 - 0xc7ff0000   ( 127 MB)
[   32.083492]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   32.083501]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   32.083509]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   32.083529] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   32.160787] Calibrating delay using timer specific routine.. 664.33 BogoMIPS (lpj=1328676)
[   32.161080] Security Framework v1.0.0 initialized
[   32.161132] SELinux:  Disabled at boot.
[   32.161258] Mount-cache hash table entries: 512
[   32.162227] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   32.162297] CPU: L1 I cache: 16K, L1 D cache: 16K
[   32.162321] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   32.162400] Compat vDSO mapped to ffffe000.
[   32.162440] Remapping vsyscall page to ffffe000
[   32.162495] Checking 'hlt' instruction... OK.
[   32.176926] SMP alternatives: switching to UP code
[   32.177817] Freeing SMP alternatives: 11k freed
[   32.178905] Early unpacking initramfs... done
[   34.507044] CPU0: Intel Mobile Pentium II stepping 0a
[   34.507079] SMP motherboard not detected.
[   34.507092] Local APIC not detected. Using dummy APIC emulation.
[   34.507484] Brought up 1 CPUs
[   34.509113] Booting paravirtualized kernel on bare hardware
[   34.509527] Time:  2:16:16  Date: 06/17/107
[   34.509733] NET: Registered protocol family 16
[   34.510519] EISA bus registered
[   34.514298] PCI: PCI BIOS revision 2.10 entry at 0xfd9e4, last bus=0
[   34.514318] PCI: Using configuration type 1
[   34.514331] Setting up standard PCI resources
[   34.524035] ACPI: Interpreter disabled.
[   34.524066] Linux Plug and Play Support v0.97 (c) Adam Belay
[   34.524140] pnp: PnP ACPI: disabled
[   34.524157] PnPBIOS: Scanning system for PnP BIOS support...
[   34.524290] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6df0
[   34.524312] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb548, dseg 0x400
[   34.541384] PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
[   34.541879] PCI: Probing PCI hardware
[   34.541908] PCI: Probing PCI hardware (bus 00)
[   34.542788] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   34.542802] * this clock source is slow. Consider trying other clock sources
[   34.542897] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[   34.542916] PCI quirk: region 2180-218f claimed by PIIX4 SMB
[   34.542935] PIIX4 devres B PIO at 8040-8043
[   34.542952] PIIX4 devres E PIO at 0140-0147
[   34.542972] PIIX4 devres J PIO at 0370-0371
[   34.543091] Boot video device is 0000:00:08.0
[   34.550341] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   34.550421] PCI: setting IRQ 9 as level-triggered
[   34.550438] PCI: Found IRQ 9 for device 0000:00:0a.0
[   34.550468] PCI: Sharing IRQ 9 with 0000:00:08.1
[   34.550504] PCI: Found IRQ 9 for device 0000:00:0b.0
[   34.550531] PCI: Sharing IRQ 9 with 0000:00:08.0
[   34.552872] NET: Registered protocol family 8
[   34.552892] NET: Registered protocol family 20
[   34.553467] pnp: 00:00: ioport range 0x4d0-0x4d1 has been reserved
[   34.553494] pnp: 00:00: ioport range 0x370-0x371 has been reserved
[   34.553514] pnp: 00:00: ioport range 0x8000-0x804f could not be reserved
[   34.553532] pnp: 00:00: ioport range 0x2180-0x218f has been reserved
[   34.553550] pnp: 00:00: ioport range 0x230-0x233 has been reserved
[   34.558178] PCI: Ignore bogus resource 6 [0:0] of 0000:00:08.0
[   34.558268] PCI: Bus 1, cardbus bridge: 0000:00:0a.0
[   34.558283]   IO window: 00001000-000010ff
[   34.558300]   IO window: 00001400-000014ff
[   34.558318]   PREFETCH window: 10000000-13ffffff
[   34.558335]   MEM window: 14000000-17ffffff
[   34.558351] PCI: Bus 5, cardbus bridge: 0000:00:0a.1
[   34.558364]   IO window: 00001800-000018ff
[   34.558380]   IO window: 00001c00-00001cff
[   34.558396]   PREFETCH window: 18000000-1bffffff
[   34.558413]   MEM window: 1c000000-1fffffff
[   34.558466] PCI: Found IRQ 9 for device 0000:00:0a.0
[   34.558501] PCI: Sharing IRQ 9 with 0000:00:08.1
[   34.558533] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   34.558577] PCI: Assigned IRQ 9 for device 0000:00:0a.1
[   34.558611] PCI: Sharing IRQ 9 with 0000:00:09.0
[   34.558636] PCI: Setting latency timer of device 0000:00:0a.1 to 64
[   34.558770] NET: Registered protocol family 2
[   34.596500] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[   34.597074] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[   34.597328] TCP bind hash table entries: 2048 (order: 2, 16384 bytes)
[   34.597471] TCP: Hash tables configured (established 4096 bind 2048)
[   34.597488] TCP reno registered
[   34.608696] checking if image is initramfs... it is
[   38.950500] Freeing initrd memory: 7012k freed
[   38.953641] audit: initializing netlink socket (disabled)
[   38.953710] audit(1184638580.080:1): initialized
[   38.954895] VFS: Disk quotas dquot_6.5.1
[   38.955035] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   38.955463] io scheduler noop registered
[   38.955490] io scheduler anticipatory registered
[   38.955504] io scheduler deadline registered
[   38.955609] io scheduler cfq registered (default)
[   38.955647] Limiting direct PCI/PCI transfers.
[   38.957128] isapnp: Scanning for PnP cards...
[   39.310920] isapnp: No Plug & Play device found
[   39.750958] Real Time Clock Driver v1.12ac
[   39.751839] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   39.752464] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   39.754775] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[   39.759537] 00:0f: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   39.762048] mice: PS/2 mouse device common for all mice
[   39.770304] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   39.771714] input: Macintosh mouse button emulation as /class/input/input0
[   39.772183] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   39.772214] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   39.773677] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   39.777258] serio: i8042 KBD port at 0x60,0x64 irq 1
[   39.777300] serio: i8042 AUX port at 0x60,0x64 irq 12
[   39.778783] EISA: Probing bus 0 at eisa.0
[   39.778846] Cannot allocate resource for EISA slot 1
[   39.778905] Cannot allocate resource for EISA slot 8
[   39.778918] EISA: Detected 0 cards.
[   39.779373] TCP cubic registered
[   39.779443] NET: Registered protocol family 1
[   39.779591] Using IPI No-Shortcut mode
[   39.779743]   Magic number: 15:211:258
[   39.779830]   hash matches device ttyx0
[   39.782137] Time: tsc clocksource has been installed.
[   39.782978] Freeing unused kernel memory: 328k freed
[   39.806765] input: AT Translated Set 2 keyboard as /class/input/input1
[   42.654341] Capability LSM initialized
[   43.079705] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   47.481186] SCSI subsystem initialized
[   47.627598] libata version 2.20 loaded.
[   47.674290] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   47.674359] PIIX4: chipset revision 1
[   47.674373] PIIX4: not 100% native mode: will probe irqs later
[   47.674405]     ide0: BM-DMA at 0xfcf0-0xfcf7, BIOS settings: hda:DMA, hdb:pio
[   47.674466]     ide1: BM-DMA at 0xfcf8-0xfcff, BIOS settings: hdc:DMA, hdd:pio
[   47.674513] Probing IDE interface ide0...
[   47.811618] usbcore: registered new interface driver usbfs
[   47.811832] usbcore: registered new interface driver hub
[   47.812170] usbcore: registered new device driver usb
[   47.831073] USB Universal Host Controller Interface driver v3.0
[   48.330357] hda: IBM-DARA-209000, ATA DISK drive
[   48.999646] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   48.999938] Probing IDE interface ide1...
[   49.138246] Floppy drive(s): fd0 is 1.44M
[   49.378243] FDC 0 is a post-1991 82077
[   49.734850] hdc: TOSHIBA DVD-ROM SD-C2202, ATAPI CD/DVD-ROM drive
[   50.407248] ide1 at 0x170-0x177,0x376 on irq 15
[   50.422498] PCI: Enabling device 0000:00:07.2 (0000 -> 0001)
[   50.422542] PCI: Assigned IRQ 9 for device 0000:00:07.2
[   50.422625] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   50.424794] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   50.424891] uhci_hcd 0000:00:07.2: irq 9, io base 0x0000fcc0
[   50.429088] usb usb1: configuration #1 chosen from 1 choice
[   50.430938] hub 1-0:1.0: USB hub found
[   50.431028] hub 1-0:1.0: 2 ports detected
[   50.504501] hda: max request size: 128KiB
[   50.535134] hub 1-0:1.0: over-current change on port 2
[   50.840502] hda: 12594960 sectors (6448 MB) w/418KiB Cache, CHS=13328/15/63, UDMA(33)
[   50.840543] hda: cache flushes not supported
[   50.840745]  hda: hda1 hda2 <<6>usb 1-2: new full speed USB device using uhci_hcd and address 2
[   50.885239]  hda5 >
[   50.950453] hdc: ATAPI 24X DVD-ROM drive, 128kB Cache, UDMA(33)
[   50.950499] Uniform CD-ROM driver Revision: 3.20
[   51.062318] usb 1-2: configuration #1 chosen from 1 choice
[   51.889745] Attempting manual resume
[   51.889771] swsusp: Resume From Partition 3:5
[   51.889782] PM: Checking swsusp image.
[   51.890324] PM: Resume from disk failed.
[   52.090448] EXT3-fs: INFO: recovery required on readonly filesystem.
[   52.090475] EXT3-fs: write access will be enabled during recovery.
[   60.552870] kjournald starting.  Commit interval 5 seconds
[   60.552954] EXT3-fs: recovery complete.
[   60.563227] EXT3-fs: mounted filesystem with ordered data mode.
[  103.156449] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[  103.303685] Yenta: CardBus bridge found at 0000:00:0a.0 [104d:8042]
[  103.439882] Yenta: ISA IRQ mask 0x0cb8, PCI irq 9
[  103.439947] Socket status: 30000006
[  103.440739] Yenta: CardBus bridge found at 0000:00:0a.1 [104d:8042]
[  103.568835] Yenta: ISA IRQ mask 0x0cb8, PCI irq 9
[  103.568857] Socket status: 30000006
[  104.425296] input: PC Speaker as /class/input/input2
[  104.432127] input: PS/2 Mouse as /class/input/input3
[  104.449196] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[  106.533606] parport: PnPBIOS parport detected.
[  106.533697] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  106.751247] irda_init()
[  106.751330] NET: Registered protocol family 23
[  106.847052] found SMC SuperIO Chip (devid=0x09 rev=01 base=0x0370): FDC37N958FR
[  106.847074] Revision higher than expected
[  107.494022] PCI: Found IRQ 9 for device 0000:00:08.1
[  107.494076] PCI: Sharing IRQ 9 with 0000:00:0a.0
[  107.494137] nm256: found card signature in video RAM: 0x27ec00
[  107.494169] nm256: Mapping port 1 from 0x2709a0 - 0x27ec00
[  107.838549] drivers/usb/net/kaweth.c: Downloading firmware...
[  108.306380] drivers/usb/net/kaweth.c: Firmware loaded.  I'll be back...
[  108.306451] kaweth: probe of 1-2:1.0 failed with error -5
[  108.306505] usbcore: registered new interface driver kaweth
[  108.406760] cs: IO port probe 0x100-0x3af: excluding 0x140-0x147
[  108.408245] cs: IO port probe 0x3e0-0x4ff: clean.
[  108.409090] cs: IO port probe 0x820-0x8ff: clean.
[  108.409883] cs: IO port probe 0xc00-0xcf7: clean.
[  108.411898] cs: IO port probe 0xa00-0xaff: clean.
[  108.954136] usb 1-2: USB disconnect, address 2
[  109.173551] cs: IO port probe 0x100-0x3af: excluding 0x140-0x147
[  109.175100] cs: IO port probe 0x3e0-0x4ff: clean.
[  109.175947] cs: IO port probe 0x820-0x8ff: clean.
[  109.176738] cs: IO port probe 0xc00-0xcf7: clean.
[  109.178893] cs: IO port probe 0xa00-0xaff: clean.
[  110.807705] fuse init (API version 7.8)
[  110.976278] lp0: using parport0 (interrupt-driven).
[  111.457064] Adding 329292k swap on /dev/hda5.  Priority:-1 extents:1 across:329292k
[  111.856859] EXT3 FS on hda1, internal journal
[  114.272250] usb 1-2: new full speed USB device using uhci_hcd and address 3
[  114.455762] usb 1-2: configuration #1 chosen from 1 choice
[  114.469160] drivers/usb/net/kaweth.c: Firmware present in device.
[  114.471265] drivers/usb/net/kaweth.c: Statistics collection: 13fbffff
[  114.471292] drivers/usb/net/kaweth.c: Multicast filter limit: 80
[  114.471308] drivers/usb/net/kaweth.c: MTU: 1514
[  114.471328] drivers/usb/net/kaweth.c: Read MAC address 08:00:46:02:5c:20
[  114.474689] drivers/usb/net/kaweth.c: kaweth interface created at eth0
[  116.214239] NET: Registered protocol family 17
[  116.252492] drivers/usb/net/kaweth.c: Failed to set Rx mode: -16
[  147.584720] drivers/usb/net/kaweth.c: Failed to set Rx mode: -16
[  158.679464] NET: Registered protocol family 10
[  158.680180] lo: Disabled Privacy Extensions
[  158.688724] drivers/usb/net/kaweth.c: Failed to set Rx mode: -16
[  163.880946] ieee80211_crypt: registered algorithm 'NULL'
[  163.933651] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  163.933675] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  164.552288] ndiswrapper version 1.47 loaded (smp=yes)
[  164.637692] usbcore: registered new interface driver ndiswrapper
[  168.861079] eth0: no IPv6 routers present
[  171.216579] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[  171.217699] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[  171.220999] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[  171.222538] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[  192.118167] capifs: Rev 1.1.2.3
[  196.893225] ppdev: user-space parallel port driver
[  217.171914] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  241.013200] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[  241.623284] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  241.649750] NFSD: starting 90-second grace period
[  245.735795] Bluetooth: Core ver 2.11
[  245.736126] NET: Registered protocol family 31
[  245.736147] Bluetooth: HCI device and connection manager initialized
[  245.736165] Bluetooth: HCI socket layer initialized
[  246.105741] Bluetooth: L2CAP ver 2.8
[  246.105767] Bluetooth: L2CAP socket layer initialized
[  246.176734] Bluetooth: RFCOMM socket layer initialized
[  246.176813] Bluetooth: RFCOMM TTY layer initialized
[  246.176829] Bluetooth: RFCOMM ver 1.8
[  494.007610] pccard: CardBus card inserted into slot 0
[  494.992340] ndiswrapper: driver mrv8k51 (D-Link,12/21/2003,2.2.0.19) loaded
[  494.993354] PCI: Enabling device 0000:01:00.0 (0000 -> 0002)
[  494.993459] PCI: Setting latency timer of device 0000:01:00.0 to 64
[  494.999095] ndiswrapper: using IRQ 9
[  510.666398] wlan0: ethernet device 00:0d:88:e9:de:f5 using NDIS driver: mrv8k51, version: 0x202000b, NDIS version: 0x500, vendor: 'Marvell 802.11 Driver', 11AB:1FA6.5.conf
[  510.666481] ndiswrapper (set_encr_mode:673): setting encryption mode to 6 failed (C00000BB)
[  510.666517] wlan0: encryption modes supported: WEP; TKIP with WPA
[  539.785250] drivers/usb/net/kaweth.c: Failed to set Rx mode: -16
[  542.864466] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  542.955335] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  553.626775] wlan0: no IPv6 routers present
[ 4240.597542] drivers/usb/net/kaweth.c: Failed to set Rx mode: -16
[ 4271.877580] drivers/usb/net/kaweth.c: Failed to set Rx mode: -16
[ 4276.471476] drivers/usb/net/kaweth.c: Failed to set Rx mode: -16
[ 4815.479285] drivers/usb/net/kaweth.c: Failed to set Rx mode: -16
[ 4815.579302] drivers/usb/net/kaweth.c: Failed to set Rx mode: -16
[ 4819.273937] drivers/usb/net/kaweth.c: Failed to set Rx mode: -16
[ 4829.278376] eth0: no IPv6 routers present.

---

### Post by Mr. C. on 2007-07-18
Sorry, I had two arguments to ethtool backwards.  It should be:

```
ethtool  -s  eth0  speed 10 duplex half autoneg off
```

Go ahead and try again.

Your driver is unable to set the receive mode on the NIC for some reason; its not clear why.

MrC

---

### Post by Dwiman89 on 2007-07-18
Um, this is what i got for that onek# ethtool  -s  eth0  speed 10 duplex half autoneg off
Cannot get current device settings: Operation not supported
  not setting speed
  not setting duplex
  not setting autoneg

---

### Post by Mr. C. on 2007-07-18
I looked at the driver again - it does not appear to support setting options via ethtool.  Sorry about the waste of time.

I see two error messages that I don't know how to resolve:

```
kaweth: probe of 1-2:1.0 failed with error -5
drivers/usb/net/kaweth.c: Failed to set Rx mode: -16
```

The first indicates that a device detection problem (a probe).  The second is a failure to set the receive mode, as I mentioned earlier.

The driver for this card has been around for a long time; I don't know anything about its status, and not much about USB ethernet drivers.  This may be a problem best posted on the linux kernel list, as there isn't much information about these issues that I can find, and the specialists there might guide you in the right direction.

I told you it would be fairly easy to get your two networks operational; it typically is. Unfortunately, you have one of those devices that does not seem to work out of the box, or at least not with this kernel setup.

Sorry I couldn't be of more help.
MrC

---

