---
title: "Odd Linksys WUSB100 connection problem"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by MarshallNS on 2008-07-10
Yesterday I installed a Linksys usb wireless card,  after some doing I ndiswrapper'd the driver file (rt2870.inf) that came on the installation cd, which allowed me to connect to my wireless network.  After installing the card on my separate windows drive however,  It is failing to find any networks on the network manager.  I'm running Gutsy 7.10.

Here is some info I gleened off the terminal.
ndiswrapper -l
> rt2870 : driver installed
       device (1737:0070) present

ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:16:76:CE:C6:B2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
lsusb
> Bus 003 Device 004: ID 0930:653d Toshiba Corp. 
Bus 003 Device 002: ID 1737:0070  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

Thank you for your help! :)

---

### Post by MarshallNS on 2008-07-10
Managed to figure it out myself,  i needed to run
sudo depmod -a
sudo modprobe ndiswrapper

what exactly was it that these commands did?

---

