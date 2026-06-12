---
title: "Another ndiswrapper question"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by kevinfitch83 on 2007-10-08
I have a Dell Inspiron 1150 with a Dell Wireless 1350 Mini PCI card. I just got it up and working with ndiswrapper using this guide [HTML]https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)[/HTML]
but now my wired connection stopped working. Any ideas.

Thanks for your help; as you can tell I'm pretty new to Ubuntu and Linux in general. I'd like to continue to learn as much as possible and crawl out from under Bill Gates thumb.

---

### Post by spd106 on 2007-10-08
Try opening System -> Admin -> Network and see if your wired card shows up. 

If it does make sure it enabled and that both wired and wireless interfaces are set to roaming mode. Now your wired card should work when you plug it in.

If not can you please open a terminal and post the output of these commands.
```
lspci
```
```
sudo lshw -class network
```

---

### Post by kevinfitch83 on 2007-10-09
Unfortunately that didn't work. I should probably tell you more about my connection. I need to use a static IP to connect however when I type it in the network monitor doesn't seem to read my connection.

Here's that code:

```
kevin@Kevin:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) 
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) 
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01) 
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) 
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01) 
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) 
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller 

```

```
kevin@Kevin:~$ sudo lshw -class network 
Password: 
  *-network:0              
       description: Ethernet interface 
       product: BCM4401 100Base-T 
       vendor: Broadcom Corporation 
       physical id: 1 
       bus info: pci@02:01.0 
       logical name: eth0 
       version: 01 
       serial: 00:0f:1f:2a:44:a7 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=207.24.153.193 latency=32 link=yes multicast=yes port=twisted pair speed=100MB/s 
       resources: iomemory:fcffe000-fcffffff irq:7 
  *-network:1 
       description: Wireless interface 
       product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 2 
       bus info: pci@02:02.0 
       logical name: wlan0 
       version: 03 
       serial: 00:0b:7d:09:ff:de 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master ethernet physical wireless 
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Broadcom,11/02/2005, 4.10.40.0 latency=32 link=no multicast=yes wireless=IEEE 802.11g 
       resources: iomemory:fcffc000-fcffdfff irq:11 

```

Thanks for the help.

---

### Post by kevdog on 2007-10-09
Can you post the following:

lsmod | grep ndiswrapper
iwlist scan

Seems right now everything from what you posted is correct!!

---

### Post by kevinfitch83 on 2007-10-09
```
kevin@Kevin:~$ lsmod | grep ndiswrapper 
ndiswrapper           194608  0  
usbcore               134280  4 ndiswrapper,ehci_hcd,uhci_hcd 

```


```
kevin@Kevin:~$ iwlist scan 
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wlan0     Scan completed : 
          Cell 01 - Address: 00:0C:41:FA:46:8B 
                    ESSID:"CCR WAP" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
```

---

### Post by kevinfitch83 on 2007-10-09
I would think that there is some problem with the connecting Linux on the this network if it wasn't for the fact that my connection worked fine until I got the wireless card working. After the wired connection failed I just reinstalled Ubuntu and started over but I still couldn't get the wired connection working again.

---

### Post by kevdog on 2007-10-09
So what doesnt work

Your wired or wireless connection??

You should probably take the space out of your essid name.

---

### Post by spd106 on 2007-10-09
It looks like both interfaces are working fine, so it seems that this is more likely to be a routing issue. Are you using both interfaces at the same time? If so you will have to be careful about setting the default route/gateway properly. Which ever interface is in roaming mode will overwrite the gateway information.

Try running this command to see the current routing table.
```
ip route
```

If you have more than one default entry you'll have to remove one or disable one of the interfaces.

---

### Post by kevinfitch83 on 2007-10-11
So do you mean that if my wireless card is set on roaming mode it might override my wired card?

By the way here's the return on the ip route:

```
kevin@Kevin:~$ ip route
192.168.111.0/24 dev wlan0  proto kernel  scope link  src 192.168.111.5 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
default via 192.168.111.1 dev wlan0 
```

---

