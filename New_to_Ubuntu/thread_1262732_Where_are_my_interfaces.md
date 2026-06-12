---
title: "Where are my interfaces"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by chet on 2009-09-10
Hi all

I have running Ubuntu 8.04 on an IBM x3500, I have my eth0 configured with a static IP address and I now want to add another IP address to my box however I only see eth0 , how to I enable the other two built in NIC's, I thought that they would just be sitting there when I did ifconfig.

Thanks all and I hope this question is so stupid I do not get any replies :)

eth0      Link encap:Ethernet  HWaddr 00:14:5e:17:39:70  
          inet addr:192.168.3.243  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::214:5eff:fe17:3970/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2602596 (2.4 MB)  TX bytes:2399706 (2.2 MB)
          Interrupt:18 Memory:c8000000-c8012100 
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8806 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8806 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4286133 (4.0 MB)  TX bytes:4286133 (4.0 MB)

---

### Post by ukripper on 2009-09-10
you can configure in /etc/network/interfaces file
eth1 or eth2 so on....

---

### Post by chet on 2009-09-10
Thanks for the reply, file now looks like below and I can ping the 240 address, however when I pull the cable on eth1 the ping to 240 is still responding, how can that be.

iface eth0 inet static
        address 192.168.3.243
        netmask 255.255.255.0
        network 192.168.3.0
        broadcast 192.168.3.255
        gateway 192.168.3.254
        # dns-* options are implemented by the resolvconf package, if installed
         
iface eth1 inet static
        address 192.168.3.240
        netmask 255.255.255.0
        broadcast 192.168.3.255
        network 192.168.3.0
        gateway 192.168.3.254
        # dns-* options are implemented by the resolvconf package, if installed

---

### Post by ukripper on 2009-09-10
I think when you ping 240 it is virtually getting bridged by eth0 interface therefore returning you ping response. Try pinging both of them unplugged and then plug eth1 and ping 243

---

### Post by halitech on 2009-09-10
does the system actually see the other NICs that are installed?

```
lspci
```

---

### Post by chet on 2009-09-10
Hi I removed both Ethernet cables and ping to both IP's stopped (as it should), I then put eth1 cable back in so I should be able to ping 240 which I can not, no pings from either IP's at this stage.

---

### Post by chet on 2009-09-10
> **halitech said:**
> does the system actually see the other NICs that are installed?

```
lspci
```

Hi halitech, below is the output

Thanks

00:00.0 Host bridge: Intel Corporation 5000X Chipset Memory Controller Hub (rev 12)
00:02.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x8 Port 2-3 (rev 12)
00:03.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 3 (rev 12)
00:04.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x8 Port 4-5 (rev 12)
00:05.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 5 (rev 12)
00:06.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 6 (rev 12)
00:07.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 7 (rev 12)
00:08.0 System peripheral: Intel Corporation 5000 Series Chipset DMA Engine (rev 12)
00:10.0 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 12)
00:10.1 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 12)
00:10.2 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 12)
00:11.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev 12)
00:13.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev 12)
00:15.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev 12)
00:16.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev 12)
00:1c.0 PCI bridge: Intel Corporation 631xESB/632xESB/3100 Chipset PCI Express Root Port 1 (rev 09)
00:1d.0 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #1 (rev 09)
00:1d.1 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #2 (rev 09)
00:1d.2 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #3 (rev 09)
00:1d.7 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset EHCI USB2 Controller (rev 09)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d9)
00:1f.0 ISA bridge: Intel Corporation 631xESB/632xESB/3100 Chipset LPC Interface Controller (rev 09)
00:1f.1 IDE interface: Intel Corporation 631xESB/632xESB IDE Controller (rev 09)
00:1f.3 SMBus: Intel Corporation 631xESB/632xESB/3100 Chipset SMBus Controller (rev 09)
01:01.0 VGA compatible controller: ATI Technologies Inc ES1000 (rev 02)
02:00.0 RAID bus controller: Adaptec AAC-RAID (Rocket) (rev 02)
03:00.0 PCI bridge: Broadcom EPB PCI-Express to PCI-X Bridge (rev c2)
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet (rev 11)
05:00.0 PCI bridge: Broadcom EPB PCI-Express to PCI-X Bridge (rev c2)
06:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet (rev 11)
10:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Upstream Port (rev 01)
10:00.3 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express to PCI-X Bridge (rev 01)
11:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E1 (rev 01)
11:01.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E2 (rev 01)

---

