---
title: "Nvidia driver help! Please!!!"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by itsbrad212 on 2009-11-10
ok so when i installed 9.04 on my mom's laptop, it boots up, but everything loads slowly (from top to bottom) and it has extreme lag. when i try and change the settings from the menu (visual effects) it says unable to change. it is really laggy. all help is appreciated !! :D

---

### Post by The Funkbomb on 2009-11-10
Did you check Hardware Drivers for proprietary drivers?  Usually I have to reboot the machine for Ubuntu to pick up on them.

---

### Post by itsbrad212 on 2009-11-10
> **The Funkbomb said:**
> Did you check Hardware Drivers for proprietary drivers?  Usually I have to reboot the machine for Ubuntu to pick up on them.

yea theres only one for the wireless :(

---

### Post by The Funkbomb on 2009-11-10
Let's see a print out of video card.

sudo lshw and copy what it says under display.

---

### Post by itsbrad212 on 2009-11-10
description: Notebook
    product: Compaq Presario CQ60 Notebook PC
    vendor: Hewlett-Packard
    version: F.35
    serial: 2CE911HFJK
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 uuid=D3E23E80-1793-11DE-B76B-F95FAFB726EA
  *-core
       description: Motherboard
       product: 303C
       vendor: Wistron
       physical id: 0
       version: 08.49
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.35 (02/17/2009)
          size: 102KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon Dual-Core QL-62
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.3.1
          slot: Socket A
          size: 1GHz
          capacity: 2GHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit cpufreq
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
             capacity: 2MiB
             capabilities: synchronous internal write-through unified
     *-memory:0
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DRAM Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: S1
             size: 1GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DRAM Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: S2
             size: 1GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 5
          bus info: cpu@1
          version: 15.3.1
          size: 1GHz
          capacity: 1GHz
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
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial UNCLAIMED
          description: SMBus
          product: MCP78S [GeForce 8200] SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: latency=0
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP78S [GeForce 8200] Co-Processor
          vendor: nVidia Corporation
          physical id: 1.3
          bus info: pci@0000:00:01.3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 1.4
          bus info: pci@0000:00:01.4
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
     *-usb:1
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-usb:2
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
     *-usb:3
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: MCP78S [GeForce 8200] IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
     *-multimedia
          description: Audio device
          product: MCP78S [GeForce 8200] High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-pci:0
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
     *-ide:1
          description: IDE interface
          product: MCP78S [GeForce 8200] SATA Controller (non-AHCI mode)
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: scsi0
          logical name: scsi1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3 module=ahci
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GSA-T50N
             vendor: HL-DT-ST
             physical id: 0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: RC04
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: TOSHIBA MK2555GS
             vendor: Toshiba
             physical id: 1
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: FG00
             serial: 395NT1V4T
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=2d900954
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: f2482ccf-3ae6-427f-bdb7-e7a0afc03b8e
                size: 227GiB
                capacity: 227GiB
                capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                configuration: created=2009-11-10 21:06:20 filesystem=ext3 modified=2009-11-10 15:56:31 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-11-10 21:50:27 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                size: 5153MiB
                capacity: 5153MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 5153MiB
                   capabilities: nofs
     *-network
          description: Ethernet interface
          product: MCP78S [GeForce 8200] Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: 00:1f:16:75:65:a7
          capacity: 100MB/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
     *-pci:1
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:0b.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm ht bus_master cap_list
        *-display UNCLAIMED
             description: VGA compatible controller
             product: GeForce 8200M G
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
     *-pci:2
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
        *-network
             description: Wireless interface
             product: AR242x 802.11abg Wireless PCI Express Adapter
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:07:00.0
             logical name: wmaster0
             version: 01
             serial: 00:24:2b:c0:51:d2
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
             configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.67 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
     *-pci:3
          description: Host bridge
          product: Family 11h HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 11h DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 11h Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 11h Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: d
          bus info: usb@1:1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:1f:6f:83:fa:df
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by itsbrad212 on 2009-11-10
sorry too much there :(

---

### Post by The Funkbomb on 2009-11-10
Try rebooting the machine and then going to hardware drivers first.  The 8200 M should be supported.  It's not too old and not brand new.

According to [this post]("http://ubuntuforums.org/showthread.php?t=1222304&highlight=GeForce+8200M"), he was able to get drivers straight from Nvidia.

---

### Post by itsbrad212 on 2009-11-10
> **The Funkbomb said:**
> Try rebooting the machine and then going to hardware drivers first.  The 8200 M should be supported.  It's not too old and not brand new.

According to [this post]("http://ubuntuforums.org/showthread.php?t=1222304&highlight=GeForce+8200M"), he was able to get drivers straight from Nvidia.

when i  restarted it, it still only showed the wireless driver option :(

---

### Post by themusicalduck on 2009-11-10
EDIT: I just looked on the drivers page [http://www.nvidia.com/object/linux_display_ia32_185.18.36.html](http://www.nvidia.com/object/linux_display_ia32_185.18.36.html) - if you look under supported hardware, it doesn't list the 8200m.. perhaps this is the problem.

You could try this if you like, but it might not work and MIGHT need you to reinstall (or find a fix) if it messes things up!

Couple of tips for you :)

Use command ```
lspci | grep VGA
``` tells you what card you have. And also, use the code tags by pressing the # button when posting to post large chunks of text.

As for the card, you have an 8200m card.

If Ubuntu can't install the drivers, then you could install the drivers from here: [http://www.nvidia.com/object/linux_display_ia32_185.18.36.html](http://www.nvidia.com/object/linux_display_ia32_185.18.36.html)

Save the file to your desktop.

To install them follow these steps -

Press ctrl+alt+f1

Login to the terminal. Type ```
sudo /etc/init.d/gdm stop
```

Then ```
cd Desktop
```

Then type ```
sudo sh NVIDIA
``` hit tab to autocomplete the file.

Hit enter and follow the instructions.

Once its done, type ```
sudo /etc/init.d/gdm restart
```

It looks like a pain to do, but it's not as hard as it looks.

---

### Post by itsbrad212 on 2009-11-10
thanks for all of your help guys. I don't know how i fixed it :D i just installed some random packages and messed with some config files :D :D :D

---

### Post by JoJerome on 2010-01-08
Looks like I'm having the same problem but ...

I continually get an error message telling me I'm running X server and need to exit. Ctrl+Alt+f1 looks like it exits X, but I still get the same error message.

Also, when I run sudo /etc/init.d/gdm stop

I get "command not found."

Help! Am bragging up Kubuntu 9.10 to my friend here!

---

### Post by presence1960 on 2010-01-09
> **JoJerome said:**
> Looks like I'm having the same problem but ...

I continually get an error message telling me I'm running X server and need to exit. Ctrl+Alt+f1 looks like it exits X, but I still get the same error message.

Also, when I run sudo /etc/init.d/gdm stop

I get "command not found."

Help! Am bragging up Kubuntu 9.10 to my friend here!

By similar problem you mean can't install Nvidia video driver? If so boot into Kubuntu & install envyng-core & envyng-qt & envyng-gtk
I don't use Kubuntu so I am not sure if the terminal command is ```
sudo apt-get install <package name>
``` or ```
sudo aptitude install <package name>
```

Once installed open a terminal and run ```
envyng -t
```
Follow the prompts to install Nvidia driver

---

