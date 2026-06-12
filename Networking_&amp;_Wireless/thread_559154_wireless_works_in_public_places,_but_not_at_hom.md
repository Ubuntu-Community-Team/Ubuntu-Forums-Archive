---
title: "wireless works in public places, but not at hom"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by jplowman on 2007-09-24
home, that is. ;)

My first foray outside the absolute beginner talk forum... be gentle.

I have been trying to fix this problem for several weeks, and lurking on wireless networking threads. Most recently I reinstalled Xubuntu, but the problem persists. I'm turning this one over to the forum.

The issue: I can't for love or money connect to my house's wireless router. I can see the network if I type "sudo iwlist eth1 scan" in terminal. But "sudo dhclient eth1" does not connect me. I can connect to wireless networks using the same command at my local library and gelato shop. And another computer at home (Mac) can connect to the wireless router, so it's working. I've just been connecting with an ethernet cable to the router ("sudo dhclient eth0") but the cable's about two feet long and I would really, really like to ditch it.

The computer: Toshiba Libretto L5 080TNKW
The router: Netgear WGT624 v3
The network card: ??? help me find out!

In case it helps, here is the output of some commands:

lspci:
```
00:00.0 Host bridge: Transmeta Corporation LongRun Northbridge (rev 02)
00:00.1 RAM memory: Transmeta Corporation SDRAM controller
00:00.2 RAM memory: Transmeta Corporation BIOS scratchpad
00:04.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:0a.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)
00:0b.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
00:14.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
```

lshw:
```
jon-libretto              
    description: Notebook
    product: Libretto L5/TNKW
    vendor: TOSHIBA
    version: PAL5080TNKW
    serial: 42063584J
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=4EAC9B80-57AA-11D6-8010-D51342063584
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: 0000000000
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.40 (06/11/2002)
          size: 128KB
          capacity: 448KB
          capabilities: pci pcmcia upgrade shadowing vesa cdboot bootselect pcmciaboot edd acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Transmeta(tm) Crusoe(tm) Processor TM5800
          vendor: GenuineTMx86
          physical id: 4
          bus info: cpu@0
          version: 5.4.3
          slot: IC3
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          clock: 66MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr cx8 sep cmov mmx longrun lrti up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: CPU Transmeta
             size: 128KB
             capacity: 128KB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: CPU Transmeta
             size: 512KB
             capacity: 512KB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 81
          slot: System board or motherboard
          size: 512MB
          capacity: 512MB
        *-bank:0
             description: SDRAM Synchronous
             physical id: 0
             slot: System 0
             size: 256MB
             width: 64 bits
        *-bank:1
             description: SDRAM Synchronous
             physical id: 1
             slot: MICRO DIMM 0
             size: 256MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: LongRun Northbridge
          vendor: Transmeta Corporation
          physical id: ffa00000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=64
          resources: iomemory:ffa00000-ffafffff
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: SDRAM controller
             vendor: Transmeta Corporation
             physical id: 0.1
             bus info: pci@00:00.1
             version: 00
             width: 32 bits
             clock: 33MHz (30.3ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: BIOS scratchpad
             vendor: Transmeta Corporation
             physical id: 0.2
             bus info: pci@00:00.2
             version: 00
             width: 32 bits
             clock: 33MHz (30.3ns)
             configuration: latency=0
        *-display
             description: VGA compatible controller
             product: Radeon Mobility M6 LY
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@00:04.0
             version: 00
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=64 mingnt=8
             resources: iomemory:f0000000-f7ffffff ioport:ed00-edff iomemory:ff9f0000-ff9fffff irq:11
        *-multimedia
             description: Multimedia audio controller
             product: M5451 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 6
             bus info: pci@00:06.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ALI 5451 latency=64 maxlatency=24 mingnt=2
             resources: ioport:1000-10ff iomemory:30020000-30020fff irq:11
        *-isa
             description: ISA bridge
             product: M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-system UNCLAIMED
             description: System peripheral
             product: SD TypA Controller
             vendor: Toshiba America Info Systems
             physical id: a
             bus info: pci@00:0a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: iomemory:30023000-300231ff irq:255
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: b
             bus info: pci@00:0b.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=64
             resources: iomemory:30021000-30021fff irq:11
           *-network
                description: Wireless LAN Card
                product: Version 01.01
                vendor: TOSHIBA
                physical id: 0
                slot: Socket 0
                resources: irq:11
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: e
             bus info: pci@00:0e.0
             logical name: eth0
             version: 10
             serial: 00:00:39:92:f0:f5
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.3 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
             resources: ioport:ea00-eaff iomemory:ff9eff00-ff9effff irq:7
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: 10
             bus info: pci@00:10.0
             version: c3
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ALI15x3_IDE latency=64 maxlatency=4 mingnt=2
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:e9f0-e9ff irq:255
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: TOSHIBA MK2003GAH
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: AM.05 A
                   serial: 32SW2257A
                   size: 18GB
                   capacity: 18GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma4 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 5632MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Hidden W95 FAT32 (LBA) partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 2008MB
                      capabilities: primary hidden
                 *-volume:2
                      description: Extended partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      size: 11GB
                      capacity: 11GB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume:0
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 486MB
                         capabilities: nofs
                    *-logicalvolume:1
                         description: Linux filesystem partition
                         physical id: 6
                         logical name: /dev/hda6
                         capacity: 5859MB
                    *-logicalvolume:2
                         description: Linux filesystem partition
                         physical id: 7
                         logical name: /dev/hda7
                         capacity: 5083MB
        *-bridge
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=ali1535_smbus latency=0
        *-pcmcia:1
             description: CardBus bridge
             product: ToPIC100 PCI to Cardbus Bridge with ZV Support
             vendor: Toshiba America Info Systems
             physical id: 12
             bus info: pci@00:12.0
             version: 33
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=0 maxlatency=5 mingnt=128
             resources: iomemory:30022000-30022fff irq:10
        *-usb
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 14
             bus info: pci@00:14.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: iomemory:ff9ee000-ff9eefff irq:6
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
  *-battery
       description: Lithium Ion Battery
       product: 3URFTW
       vendor: TOSHIBA
       physical id: 1
       version: 04/12/02
       serial: 0000000411
       slot: 1st Battery
       configuration: voltage=10.8V
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:5d:4b:cc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.10 link=no multicast=yes wireless=IEEE 802.11b
```

