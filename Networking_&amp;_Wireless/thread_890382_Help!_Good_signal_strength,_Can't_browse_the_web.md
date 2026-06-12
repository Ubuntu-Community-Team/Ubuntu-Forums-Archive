---
title: "Help! Good signal strength, Can't browse the web"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by DavidJxP3 on 2008-08-15
I'm new to Ubuntu and my system network icon shows I'm connected & have good signal strength but i can't browse the web!:confused:

---

### Post by jualin on 2008-08-15
Check that you were issued an IP address by your router. Right click on your network icon (next to the clock) and click on "connection information". And check that you have an IP address (usually something starting with 192.168.x.x)

---

### Post by DavidJxP3 on 2008-08-15
Sorry for not responding earlier... you were right it doesn't show an I.P address...

I don't know if this will help but in the terminal when it wasn't  showing the signal strength icon I entered ifconfig and this came up...


[SIZE="1"]david@JxP3:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:c0:a8:f4:06:2c  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



eth1      Link encap:Ethernet  HWaddr 00:50:04:82:f6:e5  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:11 Base address:0x2e80 



eth0:avahi Link encap:Ethernet  HWaddr 00:c0:a8:f4:06:2c  

          inet addr:169.254.5.225  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST MULTICAST  MTU:1500  Metric:1



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:526 errors:0 dropped:0 overruns:0 frame:0

          TX packets:526 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:26300 (25.6 KB)  TX bytes:26300 (25.6 KB)



wlan0     Link encap:Ethernet  HWaddr 00:16:b6:52:86:d4  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



wmaster0  Link encap:UNSPEC  HWaddr 00-16-B6-52-86-D4-00-00-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/SIZE]





and when it was showing signal strength...


[SIZE="1"]david@JxP3:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:c0:a8:f4:06:2c  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



eth1      Link encap:Ethernet  HWaddr 00:50:04:82:f6:e5  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:11 Base address:0x2e80 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:541 errors:0 dropped:0 overruns:0 frame:0

          TX packets:541 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:27620 (26.9 KB)  TX bytes:27620 (26.9 KB)



wlan0     Link encap:Ethernet  HWaddr 00:16:b6:52:86:d4  

          inet6 addr: fe80::216:b6ff:fe52:86d4/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:7 errors:0 dropped:0 overruns:0 frame:0

          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:832 (832.0 B)  TX bytes:4169 (4.0 KB)



wmaster0  Link encap:UNSPEC  HWaddr 00-16-B6-52-86-D4-00-00-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/SIZE]






hopefully that helps!!!  :)

---

### Post by jualin on 2008-08-16
I have two questions, first Can you connect to your wireless network with another computer or using Windows?, and second How did you install your Wireless in Ubuntu?

---

### Post by DavidJxP3 on 2008-08-16
Yes I can connect to my wireless network using another computer and Windows. I installed Ubuntu and this is how it was.

---

### Post by jualin on 2008-08-16
You may need to install the drivers for your wireless card. Run this two commands in the terminal and post the results on the forums, so we can find out what wireless card are you using. > lspci
lshw
I will check them tomorrow since right now it's 1:52 AM where I live (US Eastern Time). Good luck!

---

### Post by DavidJxP3 on 2008-08-16
Here it is... Oh and thank you very much for taking the time to help me. :guitar:



[SIZE="1"]david@JxP3:~$ lspci

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)

00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 04)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 11)

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 11)

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 11)

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 11)

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 11)

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 11)

01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)

01:0b.0 USB Controller: NEC Corporation USB (rev 43)

01:0b.1 USB Controller: NEC Corporation USB (rev 43)

01:0b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

01:0d.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)

01:0f.0 Multimedia controller: Sigma Designs, Inc. REALmagic Hollywood Plus DVD Decoder (rev 02)

david@JxP3:~$ lshw

WARNING: you should run this program as super-user.

