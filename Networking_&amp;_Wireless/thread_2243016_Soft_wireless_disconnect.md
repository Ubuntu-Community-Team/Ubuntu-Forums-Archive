---
title: "Soft wireless disconnect"
date: 2014-09-05
forum: Networking &amp; Wireless
---

### Post by vladilinsky on 2014-09-05
I tried googling for an answer to this but I could not find anything, so I hope it has not been asked before.

I am running Kubuntu 14.04, and have been suffering from frequent disconnects, but not complete disconnects, the network manager still shows that I am connected and it will sometimes still work but extremely slowly (bits per second) clicking disconnect and reconnect fixes the problem for about 5 to 10 minutes.  I am using a wireless usb adapter (I have tried two of them both do the same thing)  some info  on this computer and hardware 
The wireless adaptor is a TL-WN822N (previously it was a endimax ew-7822uac)

I have included the out put from the following commands 
lshw,
lshw -C network, 
ping google.ca
some of the dmesg, 
ifconfig, 
lsmod

lshw```
pvr-system-liivingroom    
    description: Desktop Computer
    product: System Product Name (SKU)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 ldt16 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=SKU uuid=C083B335-DAD7-DD11-A887-50465DA1C49F
  *-core
       description: Motherboard
       product: P8B75-M
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev X.0x
       serial: 121002923500468
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0812
          date: 08/03/2012
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-3570K CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-3570K CPU @ 3.40GHz
          serial: To Be Filled By O.E.M.
          slot: LGA1155
          size: 1600MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=4 enabledcores=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: internal unified
     *-memory:0 UNCLAIMED
          physical id: 1
        *-bank UNCLAIMED
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 0
             serial: [Empty]
             slot: ChannelA-DIMM0
     *-memory:1
          description: System Memory
          physical id: 5c
          slot: System board or motherboard
        *-bank:0
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: KHX1600C9D3/4GX
             vendor: Kingston
             physical id: 0
             serial: B82EC912
             slot: ChannelA-DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [Empty]
             slot: ChannelB-DIMM0
        *-bank:2
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: KHX1600C9D3/4GX
             vendor: Kingston
             physical id: 2
             serial: B82EC813
             slot: ChannelB-DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-memory:2 UNCLAIMED
          physical id: 2
     *-memory:3 UNCLAIMED
          physical id: 3
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:f4000000-f60fffff ioport:e0000000(size=201326592)
           *-display
                description: VGA compatible controller
                product: GF104 [GeForce GTX 460]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:45 memory:f4000000-f5ffffff memory:e0000000-e7ffffff memory:e8000000-ebffffff ioport:e000(size=128) memory:f6000000-f607ffff
           *-multimedia
                description: Audio device
                product: GF104 High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f6080000-f6083fff
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:41 memory:f6100000-f610ffff
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:43 memory:f611a000-f611a00f
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f6117000-f61173ff
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:f6110000-f6113fff
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:d000(size=4096) ioport:ec100000(size=1048576)
           *-network DISABLED
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 09
                serial: 50:46:5d:a1:c4:9f
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:42 ioport:d000(size=256) memory:ec104000-ec104fff memory:ec100000-ec103fff
        *-usb:2
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f6116000-f61163ff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: B75 Express Chipset LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 7 Series/C210 Series Chipset Family 4-port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f0d0(size=8) ioport:f0c0(size=4) ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=16) ioport:f080(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f6115000-f61150ff ioport:f000(size=32)
        *-ide:1
             description: IDE interface
             product: 7 Series/C210 Series Chipset Family 2-port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f030(size=16) ioport:f020(size=16)
     *-scsi:0
          physical id: 5
          logical name: scsi0
          capabilities: emulated
        *-disk:0
             description: ATA Disk
             product: WDC WD5000AAKS-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 05.0
             serial: WD-WMAWF0253095
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00060038
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 3fa268a3-5fc1-41e2-86b3-0986dbd5f4a3
                size: 27GiB
                capacity: 27GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-10-17 13:43:10 filesystem=ext4 lastmountpoint=/ modified=2014-09-05 10:42:47 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-09-05 10:42:47 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 437GiB
                capacity: 437GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /home
                   capacity: 435GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 2008MiB
                   capabilities: nofs
        *-disk:1
             description: ATA Disk
             product: ST31000528AS
             vendor: Seagate
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/sdb
             version: CC46
             serial: 6VPAQW80
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0003fcd8
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.1.0,1
                logical name: /dev/sdb1
                version: 1.0
                serial: e73dda5d-72be-4f05-8309-187fd6f098d4
                size: 931GiB
                capacity: 931GiB
                capabilities: primary multi journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2011-05-04 14:07:52 filesystem=ext4 modified=2011-05-04 14:07:58 state=clean
     *-scsi:1
          physical id: 6
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GH22NS50
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: TN02
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: ST31000528AS
             vendor: Seagate
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/sdc
             version: CC46
             serial: 6VP9GFS2
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000dbe70
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.1.0,1
                logical name: /dev/sdc1
                version: 1.0
                serial: 7afa0bb9-6c64-4560-bc16-4c006955b8c4
                size: 931GiB
                capacity: 931GiB
                capabilities: primary bootable multi journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2011-05-04 14:07:44 filesystem=ext4 modified=2011-05-04 14:07:51 state=clean
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@2:1.6
       logical name: wlan1
       serial: e8:de:27:14:0b:bb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.13.0-32-generic firmware=N/A ip=192.168.1.184 link=yes multicast=yes wireless=IEEE 802.11bgn
```

