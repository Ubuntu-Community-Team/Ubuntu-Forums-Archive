---
title: "need help with AIRONET 350"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by jupiterlabs on 2006-09-02
hello,

i am still pretty new to the linux world, no problems with my pc yet, but the laptop...

got a nice t41 and installed xubuntu, but no wireless device found in network-admin.

when i check for pci devices i can see it:

0000:02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b
        Subsystem: AIRONET Wireless Communications: Unknown device 5000
        Flags: bus master, fast devsel, latency 64, IRQ 11
        I/O ports at 8000 [size=256]
        Memory at c0214000 (32-bit, non-prefetchable) [size=16K]
        Memory at c0400000 (32-bit, non-prefetchable) [size=4M]
        Expansion ROM at ec000000 [disabled] [size=2M]
        Capabilities: <available only to root>

but as i said, it won't show up in network-admin, so how can i turn this thing on and make it work?

for ifup eth1 i get this:

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

special thnx for your help...

---

### Post by augied on 2006-09-03
I've got the exact same problem with a t40 and kubuntu.  Everything I can find says that it works out of the box, but I have here pretty conclusive evidence that it doesn't.
Any help would be helpful,

Augie

---

### Post by kosak on 2006-11-11
I had ubuntu before but changed for speed reasons to XUBUNTU. on ubuntu my aironet 350 worked perfectly now on xubuntu thats another story... I remember that on my network manager i had the icon of my wifi card whenever i poped it and the system automatically located nearby SSID's. with xubuntu thats not so true.. it seems more like a glitch when i try to pull the dropdown after enabling the device, nothing happens. when i do 

nico@Nico-xubuntu:~$ lsmod | grep -i airo
airo_cs                 7552  1 
airo                   78496  1 airo_cs
pcmcia                 40380  1 airo_cs
pcmcia_core            43924  4 airo_cs,pcmcia,yenta_socket,rsrc_nonstatic

the bad part is here....

nico@Nico-xubuntu:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                                                              There is already a pid file /var/run/dhclient.eth0.pid with pid 5165
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:06:5b:e2:75:40
Sending on   LPF/eth0/00:06:5b:e2:75:40
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.253 port 67
run-parts: failed to exec /etc/network/if-pre-up.d/cisco-aironet: Exec format error
run-parts: /etc/network/if-pre-up.d/cisco-aironet exited with return code 1
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:06:5b:e2:75:40
Sending on   LPF/eth0/00:06:5b:e2:75:40
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.253
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.253
bound to 192.168.1.102 -- renewal in 33939 seconds.
run-parts: failed to exec /etc/network/if-pre-up.d/cisco-aironet: Exec format error
run-parts: /etc/network/if-pre-up.d/cisco-aironet exited with return code 1
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth2.
run-parts: failed to exec /etc/network/if-pre-up.d/cisco-aironet: Exec format error
run-parts: /etc/network/if-pre-up.d/cisco-aironet exited with return code 1
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up ath0.
run-parts: failed to exec /etc/network/if-pre-up.d/cisco-aironet: Exec format error
run-parts: /etc/network/if-pre-up.d/cisco-aironet exited with return code 1
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up wlan0.

******************
then another....
******************

ico@Nico-xubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
        Flags: bus master, fast devsel, latency 0
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fc000000-fdffffff
        Prefetchable memory behind bridge: e0000000-e7ffffff

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Latitude C640
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf80 [size=32]

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=10, sec-latency=32
        I/O behind bridge: 0000e000-0000ffff
        Memory behind bridge: f4000000-fbffffff
        Prefetchable memory behind bridge: 20000000-24ffffff

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Intel Corporation Latitude C640
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at bfa0 [size=16]
        Memory at 25000000 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
        Subsystem: Cirrus Logic Crystal WMD Audio Codec
        Flags: bus master, medium devsel, latency 0, IRQ 7
        I/O ports at d800 [size=256]
        I/O ports at dc80 [size=64]

