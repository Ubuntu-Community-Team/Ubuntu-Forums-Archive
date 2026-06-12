---
title: "Screen resolution nightmare"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by phillymatt on 2011-02-02
I'm trying to give Linux another try, but it won't load the correct screen resolution. I have searched the forums, seen that other people have this problem, but don't understand what the instructions are asking me to do.

I go to System, Preferences, Monitors, and I get this error:

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

If I click on "No" I am taken to my Monitor Preferences window. Here when I click on 'Resolution" my only options are 800x600 and 640x480.

Alternatively, when I click on "Yes" I am taken to my Nvidia X Server Setting window. Here I am given the error:

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

So I go into my terminal, type 'sudo su' for root and then type `nvidia-xconfig`. I then hit Ctrl+Alt+Backspace to restart the X Server. When I log in again and return to the Moniters, the same errors come up. Help???

---

### Post by sydbat on 2011-02-02
> **phillymatt said:**
> I'm trying to give Linux another try, but it won't load the correct screen resolution. I have searched the forums, seen that other people have this problem, but don't understand what the instructions are asking me to do.

I go to System, Preferences, Monitors, and I get this error:

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

If I click on "No" I am taken to my Monitor Preferences window. Here when I click on 'Resolution" my only options are 800x600 and 640x480.

Alternatively, when I click on "Yes" I am taken to my Nvidia X Server Setting window. Here I am given the error:

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

So I go into my terminal, type 'sudo su' for root and then type `nvidia-xconfig`. I then hit Ctrl+Alt+Backspace to restart the X Server. When I log in again and return to the Moniters, the same errors come up. Help???Some more info will help us help you.

What is your graphics card?
Which version of Ubuntu are you running?
Other info about your computer (RAM, CPU, etc)?

---

### Post by AlecJ on 2011-02-02
gksudo nvidia-settings

and then save settings to xorg.conf

---

### Post by phillymatt on 2011-02-02
> What is your graphics card?

I don't know, Nvidia but not sure about the model.

> Which version of Ubuntu are you running?

Ubuntu 10.04

Other info about your computer (RAM, CPU, etc)? 

Again, not sure.

EDIT: Specs are a few posts down.

---

### Post by phillymatt on 2011-02-02
> gksudo nvidia-settings

and then save settings to xorg.conf

I just tried this and nothing happened.

---

### Post by 1clue on 2011-02-02
You're using the generic driver.

You have 2 options, one is the 'nv' open-source driver or the other is the nvidia-supplied nvidia driver.  The nv driver is less functional but will get you everything except fancy desktop effects, dual monitor support and maybe some game performance.  You need to get into your package manager and search for 'nvidia' and make sure it's installed.

That said, I use nvidia's driver.  I have two monitors.

The nvidia control panel only works with the nvidia driver, not with nv.

---

