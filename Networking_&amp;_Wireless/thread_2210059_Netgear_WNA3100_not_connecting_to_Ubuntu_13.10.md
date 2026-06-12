---
title: "Netgear WNA3100 not connecting to Ubuntu 13.10"
date: 2014-03-08
forum: Networking &amp; Wireless
---

### Post by Jim Hornet on 2014-03-08
Hello 

Having issues with new wi-fi card. I have searched the forums and previous post but haven't been able to solve my issue. I used WINE and Windows Wireless Tool and downloaded Netgear software from the official site and installed.

My wi-fi is now enable (I can see the wifi icon in myconnections tab). I try to connect to my wi-fi and after 30 or so seconds of trying the "Wi-fi Network Authentication Required" keeps popping up. No joy :(

Please note I am using my ethernet atm to get the below results so wi-fi is off.
```

junkyard@junkyard:~$ lsusb
Bus 001 Device 006: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
```

```
junkyard@junkyard:~$ iwconfig
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.
```


```
junkyard@junkyard:~$ sudo modprobe ndiswrapper
[sudo] password for junkyard: 
junkyard@junkyard:~$ sudo modprobe ndiswrapper
junkyard@junkyard:~$ sudo modprobe ndiswrapper
junkyard@junkyard:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
    device (0846:9020) present
junkyard@junkyard:~$ dmesg | grep ndis
[   10.131218] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[   10.135028] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   10.837339] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[   11.299003] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc1ff000, 16000, 4
[   11.299012] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc202e80, 16000, 5
[   11.299017] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc206d00, 16000, 5
[   11.299024] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc20ab80, 16000, 5
[   11.299028] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc20ea00, 16000, 5
[   11.299032] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc212880, 16000, 5
[   11.299036] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc216700, 16000, 5
[   11.299040] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc21a580, 16000, 5
[   11.299043] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc21e400, 16000, 5
[   11.299047] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc222280, 16000, 5
[   11.299051] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc226100, 16000, 4
[   11.299055] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc229f80, 16000, 5
[   11.299059] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc22de00, 16000, 5
[   11.299062] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc231c80, 16000, 5
[   11.299066] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc235b00, 16000, 5
[   11.299071] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc239980, 16000, 5
[   11.299075] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc23d800, 16000, 5
[   11.299079] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc241680, 16000, 5
[   11.299083] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc245500, 16000, 5
[   11.299086] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc249380, 16000, 5
[   11.299090] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc24d200, 16000, 5
[   11.299094] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc251080, 16000, 4
[   11.299098] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc254f00, 16000, 5
[   11.299102] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc258d80, 16000, 5
[   11.299107] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc25cc00, 16000, 5
[   11.299111] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc260a80, 16000, 5
[   11.299115] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc264900, 16000, 5
[   11.299121] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc268780, 16000, 5
[   11.299124] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc26c600, 16000, 5
[   11.299128] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc270480, 16000, 5
[   11.299132] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc274300, 16000, 5
[   11.299136] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc278180, 16000, 4
[   11.299140] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc27c000, 16000, 4
[   11.299144] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc27fe80, 16000, 5
[   11.299147] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc283d00, 16000, 5
[   11.299151] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc287b80, 16000, 5
[   11.299155] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc28ba00, 16000, 5
[   11.299159] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc28f880, 16000, 5
[   11.299163] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc293700, 16000, 5
[   11.299166] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc297580, 16000, 5
[   11.299170] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc29b400, 16000, 5
[   11.299174] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc29f280, 16000, 5
[   11.299178] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc2a3100, 16000, 4
[   11.299181] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc2a6f80, 16000, 5
[   11.299185] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc2aae00, 16000, 5
[   11.299191] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc2aec80, 16000, 5
[   11.299195] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc2b2b00, 16000, 5
[   11.299199] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc2b6980, 16000, 5
[   11.299204] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc2ba800, 16000, 5
[   11.299208] ndiswrapper (MmBuildMdlForNonPagedPool:1864): fc2be680, 16000, 5
[   11.325237] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[   11.622703] usbcore: registered new interface driver ndiswrapper
```

I'm not sure what I need to next - This is my second attempt at Ubuntu - my last wifi issue with a Ralink adpter broke me.

2nd attempt at Linux for me - wish me luck

Thanks

edit not sure if this helps:
wifi.text gedit
```
[   10.837339] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[   11.608146] wlan0: ethernet device 44:94:fc:eb:ff:ff using NDIS driver: bcmwlhigh5, version: 0x564442e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[   11.615904] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   12.298401] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.298928] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.367581] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.368398] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  459.400798] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

```
junkyard@junkyard:~$ arch
i686
```


```
junkyard@junkyard:~$ sudo modprobe ndiswrapper
[sudo] password for junkyard: 
junkyard@junkyard:~$ sudo modprobe ndiswrapper
junkyard@junkyard:~$ dmesg | grep ndis
[    8.061909] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[    8.063314] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[    8.257027] usbcore: registered new interface driver ndiswrapper
junkyard@junkyard:~$ ndiswrapper -l
```

sorry guys just confused I have followed as much as I can from suggestions from other posts (thanks chilli555) i am sure I have installed the correct drivers etc ??? not sure how to proceed?

---

### Post by Jim Hornet on 2014-03-10
```
junkyard@junkyard:~$ sudo lsusb
[sudo] password for junkyard: 
Bus 001 Device 007: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 006: ID 0bc2:3312 Seagate RSS LLC 
Bus 001 Device 005: ID 0d8c:5200 C-Media Electronics, Inc. Mass Storage Controller(0D8C,5200)
Bus 001 Device 004: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04fc:0013 Sunplus Technology Co., Ltd ViewMate Desktop Mouse CC2201
Bus 002 Device 002: ID 045e:00bb Microsoft Corp. Fingerprint Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
```
junkyard@junkyard:t:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:b8:47:23
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=220.237.26.91 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:18 ioport:ec00(size=256) memory:fdeff000-fdeff0ff memory:fdd00000-fdd0ffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 44:94:fc:eb:ff:ff
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwlhigh5 driverversion=1.58+Netgear,03/28/2011, 5.100.6 link=no multicast=yes wireless=IEEE 802.11g
```

anybody know what I can do next? I don't get why it doesnt work - IO reinstalled Windows XP to make sure the wi-fi adaptor wasn't faulty but worked well with XP - so I have dual booted Ubuntu 13.10 with XP (which I really didnt want to do but its the only way I can get my wifi working) 

Just a thought: if I rolled back Ubuntu 13.10 back to 12.04 would it work?

arghhh I love Ubuntu but wifi issue keep me from using this

wifi keeps try to connect but has never connected - keep getting "Wi-Fi Authentication Required" keep pooping up every 30 seconds.....

---

### Post by kurt18947 on 2014-03-10
You say this adapter is new.  Any chance you can return it?  Netgear's WNA3100 doesn't have a great rep with linux as you may have discovered, WNA3100v2 is worse.  There are adapters that you can plug in and they work.  Netgear's WNA1100 is one (uses an Atheros chipset) though it I think it maxes out at 150 mb./sec.  Another is Tenda W311mi using RealTek's RT5370 chip, same 150 mb./sec.  A favorite of mine is Trendnet TEW-649UB using Realtek's RTL8192SU chipset.  Very good signal strength and speed 300 mb./sec down, 150 mb./sec up.  Adapters using Realtek RTL8192**CU** chips seem more common but they don't work out of the box.  They do work using a patched Realtek driver.

The 8192SU chipset based adapters may have one niggle.  If I suspend then resume, the wifi will not reconnect.  Unplug then replug the adapter and it works.  The problem is that the adapter doesn't suspend properly. Because it doesn't suspend properly, it can't resume.  There is a simple fix.

---

### Post by Jim Hornet on 2014-03-10
Thanks Kurt for suggestion -   Has anyone had any problems with the below adaptor?  D-Link DWA131 Wireless N USB Adaptor $39 or I may try ebay.

---

### Post by kurt18947 on 2014-03-10
> **Jim Hornet said:**
> Thanks Kurt for suggestion -   Has anyone had any problems with the below adaptor?  D-Link DWA131 Wireless N USB Adaptor $39 or I may try ebay.

Oh boy.  The early D-Link DWA131s were perfect - they were twins to the Trendnet TEW-649UB using the RealTek RTL-8192SU chip set.  Then D-Link switched chipsets to something - I'm not certain what - that was not plug'n'play.  The only way to know which one you were buying was to open the package and read the label on the device.  The 'problem child' was ver.B or v.2 or something like that.  That's been a while ago so I don't know how much of the original stock is left in the pipeline.  If you have a strong wifi signal, the Tenda W311mi seems like a pretty good bet.

It's not unheard of for manufacturers do switch chipsets without changing model designation.  That's what makes recommending a "works-out-of-the-box" device a little dicy.  It appears to me that D-Link is pretty prone to that behavior though.  I use a web site called wikidevi.com to check devices against chipsets.  It's not perfect but I haven't found better so far.  In my experience, finding a plug'n'play wireless adapter is one of the bigger challenges  to setting up a linux machine.  The good news is that once you find an adapter that works well and is supported natively,  it stays supported for quite some time. 

 I have an old RealTek RTL8187B device that I bought when starting with Ubuntu 9.04 I think.  It still works as soon as its plugged in.  It's useful to have a wireless adapter like that, even if it's slow and ugly.  Many of the newest gee-whiz devices require downloading firmware, an updated driver or something requiring an internet connection.  If you don't have access to a wired ethernet connection, how do you download the software to make your latest sexy gee-whiz wonder work?  With your old, slow, ugly but works-every-time adapter, of course:D.

---

