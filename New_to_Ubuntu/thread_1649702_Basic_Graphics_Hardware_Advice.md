---
title: "Basic Graphics Hardware Advice"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by mlnease on 2010-12-20
Hello,

I've been happily using Ubuntu exclusively since Dapper with no complaints.

Recently I bought a Nikon digital SLR and am finding my computer a bit challenged by the size of the files.

I am woefully ignorant of hardware so please excuse what is probably an extremely elementary question:  What hardware should I upgrade to improve the speed of manipulations via GIMP of large digital graphic files?  


[LIST]
[*]Do I need a faster processor?
[/LIST]
[INDENT][INDENT]Intel Pentium 4 CPU 2.80GHz
[/INDENT][/INDENT]
[LIST]
[*]More memory?
[/LIST]
[INDENT][INDENT]494.9MB
[/INDENT][/INDENT]
[LIST]
[*]A better video card?
[/LIST]
[INDENT][INDENT]00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
[/INDENT][/INDENT]
[LIST]
[*]Maybe just a new computer all round?
[/LIST]
[INDENT][INDENT]Dell Optiplex GX270

[/INDENT][/INDENT]Any advice would be greatly appreciated--thanks in advance.

mike

---

### Post by albert s on 2010-12-20
iM NOT A MAJOR HARDWARE KNOWING PERSON,
BUT i WOULD DEFFO SAY YOU NEED MORE RAM,
(sorry about the caps.)
as much as you can TBH, 
494.9MB seems a very strange amount though, is this correct?
try
```
sudo lshw
```
in a terminal and it will show you the exact specs of your machine.

---

### Post by mlnease on 2010-12-20
> **albert s said:**
> iM NOT A MAJOR HARDWARE KNOWING PERSON,
BUT i WOULD DEFFO SAY YOU NEED MORE RAM,
(sorry about the caps.)
as much as you can TBH, 
494.9MB seems a very strange amount though, is this correct?
try
```
sudo lshw
```in a terminal and it will show you the exact specs of your machine.
Thanks for the speedy reply:
```
mn@mn-OptiPlex-GX270:~$ sudo lshw
mn-optiplex-gx270         
    description: Desktop Computer
    product: OptiPlex GX270
    vendor: Dell Computer Corporation
    serial: 6H6DY41
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=desktop cpus=1 power-on_password=enabled uuid=44454C4C-4800-1036-8044-B6C04F593431
  *-core
       description: Motherboard
       product: 0U1324
       vendor: Dell Computer Corp.
       physical id: 0
       serial: ..CN1374044A04HD.
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A03 (10/20/2003)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.9
          slot: Microprocessor
          size: 2800MHz
          capacity: 3200MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DIMM_1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns) [empty]
             physical id: 1
             slot: DIMM_2
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns) [empty]
             physical id: 2
             slot: DIMM_3
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns) [empty]
             physical id: 3
             slot: DIMM_4
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f0000000-f7ffffff
        *-display
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff ioport:ed98(size=8)
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ff60(size=32)
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff20(size=32)
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:ffa80800-ffa80bff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:fea00000-feafffff
           *-network
                description: Ethernet interface
                product: 82540EM Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: c
                bus info: pci@0000:01:0c.0
                logical name: eth0
                version: 02
                serial: 00:0d:56:f8:4e:e2
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k6-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
                resources: irq:18 memory:feae0000-feafffff ioport:df40(size=64)
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:feb7fc00-feb7ffff
           *-disk
                description: ATA Disk
                product: WDC WD400BB-75DE
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WMAD16994402
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000d1b25
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: 6fda5afa-a238-44fa-be41-711c73a61ea1
                   size: 17GiB
                   capacity: 17GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-10-10 16:19:17 filesystem=ext4 lastmountpoint=/&#65533;&#65533;]&#65533;y&#65533;&#65533;&#65533;&#65533;l&#1984;s &#1940;>&#65533;&#65533;&#65533;m &#65533;m/&#65533;&#65533;>&#65533;&#65533;^!&#65533;@&#65533;H&#65533;@&#65533;H&#65533;y&#65533;&#65533;&#65533;>&#65533;&#1904;>&#65533;&#65533;mp modified=2010-12-16 08:17:35 mounted=2010-12-19 08:29:48 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1449MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 17GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 804MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GH22NP20
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.04
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fea0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:eda0(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:ee00(size=256) ioport:edc0(size=64) memory:feb7fa00-feb7fbff memory:feb7f900-feb7f9ff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: 00:22:6b:a5:1b:5c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.35-24-generic firmware=N/A ip=192.168.1.125 link=yes multicast=yes wireless=IEEE 802.11bg
```I'm afraid this doesn't mean a lot to me--is it of any help?

