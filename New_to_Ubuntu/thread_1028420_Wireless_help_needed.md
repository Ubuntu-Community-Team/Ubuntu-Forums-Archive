---
title: "Wireless help needed"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by bradwal on 2009-01-02
I installed Ubuntu 8.10 for the first time three days ago but after reading countless threads and guides I still can't figure out how to get my wireless working so I figured I should get help. 

I have a Gateway 4520gz laptop and a Linksys WRT54G wireless router (connected to ethernet right now). I think I have a Broadcom BCM94306 wireless network card and here's a link to my computer's Windows driver downloads if that helps -

[http://support.gateway.com/support/drivers/search.asp?st=pn&param=3727](http://support.gateway.com/support/drivers/search.asp?st=pn&param=3727)

Ive also done ifconfig, iwconfig, lspci, lsusb, and lshw -class network since most responders often ask for these. Any help on getting this to work is appreciated.





bad@ccm:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:10:57:e9  
          inet6 addr: fe80::203:25ff:fe10:57e9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:357076 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:535531296 (535.5 MB)  TX bytes:10952660 (10.9 MB)
          Interrupt:10 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:0e:35:27:e0:72  
          inet6 addr: fe80::20e:35ff:fe27:e072/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3678 errors:0 dropped:0 overruns:0 frame:0
          TX packets:702 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x2000 Memory:e0200000-e0200fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:279 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17919 (17.9 KB)  TX bytes:17919 (17.9 KB)


---------------------------------------------------------------
bad@ccm:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

-----------------------------------------------------------------
bad@ccm:~$ lspci
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
02:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

----------------------------------------------------------
bad@ccm:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


--------------------------------------------------------------------
bad@ccm:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 10
       serial: 00:03:25:10:57:e9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.100 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:27:e0:72
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b2:3f:5e:fc:95:da
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
bad@ccm:~$

---

### Post by mikewhatever on 2009-01-02
You seem to have an Intel PRO/Wireless 2200BG, Broadcom is not mentioned, and that Intel card should work out of the box.

---

### Post by BenAshton24 on 2009-01-02
Quick suggestion.. if your router has WPA security, try changing it to WEP or none just for a minute to see if that works... also see if ipw2200 is listed when your run lsmod

Ben

---

### Post by bradwal on 2009-01-02
Thanks for the quick replies. I just reset my router to the default but still nothing. I guess I really don't know how to connect to it if it's there, Im looking for something basic like a wireless icon in the system tray like XP had. ipw2200 is listed-

ipw2200               151244  0 

edit: I've also tried connecting using the program "Wifi radar" and that didn't do anything

---

### Post by mikewhatever on 2009-01-02
Did you uninstall the network manager and installed wifiradar instead?

---

### Post by wolfen69 on 2009-01-02
disconnect your ethernet for a moment. single click the little computer icon in top right taskbar. what happens?

---

### Post by neu2buntu on 2009-01-02
when u talk about looking for a wireless icon ,am i right in saying you dont see it,..by default it should be on your top panel ,,,if it is off the icon is like 2screens with an orange triangle with an !
  to activate it right click and enable networking and wireless

---

### Post by handydan918 on 2009-01-02
For starters, try ```
sudo dhclient
```

You might also want to install wicd. It seems to help a lot of people with wireless issues.

---

### Post by bradwal on 2009-01-02
> **wolfen69 said:**
> disconnect your ethernet for a moment. single click the little computer icon in top right taskbar. what happens?

Wow, that was simple lol. I guess that's all I needed to do, Ive only ever tried right clicking on that icon. My wireless is working now and I feel like an idiot.

Thanks for the help everyone.

edit: or maybe it was these commands I just tried -

sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo ifconfig eth1] up
sudo iwconfig eth1 essid &#8220;linksys&#8221;
sudo iwconfig eth1 mode Managed
sudo dhclient eth1

either way it's working now

---

