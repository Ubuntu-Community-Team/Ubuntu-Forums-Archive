---
title: "slow connection"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by egwest on 2008-05-02
My wifi card is working, but I am noticing that it has a much slower transfer rate in 8.04 then I had in 7.10.

I followed the info from an earlier post and got my data rate to 54 Mb/s but it is still really sluggish on loading pages and on downloads. 

I really noticed it on a download when I installed a large file from the package manager, it took almost 40 minutes to download it, it only took 10 minutes on my notebook. Both are accessing the same wifi router.

Here are the specifics of my card if anyone has any ideas how to boost the transfer signal.

01:05.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: Linksys WMP54G 2.0 PCI Adapter
        Flags: bus master, slow devsel, latency 32, IRQ 20
        Memory at ed002000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2
        

If anyone has an idea, please let me know.

---

### Post by Paris Heng on 2008-05-03
> **egwest said:**
> My wifi card is working, but I am noticing that it has a much slower transfer rate in 8.04 then I had in 7.10.

I followed the info from an earlier post and got my data rate to 54 Mb/s but it is still really sluggish on loading pages and on downloads. 

I really noticed it on a download when I installed a large file from the package manager, it took almost 40 minutes to download it, it only took 10 minutes on my notebook. Both are accessing the same wifi router.

Here are the specifics of my card if anyone has any ideas how to boost the transfer signal.

01:05.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: Linksys WMP54G 2.0 PCI Adapter
        Flags: bus master, slow devsel, latency 32, IRQ 20
        Memory at ed002000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2
        

If anyone has an idea, please let me know.

Most of the time is the network card problems, just change a new card.

---

### Post by egwest on 2008-05-03
> **Paris Heng said:**
> Most of the time is the network card problems, just change a new card.


I have to buy a new card again? Darn! I just bought that card 2 months ago! And it was working so good in 7.10.

---

### Post by norwegianblue on 2008-05-03
No! Don't buy a new card.

See this sticky...

[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

---

### Post by egwest on 2008-05-04
> **norwegianblue said:**
> No! Don't buy a new card.

See this sticky...

[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

Thanks, it did not work, locked out my wifi card and it took me awhile to figure out how to undo it. I must have messed up somewhere.

I'll stick with the slow connection for awhile, perhaps a fix will come along, or I get a new card that is fully supported.

---

### Post by gmrishel on 2008-05-07
egwest, i guess we are in the same boat here.  i am fairly new to linux, and i found something that confuses me.  

according to the linksys site i have a wmp54g v1.0.  (no version number printed on the device after the model number)
according to the supported card wiki, it should use a Broadcom BCM4306 chip set.   
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

but in terminal i get this?

lspci -v | less

Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
Subsystem: Linksys WMP54G 2.0 PCI Adapter
Flags: bus master, slow devsel, latency 32, IRQ 21
Memory at cc004000 (32-bit, non-prefetchable) [size=8K]
Capabilities: <access denied>


lshw -C network

  *-network:1
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: wmaster0
       version: 01
       serial: 00:12:17:8a:e5:15
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.4.102 latency=32 module=rt2500pci multicast=yes wireless=IEEE 802.11g


so so who is wrong?  is the wiki wrong about what chipset or is their something wrong with how hardy determines the hardware.

also i am getting slow speeds, and according the wifi radar it show connection as wireless b.  my vostro 1500 is getting g?

i did everything from wieman01's guide for ndiswrapper, and it said something like "device present: no" so that didnt work..

another issue i have is that i have an asus ah2600pro video card that i would like to install in this desktop, but when i have the card in the box, the wireless device just disappears completely, but i guess thats maybe a different issue that i should post about in a different section.  those 2 rascals just don't seem to be getting along well.

---

### Post by kennedy7 on 2008-11-25
[http://download.opendrivers.com/showfile.php?file=TDI1bGRIZHZjbXN2Y21Gc2FXNXJMMVpCWDBsVFgxTlVRVjgyZUY5RUxUSXVNQzR6TGpCZk1qVXdNRjlFTFRNdU1pNHdMakJmVWxVdE1TNHdMalF1TUY4d01qRXpNRGRmTUM0d0xqQXVPR1l1ZW1sdz0=](http://download.opendrivers.com/showfile.php?file=TDI1bGRIZHZjbXN2Y21Gc2FXNXJMMVpCWDBsVFgxTlVRVjgyZUY5RUxUSXVNQzR6TGpCZk1qVXdNRjlFTFRNdU1pNHdMakJmVWxVdE1TNHdMalF1TUY4d01qRXpNRGRmTUM0d0xqQXVPR1l1ZW1sdz0=)
If that doesnt work here is a list of drivers to choose from

[http://www.opendrivers.com/categorycompany/1113/1159/network-ralink-free-driver-download.html](http://www.opendrivers.com/categorycompany/1113/1159/network-ralink-free-driver-download.html)

There is a list of drivers that you can choose from.

Install the driver with ndiswrapper. If you need help with ndiswrapper just reply and ill give more detailed help.

---