### Post by phillymatt on 2011-02-02
For my specs, using $sudo lshw
```

description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1879MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     E8300  @ 2.83GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority cpufreq
     *-pci
          description: Host bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.2
             bus info: pci@0000:00:01.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.3
             bus info: pci@0000:00:01.3
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:5 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.4
             bus info: pci@0000:00:01.4
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:6 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.5
             bus info: pci@0000:00:01.5
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:7 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.6
             bus info: pci@0000:00:01.6
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:8 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP73 LPC Bridge
             vendor: nVidia Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: MCP73 SMBus
             vendor: nVidia Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=nForce2_smbus latency=0
             resources: irq:7 ioport:ff00(size=64) ioport:1c00(size=64) ioport:1c80(size=64)
        *-memory:9 UNCLAIMED
             description: RAM memory
             product: MCP73 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-processor UNCLAIMED
             description: Co-processor
             product: MCP73 Co-processor
             vendor: nVidia Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: latency=0 maxlatency=1 mingnt=3
             resources: memory:eff00000-eff7ffff
        *-memory:10 UNCLAIMED
             description: RAM memory
             product: MCP73 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.4
             bus info: pci@0000:00:03.4
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: GeForce 7100/nForce 630i USB
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:effff000-efffffff
        *-usb:1
             description: USB Controller
             product: MCP73 [nForce 630i] USB 2.0 Controller (EHCI)
             vendor: nVidia Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:efffe000-efffe0ff
        *-ide:0
             description: IDE interface
             product: MCP73 IDE
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
        *-multimedia
             description: Audio device
             product: MCP73 High Definition Audio
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
             resources: irq:23 memory:efff4000-efff7fff
        *-pci:0
             description: PCI bridge
             product: MCP73 PCI Express bridge
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
             resources: ioport:c000(size=4096) memory:efb00000-efbfffff memory:efa00000-efafffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: MCP73 PCI Express bridge
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:b000(size=4096) memory:ef900000-ef9fffff ioport:ef800000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: MCP73 PCI Express bridge
             vendor: nVidia Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:e000(size=4096) memory:ef700000-ef7fffff ioport:efe00000(size=1048576)
        *-pci:3
             description: PCI bridge
             product: MCP73 PCI Express bridge
             vendor: nVidia Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:d000(size=4096) memory:efd00000-efdfffff ioport:efc00000(size=1048576)
        *-ide:1
             description: IDE interface
             product: MCP73 IDE
             vendor: nVidia Corporation
             physical id: e
             bus info: pci@0000:00:0e.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
             resources: irq:27 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:f700(size=16) memory:efff8000-efff9fff
        *-network
             description: Ethernet interface
             product: MCP73 Ethernet
             vendor: nVidia Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: eth1
             version: a2
             serial: 00:01:2e:2a:37:f2
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes
             resources: irq:28 memory:efffd000-efffdfff ioport:f600(size=8) memory:efffc000-efffc0ff memory:efffb000-efffb00f
        *-display
             description: VGA compatible controller
             product: C73 [GeForce 7050 / nForce 610i]
             vendor: nVidia Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a2
             width: 64 bits
             clock: 66MHz
             capabilities: bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:22 memory:ed000000-edffffff memory:d0000000-dfffffff(prefetchable) memory:ee000000-eeffffff memory:80000000-8001ffff(prefetchable)
  *-network
```

---

### Post by AlecJ on 2011-02-02
You have loaded the Nvidia drivers from System/Administration/Additional Drivers

I'm on Version 173

---

### Post by phillymatt on 2011-02-02
> You're using the generic driver.

You have 2 options, one is the 'nv' open-source driver or the other is the nvidia-supplied nvidia driver. The nv driver is less functional but will get you everything except fancy desktop effects, dual monitor support and maybe some game performance. You need to get into your package manager and search for 'nvidia' and make sure it's installed.

That said, I use nvidia's driver. I have two monitors.

The nvidia control panel only works with the nvidia driver, not with nv.

OK, I went to system, administration, hardware drivers. There are two options:

Nvidia Accelerated Graphics Driver (version 173)
&
Nvidia Accelerated Graphics Driver (version current)[recommended]

The first option is checked. I'm going to try to switch and reboot. Will report back in a minute.

---

### Post by phillymatt on 2011-02-02
OK, so after reboot things were looking up: my login screen was in bautiful full resolution. However, after entering my password the screen went blank and my monitor shot up an "Input not Supported" error. 

After rebooting again, I was greeted with an error saying that:

"Ubuntu is running in low-graphics mode.

The following error was encountered. You may need to update your configuration.

(EE) Feb 02 20:15 NVIDIA(0) Failed to initialize the NVIDIA kernal module."

There were a couple more lines saying basically the same thing (if it helps I can go back and copy them down).

I then chose to run this session in low-graphics mode and here I am, in low resolution hell.

---

### Post by quesadilla on 2011-02-02
you can download the correct driver from the nvidia website. I did the same thing for my graphics card.

---

### Post by AlecJ on 2011-02-02
It's a prob lem card, but here is the driver, I guess your 32 bit there?


[http://www.nvidia.com/object/linux-display-ia32-260.19.36-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.36-driver.html)

---

