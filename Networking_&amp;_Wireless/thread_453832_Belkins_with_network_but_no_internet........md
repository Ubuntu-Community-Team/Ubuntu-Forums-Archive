---
title: "Belkins with network but no internet......."
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by Ken UK on 2007-05-24
Hi all,

I just installed 7.04 and unlike the previuos version it worked like a charm which I am really chuffed about.
Only thing I need to wok out now is how to get the internet going.

I have a Belkins USB adaptor and Ubuntu seems to pick it up now I've enabled it but when I hover it over the Icon it says its connected at 0% but when I click on it the orange bar for the signal is nearly full.

After reading around I've come to the conclusion I need the Ndiswrapper and my windows drivers installed to get this working properly so I downloaded it and unpacked it and typed make in the terminal just like it tells you to do. The attached file is what I get.

Im guessing its something really obvious to a Linux user but Im completely new so Im not sure why Im getting all these errors.

Im loving Ubuntu so far and if I could, I would definitely full migrate from windows, cant wait to get this running so any help is appreciated :)

PS remember Im new so please try and keep it simple and fully explain things, thanks :D

EDIT: After reading around even more Im getting the idea that I should have used the Ndiswrapper especially for Ubuntu because I just got Ndiswrapper from the main Ndiswrapper site and thats why Im getting errors.
Question now is which do I need, whats the difference between ndiswrapper-utils-1.9  and ndiswrapper-commen and do they work the same as the one I downloaded?

---

### Post by Ken UK on 2007-05-25
If someone could at least explain to me why there is a ndiswrapper-utils-1.9 and ndiswrapper-common under Ubuntu packages that would provide at least alittle help. Im guessing they do two different things but which do I need?

Also does installing this Ubuntu version exactly the same as the plain one I found on the main Ndiswrapper site.

Thanks for any help.

---

### Post by Ken UK on 2007-05-27
hm I see Im not going to get much help anytime soon so I think I might leave it for now and have another go at Ubuntu sometime in the future again like last time. At least I got alot closer this time anyway.

---

### Post by Kourosism on 2007-05-27
> **Ken UK said:**
> hm I see Im not going to get much help anytime soon so I think I might leave it for now and have another go at Ubuntu sometime in the future again like last time. At least I got alot closer this time anyway.

Hi Ken,

Don't know if you'll read this, but I am having the exact same issue. I have an Advent 7113 with an inbuilt Wifi card.

I also have a Belkin F5D7050 USB adapter, and have also tried getting Ubuntu to recognise this, all to no avail.It would be ideal if I could get WiFi running before installing Ubuntu. While both can see nearby networks (my WEP secured network, and a nearby unprotected one) it simply cannot connect to either.

I too would be grateful for any help anyone could give.

---

### Post by pfwd.tech on 2007-05-27
I am too in the same boat.  See my thread [http://ubuntuforums.org/showthread.php?t=455034]("http://ubuntuforums.org/showthread.php?t=455034")
I have a Belkin f5d7050 Version 1000 and the chipset is GW3887 (ithink).  
I don't know:
What drivers i need? I cant find the inf and sys files in the setup.exe 
What Ndsiwapper version i need? 
If i need the PRISMAXP.sys and what to do with it )From the prism 54 Project

I too would be most greatful if someone could guide us through how to get our Belkins work.  Im assuming your all using f5d7050?  
What versions are you all using?

---

### Post by Austin_KW on 2007-05-27
There are at least 4 version of the belkin usb adapter. Some are prism chip set (? v100x), some are Zydas (?v400x) . Mine are the ralink chipset (v300x).. And some reports have them mislabled. You can figure out which you have from the working windows driver.