sudo iwlist eth1 scan: ("Plum" is the network I want to connect to)
```
eth1      Scan completed :
          Cell 01 - Address: 00:18:4D:57:BB:88
                    ESSID:"Plum"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Signal level:-12 dBm  Noise level:-97 dBm
                    Encryption key:on
          Cell 02 - Address: 00:18:39:F5:1B:25
                    ESSID:"gibby"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:-65 dBm  Noise level:-62 dBm
                    Encryption key:on
```

sudo dhclient eth1:
```
There is already a pid file /var/run/dhclient.pid with pid 6742
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:02:2d:5d:4b:cc
Sending on   LPF/eth1/00:02:2d:5d:4b:cc
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

What in tarnation is going on here? Please, please help.

---

### Post by ogara0c9 on 2007-09-24
Right off the bat, I think this is an encryption problem since your encryption key is on (iwlist).  Using dhclient at the public sites would work if you don't have to specify a security code.  dhclient just checks for information it needs to connect to a network.  

For Xubuntu, go to your menu (right click on desktop), system -> networking.  From here you should be able to click on your wireless device (eth1) and select <properties>.  From here you can enter the network name (Plum) and your security information for the router.  May have to check your Mac machine for its settings.  Hope this works.

---

### Post by jplowman on 2007-09-24
This sounds right, because even at home I can sometimes connect to some neighbor's wireless network, just not my own.

However, changing the settings in Applications>System>Network doesn't seem to do any good. I input the network name and password, and I've tried both WEP key (hexadecimal) and WEP key (ascii) and the computer still has no internet access when the ethernet cable is unplugged.

Might there be a setting I could change at the router to try to address this?

The Mac seems to have the same network name and password that I'm using, but I don't know enough about Macs to figure out much beyond that.

Do you think it's a problem that no "network controller" shows up when I type "lspci"?

Thanks for helping! Frustrating problem.

---

### Post by ogara0c9 on 2007-09-25
Are you still getting the same error message if you do a <sudo dhclient> on eth1?

The only other suggestion to make at this time is to put in your network name and password (most likely hexadecimal).  After closing, unplug your ethernet cable and type <sudo /etc/init.d/networking restart>.  This will basically start the process that occurs during startup over again.  Not sure if it will do any better than using dhclient, but it couldn't hurt.

The ethernet controller you have installed should be good.  I don't have a "network controller" under my pci devices either.  I'm basically working through this with my desktop configuration.

The thing to do with the router is to maybe just take a peek at its settings.  I'd be cautious about changing things around too much though :)

Edit: change your gateway preference as well under the main networking window if you haven't already

---

### Post by pxwpxw on 2007-09-26
**jplowman**

Also, it is just possible that the home wireless router is set up with Media Access Control, requiring the ethernet id to be added.
(like 00:02:2d:5d:4b:cc ). I use that system, but not that router.
That would only make sense if you had not accessed the router before from that computer wireless card, but it seems to fit the other symptoms.

---

### Post by jplowman on 2007-09-26
I do meet those criteria - I've never been able to access the router with this computer.

Where can I find the ethernet code, and how would I add it?

---

### Post by pxwpxw on 2007-09-27
> **jplowman said:**
> I do meet those criteria - I've never been able to access the router with this computer.

Where can I find the ethernet code, and how would I add it?

It is the Media Access Control (MAC) hardware address for the wireless card, ifconfig will show it - example
```

