---
title: "Wifi not working on Acer laptop with Ubuntu 8.1"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by Rainbow-C on 2009-03-11
How do I make my wifi work?

I have a Acer, and it has a button near the screen that I press to enable wireless LAN

but when I'm in Ubuntu the light doesn't come on, and I cant connect to the internet.

if you need information from my laptop, just let me know, ill help however i can

thanks :3

---

### Post by martrn on 2009-03-11
Acer Laptops use different wifi chip-sets for different types of their Laptops.

If you want to determine what wireless card/chipset you have, open up a terminal and type the following.

```
lspci -v | less
```

Then make sure your wireless chipset card is supported by ubuntu.  Visit :  
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") .

Maybe if someone has the same chip-set of wireless cards, then they might know how to solve ?

---

### Post by Bölvaður on 2009-03-11
Follow this please¹:

*Applications² &#8594; Accessories &#8594; Terminal*
Type : ***lshw***
This is a list of most it not all your hardware. Please find the wireless card and post it here³

¹: I know you are not pleasuring me or your self over following these steps and it sounds absolutely *bananas*.. but somehow the English managed to make it not sound strange pleasing each other by handing over the salt during the evening's meal.

²: top left corner of your screen

³: This is a demonstration of my network card (not wireless)
```
  *-network
             description: Ethernet interface
             product: 82566DC Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 02
             serial: 00:19:d1:e3:a2:ac
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-0 ip=192.168.1.30 latency=0 module=e1000e multicast=yes

```

---

### Post by Rainbow-C on 2009-03-11
here is what i got when i typed in lshw in the terminal( like you said to do):
jenna@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 999MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU          530  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.6.1
          serial: 0001-0661-0000-0000-0000-0000
          size: 50MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe x86-64 constant_tsc up arch_perfmon pebs bts pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetLink BCM5906M Fast Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 02
                serial: 00:1b:38:69:41:d2
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 module=tg3 multicast=yes
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0 module=ahci
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:36:72:4e:79:74
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


i ahve no idea what it means.

---

### Post by Rainbow-C on 2009-03-11
anyone? HELPP ME

---

### Post by martrn on 2009-03-11
According to your specs you posted your networkcards are :

*-network
description: Ethernet interface
product: NetLink BCM5906M Fast Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:05:00.0
logical name: eth0
version: 02
serial: 00:1b:38:69:41:d2
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 module=tg3 multicast=yes
-----------------------------------

*-network UNCLAIMED
description: Ethernet controller
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:06:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0

According to the ubuntu supported list :
[https://help.ubuntu.com/../WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") and then clicking on various your Atheros Ethernet contoller is on the install system when installing from a new cd only.

The [http://madwifi.org/]("http://madwifi.org/") have install scripts to get the madwifi kernel modules (drivers) installed into your system.

There are howto to read there and stuff.
I am just going to read them.  Might be better if you did, as I don't need wifi drivers.  (Just answering your question how to make your wifi work - see madwifi).

---

### Post by martrn on 2009-03-11
See : [https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi]("https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi") for the community documentation of MadWiFi drivers (kernel modules).  From there you can debug and rebuild the wifi kernel modules (drivers).

Not exactly an easy task.

---

### Post by Rainbow-C on 2009-03-11
so what do i do?

im sorry, i have no idea where to go from there.

---

### Post by martrn on 2009-03-11
> **Rainbow-C said:**
> so what do i do? im sorry, i have no idea where to go from there.

1. Enable the back-ports repository for intrepid.  Type (at a terminal) ```
 sudo gedit /etc/apt/sources.list
``` and comment out all of the back-port repositories, and then

2. Goto a terminal and type : ```
sudo apt-get install ath5k
``` and reboot.

And then visit 
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros")
and follow steps 1 to 5 if that don't work.

and post back here ?????

---

### Post by Miljet on 2009-03-11
What version Ubuntu are you using? There is no longer any need to use madwifi for Atheros wireless cards. There is an open source driver available now and it is included in Ubuntu 8.10.

---

