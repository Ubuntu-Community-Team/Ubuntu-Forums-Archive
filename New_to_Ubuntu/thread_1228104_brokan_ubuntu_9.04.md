---
title: "brokan ubuntu 9.04"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by r.v.the.evil on 2009-07-31
well i am new on ubuntu 9.04 and has installed it yesterday
it is my first try 2 linux, ,
but i m nt happy
broken graphics , no audio and internet not working, i even dont know what 2 do
i have a compaq laptop with athlon x2 dual core (amd 64)
processor and raedon graphics card 
can anyone really help me 
please waiting for reply

---

### Post by ukripper on 2009-07-31
What is your compaq laptop model?

---

### Post by Idefix82 on 2009-07-31
Welcome! Don't worry, to most problems there is a solution.

Let's start with the graphics. If you go to System->Administration->Hardware Drivers, are you offered a graphics driver? If so then activate it.

Next for the internet. How are you trying to connect to the internet (wired or wireless, via router or not, ...)?

We also need to know what your ethernet card and/or wireless card are. Please go to Applications->->Accessories->Terminal and type in
```
lshw -C network
```
the copy the output and paste it here.

I'm sure people will be able to sort you out.

---

### Post by Liolikas on 2009-07-31
You have topic about internet.

follow this to get graphics:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Show outpout of command: 
lspci
(we have to know audio card model)

---

### Post by r.v.the.evil on 2009-07-31
2 gb ram and 3200 raedon graphics
well in hardware devices it only shows broadcam device
which is bluetooth
i am using wvdial on tata indicom plug to surf 1280 sxc modem
a usb

---

### Post by Liolikas on 2009-07-31
> **r.v.the.evil said:**
> 2 gb ram and 3200 raedon graphics
well in hardware devices it only shows broadcam device
which is bluetooth
i am using wvdial on tata indicom plug to surf 1280 sxc modem
a usb
Show output of lspci command.

---

### Post by r.v.the.evil on 2009-07-31
Well can i chek it on window i have to reboot system again and again
because internet work on vista

---

### Post by Idefix82 on 2009-07-31
What is the output if you type in the terminal
```
lsusb
```

---

### Post by Idefix82 on 2009-07-31
> **r.v.the.evil said:**
> Well can i chek it on window i have to reboot system again and again
because internet work on vista

Just do all the commands, save the output in a file on the Windows partition, then reboot, open the file and paste its content here.

---

### Post by Liolikas on 2009-07-31
Oh you are really in big problem:
lspci > lspci.txt
Then grab lspci.txt into USB drive into windows to paste here.

Better forget this for a while and concentrate on fixing internet.

---

### Post by philinux on 2009-07-31
> **r.v.the.evil said:**
> well i am new on ubuntu 9.04 and has installed it yesterday
it is my first try 2 linux, ,
but i m nt happy
broken graphics , no audio and internet not working, i even dont know what 2 do
i have a compaq laptop with athlon x2 dual core (amd 64)
processor and raedon graphics card 
can anyone really help me 
please waiting for reply

Before attempting to fix other problems. You really need the net.

Can you connect wired.

---

### Post by r.v.the.evil on 2009-07-31
internet has been fixed by wvdial subscribed on another thread now i am on ubuntu
and lsusb gives
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 138a:0001  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1b7d:070c  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:09b8 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Liolikas on 2009-07-31
You have graphics if not System->Administration->Hardware Drivers.
lspci is most interesting you have no sound?

---

### Post by Idefix82 on 2009-07-31
Excellent. Now you will need to apply the latest updates. Open the terminal once again and type in
```
sudo apt-get update
sudo apt-get upgrade
```

Then see if you are offered a graphics driver as I described before. If your sound still doesn't work then please provide the output from
```
lspci
```

---

### Post by r.v.the.evil on 2009-07-31
hardware devices show blutooth broadcam only
and lspci gives




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
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by Liolikas on 2009-07-31
```

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

```
So some search and:
[http://ubuntuforums.org/showthread.php?t=1124049](http://ubuntuforums.org/showthread.php?t=1124049)
Fix is there.;)

---

### Post by r.v.the.evil on 2009-07-31
update has been set it is taling time and slowing my net speed
but good thing is new packages are being installed

---

### Post by Liolikas on 2009-07-31
So everything fixed? Have fun then :D

---