### Post by ukripper on 2009-09-10
> **chet said:**
> Hi I removed both Ethernet cables and ping to both IP's stopped (as it should), I then put eth1 cable back in so I should be able to ping 240 which I can not, no pings from either IP's at this stage.

can you ping 243 with only eth1 connected?

---

### Post by chet on 2009-09-10
No, I can not ping anything, are we talking local or remote

---

### Post by ukripper on 2009-09-10
> **chet said:**
> No, I can not ping anything, are we talking local or remote

I mean from different machine on you LAN.

---

### Post by chet on 2009-09-10
This is where I'm at now

With eth0 and eth1 connected I can ping both IP addresses

Remove eth0, Ping nothing.

replace eth0, Ping both again.

Remove eth1, Ping both.

If I look at the server's monitor it informs me that I have removed eth0 and eth1 so it recognises the ports.

Thanks

edit...yes from a different PC on the LAN

---

### Post by ukripper on 2009-09-10
> **chet said:**
> This is where I'm at now

With eth0 and eth1 connected I can ping both IP addresses

Remove eth0, Ping nothing.

replace eth0, Ping both again.

Remove eth1, Ping both.

If I look at the server's monitor it informs me that I have removed eth0 and eth1 so it recognises the ports.

Thanks

edit...yes from a different PC on the LAN

can you post output of the following:
```
ifconfig
```

---

### Post by chet on 2009-09-10
Here you go

eth0      Link encap:Ethernet  HWaddr 00:14:5e:17:39:70  
          inet addr:192.168.3.243  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::214:5eff:fe17:3970/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16055 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3042024 (2.9 MB)  TX bytes:3078034 (2.9 MB)
          Interrupt:18 Memory:c8000000-c8012100 
 
eth1      Link encap:Ethernet  HWaddr 00:14:5e:17:39:72  
          inet addr:192.168.3.240  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::214:5eff:fe17:3972/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:27645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6179831 (5.8 MB)  TX bytes:5362010 (5.1 MB)
          Interrupt:17 Memory:ce000000-ce012100 
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16330585 (15.5 MB)  TX bytes:16330585 (15.5 MB)

---

### Post by ukripper on 2009-09-10
obvious question may i ask what is the purpose for you to use two NICS on one machine e.g throughput, NAT ???

---

### Post by chet on 2009-09-10
Yep not problem...

I have a network monitoring system that I monitor Cisco kit with, I'm trying to create a second box as a fail over box.

So I have three IP address, two IP's that are different on each eth0 for management and then one IP that is the same for eth1, so if a box goes down I can enable eth1 on the slave and this will then become the monitoring box.

Hope it makes some kind of sense

---

### Post by ukripper on 2009-09-10
> **chet said:**
> Yep not problem...

I have a network monitoring system that I monitor Cisco kit with, I'm trying to create a second box as a fail over box.

So I have three IP address, two IP's that are different on each eth0 for management and then one IP that is the same for eth1, so if a box goes down I can enable eth1 on the slave and this will then become the monitoring box.

Hope it makes some kind of sense

In this day and age it is less than 1% chance that your NIC will fail. Personally, for this purpose it would be overkill to have something like that in place. However, you may wish to increase the throughput of your packets using two NICS, when implemented which could act as failover as well throughput booster while provide you better networking coupling.

---

### Post by chet on 2009-09-10
Understand what you are saying but its a requirement that I have been asked to achieve.

percentage wise is zero for me as I have never lost a nic, programs become buggy though; so they would like to have a quick fix at the network layer.

Cheers

---

### Post by ukripper on 2009-09-10
> **chet said:**
> Understand what you are saying but its a requirement that I have been asked to achieve.

percentage wise is zero for me as I have never lost a nic, programs become buggy though; so they would like to have a quick fix at the network layer.

Cheers

Why not rather consider  clustering for high availability?

Here is good guide - [https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide](https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide)

---

### Post by Borusa on 2009-09-10
Sorry, possibly a stupid question, but could you post all of your /etc/network/interfaces file?

In particular, do you have eth1 in the auto line?

---

### Post by chet on 2009-09-10
> **Borusa said:**
> Sorry, possibly a stupid question, but could you post all of your /etc/network/interfaces file?

In particular, do you have eth1 in the auto line?


Cheers UKripper, will take a look

Borusa, that is my whole file

Cheers

---

### Post by chet on 2009-09-10
> **Borusa said:**
> Sorry, possibly a stupid question, but could you post all of your /etc/network/interfaces file?

