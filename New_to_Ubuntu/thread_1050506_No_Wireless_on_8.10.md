---
title: "No Wireless on 8.10"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by jfig345 on 2009-01-25
Hello everyone. I got Ubuntu 8.10 yesterday.

I have been trying to get my wireless set up but have not been having any luck.
I did read the wireless on the  "how to" but didnt have any luck there either.

I have put in my network information however if I mouse over the network icon on the taskbar it tells me that the device is not enabled.

The only command that I have put in the terminal is

```
sudo ifconfig eth1 down
```
which I read on a howto

Is this causing the problem.

I am typing from my laptop which is on the same wireless network so I know the network is up and running.  Any help would be appreciated.

8.10 is on my desktop

---

### Post by Crandom on 2009-01-25
Which wireless card do you have? Have you installed any drivers for it? What is the model of the laptop?

Try going to System > Administation > Hardware Drivers and if your wireless driver is there, check the checkbox and restart your pc. If not, reply to the questions.

---

### Post by jfig345 on 2009-01-25
here is the output of 

```
lspci
lshw -class network
```

I had to copy a txt file from ubuntu onto a flash disk but here it is
```

[\john@john-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0e.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
john@john-desktop:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0c:6e:2f:70:83
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:e5:20:35:59
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: aa:13:d5:5c:33:5c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

Hope this helps

---

### Post by jfig345 on 2009-01-25
Its a wireless G
If I go to hardware drivers it says
broadcomm b43 wireless driver is enabled.

---

### Post by jfig345 on 2009-01-25
if I type
```

sudo iwlist scan
```

I can see my network but it still says my device is not managed.

---