### Post by r.v.the.evil on 2009-07-31
update is working but how can i get sound driversas that link really not help me as much

---

### Post by Liolikas on 2009-07-31
Edit /etc/modprobe.d/sound file and put this :
> 
options snd slots=snd-hda-intel,snd-hda-intel
options snd-hda-intel model=dell-m4-2
# 5Dex.Jpa__qQ4asA:SBx00 Azalia (Intel HDA)
alias snd-card-1 snd-hda-intel
# l4dC.vfAxXUx5zd4:RS780 Azalia controller
alias snd-card-0 snd-hda-intel


---

### Post by sonu 1807 on 2009-07-31
update would take a lot of time.... but once done ubuntu would prove to be a great fun.... after update (reboot will be probably required) in Applications ---> Add/Remove box type gstreamer and check boxes corresponding to plugins and also ubuntu restircted extras and then hit apply changes....

While you can connect to internet form network manager ... its much easier than having to type sudo wvdial in terminal.... I would again post it here in case you ignored it in another thread 

If you right click network manager... it will open up a network connection window ...in mobile broadband tab click add... a connectionn assistant will be there...go forward..choose tata indicom plug 2 surf...it will work automatically....u may have to edit it for ur username and pswd...during installation if you had not chosen india as your location then you have to choose india in assistant

---

### Post by r.v.the.evil on 2009-07-31
now the upgrade asks for closing all programs meet u tomorrow
be online to fix all eroors

---

### Post by r.v.the.evil on 2009-08-01
hello friends can any one help out
my graphics are still dumb
in hardware drivers ati is being shown but is not activating sound still not installing

---

### Post by r.v.the.evil on 2009-08-01
any one there to help

---

### Post by Idefix82 on 2009-08-01
How do you mean ATI is not activating? Have you clicked on it to activate the driver? What happens if you do?

Edit: to bump a thread after 10 minutes is spamming. 24 hours is the generally recommended time to wait on these forums before bumping.

---

