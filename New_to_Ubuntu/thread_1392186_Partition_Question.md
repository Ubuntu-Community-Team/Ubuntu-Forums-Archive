---
title: "Partition Question"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by Zagoofeek on 2010-01-27
Okay so I need some help with this.  I have taken a screen shot of my GParted so everyone can see my partitions.  I installed Ubuntu not too long ago and my computer has been sort of lagging a little more with each use.  It lags while surfing the web, I have my visual effects at none, which helped a little.  I'm unsure if the reason I am having such bad lag is possibly due to still having a windows partition on my drive or just because I need to upgrade some of drive.  So my question is looking at the partition what do I have on here?  Do I still have windows?  Can someone break down what ext 3, extended, and linux-swap is?  Any advice would be appreciated if I should resize or remove any of the partitions.  Thanks.

---

### Post by nhasian on 2010-01-27
hello Zagoofeek,

your screenshot shows us that on your first drive which is 300 gigs, all of it is setup for your root partition except for 2.5 gigs reserved for the swap partition.  I dont see any windows partitions on this drive, but if you have a different hard disk it may be on that one.  there could be many reasons why your computer becomes slow.  to find out we will need more information.

you can copy/paste the output of the following terminal commands to help us troubleshoot your issue:

```
uname -a
```
```
lsb_release -a
```
```
free -m
```
```
lshw
```

also when your computer becomes slow, you can use the terminal command top to see whats taking up your resources

```
top
```

[COLOR="Red"]TIP[/COLOR] please remember to use the quote and code tags to properly format your output to make it easier to read

---

