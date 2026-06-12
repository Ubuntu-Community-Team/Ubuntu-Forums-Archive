---
title: "Can't connect to internet"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by donald52duck on 2006-10-19
I'm completely new to linux & need help.

Problem: Using the "live CD" of ubunto 6.06LTS (i believe it's Dapper?), connection to the inetenet is good (it works even going through my Linksys BEFSR41 router using a CNET PRO 200 etho, "ancient Pavilian 6645c [stock]").

Everything is recognized from the CD, however when rebboting into the system (installed), NOTHING!! the card is recognized, but when using ifconfig no ipadd is listed (whereas it is in the CD start), DNS items about my ISP are present EVERYTHING LOKKS OK, but nothing is working????

My router is apprently able to handle the ipv6 (coz I get an address using the CD then checking ifconfig).

I've tried EVERYTHING I've found in these forums regarding this, BUT NOTHING WORKS!!!!!!!!

With all the collective brains of you Linux GODS (those who aren't stupid like us newbies) you still CAN'T come up with a solution?????? I mean it's VERY simple, "if it works from the CD, IT SHOULD ALSO WORK AFTER INSTALLATION". I know to you "GODS" us newbies must be stupid but to us you're still "THE MAN" with the answers. JUST REMEMBER........YOU WERE ONCE NEWBIES ALSO and just as stupid (once upon a time).

YOU GUYS CAN MAKE A FAR SUPERIOR SYTEM TO "Windows", but you can't seem to fix a simple issue like this????? AND IMCORPORATE IT INTO THE SETUP/INSTALL?????? 

GIVE US NEWBIES A FIX TO THIS.......... or stop bitching about Windows. Even if it is a "f______kd" up system, THEY seem to have figured it out. If not for "stupid" problems like this, Linux would already have "buried" Windows.  

I challenge you, the "GODS" of linux to give me an answer and a fix.

---

### Post by wieman01 on 2006-10-19
Please run these commands from a terminal window & post the output:
> ifconfig
> iwconfig
> iwlist scan
> sudo /etc/init.d/networking restart
> route
> sudo gedit /etc/network/interfaces
> sudo lspci
> sudo lshw
Then we'll see what's going on. Also tell me a bit more about your network: DHCP vs. Static IP, encryption (e.g. WEP, WPA), etc.

---

### Post by dmizer on 2006-10-19
might not want to be so belligerent toward the people who you seem to need to rely on for assistance.  don't bite the hand that feeds you ... so to speak.

and just because it works in the live install doesn't mean it will work in the hard drive install on the first try.  i challenge you to find a fully functional windows operating system that runs from a cd such that you can make a more similar comparison between linux and windows.  so sorry, even your windows hasn't "figured it out".

now the good news is that if it does work in the live cd, that you will be able to make it work in your full install.

have you tried configuring/enabling the card in system > administration > networking?

if so, post the results of wieman01's request.

---

### Post by donald52duck on 2006-10-19
dmizer..........forgive me if it sounds like "anger" at you guys.
it's more frustration becoz I so much want to get this working and away from windows. I tried the net install with debian but could never get the graphical interface to work. Ubuntu has a great install (better than windows) but for us newbies and windows addicts (not by choice but my need) our frustration comes from our "ignorance" at not being able to figure out something WE KNOW is so SIMPLE, yet for us (becoz windows has taken away our ability to THINK) we can't see what is staring us in the face. And when we DO finally "get it" we can't understand WHY we were so stupid. And for others of us we can't understand the "il-logic" of something working on the LV CD but NOT after the install. But you have to agree, it should be that way should it? 
Logically speaking. 

Please forgive me if I "barked" instead of "wimper" haha. 
It really is hard to teach old dogs new tricks, harder still when us old dogs know the new tricks are so simple. :-D :confused: :-k 

As soon as the Girl friends family isn't using thier PC I can use that monitor to get the info wieman01 needs (mine is being fixed).

---

### Post by donald52duck on 2006-10-19
To wieman01;


Here is the Info you asked for:
Also, I'm set to DHCP and my linksys is set to DHCP and as far as I know no "encryption"?? 
Half of my hdd is windows xp (using Kiero FW) and the other ubuntu. Here's the info.......


------- paul@pavilian:~$ ifconfig --------

eth0      Link encap:Ethernet  HWaddr 00:08:A1:90:CD:49
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:60 (60.0 b)  TX bytes:2394 (2.3 KiB)
          Interrupt:3 Base address:0x3400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

------ paul@pavilian:~$ iwconfig ------

lo        no wireless extensions.

eth0      no wireless extensions.

paul@pavilian:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

------ paul@pavilian:~$ sudo/etc/init.d/networking restart ------

bash: sudo/etc/init.d/networking: No such file or directory
paul@pavilian:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
paul@pavilian:~$ sudo gedit /etc/network/interfaces
Password:

(gedit:5015): Gdk-WARNING **: locale not supported by Xlib

(gedit:5015): Gdk-WARNING **: cannot set locale modifiers

-------- then in separate window ---------

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

----- paul@pavilian:~$ lspci ------

0000:00:00.0 Host bridge: Intel Corporation 82810 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corporation 82810 CGC [Chipset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
0000:01:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 04)
0000:01:0e.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 40)

------ paul@pavilian:~$ sudo lshw ------

Password:
pavilian
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 190MB
     *-cpu
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.3
          size: 550MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 128KB
     *-pci
          description: Host bridge
          product: 82810 GMCH [Graphics Memory Controller Hub]
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 82810 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             size: 64MB
             width: 32 bits
             clock: 66MHz
             capabilities: vga bus_master cap_list
             configuration: driver=i810_smbus
             resources: iomemory:f8000000-fbffffff iomemory:f4000000-f407ffff irq:3
        *-pci
             description: PCI bridge
             product: 82801AA PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-usb
                description: USB Controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: b
                bus info: pci@01:0b.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: uhci bus_master
                configuration: driver=uhci_hcd
                resources: ioport:3000-301f irq:11
              *-usbhost
                   product: UHCI Host Controller
                   vendor: Linux 2.6.15-23-386 uhci_hcd
                   physical id: 1
                   bus info: usb@2
                   logical name: usb2
                   version: 2.06
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s                 *-usb
                      description: Mouse
                      product: USB Mouse
                      vendor: 2D Mouse
                      physical id: 1
                      bus info: usb@2:1
                      version: 0.00
                      capabilities: usb-1.00
                      configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
           *-network
                description: Ethernet interface
                product: 21x4x DEC-Tulip compatible 10/100 Ethernet
                vendor: Davicom Semiconductor, Inc.
                physical id: e
                bus info: pci@01:0e.0
                logical name: eth0
                version: 40
                serial: 00:08:a1:90:cd:49
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tulip driverversion=1.1.13 multicast=yes
                resources: ioport:3400-34ff iomemory:f4100000-f41000ff irq:3
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801AA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801AA IDE
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1800-180f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: SAMSUNG SV2042H
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: PK100-21
                   serial: 0347J1FR401008
                   size: 19GB
                   capacity: 19GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma2 smart=on
                 *-volume:0
                      description: W95 FAT32 (LBA) partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 9460MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 9499MB
                      capabilities: primary
                 *-volume:2
                      description: Linux swap / Solaris partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 502MB
                      capabilities: primary nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: CD-R/CD-RW writer
                   product: CD-W54E
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.1B
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb
             description: USB Controller
             product: 82801AA USB
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1820-183f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-23-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: 82801AA SMBus
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             resources: ioport:1810-181f irq:9
        *-multimedia
             description: Multimedia audio controller
             product: 82801AA AC'97 Audio
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH
             resources: ioport:1200-12ff ioport:1300-133f irq:9

---

### Post by wieman01 on 2006-10-19
Ok, it seems that your card has not been recognized. Can you now tell me what wireless adapter you are using e.g. USB, brand, model no. etc.? Is it this one: "CNET PRO 200 etho"?

We may have to use "ndiwrapper" so please get the latest driver for your card.

---

### Post by dmizer on 2006-10-19
the cnet pro 200 is a wired ethernet adapter, so you won't need ndiswrapper or the latest drivers.  to me, everything looks like it should be working, you're just not getting a dhcp lease.

are the lights on your network adapter lit (indicating a physical link)?  if not, you might consider trying a different network cable, or checking to make sure that the cable is plugged in tightly.  might also try a different port on your router.

also, on a whim, post what happens when you do this:
```
sudo /etc/init.d/networking restart
```

ps. i am no linux god (or even remotely close to a guru for that matter).  i only started using ubuntu for the first time in march of this year, so i'm very familiar with the frustration of trying to make something work.  i also have many unresolved and unanswered threads that drive me nuts.

give it time and be patient.  but most of all remember that linux is not windows, and will not function like windows.

---

### Post by wieman01 on 2006-10-19
Oh d@#! it... you're right, it's wired. I'll shut up then. Have mistaken the thread. 

In that case everything looks fine indeed. I think this has more to do with the network settings as in "/etc/network/interfaces" rather than the hardware recognition. "ls*" say that the hardware is installed. Let's see what the mentioned command ("sudo /etc/init.d/networking restart") does.

---

### Post by platinummonkey on 2006-10-19
oops, :P sorry (see below) i moved it to a new thread. thanks, and good luck to donaldduck!

---

### Post by wieman01 on 2006-10-19
Hello Platinummonkey, 

I understand that you are excited about it, but hijacking a thread is not exactly what is considered polite in here. Please either follow this thread or open a new one. You can send us the link anytime by email, etc.

---

### Post by donald52duck on 2006-10-20
wieman01 

all lites on both card and router say there is a connection......
here's what ifconfig says when using the CD:

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:A1:90:CD:49
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe90:cd49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2315 (2.2 KiB)  TX bytes:2139 (2.0 KiB)
          Interrupt:3 Base address:0x3400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)



