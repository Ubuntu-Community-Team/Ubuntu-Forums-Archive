---
title: "I'm getting lock ups and restarts. Please help me."
date: 2009-05-24
forum: New to Ubuntu
---

### Post by mvalviar on 2009-05-24
I just moved to a new apartment 1 week ago and my ubuntu pc started acting up. I get sporadic lock ups or restarts. I tried it with an XP hard drive and it works fine. Can anyone tell me what to do? 

Whenever I have compiz on it happens much often. But it also happens even if I'm using metacity.

I've been down this road before ([http://ubuntuforums.org/showthread.php?t=995739]("http://ubuntuforums.org/showthread.php?t=995739")). I have my sensors and they read CPU: 40, GPU:68, HD:44 (all in celsius) should I be concerned with those figures?

```

mumee
    description: Desktop Computer
    product: 945GCT-M2
    vendor: ECS
    version: 1.x
    serial: 1131
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: 945GCT-M2
       vendor: ECS
       physical id: 0
       version: ECS
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012 (02/18/2008)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.6.5
          serial: 0000-0F65-0000-0000-0000-0000
          slot: CPU 1
          size: 2403MHz
          capacity: 2403MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM [empty]
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
        *-bank:1
             description: DIMM [empty]
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
        *-bank:2
             description: DIMM SDRAM Synchronous
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM2
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.6.5
          serial: 0000-0F65-0000-0000-0000-0000
          size: 2403MHz
          capacity: 2403MHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 7100 GS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-network:0
                description: Wireless interface
                product: AR2413 802.11bg NIC
                vendor: Atheros Communications Inc.
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: wmaster0
                version: 01
                serial: 00:14:78:ec:09:8c
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k_pci latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 10
                serial: 00:1e:90:f4:20:72
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.100 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: ST320014A
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.07
                serial: 5JZAY23Z
                size: 18GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=fc0e78df
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: e18875f4-6abd-4536-b18a-30c82ff0a1ac
                   size: 5718MiB
                   capacity: 5718MiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-04-24 06:05:54 filesystem=ext3 modified=2009-05-25 02:39:41 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-05-25 02:29:48 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 13GiB
                   capacity: 13GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 486MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 12GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered state=mounted
           *-cdrom
                description: CD-R/CD-RW writer
                product: CD-R/RW SH-R522C
                vendor: TSSTcorp
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TS04
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 82:34:4a:ae:ae:6e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Thats a complete hardware list. I'm using ubuntu Jaunty. Please help me.

---

### Post by Uzi304 on 2009-05-24
Were you using Jaunty before you moved? I ask this because Jaunty and certain Intel graphics card don't get along very well so I think that's your problems. If that is the case then there are a few workarounds that you can try.

One: You can go into your xorg.conf(/etc/X11/xorg.conf) and enable UXA by adding the line ```
Option          "AccelMethod"                   "uxa"
``` under the section where it says Section "Device". 

Two: You can revert back to the Intrepid Intel driver if that worked better for you by following the instructions [here]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

Three: You can upgrade to an unsupported kernel that has helped numerous people by following the instructions [here]("http://ubuntuforums.org/showthread.php?t=1130582&highlight=command%3F")

---

### Post by mvalviar on 2009-05-24
Yes, I was using Jaunty. But I'll be moving so I lost my internet connection for a week. I wasnt getting any updates the entire time and everything is working fine. On the day I moved I got my connection back and I installed updates. Just a few minutes later and I got my first lock-up. 

I asked in ubuntu IRC about this an someone suggested that perhaps its compiz. I'm not getting that much lock up when I turn compiz off. But still happens.

Does this really happen with other users? I thought GNU/Linux is supposed to be crash proof.

---

### Post by Cresho on 2009-05-24
I don't know about you but I know that power is needed.  If you have bad home circuit, your pc will either die sooner, crash, even not boot at all


I'm goinb by what you said.
"I just moved to a new apartment 1 week ago and my ubuntu pc started acting up." 

and ever since I updated my girfriends home electrical system, her pc runs fine.

you may need a power massager to correct bad spikes in your home.  Most problems are related to bad power or memory.  xp seems to run less power since compiz is not enabled.  Jaunty runs hotter than other OS's.  I mean hotter because it makes mines crawl to my knees.

---

### Post by mvalviar on 2009-05-24
> **Uzi304 said:**
> Were you using Jaunty before you moved? I ask this because Jaunty and certain Intel graphics card don't get along very well so I think that's your problems. If that is the case then there are a few workarounds that you can try.

One: You can go into your xorg.conf(/etc/X11/xorg.conf) and enable UXA by adding the line ```
Option          "AccelMethod"                   "uxa"
``` under the section where it says Section "Device". 

Two: You can revert back to the Intrepid Intel driver if that worked better for you by following the instructions [here]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

Three: You can upgrade to an unsupported kernel that has helped numerous people by following the instructions [here]("http://ubuntuforums.org/showthread.php?t=1130582&highlight=command%3F")

Maybe this is what I'm looking for. I skimmed through the links you gave. There are lots of mentions regarding crashes on one of the link. I tried to play a vid full screen and I got a crash (although I played vids fullscreen before and I didn't get a crash). 

I tried the 3rd option. One question though. I went to a virtual terminal to restart the gdm. it said stopping...[OK] starting...[failed] is that normal? I assumed it is because went back to ctrl-alt-f7 and I still have access to the desktop.

I hope this works.

---

### Post by clhsharky on 2009-05-24
It might be time open up it up and clean. I have to do it twice a year, here where I live.

---

### Post by mvalviar on 2009-05-24
I just did that. I lesson I learned from a previous thread I wrote regarding lock-ups. 

I'll just wait if Uzi's suggestion works. (fingers crossed)

---

### Post by Uzi304 on 2009-05-24
Well if you were using the same PC with Jaunty before you moved, I'm not so sure that the graphics card is your problem but it very well could be because you said it crashed when trying to watch a video. Either way, it can't hurt to try. Tell us how it works out for you.

---

### Post by Cresho on 2009-05-24
its power related from home circuit

---

### Post by CBHedricks on 2009-05-24
When you move from one site to another you can have more than one issue crop up.  In your situation I would look at resetting the graphic card (if possible) then the memory and other PCI cards that might be in your system.

Secondly - the temperatures are not too bad for a home that is rather cool.  If you are going to have a hot summer I would watch the temps closely to make sure it does not overheat.

Third - I agree that you should look into a good battery backup that also has 'line conditioning' or Automatic Voltage Regulation circuitry as well.  This will stabilize the incoming power so your computer does not get hit with fluctuations.

Lastly - make sure your power supply is not pushing really hot air out.  If there is a large difference between the temperature in your case and the power supply exhaust you should look for a new and stronger power supply.  The proper size power supply should only run slightly warmer than the air in the case.

Hope that helps.

CB

---

### Post by Cresho on 2009-05-24
> **CBHedricks said:**
> When you move from one site to another you can have more than one issue crop up.  In your situation I would look at resetting the graphic card (if possible) then the memory and other PCI cards that might be in your system.

Secondly - the temperatures are not too bad for a home that is rather cool.  If you are going to have a hot summer I would watch the temps closely to make sure it does not overheat.

Third - I agree that you should look into a good battery backup that also has 'line conditioning' or Automatic Voltage Regulation circuitry as well.  This will stabilize the incoming power so your computer does not get hit with fluctuations.

Lastly - make sure your power supply is not pushing really hot air out.  If there is a large difference between the temperature in your case and the power supply exhaust you should look for a new and stronger power supply.  The proper size power supply should only run slightly warmer than the air in the case.

Hope that helps.

CB

ya like this guy and the guy before stated with the cleaning of the heatsinks inside your pc.

---

### Post by mvalviar on 2009-05-26
Uzi's 3rd suggestion works. I'm not getting any hangs or restarts anymore. Although compiz still crashes (as it always do sometimes) metacity happily takes over without a problem. Thanks y'all

---

