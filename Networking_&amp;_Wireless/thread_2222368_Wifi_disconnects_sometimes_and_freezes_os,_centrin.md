---
title: "Wifi disconnects sometimes and freezes os, centrino n-1000,"
date: 2014-05-06
forum: Networking &amp; Wireless
---

### Post by 3vilpad on 2014-05-06
[FONT=arial]Hi everyone :)
First of all I want to say "Thank you" to all ubuntu&linux&open_source community for it's general awesomeness! Now for the case. I solved many problems using this, and similar sites but now I'm stuck. Few days ago (01.may.2014) my laptop completly out of blue started having issues with wi-fi connection. It never happend before. I haven't installed anything or messed up with anything. Maybe it's caused by some update, actually I think it's only rational reason for this problem. 


WiFi issue:

[LIST]
[*]Most of a time it can't see any wifi network.
[*]Sometimes when I reboot it works but only for a short period of time (seconds to few hours), and it's always disconnects.
[*]Before it disconnects its freezing system for few seconds.
[/LIST]


Specification:

[LIST]
[*]Asus N53JF
[*]Ubuntu [13.10 / 14.04]("tel:13.10%20%2F%2014.04") LTS (only OS) 64 bit - upgraded it recently from 13.10 to check if this would solve the problem (It started on 13.10). It didn't.
[*]WLAN: Intel Centrino Wireless n-1000
[/LIST]


What I have done till now:

[LIST]
[*]I updated firmware using this commands:
[/LIST]
```
cd /home/kzp3r/Pulpit/iwlwifi-1000-ucode-39.31.5.1
sudo cp iwlwifi-1000-5.ucode /lib/firmware/

```
but nothing changed

[LIST]
[*]I ignored ipv6 in network properties
[*]I runned this commands because someone told me to:
[/LIST]
```
sudo modprobe iwlwifi 11n_disable=1


echo 'options iwlagn 11ndisable=1' | sudo tee /etc/modprobe.d/iwlagn.conf >/dev/null



```

[LIST]
[*]I checked hardware switch, but it's not the case.
[*]Router and network is ok, other devices are cooperating with it.
[/LIST]


I also got this messages during os boot few times (i can't see it now):
> iwlgn "somethin somethin" no suitable firmware found! 


and other time but only once:
> unable to init eeprom


Ok now for the terminal black magic:
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]LSHW (this command was runned while there was no wifi):
```
3vil                      
    description: Notebook
    product: N53Jf ()
    vendor: ASUSTeK Computer Inc.
    version: 1.0
    serial: A9N0CH04220439
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=notebook uuid=1F7C0A00-0029-1080-FFFF-485B3999A5AB
  *-core
       description: Motherboard
       product: N53Jf
       vendor: ASUSTeK Computer Inc.
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: N53Jf.206
          date: 10/01/2010
          size: 64KiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GH
          serial: To Be Filled By O.E.M.
          slot: Socket 989
          size: 1199MHz
          capacity: 4GHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt lahf_lm ida arat dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=1 threads=2
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
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 41
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1067 MHz (0,9 ns)
             product: EBJ21UE8BDS0-DJ-F
             vendor: AMI
             physical id: 0
             serial: 3729206F
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [Empty]
             slot: DIMM1
        *-bank:2
             description: SODIMM DDR3 Synchronous 1067 MHz (0,9 ns)
             product: EBJ21UE8BDS0-DJ-F
             vendor: AMI
             physical id: 2
             serial: 3429206F
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:3
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 3
             serial: [Empty]
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 18
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 18
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:c0000000-d30fffff
           *-generic UNCLAIMED
                description: Unassigned class
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0
                bus info: pci@0000:01:00.0
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
                resources: memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:d000(size=128) memory:d3000000-d307ffff
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 18
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:48 memory:d3400000-d37fffff memory:b0000000-bfffffff ioport:e080(size=8)
        *-communication
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:47 memory:d9c0a000-d9c0a00f
        *-usb:0
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:d9c08000-d9c083ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:49 memory:d9c00000-d9c03fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:c000(size=4096) memory:d8800000-d9bfffff ioport:d3100000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:b000(size=4096) memory:d7400000-d87fffff
           *-generic
                description: Unassigned class
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0
                bus info: pci@0000:03:00.0
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: driver=iwlwifi latency=255 maxlatency=255 mingnt=255
                resources: irq:17 memory:d7400000-d7401fff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:a000(size=4096) memory:d6000000-d73fffff ioport:d9d00000(size=2097152)
           *-usb
                description: USB controller
                product: Fresco Logic
                vendor: Fresco Logic
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:d6000000-d600ffff
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:9000(size=4096) memory:d4c00000-d5ffffff ioport:d9f00000(size=2097152)
        *-pci:5
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:8000(size=4096) memory:d3800000-d4bfffff ioport:da100000(size=2097152)
           *-network
                description: Ethernet interface
                product: AR8131 Gigabit Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth0
                version: c0
                serial: 48:5b:39:99:a5:ab
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=192.168.1.102 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:50 memory:d3800000-d383ffff ioport:8000(size=128)
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:d9c07000-d9c073ff
        *-pci:6
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:46 ioport:e070(size=8) ioport:e060(size=4) ioport:e050(size=8) ioport:e040(size=4) ioport:e020(size=32) memory:d9c06000-d9c067ff
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel ips latency=0
             resources: irq:18 memory:d9c04000-d9c04fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 05
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1000LM024 HN-M
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2AR1
             serial: S2R8J9ADA06099
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=000d5fc6
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: df5f13e0-5e21-4513-85c1-f636c018eb3c
                size: 927GiB
                capacity: 927GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2013-12-05 18:13:32 filesystem=ext4 lastmountpoint=/ modified=2014-05-06 10:58:31 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-05-06 10:58:31 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 3883MiB
                capacity: 3883MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3883MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GT32N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: AS01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc

```[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]LSHW -C NETWORK (runned with wifi; when the issue occurs it only shows ethernet):