ubuntu@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

Here's the additional info:

------ paul@pavilian:~$ sudo /etc/init.d/networking restart ------

 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:08:a1:90:cd:49
Sending on   LPF/eth0/00:08:a1:90:cd:49
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:08:a1:90:cd:49
Sending on   LPF/eth0/00:08:a1:90:cd:49
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

---

### Post by wieman01 on 2006-10-20
Ok, this suggests that you have established a connection already:
> buntu@ubuntu:~$ route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.1.0 * 255.255.255.0 U 0 0 0 eth0
default 192.168.1.1 0.0.0.0 UG 0 0 0 eth0
Can you ping your router:
> ping 192.168.1.1
What does the system return?

That done also post the contents of this file please:
> sudo gedit /etc/network/interfaces

---

### Post by dmizer on 2006-10-22
> No DHCPOFFERS received.
No working leases in persistent database - sleeping.
this shows that you are not getting connected.

your card is working, but it's not pulling a dhcp lease.

try going to networking and setting your ip statically.  just use 192.168.1.101 (same as what your computer uses when connecting with the live cd).

if you can browse then, the problem is with dhcp, but i can't imagine what would be different between your live cd and the full install.

also ... make a backup of your interfaces:
```
sudo cp /etc/network/interfaces /etc/network/interfaces_old
```
then edit your interfaces to remove all entries except for your eth0:
```
gksudo gedit /etc/network/interfaces
```
save, exit, and do sudo /etc/init.d/networking restart again. (or reboot).

---

