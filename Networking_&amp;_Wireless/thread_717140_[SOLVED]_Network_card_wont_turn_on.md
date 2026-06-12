---
title: "[SOLVED] Network card wont turn on"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by devils3cups on 2008-03-06
I'm not sure what happened to my card. I changed my wireless driver and it didnt seem to work but it started to use a backup driver?? I'm not sure thats correct. Now today the wireless wont even turn on. I looked under networks and my card wasn't even there. i did a lshw and it found the card but the light is not on saying its scanning for a network. I'm not sure if my card died or its not using the correct driver. Any help?

Thanks,
Kraig

---

### Post by devils3cups on 2008-03-06
Maybe this can help. I dont see any driver listed.

```

kraig@kraig-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:d5:40:12
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.11.3 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

```

---

### Post by chili555 on 2008-03-06
I see your wired ethernet is connected and has an IP address. Network Manager is designed to shut down wireless when ethernet can and does connect. See: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) , especially this:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk.I suggest unplugging the wire and see if wireless springs to life. A reboot may be advisable here.

---

### Post by devils3cups on 2008-03-06
Same thing
```
  *-network UNCLAIMED     
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:d5:40:12
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s

```

---

### Post by devils3cups on 2008-03-07
Anyone? Really need help here

---

### Post by lswest on 2008-03-07
the output of lshw -C network won't change except for an IP address or not, could you post the output of: ```
lspci
ndiswrapper -l
iwconfig
ifconfig
```

(if command #2 (second line) says the program is no installed, skip that command and post back telling us the program is not there)

also, i believe i have the same card as you, and i configured it using ndiswrapper, my output from lshw -C network looks like this:
```
*-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:7c:f4:1c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. ip=192.168.2.34 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

``` looks like we need to either install a driver using ndiswrapper or you can try bcm43xx-fwcutter

---

### Post by devils3cups on 2008-03-07
I cant respond much because I'm running to catch a train.
Heres my output

lspci
```

kraig@kraig-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
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
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
05:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

ndiswrapper -l
```

kraig@kraig-laptop:~$ ndiswrapper -l
bcm43xx-fwcutter : invalid driver!

```

iwconfig
```

kraig@kraig-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

ifconfig
```

kraig@kraig-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:D5:40:12  
          inet addr:192.168.11.3  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fed5:4012/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:997 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:982183 (959.1 KB)  TX bytes:199351 (194.6 KB)
          Interrupt:21 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by lswest on 2008-03-07
okay, well, the problem is this: your card isn't recognized.  Do you remember how you set it up?  if you set it up using the bcm43xx-fwcutter method (which it looks like) try [this guide]("http://ubuntuforums.org/showthread.php?t=542264"). and repeat the process.

---

### Post by devils3cups on 2008-03-07
Unfortunately I recently tried to change my driver so fwcutter was not my original driver. I would like to use it though would following this guide help?

I ran through the guide and it still isnt helping. I have a suspicion my card died. The card light doesn't even turn on anymore and when I go under networks the wireless card isn't even listed.

---

### Post by lswest on 2008-03-08
no, if there is no driver for the card, the light won't turn on (sometimes even with a driver it doesn't work) and the card won't be listed.  Attached are the drivers i use to get my broadcom card working.  First off extract the drivers from the archive to a folder of your choice, then do this:
```
sudo aptitude remove bcm43xx-fwcutter
```
then:
```

cd [path to driver files]
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper
gksudo gedit /etc/modules and add "ndiswrapper" (without the quotes) to the end of the file
sudo reboot
```

after this it should work, if not, try this:
```
gksudo gedit /etc/modprobe.d/blacklist
``` and add "blacklist bcm43xx-fwcutter" (without the quotes) then reboot again

---

### Post by devils3cups on 2008-03-10
That was it THANKS!

---

### Post by lswest on 2008-03-11
no problem, glad we got it sorted ^^

---

