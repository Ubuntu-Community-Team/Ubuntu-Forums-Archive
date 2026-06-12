---
title: "Eth0 suddenly shutting down"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by NaiNebel on 2007-04-24
I just had my computer repaired. Upon its return, I hooked it up to my ethernet to reinstall Ubuntu. Everything was working fine until I started updating. Halfway through the update, the ethernet stopped working (says its disconnected), and will not work on the computer period. I haven't yet been able to get wireless working. I booted to Windows and, even there, the ethernet is not working.

I checked both the ethernet cable and the router itself, no problem with either. There's also no firewall against the ethernet cable that I'm aware of.

Any ideas?

---

### Post by amohanty on 2007-04-24
can you post the output of:

ifconfig -a

and 

dmesg | tail -n 100

AM

---

### Post by NaiNebel on 2007-04-24
Can do:

ifconfig -a:

> eth 0 Link encap: Ethernet HWadder 00:0F:B0:0B:41:FA
UP BROADCAST MULTICAST MTU:1500 Metric: 1
Rx Packets:0 errors:0 dropped: 0 overruns: 0 frame: 0
TX packerts:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX Bytes:0 (0.0 b)
Interrupt: 185  Base address: 0x4000

eth 1 Link encap: Ethernet HWadder 00:90:4B:9D:B4:62
UP BROADCAST MULTICAST MTU:1500 Metric: 1
Rx Packets:0 errors:0 dropped: 0 overruns: 0 frame: 0
TX packerts:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX Bytes:0 (0.0 b)
Interrupt: 185  Base address: 0xc000

As for DMSEG, the applicable line seems to be:

> [17179617.036000]ADDRCONF (NETDEV_UP): eth0: link is not ready

With an earlier line saying Link Down.

---

### Post by NaiNebel on 2007-04-25
upgraded to Feisty, which seems to be helping the problem. I'm working on getting wireless working on it.

However, though I do seem to have my wired connection working fairly often, I can't seem to make it constant. It will randomly shut off for, on occasion, extended periods of time. I'll be able to post exact logs of requested info, I think, as I can now copy/paste instead of having to transcribe it between computers.

---

### Post by amohanty on 2007-04-25
The next time it goes down try:

sudo ifup eth0

Also post the contents of /etc/network/interfaces

AM

---

### Post by NaiNebel on 2007-04-25
The Ifup replies:

"Ifup: interface eth0 already configured."

And interfaces includes:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by amohanty on 2007-04-26
And this is right after the connection went down??
AM

---

### Post by jfinkels on 2007-04-26
Just for good measure, I always do the following:
```

sudo ifdown eth0 && sudo ifup eth0

```
because ifup doesn't like when eth0 is already configured.

---

### Post by selim76 on 2007-04-26
can you sen the output of lshw?

---

### Post by NaiNebel on 2007-04-26
sudo ifdown eth0 && sudo ifup eth0
> RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5399
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0f:b0:0b:41:fa
Sending on   LPF/eth0/00:0f:b0:0b:41:fa
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0f:b0:0b:41:fa
Sending on   LPF/eth0/00:0f:b0:0b:41:fa
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15

