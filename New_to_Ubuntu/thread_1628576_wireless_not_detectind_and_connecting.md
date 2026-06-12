---
title: "wireless not detectind and connecting"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by aagavin on 2010-11-22
I am Using Ubuntu 10.10 and I am trying to connect to a Wireless network but it doesn't seem detect the network, so I tried to connect to a hidden network and I but it loops back to asking me for the password

also I have install the Broadcom STA wireless drive

---

### Post by spikoley on 2010-11-22
Double check your password and if that doesn't work then try connecting with out encryption and make it visible.  Once you connect then turn on each feature one at a time after connecting.

---

### Post by Dark7man on 2010-11-23
> **aagavin said:**
> I am Using Ubuntu 10.10 and I am trying to connect to a Wireless network but it doesn't seem detect the network, so I tried to connect to a hidden network and I but it loops back to asking me for the password

also I have install the Broadcom STA wireless drive

Sent You a PM mate - might be able to help! :)

---

### Post by aagavin on 2010-11-23
> **spikoley said:**
> Double check your password and if that doesn't work then try connecting with out encryption and make it visible.  Once you connect then turn on each feature one at a time after connecting.

ok I tried that but it still doesn't connect 
it tries to connect and then just disconnects

---

### Post by aagavin on 2010-11-23
> **Dark7man said:**
> Sent You a PM mate - might be able to help! :)
Here is the output of the command you sent me
```
aaron-pc
    description: Notebook
    product: Compaq Presario CQ50 Notebook PC
    vendor: Hewlett-Packard
    version: F.06
    serial: 2CE8255ZPT
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=oem-specific chassis=notebook uuid=D2AFF100-44B8-11DD-AB4F-A83153A7773A
  *-core
       description: Motherboard
       product: 360A
       vendor: Wistron
       physical id: 0
       version: 08.36
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.06 (06/10/2008)
          size: 102KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon Dual-Core QL-60
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon Dual-Core QL-60
          slot: Socket A
          size: 950MHz
          capacity: 1900MHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit lbrv svm_lock nrip_save cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 2MiB
             capabilities: synchronous internal write-through unified
     *-memory:0
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DRAM Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: S1
             size: 2GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DRAM Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: S2
             size: 1GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 5
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
          resources: ioport:1a00(size=256)
     *-serial
          description: SMBus
          product: MCP78S [GeForce 8200] SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:3080(size=64) ioport:3040(size=64) ioport:3000(size=64)
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
          resources: memory:c0080000-c00fffff
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
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:17 memory:c0006000-c0006fff
     *-usb:1
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:17 memory:c0007000-c00070ff
     *-usb:2
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:16 memory:c0008000-c0008fff
     *-usb:3
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:16 memory:c0007400-c00074ff
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
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:30c0(size=16)
     *-multimedia
          description: Audio device
          product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:20 memory:c0000000-c0003fff
     *-pci:0
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-ide:1
          description: IDE interface
          product: MCP78S [GeForce 8200] SATA Controller (non-AHCI mode)
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: scsi3
          logical name: scsi4
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
          resources: irq:41 ioport:30f0(size=8) ioport:30e4(size=4) ioport:30e8(size=8) ioport:30e0(size=4) ioport:30d0(size=16) memory:c0004000-c0005fff
        *-cdrom
             description: DVD-RAM writer
             product: DVD RW AD-7561S
             vendor: Optiarc
             physical id: 0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: AH03
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: ST9250827AS
             vendor: Seagate
             physical id: 1
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: 3.AH
             serial: 5RG20KER
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00093d20
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 9e155c6a-e30b-401c-8b0d-f9b3df0e1361
                size: 184GiB
                capacity: 184GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2010-11-22 19:52:48 filesystem=ext4 lastmountpoint=/&#65533;|&#1515;&#65533;&#65533;&#65533;!i&#65533;&#65533;L7&#65533;&#65533;&#65533;H7&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;}&#1515;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2010-11-22 20:02:02 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-11-23 08:12:44 state=mounted
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: eca5-7931
                size: 90MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-11-17 18:32:06 filesystem=ntfs label=System Reserved state=clean
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@4:0.0.0,3
                logical name: /dev/sda3
                logical name: /media/A880AABD80AA917C
                version: 3.1
                serial: 229c952d-caeb-4d41-b8e7-277a74a801b0
                size: 39GiB
                capacity: 39GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-11-17 18:32:11 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@4:0.0.0,4
                logical name: /dev/sda4
                size: 8096MiB
                capacity: 8096MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 8096MiB
                   capabilities: nofs
     *-network
          description: Ethernet interface
          product: MCP77 Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: 00:1d:72:61:99:2d
          size: 100MB/s
          capacity: 100MB/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.154 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: irq:42 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
     *-pci:1
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:0b.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm ht normal_decode bus_master cap_list
          resources: ioport:4000(size=4096) memory:c1000000-c1ffffff ioport:c4000000(size=469762048)
        *-display
             description: VGA compatible controller
             product: C77 [GeForce 8200M G]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:19 memory:c1000000-c1ffffff memory:d0000000-dfffffff memory:c4000000-c5ffffff ioport:4000(size=128) memory:c6000000-c601ffff
     *-pci:2
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 memory:c2000000-c20fffff
        *-network
             description: Wireless interface
             product: BCM4312 802.11b/g LP-PHY
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@0000:07:00.0
             logical name: eth1
             version: 01
             serial: 00:21:00:25:94:a6
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
             resources: irq:23 memory:c2000000-c2003fff
     *-pci:3
          description: Host bridge
          product: Family 11h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h Processor Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 11h Processor DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
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
     *-pci:7
          description: Host bridge
          product: Family 11h Processor Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: c
          bus info: usb@1:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
```

