---
title: "Wireless not working - Ubuntu starting to lockup"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by linux_newf on 2009-01-30
Hey guys, i've had Hardy on my laptop now for close to a year i guess and its been very smooth until the last few weeks or so.

The main thing is my wireless stopped working - I really thought it was a hardware problem but it started working this morning unexpectly.

Anyhow, i just rebooted my laptop and its not working anymore.

I've been using wireless now for mths.

Where can i get some info on this problem? I really can't remeber how i got it working in the first place....

---

### Post by porchrat on 2009-01-30
We recently had a kernel header update in Ubuntu Hardy.  Generally when that happens the wireless drivers no longer point to the right locations.  You probably need to reload the drivers.

Could you run this command in the terminal and post the ouput:

```
lshw -C network
```

---

### Post by linux_newf on 2009-01-30
> **porchrat said:**
> We recently had a kernel header update in Ubuntu Hardy.  Generally when that happens the wireless drivers no longer point to the right locations.  You probably need to reload the drivers.

Could you run this command in the terminal and post the ouput:

```
lshw -C network
```

```
brad@Brad:~$ lshw -C network
WARNING: you should run this program as super-user.
brad@Brad:~$
```
           
I can't remember how to login has the super used - sudo or something?

---

### Post by boof1988 on 2009-01-30
> **linux_newf said:**
> ```
brad@Brad:~$ lshw -C network
WARNING: you should run this program as super-user.
brad@Brad:~$
```
           
I can't remember how to login has the super used - sudo or something?

Just add the "sudo" before the command.

```
sudo lshw -C network
```

Also (for more information on using sudo) you can try: 

```
man sudo
```

---

### Post by linux_newf on 2009-01-30
Can someone help me out here? My wireless hasn't been working now for a few weeks.

Thanks

Whoops thanks for the feedback. I used the command again and PCI (sysfs) comes up but disappears.

btw when i right click on my network icon the "Enable Wireless" is not there anymore but rather "Edit wireless" near the bottom.

---

### Post by buffy^ on 2009-01-30
Please could you do 
```
ifconfig
```

And paste the results in below.

---

### Post by linux_newf on 2009-01-30
> **buffy^ said:**
> Please could you do 
```
ifconfig
```

And paste the results in below.

```
brad@Brad:~$ ifconfig     
eth0      Link encap:Ethernet  HWaddr 00:1b:24:9b:cd:4e  
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe9b:cd4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14596 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16606716 (15.8 MB)  TX bytes:3078482 (2.9 MB)
          Interrupt:19 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:976 errors:0 dropped:0 overruns:0 frame:0
          TX packets:976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48800 (47.6 KB)  TX bytes:48800 (47.6 KB)

```

---

### Post by buffy^ on 2009-01-30
Its not seeing it at all is it. On the laptop do you havea wireless power button is that set to on?

Also do you know what the make and model of your wireless is?

---

### Post by linux_newf on 2009-01-30
> **buffy^ said:**
> Its not seeing it at all is it. On the laptop do you havea wireless power button is that set to on?

Also do you know what the make and model of your wireless is?

Yep its on, maybe the hardware is broke or something. Just found it weird it was working this morning after 2 weeks of nothing.

All i know its a Broadcom card.

---

### Post by buffy^ on 2009-01-30
I used to run an NX6110 and the wireless button didnt work in linux, driver issue i think. However if i turned it off in bios and then booted into linux, then reboot truned it back on and booted into linux it would detect it again.

If that dosnt work we could remove the drivers and reinstall them.

---

### Post by linux_newf on 2009-01-30
> **buffy^ said:**
> I used to run an NX6110 and the wireless button didnt work in linux, driver issue i think. However if i turned it off in bios and then booted into linux, then reboot truned it back on and booted into linux it would detect it again.

The thing is i've been using wireless for mths up to a few weeks ago.

Beats me. Maybe it was an update that messed it up.

Thanks for the help.

---

### Post by Neural oD on 2009-01-30
maybe it somehow got uninstalled - do a sudo lshw  - and look for something that could indicate your wireless card. If this shows up - it means the kernel can see the card - which is good.

