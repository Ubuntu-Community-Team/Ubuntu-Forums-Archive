---
title: "Is my wireless recognized?"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by jodef on 2008-11-16
I recently installed ubuntu 8.10 on my Dell Inspiron 9400 while I am a bit familiar with linux wireless networking new to me; I am trying to determine whether my wireless card is recognized and working.

I searched the forums and have posted some of the info I have seen requested in previous posts:

lshw -C Network

```
 [B]*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:23:fd:85
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg[/B]
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:4b:04:b2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.2 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0e:b3:2f:24:ba:c3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

iwlist scan

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.
```

ifconfig wlan0

```
wlan0     Link encap:Ethernet  HWaddr 00:13:02:23:fd:85  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

One last thing the wifi light on the laptop is on.

Any help would be greatly appreciated. Thanks.

---

### Post by iponeverything on 2008-11-16
It looks like it almost wanted to work out of the box.

There is probably a conflicting module loading. Post the output of:
```
lsmod 

```

Just found this thread that might help you!

[http://ubuntuforums.org/showthread.php?t=820297](http://ubuntuforums.org/showthread.php?t=820297)

---

### Post by jodef on 2008-11-16
My lsmod looks as follows:

```
Module                  Size  Used by
ipv6                  263972  14 
i915                   38144  3 
drm                    86056  4 i915
af_packet              25728  4 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
vboxdrv                72472  0 
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
container              11520  0 
pci_slot               12552  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
arc4                    9984  2 
snd_mixer_oss          22784  1 snd_pcm_oss
ecb                    10880  2 
dcdbas                 15008  0 
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
crypto_blkcipher       25476  1 ecb
evdev                  17696  13 
psmouse                45200  0 
pcspkr                 10624  0 
serio_raw              13444  0 
snd_seq_dummy          10884  0 
iwl3945                98804  0 
rfkill                 17176  2 iwl3945
mac80211              216820  1 iwl3945
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
sdhci_pci              15360  0 
led_class              12164  1 iwl3945
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
sdhci                  23940  1 sdhci_pci
cfg80211               32392  2 iwl3945,mac80211
mmc_core               58268  1 sdhci
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  25104  0 
output                 11008  1 video
iTCO_wdt               18596  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_vendor_support    11652  1 iTCO_wdt
ac                     12292  0 
wmi                    14504  0 
battery                18436  0 
button                 14224  0 
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
soundcore              15328  1 snd
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_generic            12932  0 
ata_piix               24580  2 
b44                    35984  0 
pata_acpi              12160  0 
libata                177312  3 ata_generic,ata_piix,pata_acpi
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
ssb                    40580  1 b44
ohci1394               37936  0 
uhci_hcd               30736  0 
dock                   16656  1 libata
mii                    13440  1 b44
ieee1394               96324  2 sbp2,ohci1394
ehci_hcd               43276  0 
usbcore               148848  3 uhci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```
> 
Just found this thread that might help you!

[http://ubuntuforums.org/showthread.php?t=820297](http://ubuntuforums.org/showthread.php?t=820297)

Thanks saw it as well in my search but just didn't want to break anything without asking first.

---

### Post by jnorthr on 2008-11-16
if you know the I/P address of your router you could try to ping it. My wireless router allocates all i/p addresses on my home network and has assigned itself an i/p address of 192.168.2.1 so from my unbuntu laptop i do
ping 192.168.2.1
and get
[B]jim@tiny:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=128 time=1.25 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=128 time=1.22 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=128 time=1.72 ms
[/B]
So i know my wireless card in my laptop can 'see' the router. Yours just does not appear to have an i/p address assigned.

---

### Post by jodef on 2008-11-16
> **jnorthr said:**
> if you know the I/P address of your router you could try to ping it. My wireless router allocates all i/p addresses on my home network and has assigned itself an i/p address of 192.168.2.1 so from my unbuntu laptop i do
ping 192.168.2.1
and get
[B]jim@tiny:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=128 time=1.25 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=128 time=1.22 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=128 time=1.72 ms
[/B]
So i know my wireless card in my laptop can 'see' the router. Yours just does not appear to have an i/p address assigned.

I am following the instructions on this page to establish an ad-hoc connection: [http://prash-babu.blogspot.com/2008/08/how-to-createjoin-adhoc-network-in.html](http://prash-babu.blogspot.com/2008/08/how-to-createjoin-adhoc-network-in.html)

But I get the following error on step 6:
```
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Input/output error.

