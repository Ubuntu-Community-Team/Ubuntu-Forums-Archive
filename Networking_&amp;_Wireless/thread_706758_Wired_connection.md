---
title: "Wired connection"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by Condor1 on 2008-02-24
I've recently installed Ubuntu on a laptop and have been having problems trying to set up a wired network connection.I have the cat5 cable connected  o a netgear FA510 card on one end and the other end going to port 2 on my 2WIRE router. Here are some of the outputs from the terminal: 

**sudo lshw**
```

            
description: Computer
product: PCG-F420(UC)
vendor: Sony Corporation
version: 01
serial: 28306930-3506017
 width: 32 bits
    capabilities: smbios-2.1 dmi-2.1
  *-core
       description: Motherboard
       product: PCG-F420(UC)
       vendor: Sony Corporation
       physical id: 0
       version: 01
       serial: 28306930-3506017
       slot: @
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0114K1 (02/03/00)
          size: 84KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing acpi usb agp ieee1394boot smartbattery netboot
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: MMO Con1
          size: 450MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 32KB
             capacity: 512KB
             capabilities: burst external write-back
        *-cache:1
             description: L2 cache
             physical id: 0
             size: 256KB
     *-cache
          description: L1 cache
          physical id: 9
          slot: L1 Cache
          size: 16KB
          capacity: 16KB
          capabilities: asynchronous internal write-back
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 256MB
          capacity: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: J28
             size: 256MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous [empty]
             physical id: 1
             slot: J24
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: J31
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 40000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: latency=64
          resources: iomemory:40000000-40ffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NM2200 [MagicGraph 256AV]
                vendor: Neomagic Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: 20
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: latency=128 maxlatency=255 mingnt=16
                resources: iomemory:fd000000-fdffffff iomemory:fe800000-febfffff iomemory:fec00000-fecfffff irq:9
        *-isa
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@00:07.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE latency=64
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:fcf0-fcff
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: HITACHI_DK23AA-60
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 00XEA0G2
                   serial: E52317
                   size: 5729MB
                   capacity: 5729MB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma2 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 5428MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 298MB
                      capacity: 298MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 298MB
                         capabilities: nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: IDE CD-ROM
                   product: CD-224E
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.5A
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=64
             resources: ioport:fcc0-fcdf irq:9
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-bridge
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus latency=0
             resources: irq:9
        *-firewire
             description: FireWire (IEEE 1394)
             product: CXD3222 i.LINK Controller
             vendor: Sony Corporation
             physical id: 8
             bus info: pci@00:08.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=4
             resources: iomemory:fedff000-fedff7ff iomemory:fedffc00-fedffdff irq:9
        *-multimedia
             description: Multimedia audio controller
             product: YMF-744B [DS-1S Audio Controller]
             vendor: Yamaha Corporation
             physical id: 9
             bus info: pci@00:09.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Yamaha DS-1 PCI latency=64 maxlatency=25 mingnt=5
             resources: iomemory:fedf0000-fedf7fff ioport:fc40-fc7f ioport:fcec-fcef irq:9
        *-communication UNCLAIMED
             description: Communication controller
             product: HCF 56k Data/Fax Modem
             vendor: Rockwell International
             physical id: a
             bus info: pci@00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=64
             resources: iomemory:fede0000-fedeffff irq:9
        *-pcmcia:0
             description: CardBus bridge
             product: RL5c478
             vendor: Ricoh Co Ltd
             physical id: c
             bus info: pci@00:0c.0
             version: 80
             width: 64 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5
             resources: iomemory:30010000-30010fff iomemory:b00502000-b00501fff irq:9
           *-network
                description: FA510
                product: Fast Ethernet CardBus Card
                vendor: NETGEAR
                physical id: 0
                version: 1.00
                slot: Socket 0
                resources: irq:9
        *-pcmcia:1
             description: CardBus bridge
             product: RL5c478
             vendor: Ricoh Co Ltd
             physical id: c.1
             bus info: pci@00:0c.1
             version: 80
             width: 64 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
             resources: iomemory:30011000-30011fff iomemory:b00906000-b00905fff irq:9
     *-network
          description: Ethernet interface
          product: DECchip 21142/43
          vendor: Digital Equipment Corporation
          physical id: 1
          bus info: pci@02:00.0
          logical name: eth0
          version: 41
          serial: 00:10:7a:60:31:9c
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master ethernet physical
          configuration: broadcast=yes driver=tulip driverversion=1.1.14 latency=64 maxlatency=40 mingnt=20 multicast=yes
          resources: ioport:1400-147f iomemory:24000000-240003ff irq:9


```

