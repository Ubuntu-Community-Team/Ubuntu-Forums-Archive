---
title: "DWL-G122 (H/W Ver. C1) Wireless USB"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by KevinP-Ott on 2007-01-29
I had previously tried to get my Wireless USB to be seen in Mepis 6.0 (a fine distro) but it just refused to see any wireless interface.  After a lot of wrestling with ndiswrapper I fianlly ended up stymied when I went to compile a driver and found out that the default debian kernel headers are not as useful as I had hoped.  Since a  lot of the How-tos I had found referenced Ubuntu I decided to give it a try.

So I install Kubuntu 6.10 on the computer and before I tried the ndiswrapper thing I took a quick look and was surprised to see that Kubuntu seemed to see the wireless adapter.

It sees my USB adapter in 'isusb'. So then I checked 'ifconfig' and sure enough I now see wlan0 ... and wmaster0?  Well, this is better than Mepis I think, but why are there two listed?  Maybe the wmaster0 is an anomoly or general place-holder?  The 'iwconfig' didn't tell me much more but it seems to see the card at least.  

So the question now is, am I mistaken in thinking that it sees the card?  Is this one of those cases where native drivers are messing with me and I really want to get back to ndiswrapper? Or is the USB Adapter seen but I have no way to connect to my network?

kevin@kevin-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz
          RTS thr:off   Fragment thr=2346 B

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          RTS thr:off   Fragment thr=2346 B

kevin@kevin-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:95:31:A2:CA
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0xcc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2368 (2.3 KiB)  TX bytes:2368 (2.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:15:E9:B4:92:D6
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:2160 (2.1 KiB)
          Base address:0x9000

wmaster0  Link encap:UNSPEC  HWaddr 00-15-E9-B4-92-D6-00-90-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x9000

kevin@kevin-desktop:~$ lsusb
Bus 001 Device 004: ID 046d:0870 Logitech, Inc. QuickCam Express
Bus 001 Device 002: ID 045e:0084 Microsoft Corp.
Bus 001 Device 003: ID 07d1:3c03 D-Link System
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

---

### Post by crys on 2007-01-30
Try out the native driver on [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads).
It's the rt73-CVS. It works fine here with my DWL-G122 C1.

Chris

---

