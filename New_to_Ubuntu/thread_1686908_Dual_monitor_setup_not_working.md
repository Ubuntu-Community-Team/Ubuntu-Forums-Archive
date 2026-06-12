---
title: "Dual monitor setup not working"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by ARMNHIE on 2011-02-13
Alright, I&#8217;ve been at this for weeks. I&#8217;ve been trying to get a second monitor working with Ubuntu 10.04. I&#8217;ve watched numerous videos showing how to use the NVIDIA XServer Settings and I&#8217;ve done exactly what they&#8217;ve said to do. I&#8217;ve read numerous forums about this and nothing is working. I have an 18 in acer monitor I&#8217;m trying to hook up to my laptop via VGA. When I connect the second monitor to my laptop and even after doing everything in Nvidia XServer Settings right, the second monitor still displays a &#8220;No input signal&#8221; message. VERY FRUSTRATING! I&#8217;ve been at this for some time now. I'm a proficiently experienced Ubuntu user but this is making me feel like a complete idiot. Here is a copy of everything in my xorg conf: And for some reason I get the feeling I&#8217;m missing some stuff. Check it out.
PLEAS PLEASE PLEASE help me out.

Section &#8220;Monitor&#8221;

# HorizSync source: builtin, VertRefresh source: builtin
Identifier &#8220;Monitor0&#8243;
VendorName &#8220;Unknown&#8221;
ModelName &#8220;Seiko&#8221;
HorizSync 30.0 - 75.0
VertRefresh 60.0
Option &#8220;DPMS&#8221;
EndSection

Section &#8220;Device&#8221;
Identifier &#8220;Device0&#8243;
Driver &#8220;nvidia&#8221;
VendorName &#8220;NVIDIA Corporation&#8221;
BoardName &#8220;GeForce Go 6150&#8243;
EndSection

Section &#8220;Device&#8221;
Identifier &#8220;Device0&#8243;
Driver &#8220;nvidia&#8221;
VendorName &#8220;NVIDIA Corporation&#8221;
BoardName &#8220;GeForce Go 6150&#8243;
EndSection

Section &#8220;Screen&#8221;

# Removed Option &#8220;TwinView&#8221; &#8220;1&#8243;
# Removed Option &#8220;metamodes&#8221; &#8220;CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0&#8243;
# Removed Option &#8220;TwinView&#8221; &#8220;0&#8243;
# Removed Option &#8220;metamodes&#8221; &#8220;nvidia-auto-select +0+0&#8243;
# Removed Option &#8220;TwinView&#8221; &#8220;True&#8221;
# Removed Option &#8220;MetaModes&#8221; &#8220;nvidia-auto-select, nvidia-auto-select&#8221;
Identifier &#8220;Screen0&#8243;
Device &#8220;Device0&#8243;
Monitor &#8220;Monitor0&#8243;
DefaultDepth 24
Option &#8220;TwinView&#8221; &#8220;0&#8243;
Option &#8220;TwinViewXineramaInfoOrder&#8221; &#8220;DFP-0&#8243;
Option &#8220;metamodes&#8221; &#8220;DFP: nvidia-auto-select +0+0&#8243;
SubSection &#8220;Display&#8221;
Depth 24
EndSubSection
EndSection

---

### Post by jwcalla on 2011-02-13
Does your video chip support twinview or are you just trying to get the laptop display onto the monitor?  Unfortunately I don't know much about laptop video setups so I will probably be of no help.

Have you tried this config:

Option &#8220;TwinView&#8221; &#8220;1&#8243;
Option &#8220;metamodes&#8221; &#8220;CRT: 1024x768 +1280+0, DFP: nvidia-auto-select +0+0&#8243;

My next suggestion is to make sure the HorizSync and VertRefresh options are correct for your monitor.  Sometimes the manufacturer provides this information somewhere.

---

### Post by ARMNHIE on 2011-02-13
Ok I put what you suggested in the config. I checked the HorizSynch and VerRefresh. I haven't messed with either of those since I've had the laptop. Still not working. The computer almost acts like it's connected to the other monitor, yet the other monitor is still "No signal detected". Here is my config now that I put in the Option "TwinView" "1" , etc.:

This still wasn't working so I was wondering, maybe I didn't stick it in the right place? And just to verify, my laptop monitor is 1280x800 and the second monitor is 1368x768 if that helps.


EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6150"
EndSection

Section "Screen"

# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "TwinView" "True"
    Option         "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Monitor"

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6150"
EndSection

Section "Screen"

# Option “RenderAccel” “true”
# Option “TwinView” “1&#8243;
# Option “metamodes” “CRT: 1024x768 +1280+0, DFP: nvidia-auto-select +0+0&#8243;
# Option "TwinView" "2"
# Option "metamodes" "nvidia-auto-select +0+0"
# Option "TwinView" "True"
# Option "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by jwcalla on 2011-02-13
> **ARMNHIE said:**
> This still wasn't working so I was wondering, maybe I didn't stick it in the right place? And just to verify, my laptop monitor is 1280x800 and the second monitor is 1368x768 if that helps.


Yeah there are a couple of repeated sections that might cause some conflicts, but we'll get this working.  In the meantime, so I understand better, is your intention to have two simultaneous displays, the primary on the laptop and a secondary on an external monitor?  And are you looking to have the output shared across both displays (one big desktop) or cloned (identical output to each display)?  And finally, what is the model # of the external monitor?

---

### Post by ARMNHIE on 2011-02-13
Thank you guys, I'm appreciating your time to look at my issues. I would like to have my laptop monitor be the main screen with the secondary being an extra workspace. For example, all my menu options on one screen while the other is basically an extra background. I'm not so much for the stretching of one desktop over multiple monitors. The model number for the secondary is G185H.

---

### Post by jwcalla on 2011-02-13
Okay try this.

Make a copy of your /etc/X11/xorg.conf first, then replace it with this one:

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Acer"
    ModelName      "G185H"
    HorizSync       30.0 - 80.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "MetaModes" "DFP: 1280x800 +0+0, CRT: 1366x768 +1280+0"
    Option         "ConnectedMonitor" "DFP, CRT"
    DefaultDepth    24
    SubSection "Display"
        Depth       24
    EndSubSection
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
    # generated from default
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Device"
    Identifier     "Device0"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6150"
    Driver    "nvidia"
EndSection

