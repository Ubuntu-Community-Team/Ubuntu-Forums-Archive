---
title: "Is it possible to tell how many hard drive slots I have from the command line?"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2011-06-05
I'm on an HP Pavilion DV7-1240US laptop, and I'm trying to figure out if it has a second hard drive slot because if it does then I want to put a solid state drive in it for the OS, and leave my /home and stuff on my normal hard drive. The [1260US](http://www.amazon.com/HP-Pavilion-DV7-1240US-17-0-Inch-Laptop/dp/B001NPDKUS) model apparently has two hard drives according to one of the reviews.

Results of lshw
```
bibo@bibos-computer:~$ lshw
WARNING: you should run this program as super-user.
bibos-computer            
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3708MiB
     *-cpu
          product: AMD Turion(tm) X2 Dual-Core Mobile RM-72
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 2100MHz
          capacity: 2100MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit lbrv svm_lock nrip_save cpufreq
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: Hewlett-Packard Company
             vendor: Hewlett-Packard Company
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
             resources: ioport:7000(size=4096) memory:d2300000-d24fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS780M/RS780MN [Radeon HD 3200 Graphics]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:46 memory:c0000000-cfffffff ioport:7000(size=256) memory:d2400000-d240ffff memory:d2300000-d23fffff
           *-multimedia
                description: Audio device
                product: RS780 Azalia controller
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:45 memory:d2410000-d2413fff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=16384) memory:d1300000-d22fffff ioport:d0000000(size=16777216)
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices [AMD]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:d1200000-d12fffff ioport:d2600000(size=1048576)
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:d1200300-d12003ff memory:d2600000-d260ffff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:08:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:d1200200-d12002ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:08:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:17 memory:d1200100-d12001ff
           *-generic:3 UNCLAIMED
                description: System peripheral
                product: xD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.4
                bus info: pci@0000:08:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:d1200000-d12000ff
        *-pci:3
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 memory:d1100000-d11fffff
           *-network DISABLED
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: wlan0
                version: 01
                serial: 00:24:2b:e2:6b:20
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.35-28-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:18 memory:d1100000-d110ffff
        *-pci:4
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:2000(size=4096) memory:d2700000-d27fffff ioport:d1000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:0a:00.0
                logical name: eth0
                version: 02
                serial: 00:23:5a:38:92:e1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.8 latency=0 multicast=yes
                resources: irq:44 ioport:2000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d1020000-d103ffff
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:8038(size=8) ioport:804c(size=4) ioport:8030(size=8) ioport:8048(size=4) ioport:8010(size=16) memory:d2508000-d25083ff
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:d2507000-d2507fff
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:d2506000-d2506fff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:d2508500-d25085ff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:d2505000-d2505fff
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:d2504000-d2504fff
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:d2508400-d25084ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8000(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:d2500000-d2503fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:5
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:1000(size=4096)
     *-pci:1
          description: Host bridge
          product: Family 11h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 11h Processor Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 11h Processor DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h Processor Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 11h Processor Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

and lspci

```


bibo@bibos-computer:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
08:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

---

### Post by dFlyer on 2011-06-05
Just open the case and look. Of course that will more than likely void your warranty.

---

### Post by wolfen69 on 2011-06-05
If there was an extra space, there would probably be a door on the bottom with screws. Get a small screwdriver and open them up to have a look.

---

### Post by Legendary_Bibo on 2011-06-05
> **wolfen69 said:**
> If there was an extra space, there would probably be a door on the bottom with screws. Get a small screwdriver and open them up to have a look.

Will I know it when I see it?

---

### Post by wolfen69 on 2011-06-05
Just look for a door big enough for a hard drive. ;)

---

### Post by ikt on 2011-06-05
> **Legendary_Bibo said:**
> Will I know it when I see it?

ide looks like this: [http://www.google.com.au/search?um=1&hl=en&safe=active&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&biw=1280&bih=841&tbm=isch&sa=1&q=ide+connection+motherboard&aq=f&aqi=&aql=&oq=](http://www.google.com.au/search?um=1&hl=en&safe=active&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&biw=1280&bih=841&tbm=isch&sa=1&q=ide+connection+motherboard&aq=f&aqi=&aql=&oq=)

sata like this: [http://www.google.com.au/search?um=1&hl=en&safe=active&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&biw=1280&bih=841&tbm=isch&sa=1&q=sata+connection+motherboard&aq=f&aqi=&aql=&oq=](http://www.google.com.au/search?um=1&hl=en&safe=active&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&biw=1280&bih=841&tbm=isch&sa=1&q=sata+connection+motherboard&aq=f&aqi=&aql=&oq=)

You need 1 sata or ide connection on your motherboard to be free in order to connect your hard drive, whether you need a sata or ide hard drive will depend on what connection is on your motherboard.

A hard drive enclosure inside a computer case looks like this:

[http://www.crunchgear.com/wp-content/uploads/2008/06/enclosure.jpg](http://www.crunchgear.com/wp-content/uploads/2008/06/enclosure.jpg)

You probably won't need to worry about it so much though, as SSD drives can just sit in the bottom of the computer without an issue.

---

### Post by wep940 on 2011-06-05
This is the specification page for your laptop:
 
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01631355&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3860622](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01631355&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3860622)
 
Please notice there is no mention of a 2nd hard disk bay - you get your normal hard drive and optical media drive - that's it. 
 
About the only choice you're going to have is an external disk.

---

### Post by ikt on 2011-06-05
> **wep940 said:**
> This is the specification page for your laptop:
 
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01631355&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3860622](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01631355&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3860622)
 
Please notice there is no mention of a 2nd hard disk bay - you get your normal hard drive and optical media drive - that's it. 
 
About the only choice you're going to have is an external disk.

that'll teach me for skimming the op.

---

### Post by HydroMX on 2011-08-31
I know this thread is a few months old, but I just wanted to give a firm answer for anyone else who may have this laptop.

The HP DV7-1240US laptop has 2 sata connections for 2 HDD's.

I am running a Primary Drive 320GB partitioned and dual booting with Ubuntu 11.04 and Windows 7.  I also have a secondary 320GB drive for storage. Remove the back cover to access your Memory and HDD bays.

---

### Post by jockyburns on 2011-08-31
HP computers may show  on my computer that they have a drive C and drive D (both classed as HDD's) . My old HP 760 showed 2 HDD's but physically only had one Seagate HDD. :wink:

---

