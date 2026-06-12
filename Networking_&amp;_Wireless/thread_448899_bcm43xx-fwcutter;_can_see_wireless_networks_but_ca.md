---
title: "bcm43xx-fwcutter; can see wireless networks but can't connect"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by PJV on 2007-05-19
Hi, all

I'm new to Ubuntu and downloaded and installed Ubuntu 7.04 desktop to my Dell Inspiron 8200. I got the updates and upgrades using apt-get. Now I'm trying to set up my wireless card, a Linksys WPC54GS ver.2 notebook adapter. I did my research and was able to get and install the bcm43xx-fwcutter. NetworkManager detects my wireless network (and others) but I can't connect to it after I give my pass-phrase information. I tried all sorts of combination for the WEP, including the WEP64 hex. I can connect wirelessly on my other Windows laptop but can't on this one. The network icon just goes on a loop when I connect and I come back to the password box. 

**iwconfig:**

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"arminta"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.484 GHz  Access Point: 00:11:F5:30:79:E8   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**lspci:**

00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 01)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
07:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

**lshw:**

<previous lines omitted>
     *-network
          description: Wireless interface
          product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
          vendor: Broadcom Corporation
          physical id: 0
          bus info: pci@07:00.0
          logical name: eth1
          version: 02
          serial: 00:14:bf:ca:a5:9c
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master ethernet physical wireless
          configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 multicast=yes wireless=IEEE 802.11b/g
          resources: iomemory:7c000000-7c001fff irq:11


Let me know what other info you guys need. Appreciate the help.

Thanks,

---

### Post by Guranic on 2007-05-19
I have same wireless chip and I got it working with fwcutter. Sometimes it just won't connect when I boot and the easiest way to get around it is to reboot, normally it works. Other thing is that connecting my laptop to my router causes router crashes sometimes, not often though. The last thing in this play is keyring. Gnome keyring saves keys for encrypted wireless networks and I had problems with it. I did this [http://ubuntuforums.org/showthread.php?t=192281&highlight=pam+network+manager&page=8](http://ubuntuforums.org/showthread.php?t=192281&highlight=pam+network+manager&page=8) and got rid of keyring password dialog. After this problems with connecting significantly reduced. There was also a mention in forums that you should comment out everything else but lo interface from /etc/network/interfaces.

 I think you should make sure that keyring has right key saved or just reset your router's encryption off and try if network manager connects then.

Hope you get it working. It should work ok with fwcutter and network manager...

---

