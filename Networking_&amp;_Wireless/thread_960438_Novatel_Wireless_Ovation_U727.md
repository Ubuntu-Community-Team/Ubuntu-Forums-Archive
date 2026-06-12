---
title: "Novatel Wireless Ovation U727"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by grungedoobie on 2008-10-27
Has anyone out there actually been able to get their Novatel Wireless Ovation U727 to work in Kubuntu Hardy on a 64bit laptop?

I have been able to connect to the hardware from terminal and get it to uplink with KPPP, but the knetworkmanager manager refuses to see it.  I've tried using KPPP through knetworkmanager options and straight from KPPP itself, neither has the desired affect.

First problem I run in to is that whenever the laptop is rebooted, or the card is unplugged, I have to go back to terminal and reset the hardware link.

If it's plugged into usb before boot, Kubuntu doesn't even see it.  If it's plugged in after boot, Kubuntu only sees it as a mass storage device.

Here are the commands I use to connect to the hardware in terminal:

sudo modprobe -r usbserial

sudo modprobe usbserial vendor=1410 product=4100

sudo dmesg|grep -i ttyUSB

ifconfig (which pulls up the following)

"eth0      Link encap:Ethernet  HWaddr 00:1e:68:78:3e:41
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:99.200.183.204  P-t-P:209.97.107.28  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:64 (64.0 B)  TX bytes:97 (97.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:5d:4d:6f
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe5d:4d6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3765 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1670 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2620014 (2.4 MB)  TX bytes:304414 (297.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-5D-4D-6F-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)"

Thanks in advance for any helps or pointers 8-)

The Grunge

---

### Post by grungedoobie on 2008-10-27
I feel so stupid.  :mad:  The dongle is through Sprint, and they don't have coverage in my location!

The other thing though, is there a way to have this thing connect without having to go through the terminal setup every time?

---

### Post by grungedoobie on 2009-03-22
If anyone is interested, this thread can be closed.  It turned out to be a clash in KNetworkManager.  KNetworkManager was unable to use the Novatel device driver to connect.  All I had to do was install a more capable network device manager then tie that in with KNetworkManager and all is well in the land of the Penguins.

If a mod comes across this post, they can view this one as solved.


The Grunge.  :)

---

