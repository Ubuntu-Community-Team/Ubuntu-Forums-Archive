---
title: "Reinstalled intrepid 8.10, wireless problem."
date: 2009-02-25
forum: New to Ubuntu
---

### Post by Elizabeth-dane on 2009-02-25
Howdy! I recently had a hard disk problem with my laptop and had to reinstall intrepid. Everything is fine aside from one tiny detail, that being the wireless connection. 

Before I had my problem I could click the network icon and got a list of available networks in range, then just click to connect to the one I wanted, this was very much like the windows system and made it very easy to connect when on the move. Now however this whole thing seems to have vanished. The system auto detected my wireless card and installed the broadcom drivers which I believe are the same as the original ones, but when I click the network icon all I get is:

Wired Network
Auto eth 0
Wireless Network (greyed out)

VPN Connections
Connect to hidden wireless network
Create new wireless network

I've tried to configure the connection manually but it seems to connect to the router for just about a second then drops off. I'm pretty lost now. Any help? :guitar:

---

### Post by yeats on 2009-02-25
> Howdy! 

Howdy to you, and welcome :-).

What model (chipset) is your wireless card?  For troubleshooting purposes, please open a terminal window and do the following commands, then post the output here

```
ifconfig
cat /etc/network/interfaces
lspci -v
```

In your previous installation, did the wireless card work "out of the box", or did you have to go through this before?

---

### Post by Elizabeth-dane on 2009-02-25
Ok here we go...


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:6d:d0:f9  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe6d:d0f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10874 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13099481 (13.0 MB)  TX bytes:1292968 (1.2 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:c8:44:b8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-C8-44-B8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback




:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: Dell Device 01c9
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Dell Device 01c9
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at eff8 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Dell Device 01c9
	Flags: bus master, fast devsel, latency 0
	Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
	Subsystem: Dell Device 01c9
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: dfc00000-dfdfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
	Subsystem: Dell Device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bf80 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
	Subsystem: Dell Device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at bf60 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
	Subsystem: Dell Device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at bf40 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
	Subsystem: Dell Device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at bf20 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20)
	Subsystem: Dell Device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at b0000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	Memory behind bridge: dfb00000-dfbfffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
	Subsystem: Dell Device 01c9
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Device 01c9
	Flags: bus master, fast devsel, latency 64, IRQ 18
	Memory at dfbfc000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: b44
	Kernel modules: b44

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: Dell Device 0005
	Flags: bus master, fast devsel, latency 64, IRQ 17
	Memory at dfbfe000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb



Hope that's what you were after, I also hope it means significantly more to you than it does to me! 

:p

---

### Post by Elizabeth-dane on 2009-02-25
I should add that in the previous installation the whole setup was automatic, the system detected the card, installed the drivers and was up and running in minutes.

---

### Post by detroit/zero on 2009-02-25
I'm assuming you're using straight Ubuntu and not k or x variants... But have you tried right-clicking on the nm-applet (the place where the drop-down menu of ap's appears from) and selecting "enable wireless"?

Sometimes I disable that option and forget to turn it back on and end up chasing my tail until I figure it out.

---

### Post by yeats on 2009-02-25
> Hope that's what you were after, I also hope it means significantly more to you than it does to me! 

It is very helpful for troubleshooting, thank you.  You will learn all this too, if only getting through this sort of thing. :-)