In particular, do you have eth1 in the auto line?


oops sorry that was my ifconfig

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
 
# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback
 
# The primary network interface
iface eth0 inet static
        address 192.168.3.243
        netmask 255.255.255.0
        network 192.168.3.0
        broadcast 192.168.3.255
        gateway 192.168.3.254
        # dns-* options are implemented by the resolvconf package, if installed
        
 
iface eth1 inet static
        address 192.168.3.240
        netmask 255.255.255.0
        broadcast 192.168.3.255
        network 192.168.3.0
        gateway 192.168.3.254
        # dns-* options are implemented by the resolvconf package, if installed

---

### Post by chet on 2009-09-11
Also noticed that when I insert a CAT5 into eth0 eth1 drops, happens on both servers that I have, can these NIC's be bonded at all and if so could this be my issue?

---

### Post by chet on 2009-10-14
I would like to revisit this today as I'm still no further forward getting this to work, I will post my interfaces and such to see if any of it helps you to help me resolve my problem.

Problem still that same as if I configure a second IP address on my second Ethernet card it for some reason bridges, I can ping both IP's even if one cable is removed.

 sudo lspci
> 00:00.0 Host bridge: Intel Corporation 5000X Chipset Memory Controller Hub (rev 12)
00:02.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x8 Port 2-3 (rev 12)
00:03.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 3 (rev 12)
00:04.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x8 Port 4-5 (rev 12)
00:05.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 5 (rev 12)
00:06.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 6 (rev 12)
00:07.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 7 (rev 12)
00:08.0 System peripheral: Intel Corporation 5000 Series Chipset DMA Engine (rev 12)
00:10.0 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 12)
00:10.1 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 12)
00:10.2 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 12)
00:11.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev 12)
00:13.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev 12)
00:15.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev 12)
00:16.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev 12)
00:1c.0 PCI bridge: Intel Corporation 631xESB/632xESB/3100 Chipset PCI Express Root Port 1 (rev 09)
00:1d.0 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #1 (rev 09)
00:1d.1 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #2 (rev 09)
00:1d.2 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #3 (rev 09)
00:1d.7 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset EHCI USB2 Controller (rev 09)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d9)
00:1f.0 ISA bridge: Intel Corporation 631xESB/632xESB/3100 Chipset LPC Interface Controller (rev 09)
00:1f.1 IDE interface: Intel Corporation 631xESB/632xESB IDE Controller (rev 09)
00:1f.3 SMBus: Intel Corporation 631xESB/632xESB/3100 Chipset SMBus Controller (rev 09)
01:01.0 VGA compatible controller: ATI Technologies Inc ES1000 (rev 02)
02:00.0 RAID bus controller: Adaptec AAC-RAID (Rocket) (rev 02)
03:00.0 PCI bridge: Broadcom EPB PCI-Express to PCI-X Bridge (rev c2)
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet (rev 11)
05:00.0 PCI bridge: Broadcom EPB PCI-Express to PCI-X Bridge (rev c2)
06:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet (rev 11)
10:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Upstream Port (rev 01)
10:00.3 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express to PCI-X Bridge (rev 01)
11:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E1 (rev 01)
11:01.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E2 (rev 01)

more /etc/network/interfaces
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
 
# The loopback network interface
auto lo
iface lo inet loopback
 
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.3.243
        netmask 255.255.255.0
        network 192.168.3.0
        broadcast 192.168.3.255
        gateway 192.168.3.254
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 194.168.4.100 194.168.8.100
        dns-search smartservermonitoring.com
 
auto eth1
iface eth1 inet static
        address 192.168.3.140
        netmask 255.255.255.0
        network 192.168.3.0
        broadcast 192.168.3.255
        gateway 192.168.3.254

ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:14:5e:17:39:70  
          inet addr:192.168.3.243  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::214:5eff:fe17:3970/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41315 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42070 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8134323 (7.7 MB)  TX bytes:6990774 (6.6 MB)
          Interrupt:18 Memory:c8000000-c8012100 
 
eth1      Link encap:Ethernet  HWaddr 00:14:5e:17:39:72  
          inet addr:192.168.3.140  Bcast:192.168.3.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:ce000000-ce012100 
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25523 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12538227 (11.9 MB)  TX bytes:12538227 (11.9 MB)

I can at the minute ping both the above IP's even though there is no Ethernet cable connected to eth1

Does anybody know how I resolve this issue please

Thanks

---

