---
title: "toshiba satellite wireless woes"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by yonson_yon on 2006-08-17
howdy folks,

i'm using a toshiba m105-s3002, and i can't seem to get wireless to work
it's an intel centrino duo so i think it's the Intel® PRO/Wireless 2915ABG or the Intel® PRO/Wireless 2200BG. however i have been unable to positively identify the built-in wireless and install/configure the proper drivers and whatnot.

using dapper 6.0.6

any assitance would be greatly appreciated
thanks!

---

### Post by yonson_yon on 2006-08-17
additionally, sorry about the double post kids,

here's a little more info
lshw -C network

  *-network
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945
       resources: iomemory:d0100000-d0100fff irq:169
  *-network
       description: Ethernet interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@05:08.0
       logical name: eth0
       version: 02
       serial: 00:0f:b0:e3:2b:e7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.14-k4-NAPI duplex=full firmware=N/A ip=192.168.1.35 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:d0006000-d0006fff ioport:2000-203f irq:233

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:E3:2B:E7
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fee3:2be7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2004027 (1.9 MiB)  TX bytes:408873 (399.2 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

---

### Post by yonson_yon on 2006-09-05
i believe it's the intell 2200bg

but when i tried to install the software in windoze it said that the hardware was turned off.  so i did the fn-f8 keyboard thingy and it didn't do anything, but it was a blank windows with no other software installed. hrm...

so i suppose the better question is how do i turn the damned thing on so that  the drivers will actually have something to drive.?

---

### Post by galamud on 2006-09-10
> **yonson_yon said:**
> i believe it's the intell 2200bg

but when i tried to install the software in windoze it said that the hardware was turned off.  so i did the fn-f8 keyboard thingy and it didn't do anything, but it was a blank windows with no other software installed. hrm...

so i suppose the better question is how do i turn the damned thing on so that  the drivers will actually have something to drive.?

Heh, I had the same problem and felt really stupid when I figured out what was wrong:

There's a little switch on the right-hand side of the laptop, near the front.  It turns the wireless on and off.  It's probably in the off position right now.  Turn it on and everything will work.

---

