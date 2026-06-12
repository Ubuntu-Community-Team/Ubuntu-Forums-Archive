---
title: "wireless card detection problem"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by MEGAMANULTIMATE on 2007-12-11
I'm using a Dell XPS M1210.

I was forced recently to reinstall linux, and no problems seemed to persist through the process. However, my wireless card has not been detected, and I have no idea why. It was working before, but has not since the reinstallation. Has anyone else had this happen to them? Please help if possible.

---

### Post by Original Brownster on 2007-12-12
> **MEGAMANULTIMATE said:**
> I'm using a Dell XPS M1210.

I was forced recently to reinstall linux, and no problems seemed to persist through the process. However, my wireless card has not been detected, and I have no idea why. It was working before, but has not since the reinstallation. Has anyone else had this happen to them? Please help if possible.

Hi,
Have you installed Gutsy Gibbon and was this what you ran before?


I take it that if you run the gui tool network manager you see no wireless connection?


plz post the output from the following commands from a terminal:

$ lshw -C network
$ lsmod
$ ifconfig -a 
$ iwconfig
$ netstat -rn

are you using a wired ethernet in the meantime on this laptop?

---

### Post by MEGAMANULTIMATE on 2007-12-12
No, I've been running Feisty Fawn before, and that's what I reinstalled. I'd upgrade to Gutsy Gibbon, but I heard that I should wait a while. Does the information you posted still apply?

---

### Post by MEGAMANULTIMATE on 2007-12-12
Here's the first command: 

 *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:dcfff000-dcffffff irq:17
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:3e:1a:33
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=10.224.67.152 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:dcbfe000-dcbfffff irq:17

---

### Post by MEGAMANULTIMATE on 2007-12-12
And the second:

Module                  Size  Used by
usb_storage            72256  0 
libusual               17936  1 usb_storage
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
acpi_cpufreq           10056  0 
cpufreq_ondemand        9228  2 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
pcc_acpi               13184  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
video                  16388  0 
ac                      6020  0 
battery                10756  0 
button                  8720  0 
asus_acpi              17308  0 
dock                   10268  0 
backlight               7040  1 asus_acpi
container               5248  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
ipv6                  268960  10 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
joydev                 10816  0 
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
af_packet              23816  2 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sdhci                  18700  0 
ipw3945               118816  1 
nvidia               4713780  22 
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mmc_core               26756  1 sdhci
i2c_core               22656  2 i2c_ec,nvidia
ieee80211              34760  1 ipw3945
ieee80211_crypt         7040  1 ieee80211
serio_raw               7940  0 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
pcspkr                  4224  0 
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
psmouse                38920  0 
intel_agp              26140  1 
agpgart                35400  2 nvidia,intel_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  2 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  4 
generic                 5124  0 [permanent]
ata_generic             9092  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
b44                    28044  0 
mii                     6528  1 b44
ehci_hcd               34188  0 
ata_piix               15492  3 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  6 usb_storage,sbp2,sg,sr_mod,sd_mod,libata
uhci_hcd               25360  0 
usbcore               134280  5 usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

---

### Post by MEGAMANULTIMATE on 2007-12-12
The third:

