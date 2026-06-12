---
title: "Need help getting wireless to work"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by mern1 on 2009-08-07
I just installed Ubuntu on my friend's old Compaq Evo N800c laptop.  Everything worked great except the wireless.  I'm not sure that any drivers were installed and I don't know how to even turn the wireless on (there is no hardware switch only Fn + F2).  Can anyone help?  Thanks

---

### Post by pastalavista on 2009-08-07
Check in System > Administration > Hardware Drivers. And activate any wireless drivers there. Then right-click on the network-manager icon in the upper right panel and check 'enable wireless'. Also you could check the output of ```
lshw -c network

lspci | grep 802.11

ifconfig
```
to see if your card is recognized

---

### Post by mern1 on 2009-08-07
There are no drivers listed in the Hardware Drivers menu.  Also, there is no "enable wireless" option after right-clicking the network icon in the upper right corner.  

```
laptop:~$ lswh -c network
bash: lswh: command not found
laptop:~$ lspci | grep 802.11
laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:02:69:d9:5c  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fe69:d95c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3676 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3621 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3215116 (3.2 MB)  TX bytes:727516 (727.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```

---

### Post by superprash2003 on 2009-08-07
its lshw -C network with a capital C

---

### Post by mern1 on 2009-08-08
```
laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:08:02:69:d9:5c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A ip=192.168.1.105 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 06:6e:d8:b7:e7:20
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by halitech on 2009-08-08
post the full output of
```
lspci
```and ```
lsusb
```

---

### Post by mern1 on 2009-08-09
```
laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:04.0 Communication controller: Agere Systems LT WinModem (rev 02)
02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0e.0 USB Controller: NEC Corporation USB (rev 41)
02:0e.1 USB Controller: NEC Corporation USB (rev 41)
02:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 02)

```

```
laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 049f:0033 Compaq Computer Corp. 802.11b Adapter [orinoco]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by halitech on 2009-08-10
the only thing I can find is that you need to download a firmware 

more info here

[https://wiki.ubuntu.com/OrinocoMonitorMode](https://wiki.ubuntu.com/OrinocoMonitorMode)

---

### Post by mapes12 on 2009-08-10
Hi there,

I found this which I think makes reference to your wifi adapter:

[https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200)

Mark

---

### Post by MrJoeyUK on 2009-08-10
I had the same problem when I first switched to Ubuntu.. what I did was blacklist my current ndiswrapper drivers and did a fresh install, and walla! If you need any reference, have a look here: [http://ubuntuforums.org/showthread.php?t=857810&page=5](http://ubuntuforums.org/showthread.php?t=857810&page=5), 

the solution which worked for me was following falcon61102's post on the 5th page. Hope it helps you too.

---

### Post by mern1 on 2009-09-08
I had some issues when following the "[OrinocoMonitorMode]("https://wiki.ubuntu.com/OrinocoMonitorMode")" guide.  

At step 3 I got the following error:

```
E: Couldn't find package linux-headers-686

```

I didn't think this was major so I continued...

At step 4 nothing worked because I think its dependent on step 3

At step 5 I got the following error when trying to run make:

```
laptop:/orinoco/orinoco-0.13e-SN-8# make
make -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/orinoco/orinoco-0.13e-SN-8 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /orinoco/orinoco-0.13e-SN-8/hermes.o
/orinoco/orinoco-0.13e-SN-8/hermes.c:41:26: error: linux/config.h: No such file or directory
make[2]: *** [/orinoco/orinoco-0.13e-SN-8/hermes.o] Error 1
make[1]: *** [_module_/orinoco/orinoco-0.13e-SN-8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [modules] Error 2

```

As that didn't turn out too well I didn't try step 6 ("Install it")

Can anyone shed some light on all this?  I just want my wireless to work; does it really have to be this hard?

---

### Post by halitech on 2009-09-08
all steps are dependant on the preceding steps working. For step 3, try this instead
```
sudo apt-get install linux-headers-`uname -r`
```

note: the ` are backticks, not single quotes so might be easier to copy and paste the text instead of typing it in if you can.

---

### Post by mern1 on 2009-09-08
Thanks, that helped but I still get the same error when I try to make @ step 5:

```
laptop:/orinoco/orinoco-0.13e-SN-8# make
make -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/orinoco/orinoco-0.13e-SN-8 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /orinoco/orinoco-0.13e-SN-8/hermes.o
/orinoco/orinoco-0.13e-SN-8/hermes.c:41:26: error: linux/config.h: No such file or directory
make[2]: *** [/orinoco/orinoco-0.13e-SN-8/hermes.o] Error 1
make[1]: *** [_module_/orinoco/orinoco-0.13e-SN-8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [modules] Error 2

```

I have no idea what any of that means.

---

### Post by mern1 on 2009-09-10
bump ?

---

### Post by mern1 on 2009-09-23
bump

---

