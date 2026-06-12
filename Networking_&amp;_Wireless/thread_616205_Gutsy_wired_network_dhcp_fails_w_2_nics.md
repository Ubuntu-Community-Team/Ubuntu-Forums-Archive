---
title: "Gutsy wired network dhcp fails w/ 2 nics"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by metrodcjay on 2007-11-18
I've done quite a bit of reading and experimenting, but haven't had any luck yet getting either of my nics to work whether I assign a static ip or use dhcp.  Here's my lshw and ifconfig info.  Ideas?  Thank you.

-metrodcjay

ubuntu
    description: Space-saving Computer
    product: OptiPlex GX100
    vendor: Dell Computer Corporation
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=enabled boot=normal chassis=space-saving frontpanel_password=enabled power-on_password=enabled uuid=44454C4C-3994-104A-804D-B8C04F303042
  *-core
       description: Motherboard
       product: OptiPlex GX100
       vendor: Dell Computer Corporation
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A10 (08/30/2001)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Celeron (Mendocino)
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.6.5
          slot: Microprocessor
          size: 466MHz
          capacity: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr up
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KB
             capacity: 32KB
             capabilities: internal varies unified
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 128KB
             capacity: 128KB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 128MB
          capacity: 512MB
        *-bank:0
             description: DIMM SDRAM Synchronous 100 MHz (10.0 ns)
             physical id: 0
             slot: DIMM_A
             size: 128MB
             width: 64 bits
             clock: 100MHz (10.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 100 MHz (10.0 ns) [empty]
             physical id: 1
             slot: DIMM_B
             width: 64 bits
             clock: 100MHz (10.0ns)
     *-pci
          description: Host bridge
          product: 82810 DC-100 (GMCH) Graphics Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display
             description: VGA compatible controller
             product: 82810 DC-100 (CGC) Chipset Graphics Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pm vga bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810
        *-pci
             description: PCI bridge
             product: 82801AA PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-multimedia
                description: Multimedia audio controller
                product: ES1371 [AudioPCI-97]
                vendor: Ensoniq
                physical id: 7
                bus info: pci@0000:01:07.0
                version: 06
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ENS1371 latency=64 maxlatency=128 mingnt=12 module=snd_ens1371
           *-network:0
                description: Ethernet interface
                product: RTL-8029(AS)
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ethernet physical
                configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 latency=0 module=ne2k_pci multicast=yes
           *-network:1
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: c
                bus info: pci@0000:01:0c.0
                logical name: eth1
                version: 78
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
        *-isa
             description: ISA bridge
             product: 82801AA ISA Bridge (LPC)
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
             product: 82801AA IDE Controller
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
                description: SCSI Disk
                product: ST36811A
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.09
                size: 6149MB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 5828MB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 321MB
                   capacity: 321MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 321MB
                      capabilities: nofs
           *-cdrom
                description: SCSI CD-ROM
                product: CD-ROM SN-124
                vendor: SAMSUNG
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: S003
                capabilities: removable audio
                configuration: ansiversion=5 status=open
        *-usb
             description: USB Controller
             product: 82801AA USB Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-serial UNCLAIMED
             description: SMBus
             product: 82801AA SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
     *-scsi
          physical id: 1
          bus info: usb@1:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: U3 Cruzer Micro
             vendor: SanDisk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.02
             size: 483MB
             capabilities: removable
             configuration: ansiversion=2
           *-disc
                physical id: 0
                logical name: /dev/sdb
                size: 483MB
                capabilities: partitioned partitioned:dos
              *-volume
                   description: W95 FAT32 partition
                   physical id: 1
                   logical name: /dev/sdb1
                   capacity: 478MB
                   capabilities: primary


ifconfig
eth0      Link encap:Ethernet   
          inet6 addr: fe80::2e0:29ff:fe28:2b2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48720 (47.5 KB)  TX bytes:18759 (18.3 KB)
          Interrupt:10 Base address:0xeca0 

eth1      Link encap:Ethernet    
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:197 (197.0 b)  TX bytes:60 (60.0 b)
          Interrupt:5 Base address:0x2c00 

eth0:avah Link encap:Ethernet  
          inet addr:169.254.3.46  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0xeca0 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10912 (10.6 KB)  TX bytes:10912 (10.6 KB)

---

### Post by ofb on 2007-11-18
Have you tried disabling network-manager? Either by deselecting it in Prefs>Sessions, or by uninstalling through Synaptic. I've always found it got in the way on my two machines with two NIC each.

---

### Post by metrodcjay on 2007-11-19
Update:  I followed the suggestion and removed network-manager, but I´m still not able to get an ip address.

---

### Post by ofb on 2007-11-20
Well, crud.

Let's be thorough then. With network-manager out of the way, did you open the Sys>Admin>Network GUI, assign DHCP and Static IP as appropriate to your connections [Presuming DHCP for your internet, and IP for your LAN], deselect their Roaming Mode, then back on the first panel make sure there is a little checkmark in the checkbox for each?

Which is not to insult your intelligence, just an agreement with you that it really ought to be working - so let's make sure all details are correct. May as well check your cables while at it, and give the thing a reboot. Though I'm pretty sure the latter is unnecessary for this, and is more of a good-luck superstition after years of Windows.

Dual-boot by chance? How's the connection with that?

And does a LiveCD connect, and what settings does it use?

Oh, and what are you doing for firewall? And is there a router involved?


EDIT: 6.10? I seem to recall you may not have the checkbox for Roaming Mode. I think that showed up in 7.04 or 7.10. Memory suggests in its place was something like 'Activate this connection'.

---

### Post by metrodcjay on 2007-11-20
I did some further testing as follows.

1. I tested network cable/router port by plugging it into another machine.  It was able to obtain an IP via DHCP.
2.  The machine isn't really beefy enough to handle a Live CD.  I installed Gutsy using the alternate CD.
3. It's a fresh install - repartitioned and not dual boot.
4. I took IPv6 out of the picture by adding it to a bad_list file
4. To test further I assigned (via Terminal/Pico not GUI) each NIC a static IP, netmask , gateway and made sure the resolv.conf has my proper router IP.
5. I then set up to capture traffic so I could do some ping tests.
6. From the machine I am able to ping/receive replies from other devices on my network EXCEPT my router.  From other devices I can ping/receive replies from my router.
7. I am able to see broadcast traffic from other devices on my network.
8. I am able to ping the problem machine (either NIC) from other devices on my network.
9. I cannot ping/receive replies from Internet devices (outside my network) by IP or name
10. I cannot perform DNS resolution for Internet devices

I'll do some more testing, but suggestions are most welcome.  Thanks.

---

### Post by ofb on 2007-11-20
You read this one already?
[http://ubuntuforums.org/showthread.php?t=354031](http://ubuntuforums.org/showthread.php?t=354031)

---

### Post by arkhitekton on 2007-11-25
Hi metrodcjay

I've had a similar problem when I've tried to install Ubuntu 7.10 on a Dell GX100.  During the alternative CD install the network card was not being configured - DHCP was not working.  [Too cut a long story short] I noticed that the repair and command line installs both detected the network card and configured it correctly using DHCP.  So I did a command line only system install from the alternative CD.  When that was finished I logged in and ran:-
> **sudo apt-get install ubuntu-desktop**The gnome windows manager and the rest of the applications were then installed.  It's a bit of a long way round but at least I got Ubuntu 7.10 up and running on the Dell GX100.

---

### Post by metrodcjay on 2007-11-25
> **ofb said:**
> You read this one already?
[http://ubuntuforums.org/showthread.php?t=354031](http://ubuntuforums.org/showthread.php?t=354031)

I hadn't.  Good info, thanks.  

However, I finally figured out the problem.  I made the the mistake of looking past the basics in solving this.  It turned out that I had just forgotten I needed to add the address to my router - I'm using mac address filtering.  Oh well I'm sure I'm not the only one to have made this boneheaded move.

---

