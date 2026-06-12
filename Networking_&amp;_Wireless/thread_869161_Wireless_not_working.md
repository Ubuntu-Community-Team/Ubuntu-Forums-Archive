---
title: "Wireless not working"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by rosslev on 2008-07-24
Hopefully somebody may be able to help with this one as it has got me really stuck.

I cannot seem to get any kind of wireless connection on my laptop, I have tried using the internal card, 2 PCMCIA cards  and 2 usb sticks, all of which seem to be detected fine, some automatically used restricted drivers, some didn't. However the wireless functionality seems to be disabled.  when I right click the network icon on the top right of the gnome panel the wireless option is greyed out. I am able to connect via ethernet cable only. The wireless is proven working by another PC

any ideas?

---

### Post by ModelM on 2008-07-24
Just because the wireless cards are detected that doesn't mean the proper drivers are installed & configured. 

To begin, list here which wireless cards you have available & the folks who know can choose the one which easiest to get working & we can go from there.

---

### Post by Kevbert on 2008-07-24
It's probably best to use the internal wireless card.  Please enter the following in terminal and post the responses to each command:
```
lspci
iwconfig
ifconfig
```

---

### Post by rosslev on 2008-07-25
Thanks,
My main concern is that one of the pcmcia cards that I used was the same Atheros based card I used in my previous laptop with edgy, and it always worked fine without installing a driver, now when I plug it into my new laptop running Hardy, It shows up under the restricted hardware manager as using the atheros driver, but wireless is still disabled under the connection manager.

I woudl however prefer to get the internal card working if possible.

Here are the responses to those commands;



```
lspci

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
02:05.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:06.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:09.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
```



```
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-94 dBm  Noise level=-94 dBm
          Rx invalid nwid:1043  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

```


```
ifconfig

ath0      Link encap:Ethernet  HWaddr 00:03:2f:15:c2:f8  
          inet6 addr: fe80::203:2fff:fe15:c2f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:0a:e4:23:07:21  
          inet addr:192.168.2.106  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fe23:721/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19150 (18.7 KB)  TX bytes:12857 (12.5 KB)
          Interrupt:10 

irda0     Link encap:IrLAP  HWaddr 00:24:ff:4a  
          UP RUNNING NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:34112 (33.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3056 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3056 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:152800 (149.2 KB)  TX bytes:152800 (149.2 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-03-2F-15-C2-F8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1051 errors:0 dropped:0 overruns:0 frame:1015
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:157398 (153.7 KB)  TX bytes:1610 (1.5 KB)
          Interrupt:10
```

---

### Post by Kevbert on 2008-07-25
Interesting. The PC wireless interface is an Intel ipw2100 on eth1 and your PCMCIA Atheros is on ath0 but can't see any network. 
The Intel is turned off.  Is there an on/off wireless switch on the laptop ?
If there is and it still doesn't work when you press the switch, do you have Windows on the laptop ?  I had a similar problem on my Acer laptop.  In windows I turned on the wireless, then rebooted into Ubuntu and the card was then detected (also an ipw2100).
If you still have problems there is linux software available via the Intel [[COLOR="Red"]Website[/COLOR]]("http://www.intel.com/support/notebook/sb/cs-006408.htm").

---

