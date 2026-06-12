---
title: "Wireless Realtek 8170"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by gonzeaux on 2009-07-25
I have been following threads on this topic in MSI  Wind forums and Linux forums. I had installed 8.10 and was unable to get my wireless card working. I had searched and found instructions for using ndiswrapper and bogarting the Windows driver...no connection. BTW, the card works fine with Windows, Mandriva and Ubuntu Netbook Remix (all right out of the box with no fiddling around).

Then I found a disclaimer somewhere in Ubuntu online help to the effect that the current drivers for this card do not support WPA-2 encryption. Indeed, my little netbook seemed to be lost in a loop of asking for the password but never connecting.

BUT, UNR works fine. It puzzles me.Can somebody educate me about the driver setup in Ubuntu? UNR is fine but I would prefer straight Ubuntu. (Actually I would prefer straight Jack Black.....maybe later....).

Q) Can I get the wireless driver from UNR and insert it into 9.04 so I can connect?
Q) When I upgraded from 8.10 to 9.04, the new install apparently kept the previous driver, which in my case was the ndiswrapper/windows driver combination. Where may I find a functional Ubuntu driver that allows WPA-2 (If indeed such exists) and how do I install the driver. AND may I point out, installing drivers on the OS sold by the evil empire (You know which OS I speak of) is a snap compared to this drill....that has been my honest experience so far:

WINDOWS scenario: install driver. Either it is done automatically (plug and play), or one inserts the media that came with whatever it is; or google it, download, install following easy instructios. Re-boot may be required. I could do this in my sleep.

UBUNTU method: Get sucked in by hype and desire for an alternative to Windows. Hardware inoperative. Search the internet and discover others have had this problem and there appear to be several fixes (Boskastrona, ndiswrapper...I'm sure there are others). Attempt to follow instructions found in Forum threads or Boskastrona website. Device appears to be recognized by OS but no connection. Googling 'changing drivers in Ubuntu'....sure, I could just jump right in and take another degree, this time in Comp Sci...

I have read about half of Keir's Pocket Guide...great book, but doesn't seem to point me towards the remedy. Yes, I value education and knowledge and it would be wonderful to RTFM end to end and extract therefrom what I need. HOWEVER, I am just one small glitch away from happiness and functionality....or at least my MSI Wind U-100 is. Can anybody explain how I might jam a functional wireless driver into an otherwise great OS?

Thanks!!

---

### Post by swoll1980 on 2009-07-25
Everything you ever needed to know about [ndiswrapper]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?joomla/index.php").

---

### Post by mapes12 on 2009-07-25
Many of us share your frustration with wifi. Problem is that the vendors of wifi adapters are more than happy to have an alliance with the "evil empire" and distribute locked down drivers for the empires OS. The Linux devs do what they can and I'm sure much lobbying goes on behind the scenes but until such time as the vendors realise they are losing sales because we in the free world will not buy their products then we are somewhat stuffed!

To help us have a look at where you go from here perhaps you would be good enough to post the output to ```
lspci
``` and ```
sudo lshw
```
as a start.

IMHO ndiswrapper should be in the last chance saloon of solutions

Mark

---

### Post by LewRockwell on 2009-07-25
I did a quick search for "Realtek 8170" and didn't come up with much

I did notice realtek and 8170 coming up in separate places

maybe you might check:```
sudo lshw -C network
```that's a little "L"(shw) and a capital "C"

.

---

### Post by gonzeaux on 2009-07-25
Mapes: Thanks for your analysis and suggestion. the output of 'lspci':

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)

The output of 'sudo lshw':

