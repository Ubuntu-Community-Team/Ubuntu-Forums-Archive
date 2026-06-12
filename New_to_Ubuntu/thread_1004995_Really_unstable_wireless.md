---
title: "Really unstable wireless"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by tegnoto89 on 2008-12-07
I'm connected to my college wireless, and I get booted off literally every ten minutes, and it takes a ton of tries to reconnect.  I used to connect just fine with windows, and I'm pretty sure all my authentication stuff is set up correctly.  How can I make it stop kicking me off?  NOTE: I had the same problem with ubuntu.

---

### Post by nixforme on 2008-12-08
A couple of questions:

1. Is this a fresh install?

2. What kind of wireless network do you have? If you don't know open a terminal and type this. Please post the output of both commands: 

```
lspci
```

and

```
sudo lshw -C network
```

3. Is this a school wide wireless network? or just a friends network?

---

### Post by tegnoto89 on 2008-12-08
okay the first thing:

tom@tom-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)                                                                  
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)                                                                   
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)                                                                      
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)                                                                  
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)                                                                  
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)                                                                 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)                                                                       
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)                                                                          
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
02:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

and the other:

 *-network                                                                     
       description: Ethernet interface                                          
       product: 82566MM Gigabit Network Connection                              
       vendor: Intel Corporation                                                
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1a:6b:38:aa:48
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.3-0 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:76:8f:7f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=128.230.45.220 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fe:b4:57:19:b8:54
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



A fresh install?  Of kubuntu?  And yes, this is the main university wireless; it's campuswide.

I was at the library last night, and I didn't get kicked off quite as much it seemed like.

---

### Post by Captain_tux on 2008-12-08
A fresh install is when you're **not** doing an upgrade of a previously installed version ... you're doing a brand *new* or *fresh* installation of the system.

Are you experiencing kernel panics or just getting kicked off/taking a long time to reconnect?

---

### Post by tegnoto89 on 2008-12-09
yes it was a fresh install.  no kernel panics just being kicked off a lot and having a hard time reconnecting.

---

### Post by hyper_ch on 2008-12-09
(1) when asked for posting output of a comamnd or file enclose it individually in [noparse]```

```[/noparse] brackets. That makes it easier to read.

(2) yuo might want to try an alternate network manager. I have never been happy with the default ones and use now WICD.

---

### Post by nixforme on 2008-12-09
> **tegnoto89 said:**
> okay the first thing:

tom@tom-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)                                                                  
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)                                                                   
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)                                                                      
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)                                                                  
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)                                                                  
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)                                                                 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)                                                                       
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)                                                                          
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
02:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

and the other:

 *-network                                                                     
       description: Ethernet interface                                          
       product: 82566MM Gigabit Network Connection                              
       vendor: Intel Corporation                                                
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1a:6b:38:aa:48
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.3-0 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:76:8f:7f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=128.230.45.220 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fe:b4:57:19:b8:54
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



A fresh install?  Of kubuntu?  And yes, this is the main university wireless; it's campuswide.

I was at the library last night, and I didn't get kicked off quite as much it seemed like.

Have you tried to connect to any other wireless networks to test the quality on the network. I mean by that is do you get kicked off the same amount as you did before?

Another thing to check for is to make sure the drivers is enabled in the Restricted Drivers Manager. I belive now it is called Hardware drivers.

---

### Post by tegnoto89 on 2008-12-09
The only other network I've connected to was the help network, and since it doesn't let me browse and really use the connect, I couldn't tell if I was going to be kicked off that one.

But I am being kicked off more than before (I used the same connection before, just through windows).

I checked my drivers and the only things that I can install were my NVDIA 3D accelerator graphics card drive (which I did).

What other network managers can you guys recommend?

---