Thanks again.

mike

---

### Post by Putnam11 on 2010-12-20
The GX270 is very old, and I'd recommend you get a new computer if you have money to do so.  This issue is a problem with the amount of RAM.  512MB is very, very small and I would recommend at least 2-4GB for editing pictures.
It looks as though your Dell can support 2GB of memory, so if you don't want to have to buy a new computer you could buy this:
EDIT: refer to below
for $70 and install it yourself or have somebody you know who is tech-savvy do it for you.  This is your cheapest option.

Your computer is really old, and buying a new one, even if it is the cheapest available, would be best.

EDIT:  I see through your specs that you have 4 slot, and the memory I listed before is not compatible.
I would recommend buying two, three, or four sticks of this 1GB stick:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820178282&Tpk=333%20MHz]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820178282&Tpk=333%20MHz")
and getting rid of your old 256MB stick.  It's $39.99 per stick so you should buy four if you are willing to spend the money.

---

### Post by coffeecat on 2010-12-20
More RAM would certainly help, but the cost of buying the older SDRAM memory you have would be high - unless you bought second-hand. It's an unfortunate fact  that obsolete hardware, when you can source it, is more expensive than more recent designs.

Better graphics would help a little - the Intel 865G is pretty ancient - but again would be expensive because you would need an AGP card (yesterday's technology) or even a PCI card if there is no AGP slot. The chances of that machine having the current PCIe slot are zero.

Lastly, even if you could find a compatible higher specification Intel P4 for your motherboard, the speed increase would be marginal. It's a single-core CPU and the P4's are notorious for running very hot.

In short, spending money on a machine that age is not economical.

Do you have the budget for a new machine? A decent machine with a good dual-core processor, 4GB RAM, a decent nvidia or ATI card, and a hard drive 10-20 times the capacity of your 40GB one, would be cheaper in real terms than what you bought that Dell for in - what - 2002/3?

---

### Post by mlnease on 2010-12-20
> **Putnam11 said:**
> The GX270 is very old, and I'd recommend you get a new computer if you have money to do so.  This issue is a problem with the amount of RAM.  512MB is very, very small and I would recommend at least 2-4GB for editing pictures.
It looks as though your Dell can support 2GB of memory, so if you don't want to have to buy a new computer you could buy this:
EDIT: refer to below
for $70 and install it yourself or have somebody you know who is tech-savvy do it for you.  This is your cheapest option.

Your computer is really old, and buying a new one, even if it is the cheapest available, would be best.

EDIT:  I see through your specs that you have 4 slot, and the memory I listed before is not compatible.
I would recommend buying two, three, or four sticks of this 1GB stick:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820178282&Tpk=333%20MHz](http://www.newegg.com/Product/Product.aspx?Item=N82E16820178282&Tpk=333%20MHz)
and getting rid of your old 256MB stick.  It's $39.99 per stick so you should buy four if you are willing to spend the money.
Thanks for this.  I realize my workstation's a bit of an antique (as am I) but it still runs like a top, so I'll consider the memory first.  I've added memory sticks before, should I expect these to be particularly challenging?

However, a new (or refurbished) computer is not out of the question.  Can you recommend a good, solid workstation for my purposes--that is, all round OO app, VOIP etc. use plus GIMP manipulation of large files, all Ubuntu all the time?

Thanks again for the advice, really appreciate it.

mike

---

### Post by mlnease on 2010-12-20
So to paraphrase, I should be looking for:

[LIST]
[*]a good dual-core processor,
[/LIST]

[LIST]
[*]4GB RAM,
[/LIST]

[LIST]
[*]a decent nvidia or ATI card and
[/LIST]

[LIST]
[*]a 400GB - 800GB hard drive
[/LIST]
Unfortunately all my hardware experience has been on the job with typical office Dell and Compaq workstations, so I'm really unfamiliar with available brands.

Can anyone recommend a particular (as in brand and model) machine with a good, solid reputation (especially for performance and reliability) and the features above?

Many thanks in advance!

mike

---

### Post by albert s on 2010-12-20
my PC isnt much better than what you have so no point me trying to tell you what you need,
may be better to start a new thread detailing what you intend doing and what sort of budget you have,
oh, and your location in case there are any specific local deals to be had.

---

### Post by amjjawad on 2010-12-20
> **mlnease said:**
> 
[LIST]
[*]More memory?
[/LIST]
[INDENT][INDENT]494.9MB
[/INDENT][/INDENT]

Yes!

Edit:
I liked what Coffeecat [wrote]("http://ubuntuforums.org/showpost.php?p=10261621&postcount=5").

---

### Post by theozzlives on 2010-12-20
Your video seems to be sharing your RAM so I would recommend getting an inexpensive nVidea card off ebay and at least 1 GB RAM.

---

### Post by mr clark25 on 2010-12-20
everyone is making it sound like the OP's system is older than it is!

i have a system with a pentium 4 @ 2.4ghz, 1 gb of ddr 333 ram, and a nvidia mx-440 graphics card. it runs ubuntu 10.04 flawlessly. i can do almost anything i want on it. (even some light gaming!)


here is what i would do:
upgrade the ram to at least 1gb, maybe a little more.

get a dedicated graphics card. (preferably nvidia) 


onboard graphics will make the cpu do the graphics processing work, which then severely cuts performance.

---

### Post by amjjawad on 2010-12-20
> **mr clark25 said:**
> everyone is making it sound like the OP's system is older than it is!

i have a system with a pentium 4 @ 2.4ghz, 1 gb of ddr 333 ram, and a nvidia mx-440 graphics card. it runs ubuntu 10.04 flawlessly. i can do almost anything i want on it. (even some light gaming!)


here is what i would do:
upgrade the ram to at least 1gb, maybe a little more.

get a dedicated graphics card. (preferably nvidia) 

onboard graphics will make the cpu do the graphics processing work, which then severely cuts performance.

And you just did/wrote exactly what everyone else did/wrote ;)