```
 *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1000 [Condor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:64:51:99:cc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-24-generic firmware=39.31.5.1 build 35138 ip=192.168.1.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:47 memory:d7400000-d7401fff
  *-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: c0
       serial: 48:5b:39:99:a5:ab
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:51 memory:d3800000-d383ffff ioport:8000(size=128)


```[/FONT]
[FONT=arial]
LSMOD:

```
Module                  Size  Used by
bbswitch               13943  0 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
rfcomm                 69160  8 
bnep                   19624  2 
binfmt_misc            17468  1 
joydev                 17381  0 
snd_hda_codec_realtek    61438  1 
iwldvm                232285  0 
mac80211              626489  1 iwldvm
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
mxm_wmi                13021  0 
snd_hda_intel          52355  3 
btusb                  32412  0 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
bluetooth             395423  22 bnep,btusb,rfcomm
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
kvm_intel             143060  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
kvm                   451511  1 kvm_intel
snd_rawmidi            30144  1 snd_seq_midi
iwlwifi               169932  1 iwldvm
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
i915                  783485  9 
psmouse               102222  0 
serio_raw              13462  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
drm_kms_helper         52758  1 i915
intel_ips              18664  0 
drm                   302817  5 i915,drm_kms_helper
lpc_ich                21080  0 
snd                    69238  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_algo_bit           13413  1 i915
mei_me                 18627  0 
mei                    82274  1 mei_me
soundcore              12680  1 snd
parport_pc             32701  0 
ppdev                  17671  0 
video                  19476  1 i915
wmi                    19177  1 mxm_wmi
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
asus_laptop            28833  0 
sparse_keymap          13948  1 asus_laptop
input_polldev          13896  1 asus_laptop
mac_hid                13205  0 
ahci                   25819  2 
libahci                32168  1 ahci
atl1c                  46086  0 

```[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]IWCONFIG (without wifi):[/FONT]
```
[FONT=arial]eth0      no wireless extensions.


lo        no wireless extensions.
[/FONT]

```[FONT=arial]
[/FONT]
[FONT=arial]2 (with wifi)
```

eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"3vil"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:24:62:26   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-22 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:90   Missed beacon:0




```



IWLIST SCAN (without):
```
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.

```[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]2 (with)[/FONT]
```
[FONT=arial]eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:24:62:26
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"3vil"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000cc4737f26
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 00043376696C
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
[/FONT]
[FONT=arial]
[/FONT]

```[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]RFKILL LIST:[/FONT]
```
[FONT=arial]0: asus-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no
1: asus-wimax: WiMAX
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
[/FONT]

```[FONT=arial]
[/FONT]
[FONT=arial]NM TOOL (with):

