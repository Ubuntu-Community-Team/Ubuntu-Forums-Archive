---
title: "Belkin wireless network adapter"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by jay3712 on 2007-09-13
Hey guys, I hope someone can help me here. I just did a fresh install of feisty and the wired network connection simply would not work. So I looked around and bought a Belkin F5D7000 wireless adapter because it was said to be supported out of the box. Well I just installed it and it is not detected by Ubuntu. Can anyone give me some help on how to figure this out? What other information do you gurus need to get this figured out?
Thanks a million.

---

### Post by ntetreau on 2007-09-13
Welcome to ubuntu, don't worry people will give you a hand surely.  From a terminal (Applications > Accessories > terminal) post the output of 

```
lspci -v
```

```
ifconfig
```

and

```
more /etc/network/interfaces
```

Please make sure to insert the outputs in between a CODE markers (go in advanced forum edit mode).

By the way, what happens in a terminal and then in the upper right corner when you type in a terminal:

```
sudo NetworkManager --no-daemon
```

Nic

---

### Post by jay3712 on 2007-09-13
Alright here we go.
lspci -v:
```

lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8086
        Flags: bus master, medium devsel, latency 32
        Memory at d0000000 (32-bit, non-prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: cf000000-cfffffff
        Prefetchable memory behind bridge: e0000000-febfffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 04)
        Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at e600 [size=32]

00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 809a
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at ce800000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at dffe0000 [disabled] [size=128K]
        Capabilities: <access denied>

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8087
        Flags: bus master, medium devsel, latency 128, IRQ 17
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at a400 [size=16]

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8096
        Flags: bus master, medium devsel, latency 32, IRQ 23
        I/O ports at 9400 [size=256]
        I/O ports at 9000 [size=128]
        Capabilities: <access denied>

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8087
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at ce000000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8087
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at cd800000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8087
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at cd000000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8087
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at cc800000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
        Subsystem: ASUSTeK Computer Inc. Unknown device 80a7
        Flags: bus master, medium devsel, latency 32, IRQ 22
        I/O ports at 8800 [size=256]
        Memory at cc000000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at dffc0000 [disabled] [size=128K]
        Capabilities: <access denied>

00:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs Unknown device 1002
        Flags: bus master, medium devsel, latency 32, IRQ 22
        I/O ports at 8400 [size=64]
        Capabilities: <access denied>

00:08.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
        Subsystem: Creative Labs Unknown device 0060
        Flags: bus master, medium devsel, latency 32
        I/O ports at 8000 [size=8]
        Capabilities: <access denied>

00:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at cb800000 (32-bit, non-prefetchable) [size=2K]
        Memory at cb000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:0a.0 Multimedia video controller: Ensoniq Unknown device 5882 (rev 02)
        Subsystem: Ensoniq Unknown device 5882
        Flags: bus master, slow devsel, latency 32, IRQ 5
        I/O ports at 7800 [size=64]
        I/O ports at 7400 [size=64]
        Capabilities: <access denied>

00:0c.0 Ethernet controller: Belkin Unknown device 700f (rev 20)
        Subsystem: Belkin Unknown device 700f
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at 7000 [size=256]
        Memory at ca800000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>

00:0e.0 RAID bus controller: Promise Technology, Inc. PDC20376 (FastTrak 376) (rev 02)
        Subsystem: ASUSTeK Computer Inc. A7V8X motherboard
        Flags: bus master, 66MHz, medium devsel, latency 96, IRQ 17
        I/O ports at 6800 [size=64]
        I/O ports at 6400 [size=16]
        I/O ports at 6000 [size=128]
        Memory at ca000000 (32-bit, non-prefetchable) [size=4K]
        Memory at c9800000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 0002
        Flags: bus master, stepping, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at d800 [size=256]
        Memory at cf800000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at effe0000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)
        Subsystem: ATI Technologies Inc Unknown device 0003
        Flags: bus master, stepping, 66MHz, medium devsel, latency 64
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Memory at cf000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

```
ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:E0:18:D2:09:CE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0x8800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5356 (5.2 KiB)  TX bytes:5356 (5.2 KiB)

```
more /etc/network/interfaces:
```

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```
NetworkMgr:
```
Password:
NetworkManager: <information>   starting...
NetworkManager: <WARNING>        nm_dbus_init (): nm_dbus_init() could not acquire the NetworkManager service as it is already taken (ret=3). Is the daemon already running?
NetworkManager: <ERROR> [1189681672.880067] main (): nm_dbus_init() failed, exiting. Either dbus is not running, or the NetworkManager dbus security policy was not loaded.
NetworkManager: traceback:
NetworkManager:         NetworkManager(main+0x47f) [0x806916f]
NetworkManager:         /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7c57ebc]
NetworkManager:         NetworkManager [0x8053e41]
Trace/breakpoint trap (core dumped)

