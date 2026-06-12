---
title: "WLAN only works after every second Ubuntu-reboot"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by Stevi on 2006-11-02
Hello,

I have a big problem which I already posted at the [german ubuntu forum]("http://forum.ubuntuusers.de/topic/55756/"). Hopefully anybody can help me!?
My WLAN only works every second time I boot Edgy.

Some Info:
I use NdisWrapper with a Windows-Driver (Gemtek WL850FJx (Conexant)). I blacklist "islsm_pci" in etc/modprobe.d/blacklist. I write Ndiswrapper into modules. After sudo ndiswrapper -i PRISMA00.inf and reboot the card works (declared as eth1 - with dapper it worked also fine as eth1). But after the next reboot it doesn't work. When I again reboot it works and so on...
Some Terminal-Output:
[B]
WLAN works:[/B] 
sudo lshw 
```
(...)*-network:1
             description: Wireless interface
             **product: ISL3886 [Prism Javelin/Prism Xbow]**
             vendor: Intersil Corporation
             physical id: b
             bus info: pci@00:0b.0
             logical name: eth1
             version: 01
             serial: 00:90:4b:d6:9e:b4
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ndiswrapper driverversion=1.22(...)

```
**WLAN doesn't work:**
```
(...)*-network:1 UNCLAIMED
             description: Network controller
             product: ISL3886 [Prism Javelin/Prism Xbow]
             vendor: Intersil Corporation
             physical id: b
             bus info: pci@00:0b.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:dfff8000-dfff9fff irq:209(...) 
```
```
stevi@eiram:~$ sudo ndiswrapper -l
Installed drivers:
prisma00                driver installed, hardware present

stevi@eiram:~$ sudo modprobe ndiswrapper
stevi@eiram:~$ sudo ifup eth1
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
**There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416**
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
stevi@eiram:~$
```

---

### Post by ivannavi on 2006-11-19
Hello.


I had the same problem and I could solve doing this:


I suppose that you removed islsm devices but I had to remove another devices, so you had to do:

sudo modprobe -r islsm_usb islsm_pci islsm_device islsm prism54 prism2 prism2_usb prism2_pci prism2_plx

(if you have remove islsm before, then you have only had to remove the last)

Add these devices to modprobe blacklist
Open the file:
sudo gedit /etc/modprobe.d/blacklist
Add:
blacklist islsm_usb
blacklist islsm_pci
blacklist islsm_device
blacklist islsm
blacklist prism54
blacklist prism2
blacklist prism2_usb
blacklist prism2_pci
blacklist prism2_plx

And now install ndiswrapper driver and config network device.

I can work with this card ever without any problem.

Sorry for my english.....i can promise that my spanish is better!!!!

---

### Post by FrodoB on 2006-11-19
If ivannavi's suggestion does not cure this please provide the output of iwconfig when it does work. 

It would also help to see the two ndiswrapper startup section from dmesg when it works and does not work.

---