**ifconfig -a**

```
eth0      Link encap:Ethernet  HWaddr 00:10:7A:60:31:9C  

inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:6 dropped:0 overruns:0 carrier:6
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
Interrupt:9 Base address:0x1400 


lo        Link encap:Local Loopback  

inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:61 errors:0 dropped:0 overruns:0 frame:0
TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:5369 (5.2 KiB)  TX bytes:5369 (5.2 KiB)

```



**route**

```
Kernel IP routing table

Destination     Gateway     Genmask         Flags Metric    Ref    Use Iface

192.168.1.0     *              55.255.255.0     U     0            0        0 eth0

link-local           *              255.255.0.0       U     1000       0        0 eth0

default       192.168.1.254   0.0.0.0         UG     0            0        0 eth0
```



**sudo dhclient**

```
Internet Systems Consortium DHCP Client V3.0.4

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:10:7a:60:31:9c
Sending on   LPF/eth0/00:10:7a:60:31:9c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.

No working leases in persistent database - sleeping.
```


If I go to: /etc/network/interfaces. I get: 

auto l0
iface l0 inet loopback


iface eth0 inet static
address 192.168.1.64
netmask 255.255.255.0
gateway 192.168.1.254

auto eth0



If I go to: System--Administration--Network and set up for "static", I get inept address shown. But if I set it up for "automatic DHCP:, it doesn't show up under eth0. 

I'm leaning towards DHCP not being configured, but I'm not sure.  Any help will be appreciated.
Also, I have my desktop computer (running windows) that is connected to my 2WIRE router (using WEP key) that is running good.

---

### Post by nixscripter on 2008-02-25
You did not describe exactly what the symptoms are. I am assuming that you cannot connect to anything. If this is not the case, please be specific about the problem.

From your output, DHCP looks to be the problem, but first, I want to rule out a few simple things:

1. Try just pinging the router. Does that work?

2. Is the router's IP address 192.168.1.254? If not, figure out what it is and change the default gateway to that with:
```
sudo route del default
sudo route add default gw **real-ip-address**

``` and try again.

3. Is the router set up to use DHCP? If so, what is its IP address range? Does that conflict with the static IP the machine currently has?

---

### Post by Condor1 on 2008-02-26
I should have gave more information last time. sorry about that. 

I can't get connected to the network at all on this laptop. I've installed Ubuntu on this laptop just recently. (No other operating system was installed on here). I can't even take any software updates I have pending on here to install  on this laptop because it requires internet connection. 

1.) I went to System ---Administration---Network tools. tabbed over to "ping". I entered th router's ip and clicked  "ping". The result I got was: 

Round trip time statistics                Transmission statistics 
Minimum:  0.00ms                           Packets transmitted: 5
Average: 0.00ms                            packets received: 0
Maximum: 0.00ms                           successful packets: 0%

2.) I called my dsl provider and they even confirmed that my router's ip is 192.168.1.254  
They also gave me the primary and alternate DNS server as well.  

I went to the terminal and typed "sudo route del default", I get     No such process
When I type this: "sudo route add default gw 192.168.1.254", I get "**network is unreachable**". 

3.) My dsl  provider told me I have dynamic, not static ip. So, I think the manual settings I have there now is wrong. 

Question? under network settings (in connection settings), there is three options listed.. 1) Static IP address..2) Automatic configuration (DHCP)...3) local zeroconf network (IPv4 LL). I'm not sure if it should be the second or third now. (i'm assuming it might be #2).

---

### Post by nixscripter on 2008-02-26
Hmm. It would stilll appear to be a routing problem. Try this.

