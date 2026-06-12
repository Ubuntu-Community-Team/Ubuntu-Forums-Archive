---
title: "Wireless cards are not Wlan0"
date: 2005-11-03
forum: Networking &amp; Wireless
---

### Post by MightyMouse on 2005-11-03
Hi everybody,
I have a problem with the configuration of wireless cards.
I have a PC and a Laptop and I recently installed Ubuntu Breezy on both.
I distinctly remember that during the installation of my PC a wireless network card was detected, but I could not configure the network because no AP could be found. Now if I use iwconfig I get the following:

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      NOT READY!  ESSID:"XXXXXX"
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

This is the same I see on my Laptop.

In Network settings I see a wireless devive, but not configured.

I am wondering, how can I see that I actually do have wireless cards (could I have mixed them up with my ethernet cards somehow)?
And is there some way to figure out why I cant activate any of the wireless cards in Network settings even when I am sure I have the right information and even switched of WEP encryption?
I tried ndiswrapper but even though I have a driver for my SMC2802W card that I loaded and I get the information that also the Hardware is working when I ask to scan I get 'No scan results'.

In my PC I have a Realtek RTL-8319/8139C/8139C+ ethernet card and a SMC2802W PCI-card with Intersil ISL3890 (Prism GT/Prism) chipset (this information is from Device Manager).
My Laptop has a Realtek RTL-8169 Gigabit ethernet card, a (Integrated, so I don't know exactly what is is) wireless card with Intersil ISL-3886 chipset and I also have a ASUS USB WL-167G wireless adapter which is listed in the Device Manager as a USB2.0 device, but if I check with the Windows Wireles GUI than no Hardware is detected (something I aslo do not understand quit well)

I would very much appreciate if someone could help me out, especially with the problem that ny wireless devices are not recognized as such in iwconfig.

THANKS!!!!
MightyMouse

---

### Post by insitu on 2005-11-03
lspci -v 
gives you the (registered) name manufacturer and model of all your pci cards.  This should solve your problem of identification for laptop card (maybe an Intel wireless pro ?).

Do you see mac address of  wireless card with ifconfig -a ? 

What is the output of dmesg (or cat /var/log/messages) relating to the device driver ?

Have you identified the driver for the card and if so, is the chid id supported ?

---

### Post by MightyMouse on 2005-11-04
Hi,
thanks for your help, most appreciated 
This is the output for lspci -v

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge  (rev 01)
        Subsystem: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: [80] AGP version 3.5
        Capabilities: [c0] #08 [0060]
        Capabilities: [68] Power Management version 2
        Capabilities: [58] #08 [8001]

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800 South]  (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: d8000000-dfffffff
        Capabilities: [80] Power Management version 2

0000:00:05.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Pri sm Xbow] (rev 01)
        Subsystem: Unknown device 17cf:0036
        Flags: bus master, medium devsel, latency 80, IRQ 16
        Memory at 20000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [dc] Power Management version 1

0000:00:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 C ontroller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: CLEVO/KAPOK Computer: Unknown device 4701
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at d0008000 (32-bit, non-prefetchable) [size=2K]
        Memory at d0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

0000:00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigab it Ethernet (rev 10)
        Subsystem: CLEVO/KAPOK Computer: Unknown device 4701
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        I/O ports at 1000 [size=256]
        Memory at d0008800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [dc] Power Management version 2

0000:00:0c.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 0 1)
        Subsystem: CLEVO/KAPOK Computer: Unknown device 4701
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at 20002000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20400000-207ff000 (prefetchable)
        Memory window 1: 20800000-20bff000
        I/O window 0: 00004400-000044ff
        I/O window 1: 00004800-000048ff
        16-bit legacy interface ports at 0001

0000:00:0e.0 Unknown mass storage controller: Winbond Electronics Corp: Unknown device 8481 (rev 01)
        Subsystem: Winbond Electronics Corp: Unknown device 1050
        Flags: medium devsel, IRQ 5
        Memory at d0005000 (32-bit, non-prefetchable) [size=4K]
        Memory at d0004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c0] Power Management version 2

0000:00:0e.1 Unknown mass storage controller: Winbond Electronics Corp: Unknown device 8482 (rev 01)
        Subsystem: Winbond Electronics Corp: Unknown device 1050
        Flags: medium devsel, IRQ 5
        Memory at d0007000 (32-bit, non-prefetchable) [size=4K]
        Memory at d0006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c0] Power Management version 2