```

That's why am wondering if the card is recognized and working.

---

### Post by gnusci on 2008-11-16
I see something weird here. The output of:

**$ sudo lshw -C Network**

> *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:23:fd:85
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network


the module is **driver=iwl3945** but **lsmod** shows

> iwl3945                98804  0 
rfkill                 17176  2 iwl3945
mac80211              216820  1 iwl3945

as you can see the module is not in use?... I have not experience with the brand of your wireless card, but I think you may need to black list some modules.

---

### Post by jodef on 2008-11-16
> I have not experience with the brand of your wireless card, but I think you may need to black list some modules.

What tells me the module not in use and how and what do I blacklist?

---

### Post by iponeverything on 2008-11-16
This is from the other thread on fixing your card. Its very benign and easy to undo if it does not solve the problem. 

```
1.sudo su

2.echo -e “alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1&#8243; > /etc/modprobe.d/iwl3945

3.reboot 

```

---

### Post by jodef on 2008-11-17
> **iponeverything said:**
> This is from the other thread on fixing your card. Its very benign and easy to undo if it does not solve the problem. 

```
1.sudo su

2.echo -e “alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1&#8243; > /etc/modprobe.d/iwl3945

3.reboot 

```

Tried this didn't work for me.

---

### Post by iponeverything on 2008-11-17
Can you post the output of .. we can keep digging.

```
dmesg


```

---

### Post by jodef on 2008-11-17
Not sure this is whole dmesg kind of scrolled off screen:
```