sudo lshw
[sudo] password for walter: 
cute                      
    description: Desktop Computer
    product: U-100
    vendor: MICRO-STAR INTERNATIONAL CO., LTD
    version: Ver.001
    serial: FFFFFFFF
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=desktop uuid=00000000-0000-0000-0000-002185E7EFF1
  *-core
       description: Motherboard
       product: U-100
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
       version: Ver.001
       serial: FFFFFFFF
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 4.6.3 (12/03/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: CPU 1
          size: 800MHz
          capacity: 4GHz
          width: 32 bits
          clock: 533MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 24KiB
             capacity: 24KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 992MiB
        *-bank:0
             description: DIMM Synchronous [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: DIMM Synchronous [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 02
                serial: 00:21:85:e7:ef:f1
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.12 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: RTL8187SE Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 22
                serial: 00:21:85:b5:c9:86
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+net8187se driverversion=1.53+Realtek,07/10/2008,5.9067.0 ip=10.42.43.1 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
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
             product: 82801G (ICH7 Family) USB UHCI Controller #2
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
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: FUJITSU MHZ2160B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0000
                serial: K665T8C2CKND
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a8971d0b
              *-volume:0
                   description: Windows FAT volume
                   vendor: MSDOS5.0
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT32
                   serial: 80ae-9d55
                   size: 4000MiB
                   capacity: 4000MiB
                   capabilities: primary boot fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: bce99ed7-4f68-9049-9560-58eff6b0db51
                   size: 39GiB
                   capacity: 39GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-04-25 12:09:00 filesystem=ntfs label=OS_Install state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 22585021-419b-6e44-bd1a-3ab900d4cd3d
                   size: 3068MiB
                   capacity: 3074MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2005-05-06 10:31:00 filesystem=ntfs state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 103GiB
                   capacity: 103GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 100GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 2925MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
     *-scsi
          physical id: 1
          bus info: usb@1:6
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 52:7b:3b:af:dd:05
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


Just pasted the entire screen output in, please excuse me. I believe, mind you I am a beginner, that the output identifies my wireless card (Realtek 8187se) the driver ndiswrapper and network unavailable. It is toggled on, of course.

Mapes., I'd love to cease and desist with ndiswrapper....if someone could show me how to do so and replace it with a functional driver.

Thanks to all for your help!!

---

### Post by gonzeaux on 2009-07-25
Oh, one more thing....when the wireless is toggled on, the network icon on the top panel will indicate 'wireless network [name] active......the network name appears greyed out, as well as the radio button to select and the progress bar that gets brown as the connection is made. I only know that because it works fine in UNR. So how can I get a hybrid of the best parts of UNR (wireless driver) and 9/04 (everything else)?

Thanks again!!

---

### Post by mapes12 on 2009-07-26
As I see it you need to do 2 things:

1. Uninstall ndiswrapper
In synaptic search for ndiswrapper. You should have 3 packages installed- ndisgtk, ndiswrapper-common and ndiswrapper-utils-(version number). Mark them for complete removal. This link may also help but where the command line refers to "install" substitute "uninstall". If you installed ndiswrapper via some other means than Synaptic you will need to reverse the process.

2. Install native Linux support for your Realtek adapter:
[http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html](http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html)

[http://www.google.co.uk/search?hl=en&q=RTL8187SE+ubuntu&btnG=Search&meta=](http://www.google.co.uk/search?hl=en&q=RTL8187SE+ubuntu&btnG=Search&meta=)

---

### Post by gonzeaux on 2009-07-26
Mapes,
           I followed your advice. Removing ndiswrapper and its minions was successful. Downloading Boskie's drivers was a little trickier. It seems Firefox would only save the download to the desktop. Surely this is a sign of a dumbass beginner ignorant mistake. May I inquire, what would be the proper directory to place the driver package download into? May I ask how I might tickle Firefox into complying?

Anyways, I was able to run the command as given in Boskie;s MSI forum post with this result:


walter@CUTE:~/Desktop$ sudo dpkg -i linux-rtl8187se-*.deb 
[sudo] password for walter: 
(Reading database ... 112093 files and directories currently installed.)
Preparing to replace linux-rtl8187se-modules 1023@2.6.27.7.11 (using [email]linux-rtl8187se-modules-1023@2.6.27.7.11.deb[/email]) ...
Restoring previous drivers from backup.
/bin/mv: cannot stat `/lib/modules/rtl8187se-backup-2.6.27-7/rtl8187.ko': No such file or directory
Restoring drivers failed.
Unpacking replacement linux-rtl8187se-modules ...
Setting up linux-rtl8187se-modules (1023@2.6.27.7.11) ...
Making backup of existing IEEE80211 and RTL8187-USB drivers
/bin/mv: cannot stat `/lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/rtl8187.ko': No such file or directory
Something went wrong.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module r8180 not found.

I am a beginner, so I can not tell if this was successful or not. I would be most grateful for your advice...I have a gut feeling that I am neglecting obvious elementary steps that are unknown to me as a beginner.

Thanks again!!

---

