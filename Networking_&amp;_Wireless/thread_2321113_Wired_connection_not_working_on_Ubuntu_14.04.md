---
title: "Wired connection not working on Ubuntu 14.04"
date: 2016-04-20
forum: Networking &amp; Wireless
---

### Post by Mateus_Dias_Ribeir on 2016-04-20
Hello,

I have an Asus G73SW laptop and I'm not able to connect to the internet by wire on Ubuntu 14.04. Wireless connection works fine.

First of all, I can't find any Ethernet controller when I type the command lspci, but the Network controller is there:

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF106M [GeForce GTX 460M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF106 High Definition Audio Controller (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 [Kilmer Peak] (rev 5f)
04:00.0 USB controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev 04)
```

I checked BIOS to see if Ethernet connection was off there but I could not find an option for this there. Is it possible that in my case the Ethernet controller is integrated on the motherboard?

When I type ifconfig -a I realize there is no "eth0" but I guess it is there renamed as "wmx0":

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74539 (74.5 KB)  TX bytes:74539 (74.5 KB)

wlan0     Link encap:Ethernet  HWaddr 64:80:99:08:39:f0  
          inet addr:186.217.153.44  Bcast:186.217.153.255  Mask:255.255.254.0
          inet6 addr: fe80::6680:99ff:fe08:39f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31801 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10015629 (10.0 MB)  TX bytes:1033967 (1.0 MB)

wmx0      Link encap:Ethernet  HWaddr 64:d4:da:25:1b:63  
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Command sudo lswh -C network returns:

```
mateus@mateus-G73Sw:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Centrino Advanced-N + WiMAX 6250 [Kilmer Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 5f
       serial: 64:80:99:08:39:f0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.19.0-56-generic firmware=41.28.5.1 build 33926 ip=186.217.153.44 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f4c00000-f4c01fff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: wmx0
       serial: 64:d4:da:25:1b:63
       capabilities: ethernet physical
       configuration: driver=i2400m_usb firmware=i6050-fw-usb-1.5.sbcf link=no
```

And finally command mii-tool -vv returns:

```
Using SIOCGMIIPHY=0x8947
SIOCGMIIPHY on 'eth0' failed: Operation not permitted
SIOCGMIIPHY on 'eth1' failed: Operation not permitted
SIOCGMIIPHY on 'eth2' failed: Operation not permitted
SIOCGMIIPHY on 'eth3' failed: Operation not permitted
SIOCGMIIPHY on 'eth4' failed: Operation not permitted
SIOCGMIIPHY on 'eth5' failed: Operation not permitted
SIOCGMIIPHY on 'eth6' failed: Operation not permitted
SIOCGMIIPHY on 'eth7' failed: Operation not permitted
```

Any ideas of how can I solve this problem?

Thanks in advance,
Mateus

---

