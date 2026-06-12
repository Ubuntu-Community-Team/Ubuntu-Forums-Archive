---
title: "enumeration of nics"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by wshieh on 2007-01-17
hello,

(i'm new here btw!)

I'm having trouble with the enumeration of the nics....
Sometime after reboot eth3 became eth4
and I'm have configuration to add eth0, eth1, eth2, eth3 to a bond,
so when eth3 changes to eth4, there is only 3 ethX added to the bond.

What can I do here to ensure it always uses eth 0, 1,2,3 ??

Thanks!
newbie

---

### Post by hal10000 on 2007-01-17
What network cards do have? Are they ordinary ethernet cards, pcmcia wireless usb or whatever?

Open a terminal window (Apps--->Terminal). Try the following commands:

1. [COLOR="Red"]lspci[/COLOR]
2. [COLOR="Red"]cat /etc/interfaces[/COLOR]
3. [COLOR="Red"]ifconfig[/COLOR]

and post their outputs
To post the output you can mark the output with your mouse and past it with the middle mouse button to the browser.

---

### Post by wshieh on 2007-01-17
[B]output from lspci:
[/B]
0000:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
0000:00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
0000:00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
0000:00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
0000:00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
0000:00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
0000:04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 11)
0000:05:00.0 Ethernet controller: Intel Corporation: Unknown device 105e (rev 06)
0000:05:00.1 Ethernet controller: Intel Corporation: Unknown device 105e (rev 06)


[B]output from cat /etc/network/interfaces
[/B]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto bond0
iface bond0 inet static
address 10.3.31.194
netmask 255.255.255.0
gateway 10.3.31.31
post-up ifenslave bond0 eth0 eth1 eth2 eth3
pre-down ifenslave -d bond0 eth0 eth1 eth2 eth3



[B]output from ifconfig:
[/B]
bond0     Link encap:Ethernet  HWaddr 00:E0:81:59:25:C1
          inet addr:10.3.31.194  Bcast:10.3.31.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:fe59:25c1/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:413 errors:0 dropped:0 overruns:0 frame:0
          TX packets:527 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:39482 (38.5 KiB)  TX bytes:140290 (137.0 KiB)

eth0      Link encap:Ethernet  HWaddr 00:E0:81:59:25:C1
          UP BROADCAST SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0x8000

eth1      Link encap:Ethernet  HWaddr 00:E0:81:59:25:C1
          inet6 addr: fe80::2e0:81ff:fe59:25c1/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:413 errors:0 dropped:0 overruns:0 frame:0
          TX packets:527 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:39482 (38.5 KiB)  TX bytes:140290 (137.0 KiB)
          Interrupt:58

eth2      Link encap:Ethernet  HWaddr 00:E0:81:59:25:C1
          UP BROADCAST SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x6c00 Memory:fd8e0000-fd900000

eth3      Link encap:Ethernet  HWaddr 00:E0:81:59:25:C1
          UP BROADCAST SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x6800 Memory:fd8a0000-fd8c0000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1015 (1015.0 b)  TX bytes:1015 (1015.0 b)

---

### Post by yota on 2007-01-17
The bindings between names and HW address of the network interfaces are set in the /etc/iftab file
```

yota@linbook:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.  See iftab(5).
eth0 mac 00:C0:9F:50:BB:EC arp 1
wlan0 mac 00:0E:35:4D:DD:13

```

just modify it to your needs picking the HWaddr from 'ifconfig -a'.
'man iftab' for details.

Hope this helps!

---

### Post by wshieh on 2007-01-18
Thank you yota!!

---

### Post by whit on 2008-05-26
In current Ubuntu, the bindings between NIC hardware and names are in /etc/udev/rules.d/70-persistent-net.rules

---

