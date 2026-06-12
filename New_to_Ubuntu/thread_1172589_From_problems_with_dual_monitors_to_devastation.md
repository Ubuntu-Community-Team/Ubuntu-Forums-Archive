---
title: "From problems with dual monitors to devastation"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by dbvaio on 2009-05-28
The trouble started when I attempted to temporarily attach a monitor to my laptop. I eventually figured out that whole mess but it left me with no desktop effects. I had that problem when I first upgraded to Ubuntu 9.04 but I thought I had fixed it (if only I could remember how). After extensive searching through forums I tried to tweak compiz settings ... fail... Then I saw some stuff about messing with xorg and I tried tweaking the resolution in the xorg.conf file ... epic fail... finally I tried reinstalling compiz and anything else graphic related that I could find and restarted ... epic doom fail ... now I can't get to the login screen, can't get to the terminal unless I use recovery mode (again not much success there), and am pretty much stuck using a usb startup disk and/or windows (don't mind the disk but I'd like to avoid windows). Here's some info that might be helpful. 

lshw info (I'll try and trim some unnecessary info)
sudo lshw
ubuntu                    
    description: Notebook
    product: VGN-N350E
    vendor: Sony Corporation
    version: C3LP32EW
    serial: 28204232-3007739
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=2 uuid=D29B70E0-F298-11DB-8948-0013A9C8A26C
  *-core
       description: Motherboard
       product: VAIO
       vendor: Sony Corporation
       physical id: 0
       version: N/A
       serial: N/A
       slot: &#65533;&#65533;@
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0100J4 (02/08/2007)
          size: 99KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int9keyboard int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          slot: N/A
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor est tm2 xtpr pdcm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3 Cache
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: SODIMM
             physical id: 0
             slot: SODIMM1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: SODIMM
             physical id: 1
             slot: SODIMM2
             size: 512MiB
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller




Hopefully that's enough info, I'm more than willing to supply any other bits of information. Thank you in advance. 

Dustin

---

### Post by The Cog on 2009-05-28
That happened to me last week. In my case, I found that trying to configure the second monitor had added some lines to xorg.conf. Fortunately, it had created a backup xorg.conf that had a date stamp on the end, and copying that back to xorg.conf allowed compix to be re-enabled.

---

### Post by ssanders4917 on 2009-05-28
I am not a super brain on the issue but i know that you mess with the config files when you know exactly what you are doing. I learned the hard way try to enable 3D on a ATi card. I messed with config files and my final solution was just a fresh install.

---

### Post by dbvaio on 2009-05-28
The Cog:
For some reason it didn't create a backup at the time. Afterward I tried messing with it some more and I noticed some backups. Nothing useful though. Thanks for the info though. 

ssanders4917:
I was going off of a guide for the xorg.conf file. Hopefully I can get to the point where I don't need to do a fresh install but at least it's an option. Thanks for the input.

---

### Post by fatality_uk on 2009-05-28
A quick and dirty way back.
Have you tried copying your xorg.conf from your livecd to your install?

---

### Post by dbvaio on 2009-05-28
fatality_uk:
Yes a couple times actually. I've been at this for hours and I'm sure I'm just making things worse. I think it could possibly be something other than xorg causing the problems but I have no clue. Thank you though

---