lshw
> nai-laptop                
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 511MB
     *-cpu
          product: AMD Athlon(tm) XP Processor 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.12.0
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext 3dnowext 3dnow up ts fid vid ttp cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci:0
          description: Host bridge
          product: nForce3 Host Bridge
          vendor: nVidia Corporation
          physical id: f0000000
          bus info: pci@00:00.0
          version: a4
          width: 32 bits
          clock: 66MHz
          resources: iomemory:f0000000-f7ffffff
        *-isa
             description: ISA bridge
             product: nForce3 LPC Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: a6
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce3 SMBus
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@00:01.1
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
             resources: ioport:2040-207f ioport:2000-203f irq:10
        *-usb:0
             description: USB Controller
             product: nForce3 USB 1.1
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: a5
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: iomemory:e8000000-e8000fff irq:19
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: nForce3 USB 1.1
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: a5
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: iomemory:e8001000-e8001fff irq:20
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: USB-PS/2 Optical Mouse
                   vendor: B16_b_02
                   physical id: 1
                   bus info: usb@2:1
                   version: 98.02
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: nForce3 USB 2.0
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@00:02.2
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: iomemory:e8004000-e80040ff irq:18
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-15-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb
                   description: Mass storage device
                   product: External HDD
                   vendor: Western Digital
                   physical id: 1
                   bus info: usb@3:1
                   version: 6.02
                   serial: 57442D5743414C3935383138323933
                   capabilities: usb-2.00 scsi
                   configuration: driver=usbhid maxpower=100mA speed=480.0MB/s
        *-multimedia
             description: Multimedia audio controller
             product: nForce3 Audio
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@00:06.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
             resources: ioport:1400-14ff ioport:1c00-1c7f iomemory:e8002000-e8002fff irq:19
        *-communication UNCLAIMED
             description: Modem
             product: nForce3 Audio
             vendor: nVidia Corporation
             physical id: 6.1
             bus info: pci@00:06.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: generic cap_list
             configuration: latency=0 maxlatency=5 mingnt=2
             resources: ioport:1800-18ff ioport:1c80-1cff iomemory:e8003000-e8003fff irq:18
        *-ide
             description: IDE interface
             product: nForce3 IDE
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@00:08.0
             version: a5
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:2080-208f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   product: TOSHIBA MK8032GAX
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 74GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   product: HL-DT-STCD-RW/DVD DRIVE GCC-4243N
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 692MB
                   capabilities: packet
        *-pci:0
             description: PCI bridge
             product: nForce3 PCI Bridge
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@00:0a.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@02:01.0
                logical name: eth0
                version: 10
                serial: 00:0f:b0:0b:41:fa
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
                resources: ioport:7000-70ff iomemory:e8104000-e81040ff irq:17
           *-network:1 DISABLED
                description: Wireless interface
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@02:02.0
                logical name: eth1
                version: 03
                serial: 00:90:4b:9d:b4:62
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:e8100000-e8101fff irq:22
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1620 PC Card Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@02:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: iomemory:e8102000-e8102fff irq:16
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1620 PC Card Controller
                vendor: Texas Instruments
                physical id: 4.1
                bus info: pci@02:04.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: iomemory:e8103000-e8103fff irq:17
           *-system UNCLAIMED
                description: System peripheral
                product: PCI1620 Firmware Loading Function
                vendor: Texas Instruments
                physical id: 4.2
                bus info: pci@02:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=7
                resources: ioport:7400-743f
        *-pci:1
             description: PCI bridge
             product: nForce3 AGP Bridge
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@00:0b.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV17 [GeForce4 420 Go 32M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a3
                size: 64MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: iomemory:ea000000-eaffffff iomemory:f8000000-fbffffff iomemory:fc000000-fc07ffff irq:21
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
  *-scsi
       physical id: 1
       bus info: scsi@0
       logical name: scsi0
       capabilities: scsi-host
       configuration: driver=usb-storage


---

### Post by NaiNebel on 2007-04-30
Are there any thoughts on how to fix this? I can't get the computer wireless enabled without it.

---

### Post by amohanty on 2007-05-01
Lets try another approach, is this an onboard NIC or a PCI nic?

AM

---

### Post by NaiNebel on 2007-05-01
If you mean between an built-in wireless card or one I plug in and bought separately, it's built-in.

Edit: Er, ethernet, I mean.

---

### Post by amohanty on 2007-05-01
I was talking about the wired connection. Is that a built-in card or one that you plugged in?

AM

---

### Post by NaiNebel on 2007-05-01
The wired card is built in.

---

### Post by amohanty on 2007-05-01
Can you post the output of 
**lspci**

the card should still be on the pci bus.

AM

---

