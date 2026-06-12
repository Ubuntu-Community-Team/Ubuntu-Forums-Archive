---
title: "Cannot access wireless network in 10.04"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by Dovdimus Prime on 2010-08-10
I have just installed 10.04 on a laptop which also has XP. It has a Dell Truemobile 1150 wireless adapter. Ubuntu appears to automatically detect the wireless network, and bizarrely, at one point it was able to connect and I surfed the web for a bit.

But now, it seems unable to connect. The wireless network icon has an exclamation mark, no matter how often I ask it to reconnect. I have tried restarting the system.

During all of this, an XP netbook was able to connect without difficulty.

Does anyone have any suggestion what might be happening, or what tools I might use to try to diagnose the problem?

Thanks

David

---

### Post by S.R on 2010-08-10
In the terminal type ifconfig and post results.

---

### Post by tommy223 on 2010-08-10
try plugging it into a router and updating it....under system- administration look for hardware drivers..look for one and activate it.

---

### Post by Dovdimus Prime on 2010-08-11
> **S.R said:**
> In the terminal type ifconfig and post results.

Here you go:

eth0      Link encap:Ethernet  HWaddr 00:11:43:60:7d:fa  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:7 

eth1      Link encap:Ethernet  HWaddr 00:02:2d:7b:88:e6  
          inet6 addr: fe80::202:2dff:fe7b:88e6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:371 (371.0 B)  TX bytes:3297 (3.2 KB)
          Interrupt:11 Base address:0xd100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by Dovdimus Prime on 2010-08-12
> **tommy223 said:**
> try plugging it into a router and updating it....under system- administration look for hardware drivers..look for one and activate it.

Thanks, I tried that this morning but I got something along the lines of 'No proprietary drivers were found on this system'. Presumably this means there are no better drivers out there?

---

### Post by realzippy on 2010-08-12
maybe a orinoco wireless card which cannot run WPA...

Can you run this in terminal and post the output

```
lspci | grep Wireless
```

so we know which wireless chip/card is running?

---

### Post by Dovdimus Prime on 2010-08-12
> **realzippy said:**
> maybe a orinoco wireless card which cannot run WPA...

Can you run this in terminal and post the output

```
lspci | grep Wireless
```so we know which wireless chip/card is running?

I get nothing. When I just do lspci, I get:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

---

### Post by zdenal on 2010-08-25
I'm not sure if your wireles card is based on the Broadcom chip, but I had simmilar problem with my Dell Wireless.

Try this HowTo

[http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx](http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx)

and let me know if it helps or not.

---

