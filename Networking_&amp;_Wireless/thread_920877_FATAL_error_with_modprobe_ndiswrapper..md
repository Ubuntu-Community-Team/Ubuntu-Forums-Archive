---
title: "FATAL error with modprobe ndiswrapper."
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by osdarodi on 2008-09-15
**[COLOR="Blue"]Hello, mi name is david and  i am begginer in ubuntu, i have o.s. ubuntu 8.04 in CD and i can't connect to internet via wifi :(, i have this error:[/COLOR]**

david@david-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
david@david-laptop:~$ sudo depmod -a
david@david-laptop:~$ sudo modprobe ndiswrapper
[COLOR="Red"]FATAL: Module ndiswrapper not found.[/COLOR]
david@david-laptop:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:16:36:a9:61:b5  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:20 Dirección base: 0x6000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:2602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2602 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:131316 (128.2 KB)  TX bytes:131316 (128.2 KB)

david@david-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


[COLOR="Blue"]**please help me, thank you very much. Sorry for my english:)**.[/COLOR]

---

### Post by Ayuthia on 2008-09-15
If you do this in the terminal:
```
ls /lib/modules/2.6.24-20-generic/ubuntu/misc/ndiswrapper
```Does it return:
```
ndiswrapper.ko
```

If it does, please do:
```
sudo depmod -a
```
If it does not, try reinstalling linux-ubuntu-modules:
```
sudo aptitude install linux-ubuntu-modules-`uname -r`
```
The ` is a back-quote and not a single quote '.  It will replace uname -r with your kernel version.

Hope that helps.

---

### Post by osdarodi on 2008-09-16
Thank you very much

---

