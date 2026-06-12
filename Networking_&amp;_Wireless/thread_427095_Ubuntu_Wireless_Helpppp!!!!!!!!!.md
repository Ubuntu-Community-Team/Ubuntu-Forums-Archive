---
title: "Ubuntu Wireless Helpppp!!!!!!!!!"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by djuldjul on 2007-04-29
Hallow there

I'm 100% new to Ubuntu. I have just installed it for the first time on my Dell D600.
I need a guide how to connect my laptop to the internet via my wireless network.
The guide have to be very easy as I don't have a programing backround.

I'm looking forwared to hear from someone soon!

/DJULDJUL

---

### Post by solar george on 2007-04-29
Open a terminal, you will see a prompt similar to,
```
george@george-laptop:~$ 
```

Type
```
george@george-laptop:~$  lspci
```

You will get an output like,
```
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:00.0 CardBus bridge: Texas Instruments PCI1420
02:00.1 CardBus bridge: Texas Instruments PCI1420
02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
07:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
george@george-laptop:~$ 

```

When you get that post it here. (you can use copy and paste from the terminal)

---

### Post by djuldjul on 2007-04-29
This is what I got:


0000:00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller ( rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EH CI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridg e (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller ( rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH 4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97  Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [Fir eGL 9000] (rev 01)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabi t Ethernet (rev 02)
0000:02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (re v 20)
0000:02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (re v 20)
0000:02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini  PCI Adapter (rev 04)

---

### Post by solar george on 2007-04-29
Open a terminal and type 
```
iwconfig
```

Then post the output.

---

### Post by djuldjul on 2007-04-29
Now I got:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"BeCarFull"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:off
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by solar george on 2007-04-29
You should be able to configure wireless networking through the standard network-admin program
System>Administration>Network

There you need to click on wireless connection and click properties.

Uncheck the 'roaming mode' box and choose your essid (network name) from the drop down list, enter any password info and click OK.

You may need to click the check box next to wireless network to enable it.

---

### Post by djuldjul on 2007-04-29
What I did is, I clicked on Sysytem>Administration>Networking (I don't have Network!). From the "Connection Tab" I choose "Wireless Connection" then "Properties". Under "Wireless settings" I choose my wireless network the under  "Key type" I choose HEX, Then I entered the WEP key. I don't have  'roaming mode' and the connection is enabled. It is still not working. Maby something wron with the driver?

---

### Post by solar george on 2007-04-29
Open a terminal and type
```
sudo ifdown eth1
sudo ifup eth1
```

---

### Post by djuldjul on 2007-04-30
Still not worrking. Evenlly when Ientered manually the IP address:

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:04:23:48:fc:0f
Sending on   LPF/eth1/00:04:23:48:fc:0f
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by jubilee33 on 2007-04-30
I have the same wireless network card as you do.  It actually worked "out of the box" - although during the CD installation of ubuntu I got the error that my wireless connection wasn't configured right.  So I might be able to help.

Please give me the following two outputs.  In the terminal, type as follows:

```
gedit /etc/network/interfaces
```

```
cat /etc/resolv.conf
```

---

### Post by djuldjul on 2007-04-30
This is wat I got from the first code:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid BeCarFull
wireless-key 30303937323937393239313733

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

The second did not gave me anything.

I aso want it to tell you, that i'm really appreciate your help :-)

---

### Post by solar george on 2007-04-30
> wireless-key 30303937323937393239313733

You do realise that you just posted your WEP key to the world. (unless of course you changed it)

---

### Post by djuldjul on 2007-04-30
It's fine, I know ;-)

---

### Post by jputman01 on 2007-04-30
so if you go to system->admin->network and click on wireless are you able to see wireless networks when you click the arrow to select a network? if so you may try commenting out all interfaces in /etc/network/interfaces except for "lo"  this is what I had to do to get it to work. also if you click on the network manager icon in the taskbar you do have the option for "enable wireless" checked right?

---

### Post by djuldjul on 2007-04-30
when I click on the network manager icon in the taskbar I don't have the option to enabled the wireless. But is says that it is Disconnected (When I write eth1 under the 'Name') and I don't know what to do to connect.

---

### Post by jputman01 on 2007-04-30
> **djuldjul said:**
> when I click on the network manager icon in the taskbar I don't have the option to enabled the wireless. But is says that it is Disconnected (When I write eth1 under the 'Name') and I don't know what to do to connect.


in system->admin->network you do have the option for "wireless" checked right? also is the light for you wireless card on?

---

### Post by djuldjul on 2007-04-30
I don't have such light. But this how the Network Setting looks like: look at the Attach File.

---

### Post by djuldjul on 2007-05-01
So what do you think?

---