---

### Post by cariboo on 2010-11-23
Depending on your wireless chipset the b43 driver may work better for you. Use System->Administration->Additional Drivers to remove the wl (STA) driver, then install the b43 driver.

---

### Post by aagavin on 2010-11-23
ok I tried that but it didn't seem to work??

---

### Post by anewguy on 2010-11-23
Please post back the output of the following:

lshw -C network

lspci

ifconfig

iwconfig

and if the adapter is USB or this is a notebook:

lsusb


We'll go from there.  BTW - I have found that once you try to set up a connection manually, such as to hidden network via network manager, and it fails to connect, you are better off to go into network manager and delete all references/definitions to that connection, then start from scratch.  Without doing the deletes first it always seems to grab the definition that didn't work.

Dave ;)

---

### Post by Dark7man on 2010-11-23
Sorry for the late response back mate - long day - I have the same WLAN card as I said in the PM - I read numerous threads and tried quiet a few different fixes.  How I got mine completely cured was by going into Synaptics Package Manager ...

Bare in mind I'm a noob still to Linux, **so any gurus dont shoot me down for trying to help but keep me right here** :D... just had the same problems as You and after 3-4 days of playing around and 3 fresh Ubuntu installs later #-o heres what I found worked for me;

1.  Ensure your connected to the internet via ethernet cable.
2.  I checked I'd install all the updates listed in "Update Manager":
       System > Administration > Update Manager
3.  Rebooted.
4.  Open "Synaptics Package Manager":
          System > Administration > Synaptic Package Manager.
5.  In top right hand corner "Search" type just the letters "BCM"

Now in the search results listed below, for me when I done this I had like 5 items installed, proved to be overkill from trying so many different fixes.

What You want to do is ensure You only have the 3 following packages installed;    

Package:             Description:
bcmwl-kernel-source /Broadcom 802.11 Linux STA wireless driver source  
b43-fwcutter        /Utility for extracting broadcom 43xx firmware  
bcmwl-modaliases    /Modaliases for the Broadcom 802.11 Linux STA
                       Driver
(See attached screenshot)

You'll notice they are the only 3 in the search results with the Ubuntu logo to the left of their name.

If You have any extra packages installed other than just the 3 listed above + in screenshot, right click and select "Mark for removal".  Edit your packages until it is the same as the screen shot I've attached.  Click apply!
After the process has finished... reboot and keep your fingers crossed :)

Go it a go pal, I tried loads of different scenarios and this one proved lucky for me, trial and error.  Hope its of some help to You!

Keep us posted how You get on!
Good Luck! :guitar:

---

### Post by nm_geo on 2010-11-23
Gurus,

Why does the wireless have eth1 as the logical name, and not wlan0?  Just wondering?

---

### Post by Dark7man on 2010-11-23
> **nm_geo said:**
> Gurus,

Why does the wireless have eth1 as the logical name, and not wlan0?  Just wondering?

