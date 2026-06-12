---
title: "Notebook won't detect wireless network"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by Armor on 2007-02-05
I have wireless broadcasting just fine, problem is I can't get my notebook to detect it and hop on. 

Here's all the information I think you guys might ask me, from browsing and seeing what other people were asked. I really have no clue what to do here. Right now, the notebook is wired into my router so it has Internet. I tried the basic steps like going to Network from System > Administration and making sure that everything else but my wireless card was disabled, there is no encryption turned on right now for wireless router. I read something about ndswrapper. Do I need this? When I go to the Networking from System > Administration, it shows that I have a wireless connection. The information below is without screwing with anything or activating anything it's with a FRESH install of Edgy, no fancy anythings just straight up Edgy and no network settings have been messed with. At first I tried doing all kinds of things, but this somehow screwed things up beyond repair and made my Wireless connection not even appear anymore so I reinstalled Edgy. Now that I reinstalled it, I just have my wired network working right now. Plz help!!

> leigh-mobile@leigh-mobile:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

leigh-mobile@leigh-mobile:~$ 


And

> 
leigh-mobile@leigh-mobile:~$ lspci
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
02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
leigh-mobile@leigh-mobile:~$ 

> leigh-mobile@leigh-mobile:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:1C:A5:CD  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe1c:a5cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:127624 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:192862559 (183.9 MiB)  TX bytes:4449827 (4.2 MiB)
          Interrupt:10 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

leigh-mobile@leigh-mobile:~$ 

> leigh-mobile@leigh-mobile:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
leigh-mobile@leigh-mobile:~$ 


---

### Post by Armor on 2007-02-05
Anyone?

---

### Post by spd106 on 2007-02-05
Try following this guide [http://www.ubuntuforums.org/showthread.php?t=340689](http://www.ubuntuforums.org/showthread.php?t=340689)

---

### Post by Armor on 2007-02-07
Hurrah! It works. Now, I have two questions - and I don't want to screw anything up so I'm going to ask first rather than try anything, because it seems like my wireless connection is very fragile...

1) Right now, I don't have secuirty setup on my router. Will it screw things up if I turn it on?
2) Can I use something like Wifi-Radar to detect wireless networks and hop on those if I bring my notebook somewhere else?

---

### Post by Armor on 2007-02-07
Nevermind I decided to try to screw around anyway, it works! WEEEEEEEEEEEEEEEEEEEEEEEEEE!!!!!!!!!!

---

