---
title: "DSL not working !!!!!! grrrrr"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by SnaveDogg on 2009-04-23
I have tried everything I know and nothing.
I'm trying to use the ethernet cable, no wireless capability with my machine.
please help. I need STEP BY STEP instructions....

---

### Post by GMod on 2009-04-23
Check your DSL modem.  make sure all lights are green. If you have an activity light it should flash occasionally. If one of your lights is red, not on or flashing that would be the cause of your issue, if you've got a spare cat5 cable try that as well, it could be a bad network cable. You may also need to reset the modem, on the bottom there should be an IP address (192.168.x.xxx) type that into your browser and the configuration page should pop up. You may also need the modem access code to reset so you might want to write that down as well. Find the tab that says "restart" (or reset/reboot) click it, enter your access code and it should work.

---

### Post by SnaveDogg on 2009-04-23
> **GMod said:**
> Check your DSL modem.  make sure all lights are green. If you have an activity light it should flash occasionally. If one of your lights is red, not on or flashing that would be the cause of your issue, if you've got a spare cat5 cable try that as well, it could be a bad network cable. You may also need to reset the modem, on the bottom there should be an IP address (192.168.x.xxx) type that into your browser and the configuration page should pop up. You may also need the modem access code to reset so you might want to write that down as well. Find the tab that says "restart" (or reset/reboot) click it, enter your access code and it should work.

reset the modem...nothing
typed in IP add into browser...nothing
no opportunity to type in any codes...just a FAILED TO CONNECT warning in Firefiox

---