00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
        Subsystem: PCTel Inc Dell Inspiron 2100 internal modem
        Flags: medium devsel, IRQ 7
        I/O ports at d400 [size=256]
        I/O ports at dc00 [size=128]

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 00e3
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at c000 [size=256]
        Memory at fcff0000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
        Subsystem: Dell Unknown device 00e3
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at ec80 [size=128]
        Memory at f8fffc00 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at 24000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:01.0 CardBus bridge: Texas Instruments PCI1420
        Subsystem: Dell Unknown device 00e3
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at f8000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: f4000000-f5fff000
        I/O window 0: 0000e000-0000e0ff
        I/O window 1: 0000e400-0000e4ff
        16-bit legacy interface ports at 0001

02:01.1 CardBus bridge: Texas Instruments PCI1420
        Subsystem: Dell Unknown device 00e3
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at f8001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 22000000-23fff000 (prefetchable)
        Memory window 1: f6000000-f7fff000
        I/O window 0: 0000e800-0000e8ff
        I/O window 1: 00001000-000010ff
        16-bit legacy interface ports at 0001

******************
and more.......
******************

sudo mousepad /etc/network/interfaces


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

any idea on how to solve this!?!?!?

---

### Post by kosak on 2006-11-11
im trying to install the drivers provided by cisco (linux-acu-driver.v21.tar.gz)and they say i need to be root to install them, no prob to get root console on... but when i do

sh install

it errors : 

The script needs to be executed as root to operate properly

I try to open the thunar as root ( so super thunar) on the terminal still the same output....

any ideas ??:-D

---

### Post by FrodoB on 2006-11-11
Have you really become root:

$ sudo /bin/bash

Then you are all root.

---

### Post by kosak on 2006-11-28
I tried that but no hope,,, i even tried loggin being root.. no go.. tried sudo, su , logged as root nothing... when i look at the code it looks for $UID = 0 

if [ "$UID" != "0"]
then
echo "This script needs to be xecuted as root to operate properly"
exit 1
fi

if [ $# -ne 0]
then 
while getopts ~~~~~

i thought that by casting  sudo i got a 0 ID.. i think the installer thinks im 1000 (my user)

now i re installed ubuntu 6.10 and doesn't work... this is so bizzar... It worked out of the box with 6.06...:evil:

---

### Post by FrodoB on 2006-11-28
Try

$ sudo /bin/bash -l

See if that helps.

---

### Post by real_ate on 2006-12-06
not sure if your still looking for answers on this but to get that script to work you need to change the first line of it first. i saw that on a how-to a while ago... open it in a text editor and let me know what the first line is

---

### Post by FrodoB on 2006-12-06
Perhaps change the first line to:

#!/bin/bash

instead of

#!/bin/sh

I did see in some version of Ubuntu that /bin/sh was not linked to /bin/bash as it should be.

---

### Post by real_ate on 2006-12-06
yea that was the fix that i was given, it fixed my problems with installing the client but now i can't get the client to work:-k

---

### Post by robobart on 2006-12-07
Ok this is interesting...

I'm running Xubuntu on a T41 with the AIRONET card... 

Wireless does not work for me at all.

Is anyone here running Ubuntu proper and still having this problem? I realize that it shouldn't make a difference, but it never hurts to check.

Maybe I'll burn a live cd of ubuntu and see if it picks up my wireless card. While this wouldn't really be a solution, it would be a start to a solution.

-Bart

---

### Post by real_ate on 2006-12-07
well i have seen a good way to get this working... its a bit extreme and i don't think its a good idea cos we shouldn't have to!! answer is: reinstall when the card is plugged in :(

i think you should be able to do it otherwise but i just don't know enough about linux to get into that stuff! bottom line, installing ubuntu with the card in has workded for other people. for me the card is "working" out of the box, i'm running ubuntu on a HP OmniBook XE3 (old i know) only thing is that all the wireless connections that i'm trying to connect to are leap or peap... i don't even know what that means :/

---

### Post by robobart on 2006-12-07
Ok so my card isn't working with Xubuntu, but it is working with the Ubuntu live cd!

Both versions 6.10 -- also, my card was plugged in both times.

---