0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80) (prog-if 00 [UHCI])
        Subsystem: CLEVO/KAPOK Computer: Unknown device 4701
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at 1c00 [size=32]
        Capabilities: [80] Power Management version 2

0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80) (prog-if 00 [UHCI])
        Subsystem: CLEVO/KAPOK Computer: Unknown device 4701
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at 1c20 [size=32]
        Capabilities: [80] Power Management version 2

0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80) (prog-if 00 [UHCI])
        Subsystem: CLEVO/KAPOK Computer: Unknown device 4701
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at 1c40 [size=32]
        Capabilities: [80] Power Management version 2

0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20  [EHCI])
        Subsystem: CLEVO/KAPOK Computer: Unknown device 4701
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at d0008c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
        Subsystem: CLEVO/KAPOK Computer: Unknown device 4701
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: [c0] Power Management version 2

0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: CLEVO/KAPOK Computer: Unknown device 4701
        Flags: bus master, medium devsel, latency 64, IRQ 23
        I/O ports at 1c60 [size=16]
        Capabilities: [c0] Power Management version 2

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 50)
        Subsystem: CLEVO/KAPOK Computer: Unknown device 4701
        Flags: medium devsel, IRQ 22
        I/O ports at 1400 [size=256]
        Capabilities: [c0] Power Management version 2

0000:00:11.6 Communication controller: VIA Technologies, Inc. Intel 537 [AC97 Mo dem] (rev 80)
        Subsystem: CLEVO/KAPOK Computer: Unknown device 4701
        Flags: medium devsel, IRQ 22
        I/O ports at 1800 [size=256]
        Capabilities: [d0] Power Management version 2

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel
        Capabilities: [80] #08 [2101]

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Rad eon 9600 M10] (prog-if 00 [VGA])
        Subsystem: CLEVO/KAPOK Computer: Unknown device 4701
        Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 9
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 2000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [58] AGP version 3.0
        Capabilities: [50] Power Management version 2


This the output for ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:30:B4:00:00:00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16

eth1      Link encap:Ethernet  HWaddr 00:90:F5:32:7B:76
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fe32:7b76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1501 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1398013 (1.3 MiB)  TX bytes:269616 (263.2 KiB)
          Interrupt:19 Base address:0x6800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10409 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:795112 (776.4 KiB)  TX bytes:795112 (776.4 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Output for dmesg that has to do with network

r8169: eth1: link up
[4295604.752000] eth1: no IPv6 routers present

ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294872.578000] eth0: resetting device...
[4294872.578000] eth0: uploading firmware...
[4294872.729000] prism54: request_firmware() failed for 'isl3886'
[4294872.729000] eth0: could not upload firmware ('isl3886')
[4294872.729000] eth0: islpci_reset: failure
[4294880.900000] eth0: resetting device...
[4294880.900000] eth0: uploading firmware...
[4294881.043000] prism54: request_firmware() failed for 'isl3886'
[4294881.043000] eth0: could not upload firmware ('isl3886')
[4294881.043000] eth0: islpci_reset: failure
[4294881.093000] eth0: resetting device...

I guess here lies the problem, I don't know what to do with tis isl3886 firmware that is missing.
When I use the "Windows Wireless Drivers" tool and load a file called Prisma00 the I get the message that the hardware is present, so at least my network card seems to be recognized.

I also figure out that it is the Insel chip-set that is the reason the crards are listed as eth0 and not Wlan0 (found that on the wireless hardware support list)

I appreciate any further help, I feel that that the solution must be close, I just am not experienced enough to figure it out!

Thanks,
MightyMouse

---

### Post by philipgm on 2005-11-06
I think that you will have a problem with the isl 3886 chip set. This is, if I remember correctly, the Javelin/Xbow and doesn't work with the Prism 54 driver. If you go to the Prism 54 web site you might get some more info there. My Fuji/Seimens laptop had a wireless card with this chipset and this is what I had to do, following a few clues around these forums.

To get this working you will have to remove the 

Prism 54 module

Install ndiswrapper

set up ndiswrapper with the windows driver for your card

My son has taken over that laptop so I can't check out the exact solution.

I hope this helps

---