```
Thanks for the welcome and any help you can give.

---

### Post by ntetreau on 2007-09-13
What is the exact model of your usb wifi adapter?  Please include the version as well.

---

### Post by jay3712 on 2007-09-13
F5D7000 ver.7000

---

### Post by jay3712 on 2007-09-13
Oh yea, it's PCI, not USB

---

### Post by ntetreau on 2007-09-14
You should be able to follow this guide for your card:

[https://help.ubuntu.com/community/WifiDocs/Device/F5D7000](https://help.ubuntu.com/community/WifiDocs/Device/F5D7000)

You can probably stop after "sudo modprobe ndiswrapper" and then it should show up in NetworkManager".  Keep reading though as there might be other steps later to make sure it is started at boot.

---

### Post by jay3712 on 2007-09-14
Alright, I need to install ndiswrapper but I think I can figure that out.

---

### Post by snevensmores on 2007-09-14
Well jay, if it's any consolation, I have the same card (F5D7000 ver 7000) in my desktop and I've had no luck getting it to work, either. It will scan and actually find routers all over my apartment building, but that's as far as I get. I'm about ready to give up and just buy a linux-friendly card.

---

### Post by jay3712 on 2007-09-14
Darn thing is according to [this]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin") website it was a linux friendly card (8th one down). I clicked on the link to the Belkin website and it said part# F5D7000, so I searched that in Newegg and bought it. Looks like I might have to RMA it, in which case I don't get back shipping, plus the 15% restocking fee. gggrrrrr.

---

### Post by snevensmores on 2007-09-14
It appears that some versions of the card do work. Unfortunately, I'm starting to think that mine's not one of them :(. I've tried just about everything. Unlike those listed on your link, mine has a RealTek chip on it. It's an 8185L, and I've seen plenty of How-Tos to get them to work, but I can't seem to get the chip to work on this card. I'm about ready to pull my hair out over here.

---

### Post by jay3712 on 2007-09-14
Mine has the 8185L chip on it too. I can't even get ndiswrapper installed. I already sent one back that was on one of the "works out of the box" lists, but it didn't. Version numbers are obviously very important yet they are not listed on newegg.

---

### Post by snevensmores on 2007-09-14
Since I don't have internet on that computer, I went here [here]("http://packages.ubuntu.com") and searched for ndiswrapper and downloaded the common and the plugin (not sure if those are even required). I put em on a usb drive and transferred them to the desktop that I'm having problems with. I can at least get it to scan and find access points, but that's it.

---

### Post by jay3712 on 2007-09-14
Ok, using your link I got ndiswrapper installed, and it appeared that the driver had installed also. sudo ndiswrapper -l gave: "bcmwl5a : driver installed" still the wireless network connection doesn't show up in System>Admin>network.

---

### Post by snevensmores on 2007-09-14
Going by GS2's directions [here]("http://ubuntuforums.org/showthread.php?t=381878&highlight=RTL8185L&page=2"), I made a driver association with the hardware.

When you run "ndiswrapper -l" , it should then tell you the driver is installed AND the hardware is present. I also ran the following commands, but take my advice with a grain of salt -- I haven't gotten my card working, either.

```
sudo depmod -a

sudo modprobe ndiswrapper
```

---

### Post by jay3712 on 2007-09-14
Alright thanks for that link, I'll give that a try and see what happens.

---

### Post by jay3712 on 2007-09-14
What do I do on this step?
> Open a terminal and type:
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by snevensmores on 2007-09-14
Actually, I didn't bother with that step, because I didn't feel like going back and installing another package. I have no idea if that affected my results or not. Maybe you can let me go if you get it working :).

More and more, I feel like it'd be easier just to spend a few bucks on a more linux-compatible card (if I can find one).

---

### Post by jay3712 on 2007-09-15
I have been doing more reading on linux friendly cards and there are a couple threads saying [this one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833127080") works straight out of the box. But then again, that was the information I had on the last two that I tried...

---

### Post by ntetreau on 2007-09-18
snevensmore:  you say that your card is now recognized and that you can scan access points.  What happens when you choose one?  If you can' t get an IP address, while is it trying to connect open a terminal and try :

```
sudo dhclient
```

Also, are you trying to connect using NetworkManager (the icon on the upper right?)  Hope you guys can get your cards working, you seem so close!

---

### Post by ntetreau on 2007-09-18
> **jay3712 said:**
> What do I do on this step?

You need to download and install the linux headers for the linux kernel you are running.  The command

```
uname -r
``` will give you exactly the kernel number you are running... something like 2.18.16 or so.  The headers are necessary for building ndiswrapper against your kernel. 

By the way, are you guys able to connect to the internet using a wired connection?  If not, then you need to download on another computer all the packages needed including their dependencies.  This is a pain but it's totally feasible.  For example, if you go to synaptics and look for "linux headers" and then right click on the package you would want to install then check the "dependencies" tab, take not of the name of the extra packages you need. In this case, libc, coreutils and fileutils.  Then go to 

[http://packages.ubuntu.com/feisty/](http://packages.ubuntu.com/feisty/)

and download them all.  Once you moved the files to your Feisty installation, use

```
sudo dpkg -i *.deb
```

in the directory where the files are.  Now keep following the instructions in the link posted above.  Copy and paste here any error you are getting.  Good luck!

Nic

---

### Post by snevensmores on 2007-09-18
> **ntetreau said:**
> snevensmore:  you say that your card is now recognized and that you can scan access points.  What happens when you choose one?  If you can' t get an IP address, while is it trying to connect open a terminal and try :

```
sudo dhclient
```

Also, are you trying to connect using NetworkManager (the icon on the upper right?)  Hope you guys can get your cards working, you seem so close!

Yeah, it has issues getting an IP address. I haven't been able to even ping my router.

I've already formatted and reinstalled windows. Now you make you want to go back and try it again :(.

---

### Post by ntetreau on 2007-09-18
You could always try it using the LiveCD!

---