ifconfig```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:19124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1643704 (1.6 MB)  TX bytes:1643704 (1.6 MB)

wlan1     Link encap:Ethernet  HWaddr e8:de:27:14:0b:bb  
          inet addr:192.168.1.184  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::eade:27ff:fe14:bbb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:805534 errors:0 dropped:2 overruns:0 frame:0
          TX packets:434232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1088445843 (1.0 GB)  TX bytes:46064407 (46.0 MB)

```
lsmod```
Module                  Size  Used by
ctr                    13049  2 
ccm                    17773  2 
xt_multiport           12798  1 
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter
x_tables               34059  3 ip_tables,xt_multiport,iptable_filter
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391196  10 bnep,rfcomm
nvidia              10540234  66 
arc4                   12608  2 
rtl8192cu              67723  0 
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
rtl_usb                18448  1 rtl8192cu
sparse_keymap          13948  1 asus_wmi
rtlwifi                63475  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
mac80211              630653  3 rtl_usb,rtlwifi,rtl8192cu
snd_hda_codec_hdmi     46254  4 
intel_rapl             18773  0 
cfg80211              484040  2 mac80211,rtlwifi
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
ir_lirc_codec          13021  3 
coretemp               13435  0 
ir_mce_kbd_decoder     13214  0 
ir_jvc_decoder         12751  0 
ir_rc5_decoder         12710  0 
ir_rc6_decoder         12874  0 
lirc_dev               19980  1 ir_lirc_codec
ir_nec_decoder         12915  0 
ir_sanyo_decoder       12839  0 
ir_sony_decoder        12713  0 
rc_rc6_mce             12502  0 
mceusb                 21980  0 
snd_hda_codec_via      27860  1 
rc_core                28124  12 lirc_dev,ir_lirc_codec,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,mceusb,ir_mce_kbd_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sanyo_decoder,rc_rc6_mce
kvm_intel             143060  0 
snd_hda_intel          52355  10 
kvm                   451511  1 kvm_intel
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
joydev                 17381  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
crct10dif_pclmul       14289  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
crc32_pclmul           13113  0 
snd_seq_midi           13324  0 
ghash_clmulni_intel    13216  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
aesni_intel            55624  4 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
aes_x86_64             17131  1 aesni_intel
snd_timer              29482  2 snd_pcm,snd_seq
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
drm                   303102  2 nvidia
snd                    69238  31 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
glue_helper            13990  1 aesni_intel
soundcore              12680  1 snd
ablk_helper            13597  1 aesni_intel
mei_me                 18627  0 
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
mei                    82276  1 mei_me
lpc_ich                21080  0 
wmi                    19177  1 asus_wmi
serio_raw              13462  0 
mac_hid                13205  0 
parport_pc             32701  1 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
raid10                 48128  0 
raid456                86484  0 
async_raid6_recov      12984  1 raid456
async_memcpy           12762  1 raid456
async_pq               13365  1 raid456
async_xor              13160  2 async_pq,raid456
async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
xor                    21411  1 async_xor
raid6_pq               97812  2 async_pq,async_raid6_recov
raid0                  17842  0 
multipath              13145  0 
linear                 12894  0 
hid_logitech_dj        18581  0 
usbhid                 52570  0 
hid                   106148  4 usbhid,hid_logitech_dj
raid1                  35530  1 
psmouse               106678  0 
r8169                  67581  0 
mii                    13934  1 r8169
video                  19476  1 asus_wmi

```
Pinging google.ca```
ping google.ca
PING google.ca (74.125.226.111) 56(84) bytes of data.
64 bytes from yyz08s13-in-f15.1e100.net (74.125.226.111): icmp_seq=1 ttl=53 time=24.4 ms
64 bytes from yyz08s13-in-f15.1e100.net (74.125.226.111): icmp_seq=2 ttl=53 time=24.7 ms
64 bytes from yyz08s13-in-f15.1e100.net (74.125.226.111): icmp_seq=3 ttl=53 time=24.0 ms
64 bytes from yyz08s13-in-f15.1e100.net (74.125.226.111): icmp_seq=4 ttl=53 time=25.5 ms
64 bytes from yyz08s13-in-f15.1e100.net (74.125.226.111): icmp_seq=5 ttl=53 time=24.3 ms
64 bytes from yyz08s13-in-f15.1e100.net (74.125.226.111): icmp_seq=6 ttl=53 time=24.5 ms
^C
--- google.ca ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5006ms
rtt min/avg/max/mdev = 24.055/24.606/25.531/0.500 ms

```