### Post by monkey89 on 2005-11-06
He is using ndiswrapper - hence the "Windows wireless gui" he's describing.

eth0 is a wireless card - it shows output in iwconfig that it has wireless extensions, which means it is wireless.  This, I guess, is your wireless card.  Can you configure it?

---

### Post by MightyMouse on 2005-11-07
Well , i got another network card with a Insel chip set working, so maybe the same will work here.

The trick was to first remove the prism54 driver, then install the windows driver with ndiswrapper, and the put the prism driver on the hotplug blacklist. I have not yet tried this on my Laptop, but it worked with my PC.

I'll post if this works.

MightyMouse

---

### Post by koenvandijk on 2005-11-13
I have the same card (prism ISL3886) so can someone explain it to me in steps ( Im new to Linux and ubuntu:)  ).

---

### Post by technophreak on 2005-11-13
I've got this exact card in my laptop too. I'm new to linux and Ubuntu but have been learning how to use the terminal with linuxcommand.org. I need the same help as koenvandijk.

Thanks

---

### Post by xsmind on 2005-11-13
[Here]("http://ubuntuforums.org/showthread.php?p=489674") is another discussion about this card. Lambert was kind enough to provide information how to remove the old module. I've tried it and it works.
[QUOTE=Lambert]If you run ```
lsmod
``` this shows you the modules that are loaded. 

To remove a module you type ```
sudo modprobe -r <module>
```[/QUOTE]

I hope this will work for you too.

---

### Post by MightyMouse on 2005-11-14
Well I finally gor everything working, and this is how I did it.

First, if you have tried already a number of things consider to re-install Ubuntu. I had the feeling that a number of changes that sneeked in during earlier attempts were difficult to get rid off.

Next thing, after installing Ubuntu base consider upgrading the Kernel to version 686. Somewhere else in the forum someone explained that the Kernel that comes with Ubuntu is not the newest (something to do with keeping the base installation compatible for most computers). Upgrading it possible from PentiumII up.

The reason you have no wlan0 but instead a eth0 is that the chipset is not recognized correctly and that has also something to do with the prism54 driver that thinks it can handle the chip-set but apparently can not.

So to get the new Kernel open a terminal and type

sudo apt-get install linix-image-686

you will be asked a password, that is the one you set during the installation (so your own!)

Restart your computer!

Make sure you have a file called prisma00.inf (you can get it from your "BillGates get's rich" version of an OS on your computer, else via the driver software that came with your wireless card or try to google it) [COLOR="Red"]and the sys file (added at 15-11-05)[/COLOR]

Apparently it makes live a lot easier if you switch off any WAP security of you AP during the first set-up attempt, you can switch it on again later if setting up the card worked (you can then use the Network tool)

I used ndiswrapper, the windows wireless tool should also work but I did it the old fashioned way.

terminal:

modprobe -r prism54

#check that this driver is unloaded by

dmesg | grep prism54

# something like unloaded should be mentioned

ndiswrapper -i /?/prisma00 

# (/?/ the directory where you placed the prisma00.inf file [COLOR="Red"]and the sys file[/COLOR] )
# check if it is loaded by

ndiswrapper -l 
# you should get this

Installed ndis drivers:
prisma00        driver present, hardware present

# now do 
sudo ndiswrapper -m
modprobe ndiswrapper

# Now check with 
iwconfig

you should have a wlan0 now!

You can set it up it with the Network function under System/Administration or use the interfaces files.

First you have to make sure the prism54 driver is not re-loaded next time you boot so do this

sudo gedit /etc/hotplug/blacklist/

add a line at the end of the file with : prism54
then save and close. This will prevent that prism54 is loaded during the boot.


# I  manually set the interfaces file 
sudo gedit /etc/network/interfaces
mine looks like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0

# The primary network interface
iface wlan0 inet dhcp

#auto eth1

auto wlan0
iface wlan0 inet dhcp
wireless_channel 01
wireless_mode managed
wireless-essid YourAPsName 
wireless-key XXXXXXXXXX (if you have WAP set this is your hexadeciaml code)

I might have forgotten a sudo somewhere but if at any point of this you get a message with no access rights or similar you should type sudo before the comand line and it should work!

This is it.

If you have problems just relpy. I might have missed something or just forgotten to put it in.

MightyMouse

---