[/FONT]
```
[FONT=arial]NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        48:5B:39:99:A5:AB


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0  [3vil] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:1E:64:51:99:CC


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *3vil:           Infra, 00:13:10:24:62:26, Freq 2437 MHz, Rate 54 Mb/s, Strength 92 WPA


  IPv4 Settings:
    Address:         192.168.1.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.88


    DNS:             62.179.1.60
    DNS:             62.179.1.61


[/FONT]

```
[FONT=arial]
MODPROBE IWLAGN:[/FONT]
```
[FONT=arial]modprobe: FATAL: Module iwlagn not found.
[/FONT]

```

It would be great if anyone could help me =)

---

### Post by 3vilpad on 2014-05-10
Sorry for bumping but I've got another theory. My computer was flooded with champaign by my dear girlfriend few months ago so maybe this is not software issue but an hardware (motherboard damage was diagnosed). Could someone help me confirm/discard this assumption? I would gladly generate wifi/system log to analyze, but im not sure how. 


This command?
```
[FONT=arial]grep -i networkmanager /var/log/syslog[/FONT]

```

Also I've tried ubuntu live to check if problem would disapear but it didn't.


PS. Excuse me for my English, it's not my mother tounge :)


[COLOR=#ff0000][SIZE=3][B]EDIT
PPS. Terribly sorry for not reading sticked threads! Below is my wifi log. [/B][/SIZE][/COLOR]



```
########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux 3vil 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0083] (rev ff)
    Kernel driver in use: iwlwifi
04:00.0 USB controller [0c03]: Fresco Logic Device [1b73:1400] (rev 01)


06:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8131 Gigabit Ethernet [1969:1063] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1820]
    Kernel driver in use: atl1c


##### lsusb #####


Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 001 Device 003: ID 13d3:5122 IMC Networks 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: asus-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no
1: asus-wimax: WiMAX
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.88    0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0  [Po&#322;&#261;czenie przewodowe 1] ------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.25
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.88


    DNS:             62.179.1.60
    DNS:             62.179.1.61


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


##### iwlist channel #####


wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz


##### lsmod #####


iwldvm                232285  0 
mac80211              626489  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm


##### modinfo #####


filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     03CC0BBD2BE23C16DB062DC
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     1E6912E109D5A43B310FB34
alias:          pci:v00008086d0000095Asv*sd00005490bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005290bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005590bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005190bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005090bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005420bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000502Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005020bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009310bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009510bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009210bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009112bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009012bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009010bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005202bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005002bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005200bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000500Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005000bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00001010bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005400bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005012bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005210bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005302bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005310bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000510Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005100bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005112bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005010bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008570bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00008270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000370bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000472bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000272bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C02Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C26Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C272bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C760bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C770bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C06Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000402Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00005070bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Cbc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A70bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000486Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004870bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000446Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000426Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004272bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000406Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004070bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00005260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004860bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd0000446Abc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd0000426Abc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd0000406Abc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004822bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00004820bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C228bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001318bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001328bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001308bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001118bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001128bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001108bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


##### modules #####


lp
rtc


##### blacklist #####


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/bumblebee.conf]
blacklist nouveau
blacklist nvidia
blacklist nvidia-current
blacklist nvidia-current-updates
blacklist nvidia-304
blacklist nvidia-304-updates
blacklist nvidia-experimental-304
blacklist nvidia-310
blacklist nvidia-310-updates
blacklist nvidia-experimental-310
blacklist nvidia-313
blacklist nvidia-313-updates
blacklist nvidia-experimental-313
blacklist nvidia-319
blacklist nvidia-319-updates
blacklist nvidia-experimental-319
blacklist nvidia-325
blacklist nvidia-325-updates
blacklist nvidia-experimental-325
blacklist nvidia-331
blacklist nvidia-331-updates
blacklist nvidia-experimental-331


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x1969:0x1063 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:0x0083 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   15.759747] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   15.759809] iwlwifi 0000:03:00.0: irq 48 for MSI/MSI-X
[   16.429456] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138 op_mode iwldvm
[   16.444298] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   16.444299] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   16.444300] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   16.444301] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   16.444354] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   16.468150] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.622988] psmouse serio4: elantech: assuming hardware version 2 (with firmware version 0x040201)
[   22.303973] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   22.311066] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
[   22.345438] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   22.352526] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
[   22.390340] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.391325] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.814385] wlan0: authenticate with <MAC address removed>
[   22.825552] wlan0: send auth to <MAC address removed> (try 1/3)
[   22.828310] wlan0: authenticated
[   22.832408] wlan0: associate with <MAC address removed> (try 1/3)
[   22.835672] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=9)
[   22.839129] wlan0: associated
[   22.839154] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[23834.260750] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[24055.464359] iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[24055.464365] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 254 write_ptr 0
[24055.464368] iwlwifi 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[24055.481431] WARNING: CPU: 1 PID: 975 at /build/buildd/linux-3.13.0/drivers/net/wireless/iwlwifi/pcie/trans.c:1002 iwl_trans_pcie_grab_nic_access+0xcb/0xe0 [iwlwifi]()
[24055.481433] Modules linked in: ses enclosure usb_storage bbswitch(OF) pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) ctr ccm rfcomm bnep binfmt_misc joydev uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev snd_hda_codec_realtek arc4 iwldvm mac80211 mxm_wmi btusb bluetooth intel_powerclamp coretemp kvm_intel kvm snd_hda_intel snd_hda_codec snd_hwdep psmouse snd_pcm serio_raw snd_page_alloc intel_ips parport_pc snd_seq_midi snd_seq_midi_event snd_rawmidi lpc_ich iwlwifi ppdev snd_seq cfg80211 snd_seq_device snd_timer snd soundcore lp parport i915 drm_kms_helper wmi video drm mei_me mei asus_laptop i2c_algo_bit sparse_keymap input_polldev mac_hid ahci libahci atl1c
[24055.481497]  [<ffffffffa02adeda>] ? iwl_read32+0x1a/0x80 [iwlwifi]
[24055.481502]  [<ffffffffa02af32b>] iwl_trans_pcie_grab_nic_access+0xcb/0xe0 [iwlwifi]
[24055.481507]  [<ffffffffa02b03c1>] iwl_trans_pcie_read_mem+0x31/0x130 [iwlwifi]
[24055.481513]  [<ffffffffa05520f2>] iwl_dump_nic_error_log+0xc2/0x6a0 [iwldvm]
[24055.481527]  [<ffffffffa02a41fd>] ? __iwl_err+0x5d/0xc0 [iwlwifi]
[24055.481532]  [<ffffffffa0555574>] iwl_nic_error+0x34/0x50 [iwldvm]
[24055.481558]  [<ffffffffa02ad5b0>] iwl_trans_pcie_send_hcmd+0x5b0/0x690 [iwlwifi]
[24055.481571]  [<ffffffffa055e556>] iwl_dvm_send_cmd+0x46/0x110 [iwldvm]
[24055.481578]  [<ffffffffa05680d8>] iwlagn_request_scan+0x888/0xcc0 [iwldvm]
[24055.481585]  [<ffffffffa05687ab>] iwl_scan_initiate+0xeb/0x180 [iwldvm]
[24055.481590]  [<ffffffffa055850a>] iwlagn_mac_hw_scan+0x8a/0x120 [iwldvm]
[24055.481784] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[24055.481790] iwlwifi 0000:03:00.0: Status: 0x000022CC, count: -1
[24055.481796] iwlwifi 0000:03:00.0: 0x3F751788 | ADVANCED_SYSASSERT          
[24055.481802] iwlwifi 0000:03:00.0: 0xFFFF8801 | uPc
[24055.481806] iwlwifi 0000:03:00.0: 0x3F751748 | branchlink1
[24055.481813] iwlwifi 0000:03:00.0: 0xFFFF8801 | branchlink2
[24055.481818] iwlwifi 0000:03:00.0: 0x00000010 | interruptlink1
[24055.481824] iwlwifi 0000:03:00.0: 0xFFFF8801 | interruptlink2
[24055.481827] iwlwifi 0000:03:00.0: 0x3F7517A0 | data1
[24055.481829] iwlwifi 0000:03:00.0: 0xFFFF8801 | data2
[24055.481831] iwlwifi 0000:03:00.0: 0x3F751788 | line
[24055.481833] iwlwifi 0000:03:00.0: 0xFFFF8801 | beacon time
[24055.481835] iwlwifi 0000:03:00.0: 0xA0579ED8 | tsf low
[24055.481837] iwlwifi 0000:03:00.0: 0xFFFFFFFF | tsf hi
[24055.481839] iwlwifi 0000:03:00.0: 0x9D955814 | time gp1
[24055.481841] iwlwifi 0000:03:00.0: 0xFFFF8800 | time gp2
[24055.481844] iwlwifi 0000:03:00.0: 0xA057B353 | time gp3
[24055.481849] iwlwifi 0000:03:00.0: 0xFFFFFFFF | uCode version
[24055.481855] iwlwifi 0000:03:00.0: 0x3F7517F0 | hw version
[24055.481860] iwlwifi 0000:03:00.0: 0xFFFF8801 | board version
[24055.481865] iwlwifi 0000:03:00.0: 0xFFFFFFFF | hcmd
[24055.481867] iwlwifi 0000:03:00.0: 0x3F751798 | isr0
[24055.481869] iwlwifi 0000:03:00.0: 0xFFFF8801 | isr1
[24055.481871] iwlwifi 0000:03:00.0: 0x00000020 | isr2
[24055.481873] iwlwifi 0000:03:00.0: 0xFFFF8801 | isr3
[24055.481875] iwlwifi 0000:03:00.0: 0x3F751800 | isr4
[24055.481877] iwlwifi 0000:03:00.0: 0xFFFF8801 | isr_pref
[24055.481879] iwlwifi 0000:03:00.0: 0x3F7517B0 | wait_event
[24055.481881] iwlwifi 0000:03:00.0: 0xFFFF8801 | l2p_control
[24055.481883] iwlwifi 0000:03:00.0: 0x3F7517B8 | l2p_duration
[24055.481886] iwlwifi 0000:03:00.0: 0xFFFF8801 | l2p_mhvalid
[24055.481888] iwlwifi 0000:03:00.0: 0x3F751818 | l2p_addr_match
[24055.481890] iwlwifi 0000:03:00.0: 0xFFFF8801 | lmpm_pmg_sel
[24055.481892] iwlwifi 0000:03:00.0: 0x3F7517C8 | timestamp
[24055.481894] iwlwifi 0000:03:00.0: 0xFFFF8801 | flow_handler
[24055.499039] WARNING: CPU: 1 PID: 975 at /build/buildd/linux-3.13.0/drivers/net/wireless/iwlwifi/dvm/../iwl-trans.h:743 iwl_dump_nic_event_log+0x330/0x370 [iwldvm]()
[24055.499041] Modules linked in: ses enclosure usb_storage bbswitch(OF) pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) ctr ccm rfcomm bnep binfmt_misc joydev uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev snd_hda_codec_realtek arc4 iwldvm mac80211 mxm_wmi btusb bluetooth intel_powerclamp coretemp kvm_intel kvm snd_hda_intel snd_hda_codec snd_hwdep psmouse snd_pcm serio_raw snd_page_alloc intel_ips parport_pc snd_seq_midi snd_seq_midi_event snd_rawmidi lpc_ich iwlwifi ppdev snd_seq cfg80211 snd_seq_device snd_timer snd soundcore lp parport i915 drm_kms_helper wmi video drm mei_me mei asus_laptop i2c_algo_bit sparse_keymap input_polldev mac_hid ahci libahci atl1c
[24055.499130]  [<ffffffffa0555500>] iwl_dump_nic_event_log+0x330/0x370 [iwldvm]
[24055.499134]  [<ffffffffa0555580>] iwl_nic_error+0x40/0x50 [iwldvm]
[24055.499146]  [<ffffffffa02ad5b0>] iwl_trans_pcie_send_hcmd+0x5b0/0x690 [iwlwifi]
[24055.499158]  [<ffffffffa055e556>] iwl_dvm_send_cmd+0x46/0x110 [iwldvm]
[24055.499164]  [<ffffffffa05680d8>] iwlagn_request_scan+0x888/0xcc0 [iwldvm]
[24055.499170]  [<ffffffffa05687ab>] iwl_scan_initiate+0xeb/0x180 [iwldvm]
[24055.499175]  [<ffffffffa055850a>] iwlagn_mac_hw_scan+0x8a/0x120 [iwldvm]
[24055.516412] WARNING: CPU: 1 PID: 975 at /build/buildd/linux-3.13.0/drivers/net/wireless/iwlwifi/dvm/../iwl-trans.h:743 iwl_dump_nic_event_log+0x30d/0x370 [iwldvm]()
[24055.516413] Modules linked in: ses enclosure usb_storage bbswitch(OF) pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) ctr ccm rfcomm bnep binfmt_misc joydev uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev snd_hda_codec_realtek arc4 iwldvm mac80211 mxm_wmi btusb bluetooth intel_powerclamp coretemp kvm_intel kvm snd_hda_intel snd_hda_codec snd_hwdep psmouse snd_pcm serio_raw snd_page_alloc intel_ips parport_pc snd_seq_midi snd_seq_midi_event snd_rawmidi lpc_ich iwlwifi ppdev snd_seq cfg80211 snd_seq_device snd_timer snd soundcore lp parport i915 drm_kms_helper wmi video drm mei_me mei asus_laptop i2c_algo_bit sparse_keymap input_polldev mac_hid ahci libahci atl1c
[24055.516480]  [<ffffffffa05554dd>] iwl_dump_nic_event_log+0x30d/0x370 [iwldvm]
[24055.516484]  [<ffffffffa0555580>] iwl_nic_error+0x40/0x50 [iwldvm]
[24055.516492]  [<ffffffffa02ad5b0>] iwl_trans_pcie_send_hcmd+0x5b0/0x690 [iwlwifi]
[24055.516502]  [<ffffffffa055e556>] iwl_dvm_send_cmd+0x46/0x110 [iwldvm]
[24055.516507]  [<ffffffffa05680d8>] iwlagn_request_scan+0x888/0xcc0 [iwldvm]
[24055.516512]  [<ffffffffa05687ab>] iwl_scan_initiate+0xeb/0x180 [iwldvm]
[24055.516516]  [<ffffffffa055850a>] iwlagn_mac_hw_scan+0x8a/0x120 [iwldvm]
[24055.533705] WARNING: CPU: 1 PID: 975 at /build/buildd/linux-3.13.0/drivers/net/wireless/iwlwifi/dvm/../iwl-trans.h:743 iwl_dump_nic_event_log+0x346/0x370 [iwldvm]()
[24055.533706] Modules linked in: ses enclosure usb_storage bbswitch(OF) pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) ctr ccm rfcomm bnep binfmt_misc joydev uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev snd_hda_codec_realtek arc4 iwldvm mac80211 mxm_wmi btusb bluetooth intel_powerclamp coretemp kvm_intel kvm snd_hda_intel snd_hda_codec snd_hwdep psmouse snd_pcm serio_raw snd_page_alloc intel_ips parport_pc snd_seq_midi snd_seq_midi_event snd_rawmidi lpc_ich iwlwifi ppdev snd_seq cfg80211 snd_seq_device snd_timer snd soundcore lp parport i915 drm_kms_helper wmi video drm mei_me mei asus_laptop i2c_algo_bit sparse_keymap input_polldev mac_hid ahci libahci atl1c
[24055.533769]  [<ffffffffa0555516>] iwl_dump_nic_event_log+0x346/0x370 [iwldvm]
[24055.533773]  [<ffffffffa0555580>] iwl_nic_error+0x40/0x50 [iwldvm]
[24055.533781]  [<ffffffffa02ad5b0>] iwl_trans_pcie_send_hcmd+0x5b0/0x690 [iwlwifi]
[24055.533791]  [<ffffffffa055e556>] iwl_dvm_send_cmd+0x46/0x110 [iwldvm]
[24055.533796]  [<ffffffffa05680d8>] iwlagn_request_scan+0x888/0xcc0 [iwldvm]
[24055.533801]  [<ffffffffa05687ab>] iwl_scan_initiate+0xeb/0x180 [iwldvm]
[24055.533805]  [<ffffffffa055850a>] iwlagn_mac_hw_scan+0x8a/0x120 [iwldvm]
[24055.551100] WARNING: CPU: 1 PID: 975 at /build/buildd/linux-3.13.0/drivers/net/wireless/iwlwifi/dvm/../iwl-trans.h:743 iwl_dump_nic_event_log+0x369/0x370 [iwldvm]()
[24055.551101] Modules linked in: ses enclosure usb_storage bbswitch(OF) pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) ctr ccm rfcomm bnep binfmt_misc joydev uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev snd_hda_codec_realtek arc4 iwldvm mac80211 mxm_wmi btusb bluetooth intel_powerclamp coretemp kvm_intel kvm snd_hda_intel snd_hda_codec snd_hwdep psmouse snd_pcm serio_raw snd_page_alloc intel_ips parport_pc snd_seq_midi snd_seq_midi_event snd_rawmidi lpc_ich iwlwifi ppdev snd_seq cfg80211 snd_seq_device snd_timer snd soundcore lp parport i915 drm_kms_helper wmi video drm mei_me mei asus_laptop i2c_algo_bit sparse_keymap input_polldev mac_hid ahci libahci atl1c
[24055.551148]  [<ffffffffa0555539>] iwl_dump_nic_event_log+0x369/0x370 [iwldvm]
[24055.551151]  [<ffffffffa0555580>] iwl_nic_error+0x40/0x50 [iwldvm]
[24055.551157]  [<ffffffffa02ad5b0>] iwl_trans_pcie_send_hcmd+0x5b0/0x690 [iwlwifi]
[24055.551164]  [<ffffffffa055e556>] iwl_dvm_send_cmd+0x46/0x110 [iwldvm]
[24055.551169]  [<ffffffffa05680d8>] iwlagn_request_scan+0x888/0xcc0 [iwldvm]
[24055.551174]  [<ffffffffa05687ab>] iwl_scan_initiate+0xeb/0x180 [iwldvm]
[24055.551178]  [<ffffffffa055850a>] iwlagn_mac_hw_scan+0x8a/0x120 [iwldvm]
[24055.551250] iwlwifi 0000:03:00.0: Log capacity -1515870811 is bogus, limit to 128 entries
[24055.551253] iwlwifi 0000:03:00.0: Log write index -1515870811 is bogus, limit to 128
[24055.551255] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[24057.326150] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 0 [0x5a5a5a5a]
[24059.101268] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 2 [0x5a5a5a5a]
[24060.910246] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 5 [0x5a5a5a5a]
[24062.685241] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 7 [0x5a5a5a5a]
[24064.435590] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[24064.504708] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
[24070.189967] iwlwifi 0000:03:00.0: Failed to load firmware chunk!
[24070.189977] iwlwifi 0000:03:00.0: Could not load the [0] uCode section
[24070.189986] iwlwifi 0000:03:00.0: Failed to start RT ucode: -110
[24071.966363] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 0 [0x5a5a5a5a]
[24073.747574] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 2 [0x5a5a5a5a]
[24075.557132] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 5 [0x5a5a5a5a]
[24077.332825] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 7 [0x5a5a5a5a]
[24079.104086] iwlwifi 0000:03:00.0: Unable to initialize device.
[24116.110282] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[24179.067457] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[24242.031168] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[24304.988974] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[24356.406501] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[24382.028236] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[24384.939353] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[24407.941422] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[24440.956176] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[24483.969163] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[24536.988816] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[24599.998121] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[24662.993680] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[24725.982612] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[24788.977836] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[24851.966962] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[24914.961811] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[24977.951484] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[25040.946212] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[25103.935226] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[25166.930671] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[25229.919179] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[25292.916060] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[25355.903971] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[25418.899089] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[25481.887795] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[25544.883516] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[25607.872014] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[25670.867769] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[25733.856891] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[25796.852022] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[25859.840964] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[25922.836133] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[25985.825614] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[26048.821214] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[26111.809538] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[26174.804720] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[26237.793749] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[26300.789191] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[26363.777834] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[26426.773355] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[26489.762001] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[26552.757777] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[26615.746856] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[26678.743648] iwlwifi 0000:03:00.0: Request scan called when driver not ready.
[26683.398568] iwlwifi 0000:03:00.0: Request scan called when driver not ready.


########## wireless info END ############

```

---

### Post by 3vilpad on 2014-05-12
I'm starting to feel a bit like... alone... in desert. If I commited something wrong, then im sorry, I really tried to find solution to my problem, but nothing seems to work. It would be great if someone could help me determine the source of the problem, if it's even possible with the informations I included. If not then please say so. Thank you in advance.

---

