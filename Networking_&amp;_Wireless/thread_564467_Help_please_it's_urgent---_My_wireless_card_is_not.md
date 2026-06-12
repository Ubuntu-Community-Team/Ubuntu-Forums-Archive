---
title: "Help please it's urgent--- My wireless card is not working"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by Hernan Moreno on 2007-10-01
I'm really new with ubuntu, currently mi laptop is a SONY VAIO 	VGN-FE550FM, with ubuntu 7.04 
and no Windows. I was really happy with ubuntu, I made some performance tweaks based in 
[http://blog.lxpages.com/2007/04/24/ubuntu-performance-guides/](http://blog.lxpages.com/2007/04/24/ubuntu-performance-guides/)
[http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192)
and everything was fine and sweet the last pending thing a had was to update the kernel, so I did it, I update the kernel to 2.6.22-12 from 2.6.20-16

The result was I loose my sound card and wireless card functionalities, so I decided to switch back and use the kernel 2.6.20-16, but ... wait.. the wireless card didn't work again.

I was investigating and I cannot find the error, so please I really need your help.

 I give what I think could help you to figure out what's happening in my ubuntu:
root@artemisa:/boot#  iwlist scan

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



vmnet1    Interface doesn't support scanning.



vmnet8    Interface doesn't support scanning.


root@artemisa:/boot# iwconfig eth1

eth1      No such device

root@artemisa:/boot# lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)

**06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)**

0a:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller

0a:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller

0a:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (re

root@artemisa:/boot# ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:13:A9:0F:64:67  

          inet addr:190.0.65.128  Bcast:190.0.65.255  Mask:255.255.255.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:357316 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1600 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:22597630 (21.5 MiB)  TX bytes:285062 (278.3 KiB)



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:86 errors:0 dropped:0 overruns:0 frame:0

          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:23450 (22.9 KiB)  TX bytes:23450 (22.9 KiB)



vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  

          inet addr:172.16.103.1  Bcast:172.16.103.255  Mask:255.255.255.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  

          inet addr:192.168.30.1  Bcast:192.168.30.255  Mask:255.255.255.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1


    RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Hernan Moreno on 2007-10-01
root@artemisa:/boot$ lshw -C network | grep -e "product:" -e "vendor:" -e "configuration:" | sed -r "s|ip=[0-9.]* ||g"
Password:
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       configuration: driver=ipw3945 latency=0
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full **firmware=N/A **latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s

---

### Post by Hernan Moreno on 2007-10-01
hmoreno@artemisa:/boot$ sudo lshw -C network
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@06:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:cc000000-cc000fff irq:18
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0a:08.0
       logical name: eth0
       version: 02
       serial: 00:13:a9:0f:64:67
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=190.0.65.128 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:d0005000-d0005fff ioport:6000-603f irq:21

---

### Post by Hernan Moreno on 2007-10-01
Ok, I fixed the issue myself. Somehow I removed the restricted modules and after a quick installation now it works.  :)

---

