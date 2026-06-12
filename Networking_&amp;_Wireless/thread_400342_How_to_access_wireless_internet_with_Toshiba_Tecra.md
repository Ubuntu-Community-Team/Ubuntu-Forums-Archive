---
title: "How to access wireless internet with Toshiba Tecra?"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by O-pos on 2007-04-03
Hello,

I'm newbie ubuntu user. Today I installed ubuntu 6.10 and now I'm wondering how to access wireless internet which is in my students' house in Austria. Now I can access it from windows (I have dual boot). I checked wireless LAN connection settings in Ubuntu, there's nothing, everything's empty. What do I have to do?

---

### Post by O-pos on 2007-04-03
I consulted following website: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

then I entered the command 

lspci -v | less

in the terminal, and this is what I got: Any suggestions how can I connect to my wireless LAN?

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/
O Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <access denied>

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor
 to I/O Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor
 to I/O Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Grap
hics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device 0033
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Memory at d0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at eff8 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics De
vice (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device 0033
        Flags: fast devsel
        Memory at 20000000 (32-bit, prefetchable) [size=128M]
        Memory at 2a000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) U
SB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 18c0 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) U
SB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 18e0 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) U
SB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1c00 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Co
ntroller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at 2a080000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 
00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=03, sec-latency=64
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: cff00000-cfffffff
        Prefetchable memory behind bridge: 28000000-29ffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (re
v 03)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 0
3) (prog-if 8a [Master SecP PriP])
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at bfa0 [size=16]
        Memory at 2a080400 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH
4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device 0412
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1000 [size=256]
        I/O ports at 1880 [size=64]
        Memory at 2a080800 (32-bit, non-prefetchable) [size=512]
        Memory at 2a080a00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Mode
m Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: medium devsel, IRQ 11
        I/O ports at 1400 [size=256]
        I/O ports at 1800 [size=128]
        Capabilities: <access denied>

01:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connec
tion (rev 05)
        Subsystem: Intel Corporation Unknown device 2741
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at cffff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet
 Controller (rev 83)
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at cfffe000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at cf00 [size=64]
        Capabilities: <access denied>

01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bri
dge with ZV Support (rev 33)
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, slow devsel, latency 168, IRQ 11
        Memory at cff00000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=01, secondary=02, subordinate=02, sec-latency=0
        Memory window 0: 28000000-29fff000 (prefetchable)
        Memory window 1: 2c000000-2dfff000
        I/O window 0: 0000c000-0000c0ff
        I/O window 1: 0000c400-0000c4ff
        16-bit legacy interface ports at 0001

---

### Post by floke on 2007-04-03
What do you get if you type 

iwconfig

---

### Post by O-pos on 2007-04-03
After command iwconfig I get:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Studentenheim_R&#65533;ssl"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:5C:3D:3C   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=87/100  Signal level=-42 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1

sit0      no wireless extensions.

In Windows I entered device managers and I clicked on wireless and that's what I got:

Intel(R) PRO/Wireless 2200BG Network Connection

What should I do?

---

### Post by floke on 2007-04-03
Well the good news is that your wireless is working - at least the PC knows it's there and what sort it is etc. - so hopefully this shouldn't be too hard. Detail the exact steps you are trying to do to connect to the wireless.

---

### Post by O-pos on 2007-04-04
Wow, I think that's good news. Why shouldn't it work then?

I don't undertake any steps to connect to wireless, I don't know any steps. For windows, when I boot XP, then I can open Firefox and just surf in internet. in Linux, when I open Firefox, I can't connect to internet, i  get "no connection". That's it..

---

### Post by floke on 2007-04-04
You have to select System/Admin/Network

Then check the box for Wireless so that it's enabled
Use 'properties' to enter your ESSID etc.
For the bottom part I selected DHCP (automatic) and left the boxes below empty.

Does this help?

---

### Post by O-pos on 2007-04-04
What should I enter for "network name"? Does it have to exactly match the real name? in Linux I don't know the names of the WLAN networks here, so I can reboot windows, copy  name of network and then paste in Linux. (Now, I'm at my work, and there's another wireless network. The parameters are not the same as at home)

Windows makes very easily automatic network search. Can I make with Linux first such a search and then choose the connection?

---

### Post by O-pos on 2007-04-04
I accessed it finally. so there's driver for wireless. I disabled cable internet and then wrote iwconfig in terminal. I  copied the name after ESSID: and pasted it in System/Admin/Network and it did work for few minutes. then I checked it again with iwconfig and there were everywhere 0-s in Link quality, signal level, noise level etc... then I observed the following: 

 In my student' house there are 5-6 wireless networks with different names. if I'd disable wireless in  System/Admin/Networkand then keep checking terminal with iwconfig, after each 5-15 minutes there was change in network name. probably it automatically selects the best one, I don't know. Then, If I immediately would copy the network name and paste it in System/Admin/Network wireless, then it would work, but again for few minutes. Then everything was on zero and I had to disable wireless, search again with iwconfig, enter new name etc..

Why can't it just stick to one?

---

### Post by floke on 2007-04-04
Yes I think that Wireless can be a bit of a pain in this case. 
Which wi-fi program are you using?

You could try using one of these instead...

sudo apt-get install network-manager-gnome

sudo apt-get install wifi-radar

They should let you choose from a list, so this might solve the problem.

---

