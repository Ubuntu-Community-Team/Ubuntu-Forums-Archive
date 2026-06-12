---
title: "Should I install 32 or 64 bit Ubuntu?"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by pcvchriskmg on 2011-04-20
Hi,

I want to install Ubuntu 10.04 (I heard 10.10 doesn't work well with my network card) but I wanted to ask if I should install the 32 or 64 bit. My current machine runs 64-bit Windows 7.

Under the "Select a Release" page, I found the following regarding the 64-bit install:
"Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead."

My processor is: Intel(R) Core(TM)2 Duo CPU @ 2.10GHz 2.1o GHz

Do I install 32-bit since I have an Intel chip? Or the 64-bit because I have a Core duo?

Thank you in advance,
Chris

---

### Post by papibe on 2011-04-20
How much RAM do you have?

---

### Post by Antarctica32 on 2011-04-20
You will probably want to install 64

---

### Post by mörgæs on 2011-04-20
Hi, welcome to the fora.

This has been debated over and over. In the recurring discussions you will see lots of threads regarding this.

[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

### Post by mr.farenheit on 2011-04-20
i have an intel core 2 duo. i ran both 32 and 64 bit just fine. just depends on how much you want out of your computer.

---

### Post by pcvchriskmg on 2011-04-20
I have 4 GB of RAM. (2 x 2GB)

---

### Post by Adrastus on 2011-04-20
A dual-core chip does not necessarily mean one architecture or the other.  However, if you are currently running 64-bit Win7 then you would be safe installing 64-bit Ubuntu.

The chief difference between the two architectures is that a 64-bit OS can access WAY more RAM (something on the order of 18 exabytes which is around 18 million terabytes compared to 4 GB for 32-bit).  This means that if you want to run a big burly desktop for intensive applications or running Virtual Machines, or other RAM-intensive endeavours, you would be far better off installing the 64-bit version so that you can have the option for that additional functionality if you need it.  But if you could really care less and don't ever see yourself adding more than 4GB RAM it's really up to you, flip a coin :wink:

I've been using the 64-bit version on my i7 Intel chip for a while now (they call it AMD64 in install packages as a matter of convention) and I love it.  The only possible drawback I can think of is that it makes creating Live disks and some VM stuff for 32-bit machines a bit weird.

To sum up my ramblings, I recommend you install the 64-bit version.


But for the love of god, what ever you do, please backup everything first and make a live disk of both the 32 and 64-bit versions just to make sure everything is bootable, and maybe burn (or flash drive) a few other distros to play with while you're at it, and play with them for a few days first before you do a final install.  Linux is great, and one of the best things about it it all of the different flavours.

---

### Post by Learning Linux 2011 on 2011-04-20
You can go either way.  32-bit works fine on most machines.  64-bit may have some troubles on some machines.  32-bit is the safer choice, 64-bit is the more adventurist choice.

You should probably download both and try them on Live CD's before committing.


caveat: If you have more than 4 GB or RAM, you will need the 64-bit version. But FYI Linux doesn't use nearly as much RAM as Windows does.

---

### Post by pcvchriskmg on 2011-04-20
Lot of good advice and explanations here, thanks guys.

I think burning live versions of both are good ideas and playing with those before I settle. Had I done that earlier, I would have discovered my network adapter (broadcom) has problems with Maverick Meerkat and I wouldn't be faced with needing to uninstall that OS in the next few days.

---

### Post by beew on 2011-04-20
Everyone is talking about hardware, what about software compatibility? This is not a rhetorical question because I want to know (e.g I heard flash 64 bit doesn't work and googleearth has problems with 64 bits and a lot of softwares have to work through 32 bit libraries which have bugs)

@OP

What is your network card, just curious

EDITED: Actually I use 10.10 on some computers with broadcom cards and it works fine, I think it would depend on which broadcom card.

---

### Post by Learning Linux 2011 on 2011-04-20
> **beew said:**
> Everyone is talking about hardware, what about software compatibility? This is not a rhetorical question because I want to know (e.g I heard flash 64 bit doesn't work and googleearth has problems with 64 bits and a lot of softwares have to work through 32 bit libraries which have bugs)

@OP

What is your network card, just curious

EDITED: Actually I use 10.10 on some computers with broadcom cards and it works fine, I think it would depend on which broadcom card.

Yeah, good point.  Most problems anyone will encounter with a 64-bit OS is software compatibility.  There are plenty of programs that either don't work, or don't work correctly with 64-bit operating systems.

---

### Post by jocko on 2011-04-20
> **pcvchriskmg said:**
> Hi,

I want to install Ubuntu 10.04 (I heard 10.10 doesn't work well with my network card) but I wanted to ask if I should install the 32 or 64 bit. My current machine runs 64-bit Windows 7.

Under the "Select a Release" page, I found the following regarding the 64-bit install:
"Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead."

My processor is: Intel(R) Core(TM)2 Duo CPU @ 2.10GHz 2.1o GHz

Do I install 32-bit since I have an Intel chip? Or the 64-bit because I have a Core duo?

Thank you in advance,
Chris

You have a 64 bit cpu, so unless you need full 32 bit support you should be better off using a 64 bit OS. Apparently they managed to exchange one confusing advice on the release page with another. The "AMD" in AMD64 to indicate that it is the 64 bit architecture that was specified by amd (and later adopted by other cpu manufacturers, including Intel), and I'm guessing they keep it there to distinguish it from earlier, less widely spread 64 bit architectures.

Some people will tell you that if you don't have more than 4 GB RAM, you should use 32 bit. That is wrong. The only situation I know where 32 bit would perform better than 64 bit on the same machine, is if you have so little ram that the OS is forced to use the swap partition (64 bit uses a bit more ram, so if you are low on ram the available ram would fill up faster on 64 bit). Can't tell you exactly where the lower limit of ram would be, but I'm sure that even with only 1 Gb, 64 bit would outperform 32 bit most of the time.

Others will tell you that there are some software that isn't available or doesn't work properly for the 64 bit version. The main reason for that is that it USED to be true, but most or all of those problems have been solved the last few years.
64 bit flash works perfectly fine. To get real 64 bit flash, install the firefox plugin [Flash-Aid]("https://addons.mozilla.org/sv-se/firefox/addon/flash-aid/").
Not sure what problems people are having with google earth. It works perfectly fine for me, and has done so for years.

---

### Post by Sef on 2011-04-20
> Everyone is talking about hardware, what about software compatibility? This is not a rhetorical question because I want to know (e.g I heard flash 64 bit doesn't work and googleearth has problems with 64 bits and a lot of softwares have to work through 32 bit libraries which have bugs)


Flash works fine with 64-bit. I just download it from the repositories. 32-bit can run under 64-bit, so almost all software will run on 64-bit.

---

### Post by beew on 2011-04-20
> **Sef said:**
> 32-bit can run under 64-bit, so almost all software will run on 64-bit.
How optimal is that? Do they work as well? How about third party softwares?

I think OP should check out related threads first. I mean people having problems with specific softwares under 64 bits rather than thread on the abstract "64 bit vs 32 bits"

---

### Post by pcvchriskmg on 2011-04-20
> **beew said:**
> Everyone is talking about hardware, what about software compatibility? This is not a rhetorical question because I want to know (e.g I heard flash 64 bit doesn't work and googleearth has problems with 64 bits and a lot of softwares have to work through 32 bit libraries which have bugs)

@OP

What is your network card, just curious

EDITED: Actually I use 10.10 on some computers with broadcom cards and it works fine, I think it would depend on which broadcom card.

It's a Dell Wireless 1397 WLAN. It uses broadcom drivers and I read in another thread that 10.10 doesn't support it. I had no problems awhile back with 9.04.

---

### Post by josephmills on 2011-04-20
Please make sure that your ethernet cable(cat5) is plugged into your machine and router.  please put in a cd of ubuntu 10.10.**EDIT:use the 32bit version for hw test** in your cd/dvd/whatever drive Then when you get a prompt window please pick **run as a live cd**then go to **Applications-->Accessories-->Terminal** then type in ```
lshw 
``` and [b]paste it here 
[/b]so **ls** stands for **List** and **hw** stands for **Hardware ** So **ls--><--hw** stands for **list hardware**  OHH by the way welcome to UbuntuForums:)
**EDIT**because with out hardware there would be no software

---

### Post by josephmills on 2011-04-20
> **beew said:**
> How optimal is that? Do they work as well? How about third party softwares?

I think OP should check out related threads first. I mean people having problems with specific softwares under 64 bits rather than thread on the abstract "64 bit vs 32 bits"

+ 1 zero shoot im :confused:

---

### Post by pcvchriskmg on 2011-04-21
> **josephmills said:**
> Please make sure that your ethernet cable(cat5) is plugged into your machine and router.  please put in a cd of ubuntu 10.10.**EDIT:use the 32bit version for hw test** in your cd/dvd/whatever drive Then when you get a prompt window please pick **run as a live cd**then go to **Applications-->Accessories-->Terminal** then type in ```
lshw 
``` and [b]paste it here 
[/b]so **ls** stands for **List** and **hw** stands for **Hardware ** So **ls--><--hw** stands for **list hardware**  OHH by the way welcome to UbuntuForums:)
**EDIT**because with out hardware there would be no software

I currently have 10.10 on my machine now, although I'm not sure if it is the 32 or 64 bit. I couldn't find it internally through Ubuntu. I'll perform those commands above tonight, and post back.

Thanks for the welcome, btw. I love participating in active forums and this seems to be a great one.

Chris

---

### Post by 3rdalbum on 2011-04-21
If you use Windows, you'll run into 64-bit software compatibility problems.

If you use Linux, most of what you can run is compiled for 64-bit, or able to be recompiled, or can be run in 32-bit compatibility mode.

---

### Post by pcvchriskmg on 2011-04-21
> **3rdalbum said:**
> If you use Windows, you'll run into 64-bit software compatibility problems.

That has definitely been my experience with Windows Vista and then 7 for the past 2 years. I've found most of the software I use is available for 64 bit, but there have been no shortage of instances where I've run into an error message during an installation.

---

### Post by pcvchriskmg on 2011-04-21
> **josephmills said:**
> Please make sure that your ethernet cable(cat5) is plugged into your machine and router.  please put in a cd of ubuntu 10.10.**EDIT:use the 32bit version for hw test** in your cd/dvd/whatever drive Then when you get a prompt window please pick **run as a live cd**then go to **Applications-->Accessories-->Terminal** then type in ```
lshw 
``` and [B]paste it here 
[/B]so **ls** stands for **List** and **hw** stands for **Hardware ** So **ls--><--hw** stands for **list hardware**  OHH by the way welcome to UbuntuForums:)
**EDIT**because with out hardware there would be no software

Hi, I followed those commands above. I received an initial warning, pressed enter and then the hardware list showed up.

Scroll a little way down, and you find the network info:

*-network
                description: Network controller
                product: BCM4312 802.11b/g LP-PHY
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:17 memory:f8000000-f8003fff

Should I be running into issues with this network card???


Here's the full text from the cli.


WARNING: you should run this program as super-user.
PCI (sysfs)  
chris-studio-1737         
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3980MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm cpufreq
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
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:fc000000-fc3fffff memory:d0000000-dfffffff ioport:1800(size=8)
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
             resources: memory:fc400000-fc4fffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:fc904800-fc904bff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:46 memory:fc700000-fc703fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:f6000000-f7ffffff ioport:f0000000(size=33554432)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:f8000000-f9ffffff ioport:f2000000(size=33554432)
           *-network
                description: Network controller
                product: BCM4312 802.11b/g LP-PHY
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:17 memory:f8000000-f8003fff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:fa000000-fbffffff ioport:f4000000(size=33554432)
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:5000(size=4096) memory:fc500000-fc5fffff ioport:c0000000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetLink BCM5784M Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 10
                serial: 00:22:19:f4:31:a2
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tg3 driverversion=3.110 firmware=sb v2.17 ip=192.168.1.111 latency=0 multicast=yes
                resources: irq:47 memory:fc500000-fc50ffff
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1880(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:18a0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18c0(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fc904c00-fc904fff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:fc600000-fc6fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:09:01.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:17 memory:fc600000-fc6007ff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:09:01.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:18 memory:fc600800-fc6008ff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:09:01.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
                resources: memory:fc600c00-fc600cff
           *-generic:2
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:09:01.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=r852 latency=64
                resources: irq:18 memory:fc601000-fc6010ff
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:1818(size=8) ioport:180c(size=4) ioport:1810(size=8) ioport:1808(size=4) ioport:18e0(size=32) memory:fc904000-fc9047ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c0200000-c02000ff ioport:1c00(size=32)

---

### Post by collisionystm on 2011-04-21
you have the same specs as me. Do the 64. It runs perfect. Much faster than 32.

---

