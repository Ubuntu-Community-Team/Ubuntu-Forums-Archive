---
title: "Movie player doesn't work properly"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by hadi3457 on 2010-05-14
Hello!
I have a Karmic on my system and get movie player codecs. when I run it. at first start to play for 20 or 30 second and after that suddenly lose voice. still I have video without sound. I test my sources but there are true. test vlc too but still have problem.
my system info: processor 1100 Mhz  intel celeron
When I open more than one window my CPU work with 100% usage but for movie player it works alone in 100% (and vlc too)
thank you for your info share

---

### Post by nhasian on 2010-05-14
post your system specs.  maybe you need more ram or switch to Lubuntu instead.

---

### Post by wojox on 2010-05-14
It asks you if you want to download codecs?

---

### Post by hadi3457 on 2010-05-14
about specs: I don't know what is it and how I can find it
but about codecs: I click on a AVI format file and movie palyer ask about download adn I allow to download but I'm not sure that is codecs.

---

### Post by wojox on 2010-05-14
Add medibuntu [http://wojox.homelinux.org/?p=12](http://wojox.homelinux.org/?p=12)

If your not using lucid just change it to what your running.

Then you can install non-free-codecs.

---

### Post by nhasian on 2010-05-14
vlc has all the codecs built in, so if the problem persists with vlc its not a codec problem.

open a terminal from Applications-> Accessories and copy/paste the following command:

```
lshw -C display,cpu,memory
```

then you can post back the data here.

---

### Post by hadi3457 on 2010-05-15
Hi again and thank you. This is code:
```

root@zxc:~# lshw -C display,cpu,memory
  *-firmware              
       description: BIOS
       vendor: Award Software, Inc.
       physical id: 0
       version: ASUS TUSI-M ACPI BIOS Revision 1017 (09/18/2002)
       size: 64KiB
       capacity: 448KiB
       capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi agp
  *-cpu
       description: CPU
       product: Intel(R) Celeron(TM) CPU                1100MHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.11.1
       slot: PGA 370
       size: 1100MHz
       capacity: 1600MHz
       width: 32 bits
       clock: 100MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up
     *-cache:0
          description: L1 cache
          physical id: 8
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: pipeline-burst synchronous internal write-back data
     *-cache:1
          description: L2 cache
          physical id: 9
          slot: L2 Cache
          size: 256KiB
          capacity: 256KiB
          capabilities: pipeline-burst synchronous internal write-back data
  *-memory
       description: System Memory
       physical id: 22
       slot: System board or motherboard
       size: 384MiB
       capacity: 512MiB
     *-bank:0
          description: DIMM DRAM Synchronous
          physical id: 0
          slot: DIMM 1
          size: 256MiB
          width: 64 bits
     *-bank:1
          description: DIMM DRAM Synchronous
          physical id: 1
          slot: DIMM 2
          size: 128MiB
          width: 64 bits
  *-display
       description: VGA compatible controller
       product: 630/730 PCI/AGP VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 21
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 cap_list rom
       configuration: driver=sisfb latency=0
       resources: irq:11 memory:f0000000-f7ffffff(prefetchable) memory:ea000000-ea01ffff ioport:a800(size=128)

```

---

### Post by nhasian on 2010-05-15
unfortunately your system does not meet the minimum system requirements for Ubuntu.  See [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

For a better user experience, please try [Lubuntu]("http://lubuntu.net/")

---