~$ ifconfig 
ath0      Link encap:Ethernet  HWaddr 00:1A:56:38:64:56  

```
But you will have to access your wireless router configuration to see where to add it (assuming access control is indeed the problem). Sorry I dont know how you do that with your router, I have an Apple Airport Express base - it uses a wireless admin utility in  Mac OSX on one computer - if you are using windows you probably have the equivalent there somewhere.

---

### Post by NotoriousTF on 2007-09-27
I recently had the very same problem with my wireless connection. After installing a new wireless router I found that wireless via Ubuntu wouldn't work - the network was visible but it just wouldn't connect (alas it would via XP). I'm always using the wireless network in college without a problem. 
I decided to rid myself of "*network-manager*", and installed "*RutilT*", which works perfectly at home and in college. So maybe changing to another program for your wireless connection may help?

---

### Post by jplowman on 2007-09-28
pxwpxw-

Well, I found the computer's MAC address:

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:00:39:92:F0:F5  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fe92:f0f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3931373 (3.7 MiB)  TX bytes:659230 (643.7 KiB)
          Interrupt:7 Base address:0x4f00 

eth1      Link encap:Ethernet  HWaddr 00:02:2D:5D:4B:CC  
          inet6 addr: fe80::202:2dff:fe5d:4bcc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:9441 (9.2 KiB)
          Interrupt:11 Base address:0x100 

eth1:avah Link encap:Ethernet  HWaddr 00:02:2D:5D:4B:CC  
          inet addr:169.254.6.156  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

However, when I accessed the router configuration "webpage", it seemed to indicate that Media Access Control was NOT on (the box is unchecked and instructions on the right seem to indicate it's disabled by default). Check out the screenshot at the bottom, see if you agree. If so, I guess we can at least rule that one out.

NotoriousTF-

I am going to try the wireless network manager you recommended, if my next move doesn't solve the problem...

...which brings me to this:

I read somewhere that my laptop (Toshiba Libretto L5, the one with built-in wireless card) supports WEP. This leads me to wonder, does it NOT support WPA? If so, that could be the problem - our router has until now been using WPA, as I discovered when I accessed the router configuration "web page." 

Any thoughts on this? My next move is going to be to try and re-configure the router to use WEP encryption instead of WPA (I know it's less secure, but it will at least tell me if that's the problem). I can't right at the moment because my flatmates are also online and I don't want to break their connection. But in a little while I think I'll try that.

Thanks so much for helping me out, already we've made much progress that I never would have been able to do by myself. Hopefully we'll track this one down. Really much appreciated.

---

### Post by pxwpxw on 2007-09-28
Yes  I would agree try WEP (or even no security) just to resolve it, very likely you got the answer there. (I just use WEP but I am out in the wilderness)

---

### Post by jplowman on 2007-09-28
Blast it... I changed security to WEP and that doesn't work either. Not sure if I am supposed to put in the "passphrase" or the hexadecimal key as my password, but I tried both and there's still no connection.

Next going to try the RutilT suggested by NotoriousTF...

Ogara0c9:  sorry, let this one get by me...

> **ogara0c9 said:**
> change your gateway preference as well under the main networking window if you haven't already

Not quite sure where to change this, perhaps the Xubuntu networking preferences GUI is slightly different from the Ubuntu. (It seems a bit buggy... for instance there are buttons at the top to save different networking configurations, but after clicking the "save" button and putting in a name, I still don't seem to be able to switch between different location configurations, i.e. it didn't really save...)

Having to crouch over the router tethered to a 2-ft. ethernet cable is such a bummer. This one may end up "resolved" when I go buy a 20-ft. cable... seems like such a shame to let it come to that though.

---

### Post by lisati on 2007-09-28
I, too, would suggest WEP in conjunction with MAC access control. This seems to suit the setup I have at home (a desktop with a wired connection to a combo wifi/wired router which supports both WEP anWPA, a Toshiba Satellite A100 laptop which supports WEP, and an older Win98SE desktop with a wireless adapter hooked in via USB)

EDIT: I also initially used a wired connection for my laptop until I got the WiFi figured out.

---

### Post by jplowman on 2007-09-28
Update... the news just seems to continue being bad.

Pxwpxw - I followed your suggestion and turned encryption off entirely on the router: no WEP, no WPA. 

It now LOOKS like I am able to connect wirelessly:

sudo dhclient eth1:

```
There is already a pid file /var/run/dhclient.pid with pid 6226
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:02:2d:5d:4b:cc
Sending on   LPF/eth1/00:02:2d:5d:4b:cc
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.104 -- renewal in 37432 seconds.
```

However, web pages don't load and "sudo apt-get update" does not successfully connect to the update servers, so the connection seems to be somehow illusory.

I love so many things about Linux, most of all the power of the command line, being able to navigate everything without the mouse. But this problem is making me nostalgic for the good old Windows XP wireless network manager... open it up, there's the network, type the password, and forget about it.

Hard to believe a wireless connection could be so intractable.

Could it be a problem with my driver? On many of the wireless problem threads, people ask what the wireless card model is. I don't even know what mine is, not quite sure how to find out...

NotoriousTF - RutilT seems to be a package for Gutsy, unfortunately I'm running Feisty. Any other wireless managers recommended?

---

### Post by pxwpxw on 2007-09-28
**jplowman**

Well that's progress by elimination.
You are getting DHCP to work according to your post above, it may then just be a problem with DNS blocked by firewall or not configured,

From your "lshw " it is a pcmcia TOSHIBA Wlan card, so it might need specific pcmcia/wireless support modules, but thats about all I can suggest there. I dont have any pcmcia cards.
```

