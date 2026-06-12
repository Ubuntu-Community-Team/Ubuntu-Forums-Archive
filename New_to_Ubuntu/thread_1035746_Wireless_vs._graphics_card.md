---
title: "Wireless vs. graphics card"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by beatrice on 2009-01-10
Hey. 
Sorry for my poor English, I really hope I'm explaining myself. :P

So, here's the thing:
I'm having some annoying problems with my graphics card (ATI/AMD proprietary FGLRX graphics driver – that's what my Hardware Drivers say).
It took me about an hour to establish the wireless connection. The I enabled the graphics card (to get the cool visual effects provided by our beloved Linux :P ), but, unfortunately, when I restarted the computer, the wireless was gone! Only *wired network* option remained. Then I disabled graphics card and reboot, and voila!, wireless came back to life again. 

Any ideas? Of course I can live without the gorgeous desktop cube (I pick wireless over good looks), but I'd rather not. :D

---

### Post by Michael.Godawski on 2009-01-10
hi, 

what is your wlan card? 
Can you please post the outputs of these terminal commands:

```
sudo lshw -C network
sudo lshw -C display
iwconfig
```

---

### Post by beatrice on 2009-01-10
**NETWORK **

 *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:22:15:2b:b8:67
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full ip=192.168.1.105 latency=0 link=yes module=sis190 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 00:22:43:09:57:b5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.109 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 92:c8:e8:20:db:35
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

**DISPLAY**

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Mobility Radeon HD 3400 Series
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0

**IWCONFIG**

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"gkacar"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:6B:56:74:70   
          Bit Rate:18 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=28/70  Signal level=-67 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.



You seriously see something out of all this?? :P

---

### Post by Michael.Godawski on 2009-01-10
I see your wlan is working and you graphic card has no drivers. :P

The newer HD series is supported by linux but sometimes there has to be some work done:
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

3d acceleration is activated for more and more ati cards of this type.

You can either have fun with the instructions above...
or try the experimental .deb package from here to install the drivers for you card.
[IMG]http://ppa.launchpad.net/icons/unknown.gif[/IMG][xserver-xorg-video-radeonhd-dbg_1.2.4+git20081220.003325a5-0ubuntu0tormod_i386.deb]("http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-radeonhd/xserver-xorg-video-radeonhd-dbg_1.2.4+git20081220.003325a5-0ubuntu0tormod_i386.deb")

It is up to you. :)

---

### Post by beatrice on 2009-01-10
Ammm, I think I messed something. I put the outputs when my card was disabled and my wireless working. Sorry. Now I enabled the card again.... :oops:

**DISPLAY:**
*-display               
       description: VGA compatible controller
       product: Mobility Radeon HD 3400 Series
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx

**NETWORK **
*-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:22:15:2b:b8:67
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full ip=192.168.1.105 latency=0 link=yes module=sis190 multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3e:a9:c3:ac:ae:29
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


**IWCONFIG**
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


That's the current situation with the enabled graphics card.

---

