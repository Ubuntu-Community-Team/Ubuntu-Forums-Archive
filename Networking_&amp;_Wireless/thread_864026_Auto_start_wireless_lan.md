---
title: "Auto start wireless lan"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by sparky100 on 2008-07-19
I am struggling to get my wireless LAN to start automatically. If can start sudo modprobe ndiswrapper.

What have I tried, Run sudo ndiswrapper -m,   modifed  etc/modules and added ndiswrapper to the end of the  file. My etc/network/interfaces file contains

auto lo
iface lo inet loopback
auto wlan0

When I add  ndiswrapper to  etc/modules my boot up appears to stop at

Jul 19 08:54:39 simon-desktop avahi-daemon[5083]: No service file found in /etc/avahi/services.

with a timeout

Any suggestions or additional information required?

Simon

---

### Post by zipperback on 2008-07-19
Please tell me the specifications for your system and what version of Ubuntu.

Please also provide the output from the following commands:

```

lspci
lsusb
ifconfig
iwconfig

```


You might not need to use ndiswrapper.


- zipperback
:popcorn:

---

### Post by sparky100 on 2008-07-20
lspci

00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01)
00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07)
00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06)
00:08.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
00:09.0 Communication controller: Agere Systems 56k WinModem (rev 01)
00:0a.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
00:0b.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0b.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0b.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0b.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:0c.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
01:05.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

lsusb
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01)
00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07)
00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06)
00:08.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
00:09.0 Communication controller: Agere Systems 56k WinModem (rev 01)
00:0a.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
00:0b.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0b.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0b.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0b.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:0c.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
01:05.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1727 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1727 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:90016 (87.9 KB)  TX bytes:90016 (87.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:d8:d4:56:ae  
          inet addr:192.168.1.138  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fed4:56ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1774 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1542 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1893030 (1.8 MB)  TX bytes:273416 (267.0 KB)
          Interrupt:10 Memory:effd0000-effe0000 

iwconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1727 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1727 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:90016 (87.9 KB)  TX bytes:90016 (87.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:d8:d4:56:ae  
          inet addr:192.168.1.138  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fed4:56ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1774 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1542 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1893030 (1.8 MB)  TX bytes:273416 (267.0 KB)
          Interrupt:10 Memory:effd0000-effe0000 

I am running Hardy Heron on a AMD athlon machine

Simon

---