[    0.644381] ACPI: bus type pnp registered
[    0.688401] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.688401] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.688401] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.688401] pnp 00:03: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.688401] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.688401] pnp 00:03: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.688766] pnp: PnP ACPI: found 12 devices
[    0.688769] ACPI: ACPI bus type pnp unregistered
[    0.688773] PnPBIOS: Disabled by ACPI PNP
[    0.688792] PCI: Using ACPI for IRQ routing
[    0.696043] NET: Registered protocol family 8
[    0.696047] NET: Registered protocol family 20
[    0.696067] NetLabel: Initializing
[    0.696067] NetLabel:  domain hash size = 128
[    0.696067] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.696079] NetLabel:  unlabeled traffic allowed by default
[    0.696088] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.696094] hpet0: 3 64-bit timers, 14318180 Hz
[    0.697744] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.697748]    actual entries 65620
[    0.697845] AppArmor: AppArmor Filesystem Enabled
[    0.697872] ACPI: RTC can wake from S4
[    0.700048] Switched to high resolution mode on CPU 0
[    0.700646] Switched to high resolution mode on CPU 1
[    0.704033] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.704037] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.704041] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.704045] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.704049] system 00:00: iomem range 0x100000-0x3f6d33ff could not be reserved
[    0.704053] system 00:00: iomem range 0x3f6d3400-0x3f6fffff could not be reserved
[    0.704057] system 00:00: iomem range 0x3f700000-0x3f7fffff could not be reserved
[    0.704061] system 00:00: iomem range 0x3f700000-0x3fefffff could not be reserved
[    0.704065] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
[    0.704069] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.704073] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    0.704077] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
[    0.704081] system 00:00: iomem range 0xffa80000-0xffa83fff could not be reserved
[    0.704085] system 00:00: iomem range 0xf4000000-0xf4003fff could not be reserved
[    0.704089] system 00:00: iomem range 0xf4004000-0xf4004fff could not be reserved
[    0.704093] system 00:00: iomem range 0xf4005000-0xf4005fff could not be reserved
[    0.704097] system 00:00: iomem range 0xf4006000-0xf4006fff could not be reserved
[    0.704101] system 00:00: iomem range 0xf4008000-0xf400bfff could not be reserved
[    0.704106] system 00:00: iomem range 0xf0000000-0xf3ffffff could not be reserved
[    0.704115] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.704123] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.704132] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.704136] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.704140] system 00:03: ioport range 0x809-0x809 has been reserved
[    0.704151] system 00:08: ioport range 0xc80-0xcff could not be reserved
[    0.704155] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.704158] system 00:08: ioport range 0x920-0x92f has been reserved
[    0.704162] system 00:08: ioport range 0xcb0-0xcbf has been reserved
[    0.704165] system 00:08: ioport range 0x930-0x97f has been reserved
[    0.704189] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.739739] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.739742] pci 0000:00:1c.0:   IO window: disabled
[    0.739749] pci 0000:00:1c.0:   MEM window: disabled
[    0.739755] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.739764] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.739767] pci 0000:00:1c.1:   IO window: disabled
[    0.739774] pci 0000:00:1c.1:   MEM window: 0xefd00000-0xefdfffff
[    0.739780] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.739789] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.739794] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.739801] pci 0000:00:1c.3:   MEM window: 0xefa00000-0xefcfffff
[    0.739808] pci 0000:00:1c.3:   PREFETCH window: 0x000000e0000000-0x000000e01fffff
[    0.739817] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.739820] pci 0000:00:1e.0:   IO window: disabled
[    0.739828] pci 0000:00:1e.0:   MEM window: 0xef900000-0xef9fffff
[    0.739833] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.739853] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.739861] pci 0000:00:1c.0: setting latency timer to 64
[    0.739873] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.739879] pci 0000:00:1c.1: setting latency timer to 64
[    0.739890] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.739896] pci 0000:00:1c.3: setting latency timer to 64
[    0.739906] pci 0000:00:1e.0: setting latency timer to 64
[    0.739911] bus: 00 index 0 io port: [0, ffff]
[    0.739914] bus: 00 index 1 mmio: [0, ffffffff]
[    0.739917] bus: 0b index 0 mmio: [0, 0]
[    0.739919] bus: 0b index 1 mmio: [0, 0]
[    0.739922] bus: 0b index 2 mmio: [0, 0]
[    0.739924] bus: 0b index 3 mmio: [0, 0]
[    0.739927] bus: 0c index 0 mmio: [0, 0]
[    0.739929] bus: 0c index 1 mmio: [efd00000, efdfffff]
[    0.739932] bus: 0c index 2 mmio: [0, 0]
[    0.739935] bus: 0c index 3 mmio: [0, 0]
[    0.739938] bus: 0d index 0 io port: [d000, dfff]
[    0.739940] bus: 0d index 1 mmio: [efa00000, efcfffff]
[    0.739943] bus: 0d index 2 mmio: [e0000000, e01fffff]
[    0.739946] bus: 0d index 3 mmio: [0, 0]
[    0.739949] bus: 03 index 0 mmio: [0, 0]
[    0.739952] bus: 03 index 1 mmio: [ef900000, ef9fffff]
[    0.739954] bus: 03 index 2 mmio: [0, 0]
[    0.739957] bus: 03 index 3 io port: [0, ffff]
[    0.739960] bus: 03 index 4 mmio: [0, ffffffff]
[    0.739972] NET: Registered protocol family 2
[    0.752070] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.752347] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.752870] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.753157] TCP: Hash tables configured (established 131072 bind 65536)
[    0.753163] TCP reno registered
[    0.760107] NET: Registered protocol family 1
[    0.760247] checking if image is initramfs... it is
[    1.501016] Clocksource tsc unstable (delta = 1818801336 ns)
[    1.601617] Freeing initrd memory: 7989k freed
[    1.601840] Simple Boot Flag at 0x79 set to 0x1
[    1.603211] audit: initializing netlink socket (disabled)
[    1.603237] type=2000 audit(1226903743.601:1): initialized
[    1.610752] highmem bounce pool size: 64 pages
[    1.610759] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.614320] VFS: Disk quotas dquot_6.5.1
[    1.614443] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.614582] msgmni has been set to 1762
[    1.614743] io scheduler noop registered
[    1.614747] io scheduler anticipatory registered
[    1.614750] io scheduler deadline registered
[    1.614765] io scheduler cfq registered (default)
[    1.614780] pci 0000:00:02.0: Boot video device
[    1.615048] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.615101] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.615154] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.615223] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.615284] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.615432] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.615482] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.615533] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.615596] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.615662] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.615796] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.615847] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.615897] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.615963] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.616037] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.616494] isapnp: Scanning for PnP cards...
[    1.970540] isapnp: No Plug & Play device found
[    2.019379] hpet_resources: 0xfed00000 is busy
[    2.019515] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.022729] brd: module loaded
[    2.022827] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.022997] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.026051] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.026060] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.026459] mice: PS/2 mouse device common for all mice
[    2.026644] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.026678] rtc0: alarms up to one month, y3k, hpet irqs
[    2.026875] EISA: Probing bus 0 at eisa.0
[    2.026884] Cannot allocate resource for EISA slot 1
[    2.026918] EISA: Detected 0 cards.
[    2.026922] cpuidle: using governor ladder
[    2.026925] cpuidle: using governor menu
[    2.027560] TCP cubic registered
[    2.027591] Using IPI No-Shortcut mode
[    2.027856] registered taskstats version 1
[    2.028009]   Magic number: 0:970:569
[    2.028046] tty ptyb1: hash matches
[    2.028138] rtc_cmos 00:06: setting system clock to 2008-11-17 06:35:44 UTC (1226903744)
[    2.028142] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.028145] EDD information not available.
[    2.028394] Freeing unused kernel memory: 424k freed
[    2.028453] Write protecting the kernel text: 2576k
[    2.028489] Write protecting the kernel read-only data: 936k
[    2.029839] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.202064] fuse init (API version 7.9)
[    2.237637] ACPI: SSDT 3F6D4176, 0202 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    2.238053] ACPI: SSDT 3F6D3F2B, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    2.238756] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.238840] processor ACPI0007:00: registered as cooling_device0
[    2.238846] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.239270] ACPI: SSDT 3F6D4378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    2.239664] ACPI: SSDT 3F6D40F1, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    2.284273] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.284343] processor ACPI0007:01: registered as cooling_device1
[    2.284349] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.290867] thermal LNXTHERM:01: registered as thermal_zone0
[    2.294607] ACPI: Thermal Zone [THM] (34 C)
[    2.715944] usbcore: registered new interface driver usbfs
[    2.715975] usbcore: registered new interface driver hub
[    2.716103] usbcore: registered new device driver usb
[    2.719335] USB Universal Host Controller Interface driver v3.0
[    2.719401] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.719414] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.719418] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.719470] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    2.719511] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    2.719717] usb usb1: configuration #1 chosen from 1 choice
[    2.719755] hub 1-0:1.0: USB hub found
[    2.719763] hub 1-0:1.0: 2 ports detected
[    2.790724] No dock devices found.
[    2.820502] SCSI subsystem initialized
[    2.883891] libata version 3.00 loaded.
[    2.924430] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.924442] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.924447] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.924478] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    2.924518] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    2.924635] usb usb2: configuration #1 chosen from 1 choice
[    2.924668] hub 2-0:1.0: USB hub found
[    2.924677] hub 2-0:1.0: 2 ports detected
[    3.028432] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    3.028447] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.028452] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.028489] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.028532] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    3.028651] usb usb3: configuration #1 chosen from 1 choice
[    3.028684] hub 3-0:1.0: USB hub found
[    3.028693] hub 3-0:1.0: 2 ports detected
[    3.036113] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    3.132433] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    3.132445] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.132450] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.132485] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.132529] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    3.132648] usb usb4: configuration #1 chosen from 1 choice
[    3.132683] hub 4-0:1.0: USB hub found
[    3.132691] hub 4-0:1.0: 2 ports detected
[    3.179726] usb 1-1: configuration #1 chosen from 1 choice
[    3.182617] hub 1-1:1.0: USB hub found
[    3.184576] hub 1-1:1.0: 4 ports detected
[    3.237536] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.237553] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.237558] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.237594] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.241505] ehci_hcd 0000:00:1d.7: debug port 1
[    3.241513] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.241524] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    3.269071] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.269265] usb usb5: configuration #1 chosen from 1 choice
[    3.269301] hub 5-0:1.0: USB hub found
[    3.269311] hub 5-0:1.0: 8 ports detected
[    3.297622] hub 1-1:1.0: hub_port_status failed (err = -71)
[    3.298604] hub 1-1:1.0: hub_port_status failed (err = -71)
[    3.299606] hub 1-1:1.0: hub_port_status failed (err = -71)
[    3.300607] hub 1-1:1.0: hub_port_status failed (err = -71)
[    3.376170] usb 1-1: USB disconnect, address 2
[    3.476552] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.476589] pata_acpi 0000:00:1f.2: setting latency timer to 64
[    3.476606] pata_acpi 0000:00:1f.2: PCI INT B disabled
[    3.480402] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.533141] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.538080] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.596193] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    3.596252] ata_piix 0000:00:1f.2: version 2.12
[    3.596270] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.596279] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    3.596355] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.596527] b44.c:v2.0
[    3.596648] scsi0 : ata_piix
[    3.596784] scsi1 : ata_piix
[    3.598008] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    3.598012] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    3.616705] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:4b:04:b2
[    3.648130] usb 5-1: new high speed USB device using ehci_hcd and address 2
[    3.760962] ata1.00: failed to set max address (err_mask=0x1)
[    3.760966] ata1.00: device aborted resize (114270345 -> 117210240), skipping HPA handling
[    3.760973] ata1.00: ATA-7: FUJITSU MHV2060BH, 00850028, max UDMA/100
[    3.760977] ata1.00: 114270345 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    3.776390] ata1.00: configured for UDMA/100
[    3.780652] usb 5-1: configuration #1 chosen from 1 choice
[    3.780946] hub 5-1:1.0: USB hub found
[    3.781117] hub 5-1:1.0: 4 ports detected
[    3.940571] ata2.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4244N, B101, max UDMA/33
[    3.956433] ata2.00: configured for UDMA/33
[    3.956592] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2060B 0085 PQ: 0 ANSI: 5
[    3.960950] scsi 1:0:0:0: CD-ROM            HL-DT-ST CDRW/DVD GCC4244 B101 PQ: 0 ANSI: 5
[    3.974788] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    3.974836] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    3.995588] Driver 'sd' needs updating - please use bus_type methods
[    3.995732] sd 0:0:0:0: [sda] 114270345 512-byte hardware sectors (58506 MB)
[    3.995759] sd 0:0:0:0: [sda] Write Protect is off
[    3.995762] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.995807] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.995900] sd 0:0:0:0: [sda] 114270345 512-byte hardware sectors (58506 MB)
[    3.996040] sd 0:0:0:0: [sda] Write Protect is off
[    3.996044] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.996092] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.996098]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.030866]  sda1 sda2 < sda5 sda6 >
[    4.069542] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.088430] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.088436] Uniform CD-ROM driver Revision: 3.20
[    4.088549] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.364977] PM: Starting manual resume from disk
[    4.364982] PM: Resume from partition 8:5
[    4.364985] PM: Checking hibernation image.
[    4.365249] PM: Resume from disk failed.
[    4.426087] kjournald starting.  Commit interval 5 seconds
[    4.426107] EXT3-fs: mounted filesystem with ordered data mode.
[    4.808417] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[334fc0000eef6121]
[   11.580378] udevd version 124 started
[   12.019713] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.037296] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.053953] Linux agpgart interface v0.103
[   12.128356] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   12.128951] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   12.145994] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   12.275747] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[   12.276273] ACPI: Lid Switch [LID]
[   12.276387] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   12.301048] ACPI: Power Button (CM) [PBTN]
[   12.301205] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   12.333031] ACPI: Sleep Button (CM) [SBTN]
[   12.333730] ACPI: AC Adapter [AC] (on-line)
[   12.360106] ACPI: WMI: Mapper loaded
[   12.473268] ACPI: Battery Slot [BAT0] (battery present)
[   12.854522] acpi device:2f: registered as cooling_device2
[   12.855160] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2b/device:2c/input/input5
[   12.872036] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   12.882208] acpi device:34: registered as cooling_device3
[   12.882746] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:31/input/input6
[   12.904029] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   12.904282] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/input/input7
[   12.936038] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   13.442339] intel_rng: FWH not detected
[   13.463058] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   13.502048] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   13.502054] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   13.502169] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.502184] iwl3945 0000:0c:00.0: setting latency timer to 64
[   13.502207] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   13.713490] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   13.714105] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   13.717097] iTCO_vendor_support: vendor-support=0
[   13.794161] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.794265] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   13.794408] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.869298] ricoh-mmc: Ricoh MMC Controller disabling driver
[   13.869302] ricoh-mmc: Copyright(c) Philip Langdale
[   14.013145] iwl3945 0000:0c:00.0: PCI INT A disabled
[   14.013223] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 1)
[   14.013245] ricoh-mmc: Controller is now disabled.
[   14.052216] sdhci: Secure Digital Host Controller Interface driver
[   14.052220] sdhci: Copyright(c) Pierre Ossman
[   14.056524] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
[   14.056547] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   14.059630] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[   14.105722] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.105754] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.513106] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xfa0b1, caps: 0xa04713/0x200000
[   14.548619] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   14.586877] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.542989] lp: driver loaded but no devices found
[   15.739182] Adding 995988k swap on /dev/sda5.  Priority:-1 extents:1 across:995988k
[   16.285542] EXT3 FS on sda6, internal journal
[   17.473954] type=1505 audit(1226918160.168:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4288
[   17.696348] type=1505 audit(1226918160.388:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4293
[   17.696578] type=1505 audit(1226918160.388:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4293
[   17.894713] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.836796] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   19.910662] apm: BIOS not found.
[   20.134929] ppdev: user-space parallel port driver
[   25.658837] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   25.658852] vboxdrv: Successfully done.
[   25.658856] vboxdrv: Found 2 processor cores.
[   25.664020] vboxdrv: fAsync=1 offMin=0xb46fc2c8 offMax=0xb46fc2c8
[   25.665683] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   25.665705] vboxdrv: Successfully loaded version 2.0.4 (interface 0x00090000).
[   27.838462] Bluetooth: Core ver 2.13
[   27.838819] NET: Registered protocol family 31
[   27.838824] Bluetooth: HCI device and connection manager initialized
[   27.838831] Bluetooth: HCI socket layer initialized
[   27.884733] Bluetooth: L2CAP ver 2.11
[   27.884745] Bluetooth: L2CAP socket layer initialized
[   27.926946] Bluetooth: SCO (Voice Link) ver 0.6
[   27.926960] Bluetooth: SCO socket layer initialized
[   27.968106] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.968120] Bluetooth: BNEP filters: protocol multicast
[   28.021292] Bridge firewalling registered
[   28.022278] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   28.055154] Bluetooth: RFCOMM socket layer initialized
[   28.055378] Bluetooth: RFCOMM TTY layer initialized
[   28.055384] Bluetooth: RFCOMM ver 1.10
[   31.598725] [drm] Initialized drm 1.1.0 20060810
[   31.607891] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   31.607909] pci 0000:00:02.0: setting latency timer to 64
[   31.609618] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   32.174851] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   32.175010] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   32.176089] firmware: requesting iwlwifi-3945-1.ucode
[   32.287533] Registered led device: iwl-phy0:radio
[   32.287863] Registered led device: iwl-phy0:assoc
[   32.288094] Registered led device: iwl-phy0:RX
[   32.288303] Registered led device: iwl-phy0:TX
[   32.439958] NET: Registered protocol family 17
[   35.816244] b44: eth0: Link is up at 100 Mbps, full duplex.
[   35.816258] b44: eth0: Flow control is off for TX and off for RX.
[   74.940772] CPU0 attaching NULL sched-domain.
[   74.940793] CPU1 attaching NULL sched-domain.
[   74.967920] CPU0 attaching sched-domain:
[   74.967936]  domain 0: span 0-1 level MC
[   74.967942]   groups: 0 1
[   74.967955] CPU1 attaching sched-domain:
[   74.967959]  domain 0: span 0-1 level MC
[   74.967964]   groups: 1 0
[   87.294999] NET: Registered protocol family 10
[   87.295735] lo: Disabled Privacy Extensions
[   87.300039] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   97.976124] eth0: no IPv6 routers present
[  444.488185] CE: hpet increasing min_delta_ns to 15000 nsec
[  444.488282] CE: hpet increasing min_delta_ns to 22500 nsec
[  444.488377] CE: hpet increasing min_delta_ns to 33750 nsec
[ 2263.048186] usb 2-2: new low speed USB device using uhci_hcd and address 2
[ 2263.218087] usb 2-2: configuration #1 chosen from 1 choice
[ 2263.384488] usbcore: registered new interface driver hiddev
[ 2263.399205] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input10
[ 2263.410792] input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-2
[ 2263.412932] usbcore: registered new interface driver usbhid
[ 2263.414404] usbhid: v2.6:USB HID core driver
[ 2710.944014] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x005f000a
[ 8970.356069] CE: hpet increasing min_delta_ns to 50624 nsec

