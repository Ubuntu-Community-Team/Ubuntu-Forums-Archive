---
title: "How can I force Xubuntu to use the correct wireless driver?"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by nickaj on 2007-06-15
I have a CB54G from MSI in a PCI slot, which should use the rt2500 driver, but for some reason Xubuntu identifies it as a BCM4306, and is thus using the wrong driver.  How can I force the system to use the rt2500 driver (already installed) with the device?

---

### Post by chili555 on 2007-06-15
Every, every, everything I can Google up says its a Broadcom. What tells you it's otherwise? lspci? sudo lshw -C network?

---

### Post by nickaj on 2007-06-15
the driver package from the msi site had rt2500, but lspci did say it was a Broadcom, thats why i thought the system wasn't recognizing it correctly.

1 site i quickly googled suggests it does use rt2500:
[http://www.netstumbler.org/archive/index.php/t-17548.html](http://www.netstumbler.org/archive/index.php/t-17548.html)

---

### Post by phonixor on 2007-06-16
dont know how to do it permentatly... havint trouble with that myself
(rt2570 instead of the one i want rt2500)

but you can unload that sorry little direver by typing this in the console
-----------
sudo rmmod rt2570
----------

if an other module is waiting i think it picks it up automaticly... though still having some problems with that part...

---

### Post by chili555 on 2007-06-16
The site you Googled up seems to refer to the CB54G**2**. Your original post refers to the CB54G.

It is quite unlikely that lspci will report a completely different chipset than what actually exists. I could see a Realtek being reported as a RT2500 when it's really a RT2570...maybe. But a Realtek being reported as a Broadcom? Very, very doubtful. I've never seen it in 7 years of Linux experience.

What does:```
sudo lshw -C network
```tell us?

This is from Ndiswrapper's site:> #Card: MSI CB54G PcCard Adapter, 802.11g

    *      Chipset: Broadcom BCM4306 (?) manfid: 02d0:0406 Windows
    *      Driver: [http://www.msi.com.tw/](http://www.msi.com.tw/) (look for ms68bm.inf and ms68bm.sys) Divers:: jec/04-apr-2005 : FedoraCore3, 4k stacks, driver loads OK. Tests::Connecting to AP is fine. Getting DHCP address also. Changinf this site with my WiFi access! Nice.[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/)

---

### Post by nickaj on 2007-06-16
thx guys, lshw -C network also inidicates a broadcom:

>   *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 41
       serial: 00:00:39:b4:93:ce
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.2.102 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:ff9ff000-ff9fffff ioport:df40-df7f irq:11
  *-network
       description: 802.11b CardBus 
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 0
       resources: irq:11
  *-network DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@03:00.0
       logical name: eth1
       version: 03
       serial: 00:0c:76:c8:61:39
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic ip=207.112.66.9 latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:2c000000-2c001fff irq:11


so my problem might just actually be that it is "disabled".  the wireless network is activated  in the network program, is there another command to enable it?

---

### Post by chili555 on 2007-06-17
I wonder if it's calling itself disabled because the card hasn't picked up the firmware, which isn't installed by default because it's proprietary, i.e. not open source. Please check here: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by nickaj on 2007-06-17
Thanks a lot Chili, my wireless is now up and running.  Help from people like you is so far the best thing about Linux.

---

### Post by chili555 on 2007-06-18
Glad it's working. Thank you very much for your kind comments!

---

