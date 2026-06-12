---
title: "[SOLVED] 8.10 - Broadcom BCM4311 - inspiron 1501 - can't get wireless working."
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by cornsay on 2008-11-16
[edit: how embarrassing, after I posted this, I retried the drivers in hardware manger, and this time, they worked fine.  I would delete the thread if I could work out how.  Duh]

Hello lovely people, 

I can see from searching the forums that many people have had this problem, and I've tried some of the suggested solutions, but can't crack it.  So, sorry if this has in fact been solved in a thread I haven't found.

Problem: fresh, clean install of 8.10 on a Dell Inspiron 1501.  Ethernet works fine. Can't get wireless to work. Wireless card is a broadcom BCM4311.  I've tried using the drivers that pop up in Hardware Manager, disabling the BC43 one and just using wl (as suggested elsewhere).  I also tried a solution that involved installing the driver manually through a terminal, but no joy.  Any ideas?

Me: complete linux noob.  Don't overlook the possibility that I'm doing something really stupid, and if you do have a walkthrough solution, dumb it down to the extreme.

Thanks in advance.  What follows is the info requested by the sticky on how to compose posts like this...

1) Machine: Dell Inspiron 1501

2) Wireless brand etc:Broadcom BCM4311 802.11b/g WLAN (rev 01)

3) Interface (is this the right info?)
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1991 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1991 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66851 (66.8 KB)  TX bytes:66851 (66.8 KB)

4) "$ lsmod | grep "wlan_module_name" gave no output

5)  Kernel boot messages list is really long - what am I looking for?!

6) Network config:
 *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:9a:a7:50
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.69 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ce:1f:63:93:64:d0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

7) scan for networks:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

8) ubuntu version: 8.10

9) kernel/archtiecture: 2.6.27-7-generic i686

10) restarting the network: $ sudo /etc/init.d/networking restart outputted:
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.

---

