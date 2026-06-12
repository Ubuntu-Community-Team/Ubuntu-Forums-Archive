---
title: "can see network but can't access"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by LouisvilleLIP on 2007-07-10
I can see my wireless network, but I can't connect.  In Windows, it works, so I'm fairly certain it's between me and the settings on my laptop.  Here is the usual info.  Thanks for your help, I've looked all over for a solution, but I can't figure it out.




eth0      Link encap:Ethernet  HWaddr 00:E0:B8:54:EA:A1  
          inet6 addr: fe80::2e0:b8ff:fe54:eaa1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1025229 (1001.2 KiB)  TX bytes:282983 (276.3 KiB)

eth0:avah Link encap:Ethernet  HWaddr 00:E0:B8:54:EA:A1  
          inet addr:169.254.10.26  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:958 (958.0 b)  TX bytes:958 (958.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0F:3D:3C:C0:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:247 errors:133 dropped:0 overruns:0 frame:0
          TX packets:8 errors:439 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:349114 (340.9 KiB)  TX bytes:684 (684.0 b)
          Interrupt:11 

wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=32/100  Signal level=5/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:439  Invalid misc:0   Missed beacon:0

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:02.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
03:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

---

### Post by sj3fk3 on 2007-07-11
> **LouisvilleLIP said:**
> I can see my wireless network, but I can't connect.  In Windows, it works, so I'm fairly certain it's between me and the settings on my laptop.  Here is the usual info.  Thanks for your help, I've looked all over for a solution, but I can't figure it out.

wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=32/100  Signal level=5/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:439  Invalid misc:0   Missed beacon:0
03:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

How did you config you wireless card to connect to your network? Maybe you can paste that config as well. I don't know what version of Ubuntu you are using, I always recommend to use gnome network manager, because it does make wireless support really easy.

---

### Post by LouisvilleLIP on 2007-07-11
I did use gnome network manager to set up.  I'm not exactly sure how to find the config for the netwok.  How do I do it?

---

### Post by sj3fk3 on 2007-07-11
> **LouisvilleLIP said:**
> I did use gnome network manager to set up.  I'm not exactly sure how to find the config for the netwok.  How do I do it?

Ok, that helps. Do you use WEP or WPA for your wireless network?

n.b.
Every sensible person should use WPA..

---

### Post by LouisvilleLIP on 2007-07-11
I'm willing to use WEP or WPA, but I'm not currently.  I disabled because I thought that the passkey might be complicating things.  My plan is to re-enable WPA once I figure out how to connect without it.

---

### Post by sj3fk3 on 2007-07-11
> **LouisvilleLIP said:**
> I'm willing to use WEP or WPA, but I'm not currently.  I disabled because I thought that the passkey might be complicating things.  My plan is to re-enable WPA once I figure out how to connect without it.

Ok so the problem might be with the network mgr. Can you try to connect to the wlan by hand?

Type in one terminal

sudo iwevent wlan0

Type in other term sudo iwconfig wlan0 ESSID ssid-name

and watch what happens, maybe paste the output of iwevent

---

