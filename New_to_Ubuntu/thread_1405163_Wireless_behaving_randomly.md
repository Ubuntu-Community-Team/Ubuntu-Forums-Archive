---
title: "Wireless behaving randomly"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by AndresM on 2010-02-12
Hello All,

I'm using an Acer Aspire 1360 laptop. with xubuntu. It seems to be a good idea to show the hardware I have, I used  sudo lshw -short.

```
andres@andres-laptop:~$ sudo lshw -short
[sudo] password for andres: 
H/W path           Device      Class          Description
=========================================================
                               system         Aspire 1360
/0                             bus            Aspire 1360
/0/0                           memory         111KiB BIOS
/0/4                           processor      Mobile AMD Sempron(tm) Processor 3
/0/4/8                         memory         128KiB L1 cache
/0/4/9                         memory         128KiB L2 cache
/0/21                          memory         512MiB System Memory
/0/21/0                        memory         256MiB DIMM DRAM Synchronous
/0/21/1                        memory         256MiB DIMM DRAM Synchronous
/0/100                         bridge         K8M800 Host Bridge
/0/100/1                       bridge         VT8237 PCI bridge [K8T800/K8T890 S
/0/100/1/0                     display        K8M800/K8N800/K8N800A [S3 UniChrom
/0/100/a           wlan0       network        [AirConn] INPROCOMM IPN 2220 Wirel
/0/100/b                       bridge         PCI7420 CardBus Controller
/0/100/b.1                     bridge         PCI7420 CardBus Controller
/0/100/b.2                     bus            PCI7x20 1394a-2000 OHCI Two-Port P
/0/100/10                      bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.1                    bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.2                    bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.3                    bus            USB 2.0
/0/100/11                      bridge         VT8235 ISA Bridge
/0/100/11.1        scsi0       storage        VT82C586A/B/VT82C686/A/B/VT823x/A/
/0/100/11.1/0      /dev/sda    disk           40GB HTS424040M9AT00
/0/100/11.1/0/1    /dev/sda1   volume         36GiB EXT4 volume
/0/100/11.1/0/2    /dev/sda2   volume         1270MiB Extended partition
/0/100/11.1/0/2/5  /dev/sda5   volume         1270MiB Linux swap / Solaris parti
/0/100/11.1/1      /dev/cdrom  disk           DVDRW SOSW-852S
/0/100/11.5                    multimedia     VT8233/A/8235/8237 AC97 Audio Cont
/0/100/11.6                    communication  AC'97 Modem Controller
/0/100/12          eth0        network        VT6102 [Rhine-II]
/0/101                         bridge         K8M800 Host Bridge
/0/102                         bridge         K8M800 Host Bridge
/0/103                         bridge         K8M800 Host Bridge
/0/104                         bridge         K8M800 Host Bridge
/0/105                         bridge         K8M800 Host Bridge
/0/106                         bridge         K8 [Athlon64/Opteron] HyperTranspo
/0/107                         bridge         K8 [Athlon64/Opteron] Address Map
/0/108                         bridge         K8 [Athlon64/Opteron] DRAM Control
/0/109                         bridge         K8 [Athlon64/Opteron] Miscellaneou
/0/1                           network        ISL3890 [Prism GT/Prism Duette]/IS
andres@andres-laptop:~$ 

```Note that I have a wireless cardbus adaptor as well has the internal wireless of the PC this is the SMC2835W, I guess the same one mentioned here: [http://ubuntuforums.org/showthread.php?t=134679](http://ubuntuforums.org/showthread.php?t=134679) The problem I have is that it sometimes detects the networks around but does not want to connect. Things i have tried in the past was installing wicd (less sucess) and i have installed the windows wireless drivers from the ACER web page.  Following the documentation indications. 
Other times it connects directly no problem on boot.
And the third situation is when it tries for a couple of times and then connects. Just now it&#347; one of those furtunate times i have wireless. In case you are wondering even though it&#347; a laptop I have never moved it from the same spot of the house. My wife uses netbook remix on her One netbook and seems to work with no problem. As well has her itouch. 
We use a netgear router. 

If I check the network now:

```
andres@andres-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: wlan1
       version: 00
       serial: 00:0e:9b:5f:23:a0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+neti2220 driverversion=1.55+LanExpress,03/29/2004,2.10. ip=192.168.1.15 latency=64 link=yes maxlatency=32 mingnt=32 multicast=yes wireless=IEEE 802.11g
       resources: irq:21 ioport:1c00(size=32) memory:d0006000-d000601f memory:d0005000-d00057ff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0a:e4:5f:aa:91
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:23 ioport:1800(size=256) memory:d0006800-d00068ff
andres@andres-laptop:~$ 

```I have removed the SMC cardbus, but it doesnt say if its  "CLAIMED, UNCLAIMED, ENABLED or DISABLED" but I do have it working!

i just wanted a bit of stability and not to be frustrated with not having wireless. 

Oh! sometimes I get a pop up that says disconected when it really is connected. 

Should i move back to Ubuntu? To say the truth I had the same problem with ubuntu
Thanks for your time!

---

### Post by nothingspecial on 2010-02-12
I would get a new wireless card. Read [[COLOR="Magenta"]this[/COLOR]]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1042480")

---

