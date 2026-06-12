---
title: "Ubuntu VERY slow on Desktop"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by dniezby on 2009-02-26
Any thoughts on a few of these issues?

Ubuntu shows no splash screen or anything (like it does on my laptop) when it's loading up. My family (unfamiliar with Ubuntu) thinks the computer shut down and keeps shutting it off in the middle. 

Getting passed the missing loading or splash screen, when I do anything, it really really moves slow. As you can guess, I'm baffled by this because I'm used to how fast everything works and how efficient it is on my laptop.

It almost seems as though it was windows with a severely fragmented drive. I know Ubuntu doesn't store files the same way so fragmentation is rare (or did I hear this wrong) so I'm guessing that's not the problem.

Is there anything I can do to test the system and figure out what might be causing these lag issues?

---

### Post by smani on 2009-02-26
Start by posting your hardware info, say the output of
```
sudo lshw
```

---

### Post by dniezby on 2009-02-26
Wow, there is a lot of info here: 

>  description: Mini Tower Computer
    product: Dell DE051
    vendor: Dell Computer Corporation
    serial: 8CFYJ91
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=44454C4C-4300-1046-8059-B8C04F4A3931
  *-core
       description: Motherboard
       product: 0WF887
       vendor: Dell Computer Corp.
       physical id: 0
       serial: ..CN708215CG08GP.
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A01 (01/03/2006)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.53GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: Microprocessor
          size: 2533MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 256KiB
             capacity: 256KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DIMM_1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: DIMM_2
             size: 512MiB
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
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-communication
                description: Modem
                product: FA82537EP 56K V.92 Data/Fax Modem PCI
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@0000:01:01.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=serial latency=64 maxlatency=62 mingnt=1
           *-network
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 02
                serial: 00:16:76:0d:54:b2
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.10.5 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
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
        *-ide
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
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: WDC WD800BB-75JH
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 06.0
                serial: WD-WMAM9M951930
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d0f4738c
              *-volume:0
                   description: Windows FAT volume
                   vendor: Dell 8.0
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT16
                   serial: 07d6-0217
                   size: 39MiB
                   capacity: 39MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=DellUtility
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: da9336a5-70fb-eb49-a76c-e6d44623775b
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2006-02-23 00:58:09 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   description: Windows FAT volume
                   vendor: Dell 8.0
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: FAT32
                   serial: 0000-0000
                   size: 3048MiB
                   capacity: 3074MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=DellRestore
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 43GiB
                   capacity: 43GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 41GiB
                      configuration: mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1859MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD+-RW GWA4164B
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: D108
                serial: [HL-DT-STDVD+-RW GWA4164BD10805/07/14
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
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
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0e:96:53:ee:d4:5e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


---

### Post by Kareeser on 2009-02-26
Hardware checks out.

Celly 2.53 GHz
1 GB RAM
Onboard graphics card...

---

### Post by achase79 on 2009-02-26
boot from the liveCD and run this
```
fsck -f /dev/sda5
```
This will help fix any errors caused by the computer being turned off before finished shutdown.

---

### Post by semitone36 on 2009-02-26
How long has it been running Ubunu?
Have you tried reinstalling?

---

### Post by smani on 2009-02-26
Hardware specs are fine, intel onboard graphiccards often work even better than nvidia or ati ones ... 
Anyway, if you happen to have a usb stick somewhere, try booting a clean ubuntu installation off the usb stick an see if you still get these issues (you can use the integrated tool or unetbootin for example).

---

### Post by Peter09 on 2009-02-26
When you get to the Grub prompt hit esc and grub will stop the boot process. Leave the normal kernel selected and type e (for edit). this will get you to the boot parameters. Remove the options for Quiet and change the parameter splash to nosplash.

(I'm doing this from memory ---) Finally hit the b key and the system will continue to boot, but you will be able to see what is happening. 

What you have done is only temporary and things will be as normal when you boot next time.

---

### Post by dniezby on 2009-02-26
A lot of questions in a single refresh. First let me say thanks for the quick help. (Another reason to DeWindowfy)
So, here are some answers:

What's a grub propt? 

I have not tried to reinstall.

I've been running Ubuntu on this computer only for a few days.

---

### Post by Peter09 on 2009-02-26
As the computer boots you will see (for only a few seconds) a menu of boot options (not your BIOS ). As soon as you see this hit esc and the machine will not continue to boot, but wait for a command.

---

### Post by semitone36 on 2009-02-26
> **dniezby said:**
> 
I have not tried to reinstall.

I've been running Ubuntu on this computer only for a few days.

Unless you enjoy challenges I would just try reinstalling, especially since you probably havent amassed too many irreplaceable personal files in just a few days.  

Reinstalling (sometimes with a new CD) has worked wonders for me in the past but normally only do it if you have no other choice or if you just installed recently.

---

### Post by dniezby on 2009-03-02
I may have to go with a fresh install. I need to expand the Ubuntu partition anyway. I've virtually eliminated a need for windows. So now I can give it even more space.

---