some recent dmesg
```
  13.907159] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   13.910359] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   13.910562] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   13.910566] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  340.32  Tue Aug  5 20:58:26 PDT 2014
[   14.617608] Bluetooth: Core ver 2.17
[   14.617629] NET: Registered protocol family 31
[   14.617638] Bluetooth: HCI device and connection manager initialized
[   14.617652] Bluetooth: HCI socket layer initialized
[   14.617653] Bluetooth: L2CAP socket layer initialized
[   14.617656] Bluetooth: SCO socket layer initialized
[   14.722061] Bluetooth: RFCOMM TTY layer initialized
[   14.722069] Bluetooth: RFCOMM socket layer initialized
[   14.722077] Bluetooth: RFCOMM ver 1.11
[   14.857951] init: cups main process (992) killed by HUP signal
[   14.857959] init: cups main process ended, respawning
[   14.863187] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.863189] Bluetooth: BNEP filters: protocol multicast
[   14.863196] Bluetooth: BNEP socket layer initialized
[   19.603807] init: udev-fallback-graphics main process (1414) terminated with status 1
[   20.940275] rtl8192cu: MAC auto ON okay!
[   20.972979] rtl8192cu: Tx queue select: 0x05
[   21.342282] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   21.342488] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   22.201386] init: samba-ad-dc main process (1399) terminated with status 1
[   25.696446] nvidia 0000:01:00.0: irq 45 for MSI/MSI-X
[   26.809703] ip_tables: (C) 2000-2006 Netfilter Core Team
[   27.421189] init: plymouth-upstart-bridge main process ended, respawning
[   44.126875] wlan1: authenticate with 74:d0:2b:42:89:20
[   44.150200] wlan1: send auth to 74:d0:2b:42:89:20 (try 1/3)
[   44.170928] wlan1: authenticated
[   44.174334] wlan1: associate with 74:d0:2b:42:89:20 (try 1/3)
[   44.179422] wlan1: RX AssocResp from 74:d0:2b:42:89:20 (capab=0x411 status=0 aid=7)
[   44.179459] wlan1: associated
[   44.179507] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   44.885453] audit_printk_skb: 114 callbacks suppressed
[   44.885456] type=1400 audit(1409928205.659:50): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2390 comm="apparmor_parser"
[   44.885460] type=1400 audit(1409928205.659:51): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2390 comm="apparmor_parser"
[   44.885711] type=1400 audit(1409928205.659:52): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2390 comm="apparmor_parser"
[   69.485045] hda-codec: out of range cmd 1:5:707:ffffffff
[ 2389.965833] wlan1: deauthenticating from 74:d0:2b:42:89:20 by local choice (reason=3)
[ 2389.978643] cfg80211: Calling CRDA to update world regulatory domain
[ 2389.982588] cfg80211: World regulatory domain updated:
[ 2389.982593] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2389.982596] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2389.982598] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2389.982600] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2389.982602] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2389.982603] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2402.748681] wlan1: authenticate with 74:d0:2b:42:89:20
[ 2402.772146] wlan1: send auth to 74:d0:2b:42:89:20 (try 1/3)
[ 2402.774592] wlan1: authenticated
[ 2402.776164] wlan1: associate with 74:d0:2b:42:89:20 (try 1/3)
[ 2402.793114] wlan1: RX AssocResp from 74:d0:2b:42:89:20 (capab=0x411 status=0 aid=7)
[ 2402.793147] wlan1: associated
[ 2928.020122] wlan1: deauthenticating from 74:d0:2b:42:89:20 by local choice (reason=3)
[ 2928.032472] cfg80211: Calling CRDA to update world regulatory domain
[ 2928.035127] cfg80211: World regulatory domain updated:
[ 2928.035130] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2928.035132] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2928.035133] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2928.035134] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2928.035136] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2928.035137] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2929.857310] wlan1: authenticate with 74:d0:2b:42:89:20
[ 2929.869353] wlan1: send auth to 74:d0:2b:42:89:20 (try 1/3)
[ 2929.918452] wlan1: authenticated
[ 2929.918645] wlan1: associate with 74:d0:2b:42:89:20 (try 1/3)
[ 2929.929563] wlan1: RX AssocResp from 74:d0:2b:42:89:20 (capab=0x411 status=0 aid=7)
[ 2929.929598] wlan1: associated
[ 3353.540935] wlan1: deauthenticating from 74:d0:2b:42:89:20 by local choice (reason=3)
[ 3353.553311] cfg80211: Calling CRDA to update world regulatory domain
[ 3353.558345] cfg80211: World regulatory domain updated:
[ 3353.558349] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3353.558352] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3353.558354] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3353.558356] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3353.558358] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3353.558359] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3355.054338] wlan1: authenticate with 74:d0:2b:42:89:20
[ 3355.066613] wlan1: send auth to 74:d0:2b:42:89:20 (try 1/3)
[ 3355.069444] wlan1: authenticated
[ 3355.070456] wlan1: associate with 74:d0:2b:42:89:20 (try 1/3)
[ 3355.075703] wlan1: RX AssocResp from 74:d0:2b:42:89:20 (capab=0x411 status=0 aid=7)
[ 3355.075740] wlan1: associated
[13375.951721] wlan1: deauthenticating from 74:d0:2b:42:89:20 by local choice (reason=3)
[13375.965947] cfg80211: Calling CRDA to update world regulatory domain
[13375.968278] cfg80211: World regulatory domain updated:
[13375.968281] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[13375.968283] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13375.968285] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13375.968286] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[13375.968288] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13375.968289] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13377.073870] wlan1: authenticate with 74:d0:2b:42:89:20
[13377.085982] wlan1: send auth to 74:d0:2b:42:89:20 (try 1/3)
[13377.090840] wlan1: authenticated
[13377.091021] wlan1: associate with 74:d0:2b:42:89:20 (try 1/3)
[13377.098711] wlan1: RX AssocResp from 74:d0:2b:42:89:20 (capab=0x411 status=0 aid=6)
[13377.098744] wlan1: associated
[16451.324452] wlan1: deauthenticating from 74:d0:2b:42:89:20 by local choice (reason=3)
[16451.337208] cfg80211: Calling CRDA to update world regulatory domain
[16451.341109] cfg80211: World regulatory domain updated:
[16451.341114] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[16451.341117] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[16451.341119] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[16451.341121] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[16451.341123] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[16451.341125] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[16454.541498] wlan1: authenticate with 74:d0:2b:42:89:20
[16454.553715] wlan1: send auth to 74:d0:2b:42:89:20 (try 1/3)
[16454.556326] wlan1: authenticated
[16454.556612] wlan1: associate with 74:d0:2b:42:89:20 (try 1/3)
[16454.631915] wlan1: RX AssocResp from 74:d0:2b:42:89:20 (capab=0x411 status=0 aid=6)
[16454.631951] wlan1: associated
[16462.811003] wlan1: deauthenticated from 74:d0:2b:42:89:20 (Reason: 15)
[16462.843983] cfg80211: Calling CRDA to update world regulatory domain
[16462.847613] cfg80211: World regulatory domain updated:
[16462.847617] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[16462.847619] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[16462.847621] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[16462.847623] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[16462.847624] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[16462.847626] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[16463.636093] wlan1: authenticate with 74:d0:2b:42:89:20
[16463.660656] wlan1: send auth to 74:d0:2b:42:89:20 (try 1/3)
[16463.676863] wlan1: authenticated
[16463.679359] wlan1: associate with 74:d0:2b:42:89:20 (try 1/3)
[16463.721587] wlan1: RX AssocResp from 74:d0:2b:42:89:20 (capab=0x411 status=0 aid=6)
[16463.721626] wlan1: associated

```

lshw -C network
```
sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 09
       serial: 50:46:5d:a1:c4:9f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:d000(size=256) memory:ec104000-ec104fff memory:ec100000-ec103fff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@2:1.6
       logical name: wlan1
       serial: e8:de:27:14:0b:bb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.13.0-32-generic firmware=N/A ip=192.168.1.184 link=yes multicast=yes wireless=IEEE 802.11bgn

```

iwconfig```
iwconfig
wlan1     IEEE 802.11bgn  ESSID:"(\/) (;,,;) (\/) "  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 74:D0:2B:42:89:20   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:32   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.


```

---

### Post by praseodym on 2014-09-06
Change the driver via:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot.

If you have problems with the LAN driver, too, change it, too:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/45/14/3005217-r8168-dkms-8.038.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.038.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.038.00
sudo dkms build -m r8168-dkms -v 8.038.00
sudo dkms install -m r8168-dkms -v 8.038.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by vladilinsky on 2014-09-10
Sorry for the long delay in replying, I had unexpected work up north away from the internet,
Thanks, your solution worked great!

---