### Post by sonu 1807 on 2009-08-01
rv go to this link for installing EnvyNG [http://albertomilone.com/envyfaq.html#A](http://albertomilone.com/envyfaq.html#A)

---

### Post by r.v.the.evil on 2009-08-01
firstly it was giving download failed installed the bug file from given adress
i again tried it and it has been downloaded 
and i had worked with graphics which are very good also
now how can i have sound

---

### Post by sonu 1807 on 2009-08-01
In the taskbar you will see the sound applet. Right click it and open Preferences. In select the device and track to control. It has 4,5 options ...see if any one among them work or not

---

### Post by r.v.the.evil on 2009-08-01
i tried all no one is working

---

### Post by sonu 1807 on 2009-08-01
I am afraid, I don't have much idea about this issue. Post the output of command "lshw" in terminal (Application -->Accesories -->); I am sure some one would be able to suggest a workaround. Sound has always worked in all ubuntu installations for me on different computers

---

### Post by r.v.the.evil on 2009-08-01
sound not working need help instantly no audio device showing on hardware drivers

---

### Post by r.v.the.evil on 2009-08-01
vendor: Hewlett-Packard
    version: 1
    serial: CND8360HHD
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook uuid=53A15BC7-600A-11DD-94FF-001EEC9D6538
  *-core
       description: Motherboard
       product: 30FB
       vendor: Hewlett-Packard
       physical id: 0
       version: 01.36
       serial: CND8360HHD
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.03 (06/27/2008)
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-cpu
          description: CPU
          product: AMD Athlon(tm) X2 Dual-Core QL-60
          vendor: Advanced Micro Devices [AMD]
          physical id: e
          bus info: cpu@0
          version: 15.3.1
          serial: NotSupport
          slot: Socket M2/S1G1
          size: 1GHz
          capacity: 1900MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit cpufreq
        *-cache:0
             description: L1 cache
             physical id: f
             slot: L1 Cache
             size: 128KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 10
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 11
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: SODIMM [empty]
             physical id: 0
             slot: SODIMM 0
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: M4 70T5663QZ3-CF7
             vendor: Samsung
             physical id: 1
             serial: CE00000000000000020835614AD876
             slot: SODIMM 1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
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
             capabilities: pci ht bus_master cap_list
           *-display
                description: VGA compatible controller
                product: RS780M/RS780MN [Radeon HD 3200 Graphics]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
           *-multimedia
                description: Audio device
                product: RS780 Azalia controller
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices [AMD]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-system:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0 module=sdhci_pci
           *-system:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.2
                bus info: pci@0000:08:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
           *-system:2 UNCLAIMED
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.3
                bus info: pci@0000:08:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD Host Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.4
                bus info: pci@0000:08:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth1
                version: 01
                serial: 00:21:00:56:24:ce
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
        *-pci:4
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:0a:00.0
                logical name: eth0
                version: 02
                serial: 00:1e:ec:9d:65:38
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64 module=ahci
           *-disk
                description: ATA Disk
                product: FUJITSU MHZ2250B
                vendor: Fujitsu
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8909
                serial: K617T882P8V0
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=31a431a3
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 08d7cbe3-0492-d34e-b4eb-d9a930227260
                   size: 48GiB
                   capacity: 48GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-06-06 23:46:23 filesystem=ntfs state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/disk
                   version: 3.1
                   serial: 9aa2d6e7-f3c6-f543-8720-551cb3c57910
                   size: 68GiB
                   capacity: 68GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-04-14 01:05:16 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 1a019133-cf20-4c4c-accf-305ccf1dced4
                   size: 66GiB
                   capacity: 66GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-04-13 05:18:43 filesystem=ntfs state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 48GiB
                   capacity: 48GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 46GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 2086MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-L633A
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: HH04
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
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
             capabilities: pci bus_master
     *-pci:1
          description: Host bridge
          product: Family 11h HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 11h Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 11h DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 11h Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d2:b9:ac:05:31:98
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ravi@ravi-laptop:~$

---

### Post by sonu 1807 on 2009-08-01
RV try this

In termina type sudo gedit /etc/modprobe.d/alsa-base... a file will open

add at the end of the file:

options snd-hda-intel model=laptop

click save and the afer it is saved close it then reboot

---

### Post by r.v.the.evil on 2009-08-01
hello is anyone there

---

### Post by r.v.the.evil on 2009-08-01
how to save file in terminal

---

### Post by r.v.the.evil on 2009-08-01
saved please wait for the reboot

---

### Post by sonu 1807 on 2009-08-01
when you paste this sudo gedit .... command in terminal a separte window will open which is of Gedit (gnome editor) ...it is just like notepad in windows just hit Ctrl + S to save it.... after that close terminal....

If I was not chatting with my GF u wud have been in lot of trouble:D...this is the last day i am going to be online...my IAS mains is coming in October...so fix it today only

---

### Post by r.v.the.evil on 2009-08-01
not worked actually
i have speakers in laptop
and in windows a light on sound button of laptops become white and red when it is  being muted in ubuntu it is continuos red and does not change 
no sound is coming but wen i use window (after reboot) sound comes 
it means no fault in speaker 
it is lack of drivers ,,, also no audio drivers are shown in system>hardware drivers

---

### Post by r.v.the.evil on 2009-08-01
well can i know ur profession 
i am persuing 3rd sem in B.tech in computer science trade

---

### Post by r.v.the.evil on 2009-08-01
?????????????????????

---

### Post by r.v.the.evil on 2009-08-01
ok bye then
i will try next day and find somone else
lots of thanks
for good graphics and internet connection 
let me find for sound elsa\e

---

### Post by sonu 1807 on 2009-08-01
Bro.. ATI does trouble...but this can't be a lack of driver issue...try googling ....give output of command lspci only (may be a separate thread)...though i belive if u now choose pulse-audio it shud work....see any thing us not set to be mute in open volume control




9

---

### Post by jacklinux on 2009-08-01
> **r.v.the.evil said:**
> well i am new on ubuntu 9.04 and has installed it yesterday
it is my first try 2 linux, ,
but i m nt happy
broken graphics , no audio and internet not working, i even dont know what 2 do
i have a compaq laptop with athlon x2 dual core (amd 64)
processor and raedon graphics card 
can anyone really help me 
please waiting for reply
To help you we need more infomation in what you want.
If your looking for fixes for the above then wait. No-one here knows everything

---

### Post by r.v.the.evil on 2009-08-01
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
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by r.v.the.evil on 2009-08-01
i am searching for drivers on net

---

### Post by keastes on 2009-08-01
looking around found this issue on the bug tracker try 
[https://bugs.launchpad.net/ubuntu/+bug/289127](https://bugs.launchpad.net/ubuntu/+bug/289127)

---

