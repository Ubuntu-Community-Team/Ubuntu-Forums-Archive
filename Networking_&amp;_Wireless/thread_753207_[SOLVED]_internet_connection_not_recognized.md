---
title: "[SOLVED] internet connection not recognized"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by shalemjale on 2008-04-12
I installed ubuntu on my computer but the connection is not being recognized....
see info below:
desktop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 03) 
00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801AB PCI Bridge (rev 02) 
00:1f.0 ISA bridge: Intel Corporation 82801AB ISA Bridge (LPC) (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801AB IDE Controller (rev 02) 
00:1f.2 USB Controller: Intel Corporation 82801AB USB Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801AB SMBus Controller (rev 02) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801AB AC'97 Audio Controller (rev 02) 
01:0d.0 USB Controller: Silicon Image, Inc. USB0673 (rev 06) 
01:0e.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86) 
desktop:~$ sudo ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:528 (528.0 b)  TX bytes:528 (528.0 b) 

Any help would be greatly appreciated.

---

### Post by nixscripter on 2008-04-12
I can see the ethernet controller is being detected by the lspci output, so that's the first thing I would rule out: hardware failure.

What are you connected to on the other end? Is it running DHCP?

Also, please **ifconfig -a** to list all of the interfaces, as well as those that have an address. And as a suggestion, use CODE forum tags to avoid formatting the output.

---

### Post by chili555 on 2008-04-12
Before you do *ifconfig -a* would you please do:```
sudo modprobe via-rhine
```Does your interface appear? If so, please do:```
sudo dhclient eth0
```Did you connect?

---

### Post by shalemjale on 2008-04-13
This is what happened... keep in mind that I know nothing about this..

~$ sudo modprobe via-rhine 
~$ dhclient eth0 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

can't create /var/lib/dhcp3/dhclient.leases: Permission denied 
Can't create /var/run/dhclient.pid: Permission denied 
drop_privileges: could not set group id: Operation not permitted

---

### Post by chili555 on 2008-04-13
sudo, my man, sudo! I'm sure that's not exactly what is means, but I call it "super user, do..." this command. The super user or root, has permission to do anything, including wreck your system. Please preface the command with sudo:```
sudo dhclient eth0
```If you have turned off your machine since you tried this, you will have to:```
sudo modprobe via-rhine 
```If it works, we will make it permanent.

---

### Post by shalemjale on 2008-04-13
ooops, here is the info>>

desktop:~$ sudo dhclient eth0 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

SIOCSIFFLAGS: Device or resource busy 
SIOCSIFFLAGS: Device or resource busy 
Listening on LPF/eth0/00:19:5b:30:09:2b 
Sending on   LPF/eth0/00:19:5b:30:09:2b 
Sending on   Socket/fallback 
receive_packet failed on eth0: Network is down 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6 
send_packet: Network is down 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 
send_packet: Network is down 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15 
send_packet: Network is down 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping.

---

### Post by chili555 on 2008-04-13
After you have done:```
sudo modprobe via-rhine
```Please let us see:```
ifconfig
sudo lshw -C network
```Thanks

---

### Post by shalemjale on 2008-04-13
:~$ ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

:~$ sudo lshw -C network 
  *-network DISABLED      
       description: Ethernet interface 
       product: VT6105 [Rhine-III] 
       vendor: VIA Technologies, Inc. 
       physical id: e 
       bus info: pci@0000:01:0e.0 
       logical name: eth0 
       version: 86 
       serial: 00:19:5b:30:09:2b 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s

---

### Post by chili555 on 2008-04-13
> *-network DISABLED Is this disabled in your BIOS?

This looks hopeful:> link=yes

---

### Post by shalemjale on 2008-04-13
I went into the bios and found that the OS was set for a windows app. After changing it to "other OS", the network worked. 
Thanks for your help!

---