jxp3                      

    description: Computer

    width: 32 bits

  *-core

       description: Motherboard

       physical id: 0

     *-memory

          description: System memory

          physical id: 0

          size: 510MiB

     *-cpu

          product: Celeron (Coppermine)

          vendor: Intel Corp.

          physical id: 1

          bus info: cpu@0

          version: 6.8.10

          size: 1100MHz

          width: 32 bits

          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up

        *-cache:0

             description: L1 cache

             physical id: 0

             size: 32KiB

        *-cache:1

             description: L2 cache

             physical id: 1

             size: 128KiB

     *-pci

          description: Host bridge

          product: 82815 815 Chipset Host Bridge and Memory Controller Hub

          vendor: Intel Corporation

          physical id: 100

          bus info: pci@0000:00:00.0

          version: 04

          width: 32 bits

          clock: 33MHz

          configuration: driver=agpgart-intel module=intel_agp

        *-display

             description: VGA compatible controller

             product: 82815 Chipset Graphics Controller (CGC)

             vendor: Intel Corporation

             physical id: 2

             bus info: pci@0000:00:02.0

             version: 04

             width: 32 bits

             clock: 66MHz

             capabilities: vga_controller bus_master cap_list

             configuration: driver=i810_smbus latency=0 module=i2c_i810

        *-pci

             description: PCI bridge

             product: 82801 PCI Bridge

             vendor: Intel Corporation

             physical id: 1e

             bus info: pci@0000:00:1e.0

             version: 11

             width: 32 bits

             clock: 33MHz

             capabilities: pci normal_decode bus_master

           *-network:0

                description: Ethernet interface

                product: 82801BA/BAM/CA/CAM Ethernet Controller

                vendor: Intel Corporation

                physical id: 8

                bus info: pci@0000:01:08.0

                logical name: eth0

                version: 03

                serial: 00:c0:a8:f4:06:2c

                width: 32 bits

                clock: 33MHz

                capabilities: bus_master cap_list ethernet physical

                configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

           *-usb:0

                description: USB Controller

                product: USB

                vendor: NEC Corporation

                physical id: b

                bus info: pci@0000:01:0b.0

                version: 43

                width: 32 bits

                clock: 33MHz

                capabilities: ohci bus_master cap_list

                configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1 module=ohci_hcd

           *-usb:1

                description: USB Controller

                product: USB

                vendor: NEC Corporation

                physical id: b.1

                bus info: pci@0000:01:0b.1

                version: 43

                width: 32 bits

                clock: 33MHz

                capabilities: ohci bus_master cap_list

                configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1 module=ohci_hcd

           *-usb:2

                description: USB Controller

                product: USB 2.0

                vendor: NEC Corporation

                physical id: b.2

                bus info: pci@0000:01:0b.2

                version: 04

                width: 32 bits

                clock: 33MHz

                capabilities: ehci bus_master cap_list

                configuration: driver=ehci_hcd latency=64 maxlatency=34 mingnt=16 module=ehci_hcd

           *-network:1

                description: Ethernet interface

                product: 3c905B 100BaseTX [Cyclone]

                vendor: 3Com Corporation

                physical id: d

                bus info: pci@0000:01:0d.0

                logical name: eth1

                version: 30

                serial: 00:50:04:82:f6:e5

                width: 32 bits

                clock: 33MHz

                capabilities: bus_master cap_list ethernet physical

                configuration: broadcast=yes driver=3c59x latency=64 maxlatency=10 mingnt=10 module=3c59x multicast=yes

           *-multimedia UNCLAIMED

                description: Multimedia controller

                product: REALmagic Hollywood Plus DVD Decoder

                vendor: Sigma Designs, Inc.

                physical id: f

                bus info: pci@0000:01:0f.0

                version: 02

                width: 32 bits

                clock: 33MHz

                capabilities: bus_master cap_list

                configuration: latency=64

        *-isa

             description: ISA bridge

             product: 82801BA ISA Bridge (LPC)

             vendor: Intel Corporation

             physical id: 1f

             bus info: pci@0000:00:1f.0

             version: 11

             width: 32 bits

             clock: 33MHz

             capabilities: isa bus_master

             configuration: latency=0

        *-ide

             description: IDE interface

             product: 82801BA IDE U100 Controller

             vendor: Intel Corporation

             physical id: 1f.1

             bus info: pci@0000:00:1f.1

             logical name: scsi0

             version: 11

             width: 32 bits

             clock: 33MHz

             capabilities: ide bus_master emulated

             configuration: driver=ata_piix latency=0 module=ata_piix

           *-cdrom

                description: DVD writer

                product: DVD16+/-DL4RWlD2

                vendor: Memorex

                physical id: 0.0.0

                bus info: scsi@0:0.0.0

                logical name: /dev/cdrom

                logical name: /dev/dvd

                logical name: /dev/scd0

                logical name: /dev/sr0

                version: JWS5

                capabilities: removable audio cd-r cd-rw dvd dvd-r

                configuration: ansiversion=5 status=open

        *-usb

             description: USB Controller

             product: 82801BA/BAM USB Controller #1

             vendor: Intel Corporation

             physical id: 1f.2

             bus info: pci@0000:00:1f.2

             version: 11

             width: 32 bits

             clock: 33MHz

             capabilities: uhci bus_master

             configuration: driver=uhci_hcd latency=0 module=uhci_hcd

        *-serial UNCLAIMED

             description: SMBus

             product: 82801BA/BAM SMBus Controller

             vendor: Intel Corporation

             physical id: 1f.3

             bus info: pci@0000:00:1f.3

             version: 11

             width: 32 bits

             clock: 33MHz

             configuration: latency=0

        *-multimedia

             description: Multimedia audio controller

             product: 82801BA/BAM AC'97 Audio Controller

             vendor: Intel Corporation

             physical id: 1f.5

             bus info: pci@0000:00:1f.5

             version: 11

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master

             configuration: driver=Intel ICH latency=0 module=snd_intel8x0

  *-network

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:16:b6:52:86:d4

       capabilities: ethernet physical wireless

       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