---

### Post by linux_newf on 2009-01-30
> **Neural oD said:**
> maybe it somehow got uninstalled - do a sudo lshw  - and look for something that could indicate your wireless card. If this shows up - it means the kernel can see the card - which is good.

Nothing it seems, strange for sure. Can a regular computer tech fix this for me? Or would he need to be aware of ubuntu?

```
 description: Notebook
    product: Presario F700 (GR967UA#ABA)
    vendor: Hewlett-Packard
    version: Rev 1
    serial: CNF7380QLG
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 uuid=434E4637-3338-3051-4C47-001B249BCD4E
  *-core
       description: Motherboard
       product: 30D3
       vendor: Quanta
       physical id: 0
       version: 65.37
       serial: None
       slot: &#65533;&#65533;@
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.1C (08/16/2007)
          size: 101KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.8.1
          slot: Socket S1
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps cpufreq
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
             size: 256KiB
             capacity: 512KiB
             capabilities: synchronous internal write-through unified
     *-memory:0
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM Synchronous 200 MHz (5.0 ns)
             product: NT512T64UH8B0FN-3C
             vendor: F7F7F7B000000000
             physical id: 0
             serial: 8B267323
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
             clock: 200MHz (5.0ns)
        *-bank:1
             description: DIMM 200 MHz (5.0 ns)
             product: NT512T64UH8B0FN-3C
             vendor: F7F7F7B000000000
             physical id: 1
             serial: A8467323
             slot: DIMM 2
             size: 512MiB
             width: 64 bits
             clock: 200MHz (5.0ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.8.1
          size: 1800MHz
          capacity: 1800MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
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
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-display
          description: VGA compatible controller
          product: MCP51 PCI-X GeForce Go 6100
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list
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
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
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
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
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
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          logical name: scsi2
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
        *-cdrom
             description: DVD-RAM writer
             product: CD/DVDW TS-L632M
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 0A17
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=open
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          logical name: scsi0
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: ATA Disk
             product: ST9120822AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.BH
             serial: 5LZ5VJFR
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00075a66
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                logical name: /dev/.static/dev
                version: 1.0
                serial: a66bd24b-ea00-447c-8e5a-81cada86626b
                size: 109GiB
                capacity: 109GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: created=2008-04-24 18:15:07 filesystem=ext3 modified=2009-01-30 10:27:20 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-01-30 08:02:24 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2769MiB
                capacity: 2769MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2768MiB
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
          capabilities: pci ht subtractive_decode bus_master cap_list
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
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: 00:1b:24:9b:cd:4e
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.2.11 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
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

```

---

### Post by buffy^ on 2009-01-30
> **linux_newf said:**
> Nothing it seems, strange for sure. Can a regular computer tech fix this for me? Or would he need to be aware of ubuntu?


It depends, if he was to pop the wireless card out and drop it in a normal laptop then there should be a problem. If the techie isnt aware of ubuntu it will be very hard from him to trouble shoot in a forigen enviroment.

---

### Post by Neural oD on 2009-01-30
if it's not picking it up - it might be that your wireless card is fried. 
Before taking it in though run a livecd - and see if the wireless card shows up

Hope that helps

---

### Post by linux_newf on 2009-01-30
> **buffy^ said:**
> It depends, if he was to pop the wireless card out and drop it in a normal laptop then there should be a problem. If the techie isnt aware of ubuntu it will be very hard from him to trouble shoot in a forigen enviroment.

So he could check to see if my card is working by putting it in another laptop? If so that's what i might do.

btw the toogle switch is on but the light is still orange but when i woke this morning it was suddenly blue, which means its working. I'm starting to believe its my card.

Thanks everyone for the help.

PS If i do need a new card what should i get?

---

### Post by buffy^ on 2009-01-30
Yes dropping it into another laptop would help to determin if its a hardware failure. However from what your saying it still be a possible driver issue, maybe power managment. Just so you know the cost of a new wireless card for a laptop should be around £10

---