If you have the v3000 then the drivers (rt73usb)  supplied in ubuntu will not work, You appear to have a connection but it does not work. You need to follow this howto  [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

### Post by pfwd.tech on 2007-05-28
I have Version 1000 (v1000).  I found that out by
```
lsusb
```
I got this result
```
Bus 007 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi

```


So i take it that....
i need the Prism drivers 
Do i ndiswrapper this? is there any kind of guide for this belkin version?

---

### Post by Austin_KW on 2007-05-28
Ok, Some people report that later versions may not have changed the usb ID from 050d:7050. Do you have the CD that came with the usb dongle. If so you can check the .inf and .sys file for the file-name and ensure it is not something rt2500usb.sys/rt2500usb.inf or rt2500.sys etc.

If it is one of the ralink chipsets i can walk you through it, if it is prism then hopefully someone will post the howto.

---

### Post by pfwd.tech on 2007-05-28
Hi thanks for the reply, I don't have the CD with me,  (cant find it).
I assume that if i try one way then and it doesnt work then i can allways set it back to how it was?
Here is the info i have on the device
It is a Belkin f5d7050 
using ```
lsusb
``` i get the following Bu```
s 002 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi

```
By default i can see my wireless network but when i type in my passpharse it wont let me connect.

---

### Post by Ken UK on 2007-05-28
Thanks for all the reply's, when I get abit of time Ill try and make heads and tails of this all, Im completely new but If I struggle I will repost again. Im not sure what your talking about with these drivers though. Are these drivers made for linux for USB adaptors by people or has it got something to do with the Belkins windows drivers and Ndiswrapper?

Thanks anyway

---

### Post by pfwd.tech on 2007-05-28
I'm new too so i could be wrong on this....
Belkin  have at least 4 different versions of this usb's chipset each version has its own driver. Some work with hardly any fuss and some need ndiswrapper and a bit of patience.
Some versions require the windows drivers and some require Linux based drivers. 
You can find out which version you have by typing in lsusb into the terminal, however as i have been told some chipsets have misprinted version numbers. Which doesn't make things any easier.

I'm determined to get my wireless adapter working, i just need some guidance.
if i get anywhere with it i will post back and let you know.

---

### Post by Austin_KW on 2007-05-28
> By default i can see my wireless network but when i type in my passpharse it wont let me connect.
Can you post the output from the following commands
[I]
lshw -C net  ### to see what ubuntu thinks it is

iwconfig                                ### to see what config you have set
ifconfig -a                             ### ....
cat /etc/network/interfaces ### ...

iwlist scan ### to see what wireless networks you can see

lsmod ###To see what drivers are loaded, to check for conflicts.
[/i]

---

### Post by pfwd.tech on 2007-05-28
Ok here is lshw-c
```
Hardware Lister (lshw) - B.02.08.01
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.08.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )

```

---

### Post by pfwd.tech on 2007-05-28
this is lshw without the c flag
```
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:ec00-ec07 ioport:e880-e883 ioport:e800-e807 ioport:e480-e483 ioport:e400-e40f ioport:e080-e08f irq:19
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: iomemory:88000000-880000ff ioport:400-41f irq:10
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             logical name: scsi3
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:d400-d407 ioport:d080-d083 ioport:d000-d007 ioport:cc00-cc03 ioport:c880-c88f ioport:c800-c80f irq:19
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7170S
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                serial: [Optiarc DVD RW AD-7170S 1.00 Oct27,2006
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@3
       logical name: rausb0
       serial: 00:11:50:88:8e:54
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RT2500USBSTA driverversion=1.0.0 - BETA2 multicast=yes wireless=RT2500USB WLAN
pfwd@PFWD-UBUNTU:~$ lshw -C
Hardware Lister (lshw) - B.02.08.01
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.08.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )

pfwd@PFWD-UBUNTU:~$ lshw
WARNING: you should run this program as super-user.
pfwd-ubuntu               
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2047MB
     *-cpu
          product: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1596MHz
          capacity: 1596MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
     *-pci
          description: Host bridge
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82P965/G965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0
                description: VGA compatible controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 256MB
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=fglrx_pci latency=0
                resources: iomemory:c0000000-cfffffff iomemory:ff7f0000-ff7fffff ioport:9000-90ff irq:16
           *-display:1 UNCLAIMED
                description: Display controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 00
                size: 64KB
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: iomemory:ff7e0000-ff7effff
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:dc00-dc1f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Keyboard
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@1:1
                   version: 13.10
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=50mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:e000-e01f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:ffaffc00-ffafffff irq:18
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:ffaf8000-ffafbfff irq:22
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@03:00.0
                logical name: eth0
                version: 01
                serial: 00:1a:92:cb:2d:07
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.2.6 latency=0 multicast=yes
                resources: ioport:b800-b8ff iomemory:ff9ff000-ff9fffff irq:19
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@02:00.0
                logical name: scsi6
                logical name: scsi7
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: storage ahci_1.0 bus_master cap_list scsi-host
                configuration: driver=ahci latency=0
                resources: iomemory:ff8fe000-ff8fffff irq:16
           *-ide
                description: IDE interface
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@02:00.1
                logical name: scsi4
                logical name: scsi5
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: ide bus_master cap_list scsi-host
                configuration: driver=pata_jmicron latency=0
                resources: ioport:ac00-ac07 ioport:a880-a883 ioport:a800-a807 ioport:a480-a483 ioport:a400-a40f irq:17
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d480-d49f irq:23
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d800-d81f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d880-d89f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:ffaff800-ffaffbff irq:23
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb
                   description: Generic USB device
                   product: Belkin 54g USB Network Adapter
                   vendor: Belkin
                   physical id: 4
                   bus info: usb@3:4
                   version: 0.01
                   capabilities: usb-2.00
                   configuration: driver=rt2570 maxpower=300mA speed=480.0MB/s
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:ec00-ec07 ioport:e880-e883 ioport:e800-e807 ioport:e480-e483 ioport:e400-e40f ioport:e080-e08f irq:19
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: iomemory:88000000-880000ff ioport:400-41f irq:10
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             logical name: scsi3
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:d400-d407 ioport:d080-d083 ioport:d000-d007 ioport:cc00-cc03 ioport:c880-c88f ioport:c800-c80f irq:19
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7170S
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                serial: [Optiarc DVD RW AD-7170S 1.00 Oct27,2006
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@3
       logical name: rausb0
       serial: 00:11:50:88:8e:54
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RT2500USBSTA driverversion=1.0.0 - BETA2 multicast=yes wireless=RT2500USB WLAN

```

---

### Post by pfwd.tech on 2007-05-28
iwconfig:
```
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:ec00-ec07 ioport:e880-e883 ioport:e800-e807 ioport:e480-e483 ioport:e400-e40f ioport:e080-e08f irq:19
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: iomemory:88000000-880000ff ioport:400-41f irq:10
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             logical name: scsi3
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:d400-d407 ioport:d080-d083 ioport:d000-d007 ioport:cc00-cc03 ioport:c880-c88f ioport:c800-c80f irq:19
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7170S
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                serial: [Optiarc DVD RW AD-7170S 1.00 Oct27,2006
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@3
       logical name: rausb0
       serial: 00:11:50:88:8e:54
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RT2500USBSTA driverversion=1.0.0 - BETA2 multicast=yes wireless=RT2500USB WLAN
pfwd@PFWD-UBUNTU:~$ lshw -C
Hardware Lister (lshw) - B.02.08.01
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.08.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )

pfwd@PFWD-UBUNTU:~$ lshw
WARNING: you should run this program as super-user.
pfwd-ubuntu               
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2047MB
     *-cpu
          product: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1596MHz
          capacity: 1596MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
     *-pci
          description: Host bridge
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82P965/G965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0
                description: VGA compatible controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 256MB
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=fglrx_pci latency=0
                resources: iomemory:c0000000-cfffffff iomemory:ff7f0000-ff7fffff ioport:9000-90ff irq:16
           *-display:1 UNCLAIMED
                description: Display controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 00
                size: 64KB
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: iomemory:ff7e0000-ff7effff
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:dc00-dc1f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Keyboard
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@1:1
                   version: 13.10
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=50mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:e000-e01f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:ffaffc00-ffafffff irq:18
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:ffaf8000-ffafbfff irq:22
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@03:00.0
                logical name: eth0
                version: 01
                serial: 00:1a:92:cb:2d:07
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.2.6 latency=0 multicast=yes
                resources: ioport:b800-b8ff iomemory:ff9ff000-ff9fffff irq:19
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@02:00.0
                logical name: scsi6
                logical name: scsi7
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: storage ahci_1.0 bus_master cap_list scsi-host
                configuration: driver=ahci latency=0
                resources: iomemory:ff8fe000-ff8fffff irq:16
           *-ide
                description: IDE interface
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@02:00.1
                logical name: scsi4
                logical name: scsi5
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: ide bus_master cap_list scsi-host
                configuration: driver=pata_jmicron latency=0
                resources: ioport:ac00-ac07 ioport:a880-a883 ioport:a800-a807 ioport:a480-a483 ioport:a400-a40f irq:17
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d480-d49f irq:23
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d800-d81f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d880-d89f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:ffaff800-ffaffbff irq:23
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb
                   description: Generic USB device
                   product: Belkin 54g USB Network Adapter
                   vendor: Belkin
                   physical id: 4
                   bus info: usb@3:4
                   version: 0.01
                   capabilities: usb-2.00
                   configuration: driver=rt2570 maxpower=300mA speed=480.0MB/s
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:ec00-ec07 ioport:e880-e883 ioport:e800-e807 ioport:e480-e483 ioport:e400-e40f ioport:e080-e08f irq:19
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: iomemory:88000000-880000ff ioport:400-41f irq:10
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             logical name: scsi3
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:d400-d407 ioport:d080-d083 ioport:d000-d007 ioport:cc00-cc03 ioport:c880-c88f ioport:c800-c80f irq:19
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7170S
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                serial: [Optiarc DVD RW AD-7170S 1.00 Oct27,2006
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@3
       logical name: rausb0
       serial: 00:11:50:88:8e:54
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RT2500USBSTA driverversion=1.0.0 - BETA2 multicast=yes wireless=RT2500USB WLAN

```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1A:92:CB:2D:07  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fecb:2d07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27356579 (26.0 MiB)  TX bytes:1273844 (1.2 MiB)
          Interrupt:19 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

rausb0    Link encap:Ethernet  HWaddr 00:11:50:88:8E:54  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63384 (61.8 KiB)  TX bytes:169260 (165.2 KiB)

```

* cat /etc/network/interfaces *

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



auto eth0



```

*iwlist scan*
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

rausb0    Scan completed :
          Cell 01 - Address: 00:11:50:93:34:8E
                    Mode:Managed
                    ESSID:"Black Box"
                    Encryption key:on
                    Channel:11

```
lsmod
```
Module                  Size  Used by
binfmt_misc            14604  1 
rfcomm                 45352  0 
l2cap                  28160  5 rfcomm
bluetooth              62340  4 rfcomm,l2cap
ppdev                  11272  0 
fglrx                 623096  11 
acpi_cpufreq           10760  0 
cpufreq_conservative     9736  0 
cpufreq_powersave       3072  0 
cpufreq_userspace       6176  0 
cpufreq_stats           8416  0 
cpufreq_ondemand       10640  2 
freq_table              6336  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
tc1100_wmi              9224  0 
dev_acpi               17028  0 
pcc_acpi               15616  0 
sony_acpi               7064  0 
video                  19080  0 
button                 10016  0 
ac                      6920  0 
container               6144  0 
dock                   11992  0 
battery                12040  0 
asus_acpi              19756  0 
backlight               8448  1 asus_acpi
sbs                    17856  0 
i2c_ec                  6912  1 sbs
i2c_core               26496  1 i2c_ec
ipv6                  307456  14 
lp                     15048  0 
fuse                   51888  0 
snd_hda_intel          24224  1 
snd_hda_codec         262528  1 snd_hda_intel
rt73usb                36096  0 
rt2x00lib              13568  1 rt73usb
crc_itu_t               3456  1 rt73usb
prism54usb             18944  0 
prism54common          13952  1 prism54usb
mac80211              192388  4 rt73usb,rt2x00lib,prism54usb,prism54common
cfg80211               26512  1 mac80211
snd_pcm_oss            49536  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
rt2570                212800  1 
snd_seq_midi           11008  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
serio_raw               9092  0 
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4736  0 
iTCO_wdt               13648  0 
iTCO_vendor_support     5636  1 iTCO_wdt
psmouse                43536  0 
parport_pc             40104  1 
parport                43404  3 ppdev,lp,parport_pc
intel_agp              29504  1 
shpchp                 37404  0 
snd                    68904  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm
pci_hotplug            36228  1 shpchp
af_packet              27020  2 
evdev                  13056  4 
tsdev                  10112  0 
ext3                  143760  1 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
sd_mod                 25092  3 
sg                     40616  0 
sr_mod                 18980  0 
cdrom                  40744  1 sr_mod
pata_jmicron            9088  2 
usbhid                 29088  0 
hid                    34048  1 usbhid
ata_generic            10628  0 
ata_piix               17412  0 
ahci                   25348  0 
libata                137000  4 pata_jmicron,ata_generic,ata_piix,ahci
scsi_mod              166968  4 sd_mod,sg,sr_mod,libata
floppy                 67944  0 
r8169                  35720  0 
ehci_hcd               37004  0 
generic                 6532  0 [permanent]
uhci_hcd               28320  0 
usbcore               154416  7 rt73usb,prism54usb,rt2570,usbhid,ehci_hcd,uhci_hcd
thermal                16912  0 
processor              34952  2 acpi_cpufreq,thermal
fan                     6536  0 
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0 
commoncap               9472  1 capability

```

hope that helps let me know if i have copied over the wrong stuff.

---

### Post by Austin_KW on 2007-05-28
Ok it thinks it is an rt73.
It is loading two drivers; rt73usb which does not work and rt2570 which would conflict with it even if it did work.

Follow the instructions in the first post of this howto,[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) ,which will tell you how to download and install the rt73 driver and stop the rt73usb & rt2570 from loading on boot.

---

### Post by Austin_KW on 2007-05-28
Just noticed; Not that simple

It is also loading the prism54usb. 

Before you try my above suggestion "gksudo gedit /etc/modprobe.d/blacklist " and add the following lines to stop the ralink drivers from loading
[I]# blacklist ralink 
blacklist rt73usb
blacklist rt2570[/I]

The reboot, if it is a prism chipset this may fix it, if not then follow the link in the above post.

---

### Post by pfwd.tech on 2007-05-29
Thanks i got as far as step 2 last night and it was saying that i didnt have permissions to extract the drivers to the  usr/src folder. i stopped after that but i will try your new post when i get in from work

---

### Post by Austin_KW on 2007-05-29
Dont bother with the second post, Just re-read your outputs and the scan rausb0 is returning results. This suggest that it is the ralink drivers.

You can extract the file to your own home directory. He is just suggesting /usr/src as you may want to keep the sources because you will need to rebuild the driver anytime you install and boot a new kernel. If you do use /urs/src you will need sudo.

---

### Post by pfwd.tech on 2007-05-29
bit of a problem, 
i can't
sudo ifconfig wlan0 up 
or
sudo ifconfig wlan0 down
It says the the device cannot be found, i cant see any wireless networks now and also when i reboot the machine it crashes and text about loading hardware and network etc appears.  I can only boot into the system now when the Belkin adapter is out of the usb socket. 
Panic!!

---

### Post by Austin_KW on 2007-05-29
You can always blacklist the driver if it is causing problems. "gksudo gedit /etc/modprobe.d/balcklist"  and add a line 
blacklist rt73

Then plug in the adapter, and
lsmod | grep usbcore

to see what other usb drivers might be loaded. 

I am guessing that it is still loading prism54usb 

You can try then try blacklisting prism54usb and rmoving rt73 from the blacklist

---

### Post by pfwd.tech on 2007-05-29
yeah  done that, but i still cant  sudo ifconfig wlan0 up plus i still have no wireless network

---

### Post by pfwd.tech on 2007-05-29
ok i got a little bit further, instead of using the rausb0 or wlan0 i used wlan1 asi i saw it set in here:
iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     No scan results

```
when i entered the essid name and key i got this output:
```
sudo dhclient wlan1
There is already a pid file /var/run/dhclient.pid with pid 7052
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:11:50:88:8e:54
Sending on   LPF/wlan1/00:11:50:88:8e:54
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
not sure why this is still working.  i have removed the network manger once and that stopped me from accessing the Ethernet so i had to reinstall Ubuntu

---

### Post by pfwd.tech on 2007-05-31
Does the ssid name have to be one word?  I noticed that when i was adding it  via the terminal it had to be a single string.

---

### Post by pfwd.tech on 2007-05-31
Hi i've done some tampering.  
- Change the SSID name to Black on my router
- added the following:  
```
pete@pfwd:~$ sudo ifconfig wlan1 down
pete@pfwd:~$ sudo ifconfig wlan1 up
pete@pfwd:~$ sudo ifconfig wlan1 essid key Black
essid: Unknown host
ifconfig: `--help' gives usage information.
pete@pfwd:~$ sudo iwconfig wlan1 essid Black
pete@pfwd:~$ sudo iwconfig wlan1 key ------------------------
```
When i type:```
 pete@pfwd:~$ sudo dhclient wlan1
```
i get:
```
There is already a pid file /var/run/dhclient.pid with pid 7077
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:11:50:88:8e:54
Sending on   LPF/wlan1/00:11:50:88:8e:54
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

What does that mean?

Heres a copy of the interfaces: 
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto rausb0
iface rausb inet dhcp

auto wlan1
iface wlan inet dhcp
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     RT73 WLAN  ESSID:"Black"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     No scan results

```

lsmod | grep usbcore
```
usbcore               154416  5 rt73,usbhid,ehci_hcd,uhci_hcd

```
Do you know what i could do to get this working?

---

### Post by peterbrewer on 2007-06-26
> **Ken UK said:**
> hm I see Im not going to get much help anytime soon so I think I might leave it for now and have another go at Ubuntu sometime in the future again like last time. At least I got alot closer this time anyway.

Use fwcutter.  When you install it it will automatically do the rest.

---

