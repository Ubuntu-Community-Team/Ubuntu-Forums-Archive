---
title: "Stupid question: Wifi card needs 300 Mhz CPU, I have a 266 Mhz CPU..."
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by Majin Zero on 2007-03-15
...

Xubuntu detects the wifi card, yet it can't seem to find my wireless network.

would the lower then required CPU be the cause of the issue?

---

### Post by chili555 on 2007-03-15
I am really surprised the CPU police haven't shown up yet! 

Seriously, linux shines on older equipment. I am sure we can get it going just fine, well, as fine as a 266 can go.

Tell us more details:```
iwconfig
sudo iwlist <your_wireless_interface_maybe_eth1> scan
```

Any encryption? WEP, WPA, etc.?

We'll get it goin'.

---

### Post by Majin Zero on 2007-03-15
no encription, just MAC filtering, but I already got the wifi card's MAC into the allow list

---

### Post by Majin Zero on 2007-03-15
tried that command

sudo iwlist eth0 scan

interface doesn't support scanning : no such device


and I was able to do other commands like retry to eth0 so....it...doesn't support scanning?

---

### Post by jglen490 on 2007-03-15
You may not be interfacing via eth0, but you may be using wlan0 or something else.  In a terminal enter:

```
ifconfig
```

---

### Post by Majin Zero on 2007-03-15
> **jglen490 said:**
> You may not be interfacing via eth0, but you may be using wlan0 or something else.  In a terminal enter:

```
ifconfig
```

I'm computer savvy but a 'nix noob, so I don't quite understand all this:

lo           Link encap:Local Loopback
             INET ADDR:127.0.0.1  Mask 255.0.0.0
             inet6 addr: ::1/128 Scope:Host
             UP LOOPBACK RUNNING MTU: 16436  Metric:1
             [too much to type everything is a 0 here]

---

### Post by Majin Zero on 2007-03-15
also iwconfig shows my wireless card as eth0

---

### Post by Majin Zero on 2007-03-15
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

this site says I need a fix...but the fix link is broken

:/

 Linksys
	

WPC54G (ver 1.2)
	

Broadcom (BCM4306 rev3)

---

### Post by Majin Zero on 2007-03-15
fix is here:

[http://bcm43xx.spugna.org/index.php?topic=29.0](http://bcm43xx.spugna.org/index.php?topic=29.0)


but....page isn't loading for me...

---

### Post by jglen490 on 2007-03-15
So far, so good.  Try to follow what I'm doing below and maybe we can get it going.  I've added some comments into the CODE box to help clear things up a bit.  Ny input commands are in bold:

```
john@john-laptop:/etc/network$ **ifconfig**

*This should show all your interface devices. I have both an ethernet (disconnected) and wifi (wlan0).*

eth0      Link encap:Ethernet  HWaddr 00:90:27:97:80:6A
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0D:0B:D0:81:6C
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:bff:fed0:816c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2596 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2252362 (2.1 MiB)  TX bytes:319344 (311.8 KiB)
          Interrupt:11 Memory:22000000-22002000

john@john-laptop:/etc/network$** lshw**

*This will list all your hardware.  Yes you can filter it, as was shown in another post.*

WARNING: you should run this program as super-user.
john-laptop
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 383MB
     *-cpu
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 6.8.3
          size: 550MHz
          capacity: 550MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse cpufreq
       
*A whole bunch of stuff here.  The important output is the network info below.*

        *-network
             description: Ethernet interface
             product: 82557/8/9 [Ethernet Pro 100]
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@00:03.0
             logical name: eth0
             version: 09
             serial: 00:90:27:97:80:6a
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e100 multicast=yes
             resources: iomemory:e8120000-e8120fff ioport:1800-183f iomemory:e8100000-e811ffff irq:11

        *More stuf.*

     *-network
          description: Wireless interface
          product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
          vendor: Broadcom Corporation
          physical id: 0
          bus info: pci@02:00.0
          logical name: wlan0
          version: 02
          serial: 00:0d:0b:d0:81:6c
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master ethernet physical wireless
          configuration: broadcast=yes driver=ndiswrapper ip=192.168.1.103 multicast=yes wireless=IEEE 802.11g
          resources: iomemory:22000000-22001fff irq:11
john@john-laptop:/etc/network$ **iwconfig**

*This is network configuration info from the viewpoint of a wifi connection, if one exists.*

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Aardvark"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:23:13:21
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-59 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

john@john-laptop:/etc/network$ **lspci -v**

*This is another view of hardware from the viewpoint of PCI devices.*

0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 128
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: f0000000-f7ffffff
        Prefetchable memory behind bridge: 28000000-280fffff

0000:00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
        Subsystem: IBM Thinkpad T20
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 22000000-23fff000
        I/O window 0: 00001400-000014ff
        I/O window 1: 00001c00-00001cff
        16-bit legacy interface ports at 0001

0000:00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
        Subsystem: IBM Thinkpad T20
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50100000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 24000000-25fff000 (prefetchable)
        Memory window 1: 26000000-27fff000
        I/O window 0: 00002000-000020ff
        I/O window 1: 00002400-000024ff
        16-bit legacy interface ports at 0001

0000:00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 09)
        Subsystem: Intel Corporation EtherExpress PRO/100+ MiniPCI
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at e8120000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 1800 [size=64]
        Memory at e8100000 (32-bit, non-prefetchable) [size=128K]
        Expansion ROM at 28100000 [disabled] [size=1M]
        Capabilities: <available only to root>

0000:00:03.1 Serial controller: Xircom Mini-PCI V.90 56k Modem (prog-if 02 [16550])
        Subsystem: Intel Corporation: Unknown device 2408
        Flags: medium devsel, IRQ 11
        I/O ports at 1840 [size=8]
        Memory at e8121000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
        Subsystem: IBM: Unknown device 0153
        Flags: bus master, slow devsel, latency 64, IRQ 11
        Memory at e8122000 (32-bit, non-prefetchable) [size=4K]
        Memory at e8000000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: <available only to root>

0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        I/O ports at 1850 [size=16]

0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 1860 [size=32]

0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
        Flags: medium devsel, IRQ 9

0000:01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11) (prog-if 00 [VGA])
        Subsystem: IBM ThinkPad T20
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at f0000000 (32-bit, non-prefetchable) [size=128M]
        Expansion ROM at 28000000 [disabled] [size=64K]
        Capabilities: <available only to root>

0000:02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Melco Inc: Unknown device 0342
        Flags: bus master, fast devsel, latency 64, IRQ 11
        Memory at 22000000 (32-bit, non-prefetchable) [size=8K]

john@john-laptop:/etc/network$ **ndiswrapper -l**

*This will show if ndiswrapper is loaded and the nature of the driver present, if any*

Installed ndis drivers:
netg54s         driver present, hardware present

john@john-laptop:/etc/network$ **iwlist wlan0 scan**

*This will show what AP your wifi detetcts, if your connection is active and any APs are in the vicinity.*

wlan0     Scan completed :
          Cell 01 - Address: 00:11:95:6B:AC:34
                    ESSID:"GTFO"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-78 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:14:BF:00:F5:4E
                    ESSID:"Ivanhoe"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:0/100  Signal level:-83 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:16:B6:23:13:21
                    ESSID:"Aardvark"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-62 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    Extra:wpa_ie=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

john@john-laptop:/etc/network$                    
```

This all will show what hardware you have for networking, if any drivers are present, and perhaps if there are conflicts or if the driver is present but doesn't work.  If you brought in ndiswrapper, and an appropriate set of Windoze drivers, and if the driver module was installed, and your network AP is setup for your wifi to communicate to, and the stars are in the right position :) , then all those entries should look something like mine.  If not, then we have a place to start.  If possible, copy your terminal entries into the CODE tag (# symbol in the thread reply box).  Or copy to a text file and migrate that over to a Windows box, or whatever you can do to get that actual info here.

---

### Post by Majin Zero on 2007-03-15
I'll find a way to get that copy pasted here if necessary.

I'm not trying to be difficult but I dunno how to find if I have that ndiswrapper, thingy.

Also; The compatibility website, as I said says I need a firmware update on the card to get it to work. I posted a link above. Does anyone know how to go about doing that? Or is there a mirror to that link?

---

### Post by jglen490 on 2007-03-15
The simplest solution to whether you have ndiswrapper or not, is to simply type it into a terminal:

```
ndiswrapper
```

It will either come back with a response, or you will get an message that the command cannot be found.

As for the firmware approach, that's getting better, too.  But it something where you need to follow the steps very carefully.  Again, not impossible.

There are web pages that list wifi hardware that works either "out of the box" with working, native Linux drivers, or nearly so.  The ndiswrapper solution is not always the only way, the same with the firmware cutter solution.

---

### Post by Majin Zero on 2007-03-15
I don't have ndiswrapper

Command not found.

Would anyone know of this new firmware I need, and where I can get it?

---

### Post by Majin Zero on 2007-03-15
found this guide:

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)


Gonna try that when I pic up a LAN card.

---

### Post by Majin Zero on 2007-03-16
last link works like a charm.

---