*-pcmcia:0
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: b
             bus info: pci@00:0b.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=64
             resources: iomemory:30021000-30021fff irq:11
           *-network
                description: Wireless LAN Card
                product: Version 01.01
                vendor: TOSHIBA
                physical id: 0
                slot: Socket 0
                resources: irq:11

```

I note you have xubuntu, same here, works for me (network manager = Applictions-System-Network) plus attention to firewall settings.

I have tried to setup networks from the command line and failed, usually have to resort to complete restart a few times to get a configuration change established automatically by the desktop applications. Also had to disable the wired connection to get the wireless established as the internet connection.

A network reconfiguration from scratch is often best to clear problems, you need a good howto for your system or someone to go through the configuration with you.

Post /etc/network/interfaces, may show something more.

If you have firestarter, check its configuration wizard.

Thats about all I can suggest for now, hope someone else can do better.

---

### Post by jplowman on 2007-09-28
> **pxwpxw said:**
> **jplowman**
 Also had to disable the wired connection to get the wireless established as the internet connection.


Well, what do you know? That was exactly the problem.
It turned out not only did I have to enable the wireless connection, I had to disable the wired connection in Xubuntu's network manager.

Once that allowed me to connect, I enabled WEP security to see if that would work, and it did. 

WPA security didn't work - Xubuntu's network manager wireless dialog gave me no password options other than WEP-ascii and WEP-hexadecimal (I used hexadecimal, so the password was 26 characters). I figure the Toshiba Wlan card doesn't support WPA.

lisati - I then followed your suggestion. Since I can't get WPA encryption, I decided to enable Media Access Control. I gave the router the MAC addresses of the two computers used on the wireless network. I guess in theory this won't allow any other machine on our network.

I appreciate everyone's suggestions deeply. I've been tethered to the router by a 2-ft cable for weeks, and within about a day, the forum came through and gave me the tools to get a real wireless connection. I can't tell you how much of a relief this is. Halle freakin lujah!

---

### Post by NotoriousTF on 2007-09-28
I also tried removing any form of security from my wireless router, but that didn't work for me either. Anyway, I myself am a Feisty user, and am having no problems with RutilT with my WEP enabled. 
I used this how-to [[COLOR="DarkOrange"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt") by sulligogs so get it all set-up. It worked straight away, like a charm!

Hope this helps!

Whops! Didn't read the very end of your last post. Glad you got it sorted, I know how frustrating that problem can be!

---

