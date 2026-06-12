---
title: "Big problems connecting to my wireless network."
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by kaminix on 2007-06-17
Router: belkin54g (that's the network name, I think that makes the router model a Belkin 54G)
Network card: RaLink RT2500 802.11g Cardbus/mini-PCI (intergrated)
OS: Kubuntu 7.04

So I CAN connectl but only for short periods of time. On the previous version of the OS with the less flashy network manager it worked fine, however on 7.04 I need to trick myself into the network. Step-by-step how I do it:
1. Open a terminal.
2. Choose belkin54g in the network manager. It will stand idle with the "Activation stage: Configuring device." at 28%. It won't move on past 28% and actually connect.
3. Before the window from the network manager closes, type "sudo dhclient ra0" (ra0 is my wireless network interface). It will then 99% of the times find we an IP immediately, and I can use the net **for a couple of minutes**. Bold for HUGE annoyance.

Any idea how to solve this? Additional information will be supplied on request, however I think this would be all.


EDIT:
**ifconfig output while online:**
kaminix@kukbuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:560 (560.0 b)  TX bytes:560 (560.0 b)

ra0       Link encap:Ethernet  HWaddr 00:0D:F0:1D:31:B1
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:f0ff:fe1d:31b1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:2866 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23364 errors:1 dropped:1 overruns:0 carrier:0
          collisions:38 txqueuelen:1000
          RX bytes:2193947 (2.0 MiB)  TX bytes:1430045 (1.3 MiB)
          Interrupt:17 Base address:0x4000

**ifconfig while offline**
kaminix@kukbuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:560 (560.0 b)  TX bytes:560 (560.0 b)

---