david@JxP3:~$ 
[/SIZE]



Hey it says you are in Miami,FL are you??? I'm there now. :lolflag:

---

### Post by jualin on 2008-08-16
Sorry for taking long to respond. One more question are you using a USB Wireless Adapter or a PCMCIA Wireless Adapter?. If you are using a USB Wireless adapter then we need to see the results of > lsusb and if you are using a PCMCIA adapter we need to see the results of > lspcmciaAlso if you know the model of your adapter we can help you better. ;)
And yes I live in Miami, FL. Do you live there too or just visiting?

---

### Post by DavidJxP3 on 2008-08-17
Sorry Ive been busy the results are!!!

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 13b1:000d Linksys 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

                                     :)

---

### Post by jualin on 2008-08-17
Is the model of your wireless card Linksys WUSB54Gv4?

---

### Post by jualin on 2008-08-17
[This link may help you install]("http://ubuntuforums.org/showthread.php?p=4373325") the driver if that's the model of your card.

---

### Post by jualin on 2008-08-17
I noticed that the drivers found on the Linksys website were and .exe file which you needed to open using Windows or Wine, so I uploaded the drivers to [Media Fire]("http://www.mediafire.com/?sharekey=06be8356ec349d57d2db6fb9a8902bda"). But don't use the guide I suggested unless that's the model of your card. Feel free to ask me if you need help. An Internet connection is not required to use the guide, only an Ubuntu LiveCD. Good luck!

---

### Post by brian mcgee on 2008-08-17
Just in case, plz post the output of

```
$ cat /etc/network/interfaces
```

---

### Post by DavidJxP3 on 2008-08-18
It's WUSB54G version 4. And yes I'm living here in Miami for now. :)

---

### Post by DavidJxP3 on 2008-08-18
Opps wrong thread :lolflag:

---

### Post by DavidJxP3 on 2008-08-18
My bad again i'm an idiot!!! ](*,)

---

### Post by jualin on 2008-08-18
Did you get it to work? Feel free to ask anything you like.

---

