---
title: "help: cpu whine &gt; max_cstate=2 &gt; heat &amp; fan noise"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by Knacker on 2010-01-26
hi, 
when i upgraded to karmic, the old cpu whine that i used to experience with older versions of ubuntu returned. annoyed by this, but whatever. i followed this: 
[http://ubuntuforums.org/showthread.php?t=1303594](http://ubuntuforums.org/showthread.php?t=1303594)

and the whine stopped. unfortunately, my cpu fan is now constantly running like crazy and that worries me. is it possible that this "fix" has created a new problem? how would i determine if this has happened? finally, how do i stop the fan from running constantly without causing any problems? 

really hope someone can help me. i have no idea how to fix this.
thanks.

---

### Post by Knacker on 2010-01-27
am i missing something obvious? anybody?

---

### Post by warfacegod on 2010-01-27
What kind of computer? What are the hardware specs (sudo lshw), etc. etc.

---

### Post by Knacker on 2010-01-27
> **warfacegod said:**
> What kind of computer? What are the hardware specs (sudo lshw), etc. etc.

Thank you for trying to help! 

Here, I think, is the relevant part of what i get back from sudo lshw:
```

vendor: LENOVO
    version: ThinkPad T61
    serial: L3D1197
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=normal chassis=notebook cpus=2 frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=363D8E81-497B-11CB-A243-EC3BD716EA27
  *-core
       description: Motherboard
       product: 766405U
       vendor: LENOVO
       physical id: 0
       version: Not Available
       serial: VF17B7AK1PV
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 7LET51WW (1.21 ) (08/22/2007)
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom edd acpi usb biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          slot: None
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: c
             slot: Internal L2 Cache
             size: 4MiB
             capabilities: burst internal write-back unified
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
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 2b
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: DIMM 1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: DIMM 2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          capabilities: vmx ht cpufreq
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
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:2000(size=4096) memory:d4000000-d6ffffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Quadro NVS 140M
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:d6000000-d6ffffff memory:e0000000-effff
```

---

### Post by warfacegod on 2010-01-27
Are you using 32 or 64 Bit Ubuntu?

---

### Post by Knacker on 2010-01-30
> **warfacegod said:**
> Are you using 32 or 64 Bit Ubuntu?

sorry for slow response...work. 
i'm using 32bit ubuntu.

---

### Post by warfacegod on 2010-01-30
> **Knacker said:**
> sorry for slow response...work. 
i'm using 32bit ubuntu.

You have 64 Bit hardware. There is nothing wrong with using 32 on a 64 machine but you'll probably get better performance performance if you switch. I suspect your issue can up from doing an upgrade install as opposed to a fresh install.

If it's only the fan running at full speed there really shouldn't be any problem except the noise. It's not going to hurt the other parts in your laptop. Watch your System Monitor or use "top" in Terminal to make sure your CPU isn't running at 100% all the time.

---