Any info on this would be great!! my adapter still has the logical name eth1, and is working fine... I had noticed this but after I got my wlan working and connected, I took the "if its not broke dont fix it" approach and moved on to sound config etc.  I was always curious and as to what possible side-effects this would have?  Configuring any applications or - does it matter at all... as long as You remember and use the correct logical name then everything should be fine?

Anybody on light to shed on this? :) Gurus?

---

### Post by nm_geo on 2010-11-23
Dark7man is your wired connection working well too?  

I know how to change the eth1 to wlan0, but I just wondered if it was needed. Like you I would probably take the "if it's working leave it alone" approach.. Nope I would change it just to see..;)

If you get brave 
```
 sudo gedit /etc/udev/rules.d/70-persistent-net.rules

```You can change it there but it might break your connection [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]
Well I really don't think it would.

---

### Post by Dark7man on 2010-11-23
Yeah both of my connections are working fine... the thing of it being misnamed has bothered me indeed.. just wasn't at the top of my list as it was doing its job anyhow... I'm gonna have a play with that little command You gave me later (Well bit earlier in the morning when I relocate and get to run a full backup... I seem to be having a little prob or I don't get exactly how BackInTime works... I'm a bit all over the place, trying to learn all the terminal commands and how to configure the system via console, but still trying to complete all aspects of my setup before I really dive in a get under to the internals :)  Loving Ubuntu so far though, its limitless :)

---

### Post by nm_geo on 2010-11-23
I will show you mine if you show me yours LOL