---

### Post by mlnease on 2010-12-20
> **albert s said:**
> my PC isnt much better than what you have so no point me trying to tell you what you need,
may be better to start a new thread detailing what you intend doing and what sort of budget you have,
oh, and your location in case there are any specific local deals to be had.
Thanks again Albert, I'll try that.

---

### Post by mlnease on 2010-12-20
> **mr clark25 said:**
> everyone is making it sound like the OP's system is older than it is!

i have a system with a pentium 4 @ 2.4ghz, 1 gb of ddr 333 ram, and a nvidia mx-440 graphics card. it runs ubuntu 10.04 flawlessly. i can do almost anything i want on it. (even some light gaming!)


here is what i would do:
upgrade the ram to at least 1gb, maybe a little more.

get a dedicated graphics card. (preferably nvidia) 


onboard graphics will make the cpu do the graphics processing work, which then severely cuts performance.
Thanks very much for the response, Mr. Clark, I will follow up on it.

mike

---

### Post by Putnam11 on 2010-12-20
Instead of looking at pre-made computers, if you know how to connect computer parts you could actually go and build yourself one off of Newegg.  You just buy all the parts and assemble them.  This way you would be saving the 15-25% markup manufacturers put on your computer, and the Windows license. (I'd say anywhere between $200-700)  You can find guides on Youtube or a simple Google search on how to build a computer.
I'm guessing that you have an IDE Hard Drive, and most motherboards nowadays use Serial-ATA and these type of hard drives have quite a bit faster read/write speeds.  I would recommend keeping your old HDD since you already have all your files and stuff, but you could get an extra HDD for extra storage.  It would also cut down on the time it takes to transfer pics to your computer.  So you would need to find a case, a CPU, a compatible motherboard, compatible RAM, a card-reader, and a optical drive.
I've put together a pretty cheap computer for you below,~ $250.
Case: [http://www.newegg.com/Product/Product.aspx?Item=N82E16811154095](http://www.newegg.com/Product/Product.aspx?Item=N82E16811154095)
This case is pretty common, I actually use it and it was easy to assemble. $19.99

Power Supply: [http://www.newegg.com/Product/Product.aspx?Item=N82E16817170014](http://www.newegg.com/Product/Product.aspx?Item=N82E16817170014)
480W power supply should suffice. $13.99

Motherboard & CPU: [http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.572627](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.572627)
AMD Athlon 245 Dual-Core should be enough for you, not too much but not too little power.
The motherboard has two slots for DDR3 RAM and comes with an onboard Nvidia 6100 graphics card, will be good enough for what you need and more.  Way better than DDR 333MHz 512MB RAM. also has support foryour IDE drive and another SATA one. $89.98 for Combo.

Memory (RAM): [http://www.newegg.com/Product/Product.aspx?Item=N82E16820146748](http://www.newegg.com/Product/Product.aspx?Item=N82E16820146748)
4GB of DDR3 RAM will be about what you want.  It'll be really about 12x or so faster than what you have right now. $41.99

Hard Drive: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136073](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136073)
500GB with 7200RPM. Will be huge compared to your 80GB one. $49.99

CD/DVD Burner: [http://www.newegg.com/Product/Product.aspx?Item=N82E16827135204](http://www.newegg.com/Product/Product.aspx?Item=N82E16827135204)
24X speed DVD/CD writer. $16.99

Card Reader: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820300608](http://www.newegg.com/Product/Product.aspx?Item=N82E16820300608)
68-in-1 card reader with USB support. $10.00

Keyboard & Mouse: [http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.563913](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.563913)
This includes an ergonomic keyboard and a fairly nice mouse, I'm actually going to buy itor my computer after Christmas. $13.98

So that comes down to $256.91.  Just for fun I went to Dell.com and built a customized computer comparable to this one, and Dell's was $419.99.  Assuming they pay around $100 for a Windows license to put on your computer that you would end up deleting anyways, that's $319.99 for parts.  The parts are comparable to the ones I listed, so they put on a 25% mark-up on them.  So you could put together your own computer fairly easily or spend $163 for Dell to build one for you.

I hoped I helped, and if you have any questions please contact me via PM or my site.
Thanks!

---

### Post by mlnease on 2010-12-20
> **Putnam11 said:**
> Instead of looking at pre-made computers, if you know how to connect computer parts you could actually go and build yourself one off of Newegg.  You just buy all the parts and assemble them.  This way you would be saving the 15-25% markup manufacturers put on your computer, and the Windows license. (I'd say anywhere between $200-700)  You can find guides on Youtube or a simple Google search on how to build a computer.
I'm guessing that you have an IDE Hard Drive, and most motherboards nowadays use Serial-ATA and these type of hard drives have quite a bit faster read/write speeds.  I would recommend keeping your old HDD since you already have all your files and stuff, but you could get an extra HDD for extra storage.  It would also cut down on the time it takes to transfer pics to your computer.  So you would need to find a case, a CPU, a compatible motherboard, compatible RAM, a card-reader, and a optical drive.
I've put together a pretty cheap computer for you below,~ $250.
Case: [http://www.newegg.com/Product/Product.aspx?Item=N82E16811154095](http://www.newegg.com/Product/Product.aspx?Item=N82E16811154095)
This case is pretty common, I actually use it and it was easy to assemble. $19.99

Power Supply: [http://www.newegg.com/Product/Product.aspx?Item=N82E16817170014](http://www.newegg.com/Product/Product.aspx?Item=N82E16817170014)
480W power supply should suffice. $13.99

Motherboard & CPU: [http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.572627](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.572627)
AMD Athlon 245 Dual-Core should be enough for you, not too much but not too little power.
The motherboard has two slots for DDR3 RAM and comes with an onboard Nvidia 6100 graphics card, will be good enough for what you need and more.  Way better than DDR 333MHz 512MB RAM. also has support foryour IDE drive and another SATA one. $89.98 for Combo.

Memory (RAM): [http://www.newegg.com/Product/Product.aspx?Item=N82E16820146748](http://www.newegg.com/Product/Product.aspx?Item=N82E16820146748)
4GB of DDR3 RAM will be about what you want.  It'll be really about 12x or so faster than what you have right now. $41.99

Hard Drive: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136073](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136073)
500GB with 7200RPM. Will be huge compared to your 80GB one. $49.99

CD/DVD Burner: [http://www.newegg.com/Product/Product.aspx?Item=N82E16827135204](http://www.newegg.com/Product/Product.aspx?Item=N82E16827135204)
24X speed DVD/CD writer. $16.99

Card Reader: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820300608](http://www.newegg.com/Product/Product.aspx?Item=N82E16820300608)
68-in-1 card reader with USB support. $10.00

Keyboard & Mouse: [http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.563913](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.563913)
This includes an ergonomic keyboard and a fairly nice mouse, I'm actually going to buy itor my computer after Christmas. $13.98

So that comes down to $256.91.  Just for fun I went to Dell.com and built a customized computer comparable to this one, and Dell's was $419.99.  Assuming they pay around $100 for a Windows license to put on your computer that you would end up deleting anyways, that's $319.99 for parts.  The parts are comparable to the ones I listed, so they put on a 25% mark-up on them.  So you could put together your own computer fairly easily or spend $163 for Dell to build one for you.

I hoped I helped, and if you have any questions please contact me via PM or my site.
Thanks!
Putnam, I think this is the best idea yet, for all the reasons mentioned above.  I've never actually assembled a computer before but have always liked the idea and think I could manage it--I just never had the nuts-and-bolts, part-by-part suggestions before much less a common source for all the parts.

I'll look seriously into this tomorrow and will take you up on your kind offer of assistance if necessary.

Thanks very much again.

mike

---

### Post by Putnam11 on 2010-12-20
No problem, I like building theoretical computers, and actually helped recommend what parts to buy at my father's business he works for.  I plan to start a business sometime in the future building computers and local upgrades/repairs.
I see you joined my site, and I thank you for that.  It's fairly new, and we are still setting up new features all the time. :)

---

### Post by cascade9 on 2010-12-21
> **coffeecat said:**
> More RAM would certainly help, but the cost of buying the older SDRAM memory you have would be high - unless you bought second-hand. It's an unfortunate fact that obsolete hardware, when you can source it, is more expensive than more recent designs.

Better graphics would help a little - the Intel 865G is pretty ancient - but again would be expensive because you would need an AGP card (yesterday's technology) or even a PCI card if there is no AGP slot. The chances of that machine having the current PCIe slot are zero.

Lastly, even if you could find a compatible higher specification Intel P4 for your motherboard, the speed increase would be marginal. It's a single-core CPU and the P4's are notorious for running very hot.

In short, spending money on a machine that age is not economical.

Do you have the budget for a new machine? A decent machine with a good dual-core processor, 4GB RAM, a decent nvidia or ATI card, and a hard drive 10-20 times the capacity of your 40GB one, would be cheaper in real terms than what you bought that Dell for in - what - 2002/3?

I'm not quite as down on the old P4 as coffeecat, but in general I agree. 

If you can source cheap SD-RAM, it might be worth trying, but for most people its to expensive. Same with an AGP video card (PCI always seems to be too expensive). 

Gettign a faster P4 CPU would help. You've got a 865 intel chipset so it should run 800MHz FSB/1MB+  cache models (faster than the 533 FSB/512k cache model in that computer). I really dont think its worth trying though, a  new machine would be a better way to go. 

> **Putnam11 said:**
> Power Supply: [http://www.newegg.com/Product/Product.aspx?Item=N82E16817170014](http://www.newegg.com/Product/Product.aspx?Item=N82E16817170014)
480W power supply should suffice. $13.99

Motherboard & CPU: [http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.572627](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.572627)
AMD Athlon 245 Dual-Core should be enough for you, not too much but not too little power.
The motherboard has two slots for DDR3 RAM and comes with an onboard Nvidia 6100 graphics card, will be good enough for what you need and more.  Way better than DDR 333MHz 512MB RAM. also has support foryour IDE drive and another SATA one. $89.98 for Combo.

Memory (RAM): [http://www.newegg.com/Product/Product.aspx?Item=N82E16820146748](http://www.newegg.com/Product/Product.aspx?Item=N82E16820146748)
4GB of DDR3 RAM will be about what you want.  It'll be really about 12x or so faster than what you have right now. $41.99

So that comes down to $256.91.  Just for fun I went to Dell.com and built a customized computer comparable to this one, and Dell's was $419.99.  Assuming they pay around $100 for a Windows license to put on your computer that you would end up deleting anyways, that's $319.99 for parts.  The parts are comparable to the ones I listed, so they put on a 25% mark-up on them.  So you could put together your own computer fairly easily or spend $163 for Dell to build one for you.

I hoped I helped, and if you have any questions please contact me via PM or my site.
Thanks!

Brave, very brave to run a 'yum-cha' power supply. Way more likely to cause problems than a decent power supply in my expereince. 

I wouldnt be getting that zotac motherbaord either. Looks nasty, and if its anything liek the zotacs I've seen 'in thye flesh' before, it will be nasty. 

Umm....DDR3 1333 is 12 times faster than DDR333? Interesting maths. 

Dell wouldnt be paying $100 a Windows licence. Lots of people round here think that they pay virtually nothing thanks to 'bundled crapware', and though I dont agree with that I'd still think its way under $100. More like $20.

---

### Post by mlnease on 2010-12-21
Thanks for the contribution cascade9--I'll bear your comments in mind and consider an upgrade of the power supply and motherboard.

---

### Post by coffeecat on 2010-12-21
> **cascade9 said:**
> I'm not quite as down on the old P4 as coffeecat, but in general I agree. 

Perhaps my feelings are coloured by a 3 GHz P4 I used to use. I was able to switch off the central heating whilst using it **and** toast chestnuts on it. I spent a fortune on "quiet" CPU coolers but they all ended up sounding like Concorde taking off every time I did anything remotely CPU-intensive. :wink:

---

### Post by cascade9 on 2010-12-21
> **coffeecat said:**
> Perhaps my feelings are coloured by a 3 GHz P4 I used to use. I was able to switch off the central heating whilst using it **and** toast chestnuts on it. I spent a fortune on "quiet" CPU coolers but they all ended up sounding like Concorde taking off every time I did anything remotely CPU-intensive. :wink:

Sign of the times, o cat on caffeine. The AMDs werent so hot, but in some cases almost as loud. I've never heard anything like the way P4s would go whiiirrrr-WHIIIIRRR-whiiirrrr as you [played with system load.  

I ended up moving to watercooling due to the screaming of 6000-7000 RPM fans.

---

### Post by coffeecat on 2010-12-21
> **cascade9 said:**
> Sign of the times, o cat on caffeine. The AMDs werent so hot, but in some cases almost as loud.

Perhaps I was lucky. At the time I was also running a machine with a single-core AMD64 with a similar performance, and it was an oasis of peace compared with the P4. The most I ever heard, even when under heavy load, was the distant whisper of a gentle summer breeze. :wink:

---

### Post by JKyleOKC on 2010-12-21
> **Putnam11 said:**
> Assuming they pay around $100 for a Windows license to put on your computer that you would end up deleting anywaysMany years ago I worked for a company that had to license Windows for redistribution as part of a complete system they sold. This was in the days of Windows 3.1, so costs have increased a bit since then, but we paid just fifty cents per copy! I seriously doubt that Dell pays more than $5 for each Win7 license -- but unless Microsoft has changed its OEM policies greatly, they pay that on every system they build, not just on the ones that ship with Win7 installed.

---

### Post by Putnam11 on 2010-12-21
Still, with Dell only paying <$20, you're saving a fortune building your own computer.  Cascade may be right about the PSU and Mobo, although I've only had bad experience with Athena and Sunbeam.  
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817371023](http://www.newegg.com/Product/Product.aspx?Item=N82E16817371023)
This might be decent for a PSU, 430W made by Antec.  Has 5-star ratings on Newegg, $39.95
I'm not sure about the motherboard, I've only had experience with Gigabyte ones.  Might want someone else around here to recommend one.
@cascade9, the compr currently has 512MB of DDR 333 RAM, so I would asume 4GB to be roughly 8x faster, and then 1333 DDR3 RAM vs 333 DDR RAM I would say is at least 3x faster.

---

### Post by JKyleOKC on 2010-12-21
Keep in mind that speed ratings for RAM are maximum speeds; the sticks can and will run slower than that. The clock speed on the motherboard's FSB (front side bus) is what determines the actual working speed of the RAM, so if you replace 333 DDR with the same amount of 1333 DDR, in the same motherboard, the speed won't change.

My experience has been that the amount of RAM installed, rather than its speed rating, is much more important to overall operating snappiness. This box with 3 GB of RAM is much snappier than my old one with only 512 MB, as I would expect. In fact, the virtual machines I run on this system are much faster than my wife's rather ancient machine, which was a state-of-the-art gaming monster in its day but has only 512 MB of RAM (in both cases the O/S is WinXP Pro; on the VMs to support my data recovery customers, and on her system by her preference).

---

### Post by Tharkun on 2010-12-21
A computer that is about 2 years old and you should be good for a while, five to ten years before you need to think about what you want to run and what you are able to run.  A few hundred dollars on a whole computer is better overall than incrementally upgrading things as you get more advanced tech overall.

---

### Post by cascade9 on 2010-12-22
> **Putnam11 said:**
> @cascade9, the compr currently has 512MB of DDR 333 RAM, so I would asume 4GB to be roughly 8x faster, and then 1333 DDR3 RAM vs 333 DDR RAM I would say is at least 3x faster.

Adding more RAM doesnt make the RAM any faster. ;)  

Generally, if somebodys computer is hitting swap (with any amount/type of RAM), then adding more RAM will help a  lot, but if swap isnt being used, it wont make any difference at all.

> **coffeecat said:**
> Perhaps I was lucky. At the time I was also running a machine with a single-core AMD64 with a similar performance, and it was an oasis of peace compared with the P4. The most I ever heard, even when under heavy load, was the distant whisper of a gentle summer breeze. :wink:

A64s tended to come with semi-decent AMD heatsink and fans. 

The 'screamers' tended to be from the days of 'OEM' retail AMD CPUs, when (almost) everybody used aftermarket heatsinks.

---

### Post by Pantera116 on 2010-12-22
Non integrated graphics is always a good idea.

Regard the RAM why dont you run the Gnome system monitor 
while processing your photos. If it shows heavy swap partition
use you Know you would benefit from more RAM.

I was asked by a friend to help with a sick GX270. What i found
was that it has (in the small format case style version) a
reputation for running very hot. This eventually degrades the 
capacitors on the motherboard. You can tell if yours is suffering
if the top of the capacitors are bulging upwards rather than being
flat. This particular PC would reboot itself after a minute of use.

If you have the full tower version and your capacitors are ok a few 
secondhand bits off ebay could really peep your PC up.

The ram was DDR standard in the one i looked at.

this link may be good for reference

[http://www.dell.com/downloads/us/products/optix/gx270_spec.pdf]("http://www.dell.com/downloads/us/products/optix/gx270_spec.pdf")

If you do want to go down the new pc route i can personally recommend the
AMD triple core AM3 style CPU. I put a machine together for my wife earlier
this year gigabyte ATX AM3 PCIE motherboard 4 gb DDR3 500GB hard
drive. I had the case, PSU, ATI 800 GTO Graphics and optical drives already.
Cost of new hardware was £250. She paid £94 for win 7 64bit Home premium retail.
Boot up and shut down is about the same as linux on a 2Ghz single core!
Much faster and quieter than her old XP machine.

---

### Post by mlnease on 2010-12-23
Hello All,

I really appreciate all the responses.  I must confess myself somewhat flummoxed.  As is often the case, my simple questions:



[LIST]
[*]Do I need a faster processor?
[/LIST]
[INDENT][INDENT]Intel Pentium 4 CPU 2.80GHz
[/INDENT][/INDENT]
[LIST]
[*]More memory?
[/LIST]
[INDENT][INDENT]494.9MB
[/INDENT][/INDENT]
[LIST]
[*]A better video card?
[/LIST]
[INDENT][INDENT]00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
[/INDENT][/INDENT]
[LIST]
[*]Maybe just a new computer all round?
[/LIST]
[INDENT][INDENT]Dell Optiplex GX270

[/INDENT][/INDENT]have resulted in not-so-simple answers.  I now know that I need to consider (in no particular order):


[LIST]
[*]the capacitors on the motherboard
[/LIST]

[LIST]
[*]a semi-decent AMD heatsink and fans
[/LIST]

[LIST]
[*]clock speed on the motherboard's FSB
[/LIST]

[LIST]
[*]P4's
[/LIST]

[LIST]
[*]a dedicated graphics card
[/LIST]

[LIST]
[*]an AGP video card
[/LIST]

[LIST]
[*]a 'yum-cha' power supply
[/LIST]

[LIST]
[*]DDR3 1333
[/LIST]

[LIST]
[*]speed ratings for RAM
[/LIST]

[LIST]
[*]hitting swap (with any amount/type of RAM)
[/LIST]

[LIST]
[*]AMD triple core AM3 style CPU
[/LIST]

[LIST]
[*]gigabyte ATX AM3 PCIE motherboard
[/LIST]

[LIST]
[*]gb DDR3 500GB hard drive
[/LIST]

[LIST]
[*]PSU
[/LIST]

[LIST]
[*]ATI 800 GTO Graphics and optical drives
[/LIST]
I'm sorry to confess that I understand little more than bits and pieces of any of the above.

I hope this doesn't seem sarcastic, I don't mean it that way--truly--and I do genuinely appreciate all the responses.

I must confess, though, that I'm thinking now more along the lines of an analog television and an abacus.

So even though it doesn't seem exactly appropriate, I think it's time to mark this thread 'SOLVED'.

Thanks *very *much (sincerely) again for all your advice and 

Happy Holidays,

mike

---

### Post by cascade9 on 2010-12-24
> **mlnease said:**
> Hello All,

I really appreciate all the responses.  I must confess myself somewhat flummoxed.  As is often the case, my simple questions:

[LIST]
[*]Do I need a faster processor?
[/LIST]
[INDENT][INDENT]Intel Pentium 4 CPU 2.80GHz
[/INDENT][/INDENT]
[LIST]
[*]More memory?
[/LIST]
[INDENT][INDENT]494.9MB
[/INDENT][/INDENT]
[LIST]
[*]A better video card?
[/LIST]
[INDENT][INDENT]00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
[/INDENT][/INDENT]
[LIST]
[*]Maybe just a new computer all round?
[/LIST]
[INDENT][INDENT] Dell Optiplex GX270
[/INDENT][/INDENT] 

I'll try to make it simpler. 

You could replace the CPU, but that will be complicated. You'd need to check the moterhboard to see if it can get a faster CPU and figure out if the power supply will take a faster CPU. If you did decide to upgrade the CPU, you'd need to find a 2nd hand CPU, order it and install it. 

It might be possible, but unless you're very lucky a CPU upgrade problably wont help much. 

Video card upgrades are almost as bad. RAM is not so complicated, but its still not super easy.  

Honestly, you are probably best off opening htop (dont use gnome system monitor, it imposes to much load), running GIMP with your hi-res images and do your normal thing. If you are getting high/100% CPU use,then more CPU would help. If you're getting high/100% RAM use, more RAM would help. My guess is that both RAM and CPU sue will be high, and you would be better off with a new system. 

> **mlnease said:**
> 

[LIST]
[*]the capacitors on the motherboard
[/LIST]

[LIST]
[*]a semi-decent AMD heatsink and fans
[/LIST]

[LIST]
[*]clock speed on the motherboard's FSB
[/LIST]

[LIST]
[*]P4's
[/LIST]

[LIST]
[*]a dedicated graphics card
[/LIST]

[LIST]
[*]an AGP video card
[/LIST]

[LIST]
[*]a 'yum-cha' power supply
[/LIST]

[LIST]
[*]DDR3 1333
[/LIST]

[LIST]
[*]speed ratings for RAM
[/LIST]

[LIST]
[*]hitting swap (with any amount/type of RAM)
[/LIST]

[LIST]
[*]AMD triple core AM3 style CPU
[/LIST]

[LIST]
[*]gigabyte ATX AM3 PCIE motherboard
[/LIST]

[LIST]
[*]gb DDR3 500GB hard drive
[/LIST]

[LIST]
[*]PSU
[/LIST]

[LIST]
[*]ATI 800 GTO Graphics and optical drives
[/LIST]
I'm sorry to confess that I understand little more than bits and pieces of any of the above.

I hope this doesn't seem sarcastic, I don't mean it that way--truly--and I do genuinely appreciate all the responses.


Were you taking notes? :S 

Most of those things arent worth worrying about. 

Capacitors? Pantera116 has a point, but if you arent getting semi-random or random shutdowns, dont worry about it. 

AMDF heatsinks and fans- AMD bundles decent heatsinks these days. 

Clock speed and P4s- only worth worrying about if you decide to go for an upgrade. 

Dedicated graphics card- worth thinking about if you decide to upgrade or get a new computer. AGP cards are thin on the ground hese days, an dcost about twice as much as the PCIe (modern systems) version of the same card. Another reason to go for a new computer. 

'Yum-cha' power supplies. Honestly, thats slang for 'peice of junk'. If you get a new system, or if you decide to upgrade and a new power supply is a needed (or at least a good idea) get a decent power supply

DDR3- only worth thinking about if you're gettign a new system. Pretty much everything aroudn now is using DDR3, apart from some 'old stock' using DDR2. 

Hitting swap- thats just to see if you are using all your RAM but the system wants more. 

Triple core AM3 AMD CPU + gigabyte ATX AM3 PCIE motherboard- I havent even seen a triple core AM3 CPU. This is something for if you get a new system. 

gb DDR3 500GB hard drive- wires crossed. DDR3 is RAM, HDDs are HDDs. 

ATI 800GTO- No. Dont even think about it. Thats a 5 year old card, with no current ATI drivers for it.

---

### Post by QLee on 2010-12-24
[QUOTE=mlnease]...

I am woefully ignorant of hardware so please excuse what is probably an extremely elementary question:  What hardware should I upgrade to improve the speed of manipulations via GIMP of large digital graphic files?  


[LIST]
[*]Do I need a faster processor?
[/LIST]
[INDENT][INDENT]Intel Pentium 4 CPU 2.80GHz
[/INDENT][/INDENT]
[LIST]
[*]More memory?
[/LIST]
[INDENT][INDENT]494.9MB
[/INDENT][/INDENT]
[LIST]
[*]A better video card?
[/LIST]
[INDENT][INDENT]00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
[/INDENT][/INDENT]
[LIST]
[*]Maybe just a new computer all round?
[/LIST]
[INDENT][INDENT]Dell Optiplex GX270[/QUOTE]

[/INDENT][/INDENT] I hear you when you say you want a simple answer. 

In my opinion that would be:

Most bang for your buck, as the saying goes, max your memory. It looks like that would be 2 or 4 G depending on the chassis of your model, sd;sf;smt.

If you plan on a lot of editing in the future, buy a new computer.

Those are my simple suggestions.

---

### Post by mlnease on 2010-12-24
Cascade9, 

Many thanks for this--it really does help a lot.  Also many thanks once again to all you other posters for your patience and kind attention.  I'll take it from here.

mike

---