```

---

### Post by jwcalla on 2011-02-13
Actually... comment out this line for now from what I posted:

# Option         "ConnectedMonitor" "DFP, CRT"

---

### Post by ARMNHIE on 2011-02-15
I put that in my config file, rebooted. Did nothing. I went back into Nvidia Config Settings after reboot made sure the acer screen was on, rebooted. Nothing. Tried it different ways in making my seiko laptop screen absolute and the other monitor right side of and vise verse, neither worked. I tried it many different ways, however there was one it did make the second monitor light up like it was turning on and then it just went back and said "No signal detected" again. Each time I've tried it different ways it will only make my laptop screen look like there is wider workspaces or it moves my bottom panel up about half an inch on the screen. So I'm thinking this was close since it made my other monitor flicker. I know this is a lot for a reply but I thought if I just threw all my specs up here it may help:


capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-56
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.8.2
          slot: Socket S1
          size: 800MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-through unified
     *-memory:0
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: M4 70T2953EZ3-CE6
             vendor: EC00000000000000
             physical id: 0
             serial: 1E706D5B
             slot: DIMM 1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 667 MHz (1.5 ns)
             product: M4 70T2953EZ3-CE6
             vendor: EC00000000000000
             physical id: 1
             serial: 1E706D7B
             slot: DIMM 2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.8.2
          size: 800MHz
          capacity: 800MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24 ioport:4000(size=4096) memory:b4000000-b5ffffff ioport:d0000000(size=2097152)
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25 memory:b6000000-b7ffffff
        *-network
             description: Wireless interface
             product: BCM4311 802.11b/g WLAN
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@0000:03:00.0
             logical name: eth1
             version: 02
             serial: 00:1a:73:6b:2a:d1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.254.100 latency=0 multicast=yes wireless=IEEE 802.11bg
             resources: irq:19 memory:b6000000-b6003fff
     *-display
          description: VGA compatible controller
          product: C51 [Geforce Go 6150]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:18 memory:b2000000-b2ffffff memory:c0000000-cfffffff(prefetchable) memory:b1000000-b1ffffff memory:80000000-8001ffff(prefetchable)
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:1d00(size=128)
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:3040(size=64) ioport:3000(size=64)
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP51 PMU
          vendor: nVidia Corporation
          physical id: a.3
          bus info: pci@0000:00:0a.3
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:b0040000-b007ffff
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:b0004000-b0004fff
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:b0005000-b00050ff
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          logical name: scsi0
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:3080(size=16)
        *-cdrom
             description: DVD-RAM writer
             product: DVD A  DS8AZH
             vendor: Slimtype
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: NH61
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          logical name: scsi2
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:30c0(size=8) ioport:30b4(size=4) ioport:30b8(size=8) ioport:30b0(size=4) ioport:3090(size=16) memory:b0006000-b0006fff
        *-disk
             description: ATA Disk
             product: ST9160821AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 3.BH
             serial: 5MA2HDS3
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000ee2b4
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 840939e4-5cc1-4fdb-841d-11cf473b83f0
                size: 143GiB
                capacity: 143GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2011-01-26 21:59:16 filesystem=ext4 lastmountpoint=/z'rW&#65533;;&#65533;&#65533;XK&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;ew &#65533;&#65533;x/&#65533;&#65533;&#65533;&#65533;&#65533;'!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;z modified=2011-02-12 23:41:38 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-02-14 23:26:36 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 5710MiB
                capacity: 5710MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 5710MiB
                   capabilities: nofs
     *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
          resources: memory:b8000000-b80fffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: R5C832 IEEE 1394 Controller
             vendor: Ricoh Co Ltd
             physical id: 5
             bus info: pci@0000:07:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
             resources: irq:5 memory:b8000000-b80007ff
        *-generic:0
             description: SD Host controller
             product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 5.1
             bus info: pci@0000:07:05.1
             version: 19
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci-pci latency=64
             resources: irq:7 memory:b8000800-b80008ff
        *-generic:1
             description: System peripheral
             product: R5C592 Memory Stick Bus Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 5.2
             bus info: pci@0000:07:05.2
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=ricoh-mmc latency=0
             resources: irq:11 memory:b8000c00-b8000cff
        *-generic:2 UNCLAIMED
             description: System peripheral
             product: xD-Picture Card Controller
             vendor: Ricoh Co Ltd
             physical id: 5.3
             bus info: pci@0000:07:05.3
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:b8001000-b80010ff
        *-generic:3 UNCLAIMED
             product: Illegal Vendor ID
             vendor: Illegal Vendor ID
             physical id: 5.4
             bus info: pci@0000:07:05.4
             version: ff
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master vga_palette cap_list
             configuration: latency=255 maxlatency=255 mingnt=255
             resources: memory:b8001400-b80014ff
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:21 memory:b0000000-b0003fff
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: 00:1b:24:53:df:4f
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:20 memory:b0008000-b0008fff ioport:30e0(size=8)
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by jwcalla on 2011-02-15
When your laptop boots up and goes through the BIOS post messages, do you have a cloned display on both screens?  You should at least be able to get that far.  I'm wondering if it's something with the hardware setup.  If you can get the CMOS screen displayed on both monitors then it's most likely a linux config issue.

You could always try adding in the ConnectedMonitor option to the "Screen" section in xorg.conf as a last result:

Option "ConnectedMonitor" "DFP-0, CRT-1"

But you have to have the right numbers for the DFP and CRT options (0 or 1), which you can get from the NVIDIA X Server Settings program.

At this point you might want to ask over at the nvidia linux forums at [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14).

---

### Post by ARMNHIE on 2011-02-15
No I don't even get that. It may be a hardware issue like you said. My laptop is a 64 bit, could the issue be related to the fact that instead of 64 bit ubuntu, I'm running 32 bit?

---

### Post by jwcalla on 2011-02-15
> **ARMNHIE said:**
> No I don't even get that. It may be a hardware issue like you said. My laptop is a 64 bit, could the issue be related to the fact that instead of 64 bit ubuntu, I'm running 32 bit?

Nahh, that shouldn't be a problem.  I ran both 32-bit and 64-bit Ubuntus on this here 64-bit proc and had twinview working.

Does your laptop have a function to send the display to an external device?  I remember the old-school laptops had something like shift-F6 or something like that to send video to an attached display.

Also, some VGA adapters / cables aren't able to pass monitor info (like refresh freqs and resolutions) to the video card like the fancy-pants DVI and HDMI adapters do, so the video card is left clueless on how to drive the monitor.  But putting that info into the xorg.conf should get around that problem.

The only other thing I can think of is that some monitors (like mine) have an "auto-select input" feature that tends to not work well.  Sometimes I have to press the buttons to scroll through the inputs to make sure the monitor is set to the correct input.  I know that's some dumb advice, but hey... I'm desperate here!

---

