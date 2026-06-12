---
title: "messed up with both of my rt73 and rt61 modules and now i'm lost"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by SysStream on 2008-04-21
I'm a new linux/ubuntu user and I'm happy with ubuntu.

I have three wireless interfaces. One of it is an ethernet controller, the RTL8810SC. Another two is a TP-LINK TL-WN321G, which uses the rt73 chipset and a D-Link DWL-G510 revision b, which uses the rt61chipset.

i've installed ubuntu hardy several times before because i was too noob. the grub messed up a few times.

on a fresh installation on ubuntu hardy, it detects all three wireless interfaces but the rt73 performs abit choppy. and i planned on turning the rt73 to a wireless sniffing device. so it happens that:

i removed the modules and made way for the serialmonkey modules.

i used the howto on this page: [http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73)

ok. it compiled. blablabla. and then when i tried to bring the device up via

```
sudo ifconfig wlan0 up
```

i got this error:

 ```
SIOCSIFFLAGS: Invalid argument
```

and the funny things is:

```
wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

the hwaddr points 00:00:00:00:00:00


now im lost. i've reached a point where all things i tried gave me no luck.. *looks at the windows xp cd*


but anyway, anyone? opinion?

---

### Post by SysStream on 2008-04-21
lspci:

```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)
02:00.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
02:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
```


iwconfig:


```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```


it detects only my rt73.. my rt61 wont load at all.

im lost :S

---