```

---

### Post by jodef on 2008-11-17
An update I setup a test adhoc networkvia the wireless manager in windows:

No encryption
SSID jkgnet

Now I get the following output:

iwlist scan

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: E2:26:A4:B8:81:04
                    ESSID:"jkgnet"
                    Mode:Ad-Hoc
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=84/100  Signal level:-49 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=000000021a27c970
                    Extra: Last beacon: 64ms ago

pan0      Interface doesn't support scanning.
```

iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Ad-Hoc  Frequency:2.447 GHz  Cell: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

It seems that the network is detected am I correct?

ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:15:c5:4b:04:b2  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe4b:4b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27022 errors:1 dropped:0 overruns:0 frame:0
          TX packets:26053 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22407187 (22.4 MB)  TX bytes:2573457 (2.5 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1731 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93393 (93.3 KB)  TX bytes:93393 (93.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:23:fd:85  
          inet6 addr: fe80::213:2ff:fe23:fd85/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8250 (8.2 KB)  TX bytes:2376 (2.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-23-FD-85-64-38-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
```

What is the wmaster0 listed?

Thanks

---

### Post by meastwood on 2008-11-17
try:
# wlist <interface> scanning essid <your essid>

if card and driver are working then you will get some info back about your access point.

If yes - get some info back - then
Your interface is not configured - are you using dhcp, provided by your router?        
how is your router set-up? use WEP, WPA, WPA2 ....

---

### Post by iponeverything on 2008-11-17
wlan0     Link encap:Ethernet  HWaddr 00:13:02:23:fd:85  
          inet6 addr: fe80::213:2ff:fe23:fd85/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
[COLOR="Red"]          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
          collisions:0 txqueuelen:1000 
          RX bytes:8250 (8.2 KB)  TX bytes:2376 (2.3 KB)

It sure is.

Do:

```
sudo iwconfig wlan0 essid jkgnet
sudo ifconfig wlan0 192.168.1.5 netmask 255.255.255.0 

```
where 192.168.1.x is an ip on the windows machine.
then try to ping the windows box..

See here for an explanation of wmaster0

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

---

### Post by jodef on 2008-11-17
> **iponeverything said:**
> wlan0     Link encap:Ethernet  HWaddr 00:13:02:23:fd:85  
          inet6 addr: fe80::213:2ff:fe23:fd85/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
[COLOR="Red"]          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
          collisions:0 txqueuelen:1000 
          RX bytes:8250 (8.2 KB)  TX bytes:2376 (2.3 KB)

It sure is.

Do:

```
sudo iwconfig wlan0 essid jkgnet
sudo ifconfig wlan0 192.168.1.5 netmask 255.255.255.0 

```
where 192.168.1.x is an ip on the windows machine.
then try to ping the windows box..

See here for an explanation of wmaster0

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

Not sure I'm making progress 2 problems:

1. when I assign an IP address to wlan0 it knocks out my existing wired (eth0) internet connection
2. my sound has died too coincidental to be unrelated

---

### Post by iponeverything on 2008-11-18
You are so close!

Is the ad-hoc network showing up in Network Manager?


Do you  have a wireless router?

---

### Post by jodef on 2008-11-18
> **iponeverything said:**
> You are so close!

Is the ad-hoc network showing up in Network Manager?


Do you  have a wireless router?

Ran into a few snags and apparently the sound thing is an Intrepid bug had to do a reinstall of 8.04 LTS will run through the steps and report back in a day or two.

Thanks for all your assistance thus far.

---

### Post by moon2js on 2008-11-18
I have a similar problem. I just bought a wireless USB card that was on a Linux compatibility list. I can see the device on lsusb. But when I do ifconfig, I don't have wlan0 or wmaster0. How do I get the system (8.10) to use the new wireless adapter?

---

