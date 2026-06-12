---
title: "I've lost internet and I don't understand why ..."
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by greppi on 2007-08-20
Hi guys, 

I have a quite strange problem ... I've installed Ubuntu Feisty Fawn and I had no problem with connect to the internet. But one day I installed  a few programs (amarok, kplayer,codecs and ntfs write support) and normally shutdown PC. On another day, when I start Ubuntu again, I've lost my internet connection.

What's wrong ?

I have Flarion DTM Network Interface (based on F-OFDM), it's modem connected via USB.

**lspci**

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8753 [P4X266 AGP] (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0b.0 Modem: Motorola Unknown device 3052 (rev 04)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
```
**ifconfig**

```
eth0      Link encap:Ethernet  HWaddr 00:07:35:B2:2A:7C  
          inet addr:195.91.85.82  Bcast:195.91.87.255  Mask:255.255.248.0
          inet6 addr: fe80::207:35ff:feb2:2a7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:729 (729.0 b)  TX bytes:4155 (4.0 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
```
**iwconfig**

```
lo        no wireless extensions.

eth0      no wireless extensions.
```

**ping google.com -c 3**
ping: unknown host google.com

**ping 72.14.207.99 -c 3**
connect: Network is unreachable

I've found this script, maybe it help you:

[U][http://greppi.bdesign.sk/_rubbish/collectNWData.out](http://greppi.bdesign.sk/_rubbish/collectNWData.out)
[/U]
and my last logs:
[U]
[http://greppi.bdesign.sk/_rubbish/dmesg1.txt](http://greppi.bdesign.sk/_rubbish/dmesg1.txt)[/U]

_[http://greppi.bdesign.sk/_rubbish/syslog1.txt](http://greppi.bdesign.sk/_rubbish/syslog1.txt)_

---