### Post by GMod on 2009-04-23
sounds like your network card isn't being found.  Heres a link to another thread, sounds to me like the same problem.
[http://ubuntuforums.org/showthread.php?t=1109089]("http://ubuntuforums.org/showthread.php?t=1109089")

---

### Post by Hospadar on 2009-04-23
In a terminal, could you run "ifconfig" and post the output, that would determine if your machine is connected to the router (and if it is, then the issue lies in the router most likely, otherwise it's probably a network card issue)

---

### Post by sandyd on 2009-04-23
nvm
posted something totally stupid

---

### Post by SnaveDogg on 2009-04-23
> **Hospadar said:**
> In a terminal, could you run "ifconfig" and post the output, that would determine if your machine is connected to the router (and if it is, then the issue lies in the router most likely, otherwise it's probably a network card issue)

here is output from terminal

lo  Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:82 errors:0 dropped:0 overruns:0 frame:0
TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueueln:0
RX bytes:4100 (4.0KB) TX bytes:4100 (4.0 KB)

swapped cat5 cable, no change
rebooted twice
no change
input IP, subnet, and def gateway, and tried inputting a dns no change

OH well, another night wasted on xubuntu. three nights in a row.
going to bed angry.

---

### Post by SnaveDogg on 2009-04-24
nobody else have any suggestions?

---

### Post by biji on 2009-04-24
your ethernet card is not detected.. check the bios first

---

### Post by SnaveDogg on 2009-04-24
I talked to one of our Network guys where I work about this problem...and as I stood there in his office talking to him, I look down and HE is running Ubuntu 8.10 (cool!)

Anyhow, he shows me the terminal, what shows up when typing in certain commands, and I showed him what I was seeing when typing in the same commands. He thinks it is a ethernet card issue.
Told me to type in eth0 up in the terminal. if that doesn't work to swap out the card. He had a couple extras to give me. I think I'm on my way to a solution sooner than later...
I learned more in 10 minutes with him, than an hour and a half last night.

---

### Post by SnaveDogg on 2009-04-25
OK, here I am still trying to get it to work.

Installed new ethernet card.

rebooted

in terminal I typed
sudo ifconfig eth1 
 
output

eth1    Link encap:Ethernet HWaddr 00:80:ad:7f:d5:6a
          BROADCAST MULTICAST MTU:1500 Metric:1
          RX packet:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets: 0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          Base address:0x3000

then I typed in sudo ifconfig eth1 up

and got

SIOCSIFFLAGS: Device or resource is busy

now what? it seems that it is recognizing the ethernet card? Am I reading that right?

I'm using a Speedstream modem, and a DYNEX wireless router. Taking the cat5 cable output from the wireless router back to the IN on the ethernet card.

how/where do I configure it?
do I use static IP or DCHP? where will I find settings?
Can I get the IP from my Windows laptop that is working (the one I am now typing on)?
Do both computers have to have the same IP address subnet mask DNS?

I have no clue what I'm doing, I just want this to work. Please help. I'm now on day 4 of this saga.

---

### Post by SnaveDogg on 2009-04-25
I did a lspci -v command in terminal ( as I saw from another post) and got this

00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 02)
    Flags: bus master, fast devsel, latency 0

00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Intel Corporation 82810 (CGC) Chipset Graphics Controller
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 3
    Memory at f8000000 (32-bit, prefetchable) [size=64M]
    Memory at f4000000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801AB PCI Bridge (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f4100000-f41fffff

00:1f.0 ISA bridge: Intel Corporation 82801AB ISA Bridge (LPC) (rev 02)
    Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801AB IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Intel Corporation 82801AB IDE Controller
    Flags: bus master, medium devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at 1800 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801AB USB Controller (rev 02) (prog-if 00 [UHCI])
    Subsystem: Intel Corporation 82801AB USB Controller
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 1820 [size=32]

00:1f.3 SMBus: Intel Corporation 82801AB SMBus Controller (rev 02)
    Subsystem: Intel Corporation 82801AB SMBus Controller
    Flags: medium devsel, IRQ 9
    I/O ports at 1810 [size=16]

00:1f.5 Multimedia audio controller: Intel Corporation 82801AB AC'97 Audio Controller (rev 02)
    Subsystem: Unknown device 4352:5933
    Flags: bus master, medium devsel, latency 0, IRQ 9
    I/O ports at 1200 [size=256]
    I/O ports at 1300 [size=64]

01:0b.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
    Subsystem: Unknown device 4554:434e
    Flags: bus master, medium devsel, latency 165
    I/O ports at 3000 [size=256]
    Memory at f4100000 (32-bit, non-prefetchable) [size=256]
    [virtual] Expansion ROM at f4140000 [disabled] [size=256K]
    Capabilities: <access denied>

01:0d.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
    Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
    Flags: 66MHz, medium devsel
    Memory at f4101000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

01:0d.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
    Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
    Flags: 66MHz, medium devsel
    Memory at f4102000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

01:0d.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
    Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
    Flags: 66MHz, medium devsel
    Memory at f4103000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

01:0d.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: Unknown device 2020:8888
    Flags: 66MHz, medium devsel
    Memory at f4100400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

01:0e.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
    Subsystem: Mac System Co Ltd HP
    Flags: bus master, medium devsel, latency 64
    Memory at f4110000 (32-bit, non-prefetchable) [disabled] [size=64K]
    I/O ports at 3400 [disabled] [size=8]
    Capabilities: <access denied>

LOOKS LIKE "access denied" on the USB card, the ethernet card and the Conexant modem


How do I fix this??

---

### Post by JK3mp on 2009-04-25
Try switchin up to super user and try that command again.  (not sudo) but actual super user.

---

### Post by SnaveDogg on 2009-04-25
> **JK3mp said:**
> Try switchin up to super user and try that command again.  (not sudo) but actual super user.


would love to do that, but how?

---

### Post by SnaveDogg on 2009-04-26
bump

---

### Post by SnaveDogg on 2009-04-27
bump

---

### Post by mrcycling on 2009-04-27
I believe it is:
sudo su

But can't help you with the rest of the issue, as I am having the same headaches with my fast ethernet adapter

---

### Post by SnaveDogg on 2009-04-29
> **SnaveDogg said:**
> I have tried everything I know and nothing.
I'm trying to use the ethernet cable, no wireless capability with my machine.
please help. I need STEP BY STEP instructions....


SO, SUCCESS!!!!
One of our IT guys here where I work got to work on my old junker computer with the eth card problems, does some checking for himself on some of the things he asked me to do, without any success.
THEN, he checks the BIOS settings, and it is set for"Win98". He changes it to "other" and BOOM!!!! it works.
Eth card being read, downloading updates ,the whole she-bang...
Just thought I'd provide an update. :popcorn:

---