The "ifconfig" command shows the currently detected network _i_nter_f_aces on your system (it's the same as the "ipconfig" command in the Windows cmd window).  A working connection shows an IP address and transmission stats:

```
eth0 Link encap:Ethernet HWaddr 00:15:c5:6d:d0:f9
**inet addr:192.168.1.68 Bcast:192.168.1.255 Mask:255.255.255.0** - *your IP*
inet6 addr: fe80::215:c5ff:fe6d:d0f9/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:10874 errors:0 dropped:0 overruns:0 frame:0  - *stats*
TX packets:8155 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:13099481 (13.0 MB) TX bytes:1292968 (1.2 MB)
Interrupt:18 
```

I can see that your "wlan0" interface is detected and up:

```
wlan0 Link encap:Ethernet HWaddr 00:14:a5:c8:44:b8
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

```

but it has no IP and the stats are all at 0.

The "cat /etc/network/interfaces" command prints (con_cat_enates - or appends) the content of the /etc/network/interfaces file.  That file contains information about how each interface is brought up by the system.  

```
auto lo
iface lo inet loopback
```

These lines define your "loopback" interface.  I was looking for something here about your other interfaces, but it's okay that they are not here.  The last command lists the information about what hardware your computer is running.  I was looking for this line (and found it):

```
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

Okay, now that we know your system sees the Broadcom card, and that the card is "up", try this command, which will manually request an IP from your router using the wireless card (you'll want to disconnect your Ethernet first):

```
sudo dhclient wlan0
```

Please post the output here and we'll go from there. :-)

---

### Post by yeats on 2009-02-25
Of course - listen to detriot/zero first - frontend solutions are always better. :-)

---

### Post by Elizabeth-dane on 2009-02-25
> **detroit/zero said:**
> I'm assuming you're using straight Ubuntu and not k or x variants... But have you tried right-clicking on the nm-applet (the place where the drop-down menu of ap's appears from) and selecting "enable wireless"?

Sometimes I disable that option and forget to turn it back on and end up chasing my tail until I figure it out.

Hi there, it is indeed the straight Ubuntu version. I tried enabling / disabling the wireless several times to see if maybe something would kick in but no joy so far. It's bizarre how lst time it just all worked fine. It's driving me nuts sitting here by the router with the cable plugged in, I really need to get up to my office and get some work done! :p

---

### Post by Elizabeth-dane on 2009-02-25
This stuff is pretty heavy! Here's what I got... 



sudo dhclient wlan0:


 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:a5:c8:44:b8
Sending on   LPF/wlan0/00:14:a5:c8:44:b8
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

:p

---

### Post by yeats on 2009-02-25
This is starting to sound like a router issue.  Your router may be denying your new installation access because you're using the same MAC address with a different system.  Have you checked this possibility?  It looks like everything is working as it should otherwise.

If you have time, you could also try to connect at a wireless hotspot, just to prove to yourself that it's not your laptop that's the problem. :-)


EDIT:
Wait - never mind - you said it was greyed out.  Hmm.  I don't know how NetworkManager works, exactly, but it sounds like the problem is there.  Sorry for not remembering that

---

### Post by Elizabeth-dane on 2009-02-25
Hmmm, I've tried restarting my router but it didn't help. The thing I used to have is this:

[IMG]http://i70.photobucket.com/albums/i95/victorcrane/thing.png[/IMG]

And this is what I no longer have. On my first installation of ubuntu this was what I got when I clicked on the network icon by the clock and it always showed six networks which belong to myself and my neighbours. As of yesterday morning all of these networks were still running and still are but now I've reinstalled I don't get this at all. I tried setting it up manually again but either I'm doing it wrong or something else is amiss.

How awfully frustrating!

---

### Post by Elizabeth-dane on 2009-02-25
Somebody somewhere must know, having looked around the net I can see there are a very large number of people who have had this problem but thus far I'm unable to find any solution. 

It makes absolutely no sense that it was working perfectly before and now not at all. If I could only ask the damn thing to just search for wireless networks, but as I said earlier 'wireless networks' is greyed out and I can't do anything at all with it. 

My ps3, desktop and work laptop are still running perfectly on the router. 

:confused::confused:

---

### Post by Elizabeth-dane on 2009-02-25
Been trying a few more things, followed the official guidance for wireless troubleshooting, I get this outcome from sudo lshw -c network

laptop:~$ sudo lshw -c network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:6d:d0:f9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.64 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:c8:44:b8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 1a:63:8c:b0:cf:f8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

I then tried iwconfig...

laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Apparently these may show that the card is recognised and installed but switched off? The wireless indicator light is on but it might make sense that it is somehow inactive. I'm still digging. Can anyone shed any more light on this or do I just give up altogether? I'm sure I can't work it out on my own. :-({|=:-({|=

---

### Post by yeats on 2009-02-25
You might benefit from reading this thread:

[http://ubuntuforums.org/showthread.php?t=1038226]("http://ubuntuforums.org/showthread.php?t=1038226")

---