```
$ cat /etc/udev/rules.d/70-persistent-net.rules

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x14e4:0x1600 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*",  ATTR{address}=="00:18:8b:c1:24:e5", ATTR{dev_id}=="0x0",  ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4312 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*",  ATTR{address}=="00:19:7d:c5:67:29", ATTR{dev_id}=="0x0",  ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

---

### Post by Dark7man on 2010-11-23
Yeah Yeah look at You LOL - showing off cuz You have Your shoes on the right feet! haha... ok gimme a sec I'm gonna give it a go here... If I disappear... it means I killed it and I'll be on tomorrow cursing and moaning lol! here goes...

---

### Post by nm_geo on 2010-11-23
> **Dark7man said:**
>  I'm a bit all over the place, trying to learn all the terminal commands and how to configure the system via console, but still trying to complete all aspects of my setup before I really dive in a get under to the internals :)  Loving Ubuntu so far though, its limitless :)

Believe me I understand.. I am just like you and yes it is limitless.

I am the proud multi-booter of windoz XP3, Ubuntu 10,04 and Fedora 14 (just for fun)  I like Ubuntu best so far..

---

### Post by Dark7man on 2010-11-23
OK I ran this command just to have a peek first... 

Code:

 cat /etc/udev/rules.d/70-persistent-net.rules

and this is what it gave me...
Code:

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:26:9e:33:a1:13", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:26:5e:8f:f8:33", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:26:5e:8f:f8:33", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

eth0 = my onboard LAN Card I know is working fine...
eth1 = my onboard WLAN Card - misnamed but behaving and do as it should... :)
wlan0 = I assue this must be my USB WLAN Dongle I was playing around with in the mean time...

I would much rather have my USB Dongle renamed wlan1 and my ONBOARD WLAN card named wlan0 (instead of eth1) so using gedit here... it gonna be like editing a word doc and then just saving? lol I'm gonna play here anyway...

---

### Post by Dark7man on 2010-11-23
Dude how do You get your code to kind of ... indent... see the way Yours is inside a nice box? I tried just typing "Code:" then pasting the code below... hasn't worked...
PS: I'm not jacking this thread on the own just waiting on him to come back and try out my advice :) helping my fellow man haha :)

---

### Post by nm_geo on 2010-11-23
Excellent maybe that is why your wireless is eth1 and it all works. I would not mess with it at all  :p

---

### Post by nm_geo on 2010-11-23
> **Dark7man said:**
> Dude how do You get your code to kind of ... indent... see the way Yours is inside a nice box? I tried just typing "Code:" then pasting the code below... hasn't worked...
PS: I'm not jacking this thread on the own just waiting on him to come back and try out my advice :) helping my fellow man haha :)

Hit the # sign in the reply box paste your info in between the Code boxes 
```
I did it here
```

The Gurus use it to put the codes in or ask the Noobs to reply in it.

---

### Post by Dark7man on 2010-11-23
> **nm_geo said:**
> Excellent maybe that is why your wireless is eth1 and it all works. I would not mess with it at all  :p

If I go in and run the gedit command on the same config I take it will let me edit the script manually?  (Guess work here)

So if  I go in and change nothing other than the NAME= would it really kill something on me... and if that being the case... would going back and undoing the changes I made not revert it back? :)

Thanks for the code pasting tip amigo :D

---

### Post by nm_geo on 2010-11-23
I would really ask someone who knows more than I the kernal thing worries me.

---

### Post by nm_geo on 2010-11-23
> **Dark7man said:**
> If I go in and run the gedit command on the same config I take it will let me edit the script manually?  (Guess work here)

So if  I go in and change nothing other than the NAME= would it really kill something on me... and if that being the case... would going back and undoing the changes I made not revert it back? :)

Thanks for the code pasting tip amigo :D

Like I said the logical name is tied to a kernal,

just don't know and I would hate to mess you up.

---

### Post by Dark7man on 2010-11-23
Yeah - I will be coming back to it though, going to start reading up on BASH Script and that - start doing a bit of homework before I start pulling bits off to fix... lol - Sorry to "Thread Owner" for the noise I've been making here... skip back a page and see my suggestion to try - not trying to hijack Your thread :)

---

### Post by nm_geo on 2010-11-23
Yes we are both sorry for gathering beans in this manner, but I had hope the OP would return with good news or we might get an answer about the eth1 to wlan0 change.. I am out of here be well Dark7man

---

### Post by Dark7man on 2010-11-23
> **nm_geo said:**
> Yes we are both sorry for gathering beans in this manner, but I had hope the OP would return with good news or we might get an answer about the eth1 to wlan0 change.. I am out of here be well Dark7man

Agree with You there mate!
Take it easy mate! :)

---

### Post by anewguy on 2010-11-24
As for the eth1/wlan0 thing, as shown in the output from Dark7man, eth1 and wlan0 are the same device wlan0 being the bridge and eth1 being the actual wireless (you can see the PCI addresses and the MAC addresses are the same).

As far as your USB dongle you said you were messing with, it's not showing in that list.

With the device plugged in, do lsusb in a terminal window and post back here.

Also, that device plugged in, you may want to try:

lshw -C network

and

ifconfig

and

iwconfig

Should give an idea of a driver is needed for it or not.

Dave ;)

---

### Post by Dark7man on 2010-11-24
> **anewguy said:**
> As for the eth1/wlan0 thing, as shown in the output from Dark7man, eth1 and wlan0 are the same device wlan0 being the bridge and eth1 being the actual wireless (you can see the PCI addresses and the MAC addresses are the same).

As far as your USB dongle you said you were messing with, it's not showing in that list.

With the device plugged in, do lsusb in a terminal window and post back here.

Also, that device plugged in, you may want to try:

lshw -C network

and

ifconfig

and

iwconfig

Should give an idea of a driver is needed for it or not.

Dave ;)

Dave I'm appreciating the help and helping me and others understand how things work... the OP however "aagavin" we are still waiting to hear back from... I got into some conversation with a fellow member last night when we were both trying to assist the OP... He'll be glad to see plenty of feedback I'm sure :)  Thanks again Dave

---

### Post by anewguy on 2010-11-25
Oooopppppssss - I guess I got lost there.  If it's any excuse, I lost control of my car on ice on the freeway Monday, went across 3 lanes of noon highway traffic and hit a large freeway light pole at about 50+.  My brain is still a little scrambled and I lose my train of thought.

Good luck here guys!  I'll back away until my mind's clearer!  ;)

Dave ;)

---

### Post by Dark7man on 2010-11-25
> **anewguy said:**
> Oooopppppssss - I guess I got lost there.  If it's any excuse, I lost control of my car on ice on the freeway Monday, went across 3 lanes of non highway traffic and hit a large freeway light pole at about 50+.  My brain is still a little scrambled and I lose my train of thought.

Good luck here guys!  I'll back away until my mind's clearer!  ;)

Dave ;)

WOW - thats nasty mate! Hope Your ok!  Don't go anywhere mate, best thing to do is keep Your mind occipied, hang in there!  Hope Your feeling better soon though!

Take Care!

---

