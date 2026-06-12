---
title: "Older wifi card, recognised but not working"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by stormvinyl on 2009-11-11
Im installing 9.10 on my sons desktop, dell, with older wireless card.  When running sudo lshw I get that the card is there with driver but it is disabled.  When I use the network tools under admin it looks like there are two wireless cards, perhaps two drivers are loaded?  One says "unknown interface (wifi0)" and one says "wireless interface (wlan0)" then I have the "ethernet interface (eth0)".  Ill attach the terminal outputs for different commands so you can see whats going on.  Any help would be greatly appreciated.  Ive been using windows since 3.0 and some Dos, but am very new to linux.  I have also tried to use the wireless troubleshooting guide on line but to no avail.


chris@chris-desktop:~$ sudo lshw
[sudo] password for chris: 
chris-desktop             
    description: Mini Tower Computer
    product: Dimension 8400
    vendor: Dell Inc.
    serial: 2SZ2P51
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=44454C4C-5300-105A-8032-B2C04F503531
  *-core
       description: Motherboard
       product: 0J3492
       vendor: Dell Inc.
       physical id: 0
       serial: ..CN4811148802N0.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A01 (07/17/2004)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: Microprocessor
          size: 3GHz
          capacity: 3600MHz
          width: 32 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 1MiB
             capacity: 1MiB
             capabilities: internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: DIMM SDRAM Synchronous 533 MHz (1.9 ns)
             physical id: 0
             slot: CHANNEL A DIMM 0
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 533 MHz (1.9 ns)
             physical id: 1
             slot: CHANNEL B DIMM 0
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 533 MHz (1.9 ns) [empty]
             physical id: 2
             slot: CHANNEL A DIMM 1
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM SDRAM Synchronous 533 MHz (1.9 ns)
             physical id: 3
             slot: CHANNEL B DIMM 1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: 82925X/XE Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82925X/XE PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 memory:dd000000-dfefffff memory:c0000000-cfffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: G72 [GeForce 7300 LE]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list
                configuration: latency=0
                resources: memory:dd000000-ddffffff memory:c0000000-cfffffff(prefetchable) memory:de000000-deffffff memory:dfe00000-dfe1ffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 memory:dcf00000-dcffffff
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:11:11:3d:97:8e
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5751-v3.23a ip=192.168.2.9 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:16 memory:dcff0000-dcffffff
        *-pci:2
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 memory:dce00000-dcefffff
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:ff80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:ff60(size=32)
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff20(size=32)
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:21 memory:ffa80800-ffa80bff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:d0000000(size=1048576)
           *-network DISABLED
                description: Wireless interface
                product: Prism 2.5 Wavelan chipset
                vendor: Intersil Corporation
                physical id: 1
                bus info: pci@0000:04:01.0
                logical name: wifi0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list logical wireless ethernet physical
                configuration: broadcast=yes driver=hostap firmware=0.0.0 latency=64 multicast=yes wireless=IEEE 802.11-DS
                resources: irq:17 memory:d0000000-d0000fff(prefetchable)
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:23 ioport:ec00(size=256) ioport:e8c0(size=64) memory:dffffe00-dfffffff memory:dffffd00-dffffdff
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FR/FRW (ICH6R/ICH6RW) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD800JD-75HK
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 14.0
                serial: WD-WMAJ95348747
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d0b2d0b2
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 0a29ee81-e4be-4dd3-8b0f-d3b77bafa393
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-11-10 07:58:11 filesystem=ext4 lastmountpoint=/&#65533;ew&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;B&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;iW&#65533;(&#65533;&#65533;&#65533;&#65533;&#65533;(&#65533;&#65533;&#65533;&#65533;&#65533;w&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Y&#65533;w&#65533;&#65533;&#65533;&#65533;%&#65533;&#65533; modified=2009-11-10 08:14:30 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-11-11 08:34:39 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 3153MiB
                   capacity: 3153MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3153MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:e8a0(size=32)

chris@chris-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd_seq_dummy           2656  0 
hostap_pci             48652  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
hostap                103360  1 hostap_pci
snd_rawmidi            22208  1 snd_seq_midi
lib80211                6432  2 hostap_pci,hostap
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
x_tables               16544  1 ip_tables
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
orinoco_pci             4700  0 
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
orinoco                63600  1 orinoco_pci
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
dell_wmi                2564  0 
dcdbas                  7292  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
serio_raw               5280  0 
usbhid                 38208  0 
tg3                   109600  0 


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11-DS  Mode:Managed  
          
wlan0     IEEE 802.11-DS  Mode:Managed  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

chris@chris-desktop:~$ 


If you need any other info, please reply and Ill get it to you.
Thanks ladies and gentlemen
Jim

---

### Post by ukripper on 2009-11-11
Can you post output of the following command:
```
lspci
```

---

### Post by stormvinyl on 2009-11-11
yep here ya go.

chris@chris-desktop:~$ sudo lspci
[sudo] password for chris: 
00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
04:01.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
chris@chris-desktop:~$

---

### Post by ukripper on 2009-11-11
Looks like you have got that nasty Prism 2.5 card. 

Follow the steps below taken from bug report filed on launchpad ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/104551](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/104551)) The reason mentioned there is "The problem is that the hostap and orinoco kernel modules are competing for control of the card." And workaround is as below:
> 1) Confirm you have the same kind of wireless card:

brett@boca:~$ lspci | grep Network
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

2) If so, add the following to /etc/modprobe/blacklist:

(as root, ie. $sudo vi /etc/modprobe.d/blacklist, or $sudo gedit /etc/modprobe.d/blacklist, and add the following lines)

blacklist orinoco
blacklist orinoco_pci
blacklist hermes
blacklist p80211
blacklist prism2_pci

Note that you have the option of blacklisting either the hostap modules or the orinoco ones, but the hostap are considerable more capable under NetworkManager, so keep the hostap ones (hostap, hostap_pci, plus ieee80211_crypt for any WPA card -- not specific to this one) which will all load by default. I was surprised I had to blacklist p80211 and prism2_pci, but it didn't fully work otherwise ... perhaps someone else can reason why.

3) reboot

After this, all should work nicely.

---

### Post by stormvinyl on 2009-11-11
Still inop.  After browsing through [http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/) it looks like I might need to update firmware on card.  It doesnt want to respond when I try to get firmware ver.  Heres what I get.


hostap_diag wlan0
ioctl[PRISM2_IOCTL_HOSTAPD]: Inappropriate ioctl for device
Could not communicate with the kernel driver.
chris@chris-desktop:~$ 

Im not sure exactly what this means but any help would be appreciated.

---

### Post by ukripper on 2009-11-11
> **stormvinyl said:**
> Still inop.  After browsing through [http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/) it looks like I might need to update firmware on card.  It doesnt want to respond when I try to get firmware ver.  Heres what I get.


hostap_diag wlan0
ioctl[PRISM2_IOCTL_HOSTAPD]: Inappropriate ioctl for device
Could not communicate with the kernel driver.
chris@chris-desktop:~$ 

Im not sure exactly what this means but any help would be appreciated.


Before flashing your card can you take "blacklist orinoco" and "blacklist orinoco_pci" out of blacklist file and then reboot and see if card comes alive.

---

### Post by stormvinyl on 2009-11-11
Hmm.  Still nothing.  Im getting ready to hard line it and connect directly to the router. Starting to drive me nuts.

---

