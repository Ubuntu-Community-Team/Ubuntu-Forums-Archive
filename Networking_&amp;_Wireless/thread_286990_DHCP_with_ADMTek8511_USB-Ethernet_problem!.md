---
title: "DHCP with ADMTek8511 USB-Ethernet problem!"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by pir4 on 2006-10-28
Im using Ubuntu 6.10.
I just installed it, and cant get the internet working...
Im using a ADMTek 8511 USB-ethernet.
Everything looks fine, i get the module loaded in dmesg and i even see the card in ifconfig -a. But im trying to use dhcp and it doesnt find any ip or gateway.
I tried to use the same ip / dns / gateway that i get in Windows but no results.

btw: i reed a lot in this forum about the device and didnt help/.


Any help ? thX ppl.

-------------------------------
Laptop HP Pavilion zv5000 (AMD 64 3400+)

**dmesg:**
[   45.877066] pegasus 2-1:1.0: eth0, ADMtek ADM8511 "Pegasus II" USB Ethernet, 00:08:54:d6:ad:de
[   45.877088] usbcore: registered new driver pegasus

**lsmod:**
usbcore               167840  7 rtl8150,spca5xx,pegasus,usbhid,ohci_hcd,ehci_hcd
pegasus                34456  0

**ifconfig -a**
eth0= Network Card /eth1= ADMTek USB-Lan / eth2= Wireless

eth0      Link encap:Ethernet  HWaddr 00:0F:B0:0D:DC:81  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0x8800 

eth1      Link encap:Ethernet  HWaddr 00:08:54:D6:AD:DE  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth2      Link encap:Ethernet  HWaddr 00:90:4B:93:99:B4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9636 (9.4 KiB)  TX bytes:9636 (9.4 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

**pir4@mAry:~$ sudo dhclient eth1**
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:08:54:d6:ad:de
Sending on   LPF/eth1/00:08:54:d6:ad:de
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9

---

### Post by pir4 on 2006-10-28
PROBLEM FIXED:

After trying everything, i figured out that loading the module with mii_mode=1 fix the problem. So:

rmmod pegasus
lsmod pegasus mii_mode=1

:p 
bye!

---

### Post by cmulder on 2007-03-26
I also looked everywhere for this fix and it worked perfectly for me as well, THANKS! :-D  Mine sounds the same... a generic USB2-Ethernet with ADM851x driver in Windows.

I'm loving the forums :D

---

### Post by RobertJohnson on 2007-11-29
hi, I had exactly the same problem... I've got Ubuntu 7.10, and I completly new to this thing, and linux also. rmmod worked ok, but when I typed this lsmod blah blah, it just said usage: lsmod. and after ifconfig there was no eth1 at all... :confused: why?!

---

