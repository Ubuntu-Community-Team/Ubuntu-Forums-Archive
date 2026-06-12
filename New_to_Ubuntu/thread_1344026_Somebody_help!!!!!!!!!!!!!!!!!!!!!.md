---
title: "Somebody help!!!!!!!!!!!!!!!!!!!!!"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2009-12-02
ok this is getting ridiculous

could somebody please help me get internet to my Toshiba Satellite M300 


internet provider is windstrem its a wired router   im currently connected to the laptop via ethernet cord   so far i have tried lots of things

like trying the pppoeconf  and when i did that i got this box saying that i need to manually install it   so i clicked ok   then they could find the modconf   said there isnt any etherent thing detected and now im lost like no other so could someobody please help




here is my lisp  

mage@mage-laptop:~$ lispci=v
mage@mage-laptop:~$ lspci-v
lspci-v: command not found
mage@mage-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Toshiba America Info Systems Device ff51
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at f4000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Toshiba America Info Systems Device ff51
	Flags: bus master, fast devsel, latency 0
	Memory at f4400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1820 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at f4a04800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f4800000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: b6000000-b60fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: b6100000-b61fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 18a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f4a04c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Memory behind bridge: f4700000-f47fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
	I/O ports at 1818 [size=8]
	I/O ports at 180c [size=4]
	I/O ports at 1810 [size=8]
	I/O ports at 1808 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at f4a04000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: medium devsel, IRQ 10
	Memory at b6200000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]
	Kernel modules: i2c-i801

07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: fast devsel, IRQ 16
	Memory at b6000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	Capabilities: <access denied>
	Kernel modules: sky2

08:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Device 1a32:4105
	Flags: fast devsel, IRQ 17
	Memory at b6100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath5k

0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 16
	Memory at ff501000 (32-bit, non-prefetchable) [size=4K]
	Memory at f4700000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02) (prog-if 01)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at f4700800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: slow devsel, IRQ 255
	Memory at f4702000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

---

### Post by endBc on 2009-12-02
```
ifconfig -a

```

Let us know the output.

---

### Post by halitech on 2009-12-02
if you are required to use pppoe and you have a router, you shouldn't need to do anything on the computers, the router should be making the connection for you and the connection to the computers should be normal ethernet.

---

### Post by pyrofreak99 on 2009-12-02
Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


here is the ifconfig

---

### Post by Dougie187 on 2009-12-02
I think the problem is he isn't getting a connection to his router from his laptop, but I am unsure.

Also, theres no sense in making three threads in three hours for the same exact problem. People were working to help you in one of the other two threads and so you probably would have been better off just sticking with that one.

EDIT: These people appear to have the same card as you, and they seem to have gotten it to work. [http://ubuntuforums.org/showthread.php?t=781022](http://ubuntuforums.org/showthread.php?t=781022)

---

### Post by pyrofreak99 on 2009-12-02
ok im trying these out now  thanks guys a bunch for this i have now learned my lesson about making multiple forums  just be patient cuz that is the key

---

### Post by pyrofreak99 on 2009-12-02
ok there solution is for ubuntu 8.04  and i dotn think im going to get much help since the last post was all the way back  in 08

---

### Post by lisati on 2009-12-02
/me scratches head in puzzlement that there were difficulties. I have a Toshiba M200 with a similar card:
> 02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)


Both the Toshiba laptops I've had have been able to connect via ethernet. When I've had connection problems it's usually been some kind of problem at the router end or with the ISP.

---

### Post by Dougie187 on 2009-12-03
> **lisati said:**
> /me scratches head in puzzlement that there were difficulties. I have a Toshiba M200 with a similar card:


Both the Toshiba laptops I've had have been able to connect via ethernet. When I've had connection problems it's usually been some kind of problem at the router end or with the ISP.

Well from his ifconfig it doesn't even look like it's installed. Since he only has "lo" no "eth0" or anything like that.

Have you looked at their website for the drivers? Also, how did you install 9.10, did you upgrade from 9.04? or did you do a fresh install?

Have you tried running the LTS 8.04? and finally, Just because the instructions are for a previous version of ubuntu doesn't mean they won't work. They still might work for you, so if you don't have any other solutions it would probably be a good idea to give them a shot and see if they fix your issue.

---

### Post by pbrane on 2009-12-03
First off the PPPoE username and password should be entered in your ADSL modem. I guess you have a SpeedStream 4200? You don't need to use any PPPoE software on your computer. If you have installed it, remove it. I assume you already tried power cycling your modem.

Also you should have an ethernet connection regardless of your ADSL connection status. Look at the lights on the modem. If you called Windstream helpdesk they probably told you to reset your modem. Hopefully they had you run setup again. You do know how to get into the modem, right? Because the Windstream helpdesk folks won't know what to do if you don't have Windows. If you can't get to the modem at all it may be bad. You may have to get a new one. Check your ethernet cable first, it may be bad.

If you access to another ( known working ) modem/router, plug your computer in to see if the ethernet port on you laptop is working.

---

### Post by Excedio on 2009-12-03
> **pbrane said:**
> *snip*If you access to another ( known working ) modem/router, plug your computer in to see if the ethernet port on you laptop is working.
 
Careful...be sure you read the entire original post...
 
> *snip*internet provider is windstrem its a wired router **im currently connected to the laptop via ethernet cord** so far i have tried lots of things
*snip*
 
This is how he's talking to us now.

---

### Post by Dougie187 on 2009-12-03
What happens when you do this?
```
lshw -c network
```

---

### Post by pbrane on 2009-12-03
Excedio: I'm sure you are right, however considering the output from his ifconfig it doesn't look like the Toshiba computer is connected to any ethernet device. I just thought I'd cover that, just in case.

Also maybe "help me get internet to my Toshiba Satellite M300" isn't really telling us a lot about the problem. But it sounds like his ethernet card isn't working. Driver problem maybe?

pyrofreak99:
are you connected to that same modem with another computer? Is it just that Toshiba that is a problem?

---

### Post by RJ12 on 2009-12-03
Have you checked if there are any Hardware Drivers available in System>Administration>Hardware Drivers (Dont know if its still in the same place for Karmic). It could have drivers for your Ethernet Card.:D

---

### Post by Dougie187 on 2009-12-04
> **RJ12 said:**
> Have you checked if there are any Hardware Drivers available in System>Administration>Hardware Drivers (Dont know if its still in the same place for Karmic). It could have drivers for your Ethernet Card.:D

If that had drivers for his ethernet card, he would have to download them. And it needs internet to search for them, so he wouldn't be able to get them.

Also, he should be using the sky2 driver, which is included in the kernel. So I was trying to see if "lshw -c network" even gave us any information as to if there is a driver currently in use with his nic.

---