FIrst, run ifconfig again, and make sure eth0 has an IP address on the 192.168.1.0 network. **If it doesn't,** give yourself one for this experiment with: ```
sudo ifconfig eth0 192.168.1.7
```

Now try just looking for the router with a ping. In the terminal ```
ping -c 1 -b 192.168.1.255
``` **If you get "network unreachable" again,** which may happen because the routing table is messed up, set the route with this: ```
sudo route add 192.168.1.0 eth0
``` and then try again.

---

### Post by bunglega on 2008-02-26
Not trying to hijack this thread or anything but I'm having a related problem.  I am receiving an IP address from DHCP but it is not setting a default gateway ... When I execute 'sudo route add default gw real-ip-address' I am able to surf the web, etc.  My problem is fixed until I reboot and the route is deleted.  

How can I 'sudo route add default gw real-ip-address' and have it stay upon a restart?

Thanks...
Wes

---

### Post by stream303 on 2008-02-26
> **bunglega said:**
> How can I 'sudo route add default gw real-ip-address' and have it stay upon a restart?

Because we are using windows-centric soho devices, the easiest cure I know of when using dhcp is to just put your ISP's primary and backup dns nameservers *into the router's setup page*, rather than mess around with a local configuration.

If you don't know your isp's dns servers, (don't make them up), try looking at [www.opendns.org](www.opendns.org) addresses at the bottom right of the page.

Change your routers useraname or at least the password.  While you are there you might want to disable any sort of remote access, or UpNP windows options.

---

### Post by Condor1 on 2008-03-16
```
ping -c 1 -b 192.168.1.255
```

The results from my laptop in the terminal was: 

```
WARNING: pinging broadcast address
PING 192.168.1.255 (192.168.1.255)  56(84)  bytes of data.

---192.168.1.255 ping statistics---
1 packets transmitted, 0 received, 100% packet loss, time 0ms
```




For the hell of it, I booted up the ubuntu cd on my desktop computer that is running windows (haven't installed linux on it yet). When I went to the desktop, ubuntu  automatically detected the 2wire router. I didn't have to manually enter any network settings. I'm actually writing this post with ubuntu on my desktop computer. :)

fhere is the output from my desktop computer: 
```

ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:80:AD:D0:E5:8F  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::280:adff:fed0:e58f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13885322 (13.2 MiB)  TX bytes:1419874 (1.3 MiB)
          Interrupt:18 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30982 (30.2 KiB)  TX bytes:30982 (30.2 KiB)

ubuntu@ubuntu:~$ ping -c 1 -b 192.168.1.255
WARNING: pinging broadcast address
PING 192.168.1.255 (192.168.1.255) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=255 time=1.93 ms

--- 192.168.1.255 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.933/1.933/1.933/0.000 ms

ubuntu@ubuntu:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 11211
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:80:ad:d0:e5:8f
Sending on   LPF/eth0/00:80:ad:d0:e5:8f
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
bound to 192.168.1.64 -- renewal in 34435 seconds.
ubuntu@ubuntu:~$ 
```


I was thinking of installing ubuntu on this desktop computer to have the option of booting the computer in linux or windows since the laptop was giving me problems. Will I be able to install linux without removing windows entirely from this computer?

---

### Post by nixscripter on 2008-03-19
```
WARNING: pinging broadcast address
PING 192.168.1.255 (192.168.1.255)  56(84)  bytes of data.

---192.168.1.255 ping statistics---
1 packets transmitted, 0 received, 100% packet loss, time 0ms
```

That means the packet never got to the router. It's being dropped on the way.

> **Condor1 said:**
> 
For the hell of it, I booted up the ubuntu cd on my desktop computer that is running windows (haven't installed linux on it yet). When I went to the desktop, ubuntu  automatically detected the 2wire router. I didn't have to manually enter any network settings. I'm actually writing this post with ubuntu on my desktop computer. :)


Looking at the output from the CD boot, that's what I would expect. I'm starting to wonder about some kind of hardware problem with the other machine.

> **Condor1 said:**
> 
I was thinking of installing ubuntu on this desktop computer to have the option of booting the computer in linux or windows since the laptop was giving me problems. Will I be able to install linux without removing windows entirely from this computer?

Yes. There are dozens of dual boot tutorials and instruction sets throughout the internet, and probably around here.

---