### Post by oldos2er on 2010-01-27
ext3 is a native Linux file system. For swap partition, see [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

What are your system specs?

---

### Post by phillw on 2010-01-27
> **Zagoofeek said:**
> Okay so I need some help with this.  I have taken a screen shot of my GParted so everyone can see my partitions.  I installed Ubuntu not too long ago and my computer has been sort of lagging a little more with each use.  It lags while surfing the web, I have my visual effects at none, which helped a little.  I'm unsure if the reason I am having such bad lag is possibly due to still having a windows partition on my drive or just because I need to upgrade some of drive.  So my question is looking at the partition what do I have on here?  Do I still have windows?  Can someone break down what ext 3, extended, and linux-swap is?  Any advice would be appreciated if I should resize or remove any of the partitions.  Thanks.

hi and welcome to the forums,

your partition table looks okay.

I am assuming you do not have more than 2.5GB of RAM in your computer.

The first thing to check is if the swap partition is being used.

```
free
```Should report back something like ..

> total       used       free     shared    buffers     cached
Mem:       1027580     325576     702004          0        204      115136
-/+ buffers/cache:     210236     817344
Swap:      3358712      10640    3348072

The numbers are not too important, just that there are some for Swap.

Post back what you get with that command.

Regards,

Phill.

---

### Post by Bucky Ball on 2010-01-27
No windows there.

If you want it I would install windows first leaving the rest of the disk blank then install ubuntu but this time make separate partitions for:

/
/home
/swap

... and anything else you might want. This can be done in the partitioning section of the install by clicking 'Manual Partitioning'. The / (root) partition need be no bigger than 15Gb, /home the rest leaving room for a 2Gb /swap (bigger not necessary) at the end.

---

### Post by Zagoofeek on 2010-01-28
I hope I did this in a way that makes it easy for you to read.

> ```
uname -a
```

This is what came up for this:
Linux lovemach 2.6.27-14-generic #1 SMP Wed Apr 15 19:29:46 UTC 2009 x86_64 GNU/Linux

> ```
lsb_release -a
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

> ```
free -m
```
             total       used       free     shared    buffers     cached
Mem:           874        822         52          0         92        300
-/+ buffers/cache:        428        445
Swap:         2557        107       2449


> ```
lshw
```
 description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 1
          size: 894MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          size: 2100MHz
          capacity: 2100MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
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
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
     *-display
          description: VGA compatible controller
          product: C51 [GeForce 6150 LE]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=nvidia latency=0 module=nvidia
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
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
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-ide:2
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master cap_list
        *-firewire
             description: FireWire (IEEE 1394)
             product: FW323
             vendor: Agere Systems
             physical id: 5
             bus info: pci@0000:03:05.0
             version: 70
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=24 mingnt=12 module=ohci1394
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k Data/Fax Modem
             vendor: Conexant Systems, Inc.
             physical id: 9
             bus info: pci@0000:03:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=32
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: 00:1a:92:2f:8f:8f
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.100 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
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
          configuration: driver=k8temp module=k8temp
  *-scsi
       physical id: 1
       bus info: scsi@8
       logical name: scsi8
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 76:69:5c:85:34:ee
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Zagoofeek on 2010-01-28
I have 1GB.
> ```
free
```

             total       used       free     shared    buffers     cached
Mem:        895020     841076      53944          0      94864     307812
-/+ buffers/cache:     438400     456620
Swap:      2618552     110296    2508256

I appreciate the help from all of you, I'm still trying to get to know Ubuntu.

---

### Post by nhasian on 2010-01-29
Zagoofeek,

based on the information you provided, i would recommend you increase the ram in your system.  That seems to be your biggest bottleneck.  Ram is cheap so it shouldn't be too expensive to put 2 or 4 gigs in your system.  Also is there a reason you are still using ubuntu 8.10?  You should consider doing a fresh install of 9.10 so you can utilize the newer EXT4 filesystem and grub2 bootloader.  then you will have a smooth upgrade path to Ubuntu Lucid Lynx 10.04 when it comes out in april.

---

### Post by mastablasta on 2010-01-29
More ram is always better, but can i ask why he needs to upgrade and why it is considered a bottleneck in this case? Afterall he has almoust 3 times amount of the requirements for RAM and he said vial effect are off.
 
I don't think RAM is really the issue here...

---

### Post by nhasian on 2010-01-29
> **mastablasta said:**
> More ram is always better, but can i ask why he needs to upgrade and why it is considered a bottleneck in this case? Afterall he has almoust 3 times amount of the requirements for RAM and he said vial effect are off.
 
I don't think RAM is really the issue here...

depends on what your running.  It's a good bet that the OP uses firefox, and firefox can eat up a ton of ram real fast.  on my machine its common for firefox to consume 300-500M of ram.  also i recommended upgrading the OS and filesystem so this should cover all the bases eh?  :)

---

### Post by dolphinaura on 2010-01-29
> **Zagoofeek said:**
> Okay so I need some help with this.  I have taken a screen shot of my GParted so everyone can see my partitions.  I installed Ubuntu not too long ago and my computer has been sort of lagging a little more with each use.  It lags while surfing the web, I have my visual effects at none, which helped a little.  I'm unsure if the reason I am having such bad lag is possibly due to still having a windows partition on my drive or just because I need to upgrade some of drive.  So my question is looking at the partition what do I have on here?  Do I still have windows?  Can someone break down what ext 3, extended, and linux-swap is?  Any advice would be appreciated if I should resize or remove any of the partitions.  Thanks.

the ext3/ext4 partition is what contains your linux install.
The extended partition contains the swap, which is the equivilent of a windows paging file.

Since you said that disabling visual effects helps, whats your graphics card model?

---

### Post by sgosnell on 2010-01-29
It's probably not the case on 8.10, but on later versions IPv6 is the slowdown.  Starting with 8.10, IPv6 is the default, and it takes a long time for it to find that it has to revert to IPv4.  Disabling IPv6 speeds up site loading by a lot.  I have IPv6 disabled both in Network Manager and in Firefox.

---

### Post by Zagoofeek on 2010-01-30
I haven't upgraded my ubuntu because I play WoW and I had a lot of issues getting it to run.  I thought maybe if I upgraded it would cause more issues, so I've avoided it.  With that in mind, what do you recommend?  Also by saying a fresh install, what do you mean exactly and how would I go about doing that?

---

### Post by Zagoofeek on 2010-01-30
My graphics card is an NVIDIA GeForce 6150 LE, which came with this pc.  Just in case anyone wanted to know my computer is an HP a1737c.  I haven't upgraded anything on it thus far.  I plan on possibly building a pc or just adding some RAM and upgrading the graphics card, but for now I want to be able to reduce the lag.

---

### Post by theozzlives on 2010-01-30
I'd recommend a seperate [/home]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/") Keep it ext3. you want a 20 GB / (root) Then install Jaunty (9.04) and reformat / to ext4. Jaunty is fast. When the time comes, you can upgrade to 10.04 LTS. Skip Karmic (9.10).

---

