---
title: "wireless card detection"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by balan3 on 2009-12-22
Hi i installed Ubuntu 9.10 on my DELL inspiron1545  laptp and my wirelles card is not detected .I have pasted the output i get when i type iwconfig and ifconfig. can someone suggest something please

@ubuntu-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

balan@ubuntu-laptop:~$ iwconfig -a
-a        No such device

balan@ubuntu-laptop:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.





@ubuntu-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:64:48:df:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
ubuntu-laptop:~$ sudo lshw -C net
[sudo] password for balan: 
  *-network               
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f6cfc000-f6cfffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:48:df:68
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:30 memory:f6bfc000-f6bfffff ioport:ce00(size=256)

---

### Post by unmole on 2009-12-22
You need to install Broadcom's STA drivers for Wifi to work

---

### Post by balan3 on 2009-12-23
hi thanks i was wondering how do i do that i clicked system-administration-hardware drivers and i am getting a blank screen

---

### Post by plusnplus on 2009-12-23
Hi balan3,
Try connect your notebook to internet use network cable.
usually latest ubuntu version will detect the hardware that not install properly.

---

### Post by mapes12 on 2009-12-23
[http://lmgtfy.com/?q=ubuntu+BCM4322](http://lmgtfy.com/?q=ubuntu+BCM4322)

and have a look through the posts.

---

### Post by balan3 on 2009-12-23
Working now thanks

---