eth0      Link encap:Ethernet  HWaddr 00:15:C5:3E:1A:33  
          inet addr:10.224.67.152  Bcast:10.224.67.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe3e:1a33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:335173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:129661745 (123.6 MiB)  TX bytes:5642369 (5.3 MiB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---

### Post by MEGAMANULTIMATE on 2007-12-12
The fourth:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by MEGAMANULTIMATE on 2007-12-12
And the last one:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.224.67.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         10.224.67.1     0.0.0.0         UG        0 0          0 eth0

---

### Post by Original Brownster on 2007-12-12
Hi,
After a bit of searching it seems that this chipset  and driver are well supported out of the box, there are a a few bugs logged against this driver but none that identify with this problem. 
The fact that the driver is loaded but you still do not see the device using 'iwconfig' is well strange.

are there any entries in /var/log/syslog pertaining to this device, either 'ipw3945' the driver or '3945ABG' the chipset?

I assume you are using the restricted driver?

What happens if you restart the network:
$sudo /etc/init.d/networking restart
does the device appear?

Try unloading the module ipw3945 and re-inserting it:
$sudo rmmod ipw3945
$sudo modprobe ipw3945

---

### Post by MEGAMANULTIMATE on 2007-12-13
Hello.

Thanks for your help. The commands didn't work, but here's something interesting after I did the sudo rmmod ipw3945 command:

ERROR: Module ipw3945 is in use

On top of that, everytime I start the comp, I'm taken to a dual boot prompt between both the Ubuntu I'm using now and the one I used to use. Is it possible the wireless card won't be detected because the old distribution is using it?

---

### Post by Original Brownster on 2007-12-14
> **MEGAMANULTIMATE said:**
> Hello.

Thanks for your help. The commands didn't work, but here's something interesting after I did the sudo rmmod ipw3945 command:

ERROR: Module ipw3945 is in use

On top of that, everytime I start the comp, I'm taken to a dual boot prompt between both the Ubuntu I'm using now and the one I used to use. Is it possible the wireless card won't be detected because the old distribution is using it?

Hi,

It still looks to me that there is a problem with the driver but try the following:

The module has been claimed and in use, try 
$sudo /etc/init.d/networking stop
$sudo rmmod ipw3945

look at the available net interfaces

$ifconfig
$iwconfig

now

$sudo modprobe ipw3945

$ifconfig
$iwconfig

do you see a new interface ? 

look at the last few lines of the command
$dmesg
and
$tail /var/log/syslog

and see if there are any errors, or any clues as to what's happening.

Your old distro cannot use it as only one system can run at a time.

---

### Post by MEGAMANULTIMATE on 2007-12-15
Hello again. That didn't work, either. No new interfaces came up at all. 

Here's what was in terminal:
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Detected 2161.499 MHz processor.
[    5.456742] Built 1 zonelists.  Total pages: 519830
[    5.456745] Kernel command line: root=UUID=a7c9dd05-0d86-4b2e-8998-72b1f0eac898 ro quiet splash
[    5.456870] mapped APIC to ffffd000 (fee00000)
[    5.456872] mapped IOAPIC to ffffc000 (fec00000)
[    5.456874] Enabling fast FPU save and restore... done.
[    5.456876] Enabling unmasked SIMD FPU exception support... done.
[    5.456883] Initializing CPU#0
[    5.456945] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    5.458824] Console: colour VGA+ 80x25
[    5.459072] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    5.459379] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    5.535972] Memory: 2066648k/2095692k available (1993k kernel code, 27728k reserved, 900k data, 328k init, 1178188k highmem)
[    5.535981] virtual kernel memory layout:
[    5.535982]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    5.535983]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    5.535984]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    5.535985]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    5.535986]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    5.535987]       .data : 0xc02f2429 - 0xc03d36d4   ( 900 kB)
[    5.535988]       .text : 0xc0100000 - 0xc02f2429   (1993 kB)
[    5.535991] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    5.612698] Calibrating delay using timer specific routine.. 4327.12 BogoMIPS (lpj=8654244)
[    5.612733] Security Framework v1.0.0 initialized
[    5.612740] SELinux:  Disabled at boot.
[    5.612755] Mount-cache hash table entries: 512
[    5.612875] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[    5.612882] monitor/mwait feature present.
[    5.612883] using mwait in idle threads.
[    5.612887] CPU: L1 I cache: 32K, L1 D cache: 32K
[    5.612889] CPU: L2 cache: 2048K
[    5.612891] CPU: Physical Processor ID: 0
[    5.612893] CPU: Processor Core ID: 0
[    5.612895] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
[    5.612903] Compat vDSO mapped to ffffe000.
[    5.612907] Remapping vsyscall page to ffffe000
[    5.612917] Checking 'hlt' instruction... OK.
[    5.628770] SMP alternatives: switching to UP code
[    5.629097] Early unpacking initramfs... done
[    5.887105] ACPI: Core revision 20060707
[    5.903362] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    5.905530] CPU0: Intel Genuine Intel(R) CPU           T2600  @ 2.16GHz stepping 08
[    5.905548] SMP alternatives: switching to SMP code
[    5.905654] Booting processor 1/1 eip 3000
[    8.113646] Initializing CPU#1
[    8.193061] Calibrating delay using timer specific routine.. 4322.84 BogoMIPS (lpj=8645697)
[    8.193067] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[    8.193071] monitor/mwait feature present.
[    8.193074] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.193075] CPU: L2 cache: 2048K
[    8.193077] CPU: Physical Processor ID: 0
[    8.193078] CPU: Processor Core ID: 1
[    8.193080] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
[    5.996457] CPU1: Intel Genuine Intel(R) CPU           T2600  @ 2.16GHz stepping 08
[    5.996476] Total of 2 processors activated (8649.97 BogoMIPS).
[    5.996648] ENABLING IO-APIC IRQs
[    5.996838] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    6.143839] checking TSC synchronization across 2 CPUs: 
[    0.000001] CPU#0 had -1100480 usecs TSC skew, fixed it up.
[    0.000003] CPU#1 had 1100480 usecs TSC skew, fixed it up.
[    0.003989] Brought up 2 CPUs
[    0.072115] migration_cost=42
[    0.072354] Booting paravirtualized kernel on bare hardware
[    0.072432] Time: 23:48:22  Date: 11/13/107
[    0.072457] NET: Registered protocol family 16
[    0.072530] EISA bus registered
[    0.072534] ACPI: bus type pci registered
[    0.099096] PCI: PCI BIOS revision 2.10 entry at 0xfb4d6, last bus=14
[    0.099098] PCI: Using configuration type 1
[    0.099099] Setting up standard PCI resources
[    0.123390] ACPI: Interpreter enabled
[    0.123393] ACPI: Using IOAPIC for interrupt routing
[    0.123910] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.123916] PCI: Probing PCI hardware (bus 00)
[    0.123990] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.135732] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.135736] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.135949] Boot video device is 0000:01:00.0
[    0.136982] PCI: Transparent bridge - 0000:00:1e.0
[    0.137065] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.154192] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *4
[    0.154400] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
[    0.154607] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    0.154814] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[    0.155021] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.155232] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.155444] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.155652] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.155990] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.156922] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.157136] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.157332] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.157589] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.157942] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.157952] pnp: PnP ACPI init
[    0.185183] pnp: PnP ACPI: found 11 devices
[    0.185186] PnPBIOS: Disabled by ACPI PNP
[    0.185223] PCI: Using ACPI for IRQ routing
[    0.185225] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.229994] NET: Registered protocol family 8
[    0.229995] NET: Registered protocol family 20
[    0.245376] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.245379] pnp: 00:02: ioport range 0x1000-0x1005 could not be reserved
[    0.245381] pnp: 00:02: ioport range 0x1008-0x100f could not be reserved
[    0.245386] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.245388] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
[    0.245390] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
[    0.245392] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
[    0.245395] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.245397] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.245403] pnp: 00:08: ioport range 0xc80-0xcff could not be reserved
[    0.245405] pnp: 00:08: ioport range 0x910-0x91f has been reserved
[    0.245407] pnp: 00:08: ioport range 0x920-0x92f has been reserved
[    0.245409] pnp: 00:08: ioport range 0x930-0x97f has been reserved
[    0.245649] PCI: Bridge: 0000:00:01.0
[    0.245650]   IO window: disabled.
[    0.245654]   MEM window: dd000000-dfefffff
[    0.245657]   PREFETCH window: c0000000-cfffffff
[    0.245660] PCI: Bridge: 0000:00:1c.0
[    0.245661]   IO window: disabled.
[    0.245666]   MEM window: disabled.
[    0.245670]   PREFETCH window: disabled.
[    0.245675] PCI: Bridge: 0000:00:1c.1
[    0.245677]   IO window: disabled.
[    0.245682]   MEM window: dcf00000-dcffffff
[    0.245687]   PREFETCH window: disabled.
[    0.245692] PCI: Bridge: 0000:00:1c.3
[    0.245695]   IO window: e000-efff
[    0.245700]   MEM window: dcc00000-dcefffff
[    0.245705]   PREFETCH window: d0000000-d01fffff
[    0.245711] PCI: Bridge: 0000:00:1e.0
[    0.245712]   IO window: disabled.
[    0.245718]   MEM window: dcb00000-dcbfffff
[    0.245722]   PREFETCH window: disabled.
[    0.245737] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.245741] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.245763] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.245768] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.245791] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    0.245796] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.245819] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
[    0.245824] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.245838] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.245862] NET: Registered protocol family 2
[    0.287560] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.287649] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.288226] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.288523] TCP: Hash tables configured (established 131072 bind 65536)
[    0.288525] TCP reno registered
[    0.299612] checking if image is initramfs... it is
[    0.811673] Freeing initrd memory: 6791k freed
[    0.811833] Simple Boot Flag at 0x79 set to 0x1
[    0.812225] audit: initializing netlink socket (disabled)
[    0.812240] audit(1197589702.584:1): initialized
[    0.812323] highmem bounce pool size: 64 pages
[    0.812397] VFS: Disk quotas dquot_6.5.1
[    0.812414] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.812457] io scheduler noop registered
[    0.812459] io scheduler anticipatory registered
[    0.812461] io scheduler deadline registered
[    0.812471] io scheduler cfq registered (default)
[    0.812701] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.812731] assign_interrupt_mode Found MSI capability
[    0.812733] Allocate Port Service[0000:00:01.0:pcie00]
[    0.812807] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.812860] assign_interrupt_mode Found MSI capability
[    0.812863] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.812891] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.812998] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.813051] assign_interrupt_mode Found MSI capability
[    0.813053] Allocate Port Service[0000:00:1c.1:pcie00]
[    0.813079] Allocate Port Service[0000:00:1c.1:pcie02]
[    0.813187] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.813240] assign_interrupt_mode Found MSI capability
[    0.813242] Allocate Port Service[0000:00:1c.3:pcie00]
[    0.813267] Allocate Port Service[0000:00:1c.3:pcie02]
[    0.813421] isapnp: Scanning for PnP cards...
[    1.167293] isapnp: No Plug & Play device found
[    1.186073] Real Time Clock Driver v1.12ac
[    1.186392] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.186908] mice: PS/2 mouse device common for all mice
[    1.187357] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.187478] input: Macintosh mouse button emulation as /class/input/input0
[    1.187507] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.187510] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.187729] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.190875] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.190878] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.191202] EISA: Probing bus 0 at eisa.0
[    1.191264] EISA: Mainboard H__FFFF detected.
[    1.191292] Cannot allocate resource for EISA slot 1
[    1.191321] EISA: Detected 0 cards.
[    1.194266] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.221357] TCP cubic registered
[    1.221365] NET: Registered protocol family 1
[    1.221385] Starting balanced_irq
[    1.221391] Using IPI No-Shortcut mode
[    1.221481] ACPI: (supports S0 S3 S4 S5)
[    1.221520]   Magic number: 3:243:858
[    1.221596]   hash matches device ptysd
[    1.221749] Freeing unused kernel memory: 328k freed
[    1.221992] Time: tsc clocksource has been installed.
[    2.392930] Capability LSM initialized
[    2.422342] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    2.422485] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    2.422650] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.422654] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.422994] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.423124] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    2.423318] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.423322] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.016000] ACPI: Thermal Zone [THM] (57 C)
[    3.024000] Time: acpi_pm clocksource has been installed.
[    3.336000] usbcore: registered new interface driver usbfs
[    3.336000] usbcore: registered new interface driver hub
[    3.336000] usbcore: registered new device driver usb
[    3.340000] USB Universal Host Controller Interface driver v3.0
[    3.340000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
[    3.340000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.340000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.340000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.340000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000bf80
[    3.340000] usb usb1: configuration #1 chosen from 1 choice
[    3.340000] hub 1-0:1.0: USB hub found
[    3.340000] hub 1-0:1.0: 2 ports detected
[    3.352000] ieee1394: Initialized config rom entry `ip1394'
[    3.364000] SCSI subsystem initialized
[    3.392000] libata version 2.20 loaded.
[    3.444000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
[    3.444000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.444000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.444000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.444000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000bf60
[    3.444000] usb usb2: configuration #1 chosen from 1 choice
[    3.444000] hub 2-0:1.0: USB hub found
[    3.444000] hub 2-0:1.0: 2 ports detected
[    3.548000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
[    3.548000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.548000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.548000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.548000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000bf40
[    3.548000] usb usb3: configuration #1 chosen from 1 choice
[    3.548000] hub 3-0:1.0: USB hub found
[    3.548000] hub 3-0:1.0: 2 ports detected
[    3.652000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 22
[    3.652000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.652000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.652000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.652000] uhci_hcd 0000:00:1d.3: irq 22, io base 0x0000bf20
[    3.652000] usb usb4: configuration #1 chosen from 1 choice
[    3.652000] hub 4-0:1.0: USB hub found
[    3.652000] hub 4-0:1.0: 2 ports detected
[    3.756000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 18
[    3.764000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[    3.764000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.764000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.764000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.764000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.764000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.764000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa80000
[    3.768000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.768000] usb usb5: configuration #1 chosen from 1 choice
[    3.768000] hub 5-0:1.0: USB hub found
[    3.768000] hub 5-0:1.0: 8 ports detected
[    3.816000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[dcbfd800-dcbfdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.872000] b44.c:v1.01 (Jun 16, 2006)
[    3.872000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[    3.872000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:15:c5:3e:1a:33
[    3.872000] ata_piix 0000:00:1f.2: version 2.10ac1
[    3.872000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    3.872000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[    3.872000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    3.876000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[    3.876000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    3.876000] scsi0 : ata_piix
[    4.040000] ata1.00: ata_hpa_resize 1: sectors = 192426570, hpa_sectors = 195371568
[    4.040000] ata1.00: Host Protected Area detected.
[    4.040000]      current size : 192426570 sectors (98522 MB)
[    4.040000]      native  size : 195371568 sectors (100030 MB)
[    4.192000] ata1.00: SET of native returned 0, expected 195371568
[    4.192000] ata1.00: ATA-7: ST910021AS, 8.02, max UDMA/133
[    4.192000] ata1.00: 192426570 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    4.264000] ata1.00: ata_hpa_resize 1: sectors = 192426570, hpa_sectors = 195371568
[    4.264000] ata1.00: Host Protected Area detected.
[    4.264000]      current size : 192426570 sectors (98522 MB)
[    4.264000]      native  size : 195371568 sectors (100030 MB)
[    4.416000] ata1.00: SET of native returned 0, expected 195371568
[    4.416000] ata1.00: configured for UDMA/133
[    4.416000] scsi1 : ata_piix
[    4.736000] ata2.00: ATAPI, max UDMA/33
[    4.900000] ata2.00: configured for UDMA/33
[    4.900000] scsi 0:0:0:0: Direct-Access     ATA      ST910021AS       8.02 PQ: 0 ANSI: 5
[    4.900000] scsi 1:0:0:0: CD-ROM            SONY     DVD+-RW DW-Q58A  UDS2 PQ: 0 ANSI: 5
[    4.912000] SCSI device sda: 192426570 512-byte hdwr sectors (98522 MB)
[    4.912000] sda: Write Protect is off
[    4.912000] sda: Mode Sense: 00 3a 00 00
[    4.912000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.912000] SCSI device sda: 192426570 512-byte hdwr sectors (98522 MB)
[    4.912000] sda: Write Protect is off
[    4.912000] sda: Mode Sense: 00 3a 00 00
[    4.912000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.912000]  sda: sda1 sda2 < sda5 sda6 > sda3
[    4.964000] sd 0:0:0:0: Attached scsi disk sda
[    4.968000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.968000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.968000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.968000] Uniform CD-ROM driver Revision: 3.20
[    4.972000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.092000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[364fc0002152ad41]
[    5.196000] Attempting manual resume
[    5.196000] swsusp: Resume From Partition 8:6
[    5.196000] PM: Checking swsusp image.
[    5.196000] PM: Resume from disk failed.
[    5.224000] kjournald starting.  Commit interval 5 seconds
[    5.224000] EXT3-fs: mounted filesystem with ordered data mode.
[   15.732000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.736000] agpgart: Detected an Intel 945GM Chipset.
[   15.752000] agpgart: AGP aperture is 256M @ 0x0
[   15.752000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.764000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.824000] iTCO_vendor_support: vendor-support=0
[   15.824000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   15.824000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   15.824000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.852000] intel_rng: FWH not detected
[   16.048000] input: PC Speaker as /class/input/input2
[   16.084000] sdhci: Secure Digital Host Controller Interface driver
[   16.084000] sdhci: Copyright(c) Pierre Ossman
[   16.084000] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
[   16.084000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
[   16.084000] mmc0: SDHCI at 0xdcbfd400 irq 23 DMA
[   16.144000] ieee80211_crypt: registered algorithm 'NULL'
[   16.172000] nvidia: module license 'NVIDIA' taints kernel.
[   16.428000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.428000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   16.428000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   16.492000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.492000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.544000] NET: Registered protocol family 17
[   16.572000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   16.572000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   16.572000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   16.572000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   16.572000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   16.596000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04713/0x200000
[   16.632000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   16.768000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
[   16.768000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   17.352000] fuse init (API version 7.8)
[   17.432000] lp: driver loaded but no devices found
[   17.468000] Adding 417616k swap on /dev/disk/by-uuid/b445dff8-13ce-49b6-a2e2-30ccf80dbbff.  Priority:-1 extents:1 across:417616k
[   17.536000] EXT3 FS on sda3, internal journal
[   18.064000] b44: eth0: Link is up at 100 Mbps, full duplex.
[   18.064000] b44: eth0: Flow control is off for TX and off for RX.
[   18.460000] ipw3945: Radio Frequency Kill Switch is On:
[   18.460000] Kill switch must be turned off for wireless networking to work.
[   21.276000] NET: Registered protocol family 10
[   21.276000] lo: Disabled Privacy Extensions
[   22.836000] ibm_acpi: ec object not found
[   22.860000] No dock devices found.
[   22.872000] input: Lid Switch as /class/input/input4
[   22.872000] ACPI: Lid Switch [LID]
[   22.872000] input: Power Button (CM) as /class/input/input5
[   22.872000] ACPI: Power Button (CM) [PBTN]
[   22.872000] input: Sleep Button (CM) as /class/input/input6
[   22.872000] ACPI: Sleep Button (CM) [SBTN]
[   22.936000] ACPI: Battery Slot [BAT0] (battery present)
[   22.948000] ACPI: AC Adapter [AC] (on-line)
[   22.968000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   22.968000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   22.968000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   22.972000] Using specific hotkey driver
[   23.088000] pcc_acpi: loading...
[   28.340000] ppdev: user-space parallel port driver
[   30.320000] apm: BIOS not found.
[   30.640000] Bluetooth: Core ver 2.11
[   30.640000] NET: Registered protocol family 31
[   30.640000] Bluetooth: HCI device and connection manager initialized
[   30.640000] Bluetooth: HCI socket layer initialized
[   30.700000] Bluetooth: L2CAP ver 2.8
[   30.700000] Bluetooth: L2CAP socket layer initialized
[   30.864000] Bluetooth: RFCOMM socket layer initialized
[   30.864000] Bluetooth: RFCOMM TTY layer initialized
[   30.864000] Bluetooth: RFCOMM ver 1.8
[   42.600000] eth0: no IPv6 routers present
[58582.136000] kjournald starting.  Commit interval 5 seconds
[58582.136000] EXT3 FS on sda1, internal journal
[58582.136000] EXT3-fs: mounted filesystem with ordered data mode.
[70352.684000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[70352.880000] usb 1-2: configuration #1 chosen from 1 choice
[70353.044000] usbcore: registered new interface driver hiddev
[70353.048000] input: Logitech Logitech USB Speaker as /class/input/input7
[70353.048000] input: USB HID v1.00 Device [Logitech Logitech USB Speaker] on usb-0000:00:1d.0-2
[70353.048000] usbcore: registered new interface driver usbhid
[70353.048000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[70353.152000] usbcore: registered new interface driver snd-usb-audio
[70353.168000] usbcore: registered new interface driver xpad
[70353.168000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[72569.120000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[72572.120000] b44: eth0: Link is up at 100 Mbps, full duplex.
[72572.120000] b44: eth0: Flow control is off for TX and off for RX.
[72572.120000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[72590.016000] eth0: no IPv6 routers present
matthew@matthew-laptop:~$ tail /var/log/syslog
Dec 15 18:53:57 matthew-laptop avahi-daemon[5042]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.3.193.
Dec 15 18:53:57 matthew-laptop avahi-autoipd(eth0)[14235]: SIOCSIFFLAGS failed: Permission denied
Dec 15 18:53:57 matthew-laptop avahi-autoipd(eth0)[14235]: Callout STOP, address 169.254.3.193 on interface eth0
Dec 15 18:53:57 matthew-laptop NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid. 
Dec 15 18:53:57 matthew-laptop NetworkManager: <information>^IDeactivating device eth0. 
Dec 15 18:53:57 matthew-laptop avahi-daemon[5042]: Withdrawing address record for fe80::215:c5ff:fe3e:1a33 on eth0.
Dec 15 18:53:57 matthew-laptop avahi-daemon[5042]: Withdrawing address record for 169.254.3.193 on eth0.
Dec 15 18:53:57 matthew-laptop avahi-autoipd(eth0)[14236]: client: RTNETLINK answers: No such process
Dec 15 18:53:57 matthew-laptop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Dec 15 18:53:57 matthew-laptop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
matthew@matthew-laptop:~$ 

I think that was all of it.

---

### Post by Original Brownster on 2007-12-16
> [ 18.460000] ipw3945: Radio Frequency Kill Switch is On:
[ 18.460000] Kill switch must be turned off for wireless networking to work.

That looks like your problem. I had a quick look and it seems your laptop will have a 'kill switch' you need to switch the wireless on.

I think the key combination Fn - F2 switches wireless on / off ?

---

### Post by MEGAMANULTIMATE on 2007-12-16
I tried the key combo you advised, but nothing has happened, even after a couple of reboots. Is there something else I need to do?

---

### Post by Original Brownster on 2007-12-16
Hi, I checked another thread and they suggest there is a small switch on the outside of the laptop?

---

### Post by MEGAMANULTIMATE on 2007-12-16
Wow, that was it. I'm very embarrassed. Thanks so much for bearing with me through this.

---

### Post by jfank on 2007-12-16
I was going to post on here, because I can't get my wireless to work either.  I stopped using my Sony laptop which the wireless was working on and switched to my Dell and it wasn't working, and after I read this topic it solved my problem.  Such a simple fix to.

---

### Post by Original Brownster on 2007-12-17
Hi,
Well I'm glad its cured the problem, sometimes a solution is so easy it's overlooked. My laptop does not have such a switch it was only the syslog message that gave it away!

---

### Post by jfank on 2007-12-17
Yeah that is always overlooked if it is the easiest solution.  I had to hit the FN+F2 keys several times just to get it to work correctly, but it finally worked.  Way to easy of a solution.  It is always helpful when there is a post that will show you the simple fix, but we all know that sometimes there is more to a fix than a simply flip of a switch or pushing 2 keys on the keyboard. lol.  Well ya'll have a good one, and lets keep the helpful topics flowing.

---

