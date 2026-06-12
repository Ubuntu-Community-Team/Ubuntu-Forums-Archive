---
title: "Cannot get stable wifi on Sony TR2MP"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by chrisgeller on 2007-06-29
Continuing problems with wireless - sorry, please help.

I've installed Ubuntu onto My Vaio TR2MP. I haven't been able to keep my wireless stable and functioning. It all worked fine in windows, so I'm sure it's not a hardware/router problem.

My wireless will work fine, for a few minutes or even up to half an hour, then stop, without warning. It can see other wireless networks, and my own. I can connect (illegally) to my neighbours unsecured connection, Ubuntu seems to be able to hold onto that connection. Occasionally, if I wait long enough, it will spontaneously fix itself.

My current iwconfig and ifconfig; when my laptop isn't working:

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"RReynolds"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4B:C6:FE:B8   
          Bit Rate:24 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/100  Signal level=-38 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:365  Invalid misc:0   Missed beacon:52



ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:CC:26:A9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:0E:35:02:F6:E0  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe02:f6e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11470 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:20004832 (19.0 MiB)  TX bytes:1435197 (1.3 MiB)
          Interrupt:9 Base address:0xe000 Memory:e0201000-e0201fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16865 (16.4 KiB)  TX bytes:16865 (16.4 KiB)

Network monitor 2.12.1 reports that I am still connected by my connection, which is at 95% signal strength. It appears to show packets being sent and received, but quite slowly, and the total amount of data is not changing.

Network manager applet 0.6.4 also shows that I am still connected to my connection. However the signal strength seems to vary more. When I click on Connection Information it says "Could not find some required resources (the glade file!)". This is an occasional problem - I think it works sometimes even when my connection doesn't, I think it says I'm connected and there is no problem.

My /etc/network/interfaces file currently states:

auto lo
iface lo inet loopback


#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp




iface eth0 inet dhcp

auto eth0


I'm basically at a loss. I had the idea that my bluetooth was coming on automatically and interfering with the connection. I managed (with the help of this forum, thanks!) to turn it off - no difference.


Any ideas?

---

### Post by into_311 on 2007-06-29
Could you please post the output of 

```
sudo lspci 
``` also? I'm wondering what type of wireless card you are using.

---

### Post by chrisgeller on 2007-06-29
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
02:05.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b8)
02:05.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

As you can see - it's an intel 2200BG - which I thought were meant to work well!

---

### Post by t4thfavor on 2007-06-29
Mine works flawlessly all of the time, Perhaps its your router dropping you. I had quite a few routers that would do that all the time. Its less than noticable in Windows, but Linux is a bit more picky. I would try to flash your router with the latest firmware, and see if that fixes. 

My wifi at work consists of a WEP/128 cloaked ssid on a 2wire dsl modem/11b router.

never fails. 

At home I run Openwrt Kamikaze on a wrt54gv4 which seems to have stability problems (it is a dev build of the firmware). All I did to stop the drops was replace the firmware with an older version marked stable, and the thing has worked ever since. in fact the uptime is measured in months.

---

### Post by chrisgeller on 2007-06-30
Ah well, I have found my laptop's recovery disk and reinstalled XP. Perhaps I will try and set up a dual boot system and continue to play around with Ubuntu.

The last time I tried to make Linux work was 2003 - dependency hell, unstable, someone on a Linux forum telling me to "get a new computer".

This time I've been well impressed with Ubuntu, practically working out of the box, great community helping iron out little problems (e.g. my laptop's weird resolution), the repository system, playing wmv's! But alaptop that can't do wireless? C'mon!

So I guess I'll try again in 2011?

---

