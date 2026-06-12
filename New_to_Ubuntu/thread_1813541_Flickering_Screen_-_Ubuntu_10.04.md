---
title: "Flickering Screen - Ubuntu 10.04"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by Lauren03001 on 2011-07-27
So from doing some googling I've found that my problem is not a terribly uncommon problem, but being a total computer moron I have no idea which fix is right for my computer ...

I just upgraded to Ubuntu 10.04 and my screen flickers every once in a while.  The flickering is horizontal multi colored lines across the lower half of the screen, and there doesn't seem to be any pattern to why or when it happens.  The lines occasionally freeze on the screen until I do something else.

From what I've read, it sounds like the default video driver is too advanced for my old computer and there is a simple fix if I uninstall that driver and replace it with the and older one.  However, I have no idea how to figure out which driver I need.  I'm a little horrified of just guessing, especially since I'm not 100% sure the driver is in fact the problem.

My computer is a Dell Inspiron 1545, and I bought it I think 3 years ago?  And of course I have no record of what my video card specs are ...

---

### Post by trustinglittle on 2011-07-27
HEllo don't know if I can help but lets start with this

run the following in Application>Accessories>terminal

sudo lshw

then post the output to here.

---

### Post by Lauren03001 on 2011-07-27
here is up through the display info:

dell-desktop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1976MiB
     *-cpu
          product: Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm cpufreq
          configuration: id=0
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
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:30 memory:f6c00000-f6ffffff memory:e0000000-efffffff(prefetchable) ioport:efe8(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:f6b00000-f6bfffff

---

